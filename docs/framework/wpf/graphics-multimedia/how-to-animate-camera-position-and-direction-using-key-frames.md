---
title: 'Nasıl yapılır: Anahtar Çerçeveler Kullanarak Kamera Konumuna ve Yönüne Animasyon Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], camera direction with key frames
- key frames [WPF], animating camera direction
- animation [WPF], camera position with key frames
- camera position [WPF], animating with key frames
- key frames [WPF], animating camera position
- camera direction [WPF], animating with key frames
ms.assetid: 5753024e-0057-454d-947f-43ea686879c7
ms.openlocfilehash: 28471f9b42140a6c75b043d33939503528b63194
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112173"
---
# <a name="how-to-animate-camera-position-and-direction-using-key-frames"></a>Nasıl yapılır: Anahtar Çerçeveler Kullanarak Kamera Konumuna ve Yönüne Animasyon Ekleme
Aşağıdaki örnekte, <xref:System.Windows.Media.Animation.Point3DAnimationUsingKeyFrames> bir 3B sahnedeki konumu <xref:System.Windows.Media.Media3D.PerspectiveCamera> canlandırmak için kullanılır. Buna ek <xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames> olarak, kameranın 3B sahnede işaret olduğu yönü canlandırmak için kullanılır. Bu animasyonların her ikisi de bir dizi animasyon efekti oluşturan birkaç anahtar kare kullanır:  
  
1. <xref:System.Windows.Media.Animation.LinearPoint3DKeyFrame><xref:System.Windows.Media.Animation.LinearVector3DKeyFrame> ve değerler arasında düzgün, doğrusal enterpolasyon oluşturmak için kullanılır.  
  
2. <xref:System.Windows.Media.Animation.DiscretePoint3DKeyFrame><xref:System.Windows.Media.Animation.DiscreteVector3DKeyFrame> ve değerler arasında ani "atlar" oluşturmak için kullanılır (enterpolasyon yok).  
  
3. <xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame><xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame.KeySpline%2A> ve <xref:System.Windows.Media.Animation.SplineVector3DKeyFrame> özelliğe bağlı olarak değerler arasında değişken bir geçiş oluşturmak için kullanılır. Aşağıdaki örnekte, animasyon yavaş başlar, ancak zaman diliminin sonuna doğru, katlanarak hızlar.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[Animation3DGallery_snip#PointVector3DAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationUsingKeyFramesExample.xaml#pointvector3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [3B Görünümde Kamera Konumuna ve Yönüne Animasyon Ekleme](how-to-animate-camera-position-and-direction-in-a-3d-scene.md)
- [3D Grafiklere Genel Bakış](3-d-graphics-overview.md)
