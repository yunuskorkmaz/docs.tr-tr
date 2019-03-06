---
title: 'Nasıl yapılır: Gölgeli Metin Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], shadow effects
- shadow effects in text [WPF]
- text [WPF], shadowed
ms.assetid: 6ab9c754-6001-4708-b479-5367f2fd1a35
ms.openlocfilehash: 4d200aa980e8f2e6d22291669dfb07db54a5f0c0
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57370689"
---
# <a name="how-to-create-text-with-a-shadow"></a><span data-ttu-id="6d6e2-102">Nasıl yapılır: Gölgeli Metin Oluşturma</span><span class="sxs-lookup"><span data-stu-id="6d6e2-102">How to: Create Text with a Shadow</span></span>
<span data-ttu-id="6d6e2-103">Bu bölümdeki örneklerde, bir gölge etkisi görüntülenen metin oluşturma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6d6e2-103">The examples in this section show how to create a shadow effect for displayed text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d6e2-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="6d6e2-104">Example</span></span>  
 <span data-ttu-id="6d6e2-105"><xref:System.Windows.Media.Effects.DropShadowEffect> Nesne gölge efektleri bırakma çeşitli oluşturmanıza imkan tanır [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] nesneleri.</span><span class="sxs-lookup"><span data-stu-id="6d6e2-105">The <xref:System.Windows.Media.Effects.DropShadowEffect> object allows you to create a variety of drop shadow effects for [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] objects.</span></span> <span data-ttu-id="6d6e2-106">Aşağıdaki örnek, metne uygulanacak gölge etkisi gösterir.</span><span class="sxs-lookup"><span data-stu-id="6d6e2-106">The following example shows a drop shadow effect applied to text.</span></span> <span data-ttu-id="6d6e2-107">Bu durumda, gölge gölge rengi Bulanıklaştırma anlamına gelir. bir yazılım gölge olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="6d6e2-107">In this case, the shadow is a soft shadow, which means the shadow color blurs.</span></span>  
  
 <span data-ttu-id="6d6e2-108">![Metin gölgesinin Yumuşaklık ile &#61; 0,25](./media/shadowtext01.jpg "ShadowText01")</span><span class="sxs-lookup"><span data-stu-id="6d6e2-108">![Text shadow with Softness &#61; 0.25](./media/shadowtext01.jpg "ShadowText01")</span></span>  
<span data-ttu-id="6d6e2-109">Yazılım gölgeli metin örneği</span><span class="sxs-lookup"><span data-stu-id="6d6e2-109">Example of text with a soft shadow</span></span>  
  
 <span data-ttu-id="6d6e2-110">Ayarlayarak Gölge genişliğini denetleyebilir <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="6d6e2-110">You can control the width of a shadow by setting the <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> property.</span></span> <span data-ttu-id="6d6e2-111">Değerini `4.0` 4 piksel Gölge genişliğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6d6e2-111">A value of `4.0` indicates a shadow width of 4 pixels.</span></span> <span data-ttu-id="6d6e2-112">Yumuşaklık denetleyebilir veya değiştirerek bir gölge Bulanıklığı <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="6d6e2-112">You can control the softness, or blur, of a shadow by modifying the <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> property.</span></span> <span data-ttu-id="6d6e2-113">Değerini `0.0` hiçbir Bulanıklaştırma gösterir.</span><span class="sxs-lookup"><span data-stu-id="6d6e2-113">A value of `0.0` indicates no blurring.</span></span> <span data-ttu-id="6d6e2-114">Aşağıdaki kod örneği, geçici bir gölge oluşturma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6d6e2-114">The following code example shows how to create a soft shadow.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet1)]  
  
> [!NOTE]
>  <span data-ttu-id="6d6e2-115">Bu gölge efektleri üzerinden geçmemektedir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] metin işleme zinciri.</span><span class="sxs-lookup"><span data-stu-id="6d6e2-115">These shadow effects do not go through the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] text rendering pipeline.</span></span> <span data-ttu-id="6d6e2-116">Sonuç olarak, ClearType bu etkileri kullanırken devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="6d6e2-116">As a result, ClearType is disabled when using these effects.</span></span>  
  
 <span data-ttu-id="6d6e2-117">Aşağıdaki örnek, metin için uygulanan sabit gölge etkisi gösterir.</span><span class="sxs-lookup"><span data-stu-id="6d6e2-117">The following example shows a hard drop shadow effect applied to text.</span></span> <span data-ttu-id="6d6e2-118">Bu durumda, gölge bulanık değildir.</span><span class="sxs-lookup"><span data-stu-id="6d6e2-118">In this case, the shadow is not blurred.</span></span>  
  
 <span data-ttu-id="6d6e2-119">![Metin gölgesinin Yumuşaklık ile &#61; 0](./media/shadowtext02.jpg "ShadowText02")</span><span class="sxs-lookup"><span data-stu-id="6d6e2-119">![Text shadow with Softness &#61; 0](./media/shadowtext02.jpg "ShadowText02")</span></span>  
<span data-ttu-id="6d6e2-120">Sabit gölgeli metin örneği</span><span class="sxs-lookup"><span data-stu-id="6d6e2-120">Example of text with a hard shadow</span></span>  
  
 <span data-ttu-id="6d6e2-121">Sabit bir gölge ayarlayarak oluşturabileceğiniz <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> özelliğini `0.0`, hiçbir Bulanıklaştırma kullanıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6d6e2-121">You can create a hard shadow by setting the <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> property to `0.0`, which indicates that no blurring is used.</span></span> <span data-ttu-id="6d6e2-122">Gölge yönünü değiştirerek denetleyebilirsiniz <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="6d6e2-122">You can control the direction of the shadow by modifying the <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> property.</span></span> <span data-ttu-id="6d6e2-123">Bu özelliğin yön değeri arasında bir dereceye ayarlayın `0` ve `360`.</span><span class="sxs-lookup"><span data-stu-id="6d6e2-123">Set the directional value of this property to a degree between `0` and `360`.</span></span> <span data-ttu-id="6d6e2-124">Tek yönlü değerlerini aşağıdaki çizimde <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> özellik ayarı.</span><span class="sxs-lookup"><span data-stu-id="6d6e2-124">The following illustration shows the directional values of the <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> property setting.</span></span>  
  
 <span data-ttu-id="6d6e2-125">![Gölgenin DropShadow derece ayarı](./media/shadowtext08.png "ShadowText08")</span><span class="sxs-lookup"><span data-stu-id="6d6e2-125">![DropShadow degree setting of shadow](./media/shadowtext08.png "ShadowText08")</span></span>  
<span data-ttu-id="6d6e2-126">DropShadow yönü diyagramı</span><span class="sxs-lookup"><span data-stu-id="6d6e2-126">DropShadow Direction diagram</span></span>  
  
 <span data-ttu-id="6d6e2-127">Aşağıdaki kod örneği, sabit bir gölge oluşturma işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6d6e2-127">The following code example shows how to create a hard shadow.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet2)]  
  
## <a name="using-a-blur-effect"></a><span data-ttu-id="6d6e2-128">Bulanıklaştırma efekt kullanma</span><span class="sxs-lookup"><span data-stu-id="6d6e2-128">Using a Blur Effect</span></span>  
 <span data-ttu-id="6d6e2-129">A <xref:System.Windows.Media.Effects.BlurBitmapEffect> metin nesnesi yerleştirilebilir bir gölge benzeri etkisi oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6d6e2-129">A <xref:System.Windows.Media.Effects.BlurBitmapEffect> can be used to create a shadow-like effect that can be placed behind a text object.</span></span> <span data-ttu-id="6d6e2-130">Metnin her yöne eşit olarak metne uygulanan bir bulanıklaştırma bit eşlem etkisi bulanıklaştırır.</span><span class="sxs-lookup"><span data-stu-id="6d6e2-130">A blur bitmap effect applied to text blurs the text evenly in all directions.</span></span>  
  
 <span data-ttu-id="6d6e2-131">Aşağıdaki örnek metni uygulanan bir bulanıklaştırma etkisini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6d6e2-131">The following example shows a blur effect applied to text.</span></span>  
  
 <span data-ttu-id="6d6e2-132">![Metin gölgesinin BlurBitmapEffect kullanarak](./media/shadowtext06.jpg "ShadowText06")</span><span class="sxs-lookup"><span data-stu-id="6d6e2-132">![Text shadow using a BlurBitmapEffect](./media/shadowtext06.jpg "ShadowText06")</span></span>  
<span data-ttu-id="6d6e2-133">Bulanıklaştırma etkisi olan metin örneği</span><span class="sxs-lookup"><span data-stu-id="6d6e2-133">Example of text with a blur effect</span></span>  
  
 <span data-ttu-id="6d6e2-134">Aşağıdaki kod örneği, Bulanıklaştırma efekti oluşturma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6d6e2-134">The following code example shows how to create a blur effect.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/BlurShadows.xaml#textshadowsnippet6)]  
  
## <a name="using-a-translate-transform"></a><span data-ttu-id="6d6e2-135">Çeviri dönüşümü kullanma</span><span class="sxs-lookup"><span data-stu-id="6d6e2-135">Using a Translate Transform</span></span>  
 <span data-ttu-id="6d6e2-136">A <xref:System.Windows.Media.TranslateTransform> metin nesnesi yerleştirilebilir bir gölge benzeri etkisi oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6d6e2-136">A <xref:System.Windows.Media.TranslateTransform> can be used to create a shadow-like effect that can be placed behind a text object.</span></span>  
  
 <span data-ttu-id="6d6e2-137">Aşağıdaki kod örneğinde bir <xref:System.Windows.Media.TranslateTransform> metin uzaklık.</span><span class="sxs-lookup"><span data-stu-id="6d6e2-137">The following code example uses a <xref:System.Windows.Media.TranslateTransform> to offset text.</span></span> <span data-ttu-id="6d6e2-138">Bu örnekte, bir gölge etkisi birincil metin aşağıdaki metni biraz uzaklık bir kopyasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6d6e2-138">In this example, a slightly offset copy of text below the primary text creates a shadow effect.</span></span>  
  
 <span data-ttu-id="6d6e2-139">![Metin gölgesinin TranslateTransform kullanan](./media/shadowtext07.jpg "ShadowText07")</span><span class="sxs-lookup"><span data-stu-id="6d6e2-139">![Text shadow using a TranslateTransform](./media/shadowtext07.jpg "ShadowText07")</span></span>  
<span data-ttu-id="6d6e2-140">Metin dönüştürme için gölge etkisi kullanarak örneği</span><span class="sxs-lookup"><span data-stu-id="6d6e2-140">Example of text using a transform for a shadow effect</span></span>  
  
 <span data-ttu-id="6d6e2-141">Aşağıdaki kod örneği, bir gölge etkisi dönüşümü oluşturma işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6d6e2-141">The following code example shows how to create a transform for a shadow effect.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/TransformShadows.xaml#textshadowsnippet7)]
