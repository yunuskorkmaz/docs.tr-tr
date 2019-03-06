---
title: 'Nasıl yapılır: Anahtar çerçeveler kullanarak 3B döndürmeye animasyon ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], 3-D translations [WPF], with key frames (Rotation3DAnimation)
- key frames [WPF], Rotation3DAnimation
- 3-D translations [WPF], animating [WPF], with key frames (Rotation3DAnimation)
ms.assetid: 6f671b95-7f30-4836-9a4f-aeb7dc30121f
ms.openlocfilehash: 90e982838cb5d5b4488185c041e946c15d1e61e8
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57369142"
---
# <a name="how-to-animate-a-3-d-rotation-using-key-frames"></a>Nasıl yapılır: Anahtar çerçeveler kullanarak 3B döndürmeye animasyon ekleme
Aşağıdaki örnekte, <xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames> bir "sallanmasına içinde" kaynaklanan dönme ekseni canlandırır olurken bir 3B nesneyi döndürmek için kullanılır. Aşağıdaki anahtar çerçeve animasyon kullanır:  
  
1.  <xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame> değerler arasında sorunsuz, doğrusal bir ilişkilendirme oluşturmak için kullanılır.  
  
2.  <xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame> değer (ilişkilendirme yok) arasındaki ani "atlar" oluşturmak için kullanılır.  
  
3.  <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame> bağlı olarak değerler arasında değişken bir geçiş oluşturmak için kullanılan <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> özelliği. Aşağıdaki örnekte, bu bölümü animasyonun başlar yavaş ama zaman diliminin sonuna doğru katlanarak hızlandırır.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[Animation3DGallery_snip#Rotation3DAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotation3DAnimationUsingKeyFramesExample.xaml#rotation3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [3B Grafiklere Genel Bakış](3-d-graphics-overview.md)
- [Anahtar-Çerçeve Animasyonlara Genel Bakış](key-frame-animations-overview.md)
- [Görsel Taslaklar Kullanarak 3B Döndürmeye Animasyon Ekleme](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [Rotation3DAnimation Kullanarak 3B Döndürmeye Animasyon Ekleme](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [Dördeyler Kullanarak 3B Döndürmeye Animasyon Ekleme](how-to-animate-a-3-d-rotation-using-quaternions.md)
- [Anahtar Çerçeveler Kullanarak 3B Döndürme Hareketlendirme (QuaternionAnimationUsingKeyFrames)](animate-a-3-d-rotation-quaternionanimationusingkeyframes.md)
