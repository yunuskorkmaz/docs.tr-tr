---
title: 'Nasıl yapilir: Anahtar Çerçeveleri Kullanarak 3B Döndürme animasyonu'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], 3D translations [WPF], with key frames (Rotation3DAnimation)
- key frames [WPF], Rotation3DAnimation
- 3D translations [WPF], animating [WPF], with key frames (Rotation3DAnimation)
ms.assetid: 6f671b95-7f30-4836-9a4f-aeb7dc30121f
ms.openlocfilehash: 2b9059df079125c34c70237c0f600751020044c6
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112316"
---
# <a name="how-to-animate-a-3d-rotation-using-key-frames"></a>Nasıl yapilir: Anahtar Çerçeveleri Kullanarak 3B Döndürme animasyonu
Aşağıdaki örnekte, <xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames> bir 3B nesnenin döndürmesini sağlamak için kullanılırken, dönüş ekseni bir "titreme" ile sonuçlanır. Bu animasyon aşağıdaki anahtar kareleri kullanır:  
  
1. <xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame>değerler arasında düzgün, doğrusal enterpolasyon oluşturmak için kullanılır.  
  
2. <xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame>değerler arasında ani "atlar" oluşturmak için kullanılır (enterpolasyon yok).  
  
3. <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame><xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> özelliğine bağlı olarak değerler arasında değişken bir geçiş oluşturmak için kullanılır. Aşağıdaki örnekte, animasyonun bu bölümü yavaş başlar, ancak zaman diliminin sonuna doğru katlanarak hızlanmıştır.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[Animation3DGallery_snip#Rotation3DAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotation3DAnimationUsingKeyFramesExample.xaml#rotation3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [3D Grafiklere Genel Bakış](3-d-graphics-overview.md)
- [Anahtar-Çerçeve Animasyonlara Genel Bakış](key-frame-animations-overview.md)
- [Storyboards kullanarak bir 3B Rotasyon animasyon](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [Rotation3DAnimation kullanarak 3B Döndürme animasyonu](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [Quaternion kullanarak 3B Döndürme animasyon](how-to-animate-a-3-d-rotation-using-quaternions.md)
- [Anahtar Çerçeveleri Kullanarak 3B Döndürmeanimasyon (QuaternionAnimationUsingKeyFrames)](animate-a-3-d-rotation-quaternionanimationusingkeyframes.md)
