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
ms.openlocfilehash: 44464cc314d649516998338e36c1b523101ac4e2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59346086"
---
# <a name="how-to-animate-camera-position-and-direction-using-key-frames"></a><span data-ttu-id="f7a2e-102">Nasıl yapılır: Anahtar Çerçeveler Kullanarak Kamera Konumuna ve Yönüne Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="f7a2e-102">How to: Animate Camera Position and Direction Using Key Frames</span></span>
<span data-ttu-id="f7a2e-103">Aşağıdaki örnekte, <xref:System.Windows.Media.Animation.Point3DAnimationUsingKeyFrames> animasyon ekleme için kullanılan bir <xref:System.Windows.Media.Media3D.PerspectiveCamera> 3B görünümde.</span><span class="sxs-lookup"><span data-stu-id="f7a2e-103">In the following example, <xref:System.Windows.Media.Animation.Point3DAnimationUsingKeyFrames> is used to animate the position of a <xref:System.Windows.Media.Media3D.PerspectiveCamera> in a 3D scene.</span></span> <span data-ttu-id="f7a2e-104">Ayrıca, <xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames> 3B görünümde kamera işaret eden yönüne animasyon uygulamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f7a2e-104">In addition, <xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames> is used to animate the direction the camera is pointing in the 3D scene.</span></span> <span data-ttu-id="f7a2e-105">Bu animasyonları her ikisi de, animasyon efektleri bir dizi oluşturmak birkaç anahtar çerçeveleri kullanın:</span><span class="sxs-lookup"><span data-stu-id="f7a2e-105">Both of these animations use several key frames which create a series of animation effects:</span></span>  
  
1. <span data-ttu-id="f7a2e-106"><xref:System.Windows.Media.Animation.LinearPoint3DKeyFrame> ve <xref:System.Windows.Media.Animation.LinearVector3DKeyFrame> değerler arasında sorunsuz, doğrusal bir ilişkilendirme oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f7a2e-106"><xref:System.Windows.Media.Animation.LinearPoint3DKeyFrame> and <xref:System.Windows.Media.Animation.LinearVector3DKeyFrame> are used to create a smooth, linear interpolation between values.</span></span>  
  
2. <span data-ttu-id="f7a2e-107"><xref:System.Windows.Media.Animation.DiscretePoint3DKeyFrame> ve <xref:System.Windows.Media.Animation.DiscreteVector3DKeyFrame> değerleri (ilişkilendirme yok) arasında ani "atlar" oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f7a2e-107"><xref:System.Windows.Media.Animation.DiscretePoint3DKeyFrame> and <xref:System.Windows.Media.Animation.DiscreteVector3DKeyFrame> are used to create sudden "jumps" between values (no interpolation).</span></span>  
  
3. <span data-ttu-id="f7a2e-108"><xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame> ve <xref:System.Windows.Media.Animation.SplineVector3DKeyFrame> bağlı olarak değerler arasında değişken bir geçiş oluşturmak için kullanılan <xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame.KeySpline%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="f7a2e-108"><xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame> and <xref:System.Windows.Media.Animation.SplineVector3DKeyFrame> are used to create a variable transition between values depending on the <xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="f7a2e-109">Aşağıdaki örnekte, animasyon başlar yavaş ama zaman diliminin sonuna doğru katlanarak hızlandırır.</span><span class="sxs-lookup"><span data-stu-id="f7a2e-109">In the example below, the animation starts off slow but toward the end of the time segment, speeds up exponentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7a2e-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="f7a2e-110">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#PointVector3DAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationUsingKeyFramesExample.xaml#pointvector3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="f7a2e-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f7a2e-111">See also</span></span>

- [<span data-ttu-id="f7a2e-112">3B Görünümde Kamera Konumuna ve Yönüne Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="f7a2e-112">Animate Camera Position and Direction in a 3D Scene</span></span>](how-to-animate-camera-position-and-direction-in-a-3d-scene.md)
- [<span data-ttu-id="f7a2e-113">3B Grafiklere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f7a2e-113">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
