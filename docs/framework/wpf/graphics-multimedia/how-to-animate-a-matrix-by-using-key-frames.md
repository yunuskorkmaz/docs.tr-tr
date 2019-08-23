---
title: 'Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Matrise Animasyon Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], Matrix properties with key frames
- Matrix properties [WPF], animating with key frames
- key frames [WPF], animating Matrix properties with
ms.assetid: b851a4c7-ecb1-420e-9203-83e7afd037fd
ms.openlocfilehash: 6aa3e27cdfda7597c9b6acbf2980a2774f2b667b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963032"
---
# <a name="how-to-animate-a-matrix-by-using-key-frames"></a>Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Matrise Animasyon Ekleme
Bu örnek, <xref:System.Windows.Media.MatrixTransform.Matrix%2A> anahtar çerçeveler kullanarak bir <xref:System.Windows.Media.MatrixTransform> öğesinin özelliğinin nasıl hareketlendirileceğini gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, öğesinin <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> <xref:System.Windows.Media.MatrixTransform.Matrix%2A> özelliğine animasyon uygulamak için sınıfını kullanır. <xref:System.Windows.Media.MatrixTransform> Örnek, görünümünü ve <xref:System.Windows.Media.MatrixTransform> konumunu <xref:System.Windows.Controls.Button>dönüştürmek için nesnesini kullanır.  
  
 Bu animasyon iki anahtar <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> çerçeve oluşturmak için sınıfını kullanır ve aşağıdakiler ile birlikte şunları yapar:  
  
1. İlk 0,2 saniye <xref:System.Windows.Media.Matrix> boyunca ilk olarak hareketlenir. Örnek, <xref:System.Windows.Media.Matrix.M11%2A> ve <xref:System.Windows.Media.Matrix.M12%2A> özelliklerini <xref:System.Windows.Media.Matrix>değiştirir. Bu değişiklik, düğmenin genişlemesine ve çarpıtılmış olmasına neden olur. Örnek ayrıca, <xref:System.Windows.Media.Matrix.OffsetX%2A> düğme konumu değişmek için ve <xref:System.Windows.Media.Matrix.OffsetY%2A> özelliklerini de değiştirir.  
  
2. Saniyeyi <xref:System.Windows.Media.Matrix> 1,0 saniye içinde hareketlendirir. Düğme artık Eğilemez veya uzatılmadıysa düğme başka bir konuma gider.  
  
3. Animasyonu süresiz olarak yineler.  
  
> [!NOTE]
> <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> Nesneden türetilen anahtar çerçeveler değerler arasında ani zıplamalar oluştur, diğer bir deyişle, animasyonun hareketi düzensiz olur.  
  
 [!code-xaml[keyframes_snip#MatrixAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/MatrixAnimationUsingKeyFramesExample.xaml#matrixanimationusingkeyframeswholepage)]  
  
 Tüm örnek için bkz. [ana kare animasyon örneği](https://go.microsoft.com/fwlink/?LinkID=160012).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.MatrixTransform.Matrix%2A>
- <xref:System.Windows.Media.MatrixTransform>
- [Anahtar-Çerçeve Animasyonlara Genel Bakış](key-frame-animations-overview.md)
- [Anahtar Çerçeve ile İlgili Nasıl Yapılır Konuları](key-frame-animation-how-to-topics.md)
