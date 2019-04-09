---
title: 'Nasıl yapılır: İkinci Dereceden Bezier Eğrisi Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- Bezier curves [WPF], creating
- quadratic Bezier curves [WPF], creating
- graphics [WPF], quadratic Bezier curves
ms.assetid: cd8fca4a-504e-4fd8-92ea-2969065a6e02
ms.openlocfilehash: a0b2145b4a5bba11186419fe680f2eca41949d6a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59134881"
---
# <a name="how-to-create-a-quadratic-bezier-curve"></a><span data-ttu-id="13dbe-102">Nasıl yapılır: İkinci Dereceden Bezier Eğrisi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="13dbe-102">How to: Create a Quadratic Bezier Curve</span></span>
<span data-ttu-id="13dbe-103">Bu örnekte, ikinci dereceden Bezier eğrisi oluşturma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="13dbe-103">This example shows how to create a quadratic Bezier curve.</span></span>  <span data-ttu-id="13dbe-104">İkinci dereceden Bezier eğrisi oluşturmak için kullanın <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, ve <xref:System.Windows.Media.QuadraticBezierSegment> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="13dbe-104">To create a quadratic Bezier curve, use the <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, and <xref:System.Windows.Media.QuadraticBezierSegment> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13dbe-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="13dbe-105">Example</span></span>  
 <span data-ttu-id="13dbe-106">Aşağıdaki örneklerde, ikinci dereceden Bezier eğrisi (300,100) için (10,100) çizilir.</span><span class="sxs-lookup"><span data-stu-id="13dbe-106">In the following examples, a quadratic Bezier curve is drawn from (10,100) to (300,100).</span></span> <span data-ttu-id="13dbe-107">Eğriyi (200,200) bir denetim noktası var.</span><span class="sxs-lookup"><span data-stu-id="13dbe-107">The curve has a control point of (200,200).</span></span>  
  
 <span data-ttu-id="13dbe-108">[xaml]</span><span class="sxs-lookup"><span data-stu-id="13dbe-108">[xaml]</span></span>  
  
 <span data-ttu-id="13dbe-109">İçinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], öznitelik sözdizimi bir yolunu tanımlamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="13dbe-109">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you can use attribute syntax to describe a path.</span></span>  
  
 [!code-xaml[GeometrySample#54](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#54)]  
  
 <span data-ttu-id="13dbe-110">[xaml]</span><span class="sxs-lookup"><span data-stu-id="13dbe-110">[xaml]</span></span>  
  
 <span data-ttu-id="13dbe-111">(Aslında bu öznitelik sözdizimi oluşturan Not bir <xref:System.Windows.Media.StreamGeometry>, daha basit sürümü bir <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="13dbe-111">(Note that this attribute syntax actually creates a <xref:System.Windows.Media.StreamGeometry>, a lighter-weight version of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="13dbe-112">Daha fazla bilgi için [yol işaretleme söz dizimi](path-markup-syntax.md) sayfası.)</span><span class="sxs-lookup"><span data-stu-id="13dbe-112">For more information, see the [Path Markup Syntax](path-markup-syntax.md) page.)</span></span>  
  
 <span data-ttu-id="13dbe-113">İçinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], nesne öğesi sözdizimi kullanarak ikinci dereceden Bezier eğrisi da çizebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="13dbe-113">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you may also draw a quadratic Bezier curve using object element syntax.</span></span> <span data-ttu-id="13dbe-114">Aşağıdaki önceki eşdeğerdir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] örnek.</span><span class="sxs-lookup"><span data-stu-id="13dbe-114">The following is equivalent to the previous [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example.</span></span>  
  
 [!code-xaml[GeometrySample#34](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 <span data-ttu-id="13dbe-115">Bu örnek, daha büyük örnek bir parçasıdır; tam bir örnek için bkz. [geometri örneği](https://go.microsoft.com/fwlink/?LinkID=159989).</span><span class="sxs-lookup"><span data-stu-id="13dbe-115">This example is part of larger sample; for the complete sample, see the [Geometries Sample](https://go.microsoft.com/fwlink/?LinkID=159989).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13dbe-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13dbe-116">See also</span></span>

- [<span data-ttu-id="13dbe-117">Elips Yay Oluşturma</span><span class="sxs-lookup"><span data-stu-id="13dbe-117">Create an Elliptical Arc</span></span>](how-to-create-an-elliptical-arc.md)
- [<span data-ttu-id="13dbe-118">Üçüncü Dereceden Bezier Eğrisi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="13dbe-118">Create a Cubic Bezier Curve</span></span>](how-to-create-a-cubic-bezier-curve.md)
