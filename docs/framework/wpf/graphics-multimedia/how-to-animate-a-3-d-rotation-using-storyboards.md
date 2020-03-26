---
title: 'Nasıl yapilir: Storyboards kullanarak bir 3D Rotasyon Animasyon'
ms.date: 03/30/2017
helpviewer_keywords:
- Storyboards [WPF]
- 3D translations [WPF], animating [WPF], with Storyboards
- animation [WPF], 3D translations [WPF], with Storyboards
ms.assetid: 1020e44e-e21e-49a8-be53-53cbc1910e83
ms.openlocfilehash: 088f1a33cfc73a706ffed55ffff6494adaf8fca4
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112225"
---
# <a name="how-to-animate-a-3d-rotation-using-storyboards"></a><span data-ttu-id="0ff70-102">Nasıl yapilir: Storyboards kullanarak bir 3D Rotasyon Animasyon</span><span class="sxs-lookup"><span data-stu-id="0ff70-102">How to: Animate a 3D Rotation Using Storyboards</span></span>
<span data-ttu-id="0ff70-103">Aşağıdaki örnek, bir <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> nesnenin özelliklerini ve özelliklerini canlandırarak "sallanırken" 3B nesnenin nasıl döndürüldüğünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="0ff70-103">The following example shows how to make a 3D object rotate while it "wobbles" by animating the <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> and <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> properties of an <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> object.</span></span> <span data-ttu-id="0ff70-104">Bu <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> nesne, 3B nesnenin döndürme dönüşümünü belirtir ve böylece özelliklerini canlandırarak istek döndürme efekti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0ff70-104">This <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> object specifies the rotation transform of the 3D object and so animating its properties creates the desire rotation effect.</span></span> <span data-ttu-id="0ff70-105">Storyboard içinde, <xref:System.Windows.Media.Animation.DoubleAnimation> <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> özelliği canlandırmak için kullanılırken <xref:System.Windows.Media.Animation.Vector3DAnimation> özelliği canlandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0ff70-105">Within the Storyboard, <xref:System.Windows.Media.Animation.DoubleAnimation> is used to animate the <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> property while <xref:System.Windows.Media.Animation.Vector3DAnimation> is used to animate the <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ff70-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="0ff70-106">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#Rotate3DUsingAxisAngleRotation3DExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotat3DUsingAxisAngleRotation3DExample.xaml#rotate3dusingaxisanglerotation3dexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="0ff70-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ff70-107">See also</span></span>

- [<span data-ttu-id="0ff70-108">Rotation3DAnimation kullanarak 3B Döndürme animasyonu</span><span class="sxs-lookup"><span data-stu-id="0ff70-108">Animate a 3D Rotation Using Rotation3DAnimation</span></span>](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [<span data-ttu-id="0ff70-109">Anahtar Çerçeveleri Kullanarak 3B Döndürme (Döndürme3DAnimationUsingKeyFrames)</span><span class="sxs-lookup"><span data-stu-id="0ff70-109">Animate a 3D Rotation Using Key Frames (Rotation3DAnimationUsingKeyFrames)</span></span>](how-to-animate-a-3-d-rotation-using-key-frames.md)
- [<span data-ttu-id="0ff70-110">3D Grafiklere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0ff70-110">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="0ff70-111">Görsel Taslaklara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0ff70-111">Storyboards Overview</span></span>](storyboards-overview.md)
