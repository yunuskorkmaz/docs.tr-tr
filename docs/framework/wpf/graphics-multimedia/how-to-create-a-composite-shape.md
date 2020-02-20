---
title: 'Nasıl yapılır: Bileşik Şekil Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- shapes [WPF], composite
- composite shapes [WPF]
- graphics [WPF], composite shapes
ms.assetid: 8e5c7ef4-d7ed-4c43-afc9-ca01325c300b
ms.openlocfilehash: c56053f2b07d6055deac5097a68fd7b80ad704ba
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452103"
---
# <a name="how-to-create-a-composite-shape"></a><span data-ttu-id="73f5a-102">Nasıl yapılır: Bileşik Şekil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="73f5a-102">How to: Create a Composite Shape</span></span>
<span data-ttu-id="73f5a-103">Bu örnek, <xref:System.Windows.Media.Geometry> nesneleri kullanarak bileşik şekillerin nasıl oluşturulduğunu ve <xref:System.Windows.Shapes.Path> bir öğesi kullanarak nasıl görüntüleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="73f5a-103">This example shows how to create composite shapes using <xref:System.Windows.Media.Geometry> objects and display them using a <xref:System.Windows.Shapes.Path> element.</span></span> <span data-ttu-id="73f5a-104">Aşağıdaki örnekte, bir <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.EllipseGeometry>ve bir <xref:System.Windows.Media.RectangleGeometry> bileşik şekil oluşturmak için <xref:System.Windows.Media.GeometryGroup> ile birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="73f5a-104">In the following example, a <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.EllipseGeometry>, and a <xref:System.Windows.Media.RectangleGeometry> are used with a <xref:System.Windows.Media.GeometryGroup> to create a composite shape.</span></span> <span data-ttu-id="73f5a-105">Geometriler daha sonra bir <xref:System.Windows.Shapes.Path> öğesi kullanılarak çizilir.</span><span class="sxs-lookup"><span data-stu-id="73f5a-105">The geometries are then drawn using a <xref:System.Windows.Shapes.Path> element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73f5a-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="73f5a-106">Example</span></span>  
 [!code-xaml[GeometrySample#19](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#19)]  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/CompositeShapeExample.cs#compositeshapecodeexampleinline1)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/compositeshapeexample.vb#compositeshapecodeexampleinline1)]  
  
 <span data-ttu-id="73f5a-107">Aşağıdaki çizimde, önceki örnekte oluşturulan Şekil gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="73f5a-107">The following illustration shows the shape created in the previous example.</span></span>  
  
 <span data-ttu-id="73f5a-108">![GeometryGroup kullanılarak oluşturulan bileşik geometri](./media/wcpsdk-graphicsmm-compositegeometryexample1.jpg "wcpsdk_graphicsmm_compositegeometryexample1")</span><span class="sxs-lookup"><span data-stu-id="73f5a-108">![A composite geometry created using a GeometryGroup](./media/wcpsdk-graphicsmm-compositegeometryexample1.jpg "wcpsdk_graphicsmm_compositegeometryexample1")</span></span>  
<span data-ttu-id="73f5a-109">Bileşik geometri</span><span class="sxs-lookup"><span data-stu-id="73f5a-109">Composite Geometry</span></span>  
  
 <span data-ttu-id="73f5a-110"><xref:System.Windows.Media.PathGeometry>kullanılarak çokgenler ve eğri kesimli şekiller gibi daha karmaşık şekiller oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="73f5a-110">More complex shapes, such as polygons and shapes with curved segments, may be created using a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="73f5a-111"><xref:System.Windows.Media.PathGeometry>kullanarak şekil oluşturmayı gösteren bir örnek için, bkz. [PathGeometry kullanarak şekil oluşturma](how-to-create-a-shape-by-using-a-pathgeometry.md).</span><span class="sxs-lookup"><span data-stu-id="73f5a-111">For an example showing how to create a shape using a <xref:System.Windows.Media.PathGeometry>, see [Create a Shape by Using a PathGeometry](how-to-create-a-shape-by-using-a-pathgeometry.md).</span></span>  <span data-ttu-id="73f5a-112">Bu örnek, <xref:System.Windows.Shapes.Path> bir öğesi kullanarak ekrana bir şekil çizer, ancak <xref:System.Windows.Media.Geometry> nesneleri, bir <xref:System.Windows.Media.GeometryDrawing> veya bir <xref:System.Windows.Media.DrawingContext>içeriğini anlatmak için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="73f5a-112">Although this example renders a shape to the screen using a <xref:System.Windows.Shapes.Path> element, <xref:System.Windows.Media.Geometry> objects may also be used to describe the contents of a <xref:System.Windows.Media.GeometryDrawing> or a <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="73f5a-113">Bunlar, kırpma ve isabet testi için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="73f5a-113">They may also be used for clipping and hit-testing.</span></span>  
  
 <span data-ttu-id="73f5a-114">Bu örnek, daha büyük bir örnek parçasıdır; Tüm örnek için bkz. [geometriler örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span><span class="sxs-lookup"><span data-stu-id="73f5a-114">This example is part of larger sample; for the complete sample, see the [Geometries Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span></span>
