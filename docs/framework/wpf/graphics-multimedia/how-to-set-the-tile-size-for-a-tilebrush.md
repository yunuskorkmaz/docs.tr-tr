---
title: 'Nasıl yapılır: TileBrush için Döşeme Boyutunu Ayarlama'
ms.date: 03/30/2017
helpviewer_keywords:
- TileBrush [WPF], size of tile properties
- Viewport property of TileBrush [WPF]
ms.assetid: 04f41090-1b46-4e36-832f-d27d28708b8c
ms.openlocfilehash: af7bab59a292549b29dad9b6a7417f22b1b84e48
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186829"
---
# <a name="how-to-set-the-tile-size-for-a-tilebrush"></a><span data-ttu-id="b793b-102">Nasıl yapılır: TileBrush için Döşeme Boyutunu Ayarlama</span><span class="sxs-lookup"><span data-stu-id="b793b-102">How to: Set the Tile Size for a TileBrush</span></span>

<span data-ttu-id="b793b-103">Bu örnek, bir <xref:System.Windows.Media.TileBrush>.</span><span class="sxs-lookup"><span data-stu-id="b793b-103">This example shows how to set the tile size for a <xref:System.Windows.Media.TileBrush>.</span></span> <span data-ttu-id="b793b-104">Varsayılan olarak, <xref:System.Windows.Media.TileBrush> bir resim yaptığınız alanı tamamen dolduran tek bir döşeme üretir.</span><span class="sxs-lookup"><span data-stu-id="b793b-104">By default, a <xref:System.Windows.Media.TileBrush> produces a single tile that completely fills the area that you are painting.</span></span> <span data-ttu-id="b793b-105">Bu davranışı <xref:System.Windows.Media.TileBrush.Viewport%2A> ve <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> özellikleri ayarlayarak geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b793b-105">You can override this behavior by setting the <xref:System.Windows.Media.TileBrush.Viewport%2A> and <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> properties.</span></span>

<span data-ttu-id="b793b-106">Özellik, <xref:System.Windows.Media.TileBrush.Viewport%2A> bir <xref:System.Windows.Media.TileBrush>.</span><span class="sxs-lookup"><span data-stu-id="b793b-106">The <xref:System.Windows.Media.TileBrush.Viewport%2A> property specifies the tile size for a <xref:System.Windows.Media.TileBrush>.</span></span> <span data-ttu-id="b793b-107">Varsayılan olarak, özelliğin <xref:System.Windows.Media.TileBrush.Viewport%2A> değeri boyanmakta olan alanın boyutuna göredir.</span><span class="sxs-lookup"><span data-stu-id="b793b-107">By default, the value of the <xref:System.Windows.Media.TileBrush.Viewport%2A> property is relative to the size of the area being painted.</span></span> <span data-ttu-id="b793b-108"><xref:System.Windows.Media.TileBrush.Viewport%2A> Özelliğin mutlak bir döşeme boyutu belirtinsin, <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> özelliği ' ne <xref:System.Windows.Media.BrushMappingMode.Absolute>göre ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b793b-108">To make the <xref:System.Windows.Media.TileBrush.Viewport%2A> property specify an absolute tile size, set the <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> property to <xref:System.Windows.Media.BrushMappingMode.Absolute>.</span></span>

## <a name="example"></a><span data-ttu-id="b793b-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="b793b-109">Example</span></span>

<span data-ttu-id="b793b-110">Aşağıdaki örnek, <xref:System.Windows.Media.ImageBrush>bir dikdörtgeni <xref:System.Windows.Media.TileBrush>karolarla boyamak için bir tür , bir tür kullanır.</span><span class="sxs-lookup"><span data-stu-id="b793b-110">The following example uses an <xref:System.Windows.Media.ImageBrush>, a type of <xref:System.Windows.Media.TileBrush>, to paint a rectangle with tiles.</span></span> <span data-ttu-id="b793b-111">Örnek, her döşemeyi çıkış alanının (dikdörtgenin) yüzde 50'si oranında yüzde 50 olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b793b-111">The example sets each tile to 50 percent by 50 percent of the output area (the rectangle).</span></span> <span data-ttu-id="b793b-112">Sonuç olarak, dikdörtgen görüntünün dört projeksiyonları ile boyanır.</span><span class="sxs-lookup"><span data-stu-id="b793b-112">As a result, the rectangle is painted with four projections of the image.</span></span>

<span data-ttu-id="b793b-113">Aşağıdaki resimde, örneğin ürettiği çıktı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="b793b-113">The following illustration shows the output that the example produces:</span></span>

![Bir görüntü fırçası ile fayans gösteren dört kiraz ile bir dikdörtgen.](./media/how-to-set-the-tile-size-for-a-tilebrush/rectangle-tile-image-brush.png)

[!code-csharp[UsingImageBrush_snip#RelativeTileSizeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#relativetilesizeexample)]

<span data-ttu-id="b793b-115">Sonraki örnek, bir <xref:System.Windows.Media.ImageBrush>oluşturur <xref:System.Windows.Media.TileBrush.Viewport%2A> , `0,0,25,25` onun <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> <xref:System.Windows.Media.BrushMappingMode.Absolute>ve onun ayarlar , ve başka bir dikdörtgen boyamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="b793b-115">The next example creates an <xref:System.Windows.Media.ImageBrush>, sets its <xref:System.Windows.Media.TileBrush.Viewport%2A> to `0,0,25,25` and its <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> to <xref:System.Windows.Media.BrushMappingMode.Absolute>, and uses it to paint another rectangle.</span></span> <span data-ttu-id="b793b-116">Sonuç olarak, fırça 25 piksel genişliğinde ve 25 piksel yüksekliğe sahip karolar üretir.</span><span class="sxs-lookup"><span data-stu-id="b793b-116">As a result, the brush produces tiles that have a width of 25  pixels and a height of 25 pixels .</span></span>

<span data-ttu-id="b793b-117">Aşağıdaki resimde, örneğin ürettiği çıktı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="b793b-117">The following illustration shows the output that the example produces:</span></span>

![Kırk sekiz kiraz ile bir dikdörtgen bir Viewport ile bir kiremitli TileFırça gösteren.](./media/how-to-set-the-tile-size-for-a-tilebrush/25-x-25-viewport-tilebrush.png)

[!code-csharp[UsingImageBrush_snip#AbsoluteTileSizeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#absolutetilesizeexample)]

<span data-ttu-id="b793b-119">Önceki örnekler daha büyük bir örneğin parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="b793b-119">The preceding examples are part of a larger sample.</span></span> <span data-ttu-id="b793b-120">Tam örnek için [ImageBrush Örneği'ne](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush)bakın.</span><span class="sxs-lookup"><span data-stu-id="b793b-120">For the complete sample, see [ImageBrush Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush).</span></span>

<span data-ttu-id="b793b-121">Bu örnek sınıfı <xref:System.Windows.Media.ImageBrush> kullansa da, <xref:System.Windows.Media.TileBrush.Viewport%2A> diğer <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> <xref:System.Windows.Media.TileBrush> nesneler için özellikler aynı şekilde <xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Media.VisualBrush>çalışır, yani, için ve .</span><span class="sxs-lookup"><span data-stu-id="b793b-121">Although this example uses the <xref:System.Windows.Media.ImageBrush> class, the <xref:System.Windows.Media.TileBrush.Viewport%2A> and <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> properties behave identically for the other <xref:System.Windows.Media.TileBrush> objects, that is, for <xref:System.Windows.Media.DrawingBrush> and <xref:System.Windows.Media.VisualBrush>.</span></span> <span data-ttu-id="b793b-122">Ve diğer <xref:System.Windows.Media.TileBrush> <xref:System.Windows.Media.ImageBrush> nesneler hakkında daha fazla bilgi için [Resim, Çizim ve Görsellerle Boyama](painting-with-images-drawings-and-visuals.md)konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="b793b-122">For more information about <xref:System.Windows.Media.ImageBrush> and the other <xref:System.Windows.Media.TileBrush> objects, see [Painting with Images, Drawings, and Visuals](painting-with-images-drawings-and-visuals.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b793b-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b793b-123">See also</span></span>

- <xref:System.Windows.Media.TileBrush>
- [<span data-ttu-id="b793b-124">Görüntüler, Çizimler ve Görsellerle Boyama</span><span class="sxs-lookup"><span data-stu-id="b793b-124">Painting with Images, Drawings, and Visuals</span></span>](painting-with-images-drawings-and-visuals.md)
- [<span data-ttu-id="b793b-125">TileBrush ile Farklı Döşeme Desenleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b793b-125">Create Different Tile Patterns with a TileBrush</span></span>](how-to-create-different-tile-patterns-with-a-tilebrush.md)
