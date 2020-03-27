---
title: 'Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Çifte Animasyon Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Doubles [WPF], animating with key frames
- animation [WPF], Doubles with key frames
- key frames [WPF], animating Doubles with
ms.assetid: 3a1a7dba-7694-4907-8a2f-3408baebfa82
ms.openlocfilehash: 9eab794cc8411230226cddc97beaa13c1bdd9405
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344923"
---
# <a name="how-to-animate-a-double-by-using-key-frames"></a>Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Çifte Animasyon Ekleme
Bu örnek, anahtar çerçeveleri kullanarak bir <xref:System.Double> gereken bir özelliğin değerini nasıl canlandırılabildiğini gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir dikdörtgeni ekran üzerinde taşır. Örnek, uygulanan bir <xref:System.Windows.Media.TranslateTransform> <xref:System.Windows.Shapes.Rectangle> <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> <xref:System.Windows.Media.TranslateTransform.X%2A> Süresiz olarak yineleyen bu animasyon, aşağıdaki şekilde üç anahtar kare kullanır:  
  
1. İlk üç saniye boyunca, dikdörtgeni <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> başlangıç konumundan 500 konumuna sabit bir hızda bir yol boyunca taşımak için sınıfın bir örneğini kullanır. Değerler arasında düzgün <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> doğrusal geçiş oluşturma gibi doğrusal anahtar çerçeveler.  
  
2. Dördüncü saniyenin sonunda, dikdörtgeni <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> aniden bir sonraki konuma taşımak için sınıfın bir örneğini kullanır. Değerler arasında ani <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> sıçramalar oluşturmak gibi ayrık anahtar kareler. Bu örnekte, dikdörtgen başlangıç konumundadır ve sonra aniden 500 konumunda görünür.  
  
3. Son iki saniye içinde, dikdörtgeni <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> başlangıç konumuna geri taşımak için sınıfın bir örneğini kullanır. Özellik değerine <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A> göre <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> değerler arasında değişken bir geçiş oluşturmak gibi spline anahtar çerçeveleri. Bu örnekte, dikdörtgen yavaş hareket ederek başlar ve sonra zaman diliminin sonuna doğru katlanarak hızlanır.  
  
 [!code-csharp[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/AltDoubleAnimationUsingKeyFramesExample.cs#altdoubleanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/altdoubleanimationusingkeyframesexample.vb#altdoubleanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/AltDoubleAnimationUsingKeyFramesExample.xaml#altdoubleanimationusingkeyframeswholepage)]  
  
 Tam örnek için [Anahtar Çerçeve Animasyon Örneği'ne](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation)bakın.  
  
 Diğer animasyon örnekleri ile tutarlılık için, bu örneğin <xref:System.Windows.Media.Animation.Storyboard> kod sürümleri <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>bir nesne uygulamak için kullanın. Alternatif olarak, kod da tek bir animasyon uygularken, <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> bir <xref:System.Windows.Media.Animation.Storyboard>. Örneğin, Bir [Storyboard kullanmadan bir Özellik Animasyon](how-to-animate-a-property-without-using-a-storyboard.md)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>
- <xref:System.Windows.Shapes.Rectangle>
- <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>
- <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>
- [Anahtar-Çerçeve Animasyonlara Genel Bakış](key-frame-animations-overview.md)
- [Anahtar Çerçeve ile İlgili Nasıl Yapılır Konuları](key-frame-animation-how-to-topics.md)
