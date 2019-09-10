---
title: 'Nasıl yapılır: Görsel Taslağı başladıktan sonra denetleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboards [WPF], controlling after start
ms.assetid: 040f13f0-69f9-4ab5-be2b-079f4f80c7c0
ms.openlocfilehash: de30cfdb49df721cb4d6845dc67464e8a5b61f93
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855870"
---
# <a name="how-to-control-a-storyboard-after-it-starts"></a>Nasıl yapılır: Görsel Taslağı başladıktan sonra denetleme

Bu örnek, başlatıldıktan sonra bir <xref:System.Windows.Media.Animation.Storyboard> nasıl kontrol etmek için kodun nasıl kullanılacağını gösterir. İçindeki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]bir film şeridini denetlemek için ve <xref:System.Windows.Trigger> <xref:System.Windows.TriggerAction> nesneleri kullanın; bir örnek için bkz. [bir film şeridini başladıktan sonra denetlemek için olay tetikleyicilerini kullanma](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).

Görsel Taslağı başlatmak için, film şeridinin animasyonlarını <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> canlandırdıkları özelliklere dağıtan ve film şeridini Başlatan yöntemini kullanırsınız.

Bir film şeridini denetlenebilir yapmak için <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> yöntemini kullanın ve ikinci parametre olarak **true değerini** belirtin. Daha sonra görsel taslağın etkileşimli yöntemlerini kullanarak film şeridini duraklatabilir, sürdürebilir, arayabilir, durdurabilir, hızlandıramaz veya yavaşlatabilir ya da bunu kendi Fill dönemine ilerletebilirsiniz. Görsel taslağın etkileşimli yöntemlerinin bir listesi aşağıda verilmiştir:

- <xref:System.Windows.Media.Animation.Storyboard.Pause%2A>: Film şeridini duraklatır.

- <xref:System.Windows.Media.Animation.Storyboard.Resume%2A>: Duraklatılmış bir film şeridini sürdürür.

- <xref:System.Windows.Media.Animation.Storyboard.SetSpeedRatio%2A>: Görsel taslağın etkileşimli hızını ayarlar.

- <xref:System.Windows.Media.Animation.Storyboard.Seek%2A>: Film şeridini belirtilen konumu arar.

- <xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A>: Görsel Taslağı belirtilen konuma arar. <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> Yönteminden farklı olarak, bu işlem sonraki Tick 'ten önce işlenir.

- <xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>: Film şeridini, varsa, kendi Fill dönemine ilerletir.

- <xref:System.Windows.Media.Animation.Storyboard.Stop%2A>: Film şeridini sonlandırır.

Aşağıdaki örnekte, bir görsel taslağı etkileşimli olarak denetlemek için çeşitli görsel taslak yöntemleri kullanılır.

> [!NOTE]
> İle [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]Tetikleyicileri kullanarak bir film şeridini denetlemeye ilişkin bir örnek görmek için bkz. [bir film şeridini başladıktan sonra denetlemek için olay tetikleyicilerini kullanma](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).

## <a name="example"></a>Örnek

[!code-csharp[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ControlStoryboardExample.cs#controlstoryboardexampleusingwholepage)]
[!code-vb[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/controlstoryboardexample.vb#controlstoryboardexampleusingwholepage)]

## <a name="see-also"></a>Ayrıca bkz.

- [Görsel Taslağı Başladıktan Sonra Denetlemek için Olay Tetikleyicilerini Kullanma](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)
