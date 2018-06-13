---
title: "Nasıl yapılır: Görsel Taslak Kullanarak MediaElement'i Denetleme"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- multimedia [WPF], controlling playback of media with Storyboards
- controlling playback of media [WPF], with Storyboards
- Storyboards [WPF], controlling playback of media with
- media [WPF], controlling playback with Storyboards
- playback of media [WPF], controlling with Storyboards
ms.assetid: 6128ca77-b826-4e36-b968-6f237157c543
ms.openlocfilehash: 88124d5b26a991a10b470c8cf0e587a5c7a4b10a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561615"
---
# <a name="how-to-control-a-mediaelement-by-using-a-storyboard"></a><span data-ttu-id="b2b46-102">Nasıl yapılır: Görsel Taslak Kullanarak MediaElement'i Denetleme</span><span class="sxs-lookup"><span data-stu-id="b2b46-102">How to: Control a MediaElement by Using a Storyboard</span></span>
<span data-ttu-id="b2b46-103">Bu örnek nasıl denetleneceğini gösterir bir <xref:System.Windows.Controls.MediaElement> kullanarak bir <xref:System.Windows.Media.MediaTimeline> içinde bir <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="b2b46-103">This example shows how to control a <xref:System.Windows.Controls.MediaElement> by using a <xref:System.Windows.Media.MediaTimeline> in a <xref:System.Windows.Media.Animation.Storyboard>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2b46-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="b2b46-104">Example</span></span>  
 <span data-ttu-id="b2b46-105">Kullandığınızda, bir <xref:System.Windows.Media.MediaTimeline> içinde bir <xref:System.Windows.Media.Animation.Storyboard> zamanlamasını denetlemek için bir <xref:System.Windows.Controls.MediaElement>, diğer işlevselliğini özdeş bir işlevdir <xref:System.Windows.Media.Animation.Timeline> animasyonları gibi nesneler.</span><span class="sxs-lookup"><span data-stu-id="b2b46-105">When you use a <xref:System.Windows.Media.MediaTimeline> in a <xref:System.Windows.Media.Animation.Storyboard> to control the timing of a <xref:System.Windows.Controls.MediaElement>, the functionality is identical to the functionality of other <xref:System.Windows.Media.Animation.Timeline> objects, such as animations.</span></span> <span data-ttu-id="b2b46-106">Örneğin, bir <xref:System.Windows.Media.MediaTimeline> kullanan <xref:System.Windows.Media.Animation.Timeline> gibi özellikleri <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> zaman başlatılacağını belirtmek için özelliği bir <xref:System.Windows.Controls.MediaElement> (medya kayıttan yürütme Başlat).</span><span class="sxs-lookup"><span data-stu-id="b2b46-106">For example, a <xref:System.Windows.Media.MediaTimeline> uses <xref:System.Windows.Media.Animation.Timeline> properties like the <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> property to specify when to start a <xref:System.Windows.Controls.MediaElement> (start media playback).</span></span> <span data-ttu-id="b2b46-107">Ayrıca kullanır <xref:System.Windows.Media.Animation.Timeline.Duration%2A> özelliği belirtmek için ne kadar süreyle <xref:System.Windows.Controls.MediaElement> etkin (kayıttan yürütme süresi).</span><span class="sxs-lookup"><span data-stu-id="b2b46-107">It also uses the <xref:System.Windows.Media.Animation.Timeline.Duration%2A> property to specify how long the <xref:System.Windows.Controls.MediaElement> is active (duration of media playback).</span></span> <span data-ttu-id="b2b46-108">Kullanma hakkında daha fazla bilgi için <xref:System.Windows.Media.Animation.Timeline> nesnelerini bir <xref:System.Windows.Media.Animation.Storyboard>, bkz: [film şeritleri genel bakış](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b2b46-108">For more information about using <xref:System.Windows.Media.Animation.Timeline> objects with a <xref:System.Windows.Media.Animation.Storyboard>, see [Storyboards Overview](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).</span></span>  
  
 <span data-ttu-id="b2b46-109">Bu örnek kullanan bir basit medya oynatıcı oluşturulacağını gösterir bir <xref:System.Windows.Media.MediaTimeline> kayıttan yürütmeyi denetlemek için.</span><span class="sxs-lookup"><span data-stu-id="b2b46-109">This example shows how to create a simple media player that uses a <xref:System.Windows.Media.MediaTimeline> to control playback.</span></span> <span data-ttu-id="b2b46-110">Yürütme, media player içerir duraklatma, sürdürme ve durdurma düğmeler.</span><span class="sxs-lookup"><span data-stu-id="b2b46-110">The media player includes play, pause, resume, and stop buttons.</span></span> <span data-ttu-id="b2b46-111">Player de sahip bir <xref:System.Windows.Controls.Slider> bir ilerleme çubuğu olarak davranan denetim.</span><span class="sxs-lookup"><span data-stu-id="b2b46-111">The player also has a <xref:System.Windows.Controls.Slider> control that acts as a progress bar.</span></span>  
  
 <span data-ttu-id="b2b46-112">Aşağıdaki örnekte [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] media player için.</span><span class="sxs-lookup"><span data-stu-id="b2b46-112">The following example creates the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] for the media player.</span></span>  
  
 [!code-xaml[MediaGallery_snip#MediaTimelineExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml#mediatimelineexamplewholepage)]  
  
 <span data-ttu-id="b2b46-113">Aşağıdaki örnek, ilerleme çubuğu için işlevsellik oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b2b46-113">The following example creates the functionality for the progress bar.</span></span>  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaTimelineExample.xaml.cs#codebehindmediatimelineexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml.vb#codebehindmediatimelineexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="b2b46-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b2b46-114">See Also</span></span>  
 <xref:System.Windows.Controls.MediaElement>  
 <xref:System.Windows.Media.MediaTimeline>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 [<span data-ttu-id="b2b46-115">MediaElement (Yürüt, Duraklat, Durdur, Ses Düzeyi ve Hız) Denetimi</span><span class="sxs-lookup"><span data-stu-id="b2b46-115">Control a MediaElement (Play, Pause, Stop, Volume, and Speed)</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md)  
 [<span data-ttu-id="b2b46-116">Görsel Taslaklara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b2b46-116">Storyboards Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)  
 [<span data-ttu-id="b2b46-117">Anahtar-Çerçeve Animasyonlara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b2b46-117">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="b2b46-118">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="b2b46-118">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="b2b46-119">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="b2b46-119">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)  
 [<span data-ttu-id="b2b46-120">Grafikler ve Multimedya</span><span class="sxs-lookup"><span data-stu-id="b2b46-120">Graphics and Multimedia</span></span>](../../../../docs/framework/wpf/graphics-multimedia/index.md)
