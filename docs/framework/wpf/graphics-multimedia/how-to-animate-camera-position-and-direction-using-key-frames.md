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
ms.openlocfilehash: 5be14513755c3b5c80c13cbc5cae889cc4663cec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33558852"
---
# <a name="how-to-animate-camera-position-and-direction-using-key-frames"></a><span data-ttu-id="16697-102">Nasıl yapılır: Anahtar Çerçeveler Kullanarak Kamera Konumuna ve Yönüne Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="16697-102">How to: Animate Camera Position and Direction Using Key Frames</span></span>
<span data-ttu-id="16697-103">Aşağıdaki örnekte, <xref:System.Windows.Media.Animation.Point3DAnimationUsingKeyFrames> konumunu hareketli hale getirmeyi için kullanılan bir <xref:System.Windows.Media.Media3D.PerspectiveCamera> 3B Sahne içinde.</span><span class="sxs-lookup"><span data-stu-id="16697-103">In the following example, <xref:System.Windows.Media.Animation.Point3DAnimationUsingKeyFrames> is used to animate the position of a <xref:System.Windows.Media.Media3D.PerspectiveCamera> in a 3D scene.</span></span> <span data-ttu-id="16697-104">Ayrıca, <xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames> Kamera 3B Sahne işaret yönü animasyon için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="16697-104">In addition, <xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames> is used to animate the direction the camera is pointing in the 3D scene.</span></span> <span data-ttu-id="16697-105">Bu animasyonların ikisi de animasyon efektleri dizisi oluşturan birçok anahtar çerçeve kullanın:</span><span class="sxs-lookup"><span data-stu-id="16697-105">Both of these animations use several key frames which create a series of animation effects:</span></span>  
  
1.  <span data-ttu-id="16697-106"><xref:System.Windows.Media.Animation.LinearPoint3DKeyFrame> ve <xref:System.Windows.Media.Animation.LinearVector3DKeyFrame> değerler arasında düzgün, doğrusal ilişkilendirme oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="16697-106"><xref:System.Windows.Media.Animation.LinearPoint3DKeyFrame> and <xref:System.Windows.Media.Animation.LinearVector3DKeyFrame> are used to create a smooth, linear interpolation between values.</span></span>  
  
2.  <span data-ttu-id="16697-107"><xref:System.Windows.Media.Animation.DiscretePoint3DKeyFrame> ve <xref:System.Windows.Media.Animation.DiscreteVector3DKeyFrame> değerleri (ilişkilendirme yok) arasında ani "atlar" oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="16697-107"><xref:System.Windows.Media.Animation.DiscretePoint3DKeyFrame> and <xref:System.Windows.Media.Animation.DiscreteVector3DKeyFrame> are used to create sudden "jumps" between values (no interpolation).</span></span>  
  
3.  <span data-ttu-id="16697-108"><xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame> ve <xref:System.Windows.Media.Animation.SplineVector3DKeyFrame> bağlı olarak değerler arasında değişken geçiş oluşturmak için kullanılan <xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame.KeySpline%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="16697-108"><xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame> and <xref:System.Windows.Media.Animation.SplineVector3DKeyFrame> are used to create a variable transition between values depending on the <xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="16697-109">Aşağıdaki örnekte, animasyon yavaş ancak zaman diliminin sonuna doğru başlatır ve katlanarak hızlanır.</span><span class="sxs-lookup"><span data-stu-id="16697-109">In the example below, the animation starts off slow but toward the end of the time segment, speeds up exponentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16697-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="16697-110">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#PointVector3DAnimationUsingKeyFramesExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationUsingKeyFramesExample.xaml#pointvector3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="16697-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="16697-111">See Also</span></span>  
 [<span data-ttu-id="16697-112">3B Görünümde Kamera Konumuna ve Yönüne Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="16697-112">Animate Camera Position and Direction in a 3D Scene</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-camera-position-and-direction-in-a-3d-scene.md)  
 [<span data-ttu-id="16697-113">3B Grafiklere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="16697-113">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
