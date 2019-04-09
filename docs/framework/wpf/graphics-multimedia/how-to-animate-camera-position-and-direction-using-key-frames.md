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
ms.openlocfilehash: 3be3fc8d82d9c3061891bd67605548c49230ef87
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59143240"
---
# <a name="how-to-animate-camera-position-and-direction-using-key-frames"></a>Nasıl yapılır: Anahtar Çerçeveler Kullanarak Kamera Konumuna ve Yönüne Animasyon Ekleme
Aşağıdaki örnekte, <xref:System.Windows.Media.Animation.Point3DAnimationUsingKeyFrames> animasyon ekleme için kullanılan bir <xref:System.Windows.Media.Media3D.PerspectiveCamera> 3B görünümde. Ayrıca, <xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames> 3B görünümde kamera işaret eden yönüne animasyon uygulamak için kullanılır. Bu animasyonları her ikisi de, animasyon efektleri bir dizi oluşturmak birkaç anahtar çerçeveleri kullanın:  
  
1.  <xref:System.Windows.Media.Animation.LinearPoint3DKeyFrame> ve <xref:System.Windows.Media.Animation.LinearVector3DKeyFrame> değerler arasında sorunsuz, doğrusal bir ilişkilendirme oluşturmak için kullanılır.  
  
2.  <xref:System.Windows.Media.Animation.DiscretePoint3DKeyFrame> ve <xref:System.Windows.Media.Animation.DiscreteVector3DKeyFrame> değerleri (ilişkilendirme yok) arasında ani "atlar" oluşturmak için kullanılır.  
  
3.  <xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame> ve <xref:System.Windows.Media.Animation.SplineVector3DKeyFrame> bağlı olarak değerler arasında değişken bir geçiş oluşturmak için kullanılan <xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame.KeySpline%2A> özelliği. Aşağıdaki örnekte, animasyon başlar yavaş ama zaman diliminin sonuna doğru katlanarak hızlandırır.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[Animation3DGallery_snip#PointVector3DAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationUsingKeyFramesExample.xaml#pointvector3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [3B Görünümde Kamera Konumuna ve Yönüne Animasyon Ekleme](how-to-animate-camera-position-and-direction-in-a-3d-scene.md)
- [3B Grafiklere Genel Bakış](3-d-graphics-overview.md)
