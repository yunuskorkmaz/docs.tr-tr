---
title: 'Nasıl yapılır: Anahtar Çerçeveleri Kullanarak 3B Döndürme animasyonu (QuaternionAnimationUsingKeyFrames)'
ms.date: 03/30/2017
helpviewer_keywords:
- 3D translations [WPF], animating [WPF], with key frames (QuaternionAnimationUsingKeyFrames)
- key frames [WPF], QuaternionAnimationUsingKeyFrames
- animation [WPF], 3D translations [WPF], with key frames (QuaternionAnimationUsingKeyFrames)
ms.assetid: 09e5707b-7523-4a08-9aa7-bb13cbedccdf
ms.openlocfilehash: 5273183aaa49a743cc401dec0b4b16bae09e3129
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112303"
---
# <a name="how-to-animate-a-3d-rotation-using-key-frames-quaternionanimationusingkeyframes"></a><span data-ttu-id="58e3d-102">Nasıl yapılır: Anahtar Çerçeveleri Kullanarak 3B Döndürme animasyonu (QuaternionAnimationUsingKeyFrames)</span><span class="sxs-lookup"><span data-stu-id="58e3d-102">How to: Animate a 3D Rotation Using Key Frames (QuaternionAnimationUsingKeyFrames)</span></span>
<span data-ttu-id="58e3d-103">Aşağıdaki örnekte, <xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames> 3B nesnedöndürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="58e3d-103">In the following example, <xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames> is used to make a 3D object rotate.</span></span> <span data-ttu-id="58e3d-104">Bu animasyon aşağıdaki anahtar kareleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="58e3d-104">This animation uses the following key frames:</span></span>  
  
1. <span data-ttu-id="58e3d-105"><xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame>değerler arasında düzgün, doğrusal enterpolasyon oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="58e3d-105"><xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame> is used to create a smooth, linear interpolation between values.</span></span>  
  
2. <span data-ttu-id="58e3d-106"><xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame>değerler arasında ani "atlar" oluşturmak için kullanılır (enterpolasyon yok).</span><span class="sxs-lookup"><span data-stu-id="58e3d-106"><xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame> is used to create sudden "jumps" between values (no interpolation).</span></span>  
  
3. <span data-ttu-id="58e3d-107"><xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame><xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> özelliğine bağlı olarak değerler arasında değişken bir geçiş oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="58e3d-107"><xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame> is used to create a variable transition between values depending on the <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="58e3d-108">Aşağıdaki örnekte, animasyonun bu bölümü yavaş başlar, ancak zaman diliminin sonuna doğru katlanarak hızlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="58e3d-108">In the example below, this part of the animation starts off slow but toward the end of the time segment, speeds up exponentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58e3d-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="58e3d-109">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationUsingKeyFramesExample.xaml#quaternionanimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="58e3d-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="58e3d-110">See also</span></span>

- [<span data-ttu-id="58e3d-111">Storyboards kullanarak bir 3B Rotasyon animasyon</span><span class="sxs-lookup"><span data-stu-id="58e3d-111">Animate a 3D Rotation Using Storyboards</span></span>](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [<span data-ttu-id="58e3d-112">Rotation3DAnimation kullanarak 3B Döndürme animasyonu</span><span class="sxs-lookup"><span data-stu-id="58e3d-112">Animate a 3D Rotation Using Rotation3DAnimation</span></span>](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [<span data-ttu-id="58e3d-113">Quaternion kullanarak 3B Döndürme animasyon</span><span class="sxs-lookup"><span data-stu-id="58e3d-113">Animate a 3D Rotation Using Quaternions</span></span>](how-to-animate-a-3-d-rotation-using-quaternions.md)
- [<span data-ttu-id="58e3d-114">Anahtar Çerçeveleri Kullanarak 3B Döndürme (Döndürme3DAnimationUsingKeyFrames)</span><span class="sxs-lookup"><span data-stu-id="58e3d-114">Animate a 3D Rotation Using Key Frames (Rotation3DAnimationUsingKeyFrames)</span></span>](how-to-animate-a-3-d-rotation-using-key-frames.md)
- [<span data-ttu-id="58e3d-115">3D Grafiklere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="58e3d-115">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="58e3d-116">Anahtar-Çerçeve Animasyonlara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="58e3d-116">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
