---
title: Yerelleştirilebilirlik İncelemesi
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
ms.openlocfilehash: b286bdd2c5d7b03a0a2b5f94478e252da6cd0ae2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120856"
---
# <a name="localizability-review"></a><span data-ttu-id="170bd-102">Yerelleştirilebilirlik incelemesi</span><span class="sxs-lookup"><span data-stu-id="170bd-102">Localizability review</span></span>

<span data-ttu-id="170bd-103">Yerelleştirilebilirlik incelemesi, dünya çapında bir uygulama geliştirmenin bir ara adımıdır.</span><span class="sxs-lookup"><span data-stu-id="170bd-103">The localizability review is an intermediate step in the development of a world-ready application.</span></span> <span data-ttu-id="170bd-104">Bir Genelleştirilmiş uygulamasının yerelleştirme için hazırlandığını doğrular ve herhangi bir kodu veya özel işleme gerektiren Kullanıcı arabiriminin herhangi bir yönlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="170bd-104">It verifies that a globalized application is ready for localization and identifies any code or any aspects of the user interface that require special handling.</span></span> <span data-ttu-id="170bd-105">Bu adım Ayrıca yerelleştirme işleminin uygulamanıza işlevsel hatalar sunmaz.</span><span class="sxs-lookup"><span data-stu-id="170bd-105">This step also helps ensure that the localization process will not introduce any functional defects into your application.</span></span> <span data-ttu-id="170bd-106">Yerelleştirilebilirlik incelemesi tarafından oluşturulan tüm sorunlar ele geçirilmemişse, uygulamanız yerelleştirme için hazırlayın.</span><span class="sxs-lookup"><span data-stu-id="170bd-106">When all the issues raised by the localizability review have been addressed, your application is ready for localization.</span></span> <span data-ttu-id="170bd-107">Yerelleştirilebilirlik incelemesi tam ise, yerelleştirme işlemi sırasında herhangi bir kaynak kodunu değiştirmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="170bd-107">If the localizability review is thorough, you should not have to modify any source code during the localization process.</span></span>

<span data-ttu-id="170bd-108">Yerelleştirilebilirlik incelemesi, aşağıdaki üç denetimi içerir:</span><span class="sxs-lookup"><span data-stu-id="170bd-108">The localizability review consists of the following three checks:</span></span>

- [<span data-ttu-id="170bd-109">Genelleştirme önerileri uygulandı mi?</span><span class="sxs-lookup"><span data-stu-id="170bd-109">Are the globalization recommendations implemented?</span></span>](#global)

- [<span data-ttu-id="170bd-110">Kültüre duyarlı özellikler doğru şekilde işlensin mi?</span><span class="sxs-lookup"><span data-stu-id="170bd-110">Are culture-sensitive features handled correctly?</span></span>](#culture)

- [<span data-ttu-id="170bd-111">Uygulamanızı Uluslararası verilerle test etmeniz mi gerekiyor?</span><span class="sxs-lookup"><span data-stu-id="170bd-111">Have you tested your application with international data?</span></span>](#test)

<a name="global"></a>
## <a name="implement-globalization-recommendations"></a><span data-ttu-id="170bd-112">Genelleştirme önerilerini Uygula</span><span class="sxs-lookup"><span data-stu-id="170bd-112">Implement globalization recommendations</span></span>

<span data-ttu-id="170bd-113">Uygulamanızı aklına göre tasarlanıp geliştirip geliştirdiyseniz ve [Genelleştirme](../../../docs/standard/globalization-localization/globalization.md) makalesinde açıklanan önerileri izlediyseniz, Yerelleştirilebilirlik incelemesi büyük ölçüde kalite güvencesi geçişine sahip olur.</span><span class="sxs-lookup"><span data-stu-id="170bd-113">If you have designed and developed your application with localization in mind, and if you have followed the recommendations discussed in the [Globalization](../../../docs/standard/globalization-localization/globalization.md) article, the localizability review will largely be a quality assurance pass.</span></span> <span data-ttu-id="170bd-114">Aksi takdirde, bu aşamada [Genelleştirme](../../../docs/standard/globalization-localization/globalization.md) önerilerini gözden geçirmeniz ve uygulamanız ve kaynak koddaki yerelleştirmeyi önleyen hataları çözmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="170bd-114">Otherwise, during this stage you should review and implement the recommendations for [globalization](../../../docs/standard/globalization-localization/globalization.md) and fix the errors in source code that prevent localization.</span></span>

<a name="culture"></a>
## <a name="handle-culture-sensitive-features"></a><span data-ttu-id="170bd-115">Kültüre duyarlı özellikleri işleme</span><span class="sxs-lookup"><span data-stu-id="170bd-115">Handle culture-sensitive features</span></span>

<span data-ttu-id="170bd-116">.NET, kültüre göre farklılık gösteren çeşitli alanlarda programlama desteği sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="170bd-116">.NET does not provide programmatic support in a number of areas that vary widely by culture.</span></span> <span data-ttu-id="170bd-117">Çoğu durumda, aşağıdaki gibi özellik alanlarının işlenmesi için özel kod yazmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="170bd-117">In most cases, you have to write custom code to handle feature areas like the following:</span></span>

- <span data-ttu-id="170bd-118">Adresler</span><span class="sxs-lookup"><span data-stu-id="170bd-118">Addresses</span></span>

- <span data-ttu-id="170bd-119">Telefon numaraları</span><span class="sxs-lookup"><span data-stu-id="170bd-119">Telephone numbers</span></span>

- <span data-ttu-id="170bd-120">Kağıt boyutları</span><span class="sxs-lookup"><span data-stu-id="170bd-120">Paper sizes</span></span>

- <span data-ttu-id="170bd-121">Uzunluk, ağırlık, alan, birim ve sıcaklıklar için kullanılan ölçü birimleri</span><span class="sxs-lookup"><span data-stu-id="170bd-121">Units of measure used for lengths, weights, area, volume, and temperatures</span></span>

   <span data-ttu-id="170bd-122">.NET, ölçü birimleri arasında dönüştürme için yerleşik destek sunmasa da, aşağıdaki örnekte gösterildiği gibi belirli bir ülkenin veya bölgenin ölçüm sistemini kullanıp kullanmadığını anlamak için <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="170bd-122">Although .NET does not offer built-in support for converting between units of measure, you can use the <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> property to determine whether a particular country or region uses the metric system, as the following example illustrates.</span></span>

   [!code-csharp[Conceptual.Localizability#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.localizability/cs/ismetric1.cs#1)]
   [!code-vb[Conceptual.Localizability#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.localizability/vb/ismetric1.vb#1)]

<a name="test"></a>
## <a name="test-your-application"></a><span data-ttu-id="170bd-123">Uygulamanızı test etme</span><span class="sxs-lookup"><span data-stu-id="170bd-123">Test your application</span></span>

<span data-ttu-id="170bd-124">Uygulamanızı yerelleştirebilmeniz için, işletim sisteminin Uluslararası sürümlerindeki Uluslararası verileri kullanarak test etmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="170bd-124">Before you localize your application, you should test it by using international data on international versions of the operating system.</span></span> <span data-ttu-id="170bd-125">Bu noktada Kullanıcı arabiriminin büyük bir çoğunluğu yerelleştirilemez, ancak aşağıdaki gibi sorunları tespit edebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="170bd-125">Although most of the user interface will not be localized at this point, you will be able to detect problems such as the following:</span></span>

- <span data-ttu-id="170bd-126">İşletim sistemi sürümlerinde doğru şekilde seri durumdan çıkarmayan serileştirilmiş veriler.</span><span class="sxs-lookup"><span data-stu-id="170bd-126">Serialized data that does not deserialize correctly across operating system versions.</span></span>

- <span data-ttu-id="170bd-127">Geçerli kültürün kurallarını yansıtmayan sayısal veriler.</span><span class="sxs-lookup"><span data-stu-id="170bd-127">Numeric data that does not reflect the conventions of the current culture.</span></span> <span data-ttu-id="170bd-128">Örneğin, sayılar yanlış Grup ayırıcılar, Ondalık ayırıcılar veya para birimi sembolleri ile görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="170bd-128">For example, numbers may be displayed with inaccurate group separators, decimal separators, or currency symbols.</span></span>

- <span data-ttu-id="170bd-129">Geçerli kültürün kurallarını yansıtmayan tarih ve saat verileri.</span><span class="sxs-lookup"><span data-stu-id="170bd-129">Date and time data that does not reflect the conventions of the current culture.</span></span> <span data-ttu-id="170bd-130">Örneğin, ayı ve günü temsil eden sayılar yanlış sırada görünebilir, tarih ayırıcıları yanlış olabilir veya saat dilimi bilgisi yanlış olabilir.</span><span class="sxs-lookup"><span data-stu-id="170bd-130">For example, numbers that represent the month and day may appear in the wrong order, date separators may be incorrect, or time zone information may be incorrect.</span></span>

- <span data-ttu-id="170bd-131">Uygulamanız için bir varsayılan kültür belirlemei olmadığınızdan, bulunamayan kaynaklar.</span><span class="sxs-lookup"><span data-stu-id="170bd-131">Resources that cannot be found because you have not identified a default culture for your application.</span></span>

- <span data-ttu-id="170bd-132">Belirli kültür için olağan dışı bir düzende görüntülenen dizeler.</span><span class="sxs-lookup"><span data-stu-id="170bd-132">Strings that are displayed in an unusual order for the specific culture.</span></span>

- <span data-ttu-id="170bd-133">Beklenmeyen sonuçlar döndüren eşitlik için dize karşılaştırmaları veya karşılaştırmalar.</span><span class="sxs-lookup"><span data-stu-id="170bd-133">String comparisons or comparisons for equality that return unexpected results.</span></span>

<span data-ttu-id="170bd-134">Uygulamanızı geliştirirken Genelleştirme önerilerini izlediyseniz, kültüre duyarlı özellikleri doğru bir şekilde işlemişseniz ve test sırasında kullanılan yerelleştirme sorunlarını tanımladıysanız, bir sonraki adımla [devam edebilirsiniz. Yerelleştirme](../../../docs/standard/globalization-localization/localization.md).</span><span class="sxs-lookup"><span data-stu-id="170bd-134">If you've followed the globalization recommendations when developing your application, handled culture-sensitive features correctly, and identified and addressed the localization issues that arose during testing, you can proceed to the next step, [Localization](../../../docs/standard/globalization-localization/localization.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="170bd-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="170bd-135">See also</span></span>

- [<span data-ttu-id="170bd-136">Genelleştirme ve Yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="170bd-136">Globalization and Localization</span></span>](../../../docs/standard/globalization-localization/index.md)
- [<span data-ttu-id="170bd-137">Yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="170bd-137">Localization</span></span>](../../../docs/standard/globalization-localization/localization.md)
- [<span data-ttu-id="170bd-138">Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="170bd-138">Globalization</span></span>](../../../docs/standard/globalization-localization/globalization.md)
- [<span data-ttu-id="170bd-139">Masaüstü Uygulamalarındaki Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="170bd-139">Resources in Desktop Apps</span></span>](../../../docs/framework/resources/index.md)
