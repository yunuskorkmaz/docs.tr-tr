---
title: 'Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Matrise Animasyon Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], Matrix properties with key frames
- Matrix properties [WPF], animating with key frames
- key frames [WPF], animating Matrix properties with
ms.assetid: b851a4c7-ecb1-420e-9203-83e7afd037fd
ms.openlocfilehash: ff5320fa5b4441ae3e0f414b274ab9118b77ec50
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59336804"
---
# <a name="how-to-animate-a-matrix-by-using-key-frames"></a>Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Matrise Animasyon Ekleme
Bu örnek, animasyon ekleme işlemi gösterilmektedir <xref:System.Windows.Media.MatrixTransform.Matrix%2A> özelliği bir <xref:System.Windows.Media.MatrixTransform> anahtar çerçeveler kullanarak.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> animasyon uygulamak için sınıfı <xref:System.Windows.Media.MatrixTransform.Matrix%2A> özelliği bir <xref:System.Windows.Media.MatrixTransform>. Örnekte <xref:System.Windows.Media.MatrixTransform> konumunu ve görünümünü dönüştürmesini nesne bir <xref:System.Windows.Controls.Button>.  
  
 Bu animasyon kullanır <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> iki anahtar kare oluşturmak için sınıf ve bunları ile aşağıdakileri yapar:  
  
1. İlk canlandırır <xref:System.Windows.Media.Matrix> ilk 0.2 saniye boyunca. Örnek değişiklikleri <xref:System.Windows.Media.Matrix.M11%2A> ve <xref:System.Windows.Media.Matrix.M12%2A> özelliklerini <xref:System.Windows.Media.Matrix>. Bu değişiklik, esnetme için dengesiz hale düğmesini neden olur. Örnek ayrıca değiştirir <xref:System.Windows.Media.Matrix.OffsetX%2A> ve <xref:System.Windows.Media.Matrix.OffsetY%2A> özellikleri böylece düğmeyi konumunu değiştirir.  
  
2. İkinci canlandırır <xref:System.Windows.Media.Matrix> 1.0 saniye. Düğme artık dengesiz esnetildiğini veya sırasında düğmeyi başka bir konuma taşır.  
  
3. Animasyon süresiz olarak tekrarlar.  
  
> [!NOTE]
>  Anahtarı türetin çerçeveler <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> nesnesi değerleri arasında ani atlamalar oluşturur, diğer bir deyişle, animasyon hareketini düzensiz olur.  
  
 [!code-xaml[keyframes_snip#MatrixAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/MatrixAnimationUsingKeyFramesExample.xaml#matrixanimationusingkeyframeswholepage)]  
  
 Tam bir örnek için bkz. [ana kare animasyon örnek](https://go.microsoft.com/fwlink/?LinkID=160012).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.MatrixTransform.Matrix%2A>
- <xref:System.Windows.Media.MatrixTransform>
- [Anahtar-Çerçeve Animasyonlara Genel Bakış](key-frame-animations-overview.md)
- [Anahtar Çerçeve ile İlgili Nasıl Yapılır Konuları](key-frame-animation-how-to-topics.md)
