---
title: 'Nasıl yapılır: GeometryDrawing Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], renderable
- renderable shapes [WPF]
- graphics [WPF], GeometryDrawing class
- classes [WPF], GeometryDrawing
ms.assetid: 11d3c096-91ba-4d41-9bba-aeac0db70f97
ms.openlocfilehash: f5cdcfdb68ad8030bcbd6c689f45a8baddd000e1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59179796"
---
# <a name="how-to-create-a-geometrydrawing"></a><span data-ttu-id="1a75e-102">Nasıl yapılır: GeometryDrawing Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1a75e-102">How to: Create a GeometryDrawing</span></span>
<span data-ttu-id="1a75e-103">Bu örnek, oluşturmak ve görüntülemek nasıl gösterir. bir <xref:System.Windows.Media.GeometryDrawing>.</span><span class="sxs-lookup"><span data-stu-id="1a75e-103">This example shows how to create and display a <xref:System.Windows.Media.GeometryDrawing>.</span></span> <span data-ttu-id="1a75e-104">A <xref:System.Windows.Media.GeometryDrawing> ilişkilendirerek şeklin dolgu ile ana hat oluşturmanızı sağlayan bir <xref:System.Windows.Media.Pen> ve <xref:System.Windows.Media.Brush> ile bir <xref:System.Windows.Media.Geometry>.</span><span class="sxs-lookup"><span data-stu-id="1a75e-104">A <xref:System.Windows.Media.GeometryDrawing> enables you to create shape with a fill and an outline by associating a <xref:System.Windows.Media.Pen> and a <xref:System.Windows.Media.Brush> with a <xref:System.Windows.Media.Geometry>.</span></span> <span data-ttu-id="1a75e-105"><xref:System.Windows.Media.GeometryDrawing.Geometry%2A> Şeklin yapısını açıklar <xref:System.Windows.Media.GeometryDrawing.Brush%2A> şeklin dolgu açıklar ve <xref:System.Windows.Media.GeometryDrawing.Pen%2A> şeklin ana hat açıklar.</span><span class="sxs-lookup"><span data-stu-id="1a75e-105">The <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> describes the shape's structure, the <xref:System.Windows.Media.GeometryDrawing.Brush%2A> describes the shape's fill, and the <xref:System.Windows.Media.GeometryDrawing.Pen%2A> describes the shape's outline.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a75e-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="1a75e-106">Example</span></span>  
 <span data-ttu-id="1a75e-107">Aşağıdaki örnekte bir <xref:System.Windows.Media.GeometryDrawing> şekil işlemek için.</span><span class="sxs-lookup"><span data-stu-id="1a75e-107">The following example uses a <xref:System.Windows.Media.GeometryDrawing> to render a shape.</span></span> <span data-ttu-id="1a75e-108">Şekil tarafından açıklanan bir <xref:System.Windows.Media.GeometryGroup> ve iki <xref:System.Windows.Media.EllipseGeometry> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="1a75e-108">The shape is described by a <xref:System.Windows.Media.GeometryGroup> and two <xref:System.Windows.Media.EllipseGeometry> objects.</span></span> <span data-ttu-id="1a75e-109">Şeklin içinin ile boyanır bir <xref:System.Windows.Media.LinearGradientBrush> ve anahattı ile çizilen bir <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>.</span><span class="sxs-lookup"><span data-stu-id="1a75e-109">The shape's interior is painted with a <xref:System.Windows.Media.LinearGradientBrush> and its outline is drawn with a <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>.</span></span> <span data-ttu-id="1a75e-110"><xref:System.Windows.Media.GeometryDrawing> Kullanarak görüntülenen bir <xref:System.Windows.Media.ImageDrawing> ve <xref:System.Windows.Controls.Image> öğesi.</span><span class="sxs-lookup"><span data-stu-id="1a75e-110">The <xref:System.Windows.Media.GeometryDrawing> is displayed using an <xref:System.Windows.Media.ImageDrawing> and an <xref:System.Windows.Controls.Image> element.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#GeometryDrawingExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexamplewholepage)]  
  
 <span data-ttu-id="1a75e-111">Sonuç, aşağıdaki resimde gösterilmektedir <xref:System.Windows.Media.GeometryDrawing>.</span><span class="sxs-lookup"><span data-stu-id="1a75e-111">The following illustration shows the resulting <xref:System.Windows.Media.GeometryDrawing>.</span></span>  
  
 <span data-ttu-id="1a75e-112">![GeometryDrawing iki elips](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")</span><span class="sxs-lookup"><span data-stu-id="1a75e-112">![A GeometryDrawing of two ellipses](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")</span></span>  
  
 <span data-ttu-id="1a75e-113">Daha karmaşık çizimler için tek bir bileşik kullanarak çizim birden çok çizim nesneleri birleştirebilirsiniz. bir <xref:System.Windows.Media.DrawingGroup>.</span><span class="sxs-lookup"><span data-stu-id="1a75e-113">To create more complex drawings, you can combine multiple drawing objects into a single composite drawing using a <xref:System.Windows.Media.DrawingGroup>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a75e-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1a75e-114">See also</span></span>

- <xref:System.Windows.Media.DrawingGroup>
- [<span data-ttu-id="1a75e-115">Çizim Nesnelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="1a75e-115">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="1a75e-116">Geometriye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="1a75e-116">Geometry Overview</span></span>](geometry-overview.md)
- [<span data-ttu-id="1a75e-117">Bileşik Çizim Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1a75e-117">Create a Composite Drawing</span></span>](how-to-create-a-composite-drawing.md)
