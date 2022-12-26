---
name: Troubleshooting
name: Resolução de Problemas
icon: "images/troubleshoot.svg"
aliases:
  - /pt/docs/troubleshooting
---

# Troubleshooting
# Resolução de Problemas

{{< faq "A aplicação parou de funcionar com a mensagem `securecookie: hash key is not set`" "securecookie-hash-key-not-set">}}
After a recent change in the [github.com/gorilla/sessions](http://www.gorillatoolkit.org/pkg/sessions) Buffalo applications will fail to start with the error `securecookie: hash key is not set`.
Depois de uma mudança recente na [github.com/gorilla/sessions](http://www.gorillatoolkit.org/pkg/sessions) as aplicações em Buffalo falharão ao iniciar com a seguinte mensagem de erro `securecookie: hash key is not set`.

To fix this you must set an environment variable named `SESSION_SECRET`.
Para corrigir isto deves definir uma variável de ambiente com o nome `SESSION_SECRET`.

For information see [github.com/gobuffalo/buffalo/issues/1067](https://github.com/gobuffalo/buffalo/issues/1067)
Para mais informações consulte [github.com/gobuffalo/buffalo/issues/1067](https://github.com/gobuffalo/buffalo/issues/1067)
{{< /faq >}}
      
{{< faq "A linha de comando está lenta" "slow-commands">}}
If executing `buffalo --help` or any other command from the terminal takes longer than expected, set `export BUFFALO_PLUGIN_PATH=$GOPATH/bin` in your shell config (e.g. .bash_profile).
Se a execução de `buffalo --help` ou qualquer outro comando de terminal demora mais do que o esperado, configure `export BUFFALO_PLUGIN_PATH=$GOPATH/bin` na tua configuração do shell (por exemplo, `bash_profile`).
{{< /faq >}}


{{< faq "Não consegue encontrar o binário `buffalo`." "binary-not-found">}}
If you can't find the `buffalo` binary after a successful installation, this is problably caused because `$GOPATH/bin`, or `%GOPATH\bin` (Windows), isn't in your `$PATH` variable. When a Go binary is installed it is placed in `$GOPATH/bin`. Adding this to your global `$PATH` will allow you to find **any** Go binary everywhere in your system. See [golang.org/doc/code.html#GOPATH](https://golang.org/doc/code.html#GOPATH) for more details.
Se não consegues encontrar o binário de `buffalo` depois de uma instalação bem-sucedida, isto está acontecendo porque provavelmente a `$GOPATH/bin`, ou `%GOPATH\bin` (Windows), não é a tua variável de `$PATH`. Quando um binário de Go é instalado ele é colocado em `$GOPATH/bin`. Adicionando isto a tua `$PATH` global te permitirá encontrar **qualquer** binário de Go em qualquer lugar no teu sistema. Consulte [golang.org/doc/code.html#GOPATH](https://golang.org/doc/code.html#GOPATH) para mais detalhes.
{{< /faq >}}

{{< faq "`buffalo new` falha ao gerar um projeto completo." "failed-to-gen">}}
This happens because the `buffalo new` command cannot find the templates it needs to generate a new application.
Isto acontece porque o comando `buffalo new` não consegue encontrar os modelos que ele precisa para gerar uma nova aplicação.


There are a couple of things that could cause this issue.
Há algumas coisas que poderiam causar este problema.

* Using multiple `$GOPATH`s. This can happen when you install Buffalo to one `$GOPATH` and then create a new, temporary, `$GOPATH` and try to create a new application there. Because the templates are in the first, original `$GOPATH`, the installer does not find them, and subsequently generates an incomplete application. To fix this, use just one `$GOPATH`.
* Utilizando vários `$GOPATH`. Isto pode acontecer quando instalas a Buffalo para uma `$GOPATH` e depois crias uma nova, temporariamente, `$GOPATH` e tentas criar uma nova aplicação lá. Visto que os modelos estão no primeiros, `$GOPATH` original, o instalador não os encontra, posteriormente gera uma aplicação incompleta. Para corrigir isto, utilize apenas um `$GOPATH`.

* Using a single `$GOPATH`. If you aren't using multiple `$GOPATH`s and are still seeing this issue, it is most likely caused by a bad installation. Run `$ go get -u -v github.com/gobuffalo/buffalo/buffalo` again, and it should, hopefully, repair the installation for you.
* Utilizando um único `$GOPATH`. Se não estiveres utilizando vários `$GOPATH` e continuas vendo este problema, é muito provavelmente seja causado por uma má instalação. Execute `$ go get -u -v github.com/gobuffalo/buffalo/buffalo` novamente, e deve, com sorte, reparar a instalação por ti.

The original ticket for this issue can be found at [github.com/gobuffalo/buffalo/issues/629](https://github.com/gobuffalo/buffalo/issues/629).
{{< /faq >}}
O bilhete original para este problema pode ser encontrado em [github.com/gobuffalo/buffalo/issues/629](https://github.com/gobuffalo/buffalo/issues/629).

{{< faq "`buffalo new` falha com problemas de permissões do NPM." "npm-permissions">}}
This is caused by incorrectly setup Node/NPM installation.
Isto é causado por configurar a instalação da Node e do NPM incorretamente.

See [docs.npmjs.com/resolving-eacces-permissions-errors-when-installing-packages-globally](https://docs.npmjs.com/resolving-eacces-permissions-errors-when-installing-packages-globally) for information on how to fix this issue.
Consulte [docs.npmjs.com/resolving-eacces-permissions-errors-when-installing-packages-globally](https://docs.npmjs.com/resolving-eacces-permissions-errors-when-installing-packages-globally) para obter informação a respeito de como corrigir este problema.
{{< /faq >}}


{{< faq "`buffalo dev` reconstrução automática não funciona com NFS." "nfs-rebuild">}}
This is caused by the `fsnotify` package not supporting NFS.
Isto é causado porque o pacote `fsnotify` não suporta a NFS.

See [github.com/gobuffalo/buffalo/issues/620](https://github.com/gobuffalo/buffalo/issues/620) for more details and a workaround.
Consulte [github.com/gobuffalo/buffalo/issues/620](https://github.com/gobuffalo/buffalo/issues/620) para obter mais detalhes e uma forma de dar a volta a isto.
{{< /faq >}}

{{< faq "`buffalo new` falha com `import path does not begin with hostname`" "import-begins-hostname">}}
This is caused by a mismatched `$GOPATH` and file system.
Isto é causado por uma disparidade em `$GOPATH` e no sistema de ficheiro.


```text
GOPATH: /Users/foobar/Documents/Programming/Go
ACTUAL: /Users/foobar/Documents/programming/go
```

Those are not the same and cause problems with a lot of Go tools. Correct the `$GOPATH` to match the file system and retry.
Aqueles não são os mesmos problemas causados com uma muitas ferramentas de Go. Corrija o `$GOPATH` para corresponder o sistema de ficheiro e tentar novamente, 
{{< /faq >}}

{{< faq "`buffalo new` falha procurando por `golang.org/x/tools/go/gcimporter`" "gcimporter">}}
This is caused by an outdated copy of the `github.com/motemen/gore` package. To fix simply update `gore`:
Isto é causado por uma cópia desatualizada do pacote `github.com/motemen/gore`. Simplesmente atualize `gore` para corrigir: 


```text
$ go get -u github.com/motemen/gore
```

For information see [https://github.com/gobuffalo/buffalo/issues/108](https://github.com/gobuffalo/buffalo/issues/108) and [https://github.com/motemen/gore/issues/63](https://github.com/motemen/gore/issues/63).
Para mais informações consulte [https://github.com/gobuffalo/buffalo/issues/108](https://github.com/gobuffalo/buffalo/issues/108) e [https://github.com/motemen/gore/issues/63](https://github.com/motemen/gore/issues/63).
{{< /faq >}}

{{< faq "`buffalo dev` falha ao iniciar com `Unknown`" "fails-unknown">}}
When starting `$ buffalo dev`, and you encounter this error:
Quando ao iniciando com `$ buffalo dev`, e encontras este erro:


```text
There was a problem starting the dev server: Unknown, Please review the troubleshooting docs.

tradução:
Houve um problema ao iniciar o servidor de desenvolvimento: Unknown, Por favor revise a documentação de resolução de problemas.
```

This may be due to your system missing NodeJS/NPM, Ensure that Node/NPM is installed and is in your `$PATH`. If  Node/NPM are indeed in your `$PATH`, try renaming webpack.config.js.

If you are still having issues after attempting the steps above, please reach out to the community in the #buffalo channel on Gophers Slack.
{{< /faq >}}

{{< faq "`package context: unrecognized import path \"context\" (import path does not begin with hostname)`" "unrecognized-context-import">}}
When trying to install Buffalo `go get` returns this error:


```text
package context: unrecognized import path "context" (import path does not begin with hostname)
```

This is due to an outdated version of Go. Buffalo requires Go 1.7 or higher. Please check your installation of Go and ensure you running the latest version.
{{< /faq >}}

{{< faq "Error: `unexpected directory layout:` during `go get`" "unexpected-dir-layout">}}
Occasionally when running `go get` on Buffalo you will get the following error:


```text
unexpected directory layout:
import path: github.com/mattn/go-colorable
dir: /go/src/github.com/fatih/color/vendor/github.com/mattn/go-colorable
expand dir: /go/src/github.com/fatih/color/vendor/github.com/mattn/go-colorable
separator: /
```

This issue has been reported previously the Go team, [github.com/golang/go/issues/17597](https://github.com/golang/go/issues/17597).

The best way to solve this problem is to run `go get` again, and it seems to fix itself.
{{< /faq >}}

{{< faq "Error: in `application.js` from UglifyJs" "appjs-uglify">}}
If you get this error when running `buffalo build` you need to update your `webpack.config.js` to work with [https://github.com/gobuffalo/buffalo/pull/350/files](https://github.com/gobuffalo/buffalo/pull/350/files).

{{< /faq >}}

{{< faq "Error: `Killed 9` when running `buffalo` on Mac OS X with Go 1.8.0" "mac-killed9">}}
This is a known issue with Go, <a href="https://github.com/golang/go/issues/19734" target="_blank">github.com/golang/go/issues/19734</a>, not with Buffalo.


The best solution is to upgrade to Go 1.8.1, or greater, and rebuild your Go binaries.
{{< /faq >}}

{{< faq "Mac OS X: `Too many open files in system` error" "mac-too-many-files">}}
If you get this error when running `buffalo dev` that means you are "watching" too many files, either `.go` files or asset files. To correct this you can [change](http://blog.mact.me/2014/10/22/yosemite-upgrade-changes-open-file-limit) the maximum number of open files on your system.

{{< /faq >}}

{{< faq "`buffalo new` fails trying to run `goimports`" "new-goimports">}}
The full error may appear something like the following, and seems to be the result of outdated go tools. To resolve run `rm -r $GOPATH/src/golang.org/`, then run `go get` again.

```bash
$ buffalo new myapp

--> go get -u golang.org/x/tools/cmd/goimports
package golang.org/x/tools/cmd/goimports: golang.org/x/tools is a custom import path for https://go.googlesource.com/tools, but /Users/foo/go/src/golang.org/x/tools is checked out from https://code.google.com/p/go.tools

Error: exit status 1
```
{{< /faq >}}

{{< faq "`buffalo g goth` fails to generate `auth.go`" "goth-auth-fails">}}
You might see errors similar to this when you build:

```bash
buffalo: 2018/01/19 20:58:47 === Error! ===
buffalo: 2018/01/19 20:58:47 === exit status 2
path/path/models
path/path/actions
# path/path/actions
actions/app.go:17:2: gothic redeclared as imported package name
    previous declaration at actions/app.go:15:2
actions/app.go:66:36: undefined: AuthCallback
actions/app.go:67:11: undefined: SetCurrentUser
actions/app.go:68:11: undefined: Authorize
actions/app.go:69:23: undefined: Authorize
```

This could be because the `goth` plugin isn't able to find the templates for the different providers. This can happen when the `goth` plugin is available in `$PATH`, but the project isn't in your current `$GOPATH`.

To fix it, you can either `go get -u github.com/gobuffalo/buffalo-goth` in your project's `$GOPATH` or use `dep`.
{{< /faq >}}