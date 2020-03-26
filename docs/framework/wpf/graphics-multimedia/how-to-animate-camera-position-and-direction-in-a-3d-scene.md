---
title: 'Nasıl yapılır: 3B Görünümde Kamera Konumuna ve Yönüne Animasyon Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], camera position in 3D scenes
- camera direction [WPF], animating in 3D scenes
- 3D scenes [WPF], animating camera position
- 3D scenes [WPF], animating camera direction
- camera position [WPF], animating in 3D scenes
- animation [WPF], camera direction in 3D scenes
ms.assetid: 480224b7-a5e5-4165-ba7f-ef760ddff94a
ms.openlocfilehash: 5ce94e154cd5aa29b59260f893ec2b63a08db0fc
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112224"
---
# <a name="how-to-animate-camera-position-and-direction-in-a-3d-scene"></a>Nasıl yapılır: 3B Görünümde Kamera Konumuna ve Yönüne Animasyon Ekleme
Aşağıdaki örnek, bir kameranın konumunu nasıl canlandıracak larını ve 3B bir sahnede işaret ediyor olduğu yönü nasıl canlandıracaklarını gösterir. <xref:System.Windows.Media.Animation.Point3DAnimation> Bu kullanarak yapılır <xref:System.Windows.Media.Animation.Vector3DAnimation> ve sırasıyla <xref:System.Windows.Media.Media3D.ProjectionCamera.Position%2A> ve <xref:System.Windows.Media.Media3D.ProjectionCamera.LookDirection%2A> özellikleri <xref:System.Windows.Media.Media3D.PerspectiveCamera>animasyon. Bir olaya yanıt olarak görüntüleyenin bir sahnenin görünümünü değiştirmek için böyle bir animasyon kullanabilirsiniz.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[Animation3DGallery_snip#PointVector3DAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationExample.xaml#pointvector3danimationexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.Animation.Vector3DAnimation>
- <xref:System.Windows.Media.Animation.Point3DAnimation>
- [Anahtar Çerçeveler Kullanarak Kamera Konumuna ve Yönüne Animasyon Ekleme](how-to-animate-camera-position-and-direction-using-key-frames.md)
- [3D Grafiklere Genel Bakış](3-d-graphics-overview.md)
