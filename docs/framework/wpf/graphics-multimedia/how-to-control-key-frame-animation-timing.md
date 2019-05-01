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
ms.openlocfilehash: d0ea56b24f8fffeb688d297a675681bce3fdc4e0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61911513"
---
# <a name="how-to-control-key-frame-animation-timing"></a>Nasıl yapılır: Anahtar Çerçeve Animasyonu Zamanlamasını Denetleme

Bu örnekte anahtar çerçeveler içinde bir anahtar çerçeve animasyonu zamanlamasını denetlemek nasıl gösterir. Diğer animasyonlar gibi anahtar-çerçeve animasyonlara sahip bir <xref:System.Windows.Media.Animation.Timeline.Duration%2A> özelliği. Bir animasyonun süresini belirtmeye ek olarak, hangi parçası bir bu süre her anahtar çerçeveler için ayrılan belirtmeniz gerekir. Zamanı paylaştırmak için belirttiğiniz bir <xref:System.Windows.Media.Animation.KeyTime> her anahtar kare animasyon için.

<xref:System.Windows.Media.Animation.KeyTime> Her anahtar çerçevesi (Bu belirtmiyor bir anahtar kare oynatıldığında sürenin uzunluğunu) bir anahtar kare bittiğini belirtir. Belirtebileceğiniz bir <xref:System.Windows.Media.Animation.KeyTime> olarak bir <xref:System.TimeSpan> değeri, bir yüzdesi olarak veya <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> veya <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> özel değeri.

## <a name="example"></a>Örnek

Aşağıdaki örnekte bir <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> ekranda bir dikdörtgene animasyon ekleme için. Anahtar çerçeveler anahtar zaman ayarlanır <xref:System.TimeSpan> değerleri.

[!code-csharp[keyframes_snip#KeyTimesTimeSpanExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimestimespanexample)]
[!code-vb[keyframes_snip#KeyTimesTimeSpanExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimestimespanexample)]
[!code-xaml[keyframes_snip#KeyTimesTimeSpanExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimestimespanexample)]

Her bir anahtar kare değerini erişildiğinde, aşağıdaki şekilde gösterilmiştir.

![Anahtar değerlerini 3, 4 ve 10 saniyede tamamladı](./media/graphicsmm-keyframe-keytime1-timespan.png "graphicsmm_keyframe_keytime1_timespan")

Anahtar çerçeveler anahtar zaman yüzde değerleri ile ayarlanan dışında aynı olan bir animasyon sonraki örnekte gösterilmektedir.

[!code-csharp[keyframes_snip#KeyTimesPercentageExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespercentageexample)]
[!code-vb[keyframes_snip#KeyTimesPercentageExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespercentageexample)]
[!code-xaml[keyframes_snip#KeyTimesPercentageExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespercentageexample)]

Her bir anahtar kare değerini erişildiğinde, aşağıdaki şekilde gösterilmiştir.

![Anahtar değerlerini 3, 4 ve 10 saniyede tamamladı](./media/graphicsmm-keyframe-keytime2-percentage.png "graphicsmm_keyframe_keytime2_percentage")

Sonraki örnekte <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> anahtar saat değerleri.

[!code-csharp[keyframes_snip#KeyTimesUniformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimesuniformexample)]
[!code-vb[keyframes_snip#KeyTimesUniformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimesuniformexample)]
[!code-xaml[keyframes_snip#KeyTimesUniformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimesuniformexample)]

Her bir anahtar kare değerini erişildiğinde, aşağıdaki şekilde gösterilmiştir.

![Anahtar değerlerini 3.3,6.6 ve 9,9 saniyede tamamladı](./media/graphicsmm-keyframe-keytime3-uniform.png "graphicsmm_keyframe_keytime3_uniform")

Son örnekte <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> anahtar saat değerleri.

[!code-csharp[keyframes_snip#KeyTimesPacedExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespacedexample)]
[!code-vb[keyframes_snip#KeyTimesPacedExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespacedexample)]
[!code-xaml[keyframes_snip#KeyTimesPacedExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespacedexample)]

Her bir anahtar kare değerini erişildiğinde, aşağıdaki şekilde gösterilmiştir.

![Anahtar değerler 0, 5 ve 10 saniyede tamamladı](./media/graphicsmm-keyframe-keytime4-paced.png "graphicsmm_keyframe_keytime4_paced")

Kolaylık olması için bu örnek yerel animasyonları kullanır, kod sürümlerini değil film şeritleri, yalnızca tek bir animasyonu tek bir özelliğe uygulanmakta olduğu, ancak örnekler, film şeritleri kullanmayı değiştirilebilir. Kod içinde bir film şeridini bildirmeyi gösteren bir örnek için bkz: [görsel taslak kullanarak özelliğe animasyon ekleme](how-to-animate-a-property-by-using-a-storyboard.md).

Tam bir örnek için bkz. [ana kare animasyon örnek](https://go.microsoft.com/fwlink/?LinkID=160012). Anahtar çerçeve animasyonları hakkında daha fazla bilgi için bkz. [anahtar-çerçeve animasyonlara genel bakış](key-frame-animations-overview.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Anahtar-Çerçeve Animasyonlara Genel Bakış](key-frame-animations-overview.md)
- [Animasyona Genel bakış](animation-overview.md)
- [Nasıl Yapılır Konuları](animation-and-timing-how-to-topics.md)
