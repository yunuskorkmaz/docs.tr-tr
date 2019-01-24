---
title: 'Nasıl yapılır: RectangleGeometry Kullanarak Dikdörtgen Tanımlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], rectangles
- rectangles [WPF], creating with RectangleGeometry class
ms.assetid: e40b8a8e-54b8-416b-a9f2-be6dca9fdf0b
ms.openlocfilehash: 9c57f1536065af0bca1f3752179547daa502c066
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54511652"
---
# <a name="how-to-define-a-rectangle-using-a-rectanglegeometry"></a><span data-ttu-id="0afae-102">Nasıl yapılır: RectangleGeometry Kullanarak Dikdörtgen Tanımlama</span><span class="sxs-lookup"><span data-stu-id="0afae-102">How to: Define a Rectangle Using a RectangleGeometry</span></span>
<span data-ttu-id="0afae-103">Bu örnek nasıl kullanılacağını açıklar <xref:System.Windows.Media.RectangleGeometry> dikdörtgen açıklamak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="0afae-103">This example describes how to use the <xref:System.Windows.Media.RectangleGeometry> class to describe a rectangle.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0afae-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="0afae-104">Example</span></span>  
 <span data-ttu-id="0afae-105">Aşağıdaki örnek oluşturmak ve işlemek nasıl gösterir bir <xref:System.Windows.Media.RectangleGeometry>.</span><span class="sxs-lookup"><span data-stu-id="0afae-105">The following example shows how to create and render a <xref:System.Windows.Media.RectangleGeometry>.</span></span>  <span data-ttu-id="0afae-106">Göreli konum ve boyut dikdörtgenin tarafından tanımlanan bir <xref:System.Windows.Rect> yapısı.</span><span class="sxs-lookup"><span data-stu-id="0afae-106">The relative position and the dimensions of the rectangle are defined by a <xref:System.Windows.Rect> structure.</span></span> <span data-ttu-id="0afae-107">Göreli konumu `50,50` ve yüksekliğini ve genişliğini `25` kare oluşturma.</span><span class="sxs-lookup"><span data-stu-id="0afae-107">The relative position is `50,50` and the height and the width are both `25` creating a square.</span></span> <span data-ttu-id="0afae-108">Dikdörtgenin iç ile boyanacağını bir <xref:System.Windows.Media.Brushes.LemonChiffon%2A> fırça ve anahattı boyanır bir <xref:System.Windows.Media.Brushes.Black%2A> bir kalınlığı vuruşlu `1`.</span><span class="sxs-lookup"><span data-stu-id="0afae-108">The rectangle's interior is painted with a <xref:System.Windows.Media.Brushes.LemonChiffon%2A> brush and its outline is painted with a <xref:System.Windows.Media.Brushes.Black%2A> stroke with a thickness of `1`.</span></span>  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmrectanglegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmrectanglegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmrectanglegeometryexample)]  
  
 <span data-ttu-id="0afae-109">![RectangleGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rectangle.gif "graphicsmm_rectangle")</span><span class="sxs-lookup"><span data-stu-id="0afae-109">![A RectangleGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rectangle.gif "graphicsmm_rectangle")</span></span>  
<span data-ttu-id="0afae-110">RectangleGeometry</span><span class="sxs-lookup"><span data-stu-id="0afae-110">RectangleGeometry</span></span>  
  
 <span data-ttu-id="0afae-111">Bu örnekte kullanılan olsa da bir <xref:System.Windows.Shapes.Path> işlemek için <xref:System.Windows.Media.RectangleGeometry>, kullanmak için başka birçok yöntemle <xref:System.Windows.Media.RectangleGeometry> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="0afae-111">Although this example used a <xref:System.Windows.Shapes.Path> element to render the <xref:System.Windows.Media.RectangleGeometry>, there are many other ways to use <xref:System.Windows.Media.RectangleGeometry> objects.</span></span> <span data-ttu-id="0afae-112">Örneğin, bir <xref:System.Windows.Media.RectangleGeometry> belirtmek için kullanılan <xref:System.Windows.UIElement.Clip%2A> , bir <xref:System.Windows.UIElement> veya <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> , bir <xref:System.Windows.Media.GeometryDrawing>.</span><span class="sxs-lookup"><span data-stu-id="0afae-112">For example, a <xref:System.Windows.Media.RectangleGeometry> can be used to specify the <xref:System.Windows.UIElement.Clip%2A> of a <xref:System.Windows.UIElement> or the <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> of a <xref:System.Windows.Media.GeometryDrawing>.</span></span>  
  
 <span data-ttu-id="0afae-113">Diğer basit geometri sınıfları <xref:System.Windows.Media.LineGeometry> ve <xref:System.Windows.Media.EllipseGeometry>.</span><span class="sxs-lookup"><span data-stu-id="0afae-113">Other simple geometry classes include <xref:System.Windows.Media.LineGeometry> and <xref:System.Windows.Media.EllipseGeometry>.</span></span> <span data-ttu-id="0afae-114">Daha karmaşık olanları yanı sıra bu geometriler ayrıca kullanılarak oluşturulabilir bir <xref:System.Windows.Media.PathGeometry> veya <xref:System.Windows.Media.StreamGeometry>.</span><span class="sxs-lookup"><span data-stu-id="0afae-114">These geometries, as well as more complex ones, can also be created using a <xref:System.Windows.Media.PathGeometry> or <xref:System.Windows.Media.StreamGeometry>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0afae-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0afae-115">See also</span></span>
- [<span data-ttu-id="0afae-116">Geometriye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0afae-116">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)
- [<span data-ttu-id="0afae-117">Bileşik Şekil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0afae-117">Create a Composite Shape</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)
- [<span data-ttu-id="0afae-118">PathGeometry Kullanarak Şekil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0afae-118">Create a Shape by Using a PathGeometry</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)
