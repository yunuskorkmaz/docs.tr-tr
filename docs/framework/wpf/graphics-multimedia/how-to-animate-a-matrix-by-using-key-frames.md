---
title: "Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Matrise Animasyon Ekleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], Matrix properties with key frames
- Matrix properties [WPF], animating with key frames
- key frames [WPF], animating Matrix properties with
ms.assetid: b851a4c7-ecb1-420e-9203-83e7afd037fd
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c8c67b5c8e179485083a40aa8a196fbee3e0fc24
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-a-matrix-by-using-key-frames"></a>Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Matrise Animasyon Ekleme
Bu örnek animasyon gösterilmektedir <xref:System.Windows.Media.MatrixTransform.Matrix%2A> özelliği bir <xref:System.Windows.Media.MatrixTransform> anahtar çerçeveler kullanarak.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames> animasyon sınıfı <xref:System.Windows.Media.MatrixTransform.Matrix%2A> özelliği bir <xref:System.Windows.Media.MatrixTransform>. Örnek kullanır <xref:System.Windows.Media.MatrixTransform> görünümünü ve konumunu dönüştürmek için nesne bir <xref:System.Windows.Controls.Button>.  
  
 Bu animasyon kullanır <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> iki anahtar çerçeve oluşturmak için sınıf ve bunlar ile aşağıdakileri yapar:  
  
1.  İlk canlandırır <xref:System.Windows.Media.Matrix> ilk 0.2 saniye sırasında. Örnek değişiklikleri <xref:System.Windows.Media.Matrix.M11%2A> ve <xref:System.Windows.Media.Matrix.M12%2A> özelliklerini <xref:System.Windows.Media.Matrix>. Bu değişiklik düğmesine uzatma ve eğri duruma neden olur. Bu örnek ayrıca değiştirir <xref:System.Windows.Media.Matrix.OffsetX%2A> ve <xref:System.Windows.Media.Matrix.OffsetY%2A> özellikleri böylece düğme konumunu değiştirir.  
  
2.  İkinci canlandırır <xref:System.Windows.Media.Matrix> 1.0 saniye adresindeki. Düğme artık eğri veya uzatılmış düğme başka bir konuma taşır.  
  
3.  Animasyonun süresiz olarak tekrarlar.  
  
> [!NOTE]
>  Anahtarı türetin çerçeveler <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> nesnesi oluşturma değerler arasında ani atlar, diğer bir deyişle, animasyonun hareketi düzensiz olur.  
  
 [!code-xaml[keyframes_snip#MatrixAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/MatrixAnimationUsingKeyFramesExample.xaml#matrixanimationusingkeyframeswholepage)]  
  
 Tam bir örnek için bkz: [ana kare animasyon örneği](http://go.microsoft.com/fwlink/?LinkID=160012).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.MatrixTransform.Matrix%2A>  
 <xref:System.Windows.Media.MatrixTransform>  
 [Anahtar çerçeve animasyonları genel bakış](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Anahtar çerçeve nasıl yapılır konuları](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
