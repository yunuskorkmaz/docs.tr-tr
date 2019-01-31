---
title: 'Nasıl yapılır: Saatin Durumu Değiştiğinde Bildirim Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clocks [WPF], notification of state changes
- notifications [WPF], clocks' state changes
ms.assetid: ecb10fc9-d0c2-45c3-b0a1-7b11baa733da
ms.openlocfilehash: 116647b6b7df9c012ee7d5f08abd760b7f310f71
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55277114"
---
# <a name="how-to-receive-notification-when-a-clocks-state-changes"></a>Nasıl yapılır: Saatin Durumu Değiştiğinde Bildirim Alma
Saatin <xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated> bir olay oluşursa, kendi <xref:System.Windows.Media.Animation.Clock.CurrentState%2A> zaman saati başlatıldığında veya durdurulduğunda gibi geçersiz hale gelir. Bu olay ile kullanarak doğrudan kaydedebilirsiniz bir <xref:System.Windows.Media.Animation.Clock>, ya da kullanarak kaydedebilirsiniz bir <xref:System.Windows.Media.Animation.Timeline>.  
  
 Aşağıdaki örnekte, bir <xref:System.Windows.Media.Animation.Storyboard> ve iki <xref:System.Windows.Media.Animation.DoubleAnimation> nesneleri iki dikdörtgenin genişliğini animasyon uygulamak için kullanılır. <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> Olay saati durumu değişiklikleri dinlemek için kullanılır.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[timingbehaviors_snip#_graphicsmm_StateExampleMarkupWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StateExample.xaml#_graphicsmm_stateexamplemarkupwholepage)]  
  
 [!code-csharp[timingbehaviors_snip#_graphicsmm_StateEventHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StateExample.xaml.cs#_graphicsmm_stateeventhandlers)]
 [!code-vb[timingbehaviors_snip#_graphicsmm_StateEventHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/stateexample.xaml.vb#_graphicsmm_stateeventhandlers)]  
  
 Farklı durumlar animasyon üst zaman çizelgesi girin, aşağıdaki resimde gösterilmektedir (*film şeridi*) ilerler.  
  
 ![İki animasyon film şeridi için durumları saat](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-3timelines.png "graphicsmm_3timelines")  
  
 Aşağıdaki tabloda, zamanları gösterilmektedir *Animation1*'s <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> olay harekete geçirilir:  
  
||||||||  
|-|-|-|-|-|-|-|  
|Süre (saniye)|1.|10|19|21|30|39|  
|Durum|Etkin|Etkin|Durduruldu|Etkin|Etkin|Durduruldu|  
  
 Aşağıdaki tabloda, zamanları gösterilmektedir *Animation2*'s <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> olay harekete geçirilir:  
  
||||||||||  
|-|-|-|-|-|-|-|-|-|  
|Süre (saniye)|1.|9|11|19|21|29|31|39|  
|Durum|Etkin|Doldurma|Etkin|Durduruldu|Etkin|Doldurma|Etkin|Durduruldu|  
  
 Dikkat *Animation1*'s <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> olayı tetikler 10 saniyede durumuna kalsa da <xref:System.Windows.Media.Animation.ClockState.Active>. Onun durumunu değiştiren 10 saniyede, ancak bunu değiştirildi çünkü <xref:System.Windows.Media.Animation.ClockState.Active> için <xref:System.Windows.Media.Animation.ClockState.Filling> ve ardından yeniden <xref:System.Windows.Media.Animation.ClockState.Active> aynı değer çizgisi olarak.
