---
title: 'Nasıl yapılır: VideoDrawing Kullanarak Medya Yürütme'
ms.date: 03/30/2017
helpviewer_keywords:
- playback of media [WPF]
- classes [WPF], MediaPlayer
ms.assetid: 165d47ed-22ce-4ded-aa6a-aa9b7467de87
ms.openlocfilehash: 2e2007525be770186a17cf9d2d42a7c52ba93fba
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956962"
---
# <a name="how-to-play-media-using-a-videodrawing"></a><span data-ttu-id="8933d-102">Nasıl yapılır: VideoDrawing Kullanarak Medya Yürütme</span><span class="sxs-lookup"><span data-stu-id="8933d-102">How to: Play Media using a VideoDrawing</span></span>
<span data-ttu-id="8933d-103">Ses veya video dosyası oynatmak için bir <xref:System.Windows.Media.VideoDrawing> <xref:System.Windows.Media.MediaPlayer>ve kullanın.</span><span class="sxs-lookup"><span data-stu-id="8933d-103">To play an audio or video file, you use a <xref:System.Windows.Media.VideoDrawing> and a <xref:System.Windows.Media.MediaPlayer>.</span></span> <span data-ttu-id="8933d-104">Medyayı yüklemek ve oynatmak için kullanabileceğiniz iki yol vardır.</span><span class="sxs-lookup"><span data-stu-id="8933d-104">There are two ways to load and play media.</span></span> <span data-ttu-id="8933d-105">Birincisi <xref:System.Windows.Media.MediaPlayer> <xref:System.Windows.Media.MediaTimeline> <xref:System.Windows.Media.MediaPlayer> <xref:System.Windows.Media.VideoDrawing>, ve ' ı kendi başlarına ve ikinci şekilde, ve ile kullanmak için kendi oluşturmanız gerekir. <xref:System.Windows.Media.VideoDrawing></span><span class="sxs-lookup"><span data-stu-id="8933d-105">The first is to use a <xref:System.Windows.Media.MediaPlayer> and a <xref:System.Windows.Media.VideoDrawing> by themselves, and the second way is to create your own <xref:System.Windows.Media.MediaTimeline> to use with the <xref:System.Windows.Media.MediaPlayer> and <xref:System.Windows.Media.VideoDrawing>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8933d-106">Medyayı uygulamanızla dağıtırken, bir görüntü gibi bir proje kaynağı olarak bir medya dosyası kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="8933d-106">When distributing media with your application, you cannot use a media file as a project resource, like you would an image.</span></span> <span data-ttu-id="8933d-107">Proje dosyanızda, bunun yerine medya `Content` türünü olarak ayarlamanız ve ya `Always`da olarak `PreserveNewest` ayarlamanız `CopyToOutputDirectory` gerekir.</span><span class="sxs-lookup"><span data-stu-id="8933d-107">In your project file, you must instead set the media type to `Content` and set `CopyToOutputDirectory` to `PreserveNewest` or `Always`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8933d-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="8933d-108">Example</span></span>  
 <span data-ttu-id="8933d-109">Aşağıdaki örnek, bir video <xref:System.Windows.Media.VideoDrawing> dosyasını bir <xref:System.Windows.Media.MediaPlayer> kez çalmak için bir ve bir kullanır.</span><span class="sxs-lookup"><span data-stu-id="8933d-109">The following example uses a <xref:System.Windows.Media.VideoDrawing> and a <xref:System.Windows.Media.MediaPlayer> to play a video file once.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 <span data-ttu-id="8933d-110">Medya üzerinde ek zamanlama denetimi kazanmak için, <xref:System.Windows.Media.MediaTimeline> <xref:System.Windows.Media.MediaPlayer> ve <xref:System.Windows.Media.VideoDrawing> nesneleriyle bir kullanın.</span><span class="sxs-lookup"><span data-stu-id="8933d-110">To gain additional timing control over the media, use a <xref:System.Windows.Media.MediaTimeline> with the <xref:System.Windows.Media.MediaPlayer> and <xref:System.Windows.Media.VideoDrawing> objects.</span></span> <span data-ttu-id="8933d-111">Videonun yinelenmesi gerekip gerekmediğini belirtmenizi sağlar.<xref:System.Windows.Media.MediaTimeline></span><span class="sxs-lookup"><span data-stu-id="8933d-111">The <xref:System.Windows.Media.MediaTimeline> enables you to specify whether the video should repeat.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8933d-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="8933d-112">Example</span></span>  
 <span data-ttu-id="8933d-113">Aşağıdaki örnek, <xref:System.Windows.Media.MediaTimeline> <xref:System.Windows.Media.MediaPlayer> bir videoyu art arda oynatmak <xref:System.Windows.Media.VideoDrawing> için ve nesneleriyle birlikte kullanır.</span><span class="sxs-lookup"><span data-stu-id="8933d-113">The following example uses a <xref:System.Windows.Media.MediaTimeline> with the <xref:System.Windows.Media.MediaPlayer> and <xref:System.Windows.Media.VideoDrawing> objects to play a video repeatedly.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 <span data-ttu-id="8933d-114"><xref:System.Windows.Media.MediaTimeline>' I kullandığınızda, ' ın <xref:System.Windows.Media.Animation.Clock.Controller%2A> özelliğinden <xref:System.Windows.Media.MediaClock> döndürülen etkileşimli <xref:System.Windows.Media.Animation.ClockController> öğesini, uygulamasının <xref:System.Windows.Media.MediaPlayer>etkileşimli yöntemleri yerine medya kayıttan yürütmeyi denetlemek için kullanacağınızı unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8933d-114">Note that, when you use a <xref:System.Windows.Media.MediaTimeline>, you use the interactive <xref:System.Windows.Media.Animation.ClockController> returned from the <xref:System.Windows.Media.Animation.Clock.Controller%2A> property of the <xref:System.Windows.Media.MediaClock> to control media playback instead of the interactive methods of <xref:System.Windows.Media.MediaPlayer>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8933d-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8933d-115">See also</span></span>

- <xref:System.Windows.Media.VideoDrawing>
- [<span data-ttu-id="8933d-116">Çizim Nesnelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8933d-116">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
