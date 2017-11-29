---
title: "Nasıl yapılır: Zaman Çizelgesinin Otomatik Olarak Ters Çevrilip Çevrilmeyeceğini Belirtme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- AutoReverse property of timelines [WPF]
- Timelines [WPF], AutoReverse property
ms.assetid: 1648dd90-1bee-409a-ac69-ac729867f557
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2abce54905f0bb06bf983c065e064ce2dfeba932
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-specify-whether-a-timeline-automatically-reverses"></a>Nasıl yapılır: Zaman Çizelgesinin Otomatik Olarak Ters Çevrilip Çevrilmeyeceğini Belirtme
Bir zaman çizelgesinin <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> özelliği, ileriye doğru yineleme tamamlandıktan sonra geriye doğru çalar olup olmadığını belirler. Aşağıdaki örnek, birkaç animasyon ile aynı süre ve hedef değerleri, ancak farklı gösterir <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> ayarlar. Göstermek için nasıl <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> özelliği ile farklı davranan <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> ayarları, bazı animasyonları yinelenecek şekilde ayarlanır. Son animasyon gösterir nasıl <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> özelliği iç içe geçmiş zaman çizelgelerini üzerinde çalışır.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[timingbehaviors_snip#AutoReverseAndRepeatBehaviorExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AutoReverseExample.xaml#autoreverseandrepeatbehaviorexamplewholepage)]
