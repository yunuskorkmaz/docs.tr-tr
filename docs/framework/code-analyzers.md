---
title: .NET Framework için kod Çözümleyicileri
titleSuffix: ''
description: Kodunuzda sorunları bulmak ve gidermek için .NET Framework Çözümleyicileri paketindeki Çözümleyicileri nasıl kullanacağınızı öğrenin.
author: billwagner
ms.author: wiwagn
ms.date: 10/23/2020
ms.openlocfilehash: 69dfbc9f9645c7f602ffbce46308b241c119fd96
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92687918"
---
# <a name="code-analysis"></a><span data-ttu-id="e2105-103">Kod analizi</span><span class="sxs-lookup"><span data-stu-id="e2105-103">Code analysis</span></span>

<span data-ttu-id="e2105-104">.NET Framework uygulama kodunuzda olası sorunları bulmak için kod Çözümleyicileri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e2105-104">You can use code analyzers to find potential issues in your .NET Framework application code.</span></span> <span data-ttu-id="e2105-105">Çözümleyiciler olası sorunları bullar ve bunlara yönelik düzeltmeler önerir.</span><span class="sxs-lookup"><span data-stu-id="e2105-105">The analyzers find potential issues and suggest fixes for them.</span></span>

<span data-ttu-id="e2105-106">Roslyn tabanlı kod Çözümleyicileri, kodunuzu yazarken veya bir CI yapısının parçası olarak Visual Studio 'da etkileşimli olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="e2105-106">Roslyn-based code analyzers run interactively in Visual Studio as you write your code or as part of a CI build.</span></span> <span data-ttu-id="e2105-107">Çözümleyiciler geliştirme döngüsünün mümkün olduğunca erken eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e2105-107">You should add the analyzers to your project as early as possible in the development cycle.</span></span> <span data-ttu-id="e2105-108">Kodunuzda olası sorunları daha önce bulduklarında, bunları çözmeleri daha kolay olur.</span><span class="sxs-lookup"><span data-stu-id="e2105-108">The sooner you find any potential issues in your code, the easier they are to fix.</span></span> <span data-ttu-id="e2105-109">Çözümleyiciler, var olan koddaki sorunları bayrak ve geliştirmeye devam ederken yeni sorunlar hakkında uyarır.</span><span class="sxs-lookup"><span data-stu-id="e2105-109">The analyzers flag issues in existing code and warn about new issues as you continue development.</span></span>

## <a name="install-and-configure-analyzers"></a><span data-ttu-id="e2105-110">Çözümleyicileri yükleyip yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e2105-110">Install and configure analyzers</span></span>

<span data-ttu-id="e2105-111">.NET Framework Çözümleyicisi, [Microsoft. NetFramework. çözümleyiciler](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) NuGet paketinde dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="e2105-111">The .NET Framework Analyzer is delivered in the [Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) NuGet package.</span></span> <span data-ttu-id="e2105-112">Bu paket, güvenlik Çözümleyicileri içeren .NET Framework API 'Lerine özgü çözümleyiciler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e2105-112">This package provides analyzers that are specific to .NET Framework APIs, which includes security analyzers.</span></span> <span data-ttu-id="e2105-113">Paket, [Microsoft. CodeAnalysis. Fxcopçözümleyiciler paketine](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers)dahildir. bu nedenle, paketi yüklerseniz, .NET Framework çözümleyicilerinin ayrı olarak yüklenmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="e2105-113">The package is included with the [Microsoft.CodeAnalysis.FxCopAnalyzers package](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers), so if you install that package, there's no need to install the .NET Framework analyzers separately.</span></span>

<span data-ttu-id="e2105-114">Çözümleyicilerin çalıştırmasını istediğiniz her projeye NuGet paketini yükler.</span><span class="sxs-lookup"><span data-stu-id="e2105-114">Install the NuGet package on every project where you want the analyzers to run.</span></span> <span data-ttu-id="e2105-115">Yalnızca bir geliştiricinin projeye eklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="e2105-115">Only one developer needs to add them to the project.</span></span> <span data-ttu-id="e2105-116">Çözümleyici paketi bir proje bağımlılığıdır ve güncelleştirilmiş çözüme sahip olduktan sonra her geliştiricinin makinesinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="e2105-116">The analyzer package is a project dependency and will run on every developer's machine once it has the updated solution.</span></span>

<span data-ttu-id="e2105-117">Paketi yüklemek için projeye sağ tıklayın ve "bağımlılıkları Yönet" i seçin.</span><span class="sxs-lookup"><span data-stu-id="e2105-117">To install the package, right-click on the project, and select "Manage Dependencies".</span></span> <span data-ttu-id="e2105-118">NuGet Gezgini 'nden "Microsoft. NetFramework. çözümleyiciler" araması yapın.</span><span class="sxs-lookup"><span data-stu-id="e2105-118">From the NuGet explorer, search for "Microsoft.NetFramework.Analyzers".</span></span> <span data-ttu-id="e2105-119">Çözümünüzdeki tüm projelere en son kararlı sürümü yükler.</span><span class="sxs-lookup"><span data-stu-id="e2105-119">Install the latest stable version in all projects in your solution.</span></span>

## <a name="use-the-analyzers"></a><span data-ttu-id="e2105-120">Çözümleyicileri kullanma</span><span class="sxs-lookup"><span data-stu-id="e2105-120">Use the analyzers</span></span>

<span data-ttu-id="e2105-121">NuGet paketi yüklendikten sonra çözümünüzü derleyin.</span><span class="sxs-lookup"><span data-stu-id="e2105-121">Once the NuGet package is installed, build your solution.</span></span> <span data-ttu-id="e2105-122">Çözümleyici, kod tabanınızda bulduğu tüm sorunları rapor eder.</span><span class="sxs-lookup"><span data-stu-id="e2105-122">The analyzer will report any issues it locates in your codebase.</span></span> <span data-ttu-id="e2105-123">Sorunlar, aşağıdaki görüntüde gösterildiği gibi Visual Studio Hata Listesi penceresinde uyarı olarak bildirilir:</span><span class="sxs-lookup"><span data-stu-id="e2105-123">The issues are reported as warnings in the Visual Studio Error List window, as shown in the following image:</span></span>

![.NET Framework Çözümleyicileri tarafından bildirilen sorunlar.](./media/framework-analyzers-2.png)

<span data-ttu-id="e2105-125">Kod yazarken, kodunuzda olası bir sorunu dalgalı çizgiler görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="e2105-125">As you write code, you see squiggles underneath any potential issue in your code.</span></span>
<span data-ttu-id="e2105-126">Daha fazla bilgi edinmek için herhangi bir sorunun üzerine gelin ve aşağıdaki görüntüde gösterildiği gibi olası bir düzeltmeyle ilgili önerileri görün:</span><span class="sxs-lookup"><span data-stu-id="e2105-126">Hover over any issue to get more information and see suggestions for any possible fix, as shown in the following image:</span></span>

![Kod Çözümleyicileri tarafından bulunan sorunların etkileşimli raporu.](./media/framework-analyzers-1.png)

<span data-ttu-id="e2105-128">Daha fazla bilgi için bkz. [Visual Studio 'Da kod analizi](/visualstudio/code-quality/roslyn-analyzers-overview).</span><span class="sxs-lookup"><span data-stu-id="e2105-128">For more information, see [Code analysis in Visual Studio](/visualstudio/code-quality/roslyn-analyzers-overview).</span></span>

## <a name="types-of-rules"></a><span data-ttu-id="e2105-129">Kural türleri</span><span class="sxs-lookup"><span data-stu-id="e2105-129">Types of rules</span></span>

<span data-ttu-id="e2105-130">Çözümleyiciler çözümünüzdeki kodu ve bir ön ek ile yüzey uyarılarını inceler `CA` .</span><span class="sxs-lookup"><span data-stu-id="e2105-130">The analyzers examine the code in your solution and surface warnings with a `CA` prefix.</span></span> <span data-ttu-id="e2105-131">Olası tüm uyarıların listesi için bkz. [kod kalitesi kuralları](../fundamentals/code-analysis/quality-rules/index.md).</span><span class="sxs-lookup"><span data-stu-id="e2105-131">For a list of all possible warnings, see [Code quality rules](../fundamentals/code-analysis/quality-rules/index.md).</span></span> <span data-ttu-id="e2105-132">Bu uyarılardan yalnızca bazıları aşağıdakiler dahil .NET Framework API 'LERI için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="e2105-132">Only some of these warnings apply to .NET Framework APIS, including:</span></span>

- [<span data-ttu-id="e2105-133">CA1058: Türler belirli temel türleri aşmamalıdır</span><span class="sxs-lookup"><span data-stu-id="e2105-133">CA1058: Types should not extend certain base types</span></span>](../fundamentals/code-analysis/quality-rules/ca1058.md)

- [<span data-ttu-id="e2105-134">CA2153: bozuk durum özel durumlarını yakalamayın</span><span class="sxs-lookup"><span data-stu-id="e2105-134">CA2153: Do not catch corrupted state exceptions</span></span>](../fundamentals/code-analysis/quality-rules/ca2153.md)

- [<span data-ttu-id="e2105-135">CA2229: Serileştirme oluşturucularını uygulayın</span><span class="sxs-lookup"><span data-stu-id="e2105-135">CA2229: Implement serialization constructors</span></span>](../fundamentals/code-analysis/quality-rules/ca2229.md)

- [<span data-ttu-id="e2105-136">CA2235: Tüm serileştirilebilir olmayan alanları işaretleyin</span><span class="sxs-lookup"><span data-stu-id="e2105-136">CA2235: Mark all non-serializable fields</span></span>](../fundamentals/code-analysis/quality-rules/ca2235.md)

- [<span data-ttu-id="e2105-137">CA2237: ISerializable türlerini seri hale getirilebilir ile Işaretle</span><span class="sxs-lookup"><span data-stu-id="e2105-137">CA2237: Mark ISerializable types with serializable</span></span>](../fundamentals/code-analysis/quality-rules/ca2237.md)

- [<span data-ttu-id="e2105-138">CA3075: XML 'de güvenli olmayan DTD işleme</span><span class="sxs-lookup"><span data-stu-id="e2105-138">CA3075: Insecure DTD processing in XML</span></span>](../fundamentals/code-analysis/quality-rules/ca3075.md)

- [<span data-ttu-id="e2105-139">CA5350: zayıf şifreleme algoritmaları kullanmayın</span><span class="sxs-lookup"><span data-stu-id="e2105-139">CA5350: Do not use weak cryptographic algorithms</span></span>](../fundamentals/code-analysis/quality-rules/ca5350.md)

- [<span data-ttu-id="e2105-140">CA5351 kopuk şifreleme algoritmaları kullanma</span><span class="sxs-lookup"><span data-stu-id="e2105-140">CA5351 Do not use broken cryptographic algorithms</span></span>](../fundamentals/code-analysis/quality-rules/ca5351.md)

## <a name="see-also"></a><span data-ttu-id="e2105-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2105-141">See also</span></span>

- [<span data-ttu-id="e2105-142">Visual Studio’da kod analizi</span><span class="sxs-lookup"><span data-stu-id="e2105-142">Code analysis in Visual Studio</span></span>](/visualstudio/code-quality/roslyn-analyzers-overview)
- [<span data-ttu-id="e2105-143">.NET SDK 'da kod analizi</span><span class="sxs-lookup"><span data-stu-id="e2105-143">Code analysis in the .NET SDK</span></span>](../fundamentals/code-analysis/overview.md)
