---
title: "Nasıl yapilir: Kuaterniyonlar Kullanarak 3D Rotasyon'u canlandırma"
ms.date: 03/30/2017
helpviewer_keywords:
- quaternions [WPF]
- animation [WPF], 3D translations [WPF], with quaternions
- 3D translations [WPF], animating [WPF], with quaternions
ms.assetid: adca9cb1-066b-4de8-abbb-6b4007579ee7
ms.openlocfilehash: 0d229b0a714cc53459943fae751ab4d4f787d7d8
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112251"
---
# <a name="how-to-animate-a-3d-rotation-using-quaternions"></a><span data-ttu-id="91147-102">Nasıl yapilir: Kuaterniyonlar Kullanarak 3D Rotasyon'u canlandırma</span><span class="sxs-lookup"><span data-stu-id="91147-102">How to: Animate a 3D Rotation Using Quaternions</span></span>
<span data-ttu-id="91147-103">Bu örnek, kuaterniyonlar kullanarak bir 3B nesnenin döndürme nasıl animasyon gösterir.</span><span class="sxs-lookup"><span data-stu-id="91147-103">This example shows how to animate a rotation of a 3D object using quaternions.</span></span>  
  
 <span data-ttu-id="91147-104">Aşağıdaki kod, <xref:System.Windows.Media.Media3D.QuaternionRotation3D> bir <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> <xref:System.Windows.Media.Media3D.RotateTransform3D>. özelliği için kullanılan bir değeri gösterir</span><span class="sxs-lookup"><span data-stu-id="91147-104">The code below shows a <xref:System.Windows.Media.Media3D.QuaternionRotation3D> used as the value for the <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> property of a <xref:System.Windows.Media.Media3D.RotateTransform3D>.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline1)]  
  
 <span data-ttu-id="91147-105">Bu, <xref:System.Windows.Media.Media3D.QuaternionRotation3D> aşağıdaki <xref:System.Windows.Media.Animation.QuaternionAnimation> kodu <xref:System.Windows.Media.Animation.Storyboard> kullanarak bir içinde animasyonludur.</span><span class="sxs-lookup"><span data-stu-id="91147-105">This <xref:System.Windows.Media.Media3D.QuaternionRotation3D> is animated with a <xref:System.Windows.Media.Animation.QuaternionAnimation> within a <xref:System.Windows.Media.Animation.Storyboard> using the code below.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline2)]  
  
## <a name="example"></a><span data-ttu-id="91147-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="91147-106">Example</span></span>  
 <span data-ttu-id="91147-107">Aşağıdaki kod, tüm örneği gösterir.</span><span class="sxs-lookup"><span data-stu-id="91147-107">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="91147-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="91147-108">See also</span></span>

- [<span data-ttu-id="91147-109">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="91147-109">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="91147-110">3B Sahne Oluşturma</span><span class="sxs-lookup"><span data-stu-id="91147-110">Create a 3D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="91147-111">3D Grafiklere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="91147-111">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="91147-112">Dönüşümlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="91147-112">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="91147-113">Storyboards kullanarak bir 3B Rotasyon animasyon</span><span class="sxs-lookup"><span data-stu-id="91147-113">Animate a 3D Rotation Using Storyboards</span></span>](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [<span data-ttu-id="91147-114">Rotation3DAnimation kullanarak 3B Döndürme animasyonu</span><span class="sxs-lookup"><span data-stu-id="91147-114">Animate a 3D Rotation Using Rotation3DAnimation</span></span>](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
