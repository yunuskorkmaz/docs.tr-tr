---
title: "Nasıl yapilir: Kuaterniyonlar Kullanarak 3D Rotasyon'u canlandırma"
ms.date: 03/30/2017
helpviewer_keywords:
- quaternions [WPF]
- animation [WPF], 3D translations [WPF], with quaternions
- 3D translations [WPF], animating [WPF], with quaternions
ms.assetid: adca9cb1-066b-4de8-abbb-6b4007579ee7
ms.openlocfilehash: 0d229b0a714cc53459943fae751ab4d4f787d7d8
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112251"
---
# <a name="how-to-animate-a-3d-rotation-using-quaternions"></a>Nasıl yapilir: Kuaterniyonlar Kullanarak 3D Rotasyon'u canlandırma
Bu örnek, kuaterniyonlar kullanarak bir 3B nesnenin döndürme nasıl animasyon gösterir.  
  
 Aşağıdaki kod, <xref:System.Windows.Media.Media3D.QuaternionRotation3D> bir <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> <xref:System.Windows.Media.Media3D.RotateTransform3D>. özelliği için kullanılan bir değeri gösterir  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline1)]  
  
 Bu, <xref:System.Windows.Media.Media3D.QuaternionRotation3D> aşağıdaki <xref:System.Windows.Media.Animation.QuaternionAnimation> kodu <xref:System.Windows.Media.Animation.Storyboard> kullanarak bir içinde animasyonludur.  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline2)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, tüm örneği gösterir.  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Animasyona Genel bakış](animation-overview.md)
- [3B Sahne Oluşturma](how-to-create-a-3-d-scene.md)
- [3D Grafiklere Genel Bakış](3-d-graphics-overview.md)
- [Dönüşümlere Genel Bakış](transforms-overview.md)
- [Storyboards kullanarak bir 3B Rotasyon animasyon](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [Rotation3DAnimation kullanarak 3B Döndürme animasyonu](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
