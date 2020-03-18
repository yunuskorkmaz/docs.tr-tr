---
title: Sekme tamamlamayı etkinleştirme
description: Bu makalede, PowerShell, Bash ve zsh için .NET Core CLI için sekme tamamlamayı nasıl etkinleştirdiğinizi öğreter.
author: thraka
ms.author: adegeo
ms.date: 11/03/2019
ms.openlocfilehash: 31328be14811760bc8d7fb527e0d55abfe6b1493
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156757"
---
# <a name="how-to-enable-tab-completion-for-the-net-core-cli"></a>.NET Core CLI için TAB tamamlama nasıl etkinleştirilir?

**Bu makale şu şekilde dir:** ✔️ .NET Core 2.1 SDK ve sonraki sürümler

Bu makalede, üç kabuk, PowerShell, Bash ve zsh için sekme tamamlama yapılandırmak için nasıl açıklanır. Diğer kabuklar için sekme tamamlamanın nasıl yapılandırılabildiğini belgelemelerine bakın.

Ayarlandıktan sonra,.NET Core CLI için sekme tamamlama, kabuğuna bir `dotnet` komut yazıp TAB tuşuna basarak tetiklenir. Geçerli komut satırı komutana `dotnet complete` gönderilir ve sonuçlar kabuğunuz tarafından işlenir. Doğrudan `dotnet complete` komuta bir şey göndererek sekme tamamlamayı etkinleştirmeden sonuçları test edebilirsiniz. Örnek:

```console
> dotnet complete "dotnet a"
add
clean
--diagnostics
migrate
pack
```

Bu komut çalışmıyorsa, .NET Core 2.0 SDK veya üzeri nin yüklü olduğundan emin olun. Yüklüyse, ancak bu komut hala çalışmıyorsa, komutun `dotnet` .NET Core 2.0 SDK ve üzeri bir sürüme göre çözüldüğünden emin olun. Geçerli `dotnet --version` `dotnet` yolunuzun hangi sürümüne çözüm bulmak için komutu kullanın. Daha fazla bilgi için [bkz.](../versions/selection.md)

### <a name="examples"></a>Örnekler

Sekme tamamlamanın sağladığı bazı örnekler aşağıda verilmiştir:

Girdi                                | Olur                                                                     | HTTPS
:------------------------------------|:----------------------------------------------------------------------------|:--------------------------------
`dotnet a⇥`                          | `dotnet add`                                                                 | `add`alfabetik olarak ilk alt komutudur.
`dotnet add p⇥`                      | `dotnet add --help`                                                          | Sekme tamamlama substrings eşleşir ve `--help` ilk alfabetik olarak gelir.
`dotnet add p⇥⇥`                    | `dotnet add package`                                                          | Sekme ikinci kez basıldığında bir sonraki öneri gündeme getirir.
`dotnet add package Microsoft⇥`      | `dotnet add package Microsoft.ApplicationInsights.Web`                      | Sonuçlar alfabetik olarak döndürülür.
`dotnet remove reference ⇥`          | `dotnet remove reference ..\..\src\OmniSharp.DotNet\OmniSharp.DotNet.csproj` | Sekme tamamlama proje dosyası nın farkındadır.

## <a name="powershell"></a>PowerShell

.NET Core CLI için **PowerShell'e** sekme tamamlama eklemek için, değişkende `$PROFILE`depolanan profili oluşturun veya değiştirin. Daha fazla bilgi için [profilinizi, Profillerinizi](/powershell/module/microsoft.powershell.core/about/about_profiles#how-to-create-a-profile) ve yürütme politikanızı nasıl oluşturabilirsiniz [abakın.](/powershell/module/microsoft.powershell.core/about/about_profiles#profiles-and-execution-policy)

Profilinize aşağıdaki kodu ekleyin:

```powershell
# PowerShell parameter completion shim for the dotnet CLI
Register-ArgumentCompleter -Native -CommandName dotnet -ScriptBlock {
     param($commandName, $wordToComplete, $cursorPosition)
         dotnet complete --position $cursorPosition "$wordToComplete" | ForEach-Object {
            [System.Management.Automation.CompletionResult]::new($_, $_, 'ParameterValue', $_)
         }
 }
```

## <a name="bash"></a>bash

.NET Core CLI için **bash** kabuğunuza sekme tamamlama eklemek `.bashrc` için dosyanıza aşağıdaki kodu ekleyin:

```bash
# bash parameter completion for the dotnet CLI

_dotnet_bash_complete()
{
  local word=${COMP_WORDS[COMP_CWORD]}

  local completions
  completions="$(dotnet complete --position "${COMP_POINT}" "${COMP_LINE}" 2>/dev/null)"
  if [ $? -ne 0 ]; then
    completions=""
  fi

  COMPREPLY=( $(compgen -W "$completions" -- "$word") )
}

complete -f -F _dotnet_bash_complete dotnet
```

## <a name="zsh"></a>zş

.NET Core CLI için **zsh** kabuğunuza sekme tamamlama eklemek `.zshrc` için dosyanıza aşağıdaki kodu ekleyin:

```zsh
# zsh parameter completion for the dotnet CLI

_dotnet_zsh_complete()
{
  local completions=("$(dotnet complete "$words")")

  reply=( "${(ps:\n:)completions}" )
}

compctl -K _dotnet_zsh_complete dotnet
```
