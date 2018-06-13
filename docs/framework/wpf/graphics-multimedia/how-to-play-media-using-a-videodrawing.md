---
title: 'Nasıl yapılır: VideoDrawing Kullanarak Medya Yürütme'
ms.date: 03/30/2017
helpviewer_keywords:
- playback of media [WPF]
- classes [WPF], MediaPlayer
ms.assetid: 165d47ed-22ce-4ded-aa6a-aa9b7467de87
ms.openlocfilehash: 27959cc967eac0a0f642da079f8758b0f756800e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33560977"
---
# <a name="how-to-play-media-using-a-videodrawing"></a><span data-ttu-id="4b93d-102">Nasıl yapılır: VideoDrawing Kullanarak Medya Yürütme</span><span class="sxs-lookup"><span data-stu-id="4b93d-102">How to: Play Media using a VideoDrawing</span></span>
<span data-ttu-id="4b93d-103">Bir ses veya video dosyasını oynatmak için kullandığınız bir <xref:System.Windows.Media.VideoDrawing> ve <xref:System.Windows.Media.MediaPlayer>.</span><span class="sxs-lookup"><span data-stu-id="4b93d-103">To play an audio or video file, you use a <xref:System.Windows.Media.VideoDrawing> and a <xref:System.Windows.Media.MediaPlayer>.</span></span> <span data-ttu-id="4b93d-104">Yük ve medya yürütmek için iki yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="4b93d-104">There are two ways to load and play media.</span></span> <span data-ttu-id="4b93d-105">İlk kullanmaktır bir <xref:System.Windows.Media.MediaPlayer> ve <xref:System.Windows.Media.VideoDrawing> kendilerini ve ikinci yolu kendi oluşturmaktır <xref:System.Windows.Media.MediaTimeline> ile kullanılacak <xref:System.Windows.Media.MediaPlayer> ve <xref:System.Windows.Media.VideoDrawing>.</span><span class="sxs-lookup"><span data-stu-id="4b93d-105">The first is to use a <xref:System.Windows.Media.MediaPlayer> and a <xref:System.Windows.Media.VideoDrawing> by themselves, and the second way is to create your own <xref:System.Windows.Media.MediaTimeline> to use with the <xref:System.Windows.Media.MediaPlayer> and <xref:System.Windows.Media.VideoDrawing>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4b93d-106">Bir görüntü gibi medyayı uygulamanız ile dağıtırken, bir medya dosyasını proje kaynağı olarak kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="4b93d-106">When distributing media with your application, you cannot use a media file as a project resource, like you would an image.</span></span> <span data-ttu-id="4b93d-107">Proje dosyanızda, bunun yerine medya türü ayarlamalısınız `Content` ve `CopyToOutputDirectory` için `PreserveNewest` veya `Always`.</span><span class="sxs-lookup"><span data-stu-id="4b93d-107">In your project file, you must instead set the media type to `Content` and set `CopyToOutputDirectory` to `PreserveNewest` or `Always`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b93d-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="4b93d-108">Example</span></span>  
 <span data-ttu-id="4b93d-109">Aşağıdaki örnek kullanan bir <xref:System.Windows.Media.VideoDrawing> ve <xref:System.Windows.Media.MediaPlayer> bir video dosyası bir kez oynatmak için.</span><span class="sxs-lookup"><span data-stu-id="4b93d-109">The following example uses a <xref:System.Windows.Media.VideoDrawing> and a <xref:System.Windows.Media.MediaPlayer> to play a video file once.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 <span data-ttu-id="4b93d-110">Medya üzerinde ek zamanlama denetim kazanmak için bir <xref:System.Windows.Media.MediaTimeline> ile <xref:System.Windows.Media.MediaPlayer> ve <xref:System.Windows.Media.VideoDrawing> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="4b93d-110">To gain additional timing control over the media, use a <xref:System.Windows.Media.MediaTimeline> with the <xref:System.Windows.Media.MediaPlayer> and <xref:System.Windows.Media.VideoDrawing> objects.</span></span> <span data-ttu-id="4b93d-111"><xref:System.Windows.Media.MediaTimeline> Video yinelenmesi gerektiğini belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="4b93d-111">The <xref:System.Windows.Media.MediaTimeline> enables you to specify whether the video should repeat.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b93d-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="4b93d-112">Example</span></span>  
 <span data-ttu-id="4b93d-113">Aşağıdaki örnek kullanan bir <xref:System.Windows.Media.MediaTimeline> ile <xref:System.Windows.Media.MediaPlayer> ve <xref:System.Windows.Media.VideoDrawing> art arda çalmasına nesneleri.</span><span class="sxs-lookup"><span data-stu-id="4b93d-113">The following example uses a <xref:System.Windows.Media.MediaTimeline> with the <xref:System.Windows.Media.MediaPlayer> and <xref:System.Windows.Media.VideoDrawing> objects to play a video repeatedly.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 <span data-ttu-id="4b93d-114">Kullandığınızda, Not bir <xref:System.Windows.Media.MediaTimeline>, etkileşimli kullandığınız <xref:System.Windows.Media.Animation.ClockController> döndürülen <xref:System.Windows.Media.Animation.Clock.Controller%2A> özelliği <xref:System.Windows.Media.MediaClock> etkileşimli yöntemlerinin yerine medya kayıttan yürütmeyi denetlemek için <xref:System.Windows.Media.MediaPlayer>.</span><span class="sxs-lookup"><span data-stu-id="4b93d-114">Note that, when you use a <xref:System.Windows.Media.MediaTimeline>, you use the interactive <xref:System.Windows.Media.Animation.ClockController> returned from the <xref:System.Windows.Media.Animation.Clock.Controller%2A> property of the <xref:System.Windows.Media.MediaClock> to control media playback instead of the interactive methods of <xref:System.Windows.Media.MediaPlayer>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b93d-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4b93d-115">See Also</span></span>  
 <xref:System.Windows.Media.VideoDrawing>  
 [<span data-ttu-id="4b93d-116">Çizim Nesnelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4b93d-116">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
