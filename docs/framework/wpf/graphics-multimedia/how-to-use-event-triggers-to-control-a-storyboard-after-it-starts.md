---
title: 'Nasıl yapılır: Görsel Taslağı Başladıktan Sonra Denetlemek için Olay Tetikleyicilerini Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- triggers [WPF], controlling Storyboards
- event triggers [WPF], controlling Storyboards
- Storyboards [WPF], controlling after start
ms.assetid: 3b115594-6a93-4972-b24d-61aa16f1c15f
ms.openlocfilehash: d0b25f56caf3f25b6e649c05ecf1cbe50046dd93
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57362376"
---
# <a name="how-to-use-event-triggers-to-control-a-storyboard-after-it-starts"></a>Nasıl yapılır: Görsel Taslağı Başladıktan Sonra Denetlemek için Olay Tetikleyicilerini Kullanma
Bu örnek nasıl denetleneceğini gösterir bir <xref:System.Windows.Media.Animation.Storyboard> başladıktan sonra. Başlamak için bir <xref:System.Windows.Media.Animation.Storyboard> kullanarak [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], kullanın <xref:System.Windows.Media.Animation.BeginStoryboard>, nesneleri ve özellikleri animasyon ve görsel Taslak'ı başlatır animasyonları dağıtır. Size, <xref:System.Windows.Media.Animation.BeginStoryboard> bir ad belirterek, <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> özelliği yaptığınız, denetlenebilir bir film şeridi. Başladıktan sonra görsel taslak ardından etkileşimli olarak denetleyebilirsiniz.  
  
 Aşağıdaki görsel taslak eylemleri ile birlikte kullanmak <xref:System.Windows.EventTrigger> bir film şeridini denetlemek için nesneleri.  
  
-   <xref:System.Windows.Media.Animation.PauseStoryboard>: Film duraklatılır.  
  
-   <xref:System.Windows.Media.Animation.ResumeStoryboard>: Duraklatılmış bir film şeridini sürdürür.  
  
-   <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Görsel taslak hızını değiştirir.  
  
-   <xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Varsa, bir görsel taslak dolgu süresinin sonuna ilerler.  
  
-   <xref:System.Windows.Media.Animation.StopStoryboard>: Görsel taslak durdurur.  
  
-   <xref:System.Windows.Media.Animation.RemoveStoryboard>: Kaynakları boşaltma, film şeridi kaldırır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, etkileşimli bir film şeridini denetlemek için denetlenebilir film şeridi eylemleri kullanır.  
  
 **Not:** Kod kullanarak bir film şeridini denetlemek için bir örnek görmek için bkz: [bir görsel taslak sonra onu başlatır kullanarak kendi etkileşimli yöntemlerini denetlemesine](how-to-control-a-storyboard-after-it-starts.md).  
  
 [!code-xaml[timingbehaviors_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/ControlStoryboardExample.xaml#controlstoryboardexampleusingwholepage)]  
  
 Diğer örnekler için [animasyon örnek Galerisi](https://go.microsoft.com/fwlink/?LinkID=159969).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Media.Animation.ResumeStoryboard>
- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>
- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>
- <xref:System.Windows.Media.Animation.PauseStoryboard>
- <xref:System.Windows.Media.Animation.StopStoryboard>
- <xref:System.Windows.Media.Animation.SeekStoryboard>
- [Görsel Taslağı Başladıktan Sonra Etkileşimli Yöntemlerini Kullanarak Denetleme](how-to-control-a-storyboard-after-it-starts.md)
- [Animasyona Genel bakış](animation-overview.md)
- [Görsel Taslaklara Genel Bakış](storyboards-overview.md)
