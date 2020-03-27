---
title: 'Nasıl yapılır: Anahtar Çerçeve Animasyonu Zamanlamasını Denetleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], timing
- timing key-frame animation
ms.assetid: b059216f-7d4b-4ca8-a019-bc287ee7bf16
ms.openlocfilehash: 8cfd2be0bbc526ed92a5fb1b558a5a41dc9c3113
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344730"
---
# <a name="how-to-control-key-frame-animation-timing"></a>Nasıl yapılır: Anahtar Çerçeve Animasyonu Zamanlamasını Denetleme

Bu örnek, anahtar kare animasyonu içindeki anahtar karelerin zamanlamasını nasıl denetler, gösterir. Diğer animasyonlar gibi, anahtar kare <xref:System.Windows.Media.Animation.Timeline.Duration%2A> animasyonların da bir özelliği vardır. Animasyonun süresini belirtmenin yanı sıra, bu sürenin her bir anahtar çerçevesine hangi bölümünün ayrılmış olduğunu belirtmeniz gerekir. Zamanı tahsis etmek için, <xref:System.Windows.Media.Animation.KeyTime> animasyondaki her anahtar kare için bir tane belirtirsiniz.

Her <xref:System.Windows.Media.Animation.KeyTime> anahtar kare için bir anahtar çerçevesi sona erdiğinde belirtilir (bir anahtar çerçevesi çalış süresini belirtmez). Bir <xref:System.Windows.Media.Animation.KeyTime> <xref:System.TimeSpan> değeri bir değer olarak, yüzde olarak <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> veya <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> özel değer olarak belirtebilirsiniz.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> ekran daki bir dikdörtgeni canlandırmak için a kullanır. Anahtar çerçevelerin anahtar süreleri değerlerle <xref:System.TimeSpan> ayarlanır.

[!code-csharp[keyframes_snip#KeyTimesTimeSpanExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimestimespanexample)]
[!code-vb[keyframes_snip#KeyTimesTimeSpanExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimestimespanexample)]
[!code-xaml[keyframes_snip#KeyTimesTimeSpanExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimestimespanexample)]

Aşağıdaki resimde, her anahtar çerçevenin değerine ne zaman ulaşıldığı gösterilmektedir.

![Anahtar değerlere 3, 4 ve 10 saniyede ulaşılır](./media/graphicsmm-keyframe-keytime1-timespan.png "graphicsmm_keyframe_keytime1_timespan")

Sonraki örnekte, anahtar çerçevelerin anahtar süreleri yüzde değerleriyle ayarlanan dışında, aynı olan bir animasyon gösterilmektedir.

[!code-csharp[keyframes_snip#KeyTimesPercentageExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespercentageexample)]
[!code-vb[keyframes_snip#KeyTimesPercentageExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespercentageexample)]
[!code-xaml[keyframes_snip#KeyTimesPercentageExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespercentageexample)]

Aşağıdaki resimde, her anahtar çerçevenin değerine ne zaman ulaşıldığı gösterilmektedir.

![Anahtar değerlere 3, 4 ve 10 saniyede ulaşılır](./media/graphicsmm-keyframe-keytime2-percentage.png "graphicsmm_keyframe_keytime2_percentage")

Sonraki örnekanahtar <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> zaman değerlerini kullanır.

[!code-csharp[keyframes_snip#KeyTimesUniformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimesuniformexample)]
[!code-vb[keyframes_snip#KeyTimesUniformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimesuniformexample)]
[!code-xaml[keyframes_snip#KeyTimesUniformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimesuniformexample)]

Aşağıdaki resimde, her anahtar çerçevenin değerine ne zaman ulaşıldığı gösterilmektedir.

![Anahtar değerlere 3.3,6.6 ve 9.9 saniye olarak ulaşılır](./media/graphicsmm-keyframe-keytime3-uniform.png "graphicsmm_keyframe_keytime3_uniform")

Son örnek, <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> anahtar zaman değerlerini kullanır.

[!code-csharp[keyframes_snip#KeyTimesPacedExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespacedexample)]
[!code-vb[keyframes_snip#KeyTimesPacedExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespacedexample)]
[!code-xaml[keyframes_snip#KeyTimesPacedExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespacedexample)]

Aşağıdaki resimde, her anahtar çerçevenin değerine ne zaman ulaşıldığı gösterilmektedir.

![Anahtar değerlere 0, 5 ve 10 saniyede ulaşılır](./media/graphicsmm-keyframe-keytime4-paced.png "graphicsmm_keyframe_keytime4_paced")

Basitlik için, bu örneğin kod sürümleri, yalnızca tek bir animasyon tek bir özelliğe uygulandığından, film şeridi değil, yerel animasyonlar kullanır, ancak örnekler bunun yerine film şeridi kullanmak üzere değiştirilebilir. Bir film şeridinin kod da nasıl bildirilen bir örnek için, [Storyboard kullanarak Bir Özellik Animasyon'a](how-to-animate-a-property-by-using-a-storyboard.md)bakın.

Tam örnek için [Anahtar Çerçeve Animasyon Örneği'ne](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation)bakın. Anahtar kare animasyonları hakkında daha fazla bilgi için [Anahtar Kare Animasyonlarına Genel Bakış'a](key-frame-animations-overview.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Anahtar-Çerçeve Animasyonlara Genel Bakış](key-frame-animations-overview.md)
- [Animasyona Genel bakış](animation-overview.md)
- [Nasıl Yapılır Konuları](animation-and-timing-how-to-topics.md)
