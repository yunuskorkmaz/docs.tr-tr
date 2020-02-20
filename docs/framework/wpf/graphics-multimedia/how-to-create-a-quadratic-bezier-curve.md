---
title: 'Nasıl yapılır: İkinci Dereceden Bezier Eğrisi Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- Bezier curves [WPF], creating
- quadratic Bezier curves [WPF], creating
- graphics [WPF], quadratic Bezier curves
ms.assetid: cd8fca4a-504e-4fd8-92ea-2969065a6e02
ms.openlocfilehash: caaf967b7cb5447d86dd031beeb16195413b0393
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452077"
---
# <a name="how-to-create-a-quadratic-bezier-curve"></a><span data-ttu-id="f522f-102">Nasıl yapılır: İkinci Dereceden Bezier Eğrisi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f522f-102">How to: Create a Quadratic Bezier Curve</span></span>
<span data-ttu-id="f522f-103">Bu örnek, ikinci dereceden Bezier eğrisinin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f522f-103">This example shows how to create a quadratic Bezier curve.</span></span>  <span data-ttu-id="f522f-104">İkinci dereceden Bezier eğrisi oluşturmak için <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>ve <xref:System.Windows.Media.QuadraticBezierSegment> sınıflarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="f522f-104">To create a quadratic Bezier curve, use the <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, and <xref:System.Windows.Media.QuadraticBezierSegment> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f522f-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="f522f-105">Example</span></span>  
 <span data-ttu-id="f522f-106">Aşağıdaki örneklerde, (10.100) ile (300.100) arasında bir ikinci dereceden Bezier eğrisi çizilir.</span><span class="sxs-lookup"><span data-stu-id="f522f-106">In the following examples, a quadratic Bezier curve is drawn from (10,100) to (300,100).</span></span> <span data-ttu-id="f522f-107">Eğrinin bir denetim noktası (200.200) vardır.</span><span class="sxs-lookup"><span data-stu-id="f522f-107">The curve has a control point of (200,200).</span></span>  
  
 <span data-ttu-id="f522f-108">xaml</span><span class="sxs-lookup"><span data-stu-id="f522f-108">[xaml]</span></span>  
  
 <span data-ttu-id="f522f-109">[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], bir yolu anlatmak için öznitelik sözdizimini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f522f-109">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you can use attribute syntax to describe a path.</span></span>  
  
 [!code-xaml[GeometrySample#54](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#54)]  
  
 <span data-ttu-id="f522f-110">xaml</span><span class="sxs-lookup"><span data-stu-id="f522f-110">[xaml]</span></span>  
  
 <span data-ttu-id="f522f-111">(Bu öznitelik sözdiziminin aslında bir <xref:System.Windows.Media.PathGeometry>daha hafif bir sürümünü <xref:System.Windows.Media.StreamGeometry>oluşturduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f522f-111">(Note that this attribute syntax actually creates a <xref:System.Windows.Media.StreamGeometry>, a lighter-weight version of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="f522f-112">Daha fazla bilgi için [yol biçimlendirme sözdizimi](path-markup-syntax.md) sayfasına bakın.)</span><span class="sxs-lookup"><span data-stu-id="f522f-112">For more information, see the [Path Markup Syntax](path-markup-syntax.md) page.)</span></span>  
  
 <span data-ttu-id="f522f-113">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], nesne öğesi söz dizimini kullanarak ikinci dereceden Bezier eğrisi da çizebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f522f-113">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you may also draw a quadratic Bezier curve using object element syntax.</span></span> <span data-ttu-id="f522f-114">Aşağıdaki, önceki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] örneğine eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="f522f-114">The following is equivalent to the previous [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example.</span></span>  
  
 [!code-xaml[GeometrySample#34](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 <span data-ttu-id="f522f-115">Bu örnek, daha büyük bir örnek parçasıdır; Tüm örnek için bkz. [geometriler örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span><span class="sxs-lookup"><span data-stu-id="f522f-115">This example is part of larger sample; for the complete sample, see the [Geometries Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f522f-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f522f-116">See also</span></span>

- [<span data-ttu-id="f522f-117">Elips Yay Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f522f-117">Create an Elliptical Arc</span></span>](how-to-create-an-elliptical-arc.md)
- [<span data-ttu-id="f522f-118">Üçüncü Dereceden Bezier Eğrisi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f522f-118">Create a Cubic Bezier Curve</span></span>](how-to-create-a-cubic-bezier-curve.md)
