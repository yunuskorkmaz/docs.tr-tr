---
title: 'Nasıl yapılır: Animasyon Başlangıç Değerine Animasyon Çıkış Değeri Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF]
ms.assetid: b89a82be-b03d-481e-a8d3-cc513d09ca00
ms.openlocfilehash: 3f1110880b7a8d4bcef40bcb66bcade6597a15dc
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56303367"
---
# <a name="how-to-add-an-animation-output-value-to-an-animation-starting-value"></a>Nasıl yapılır: Animasyon Başlangıç Değerine Animasyon Çıkış Değeri Ekleme
Bu örnek, bir animasyon başlangıç değerine animasyon çıkış değeri ekleme gösterir.  
  
## <a name="example"></a>Örnek  
 <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> Özelliği, bir animasyonlu özelliğinin başlangıç değerine (temel değer) eklenen bir animasyon çıkış değeri isteyip istemediğinizi belirtir. Kullanabileceğiniz <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> en temel animasyon ve çoğu anahtar çerçeve animasyon özelliği. Daha fazla bilgi için [animasyona genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) ve [anahtar-çerçeve animasyonlara genel bakış](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).  
  
 Aşağıdaki örnek kullanarak etkisini gösterir <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A?displayProperty=nameWithType> özelliğiyle <xref:System.Windows.Media.Animation.DoubleAnimation> ve kullanarak <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsAdditive%2A?displayProperty=nameWithType> özelliğiyle <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>.  
  
 [!code-xaml[timingbehaviors_snip#IsAdditiveWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/IsAdditiveExample.xaml#isadditivewholepage)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Yineleme Döngüsü Sırasında Animasyon Değerlerini Biriktirme](../../../../docs/framework/wpf/graphics-multimedia/how-to-accumulate-animation-values-during-repeat-cycles.md)
- [Animasyona Genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [Anahtar-Çerçeve Animasyonlara Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)
- [Animasyon ve zamanlama ile ilgili nasıl yapılır konuları](animation-and-timing-how-to-topics.md)
