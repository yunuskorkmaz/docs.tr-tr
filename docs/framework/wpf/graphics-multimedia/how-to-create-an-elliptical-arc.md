---
title: 'Nasıl yapılır: Elips Yay Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], elliptical arcs
- elliptical arcs [WPF], creating
- arcs [WPF], elliptical
ms.assetid: 3dcfe502-3485-45de-99fb-d53a1367c484
ms.openlocfilehash: 3b8aab2f2d79b1158adb006049b27a9f15575216
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33560896"
---
# <a name="how-to-create-an-elliptical-arc"></a><span data-ttu-id="73aad-102">Nasıl yapılır: Elips Yay Oluşturma</span><span class="sxs-lookup"><span data-stu-id="73aad-102">How to: Create an Elliptical Arc</span></span>
<span data-ttu-id="73aad-103">Bu örnek nasıl elips yay çizileceğini gösterir. Elips yay oluşturmak üzere kullanmanız <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, ve <xref:System.Windows.Media.ArcSegment> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="73aad-103">This example shows how to draw an elliptical arc. To create an elliptical arc, use the <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, and <xref:System.Windows.Media.ArcSegment> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73aad-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="73aad-104">Example</span></span>  
 <span data-ttu-id="73aad-105">Aşağıdaki örneklerde, elips yay (10,100) dan (200,100) çizilir.</span><span class="sxs-lookup"><span data-stu-id="73aad-105">In the following examples, an elliptical arc is drawn from (10,100) to (200,100).</span></span> <span data-ttu-id="73aad-106">Yayı sahip bir <xref:System.Windows.Media.ArcSegment.Size%2A> 100 50 aygıttan bağımsız piksel tarafından bir <xref:System.Windows.Media.ArcSegment.RotationAngle%2A> 45 derece bir <xref:System.Windows.Media.ArcSegment.IsLargeArc%2A> ayarıyla `true`ve bir <xref:System.Windows.Media.ArcSegment.SweepDirection%2A> , <xref:System.Windows.Media.SweepDirection.Counterclockwise>.</span><span class="sxs-lookup"><span data-stu-id="73aad-106">The arc has a <xref:System.Windows.Media.ArcSegment.Size%2A> of 100 by 50 device-independent pixels, a <xref:System.Windows.Media.ArcSegment.RotationAngle%2A> of 45 degrees, an <xref:System.Windows.Media.ArcSegment.IsLargeArc%2A> setting of `true`, and a <xref:System.Windows.Media.ArcSegment.SweepDirection%2A> of <xref:System.Windows.Media.SweepDirection.Counterclockwise>.</span></span>  
  
 <span data-ttu-id="73aad-107">[xaml]</span><span class="sxs-lookup"><span data-stu-id="73aad-107">[xaml]</span></span>  
  
 <span data-ttu-id="73aad-108">İçinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], bir yolu açıklamak için öznitelik sözdizimini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73aad-108">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you can use attribute syntax to describe a path.</span></span>  
  
 [!code-xaml[GeometrySample#56](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#56)]  
  
 <span data-ttu-id="73aad-109">[xaml]</span><span class="sxs-lookup"><span data-stu-id="73aad-109">[xaml]</span></span>  
  
 <span data-ttu-id="73aad-110">(Bu öznitelik sözdizimi gerçekte oluşturur Not bir <xref:System.Windows.Media.StreamGeometry>, hafifletilmiş sürümü bir <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="73aad-110">(Note that this attribute syntax actually creates a <xref:System.Windows.Media.StreamGeometry>, a lighter-weight version of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="73aad-111">Daha fazla bilgi için bkz: [biçimlendirme sözdizimi yolu](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) sayfası.)</span><span class="sxs-lookup"><span data-stu-id="73aad-111">For more information, see the [Path Markup Syntax](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) page.)</span></span>  
  
 <span data-ttu-id="73aad-112">İçinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], açıkça nesne etiketleri kullanılarak elips yay çizebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73aad-112">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can also draw an elliptical arc by explicitly using object tags.</span></span> <span data-ttu-id="73aad-113">Aşağıdaki önceki eşdeğerdir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirme.</span><span class="sxs-lookup"><span data-stu-id="73aad-113">The following is equivalent to the preceding [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 [!code-xaml[GeometrySample#36](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#36)]  
  
 <span data-ttu-id="73aad-114">Bu örnek daha büyük bir örneğin parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="73aad-114">This example is part of a larger sample.</span></span> <span data-ttu-id="73aad-115">Tam bir örnek için bkz: [geometri örneği](http://go.microsoft.com/fwlink/?LinkID=159989).</span><span class="sxs-lookup"><span data-stu-id="73aad-115">For the complete sample, see the [Geometries Sample](http://go.microsoft.com/fwlink/?LinkID=159989).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73aad-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="73aad-116">See Also</span></span>  
 [<span data-ttu-id="73aad-117">İkinci Dereceden Bezier Eğrisi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="73aad-117">Create a Quadratic Bezier Curve</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md)  
 [<span data-ttu-id="73aad-118">Üçüncü Dereceden Bezier Eğrisi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="73aad-118">Create a Cubic Bezier Curve</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md)
