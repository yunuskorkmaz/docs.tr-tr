---
title: "Nasıl yapılır: Görsel Taslak Kullanarak MediaElement'i Denetleme"
description: Windows Presentation Foundation 'da (WPF) görsel taslak kullanarak medyanın yürütülmesini denetleme. Basit medya oynatıcı oluşturmak için bu örneği göz önünde bulundurun.
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
ms.openlocfilehash: 5a5e41b9a28211495fd3374c1a51a655dd867bca
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853731"
---
# <a name="how-to-control-a-mediaelement-by-using-a-storyboard"></a><span data-ttu-id="9f916-104">Nasıl yapılır: Görsel Taslak Kullanarak MediaElement'i Denetleme</span><span class="sxs-lookup"><span data-stu-id="9f916-104">How to: Control a MediaElement by Using a Storyboard</span></span>
<span data-ttu-id="9f916-105">Bu örnek, içinde bir ile kullanılarak nasıl kontrol yapılacağını gösterir <xref:System.Windows.Controls.MediaElement> <xref:System.Windows.Media.MediaTimeline> <xref:System.Windows.Media.Animation.Storyboard> .</span><span class="sxs-lookup"><span data-stu-id="9f916-105">This example shows how to control a <xref:System.Windows.Controls.MediaElement> by using a <xref:System.Windows.Media.MediaTimeline> in a <xref:System.Windows.Media.Animation.Storyboard>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f916-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="9f916-106">Example</span></span>  
 <span data-ttu-id="9f916-107">Bir ' ın <xref:System.Windows.Media.MediaTimeline> ' a <xref:System.Windows.Media.Animation.Storyboard> zamanlamasını denetlemek için kullandığınızda <xref:System.Windows.Controls.MediaElement> , işlevselliği animasyonlar gibi diğer nesnelerin işlevselliğiyle aynıdır <xref:System.Windows.Media.Animation.Timeline> .</span><span class="sxs-lookup"><span data-stu-id="9f916-107">When you use a <xref:System.Windows.Media.MediaTimeline> in a <xref:System.Windows.Media.Animation.Storyboard> to control the timing of a <xref:System.Windows.Controls.MediaElement>, the functionality is identical to the functionality of other <xref:System.Windows.Media.Animation.Timeline> objects, such as animations.</span></span> <span data-ttu-id="9f916-108">Örneğin, bir, <xref:System.Windows.Media.MediaTimeline> <xref:System.Windows.Media.Animation.Timeline> <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> ne zaman başlatılacağını belirlemek için özelliği gibi özellikleri kullanır <xref:System.Windows.Controls.MediaElement> (medyayı kayıttan yürütmeyi Başlat).</span><span class="sxs-lookup"><span data-stu-id="9f916-108">For example, a <xref:System.Windows.Media.MediaTimeline> uses <xref:System.Windows.Media.Animation.Timeline> properties like the <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> property to specify when to start a <xref:System.Windows.Controls.MediaElement> (start media playback).</span></span> <span data-ttu-id="9f916-109">Ayrıca <xref:System.Windows.Media.Animation.Timeline.Duration%2A> , özelliğinin ne kadar süreyle <xref:System.Windows.Controls.MediaElement> etkin olduğunu (medya kayıttan yürütme süresi) belirtmek için özelliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="9f916-109">It also uses the <xref:System.Windows.Media.Animation.Timeline.Duration%2A> property to specify how long the <xref:System.Windows.Controls.MediaElement> is active (duration of media playback).</span></span> <span data-ttu-id="9f916-110">İle nesneleri kullanma hakkında daha fazla bilgi için <xref:System.Windows.Media.Animation.Timeline> <xref:System.Windows.Media.Animation.Storyboard> bkz. [Görsel Taslaklara Genel Bakış](storyboards-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9f916-110">For more information about using <xref:System.Windows.Media.Animation.Timeline> objects with a <xref:System.Windows.Media.Animation.Storyboard>, see [Storyboards Overview](storyboards-overview.md).</span></span>  
  
 <span data-ttu-id="9f916-111">Bu örnek, <xref:System.Windows.Media.MediaTimeline> kayıttan yürütmeyi denetlemek için kullanarak bir basit medya oynatıcı oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="9f916-111">This example shows how to create a simple media player that uses a <xref:System.Windows.Media.MediaTimeline> to control playback.</span></span> <span data-ttu-id="9f916-112">Medya oynatıcı oynat, Duraklat, devam ve Durdur düğmelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="9f916-112">The media player includes play, pause, resume, and stop buttons.</span></span> <span data-ttu-id="9f916-113">Player ayrıca <xref:System.Windows.Controls.Slider> ilerleme çubuğu olarak davranan bir denetime sahiptir.</span><span class="sxs-lookup"><span data-stu-id="9f916-113">The player also has a <xref:System.Windows.Controls.Slider> control that acts as a progress bar.</span></span>  
  
 <span data-ttu-id="9f916-114">Aşağıdaki örnek [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] medya oynatıcı için oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9f916-114">The following example creates the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] for the media player.</span></span>  
  
 [!code-xaml[MediaGallery_snip#MediaTimelineExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml#mediatimelineexamplewholepage)]  
  
 <span data-ttu-id="9f916-115">Aşağıdaki örnek, ilerleme çubuğu için işlevselliği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9f916-115">The following example creates the functionality for the progress bar.</span></span>  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaTimelineExample.xaml.cs#codebehindmediatimelineexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml.vb#codebehindmediatimelineexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="9f916-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9f916-116">See also</span></span>

- <xref:System.Windows.Controls.MediaElement>
- <xref:System.Windows.Media.MediaTimeline>
- <xref:System.Windows.Media.Animation.Storyboard>
- [<span data-ttu-id="9f916-117">MediaElement (Yürüt, Duraklat, Durdur, Ses Düzeyi ve Hız) Denetimi</span><span class="sxs-lookup"><span data-stu-id="9f916-117">Control a MediaElement (Play, Pause, Stop, Volume, and Speed)</span></span>](how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md)
- [<span data-ttu-id="9f916-118">Görsel Taslaklara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9f916-118">Storyboards Overview</span></span>](storyboards-overview.md)
- [<span data-ttu-id="9f916-119">Anahtar-Çerçeve Animasyonlara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9f916-119">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="9f916-120">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="9f916-120">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="9f916-121">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="9f916-121">How-to Topics</span></span>](audio-and-video-how-to-topics.md)
- [<span data-ttu-id="9f916-122">Grafikler ve multimedya</span><span class="sxs-lookup"><span data-stu-id="9f916-122">Graphics and Multimedia</span></span>](index.md)
