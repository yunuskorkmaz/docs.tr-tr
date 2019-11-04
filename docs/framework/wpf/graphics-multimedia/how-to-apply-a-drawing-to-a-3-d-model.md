---
title: 'Nasıl yapılır: 3B Modeline Çizim Uygulama'
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], applying to 3-D models
- 3-D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
ms.openlocfilehash: 311a3ac1d9fa219a3a365d506d9d0c3e8b6bc229
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459374"
---
# <a name="how-to-apply-a-drawing-to-a-3-d-model"></a><span data-ttu-id="cc867-102">Nasıl yapılır: 3B Modeline Çizim Uygulama</span><span class="sxs-lookup"><span data-stu-id="cc867-102">How to: Apply a Drawing to a 3-D Model</span></span>

<span data-ttu-id="cc867-103">Bu örnek, bir <xref:System.Windows.Media.DrawingBrush> bir 3-b modele uygulanan <xref:System.Windows.Media.Media3D.Material> olarak nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="cc867-103">This example shows how to use a <xref:System.Windows.Media.DrawingBrush> as the <xref:System.Windows.Media.Media3D.Material> applied to a 3-D model.</span></span>

<span data-ttu-id="cc867-104">Aşağıdaki kod, bir <xref:System.Windows.Media.DrawingBrush>içeriği olarak bir <xref:System.Windows.Media.DrawingGroup> tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cc867-104">The following code defines a <xref:System.Windows.Media.DrawingGroup> as the content of a <xref:System.Windows.Media.DrawingBrush>.</span></span>  <span data-ttu-id="cc867-105"><xref:System.Windows.Media.DrawingBrush>, 3-b düzlemine uygulanan <xref:System.Windows.Media.Media3D.DiffuseMaterial> <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> özelliği olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="cc867-105">The <xref:System.Windows.Media.DrawingBrush> is set as the <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> property of the <xref:System.Windows.Media.Media3D.DiffuseMaterial> applied to a 3-D plane.</span></span>

> [!NOTE]
> <span data-ttu-id="cc867-106">Daha önce yeniden kullanılabilen ve kodunuzu basitleştirecek kaynaklar olarak aşağıdaki çizimde gösterildiği gibi karmaşık nesne ve değerleri tanımlamak genellikle tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="cc867-106">It is often desirable to define complex objects and values like the drawing below as resources which can be reused and simplify your code.</span></span> <span data-ttu-id="cc867-107">Daha fazla bilgi için bkz. [xaml kaynakları](../../../desktop-wpf/fundamentals/xaml-resources-define.md) .</span><span class="sxs-lookup"><span data-stu-id="cc867-107">See [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md) for more information.</span></span>

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]

## <a name="example"></a><span data-ttu-id="cc867-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="cc867-108">Example</span></span>

<span data-ttu-id="cc867-109">Aşağıdaki kod, tüm örneği gösterir.</span><span class="sxs-lookup"><span data-stu-id="cc867-109">The following code shows the entire sample.</span></span>

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]

## <a name="see-also"></a><span data-ttu-id="cc867-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cc867-110">See also</span></span>

- [<span data-ttu-id="cc867-111">XAML Kaynakları</span><span class="sxs-lookup"><span data-stu-id="cc867-111">XAML Resources</span></span>](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="cc867-112">3B Görünümü Oluşturma</span><span class="sxs-lookup"><span data-stu-id="cc867-112">Create a 3-D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="cc867-113">Çizim Nesnelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="cc867-113">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="cc867-114">3B Grafiklere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="cc867-114">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
