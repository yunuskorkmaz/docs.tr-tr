---
title: 'Nasıl yapılır: Elips Yay Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], elliptical arcs
- elliptical arcs [WPF], creating
- arcs [WPF], elliptical
ms.assetid: 3dcfe502-3485-45de-99fb-d53a1367c484
ms.openlocfilehash: d0fffbb25f3c5aaceb2cd80af4f1093e44111200
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453071"
---
# <a name="how-to-create-an-elliptical-arc"></a><span data-ttu-id="2bb72-102">Nasıl yapılır: Elips Yay Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2bb72-102">How to: Create an Elliptical Arc</span></span>
<span data-ttu-id="2bb72-103">Bu örnek, elips bir yayı nasıl çizileceğini gösterir. Elips bir yay oluşturmak için <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>ve <xref:System.Windows.Media.ArcSegment> sınıflarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="2bb72-103">This example shows how to draw an elliptical arc. To create an elliptical arc, use the <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, and <xref:System.Windows.Media.ArcSegment> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2bb72-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="2bb72-104">Example</span></span>  
 <span data-ttu-id="2bb72-105">Aşağıdaki örneklerde, (10.100) öğesinden (200.100) bir elips yay çizilir.</span><span class="sxs-lookup"><span data-stu-id="2bb72-105">In the following examples, an elliptical arc is drawn from (10,100) to (200,100).</span></span> <span data-ttu-id="2bb72-106">Arc, <xref:System.Windows.Media.ArcSegment.IsLargeArc%2A> cihazdan bağımsız piksel, 45 <xref:System.Windows.Media.ArcSegment.RotationAngle%2A> bir `true`ve <xref:System.Windows.Media.ArcSegment.SweepDirection%2A> <xref:System.Windows.Media.SweepDirection.Counterclockwise>bir 50 100 <xref:System.Windows.Media.ArcSegment.Size%2A> sahiptir.</span><span class="sxs-lookup"><span data-stu-id="2bb72-106">The arc has a <xref:System.Windows.Media.ArcSegment.Size%2A> of 100 by 50 device-independent pixels, a <xref:System.Windows.Media.ArcSegment.RotationAngle%2A> of 45 degrees, an <xref:System.Windows.Media.ArcSegment.IsLargeArc%2A> setting of `true`, and a <xref:System.Windows.Media.ArcSegment.SweepDirection%2A> of <xref:System.Windows.Media.SweepDirection.Counterclockwise>.</span></span>  
  
 <span data-ttu-id="2bb72-107">xaml</span><span class="sxs-lookup"><span data-stu-id="2bb72-107">[xaml]</span></span>  
  
 <span data-ttu-id="2bb72-108">[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], bir yolu anlatmak için öznitelik sözdizimini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2bb72-108">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you can use attribute syntax to describe a path.</span></span>  
  
 [!code-xaml[GeometrySample#56](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#56)]  
  
 <span data-ttu-id="2bb72-109">xaml</span><span class="sxs-lookup"><span data-stu-id="2bb72-109">[xaml]</span></span>  
  
 <span data-ttu-id="2bb72-110">(Bu öznitelik sözdiziminin aslında bir <xref:System.Windows.Media.PathGeometry>daha hafif bir sürümünü <xref:System.Windows.Media.StreamGeometry>oluşturduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2bb72-110">(Note that this attribute syntax actually creates a <xref:System.Windows.Media.StreamGeometry>, a lighter-weight version of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="2bb72-111">Daha fazla bilgi için [yol biçimlendirme sözdizimi](path-markup-syntax.md) sayfasına bakın.)</span><span class="sxs-lookup"><span data-stu-id="2bb72-111">For more information, see the [Path Markup Syntax](path-markup-syntax.md) page.)</span></span>  
  
 <span data-ttu-id="2bb72-112">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]' de, açıkça nesne etiketleri kullanarak elips bir yay çizebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2bb72-112">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can also draw an elliptical arc by explicitly using object tags.</span></span> <span data-ttu-id="2bb72-113">Aşağıda, önceki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirmesine eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="2bb72-113">The following is equivalent to the preceding [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 [!code-xaml[GeometrySample#36](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#36)]  
  
 <span data-ttu-id="2bb72-114">Bu örnek, daha büyük bir örneğin bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="2bb72-114">This example is part of a larger sample.</span></span> <span data-ttu-id="2bb72-115">Tüm örnek için bkz. [geometriler örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span><span class="sxs-lookup"><span data-stu-id="2bb72-115">For the complete sample, see the [Geometries Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bb72-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2bb72-116">See also</span></span>

- [<span data-ttu-id="2bb72-117">İkinci Dereceden Bezier Eğrisi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2bb72-117">Create a Quadratic Bezier Curve</span></span>](how-to-create-a-quadratic-bezier-curve.md)
- [<span data-ttu-id="2bb72-118">Üçüncü Dereceden Bezier Eğrisi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2bb72-118">Create a Cubic Bezier Curve</span></span>](how-to-create-a-cubic-bezier-curve.md)
