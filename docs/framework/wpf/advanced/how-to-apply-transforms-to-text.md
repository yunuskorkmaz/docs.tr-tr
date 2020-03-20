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
ms.openlocfilehash: 867f39e3df8493014d8601530e91310c3bbbeeb5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141620"
---
# <a name="how-to-apply-transforms-to-text"></a><span data-ttu-id="9c42d-102">Nasıl yapılır: Metne Dönüşüm Uygulama</span><span class="sxs-lookup"><span data-stu-id="9c42d-102">How to: Apply Transforms to Text</span></span>
<span data-ttu-id="9c42d-103">Dönüşümler, uygulamanızdaki metnin ekranını değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="9c42d-103">Transforms can alter the display of text in your application.</span></span> <span data-ttu-id="9c42d-104">Aşağıdaki örnekler, bir <xref:System.Windows.Controls.TextBlock> denetimdeki metnin görüntülenmesini etkilemek için farklı türde işleme dönüşümleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="9c42d-104">The following examples use different types of rendering transforms to affect the display of text in a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c42d-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="9c42d-105">Example</span></span>  
 <span data-ttu-id="9c42d-106">Aşağıdaki örnekte, iki boyutlu x-y düzleminde belirtilen bir nokta hakkında döndürülen metin gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9c42d-106">The following example shows text rotated about a specified point in the two-dimensional x-y plane.</span></span>  
  
 ![DöndürmeTransform kullanılarak döndürülen metin](./media/how-to-apply-transforms-to-text/text-rotated-ninety-degrees.jpg)  
  
 <span data-ttu-id="9c42d-108">Aşağıdaki kod örneği <xref:System.Windows.Media.RotateTransform> metni döndürmek için a kullanır.</span><span class="sxs-lookup"><span data-stu-id="9c42d-108">The following code example uses a <xref:System.Windows.Media.RotateTransform> to rotate text.</span></span> <span data-ttu-id="9c42d-109">90 <xref:System.Windows.Media.RotateTransform.Angle%2A> değeri, öğeyi saat yönünde 90 derece döndürür.</span><span class="sxs-lookup"><span data-stu-id="9c42d-109">An <xref:System.Windows.Media.RotateTransform.Angle%2A> value of 90 rotates the element 90 degrees clockwise.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample1)]  
  
 <span data-ttu-id="9c42d-110">Aşağıdaki örnek, x ekseni boyunca %150 ölçeklendirilen ikinci metin satırını ve y ekseni boyunca %150 ölçeklendirilen üçüncü metin satırını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9c42d-110">The following example shows the second line of text scaled by 150% along the x-axis, and the third line of text scaled by 150% along the y-axis.</span></span>  
  
 ![Bir ScaleTransform kullanılarak ölçeklendirilen metin](./media/how-to-apply-transforms-to-text/scaled-text-scaletransform.jpg)
  
 <span data-ttu-id="9c42d-112">Aşağıdaki kod örneği, <xref:System.Windows.Media.ScaleTransform> metni özgün boyutundan ölçeklendirmek için bir kod kullanır.</span><span class="sxs-lookup"><span data-stu-id="9c42d-112">The following code example uses a <xref:System.Windows.Media.ScaleTransform> to scale text from its original size.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample2)]  
  
> [!NOTE]
> <span data-ttu-id="9c42d-113">Metni ölçekleme, metnin yazı tipi boyutunu artırmakla aynı şey değildir.</span><span class="sxs-lookup"><span data-stu-id="9c42d-113">Scaling text is not the same as increasing the font size of text.</span></span> <span data-ttu-id="9c42d-114">Yazı tipi boyutları, farklı boyutlarda en iyi çözünürlüğü sağlamak için birbirinden bağımsız olarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="9c42d-114">Font sizes are calculated independently of each other in order to provide the best resolution at different sizes.</span></span> <span data-ttu-id="9c42d-115">Diğer taraftan, ölçeklenmiş metin orijinal boyutlu metnin oranlarını korur.</span><span class="sxs-lookup"><span data-stu-id="9c42d-115">Scaled text, on the other hand, preserves the proportions of the original-sized text.</span></span>  
  
 <span data-ttu-id="9c42d-116">Aşağıdaki örnek, x ekseni boyunca eğriltilen metni gösterir.</span><span class="sxs-lookup"><span data-stu-id="9c42d-116">The following example shows text skewed along the x-axis.</span></span>  
  
 ![SkewTransform kullanılarak eğriltilen metin](./media/how-to-apply-transforms-to-text/skewed-transformed-text.jpg)

 <span data-ttu-id="9c42d-118">Aşağıdaki kod örneği, <xref:System.Windows.Media.SkewTransform> metni eğriltmek için a kullanır.</span><span class="sxs-lookup"><span data-stu-id="9c42d-118">The following code example uses a <xref:System.Windows.Media.SkewTransform> to skew text.</span></span> <span data-ttu-id="9c42d-119">Bir eğrilik, aynı zamanda bir yama olarak bilinen, olmayan bir üniforma şekilde koordinat alanı uzanan bir dönüşümdür.</span><span class="sxs-lookup"><span data-stu-id="9c42d-119">A skew, also known as a shear, is a transformation that stretches the coordinate space in a non-uniform manner.</span></span> <span data-ttu-id="9c42d-120">Bu örnekte, iki metin dizeleri x-koordinatı boyunca -30° ve 30° şeklinde eğriltilir.</span><span class="sxs-lookup"><span data-stu-id="9c42d-120">In this example, the two text strings are skewed -30° and 30° along the x-coordinate.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample3)]  
  
 <span data-ttu-id="9c42d-121">Aşağıdaki örnekte, x- ve y ekseni boyunca çevrilen veya taşınan metin gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9c42d-121">The following example shows text translated, or moved, along the x- and y-axis.</span></span>  
  
 ![TranslateTransform kullanarak metin mahsup](./media/how-to-apply-transforms-to-text/transformed-text-x-y-axis.jpg)
  
 <span data-ttu-id="9c42d-123">Aşağıdaki kod örneği, <xref:System.Windows.Media.TranslateTransform> metni dengelemek için a kullanır.</span><span class="sxs-lookup"><span data-stu-id="9c42d-123">The following code example uses a <xref:System.Windows.Media.TranslateTransform> to offset text.</span></span> <span data-ttu-id="9c42d-124">Bu örnekte, birincil metnin altındaki metnin biraz ofset kopyası gölge efekti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9c42d-124">In this example, a slightly offset copy of text below the primary text creates a shadow effect.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample4](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample4)]  
  
> [!NOTE]
> <span data-ttu-id="9c42d-125">Gölge <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> efektleri sağlamak için zengin bir özellik kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="9c42d-125">The <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> provides a rich set of features for providing shadow effects.</span></span> <span data-ttu-id="9c42d-126">Daha fazla bilgi için [bkz.](how-to-create-text-with-a-shadow.md)</span><span class="sxs-lookup"><span data-stu-id="9c42d-126">For more information, see [Create Text with a Shadow](how-to-create-text-with-a-shadow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c42d-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9c42d-127">See also</span></span>

- [<span data-ttu-id="9c42d-128">Metne Animasyon Uygulama</span><span class="sxs-lookup"><span data-stu-id="9c42d-128">Apply Animations to Text</span></span>](how-to-apply-animations-to-text.md)
