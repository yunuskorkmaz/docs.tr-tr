---
title: Yerelleştirilebilirlik Gözden Geçirmesi
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a4c205d61e6de3e835954e405cece143520b4d2c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54623995"
---
# <a name="localizability-review"></a><span data-ttu-id="717c4-102">Yerelleştirilebilirlik Gözden Geçirmesi</span><span class="sxs-lookup"><span data-stu-id="717c4-102">Localizability Review</span></span>
<span data-ttu-id="717c4-103">Yerelleştirilebilirlik gözden geçirmesi dünya çapında kullanılmaya hazır uygulama geliştirmeyi Ara bir adımdır.</span><span class="sxs-lookup"><span data-stu-id="717c4-103">The localizability review is an intermediate step in the development of a world-ready application.</span></span> <span data-ttu-id="717c4-104">Genelleştirilmiş bir uygulamayı yerelleştirme için hazırdır ve herhangi bir kod veya özel işlem gerektiren kullanıcı arabirimi yönleri tanımlar doğrular.</span><span class="sxs-lookup"><span data-stu-id="717c4-104">It verifies that a globalized application is ready for localization and identifies any code or any aspects of the user interface that require special handling.</span></span> <span data-ttu-id="717c4-105">Bu adım ayrıca yerelleştirme işlemi herhangi bir işlev hatasıyla uygulamanıza neden olmaz emin olun yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="717c4-105">This step also helps ensure that the localization process will not introduce any functional defects into your application.</span></span> <span data-ttu-id="717c4-106">Yerelleştirilebilirlik gözden geçirmesi tarafından oluşturulan tüm sorunları ele, uygulamanızın yerelleştirme için hazırdır.</span><span class="sxs-lookup"><span data-stu-id="717c4-106">When all the issues raised by the localizability review have been addressed, your application is ready for localization.</span></span> <span data-ttu-id="717c4-107">Yerelleştirilebilirlik gözden geçirmesi kapsamlı ise, yerelleştirme işlemi sırasında herhangi bir kaynak kodu değiştirmek olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="717c4-107">If the localizability review is thorough, you should not have to modify any source code during the localization process.</span></span>  
  
 <span data-ttu-id="717c4-108">Yerelleştirilebilirlik gözden geçirmesi aşağıdaki üç denetimleri oluşur:</span><span class="sxs-lookup"><span data-stu-id="717c4-108">The localizability review consists of the following three checks:</span></span>  
  
-   [<span data-ttu-id="717c4-109">Genelleştirme önerileri uygulanır?</span><span class="sxs-lookup"><span data-stu-id="717c4-109">Are the globalization recommendations implemented?</span></span>](#global)  
  
-   [<span data-ttu-id="717c4-110">Kültüre duyarlı özellikleri doğru bir şekilde ele alınır?</span><span class="sxs-lookup"><span data-stu-id="717c4-110">Are culture-sensitive features handled correctly?</span></span>](#culture)  
  
-   [<span data-ttu-id="717c4-111">Uygulamanızın uluslararası verilerle sınanmıştır?</span><span class="sxs-lookup"><span data-stu-id="717c4-111">Have you tested your application with international data?</span></span>](#test)  
  
<a name="global"></a>   
## <a name="implementing-globalization-recommendations"></a><span data-ttu-id="717c4-112">Uygulama genelleştirme önerileri</span><span class="sxs-lookup"><span data-stu-id="717c4-112">Implementing globalization recommendations</span></span>  
 <span data-ttu-id="717c4-113">Tasarlanmış ve geliştirilmiş yerelleştirme aklınızda uygulamanızla ve öneriler, izlediyseniz ele [Genelleştirme](../../../docs/standard/globalization-localization/globalization.md) makalenin yerelleştirilebilirlik gözden geçirmesi kalite güvencesi geçişi büyük ölçüde olacaktır .</span><span class="sxs-lookup"><span data-stu-id="717c4-113">If you have designed and developed your application with localization in mind, and if you have followed the recommendations discussed in the [Globalization](../../../docs/standard/globalization-localization/globalization.md) article, the localizability review will largely be a quality assurance pass.</span></span> <span data-ttu-id="717c4-114">Aksi takdirde, bu aşamada gözden geçirmeli ve uygulamak için öneriler [Genelleştirme](../../../docs/standard/globalization-localization/globalization.md)ve yerelleştirme engelleyen kaynak kodundaki hataları düzeltin.</span><span class="sxs-lookup"><span data-stu-id="717c4-114">Otherwise, during this stage you should review and implement the recommendations for [globalization](../../../docs/standard/globalization-localization/globalization.md), and fix the errors in source code that prevent localization.</span></span>  
  
<a name="culture"></a>   
## <a name="handling-culture-sensitive-features"></a><span data-ttu-id="717c4-115">Kültüre duyarlı özellikleri işleme</span><span class="sxs-lookup"><span data-stu-id="717c4-115">Handling culture-sensitive features</span></span>  
 <span data-ttu-id="717c4-116">.NET Framework, kültüre göre büyük ölçüde farklılık alanları çeşitli programlama desteği sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="717c4-116">The .NET Framework does not provide programmatic support in a number of areas that vary widely by culture.</span></span> <span data-ttu-id="717c4-117">Çoğu durumda, aşağıdaki gibi özellik alanları işlemek için özel kod yazmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="717c4-117">In most cases, you have to write custom code to handle feature areas like the following:</span></span>  
  
-   <span data-ttu-id="717c4-118">Adresleri.</span><span class="sxs-lookup"><span data-stu-id="717c4-118">Addresses.</span></span>  
  
-   <span data-ttu-id="717c4-119">Telefon numaraları.</span><span class="sxs-lookup"><span data-stu-id="717c4-119">Telephone numbers.</span></span>  
  
-   <span data-ttu-id="717c4-120">Kağıt boyutları.</span><span class="sxs-lookup"><span data-stu-id="717c4-120">Paper sizes.</span></span>  
  
-   <span data-ttu-id="717c4-121">Ölçü birimi uzunlukları, ağırlıkları, alan, birim ve sıcaklıklar için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="717c4-121">Units of measure used for lengths, weights, area, volume, and temperatures.</span></span> <span data-ttu-id="717c4-122">.NET Framework ölçü arasında dönüştürmek için yerleşik destek sunmaz olsa da, kullanabileceğiniz <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> özelliği aşağıdaki örnekte gösterildiği gibi belirli bir ülke veya bölge Ölçüm sistemi kullanıp kullanmadığını belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="717c4-122">Although the .NET Framework does not offer built-in support for converting between units of measure, you can use the <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> property to determine whether a particular country or region uses the metric system, as the following example illustrates.</span></span>  
  
     [!code-csharp[Conceptual.Localizability#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.localizability/cs/ismetric1.cs#1)]
     [!code-vb[Conceptual.Localizability#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.localizability/vb/ismetric1.vb#1)]  
  
<a name="test"></a>   
## <a name="testing-your-application"></a><span data-ttu-id="717c4-123">Uygulamanızı sınama</span><span class="sxs-lookup"><span data-stu-id="717c4-123">Testing your application</span></span>  
 <span data-ttu-id="717c4-124">Uygulamanızı yerelleştirmek önce uluslararası işletim sistemi sürümlerinde uluslararası veriler kullanarak test etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="717c4-124">Before you localize your application, you should test it by using international data on international versions of the operating system.</span></span> <span data-ttu-id="717c4-125">Çoğu kullanıcı arabiriminin bu noktada yerelleştirilmez olsa da, aşağıdaki gibi sorunları algılamak mümkün olacaktır:</span><span class="sxs-lookup"><span data-stu-id="717c4-125">Although most of the user interface will not be localized at this point, you will be able to detect problems such as the following:</span></span>  
  
-   <span data-ttu-id="717c4-126">Doğru işletim sistemi sürümleri arasında serisini değil, serileştirilmiş veriler.</span><span class="sxs-lookup"><span data-stu-id="717c4-126">Serialized data that does not deserialize correctly across operating system versions.</span></span>  
  
-   <span data-ttu-id="717c4-127">Geçerli kültürün kuralları yansıtmaz sayısal veriler.</span><span class="sxs-lookup"><span data-stu-id="717c4-127">Numeric data that does not reflect the conventions of the current culture.</span></span> <span data-ttu-id="717c4-128">Örneğin, sayılar, yanlış Grup ayırıcıları, ondalık ayırıcı veya para birimi simgeleri görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="717c4-128">For example, numbers may be displayed with inaccurate group separators, decimal separators, or currency symbols.</span></span>  
  
-   <span data-ttu-id="717c4-129">Geçerli kültürün kuralları yansıtmaz tarih ve saat verileri.</span><span class="sxs-lookup"><span data-stu-id="717c4-129">Date and time data that does not reflect the conventions of the current culture.</span></span> <span data-ttu-id="717c4-130">Örneğin, ayı ve günü temsil eden sayı yanlış sırada görünebilir, tarih ayırıcı yanlış olabilir veya saat dilimi bilgilerini yanlış olabilir.</span><span class="sxs-lookup"><span data-stu-id="717c4-130">For example, numbers that represent the month and day may appear in the wrong order, date separators may be incorrect, or time zone information may be incorrect.</span></span>  
  
-   <span data-ttu-id="717c4-131">Bir varsayılan kültür, uygulamanız için belirlediğiniz değil çünkü bulunamayan kaynaklar.</span><span class="sxs-lookup"><span data-stu-id="717c4-131">Resources that cannot be found because you have not identified a default culture for your application.</span></span>  
  
-   <span data-ttu-id="717c4-132">Olağan dışı bir sırada belirli bir kültür için görüntülenen dize.</span><span class="sxs-lookup"><span data-stu-id="717c4-132">Strings that are displayed in an unusual order for the specific culture.</span></span>  
  
-   <span data-ttu-id="717c4-133">Dize karşılaştırmaları veya beklenmeyen sonuçlar döndüren eşitlik karşılaştırmaları.</span><span class="sxs-lookup"><span data-stu-id="717c4-133">String comparisons or comparisons for equality that return unexpected results.</span></span>  
  
 <span data-ttu-id="717c4-134">Sizin Uygulamanızı geliştirirken Genelleştirme önerileri takip, kültüre duyarlı özellikleri doğru işlendiğini ve ve test sırasında çıkan Yerelleştirme sorunları ele, sonraki adıma geçebilirsiniz [Yerelleştirme](../../../docs/standard/globalization-localization/localization.md).</span><span class="sxs-lookup"><span data-stu-id="717c4-134">If you've followed the globalization recommendations when developing your application, handled culture-sensitive features correctly, and identified and addressed the localization issues that arose during testing, you can proceed to the next step, [Localization](../../../docs/standard/globalization-localization/localization.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="717c4-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="717c4-135">See also</span></span>

- [<span data-ttu-id="717c4-136">Genelleştirme ve Yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="717c4-136">Globalization and Localization</span></span>](../../../docs/standard/globalization-localization/index.md)
- [<span data-ttu-id="717c4-137">Yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="717c4-137">Localization</span></span>](../../../docs/standard/globalization-localization/localization.md)
- [<span data-ttu-id="717c4-138">Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="717c4-138">Globalization</span></span>](../../../docs/standard/globalization-localization/globalization.md)
- [<span data-ttu-id="717c4-139">Masaüstü Uygulamalarındaki Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="717c4-139">Resources in Desktop Apps</span></span>](../../../docs/framework/resources/index.md)
