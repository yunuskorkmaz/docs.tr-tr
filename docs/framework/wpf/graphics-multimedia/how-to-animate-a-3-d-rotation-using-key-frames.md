---
title: 'Nasıl yapılır: Anahtar Çerçeveler Kullanarak 3B Döndürmeye Animasyon Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], 3-D translations [WPF], with key frames (Rotation3DAnimation)
- key frames [WPF], Rotation3DAnimation
- 3-D translations [WPF], animating [WPF], with key frames (Rotation3DAnimation)
ms.assetid: 6f671b95-7f30-4836-9a4f-aeb7dc30121f
ms.openlocfilehash: 085b2da20410d53fce6099131bf07249bde3209c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557632"
---
# <a name="how-to-animate-a-3-d-rotation-using-key-frames"></a><span data-ttu-id="fea1a-102">Nasıl yapılır: Anahtar Çerçeveler Kullanarak 3B Döndürmeye Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="fea1a-102">How to: Animate a 3-D Rotation Using Key Frames</span></span>
<span data-ttu-id="fea1a-103">Aşağıdaki örnekte, <xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames> bir "sallanmasına içinde" kaynaklanan dönme ekseni canlandırır olurken bir 3B nesneyi döndürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fea1a-103">In the following example, <xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames> is used to make a 3D object rotate while its axis of rotation animates resulting in a "wobble".</span></span> <span data-ttu-id="fea1a-104">Bu animasyon aşağıdaki anahtar çerçevelerini kullanır:</span><span class="sxs-lookup"><span data-stu-id="fea1a-104">This animation uses the following key frames:</span></span>  
  
1.  <span data-ttu-id="fea1a-105"><xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame> değerler arasında düzgün, doğrusal ilişkilendirme oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fea1a-105"><xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame> is used to create a smooth, linear interpolation between values.</span></span>  
  
2.  <span data-ttu-id="fea1a-106"><xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame> değerler (ilişkilendirme yok) arasında ani "atlar" oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fea1a-106"><xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame> is used to create sudden "jumps" between values (no interpolation).</span></span>  
  
3.  <span data-ttu-id="fea1a-107"><xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame> bağlı olarak değerler arasında değişken geçiş oluşturmak için kullanılan <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="fea1a-107"><xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame> is used to create a variable transition between values depending on the <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="fea1a-108">Aşağıdaki örnekte, bu bölümü animasyonun yavaş ancak zaman diliminin sonuna doğru başlatır ve katlanarak hızlanır.</span><span class="sxs-lookup"><span data-stu-id="fea1a-108">In the example below, this part of the animation starts off slow but toward the end of the time segment, speeds up exponentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fea1a-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="fea1a-109">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#Rotation3DAnimationUsingKeyFramesExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotation3DAnimationUsingKeyFramesExample.xaml#rotation3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="fea1a-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fea1a-110">See Also</span></span>  
 [<span data-ttu-id="fea1a-111">3B Grafiklere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="fea1a-111">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [<span data-ttu-id="fea1a-112">Anahtar-Çerçeve Animasyonlara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="fea1a-112">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="fea1a-113">Görsel Taslaklar Kullanarak 3B Döndürmeye Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="fea1a-113">Animate a 3-D Rotation Using Storyboards</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-storyboards.md)  
 [<span data-ttu-id="fea1a-114">Rotation3DAnimation Kullanarak 3B Döndürmeye Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="fea1a-114">Animate a 3-D Rotation Using Rotation3DAnimation</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-rotation3danimation.md)  
 [<span data-ttu-id="fea1a-115">Dördeyler Kullanarak 3B Döndürmeye Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="fea1a-115">Animate a 3-D Rotation Using Quaternions</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-quaternions.md)  
 [<span data-ttu-id="fea1a-116">Anahtar Çerçeveler Kullanarak 3B Döndürme Hareketlendirme (QuaternionAnimationUsingKeyFrames)</span><span class="sxs-lookup"><span data-stu-id="fea1a-116">Animate a 3-D Rotation Using Key Frames (QuaternionAnimationUsingKeyFrames)</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animate-a-3-d-rotation-quaternionanimationusingkeyframes.md)
