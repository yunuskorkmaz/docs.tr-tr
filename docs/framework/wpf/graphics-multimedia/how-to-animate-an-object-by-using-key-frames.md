---
title: 'Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Nesneye Animasyon Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], objects with key frames
- key frames [WPF], animating objects with
ms.assetid: b1f15ba9-cac7-4cea-8699-5c6b55c05c5e
ms.openlocfilehash: 0bc33b189fd856dbe8106c1db35bc18e27ea131e
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344713"
---
# <a name="how-to-animate-an-object-by-using-key-frames"></a>Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Nesneye Animasyon Ekleme
Bu örnekte, anahtar çerçeveleri kullanarak, bu örnekte <xref:System.Windows.Controls.Page.Background%2A> denetimin özelliği olan bir <xref:System.Windows.Controls.Page> nesnenin nasıl canlandırılanın gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> bir <xref:System.Windows.Controls.Page.Background%2A> <xref:System.Windows.Controls.Page> denetimin özelliği için renk değişikliklerini canlandırmak için sınıfı kullanır. Örnek animasyon, düzenli aralıklarla farklı bir arka plan fırçasına dönüşür. Bu animasyon, <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> üç farklı anahtar kare oluşturmak için sınıfı kullanır. Animasyon aşağıdaki şekilde anahtar kareler kullanır:  
  
1. İlk saniyenin sonunda, sınıfın bir örneğini <xref:System.Windows.Media.LinearGradientBrush> animasyona serer. Örneğin bu bölümü, rengin sarıdan turuncuya, kırmızıya geçmesi için arka plan rengine doğrusal bir degrade uygular.  
  
2. Sonraki saniyenin sonunda, sınıfın bir örneğini <xref:System.Windows.Media.RadialGradientBrush> animasyona serer. Örneğin bu bölümü, rengin beyazdan maviye, siyaha geçmesi için arka plan rengine radyal bir degrade uygular.  
  
3. Üçüncü saniyenin sonunda, sınıfın bir örneğini <xref:System.Windows.Media.DrawingBrush> animasyona serer. Örneğin bu bölümü arka plana bir dama tahtası deseni uygular.  
  
4. Animasyon yeniden başlar ve süresiz olarak yinelenir.  
  
> [!NOTE]
> <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame><xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> sınıfla birlikte kullanabileceğiniz tek anahtar kare türüdür. Değerlerde ani değişiklikler oluşturmak gibi <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> anahtar çerçeveler, yani bu örnekteki renk değişiklikleri aniden oluşur.  
  
 [!code-xaml[keyframes_snip#ObjectAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ObjectAnimationUsingKeyFramesExample.xaml#objectanimationusingkeyframeswholepage)]  
  
 Tam örnek için [Anahtar Çerçeve Animasyon Örneği'ne](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>
- <xref:System.Windows.Controls.Page.Background%2A>
- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>
- <xref:System.Windows.Media.LinearGradientBrush>
- <xref:System.Windows.Media.RadialGradientBrush>
- <xref:System.Windows.Media.DrawingBrush>
- [Anahtar-Çerçeve Animasyonlara Genel Bakış](key-frame-animations-overview.md)
- [Anahtar Çerçeve ile İlgili Nasıl Yapılır Konuları](key-frame-animation-how-to-topics.md)
