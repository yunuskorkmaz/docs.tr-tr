---
title: 'Nasıl yapılır: TileBrush için Döşeme Boyutunu Ayarlama'
ms.date: 03/30/2017
helpviewer_keywords:
- TileBrush [WPF], size of tile properties
- Viewport property of TileBrush [WPF]
ms.assetid: 04f41090-1b46-4e36-832f-d27d28708b8c
ms.openlocfilehash: 80b5dfc668464df829db593668bea8a9a4ec09e4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58839703"
---
# <a name="how-to-set-the-tile-size-for-a-tilebrush"></a><span data-ttu-id="596f1-102">Nasıl yapılır: TileBrush için Döşeme Boyutunu Ayarlama</span><span class="sxs-lookup"><span data-stu-id="596f1-102">How to: Set the Tile Size for a TileBrush</span></span>

<span data-ttu-id="596f1-103">Bu örnek için döşeme boyutunu ayarlama işlemi gösterilmektedir bir <xref:System.Windows.Media.TileBrush>.</span><span class="sxs-lookup"><span data-stu-id="596f1-103">This example shows how to set the tile size for a <xref:System.Windows.Media.TileBrush>.</span></span> <span data-ttu-id="596f1-104">Varsayılan olarak, bir <xref:System.Windows.Media.TileBrush> tamamen boyama yaptığınız alanı dolduran kutucuk üretir.</span><span class="sxs-lookup"><span data-stu-id="596f1-104">By default, a <xref:System.Windows.Media.TileBrush> produces a single tile that completely fills the area that you are painting.</span></span> <span data-ttu-id="596f1-105">Ayarlayarak bu davranışı geçersiz kılabilirsiniz <xref:System.Windows.Media.TileBrush.Viewport%2A> ve <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="596f1-105">You can override this behavior by setting the <xref:System.Windows.Media.TileBrush.Viewport%2A> and <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> properties.</span></span>

<span data-ttu-id="596f1-106"><xref:System.Windows.Media.TileBrush.Viewport%2A> Özelliği için döşeme boyutunu belirten bir <xref:System.Windows.Media.TileBrush>.</span><span class="sxs-lookup"><span data-stu-id="596f1-106">The <xref:System.Windows.Media.TileBrush.Viewport%2A> property specifies the tile size for a <xref:System.Windows.Media.TileBrush>.</span></span> <span data-ttu-id="596f1-107">Varsayılan olarak, değerini <xref:System.Windows.Media.TileBrush.Viewport%2A> boyanan alanın boyutuna göre bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="596f1-107">By default, the value of the <xref:System.Windows.Media.TileBrush.Viewport%2A> property is relative to the size of the area being painted.</span></span> <span data-ttu-id="596f1-108">Yapmak <xref:System.Windows.Media.TileBrush.Viewport%2A> özelliğini belirtin, mutlak bir döşeme boyutunu ayarlama <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> özelliğini <xref:System.Windows.Media.BrushMappingMode.Absolute>.</span><span class="sxs-lookup"><span data-stu-id="596f1-108">To make the <xref:System.Windows.Media.TileBrush.Viewport%2A> property specify an absolute tile size, set the <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> property to <xref:System.Windows.Media.BrushMappingMode.Absolute>.</span></span>

## <a name="example"></a><span data-ttu-id="596f1-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="596f1-109">Example</span></span>

<span data-ttu-id="596f1-110">Aşağıdaki örnekte bir <xref:System.Windows.Media.ImageBrush>, bir tür <xref:System.Windows.Media.TileBrush>kutucuklar içeren bir dikdörtgen boyamak için.</span><span class="sxs-lookup"><span data-stu-id="596f1-110">The following example uses an <xref:System.Windows.Media.ImageBrush>, a type of <xref:System.Windows.Media.TileBrush>, to paint a rectangle with tiles.</span></span> <span data-ttu-id="596f1-111">Örnek her kutucuk yüzde 50 ' (dikdörtgen) çıktı alanının yüzde 50 ayarlar.</span><span class="sxs-lookup"><span data-stu-id="596f1-111">The example sets each tile to 50 percent by 50 percent of the output area (the rectangle).</span></span> <span data-ttu-id="596f1-112">Sonuç olarak, dikdörtgeni görüntünün dört projeksiyonlar ile boyanır.</span><span class="sxs-lookup"><span data-stu-id="596f1-112">As a result, the rectangle is painted with four projections of the image.</span></span>

<span data-ttu-id="596f1-113">Örneğin oluşturduğu çıktı aşağıda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="596f1-113">The following illustration shows the output that the example produces:</span></span>

![Resim fırçası ile döşeme gösteren dört cherries bir dikdörtgen.](./media/how-to-set-the-tile-size-for-a-tilebrush/rectangle-tile-image-brush.png)

[!code-csharp[UsingImageBrush_snip#RelativeTileSizeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#relativetilesizeexample)]

<span data-ttu-id="596f1-115">Sonraki örnek, oluşturur bir <xref:System.Windows.Media.ImageBrush>, ayarlar, <xref:System.Windows.Media.TileBrush.Viewport%2A> için `0,0,25,25` ve kendi <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> için <xref:System.Windows.Media.BrushMappingMode.Absolute>ve başka bir dikdörtgen boyamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="596f1-115">The next example creates an <xref:System.Windows.Media.ImageBrush>, sets its <xref:System.Windows.Media.TileBrush.Viewport%2A> to `0,0,25,25` and its <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> to <xref:System.Windows.Media.BrushMappingMode.Absolute>, and uses it to paint another rectangle.</span></span> <span data-ttu-id="596f1-116">Sonuç olarak, fırça 25 piksel genişliği ve yüksekliği 25 piksel kutucukları üretir.</span><span class="sxs-lookup"><span data-stu-id="596f1-116">As a result, the brush produces tiles that have a width of 25  pixels and a height of 25 pixels .</span></span>

<span data-ttu-id="596f1-117">Örneğin oluşturduğu çıktı aşağıda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="596f1-117">The following illustration shows the output that the example produces:</span></span>

![Kırk sekiz cherries döşenmiş TileBrush ile görünüm penceresini gösteren bir dikdörtgen.](./media/how-to-set-the-tile-size-for-a-tilebrush/25-x-25-viewport-tilebrush.png)

[!code-csharp[UsingImageBrush_snip#AbsoluteTileSizeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#absolutetilesizeexample)]

<span data-ttu-id="596f1-119">Önceki örneklerde, daha büyük bir örnek bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="596f1-119">The preceding examples are part of a larger sample.</span></span> <span data-ttu-id="596f1-120">Tam bir örnek için bkz. [ImageBrush örnek](https://go.microsoft.com/fwlink/?LinkID=160005).</span><span class="sxs-lookup"><span data-stu-id="596f1-120">For the complete sample, see [ImageBrush Sample](https://go.microsoft.com/fwlink/?LinkID=160005).</span></span>

<span data-ttu-id="596f1-121">Bu örnek kullansa <xref:System.Windows.Media.ImageBrush> sınıfı <xref:System.Windows.Media.TileBrush.Viewport%2A> ve <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> özellikleri aynı şekilde davranır diğeri için <xref:System.Windows.Media.TileBrush> nesnelerini, diğer bir deyişle, için <xref:System.Windows.Media.DrawingBrush> ve <xref:System.Windows.Media.VisualBrush>.</span><span class="sxs-lookup"><span data-stu-id="596f1-121">Although this example uses the <xref:System.Windows.Media.ImageBrush> class, the <xref:System.Windows.Media.TileBrush.Viewport%2A> and <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> properties behave identically for the other <xref:System.Windows.Media.TileBrush> objects, that is, for <xref:System.Windows.Media.DrawingBrush> and <xref:System.Windows.Media.VisualBrush>.</span></span> <span data-ttu-id="596f1-122">Hakkında daha fazla bilgi için <xref:System.Windows.Media.ImageBrush> ve diğer <xref:System.Windows.Media.TileBrush> nesneleri bkz [görüntüler, çizimler ve görsellerle boyama](painting-with-images-drawings-and-visuals.md).</span><span class="sxs-lookup"><span data-stu-id="596f1-122">For more information about <xref:System.Windows.Media.ImageBrush> and the other <xref:System.Windows.Media.TileBrush> objects, see [Painting with Images, Drawings, and Visuals](painting-with-images-drawings-and-visuals.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="596f1-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="596f1-123">See also</span></span>

- <xref:System.Windows.Media.TileBrush>
- [<span data-ttu-id="596f1-124">Görüntüler, Çizimler ve Görsellerle Boyama</span><span class="sxs-lookup"><span data-stu-id="596f1-124">Painting with Images, Drawings, and Visuals</span></span>](painting-with-images-drawings-and-visuals.md)
- [<span data-ttu-id="596f1-125">TileBrush ile Farklı Döşeme Desenleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="596f1-125">Create Different Tile Patterns with a TileBrush</span></span>](how-to-create-different-tile-patterns-with-a-tilebrush.md)
