---
title: 'Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Nesneye Animasyon Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], objects with key frames
- key frames [WPF], animating objects with
ms.assetid: b1f15ba9-cac7-4cea-8699-5c6b55c05c5e
ms.openlocfilehash: ffbe1845b634c8f94eb6a10dfa44fcf9903e0cd5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933903"
---
# <a name="how-to-animate-an-object-by-using-key-frames"></a>Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Nesneye Animasyon Ekleme
Bu örnek, anahtar çerçeveler kullanarak bu örnekteki <xref:System.Windows.Controls.Page.Background%2A> bir <xref:System.Windows.Controls.Page> denetimin özelliği olan bir nesnenin nasıl hareketlendirileceğini gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> <xref:System.Windows.Controls.Page.Background%2A> <xref:System.Windows.Controls.Page> denetimin özelliği için renk değişikliklerine animasyon uygulamak için sınıfını kullanır. Örnek animasyon, düzenli aralıklarla farklı bir arka plan fırçasına değişir. Bu animasyon üç farklı <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> anahtar çerçeve oluşturmak için sınıfını kullanır. Animasyon aşağıdaki şekilde anahtar çerçeveler kullanır:  
  
1. İlk saniyenin sonunda, <xref:System.Windows.Media.LinearGradientBrush> sınıfının bir örneğini hareketlendirir. Örneğin bu bölümü, arka plan rengine doğrusal bir gradyan uygular ve bu sayede renk geçişleri sarıdan turuncu ' a kadar kırmızıya olur.  
  
2. Sonraki saniyenin sonunda, <xref:System.Windows.Media.RadialGradientBrush> sınıfının bir örneğini hareketlendirir. Örneğin bu bölümü, arka plan rengine bir radyal gradyan uygular, böylece renk geçişi beyaz, mavi ile siyah arasında olur.  
  
3. Üçüncü saniyenin sonunda, <xref:System.Windows.Media.DrawingBrush> sınıfının bir örneğini hareketlendirir. Örneğin bu bölümü arka plana dama tahtası için bir model uygular.  
  
4. Animasyon yeniden başlar ve süresiz olarak yinelenir.  
  
> [!NOTE]
> <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>, <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> sınıfıyla kullanabileceğiniz tek anahtar çerçevesi türüdür. Değerlerde ani değişiklikler <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> oluşturma gibi önemli çerçeveler, diğer bir deyişle, bu örnekteki renk değişiklikleri aniden meydana gelir.  
  
 [!code-xaml[keyframes_snip#ObjectAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ObjectAnimationUsingKeyFramesExample.xaml#objectanimationusingkeyframeswholepage)]  
  
 Tüm örnek için bkz. [ana kare animasyon örneği](https://go.microsoft.com/fwlink/?LinkID=160012).  
  
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
