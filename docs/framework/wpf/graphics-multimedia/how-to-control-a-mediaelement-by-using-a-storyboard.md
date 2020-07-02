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
# <a name="how-to-control-a-mediaelement-by-using-a-storyboard"></a>Nasıl yapılır: Görsel Taslak Kullanarak MediaElement'i Denetleme
Bu örnek, içinde bir ile kullanılarak nasıl kontrol yapılacağını gösterir <xref:System.Windows.Controls.MediaElement> <xref:System.Windows.Media.MediaTimeline> <xref:System.Windows.Media.Animation.Storyboard> .  
  
## <a name="example"></a>Örnek  
 Bir ' ın <xref:System.Windows.Media.MediaTimeline> ' a <xref:System.Windows.Media.Animation.Storyboard> zamanlamasını denetlemek için kullandığınızda <xref:System.Windows.Controls.MediaElement> , işlevselliği animasyonlar gibi diğer nesnelerin işlevselliğiyle aynıdır <xref:System.Windows.Media.Animation.Timeline> . Örneğin, bir, <xref:System.Windows.Media.MediaTimeline> <xref:System.Windows.Media.Animation.Timeline> <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> ne zaman başlatılacağını belirlemek için özelliği gibi özellikleri kullanır <xref:System.Windows.Controls.MediaElement> (medyayı kayıttan yürütmeyi Başlat). Ayrıca <xref:System.Windows.Media.Animation.Timeline.Duration%2A> , özelliğinin ne kadar süreyle <xref:System.Windows.Controls.MediaElement> etkin olduğunu (medya kayıttan yürütme süresi) belirtmek için özelliğini kullanır. İle nesneleri kullanma hakkında daha fazla bilgi için <xref:System.Windows.Media.Animation.Timeline> <xref:System.Windows.Media.Animation.Storyboard> bkz. [Görsel Taslaklara Genel Bakış](storyboards-overview.md).  
  
 Bu örnek, <xref:System.Windows.Media.MediaTimeline> kayıttan yürütmeyi denetlemek için kullanarak bir basit medya oynatıcı oluşturmayı gösterir. Medya oynatıcı oynat, Duraklat, devam ve Durdur düğmelerini içerir. Player ayrıca <xref:System.Windows.Controls.Slider> ilerleme çubuğu olarak davranan bir denetime sahiptir.  
  
 Aşağıdaki örnek [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] medya oynatıcı için oluşturur.  
  
 [!code-xaml[MediaGallery_snip#MediaTimelineExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml#mediatimelineexamplewholepage)]  
  
 Aşağıdaki örnek, ilerleme çubuğu için işlevselliği oluşturur.  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaTimelineExample.xaml.cs#codebehindmediatimelineexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml.vb#codebehindmediatimelineexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.MediaElement>
- <xref:System.Windows.Media.MediaTimeline>
- <xref:System.Windows.Media.Animation.Storyboard>
- [MediaElement (Yürüt, Duraklat, Durdur, Ses Düzeyi ve Hız) Denetimi](how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md)
- [Görsel Taslaklara Genel Bakış](storyboards-overview.md)
- [Anahtar-Çerçeve Animasyonlara Genel Bakış](key-frame-animations-overview.md)
- [Animasyona Genel bakış](animation-overview.md)
- [Nasıl Yapılır Konuları](audio-and-video-how-to-topics.md)
- [Grafikler ve multimedya](index.md)
