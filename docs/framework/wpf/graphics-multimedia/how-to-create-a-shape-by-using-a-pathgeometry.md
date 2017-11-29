---
title: "Nasıl yapılır: PathGeometry Kullanarak Şekil Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- shapes [WPF], creating with PathGeometry class
- graphics [WPF], shapes
ms.assetid: 49a4a8b7-e738-45be-8dac-b54a6d8f5b21
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 31f77f0921bb018317834077f70e4623c47a4f7f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-shape-by-using-a-pathgeometry"></a><span data-ttu-id="aa08c-102">Nasıl yapılır: PathGeometry Kullanarak Şekil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="aa08c-102">How to: Create a Shape by Using a PathGeometry</span></span>
<span data-ttu-id="aa08c-103">Bu örnek kullanılarak bir şeklin oluşturulacağını gösterir <xref:System.Windows.Media.PathGeometry> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="aa08c-103">This example shows how to create a shape using the <xref:System.Windows.Media.PathGeometry> class.</span></span> <span data-ttu-id="aa08c-104"><xref:System.Windows.Media.PathGeometry>nesnelerinden oluşan bir veya daha fazla <xref:System.Windows.Media.PathFigure> nesneleri; her <xref:System.Windows.Media.PathFigure> farklı "Şekil" veya şekli temsil eder.</span><span class="sxs-lookup"><span data-stu-id="aa08c-104"><xref:System.Windows.Media.PathGeometry> objects are composed of one or more <xref:System.Windows.Media.PathFigure> objects; each <xref:System.Windows.Media.PathFigure> represents a different "figure" or shape.</span></span> <span data-ttu-id="aa08c-105">Her <xref:System.Windows.Media.PathFigure> kendisini bir veya daha fazla oluşur <xref:System.Windows.Media.PathSegment> , her biri bir resim veya şeklin bağlı bir bölümünü temsil eden nesneler.</span><span class="sxs-lookup"><span data-stu-id="aa08c-105">Each <xref:System.Windows.Media.PathFigure> is itself composed of one or more <xref:System.Windows.Media.PathSegment> objects, each representing a connected portion of the figure or shape.</span></span> <span data-ttu-id="aa08c-106">Segment türler <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.ArcSegment>, ve <xref:System.Windows.Media.BezierSegment>.</span><span class="sxs-lookup"><span data-stu-id="aa08c-106">Segment types include <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.ArcSegment>, and <xref:System.Windows.Media.BezierSegment>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa08c-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="aa08c-107">Example</span></span>  
 <span data-ttu-id="aa08c-108">Aşağıdaki örnek kullanan bir <xref:System.Windows.Media.PathGeometry> bir üçgen oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="aa08c-108">The following example uses a <xref:System.Windows.Media.PathGeometry> to create a triangle.</span></span> <span data-ttu-id="aa08c-109"><xref:System.Windows.Media.PathGeometry> Kullanılarak görüntülenen bir <xref:System.Windows.Shapes.Path> öğesi.</span><span class="sxs-lookup"><span data-stu-id="aa08c-109">The  <xref:System.Windows.Media.PathGeometry> is displayed using a <xref:System.Windows.Shapes.Path> element.</span></span>  
  
 [!code-xaml[GeometrySample#49](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#49)]  
  
 <span data-ttu-id="aa08c-110">Aşağıdaki çizimde önceki örnekte oluşturulan şekli gösterir.</span><span class="sxs-lookup"><span data-stu-id="aa08c-110">The following illustration shows the shape created in the previous example.</span></span>  
  
 <span data-ttu-id="aa08c-111">![PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-pathgeometry-triangle.gif "wcpsdk_graphicsmm_pathgeometry_triangle")</span><span class="sxs-lookup"><span data-stu-id="aa08c-111">![A PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-pathgeometry-triangle.gif "wcpsdk_graphicsmm_pathgeometry_triangle")</span></span>  
<span data-ttu-id="aa08c-112">PathGeometry ile oluşturulan bir üçgen</span><span class="sxs-lookup"><span data-stu-id="aa08c-112">A triangle created with a PathGeometry</span></span>  
  
 <span data-ttu-id="aa08c-113">Önceki örnekte oldukça basit bir şekil, bir üçgen nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="aa08c-113">The previous example showed how to create a relatively simple shape, a triangle.</span></span> <span data-ttu-id="aa08c-114">A <xref:System.Windows.Media.PathGeometry> yaylar ve eğrileri gibi daha karmaşık şekilleri oluşturmak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="aa08c-114">A <xref:System.Windows.Media.PathGeometry> can also be used to create more complex shapes, including arcs and curves.</span></span> <span data-ttu-id="aa08c-115">Örnekler için bkz: [elips yay oluşturma](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-an-elliptical-arc.md), [küp Bezier eğrisi oluşturmak](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md), ve [ikinci dereceden Bezier eğrisi oluşturmak](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md).</span><span class="sxs-lookup"><span data-stu-id="aa08c-115">For examples, see [Create an Elliptical Arc](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-an-elliptical-arc.md), [Create a Cubic Bezier Curve](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md), and [Create a Quadratic Bezier Curve](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md).</span></span>  
  
 <span data-ttu-id="aa08c-116">Bu örnek daha büyük bir parçasıdır; tam bir örnek için bkz: [geometri örneği](http://go.microsoft.com/fwlink/?LinkID=159989).</span><span class="sxs-lookup"><span data-stu-id="aa08c-116">This example is part of larger sample; for the complete sample, see the [Geometries Sample](http://go.microsoft.com/fwlink/?LinkID=159989).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa08c-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="aa08c-117">See Also</span></span>  
 <xref:System.Windows.Shapes.Path>  
 <xref:System.Windows.Media.GeometryDrawing>  
 [<span data-ttu-id="aa08c-118">Geometri genel bakış</span><span class="sxs-lookup"><span data-stu-id="aa08c-118">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [<span data-ttu-id="aa08c-119">Geometri örneği</span><span class="sxs-lookup"><span data-stu-id="aa08c-119">Geometries Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=159989)
