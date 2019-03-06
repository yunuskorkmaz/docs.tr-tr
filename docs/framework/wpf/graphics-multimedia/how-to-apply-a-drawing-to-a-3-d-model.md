---
title: 'Nasıl yapılır: 3B Modeline Çizim Uygulama'
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], applying to 3-D models
- 3-D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
ms.openlocfilehash: cfd133b04e0c04b4a502d2466e67685700e3f408
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57368927"
---
# <a name="how-to-apply-a-drawing-to-a-3-d-model"></a><span data-ttu-id="3bf57-102">Nasıl yapılır: 3B Modeline Çizim Uygulama</span><span class="sxs-lookup"><span data-stu-id="3bf57-102">How to: Apply a Drawing to a 3-D Model</span></span>
<span data-ttu-id="3bf57-103">Bu örnek nasıl kullanılacağını gösterir. bir <xref:System.Windows.Media.DrawingBrush> olarak <xref:System.Windows.Media.Media3D.Material> uygulanan bir [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] modeli.</span><span class="sxs-lookup"><span data-stu-id="3bf57-103">This example shows how to use a <xref:System.Windows.Media.DrawingBrush> as the <xref:System.Windows.Media.Media3D.Material> applied to a [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] model.</span></span>  
  
 <span data-ttu-id="3bf57-104">Aşağıdaki kodu tanımlayan bir <xref:System.Windows.Media.DrawingGroup> içeriği olarak bir <xref:System.Windows.Media.DrawingBrush>.</span><span class="sxs-lookup"><span data-stu-id="3bf57-104">The following code defines a <xref:System.Windows.Media.DrawingGroup> as the content of a <xref:System.Windows.Media.DrawingBrush>.</span></span>  <span data-ttu-id="3bf57-105"><xref:System.Windows.Media.DrawingBrush> Olarak ayarlandığından <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> özelliği <xref:System.Windows.Media.Media3D.DiffuseMaterial> uygulanan bir [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] düzlemi.</span><span class="sxs-lookup"><span data-stu-id="3bf57-105">The <xref:System.Windows.Media.DrawingBrush> is set as the <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> property of the <xref:System.Windows.Media.Media3D.DiffuseMaterial> applied to a [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] plane.</span></span>  
  
 <span data-ttu-id="3bf57-106">**Not:** Genellikle karmaşık nesneler ve değerleri gibi aşağıdaki çizim, kodunuzu basitleştirerek ve yeniden kullanılabilir kaynaklar olarak tanımlamak için tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="3bf57-106">**Note:** It is often desirable to define complex objects and values like the drawing below as resources which can be reused and simplify your code.</span></span> <span data-ttu-id="3bf57-107">Bkz: [XAML kaynakları](../advanced/xaml-resources.md) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="3bf57-107">See [XAML Resources](../advanced/xaml-resources.md) for more information.</span></span>  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]  
  
## <a name="example"></a><span data-ttu-id="3bf57-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="3bf57-108">Example</span></span>  
 <span data-ttu-id="3bf57-109">Aşağıdaki kod, tüm örnek gösterir.</span><span class="sxs-lookup"><span data-stu-id="3bf57-109">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="3bf57-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3bf57-110">See also</span></span>
- [<span data-ttu-id="3bf57-111">XAML Kaynakları</span><span class="sxs-lookup"><span data-stu-id="3bf57-111">XAML Resources</span></span>](../advanced/xaml-resources.md)
- [<span data-ttu-id="3bf57-112">3B Görünümü Oluşturma</span><span class="sxs-lookup"><span data-stu-id="3bf57-112">Create a 3-D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="3bf57-113">Çizim Nesnelerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3bf57-113">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="3bf57-114">3B Grafiklere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3bf57-114">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
