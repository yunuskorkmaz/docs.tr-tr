---
title: 'Nasıl Yapılır: Çizimi 3B Modele Uygula'
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], applying to 3D models
- 3D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
ms.openlocfilehash: 5b10630ab674fa9489cdf7ad53516a680f19da08
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112186"
---
# <a name="how-to-apply-a-drawing-to-a-3d-model"></a><span data-ttu-id="7207c-102">Nasıl Yapılır: Çizimi 3B Modele Uygula</span><span class="sxs-lookup"><span data-stu-id="7207c-102">How to: Apply a Drawing to a 3D Model</span></span>

<span data-ttu-id="7207c-103">Bu örnek, bir <xref:System.Windows.Media.DrawingBrush> 3B <xref:System.Windows.Media.Media3D.Material> modele uygulandığı şeklin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7207c-103">This example shows how to use a <xref:System.Windows.Media.DrawingBrush> as the <xref:System.Windows.Media.Media3D.Material> applied to a 3D model.</span></span>

<span data-ttu-id="7207c-104">Aşağıdaki kod bir <xref:System.Windows.Media.DrawingGroup> . <xref:System.Windows.Media.DrawingBrush></span><span class="sxs-lookup"><span data-stu-id="7207c-104">The following code defines a <xref:System.Windows.Media.DrawingGroup> as the content of a <xref:System.Windows.Media.DrawingBrush>.</span></span>  <span data-ttu-id="7207c-105">3B <xref:System.Windows.Media.DrawingBrush> düzleme <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> <xref:System.Windows.Media.Media3D.DiffuseMaterial> uygulanan özelliği olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="7207c-105">The <xref:System.Windows.Media.DrawingBrush> is set as the <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> property of the <xref:System.Windows.Media.Media3D.DiffuseMaterial> applied to a 3D plane.</span></span>

> [!NOTE]
> <span data-ttu-id="7207c-106">Genellikle, aşağıdaki çizim gibi karmaşık nesneleri ve değerleri yeniden kullanılabilecek ve kodunuzu basitleştirebilecek kaynaklar olarak tanımlamak istenir.</span><span class="sxs-lookup"><span data-stu-id="7207c-106">It is often desirable to define complex objects and values like the drawing below as resources which can be reused and simplify your code.</span></span> <span data-ttu-id="7207c-107">Daha fazla bilgi için [XAML Kaynakları'na](../../../desktop-wpf/fundamentals/xaml-resources-define.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="7207c-107">See [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md) for more information.</span></span>

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]

## <a name="example"></a><span data-ttu-id="7207c-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="7207c-108">Example</span></span>

<span data-ttu-id="7207c-109">Aşağıdaki kod, tüm örneği gösterir.</span><span class="sxs-lookup"><span data-stu-id="7207c-109">The following code shows the entire sample.</span></span>

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]

## <a name="see-also"></a><span data-ttu-id="7207c-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7207c-110">See also</span></span>

- [<span data-ttu-id="7207c-111">XAML Kaynakları</span><span class="sxs-lookup"><span data-stu-id="7207c-111">XAML Resources</span></span>](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [<span data-ttu-id="7207c-112">3B Sahne Oluşturma</span><span class="sxs-lookup"><span data-stu-id="7207c-112">Create a 3D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="7207c-113">Çizim Nesnelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7207c-113">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="7207c-114">3D Grafiklere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7207c-114">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
