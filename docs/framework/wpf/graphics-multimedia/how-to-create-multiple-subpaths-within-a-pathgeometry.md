---
title: 'Nasıl yapılır: Bir PathGeometry İçinde Birden Çok Alt Yol Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- multiple subpaths [WPF]
- graphics [WPF], subpaths
- subpaths [WPF]
ms.assetid: 104a862c-dde2-4e62-ac87-80660dd1681c
ms.openlocfilehash: 286075448cd6a343f8a7b15b2b5005f840f68e1d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59111754"
---
# <a name="how-to-create-multiple-subpaths-within-a-pathgeometry"></a><span data-ttu-id="98c3e-102">Nasıl yapılır: Bir PathGeometry İçinde Birden Çok Alt Yol Oluşturma</span><span class="sxs-lookup"><span data-stu-id="98c3e-102">How to: Create Multiple Subpaths Within a PathGeometry</span></span>
<span data-ttu-id="98c3e-103">Bu örnek, birden çok alt yol oluşturma işlemini gösterir bir <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="98c3e-103">This example shows how to create multiple subpaths in a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="98c3e-104">Birden çok alt yol oluşturma için oluşturduğunuz bir <xref:System.Windows.Media.PathFigure> için her alt yol.</span><span class="sxs-lookup"><span data-stu-id="98c3e-104">To create multiple subpaths, you create a <xref:System.Windows.Media.PathFigure> for each subpath.</span></span>  
  
## <a name="example"></a><span data-ttu-id="98c3e-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="98c3e-105">Example</span></span>  
 <span data-ttu-id="98c3e-106">Aşağıdaki örnek, iki alt, her biri bir üçgen oluşturur.</span><span class="sxs-lookup"><span data-stu-id="98c3e-106">The following example creates two subpaths, each one a triangle.</span></span>  
  
 [!code-xaml[GeometrySample#38](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#38)]  
  
 <span data-ttu-id="98c3e-107">Aşağıdaki örnek, kullanarak birden çok alt yol oluşturma işlemi gösterilmektedir bir <xref:System.Windows.Shapes.Path> ve [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] öznitelik sözdizimi.</span><span class="sxs-lookup"><span data-stu-id="98c3e-107">The following example shows how to create multiple subpaths by using a <xref:System.Windows.Shapes.Path> and [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] attribute syntax.</span></span> <span data-ttu-id="98c3e-108">Her `M` çizen bir üçgen her iki alt örneği oluşturur, böylece yeni bir alt oluşturur.</span><span class="sxs-lookup"><span data-stu-id="98c3e-108">Each `M` creates a new subpath so that the example creates two subpaths that each draw a triangle.</span></span>  
  
 [!code-xaml[GeometrySample#58](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#58)]  
  
 <span data-ttu-id="98c3e-109">(Aslında bu öznitelik sözdizimi oluşturan Not bir <xref:System.Windows.Media.StreamGeometry>, daha basit sürümü bir <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="98c3e-109">(Note that this attribute syntax actually creates a <xref:System.Windows.Media.StreamGeometry>, a lighter-weight version of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="98c3e-110">Daha fazla bilgi için [yol işaretleme söz dizimi](path-markup-syntax.md) sayfası.)</span><span class="sxs-lookup"><span data-stu-id="98c3e-110">For more information, see the [Path Markup Syntax](path-markup-syntax.md) page.)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98c3e-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="98c3e-111">See also</span></span>

- [<span data-ttu-id="98c3e-112">Geometriye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="98c3e-112">Geometry Overview</span></span>](geometry-overview.md)
