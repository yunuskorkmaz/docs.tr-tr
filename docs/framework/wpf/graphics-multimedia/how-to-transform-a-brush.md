---
title: 'Nasıl yapılır: Fırça Dönüşümü'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], rotating contents
- brushes [WPF], Transform property
- rotating contents of brushes [WPF]
ms.assetid: ebada2f9-f01f-4863-9ea2-c2e4e51610f1
ms.openlocfilehash: b4484e2fc1ae3e969b02b1d8f3ae4ab2a035558e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187331"
---
# <a name="how-to-transform-a-brush"></a><span data-ttu-id="300a9-102">Nasıl yapılır: Fırça Dönüşümü</span><span class="sxs-lookup"><span data-stu-id="300a9-102">How to: Transform a Brush</span></span>
<span data-ttu-id="300a9-103">Bu örnek, iki <xref:System.Windows.Media.Brush> dönüştürme özelliklerini kullanarak nesnelerin <xref:System.Windows.Media.Brush.RelativeTransform%2A> nasıl <xref:System.Windows.Media.Brush.Transform%2A>dönüştürüleceklerini gösterir: ve.</span><span class="sxs-lookup"><span data-stu-id="300a9-103">This example shows how to transform <xref:System.Windows.Media.Brush> objects by using their two transformation properties: <xref:System.Windows.Media.Brush.RelativeTransform%2A> and <xref:System.Windows.Media.Brush.Transform%2A>.</span></span>  
  
 <span data-ttu-id="300a9-104">Aşağıdaki örneklerde <xref:System.Windows.Media.RotateTransform> a, bir <xref:System.Windows.Media.ImageBrush> derecenin içeriğini 45 derece döndürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="300a9-104">The following examples use a <xref:System.Windows.Media.RotateTransform> to rotate the content of an <xref:System.Windows.Media.ImageBrush> by 45 degrees.</span></span>  
  
 <span data-ttu-id="300a9-105">Aşağıdaki resimde, <xref:System.Windows.Media.ImageBrush> <xref:System.Windows.Media.Brush.RelativeTransform%2A> özelliğe <xref:System.Windows.Media.RotateTransform> <xref:System.Windows.Media.RotateTransform> uygulanan bir , olmayan ve <xref:System.Windows.Media.RotateTransform> <xref:System.Windows.Media.Brush.Transform%2A> özelliğe uygulanan ile gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="300a9-105">The following illustration shows the <xref:System.Windows.Media.ImageBrush> without a <xref:System.Windows.Media.RotateTransform>, with the <xref:System.Windows.Media.RotateTransform> applied to the <xref:System.Windows.Media.Brush.RelativeTransform%2A> property, and with the <xref:System.Windows.Media.RotateTransform> applied to the <xref:System.Windows.Media.Brush.Transform%2A> property.</span></span>  
  
 <span data-ttu-id="300a9-106">![Fırça RelativeTransform ve Transform ayarları](./media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")</span><span class="sxs-lookup"><span data-stu-id="300a9-106">![Brush RelativeTransform and Transform settings](./media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")</span></span>  
  
## <a name="example"></a><span data-ttu-id="300a9-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="300a9-107">Example</span></span>  
 <span data-ttu-id="300a9-108">İlk örnek bir <xref:System.Windows.Media.RotateTransform> <xref:System.Windows.Media.Brush.RelativeTransform%2A> . <xref:System.Windows.Media.ImageBrush></span><span class="sxs-lookup"><span data-stu-id="300a9-108">The first example applies a <xref:System.Windows.Media.RotateTransform> to the <xref:System.Windows.Media.Brush.RelativeTransform%2A> property of an <xref:System.Windows.Media.ImageBrush>.</span></span> <span data-ttu-id="300a9-109">Bir <xref:System.Windows.Media.RotateTransform.CenterX%2A> <xref:System.Windows.Media.RotateTransform.CenterY%2A> <xref:System.Windows.Media.RotateTransform> nesnenin ve özelliklerinin her ikisi de 0,5 olarak ayarlanır, bu da bu içeriğin merkez noktasının göreli koordinatıdır.</span><span class="sxs-lookup"><span data-stu-id="300a9-109">The <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties of a <xref:System.Windows.Media.RotateTransform> object are both set to 0.5, which is the relative coordinate of the center point of this content.</span></span> <span data-ttu-id="300a9-110">Sonuç olarak, <xref:System.Windows.Media.ImageBrush> içerik merkezi etrafında döner.</span><span class="sxs-lookup"><span data-stu-id="300a9-110">As a result, the <xref:System.Windows.Media.ImageBrush> content rotates about its center.</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 <span data-ttu-id="300a9-111">İkinci örnek de bir; <xref:System.Windows.Media.RotateTransform> <xref:System.Windows.Media.ImageBrush> ancak, bu örnek <xref:System.Windows.Media.Brush.Transform%2A> <xref:System.Windows.Media.Brush.RelativeTransform%2A> özelliği yerine özelliği kullanır.</span><span class="sxs-lookup"><span data-stu-id="300a9-111">The second example also applies a <xref:System.Windows.Media.RotateTransform> to an <xref:System.Windows.Media.ImageBrush>; however, this example uses the <xref:System.Windows.Media.Brush.Transform%2A> property instead of the <xref:System.Windows.Media.Brush.RelativeTransform%2A> property.</span></span>  
  
 <span data-ttu-id="300a9-112">Fırçayı merkezi yle döndürmek için, örnek <xref:System.Windows.Media.RotateTransform.CenterX%2A> <xref:System.Windows.Media.RotateTransform.CenterY%2A> nesnenin <xref:System.Windows.Media.RotateTransform> özelliklerini ve özelliklerini mutlak koordinatlara ayarlar.</span><span class="sxs-lookup"><span data-stu-id="300a9-112">To rotate the brush about its center, the example sets the <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties of the <xref:System.Windows.Media.RotateTransform> object to absolute coordinates.</span></span> <span data-ttu-id="300a9-113">Fırça 175'e 90 piksellik bir dikdörtgen boyadığından, dikdörtgenin orta noktası (87,5, 45).</span><span class="sxs-lookup"><span data-stu-id="300a9-113">Because the brush paints a rectangle that is 175 by 90 pixels, the center point of the rectangle is (87.5, 45).</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 <span data-ttu-id="300a9-114">Özelliklerin ve <xref:System.Windows.Media.Brush.RelativeTransform%2A> <xref:System.Windows.Media.Brush.Transform%2A> özelliklerinin nasıl çalıştığına yönelik bir açıklama için [Fırça Dönüşümüne Genel Bakış'a](brush-transformation-overview.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="300a9-114">For a description of how the <xref:System.Windows.Media.Brush.RelativeTransform%2A> and <xref:System.Windows.Media.Brush.Transform%2A> properties work, see the [Brush Transformation Overview](brush-transformation-overview.md).</span></span>  
  
 <span data-ttu-id="300a9-115">Tam örnek için [Fırçalar Örneği'ne](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes)bakın.</span><span class="sxs-lookup"><span data-stu-id="300a9-115">For the complete sample, see [Brushes Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span></span> <span data-ttu-id="300a9-116">Fırçalar hakkında daha fazla bilgi için, [Düz Renkler ve Degradeler Genel Bakış ile Boyama](painting-with-solid-colors-and-gradients-overview.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="300a9-116">For more information about brushes, see [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="300a9-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="300a9-117">See also</span></span>

- [<span data-ttu-id="300a9-118">Fırça Dönüşümüne Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="300a9-118">Brush Transformation Overview</span></span>](brush-transformation-overview.md)
- [<span data-ttu-id="300a9-119">Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="300a9-119">Painting with Solid Colors and Gradients Overview</span></span>](painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="300a9-120">Dönüşümlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="300a9-120">Transforms Overview</span></span>](transforms-overview.md)
