---
title: 'Nasıl yapılır: Dördeyler Kullanarak 3B Döndürmeye Animasyon Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- quaternions [WPF]
- animation [WPF], 3-D translations [WPF], with quaternions
- 3-D translations [WPF], animating [WPF], with quaternions
ms.assetid: adca9cb1-066b-4de8-abbb-6b4007579ee7
ms.openlocfilehash: 4c2a46aad1feeefe5c7c31ec192f46b8c891337f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33556945"
---
# <a name="how-to-animate-a-3-d-rotation-using-quaternions"></a>Nasıl yapılır: Dördeyler Kullanarak 3B Döndürmeye Animasyon Ekleme
Bu örnek, dördey kullanarak 3B bir nesnenin dönüşünü animasyon gösterilmektedir.  
  
 Aşağıdaki kodu gösterir bir <xref:System.Windows.Media.Media3D.QuaternionRotation3D> değeri olarak kullanılan <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> özelliği bir <xref:System.Windows.Media.Media3D.RotateTransform3D>.  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline1)]  
  
 Bu <xref:System.Windows.Media.Media3D.QuaternionRotation3D> ile Animasyonlu bir <xref:System.Windows.Media.Animation.QuaternionAnimation> içinde bir <xref:System.Windows.Media.Animation.Storyboard> aşağıdaki kodu kullanarak.  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleInline2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline2)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod tüm örneği gösterir.  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Animasyona Genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [3B Görünümü Oluşturma](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)  
 [3B Grafiklere Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [Dönüşümlere Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [Görsel Taslaklar Kullanarak 3B Döndürmeye Animasyon Ekleme](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-storyboards.md)  
 [Rotation3DAnimation Kullanarak 3B Döndürmeye Animasyon Ekleme](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
