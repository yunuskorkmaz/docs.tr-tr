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
# <a name="how-to-enable-tab-completion-for-net-core-cli"></a><span data-ttu-id="44599-103">.NET Core CLI için sekme tamamlamayı etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="44599-103">How to enable TAB completion for .NET Core CLI</span></span>

<span data-ttu-id="44599-104">.NET Core 2.0 SDK'sı ile başlayarak, .NET Core CLI sekme tamamlamayı destekler.</span><span class="sxs-lookup"><span data-stu-id="44599-104">Starting with .NET Core 2.0 SDK, the .NET Core CLI supports tab completion.</span></span> <span data-ttu-id="44599-105">Bu makalede, üç Kabukları, PowerShell, Bash ve zsh için sekmesinde tamamlama yapılandırma açıklanır.</span><span class="sxs-lookup"><span data-stu-id="44599-105">This article describes how to configure tab completion for three shells, PowerShell, Bash, and zsh.</span></span> <span data-ttu-id="44599-106">Diğer Kabuk otomatik tamamlama desteği olabilir.</span><span class="sxs-lookup"><span data-stu-id="44599-106">Other shells may have support for auto completion.</span></span> <span data-ttu-id="44599-107">Otomatik Tamamlama yapılandırma kendi belgelerine başvurun, adımlar bu makalede açıklanan adımları aşağıdakine benzer olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="44599-107">Refer to their documentation on how to configure auto completion, the steps should be similar to the steps described in this article.</span></span>

[!INCLUDE [topic-appliesto-net-core-2plus](~/includes/topic-appliesto-net-core-2plus.md)]

<span data-ttu-id="44599-108">Bir kez Kurulum, sekme tamamlama için .NET Core CLI yazarak tetiklenir bir `dotnet ` komut kabuğu'nda ve ardından SEKME tuşuna basmak.</span><span class="sxs-lookup"><span data-stu-id="44599-108">Once setup, tab completion for the .NET Core CLI is triggered by typing a `dotnet ` command in the shell, and then hitting the TAB key.</span></span> <span data-ttu-id="44599-109">Geçerli komut satırı gönderilen `dotnet complete` komut ve sonuçları, kabuk tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="44599-109">The current command line is sent to the `dotnet complete` command, and the results are processed by your shell.</span></span> <span data-ttu-id="44599-110">Sonuçları sekme tamamlama etkinleştirmeden bir şey doğrudan göndererek test edebilirsiniz `dotnet complete` komutu.</span><span class="sxs-lookup"><span data-stu-id="44599-110">You can test the results without enabling tab completion by sending something directly to the `dotnet complete` command.</span></span> <span data-ttu-id="44599-111">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="44599-111">For example:</span></span>

```
> dotnet complete "dotnet a"
add
clean
--diagnostics
migrate
pack
```

<span data-ttu-id="44599-112">Bu komut işe yaramazsa, bu .NET Core 2.0 SDK'sını emin olun veya yukarıda yüklenir.</span><span class="sxs-lookup"><span data-stu-id="44599-112">If that command doesn't work, make sure that .NET Core 2.0 SDK or above is installed.</span></span> <span data-ttu-id="44599-113">Yüklü olduğu, ancak bu komut işe yaramazsa, emin `dotnet` komutu, .NET Core 2.0 SDK'sını ve üzeri bir sürüm olarak çözer.</span><span class="sxs-lookup"><span data-stu-id="44599-113">If it's installed, but that command still doesn't work, make sure that the `dotnet` command resolves to a version of .NET Core 2.0 SDK and above.</span></span> <span data-ttu-id="44599-114">Kullanım `dotnet --version` hangi sürümünü görmek için komutu `dotnet` için geçerli yolunuzu çözüyor.</span><span class="sxs-lookup"><span data-stu-id="44599-114">Use the `dotnet --version` command to see what version of `dotnet` your current path is resolving to.</span></span> <span data-ttu-id="44599-115">Daha fazla bilgi için [kullanmak için .NET Core sürümü](../versions/selection.md).</span><span class="sxs-lookup"><span data-stu-id="44599-115">For more information, see [Select the .NET Core version to use](../versions/selection.md).</span></span>

### <a name="examples"></a><span data-ttu-id="44599-116">Örnekler</span><span class="sxs-lookup"><span data-stu-id="44599-116">Examples</span></span>

<span data-ttu-id="44599-117">Hangi sekme tamamlamayı sağlayan bazı örnekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="44599-117">Here are some examples of what tab completion provides:</span></span>

<span data-ttu-id="44599-118">Giriş</span><span class="sxs-lookup"><span data-stu-id="44599-118">Input</span></span>                                | <span data-ttu-id="44599-119">olur</span><span class="sxs-lookup"><span data-stu-id="44599-119">becomes</span></span>                                                                     | <span data-ttu-id="44599-120">nedeni</span><span class="sxs-lookup"><span data-stu-id="44599-120">because</span></span>
:------------------------------------|:----------------------------------------------------------------------------|:--------------------------------
`dotnet a⇥`                          | `dotnet add`                                                                 | <span data-ttu-id="44599-121">`add` ilk alt alfabetik olur.</span><span class="sxs-lookup"><span data-stu-id="44599-121">`add` is the first subcommand, alphabetically.</span></span>
`dotnet add p⇥`                      | `dotnet add --help`                                                          | <span data-ttu-id="44599-122">Sekme tamamlama eşleşen alt dizeler ve `--help` alfabetik olarak ilk gelir.</span><span class="sxs-lookup"><span data-stu-id="44599-122">Tab completion matches substrings and `--help` comes first alphabetically.</span></span>
`dotnet add p⇥⇥`                    | `dotnet add package`                                                          | <span data-ttu-id="44599-123">İkinci kez Tab tuşuna basarak sonraki öneri sunar.</span><span class="sxs-lookup"><span data-stu-id="44599-123">Pressing tab a second time brings up the next suggestion.</span></span>      
`dotnet add package Microsoft⇥`      | `dotnet add package Microsoft.ApplicationInsights.Web`                      | <span data-ttu-id="44599-124">Sonuçlar alfabetik olarak döndürülür.</span><span class="sxs-lookup"><span data-stu-id="44599-124">Results are returned alphabetically.</span></span>
`dotnet remove reference ⇥`          | `dotnet remove reference ..\..\src\OmniSharp.DotNet\OmniSharp.DotNet.csproj` | <span data-ttu-id="44599-125">Sekme tamamlama, proje dosyası kullanan içindir.</span><span class="sxs-lookup"><span data-stu-id="44599-125">Tab completion is project file aware.</span></span>

## <a name="powershell"></a><span data-ttu-id="44599-126">PowerShell</span><span class="sxs-lookup"><span data-stu-id="44599-126">PowerShell</span></span>

<span data-ttu-id="44599-127">Sekme tamamlama eklemek için **PowerShell** .NET Core CLI için oluşturma veya değişkeninde depolanan profil düzenleme `$PROFILE`.</span><span class="sxs-lookup"><span data-stu-id="44599-127">To add tab completion to **PowerShell** for the .NET Core CLI, create or edit the profile stored in the variable `$PROFILE`.</span></span> <span data-ttu-id="44599-128">Daha fazla bilgi için [profilinizi oluşturma](/powershell/module/microsoft.powershell.core/about/about_profiles?view=powershell-6#how-to-create-a-profile) ve [profilleri ve yürütme İlkesi](/powershell/module/microsoft.powershell.core/about/about_profiles?view=powershell-6#profiles-and-execution-policy).</span><span class="sxs-lookup"><span data-stu-id="44599-128">For more information, see [How to create your profile](/powershell/module/microsoft.powershell.core/about/about_profiles?view=powershell-6#how-to-create-a-profile) and [Profiles and execution policy](/powershell/module/microsoft.powershell.core/about/about_profiles?view=powershell-6#profiles-and-execution-policy).</span></span> 

<span data-ttu-id="44599-129">Profiliniz için aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="44599-129">Add the following code to your profile:</span></span>

```powershell
# PowerShell parameter completion shim for the dotnet CLI 
Register-ArgumentCompleter -Native -CommandName dotnet -ScriptBlock {
     param($commandName, $wordToComplete, $cursorPosition)
         dotnet complete --position $cursorPosition "$wordToComplete" | ForEach-Object {
            [System.Management.Automation.CompletionResult]::new($_, $_, 'ParameterValue', $_)
         }
 }
```

## <a name="bash"></a><span data-ttu-id="44599-130">Bash</span><span class="sxs-lookup"><span data-stu-id="44599-130">Bash</span></span>

<span data-ttu-id="44599-131">Sekme tamamlama eklemek için **bash** Kabuk için .NET Core CLI, aşağıdaki kodu ekleyin, `.bashrc` dosyası:</span><span class="sxs-lookup"><span data-stu-id="44599-131">To add tab completion to your **bash** shell for the .NET Core CLI, add the following code to your `.bashrc` file:</span></span>

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

## <a name="zsh"></a><span data-ttu-id="44599-132">zsh</span><span class="sxs-lookup"><span data-stu-id="44599-132">Zsh</span></span>

<span data-ttu-id="44599-133">Sekme tamamlama eklemek için **zsh** Kabuk için .NET Core CLI, aşağıdaki kodu ekleyin, `.zshrc` dosyası:</span><span class="sxs-lookup"><span data-stu-id="44599-133">To add tab completion to your **zsh** shell for the .NET Core CLI, add the following code to your `.zshrc` file:</span></span>

```zsh
# zsh parameter completion for the dotnet CLI

_dotnet_zsh_complete() 
{
  local completions=("$(dotnet complete "$words")")

  reply=( "${(ps:\n:)completions}" )
}

compctl -K _dotnet_zsh_complete dotnet
```
