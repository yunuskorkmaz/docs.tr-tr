---
title: 'Nasıl yapılır: Görsel Taslağı Başladıktan Sonra Denetlemek için Olay Tetikleyicilerini Kullanma'
ms.date: 03/30/2017
helpviewer_keywords:
- triggers [WPF], controlling Storyboards
- event triggers [WPF], controlling Storyboards
- Storyboards [WPF], controlling after start
ms.assetid: 3b115594-6a93-4972-b24d-61aa16f1c15f
ms.openlocfilehash: 32591edd065a8122b84ff14102f672ccf6001d67
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855853"
---
# <a name="how-to-use-event-triggers-to-control-a-storyboard-after-it-starts"></a>Nasıl yapılır: Görsel Taslağı Başladıktan Sonra Denetlemek için Olay Tetikleyicilerini Kullanma

Bu örnek, başladıktan <xref:System.Windows.Media.Animation.Storyboard> sonra nasıl kontrol yapılacağını gösterir. <xref:System.Windows.Media.Animation.BeginStoryboard>Kullanarak <xref:System.Windows.Media.Animation.Storyboard> başlatmakiçin,animasyonlarınıcanlandırdıklarınesnelereveözellikleredağıtanvesonrafilmşeridiniBaşlatanöğesinikullanın.[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Özelliğini belirterek bir <xref:System.Windows.Media.Animation.BeginStoryboard> ad verirseniz, denetlenebilir bir <xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> görsel taslak yaparsınız. Sonra film şeridini başladıktan sonra etkileşimli bir şekilde denetleyebilirsiniz.

Film şeridini denetlemek için aşağıdaki film şeridi <xref:System.Windows.EventTrigger> eylemlerini nesneleriyle birlikte kullanın.

- <xref:System.Windows.Media.Animation.PauseStoryboard>: Film şeridini duraklatır.

- <xref:System.Windows.Media.Animation.ResumeStoryboard>: Duraklatılmış bir film şeridini sürdürür.

- <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: Görsel taslak hızını değiştirir.

- <xref:System.Windows.Media.Animation.SkipStoryboardToFill>: Bir film şeridini, varsa, kendi Fill döneminin sonuna ilerletir.

- <xref:System.Windows.Media.Animation.StopStoryboard>: Film şeridini sonlandırır.

- <xref:System.Windows.Media.Animation.RemoveStoryboard>: Kaynak şeridi kaldırır ve kaynakları serbest bırakır.

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir görsel taslağı etkileşimli olarak denetlemek için denetlenebilir görsel taslak eylemlerini kullanır.

> [!NOTE]
> Kodu kullanarak bir film şeridini denetlemeye ilişkin bir örnek görmek için bkz. [etkileşimli yöntemlerini kullanarak başladıktan sonra bir görsel taslağı denetleme](how-to-control-a-storyboard-after-it-starts.md).

[!code-xaml[timingbehaviors_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/ControlStoryboardExample.xaml#controlstoryboardexampleusingwholepage)]

Daha fazla örnek için [animasyon örnek galerisine](https://go.microsoft.com/fwlink/?LinkID=159969)bakın.

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
