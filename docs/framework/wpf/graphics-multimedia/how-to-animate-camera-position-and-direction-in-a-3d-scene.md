---
title: 'Nasıl yapılır: 3B Görünümde Kamera Konumuna ve Yönüne Animasyon Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], camera position in 3-D scenes
- camera direction [WPF], animating in 3-D scenes
- 3-D scenes [WPF], animating camera position
- 3-D scenes [WPF], animating camera direction
- camera position [WPF], animating in 3-D scenes
- animation [WPF], camera direction in 3-D scenes
ms.assetid: 480224b7-a5e5-4165-ba7f-ef760ddff94a
ms.openlocfilehash: b64263a495ffe845a76317aad8f5b4a14e11b31e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61651382"
---
# <a name="how-to-animate-camera-position-and-direction-in-a-3d-scene"></a><span data-ttu-id="1e6c9-102">Nasıl yapılır: 3B Görünümde Kamera Konumuna ve Yönüne Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="1e6c9-102">How to: Animate Camera Position and Direction in a 3D Scene</span></span>
<span data-ttu-id="1e6c9-103">Aşağıdaki örnek, bir kamera konumuna animasyon ekleme ve 3B Sahne işaret eden yönüne animasyon ekleme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1e6c9-103">The following example shows how to animate the position of a camera and animate the direction it is pointing in a 3D scene.</span></span> <span data-ttu-id="1e6c9-104">Bu kullanılarak yapılır <xref:System.Windows.Media.Animation.Point3DAnimation> ve <xref:System.Windows.Media.Animation.Vector3DAnimation> animasyon uygulamak için <xref:System.Windows.Media.Media3D.ProjectionCamera.Position%2A> ve <xref:System.Windows.Media.Media3D.ProjectionCamera.LookDirection%2A> özellikleri sırasıyla <xref:System.Windows.Media.Media3D.PerspectiveCamera>.</span><span class="sxs-lookup"><span data-stu-id="1e6c9-104">This is done by using <xref:System.Windows.Media.Animation.Point3DAnimation> and <xref:System.Windows.Media.Animation.Vector3DAnimation> to animate the <xref:System.Windows.Media.Media3D.ProjectionCamera.Position%2A> and <xref:System.Windows.Media.Media3D.ProjectionCamera.LookDirection%2A> properties respectively of the <xref:System.Windows.Media.Media3D.PerspectiveCamera>.</span></span> <span data-ttu-id="1e6c9-105">Bunun gibi bir animasyon, bir olaya yanıt olarak izleyicisinin görünüm değiştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1e6c9-105">You might use an animation like this to change the onlooker's view of a scene in response to an event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e6c9-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="1e6c9-106">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#PointVector3DAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationExample.xaml#pointvector3danimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="1e6c9-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1e6c9-107">See also</span></span>

- <xref:System.Windows.Media.Animation.Vector3DAnimation>
- <xref:System.Windows.Media.Animation.Point3DAnimation>
- [<span data-ttu-id="1e6c9-108">Anahtar Çerçeveler Kullanarak Kamera Konumuna ve Yönüne Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="1e6c9-108">Animate Camera Position and Direction Using Key Frames</span></span>](how-to-animate-camera-position-and-direction-using-key-frames.md)
- [<span data-ttu-id="1e6c9-109">3B Grafiklere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="1e6c9-109">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
