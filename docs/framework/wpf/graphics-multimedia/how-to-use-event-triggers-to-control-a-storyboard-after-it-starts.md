---
title: 'Nasıl yapılır: Görsel Taslağı Başladıktan Sonra Denetlemek için Olay Tetikleyicilerini Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- triggers [WPF], controlling Storyboards
- event triggers [WPF], controlling Storyboards
- Storyboards [WPF], controlling after start
ms.assetid: 3b115594-6a93-4972-b24d-61aa16f1c15f
ms.openlocfilehash: 518f5d7ea0b5dc00677489f1383814563c565145
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186709"
---
# <a name="how-to-use-event-triggers-to-control-a-storyboard-after-it-starts"></a>Nasıl yapılır: Görsel Taslağı Başladıktan Sonra Denetlemek için Olay Tetikleyicilerini Kullanma

Bu örnek, bir <xref:System.Windows.Media.Animation.Storyboard> başlatıldıktan sonra nasıl denetler gösterin. Animasyonları <xref:System.Windows.Media.Animation.Storyboard> animasyonlarına [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ve <xref:System.Windows.Media.Animation.BeginStoryboard>özelliklerine dağıtan ve sonra film şeridini başlatan , kullanarak bir başlangıç yapmak için. Özelliğini <xref:System.Windows.Media.Animation.BeginStoryboard> belirterek <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> bir ad verirseniz, onu denetlenebilir bir film şeridi haline getirebilirsiniz. Daha sonra başladıktan sonra film şeridini etkileşimli olarak denetleyebilirsiniz.

Bir film şeridini denetlemek <xref:System.Windows.EventTrigger> için nesnelerle birlikte aşağıdaki film şeridi eylemlerini kullanın.

- <xref:System.Windows.Media.Animation.PauseStoryboard>: Film şeridini duraklatabilir.

- <xref:System.Windows.Media.Animation.ResumeStoryboard>: Duraklatılmış bir film şeridini devam ettirer.

- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Film şeridi hızını değiştirir.

- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Eğer varsa, bir film şeridini dolum süresinin sonuna kadar ilerletir.

- <xref:System.Windows.Media.Animation.StopStoryboard>: Hikaye şeridini durdurur.

- <xref:System.Windows.Media.Animation.RemoveStoryboard>: Film şeridini kaldırır, kaynakları serbest çehresini serbest klar.

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir film şeridini etkileşimli olarak denetlemek için denetlenebilir film şeridi eylemlerini kullanır.

> [!NOTE]
> Kodu kullanarak bir film şeridini denetleme örneğini görmek için, [Etkileşimli Yöntemleri Kullanmaya Başladıktan Sonra Bir Film Şeridini Denetleme](how-to-control-a-storyboard-after-it-starts.md)bölümüne bakın.

[!code-xaml[timingbehaviors_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/ControlStoryboardExample.xaml#controlstoryboardexampleusingwholepage)]

Ek örnekler için [Animasyon Örnek Galerisi'ne](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples)bakın.

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
