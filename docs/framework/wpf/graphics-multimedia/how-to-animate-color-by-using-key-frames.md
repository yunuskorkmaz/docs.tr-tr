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
ms.openlocfilehash: e579c4beb757ccf58eb1b9ca1f3852a5b96cac1a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59326092"
---
# <a name="how-to-animate-color-by-using-key-frames"></a>Nasıl yapılır: Anahtar Çerçeveler Kullanarak Renge Animasyon Ekleme
Bu örnek, animasyon ekleme işlemi gösterilmektedir <xref:System.Windows.Media.SolidColorBrush.Color%2A> , bir <xref:System.Windows.Media.SolidColorBrush> anahtar çerçeveler kullanarak.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames> animasyon uygulamak için sınıfı <xref:System.Windows.Media.SolidColorBrush.Color%2A> özelliği bir <xref:System.Windows.Media.SolidColorBrush>. Bu animasyonu üç anahtar çerçeveler şu şekilde kullanılır:  
  
1. İlk iki saniye boyunca bir örneği kullanan <xref:System.Windows.Media.Animation.LinearColorKeyFrame> rengi yeşilden kırmızıya kademeli olarak değiştirmek için sınıf. Gibi anahtar doğrusal çerçeveler <xref:System.Windows.Media.Animation.LinearColorKeyFrame> değerler arasında sorunsuz bir doğrusal geçişi oluşturun.  
  
2. Sonraki sonuna sırasında yarım saniye kullanan bir örneğini <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> sınıfı hızlı bir şekilde kırmızı rengi sarı olarak değişir. Gibi ayrı anahtar çerçeveler <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> ani değişiklikleri değerler arasında oluşturur, bu bölümü animasyonun rengi değişiklik hızla gerçekleşir ve ince değil.  
  
3. Son iki saniye boyunca bir örneği kullanan <xref:System.Windows.Media.Animation.SplineColorKeyFrame> yeniden rengini değiştirmek için sınıf — yeşil sarı arka bu süre. Eğri anahtar çercevesi ister <xref:System.Windows.Media.Animation.SplineColorKeyFrame> değerlerine göre değerleri arasında bir değişken geçiş oluşturmak <xref:System.Windows.Media.Animation.SplineColorKeyFrame.KeySpline%2A> özelliği. Bu örnekte, renginde de değişiklik yavaş başlar ve zaman diliminin sonuna doğru katlanarak hızlandırır.  
  
 [!code-csharp[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/ColorAnimationUsingKeyFramesExample.cs#coloranimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/coloranimationusingkeyframesexample.vb#coloranimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ColorAnimationUsingKeyFramesExample.xaml#coloranimationusingkeyframeswholepage)]  
  
 Tam bir örnek için bkz. [ana kare animasyon örnek](https://go.microsoft.com/fwlink/?LinkID=160012).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.SolidColorBrush.Color%2A>
- <xref:System.Windows.Media.SolidColorBrush>
- <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>
- [Anahtar-Çerçeve Animasyonlara Genel Bakış](key-frame-animations-overview.md)
- [Anahtar Çerçeve ile İlgili Nasıl Yapılır Konuları](key-frame-animation-how-to-topics.md)
