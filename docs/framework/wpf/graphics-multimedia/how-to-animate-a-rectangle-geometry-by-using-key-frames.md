---
title: 'Nasıl yapılır: Anahtar Çerçeveler Kullanarak Dikdörtgen Geometriye Animasyon Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], animating RectangleGeometry objects with
- RectangleGeometry objects [WPF], animating with key frames
- animation [WPF], RectangleGeometry objects with key frames
ms.assetid: a8b45ceb-0e32-4ba1-928f-df6d30db17c6
ms.openlocfilehash: 03953b79127ffceeb49e4ece2070d09f382448a5
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59311350"
---
# <a name="how-to-animate-a-rectangle-geometry-by-using-key-frames"></a>Nasıl yapılır: Anahtar Çerçeveler Kullanarak Dikdörtgen Geometriye Animasyon Ekleme
Bu örnek, animasyon ekleme işlemi gösterilmektedir <xref:System.Windows.Media.RectangleGeometry.Rect%2A> özelliği bir <xref:System.Windows.Media.RectangleGeometry> anahtar çerçeveler kullanarak.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames> animasyon uygulamak için sınıfı <xref:System.Windows.Media.RectangleGeometry.Rect%2A> özelliği bir <xref:System.Windows.Media.RectangleGeometry>. Bu animasyonu üç anahtar çerçeveler şu şekilde kullanılır:  
  
1. İlk iki saniye boyunca bir örneği kullanan <xref:System.Windows.Media.Animation.LinearRectKeyFrame> konumunu, genişliğini ve bir dikdörtgenin yüksekliğini değişim animasyon uygulamak için sınıfı. Gibi anahtar doğrusal çerçeveler <xref:System.Windows.Media.Animation.LinearRectKeyFrame> değerler arasında sorunsuz bir doğrusal geçişi oluşturun.  
  
2. Sonraki sonuna sırasında yarım saniye kullanan bir örneğini <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> aniden dikdörtgenin yüksekliğini azaltmak için sınıf. Gibi ayrı anahtar çerçeveler <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> ani değişiklikleri değerler arasında oluşturur, yükseklik hızla gerçekleşir ve ince değil.  
  
3. Son iki saniye boyunca bir örneği kullanan <xref:System.Windows.Media.Animation.SplineRectKeyFrame> dikdörtgeni özgün boyutunu ve konumunu geri değiştirmek için sınıf. Eğri anahtar çercevesi ister <xref:System.Windows.Media.Animation.SplineRectKeyFrame> değerlerine göre değerleri arasında bir değişken geçiş oluşturmak <xref:System.Windows.Media.Animation.SplineRectKeyFrame.KeySpline%2A> özelliği. Bu örnekte, değişiklik yavaş başlar ve zaman diliminin sonuna doğru katlanarak hızlandırır.  
  
 [!code-csharp[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/RectAnimationUsingKeyFramesExample.cs#rectanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/rectanimationusingkeyframesexample.vb#rectanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/RectAnimationUsingKeyFramesExample.xaml#rectanimationusingkeyframeswholepage)]  
  
 Tam bir örnek için bkz. [ana kare animasyon örnek](https://go.microsoft.com/fwlink/?LinkID=160012).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.RectangleGeometry>
- <xref:System.Windows.Media.RectangleGeometry.Rect%2A>
- <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames>
- [Anahtar-Çerçeve Animasyonlara Genel Bakış](key-frame-animations-overview.md)
- [Anahtar Çerçeve ile İlgili Nasıl Yapılır Konuları](key-frame-animation-how-to-topics.md)
