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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73120856"
---
# <a name="localizability-review"></a><span data-ttu-id="d8796-102">Yerelleştirilebilirlik incelemesi</span><span class="sxs-lookup"><span data-stu-id="d8796-102">Localizability review</span></span>

<span data-ttu-id="d8796-103">Yerelleştirilebilirlik incelemesi, dünyaya hazır bir uygulamanın geliştirilmesinde ara adımdır.</span><span class="sxs-lookup"><span data-stu-id="d8796-103">The localizability review is an intermediate step in the development of a world-ready application.</span></span> <span data-ttu-id="d8796-104">Küreselleştirilmiş bir uygulamanın yerelleştirme için hazır olduğunu doğrular ve kullanıcı arabiriminin özel işleme gerektiren herhangi bir kodu veya herhangi bir yönünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d8796-104">It verifies that a globalized application is ready for localization and identifies any code or any aspects of the user interface that require special handling.</span></span> <span data-ttu-id="d8796-105">Bu adım, yerelleştirme işleminin uygulamanıza işlevsel hatalar getirmemesini de sağlamaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="d8796-105">This step also helps ensure that the localization process will not introduce any functional defects into your application.</span></span> <span data-ttu-id="d8796-106">Yerelleştirilebilirlik incelemesi tarafından ortaya atılan tüm sorunlar ele alındığunda, başvurunuz yerelleştirme için hazırdır.</span><span class="sxs-lookup"><span data-stu-id="d8796-106">When all the issues raised by the localizability review have been addressed, your application is ready for localization.</span></span> <span data-ttu-id="d8796-107">Yerelleştirilebilirlik incelemesi kapsamlıysa, yerelleştirme işlemi sırasında herhangi bir kaynak kodu değiştirmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="d8796-107">If the localizability review is thorough, you should not have to modify any source code during the localization process.</span></span>

<span data-ttu-id="d8796-108">Yerelleştirilebilirlik incelemesi aşağıdaki üç denetimden oluşur:</span><span class="sxs-lookup"><span data-stu-id="d8796-108">The localizability review consists of the following three checks:</span></span>

- [<span data-ttu-id="d8796-109">Küreselleşme önerileri uygulanıyor mu?</span><span class="sxs-lookup"><span data-stu-id="d8796-109">Are the globalization recommendations implemented?</span></span>](#global)

- [<span data-ttu-id="d8796-110">Kültüre duyarlı özellikler doğru işlenir mi?</span><span class="sxs-lookup"><span data-stu-id="d8796-110">Are culture-sensitive features handled correctly?</span></span>](#culture)

- [<span data-ttu-id="d8796-111">Başvurunuzu uluslararası verilerle test ettiniz mi?</span><span class="sxs-lookup"><span data-stu-id="d8796-111">Have you tested your application with international data?</span></span>](#test)

<a name="global"></a>
## <a name="implement-globalization-recommendations"></a><span data-ttu-id="d8796-112">Küreselleşme önerilerini uygulama</span><span class="sxs-lookup"><span data-stu-id="d8796-112">Implement globalization recommendations</span></span>

<span data-ttu-id="d8796-113">Uygulamanızı yerelleştirme yi göz önünde bulundurarak tasarladıysanız ve geliştirdiyseniz ve [Küreselleşme](../../../docs/standard/globalization-localization/globalization.md) makalesinde tartışılan tavsiyelere uyduysanız, yerelleştirilebilirlik incelemesi büyük ölçüde bir kalite güvencesi geçişi olacaktır.</span><span class="sxs-lookup"><span data-stu-id="d8796-113">If you have designed and developed your application with localization in mind, and if you have followed the recommendations discussed in the [Globalization](../../../docs/standard/globalization-localization/globalization.md) article, the localizability review will largely be a quality assurance pass.</span></span> <span data-ttu-id="d8796-114">Aksi takdirde, bu [aşamada, küreselleşme](../../../docs/standard/globalization-localization/globalization.md) için önerileri gözden geçirmeli ve uygulamalı ve yerelleştirmeyi engelleyen kaynak kodundaki hataları düzeltmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="d8796-114">Otherwise, during this stage you should review and implement the recommendations for [globalization](../../../docs/standard/globalization-localization/globalization.md) and fix the errors in source code that prevent localization.</span></span>

<a name="culture"></a>
## <a name="handle-culture-sensitive-features"></a><span data-ttu-id="d8796-115">Kültüre duyarlı özellikleri işleme</span><span class="sxs-lookup"><span data-stu-id="d8796-115">Handle culture-sensitive features</span></span>

<span data-ttu-id="d8796-116">.NET, kültüre göre büyük farklılıklar gösteren alanlarda programlı destek sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="d8796-116">.NET does not provide programmatic support in a number of areas that vary widely by culture.</span></span> <span data-ttu-id="d8796-117">Çoğu durumda, aşağıdaki gibi özellik alanlarını işlemek için özel kod yazmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="d8796-117">In most cases, you have to write custom code to handle feature areas like the following:</span></span>

- <span data-ttu-id="d8796-118">Adresler</span><span class="sxs-lookup"><span data-stu-id="d8796-118">Addresses</span></span>

- <span data-ttu-id="d8796-119">Telefon numaraları</span><span class="sxs-lookup"><span data-stu-id="d8796-119">Telephone numbers</span></span>

- <span data-ttu-id="d8796-120">Kağıt boyutları</span><span class="sxs-lookup"><span data-stu-id="d8796-120">Paper sizes</span></span>

- <span data-ttu-id="d8796-121">Uzunluklar, ağırlıklar, alan, hacim ve sıcaklıklar için kullanılan ölçü birimleri</span><span class="sxs-lookup"><span data-stu-id="d8796-121">Units of measure used for lengths, weights, area, volume, and temperatures</span></span>

   <span data-ttu-id="d8796-122">.NET, ölçü birimleri arasında dönüştürme için yerleşik destek sunmasa da, aşağıdaki örnekte gösterildiği gibi, belirli bir ülkenin veya bölgenin metrik sistemi kullanıp kullanmadığını belirlemek için <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> özelliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8796-122">Although .NET does not offer built-in support for converting between units of measure, you can use the <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> property to determine whether a particular country or region uses the metric system, as the following example illustrates.</span></span>

   [!code-csharp[Conceptual.Localizability#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.localizability/cs/ismetric1.cs#1)]
   [!code-vb[Conceptual.Localizability#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.localizability/vb/ismetric1.vb#1)]

<a name="test"></a>
## <a name="test-your-application"></a><span data-ttu-id="d8796-123">Başvurunuzu test edin</span><span class="sxs-lookup"><span data-stu-id="d8796-123">Test your application</span></span>

<span data-ttu-id="d8796-124">Uygulamanızı yerelleştirmeden önce, işletim sisteminin uluslararası sürümlerinde uluslararası verileri kullanarak uygulamayı test etmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="d8796-124">Before you localize your application, you should test it by using international data on international versions of the operating system.</span></span> <span data-ttu-id="d8796-125">Kullanıcı arabiriminin çoğu bu noktada yerelleştirilmese de, aşağıdaki gibi sorunları algılayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d8796-125">Although most of the user interface will not be localized at this point, you will be able to detect problems such as the following:</span></span>

- <span data-ttu-id="d8796-126">İşletim sistemi sürümlerinde doğru şekilde deserialize olmayan serileştirilmiş veriler.</span><span class="sxs-lookup"><span data-stu-id="d8796-126">Serialized data that does not deserialize correctly across operating system versions.</span></span>

- <span data-ttu-id="d8796-127">Geçerli kültürün kurallarını yansıtmayan sayısal veriler.</span><span class="sxs-lookup"><span data-stu-id="d8796-127">Numeric data that does not reflect the conventions of the current culture.</span></span> <span data-ttu-id="d8796-128">Örneğin, sayılar yanlış grup ayırıcıları, ondalık ayırıcılar veya para birimi sembolleri ile görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="d8796-128">For example, numbers may be displayed with inaccurate group separators, decimal separators, or currency symbols.</span></span>

- <span data-ttu-id="d8796-129">Geçerli kültürün kurallarını yansıtmayan tarih ve saat verileri.</span><span class="sxs-lookup"><span data-stu-id="d8796-129">Date and time data that does not reflect the conventions of the current culture.</span></span> <span data-ttu-id="d8796-130">Örneğin, ay ve günü temsil eden sayılar yanlış sırada görünebilir, tarih ayırıcıları yanlış olabilir veya saat dilimi bilgileri yanlış olabilir.</span><span class="sxs-lookup"><span data-stu-id="d8796-130">For example, numbers that represent the month and day may appear in the wrong order, date separators may be incorrect, or time zone information may be incorrect.</span></span>

- <span data-ttu-id="d8796-131">Uygulamanız için varsayılan bir kültür tanımlamadığınız için bulunamayan kaynaklar.</span><span class="sxs-lookup"><span data-stu-id="d8796-131">Resources that cannot be found because you have not identified a default culture for your application.</span></span>

- <span data-ttu-id="d8796-132">Belirli bir kültür için alışılmadık bir sırada görüntülenen dizeleri.</span><span class="sxs-lookup"><span data-stu-id="d8796-132">Strings that are displayed in an unusual order for the specific culture.</span></span>

- <span data-ttu-id="d8796-133">Beklenmeyen sonuçlar döndüren eşitlik için dize karşılaştırmaları veya karşılaştırmalar.</span><span class="sxs-lookup"><span data-stu-id="d8796-133">String comparisons or comparisons for equality that return unexpected results.</span></span>

<span data-ttu-id="d8796-134">Uygulamanızı geliştirirken küreselleşme önerilerini izlediyseniz, kültüre duyarlı özellikleri doğru şekilde ele aldıysanız ve test sırasında ortaya çıkan yerelleştirme sorunlarını tespit edip ele aldıysanız, bir sonraki adımolan [Yerelleştirme'ye](../../../docs/standard/globalization-localization/localization.md)geçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8796-134">If you've followed the globalization recommendations when developing your application, handled culture-sensitive features correctly, and identified and addressed the localization issues that arose during testing, you can proceed to the next step, [Localization](../../../docs/standard/globalization-localization/localization.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d8796-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8796-135">See also</span></span>

- [<span data-ttu-id="d8796-136">Genelleştirme ve Yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="d8796-136">Globalization and Localization</span></span>](../../../docs/standard/globalization-localization/index.md)
- [<span data-ttu-id="d8796-137">Yerelleştirme</span><span class="sxs-lookup"><span data-stu-id="d8796-137">Localization</span></span>](../../../docs/standard/globalization-localization/localization.md)
- [<span data-ttu-id="d8796-138">Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="d8796-138">Globalization</span></span>](../../../docs/standard/globalization-localization/globalization.md)
- [<span data-ttu-id="d8796-139">Masaüstü Uygulamalarında Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="d8796-139">Resources in Desktop Apps</span></span>](../../../docs/framework/resources/index.md)
