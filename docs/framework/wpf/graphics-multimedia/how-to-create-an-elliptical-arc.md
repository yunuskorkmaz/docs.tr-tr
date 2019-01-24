---
title: 'Nasıl yapılır: Elips Yay Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], elliptical arcs
- elliptical arcs [WPF], creating
- arcs [WPF], elliptical
ms.assetid: 3dcfe502-3485-45de-99fb-d53a1367c484
ms.openlocfilehash: 4f4461f778e2c86adb3932edf8435ca75b3b5e98
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54679571"
---
# <a name="how-to-create-an-elliptical-arc"></a><span data-ttu-id="74d89-102">Nasıl yapılır: Elips Yay Oluşturma</span><span class="sxs-lookup"><span data-stu-id="74d89-102">How to: Create an Elliptical Arc</span></span>
<span data-ttu-id="74d89-103">Bu örnek, bir elips yay çizmenin gösterilmektedir. Elips yay oluşturma için kullanın <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, ve <xref:System.Windows.Media.ArcSegment> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="74d89-103">This example shows how to draw an elliptical arc. To create an elliptical arc, use the <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, and <xref:System.Windows.Media.ArcSegment> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74d89-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="74d89-104">Example</span></span>  
 <span data-ttu-id="74d89-105">Aşağıdaki örneklerde, elips yay dan (200,100) (10,100) çizilir.</span><span class="sxs-lookup"><span data-stu-id="74d89-105">In the following examples, an elliptical arc is drawn from (10,100) to (200,100).</span></span> <span data-ttu-id="74d89-106">Yayı sahip bir <xref:System.Windows.Media.ArcSegment.Size%2A> 100 tarafından 50 CİHAZDAN bağımsız piksel bir <xref:System.Windows.Media.ArcSegment.RotationAngle%2A> açısını 45 derecenin bir <xref:System.Windows.Media.ArcSegment.IsLargeArc%2A> ayarıyla `true`ve <xref:System.Windows.Media.ArcSegment.SweepDirection%2A> , <xref:System.Windows.Media.SweepDirection.Counterclockwise>.</span><span class="sxs-lookup"><span data-stu-id="74d89-106">The arc has a <xref:System.Windows.Media.ArcSegment.Size%2A> of 100 by 50 device-independent pixels, a <xref:System.Windows.Media.ArcSegment.RotationAngle%2A> of 45 degrees, an <xref:System.Windows.Media.ArcSegment.IsLargeArc%2A> setting of `true`, and a <xref:System.Windows.Media.ArcSegment.SweepDirection%2A> of <xref:System.Windows.Media.SweepDirection.Counterclockwise>.</span></span>  
  
 <span data-ttu-id="74d89-107">[xaml]</span><span class="sxs-lookup"><span data-stu-id="74d89-107">[xaml]</span></span>  
  
 <span data-ttu-id="74d89-108">İçinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], öznitelik sözdizimi bir yolunu tanımlamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74d89-108">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you can use attribute syntax to describe a path.</span></span>  
  
 [!code-xaml[GeometrySample#56](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#56)]  
  
 <span data-ttu-id="74d89-109">[xaml]</span><span class="sxs-lookup"><span data-stu-id="74d89-109">[xaml]</span></span>  
  
 <span data-ttu-id="74d89-110">(Aslında bu öznitelik sözdizimi oluşturan Not bir <xref:System.Windows.Media.StreamGeometry>, daha basit sürümü bir <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="74d89-110">(Note that this attribute syntax actually creates a <xref:System.Windows.Media.StreamGeometry>, a lighter-weight version of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="74d89-111">Daha fazla bilgi için [yol işaretleme söz dizimi](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) sayfası.)</span><span class="sxs-lookup"><span data-stu-id="74d89-111">For more information, see the [Path Markup Syntax](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) page.)</span></span>  
  
 <span data-ttu-id="74d89-112">İçinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], nesne etiketleri kullanarak açıkça elips yay çizebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74d89-112">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can also draw an elliptical arc by explicitly using object tags.</span></span> <span data-ttu-id="74d89-113">Aşağıdaki önceki eşdeğerdir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirme.</span><span class="sxs-lookup"><span data-stu-id="74d89-113">The following is equivalent to the preceding [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 [!code-xaml[GeometrySample#36](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#36)]  
  
 <span data-ttu-id="74d89-114">Bu örnek, daha büyük bir örnek bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="74d89-114">This example is part of a larger sample.</span></span> <span data-ttu-id="74d89-115">Tam bir örnek için bkz. [geometri örneği](https://go.microsoft.com/fwlink/?LinkID=159989).</span><span class="sxs-lookup"><span data-stu-id="74d89-115">For the complete sample, see the [Geometries Sample](https://go.microsoft.com/fwlink/?LinkID=159989).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74d89-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="74d89-116">See also</span></span>
- [<span data-ttu-id="74d89-117">İkinci Dereceden Bezier Eğrisi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="74d89-117">Create a Quadratic Bezier Curve</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md)
- [<span data-ttu-id="74d89-118">Üçüncü Dereceden Bezier Eğrisi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="74d89-118">Create a Cubic Bezier Curve</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md)
