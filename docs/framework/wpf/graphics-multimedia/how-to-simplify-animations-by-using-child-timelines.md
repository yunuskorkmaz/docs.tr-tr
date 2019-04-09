---
title: 'Nasıl yapılır: Alt Öğe Zaman Çizelgelerini Kullanarak Animasyonları Basitleştirme'
ms.date: 03/30/2017
helpviewer_keywords:
- simplifying animations by child timelines [WPF]
- animation [WPF], simplifying by child timelines
- child timelines [WPF]
ms.assetid: 8335d770-d13d-42bd-8dfa-63f92c0327e2
ms.openlocfilehash: 21a297208be045eea79d6f5ca6c8eac016d26345
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59096400"
---
# <a name="how-to-simplify-animations-by-using-child-timelines"></a>Nasıl yapılır: Alt Öğe Zaman Çizelgelerini Kullanarak Animasyonları Basitleştirme
Bu örnekte alt kullanarak animasyonları basitleştirme gösterilmektedir <xref:System.Windows.Media.Animation.ParallelTimeline> nesneleri. A <xref:System.Windows.Media.Animation.Storyboard> bir tür <xref:System.Windows.Media.Animation.Timeline> içerdiği zaman çizelgeleri için hedefleme bilgileri sağlar. Kullanım bir <xref:System.Windows.Media.Animation.Storyboard> nesne ve özellik bilgiler dahil bilgilerin hedefleyen zaman çizelgesi sağlamak için.  
  
 Animasyonu başlatmak için bir veya daha fazla kullanın <xref:System.Windows.Media.Animation.ParallelTimeline> nesneler iç içe geçmiş alt öğeleri olarak bir <xref:System.Windows.Media.Animation.Storyboard>. Bunlar <xref:System.Windows.Media.Animation.ParallelTimeline> nesneler diğer animasyonları içerebilir ve bu nedenle, karmaşık animasyonları serilerini daha iyi kapsayabilir. Örneğin, animasyon, bir <xref:System.Windows.Controls.TextBlock> ve aynı çeşitli şekillerde <xref:System.Windows.Media.Animation.Storyboard>, animasyon için ayırabilirsiniz <xref:System.Windows.Controls.TextBlock> ve her bir ayrı koymadan <xref:System.Windows.Media.Animation.ParallelTimeline>. Çünkü her <xref:System.Windows.Media.Animation.ParallelTimeline> kendi <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> ve tüm alt öğelerini <xref:System.Windows.Media.Animation.ParallelTimeline> bu göreli başlamak <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>, zamanlama daha iyi kapsüllenir.  
  
 Aşağıdaki örnek iki parça metin canlandırır (<xref:System.Windows.Controls.TextBlock> nesneleri) gelen aynı <xref:System.Windows.Media.Animation.Storyboard>. A <xref:System.Windows.Media.Animation.ParallelTimeline> birinin animasyonları kapsülleyen <xref:System.Windows.Controls.TextBlock> nesneleri.  
  
 **Performans Not:** İç içe yerleştirebilseniz <xref:System.Windows.Media.Animation.Storyboard> zaman çizelgelerini, birbiriyle iç <xref:System.Windows.Media.Animation.ParallelTimeline>lar bunlar yükü daha azdır gerektirdiğinden, iç içe geçirme daha uygundur. ( <xref:System.Windows.Media.Animation.Storyboard> Sınıfının devraldığı <xref:System.Windows.Media.Animation.ParallelTimeline> sınıfı.)  
  
## <a name="example"></a>Örnek  
 [!code-xaml[Timelines_snip#ParallelTimelineWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Timelines_snip/CS/ParallelTimelineExample.xaml#paralleltimelinewholepage)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Animasyona Genel bakış](animation-overview.md)
- [Görsel Taslak Animasyonları Arasında HandoffBehavior Belirtme](how-to-specify-handoffbehavior-between-storyboard-animations.md)
