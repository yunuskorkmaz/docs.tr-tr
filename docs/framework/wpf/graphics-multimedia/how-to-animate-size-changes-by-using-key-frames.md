---
title: 'Nasıl yapılır: Anahtar Çerçeveler Kullanarak Boyut Değişikliklerine Animasyon Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- key frames [WPF], animating size changes with
- animation [WPF], size changes with key frames
- size changes [WPF], animating with key frames
ms.assetid: 86bd2950-d4c9-4ec4-aa8d-7dc3ccadded4
ms.openlocfilehash: 42cecfc9df4304be4033ea39edc0517016de4a92
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344649"
---
# <a name="how-to-animate-size-changes-by-using-key-frames"></a>Nasıl yapılır: Anahtar Çerçeveler Kullanarak Boyut Değişikliklerine Animasyon Ekleme
Bu örnek, anahtar kareler kullanarak boyut değişikliklerini nasıl canlandıracaklarını gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames> bir <xref:System.Windows.Media.ArcSegment>. özelliğini <xref:System.Windows.Media.ArcSegment.Size%2A> canlandırmak için sınıfı kullanır. Bu animasyon aşağıdaki şekilde üç anahtar kare kullanır:  
  
1. Animasyonun ilk yarısında, yavaş yavaş yay <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> boyutunu artırmak için sınıfın bir örnek kullanır. Değerler arasında düzgün <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> doğrusal geçiş oluşturma gibi doğrusal anahtar çerçeveler.  
  
2. Sonraki yarım saniyenin sonunda, aniden yay <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> boyutunu artırmak için sınıfın bir örnek kullanır. Değerler arasında ani <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> sıçramalar oluşturmak gibi ayrık anahtar çerçeveleri, yani boyut değişiklikleri aniden oluşur ve ince değildir.  
  
3. Son iki saniye içinde, yay <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> boyutunu artırmak için sınıfın bir örneğini kullanır. Özellik değerlerine <xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A> göre <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> değerler arasında değişken bir geçiş oluşturmak gibi spline anahtar çerçeveleri. Bu örnekte, yay boyutu ilk başta yavaş yavaş artar ve daha sonra zaman diliminin sonuna doğru katlanarak artar.  
  
 [!code-xaml[keyframes_snip#SizeAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/SizeAnimationUsingKeyFramesExample.xaml#sizeanimationusingkeyframeswholepage)]  
  
 Tam örnek için [Anahtar Çerçeve Animasyon Örneği'ne](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>
- <xref:System.Windows.Media.ArcSegment.Size%2A>
- <xref:System.Windows.Media.ArcSegment>
- <xref:System.Windows.Media.Animation.LinearSizeKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>
- <xref:System.Windows.Media.Animation.SplineSizeKeyFrame>
- [Anahtar-Çerçeve Animasyonlara Genel Bakış](key-frame-animations-overview.md)
- [Anahtar Çerçeve ile İlgili Nasıl Yapılır Konuları](key-frame-animation-how-to-topics.md)
