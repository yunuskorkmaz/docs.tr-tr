---
title: 'Nasıl yapılır: Anahtar Çerçeveler Kullanarak 3B Döndürme Hareketlendirme (QuaternionAnimationUsingKeyFrames)'
ms.date: 03/30/2017
helpviewer_keywords:
- 3-D translations [WPF], animating [WPF], with key frames (QuaternionAnimationUsingKeyFrames)
- key frames [WPF], QuaternionAnimationUsingKeyFrames
- animation [WPF], 3-D translations [WPF], with key frames (QuaternionAnimationUsingKeyFrames)
ms.assetid: 09e5707b-7523-4a08-9aa7-bb13cbedccdf
ms.openlocfilehash: b524e9a37f778243cdf25255461f7f6607051264
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354277"
---
# <a name="how-to-animate-a-3-d-rotation-using-key-frames-quaternionanimationusingkeyframes"></a>Nasıl yapılır: Anahtar Çerçeveler Kullanarak 3B Döndürme Hareketlendirme (QuaternionAnimationUsingKeyFrames)
Aşağıdaki örnekte, <xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames> 3B nesneyi döndürmek için kullanılır. Aşağıdaki anahtar çerçeve animasyon kullanır:  
  
1.  <xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame> değerler arasında sorunsuz, doğrusal bir ilişkilendirme oluşturmak için kullanılır.  
  
2.  <xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame> değer (ilişkilendirme yok) arasındaki ani "atlar" oluşturmak için kullanılır.  
  
3.  <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame> bağlı olarak değerler arasında değişken bir geçiş oluşturmak için kullanılan <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> özelliği. Aşağıdaki örnekte, bu bölümü animasyonun başlar yavaş ama zaman diliminin sonuna doğru katlanarak hızlandırır.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationUsingKeyFramesExample.xaml#quaternionanimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Görsel Taslaklar Kullanarak 3B Döndürmeye Animasyon Ekleme](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [Rotation3DAnimation Kullanarak 3B Döndürmeye Animasyon Ekleme](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [Dördeyler Kullanarak 3B Döndürmeye Animasyon Ekleme](how-to-animate-a-3-d-rotation-using-quaternions.md)
- [Anahtar Çerçeveler Kullanarak 3B Döndürmeye Animasyon Ekleme (Rotation3DAnimationUsingKeyFrames)](how-to-animate-a-3-d-rotation-using-key-frames.md)
- [3B Grafiklere Genel Bakış](3-d-graphics-overview.md)
- [Anahtar-Çerçeve Animasyonlara Genel Bakış](key-frame-animations-overview.md)
