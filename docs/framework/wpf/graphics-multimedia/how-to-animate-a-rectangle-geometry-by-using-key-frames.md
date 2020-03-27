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
ms.openlocfilehash: bcc9e7f198b8a20ffe13daf6508fb8a735937652
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344686"
---
# <a name="how-to-animate-a-rectangle-geometry-by-using-key-frames"></a>Nasıl yapılır: Anahtar Çerçeveler Kullanarak Dikdörtgen Geometriye Animasyon Ekleme
Bu örnek, anahtar çerçeveleri <xref:System.Windows.Media.RectangleGeometry.Rect%2A> kullanarak <xref:System.Windows.Media.RectangleGeometry> bir özelliği animasyon nasıl gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames> bir <xref:System.Windows.Media.RectangleGeometry>. özelliğini <xref:System.Windows.Media.RectangleGeometry.Rect%2A> canlandırmak için sınıfı kullanır. Bu animasyon aşağıdaki şekilde üç anahtar kare kullanır:  
  
1. İlk iki saniye boyunca, dikdörtgenin <xref:System.Windows.Media.Animation.LinearRectKeyFrame> konumu, genişliği ve yüksekliğinde kademeli bir değişikliği canlandırmak için sınıfın bir örneğini kullanır. Değerler arasında düzgün <xref:System.Windows.Media.Animation.LinearRectKeyFrame> doğrusal geçiş oluşturma gibi doğrusal anahtar çerçeveler.  
  
2. Sonraki yarım saniyenin sonunda, aniden dikdörtgenin <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> yüksekliğini azaltmak için sınıfın bir örneğini kullanır. Değerler arasında ani <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> değişiklikler oluşturmak gibi ayrık anahtar çerçeveleri, yani yükseklik düşüşü hızlı bir şekilde oluşur ve ince değildir.  
  
3. Son iki saniye boyunca, dikdörtgeni <xref:System.Windows.Media.Animation.SplineRectKeyFrame> orijinal boyutuna ve konumuna geri değiştirmek için sınıfın bir örneğini kullanır. Özellik değerlerine <xref:System.Windows.Media.Animation.SplineRectKeyFrame.KeySpline%2A> göre <xref:System.Windows.Media.Animation.SplineRectKeyFrame> değerler arasında değişken bir geçiş oluşturmak gibi spline anahtar çerçeveleri. Bu örnekte, değişim yavaş yavaş başlar ve zaman diliminin sonuna doğru katlanarak hızlar.  
  
 [!code-csharp[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/RectAnimationUsingKeyFramesExample.cs#rectanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/rectanimationusingkeyframesexample.vb#rectanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#RectAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/RectAnimationUsingKeyFramesExample.xaml#rectanimationusingkeyframeswholepage)]  
  
 Tam örnek için [Anahtar Çerçeve Animasyon Örneği'ne](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.RectangleGeometry>
- <xref:System.Windows.Media.RectangleGeometry.Rect%2A>
- <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames>
- [Anahtar-Çerçeve Animasyonlara Genel Bakış](key-frame-animations-overview.md)
- [Anahtar Çerçeve ile İlgili Nasıl Yapılır Konuları](key-frame-animation-how-to-topics.md)
