---
title: 'Nasıl yapılır: Zaman Çizelgesinin Otomatik Olarak Ters Çevrilip Çevrilmeyeceğini Belirtme'
ms.date: 03/30/2017
helpviewer_keywords:
- AutoReverse property of timelines [WPF]
- Timelines [WPF], AutoReverse property
ms.assetid: 1648dd90-1bee-409a-ac69-ac729867f557
ms.openlocfilehash: 0fe2d337d8afa5197475e5b9ee40950226596e8b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354212"
---
# <a name="how-to-specify-whether-a-timeline-automatically-reverses"></a>Nasıl yapılır: Zaman Çizelgesinin Otomatik Olarak Ters Çevrilip Çevrilmeyeceğini Belirtme
Zaman çizelgesinin <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> özelliği, bir ileriye doğru yineleme tamamlandıktan sonra ter yönde oynatılır olup olmadığını belirler. Aşağıdaki örnek, aynı süre ve hedef değerleri ile ancak farklı olan birkaç animasyon gösterir <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> ayarları. Göstermek için nasıl <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> özelliği ile farklı davranır <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> ayarları, bazı animasyonlar yinelenecek şekilde ayarlanır. Son animasyon gösterir nasıl <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> özelliği, iç içe geçmiş zaman çizelgesi üzerinde çalışır.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[timingbehaviors_snip#AutoReverseAndRepeatBehaviorExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AutoReverseExample.xaml#autoreverseandrepeatbehaviorexamplewholepage)]
