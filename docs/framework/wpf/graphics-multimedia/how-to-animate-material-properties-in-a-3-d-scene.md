---
title: 'Nasıl yapilir: 3B Sahnede Malzeme Özelliklerini Animasyona'
ms.date: 03/30/2017
helpviewer_keywords:
- Material properties [WPF], animating in 3D scenes
- animation [WPF], Material properties in 3D scenes
- 3D scenes [WPF], animating Material properties
ms.assetid: 229fd6eb-7401-4992-b0c9-8b28de230c0f
ms.openlocfilehash: db59debcd7558cde52d8604cb04c8c4e68921825
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112199"
---
# <a name="how-to-animate-material-properties-in-a-3d-scene"></a><span data-ttu-id="fa9bd-102">Nasıl yapilir: 3B Sahnede Malzeme Özelliklerini Animasyona</span><span class="sxs-lookup"><span data-stu-id="fa9bd-102">How to: Animate Material Properties in a 3D Scene</span></span>
<span data-ttu-id="fa9bd-103">Bu örnek, <xref:System.Windows.Media.Brush.Opacity%2A> <xref:System.Windows.Media.Media3D.Material> uygulanan bir 3B modele uygulanan özelliğin nasıl canlandırılabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="fa9bd-103">This example shows how to animate the <xref:System.Windows.Media.Brush.Opacity%2A> property of the <xref:System.Windows.Media.Media3D.Material> applied to a 3D model.</span></span>  
  
 <span data-ttu-id="fa9bd-104">Aşağıdaki kod örneği 3B nesneye <xref:System.Windows.Media.LinearGradientBrush> <xref:System.Windows.Media.Media3D.Material> uygulanan olarak kullanılır tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fa9bd-104">The following code example defines the <xref:System.Windows.Media.LinearGradientBrush> used as the <xref:System.Windows.Media.Media3D.Material> applied to the 3D object.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#AnimateMaterialExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexampleinline1)]  
  
 <span data-ttu-id="fa9bd-105">Bunun <xref:System.Windows.Media.Brush.Opacity%2A> <xref:System.Windows.Media.LinearGradientBrush> özelliği aşağıdaki kod örneği kullanılarak animasyonludur.</span><span class="sxs-lookup"><span data-stu-id="fa9bd-105">The <xref:System.Windows.Media.Brush.Opacity%2A> property of this <xref:System.Windows.Media.LinearGradientBrush> is animated using the code example below.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#AnimateMaterialExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexampleinline2)]  
  
## <a name="example"></a><span data-ttu-id="fa9bd-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="fa9bd-106">Example</span></span>  
 <span data-ttu-id="fa9bd-107">Aşağıdaki kod, tüm örneği gösterir.</span><span class="sxs-lookup"><span data-stu-id="fa9bd-107">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#AnimateMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="fa9bd-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fa9bd-108">See also</span></span>

- [<span data-ttu-id="fa9bd-109">3B Sahne Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fa9bd-109">Create a 3D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="fa9bd-110">3D Grafiklere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="fa9bd-110">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
