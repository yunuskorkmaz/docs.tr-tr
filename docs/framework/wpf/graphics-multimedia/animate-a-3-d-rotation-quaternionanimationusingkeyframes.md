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
# <a name="how-to-animate-a-3-d-rotation-using-key-frames-quaternionanimationusingkeyframes"></a><span data-ttu-id="1d98c-102">Nasıl yapılır: Anahtar Çerçeveler Kullanarak 3B Döndürmeye Animasyon Ekleme (QuaternionAnimationUsingKeyFrames)</span><span class="sxs-lookup"><span data-stu-id="1d98c-102">How to: Animate a 3-D Rotation Using Key Frames (QuaternionAnimationUsingKeyFrames)</span></span>
<span data-ttu-id="1d98c-103">Aşağıdaki örnekte, <xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames> 3B nesneyi döndürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1d98c-103">In the following example, <xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames> is used to make a 3D object rotate.</span></span> <span data-ttu-id="1d98c-104">Bu animasyon aşağıdaki anahtar çerçevelerini kullanır:</span><span class="sxs-lookup"><span data-stu-id="1d98c-104">This animation uses the following key frames:</span></span>  
  
1.  <span data-ttu-id="1d98c-105"><xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame>değerler arasında düzgün, doğrusal ilişkilendirme oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1d98c-105"><xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame> is used to create a smooth, linear interpolation between values.</span></span>  
  
2.  <span data-ttu-id="1d98c-106"><xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame>değerler (ilişkilendirme yok) arasında ani "atlar" oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1d98c-106"><xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame> is used to create sudden "jumps" between values (no interpolation).</span></span>  
  
3.  <span data-ttu-id="1d98c-107"><xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame>bağlı olarak değerler arasında değişken geçiş oluşturmak için kullanılan <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="1d98c-107"><xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame> is used to create a variable transition between values depending on the <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="1d98c-108">Aşağıdaki örnekte, bu bölümü animasyonun yavaş ancak zaman diliminin sonuna doğru başlatır ve katlanarak hızlanır.</span><span class="sxs-lookup"><span data-stu-id="1d98c-108">In the example below, this part of the animation starts off slow but toward the end of the time segment, speeds up exponentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d98c-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="1d98c-109">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationUsingKeyFramesExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationUsingKeyFramesExample.xaml#quaternionanimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="1d98c-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1d98c-110">See Also</span></span>  
 [<span data-ttu-id="1d98c-111">Film şeritleri kullanarak 3B Döndürme animasyon ekleme</span><span class="sxs-lookup"><span data-stu-id="1d98c-111">Animate a 3-D Rotation Using Storyboards</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-storyboards.md)  
 [<span data-ttu-id="1d98c-112">Rotation3DAnimation kullanarak 3B Döndürme animasyon ekleme</span><span class="sxs-lookup"><span data-stu-id="1d98c-112">Animate a 3-D Rotation Using Rotation3DAnimation</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-rotation3danimation.md)  
 [<span data-ttu-id="1d98c-113">Dördey kullanarak 3B Döndürme animasyon ekleme</span><span class="sxs-lookup"><span data-stu-id="1d98c-113">Animate a 3-D Rotation Using Quaternions</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-quaternions.md)  
 [<span data-ttu-id="1d98c-114">Animasyon ana kare (Rotation3DAnimationUsingKeyFrames) kullanarak 3B Döndürme</span><span class="sxs-lookup"><span data-stu-id="1d98c-114">Animate a 3-D Rotation Using Key Frames (Rotation3DAnimationUsingKeyFrames)</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-key-frames.md)  
 [<span data-ttu-id="1d98c-115">3B Grafiklere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="1d98c-115">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [<span data-ttu-id="1d98c-116">Anahtar çerçeve animasyonları genel bakış</span><span class="sxs-lookup"><span data-stu-id="1d98c-116">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)
