---
title: "Nasıl yapılır: Görsel Taslak Kullanarak MediaElement'i Denetleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2341d2814e5bd42c652865c76d115defcc5b15b2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-control-a-mediaelement-by-using-a-storyboard"></a>Nasıl yapılır: Görsel Taslak Kullanarak MediaElement'i Denetleme
Bu örnek nasıl denetleneceğini gösterir bir <xref:System.Windows.Controls.MediaElement> kullanarak bir <xref:System.Windows.Media.MediaTimeline> içinde bir <xref:System.Windows.Media.Animation.Storyboard>.  
  
## <a name="example"></a>Örnek  
 Kullandığınızda, bir <xref:System.Windows.Media.MediaTimeline> içinde bir <xref:System.Windows.Media.Animation.Storyboard> zamanlamasını denetlemek için bir <xref:System.Windows.Controls.MediaElement>, diğer işlevselliğini özdeş bir işlevdir <xref:System.Windows.Media.Animation.Timeline> animasyonları gibi nesneler. Örneğin, bir <xref:System.Windows.Media.MediaTimeline> kullanan <xref:System.Windows.Media.Animation.Timeline> gibi özellikleri <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> zaman başlatılacağını belirtmek için özelliği bir <xref:System.Windows.Controls.MediaElement> (medya kayıttan yürütme Başlat). Ayrıca kullanır <xref:System.Windows.Media.Animation.Timeline.Duration%2A> özelliği belirtmek için ne kadar süreyle <xref:System.Windows.Controls.MediaElement> etkin (kayıttan yürütme süresi). Kullanma hakkında daha fazla bilgi için <xref:System.Windows.Media.Animation.Timeline> nesnelerini bir <xref:System.Windows.Media.Animation.Storyboard>, bkz: [film şeritleri genel bakış](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
 Bu örnek kullanan bir basit medya oynatıcı oluşturulacağını gösterir bir <xref:System.Windows.Media.MediaTimeline> kayıttan yürütmeyi denetlemek için. Yürütme, media player içerir duraklatma, sürdürme ve durdurma düğmeler. Player de sahip bir <xref:System.Windows.Controls.Slider> bir ilerleme çubuğu olarak davranan denetim.  
  
 Aşağıdaki örnekte [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] media player için.  
  
 [!code-xaml[MediaGallery_snip#MediaTimelineExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml#mediatimelineexamplewholepage)]  
  
 Aşağıdaki örnek, ilerleme çubuğu için işlevsellik oluşturur.  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaTimelineExample.xaml.cs#codebehindmediatimelineexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml.vb#codebehindmediatimelineexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.MediaElement>  
 <xref:System.Windows.Media.MediaTimeline>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 [(Play, duraklatma, durdurma, birim ve hız) MediaElement'i denetleme](../../../../docs/framework/wpf/graphics-multimedia/how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md)  
 [Film şeritleri genel bakış](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)  
 [Anahtar çerçeve animasyonları genel bakış](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Animasyon genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)  
 [Grafik ve çoklu ortam](../../../../docs/framework/wpf/graphics-multimedia/index.md)
