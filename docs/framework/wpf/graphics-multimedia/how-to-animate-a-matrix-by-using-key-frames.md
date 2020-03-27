---
title: 'Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Matrise Animasyon Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], Matrix properties with key frames
- Matrix properties [WPF], animating with key frames
- key frames [WPF], animating Matrix properties with
ms.assetid: b851a4c7-ecb1-420e-9203-83e7afd037fd
ms.openlocfilehash: eb596cf728f8a7cc1964963b8509f42bdd7a392a
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344913"
---
# <a name="how-to-animate-a-matrix-by-using-key-frames"></a>Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Matrise Animasyon Ekleme
Bu örnek, anahtar çerçeveleri <xref:System.Windows.Media.MatrixTransform.Matrix%2A> kullanarak <xref:System.Windows.Media.MatrixTransform> bir özelliği animasyon nasıl gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> bir <xref:System.Windows.Media.MatrixTransform>. özelliğini <xref:System.Windows.Media.MatrixTransform.Matrix%2A> canlandırmak için sınıfı kullanır. Örnek, <xref:System.Windows.Media.MatrixTransform> bir <xref:System.Windows.Controls.Button>.  
  
 Bu animasyon, <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> iki anahtar kare oluşturmak için sınıfı kullanır ve onlarla aşağıdakileri yapar:  
  
1. İlk 0.2 <xref:System.Windows.Media.Matrix> saniye boyunca ilk animasyon. Örnek, .'ın <xref:System.Windows.Media.Matrix.M11%2A> <xref:System.Windows.Media.Matrix.M12%2A> <xref:System.Windows.Media.Matrix>özelliklerini ve özelliklerini değiştirir. Bu değişiklik düğmenin esnemesine ve eğrilmeye neden olur. Örnek, düğmenin <xref:System.Windows.Media.Matrix.OffsetX%2A> <xref:System.Windows.Media.Matrix.OffsetY%2A> konumunu değiştirmesi için de ve özelliklerini değiştirir.  
  
2. Saniyeyi <xref:System.Windows.Media.Matrix> 1.0 saniyede canlandırın. Düğme artık eğriltilmiş veya uzatılmış değilken düğme başka bir konuma taşınır.  
  
3. Animasyonu süresiz olarak yineler.  
  
> [!NOTE]
> <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> Nesneden türeyen anahtar kareler değerler arasında ani atlar oluşturur, yani animasyonun hareketi sarsıntılıdır.  
  
 [!code-xaml[keyframes_snip#MatrixAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/MatrixAnimationUsingKeyFramesExample.xaml#matrixanimationusingkeyframeswholepage)]  
  
 Tam örnek için [Anahtar Çerçeve Animasyon Örneği'ne](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.MatrixTransform.Matrix%2A>
- <xref:System.Windows.Media.MatrixTransform>
- [Anahtar-Çerçeve Animasyonlara Genel Bakış](key-frame-animations-overview.md)
- [Anahtar Çerçeve ile İlgili Nasıl Yapılır Konuları](key-frame-animation-how-to-topics.md)
