---
title: 'Nasıl yapılır: Bileşik Çizim Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], composite
- composite drawings [WPF]
- graphics [WPF], composite drawings
ms.assetid: 066eb0ab-5f0e-439d-85c6-dca60af269fc
ms.openlocfilehash: bb222fff11c81b491c0413f174539ff0005d11b8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561599"
---
# <a name="how-to-create-a-composite-drawing"></a><span data-ttu-id="90ca5-102">Nasıl yapılır: Bileşik Çizim Oluşturma</span><span class="sxs-lookup"><span data-stu-id="90ca5-102">How to: Create a Composite Drawing</span></span>
<span data-ttu-id="90ca5-103">Bu örnek nasıl kullanılacağını gösteren bir <xref:System.Windows.Media.DrawingGroup> birden çok birleştirerek karmaşık çizimler oluşturmak için <xref:System.Windows.Media.Drawing> tek bileşik çizim nesnelerine.</span><span class="sxs-lookup"><span data-stu-id="90ca5-103">This example shows how to use a <xref:System.Windows.Media.DrawingGroup> to create complex drawings by combining multiple <xref:System.Windows.Media.Drawing> objects into a single composite drawing.</span></span>  
  
## <a name="example"></a><span data-ttu-id="90ca5-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="90ca5-104">Example</span></span>  
 <span data-ttu-id="90ca5-105">Aşağıdaki örnek kullanan bir <xref:System.Windows.Media.DrawingGroup> çizim bileşik oluşturmak için <xref:System.Windows.Media.GeometryDrawing> ve <xref:System.Windows.Media.ImageDrawing> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="90ca5-105">The following example uses a <xref:System.Windows.Media.DrawingGroup> to create a composite drawing from the <xref:System.Windows.Media.GeometryDrawing> and <xref:System.Windows.Media.ImageDrawing> objects.</span></span> <span data-ttu-id="90ca5-106">Bu örneğin oluşturduğu çıktı aşağıda gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="90ca5-106">The following illustration shows the output that this example produces.</span></span>  
  
 <span data-ttu-id="90ca5-107">![Birden çok çizimler DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple.jpg "graphicsmm_simple")</span><span class="sxs-lookup"><span data-stu-id="90ca5-107">![A DrawingGroup with multiple drawings](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-simple.jpg "graphicsmm_simple")</span></span>  
<span data-ttu-id="90ca5-108">DrawingGroup kullanılarak oluşturulan bir bileşik çizim</span><span class="sxs-lookup"><span data-stu-id="90ca5-108">A composite drawing that is created by using DrawingGroup</span></span>  
  
 <span data-ttu-id="90ca5-109">Çizim sınırlarına gösterir gri kenarlık unutmayın.</span><span class="sxs-lookup"><span data-stu-id="90ca5-109">Note the gray border, which shows the bounds of the drawing.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmsimpledrawinggroupexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmsimpledrawinggroupexample)]  
  
 <span data-ttu-id="90ca5-110">Kullanabileceğiniz bir <xref:System.Windows.Media.DrawingGroup> uygulamak için bir <xref:System.Windows.Media.DrawingGroup.Transform%2A>, <xref:System.Windows.Media.DrawingGroup.Opacity%2A> ayarı <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>, <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>, <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>, veya <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> içerdiği çizimler için.</span><span class="sxs-lookup"><span data-stu-id="90ca5-110">You can use a <xref:System.Windows.Media.DrawingGroup> to apply a <xref:System.Windows.Media.DrawingGroup.Transform%2A>, <xref:System.Windows.Media.DrawingGroup.Opacity%2A> setting, <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>, <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>, <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>, or <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> to the drawings it contains.</span></span> <span data-ttu-id="90ca5-111">Çünkü bir <xref:System.Windows.Media.DrawingGroup> aynı zamanda bir <xref:System.Windows.Media.Drawing>, diğer içerebilir <xref:System.Windows.Media.DrawingGroup> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="90ca5-111">Because a <xref:System.Windows.Media.DrawingGroup> is also a <xref:System.Windows.Media.Drawing>, it can contain other <xref:System.Windows.Media.DrawingGroup> objects.</span></span>  
  
 <span data-ttu-id="90ca5-112">Ek kullanan aşağıdaki örnek önceki örneğe benzerdir <xref:System.Windows.Media.DrawingGroup> bazı çizimlerde bit eşlem efektleri ve geçirgenlik maskesi uygulamak için nesneleri.</span><span class="sxs-lookup"><span data-stu-id="90ca5-112">The following example is similar to the preceding example, except that it uses additional <xref:System.Windows.Media.DrawingGroup> objects to apply bitmap effects and an opacity mask to some of its drawings.</span></span> <span data-ttu-id="90ca5-113">Bu örneğin oluşturduğu çıktı aşağıda gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="90ca5-113">The following illustration shows the output that this example produces.</span></span>  
  
 <span data-ttu-id="90ca5-114">![Birden çok çizimler DrawingGroup](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-multiple.jpg "graphicsmm_multiple")</span><span class="sxs-lookup"><span data-stu-id="90ca5-114">![A DrawingGroup with multiple drawings](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-multiple.jpg "graphicsmm_multiple")</span></span>  
<span data-ttu-id="90ca5-115">Birden çok DrawingGroup nesneleri bileşik çizim sahip</span><span class="sxs-lookup"><span data-stu-id="90ca5-115">Composite drawing that has multiple DrawingGroup objects</span></span>  
  
 <span data-ttu-id="90ca5-116">Çizim sınırlarına gösterir gri kenarlık unutmayın.</span><span class="sxs-lookup"><span data-stu-id="90ca5-116">Note the gray border, which shows the bounds of the drawing.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMMultipleDrawingGroupsExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmmultipledrawinggroupsexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMMultipleDrawingGroupsExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmmultipledrawinggroupsexample)]  
  
 <span data-ttu-id="90ca5-117">Hakkında daha fazla bilgi için <xref:System.Windows.Media.Drawing> nesneleri bkz [çizim nesnelere genel bakış](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md).</span><span class="sxs-lookup"><span data-stu-id="90ca5-117">For more information about <xref:System.Windows.Media.Drawing> objects, see [Drawing Objects Overview](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90ca5-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="90ca5-118">See Also</span></span>  
 <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>  
 <xref:System.Windows.Media.DrawingGroup.Transform%2A>  
 <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>  
 <xref:System.Windows.Media.DrawingGroup.Opacity%2A>  
 <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>  
 <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>  
 [<span data-ttu-id="90ca5-119">Çizim Nesnelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="90ca5-119">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
