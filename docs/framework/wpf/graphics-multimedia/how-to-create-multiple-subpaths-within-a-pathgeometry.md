---
title: 'Nasıl yapılır: Bir PathGeometry İçinde Birden Çok Alt Yol Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- multiple subpaths [WPF]
- graphics [WPF], subpaths
- subpaths [WPF]
ms.assetid: 104a862c-dde2-4e62-ac87-80660dd1681c
ms.openlocfilehash: 5b129b1bacb5dc2cba87376e8df70e115a5ebd72
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559338"
---
# <a name="how-to-create-multiple-subpaths-within-a-pathgeometry"></a><span data-ttu-id="8d747-102">Nasıl yapılır: Bir PathGeometry İçinde Birden Çok Alt Yol Oluşturma</span><span class="sxs-lookup"><span data-stu-id="8d747-102">How to: Create Multiple Subpaths Within a PathGeometry</span></span>
<span data-ttu-id="8d747-103">Bu örnek, birden çok alt oluşturulacağını gösterir bir <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="8d747-103">This example shows how to create multiple subpaths in a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="8d747-104">Birden çok alt yolların oluşturmak için oluşturduğunuz bir <xref:System.Windows.Media.PathFigure> her alt yolu için.</span><span class="sxs-lookup"><span data-stu-id="8d747-104">To create multiple subpaths, you create a <xref:System.Windows.Media.PathFigure> for each subpath.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d747-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="8d747-105">Example</span></span>  
 <span data-ttu-id="8d747-106">Aşağıdaki örnekte, iki alt, her biri bir üçgen oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8d747-106">The following example creates two subpaths, each one a triangle.</span></span>  
  
 [!code-xaml[GeometrySample#38](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#38)]  
  
 <span data-ttu-id="8d747-107">Aşağıdaki örnek kullanarak birden çok alt yolların oluşturulacağını gösterir bir <xref:System.Windows.Shapes.Path> ve [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] öznitelik sözdizimi.</span><span class="sxs-lookup"><span data-stu-id="8d747-107">The following example shows how to create multiple subpaths by using a <xref:System.Windows.Shapes.Path> and [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] attribute syntax.</span></span> <span data-ttu-id="8d747-108">Her `M` her bir üçgen çizmek iki alt örneği oluşturur, böylece yeni bir alt yolu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8d747-108">Each `M` creates a new subpath so that the example creates two subpaths that each draw a triangle.</span></span>  
  
 [!code-xaml[GeometrySample#58](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#58)]  
  
 <span data-ttu-id="8d747-109">(Bu öznitelik sözdizimi gerçekte oluşturur Not bir <xref:System.Windows.Media.StreamGeometry>, hafifletilmiş sürümü bir <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="8d747-109">(Note that this attribute syntax actually creates a <xref:System.Windows.Media.StreamGeometry>, a lighter-weight version of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="8d747-110">Daha fazla bilgi için bkz: [biçimlendirme sözdizimi yolu](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) sayfası.)</span><span class="sxs-lookup"><span data-stu-id="8d747-110">For more information, see the [Path Markup Syntax](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) page.)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d747-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8d747-111">See Also</span></span>  
 [<span data-ttu-id="8d747-112">Geometriye Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8d747-112">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)
