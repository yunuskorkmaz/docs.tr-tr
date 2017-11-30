---
title: "Nasıl yapılır: Animasyon için Süre Ayarlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], duration
- Timelines [WPF], description
- duration of animations [WPF]
ms.assetid: 155034ef-7d00-4416-a73c-b1713992d2eb
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9560e9d0a2809ae8f55a060eaec3b271539d5f94
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-a-duration-for-an-animation"></a>Nasıl yapılır: Animasyon için Süre Ayarlama
A <xref:System.Windows.Media.Animation.Timeline> zaman kesimini ve bu kesimin uzunluğu zaman çizelgesinin tarafından belirlenir temsil <xref:System.Windows.Duration>. Zaman bir <xref:System.Windows.Media.Animation.Timeline> sonuna ulaşıldığında süresinin, yürütmeyi durdurur. Varsa <xref:System.Windows.Media.Animation.Timeline> alt zaman çizelgeleri varsa bunlar da yürütmeyi durdurur. Animasyonun, söz konusu olduğunda <xref:System.Windows.Duration> animasyon geçiş bitiş değeri başlangıç değerinden gereken süreyi belirtir.  
  
 Belirleyebileceğiniz bir <xref:System.Windows.Duration> belirli, sınırlı bir süre veya özel değerler ile <xref:System.Windows.Duration.Automatic%2A> veya <xref:System.Windows.Duration.Forever%2A>. Animasyonun her zaman bir sonlu uzunluğu olması gerektiğinden animasyonun süresi her zaman bir saat değeri olmalıdır; aksi takdirde, animasyonun hedef değerler arasında geçiş yapma bilmez. Kapsayıcı zaman çizelgeleri (<xref:System.Windows.Media.Animation.TimelineGroup> nesneler), aşağıdaki gibi <xref:System.Windows.Media.Animation.Storyboard> ve <xref:System.Windows.Media.Animation.ParallelTimeline>, varsayılan süre olan sahip <xref:System.Windows.Duration.Automatic%2A>, bunlar otomatik olarak sona kendi son alt çalma durduğunda anlamına gelir.  
  
 Aşağıdaki örnekte, genişlik, yükseklik ve dolgu rengini içinde bir <xref:System.Windows.Shapes.Rectangle> animasyon eklenir. Süreleri animasyon efektleri animasyonun algılanan hızına denetleme ve kapsayıcı zaman çizelgesi süresini alt zaman çizelgeleri süresiyle geçersiz kılma gibi sonuçta animasyon ve kapsayıcı zaman çizelgeleri ayarlanır.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[timingbehaviors_snip#DurationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/DurationExample.xaml#durationexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Duration>  
 [Animasyon genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
