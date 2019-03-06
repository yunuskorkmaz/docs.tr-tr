---
title: 'Nasıl yapılır: Metne Dönüşüm Uygulama'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], rotated text
- typography [WPF], scaled text
- skewed text [WPF]
- typography [WPF], translated text
- typography [WPF], shadowed text
- rotated text [WPF]
- translated text [WPF]
- shadowed text [WPF]
- transforms in text [WPF]
- typography [WPF], transforms
- scaled text [WPF]
- typography [WPF], skewed text
ms.assetid: 0d61678a-4185-4f2a-85c6-c1d020f96fa0
ms.openlocfilehash: fd86293c539bf58ac93894e0b879dddb984825e1
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378957"
---
# <a name="how-to-apply-transforms-to-text"></a><span data-ttu-id="3e6c6-102">Nasıl yapılır: Metne Dönüşüm Uygulama</span><span class="sxs-lookup"><span data-stu-id="3e6c6-102">How to: Apply Transforms to Text</span></span>
<span data-ttu-id="3e6c6-103">Dönüşümler uygulamanızda metin görünümünü değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e6c6-103">Transforms can alter the display of text in your application.</span></span> <span data-ttu-id="3e6c6-104">Aşağıdaki örnekler işleme dönüşümleri farklı türde metin görünümünü kullanın. bir <xref:System.Windows.Controls.TextBlock> denetimi.</span><span class="sxs-lookup"><span data-stu-id="3e6c6-104">The following examples use different types of rendering transforms to affect the display of text in a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e6c6-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="3e6c6-105">Example</span></span>  
 <span data-ttu-id="3e6c6-106">Aşağıdaki örnek, iki boyutlu x-y düzlemleriyle içinde belirtilen bir noktadan döndürülen metni gösterir.</span><span class="sxs-lookup"><span data-stu-id="3e6c6-106">The following example shows text rotated about a specified point in the two-dimensional x-y plane.</span></span>  
  
 <span data-ttu-id="3e6c6-107">![RotateTransform kullanılarak döndürülen metin](./media/transformedtext01.jpg "TransformedText01")</span><span class="sxs-lookup"><span data-stu-id="3e6c6-107">![Text rotated using a RotateTransform](./media/transformedtext01.jpg "TransformedText01")</span></span>  
<span data-ttu-id="3e6c6-108">90 derece döndürülmüş metin örneği</span><span class="sxs-lookup"><span data-stu-id="3e6c6-108">Example of text rotated 90 degrees</span></span>  
  
 <span data-ttu-id="3e6c6-109">Aşağıdaki kod örneğinde bir <xref:System.Windows.Media.RotateTransform> metni döndürmek için.</span><span class="sxs-lookup"><span data-stu-id="3e6c6-109">The following code example uses a <xref:System.Windows.Media.RotateTransform> to rotate text.</span></span> <span data-ttu-id="3e6c6-110">Bir <xref:System.Windows.Media.RotateTransform.Angle%2A> 90 değerini 90 derece saat yönünde öğeyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="3e6c6-110">An <xref:System.Windows.Media.RotateTransform.Angle%2A> value of 90 rotates the element 90 degrees clockwise.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample1)]  
  
 <span data-ttu-id="3e6c6-111">Aşağıdaki örnek, % 150 x ekseni boyunca ölçeği metnin ikinci satırı ve y ekseni boyunca % 150 ölçeklendirilmiş metin üçüncü satır gösterir.</span><span class="sxs-lookup"><span data-stu-id="3e6c6-111">The following example shows the second line of text scaled by 150% along the x-axis, and the third line of text scaled by 150% along the y-axis.</span></span>  
  
 <span data-ttu-id="3e6c6-112">![ScaleTransform kullanılarak ölçeklendirilen metin](./media/transformedtext02.jpg "TransformedText02")</span><span class="sxs-lookup"><span data-stu-id="3e6c6-112">![Text scaled using a ScaleTransform](./media/transformedtext02.jpg "TransformedText02")</span></span>  
<span data-ttu-id="3e6c6-113">Ölçeklendirilmiş metin örneği</span><span class="sxs-lookup"><span data-stu-id="3e6c6-113">Example of scaled text</span></span>  
  
 <span data-ttu-id="3e6c6-114">Aşağıdaki kod örneğinde bir <xref:System.Windows.Media.ScaleTransform> özgün boyutuna ölçek metni için.</span><span class="sxs-lookup"><span data-stu-id="3e6c6-114">The following code example uses a <xref:System.Windows.Media.ScaleTransform> to scale text from its original size.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample2)]  
  
> [!NOTE]
>  <span data-ttu-id="3e6c6-115">Metin ölçeklendirme metnin yazı tipi boyutunu artırma ile aynı değil.</span><span class="sxs-lookup"><span data-stu-id="3e6c6-115">Scaling text is not the same as increasing the font size of text.</span></span> <span data-ttu-id="3e6c6-116">Yazı tipi boyutlarını birbirinden farklı boyutlarda en iyi çözüm sağlamak için hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="3e6c6-116">Font sizes are calculated independently of each other in order to provide the best resolution at different sizes.</span></span> <span data-ttu-id="3e6c6-117">Ölçeklendirilmiş metin, diğer taraftan, özgün boyutunda metin oranlarını korur.</span><span class="sxs-lookup"><span data-stu-id="3e6c6-117">Scaled text, on the other hand, preserves the proportions of the original-sized text.</span></span>  
  
 <span data-ttu-id="3e6c6-118">Aşağıdaki örnek x ekseni boyunca Eğilmiş metin gösterir.</span><span class="sxs-lookup"><span data-stu-id="3e6c6-118">The following example shows text skewed along the x-axis.</span></span>  
  
 <span data-ttu-id="3e6c6-119">![SkewTransform kullanılarak Eğilmiş metin](./media/transformedtext03.jpg "TransformedText03")</span><span class="sxs-lookup"><span data-stu-id="3e6c6-119">![Text skewed using a SkewTransform](./media/transformedtext03.jpg "TransformedText03")</span></span>  
<span data-ttu-id="3e6c6-120">Eğilmiş metin örneği</span><span class="sxs-lookup"><span data-stu-id="3e6c6-120">Example of skewed text</span></span>  
  
 <span data-ttu-id="3e6c6-121">Aşağıdaki kod örneğinde bir <xref:System.Windows.Media.SkewTransform> metin eğriltmek için.</span><span class="sxs-lookup"><span data-stu-id="3e6c6-121">The following code example uses a <xref:System.Windows.Media.SkewTransform> to skew text.</span></span> <span data-ttu-id="3e6c6-122">Bir eğme yamultma olarak da bilinen bir koordinat bir Tekdüzen olmayan şekilde uzatır bir dönüşümdür.</span><span class="sxs-lookup"><span data-stu-id="3e6c6-122">A skew, also known as a shear, is a transformation that stretches the coordinate space in a non-uniform manner.</span></span> <span data-ttu-id="3e6c6-123">Bu örnekte, iki metin dengesiz-30 ° ve x koordinatını boyunca 30 ° dizelerdir.</span><span class="sxs-lookup"><span data-stu-id="3e6c6-123">In this example, the two text strings are skewed -30° and 30° along the x-coordinate.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample3)]  
  
 <span data-ttu-id="3e6c6-124">Aşağıdaki örnek, çevrilmiş veya taşınmış, x ve y ekseni metni gösterir.</span><span class="sxs-lookup"><span data-stu-id="3e6c6-124">The following example shows text translated, or moved, along the x- and y-axis.</span></span>  
  
 <span data-ttu-id="3e6c6-125">![Metin TranslateTransform kullanan uzaklığı](./media/transformedtext04.jpg "TransformedText04")</span><span class="sxs-lookup"><span data-stu-id="3e6c6-125">![Text offset using a TranslateTransform](./media/transformedtext04.jpg "TransformedText04")</span></span>  
<span data-ttu-id="3e6c6-126">Çevrilmiş metin örneği</span><span class="sxs-lookup"><span data-stu-id="3e6c6-126">Example of translated text</span></span>  
  
 <span data-ttu-id="3e6c6-127">Aşağıdaki kod örneğinde bir <xref:System.Windows.Media.TranslateTransform> metin uzaklık.</span><span class="sxs-lookup"><span data-stu-id="3e6c6-127">The following code example uses a <xref:System.Windows.Media.TranslateTransform> to offset text.</span></span> <span data-ttu-id="3e6c6-128">Bu örnekte, bir gölge etkisi birincil metin aşağıdaki metni biraz uzaklık bir kopyasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3e6c6-128">In this example, a slightly offset copy of text below the primary text creates a shadow effect.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample4](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample4)]  
  
> [!NOTE]
>  <span data-ttu-id="3e6c6-129"><xref:System.Windows.Media.Effects.DropShadowBitmapEffect> Gölge efektleri sağlayan zengin bir özellikler kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="3e6c6-129">The <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> provides a rich set of features for providing shadow effects.</span></span> <span data-ttu-id="3e6c6-130">Daha fazla bilgi için [gölgeli metin oluşturma](how-to-create-text-with-a-shadow.md).</span><span class="sxs-lookup"><span data-stu-id="3e6c6-130">For more information, see [Create Text with a Shadow](how-to-create-text-with-a-shadow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e6c6-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3e6c6-131">See also</span></span>
- [<span data-ttu-id="3e6c6-132">Metne Animasyon Uygulama</span><span class="sxs-lookup"><span data-stu-id="3e6c6-132">Apply Animations to Text</span></span>](how-to-apply-animations-to-text.md)
