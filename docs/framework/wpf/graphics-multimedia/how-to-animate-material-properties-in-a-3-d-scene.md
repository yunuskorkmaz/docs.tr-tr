---
title: 'Nasıl yapılır: 3B Görünümde Malzeme Özelliklerine Animasyon Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- Material properties [WPF], animating in 3-D scenes
- animation [WPF], Material properties in 3-D scenes
- 3-D scenes [WPF], animating Material properties
ms.assetid: 229fd6eb-7401-4992-b0c9-8b28de230c0f
ms.openlocfilehash: 8dfd7f01b87e2becfbcf57544ec4f8340cf8d5cc
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662547"
---
# <a name="how-to-animate-material-properties-in-a-3-d-scene"></a><span data-ttu-id="d5f6c-102">Nasıl yapılır: 3B Görünümde Malzeme Özelliklerine Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="d5f6c-102">How to: Animate Material Properties in a 3-D Scene</span></span>
<span data-ttu-id="d5f6c-103">Bu örnek, animasyon ekleme işlemi gösterilmektedir <xref:System.Windows.Media.Brush.Opacity%2A> özelliği <xref:System.Windows.Media.Media3D.Material> 3B modeline uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d5f6c-103">This example shows how to animate the <xref:System.Windows.Media.Brush.Opacity%2A> property of the <xref:System.Windows.Media.Media3D.Material> applied to a 3-D model.</span></span>  
  
 <span data-ttu-id="d5f6c-104">Aşağıdaki kod örneği tanımlar <xref:System.Windows.Media.LinearGradientBrush> olarak kullanılan <xref:System.Windows.Media.Media3D.Material> 3B nesneye uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d5f6c-104">The following code example defines the <xref:System.Windows.Media.LinearGradientBrush> used as the <xref:System.Windows.Media.Media3D.Material> applied to the 3D object.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#AnimateMaterialExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexampleinline1)]  
  
 <span data-ttu-id="d5f6c-105"><xref:System.Windows.Media.Brush.Opacity%2A> Bu özelliği <xref:System.Windows.Media.LinearGradientBrush> aşağıdaki kod örneği kullanarak bir animasyon görünür.</span><span class="sxs-lookup"><span data-stu-id="d5f6c-105">The <xref:System.Windows.Media.Brush.Opacity%2A> property of this <xref:System.Windows.Media.LinearGradientBrush> is animated using the code example below.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#AnimateMaterialExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexampleinline2)]  
  
## <a name="example"></a><span data-ttu-id="d5f6c-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="d5f6c-106">Example</span></span>  
 <span data-ttu-id="d5f6c-107">Aşağıdaki kod, tüm örnek gösterir.</span><span class="sxs-lookup"><span data-stu-id="d5f6c-107">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#AnimateMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="d5f6c-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d5f6c-108">See also</span></span>

- [<span data-ttu-id="d5f6c-109">3B Görünümü Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d5f6c-109">Create a 3-D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="d5f6c-110">3B Grafiklere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d5f6c-110">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
