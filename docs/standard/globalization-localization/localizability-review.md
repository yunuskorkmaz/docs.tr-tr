---
title: "Yerelleştirilebilirlik Gözden Geçirmesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- world-ready applications, localizability
- application development [.NET Framework], localization
- localizability [.NET Framework]
- international applications [.NET Framework], localizability
- globalization [.NET Framework], localizability
- culture, localizability
- localization [.NET Framework], localizability
- global applications, localizability
- localizing resources
ms.assetid: 3aee2fbb-de47-4e37-8fe4-ddebb9719247
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2aaf7c466c6662611e2b37d5c967a99d050158df
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="localizability-review"></a><span data-ttu-id="41ec6-102">Yerelleştirilebilirlik Gözden Geçirmesi</span><span class="sxs-lookup"><span data-stu-id="41ec6-102">Localizability Review</span></span>
<span data-ttu-id="41ec6-103">Yerelleştirilebilirlik gözden geçirme, dünya çapında kullanılmaya hazır uygulama geliştirmede Ara bir adımdır.</span><span class="sxs-lookup"><span data-stu-id="41ec6-103">The localizability review is an intermediate step in the development of a world-ready application.</span></span> <span data-ttu-id="41ec6-104">Globalized uygulama yerelleştirme için hazır ve herhangi bir kod veya özel işlem gerektiren tüm yönlerini kullanıcı arabirimini tanımlar doğrular.</span><span class="sxs-lookup"><span data-stu-id="41ec6-104">It verifies that a globalized application is ready for localization and identifies any code or any aspects of the user interface that require special handling.</span></span> <span data-ttu-id="41ec6-105">Bu adım ayrıca yerelleştirme işlemi işlev bozuklukları uygulamanıza tanıtılacaktır değil, sağlamaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="41ec6-105">This step also helps ensure that the localization process will not introduce any functional defects into your application.</span></span> <span data-ttu-id="41ec6-106">Yerelleştirilebilirlik gözden geçirmesi tarafından gerçekleştirilen tüm sorunlar ele uygulamanızı yerelleştirme için hazır olur.</span><span class="sxs-lookup"><span data-stu-id="41ec6-106">When all the issues raised by the localizability review have been addressed, your application is ready for localization.</span></span> <span data-ttu-id="41ec6-107">Yerelleştirilebilirlik gözden geçirmesi kapsamlı ise, herhangi bir kaynak kod yerelleştirme işlemi sırasında değiştirmek olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="41ec6-107">If the localizability review is thorough, you should not have to modify any source code during the localization process.</span></span>  
  
 <span data-ttu-id="41ec6-108">Yerelleştirilebilirlik gözden geçirmesi aşağıdaki üç çekler oluşur:</span><span class="sxs-lookup"><span data-stu-id="41ec6-108">The localizability review consists of the following three checks:</span></span>  
  
-   [<span data-ttu-id="41ec6-109">Genelleştirme önerileri uygulanır?</span><span class="sxs-lookup"><span data-stu-id="41ec6-109">Are the globalization recommendations implemented?</span></span>](#global)  
  
-   [<span data-ttu-id="41ec6-110">Kültüre duyarlı özellikleri doğru şekilde işlenir?</span><span class="sxs-lookup"><span data-stu-id="41ec6-110">Are culture-sensitive features handled correctly?</span></span>](#culture)  
  
-   [<span data-ttu-id="41ec6-111">Uygulamanızı uluslararası verilerle sınanmıştır?</span><span class="sxs-lookup"><span data-stu-id="41ec6-111">Have you tested your application with international data?</span></span>](#test)  
  
<a name="global"></a>   
## <a name="implementing-globalization-recommendations"></a><span data-ttu-id="41ec6-112">Uygulama genelleştirme önerileri</span><span class="sxs-lookup"><span data-stu-id="41ec6-112">Implementing globalization recommendations</span></span>  
 <span data-ttu-id="41ec6-113">Tasarlanmış ve yerelleştirme aklınızda uygulamanızla geliştirilmiştir ve öneriler, izlediyseniz ele [Genelleştirme](../../../docs/standard/globalization-localization/globalization.md) makalenin yerelleştirilebilirlik gözden geçirmesi büyük ölçüde kalite güvence geçişi olacaktır .</span><span class="sxs-lookup"><span data-stu-id="41ec6-113">If you have designed and developed your application with localization in mind, and if you have followed the recommendations discussed in the [Globalization](../../../docs/standard/globalization-localization/globalization.md) article, the localizability review will largely be a quality assurance pass.</span></span> <span data-ttu-id="41ec6-114">Aksi takdirde, bu aşamada gözden geçirmeli ve uygulamak için öneriler [Genelleştirme](../../../docs/standard/globalization-localization/globalization.md)ve kaynak kodunda yerelleştirme önlemek hataları düzeltin.</span><span class="sxs-lookup"><span data-stu-id="41ec6-114">Otherwise, during this stage you should review and implement the recommendations for [globalization](../../../docs/standard/globalization-localization/globalization.md), and fix the errors in source code that prevent localization.</span></span>  
  
<a name="culture"></a>   
## <a name="handling-culture-sensitive-features"></a><span data-ttu-id="41ec6-115">Kültüre duyarlı özellikleri işleme</span><span class="sxs-lookup"><span data-stu-id="41ec6-115">Handling culture-sensitive features</span></span>  
 <span data-ttu-id="41ec6-116">.NET Framework tarafından kültür büyük ölçüde farklılık alanları çeşitli programlama desteği sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="41ec6-116">The .NET Framework does not provide programmatic support in a number of areas that vary widely by culture.</span></span> <span data-ttu-id="41ec6-117">Çoğu durumda, aşağıdaki gibi özellik alanları işlemek için özel kod yazmanıza vardır:</span><span class="sxs-lookup"><span data-stu-id="41ec6-117">In most cases, you have to write custom code to handle feature areas like the following:</span></span>  
  
-   <span data-ttu-id="41ec6-118">Adresleri.</span><span class="sxs-lookup"><span data-stu-id="41ec6-118">Addresses.</span></span>  
  
-   <span data-ttu-id="41ec6-119">Telefon numaraları.</span><span class="sxs-lookup"><span data-stu-id="41ec6-119">Telephone numbers.</span></span>  
  
-   <span data-ttu-id="41ec6-120">Kağıt boyutları.</span><span class="sxs-lookup"><span data-stu-id="41ec6-120">Paper sizes.</span></span>  
  
-   <span data-ttu-id="41ec6-121">Ölçü birimi uzunlukları, ağırlıkları, alan, birim ve etme için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="41ec6-121">Units of measure used for lengths, weights, area, volume, and temperatures.</span></span> <span data-ttu-id="41ec6-122">.NET Framework ölçü arasında dönüştürme için yerleşik destek sağlamaz, ancak kullanabilirsiniz <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> özelliği aşağıdaki örnekte gösterildiği gibi belirli bir ülke veya bölge Metrik sistem kullanıp kullanmadığını belirleyin.</span><span class="sxs-lookup"><span data-stu-id="41ec6-122">Although the .NET Framework does not offer built-in support for converting between units of measure, you can use the <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> property to determine whether a particular country or region uses the metric system, as the following example illustrates.</span></span>  
  
     [!code-csharp[Conceptual.Localizability#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.localizability/cs/ismetric1.cs#1)]
     [!code-vb[Conceptual.Localizability#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.localizability/vb/ismetric1.vb#1)]  
  
<a name="test"></a>   
## <a name="testing-your-application"></a><span data-ttu-id="41ec6-123">Uygulamanızı sınama</span><span class="sxs-lookup"><span data-stu-id="41ec6-123">Testing your application</span></span>  
 <span data-ttu-id="41ec6-124">Uygulamanızı yerelleştirme önce uluslararası işletim sistemi sürümlerinde uluslararası verileri kullanarak test etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="41ec6-124">Before you localize your application, you should test it by using international data on international versions of the operating system.</span></span> <span data-ttu-id="41ec6-125">Çoğu kullanıcı arabirimi, bu noktada yerelleştirilmiş olabilir değil de, aşağıdaki gibi sorunlar algılayabilir olacaktır:</span><span class="sxs-lookup"><span data-stu-id="41ec6-125">Although most of the user interface will not be localized at this point, you will be able to detect problems such as the following:</span></span>  
  
-   <span data-ttu-id="41ec6-126">Doğru işletim sistemi sürümleri arasında serisini değil serileştirilmiş veriler.</span><span class="sxs-lookup"><span data-stu-id="41ec6-126">Serialized data that does not deserialize correctly across operating system versions.</span></span>  
  
-   <span data-ttu-id="41ec6-127">Geçerli kültür kuralları yansıtmaz sayısal veriler.</span><span class="sxs-lookup"><span data-stu-id="41ec6-127">Numeric data that does not reflect the conventions of the current culture.</span></span> <span data-ttu-id="41ec6-128">Örneğin, numaraları yanlış Grup ayırıcılar, ondalık ayırıcı veya para birimi simgeleri görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="41ec6-128">For example, numbers may be displayed with inaccurate group separators, decimal separators, or currency symbols.</span></span>  
  
-   <span data-ttu-id="41ec6-129">Geçerli kültür kuralları yansıtmaz tarih ve saat verileri.</span><span class="sxs-lookup"><span data-stu-id="41ec6-129">Date and time data that does not reflect the conventions of the current culture.</span></span> <span data-ttu-id="41ec6-130">Örneğin, ayı ve günü temsil eden sayı yanlış sırayla görünebilir, tarih ayırıcıları yanlış olabilir veya saat dilimi bilgileri hatalı olabilir.</span><span class="sxs-lookup"><span data-stu-id="41ec6-130">For example, numbers that represent the month and day may appear in the wrong order, date separators may be incorrect, or time zone information may be incorrect.</span></span>  
  
-   <span data-ttu-id="41ec6-131">Varsayılan kültürü uygulamanız için tanımladığınız değil çünkü bulunamayan kaynaklar.</span><span class="sxs-lookup"><span data-stu-id="41ec6-131">Resources that cannot be found because you have not identified a default culture for your application.</span></span>  
  
-   <span data-ttu-id="41ec6-132">Olağan dışı bir sırada belirli kültür için görüntülenen dizeleri.</span><span class="sxs-lookup"><span data-stu-id="41ec6-132">Strings that are displayed in an unusual order for the specific culture.</span></span>  
  
-   <span data-ttu-id="41ec6-133">Karşılaştırmaları veya beklenmeyen sonuçlar döndürebilir karşılaştırmaları eşitlik için dize.</span><span class="sxs-lookup"><span data-stu-id="41ec6-133">String comparisons or comparisons for equality that return unexpected results.</span></span>  
  
 <span data-ttu-id="41ec6-134">Artık Uygulamanızı geliştirirken Genelleştirme önerileri ve ardından, kültüre duyarlı özellikleri, doğru ele ve tanımlanan ve test sırasında çıkan yerelleştirme sorunlar ele, sonraki adıma geçebilirsiniz [Yerelleştirme](../../../docs/standard/globalization-localization/localization.md).</span><span class="sxs-lookup"><span data-stu-id="41ec6-134">If you've followed the globalization recommendations when developing your application, handled culture-sensitive features correctly, and identified and addressed the localization issues that arose during testing, you can proceed to the next step, [Localization](../../../docs/standard/globalization-localization/localization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41ec6-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="41ec6-135">See Also</span></span>  
 [<span data-ttu-id="41ec6-136">Genelleştirme ve Yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="41ec6-136">Globalization and Localization</span></span>](../../../docs/standard/globalization-localization/index.md)  
 [<span data-ttu-id="41ec6-137">Yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="41ec6-137">Localization</span></span>](../../../docs/standard/globalization-localization/localization.md)  
 [<span data-ttu-id="41ec6-138">Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="41ec6-138">Globalization</span></span>](../../../docs/standard/globalization-localization/globalization.md)  
 [<span data-ttu-id="41ec6-139">Masaüstü Uygulamalarındaki Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="41ec6-139">Resources in Desktop Apps</span></span>](../../../docs/framework/resources/index.md)
