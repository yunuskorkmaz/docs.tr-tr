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
# <a name="how-to-enable-tab-completion-for-the-net-core-cli"></a><span data-ttu-id="f97f8-103">.NET Core CLI için TAB tamamlama nasıl etkinleştirilir?</span><span class="sxs-lookup"><span data-stu-id="f97f8-103">How to enable TAB completion for the .NET Core CLI</span></span>

<span data-ttu-id="f97f8-104">**Bu makale şu şekilde dir:** ✔️ .NET Core 2.1 SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="f97f8-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="f97f8-105">Bu makalede, üç kabuk, PowerShell, Bash ve zsh için sekme tamamlama yapılandırmak için nasıl açıklanır.</span><span class="sxs-lookup"><span data-stu-id="f97f8-105">This article describes how to configure tab completion for three shells, PowerShell, Bash, and zsh.</span></span> <span data-ttu-id="f97f8-106">Diğer kabuklar için sekme tamamlamanın nasıl yapılandırılabildiğini belgelemelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="f97f8-106">For other shells, refer to their documentation on how to configure tab completion.</span></span>

<span data-ttu-id="f97f8-107">Ayarlandıktan sonra,.NET Core CLI için sekme tamamlama, kabuğuna bir `dotnet` komut yazıp TAB tuşuna basarak tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="f97f8-107">Once set up, tab completion for the .NET Core CLI is triggered by typing a `dotnet` command in the shell, and then pressing the TAB key.</span></span> <span data-ttu-id="f97f8-108">Geçerli komut satırı komutana `dotnet complete` gönderilir ve sonuçlar kabuğunuz tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="f97f8-108">The current command line is sent to the `dotnet complete` command, and the results are processed by your shell.</span></span> <span data-ttu-id="f97f8-109">Doğrudan `dotnet complete` komuta bir şey göndererek sekme tamamlamayı etkinleştirmeden sonuçları test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f97f8-109">You can test the results without enabling tab completion by sending something directly to the `dotnet complete` command.</span></span> <span data-ttu-id="f97f8-110">Örnek:</span><span class="sxs-lookup"><span data-stu-id="f97f8-110">For example:</span></span>

```console
> dotnet complete "dotnet a"
add
clean
--diagnostics
migrate
pack
```

<span data-ttu-id="f97f8-111">Bu komut çalışmıyorsa, .NET Core 2.0 SDK veya üzeri nin yüklü olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="f97f8-111">If that command doesn't work, make sure that .NET Core 2.0 SDK or above is installed.</span></span> <span data-ttu-id="f97f8-112">Yüklüyse, ancak bu komut hala çalışmıyorsa, komutun `dotnet` .NET Core 2.0 SDK ve üzeri bir sürüme göre çözüldüğünden emin olun.</span><span class="sxs-lookup"><span data-stu-id="f97f8-112">If it's installed, but that command still doesn't work, make sure that the `dotnet` command resolves to a version of .NET Core 2.0 SDK and above.</span></span> <span data-ttu-id="f97f8-113">Geçerli `dotnet --version` `dotnet` yolunuzun hangi sürümüne çözüm bulmak için komutu kullanın.</span><span class="sxs-lookup"><span data-stu-id="f97f8-113">Use the `dotnet --version` command to see what version of `dotnet` your current path is resolving to.</span></span> <span data-ttu-id="f97f8-114">Daha fazla bilgi için [bkz.](../versions/selection.md)</span><span class="sxs-lookup"><span data-stu-id="f97f8-114">For more information, see [Select the .NET Core version to use](../versions/selection.md).</span></span>

### <a name="examples"></a><span data-ttu-id="f97f8-115">Örnekler</span><span class="sxs-lookup"><span data-stu-id="f97f8-115">Examples</span></span>

<span data-ttu-id="f97f8-116">Sekme tamamlamanın sağladığı bazı örnekler aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="f97f8-116">Here are some examples of what tab completion provides:</span></span>

<span data-ttu-id="f97f8-117">Girdi</span><span class="sxs-lookup"><span data-stu-id="f97f8-117">Input</span></span>                                | <span data-ttu-id="f97f8-118">Olur</span><span class="sxs-lookup"><span data-stu-id="f97f8-118">becomes</span></span>                                                                     | <span data-ttu-id="f97f8-119">HTTPS</span><span class="sxs-lookup"><span data-stu-id="f97f8-119">because</span></span>
:------------------------------------|:----------------------------------------------------------------------------|:--------------------------------
`dotnet a⇥`                          | `dotnet add`                                                                 | <span data-ttu-id="f97f8-120">`add`alfabetik olarak ilk alt komutudur.</span><span class="sxs-lookup"><span data-stu-id="f97f8-120">`add` is the first subcommand, alphabetically.</span></span>
`dotnet add p⇥`                      | `dotnet add --help`                                                          | <span data-ttu-id="f97f8-121">Sekme tamamlama substrings eşleşir ve `--help` ilk alfabetik olarak gelir.</span><span class="sxs-lookup"><span data-stu-id="f97f8-121">Tab completion matches substrings and `--help` comes first alphabetically.</span></span>
`dotnet add p⇥⇥`                    | `dotnet add package`                                                          | <span data-ttu-id="f97f8-122">Sekme ikinci kez basıldığında bir sonraki öneri gündeme getirir.</span><span class="sxs-lookup"><span data-stu-id="f97f8-122">Pressing tab a second time brings up the next suggestion.</span></span>
`dotnet add package Microsoft⇥`      | `dotnet add package Microsoft.ApplicationInsights.Web`                      | <span data-ttu-id="f97f8-123">Sonuçlar alfabetik olarak döndürülür.</span><span class="sxs-lookup"><span data-stu-id="f97f8-123">Results are returned alphabetically.</span></span>
`dotnet remove reference ⇥`          | `dotnet remove reference ..\..\src\OmniSharp.DotNet\OmniSharp.DotNet.csproj` | <span data-ttu-id="f97f8-124">Sekme tamamlama proje dosyası nın farkındadır.</span><span class="sxs-lookup"><span data-stu-id="f97f8-124">Tab completion is project file aware.</span></span>

## <a name="powershell"></a><span data-ttu-id="f97f8-125">PowerShell</span><span class="sxs-lookup"><span data-stu-id="f97f8-125">PowerShell</span></span>

<span data-ttu-id="f97f8-126">.NET Core CLI için **PowerShell'e** sekme tamamlama eklemek için, değişkende `$PROFILE`depolanan profili oluşturun veya değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f97f8-126">To add tab completion to **PowerShell** for the .NET Core CLI, create or edit the profile stored in the variable `$PROFILE`.</span></span> <span data-ttu-id="f97f8-127">Daha fazla bilgi için [profilinizi, Profillerinizi](/powershell/module/microsoft.powershell.core/about/about_profiles#how-to-create-a-profile) ve yürütme politikanızı nasıl oluşturabilirsiniz [abakın.](/powershell/module/microsoft.powershell.core/about/about_profiles#profiles-and-execution-policy)</span><span class="sxs-lookup"><span data-stu-id="f97f8-127">For more information, see [How to create your profile](/powershell/module/microsoft.powershell.core/about/about_profiles#how-to-create-a-profile) and [Profiles and execution policy](/powershell/module/microsoft.powershell.core/about/about_profiles#profiles-and-execution-policy).</span></span>

<span data-ttu-id="f97f8-128">Profilinize aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f97f8-128">Add the following code to your profile:</span></span>

```powershell
# PowerShell parameter completion shim for the dotnet CLI
Register-ArgumentCompleter -Native -CommandName dotnet -ScriptBlock {
     param($commandName, $wordToComplete, $cursorPosition)
         dotnet complete --position $cursorPosition "$wordToComplete" | ForEach-Object {
            [System.Management.Automation.CompletionResult]::new($_, $_, 'ParameterValue', $_)
         }
 }
```

## <a name="bash"></a><span data-ttu-id="f97f8-129">bash</span><span class="sxs-lookup"><span data-stu-id="f97f8-129">bash</span></span>

<span data-ttu-id="f97f8-130">.NET Core CLI için **bash** kabuğunuza sekme tamamlama eklemek `.bashrc` için dosyanıza aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f97f8-130">To add tab completion to your **bash** shell for the .NET Core CLI, add the following code to your `.bashrc` file:</span></span>

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

## <a name="zsh"></a><span data-ttu-id="f97f8-131">zş</span><span class="sxs-lookup"><span data-stu-id="f97f8-131">zsh</span></span>

<span data-ttu-id="f97f8-132">.NET Core CLI için **zsh** kabuğunuza sekme tamamlama eklemek `.zshrc` için dosyanıza aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f97f8-132">To add tab completion to your **zsh** shell for the .NET Core CLI, add the following code to your `.zshrc` file:</span></span>

```zsh
# zsh parameter completion for the dotnet CLI

_dotnet_zsh_complete()
{
  local completions=("$(dotnet complete "$words")")

  reply=( "${(ps:\n:)completions}" )
}

compctl -K _dotnet_zsh_complete dotnet
```
