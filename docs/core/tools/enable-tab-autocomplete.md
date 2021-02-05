---
title: Sekme tamamlamayı etkinleştirme
description: Bu makalede PowerShell, Bash, ZSH ve balık için .NET CLı için sekme tamamlamayı nasıl etkinleştireceğinizi öğretilir.
author: adegeo
ms.author: adegeo
ms.topic: how-to
ms.date: 11/03/2019
ms.openlocfilehash: b5b63166faa1762d9fa82a93aa70aebb33167630
ms.sourcegitcommit: 65af0f0ad316858882845391d60ef7e303b756e8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/05/2021
ms.locfileid: "99585565"
---
# <a name="how-to-enable-tab-completion-for-the-net-cli"></a>.NET CLı için sekme tamamlamayı etkinleştirme

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri

Bu makalede dört kabuklar, PowerShell, Bash, ZSH ve balık için sekme tamamlamayı yapılandırma açıklanmaktadır. Diğer kabuklar için sekme tamamlamayı yapılandırma hakkında daha fazla bilgi için belgelerine bakın.

Ayarladıktan sonra, .NET CLı için sekme tamamlama, `dotnet` kabuğa bir komut yazılarak ve ardından SEKME tuşuna basarak tetiklenir. Geçerli komut satırı `dotnet complete` komuta gönderilir ve sonuçlar kabuğunuz tarafından işlenir. Doğrudan komuta bir şey göndererek, sekme tamamlamayı etkinleştirmeden sonuçları test edebilirsiniz `dotnet complete` . Örneğin:

```console
> dotnet complete "dotnet a"
add
clean
--diagnostics
migrate
pack
```

Bu komut işe yaramazsa, .NET Core 2,0 SDK veya üzeri 'ın yüklü olduğundan emin olun. Yüklüyse, ancak bu komut hala işe yaramazsa, `dotnet` komutun .NET Core 2,0 SDK ve üzeri bir sürüme çözümlendiğinden emin olun. `dotnet --version`Geçerli yolun hangi sürümünün çözümlenme olduğunu görmek için komutunu kullanın `dotnet` . Daha fazla bilgi için bkz. [kullanılacak .NET sürümünü seçme](../versions/selection.md).

### <a name="examples"></a>Örnekler

Aşağıda, hangi sekme tamamlanmasının sağladığı hakkında bazı örnekler verilmiştir:

Giriş                                | geldiğinde                                                                     | HTTPS
:------------------------------------|:----------------------------------------------------------------------------|:--------------------------------
`dotnet a⇥`                          | `dotnet add`                                                                 | `add` alfabetik olarak ilk alt komutu.
`dotnet add p⇥`                      | `dotnet add --help`                                                          | Sekme tamamlama, alt dizeleri eşleştirir ve `--help` öncelikle alfabetik olarak gelir.
`dotnet add p⇥⇥`                    | `dotnet add package`                                                          | İkinci kez Tab tuşlarına basmak sonraki öneriyi getirir.
`dotnet add package Microsoft⇥`      | `dotnet add package Microsoft.ApplicationInsights.Web`                      | Sonuçlar alfabetik olarak döndürülür.
`dotnet remove reference ⇥`          | `dotnet remove reference ..\..\src\OmniSharp.DotNet\OmniSharp.DotNet.csproj` | Sekme tamamlama proje dosyası farkınındır.

## <a name="powershell"></a>PowerShell

.NET CLı için **PowerShell** 'e sekme tamamlamayı eklemek için, değişkende depolanan profili oluşturun veya düzenleyin `$PROFILE` . Daha fazla bilgi için bkz. profil ve [profiller ve yürütme ilkeniz](/powershell/module/microsoft.powershell.core/about/about_profiles#profiles-and-execution-policy) [oluşturma](/powershell/module/microsoft.powershell.core/about/about_profiles#how-to-create-a-profile) .

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

.NET CLı için **Bash** kabuğunuzun sekme tamamlamayı eklemek için, dosyanıza aşağıdaki kodu ekleyin `.bashrc` :

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

.NET CLı için **ZSH** kabuğunuzun sekme tamamlamayı eklemek için, dosyanıza aşağıdaki kodu ekleyin `.zshrc` :

```zsh
# zsh parameter completion for the dotnet CLI

_dotnet_zsh_complete()
{
  local completions=("$(dotnet complete "$words")")

  reply=( "${(ps:\n:)completions}" )
}

compctl -K _dotnet_zsh_complete dotnet
```

## <a name="fish"></a>ta

.NET CLı için **balık** kabuğunuzun sekme tamamlamayı eklemek için, dosyanıza aşağıdaki kodu ekleyin `config.fish` :

```fish
complete -f -c dotnet -a "(dotnet complete)"
```
