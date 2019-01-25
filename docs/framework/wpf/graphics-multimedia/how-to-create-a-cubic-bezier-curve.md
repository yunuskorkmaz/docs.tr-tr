---
title: 'Nasıl yapılır: Üçüncü Dereceden Bezier Eğrisi Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- curves [WPF], cubic Bezier
- Bezier curves [WPF], cubic
- graphics [WPF], cubic Bezier curves
- cubic Bezier curves [WPF]
ms.assetid: 450a3a77-7c57-48b0-a008-0f6051add980
ms.openlocfilehash: 2850e505214da4736d05160bf5d5d051404b21a1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54606549"
---
# <a name="how-to-create-a-cubic-bezier-curve"></a><span data-ttu-id="9cd01-102">Nasıl yapılır: Üçüncü Dereceden Bezier Eğrisi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9cd01-102">How to: Create a Cubic Bezier Curve</span></span>
<span data-ttu-id="9cd01-103">Bu örnek, üçüncü dereceden Bezier eğrisi oluşturma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9cd01-103">This example shows how to create a cubic Bezier curve.</span></span> <span data-ttu-id="9cd01-104">Üçüncü dereceden Bezier eğrisi oluşturmak için kullanın <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, ve <xref:System.Windows.Media.BezierSegment> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="9cd01-104">To create a cubic Bezier curve, use the <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, and <xref:System.Windows.Media.BezierSegment> classes.</span></span>  <span data-ttu-id="9cd01-105">Sonuçta elde edilen geometri görüntülemek için kullanın bir <xref:System.Windows.Shapes.Path> öğesi veya onunla bir <xref:System.Windows.Media.GeometryDrawing> veya <xref:System.Windows.Media.DrawingContext>.</span><span class="sxs-lookup"><span data-stu-id="9cd01-105">To display the resulting geometry, use a <xref:System.Windows.Shapes.Path> element, or use it with a <xref:System.Windows.Media.GeometryDrawing> or a <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="9cd01-106">Üçüncü dereceden Bezier eğrisi çizilir aşağıdaki örneklerde (10, 100) için (300, 100).</span><span class="sxs-lookup"><span data-stu-id="9cd01-106">In the following examples, a cubic Bezier curve is drawn from (10, 100) to (300, 100).</span></span> <span data-ttu-id="9cd01-107">Eğri denetim noktaları vardır (100, 0) ve (200, 200).</span><span class="sxs-lookup"><span data-stu-id="9cd01-107">The curve has control points of (100, 0) and (200, 200).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9cd01-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="9cd01-108">Example</span></span>  
 <span data-ttu-id="9cd01-109">[xaml]</span><span class="sxs-lookup"><span data-stu-id="9cd01-109">[xaml]</span></span>  
  
 <span data-ttu-id="9cd01-110">İçinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], kısaltılmış biçimlendirme sözdizimi bir yolunu tanımlamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9cd01-110">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you may use abbreviated markup syntax to describe a path.</span></span>  
  
 [!code-xaml[GeometrySample#53](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#53)]  
  
 <span data-ttu-id="9cd01-111">[xaml]</span><span class="sxs-lookup"><span data-stu-id="9cd01-111">[xaml]</span></span>  
  
 <span data-ttu-id="9cd01-112">İçinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], nesne etiketleri kullanarak üçüncü dereceden Bezier eğrisi da çizebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9cd01-112">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can also draw a cubic Bezier curve using object tags.</span></span> <span data-ttu-id="9cd01-113">Aşağıdaki önceki eşdeğerdir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] örnek.</span><span class="sxs-lookup"><span data-stu-id="9cd01-113">The following is equivalent to the previous [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example.</span></span>  
  
 [!code-xaml[GeometrySample#33](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#33)]  
  
 <span data-ttu-id="9cd01-114">Bu örnek, daha büyük örnek bir parçasıdır; tam bir örnek için bkz. [geometri örneği](https://go.microsoft.com/fwlink/?LinkID=159989).</span><span class="sxs-lookup"><span data-stu-id="9cd01-114">This example is part of larger sample; for the complete sample, see the [Geometries Sample](https://go.microsoft.com/fwlink/?LinkID=159989).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cd01-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9cd01-115">See also</span></span>
- [<span data-ttu-id="9cd01-116">Elips Yay Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9cd01-116">Create an Elliptical Arc</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-an-elliptical-arc.md)
- [<span data-ttu-id="9cd01-117">PathGeometry İçinde LineSegment Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9cd01-117">Create a LineSegment in a PathGeometry</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-linesegment-in-a-pathgeometry.md)
- [<span data-ttu-id="9cd01-118">Üçüncü Dereceden Bezier Eğrisi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9cd01-118">Create a Cubic Bezier Curve</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md)
- [<span data-ttu-id="9cd01-119">İkinci Dereceden Bezier Eğrisi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9cd01-119">Create a Quadratic Bezier Curve</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md)
