---
title: 'Nasıl yapılır: Animasyon Başlangıç Değerine Animasyon Çıkış Değeri Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF]
ms.assetid: b89a82be-b03d-481e-a8d3-cc513d09ca00
ms.openlocfilehash: 7f60a3cd3fc88c5bb2460864be6cee008dc672fd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557634"
---
# <a name="how-to-add-an-animation-output-value-to-an-animation-starting-value"></a>Nasıl yapılır: Animasyon Başlangıç Değerine Animasyon Çıkış Değeri Ekleme
Bu örnek bir animasyon başlangıç değerine animasyon çıkış değeri eklemek nasıl gösterir.  
  
## <a name="example"></a>Örnek  
 <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> Özelliği, animasyonlu bir özelliğin başlangıç değerine (temel değer) eklenen bir animasyon çıkış değeri isteyip istemediğinizi belirtir. Kullanabileceğiniz <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> en temel animasyonları ve çoğu anahtar çerçeve animasyonları özelliği. Daha fazla bilgi için bkz: [animasyon genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) ve [anahtar çerçeve animasyonları genel bakış](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).  
  
 Aşağıdaki örnek kullanmanın etkisini gösterir <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A?displayProperty=nameWithType> özelliğiyle <xref:System.Windows.Media.Animation.DoubleAnimation> ve kullanarak <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsAdditive%2A?displayProperty=nameWithType> özelliğiyle <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>.  
  
 [!code-xaml[timingbehaviors_snip#IsAdditiveWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/IsAdditiveExample.xaml#isadditivewholepage)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yineleme Döngüsü Sırasında Animasyon Değerlerini Biriktirme](../../../../docs/framework/wpf/graphics-multimedia/how-to-accumulate-animation-values-during-repeat-cycles.md)  
 [Animasyona Genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Anahtar-Çerçeve Animasyonlara Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Animasyon ve zamanlama](http://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
