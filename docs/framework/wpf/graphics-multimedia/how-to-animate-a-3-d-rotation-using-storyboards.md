---
title: 'Nasıl yapılır: Görsel Taslaklar Kullanarak 3B Döndürmeye Animasyon Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- Storyboards [WPF]
- 3-D translations [WPF], animating [WPF], with Storyboards
- animation [WPF], 3-D translations [WPF], with Storyboards
ms.assetid: 1020e44e-e21e-49a8-be53-53cbc1910e83
ms.openlocfilehash: 03b01205f1a31426a01b09533b350682c384df4b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62024761"
---
# <a name="how-to-animate-a-3-d-rotation-using-storyboards"></a>Nasıl yapılır: Görsel Taslaklar Kullanarak 3B Döndürmeye Animasyon Ekleme
Aşağıdaki örnek, "sallarken" bir 3B nesneyi gösterilmiştir <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> ve <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> özelliklerini bir <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> nesne. Bu <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> nesnesi, 3B nesnenin döndürme dönüşümü belirler ve bu nedenle kendi özelliklerine animasyon ekleme arzusu döndürme efekti oluşturur. Film şeridi içinde <xref:System.Windows.Media.Animation.DoubleAnimation> animasyon uygulamak için kullanılan <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> özelliğinde <xref:System.Windows.Media.Animation.Vector3DAnimation> animasyon uygulamak için kullanılan <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> özelliği.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[Animation3DGallery_snip#Rotate3DUsingAxisAngleRotation3DExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotat3DUsingAxisAngleRotation3DExample.xaml#rotate3dusingaxisanglerotation3dexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Rotation3DAnimation Kullanarak 3B Döndürmeye Animasyon Ekleme](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [Anahtar Çerçeveler Kullanarak 3B Döndürmeye Animasyon Ekleme (Rotation3DAnimationUsingKeyFrames)](how-to-animate-a-3-d-rotation-using-key-frames.md)
- [3B Grafiklere Genel Bakış](3-d-graphics-overview.md)
- [Görsel Taslaklara Genel Bakış](storyboards-overview.md)
