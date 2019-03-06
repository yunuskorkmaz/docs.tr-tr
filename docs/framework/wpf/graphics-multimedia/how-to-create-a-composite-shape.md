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
ms.openlocfilehash: de9f7972c7a51ea623c3630fe62bb48f6109317e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57353497"
---
# <a name="how-to-create-a-composite-shape"></a><span data-ttu-id="01b15-102">Nasıl yapılır: Bileşik Şekil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="01b15-102">How to: Create a Composite Shape</span></span>
<span data-ttu-id="01b15-103">Bu örnekte kullanarak bileşik şekil oluşturma işlemi gösterilmektedir <xref:System.Windows.Media.Geometry> nesneleri ve bunları görüntülemek kullanarak bir <xref:System.Windows.Shapes.Path> öğesi.</span><span class="sxs-lookup"><span data-stu-id="01b15-103">This example shows how to create composite shapes using <xref:System.Windows.Media.Geometry> objects and display them using a <xref:System.Windows.Shapes.Path> element.</span></span> <span data-ttu-id="01b15-104">Aşağıdaki örnekte, bir <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.EllipseGeometry>ve <xref:System.Windows.Media.RectangleGeometry> ile kullanılan bir <xref:System.Windows.Media.GeometryGroup> bileşik şekil oluşturma.</span><span class="sxs-lookup"><span data-stu-id="01b15-104">In the following example, a <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.EllipseGeometry>, and a <xref:System.Windows.Media.RectangleGeometry> are used with a <xref:System.Windows.Media.GeometryGroup> to create a composite shape.</span></span> <span data-ttu-id="01b15-105">Geometriler kullanılarak çizilir bir <xref:System.Windows.Shapes.Path> öğesi.</span><span class="sxs-lookup"><span data-stu-id="01b15-105">The geometries are then drawn using a <xref:System.Windows.Shapes.Path> element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01b15-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="01b15-106">Example</span></span>  
 [!code-xaml[GeometrySample#19](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#19)]  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/CompositeShapeExample.cs#compositeshapecodeexampleinline1)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/compositeshapeexample.vb#compositeshapecodeexampleinline1)]  
  
 <span data-ttu-id="01b15-107">Önceki örnekte oluşturulan şekli aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="01b15-107">The following illustration shows the shape created in the previous example.</span></span>  
  
 <span data-ttu-id="01b15-108">![GeometryGroup kullanılarak oluşturulan bir Birleşik Geometri](./media/wcpsdk-graphicsmm-compositegeometryexample1.jpg "wcpsdk_graphicsmm_compositegeometryexample1")</span><span class="sxs-lookup"><span data-stu-id="01b15-108">![A composite geometry created using a GeometryGroup](./media/wcpsdk-graphicsmm-compositegeometryexample1.jpg "wcpsdk_graphicsmm_compositegeometryexample1")</span></span>  
<span data-ttu-id="01b15-109">Birleşik Geometri</span><span class="sxs-lookup"><span data-stu-id="01b15-109">Composite Geometry</span></span>  
  
 <span data-ttu-id="01b15-110">Çokgen ve şekiller eğri kesimli gibi daha karmaşık şekiller kullanarak oluşturulabilir bir <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="01b15-110">More complex shapes, such as polygons and shapes with curved segments, may be created using a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="01b15-111">Kullanma şekli oluşturmayı gösteren bir örnek için bir <xref:System.Windows.Media.PathGeometry>, bkz: [PathGeometry kullanarak şekil oluşturma](how-to-create-a-shape-by-using-a-pathgeometry.md).</span><span class="sxs-lookup"><span data-stu-id="01b15-111">For an example showing how to create a shape using a <xref:System.Windows.Media.PathGeometry>, see [Create a Shape by Using a PathGeometry](how-to-create-a-shape-by-using-a-pathgeometry.md).</span></span>  <span data-ttu-id="01b15-112">Bu örnek ekran kullanarak bir şekil çizer rağmen bir <xref:System.Windows.Shapes.Path> öğesi <xref:System.Windows.Media.Geometry> nesneleri ayrıca içeriğini açıklamak için kullanılabilir bir <xref:System.Windows.Media.GeometryDrawing> veya <xref:System.Windows.Media.DrawingContext>.</span><span class="sxs-lookup"><span data-stu-id="01b15-112">Although this example renders a shape to the screen using a <xref:System.Windows.Shapes.Path> element, <xref:System.Windows.Media.Geometry> objects may also be used to describe the contents of a <xref:System.Windows.Media.GeometryDrawing> or a <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="01b15-113">Bunlar, kırpma ve isabet sınaması için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="01b15-113">They may also be used for clipping and hit-testing.</span></span>  
  
 <span data-ttu-id="01b15-114">Bu örnek, daha büyük örnek bir parçasıdır; tam bir örnek için bkz. [geometri örneği](https://go.microsoft.com/fwlink/?LinkID=159989).</span><span class="sxs-lookup"><span data-stu-id="01b15-114">This example is part of larger sample; for the complete sample, see the [Geometries Sample](https://go.microsoft.com/fwlink/?LinkID=159989).</span></span>
