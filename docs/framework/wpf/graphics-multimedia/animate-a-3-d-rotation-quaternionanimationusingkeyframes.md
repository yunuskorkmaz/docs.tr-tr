---
title: 'Nasıl yapılır: Anahtar Çerçeveleri Kullanarak 3B Döndürme animasyonu (QuaternionAnimationUsingKeyFrames)'
ms.date: 03/30/2017
helpviewer_keywords:
- 3D translations [WPF], animating [WPF], with key frames (QuaternionAnimationUsingKeyFrames)
- key frames [WPF], QuaternionAnimationUsingKeyFrames
- animation [WPF], 3D translations [WPF], with key frames (QuaternionAnimationUsingKeyFrames)
ms.assetid: 09e5707b-7523-4a08-9aa7-bb13cbedccdf
ms.openlocfilehash: 5273183aaa49a743cc401dec0b4b16bae09e3129
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112303"
---
# <a name="how-to-animate-a-3d-rotation-using-key-frames-quaternionanimationusingkeyframes"></a>Nasıl yapılır: Anahtar Çerçeveleri Kullanarak 3B Döndürme animasyonu (QuaternionAnimationUsingKeyFrames)
Aşağıdaki örnekte, <xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames> 3B nesnedöndürmek için kullanılır. Bu animasyon aşağıdaki anahtar kareleri kullanır:  
  
1. <xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame>değerler arasında düzgün, doğrusal enterpolasyon oluşturmak için kullanılır.  
  
2. <xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame>değerler arasında ani "atlar" oluşturmak için kullanılır (enterpolasyon yok).  
  
3. <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame><xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> özelliğine bağlı olarak değerler arasında değişken bir geçiş oluşturmak için kullanılır. Aşağıdaki örnekte, animasyonun bu bölümü yavaş başlar, ancak zaman diliminin sonuna doğru katlanarak hızlanmıştır.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationUsingKeyFramesExample.xaml#quaternionanimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Storyboards kullanarak bir 3B Rotasyon animasyon](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [Rotation3DAnimation kullanarak 3B Döndürme animasyonu](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [Quaternion kullanarak 3B Döndürme animasyon](how-to-animate-a-3-d-rotation-using-quaternions.md)
- [Anahtar Çerçeveleri Kullanarak 3B Döndürme (Döndürme3DAnimationUsingKeyFrames)](how-to-animate-a-3-d-rotation-using-key-frames.md)
- [3D Grafiklere Genel Bakış](3-d-graphics-overview.md)
- [Anahtar-Çerçeve Animasyonlara Genel Bakış](key-frame-animations-overview.md)
