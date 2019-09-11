---
title: 'Nasıl yapılır: 3B Modeline Çizim Uygulama'
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], applying to 3-D models
- 3-D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
ms.openlocfilehash: 14470d0adeb948ea46a0720b5713c20fb7d8e6d8
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855873"
---
# <a name="how-to-apply-a-drawing-to-a-3-d-model"></a><span data-ttu-id="65fb4-102">Nasıl yapılır: 3B Modeline Çizim Uygulama</span><span class="sxs-lookup"><span data-stu-id="65fb4-102">How to: Apply a Drawing to a 3-D Model</span></span>

<span data-ttu-id="65fb4-103">Bu örnek, <xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Media.Media3D.Material> bir 3-b model için uygulanan olarak nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="65fb4-103">This example shows how to use a <xref:System.Windows.Media.DrawingBrush> as the <xref:System.Windows.Media.Media3D.Material> applied to a 3-D model.</span></span>

<span data-ttu-id="65fb4-104">Aşağıdaki kod, bir <xref:System.Windows.Media.DrawingGroup> <xref:System.Windows.Media.DrawingBrush>öğesinin içeriği olarak bir tanımlar.</span><span class="sxs-lookup"><span data-stu-id="65fb4-104">The following code defines a <xref:System.Windows.Media.DrawingGroup> as the content of a <xref:System.Windows.Media.DrawingBrush>.</span></span>  <span data-ttu-id="65fb4-105">, <xref:System.Windows.Media.DrawingBrush> 3-b düzlemi <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> için <xref:System.Windows.Media.Media3D.DiffuseMaterial> uygulanan özelliği olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="65fb4-105">The <xref:System.Windows.Media.DrawingBrush> is set as the <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> property of the <xref:System.Windows.Media.Media3D.DiffuseMaterial> applied to a 3-D plane.</span></span>

> [!NOTE]
> <span data-ttu-id="65fb4-106">Daha önce yeniden kullanılabilen ve kodunuzu basitleştirecek kaynaklar olarak aşağıdaki çizimde gösterildiği gibi karmaşık nesne ve değerleri tanımlamak genellikle tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="65fb4-106">It is often desirable to define complex objects and values like the drawing below as resources which can be reused and simplify your code.</span></span> <span data-ttu-id="65fb4-107">Daha fazla bilgi için bkz. [xaml kaynakları](../advanced/xaml-resources.md) .</span><span class="sxs-lookup"><span data-stu-id="65fb4-107">See [XAML Resources](../advanced/xaml-resources.md) for more information.</span></span>

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]

## <a name="example"></a><span data-ttu-id="65fb4-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="65fb4-108">Example</span></span>

<span data-ttu-id="65fb4-109">Aşağıdaki kod, tüm örneği gösterir.</span><span class="sxs-lookup"><span data-stu-id="65fb4-109">The following code shows the entire sample.</span></span>

[!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]

## <a name="see-also"></a><span data-ttu-id="65fb4-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="65fb4-110">See also</span></span>

- [<span data-ttu-id="65fb4-111">XAML Kaynakları</span><span class="sxs-lookup"><span data-stu-id="65fb4-111">XAML Resources</span></span>](../advanced/xaml-resources.md)
- [<span data-ttu-id="65fb4-112">3B Görünümü Oluşturma</span><span class="sxs-lookup"><span data-stu-id="65fb4-112">Create a 3-D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="65fb4-113">Çizim Nesnelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="65fb4-113">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="65fb4-114">3B Grafiklere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="65fb4-114">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
