---
title: "Nasıl yapılır: Animasyonlarla Medya Yürütme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- multimedia [WPF], playback with animations
- playback of media [WPF], with animations
- animation [WPF], media playback with
- media [WPF], playback with animations
ms.assetid: 8982b7b7-1c6c-4b24-8801-b328862975f5
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fb5fd3575a0caa692e4a4013452e3069210c9a4c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-play-media-with-animations"></a>Nasıl yapılır: Animasyonlarla Medya Yürütme
Bu örnek, medya ve animasyonların kullanarak aynı anda yürütme gösterilmiştir <xref:System.Windows.Media.MediaTimeline> ve <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> aynı sınıflarda <xref:System.Windows.Media.Animation.Storyboard>.  
  
## <a name="example"></a>Örnek  
 Bir veya daha fazlasını kullanabilirsiniz <xref:System.Windows.Media.MediaTimeline> nesnelerini bir <xref:System.Windows.Media.Animation.Storyboard> diğer birlikte <xref:System.Windows.Media.Animation.Timeline> animasyonları gibi nesneler.  
  
 Aşağıdaki örnek kümeleri <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A> özelliği <xref:System.Windows.Media.Animation.Storyboard> değerine `Slip`, belirten animasyon kadar medya (Bu örnekte video) ilerledikçe ilerleme değil. Yükleme süresi nedeniyle medya yürütmesini Gecikmeli ise bu işlev gerekebilir.  
  
 [!code-xaml[MediaGallery_snippet#MediaTimelinePlusAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snippet/CSharp/MediaTimelinePlusAnimationExample.xaml#mediatimelineplusanimationexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.MediaTimeline>  
 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A>  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)  
 [Film şeritleri genel bakış](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)  
 [Anahtar çerçeve animasyonları genel bakış](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Animasyon genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Grafik ve çoklu ortam](../../../../docs/framework/wpf/graphics-multimedia/index.md)
