---
title: 'Nasıl yapılır: Yineleme Döngüsü Sırasında Animasyon Değerlerini Biriktirme'
ms.date: 03/30/2017
helpviewer_keywords:
- accumulating animation values across repeating cycles [WPF]
- animation [WPF], accumulating values across repeating cycles
ms.assetid: 548df369-c7cc-4dab-b569-08b95ced2e7e
ms.openlocfilehash: 6e98b7eefd0c30e728b60926096c0f082bc079ab
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54587287"
---
# <a name="how-to-accumulate-animation-values-during-repeat-cycles"></a>Nasıl yapılır: Yineleme Döngüsü Sırasında Animasyon Değerlerini Biriktirme
Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> yineleme döngüleri arasında animasyon değerlerini biriktirme özelliği.  
  
## <a name="example"></a>Örnek  
 Kullanım <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> yineleme döngüleri arasında animasyon değerlerini temel ulaşıncaya kadar özelliği. Animasyon 9 kez yineler ayarlarsanız, örneğin, (<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> = "9 x") ve 10-15 arasında animasyon uygulamak için özelliğini ayarlayın (= 10 = 15), 15-20 ikinci döngüsü sırasında ilk döngü sırasında özelliği 10-15'e canlandırır , 25 üçüncü döngü vb. sırasında 20. Bu nedenle, her bir animasyon döngüsünün önceki animasyon döngüsünün bitiş animasyon değerini temel değer olarak kullanır.  
  
 Kullanabileceğiniz `IsCumulative` en temel animasyon ve çoğu anahtar çerçeve animasyon özelliği. Daha fazla bilgi için [animasyona genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) ve [anahtar-çerçeve animasyonlara genel bakış](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).  
  
 Aşağıdaki örnekte, dört dikdörtgenin genişliğini animasyon tarafından bu davranış gösterir. Örnek:  
  
-   İlk dikdörtgen canlandırır <xref:System.Windows.Media.Animation.DoubleAnimation> ve ayarlar <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> özelliğini `true`.  
  
-   İkinci dikdörtgen canlandırır <xref:System.Windows.Media.Animation.DoubleAnimation> ve ayarlar <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> özelliği varsayılan değerine `false`.  
  
-   Üçüncü dikdörtgen canlandırır <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> ve ayarlar <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> özelliğini `true`.  
  
-   Son dikdörtgen canlandırır <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> ve ayarlar <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> özelliğini `false`.  
  
 [!code-xaml[timingbehaviors_snip#IsCumulativeWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/IsCumulativeExample.xaml#iscumulativewholepage)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Animasyon Başlangıç Değerine Animasyon Çıkış Değeri Ekleme](../../../../docs/framework/wpf/graphics-multimedia/how-to-add-an-animation-output-value-to-an-animation-starting-value.md)
- [Animasyonu Yineleme](../../../../docs/framework/wpf/graphics-multimedia/how-to-repeat-an-animation.md)
- [Animasyona Genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [Anahtar-Çerçeve Animasyonlara Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)
- [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
