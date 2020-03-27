---
title: 'Nasıl yapılır: Anahtar Çerçeveler Kullanarak Renge Animasyon Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [WPF], animating with key frames
- animation [WPF], colors with key frames
- key frames [WPF], animating colors with
ms.assetid: ab04ffa6-4de9-4d5b-a3b4-4e35d5b2ef35
ms.openlocfilehash: 8a444706f7541b52722ab8257a88e76c3e1b0938
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344743"
---
# <a name="how-to-animate-color-by-using-key-frames"></a>Nasıl yapılır: Anahtar Çerçeveler Kullanarak Renge Animasyon Ekleme
Bu örnek, anahtar kareler <xref:System.Windows.Media.SolidColorBrush.Color%2A> kullanarak <xref:System.Windows.Media.SolidColorBrush> bir animasyon nasıl gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames> bir <xref:System.Windows.Media.SolidColorBrush>. özelliğini <xref:System.Windows.Media.SolidColorBrush.Color%2A> canlandırmak için sınıfı kullanır. Bu animasyon aşağıdaki şekilde üç anahtar kare kullanır:  
  
1. İlk iki saniye boyunca, rengi <xref:System.Windows.Media.Animation.LinearColorKeyFrame> yavaş yavaş yeşilden kırmızıya değiştirmek için sınıfın bir örneğini kullanır. Değerler arasında düzgün <xref:System.Windows.Media.Animation.LinearColorKeyFrame> doğrusal geçiş oluşturma gibi doğrusal anahtar çerçeveler.  
  
2. Sonraki yarım saniyenin sonunda, rengi hızla <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> kırmızıdan sarıya değiştirmek için sınıfın bir örneğini kullanır. Değerler arasında ani <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> değişiklikler oluşturmak gibi ayrık anahtar çerçeveleri, yani animasyonun bu bölümündeki renk değişikliği hızlı bir şekilde gerçekleşir ve ince değildir.  
  
3. Son iki saniye boyunca, rengi <xref:System.Windows.Media.Animation.SplineColorKeyFrame> yeniden değiştirmek için sınıfın bir örneğini kullanır—bu kez sarıdan yeşile geri. Özellik değerlerine <xref:System.Windows.Media.Animation.SplineColorKeyFrame.KeySpline%2A> göre <xref:System.Windows.Media.Animation.SplineColorKeyFrame> değerler arasında değişken bir geçiş oluşturmak gibi spline anahtar çerçeveleri. Bu örnekte, renk değişimi yavaş yavaş başlar ve zaman diliminin sonuna doğru katlanarak hızlar.  
  
 [!code-csharp[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/ColorAnimationUsingKeyFramesExample.cs#coloranimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/coloranimationusingkeyframesexample.vb#coloranimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ColorAnimationUsingKeyFramesExample.xaml#coloranimationusingkeyframeswholepage)]  
  
 Tam örnek için [Anahtar Çerçeve Animasyon Örneği'ne](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.SolidColorBrush.Color%2A>
- <xref:System.Windows.Media.SolidColorBrush>
- <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>
- [Anahtar-Çerçeve Animasyonlara Genel Bakış](key-frame-animations-overview.md)
- [Anahtar Çerçeve ile İlgili Nasıl Yapılır Konuları](key-frame-animation-how-to-topics.md)
