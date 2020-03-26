---
title: 'Nasıl yapilir: 3D Çevirileri Animate'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], 3D translations
- 3D translations [WPF], animating
ms.assetid: d4eece1f-0cd2-4a2c-8370-293354c380e4
ms.openlocfilehash: 7d4fff9c74663bd220ad5d15a983bcb639621afd
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112264"
---
# <a name="how-to-animate-3d-translations"></a><span data-ttu-id="6f447-102">Nasıl yapilir: 3D Çevirileri Animate</span><span class="sxs-lookup"><span data-stu-id="6f447-102">How to: Animate 3D Translations</span></span>
<span data-ttu-id="6f447-103">Bu konu, 3B modelüzerinde ayarlanmış bir çeviri dönüşümüne nasıl animasyon yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6f447-103">This topic demonstrates how to animate a translation transformation set on a 3D model.</span></span>  
  
 <span data-ttu-id="6f447-104">Aşağıdaki kod, bir <xref:System.Windows.Media.Media3D.TranslateTransform3D> nesnenin bir <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> <xref:System.Windows.Media.Media3D.GeometryModel3D>. özelliğine uygulanmasını gösterir</span><span class="sxs-lookup"><span data-stu-id="6f447-104">The code below shows the application of a <xref:System.Windows.Media.Media3D.TranslateTransform3D> object to the <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> property of a <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline1)]  
  
 <span data-ttu-id="6f447-105">Bu <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A> <xref:System.Windows.Media.Media3D.TranslateTransform3D> nesnenin özelliği aşağıdaki kod kullanılarak animasyonludur.</span><span class="sxs-lookup"><span data-stu-id="6f447-105">The <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A> property of this <xref:System.Windows.Media.Media3D.TranslateTransform3D> object is animated using the code below.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline2)]  
  
## <a name="example"></a><span data-ttu-id="6f447-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="6f447-106">Example</span></span>  
 <span data-ttu-id="6f447-107">Aşağıdaki kod, tüm örneği gösterir.</span><span class="sxs-lookup"><span data-stu-id="6f447-107">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="6f447-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f447-108">See also</span></span>

- [<span data-ttu-id="6f447-109">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="6f447-109">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="6f447-110">3B Sahne Oluşturma</span><span class="sxs-lookup"><span data-stu-id="6f447-110">Create a 3D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="6f447-111">3D Grafiklere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="6f447-111">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="6f447-112">Dönüşümlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="6f447-112">Transforms Overview</span></span>](transforms-overview.md)
