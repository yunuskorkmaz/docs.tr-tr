---
title: 'Nasıl yapılır: Anahtar Çerçeveler Kullanarak Boyut Değişikliklerine Animasyon Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- key frames [WPF], animating size changes with
- animation [WPF], size changes with key frames
- size changes [WPF], animating with key frames
ms.assetid: 86bd2950-d4c9-4ec4-aa8d-7dc3ccadded4
ms.openlocfilehash: 0c2828215527a285943a79920de51fa42fe7a8a7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-animate-size-changes-by-using-key-frames"></a>Nasıl yapılır: Anahtar Çerçeveler Kullanarak Boyut Değişikliklerine Animasyon Ekleme
Bu örnekte, anahtar çerçeveler kullanarak boyutu değişiklikleri animasyon gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames> animasyon sınıfı <xref:System.Windows.Media.ArcSegment.Size%2A> özelliği bir <xref:System.Windows.Media.ArcSegment>. Bu animasyon üç ana kare aşağıdaki şekilde kullanır:  
  
1.  Animasyonun ilk yarım saniye boyunca bir örneğini kullanan <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> yavaş yavaş yay boyutunu artırmak için sınıf. Gibi doğrusal anahtar çerçeveler <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> değerler arasında yumuşak bir doğrusal geçiş oluşturur.  
  
2.  Sonraki sonunda yarım ikinci bir örneğini kullanır <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> aniden yay boyutunu artırmak için sınıf. Gibi ayrık anahtar çerçeveler <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> değerler arasında ani atlar oluşturur, bu boyut değişiklikleri aniden ortaya çıkar ve zarif değildir.  
  
3.  Son iki saniye içinde bir örneğini kullanan <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> yay boyutunu artırmak için sınıf. Gibi Eğri anahtar çerçeveler <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> değerlerine göre değerler arasında değişken geçiş oluşturmak <xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A> özelliği. Bu örnekte, yay boyutunu yavaş ilk başta artırır ve zaman diliminin sonuna doğru katlanarak artırır.  
  
 [!code-xaml[keyframes_snip#SizeAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/SizeAnimationUsingKeyFramesExample.xaml#sizeanimationusingkeyframeswholepage)]  
  
 Tam bir örnek için bkz: [ana kare animasyon örneği](http://go.microsoft.com/fwlink/?LinkID=160012).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>  
 <xref:System.Windows.Media.ArcSegment.Size%2A>  
 <xref:System.Windows.Media.ArcSegment>  
 <xref:System.Windows.Media.Animation.LinearSizeKeyFrame>  
 <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>  
 <xref:System.Windows.Media.Animation.SplineSizeKeyFrame>  
 [Anahtar-Çerçeve Animasyonlara Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Anahtar Çerçeve ile İlgili Nasıl Yapılır Konuları](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
