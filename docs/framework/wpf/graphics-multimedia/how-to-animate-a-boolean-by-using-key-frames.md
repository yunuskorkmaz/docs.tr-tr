---
title: 'Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Boole Değerine Animasyon Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Booleans [WPF], animating with key frames
- animation [WPF], Booleans with key frames
- key frames [WPF], animating Booleans with
ms.assetid: 4b0fac96-6231-4fcf-9775-4dd673ddc785
ms.openlocfilehash: 59a72916721cccbe66f704253f148828fa8cd418
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62020211"
---
# <a name="how-to-animate-a-boolean-by-using-key-frames"></a>Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Boole Değerine Animasyon Ekleme
Bu örnekte, Boolean özelliği değerini animasyon ekleme işlemi gösterilmektedir bir <xref:System.Windows.Controls.Button> anahtar çerçeveler kullanarak bir denetim.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte <xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames> animasyon uygulamak için sınıfı <xref:System.Windows.UIElement.IsEnabled%2A> özelliği bir <xref:System.Windows.Controls.Button> denetimi. Anahtar çerçeveler Bu örnekte bir örneğini kullanması <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> sınıfı. Gibi ayrı anahtar çerçeveler <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> ani atlama, değerleri arasında oluşturur, bu animasyonu hareketini düzensiz olur.  
  
 [!code-csharp[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/BooleanAnimationUsingKeyFramesExample.cs#booleananimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/booleananimationusingkeyframesexample.vb#booleananimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/BooleanAnimationUsingKeyFramesExample.xaml#booleananimationusingkeyframeswholepage)]  
  
 Tam bir örnek için bkz. [ana kare animasyon örnek](https://go.microsoft.com/fwlink/?LinkID=160012).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames>
- <xref:System.Windows.UIElement.IsEnabled%2A>
- <xref:System.Windows.Controls.Button>
- [Anahtar-Çerçeve Animasyonlara Genel Bakış](key-frame-animations-overview.md)
- [Anahtar Çerçeve ile İlgili Nasıl Yapılır Konuları](key-frame-animation-how-to-topics.md)
