---
title: "Nasıl yapılır: Kullanıcı Olayı ile Medya Yürütme Tetikleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- synchronizing media playback with events [WPF]
- playback of media [WPF], synchronizing with events
- media [WPF], synchronizing playback with events
- multimedia [WPF], synchronizing media playback with events
ms.assetid: c4dbe632-6e7f-4d7f-9df5-98737a758bc3
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aa93b757f0af38bc6b08d87ac5485e2bf0f45a1c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-trigger-media-playback-with-a-user-event"></a><span data-ttu-id="ac6a4-102">Nasıl yapılır: Kullanıcı Olayı ile Medya Yürütme Tetikleme</span><span class="sxs-lookup"><span data-stu-id="ac6a4-102">How to: Trigger Media Playback with a User Event</span></span>
<span data-ttu-id="ac6a4-103">Bu örnek, bir olay medya kayıttan yürütme eşitlemek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ac6a4-103">This example shows how to synchronize media playback with an event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac6a4-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="ac6a4-104">Example</span></span>  
 <span data-ttu-id="ac6a4-105">Aşağıdaki örnek kullanır <xref:System.Windows.Controls.MediaElement> denetim ve <xref:System.Windows.Media.MediaTimeline> kullanıcı tıklattığında oluşan bir ses çalınmaya sınıfı bir <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="ac6a4-105">The following example uses the <xref:System.Windows.Controls.MediaElement> control and the <xref:System.Windows.Media.MediaTimeline> class to play a sound that occurs when the user clicks a <xref:System.Windows.Controls.Button>.</span></span>  
  
 [!code-xaml[MediaGallery_snippet#SoundFromUserEventExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snippet/CSharp/SoundFromUserEventExample.xaml#soundfromusereventexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="ac6a4-106">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ac6a4-106">See Also</span></span>  
 <xref:System.Windows.Controls.MediaElement>  
 <xref:System.Windows.Media.MediaTimeline>  
 <xref:System.Windows.EventTrigger.RoutedEvent%2A>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 [<span data-ttu-id="ac6a4-107">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="ac6a4-107">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)  
 [<span data-ttu-id="ac6a4-108">Grafikler ve Multimedya</span><span class="sxs-lookup"><span data-stu-id="ac6a4-108">Graphics and Multimedia</span></span>](../../../../docs/framework/wpf/graphics-multimedia/index.md)
