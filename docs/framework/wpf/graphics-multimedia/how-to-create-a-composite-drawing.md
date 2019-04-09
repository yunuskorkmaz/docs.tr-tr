---
title: 'Nasıl yapılır: Bileşik Çizim Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], composite
- composite drawings [WPF]
- graphics [WPF], composite drawings
ms.assetid: 066eb0ab-5f0e-439d-85c6-dca60af269fc
ms.openlocfilehash: 0af7fbca593627ebe8cd102a02617a27eac50aa5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59132476"
---
# <a name="how-to-create-a-composite-drawing"></a><span data-ttu-id="038d6-102">Nasıl yapılır: Bileşik Çizim Oluşturma</span><span class="sxs-lookup"><span data-stu-id="038d6-102">How to: Create a Composite Drawing</span></span>
<span data-ttu-id="038d6-103">Bu örnek nasıl kullanılacağını gösterir. bir <xref:System.Windows.Media.DrawingGroup> birden çok birleştirerek karmaşık çizimleri oluşturmak için <xref:System.Windows.Media.Drawing> tek bir bileşik çizim nesneleri.</span><span class="sxs-lookup"><span data-stu-id="038d6-103">This example shows how to use a <xref:System.Windows.Media.DrawingGroup> to create complex drawings by combining multiple <xref:System.Windows.Media.Drawing> objects into a single composite drawing.</span></span>  
  
## <a name="example"></a><span data-ttu-id="038d6-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="038d6-104">Example</span></span>  
 <span data-ttu-id="038d6-105">Aşağıdaki örnekte bir <xref:System.Windows.Media.DrawingGroup> bileşik çizim oluşturma <xref:System.Windows.Media.GeometryDrawing> ve <xref:System.Windows.Media.ImageDrawing> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="038d6-105">The following example uses a <xref:System.Windows.Media.DrawingGroup> to create a composite drawing from the <xref:System.Windows.Media.GeometryDrawing> and <xref:System.Windows.Media.ImageDrawing> objects.</span></span> <span data-ttu-id="038d6-106">Bu örneğin oluşturduğu çıktı aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="038d6-106">The following illustration shows the output that this example produces.</span></span>  
  
 <span data-ttu-id="038d6-107">![Birden çok çizimler DrawingGroup](./media/graphicsmm-simple.jpg "graphicsmm_simple")</span><span class="sxs-lookup"><span data-stu-id="038d6-107">![A DrawingGroup with multiple drawings](./media/graphicsmm-simple.jpg "graphicsmm_simple")</span></span>  
<span data-ttu-id="038d6-108">DrawingGroup kullanılarak oluşturulan bir bileşik çizim</span><span class="sxs-lookup"><span data-stu-id="038d6-108">A composite drawing that is created by using DrawingGroup</span></span>  
  
 <span data-ttu-id="038d6-109">Çizim sınırları gösteren gri kenarlık unutmayın.</span><span class="sxs-lookup"><span data-stu-id="038d6-109">Note the gray border, which shows the bounds of the drawing.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmsimpledrawinggroupexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmsimpledrawinggroupexample)]  
  
 <span data-ttu-id="038d6-110">Kullanabileceğiniz bir <xref:System.Windows.Media.DrawingGroup> uygulamak için bir <xref:System.Windows.Media.DrawingGroup.Transform%2A>, <xref:System.Windows.Media.DrawingGroup.Opacity%2A> ayarını <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>, <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>, <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>, veya <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> içerdiği çizimler için.</span><span class="sxs-lookup"><span data-stu-id="038d6-110">You can use a <xref:System.Windows.Media.DrawingGroup> to apply a <xref:System.Windows.Media.DrawingGroup.Transform%2A>, <xref:System.Windows.Media.DrawingGroup.Opacity%2A> setting, <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>, <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>, <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>, or <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> to the drawings it contains.</span></span> <span data-ttu-id="038d6-111">Çünkü bir <xref:System.Windows.Media.DrawingGroup> aynı zamanda bir <xref:System.Windows.Media.Drawing>, diğer içerebilir <xref:System.Windows.Media.DrawingGroup> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="038d6-111">Because a <xref:System.Windows.Media.DrawingGroup> is also a <xref:System.Windows.Media.Drawing>, it can contain other <xref:System.Windows.Media.DrawingGroup> objects.</span></span>  
  
 <span data-ttu-id="038d6-112">Ek kullanması hariç, aşağıdaki örnek önceki örneğe benzer <xref:System.Windows.Media.DrawingGroup> bit eşlem efektleri ve geçirgenlik maskesi bazı çizimlerde uygulamak için nesne.</span><span class="sxs-lookup"><span data-stu-id="038d6-112">The following example is similar to the preceding example, except that it uses additional <xref:System.Windows.Media.DrawingGroup> objects to apply bitmap effects and an opacity mask to some of its drawings.</span></span> <span data-ttu-id="038d6-113">Bu örneğin oluşturduğu çıktı aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="038d6-113">The following illustration shows the output that this example produces.</span></span>  
  
 <span data-ttu-id="038d6-114">![Birden çok çizimler DrawingGroup](./media/graphicsmm-multiple.jpg "graphicsmm_multiple")</span><span class="sxs-lookup"><span data-stu-id="038d6-114">![A DrawingGroup with multiple drawings](./media/graphicsmm-multiple.jpg "graphicsmm_multiple")</span></span>  
<span data-ttu-id="038d6-115">Bileşik çizim sahip birden fazla DrawingGroup nesneleri</span><span class="sxs-lookup"><span data-stu-id="038d6-115">Composite drawing that has multiple DrawingGroup objects</span></span>  
  
 <span data-ttu-id="038d6-116">Çizim sınırları gösteren gri kenarlık unutmayın.</span><span class="sxs-lookup"><span data-stu-id="038d6-116">Note the gray border, which shows the bounds of the drawing.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMMultipleDrawingGroupsExample](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmmultipledrawinggroupsexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMMultipleDrawingGroupsExample](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmmultipledrawinggroupsexample)]  
  
 <span data-ttu-id="038d6-117">Hakkında daha fazla bilgi için <xref:System.Windows.Media.Drawing> nesneleri bkz [çizim nesnelerine genel bakış](drawing-objects-overview.md).</span><span class="sxs-lookup"><span data-stu-id="038d6-117">For more information about <xref:System.Windows.Media.Drawing> objects, see [Drawing Objects Overview](drawing-objects-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="038d6-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="038d6-118">See also</span></span>

- <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>
- <xref:System.Windows.Media.DrawingGroup.Transform%2A>
- <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>
- <xref:System.Windows.Media.DrawingGroup.Opacity%2A>
- <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>
- <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>
- [<span data-ttu-id="038d6-119">Çizim Nesnelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="038d6-119">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
