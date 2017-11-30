---
title: "Nasıl yapılır: Anahtar Çerçeve Animasyonu Zamanlamasını Denetleme"
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
- key frames [WPF], timing
- timing key-fram animation
ms.assetid: b059216f-7d4b-4ca8-a019-bc287ee7bf16
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3bc3566cf25282749a09c5f2372cd1c81e3ce881
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-control-key-frame-animation-timing"></a>Nasıl yapılır: Anahtar Çerçeve Animasyonu Zamanlamasını Denetleme
Bu örnek, içinde bir anahtar çerçeve animasyon ana kare zamanlamasını denetlemek gösterilmiştir. Diğer animasyonları gibi anahtar çerçeve animasyonları sahip bir <xref:System.Windows.Media.Animation.Timeline.Duration%2A> özelliği. Animasyonun süresini belirtmeye ek olarak, bu süre hangi kısmının her anahtar çerçeveleri ayrılan belirtmeniz gerekir. Zamanı paylaştırmak için belirttiğiniz bir <xref:System.Windows.Media.Animation.KeyTime> animasyonun her anahtar çerçevede için.  
  
 <xref:System.Windows.Media.Animation.KeyTime> Her anahtar çerçeve (bunu belirtmiyor anahtar çerçevesi oynadığı süre) bir anahtar çerçevesi bittiğini belirtir. Belirleyebileceğiniz bir <xref:System.Windows.Media.Animation.KeyTime> olarak bir <xref:System.TimeSpan> değeri, bir yüzdesi olarak veya <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> veya <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> özel değer.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanan bir <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> dikdörtgen ekranda animasyon eklemek için. Anahtar çerçeveler anahtar kez ayarlanır <xref:System.TimeSpan> değerleri.  
  
 [!code-csharp[keyframes_snip#KeyTimesTimeSpanExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimestimespanexample)]
 [!code-vb[keyframes_snip#KeyTimesTimeSpanExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimestimespanexample)]
 [!code-xaml[keyframes_snip#KeyTimesTimeSpanExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimestimespanexample)]  
  
 Her anahtar çerçeve değerini erişildiğinde, aşağıdaki çizimde gösterilmiştir.  
  
 ![Anahtar değerlerinin 3, 4 ve 10 saniyede tamamladı](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime1-timespan.png "graphicsmm_keyframe_keytime1_timespan")  
  
 Sonraki örnek anahtar çerçeveler anahtar zamanlarını yüzde değerlerle ayarlamak dışında aynı olan bir animasyon gösterir.  
  
 [!code-csharp[keyframes_snip#KeyTimesPercentageExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespercentageexample)]
 [!code-vb[keyframes_snip#KeyTimesPercentageExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespercentageexample)]
 [!code-xaml[keyframes_snip#KeyTimesPercentageExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespercentageexample)]  
  
 Her anahtar çerçeve değerini erişildiğinde, aşağıdaki çizimde gösterilmiştir.  
  
 ![Anahtar değerlerinin 3, 4 ve 10 saniyede tamamladı](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime2-percentage.png "graphicsmm_keyframe_keytime2_percentage")  
  
 Sonraki örnek kullanır <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> anahtar zaman değerlerini.  
  
 [!code-csharp[keyframes_snip#KeyTimesUniformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimesuniformexample)]
 [!code-vb[keyframes_snip#KeyTimesUniformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimesuniformexample)]
 [!code-xaml[keyframes_snip#KeyTimesUniformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimesuniformexample)]  
  
 Her anahtar çerçeve değerini erişildiğinde, aşağıdaki çizimde gösterilmiştir.  
  
 ![3.3,6.6 ve 9,9 saniyede anahtar değerleri üst sınırına](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime3-uniform.png "graphicsmm_keyframe_keytime3_uniform")  
  
 Son örnek kullanan <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> anahtar zaman değerlerini.  
  
 [!code-csharp[keyframes_snip#KeyTimesPacedExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespacedexample)]
 [!code-vb[keyframes_snip#KeyTimesPacedExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespacedexample)]
 [!code-xaml[keyframes_snip#KeyTimesPacedExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespacedexample)]  
  
 Her anahtar çerçeve değerini erişildiğinde, aşağıdaki çizimde gösterilmiştir.  
  
 ![Anahtar değerleri 0, 5 ve 10 saniyede tamamladı](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime4-paced.png "graphicsmm_keyframe_keytime4_paced")  
  
 Kolaylık olması için bu örnek yerel animasyonları kullanır, kod sürümleri değil film şeritleri, çünkü yalnızca tek bir animasyonu tek bir özelliğe uygulanan ancak örnekler film şeritleri kullanmayı değiştirilebilir. Kodda film şeridi bildirmeyi gösteren bir örnek için bkz: [film şeridi kullanarak bir özelliği animasyon](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md).  
  
 Tam bir örnek için bkz: [ana kare animasyon örneği](http://go.microsoft.com/fwlink/?LinkID=160012). Anahtar çerçeve animasyonları hakkında daha fazla bilgi için bkz: [anahtar çerçeve animasyonları genel bakış](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Anahtar çerçeve animasyonları genel bakış](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Animasyon genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
