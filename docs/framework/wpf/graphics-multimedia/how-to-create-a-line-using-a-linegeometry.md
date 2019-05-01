---
title: 'Nasıl yapılır: LineGeometry Kullanarak Çizgi Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], lines
ms.assetid: 41231b22-1f74-4c26-a8e7-a55b29f8f6bd
ms.openlocfilehash: f8c334a54f78aec7af91064a447fd18f23dcfbdc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61905209"
---
# <a name="how-to-create-a-line-using-a-linegeometry"></a><span data-ttu-id="3139f-102">Nasıl yapılır: LineGeometry Kullanarak Çizgi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="3139f-102">How to: Create a Line Using a LineGeometry</span></span>
<span data-ttu-id="3139f-103">Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.LineGeometry> bir satırı tanımlamak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="3139f-103">This example shows how to use the <xref:System.Windows.Media.LineGeometry> class to describe a line.</span></span> <span data-ttu-id="3139f-104">A <xref:System.Windows.Media.LineGeometry> kendi başlangıç ve bitiş noktası tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="3139f-104">A <xref:System.Windows.Media.LineGeometry> is defined by its start and end points.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3139f-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="3139f-105">Example</span></span>  
 <span data-ttu-id="3139f-106">Aşağıdaki örnek oluşturmak ve işlemek nasıl gösterir bir <xref:System.Windows.Media.LineGeometry>.</span><span class="sxs-lookup"><span data-stu-id="3139f-106">The following example shows how to create and render a <xref:System.Windows.Media.LineGeometry>.</span></span>  <span data-ttu-id="3139f-107">A <xref:System.Windows.Shapes.Path> öğesi satırı işlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3139f-107">A <xref:System.Windows.Shapes.Path> element is used to render the line.</span></span>  <span data-ttu-id="3139f-108">Bir satır, alanı olmadığından <xref:System.Windows.Shapes.Path> nesnenin <xref:System.Windows.Shapes.Shape.Fill%2A> belirtilmedi; bunun yerine <xref:System.Windows.Shapes.Shape.Stroke%2A> ve <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> özellikleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3139f-108">Since a line has no area, the <xref:System.Windows.Shapes.Path> object's <xref:System.Windows.Shapes.Shape.Fill%2A> is not specified; instead the <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> properties are used.</span></span>  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMLineGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmlinegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmlinegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmlinegeometryexample)]  
  
 <span data-ttu-id="3139f-109">![LineGeometry](./media/graphicsmm-line.gif "graphicsmm_line")</span><span class="sxs-lookup"><span data-stu-id="3139f-109">![A LineGeometry](./media/graphicsmm-line.gif "graphicsmm_line")</span></span>  
<span data-ttu-id="3139f-110">LineGeometry (10,20)'den alınan (100,130)</span><span class="sxs-lookup"><span data-stu-id="3139f-110">A LineGeometry drawn from (10,20) to (100,130)</span></span>  
  
 <span data-ttu-id="3139f-111">Diğer basit geometri sınıfları <xref:System.Windows.Media.LineGeometry> ve <xref:System.Windows.Media.EllipseGeometry>.</span><span class="sxs-lookup"><span data-stu-id="3139f-111">Other simple geometry classes include <xref:System.Windows.Media.LineGeometry> and <xref:System.Windows.Media.EllipseGeometry>.</span></span> <span data-ttu-id="3139f-112">Daha karmaşık olanları yanı sıra bu geometriler ayrıca kullanılarak oluşturulabilir bir <xref:System.Windows.Media.PathGeometry> veya <xref:System.Windows.Media.StreamGeometry>.</span><span class="sxs-lookup"><span data-stu-id="3139f-112">These geometries, as well as more complex ones, can also be created using a <xref:System.Windows.Media.PathGeometry> or <xref:System.Windows.Media.StreamGeometry>.</span></span> <span data-ttu-id="3139f-113">Daha fazla bilgi için [geometrisi](geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3139f-113">For more information, see the [Geometry Overview](geometry-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3139f-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3139f-114">See also</span></span>

- [<span data-ttu-id="3139f-115">Geometriye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3139f-115">Geometry Overview</span></span>](geometry-overview.md)
- [<span data-ttu-id="3139f-116">Bileşik Şekil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="3139f-116">Create a Composite Shape</span></span>](how-to-create-a-composite-shape.md)
- [<span data-ttu-id="3139f-117">PathGeometry Kullanarak Şekil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="3139f-117">Create a Shape by Using a PathGeometry</span></span>](how-to-create-a-shape-by-using-a-pathgeometry.md)
