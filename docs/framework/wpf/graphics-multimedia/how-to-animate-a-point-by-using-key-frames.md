---
title: 'Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Noktaya Animasyon Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], animating Points with
- Points [WPF], animating with key frames
- animation [WPF], Points with key frames
ms.assetid: d2e2ef10-0773-4133-856e-d41c09f60ded
ms.openlocfilehash: 9d976bca77629b85226da3d4e018a35cb522afef
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54738345"
---
# <a name="how-to-animate-a-point-by-using-key-frames"></a>Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Noktaya Animasyon Ekleme
Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> animasyon uygulamak için sınıfı bir <xref:System.Windows.Point>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir elips üçgen yol boyunca taşır. Örnekte <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> animasyon uygulamak için sınıfı <xref:System.Windows.Media.EllipseGeometry.Center%2A> özelliği bir <xref:System.Windows.Media.EllipseGeometry>. Bu animasyonu üç anahtar çerçeveler şu şekilde kullanılır:  
  
1.  İlk yarım saniye boyunca bir örneği kullanan <xref:System.Windows.Media.Animation.LinearPointKeyFrame> elips yol boyunca başlangıç konumundan bir hızda taşımak için sınıf. Gibi anahtar doğrusal çerçeveler <xref:System.Windows.Media.Animation.LinearPointKeyFrame> değerler arasında sorunsuz bir doğrusal ilişkilendirme oluşturun.  
  
2.  Sonraki sonuna sırasında yarım saniye kullanan bir örneğini <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> aniden elips yol boyunca sonraki konuma taşımak için sınıf. Gibi ayrı anahtar çerçeveler <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> değerleri arasında ani atlamalar oluşturun.  
  
3.  Son iki saniye boyunca bir örneği kullanan <xref:System.Windows.Media.Animation.SplinePointKeyFrame> elipsin başlangıç konumuna geri taşımak için sınıf. Eğri anahtar çercevesi ister <xref:System.Windows.Media.Animation.SplinePointKeyFrame> değerlerine göre değerleri arasında bir değişken geçiş oluşturmak <xref:System.Windows.Media.Animation.SplinePointKeyFrame.KeySpline%2A> özelliği. Bu örnekte, animasyon yavaş başlar ve zaman diliminin sonuna doğru katlanarak hızlandırır.  
  
 [!code-csharp[keyframes_snip#PointAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/PointAnimationUsingKeyFramesExample.cs#pointanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#PointAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/pointanimationusingkeyframesexample.vb#pointanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#PointAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/PointAnimationUsingKeyFramesExample.xaml#pointanimationusingkeyframeswholepage)]  
  
 Tam bir örnek için bkz. [ana kare animasyon örnek](https://go.microsoft.com/fwlink/?LinkID=160012).  
  
 Diğer animasyon örnekleriyle tutarlılık sağlamak için bu örnek kod sürümleri kullanan bir <xref:System.Windows.Media.Animation.Storyboard> uygulanacak nesne <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>. Ancak, tek bir animasyonu kod uygularken kullanmak daha basit olduğu <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> yöntemi kullanmak yerine bir <xref:System.Windows.Media.Animation.Storyboard>. Bir örnek için bkz. [özelliği olmadan kullanarak bir görsel taslak animasyon](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>
- <xref:System.Windows.Media.EllipseGeometry.Center%2A?displayProperty=nameWithType>
- <xref:System.Windows.Media.EllipseGeometry>
- [Anahtar-Çerçeve Animasyonlara Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)
- [Anahtar Çerçeve ile İlgili Nasıl Yapılır Konuları](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
