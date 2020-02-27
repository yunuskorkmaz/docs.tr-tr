---
title: Sekme tamamlamayı etkinleştirme
description: Bu makalede PowerShell, bash ve zsh için .NET Core CLI sekme tamamlamayı nasıl etkinleştireceğinizi öğretilir.
author: thraka
ms.author: adegeo
ms.date: 11/03/2019
ms.openlocfilehash: 6614f11a9c4eb1b1aac4dd8dac8d05d15262bd0c
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626014"
---
# <a name="how-to-enable-tab-completion-for-the-net-core-cli"></a><span data-ttu-id="380cc-103">.NET Core CLI için sekme tamamlamayı etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="380cc-103">How to enable TAB completion for the .NET Core CLI</span></span>

<span data-ttu-id="380cc-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="380cc-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="380cc-105">Bu makalede, üç kabuk, PowerShell, bash ve zsh için sekme tamamlamayı yapılandırma açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="380cc-105">This article describes how to configure tab completion for three shells, PowerShell, Bash, and zsh.</span></span> <span data-ttu-id="380cc-106">Diğer kabuklar için sekme tamamlamayı yapılandırma hakkında daha fazla bilgi için belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="380cc-106">For other shells, refer to their documentation on how to configure tab completion.</span></span>

<span data-ttu-id="380cc-107">Ayarladıktan sonra, .NET Core CLI için sekme tamamlama, kabuğa bir `dotnet` komutu yazarak ve ardından SEKME tuşuna basarak tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="380cc-107">Once set up, tab completion for the .NET Core CLI is triggered by typing a `dotnet` command in the shell, and then pressing the TAB key.</span></span> <span data-ttu-id="380cc-108">Geçerli komut satırı `dotnet complete` komutuna gönderilir ve sonuçlar, kabuğunuz tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="380cc-108">The current command line is sent to the `dotnet complete` command, and the results are processed by your shell.</span></span> <span data-ttu-id="380cc-109">Sonuçları, doğrudan `dotnet complete` komutuna bir şey göndererek sekme tamamlamayı etkinleştirmeden test edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="380cc-109">You can test the results without enabling tab completion by sending something directly to the `dotnet complete` command.</span></span> <span data-ttu-id="380cc-110">Örnek:</span><span class="sxs-lookup"><span data-stu-id="380cc-110">For example:</span></span>

```console
> dotnet complete "dotnet a"
add
clean
--diagnostics
migrate
pack
```

<span data-ttu-id="380cc-111">Bu komut işe yaramazsa, .NET Core 2,0 SDK veya üzeri 'ın yüklü olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="380cc-111">If that command doesn't work, make sure that .NET Core 2.0 SDK or above is installed.</span></span> <span data-ttu-id="380cc-112">Yüklüyse, ancak bu komut hala işe yaramazsa, `dotnet` komutunun .NET Core 2,0 SDK ve üzeri bir sürüme çözümlendiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="380cc-112">If it's installed, but that command still doesn't work, make sure that the `dotnet` command resolves to a version of .NET Core 2.0 SDK and above.</span></span> <span data-ttu-id="380cc-113">Geçerli yolunuzda hangi `dotnet` sürümünün çözümlenme olduğunu görmek için `dotnet --version` komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="380cc-113">Use the `dotnet --version` command to see what version of `dotnet` your current path is resolving to.</span></span> <span data-ttu-id="380cc-114">Daha fazla bilgi için bkz. [kullanılacak .NET Core sürümünü seçme](../versions/selection.md).</span><span class="sxs-lookup"><span data-stu-id="380cc-114">For more information, see [Select the .NET Core version to use](../versions/selection.md).</span></span>

### <a name="examples"></a><span data-ttu-id="380cc-115">Örnekler</span><span class="sxs-lookup"><span data-stu-id="380cc-115">Examples</span></span>

<span data-ttu-id="380cc-116">Aşağıda, hangi sekme tamamlanmasının sağladığı hakkında bazı örnekler verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="380cc-116">Here are some examples of what tab completion provides:</span></span>

<span data-ttu-id="380cc-117">Girdi</span><span class="sxs-lookup"><span data-stu-id="380cc-117">Input</span></span>                                | <span data-ttu-id="380cc-118">geldiğinde</span><span class="sxs-lookup"><span data-stu-id="380cc-118">becomes</span></span>                                                                     | <span data-ttu-id="380cc-119">etkinleştirilemiyor</span><span class="sxs-lookup"><span data-stu-id="380cc-119">because</span></span>
:------------------------------------|:----------------------------------------------------------------------------|:--------------------------------
`dotnet a⇥`                          | `dotnet add`                                                                 | <span data-ttu-id="380cc-120">alfabetik olarak ilk alt komut `add`.</span><span class="sxs-lookup"><span data-stu-id="380cc-120">`add` is the first subcommand, alphabetically.</span></span>
`dotnet add p⇥`                      | `dotnet add --help`                                                          | <span data-ttu-id="380cc-121">Sekme tamamlama, alt dizeleri eşleştirirken `--help` ilk alfabetik olarak gelir.</span><span class="sxs-lookup"><span data-stu-id="380cc-121">Tab completion matches substrings and `--help` comes first alphabetically.</span></span>
`dotnet add p⇥⇥`                    | `dotnet add package`                                                          | <span data-ttu-id="380cc-122">İkinci kez Tab tuşlarına basmak sonraki öneriyi getirir.</span><span class="sxs-lookup"><span data-stu-id="380cc-122">Pressing tab a second time brings up the next suggestion.</span></span>      
`dotnet add package Microsoft⇥`      | `dotnet add package Microsoft.ApplicationInsights.Web`                      | <span data-ttu-id="380cc-123">Sonuçlar alfabetik olarak döndürülür.</span><span class="sxs-lookup"><span data-stu-id="380cc-123">Results are returned alphabetically.</span></span>
`dotnet remove reference ⇥`          | `dotnet remove reference ..\..\src\OmniSharp.DotNet\OmniSharp.DotNet.csproj` | <span data-ttu-id="380cc-124">Sekme tamamlama proje dosyası farkınındır.</span><span class="sxs-lookup"><span data-stu-id="380cc-124">Tab completion is project file aware.</span></span>

## <a name="powershell"></a><span data-ttu-id="380cc-125">PowerShell</span><span class="sxs-lookup"><span data-stu-id="380cc-125">PowerShell</span></span>

<span data-ttu-id="380cc-126">.NET Core CLI için **PowerShell** 'e sekme tamamlamayı eklemek için `$PROFILE`değişkende depolanan profili oluşturun veya düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="380cc-126">To add tab completion to **PowerShell** for the .NET Core CLI, create or edit the profile stored in the variable `$PROFILE`.</span></span> <span data-ttu-id="380cc-127">Daha fazla bilgi için bkz. profil ve [profiller ve yürütme ilkeniz](/powershell/module/microsoft.powershell.core/about/about_profiles#profiles-and-execution-policy) [oluşturma](/powershell/module/microsoft.powershell.core/about/about_profiles#how-to-create-a-profile) .</span><span class="sxs-lookup"><span data-stu-id="380cc-127">For more information, see [How to create your profile](/powershell/module/microsoft.powershell.core/about/about_profiles#how-to-create-a-profile) and [Profiles and execution policy](/powershell/module/microsoft.powershell.core/about/about_profiles#profiles-and-execution-policy).</span></span> 

<span data-ttu-id="380cc-128">Aşağıdaki kodu profilinize ekleyin:</span><span class="sxs-lookup"><span data-stu-id="380cc-128">Add the following code to your profile:</span></span>

```powershell
# PowerShell parameter completion shim for the dotnet CLI 
Register-ArgumentCompleter -Native -CommandName dotnet -ScriptBlock {
     param($commandName, $wordToComplete, $cursorPosition)
         dotnet complete --position $cursorPosition "$wordToComplete" | ForEach-Object {
            [System.Management.Automation.CompletionResult]::new($_, $_, 'ParameterValue', $_)
         }
 }
```

## <a name="bash"></a><span data-ttu-id="380cc-129">Bash</span><span class="sxs-lookup"><span data-stu-id="380cc-129">bash</span></span>

<span data-ttu-id="380cc-130">.NET Core CLI için **Bash** kabuğunuzun sekme tamamlamayı eklemek için, `.bashrc` dosyanıza aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="380cc-130">To add tab completion to your **bash** shell for the .NET Core CLI, add the following code to your `.bashrc` file:</span></span>

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

## <a name="zsh"></a><span data-ttu-id="380cc-131">ZSH</span><span class="sxs-lookup"><span data-stu-id="380cc-131">zsh</span></span>

<span data-ttu-id="380cc-132">.NET Core CLI için **ZSH** kabuğunuzun sekme tamamlamayı eklemek için, `.zshrc` dosyanıza aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="380cc-132">To add tab completion to your **zsh** shell for the .NET Core CLI, add the following code to your `.zshrc` file:</span></span>

```zsh
# zsh parameter completion for the dotnet CLI

_dotnet_zsh_complete() 
{
  local completions=("$(dotnet complete "$words")")

  reply=( "${(ps:\n:)completions}" )
}

compctl -K _dotnet_zsh_complete dotnet
```
