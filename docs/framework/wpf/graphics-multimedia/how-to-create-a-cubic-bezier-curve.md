---
title: 'Nasıl yapılır: Üçüncü Dereceden Bezier Eğrisi Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- curves [WPF], cubic Bezier
- Bezier curves [WPF], cubic
- graphics [WPF], cubic Bezier curves
- cubic Bezier curves [WPF]
ms.assetid: 450a3a77-7c57-48b0-a008-0f6051add980
ms.openlocfilehash: c12bd84fcebb3acebb80bef5f4479ad535fd6691
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452116"
---
# <a name="how-to-create-a-cubic-bezier-curve"></a><span data-ttu-id="c9697-102">Nasıl yapılır: Üçüncü Dereceden Bezier Eğrisi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c9697-102">How to: Create a Cubic Bezier Curve</span></span>
<span data-ttu-id="c9697-103">Bu örnek, üçüncü dereceden Bezier eğrisinin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c9697-103">This example shows how to create a cubic Bezier curve.</span></span> <span data-ttu-id="c9697-104">Üçüncü dereceden Bezier eğrisi oluşturmak için <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>ve <xref:System.Windows.Media.BezierSegment> sınıflarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="c9697-104">To create a cubic Bezier curve, use the <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, and <xref:System.Windows.Media.BezierSegment> classes.</span></span>  <span data-ttu-id="c9697-105">Elde edilen geometriyi göstermek için bir <xref:System.Windows.Shapes.Path> öğesi kullanın veya bir <xref:System.Windows.Media.GeometryDrawing> ya da <xref:System.Windows.Media.DrawingContext>ile kullanın.</span><span class="sxs-lookup"><span data-stu-id="c9697-105">To display the resulting geometry, use a <xref:System.Windows.Shapes.Path> element, or use it with a <xref:System.Windows.Media.GeometryDrawing> or a <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="c9697-106">Aşağıdaki örneklerde, (10, 100) (300, 100) arasında bir üçüncü dereceden Bezier eğrisi çizilir.</span><span class="sxs-lookup"><span data-stu-id="c9697-106">In the following examples, a cubic Bezier curve is drawn from (10, 100) to (300, 100).</span></span> <span data-ttu-id="c9697-107">Eğrinin (100, 0) ve (200, 200) denetim noktaları vardır.</span><span class="sxs-lookup"><span data-stu-id="c9697-107">The curve has control points of (100, 0) and (200, 200).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9697-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="c9697-108">Example</span></span>  
 <span data-ttu-id="c9697-109">xaml</span><span class="sxs-lookup"><span data-stu-id="c9697-109">[xaml]</span></span>  
  
 <span data-ttu-id="c9697-110">[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], bir yolu anlatmak için kısaltılmış biçimlendirme sözdizimini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9697-110">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you may use abbreviated markup syntax to describe a path.</span></span>  
  
 [!code-xaml[GeometrySample#53](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#53)]  
  
 <span data-ttu-id="c9697-111">xaml</span><span class="sxs-lookup"><span data-stu-id="c9697-111">[xaml]</span></span>  
  
 <span data-ttu-id="c9697-112">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], nesne etiketlerini kullanarak üçüncü dereceden Bezier eğrisi da çizebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9697-112">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can also draw a cubic Bezier curve using object tags.</span></span> <span data-ttu-id="c9697-113">Aşağıdaki, önceki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] örneğine eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="c9697-113">The following is equivalent to the previous [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example.</span></span>  
  
 [!code-xaml[GeometrySample#33](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#33)]  
  
 <span data-ttu-id="c9697-114">Bu örnek, daha büyük bir örnek parçasıdır; Tüm örnek için bkz. [geometriler örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span><span class="sxs-lookup"><span data-stu-id="c9697-114">This example is part of larger sample; for the complete sample, see the [Geometries Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9697-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c9697-115">See also</span></span>

- [<span data-ttu-id="c9697-116">Elips Yay Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c9697-116">Create an Elliptical Arc</span></span>](how-to-create-an-elliptical-arc.md)
- [<span data-ttu-id="c9697-117">PathGeometry İçinde LineSegment Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c9697-117">Create a LineSegment in a PathGeometry</span></span>](how-to-create-a-linesegment-in-a-pathgeometry.md)
- [<span data-ttu-id="c9697-118">Üçüncü Dereceden Bezier Eğrisi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c9697-118">Create a Cubic Bezier Curve</span></span>](how-to-create-a-cubic-bezier-curve.md)
- [<span data-ttu-id="c9697-119">İkinci Dereceden Bezier Eğrisi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c9697-119">Create a Quadratic Bezier Curve</span></span>](how-to-create-a-quadratic-bezier-curve.md)
