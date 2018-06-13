---
title: 'Nasıl yapılır: Görsel Taslaklar Kullanarak 3B Döndürmeye Animasyon Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- Storyboards [WPF]
- 3-D translations [WPF], animating [WPF], with Storyboards
- animation [WPF], 3-D translations [WPF], with Storyboards
ms.assetid: 1020e44e-e21e-49a8-be53-53cbc1910e83
ms.openlocfilehash: a6cc8774c14d4b393b0d04822216c894e486ba66
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33556711"
---
# <a name="how-to-animate-a-3-d-rotation-using-storyboards"></a>Nasıl yapılır: Görsel Taslaklar Kullanarak 3B Döndürmeye Animasyon Ekleme
Aşağıdaki örnekte, "sallarken" döndürün 3B bir nesneyi gösterilmektedir <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> ve <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> özelliklerini bir <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> nesnesi. Bu <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> nesnesi 3B nesnenin döndürme dönüştürme belirtir ve bu nedenle özelliklerini animasyon desire döndürme efekti oluşturur. Film şeridi içinde <xref:System.Windows.Media.Animation.DoubleAnimation> animasyon uygulamak için kullanılan <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> sırasında özelliği <xref:System.Windows.Media.Animation.Vector3DAnimation> animasyon uygulamak için kullanılan <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> özelliği.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[Animation3DGallery_snip#Rotate3DUsingAxisAngleRotation3DExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotat3DUsingAxisAngleRotation3DExample.xaml#rotate3dusingaxisanglerotation3dexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Rotation3DAnimation Kullanarak 3B Döndürmeye Animasyon Ekleme](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-rotation3danimation.md)  
 [Anahtar Çerçeveler Kullanarak 3B Döndürmeye Animasyon Ekleme (Rotation3DAnimationUsingKeyFrames)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-key-frames.md)  
 [3B Grafiklere Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [Görsel Taslaklara Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
