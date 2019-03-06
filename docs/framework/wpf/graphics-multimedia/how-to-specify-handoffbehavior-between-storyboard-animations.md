---
title: 'Nasıl yapılır: Görsel Taslak Animasyonları Arasında HandoffBehavior Belirtme'
ms.date: 03/30/2017
helpviewer_keywords:
- Storyboards [WPF], handoff behavior between animations
- animation [WPF], handoff behavior between
ms.assetid: 97bd6842-929b-49d9-813e-46553ae46472
ms.openlocfilehash: a919fe2a87cb11ca2197465b288eac7a17976cc3
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57379074"
---
# <a name="how-to-specify-handoffbehavior-between-storyboard-animations"></a>Nasıl yapılır: Görsel Taslak Animasyonları Arasında HandoffBehavior Belirtme
Bu örnekte, görsel taslak animasyonları arasında iletim davranışı belirtmek gösterilmektedir. <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> Özelliği <xref:System.Windows.Media.Animation.BeginStoryboard> belirtir nasıl yeni bir özellik için zaten uygulanmış olan tüm mevcut vm'lere etkileşim.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, fare imleci üzerine getirdiğinde büyütün ve işaretçiyi hemen taşır, daha küçük olur iki düğme oluşturur. Bir düğmenin üzerine fare imleci hızlı bir şekilde kaldırmak, ilk tamamlanmadan önce ikinci animasyonun uygulanır. Bu arasındaki farkı gördüğünüz gibi üst üste iki animasyon <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> değerlerini <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> ve <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>. Değerini <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> değerini animasyonlar arasında daha sorunsuz bir geçiş neden örtüşen animasyonlar birleştirir <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace> hemen önceki çakışan animasyonu değiştirmek yeni animasyonu neden olur.  
  
 [!code-xaml[timingbehaviors_snip#HandoffBehaviorWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/HandoffBehaviorExample.xaml#handoffbehaviorwholepage)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Media.Animation.BeginStoryboard>
- <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A>
- [Animasyona Genel bakış](animation-overview.md)
- [Animasyon ve zamanlama ile ilgili nasıl yapılır konuları](animation-and-timing-how-to-topics.md)
