---
title: "Nasıl yapılır: 3B Görünümde Kamera Konumuna ve Yönüne Animasyon Ekleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], camera position in 3-D scenes
- camera direction [WPF], animating in 3-D scenes
- 3-D scenes [WPF], animating camera position
- 3-D scenes [WPF], animating camera direction
- camera position [WPF], animating in 3-D scenes
- animation [WPF], camera direction in 3-D scenes
ms.assetid: 480224b7-a5e5-4165-ba7f-ef760ddff94a
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 790260f974dcb0be398af202cc7156fc91efed91
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-camera-position-and-direction-in-a-3d-scene"></a><span data-ttu-id="b8023-102">Nasıl yapılır: 3B Görünümde Kamera Konumuna ve Yönüne Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="b8023-102">How to: Animate Camera Position and Direction in a 3D Scene</span></span>
<span data-ttu-id="b8023-103">Aşağıdaki örnek, kamera konumunu hareketli hale getirmeyi ve 3B Sahne işaret ettiği yönü animasyon gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b8023-103">The following example shows how to animate the position of a camera and animate the direction it is pointing in a 3D scene.</span></span> <span data-ttu-id="b8023-104">Bu kullanılarak yapılır <xref:System.Windows.Media.Animation.Point3DAnimation> ve <xref:System.Windows.Media.Animation.Vector3DAnimation> animasyon için <xref:System.Windows.Media.Media3D.ProjectionCamera.Position%2A> ve <xref:System.Windows.Media.Media3D.ProjectionCamera.LookDirection%2A> özelliklerini sırasıyla <xref:System.Windows.Media.Media3D.PerspectiveCamera>.</span><span class="sxs-lookup"><span data-stu-id="b8023-104">This is done by using <xref:System.Windows.Media.Animation.Point3DAnimation> and <xref:System.Windows.Media.Animation.Vector3DAnimation> to animate the <xref:System.Windows.Media.Media3D.ProjectionCamera.Position%2A> and <xref:System.Windows.Media.Media3D.ProjectionCamera.LookDirection%2A> properties respectively of the <xref:System.Windows.Media.Media3D.PerspectiveCamera>.</span></span> <span data-ttu-id="b8023-105">Bunun gibi bir animasyon, bir olaya yanıt olarak izleyicisinin görünüm değiştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b8023-105">You might use an animation like this to change the onlooker's view of a scene in response to an event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8023-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="b8023-106">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#PointVector3DAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationExample.xaml#pointvector3danimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="b8023-107">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b8023-107">See Also</span></span>  
 <xref:System.Windows.Media.Animation.Vector3DAnimation>  
 <xref:System.Windows.Media.Animation.Point3DAnimation>  
 [<span data-ttu-id="b8023-108">Kamera konumunu ve anahtar çerçeveler kullanarak yönünü animasyon ekleme</span><span class="sxs-lookup"><span data-stu-id="b8023-108">Animate Camera Position and Direction Using Key Frames</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-camera-position-and-direction-using-key-frames.md)  
 [<span data-ttu-id="b8023-109">3B Grafiklere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b8023-109">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
