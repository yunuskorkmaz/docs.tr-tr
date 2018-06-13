---
title: 'Nasıl yapılır: Animasyonlarla Medya Yürütme'
ms.date: 03/30/2017
helpviewer_keywords:
- multimedia [WPF], playback with animations
- playback of media [WPF], with animations
- animation [WPF], media playback with
- media [WPF], playback with animations
ms.assetid: 8982b7b7-1c6c-4b24-8801-b328862975f5
ms.openlocfilehash: 21c9b35828dca03c05def11cff22f1f1e33d45cc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33560281"
---
# <a name="how-to-play-media-with-animations"></a><span data-ttu-id="c621c-102">Nasıl yapılır: Animasyonlarla Medya Yürütme</span><span class="sxs-lookup"><span data-stu-id="c621c-102">How to: Play Media with Animations</span></span>
<span data-ttu-id="c621c-103">Bu örnek, medya ve animasyonların kullanarak aynı anda yürütme gösterilmiştir <xref:System.Windows.Media.MediaTimeline> ve <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> aynı sınıflarda <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="c621c-103">This example shows how to play media and animations at the same time by using the <xref:System.Windows.Media.MediaTimeline> and <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> classes in the same <xref:System.Windows.Media.Animation.Storyboard>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c621c-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="c621c-104">Example</span></span>  
 <span data-ttu-id="c621c-105">Bir veya daha fazlasını kullanabilirsiniz <xref:System.Windows.Media.MediaTimeline> nesnelerini bir <xref:System.Windows.Media.Animation.Storyboard> diğer birlikte <xref:System.Windows.Media.Animation.Timeline> animasyonları gibi nesneler.</span><span class="sxs-lookup"><span data-stu-id="c621c-105">You can use one or more <xref:System.Windows.Media.MediaTimeline> objects in a <xref:System.Windows.Media.Animation.Storyboard> together with other <xref:System.Windows.Media.Animation.Timeline> objects, such as animations.</span></span>  
  
 <span data-ttu-id="c621c-106">Aşağıdaki örnek kümeleri <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A> özelliği <xref:System.Windows.Media.Animation.Storyboard> değerine `Slip`, belirten animasyon kadar medya (Bu örnekte video) ilerledikçe ilerleme değil.</span><span class="sxs-lookup"><span data-stu-id="c621c-106">The following example sets the <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A> property of the <xref:System.Windows.Media.Animation.Storyboard> to a value of `Slip`, which specifies that the animation does not progress until the media (video in this example) progresses.</span></span> <span data-ttu-id="c621c-107">Yükleme süresi nedeniyle medya yürütmesini Gecikmeli ise bu işlev gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="c621c-107">This functionality might be needed if media playback is delayed because of loading time.</span></span>  
  
 [!code-xaml[MediaGallery_snippet#MediaTimelinePlusAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snippet/CSharp/MediaTimelinePlusAnimationExample.xaml#mediatimelineplusanimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="c621c-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c621c-108">See Also</span></span>  
 <xref:System.Windows.Media.MediaTimeline>  
 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A>  
 [<span data-ttu-id="c621c-109">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="c621c-109">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)  
 [<span data-ttu-id="c621c-110">Görsel Taslaklara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c621c-110">Storyboards Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)  
 [<span data-ttu-id="c621c-111">Anahtar-Çerçeve Animasyonlara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c621c-111">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="c621c-112">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="c621c-112">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="c621c-113">Grafikler ve Multimedya</span><span class="sxs-lookup"><span data-stu-id="c621c-113">Graphics and Multimedia</span></span>](../../../../docs/framework/wpf/graphics-multimedia/index.md)
