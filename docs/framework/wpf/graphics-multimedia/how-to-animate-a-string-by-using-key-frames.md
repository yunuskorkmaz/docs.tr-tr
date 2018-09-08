---
title: 'Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Dizeye Animasyon Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], strings with key frames
- strings [WPF], animating with key frames
- key frames [WPF], animating strings with
ms.assetid: c62bc9fd-c09a-4227-bce0-0a1ab82049dd
ms.openlocfilehash: 1b55afd5938073a326789e67b66fec9cfce12015
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44189257"
---
# <a name="how-to-animate-a-string-by-using-key-frames"></a>Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Dizeye Animasyon Ekleme
Bu örnekte, bu örnekte, bir dizeye animasyon ekleme işlemi gösterilmektedir <xref:System.Windows.Controls.ContentControl.Content%2A> özelliği bir <xref:System.Windows.Controls.Button> anahtar çerçeveler kullanarak denetimi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames> animasyon uygulamak için sınıfı <xref:System.Windows.Controls.ContentControl.Content%2A> özelliği bir <xref:System.Windows.Controls.Button>.  
  
 Anahtar çerçeveler Bu örnekte bir örneğini kullanması <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> anahtar çerçeveler ile oluşturulan bir dize animasyon yalnızca ayrık anahtar çerçeveler kullanabileceğinizden sınıfı. Gibi ayrı anahtar çerçeveler <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> ani atlama, değerleri arasında oluşturur, animasyon değişiklikleri hızlı ve hafif değildir.  
  
 [!code-xaml[keyframes_snip#StringAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/StringAnimationUsingKeyFramesExample.xaml#stringanimationusingkeyframeswholepage)]  
  
 Tam bir örnek için bkz. [ana kare animasyon örnek](https://go.microsoft.com/fwlink/?LinkID=160012).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>  
 <xref:System.Windows.Controls.ContentControl.Content%2A>  
 <xref:System.Windows.Controls.Button>  
 <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame>  
 [Anahtar-Çerçeve Animasyonlara Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Anahtar Çerçeve ile İlgili Nasıl Yapılır Konuları](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
