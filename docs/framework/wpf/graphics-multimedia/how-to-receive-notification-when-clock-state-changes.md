---
title: "Nasıl yapılır: bildirim almak, bir saat &#39; s durum değişiklikleri"
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
- clocks [WPF], notification of state changes
- notifications [WPF], clocks' state changes
ms.assetid: ecb10fc9-d0c2-45c3-b0a1-7b11baa733da
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 396e2c51894ad5ed11f8953bceb1bd36899cfc62
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-receive-notification-when-a-clock39s-state-changes"></a>Nasıl yapılır: bildirim almak, bir saat &#39; s durum değişiklikleri
Saatin <xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated> olayı oluşur, kendi <xref:System.Windows.Media.Animation.Clock.CurrentState%2A> zaman saatin başlatıldığında veya durdurulduğunda gibi geçersiz hale gelir. Kullanarak doğrudan ile bu olay için kaydedebilirsiniz bir <xref:System.Windows.Media.Animation.Clock>, veya kullanarak kaydolabilirsiniz bir <xref:System.Windows.Media.Animation.Timeline>.  
  
 Aşağıdaki örnekte, bir <xref:System.Windows.Media.Animation.Storyboard> ve iki <xref:System.Windows.Media.Animation.DoubleAnimation> nesnesi iki dikdörtgen genişliğini animasyon için kullanılır. <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> Olay saat durum değişikliklerini dinlemek için kullanılır.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[timingbehaviors_snip#_graphicsmm_StateExampleMarkupWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StateExample.xaml#_graphicsmm_stateexamplemarkupwholepage)]  
  
 [!code-csharp[timingbehaviors_snip#_graphicsmm_StateEventHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StateExample.xaml.cs#_graphicsmm_stateeventhandlers)]
 [!code-vb[timingbehaviors_snip#_graphicsmm_StateEventHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/stateexample.xaml.vb#_graphicsmm_stateeventhandlers)]  
  
 Aşağıdaki çizimde animasyonların farklı durumlara girin üst zaman çizelgesi gösterir (*film şeridi*) ilerler.  
  
 ![Film şeridi iki animasyon için durumlar saat](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-3timelines.png "graphicsmm_3timelines")  
  
 Aşağıdaki tabloda kez aktarılma gösterir *Animation1*'s <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> olay ateşlenir:  
  
||||||||  
|-|-|-|-|-|-|-|  
|Süre (saniye)|1.|10|19|21|30|39|  
|Durum|Etkin|Etkin|Durduruldu|Etkin|Etkin|Durduruldu|  
  
 Aşağıdaki tabloda kez aktarılma gösterir *Animation2*'s <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> olay ateşlenir:  
  
||||||||||  
|-|-|-|-|-|-|-|-|-|  
|Süre (saniye)|1.|9|11|19|21|29|31|39|  
|Durum|Etkin|Doldurma|Etkin|Durduruldu|Etkin|Doldurma|Etkin|Durduruldu|  
  
 Dikkat *Animation1*'s <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> olay harekete 10 saniyede durumuna kalsa bile <xref:System.Windows.Media.Animation.ClockState.Active>. Durumu 10 saniyede değişti, ancak bunu değiştirildi çünkü <xref:System.Windows.Media.Animation.ClockState.Active> için <xref:System.Windows.Media.Animation.ClockState.Filling> ve ardından yeniden <xref:System.Windows.Media.Animation.ClockState.Active> aynı değer çizgilerinin içinde.
