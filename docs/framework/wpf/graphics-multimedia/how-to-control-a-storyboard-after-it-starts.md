---
title: "Nasıl yapılır: Görsel Taslağı Başladıktan Sonra Denetleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboards [WPF], controlling after start
ms.assetid: 040f13f0-69f9-4ab5-be2b-079f4f80c7c0
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 051ac6fea73b207fb5ef4d6293c5e996552f1281
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-control-a-storyboard-after-it-starts"></a>Nasıl yapılır: Görsel Taslağı Başladıktan Sonra Denetleme
Bu örnek kodu denetimi için kullanmayı gösterir bir <xref:System.Windows.Media.Animation.Storyboard> başladıktan sonra. Bir film şeridi denetlemek için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], kullanın <xref:System.Windows.Trigger> ve <xref:System.Windows.TriggerAction> nesneleri; Örneğin, bakın [bir film şeridi sonra başlar denetlemek için olay tetikleyicileri](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).  
  
 Film şeridi başlatmak için kullandığınız kendi <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> hale getirmeyi ve film şeridi başlatır özellikleri film şeridi'nın animasyonları dağıtır yöntemi.  
  
 Film şeridi denetlenebilir yapmak için kullandığınız <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> yöntemi ve belirtin **true** ikinci parametre olarak. Ardından, duraklatma, sürdürme, arama, durdurmak, hızlandırmak, veya film şeridi yavaş veya dolgu süresinin ilerletmek için film şeridi'nın etkileşimli yöntemleri kullanabilirsiniz. Film şeridi'nın etkileşimli yöntemlerin listesi aşağıdadır:  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Pause%2A>: Film şeridi duraklatır.  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Resume%2A>: Duraklatılmış film şeridi sürdürür.  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SetSpeedRatio%2A>: Film şeridi'nın etkileşimli hızını ayarlar.  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Seek%2A>: Film şeridini belirtilen konuma götürür.  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A>: Film şeridini belirtilen konuma götürür. Farklı <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> yöntemi, bu işlem bir sonraki değer çizgilerinin önce işlenir.  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>: Varsa, film şeridi dolgu süresinin ilerler.  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Stop%2A>: Film şeridi durdurur.  
  
 Aşağıdaki örnekte, birkaç film şeridi yöntemi etkileşimli olarak film şeridi denetlemek için kullanılır.  
  
 **Not:** olan tetikleyici kullanarak film şeridi denetlemeye yönelik bir örnek görmek için [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], bkz: [bir film şeridi sonra başlar denetlemek için olay tetikleyicileri kullanma](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ControlStoryboardExample.cs#controlstoryboardexampleusingwholepage)]
 [!code-vb[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/controlstoryboardexample.vb#controlstoryboardexampleusingwholepage)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görsel Taslağı Başladıktan Sonra Denetlemek için Olay Tetikleyicilerini Kullanma](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)
