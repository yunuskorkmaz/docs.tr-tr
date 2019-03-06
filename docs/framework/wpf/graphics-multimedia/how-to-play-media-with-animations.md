---
title: 'Nasıl yapılır: Animasyonlarla Medya Yürütme'
ms.date: 03/30/2017
helpviewer_keywords:
- multimedia [WPF], playback with animations
- playback of media [WPF], with animations
- animation [WPF], media playback with
- media [WPF], playback with animations
ms.assetid: 8982b7b7-1c6c-4b24-8801-b328862975f5
ms.openlocfilehash: 0dc39d08ef17a628675018c17602623f2efd0173
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372912"
---
# <a name="how-to-play-media-with-animations"></a><span data-ttu-id="11ebb-102">Nasıl yapılır: Animasyonlarla Medya Yürütme</span><span class="sxs-lookup"><span data-stu-id="11ebb-102">How to: Play Media with Animations</span></span>
<span data-ttu-id="11ebb-103">Bu örnekte, medya ve animasyonları kullanarak aynı anda yürütmek gösterilmektedir <xref:System.Windows.Media.MediaTimeline> ve <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> aynı sınıfları <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="11ebb-103">This example shows how to play media and animations at the same time by using the <xref:System.Windows.Media.MediaTimeline> and <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> classes in the same <xref:System.Windows.Media.Animation.Storyboard>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11ebb-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="11ebb-104">Example</span></span>  
 <span data-ttu-id="11ebb-105">Bir veya daha fazla kullanabileceğiniz <xref:System.Windows.Media.MediaTimeline> nesneler bir <xref:System.Windows.Media.Animation.Storyboard> diğer birlikte <xref:System.Windows.Media.Animation.Timeline> animasyonları gibi nesneler.</span><span class="sxs-lookup"><span data-stu-id="11ebb-105">You can use one or more <xref:System.Windows.Media.MediaTimeline> objects in a <xref:System.Windows.Media.Animation.Storyboard> together with other <xref:System.Windows.Media.Animation.Timeline> objects, such as animations.</span></span>  
  
 <span data-ttu-id="11ebb-106">Aşağıdaki örnek kümeleri <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A> özelliği <xref:System.Windows.Media.Animation.Storyboard> değerini `Slip`, animasyon kadar medya (Bu örnekte video) ilerledikçe ilerlemiyor belirtir.</span><span class="sxs-lookup"><span data-stu-id="11ebb-106">The following example sets the <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A> property of the <xref:System.Windows.Media.Animation.Storyboard> to a value of `Slip`, which specifies that the animation does not progress until the media (video in this example) progresses.</span></span> <span data-ttu-id="11ebb-107">Medya kayıttan yürütme yükleme süresi nedeniyle Gecikmiş bu işlevselliği gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="11ebb-107">This functionality might be needed if media playback is delayed because of loading time.</span></span>  
  
 [!code-xaml[MediaGallery_snippet#MediaTimelinePlusAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snippet/CSharp/MediaTimelinePlusAnimationExample.xaml#mediatimelineplusanimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="11ebb-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="11ebb-108">See also</span></span>
- <xref:System.Windows.Media.MediaTimeline>
- <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>
- <xref:System.Windows.Media.Animation.Storyboard>
- <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A>
- [<span data-ttu-id="11ebb-109">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="11ebb-109">How-to Topics</span></span>](audio-and-video-how-to-topics.md)
- [<span data-ttu-id="11ebb-110">Görsel Taslaklara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="11ebb-110">Storyboards Overview</span></span>](storyboards-overview.md)
- [<span data-ttu-id="11ebb-111">Anahtar-Çerçeve Animasyonlara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="11ebb-111">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="11ebb-112">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="11ebb-112">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="11ebb-113">Grafikler ve Multimedya</span><span class="sxs-lookup"><span data-stu-id="11ebb-113">Graphics and Multimedia</span></span>](index.md)
