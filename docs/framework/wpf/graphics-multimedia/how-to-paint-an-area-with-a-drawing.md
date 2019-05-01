---
title: 'Nasıl yapılır: Çizim ile bir Alanı Boyama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], painting with drawings
- painting [WPF], with drawings
- drawings [WPF], painting with
ms.assetid: c10dc4b1-09b1-41e8-ad14-456b5fb377df
ms.openlocfilehash: 6b204ae631912181333e2559ebadcdc37e7693b7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62010091"
---
# <a name="how-to-paint-an-area-with-a-drawing"></a><span data-ttu-id="d7646-102">Nasıl yapılır: Çizim ile bir Alanı Boyama</span><span class="sxs-lookup"><span data-stu-id="d7646-102">How to: Paint an Area with a Drawing</span></span>
<span data-ttu-id="d7646-103">Bu örnek, bir çizim ile bir alanı boyama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d7646-103">This example shows how to paint an area with a drawing.</span></span> <span data-ttu-id="d7646-104">Çizim ile bir alanı boyama için kullandığınız bir <xref:System.Windows.Media.DrawingBrush> ve bir veya daha fazla <xref:System.Windows.Media.Drawing> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="d7646-104">To paint an area with a drawing, you use a <xref:System.Windows.Media.DrawingBrush> and one or more <xref:System.Windows.Media.Drawing> objects.</span></span>   <span data-ttu-id="d7646-105">Aşağıdaki örnekte bir <xref:System.Windows.Media.DrawingBrush> iki elips çizim ile bir nesneyi boyamak için.</span><span class="sxs-lookup"><span data-stu-id="d7646-105">The following example uses a <xref:System.Windows.Media.DrawingBrush> to paint an object with a drawing of two ellipses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7646-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="d7646-106">Example</span></span>  
 [!code-xaml[drawingbrush_snip#DrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_snip/CS/DrawingBrushExample.xaml#drawingbrushexamplewholepage)]  
  
 [!code-csharp[drawingbrush_procedural_snip#DrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_procedural_snip/CSharp/DrawingBrushExample.cs#drawingbrushexamplewholepage)]
 [!code-vb[drawingbrush_procedural_snip#DrawingBrushExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/drawingbrush_procedural_snip/VisualBasic/DrawingBrushExample.vb#drawingbrushexamplewholepage)]  
  
 <span data-ttu-id="d7646-107">Örnekteki çıktı aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d7646-107">The following illustration shows the example's output.</span></span>  
  
 <span data-ttu-id="d7646-108">![DrawingBrush ' çıkış](./media/graphicsmm-drawingbrush-simple.png "graphicsmm_drawingbrush_simple")</span><span class="sxs-lookup"><span data-stu-id="d7646-108">![Output from a DrawingBrush](./media/graphicsmm-drawingbrush-simple.png "graphicsmm_drawingbrush_simple")</span></span>  
  
 <span data-ttu-id="d7646-109">(Açıklanan sebeplerden dolayı şeklin Orta beyaz [bileşik şeklin dolgusunu denetleme](how-to-control-the-fill-of-a-composite-shape.md).)</span><span class="sxs-lookup"><span data-stu-id="d7646-109">(The center of the shape is white for reasons described in     [Control the Fill of a Composite Shape](how-to-control-the-fill-of-a-composite-shape.md).)</span></span>  
  
 <span data-ttu-id="d7646-110">Ayarlayarak bir <xref:System.Windows.Media.DrawingBrush> nesnenin <xref:System.Windows.Media.TileBrush.Viewport%2A> ve <xref:System.Windows.Media.TileBrush.TileMode%2A> özellikleri, yinelenen bir desen oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d7646-110">By setting a <xref:System.Windows.Media.DrawingBrush> object's <xref:System.Windows.Media.TileBrush.Viewport%2A> and <xref:System.Windows.Media.TileBrush.TileMode%2A> properties, you can create a repeating pattern.</span></span> <span data-ttu-id="d7646-111">Aşağıdaki örnek, bir nesne iki elips Çizimden oluşturulan bir desen ile boyar.</span><span class="sxs-lookup"><span data-stu-id="d7646-111">The following example paints an object with a pattern created from a drawing of two ellipses.</span></span>  
  
 [!code-xaml[drawingbrush_snip#TiledDrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_snip/CS/TiledDrawingBrushExample.xaml#tileddrawingbrushexamplewholepage)]  
  
 [!code-csharp[drawingbrush_procedural_snip#TiledDrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_procedural_snip/CSharp/TiledDrawingBrushExample.cs#tileddrawingbrushexamplewholepage)]
 [!code-vb[drawingbrush_procedural_snip#TiledDrawingBrushExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/drawingbrush_procedural_snip/VisualBasic/TiledDrawingBrushExample.vb#tileddrawingbrushexamplewholepage)]  
  
 <span data-ttu-id="d7646-112">Aşağıdaki çizim döşenmiş gösterir <xref:System.Windows.Media.DrawingBrush> çıktı.</span><span class="sxs-lookup"><span data-stu-id="d7646-112">The following illustration shows the tiled <xref:System.Windows.Media.DrawingBrush> output.</span></span>  
  
 <span data-ttu-id="d7646-113">![Döşeli DrawingBrush çıkışı](./media/graphicsmm-drawingbrush-tiled.png "graphicsmm_drawingbrush_tiled")</span><span class="sxs-lookup"><span data-stu-id="d7646-113">![Tiled output from a DrawingBrush](./media/graphicsmm-drawingbrush-tiled.png "graphicsmm_drawingbrush_tiled")</span></span>  
  
 <span data-ttu-id="d7646-114">Çizim fırçaları hakkında daha fazla bilgi için bkz. [görüntüler, çizimler ve görsellerle boyama](painting-with-images-drawings-and-visuals.md).</span><span class="sxs-lookup"><span data-stu-id="d7646-114">For more information about drawing brushes, see [Painting with Images, Drawings, and Visuals](painting-with-images-drawings-and-visuals.md).</span></span> <span data-ttu-id="d7646-115">Hakkında daha fazla bilgi için <xref:System.Windows.Media.Drawing> nesneleri bkz [çizim nesnelerine genel bakış](drawing-objects-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d7646-115">For more information about <xref:System.Windows.Media.Drawing> objects, see the [Drawing Objects Overview](drawing-objects-overview.md).</span></span>
