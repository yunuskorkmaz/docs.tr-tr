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
ms.openlocfilehash: 990c82b4844ce3ca7f5b553b180280b6b37496ca
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57373770"
---
# <a name="how-to-transform-a-brush"></a><span data-ttu-id="7b86f-102">Nasıl yapılır: Fırça Dönüşümü</span><span class="sxs-lookup"><span data-stu-id="7b86f-102">How to: Transform a Brush</span></span>
<span data-ttu-id="7b86f-103">Bu örnek nasıl dönüştürüleceğini gösterir <xref:System.Windows.Media.Brush> iki dönüştürme özelliklerini kullanarak nesneleri: <xref:System.Windows.Media.Brush.RelativeTransform%2A> ve <xref:System.Windows.Media.Brush.Transform%2A>.</span><span class="sxs-lookup"><span data-stu-id="7b86f-103">This example shows how to transform <xref:System.Windows.Media.Brush> objects by using their two transformation properties: <xref:System.Windows.Media.Brush.RelativeTransform%2A> and <xref:System.Windows.Media.Brush.Transform%2A>.</span></span>  
  
 <span data-ttu-id="7b86f-104">Aşağıdaki örneklerde bir <xref:System.Windows.Media.RotateTransform> içeriğini döndürmek için bir <xref:System.Windows.Media.ImageBrush> 45 derece.</span><span class="sxs-lookup"><span data-stu-id="7b86f-104">The following examples use a <xref:System.Windows.Media.RotateTransform> to rotate the content of an <xref:System.Windows.Media.ImageBrush> by 45 degrees.</span></span>  
  
 <span data-ttu-id="7b86f-105">Aşağıdaki çizimde gösterildiği <xref:System.Windows.Media.ImageBrush> olmadan bir <xref:System.Windows.Media.RotateTransform>, ile <xref:System.Windows.Media.RotateTransform> uygulanan <xref:System.Windows.Media.Brush.RelativeTransform%2A> özelliği ile <xref:System.Windows.Media.RotateTransform> uygulanan <xref:System.Windows.Media.Brush.Transform%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="7b86f-105">The following illustration shows the <xref:System.Windows.Media.ImageBrush> without a <xref:System.Windows.Media.RotateTransform>, with the <xref:System.Windows.Media.RotateTransform> applied to the <xref:System.Windows.Media.Brush.RelativeTransform%2A> property, and with the <xref:System.Windows.Media.RotateTransform> applied to the <xref:System.Windows.Media.Brush.Transform%2A> property.</span></span>  
  
 <span data-ttu-id="7b86f-106">![Fırça RelativeTransform ve dönüşüm ayarları](./media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")</span><span class="sxs-lookup"><span data-stu-id="7b86f-106">![Brush RelativeTransform and Transform settings](./media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b86f-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="7b86f-107">Example</span></span>  
 <span data-ttu-id="7b86f-108">İlk örnek geçerli bir <xref:System.Windows.Media.RotateTransform> için <xref:System.Windows.Media.Brush.RelativeTransform%2A> özelliği bir <xref:System.Windows.Media.ImageBrush>.</span><span class="sxs-lookup"><span data-stu-id="7b86f-108">The first example applies a <xref:System.Windows.Media.RotateTransform> to the <xref:System.Windows.Media.Brush.RelativeTransform%2A> property of an <xref:System.Windows.Media.ImageBrush>.</span></span> <span data-ttu-id="7b86f-109"><xref:System.Windows.Media.RotateTransform.CenterX%2A> Ve <xref:System.Windows.Media.RotateTransform.CenterY%2A> özelliklerini bir <xref:System.Windows.Media.RotateTransform> her ikisi de ayarlanmış bu içeriğin orta noktasının göreli koordinatı 0,5 nesne.</span><span class="sxs-lookup"><span data-stu-id="7b86f-109">The <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties of a <xref:System.Windows.Media.RotateTransform> object are both set to 0.5, which is the relative coordinate of the center point of this content.</span></span> <span data-ttu-id="7b86f-110">Sonuç olarak, <xref:System.Windows.Media.ImageBrush> içeriği ortasından döndürür.</span><span class="sxs-lookup"><span data-stu-id="7b86f-110">As a result, the <xref:System.Windows.Media.ImageBrush> content rotates about its center.</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 <span data-ttu-id="7b86f-111">İkinci örnek de geçerlidir bir <xref:System.Windows.Media.RotateTransform> için bir <xref:System.Windows.Media.ImageBrush>; ancak bu örnekte <xref:System.Windows.Media.Brush.Transform%2A> özelliği yerine <xref:System.Windows.Media.Brush.RelativeTransform%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="7b86f-111">The second example also applies a <xref:System.Windows.Media.RotateTransform> to an <xref:System.Windows.Media.ImageBrush>; however, this example uses the <xref:System.Windows.Media.Brush.Transform%2A> property instead of the <xref:System.Windows.Media.Brush.RelativeTransform%2A> property.</span></span>  
  
 <span data-ttu-id="7b86f-112">Örnek merkezi fırçayı döndürmek için ayarlar <xref:System.Windows.Media.RotateTransform.CenterX%2A> ve <xref:System.Windows.Media.RotateTransform.CenterY%2A> özelliklerini <xref:System.Windows.Media.RotateTransform> mutlak koordinatlara nesne.</span><span class="sxs-lookup"><span data-stu-id="7b86f-112">To rotate the brush about its center, the example sets the <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties of the <xref:System.Windows.Media.RotateTransform> object to absolute coordinates.</span></span> <span data-ttu-id="7b86f-113">Fırça 175 90 piksel bir dikdörtgen boyar, merkez noktasını dikdörtgenin olduğundan (87.5, 45).</span><span class="sxs-lookup"><span data-stu-id="7b86f-113">Because the brush paints a rectangle that is 175 by 90 pixels, the center point of the rectangle is (87.5, 45).</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 <span data-ttu-id="7b86f-114">Nasıl bir açıklaması için <xref:System.Windows.Media.Brush.RelativeTransform%2A> ve <xref:System.Windows.Media.Brush.Transform%2A> özellikleri çalışma, bkz [fırça dönüşümüne genel bakış](brush-transformation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="7b86f-114">For a description of how the <xref:System.Windows.Media.Brush.RelativeTransform%2A> and <xref:System.Windows.Media.Brush.Transform%2A> properties work, see the [Brush Transformation Overview](brush-transformation-overview.md).</span></span>  
  
 <span data-ttu-id="7b86f-115">Tam bir örnek için bkz. [Fırçalar örnek](https://go.microsoft.com/fwlink/?LinkID=159973).</span><span class="sxs-lookup"><span data-stu-id="7b86f-115">For the complete sample, see [Brushes Sample](https://go.microsoft.com/fwlink/?LinkID=159973).</span></span> <span data-ttu-id="7b86f-116">Fırçalar hakkında daha fazla bilgi için bkz. [düz renkler ve gradyanlar genel bakış boyama](painting-with-solid-colors-and-gradients-overview.md).</span><span class="sxs-lookup"><span data-stu-id="7b86f-116">For more information about brushes, see [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b86f-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7b86f-117">See also</span></span>
- [<span data-ttu-id="7b86f-118">Fırça Dönüşümüne Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7b86f-118">Brush Transformation Overview</span></span>](brush-transformation-overview.md)
- [<span data-ttu-id="7b86f-119">Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7b86f-119">Painting with Solid Colors and Gradients Overview</span></span>](painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="7b86f-120">Dönüşümlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7b86f-120">Transforms Overview</span></span>](transforms-overview.md)
