---
title: 'Nasıl yapilir: Storyboards kullanarak bir 3D Rotasyon Animasyon'
ms.date: 03/30/2017
helpviewer_keywords:
- Storyboards [WPF]
- 3D translations [WPF], animating [WPF], with Storyboards
- animation [WPF], 3D translations [WPF], with Storyboards
ms.assetid: 1020e44e-e21e-49a8-be53-53cbc1910e83
ms.openlocfilehash: 088f1a33cfc73a706ffed55ffff6494adaf8fca4
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112225"
---
# <a name="how-to-animate-a-3d-rotation-using-storyboards"></a>Nasıl yapilir: Storyboards kullanarak bir 3D Rotasyon Animasyon
Aşağıdaki örnek, bir <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> nesnenin özelliklerini ve özelliklerini canlandırarak "sallanırken" 3B nesnenin nasıl döndürüldüğünü gösterir. Bu <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> nesne, 3B nesnenin döndürme dönüşümünü belirtir ve böylece özelliklerini canlandırarak istek döndürme efekti oluşturur. Storyboard içinde, <xref:System.Windows.Media.Animation.DoubleAnimation> <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> özelliği canlandırmak için kullanılırken <xref:System.Windows.Media.Animation.Vector3DAnimation> özelliği canlandırmak için kullanılır.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[Animation3DGallery_snip#Rotate3DUsingAxisAngleRotation3DExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotat3DUsingAxisAngleRotation3DExample.xaml#rotate3dusingaxisanglerotation3dexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Rotation3DAnimation kullanarak 3B Döndürme animasyonu](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [Anahtar Çerçeveleri Kullanarak 3B Döndürme (Döndürme3DAnimationUsingKeyFrames)](how-to-animate-a-3-d-rotation-using-key-frames.md)
- [3D Grafiklere Genel Bakış](3-d-graphics-overview.md)
- [Görsel Taslaklara Genel Bakış](storyboards-overview.md)
