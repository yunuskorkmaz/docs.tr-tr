---
title: 'Nasıl yapılır: Animasyon için Süre Ayarlama'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], duration
- Timelines [WPF], description
- duration of animations [WPF]
ms.assetid: 155034ef-7d00-4416-a73c-b1713992d2eb
ms.openlocfilehash: bdae1689ffeb8c54d756b9debbd26d57a052892d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59198796"
---
# <a name="how-to-set-a-duration-for-an-animation"></a>Nasıl yapılır: Animasyon için Süre Ayarlama
A <xref:System.Windows.Media.Animation.Timeline> zaman bir segmentini ve kesiminin uzunluğu çizelgesinin tarafından belirlenir temsil <xref:System.Windows.Duration>. Olduğunda bir <xref:System.Windows.Media.Animation.Timeline> geçerlilik süresinin, yürütmeyi durdurur. Varsa <xref:System.Windows.Media.Animation.Timeline> alt öğe zaman çizelgeleri varsa bunlar da yürütmeyi durdurur. Bir animasyon, söz konusu olduğunda <xref:System.Windows.Duration> animasyon bitiş değeri başlangıç değerinden geçişin ne kadar alacağını belirtir.  
  
 Belirtebileceğiniz bir <xref:System.Windows.Duration> belirli, sınırlı bir süre veya özel değerler <xref:System.Windows.Duration.Automatic%2A> veya <xref:System.Windows.Duration.Forever%2A>. Bir animasyon zaman sonlu uzunluğu olması gerektiğinden bir animasyonun süresi bir saat değeri her zaman olmalıdır; aksi takdirde, animasyon hedef değerleri arasında geçiş yapma bilmez. Kapsayıcı zaman çizelgeleri (<xref:System.Windows.Media.Animation.TimelineGroup> nesneleri), gibi <xref:System.Windows.Media.Animation.Storyboard> ve <xref:System.Windows.Media.Animation.ParallelTimeline>, varsayılan süre olan <xref:System.Windows.Duration.Automatic%2A>, bunlar otomatik olarak sonlandırmak son alt öğe yürütme durdurulduğunda anlamına gelir.  
  
 Aşağıdaki örnekte, genişlik, yükseklik ve dolgu rengi içinde bir <xref:System.Windows.Shapes.Rectangle> bir animasyon görünür. Süreleri, animasyon efektleri algılanan animasyonun hızını denetleme ve alt öğe zaman çizelgelerini süresi kapsayıcı zaman çizelgesinin süresiyle geçersiz kılma dahil olmak üzere sonuçta animasyon ve kapsayıcı zaman çizelgesi üzerinde ayarlanır.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[timingbehaviors_snip#DurationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/DurationExample.xaml#durationexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Duration>
- [Animasyona Genel bakış](animation-overview.md)
