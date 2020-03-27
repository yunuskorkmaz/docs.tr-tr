---
title: 'Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Dizeye Animasyon Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], strings with key frames
- strings [WPF], animating with key frames
- key frames [WPF], animating strings with
ms.assetid: c62bc9fd-c09a-4227-bce0-0a1ab82049dd
ms.openlocfilehash: c954806ca901bbfc3ab6d4bbcc237cd0e404f154
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344646"
---
# <a name="how-to-animate-a-string-by-using-key-frames"></a>Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Dizeye Animasyon Ekleme
Bu örnekte, anahtar çerçeveleri kullanarak, bu örnekte bir denetimin <xref:System.Windows.Controls.ContentControl.Content%2A> özelliği olan bir <xref:System.Windows.Controls.Button> dize nasıl animasyona alınır gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames> bir <xref:System.Windows.Controls.Button>. özelliğini <xref:System.Windows.Controls.ContentControl.Content%2A> canlandırmak için sınıfı kullanır.  
  
 Bu örnekteki tüm anahtar kareler <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> sınıfın bir örneğini kullanır, çünkü anahtar çerçevelerle oluşturulan bir dize animasyonu yalnızca ayrı anahtar çerçeveleri kullanabilir. Değerler arasında ani <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> sıçramalar oluşturmak gibi ayrık anahtar kareler, yani animasyondeğişiklikleri hızlı bir şekilde oluşur ve ince değildir.  
  
 [!code-xaml[keyframes_snip#StringAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/StringAnimationUsingKeyFramesExample.xaml#stringanimationusingkeyframeswholepage)]  
  
 Tam örnek için [Anahtar Çerçeve Animasyon Örneği'ne](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>
- <xref:System.Windows.Controls.ContentControl.Content%2A>
- <xref:System.Windows.Controls.Button>
- <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame>
- [Anahtar-Çerçeve Animasyonlara Genel Bakış](key-frame-animations-overview.md)
- [Anahtar Çerçeve ile İlgili Nasıl Yapılır Konuları](key-frame-animation-how-to-topics.md)
