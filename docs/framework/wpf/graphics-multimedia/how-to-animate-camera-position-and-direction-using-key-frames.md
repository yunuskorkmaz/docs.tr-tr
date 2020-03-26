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
# <a name="how-to-animate-camera-position-and-direction-using-key-frames"></a><span data-ttu-id="ba46a-102">Nasıl yapılır: Anahtar Çerçeveler Kullanarak Kamera Konumuna ve Yönüne Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="ba46a-102">How to: Animate Camera Position and Direction Using Key Frames</span></span>
<span data-ttu-id="ba46a-103">Aşağıdaki örnekte, <xref:System.Windows.Media.Animation.Point3DAnimationUsingKeyFrames> bir 3B sahnedeki konumu <xref:System.Windows.Media.Media3D.PerspectiveCamera> canlandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ba46a-103">In the following example, <xref:System.Windows.Media.Animation.Point3DAnimationUsingKeyFrames> is used to animate the position of a <xref:System.Windows.Media.Media3D.PerspectiveCamera> in a 3D scene.</span></span> <span data-ttu-id="ba46a-104">Buna ek <xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames> olarak, kameranın 3B sahnede işaret olduğu yönü canlandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ba46a-104">In addition, <xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames> is used to animate the direction the camera is pointing in the 3D scene.</span></span> <span data-ttu-id="ba46a-105">Bu animasyonların her ikisi de bir dizi animasyon efekti oluşturan birkaç anahtar kare kullanır:</span><span class="sxs-lookup"><span data-stu-id="ba46a-105">Both of these animations use several key frames which create a series of animation effects:</span></span>  
  
1. <span data-ttu-id="ba46a-106"><xref:System.Windows.Media.Animation.LinearPoint3DKeyFrame><xref:System.Windows.Media.Animation.LinearVector3DKeyFrame> ve değerler arasında düzgün, doğrusal enterpolasyon oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ba46a-106"><xref:System.Windows.Media.Animation.LinearPoint3DKeyFrame> and <xref:System.Windows.Media.Animation.LinearVector3DKeyFrame> are used to create a smooth, linear interpolation between values.</span></span>  
  
2. <span data-ttu-id="ba46a-107"><xref:System.Windows.Media.Animation.DiscretePoint3DKeyFrame><xref:System.Windows.Media.Animation.DiscreteVector3DKeyFrame> ve değerler arasında ani "atlar" oluşturmak için kullanılır (enterpolasyon yok).</span><span class="sxs-lookup"><span data-stu-id="ba46a-107"><xref:System.Windows.Media.Animation.DiscretePoint3DKeyFrame> and <xref:System.Windows.Media.Animation.DiscreteVector3DKeyFrame> are used to create sudden "jumps" between values (no interpolation).</span></span>  
  
3. <span data-ttu-id="ba46a-108"><xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame><xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame.KeySpline%2A> ve <xref:System.Windows.Media.Animation.SplineVector3DKeyFrame> özelliğe bağlı olarak değerler arasında değişken bir geçiş oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ba46a-108"><xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame> and <xref:System.Windows.Media.Animation.SplineVector3DKeyFrame> are used to create a variable transition between values depending on the <xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="ba46a-109">Aşağıdaki örnekte, animasyon yavaş başlar, ancak zaman diliminin sonuna doğru, katlanarak hızlar.</span><span class="sxs-lookup"><span data-stu-id="ba46a-109">In the example below, the animation starts off slow but toward the end of the time segment, speeds up exponentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba46a-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="ba46a-110">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#PointVector3DAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationUsingKeyFramesExample.xaml#pointvector3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="ba46a-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ba46a-111">See also</span></span>

- [<span data-ttu-id="ba46a-112">3B Görünümde Kamera Konumuna ve Yönüne Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="ba46a-112">Animate Camera Position and Direction in a 3D Scene</span></span>](how-to-animate-camera-position-and-direction-in-a-3d-scene.md)
- [<span data-ttu-id="ba46a-113">3D Grafiklere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ba46a-113">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
