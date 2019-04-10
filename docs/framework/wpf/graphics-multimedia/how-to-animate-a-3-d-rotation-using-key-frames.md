---
title: 'Nasıl yapılır: Anahtar çerçeveler kullanarak 3B döndürmeye animasyon ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], 3-D translations [WPF], with key frames (Rotation3DAnimation)
- key frames [WPF], Rotation3DAnimation
- 3-D translations [WPF], animating [WPF], with key frames (Rotation3DAnimation)
ms.assetid: 6f671b95-7f30-4836-9a4f-aeb7dc30121f
ms.openlocfilehash: e72ec94f830f0f5001a77e7492aa1326a47b309d
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59297999"
---
# <a name="how-to-animate-a-3-d-rotation-using-key-frames"></a><span data-ttu-id="92528-102">Nasıl yapılır: Anahtar çerçeveler kullanarak 3B döndürmeye animasyon ekleme</span><span class="sxs-lookup"><span data-stu-id="92528-102">How to: Animate a 3-D Rotation Using Key Frames</span></span>
<span data-ttu-id="92528-103">Aşağıdaki örnekte, <xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames> bir "sallanmasına içinde" kaynaklanan dönme ekseni canlandırır olurken bir 3B nesneyi döndürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="92528-103">In the following example, <xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames> is used to make a 3D object rotate while its axis of rotation animates resulting in a "wobble".</span></span> <span data-ttu-id="92528-104">Aşağıdaki anahtar çerçeve animasyon kullanır:</span><span class="sxs-lookup"><span data-stu-id="92528-104">This animation uses the following key frames:</span></span>  
  
1. <xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame> <span data-ttu-id="92528-105">değerler arasında sorunsuz, doğrusal bir ilişkilendirme oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="92528-105">is used to create a smooth, linear interpolation between values.</span></span>  
  
2. <xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame> <span data-ttu-id="92528-106">değer (ilişkilendirme yok) arasındaki ani "atlar" oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="92528-106">is used to create sudden "jumps" between values (no interpolation).</span></span>  
  
3. <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame> <span data-ttu-id="92528-107">bağlı olarak değerler arasında değişken bir geçiş oluşturmak için kullanılan <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="92528-107">is used to create a variable transition between values depending on the <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="92528-108">Aşağıdaki örnekte, bu bölümü animasyonun başlar yavaş ama zaman diliminin sonuna doğru katlanarak hızlandırır.</span><span class="sxs-lookup"><span data-stu-id="92528-108">In the example below, this part of the animation starts off slow but toward the end of the time segment, speeds up exponentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92528-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="92528-109">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#Rotation3DAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotation3DAnimationUsingKeyFramesExample.xaml#rotation3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="92528-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="92528-110">See also</span></span>

- [<span data-ttu-id="92528-111">3B Grafiklere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="92528-111">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="92528-112">Anahtar-Çerçeve Animasyonlara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="92528-112">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="92528-113">Görsel Taslaklar Kullanarak 3B Döndürmeye Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="92528-113">Animate a 3-D Rotation Using Storyboards</span></span>](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [<span data-ttu-id="92528-114">Rotation3DAnimation Kullanarak 3B Döndürmeye Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="92528-114">Animate a 3-D Rotation Using Rotation3DAnimation</span></span>](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [<span data-ttu-id="92528-115">Dördeyler Kullanarak 3B Döndürmeye Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="92528-115">Animate a 3-D Rotation Using Quaternions</span></span>](how-to-animate-a-3-d-rotation-using-quaternions.md)
- [<span data-ttu-id="92528-116">Anahtar Çerçeveler Kullanarak 3B Döndürme Hareketlendirme (QuaternionAnimationUsingKeyFrames)</span><span class="sxs-lookup"><span data-stu-id="92528-116">Animate a 3-D Rotation Using Key Frames (QuaternionAnimationUsingKeyFrames)</span></span>](animate-a-3-d-rotation-quaternionanimationusingkeyframes.md)
