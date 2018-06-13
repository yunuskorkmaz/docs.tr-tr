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
ms.openlocfilehash: 531537013ab3bbfba278ca63e14155341eefc826
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544928"
---
# <a name="how-to-apply-transforms-to-text"></a><span data-ttu-id="26a96-102">Nasıl yapılır: Metne Dönüşüm Uygulama</span><span class="sxs-lookup"><span data-stu-id="26a96-102">How to: Apply Transforms to Text</span></span>
<span data-ttu-id="26a96-103">Dönüşümler uygulamanızdaki metnin görüntüsünü değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="26a96-103">Transforms can alter the display of text in your application.</span></span> <span data-ttu-id="26a96-104">Aşağıdaki örnekler farklı türdeki işleme dönüşümlerini metin görünümünü kullanın. bir <xref:System.Windows.Controls.TextBlock> denetim.</span><span class="sxs-lookup"><span data-stu-id="26a96-104">The following examples use different types of rendering transforms to affect the display of text in a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="26a96-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="26a96-105">Example</span></span>  
 <span data-ttu-id="26a96-106">Aşağıdaki örnekte, iki boyutlu x-y düzlem olarak belirtilen bir nokta döndürülen metin gösterir.</span><span class="sxs-lookup"><span data-stu-id="26a96-106">The following example shows text rotated about a specified point in the two-dimensional x-y plane.</span></span>  
  
 <span data-ttu-id="26a96-107">![RotateTransform kullanılarak döndürülen metin](../../../../docs/framework/wpf/advanced/media/transformedtext01.jpg "TransformedText01")</span><span class="sxs-lookup"><span data-stu-id="26a96-107">![Text rotated using a RotateTransform](../../../../docs/framework/wpf/advanced/media/transformedtext01.jpg "TransformedText01")</span></span>  
<span data-ttu-id="26a96-108">90 derece döndürülmüş metin örneği</span><span class="sxs-lookup"><span data-stu-id="26a96-108">Example of text rotated 90 degrees</span></span>  
  
 <span data-ttu-id="26a96-109">Aşağıdaki kod örneğinde bir <xref:System.Windows.Media.RotateTransform> metni döndürmek için.</span><span class="sxs-lookup"><span data-stu-id="26a96-109">The following code example uses a <xref:System.Windows.Media.RotateTransform> to rotate text.</span></span> <span data-ttu-id="26a96-110">Bir <xref:System.Windows.Media.RotateTransform.Angle%2A> değeri olarak 90 90 derece saat yönünde öğesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="26a96-110">An <xref:System.Windows.Media.RotateTransform.Angle%2A> value of 90 rotates the element 90 degrees clockwise.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample1)]  
  
 <span data-ttu-id="26a96-111">Aşağıdaki örnek, x ekseni boyunca % 150 ölçeklendirilmiş metin satırının ikinci ve üçüncü y ekseni boyunca % 150 ölçeklendirilmiş metin satırının gösterir.</span><span class="sxs-lookup"><span data-stu-id="26a96-111">The following example shows the second line of text scaled by 150% along the x-axis, and the third line of text scaled by 150% along the y-axis.</span></span>  
  
 <span data-ttu-id="26a96-112">![ScaleTransform kullanılarak ölçeklendirilen metin](../../../../docs/framework/wpf/advanced/media/transformedtext02.jpg "TransformedText02")</span><span class="sxs-lookup"><span data-stu-id="26a96-112">![Text scaled using a ScaleTransform](../../../../docs/framework/wpf/advanced/media/transformedtext02.jpg "TransformedText02")</span></span>  
<span data-ttu-id="26a96-113">Ölçeklendirilmiş metin örneği</span><span class="sxs-lookup"><span data-stu-id="26a96-113">Example of scaled text</span></span>  
  
 <span data-ttu-id="26a96-114">Aşağıdaki kod örneğinde bir <xref:System.Windows.Media.ScaleTransform> özgün boyutuna ölçek metinden için.</span><span class="sxs-lookup"><span data-stu-id="26a96-114">The following code example uses a <xref:System.Windows.Media.ScaleTransform> to scale text from its original size.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample2)]  
  
> [!NOTE]
>  <span data-ttu-id="26a96-115">Metin ölçeklendirme metnin yazı tipi boyutunu artırma ile aynı değil.</span><span class="sxs-lookup"><span data-stu-id="26a96-115">Scaling text is not the same as increasing the font size of text.</span></span> <span data-ttu-id="26a96-116">Yazı tipi boyutlarını farklı boyutlarda en iyi çözüm sunmak için diğer bağımsız olarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="26a96-116">Font sizes are calculated independently of each other in order to provide the best resolution at different sizes.</span></span> <span data-ttu-id="26a96-117">Ölçeklendirilmiş metin, diğer yandan, özgün boyutlu metin oranlarını korur.</span><span class="sxs-lookup"><span data-stu-id="26a96-117">Scaled text, on the other hand, preserves the proportions of the original-sized text.</span></span>  
  
 <span data-ttu-id="26a96-118">Aşağıdaki örnek eksenindeki eğri metni gösterir.</span><span class="sxs-lookup"><span data-stu-id="26a96-118">The following example shows text skewed along the x-axis.</span></span>  
  
 <span data-ttu-id="26a96-119">![SkewTransform kullanılarak eğri metin](../../../../docs/framework/wpf/advanced/media/transformedtext03.jpg "TransformedText03")</span><span class="sxs-lookup"><span data-stu-id="26a96-119">![Text skewed using a SkewTransform](../../../../docs/framework/wpf/advanced/media/transformedtext03.jpg "TransformedText03")</span></span>  
<span data-ttu-id="26a96-120">Çarpık metin örneği</span><span class="sxs-lookup"><span data-stu-id="26a96-120">Example of skewed text</span></span>  
  
 <span data-ttu-id="26a96-121">Aşağıdaki kod örneğinde bir <xref:System.Windows.Media.SkewTransform> metin eğme için.</span><span class="sxs-lookup"><span data-stu-id="26a96-121">The following code example uses a <xref:System.Windows.Media.SkewTransform> to skew text.</span></span> <span data-ttu-id="26a96-122">Bir eğme olarak da bilinen eğme, koordinat Tekdüzen olmayan bir biçimde uzatan bir dönüşümü gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="26a96-122">A skew, also known as a shear, is a transformation that stretches the coordinate space in a non-uniform manner.</span></span> <span data-ttu-id="26a96-123">Bu örnekte, iki metin çarpık-30 ° ve 30 ° x koordinatını boyunca dizelerdir.</span><span class="sxs-lookup"><span data-stu-id="26a96-123">In this example, the two text strings are skewed -30° and 30° along the x-coordinate.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample3)]  
  
 <span data-ttu-id="26a96-124">Aşağıdaki örnek çevrilmiş veya taşınmış, x ve y ekseni metin gösterir.</span><span class="sxs-lookup"><span data-stu-id="26a96-124">The following example shows text translated, or moved, along the x- and y-axis.</span></span>  
  
 <span data-ttu-id="26a96-125">![TranslateTransform kullanan metin uzaklığı](../../../../docs/framework/wpf/advanced/media/transformedtext04.jpg "TransformedText04")</span><span class="sxs-lookup"><span data-stu-id="26a96-125">![Text offset using a TranslateTransform](../../../../docs/framework/wpf/advanced/media/transformedtext04.jpg "TransformedText04")</span></span>  
<span data-ttu-id="26a96-126">Çevrilmiş metin örneği</span><span class="sxs-lookup"><span data-stu-id="26a96-126">Example of translated text</span></span>  
  
 <span data-ttu-id="26a96-127">Aşağıdaki kod örneğinde bir <xref:System.Windows.Media.TranslateTransform> metni dengelemek için.</span><span class="sxs-lookup"><span data-stu-id="26a96-127">The following code example uses a <xref:System.Windows.Media.TranslateTransform> to offset text.</span></span> <span data-ttu-id="26a96-128">Bu örnekte, bir gölge etkisi birincil metin altındaki metin biraz uzaklık bir kopyasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="26a96-128">In this example, a slightly offset copy of text below the primary text creates a shadow effect.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample4)]  
  
> [!NOTE]
>  <span data-ttu-id="26a96-129"><xref:System.Windows.Media.Effects.DropShadowBitmapEffect> Gölge efektleri sağlayan zengin bir özellikler kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="26a96-129">The <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> provides a rich set of features for providing shadow effects.</span></span> <span data-ttu-id="26a96-130">Daha fazla bilgi için bkz: [gölgeli metin oluşturma](../../../../docs/framework/wpf/advanced/how-to-create-text-with-a-shadow.md).</span><span class="sxs-lookup"><span data-stu-id="26a96-130">For more information, see [Create Text with a Shadow](../../../../docs/framework/wpf/advanced/how-to-create-text-with-a-shadow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26a96-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="26a96-131">See Also</span></span>  
 [<span data-ttu-id="26a96-132">Metne Animasyon Uygulama</span><span class="sxs-lookup"><span data-stu-id="26a96-132">Apply Animations to Text</span></span>](../../../../docs/framework/wpf/advanced/how-to-apply-animations-to-text.md)
