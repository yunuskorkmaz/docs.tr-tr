---
title: 'Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Nesneye Animasyon Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], objects with key frames
- key frames [WPF], animating objects with
ms.assetid: b1f15ba9-cac7-4cea-8699-5c6b55c05c5e
ms.openlocfilehash: 5e948b574e1b4a1c431b9495583e9579502576a8
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43416340"
---
# <a name="how-to-animate-an-object-by-using-key-frames"></a>Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Nesneye Animasyon Ekleme
Bu örnekte olduğu bir nesneye animasyon uygulamak gösterilmektedir <xref:System.Windows.Controls.Page.Background%2A> özelliği bir <xref:System.Windows.Controls.Page> anahtar çerçeveler kullanarak denetimi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> renge animasyon ekleme için sınıf değişiklikleri için <xref:System.Windows.Controls.Page.Background%2A> özelliği bir <xref:System.Windows.Controls.Page> denetimi. Örnek animasyon için farklı bir arkaplan Fırçası düzenli aralıklarla değiştirir. Bu animasyon kullanır <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> üç farklı anahtar kare oluşturmak için sınıf. Anahtar çerçeveler aşağıdaki şekilde kullanır:  
  
1.  Örneği ilk ikinci sonunda canlandırır <xref:System.Windows.Media.LinearGradientBrush> sınıfı. Turuncu kırmızı, sarı renk geçişleri için bu bölüm örneğin arka plan rengi doğrusal gradyan geçerlidir.  
  
2.  Sonraki saniye sonunda bir örneğini canlandırır <xref:System.Windows.Media.RadialGradientBrush> sınıfı. Bu bölümde Örneğin, bir radyal gradyan arka plan rengi uygular rengi siyaha mavi beyaz gelen geçiş.  
  
3.  Üçüncü ikinci sonunda bir örneğini canlandırır <xref:System.Windows.Media.DrawingBrush> sınıfı. Bu bölümde örneğin arka planına dama tahtası desenini uygular.  
  
4.  Animasyonun yeniden başlar ve sonsuza kadar yinelenir.  
  
> [!NOTE]
>  <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> sadece türü ile kullanabileceğiniz anahtar çerçeve <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> sınıfı. Anahtar çerçeveleri gibi <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> ani değişiklikleri değerleri, diğer bir deyişle oluşturun, bu örnekte renk değişiklikleri aniden ortaya çıkar.  
  
 [!code-xaml[keyframes_snip#ObjectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ObjectAnimationUsingKeyFramesExample.xaml#objectanimationusingkeyframeswholepage)]  
  
 Tam bir örnek için bkz. [ana kare animasyon örnek](https://go.microsoft.com/fwlink/?LinkID=160012).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>  
 <xref:System.Windows.Controls.Page.Background%2A>  
 <xref:System.Windows.Controls.Page>  
 <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>  
 <xref:System.Windows.Media.LinearGradientBrush>  
 <xref:System.Windows.Media.RadialGradientBrush>  
 <xref:System.Windows.Media.DrawingBrush>  
 [Anahtar-Çerçeve Animasyonlara Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Anahtar Çerçeve ile İlgili Nasıl Yapılır Konuları](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
