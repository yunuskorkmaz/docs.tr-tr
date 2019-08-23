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
ms.openlocfilehash: b749d21c1b5940d216e244393eeb3c133dc153b6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956478"
---
# <a name="how-to-apply-transforms-to-text"></a><span data-ttu-id="e9976-102">Nasıl yapılır: Metne Dönüşüm Uygulama</span><span class="sxs-lookup"><span data-stu-id="e9976-102">How to: Apply Transforms to Text</span></span>
<span data-ttu-id="e9976-103">Dönüşümler uygulamanızdaki metnin görüntülenmesini değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="e9976-103">Transforms can alter the display of text in your application.</span></span> <span data-ttu-id="e9976-104">Aşağıdaki örnekler, bir <xref:System.Windows.Controls.TextBlock> denetimdeki metnin görüntülenmesini etkilemek için farklı türde işleme dönüştürmelerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="e9976-104">The following examples use different types of rendering transforms to affect the display of text in a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9976-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="e9976-105">Example</span></span>  
 <span data-ttu-id="e9976-106">Aşağıdaki örnekte, iki boyutlu x-y düzleinde belirtilen bir nokta hakkında döndürülmüş metin gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e9976-106">The following example shows text rotated about a specified point in the two-dimensional x-y plane.</span></span>  
  
 ![RotateTransform kullanılarak döndürülen metin](./media/how-to-apply-transforms-to-text/text-rotated-ninety-degrees.jpg)  
  
 <span data-ttu-id="e9976-108">Aşağıdaki kod örneği, metni döndürmek <xref:System.Windows.Media.RotateTransform> için bir kullanır.</span><span class="sxs-lookup"><span data-stu-id="e9976-108">The following code example uses a <xref:System.Windows.Media.RotateTransform> to rotate text.</span></span> <span data-ttu-id="e9976-109">90 <xref:System.Windows.Media.RotateTransform.Angle%2A> değeri, öğe 90 derece saat yönünde döner.</span><span class="sxs-lookup"><span data-stu-id="e9976-109">An <xref:System.Windows.Media.RotateTransform.Angle%2A> value of 90 rotates the element 90 degrees clockwise.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample1)]  
  
 <span data-ttu-id="e9976-110">Aşağıdaki örnek, x ekseni ve y ekseni üzerinde% 150 ile ölçeklenmiş üçüncü metin satırındaki 150 metnin ikinci satırını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e9976-110">The following example shows the second line of text scaled by 150% along the x-axis, and the third line of text scaled by 150% along the y-axis.</span></span>  
  
 ![ScaleTransform kullanılarak Ölçeklendirilmiş metin](./media/how-to-apply-transforms-to-text/scaled-text-scaletransform.jpg) 
  
 <span data-ttu-id="e9976-112">Aşağıdaki kod örneği, bir metni <xref:System.Windows.Media.ScaleTransform> özgün boyutundan ölçeklendirmek için bir kullanır.</span><span class="sxs-lookup"><span data-stu-id="e9976-112">The following code example uses a <xref:System.Windows.Media.ScaleTransform> to scale text from its original size.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample2)]  
  
> [!NOTE]
> <span data-ttu-id="e9976-113">Metin ölçekleme metin yazı tipi boyutunun artmasından farklı değildir.</span><span class="sxs-lookup"><span data-stu-id="e9976-113">Scaling text is not the same as increasing the font size of text.</span></span> <span data-ttu-id="e9976-114">Yazı tipi boyutları, farklı boyutlarda en iyi çözünürlüğü sağlamak için birbirinden bağımsız olarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="e9976-114">Font sizes are calculated independently of each other in order to provide the best resolution at different sizes.</span></span> <span data-ttu-id="e9976-115">Ölçeklenmiş metin, diğer yandan, orijinal boyutlu metnin oranlarını korur.</span><span class="sxs-lookup"><span data-stu-id="e9976-115">Scaled text, on the other hand, preserves the proportions of the original-sized text.</span></span>  
  
 <span data-ttu-id="e9976-116">Aşağıdaki örnek, x ekseni üzerinde eğilmiş metni gösterir.</span><span class="sxs-lookup"><span data-stu-id="e9976-116">The following example shows text skewed along the x-axis.</span></span>  
  
 ![SkewTransform kullanarak eğilmiş metin](./media/how-to-apply-transforms-to-text/skewed-transformed-text.jpg)
   
 <span data-ttu-id="e9976-118">Aşağıdaki kod örneği, metni eğmek için bir <xref:System.Windows.Media.SkewTransform> kullanır.</span><span class="sxs-lookup"><span data-stu-id="e9976-118">The following code example uses a <xref:System.Windows.Media.SkewTransform> to skew text.</span></span> <span data-ttu-id="e9976-119">Yamultma olarak da bilinen eğme, koordinat alanını Tekdüzen olmayan bir şekilde uzatır bir dönüşümdür.</span><span class="sxs-lookup"><span data-stu-id="e9976-119">A skew, also known as a shear, is a transformation that stretches the coordinate space in a non-uniform manner.</span></span> <span data-ttu-id="e9976-120">Bu örnekte, iki metin dizesi x koordinatı üzerinde 30 ° ve 30 ° eğriltilir.</span><span class="sxs-lookup"><span data-stu-id="e9976-120">In this example, the two text strings are skewed -30° and 30° along the x-coordinate.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample3)]  
  
 <span data-ttu-id="e9976-121">Aşağıdaki örnek, x ve y ekseni üzerinde çevrilmiş veya taşınan metni gösterir.</span><span class="sxs-lookup"><span data-stu-id="e9976-121">The following example shows text translated, or moved, along the x- and y-axis.</span></span>  
  
 ![TranslateTransform kullanan metin boşluğu](./media/how-to-apply-transforms-to-text/transformed-text-x-y-axis.jpg)
  
 <span data-ttu-id="e9976-123">Aşağıdaki kod örneği, metin kaydırmak <xref:System.Windows.Media.TranslateTransform> için bir kullanır.</span><span class="sxs-lookup"><span data-stu-id="e9976-123">The following code example uses a <xref:System.Windows.Media.TranslateTransform> to offset text.</span></span> <span data-ttu-id="e9976-124">Bu örnekte, birincil metnin altındaki metnin biraz bir konum kopyası bir gölge efekti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e9976-124">In this example, a slightly offset copy of text below the primary text creates a shadow effect.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample4](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample4)]  
  
> [!NOTE]
> <span data-ttu-id="e9976-125">, <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> Gölge etkileri sağlamaya yönelik zengin bir özellikler kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e9976-125">The <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> provides a rich set of features for providing shadow effects.</span></span> <span data-ttu-id="e9976-126">Daha fazla bilgi için bkz. [Gölge Ile metin oluşturma](how-to-create-text-with-a-shadow.md).</span><span class="sxs-lookup"><span data-stu-id="e9976-126">For more information, see [Create Text with a Shadow](how-to-create-text-with-a-shadow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9976-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9976-127">See also</span></span>

- [<span data-ttu-id="e9976-128">Metne Animasyon Uygulama</span><span class="sxs-lookup"><span data-stu-id="e9976-128">Apply Animations to Text</span></span>](how-to-apply-animations-to-text.md)
