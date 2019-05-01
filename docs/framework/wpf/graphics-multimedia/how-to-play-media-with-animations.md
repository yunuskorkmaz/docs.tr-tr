---
title: 'Nasıl yapılır: Animasyonlarla Medya Yürütme'
ms.date: 03/30/2017
helpviewer_keywords:
- multimedia [WPF], playback with animations
- playback of media [WPF], with animations
- animation [WPF], media playback with
- media [WPF], playback with animations
ms.assetid: 8982b7b7-1c6c-4b24-8801-b328862975f5
ms.openlocfilehash: 200f9d62c67a02088fe5a5789cdb41a04837d430
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61921673"
---
# <a name="how-to-play-media-with-animations"></a>Nasıl yapılır: Animasyonlarla Medya Yürütme
Bu örnekte, medya ve animasyonları kullanarak aynı anda yürütmek gösterilmektedir <xref:System.Windows.Media.MediaTimeline> ve <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> aynı sınıfları <xref:System.Windows.Media.Animation.Storyboard>.  
  
## <a name="example"></a>Örnek  
 Bir veya daha fazla kullanabileceğiniz <xref:System.Windows.Media.MediaTimeline> nesneler bir <xref:System.Windows.Media.Animation.Storyboard> diğer birlikte <xref:System.Windows.Media.Animation.Timeline> animasyonları gibi nesneler.  
  
 Aşağıdaki örnek kümeleri <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A> özelliği <xref:System.Windows.Media.Animation.Storyboard> değerini `Slip`, animasyon kadar medya (Bu örnekte video) ilerledikçe ilerlemiyor belirtir. Medya kayıttan yürütme yükleme süresi nedeniyle Gecikmiş bu işlevselliği gerekebilir.  
  
 [!code-xaml[MediaGallery_snippet#MediaTimelinePlusAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snippet/CSharp/MediaTimelinePlusAnimationExample.xaml#mediatimelineplusanimationexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.MediaTimeline>
- <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>
- <xref:System.Windows.Media.Animation.Storyboard>
- <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A>
- [Nasıl Yapılır Konuları](audio-and-video-how-to-topics.md)
- [Görsel Taslaklara Genel Bakış](storyboards-overview.md)
- [Anahtar-Çerçeve Animasyonlara Genel Bakış](key-frame-animations-overview.md)
- [Animasyona Genel bakış](animation-overview.md)
- [Grafikler ve Multimedya](index.md)
