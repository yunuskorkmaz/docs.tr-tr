---
description: 'Daha fazla bilgi edinin: Yerelleştirilebilirlik incelemesi'
title: Yerelleştirilebilirlik İncelemesi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- world-ready applications, localizability
- application development [.NET], localization
- localizability [.NET]
- international applications [.NET], localizability
- globalization [.NET], localizability
- culture, localizability
- localization [.NET], localizability
- global applications, localizability
- localizing resources
ms.assetid: 3aee2fbb-de47-4e37-8fe4-ddebb9719247
ms.openlocfilehash: 5228cf7ff2615f14439dfeffd0d9b511be274dae
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99675773"
---
# <a name="localizability-review"></a><span data-ttu-id="0321d-103">Yerelleştirilebilirlik incelemesi</span><span class="sxs-lookup"><span data-stu-id="0321d-103">Localizability review</span></span>

<span data-ttu-id="0321d-104">Yerelleştirilebilirlik incelemesi, dünya çapında bir uygulama geliştirmenin bir ara adımıdır.</span><span class="sxs-lookup"><span data-stu-id="0321d-104">The localizability review is an intermediate step in the development of a world-ready application.</span></span> <span data-ttu-id="0321d-105">Bir Genelleştirilmiş uygulamasının yerelleştirme için hazırlandığını doğrular ve herhangi bir kodu veya özel işleme gerektiren Kullanıcı arabiriminin herhangi bir yönlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0321d-105">It verifies that a globalized application is ready for localization and identifies any code or any aspects of the user interface that require special handling.</span></span> <span data-ttu-id="0321d-106">Bu adım Ayrıca yerelleştirme işleminin uygulamanıza işlevsel hatalar sunmaz.</span><span class="sxs-lookup"><span data-stu-id="0321d-106">This step also helps ensure that the localization process will not introduce any functional defects into your application.</span></span> <span data-ttu-id="0321d-107">Yerelleştirilebilirlik incelemesi tarafından oluşturulan tüm sorunlar ele geçirilmemişse, uygulamanız yerelleştirme için hazırlayın.</span><span class="sxs-lookup"><span data-stu-id="0321d-107">When all the issues raised by the localizability review have been addressed, your application is ready for localization.</span></span> <span data-ttu-id="0321d-108">Yerelleştirilebilirlik incelemesi tam ise, yerelleştirme işlemi sırasında herhangi bir kaynak kodunu değiştirmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="0321d-108">If the localizability review is thorough, you should not have to modify any source code during the localization process.</span></span>

<span data-ttu-id="0321d-109">Yerelleştirilebilirlik incelemesi, aşağıdaki üç denetimi içerir:</span><span class="sxs-lookup"><span data-stu-id="0321d-109">The localizability review consists of the following three checks:</span></span>

- [<span data-ttu-id="0321d-110">Genelleştirme önerileri uygulandı mi?</span><span class="sxs-lookup"><span data-stu-id="0321d-110">Are the globalization recommendations implemented?</span></span>](#global)

- [<span data-ttu-id="0321d-111">Kültüre duyarlı özellikler doğru şekilde işlensin mi?</span><span class="sxs-lookup"><span data-stu-id="0321d-111">Are culture-sensitive features handled correctly?</span></span>](#culture)

- [<span data-ttu-id="0321d-112">Uygulamanızı Uluslararası verilerle test etmeniz mi gerekiyor?</span><span class="sxs-lookup"><span data-stu-id="0321d-112">Have you tested your application with international data?</span></span>](#test)

<a name="global"></a>

## <a name="implement-globalization-recommendations"></a><span data-ttu-id="0321d-113">Genelleştirme önerilerini Uygula</span><span class="sxs-lookup"><span data-stu-id="0321d-113">Implement globalization recommendations</span></span>

<span data-ttu-id="0321d-114">Uygulamanızı aklına göre tasarlanıp geliştirip geliştirdiyseniz ve [Genelleştirme](globalization.md) makalesinde açıklanan önerileri izlediyseniz, Yerelleştirilebilirlik incelemesi büyük ölçüde kalite güvencesi geçişine sahip olur.</span><span class="sxs-lookup"><span data-stu-id="0321d-114">If you have designed and developed your application with localization in mind, and if you have followed the recommendations discussed in the [Globalization](globalization.md) article, the localizability review will largely be a quality assurance pass.</span></span> <span data-ttu-id="0321d-115">Aksi takdirde, bu aşamada [Genelleştirme](globalization.md) önerilerini gözden geçirmeniz ve uygulamanız ve kaynak koddaki yerelleştirmeyi önleyen hataları çözmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0321d-115">Otherwise, during this stage you should review and implement the recommendations for [globalization](globalization.md) and fix the errors in source code that prevent localization.</span></span>

<a name="culture"></a>

## <a name="handle-culture-sensitive-features"></a><span data-ttu-id="0321d-116">Kültüre duyarlı özellikleri işleme</span><span class="sxs-lookup"><span data-stu-id="0321d-116">Handle culture-sensitive features</span></span>

<span data-ttu-id="0321d-117">.NET, kültüre göre farklılık gösteren çeşitli alanlarda programlama desteği sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="0321d-117">.NET does not provide programmatic support in a number of areas that vary widely by culture.</span></span> <span data-ttu-id="0321d-118">Çoğu durumda, aşağıdaki gibi özellik alanlarının işlenmesi için özel kod yazmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="0321d-118">In most cases, you have to write custom code to handle feature areas like the following:</span></span>

- <span data-ttu-id="0321d-119">Adresler</span><span class="sxs-lookup"><span data-stu-id="0321d-119">Addresses</span></span>

- <span data-ttu-id="0321d-120">Telefon numaraları</span><span class="sxs-lookup"><span data-stu-id="0321d-120">Telephone numbers</span></span>

- <span data-ttu-id="0321d-121">Kağıt boyutları</span><span class="sxs-lookup"><span data-stu-id="0321d-121">Paper sizes</span></span>

- <span data-ttu-id="0321d-122">Uzunluk, ağırlık, alan, birim ve sıcaklıklar için kullanılan ölçü birimleri</span><span class="sxs-lookup"><span data-stu-id="0321d-122">Units of measure used for lengths, weights, area, volume, and temperatures</span></span>

   <span data-ttu-id="0321d-123">.NET, ölçü birimleri arasında dönüştürme için yerleşik destek sunmasa da, <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> Aşağıdaki örnekte gösterildiği gibi belirli bir ülkenin veya bölgenin ölçüm sistemini kullanıp kullanmadığını anlamak için özelliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0321d-123">Although .NET does not offer built-in support for converting between units of measure, you can use the <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> property to determine whether a particular country or region uses the metric system, as the following example illustrates.</span></span>

   [!code-csharp[Conceptual.Localizability#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.localizability/cs/ismetric1.cs#1)]
   [!code-vb[Conceptual.Localizability#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.localizability/vb/ismetric1.vb#1)]

<a name="test"></a>

## <a name="test-your-application"></a><span data-ttu-id="0321d-124">Uygulamanızı test etme</span><span class="sxs-lookup"><span data-stu-id="0321d-124">Test your application</span></span>

<span data-ttu-id="0321d-125">Uygulamanızı yerelleştirebilmeniz için, işletim sisteminin Uluslararası sürümlerindeki Uluslararası verileri kullanarak test etmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="0321d-125">Before you localize your application, you should test it by using international data on international versions of the operating system.</span></span> <span data-ttu-id="0321d-126">Bu noktada Kullanıcı arabiriminin büyük bir çoğunluğu yerelleştirilemez, ancak aşağıdaki gibi sorunları tespit edebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0321d-126">Although most of the user interface will not be localized at this point, you will be able to detect problems such as the following:</span></span>

- <span data-ttu-id="0321d-127">İşletim sistemi sürümlerinde doğru şekilde seri durumdan çıkarmayan serileştirilmiş veriler.</span><span class="sxs-lookup"><span data-stu-id="0321d-127">Serialized data that does not deserialize correctly across operating system versions.</span></span>

- <span data-ttu-id="0321d-128">Geçerli kültürün kurallarını yansıtmayan sayısal veriler.</span><span class="sxs-lookup"><span data-stu-id="0321d-128">Numeric data that does not reflect the conventions of the current culture.</span></span> <span data-ttu-id="0321d-129">Örneğin, sayılar yanlış Grup ayırıcılar, Ondalık ayırıcılar veya para birimi sembolleri ile görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="0321d-129">For example, numbers may be displayed with inaccurate group separators, decimal separators, or currency symbols.</span></span>

- <span data-ttu-id="0321d-130">Geçerli kültürün kurallarını yansıtmayan tarih ve saat verileri.</span><span class="sxs-lookup"><span data-stu-id="0321d-130">Date and time data that does not reflect the conventions of the current culture.</span></span> <span data-ttu-id="0321d-131">Örneğin, ayı ve günü temsil eden sayılar yanlış sırada görünebilir, tarih ayırıcıları yanlış olabilir veya saat dilimi bilgisi yanlış olabilir.</span><span class="sxs-lookup"><span data-stu-id="0321d-131">For example, numbers that represent the month and day may appear in the wrong order, date separators may be incorrect, or time zone information may be incorrect.</span></span>

- <span data-ttu-id="0321d-132">Uygulamanız için bir varsayılan kültür belirlemei olmadığınızdan, bulunamayan kaynaklar.</span><span class="sxs-lookup"><span data-stu-id="0321d-132">Resources that cannot be found because you have not identified a default culture for your application.</span></span>

- <span data-ttu-id="0321d-133">Belirli kültür için olağan dışı bir düzende görüntülenen dizeler.</span><span class="sxs-lookup"><span data-stu-id="0321d-133">Strings that are displayed in an unusual order for the specific culture.</span></span>

- <span data-ttu-id="0321d-134">Beklenmeyen sonuçlar döndüren eşitlik için dize karşılaştırmaları veya karşılaştırmalar.</span><span class="sxs-lookup"><span data-stu-id="0321d-134">String comparisons or comparisons for equality that return unexpected results.</span></span>

<span data-ttu-id="0321d-135">Uygulamanızı geliştirirken Genelleştirme önerilerini izlediyseniz, kültüre duyarlı özellikler doğru şekilde işlenirse ve test sırasında bulunan yerelleştirme sorunlarını tanımladıktan ve ele alırsanız, sonraki adıma, [yerelleştirmeye](localization.md)devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0321d-135">If you've followed the globalization recommendations when developing your application, handled culture-sensitive features correctly, and identified and addressed the localization issues that arose during testing, you can proceed to the next step, [Localization](localization.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0321d-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0321d-136">See also</span></span>

- [<span data-ttu-id="0321d-137">Genelleştirme ve yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="0321d-137">Globalization and Localization</span></span>](index.md)
- [<span data-ttu-id="0321d-138">Yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="0321d-138">Localization</span></span>](localization.md)
- [<span data-ttu-id="0321d-139">Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="0321d-139">Globalization</span></span>](globalization.md)
- [<span data-ttu-id="0321d-140">Masaüstü uygulamalarındaki kaynaklar</span><span class="sxs-lookup"><span data-stu-id="0321d-140">Resources in Desktop Apps</span></span>](../../framework/resources/index.md)
