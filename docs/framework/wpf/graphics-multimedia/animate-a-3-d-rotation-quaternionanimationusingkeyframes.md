---
title: "Nasıl yapılır: Anahtar Çerçeveler Kullanarak 3B Döndürmeye Animasyon Ekleme (QuaternionAnimationUsingKeyFrames)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- 3-D translations [WPF], animating [WPF], with key frames (QuaternionAnimationUsingKeyFrames)
- key frames [WPF], QuaternionAnimationUsingKeyFrames
- animation [WPF], 3-D translations [WPF], with key frames (QuaternionAnimationUsingKeyFrames)
ms.assetid: 09e5707b-7523-4a08-9aa7-bb13cbedccdf
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 61968c13d395187d1190c7a2eaaa2bfe3f6072e4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-a-3-d-rotation-using-key-frames-quaternionanimationusingkeyframes"></a>Nasıl yapılır: Anahtar Çerçeveler Kullanarak 3B Döndürmeye Animasyon Ekleme (QuaternionAnimationUsingKeyFrames)
Aşağıdaki örnekte, <xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames> 3B nesneyi döndürmek için kullanılır. Bu animasyon aşağıdaki anahtar çerçevelerini kullanır:  
  
1.  <xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame>değerler arasında düzgün, doğrusal ilişkilendirme oluşturmak için kullanılır.  
  
2.  <xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame>değerler (ilişkilendirme yok) arasında ani "atlar" oluşturmak için kullanılır.  
  
3.  <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame>bağlı olarak değerler arasında değişken geçiş oluşturmak için kullanılan <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> özelliği. Aşağıdaki örnekte, bu bölümü animasyonun yavaş ancak zaman diliminin sonuna doğru başlatır ve katlanarak hızlanır.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationUsingKeyFramesExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationUsingKeyFramesExample.xaml#quaternionanimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Film şeritleri kullanarak 3B Döndürme animasyon ekleme](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-storyboards.md)  
 [Rotation3DAnimation kullanarak 3B Döndürme animasyon ekleme](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-rotation3danimation.md)  
 [Dördey kullanarak 3B Döndürme animasyon ekleme](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-quaternions.md)  
 [Animasyon ana kare (Rotation3DAnimationUsingKeyFrames) kullanarak 3B Döndürme](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-key-frames.md)  
 [3B Grafiklere Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [Anahtar çerçeve animasyonları genel bakış](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)
