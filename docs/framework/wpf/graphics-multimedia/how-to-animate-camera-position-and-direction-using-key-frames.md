---
title: "Nasıl yapılır: Anahtar Çerçeveler Kullanarak Kamera Konumuna ve Yönüne Animasyon Ekleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], camera direction with key frames
- key frames [WPF], animating camera direction
- animation [WPF], camera position with key frames
- camera position [WPF], animating with key frames
- key frames [WPF], animating camera position
- camera direction [WPF], animating with key frames
ms.assetid: 5753024e-0057-454d-947f-43ea686879c7
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dbac99770b5cbb7dacb0468e1a892956fda6b79c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-camera-position-and-direction-using-key-frames"></a>Nasıl yapılır: Anahtar Çerçeveler Kullanarak Kamera Konumuna ve Yönüne Animasyon Ekleme
Aşağıdaki örnekte, <xref:System.Windows.Media.Animation.Point3DAnimationUsingKeyFrames> konumunu hareketli hale getirmeyi için kullanılan bir <xref:System.Windows.Media.Media3D.PerspectiveCamera> 3B Sahne içinde. Ayrıca, <xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames> Kamera 3B Sahne işaret yönü animasyon için kullanılır. Bu animasyonların ikisi de animasyon efektleri dizisi oluşturan birçok anahtar çerçeve kullanın:  
  
1.  <xref:System.Windows.Media.Animation.LinearPoint3DKeyFrame>ve <xref:System.Windows.Media.Animation.LinearVector3DKeyFrame> değerler arasında düzgün, doğrusal ilişkilendirme oluşturmak için kullanılır.  
  
2.  <xref:System.Windows.Media.Animation.DiscretePoint3DKeyFrame>ve <xref:System.Windows.Media.Animation.DiscreteVector3DKeyFrame> değerleri (ilişkilendirme yok) arasında ani "atlar" oluşturmak için kullanılır.  
  
3.  <xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame>ve <xref:System.Windows.Media.Animation.SplineVector3DKeyFrame> bağlı olarak değerler arasında değişken geçiş oluşturmak için kullanılan <xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame.KeySpline%2A> özelliği. Aşağıdaki örnekte, animasyon yavaş ancak zaman diliminin sonuna doğru başlatır ve katlanarak hızlanır.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[Animation3DGallery_snip#PointVector3DAnimationUsingKeyFramesExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationUsingKeyFramesExample.xaml#pointvector3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kamera konumunu ve 3B Sahne yönde animasyon ekleme](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-camera-position-and-direction-in-a-3d-scene.md)  
 [3B Grafiklere Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
