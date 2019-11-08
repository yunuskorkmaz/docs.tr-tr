---
title: Sekme tamamlamayı etkinleştir
description: Bu makalede PowerShell, bash ve zsh için .NET Core CLI sekme tamamlamayı nasıl etkinleştireceğinizi öğretilir.
author: thraka
ms.author: adegeo
ms.date: 11/03/2019
ms.openlocfilehash: 8c5d6a254db5ba21417ba45122ed0d7cb093c7c3
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739306"
---
# <a name="how-to-enable-tab-completion-for-net-core-cli"></a>.NET Core CLI için sekme tamamlamayı etkinleştirme

.NET Core 2,0 SDK ile başlayarak, .NET Core CLI sekme tamamlamayı destekler. Bu makalede, üç kabuk, PowerShell, bash ve zsh için sekme tamamlamayı yapılandırma açıklanmaktadır. Diğer kabukların otomatik tamamlama desteği olabilir. Otomatik tamamlamayı yapılandırma hakkında daha fazla bilgi için, bu makalede açıklanan adımlara benzer olmalıdır.

[!INCLUDE [topic-appliesto-net-core-2plus](~/includes/topic-appliesto-net-core-2plus.md)]

Kurulumdan sonra, .NET Core CLI için sekme tamamlama, kabuğa bir `dotnet` komutu yazarak ve ardından SEKME tuşuna basarak tetiklenir. Geçerli komut satırı `dotnet complete` komutuna gönderilir ve sonuçlar, kabuğunuz tarafından işlenir. Sonuçları, doğrudan `dotnet complete` komutuna bir şey göndererek sekme tamamlamayı etkinleştirmeden test edebilirsiniz. Örneğin:

```console
> dotnet complete "dotnet a"
add
clean
--diagnostics
migrate
pack
```

Bu komut işe yaramazsa, .NET Core 2,0 SDK veya üzeri 'ın yüklü olduğundan emin olun. Yüklüyse, ancak bu komut hala işe yaramazsa, `dotnet` komutunun .NET Core 2,0 SDK ve üzeri bir sürüme çözümlendiğinden emin olun. Geçerli yolunuzda hangi `dotnet` sürümünün çözümlenme olduğunu görmek için `dotnet --version` komutunu kullanın. Daha fazla bilgi için bkz. [kullanılacak .NET Core sürümünü seçme](../versions/selection.md).

### <a name="examples"></a>Örnekler

Aşağıda, hangi sekme tamamlanmasının sağladığı hakkında bazı örnekler verilmiştir:

Giriş                                | geldiğinde                                                                     | etkinleştirilemiyor
:------------------------------------|:----------------------------------------------------------------------------|:--------------------------------
`dotnet a⇥`                          | `dotnet add`                                                                 | alfabetik olarak ilk alt komut `add`.
`dotnet add p⇥`                      | `dotnet add --help`                                                          | Sekme tamamlama, alt dizeleri eşleştirirken `--help` ilk alfabetik olarak gelir.
`dotnet add p⇥⇥`                    | `dotnet add package`                                                          | İkinci kez Tab tuşlarına basmak sonraki öneriyi getirir.      
`dotnet add package Microsoft⇥`      | `dotnet add package Microsoft.ApplicationInsights.Web`                      | Sonuçlar alfabetik olarak döndürülür.
`dotnet remove reference ⇥`          | `dotnet remove reference ..\..\src\OmniSharp.DotNet\OmniSharp.DotNet.csproj` | Sekme tamamlama proje dosyası farkınındır.

## <a name="powershell"></a>PowerShell

.NET Core CLI için **PowerShell** 'e sekme tamamlamayı eklemek için `$PROFILE`değişkende depolanan profili oluşturun veya düzenleyin. Daha fazla bilgi için bkz. profil ve [profiller ve yürütme ilkeniz](/powershell/module/microsoft.powershell.core/about/about_profiles#profiles-and-execution-policy) [oluşturma](/powershell/module/microsoft.powershell.core/about/about_profiles#how-to-create-a-profile) . 

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

## <a name="bash"></a>Bash

.NET Core CLI için **Bash** kabuğunuzun sekme tamamlamayı eklemek için, `.bashrc` dosyanıza aşağıdaki kodu ekleyin:

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

.NET Core CLI için **ZSH** kabuğunuzun sekme tamamlamayı eklemek için, `.zshrc` dosyanıza aşağıdaki kodu ekleyin:

```zsh
# zsh parameter completion for the dotnet CLI

_dotnet_zsh_complete() 
{
  local completions=("$(dotnet complete "$words")")

  reply=( "${(ps:\n:)completions}" )
}

compctl -K _dotnet_zsh_complete dotnet
```
