---
title: Sekme tamamlamayı etkinleştirme
description: Bu makalede PowerShell, bash ve zsh için .NET Core CLI sekme tamamlamayı nasıl etkinleştireceğinizi öğretilir.
author: adegeo
ms.author: adegeo
ms.date: 11/03/2019
ms.openlocfilehash: 491e1ca34c20c3994a571fc2deff7392c6bdb3f2
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324384"
---
# <a name="how-to-enable-tab-completion-for-the-net-core-cli"></a>.NET Core CLI için sekme tamamlamayı etkinleştirme

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri

Bu makalede, üç kabuk, PowerShell, bash ve zsh için sekme tamamlamayı yapılandırma açıklanmaktadır. Diğer kabuklar için sekme tamamlamayı yapılandırma hakkında daha fazla bilgi için belgelerine bakın.

Ayarladıktan sonra, .NET Core CLI için sekme tamamlama, `dotnet` kabuğa bir komut yazılarak ve ardından SEKME tuşuna basarak tetiklenir. Geçerli komut satırı `dotnet complete` komuta gönderilir ve sonuçlar kabuğunuz tarafından işlenir. Doğrudan komuta bir şey göndererek, sekme tamamlamayı etkinleştirmeden sonuçları test edebilirsiniz `dotnet complete` . Örneğin:

```console
> dotnet complete "dotnet a"
add
clean
--diagnostics
migrate
pack
```

Bu komut işe yaramazsa, .NET Core 2,0 SDK veya üzeri 'ın yüklü olduğundan emin olun. Yüklüyse, ancak bu komut hala işe yaramazsa, `dotnet` komutun .NET Core 2,0 SDK ve üzeri bir sürüme çözümlendiğinden emin olun. `dotnet --version`Geçerli yolun hangi sürümünün çözümlenme olduğunu görmek için komutunu kullanın `dotnet` . Daha fazla bilgi için bkz. [kullanılacak .NET Core sürümünü seçme](../versions/selection.md).

### <a name="examples"></a>Örnekler

Aşağıda, hangi sekme tamamlanmasının sağladığı hakkında bazı örnekler verilmiştir:

Giriş                                | geldiğinde                                                                     | HTTPS
:------------------------------------|:----------------------------------------------------------------------------|:--------------------------------
`dotnet a⇥`                          | `dotnet add`                                                                 | `add`alfabetik olarak ilk alt komutu.
`dotnet add p⇥`                      | `dotnet add --help`                                                          | Sekme tamamlama, alt dizeleri eşleştirir ve `--help` öncelikle alfabetik olarak gelir.
`dotnet add p⇥⇥`                    | `dotnet add package`                                                          | İkinci kez Tab tuşlarına basmak sonraki öneriyi getirir.
`dotnet add package Microsoft⇥`      | `dotnet add package Microsoft.ApplicationInsights.Web`                      | Sonuçlar alfabetik olarak döndürülür.
`dotnet remove reference ⇥`          | `dotnet remove reference ..\..\src\OmniSharp.DotNet\OmniSharp.DotNet.csproj` | Sekme tamamlama proje dosyası farkınındır.

## <a name="powershell"></a>PowerShell

.NET Core CLI için **PowerShell** 'e sekme tamamlamayı eklemek için, değişkende depolanan profili oluşturun veya düzenleyin `$PROFILE` . Daha fazla bilgi için bkz. profil ve [profiller ve yürütme ilkeniz](/powershell/module/microsoft.powershell.core/about/about_profiles#profiles-and-execution-policy) [oluşturma](/powershell/module/microsoft.powershell.core/about/about_profiles#how-to-create-a-profile) .

Aşağıdaki kodu profilinize ekleyin:

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

.NET Core CLI için **Bash** kabuğunuzun sekme tamamlamayı eklemek için, dosyanıza aşağıdaki kodu ekleyin `.bashrc` :

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

## <a name="zsh"></a>ZSH

.NET Core CLI için **ZSH** kabuğunuzun sekme tamamlamayı eklemek için, dosyanıza aşağıdaki kodu ekleyin `.zshrc` :

```zsh
# zsh parameter completion for the dotnet CLI

_dotnet_zsh_complete()
{
  local completions=("$(dotnet complete "$words")")

  reply=( "${(ps:\n:)completions}" )
}

compctl -K _dotnet_zsh_complete dotnet
```
