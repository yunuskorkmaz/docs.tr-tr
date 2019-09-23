---
title: Sekme tamamlamayı etkinleştir
description: Bu makalede PowerShell, bash ve zsh için .NET Core CLI sekme tamamlamayı nasıl etkinleştireceğinizi öğretilir.
author: thraka
ms.author: adegeo
ms.date: 12/17/2018
ms.openlocfilehash: 0f29ba2ef1d419339a0e2dc44f67c93b326eb40d
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182461"
---
# <a name="how-to-enable-tab-completion-for-net-core-cli"></a><span data-ttu-id="4d2ae-103">.NET Core CLI için sekme tamamlamayı etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="4d2ae-103">How to enable TAB completion for .NET Core CLI</span></span>

<span data-ttu-id="4d2ae-104">.NET Core 2,0 SDK ile başlayarak, .NET Core CLI sekme tamamlamayı destekler.</span><span class="sxs-lookup"><span data-stu-id="4d2ae-104">Starting with .NET Core 2.0 SDK, the .NET Core CLI supports tab completion.</span></span> <span data-ttu-id="4d2ae-105">Bu makalede, üç kabuk, PowerShell, bash ve zsh için sekme tamamlamayı yapılandırma açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4d2ae-105">This article describes how to configure tab completion for three shells, PowerShell, Bash, and zsh.</span></span> <span data-ttu-id="4d2ae-106">Diğer kabukların otomatik tamamlama desteği olabilir.</span><span class="sxs-lookup"><span data-stu-id="4d2ae-106">Other shells may have support for auto completion.</span></span> <span data-ttu-id="4d2ae-107">Otomatik tamamlamayı yapılandırma hakkında daha fazla bilgi için, bu makalede açıklanan adımlara benzer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4d2ae-107">Refer to their documentation on how to configure auto completion, the steps should be similar to the steps described in this article.</span></span>

[!INCLUDE [topic-appliesto-net-core-2plus](~/includes/topic-appliesto-net-core-2plus.md)]

<span data-ttu-id="4d2ae-108">Kurulumdan sonra, .NET Core CLI için sekme tamamlama, kabuğa bir `dotnet` komut yazılarak ve ardından SEKME tuşuna basarak tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="4d2ae-108">Once setup, tab completion for the .NET Core CLI is triggered by typing a `dotnet` command in the shell, and then pressing the TAB key.</span></span> <span data-ttu-id="4d2ae-109">Geçerli komut satırı `dotnet complete` komuta gönderilir ve sonuçlar kabuğunuz tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="4d2ae-109">The current command line is sent to the `dotnet complete` command, and the results are processed by your shell.</span></span> <span data-ttu-id="4d2ae-110">Doğrudan `dotnet complete` komuta bir şey göndererek, sekme tamamlamayı etkinleştirmeden sonuçları test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4d2ae-110">You can test the results without enabling tab completion by sending something directly to the `dotnet complete` command.</span></span> <span data-ttu-id="4d2ae-111">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="4d2ae-111">For example:</span></span>

```console
> dotnet complete "dotnet a"
add
clean
--diagnostics
migrate
pack
```

<span data-ttu-id="4d2ae-112">Bu komut işe yaramazsa, .NET Core 2,0 SDK veya üzeri 'ın yüklü olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="4d2ae-112">If that command doesn't work, make sure that .NET Core 2.0 SDK or above is installed.</span></span> <span data-ttu-id="4d2ae-113">Yüklüyse, ancak bu komut hala işe yaramazsa, `dotnet` komutun .NET Core 2,0 SDK ve üzeri bir sürüme çözümlendiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="4d2ae-113">If it's installed, but that command still doesn't work, make sure that the `dotnet` command resolves to a version of .NET Core 2.0 SDK and above.</span></span> <span data-ttu-id="4d2ae-114">Geçerli yolun hangi `dotnet` sürümünün çözümlenme olduğunu görmek için komutunukullanın.`dotnet --version`</span><span class="sxs-lookup"><span data-stu-id="4d2ae-114">Use the `dotnet --version` command to see what version of `dotnet` your current path is resolving to.</span></span> <span data-ttu-id="4d2ae-115">Daha fazla bilgi için bkz. [kullanılacak .NET Core sürümünü seçme](../versions/selection.md).</span><span class="sxs-lookup"><span data-stu-id="4d2ae-115">For more information, see [Select the .NET Core version to use](../versions/selection.md).</span></span>

### <a name="examples"></a><span data-ttu-id="4d2ae-116">Örnekler</span><span class="sxs-lookup"><span data-stu-id="4d2ae-116">Examples</span></span>

<span data-ttu-id="4d2ae-117">Aşağıda, hangi sekme tamamlanmasının sağladığı hakkında bazı örnekler verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="4d2ae-117">Here are some examples of what tab completion provides:</span></span>

<span data-ttu-id="4d2ae-118">Giriş</span><span class="sxs-lookup"><span data-stu-id="4d2ae-118">Input</span></span>                                | <span data-ttu-id="4d2ae-119">geldiğinde</span><span class="sxs-lookup"><span data-stu-id="4d2ae-119">becomes</span></span>                                                                     | <span data-ttu-id="4d2ae-120">etkinleştirilemiyor</span><span class="sxs-lookup"><span data-stu-id="4d2ae-120">because</span></span>
:------------------------------------|:----------------------------------------------------------------------------|:--------------------------------
`dotnet a⇥`                          | `dotnet add`                                                                 | <span data-ttu-id="4d2ae-121">`add`alfabetik olarak ilk alt komutu.</span><span class="sxs-lookup"><span data-stu-id="4d2ae-121">`add` is the first subcommand, alphabetically.</span></span>
`dotnet add p⇥`                      | `dotnet add --help`                                                          | <span data-ttu-id="4d2ae-122">Sekme tamamlama, alt dizeleri `--help` eşleştirir ve öncelikle alfabetik olarak gelir.</span><span class="sxs-lookup"><span data-stu-id="4d2ae-122">Tab completion matches substrings and `--help` comes first alphabetically.</span></span>
`dotnet add p⇥⇥`                    | `dotnet add package`                                                          | <span data-ttu-id="4d2ae-123">İkinci kez Tab tuşlarına basmak sonraki öneriyi getirir.</span><span class="sxs-lookup"><span data-stu-id="4d2ae-123">Pressing tab a second time brings up the next suggestion.</span></span>      
`dotnet add package Microsoft⇥`      | `dotnet add package Microsoft.ApplicationInsights.Web`                      | <span data-ttu-id="4d2ae-124">Sonuçlar alfabetik olarak döndürülür.</span><span class="sxs-lookup"><span data-stu-id="4d2ae-124">Results are returned alphabetically.</span></span>
`dotnet remove reference ⇥`          | `dotnet remove reference ..\..\src\OmniSharp.DotNet\OmniSharp.DotNet.csproj` | <span data-ttu-id="4d2ae-125">Sekme tamamlama proje dosyası farkınındır.</span><span class="sxs-lookup"><span data-stu-id="4d2ae-125">Tab completion is project file aware.</span></span>

## <a name="powershell"></a><span data-ttu-id="4d2ae-126">PowerShell</span><span class="sxs-lookup"><span data-stu-id="4d2ae-126">PowerShell</span></span>

<span data-ttu-id="4d2ae-127">.NET Core CLI için **PowerShell** 'e sekme tamamlamayı eklemek için, değişkende `$PROFILE`depolanan profili oluşturun veya düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="4d2ae-127">To add tab completion to **PowerShell** for the .NET Core CLI, create or edit the profile stored in the variable `$PROFILE`.</span></span> <span data-ttu-id="4d2ae-128">Daha fazla bilgi için bkz. profil ve [profiller ve yürütme ilkeniz](/powershell/module/microsoft.powershell.core/about/about_profiles#profiles-and-execution-policy) [oluşturma](/powershell/module/microsoft.powershell.core/about/about_profiles#how-to-create-a-profile) .</span><span class="sxs-lookup"><span data-stu-id="4d2ae-128">For more information, see [How to create your profile](/powershell/module/microsoft.powershell.core/about/about_profiles#how-to-create-a-profile) and [Profiles and execution policy](/powershell/module/microsoft.powershell.core/about/about_profiles#profiles-and-execution-policy).</span></span> 

<span data-ttu-id="4d2ae-129">Aşağıdaki kodu profilinize ekleyin:</span><span class="sxs-lookup"><span data-stu-id="4d2ae-129">Add the following code to your profile:</span></span>

```powershell
# PowerShell parameter completion shim for the dotnet CLI 
Register-ArgumentCompleter -Native -CommandName dotnet -ScriptBlock {
     param($commandName, $wordToComplete, $cursorPosition)
         dotnet complete --position $cursorPosition "$wordToComplete" | ForEach-Object {
            [System.Management.Automation.CompletionResult]::new($_, $_, 'ParameterValue', $_)
         }
 }
```

## <a name="bash"></a><span data-ttu-id="4d2ae-130">Bash</span><span class="sxs-lookup"><span data-stu-id="4d2ae-130">Bash</span></span>

<span data-ttu-id="4d2ae-131">.NET Core CLI için **Bash** kabuğunuzun sekme tamamlamayı eklemek için, `.bashrc` dosyanıza aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="4d2ae-131">To add tab completion to your **bash** shell for the .NET Core CLI, add the following code to your `.bashrc` file:</span></span>

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

## <a name="zsh"></a><span data-ttu-id="4d2ae-132">ZSH</span><span class="sxs-lookup"><span data-stu-id="4d2ae-132">Zsh</span></span>

<span data-ttu-id="4d2ae-133">.NET Core CLI için **ZSH** kabuğunuzun sekme tamamlamayı eklemek için, `.zshrc` dosyanıza aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="4d2ae-133">To add tab completion to your **zsh** shell for the .NET Core CLI, add the following code to your `.zshrc` file:</span></span>

```zsh
# zsh parameter completion for the dotnet CLI

_dotnet_zsh_complete() 
{
  local completions=("$(dotnet complete "$words")")

  reply=( "${(ps:\n:)completions}" )
}

compctl -K _dotnet_zsh_complete dotnet
```
