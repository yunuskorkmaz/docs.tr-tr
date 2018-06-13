---
title: 'Nasıl yapılır: Görsel Taslaklar Kullanarak 3B Döndürmeye Animasyon Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- Storyboards [WPF]
- 3-D translations [WPF], animating [WPF], with Storyboards
- animation [WPF], 3-D translations [WPF], with Storyboards
ms.assetid: 1020e44e-e21e-49a8-be53-53cbc1910e83
ms.openlocfilehash: a6cc8774c14d4b393b0d04822216c894e486ba66
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33556711"
---
# <a name="how-to-animate-a-3-d-rotation-using-storyboards"></a><span data-ttu-id="a43f0-102">Nasıl yapılır: Görsel Taslaklar Kullanarak 3B Döndürmeye Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="a43f0-102">How to: Animate a 3-D Rotation Using Storyboards</span></span>
<span data-ttu-id="a43f0-103">Aşağıdaki örnekte, "sallarken" döndürün 3B bir nesneyi gösterilmektedir <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> ve <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> özelliklerini bir <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="a43f0-103">The following example shows how to make a 3D object rotate while it "wobbles" by animating the <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> and <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> properties of an <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> object.</span></span> <span data-ttu-id="a43f0-104">Bu <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> nesnesi 3B nesnenin döndürme dönüştürme belirtir ve bu nedenle özelliklerini animasyon desire döndürme efekti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a43f0-104">This <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> object specifies the rotation transform of the 3D object and so animating its properties creates the desire rotation effect.</span></span> <span data-ttu-id="a43f0-105">Film şeridi içinde <xref:System.Windows.Media.Animation.DoubleAnimation> animasyon uygulamak için kullanılan <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> sırasında özelliği <xref:System.Windows.Media.Animation.Vector3DAnimation> animasyon uygulamak için kullanılan <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="a43f0-105">Within the Storyboard, <xref:System.Windows.Media.Animation.DoubleAnimation> is used to animate the <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> property while <xref:System.Windows.Media.Animation.Vector3DAnimation> is used to animate the <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a43f0-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="a43f0-106">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#Rotate3DUsingAxisAngleRotation3DExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotat3DUsingAxisAngleRotation3DExample.xaml#rotate3dusingaxisanglerotation3dexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="a43f0-107">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a43f0-107">See Also</span></span>  
 [<span data-ttu-id="a43f0-108">Rotation3DAnimation Kullanarak 3B Döndürmeye Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="a43f0-108">Animate a 3-D Rotation Using Rotation3DAnimation</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-rotation3danimation.md)  
 [<span data-ttu-id="a43f0-109">Anahtar Çerçeveler Kullanarak 3B Döndürmeye Animasyon Ekleme (Rotation3DAnimationUsingKeyFrames)</span><span class="sxs-lookup"><span data-stu-id="a43f0-109">Animate a 3-D Rotation Using Key Frames (Rotation3DAnimationUsingKeyFrames)</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-key-frames.md)  
 [<span data-ttu-id="a43f0-110">3B Grafiklere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a43f0-110">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [<span data-ttu-id="a43f0-111">Görsel Taslaklara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a43f0-111">Storyboards Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
