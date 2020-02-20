---
title: 'Nasıl yapılır: PathGeometry Kullanarak Şekil Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], creating with PathGeometry class
- graphics [WPF], shapes
ms.assetid: 49a4a8b7-e738-45be-8dac-b54a6d8f5b21
ms.openlocfilehash: bdf3c937bfff1780a72e8743bc86a3c3dad2558d
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452051"
---
# <a name="how-to-create-a-shape-by-using-a-pathgeometry"></a><span data-ttu-id="18471-102">Nasıl yapılır: PathGeometry Kullanarak Şekil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="18471-102">How to: Create a Shape by Using a PathGeometry</span></span>
<span data-ttu-id="18471-103">Bu örnek, <xref:System.Windows.Media.PathGeometry> sınıfını kullanarak bir şeklin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="18471-103">This example shows how to create a shape using the <xref:System.Windows.Media.PathGeometry> class.</span></span> <span data-ttu-id="18471-104"><xref:System.Windows.Media.PathGeometry> nesneler bir veya daha fazla <xref:System.Windows.Media.PathFigure> nesnesinden oluşur; Her <xref:System.Windows.Media.PathFigure> farklı bir "şekil" veya şekli temsil eder.</span><span class="sxs-lookup"><span data-stu-id="18471-104"><xref:System.Windows.Media.PathGeometry> objects are composed of one or more <xref:System.Windows.Media.PathFigure> objects; each <xref:System.Windows.Media.PathFigure> represents a different "figure" or shape.</span></span> <span data-ttu-id="18471-105">Her <xref:System.Windows.Media.PathFigure> bir veya daha fazla <xref:System.Windows.Media.PathSegment> nesnesinden oluşur ve her biri şekil veya şeklin bağlı bir bölümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="18471-105">Each <xref:System.Windows.Media.PathFigure> is itself composed of one or more <xref:System.Windows.Media.PathSegment> objects, each representing a connected portion of the figure or shape.</span></span> <span data-ttu-id="18471-106">Segment türleri <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.ArcSegment>ve <xref:System.Windows.Media.BezierSegment>içerir.</span><span class="sxs-lookup"><span data-stu-id="18471-106">Segment types include <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.ArcSegment>, and <xref:System.Windows.Media.BezierSegment>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="18471-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="18471-107">Example</span></span>  
 <span data-ttu-id="18471-108">Aşağıdaki örnek, bir üçgen oluşturmak için <xref:System.Windows.Media.PathGeometry> kullanır.</span><span class="sxs-lookup"><span data-stu-id="18471-108">The following example uses a <xref:System.Windows.Media.PathGeometry> to create a triangle.</span></span> <span data-ttu-id="18471-109"><xref:System.Windows.Media.PathGeometry>, bir <xref:System.Windows.Shapes.Path> öğesi kullanılarak görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="18471-109">The  <xref:System.Windows.Media.PathGeometry> is displayed using a <xref:System.Windows.Shapes.Path> element.</span></span>  
  
 [!code-xaml[GeometrySample#49](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#49)]  
  
 <span data-ttu-id="18471-110">Aşağıdaki çizimde, önceki örnekte oluşturulan Şekil gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="18471-110">The following illustration shows the shape created in the previous example.</span></span>  
  
 <span data-ttu-id="18471-111">![PathGeometry](./media/wcpsdk-graphicsmm-pathgeometry-triangle.gif "wcpsdk_graphicsmm_pathgeometry_triangle")</span><span class="sxs-lookup"><span data-stu-id="18471-111">![A PathGeometry](./media/wcpsdk-graphicsmm-pathgeometry-triangle.gif "wcpsdk_graphicsmm_pathgeometry_triangle")</span></span>  
<span data-ttu-id="18471-112">PathGeometry ile oluşturulan üçgen</span><span class="sxs-lookup"><span data-stu-id="18471-112">A triangle created with a PathGeometry</span></span>  
  
 <span data-ttu-id="18471-113">Önceki örnekte, bir üçgen olan görece basit bir şekil oluşturma gösterildi.</span><span class="sxs-lookup"><span data-stu-id="18471-113">The previous example showed how to create a relatively simple shape, a triangle.</span></span> <span data-ttu-id="18471-114"><xref:System.Windows.Media.PathGeometry> yay ve eğriler de dahil olmak üzere daha karmaşık şekiller oluşturmak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="18471-114">A <xref:System.Windows.Media.PathGeometry> can also be used to create more complex shapes, including arcs and curves.</span></span> <span data-ttu-id="18471-115">Örnekler için bkz. [elips yay oluşturma](how-to-create-an-elliptical-arc.md), [üçüncü dereceden Bezier eğrisi oluşturma](how-to-create-a-cubic-bezier-curve.md)ve [ikinci dereceden Bezier eğrisi](how-to-create-a-quadratic-bezier-curve.md)oluşturma.</span><span class="sxs-lookup"><span data-stu-id="18471-115">For examples, see [Create an Elliptical Arc](how-to-create-an-elliptical-arc.md), [Create a Cubic Bezier Curve](how-to-create-a-cubic-bezier-curve.md), and [Create a Quadratic Bezier Curve](how-to-create-a-quadratic-bezier-curve.md).</span></span>  
  
 <span data-ttu-id="18471-116">Bu örnek, daha büyük bir örnek parçasıdır; Tüm örnek için bkz. [geometriler örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span><span class="sxs-lookup"><span data-stu-id="18471-116">This example is part of larger sample; for the complete sample, see the [Geometries Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18471-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="18471-117">See also</span></span>

- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.GeometryDrawing>
- [<span data-ttu-id="18471-118">Geometriye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="18471-118">Geometry Overview</span></span>](geometry-overview.md)
- [<span data-ttu-id="18471-119">Geometriler örneği</span><span class="sxs-lookup"><span data-stu-id="18471-119">Geometries Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry)
