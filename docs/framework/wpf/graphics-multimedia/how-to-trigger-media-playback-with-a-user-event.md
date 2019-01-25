---
title: 'Nasıl yapılır: Kullanıcı Olayı ile Medya Yürütme Tetikleme'
ms.date: 03/30/2017
helpviewer_keywords:
- synchronizing media playback with events [WPF]
- playback of media [WPF], synchronizing with events
- media [WPF], synchronizing playback with events
- multimedia [WPF], synchronizing media playback with events
ms.assetid: c4dbe632-6e7f-4d7f-9df5-98737a758bc3
ms.openlocfilehash: 5244c63aea0747c3d0f8d5bdd71496ccd3dc44d2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54530070"
---
# <a name="how-to-trigger-media-playback-with-a-user-event"></a><span data-ttu-id="bec7a-102">Nasıl yapılır: Kullanıcı Olayı ile Medya Yürütme Tetikleme</span><span class="sxs-lookup"><span data-stu-id="bec7a-102">How to: Trigger Media Playback with a User Event</span></span>
<span data-ttu-id="bec7a-103">Bu örnek, bir olayı ile medya kayıttan yürütme eşitlemek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bec7a-103">This example shows how to synchronize media playback with an event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bec7a-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="bec7a-104">Example</span></span>  
 <span data-ttu-id="bec7a-105">Aşağıdaki örnekte <xref:System.Windows.Controls.MediaElement> denetimi ve <xref:System.Windows.Media.MediaTimeline> kullanıcı tıkladığında gerçekleşen bir ses sınıfı bir <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="bec7a-105">The following example uses the <xref:System.Windows.Controls.MediaElement> control and the <xref:System.Windows.Media.MediaTimeline> class to play a sound that occurs when the user clicks a <xref:System.Windows.Controls.Button>.</span></span>  
  
 [!code-xaml[MediaGallery_snippet#SoundFromUserEventExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snippet/CSharp/SoundFromUserEventExample.xaml#soundfromusereventexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="bec7a-106">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bec7a-106">See also</span></span>
- <xref:System.Windows.Controls.MediaElement>
- <xref:System.Windows.Media.MediaTimeline>
- <xref:System.Windows.EventTrigger.RoutedEvent%2A>
- <xref:System.Windows.Media.Animation.Storyboard>
- [<span data-ttu-id="bec7a-107">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="bec7a-107">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)
- [<span data-ttu-id="bec7a-108">Grafikler ve Multimedya</span><span class="sxs-lookup"><span data-stu-id="bec7a-108">Graphics and Multimedia</span></span>](../../../../docs/framework/wpf/graphics-multimedia/index.md)
