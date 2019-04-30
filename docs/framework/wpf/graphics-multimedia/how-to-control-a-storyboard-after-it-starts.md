---
title: 'Nasıl yapılır: Görsel taslağı başladıktan sonra denetleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboards [WPF], controlling after start
ms.assetid: 040f13f0-69f9-4ab5-be2b-079f4f80c7c0
ms.openlocfilehash: 107391386dfbb718f9436d9a039b08439fbc3279
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61762143"
---
# <a name="how-to-control-a-storyboard-after-it-starts"></a>Nasıl yapılır: Görsel taslağı başladıktan sonra denetleme
Bu örnek kod denetimine kullanmayı gösterir bir <xref:System.Windows.Media.Animation.Storyboard> başlatıldıktan sonra. İçinde bir film şeridini denetlemek için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], kullanın <xref:System.Windows.Trigger> ve <xref:System.Windows.TriggerAction> nesneleri; Örneğin, bkz [bir film şeridini denetlemek için olay tetikleyicilerini](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).  
  
 Görsel taslağı'nı başlatmak için kullandığınız kendi <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> yöntemi şeridinin animasyonları özelliklerine animasyon ve görsel taslak başlar dağıtır.  
  
 Bir film şeridi denetlenebilir yapmak için kullanmanız <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> yöntemi belirtin **true** ikinci parametre olarak. Ardından, duraklatma, sürdürme, arama, Durdur, hızlandırmak, veya film şeridini yavaşlatma veya dolgu süresinin ilerleyin şeridinin etkileşimli yöntemleri kullanabilirsiniz. Görsel Taslak'ın etkileşimli yöntemlerin listesi verilmiştir:  
  
- <xref:System.Windows.Media.Animation.Storyboard.Pause%2A>: Film duraklatılır.  
  
- <xref:System.Windows.Media.Animation.Storyboard.Resume%2A>: Duraklatılmış bir film şeridini sürdürür.  
  
- <xref:System.Windows.Media.Animation.Storyboard.SetSpeedRatio%2A>: Şeridinin etkileşimli hızını ayarlar.  
  
- <xref:System.Windows.Media.Animation.Storyboard.Seek%2A>: Görsel taslak belirtilen konumda arar.  
  
- <xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A>: Belirtilen konum film şeridini götürür. Farklı <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> yöntemi, bu işlem, sonraki değer çizgisi önce işlenir.  
  
- <xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>: Varsa film şeridini dolgu süresinin ilerler.  
  
- <xref:System.Windows.Media.Animation.Storyboard.Stop%2A>: Görsel taslak durdurur.  
  
 Aşağıdaki örnekte, birkaç film şeridi yöntemi, etkileşimli bir film şeridini denetlemek için kullanılır.  
  
 **Not:** Tetikleyicilerle kullanma film şeridini denetlemek için bir örnek görmek için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], bkz: [bir film şeridini denetlemek için olay tetikleyicileri kullanma](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ControlStoryboardExample.cs#controlstoryboardexampleusingwholepage)]
 [!code-vb[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/controlstoryboardexample.vb#controlstoryboardexampleusingwholepage)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Görsel Taslağı Başladıktan Sonra Denetlemek için Olay Tetikleyicilerini Kullanma](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)
