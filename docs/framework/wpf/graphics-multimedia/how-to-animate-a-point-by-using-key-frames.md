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
ms.openlocfilehash: edcba36644cf78d6e98f934d9bd8b593af38b328
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344874"
---
# <a name="how-to-animate-a-point-by-using-key-frames"></a>Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Noktaya Animasyon Ekleme
Bu örnek, <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> bir <xref:System.Windows.Point>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir elipsi üçgen bir yol boyunca hareket ettirir. Örnek, bir <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> <xref:System.Windows.Media.EllipseGeometry.Center%2A> <xref:System.Windows.Media.EllipseGeometry>. özelliğini canlandırmak için sınıfı kullanır. Bu animasyon aşağıdaki şekilde üç anahtar kare kullanır:  
  
1. İlk yarı saniye boyunca, elipsi başlangıç konumundan sabit bir hızda bir yol boyunca taşımak için <xref:System.Windows.Media.Animation.LinearPointKeyFrame> sınıfın bir örneğini kullanır. Değerler arasında düzgün <xref:System.Windows.Media.Animation.LinearPointKeyFrame> doğrusal enterpolasyon oluşturmak gibi doğrusal anahtar çerçeveleri.  
  
2. Sonraki yarım saniyenin sonunda, aniden bir <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> sonraki konuma yol boyunca elips taşımak için sınıfın bir örnek kullanır. Değerler arasında ani <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> sıçramalar oluşturmak gibi ayrık anahtar kareler.  
  
3. Son iki saniye boyunca, elipsi başlangıç konumuna geri taşımak için <xref:System.Windows.Media.Animation.SplinePointKeyFrame> sınıfın bir örneğini kullanır. Özellik değerlerine <xref:System.Windows.Media.Animation.SplinePointKeyFrame.KeySpline%2A> göre <xref:System.Windows.Media.Animation.SplinePointKeyFrame> değerler arasında değişken bir geçiş oluşturmak gibi spline anahtar çerçeveleri. Bu örnekte, animasyon yavaş yavaş başlar ve zaman diliminin sonuna doğru katlanarak hızlar.  
  
 [!code-csharp[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/PointAnimationUsingKeyFramesExample.cs#pointanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/pointanimationusingkeyframesexample.vb#pointanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/PointAnimationUsingKeyFramesExample.xaml#pointanimationusingkeyframeswholepage)]  
  
 Tam örnek için [Anahtar Çerçeve Animasyon Örneği'ne](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation)bakın.  
  
 Diğer animasyon örnekleri ile tutarlılık için, bu örneğin <xref:System.Windows.Media.Animation.Storyboard> kod sürümleri <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>bir nesne uygulamak için kullanın. Ancak, kod halinde tek bir animasyon uygularken, <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> bir <xref:System.Windows.Media.Animation.Storyboard>. Örneğin, Bir [Storyboard kullanmadan bir Özellik Animasyon](how-to-animate-a-property-without-using-a-storyboard.md)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>
- <xref:System.Windows.Media.EllipseGeometry.Center%2A?displayProperty=nameWithType>
- <xref:System.Windows.Media.EllipseGeometry>
- [Anahtar-Çerçeve Animasyonlara Genel Bakış](key-frame-animations-overview.md)
- [Anahtar Çerçeve ile İlgili Nasıl Yapılır Konuları](key-frame-animation-how-to-topics.md)
