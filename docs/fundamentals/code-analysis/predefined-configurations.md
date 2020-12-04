---
title: Önceden tanımlı yapılandırma dosyaları (kod analizi)
description: Belirli kod analizi türlerini hedeflemek için önceden tanımlanmış editorconfig ve kural kümesi dosyalarını kullanma hakkında bilgi edinin.
ms.date: 09/24/2020
ms.topic: conceptual
ms.openlocfilehash: 4937dcab1183fa3f63be4afc71627a7c7c08c6bd
ms.sourcegitcommit: 665f8fc55258356f4d2f4a6585b750c974b26675
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/30/2020
ms.locfileid: "96589330"
---
# <a name="predefined-configuration-files"></a><span data-ttu-id="d2233-103">Önceden tanımlı yapılandırma dosyaları</span><span class="sxs-lookup"><span data-stu-id="d2233-103">Predefined configuration files</span></span>

<span data-ttu-id="d2233-104">Önceden tanımlanmış EditorConfig ve [kural kümesi](/visualstudio/code-quality/using-rule-sets-to-group-code-analysis-rules) dosyaları, güvenlik veya tasarım kuralları gibi kod kalitesi kuralları kategorisini hızlı ve kolay hale getirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d2233-104">Predefined EditorConfig and [rule set](/visualstudio/code-quality/using-rule-sets-to-group-code-analysis-rules) files are available that make it quick and easy to enable a category of code quality rules, such as security or design rules.</span></span> <span data-ttu-id="d2233-105">Belirli bir kural kategorisini etkinleştirerek, hedeflenen sorunları ve belirli koşulları belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d2233-105">By enabling a specific category of rules, you can identify targeted issues and specific conditions.</span></span> <span data-ttu-id="d2233-106">Önceden tanımlanmış bu dosyalara erişmek için [Microsoft. CodeAnalysis. Netçözümleyiciler](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) NuGet Çözümleyicisi paketini yüklersiniz.</span><span class="sxs-lookup"><span data-stu-id="d2233-106">To access these predefined files, install the [Microsoft.CodeAnalysis.NetAnalyzers](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) NuGet analyzer package.</span></span>

<span data-ttu-id="d2233-107">[Microsoft. CodeAnalysis. Netçözümleyiciler](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) aşağıdaki kural kategorileri için önceden tanımlanmış editorconfig dosyalarını ve kural kümelerini içerir:</span><span class="sxs-lookup"><span data-stu-id="d2233-107">[Microsoft.CodeAnalysis.NetAnalyzers](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) includes predefined EditorConfig files and rule sets for the following rule categories:</span></span>

- <span data-ttu-id="d2233-108">Tüm kurallar</span><span class="sxs-lookup"><span data-stu-id="d2233-108">All rules</span></span>
- <span data-ttu-id="d2233-109">Veri akışı</span><span class="sxs-lookup"><span data-stu-id="d2233-109">Dataflow</span></span>
- <span data-ttu-id="d2233-110">Tasarım</span><span class="sxs-lookup"><span data-stu-id="d2233-110">Design</span></span>
- <span data-ttu-id="d2233-111">Belgeler</span><span class="sxs-lookup"><span data-stu-id="d2233-111">Documentation</span></span>
- <span data-ttu-id="d2233-112">Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="d2233-112">Globalization</span></span>
- <span data-ttu-id="d2233-113">Birlikte çalışabilirlik</span><span class="sxs-lookup"><span data-stu-id="d2233-113">Interoperability</span></span>
- <span data-ttu-id="d2233-114">Bakım</span><span class="sxs-lookup"><span data-stu-id="d2233-114">Maintainability</span></span>
- <span data-ttu-id="d2233-115">Adlandırma</span><span class="sxs-lookup"><span data-stu-id="d2233-115">Naming</span></span>
- <span data-ttu-id="d2233-116">Performans</span><span class="sxs-lookup"><span data-stu-id="d2233-116">Performance</span></span>
- <span data-ttu-id="d2233-117">FxCop 'den</span><span class="sxs-lookup"><span data-stu-id="d2233-117">Ported from FxCop</span></span>
- <span data-ttu-id="d2233-118">Güvenilirlik</span><span class="sxs-lookup"><span data-stu-id="d2233-118">Reliability</span></span>
- <span data-ttu-id="d2233-119">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="d2233-119">Security</span></span>
- <span data-ttu-id="d2233-120">Kullanım</span><span class="sxs-lookup"><span data-stu-id="d2233-120">Usage</span></span>

<span data-ttu-id="d2233-121">Bu kural kategorilerinin her biri bir EditorConfig veya kural kümesi dosyasına sahiptir:</span><span class="sxs-lookup"><span data-stu-id="d2233-121">Each of those categories of rules has an EditorConfig or rule set file to:</span></span>

- <span data-ttu-id="d2233-122">Kategorideki tüm kuralları etkinleştir (ve diğer tüm kuralları devre dışı bırak)</span><span class="sxs-lookup"><span data-stu-id="d2233-122">Enable all the rules in the category (and disable all other rules)</span></span>
- <span data-ttu-id="d2233-123">Her kuralın varsayılan önem derecesini kullanın ve varsayılan ayar olarak etkindir (ve diğer tüm kuralları devre dışı bırakın)</span><span class="sxs-lookup"><span data-stu-id="d2233-123">Use each rule's default severity and enabled by default setting (and disable all other rules)</span></span>

> [!TIP]
> <span data-ttu-id="d2233-124">"Tüm kurallar" kategorisinin tüm kuralları devre dışı bırakmak için ek bir EditorConfig veya kural kümesi dosyası vardır.</span><span class="sxs-lookup"><span data-stu-id="d2233-124">The "all rules" category has an additional EditorConfig or rule set file to disable all rules.</span></span> <span data-ttu-id="d2233-125">Bir projedeki hiçbir çözümleyici uyarılarından veya hatalarından kurtulmak için bu dosyayı kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2233-125">Use this file to quickly get rid of any analyzer warnings or errors in a project.</span></span>

## <a name="predefined-editorconfig-files"></a><span data-ttu-id="d2233-126">Önceden tanımlanmış EditorConfig dosyaları</span><span class="sxs-lookup"><span data-stu-id="d2233-126">Predefined EditorConfig files</span></span>

<span data-ttu-id="d2233-127">Microsoft. CodeAnalysis. Netçözümleyiciler çözümleyici paketinin önceden tanımlanmış EditorConfig dosyaları, NuGet paketinin yüklendiği *EditorConfig* alt dizininde bulunur.</span><span class="sxs-lookup"><span data-stu-id="d2233-127">The predefined EditorConfig files for the Microsoft.CodeAnalysis.NetAnalyzers analyzer package are located in the *editorconfig* subdirectory of where the NuGet package was installed.</span></span> <span data-ttu-id="d2233-128">Örneğin, tüm güvenlik kurallarını etkinleştirmek için EditorConfig dosyası *editorconfig/SecurityRulesEnabled/. editorconfig* konumunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="d2233-128">For example, the EditorConfig file to enable all security rules is located at *editorconfig/SecurityRulesEnabled/.editorconfig*.</span></span>

<span data-ttu-id="d2233-129">Seçilen *. editorconfig* dosyasını projenizin kök dizinine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="d2233-129">Copy the chosen *.editorconfig* file to your project's root directory.</span></span>

## <a name="predefined-rule-sets"></a><span data-ttu-id="d2233-130">Önceden tanımlanmış kural kümeleri</span><span class="sxs-lookup"><span data-stu-id="d2233-130">Predefined rule sets</span></span>

<span data-ttu-id="d2233-131">Microsoft. CodeAnalysis. Netçözümleyiciler çözümleyici paketi için önceden tanımlanmış kural kümesi dosyaları, NuGet paketinin yüklendiği *RuleSets* alt dizininde bulunur.</span><span class="sxs-lookup"><span data-stu-id="d2233-131">The predefined rule set files for the Microsoft.CodeAnalysis.NetAnalyzers analyzer package are located in the *rulesets* subdirectory of where the NuGet package was installed.</span></span> <span data-ttu-id="d2233-132">Örneğin, tüm güvenlik kurallarını etkinleştirmek için kural kümesi dosyası *RuleSets/SecurityRulesEnabled. RuleSet* konumunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="d2233-132">For example, the rule set file to enable all security rules is located at *rulesets/SecurityRulesEnabled.ruleset*.</span></span> <span data-ttu-id="d2233-133">Kural kümelerinden birini veya birkaçını kopyalayın ve projenizi içeren dizine yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="d2233-133">Copy one or more of the rule sets and paste them in the directory that contains your project.</span></span>

## <a name="see-also"></a><span data-ttu-id="d2233-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2233-134">See also</span></span>

- [<span data-ttu-id="d2233-135">Çözümleyici yapılandırması</span><span class="sxs-lookup"><span data-stu-id="d2233-135">Analyzer configuration</span></span>](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [<span data-ttu-id="d2233-136">EditorConfig için .NET kod stili kural seçenekleri</span><span class="sxs-lookup"><span data-stu-id="d2233-136">.NET code style rule options for EditorConfig</span></span>](code-style-rule-options.md)
