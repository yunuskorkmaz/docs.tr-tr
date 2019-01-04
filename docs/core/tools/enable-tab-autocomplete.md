---
title: Sekme tamamlamayı etkinleştirme
description: Bu makalede, PowerShell, Bash ve zsh için .NET Core CLI için sekme tamamlamayı etkinleştirme öğretir.
author: thraka
ms.author: adegeo
ms.date: 12/17/2018
ms.openlocfilehash: 783868fb8300dd4a25c62a108c1c0f7a485721df
ms.sourcegitcommit: 3b9b7ae6771712337d40374d2fef6b25b0d53df6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54029612"
---
# <a name="how-to-enable-tab-completion-for-net-core-cli"></a>.NET Core CLI için sekme tamamlamayı etkinleştirme

.NET Core 2.0 SDK'sı ile başlayarak, .NET Core CLI sekme tamamlamayı destekler. Bu makalede, üç Kabukları, PowerShell, Bash ve zsh için sekmesinde tamamlama yapılandırma açıklanır. Diğer Kabuk otomatik tamamlama desteği olabilir. Otomatik Tamamlama yapılandırma kendi belgelerine başvurun, adımlar bu makalede açıklanan adımları aşağıdakine benzer olmalıdır.

[!INCLUDE [topic-appliesto-net-core-2plus](~/includes/topic-appliesto-net-core-2plus.md)]

Bir kez Kurulum, sekme tamamlama için .NET Core CLI yazarak tetiklenir bir `dotnet ` komut kabuğu'nda ve ardından SEKME tuşuna basmak. Geçerli komut satırı gönderilen `dotnet complete` komut ve sonuçları, kabuk tarafından işlenir. Sonuçları sekme tamamlama etkinleştirmeden bir şey doğrudan göndererek test edebilirsiniz `dotnet complete` komutu. Örneğin:

```
> dotnet complete "dotnet a"
add
clean
--diagnostics
migrate
pack
```

Bu komut işe yaramazsa, bu .NET Core 2.0 SDK'sını emin olun veya yukarıda yüklenir. Yüklü olduğu, ancak bu komut işe yaramazsa, emin `dotnet` komutu, .NET Core 2.0 SDK'sını ve üzeri bir sürüm olarak çözer. Kullanım `dotnet --version` hangi sürümünü görmek için komutu `dotnet` için geçerli yolunuzu çözüyor. Daha fazla bilgi için [kullanmak için .NET Core sürümü](../versions/selection.md).

### <a name="examples"></a>Örnekler

Hangi sekme tamamlamayı sağlayan bazı örnekler şunlardır:

Giriş                                | olur                                                                     | nedeni
:------------------------------------|:----------------------------------------------------------------------------|:--------------------------------
`dotnet a⇥`                          | `dotnet add`                                                                 | `add` ilk alt alfabetik olur.
`dotnet add p⇥`                      | `dotnet add --help`                                                          | Sekme tamamlama eşleşen alt dizeler ve `--help` alfabetik olarak ilk gelir.
`dotnet add p⇥⇥`                    | `dotnet add package`                                                          | İkinci kez Tab tuşuna basarak sonraki öneri sunar.      
`dotnet add package Microsoft⇥`      | `dotnet add package Microsoft.ApplicationInsights.Web`                      | Sonuçlar alfabetik olarak döndürülür.
`dotnet remove reference ⇥`          | `dotnet remove reference ..\..\src\OmniSharp.DotNet\OmniSharp.DotNet.csproj` | Sekme tamamlama, proje dosyası kullanan içindir.

## <a name="powershell"></a>PowerShell

Sekme tamamlama eklemek için **PowerShell** .NET Core CLI için oluşturma veya değişkeninde depolanan profil düzenleme `$PROFILE`. Daha fazla bilgi için [profilinizi oluşturma](/powershell/module/microsoft.powershell.core/about/about_profiles?view=powershell-6#how-to-create-a-profile) ve [profilleri ve yürütme İlkesi](/powershell/module/microsoft.powershell.core/about/about_profiles?view=powershell-6#profiles-and-execution-policy). 

Profiliniz için aşağıdaki kodu ekleyin:

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

Sekme tamamlama eklemek için **bash** Kabuk için .NET Core CLI, aşağıdaki kodu ekleyin, `.bashrc` dosyası:

```bash
# bash parameter completion for the dotnet CLI

_dotnet_bash_complete()
{
  local word=${COMP_WORDS[COMP_CWORD]}

  local completions
  completions="$(dotnet complete --position "${COMP_POINT}" "${COMP_LINE}")"

  COMPREPLY=( $(compgen -W "$completions" -- "$word") )
}

complete -f -F _dotnet_bash_complete dotnet
```

## <a name="zsh"></a>zsh

Sekme tamamlama eklemek için **zsh** Kabuk için .NET Core CLI, aşağıdaki kodu ekleyin, `.zshrc` dosyası:

```zsh
# zsh parameter completion for the dotnet CLI

_dotnet_zsh_complete() 
{
  local completions=("$(dotnet complete "$words")")

  reply=( "${(ps:\n:)completions}" )
}

compctl -K _dotnet_zsh_complete dotnet
```
