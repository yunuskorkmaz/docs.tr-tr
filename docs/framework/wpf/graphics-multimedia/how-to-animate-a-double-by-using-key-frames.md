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
ms.openlocfilehash: 67466bbb5fd7e7a46c312e14666c23048bf43d80
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45521222"
---
# <a name="how-to-animate-a-double-by-using-key-frames"></a>Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Çifte Animasyon Ekleme
Bu örnek, alan bir özelliğin değerine animasyon ekleme işlemi gösterilmektedir bir <xref:System.Double> anahtar çerçeveler kullanarak.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir dikdörtgen ekran boyunca taşır. Örnekte <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> animasyon uygulamak için sınıfı <xref:System.Windows.Media.TranslateTransform.X%2A> özelliği bir <xref:System.Windows.Media.TranslateTransform> uygulanan bir <xref:System.Windows.Shapes.Rectangle>. Süresiz olarak yinelenen animasyon, üç anahtar çerçeveler aşağıdaki şekilde kullanır:  
  
1.  İlk üç saniye boyunca bir örneği kullanan <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> yol dikdörtgen bir hızda başlangıç konumundan 500 konuma taşımak için sınıf. Gibi anahtar doğrusal çerçeveler <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> değerler arasında sorunsuz bir doğrusal geçişi oluşturun.  
  
2.  Dördüncü ikinci sonunda bir örneği kullanan <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> aniden dikdörtgen sonraki konuma taşımak için sınıf. Gibi ayrı anahtar çerçeveler <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> değerleri arasında ani atlamalar oluşturun. Bu örnekte, dikdörtgen başlangıç konumunda ve aniden 500 konumunda görünür.  
  
3.  Son iki saniye içinde bir örneği kullanan <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> rectangle geri başlangıç konumuna taşımak için sınıf. Eğri anahtar çercevesi ister <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> değerini göre değerler arasında değişken bir geçiş oluşturmak <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A> özelliği. Bu örnekte, dikdörtgen yavaş taşıyarak başlar ve ardından katlanarak zaman diliminin sonuna doğru hızlandırır.  
  
 [!code-csharp[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/AltDoubleAnimationUsingKeyFramesExample.cs#altdoubleanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/altdoubleanimationusingkeyframesexample.vb#altdoubleanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/AltDoubleAnimationUsingKeyFramesExample.xaml#altdoubleanimationusingkeyframeswholepage)]  
  
 Tam bir örnek için bkz. [ana kare animasyon örnek](https://go.microsoft.com/fwlink/?LinkID=160012).  
  
 Diğer animasyon örnekleriyle tutarlılık sağlamak için bu örnek kod sürümleri kullanan bir <xref:System.Windows.Media.Animation.Storyboard> uygulanacak nesne <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>. Alternatif olarak, kod içinde tek bir animasyonu uygularken kullanmak daha basit olduğu <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> yöntemi kullanmak yerine bir <xref:System.Windows.Media.Animation.Storyboard>. Bir örnek için bkz. [özelliği olmadan kullanarak bir görsel taslak animasyon](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>  
 <xref:System.Windows.Shapes.Rectangle>  
 <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>  
 <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>  
 <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>  
 [Anahtar-Çerçeve Animasyonlara Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Anahtar Çerçeve ile İlgili Nasıl Yapılır Konuları](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
