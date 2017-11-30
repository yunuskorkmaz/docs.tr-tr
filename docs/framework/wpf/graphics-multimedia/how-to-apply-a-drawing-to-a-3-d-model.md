---
title: "Nasıl yapılır: 3B Modeline Çizim Uygulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drawings [WPF], applying to 3-D models
- 3-D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a44607498c6870a598122f41bf2b7ddc5968c61d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-apply-a-drawing-to-a-3-d-model"></a><span data-ttu-id="c43df-102">Nasıl yapılır: 3B Modeline Çizim Uygulama</span><span class="sxs-lookup"><span data-stu-id="c43df-102">How to: Apply a Drawing to a 3-D Model</span></span>
<span data-ttu-id="c43df-103">Bu örnek nasıl kullanılacağını gösteren bir <xref:System.Windows.Media.DrawingBrush> olarak <xref:System.Windows.Media.Media3D.Material> uygulanan bir [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] modeli.</span><span class="sxs-lookup"><span data-stu-id="c43df-103">This example shows how to use a <xref:System.Windows.Media.DrawingBrush> as the <xref:System.Windows.Media.Media3D.Material> applied to a [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] model.</span></span>  
  
 <span data-ttu-id="c43df-104">Aşağıdaki kodu tanımlayan bir <xref:System.Windows.Media.DrawingGroup> içeriği olarak bir <xref:System.Windows.Media.DrawingBrush>.</span><span class="sxs-lookup"><span data-stu-id="c43df-104">The following code defines a <xref:System.Windows.Media.DrawingGroup> as the content of a <xref:System.Windows.Media.DrawingBrush>.</span></span>  <span data-ttu-id="c43df-105"><xref:System.Windows.Media.DrawingBrush> Olarak ayarlanmış olan <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> özelliği <xref:System.Windows.Media.Media3D.DiffuseMaterial> uygulanan bir [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] düzlemi.</span><span class="sxs-lookup"><span data-stu-id="c43df-105">The <xref:System.Windows.Media.DrawingBrush> is set as the <xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A> property of the <xref:System.Windows.Media.Media3D.DiffuseMaterial> applied to a [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] plane.</span></span>  
  
 <span data-ttu-id="c43df-106">**Not:** genellikle karmaşık nesneler ve değerleri aşağıdaki çizim gibi yeniden kullanılabilir ve kodunuzu basitleştiren kaynaklar olarak tanımlamak için tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="c43df-106">**Note:** It is often desirable to define complex objects and values like the drawing below as resources which can be reused and simplify your code.</span></span> <span data-ttu-id="c43df-107">Bkz: [XAML kaynakları](../../../../docs/framework/wpf/advanced/xaml-resources.md) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="c43df-107">See [XAML Resources](../../../../docs/framework/wpf/advanced/xaml-resources.md) for more information.</span></span>  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]  
  
## <a name="example"></a><span data-ttu-id="c43df-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="c43df-108">Example</span></span>  
 <span data-ttu-id="c43df-109">Aşağıdaki kod tüm örneği gösterir.</span><span class="sxs-lookup"><span data-stu-id="c43df-109">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="c43df-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c43df-110">See Also</span></span>  
 [<span data-ttu-id="c43df-111">XAML kaynakları</span><span class="sxs-lookup"><span data-stu-id="c43df-111">XAML Resources</span></span>](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [<span data-ttu-id="c43df-112">3B Sahne oluşturma</span><span class="sxs-lookup"><span data-stu-id="c43df-112">Create a 3-D Scene</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)  
 [<span data-ttu-id="c43df-113">Çizim nesnelerine genel bakış</span><span class="sxs-lookup"><span data-stu-id="c43df-113">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [<span data-ttu-id="c43df-114">3B Grafiklere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c43df-114">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
