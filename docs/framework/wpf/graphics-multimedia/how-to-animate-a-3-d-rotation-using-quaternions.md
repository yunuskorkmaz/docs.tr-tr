---
title: 'Nasıl yapılır: Dördeyler Kullanarak 3B Döndürmeye Animasyon Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- quaternions [WPF]
- animation [WPF], 3-D translations [WPF], with quaternions
- 3-D translations [WPF], animating [WPF], with quaternions
ms.assetid: adca9cb1-066b-4de8-abbb-6b4007579ee7
ms.openlocfilehash: df51db324bffc038bc585b6d977a82d54feefb3b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54550935"
---
# <a name="how-to-animate-a-3-d-rotation-using-quaternions"></a><span data-ttu-id="691bc-102">Nasıl yapılır: Dördeyler Kullanarak 3B Döndürmeye Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="691bc-102">How to: Animate a 3-D Rotation Using Quaternions</span></span>
<span data-ttu-id="691bc-103">Bu örnekte, Dördeyler kullanarak 3B nesnenin bir döndürme hareketlendirme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="691bc-103">This example shows how to animate a rotation of a 3-D object using quaternions.</span></span>  
  
 <span data-ttu-id="691bc-104">Aşağıdaki kod gösterir bir <xref:System.Windows.Media.Media3D.QuaternionRotation3D> değeri olarak kullanılan <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> özelliği bir <xref:System.Windows.Media.Media3D.RotateTransform3D>.</span><span class="sxs-lookup"><span data-stu-id="691bc-104">The code below shows a <xref:System.Windows.Media.Media3D.QuaternionRotation3D> used as the value for the <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> property of a <xref:System.Windows.Media.Media3D.RotateTransform3D>.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline1)]  
  
 <span data-ttu-id="691bc-105">Bu <xref:System.Windows.Media.Media3D.QuaternionRotation3D> ile animasyon bir <xref:System.Windows.Media.Animation.QuaternionAnimation> içinde bir <xref:System.Windows.Media.Animation.Storyboard> aşağıdaki kodu kullanarak.</span><span class="sxs-lookup"><span data-stu-id="691bc-105">This <xref:System.Windows.Media.Media3D.QuaternionRotation3D> is animated with a <xref:System.Windows.Media.Animation.QuaternionAnimation> within a <xref:System.Windows.Media.Animation.Storyboard> using the code below.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleInline2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline2)]  
  
## <a name="example"></a><span data-ttu-id="691bc-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="691bc-106">Example</span></span>  
 <span data-ttu-id="691bc-107">Aşağıdaki kod, tüm örnek gösterir.</span><span class="sxs-lookup"><span data-stu-id="691bc-107">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="691bc-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="691bc-108">See also</span></span>
- [<span data-ttu-id="691bc-109">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="691bc-109">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [<span data-ttu-id="691bc-110">3B Görünümü Oluşturma</span><span class="sxs-lookup"><span data-stu-id="691bc-110">Create a 3-D Scene</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="691bc-111">3B Grafiklere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="691bc-111">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
- [<span data-ttu-id="691bc-112">Dönüşümlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="691bc-112">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
- [<span data-ttu-id="691bc-113">Görsel Taslaklar Kullanarak 3B Döndürmeye Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="691bc-113">Animate a 3-D Rotation Using Storyboards</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-storyboards.md)
- [<span data-ttu-id="691bc-114">Rotation3DAnimation Kullanarak 3B Döndürmeye Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="691bc-114">Animate a 3-D Rotation Using Rotation3DAnimation</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
