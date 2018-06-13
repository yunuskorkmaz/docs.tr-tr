---
title: 'Nasıl yapılır: LineGeometry Kullanarak Çizgi Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], lines
ms.assetid: 41231b22-1f74-4c26-a8e7-a55b29f8f6bd
ms.openlocfilehash: 8db33fc5c611dcbcae50c71ada1c6b6f9fd9bd29
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33560475"
---
# <a name="how-to-create-a-line-using-a-linegeometry"></a><span data-ttu-id="9480a-102">Nasıl yapılır: LineGeometry Kullanarak Çizgi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9480a-102">How to: Create a Line Using a LineGeometry</span></span>
<span data-ttu-id="9480a-103">Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.LineGeometry> bir satır açıklamak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="9480a-103">This example shows how to use the <xref:System.Windows.Media.LineGeometry> class to describe a line.</span></span> <span data-ttu-id="9480a-104">A <xref:System.Windows.Media.LineGeometry> kendi başlangıç ve bitiş noktaları tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="9480a-104">A <xref:System.Windows.Media.LineGeometry> is defined by its start and end points.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9480a-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="9480a-105">Example</span></span>  
 <span data-ttu-id="9480a-106">Aşağıdaki örnek oluşturma ve işleme gösterir bir <xref:System.Windows.Media.LineGeometry>.</span><span class="sxs-lookup"><span data-stu-id="9480a-106">The following example shows how to create and render a <xref:System.Windows.Media.LineGeometry>.</span></span>  <span data-ttu-id="9480a-107">A <xref:System.Windows.Shapes.Path> öğesi çizgiyi işlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9480a-107">A <xref:System.Windows.Shapes.Path> element is used to render the line.</span></span>  <span data-ttu-id="9480a-108">Bir çizginin hiçbir alan olmadığından <xref:System.Windows.Shapes.Path> nesnenin <xref:System.Windows.Shapes.Shape.Fill%2A> belirtilmedi; bunun yerine <xref:System.Windows.Shapes.Shape.Stroke%2A> ve <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> özellikleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9480a-108">Since a line has no area, the <xref:System.Windows.Shapes.Path> object's <xref:System.Windows.Shapes.Shape.Fill%2A> is not specified; instead the <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> properties are used.</span></span>  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmlinegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmlinegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmlinegeometryexample)]  
  
 <span data-ttu-id="9480a-109">![LineGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-line.gif "graphicsmm_line")</span><span class="sxs-lookup"><span data-stu-id="9480a-109">![A LineGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-line.gif "graphicsmm_line")</span></span>  
<span data-ttu-id="9480a-110">(10,20)'den (100,130) çizilen bir LineGeometry</span><span class="sxs-lookup"><span data-stu-id="9480a-110">A LineGeometry drawn from (10,20) to (100,130)</span></span>  
  
 <span data-ttu-id="9480a-111">Diğer basit geometri sınıfları dahil <xref:System.Windows.Media.LineGeometry> ve <xref:System.Windows.Media.EllipseGeometry>.</span><span class="sxs-lookup"><span data-stu-id="9480a-111">Other simple geometry classes include <xref:System.Windows.Media.LineGeometry> and <xref:System.Windows.Media.EllipseGeometry>.</span></span> <span data-ttu-id="9480a-112">Daha karmaşık olanları yanı sıra bu geometri ayrıca kullanılarak oluşturulabilir bir <xref:System.Windows.Media.PathGeometry> veya <xref:System.Windows.Media.StreamGeometry>.</span><span class="sxs-lookup"><span data-stu-id="9480a-112">These geometries, as well as more complex ones, can also be created using a <xref:System.Windows.Media.PathGeometry> or <xref:System.Windows.Media.StreamGeometry>.</span></span> <span data-ttu-id="9480a-113">Daha fazla bilgi için bkz: [geometrisi](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9480a-113">For more information, see the [Geometry Overview](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9480a-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9480a-114">See Also</span></span>  
 [<span data-ttu-id="9480a-115">Geometriye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9480a-115">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [<span data-ttu-id="9480a-116">Bileşik Şekil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9480a-116">Create a Composite Shape</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)  
 [<span data-ttu-id="9480a-117">PathGeometry Kullanarak Şekil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9480a-117">Create a Shape by Using a PathGeometry</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)
