---
title: "Nasıl yapılır: Bileşik Şekil Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- shapes [WPF], composite
- composite shapes [WPF]
- graphics [WPF], composite shapes
ms.assetid: 8e5c7ef4-d7ed-4c43-afc9-ca01325c300b
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9ded7bd25f7f416bc512051f883b4ae12b2fa56d
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-create-a-composite-shape"></a><span data-ttu-id="cd336-102">Nasıl yapılır: Bileşik Şekil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="cd336-102">How to: Create a Composite Shape</span></span>
<span data-ttu-id="cd336-103">Bu örnek kullanarak bileşik şekillerin oluşturulacağını gösterir <xref:System.Windows.Media.Geometry> nesneleri ve bunları görüntülemek kullanarak bir <xref:System.Windows.Shapes.Path> öğesi.</span><span class="sxs-lookup"><span data-stu-id="cd336-103">This example shows how to create composite shapes using <xref:System.Windows.Media.Geometry> objects and display them using a <xref:System.Windows.Shapes.Path> element.</span></span> <span data-ttu-id="cd336-104">Aşağıdaki örnekte, bir <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.EllipseGeometry>ve bir <xref:System.Windows.Media.RectangleGeometry> ile kullanılan bir <xref:System.Windows.Media.GeometryGroup> bileşik bir şekil oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="cd336-104">In the following example, a <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.EllipseGeometry>, and a <xref:System.Windows.Media.RectangleGeometry> are used with a <xref:System.Windows.Media.GeometryGroup> to create a composite shape.</span></span> <span data-ttu-id="cd336-105">Kullanılarak geometri çizilir bir <xref:System.Windows.Shapes.Path> öğesi.</span><span class="sxs-lookup"><span data-stu-id="cd336-105">The geometries are then drawn using a <xref:System.Windows.Shapes.Path> element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd336-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="cd336-106">Example</span></span>  
 [!code-xaml[GeometrySample#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#19)]  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/CompositeShapeExample.cs#compositeshapecodeexampleinline1)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/compositeshapeexample.vb#compositeshapecodeexampleinline1)]  
  
 <span data-ttu-id="cd336-107">Aşağıdaki çizimde önceki örnekte oluşturulan şekli gösterir.</span><span class="sxs-lookup"><span data-stu-id="cd336-107">The following illustration shows the shape created in the previous example.</span></span>  
  
 <span data-ttu-id="cd336-108">![GeometryGroup kullanılarak oluşturulan bileşik geometri](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-compositegeometryexample1.jpg "wcpsdk_graphicsmm_compositegeometryexample1")</span><span class="sxs-lookup"><span data-stu-id="cd336-108">![A composite geometry created using a GeometryGroup](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-compositegeometryexample1.jpg "wcpsdk_graphicsmm_compositegeometryexample1")</span></span>  
<span data-ttu-id="cd336-109">Bileşik geometri</span><span class="sxs-lookup"><span data-stu-id="cd336-109">Composite Geometry</span></span>  
  
 <span data-ttu-id="cd336-110">Kullanarak çokgenler ve eğri kesimli şekiller gibi daha karmaşık şekiller oluşturulabilir bir <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="cd336-110">More complex shapes, such as polygons and shapes with curved segments, may be created using a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="cd336-111">Kullanarak bir şekil oluşturmak nasıl gösteren bir örnek için bir <xref:System.Windows.Media.PathGeometry>, bkz: [PathGeometry kullanarak bir şekil oluşturmak](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md).</span><span class="sxs-lookup"><span data-stu-id="cd336-111">For an example showing how to create a shape using a <xref:System.Windows.Media.PathGeometry>, see [Create a Shape by Using a PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md).</span></span>  <span data-ttu-id="cd336-112">Bu örnek kullanarak ekrana şekil işler ancak bir <xref:System.Windows.Shapes.Path> öğesi, <xref:System.Windows.Media.Geometry> nesnelerini ayrıca içeriğini tanımlamak için kullanılabilecek bir <xref:System.Windows.Media.GeometryDrawing> veya <xref:System.Windows.Media.DrawingContext>.</span><span class="sxs-lookup"><span data-stu-id="cd336-112">Although this example renders a shape to the screen using a <xref:System.Windows.Shapes.Path> element, <xref:System.Windows.Media.Geometry> objects may also be used to describe the contents of a <xref:System.Windows.Media.GeometryDrawing> or a <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="cd336-113">Bunlar, kırpma ve isabet testi için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cd336-113">They may also be used for clipping and hit-testing.</span></span>  
  
 <span data-ttu-id="cd336-114">Bu örnek daha büyük bir parçasıdır; tam bir örnek için bkz: [geometri örneği](http://go.microsoft.com/fwlink/?LinkID=159989).</span><span class="sxs-lookup"><span data-stu-id="cd336-114">This example is part of larger sample; for the complete sample, see the [Geometries Sample](http://go.microsoft.com/fwlink/?LinkID=159989).</span></span>
