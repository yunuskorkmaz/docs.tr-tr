---
title: 'Nasıl yapılır: Video ile bir Alanı Boyama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- painting with a video [WPF]
- video [WPF], painting with
- brushes [WPF], painting with a video
ms.assetid: 04dd6600-4a6e-4b43-a93e-21cce7dfbcb8
ms.openlocfilehash: d2ca0f8b70abf6e895ea275d2a47eb4a6dd4bfe4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33560783"
---
# <a name="how-to-paint-an-area-with-a-video"></a><span data-ttu-id="9e00a-102">Nasıl yapılır: Video ile bir Alanı Boyama</span><span class="sxs-lookup"><span data-stu-id="9e00a-102">How to: Paint an Area with a Video</span></span>
<span data-ttu-id="9e00a-103">Bu örnek, bir alanı ortam ile boyamak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9e00a-103">This example shows how to paint an area with media.</span></span> <span data-ttu-id="9e00a-104">Bir alanı ortam ile boyamak için bir yoldur kullanmak için bir <xref:System.Windows.Controls.MediaElement> ile birlikte bir <xref:System.Windows.Media.VisualBrush>.</span><span class="sxs-lookup"><span data-stu-id="9e00a-104">One way to paint an area with media is to use a <xref:System.Windows.Controls.MediaElement> together with a <xref:System.Windows.Media.VisualBrush>.</span></span> <span data-ttu-id="9e00a-105">Kullanmak <xref:System.Windows.Controls.MediaElement> yüklemek ve medya yürütme ve ayarlamak için kullanmak için <xref:System.Windows.Media.VisualBrush.Visual%2A> özelliği <xref:System.Windows.Media.VisualBrush>.</span><span class="sxs-lookup"><span data-stu-id="9e00a-105">Use the <xref:System.Windows.Controls.MediaElement> to load and play the media, and then use it to set the <xref:System.Windows.Media.VisualBrush.Visual%2A> property of the <xref:System.Windows.Media.VisualBrush>.</span></span> <span data-ttu-id="9e00a-106">Daha sonra <xref:System.Windows.Media.VisualBrush> bir alanı yüklü ortam ile boyamak için.</span><span class="sxs-lookup"><span data-stu-id="9e00a-106">You can then use the <xref:System.Windows.Media.VisualBrush> to paint an area with the loaded media.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e00a-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="9e00a-107">Example</span></span>  
 <span data-ttu-id="9e00a-108">Aşağıdaki örnek kullanan bir <xref:System.Windows.Controls.MediaElement> ve <xref:System.Windows.Media.VisualBrush> boyamak için <xref:System.Windows.Controls.TextBlock.Foreground%2A> , bir <xref:System.Windows.Controls.TextBlock> video denetimiyle.</span><span class="sxs-lookup"><span data-stu-id="9e00a-108">The following example uses a <xref:System.Windows.Controls.MediaElement> and a <xref:System.Windows.Media.VisualBrush> to paint the <xref:System.Windows.Controls.TextBlock.Foreground%2A> of a <xref:System.Windows.Controls.TextBlock> control with video.</span></span> <span data-ttu-id="9e00a-109">Bu örnek ayarlar <xref:System.Windows.Controls.MediaElement.IsMuted%2A> özelliği <xref:System.Windows.Controls.MediaElement> için `true` böylece ses üretilmez.</span><span class="sxs-lookup"><span data-stu-id="9e00a-109">This example sets the <xref:System.Windows.Controls.MediaElement.IsMuted%2A> property of the <xref:System.Windows.Controls.MediaElement> to `true` so that it produces no sound.</span></span>  
  
 [!code-csharp[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/PaintWithVideoExample.cs#graphicsmmvideoastextbackgroundinline)]
 [!code-vb[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/paintwithvideoexample.vb#graphicsmmvideoastextbackgroundinline)]
 [!code-xaml[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/PaintWithVideoExample.xaml#graphicsmmvideoastextbackgroundinline)]  
  
## <a name="example"></a><span data-ttu-id="9e00a-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="9e00a-110">Example</span></span>  
 <span data-ttu-id="9e00a-111">Çünkü <xref:System.Windows.Media.VisualBrush> devraldığı <xref:System.Windows.Media.TileBrush> sınıfı, birkaç döşeme modu sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e00a-111">Because <xref:System.Windows.Media.VisualBrush> inherits from the <xref:System.Windows.Media.TileBrush> class, it provides several tiling modes.</span></span> <span data-ttu-id="9e00a-112">Ayarlayarak <xref:System.Windows.Media.TileBrush.TileMode%2A> özelliği bir <xref:System.Windows.Media.VisualBrush> için <xref:System.Windows.Media.TileMode.Tile> ayarlayarak kendi <xref:System.Windows.Media.TileBrush.Viewport%2A> özelliği boyama alandan daha küçük bir değere döşeli bir desen oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e00a-112">By setting the <xref:System.Windows.Media.TileBrush.TileMode%2A> property of a <xref:System.Windows.Media.VisualBrush> to <xref:System.Windows.Media.TileMode.Tile> and by setting its <xref:System.Windows.Media.TileBrush.Viewport%2A> property to a value smaller than the area that you are painting, you can create a tiled pattern.</span></span>  
  
 <span data-ttu-id="9e00a-113">Aşağıdaki örnek, önceki örnekte, hariç eşdeğerdir <xref:System.Windows.Media.VisualBrush> video bir desen oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9e00a-113">The following example is identical to the previous example, except that the <xref:System.Windows.Media.VisualBrush> generates a pattern from the video.</span></span>  
  
 [!code-csharp[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/PaintWithVideoExample.cs#graphicsmmvideoastextbackgroundtiledinline)]
 [!code-vb[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/paintwithvideoexample.vb#graphicsmmvideoastextbackgroundtiledinline)]
 [!code-xaml[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/PaintWithVideoExample.xaml#graphicsmmvideoastextbackgroundtiledinline)]  
  
 <span data-ttu-id="9e00a-114">Uygulamanız için bir medya dosyası gibi bir içerik dosyası ekleme hakkında bilgi için bkz: [WPF Uygulama kaynağı, içerik ve veri dosyalarını](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md).</span><span class="sxs-lookup"><span data-stu-id="9e00a-114">For information about how to add a content file, such as a media file, to your application, see [WPF Application Resource, Content, and Data Files](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md).</span></span> <span data-ttu-id="9e00a-115">Medya dosyası eklediğinizde, onu eklemeniz gerekir kaynak dosyası olarak değil bir içerik dosyası olarak.</span><span class="sxs-lookup"><span data-stu-id="9e00a-115">When you add a media file, you must add it as a content file, not as a resource file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e00a-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9e00a-116">See Also</span></span>  
 <xref:System.Windows.Media.VisualBrush>  
 [<span data-ttu-id="9e00a-117">Görüntüler, Çizimler ve Görsellerle Boyama</span><span class="sxs-lookup"><span data-stu-id="9e00a-117">Painting with Images, Drawings, and Visuals</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [<span data-ttu-id="9e00a-118">TileBrush’a Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9e00a-118">TileBrush Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/tilebrush-overview.md)  
 [<span data-ttu-id="9e00a-119">Multimedyaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9e00a-119">Multimedia Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/multimedia-overview.md)
