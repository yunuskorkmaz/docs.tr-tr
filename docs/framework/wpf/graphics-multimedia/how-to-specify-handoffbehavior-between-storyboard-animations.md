---
title: "Nasıl yapılır: Görsel Taslak Animasyonları Arasında HandoffBehavior Belirtme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Storyboards [WPF], handoff behavior between animations
- animation [WPF], handoff behavior between
ms.assetid: 97bd6842-929b-49d9-813e-46553ae46472
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 323ea563aec7bc7ad0abec2372e3af977c7e38eb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-handoffbehavior-between-storyboard-animations"></a>Nasıl yapılır: Görsel Taslak Animasyonları Arasında HandoffBehavior Belirtme
Bu örnek film şeridi animasyonları arasında iletim davranışı belirtmek nasıl gösterir. <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> Özelliği <xref:System.Windows.Media.Animation.BeginStoryboard> nasıl yeni bir animasyon belirtir bir özelliğe uygulanmış olan tüm varolanları etkileşim.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, fare imleci üzerine getirdiğinde büyütün ve imleci hemen taşındığında küçültülüyor iki düğme oluşturur. Düğme üzerinde fare imleci hızlı bir şekilde kaldırmak, ikinci animasyon ilki bitmeden önce uygulanır. Üst üste iki animasyon arasındaki farkı görebilirsiniz şuna benzer tutulduğunda <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> değerlerini <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> ve <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>. Değerini <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> değerini sırasında bir animasyon arasında sorunsuz bir geçiş neden olan örtüşen animasyonları birleştirir <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace> yeni animasyonun önceki çakışan animasyonu hemen değiştirmesine neden olur.  
  
 [!code-xaml[timingbehaviors_snip#HandoffBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/HandoffBehaviorExample.xaml#handoffbehaviorwholepage)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.Animation.BeginStoryboard>  
 <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A>  
 [Animasyon genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Animasyon ve zamanlama](http://msdn.microsoft.com/en-us/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
