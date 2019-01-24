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
ms.openlocfilehash: c5995359486bcc415b048256c772ec5012b066f0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580206"
---
# <a name="how-to-paint-an-area-with-a-video"></a><span data-ttu-id="9d069-102">Nasıl yapılır: Video ile bir Alanı Boyama</span><span class="sxs-lookup"><span data-stu-id="9d069-102">How to: Paint an Area with a Video</span></span>
<span data-ttu-id="9d069-103">Bu örnekte, medya ile bir alanı boyama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9d069-103">This example shows how to paint an area with media.</span></span> <span data-ttu-id="9d069-104">Medya ile bir alanı boyama tek bir yolu bir <xref:System.Windows.Controls.MediaElement> ile birlikte bir <xref:System.Windows.Media.VisualBrush>.</span><span class="sxs-lookup"><span data-stu-id="9d069-104">One way to paint an area with media is to use a <xref:System.Windows.Controls.MediaElement> together with a <xref:System.Windows.Media.VisualBrush>.</span></span> <span data-ttu-id="9d069-105">Kullanma <xref:System.Windows.Controls.MediaElement> yük medya yürütme ve ayarlamak için kullanın <xref:System.Windows.Media.VisualBrush.Visual%2A> özelliği <xref:System.Windows.Media.VisualBrush>.</span><span class="sxs-lookup"><span data-stu-id="9d069-105">Use the <xref:System.Windows.Controls.MediaElement> to load and play the media, and then use it to set the <xref:System.Windows.Media.VisualBrush.Visual%2A> property of the <xref:System.Windows.Media.VisualBrush>.</span></span> <span data-ttu-id="9d069-106">Ardından <xref:System.Windows.Media.VisualBrush> yüklenen medyanın ile bir alanı boyama için.</span><span class="sxs-lookup"><span data-stu-id="9d069-106">You can then use the <xref:System.Windows.Media.VisualBrush> to paint an area with the loaded media.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d069-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="9d069-107">Example</span></span>  
 <span data-ttu-id="9d069-108">Aşağıdaki örnekte bir <xref:System.Windows.Controls.MediaElement> ve <xref:System.Windows.Media.VisualBrush> boyanacak <xref:System.Windows.Controls.TextBlock.Foreground%2A> , bir <xref:System.Windows.Controls.TextBlock> video denetimi.</span><span class="sxs-lookup"><span data-stu-id="9d069-108">The following example uses a <xref:System.Windows.Controls.MediaElement> and a <xref:System.Windows.Media.VisualBrush> to paint the <xref:System.Windows.Controls.TextBlock.Foreground%2A> of a <xref:System.Windows.Controls.TextBlock> control with video.</span></span> <span data-ttu-id="9d069-109">Bu örnekte ayarlar <xref:System.Windows.Controls.MediaElement.IsMuted%2A> özelliği <xref:System.Windows.Controls.MediaElement> için `true` böylece ses üretir.</span><span class="sxs-lookup"><span data-stu-id="9d069-109">This example sets the <xref:System.Windows.Controls.MediaElement.IsMuted%2A> property of the <xref:System.Windows.Controls.MediaElement> to `true` so that it produces no sound.</span></span>  
  
 [!code-csharp[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/PaintWithVideoExample.cs#graphicsmmvideoastextbackgroundinline)]
 [!code-vb[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/paintwithvideoexample.vb#graphicsmmvideoastextbackgroundinline)]
 [!code-xaml[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/PaintWithVideoExample.xaml#graphicsmmvideoastextbackgroundinline)]  
  
## <a name="example"></a><span data-ttu-id="9d069-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="9d069-110">Example</span></span>  
 <span data-ttu-id="9d069-111">Çünkü <xref:System.Windows.Media.VisualBrush> devraldığı <xref:System.Windows.Media.TileBrush> sınıfı birkaç döşeme modu sağlar.</span><span class="sxs-lookup"><span data-stu-id="9d069-111">Because <xref:System.Windows.Media.VisualBrush> inherits from the <xref:System.Windows.Media.TileBrush> class, it provides several tiling modes.</span></span> <span data-ttu-id="9d069-112">Ayarlayarak <xref:System.Windows.Media.TileBrush.TileMode%2A> özelliği bir <xref:System.Windows.Media.VisualBrush> için <xref:System.Windows.Media.TileMode.Tile> ayarlayarak onun <xref:System.Windows.Media.TileBrush.Viewport%2A> özelliği'nın boyama yaptığınız alandan daha küçük bir değere döşenmiş bir desen oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9d069-112">By setting the <xref:System.Windows.Media.TileBrush.TileMode%2A> property of a <xref:System.Windows.Media.VisualBrush> to <xref:System.Windows.Media.TileMode.Tile> and by setting its <xref:System.Windows.Media.TileBrush.Viewport%2A> property to a value smaller than the area that you are painting, you can create a tiled pattern.</span></span>  
  
 <span data-ttu-id="9d069-113">Aşağıdaki örnek dışında önceki örnekle aynıdır <xref:System.Windows.Media.VisualBrush> videodan bir düzeni oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9d069-113">The following example is identical to the previous example, except that the <xref:System.Windows.Media.VisualBrush> generates a pattern from the video.</span></span>  
  
 [!code-csharp[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/PaintWithVideoExample.cs#graphicsmmvideoastextbackgroundtiledinline)]
 [!code-vb[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/paintwithvideoexample.vb#graphicsmmvideoastextbackgroundtiledinline)]
 [!code-xaml[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/PaintWithVideoExample.xaml#graphicsmmvideoastextbackgroundtiledinline)]  
  
 <span data-ttu-id="9d069-114">Uygulamanız için bir medya dosyası gibi bir içerik dosyası ekleme hakkında daha fazla bilgi için bkz. [WPF Uygulama kaynağı, içerik ve veri dosyalarını](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md).</span><span class="sxs-lookup"><span data-stu-id="9d069-114">For information about how to add a content file, such as a media file, to your application, see [WPF Application Resource, Content, and Data Files](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md).</span></span> <span data-ttu-id="9d069-115">Bir medya dosyası eklediğinizde, onu eklemeniz gerekir kaynak dosyası olarak değil bir içerik dosyası olarak.</span><span class="sxs-lookup"><span data-stu-id="9d069-115">When you add a media file, you must add it as a content file, not as a resource file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d069-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d069-116">See also</span></span>
- <xref:System.Windows.Media.VisualBrush>
- [<span data-ttu-id="9d069-117">Görüntüler, Çizimler ve Görsellerle Boyama</span><span class="sxs-lookup"><span data-stu-id="9d069-117">Painting with Images, Drawings, and Visuals</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
- [<span data-ttu-id="9d069-118">TileBrush’a Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9d069-118">TileBrush Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/tilebrush-overview.md)
- [<span data-ttu-id="9d069-119">Multimedyaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9d069-119">Multimedia Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/multimedia-overview.md)
