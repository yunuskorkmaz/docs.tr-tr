---
title: "Nasıl yapılır: Elips Yay Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [WPF], elliptical arcs
- elliptical arcs [WPF], creating
- arcs [WPF], elliptical
ms.assetid: 3dcfe502-3485-45de-99fb-d53a1367c484
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: eeb93cefd2e55e80f27922feab788698653f405e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-an-elliptical-arc"></a><span data-ttu-id="05274-102">Nasıl yapılır: Elips Yay Oluşturma</span><span class="sxs-lookup"><span data-stu-id="05274-102">How to: Create an Elliptical Arc</span></span>
<span data-ttu-id="05274-103">Bu örnek nasıl elips yay çizileceğini gösterir. Elips yay oluşturmak üzere kullanmanız <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, ve <xref:System.Windows.Media.ArcSegment> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="05274-103">This example shows how to draw an elliptical arc. To create an elliptical arc, use the <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, and <xref:System.Windows.Media.ArcSegment> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="05274-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="05274-104">Example</span></span>  
 <span data-ttu-id="05274-105">Aşağıdaki örneklerde, elips yay (10,100) dan (200,100) çizilir.</span><span class="sxs-lookup"><span data-stu-id="05274-105">In the following examples, an elliptical arc is drawn from (10,100) to (200,100).</span></span> <span data-ttu-id="05274-106">Yayı sahip bir <xref:System.Windows.Media.ArcSegment.Size%2A> 100 50 aygıttan bağımsız piksel tarafından bir <xref:System.Windows.Media.ArcSegment.RotationAngle%2A> 45 derece bir <xref:System.Windows.Media.ArcSegment.IsLargeArc%2A> ayarıyla `true`ve bir <xref:System.Windows.Media.ArcSegment.SweepDirection%2A> , <xref:System.Windows.Media.SweepDirection.Counterclockwise>.</span><span class="sxs-lookup"><span data-stu-id="05274-106">The arc has a <xref:System.Windows.Media.ArcSegment.Size%2A> of 100 by 50 device-independent pixels, a <xref:System.Windows.Media.ArcSegment.RotationAngle%2A> of 45 degrees, an <xref:System.Windows.Media.ArcSegment.IsLargeArc%2A> setting of `true`, and a <xref:System.Windows.Media.ArcSegment.SweepDirection%2A> of <xref:System.Windows.Media.SweepDirection.Counterclockwise>.</span></span>  
  
 <span data-ttu-id="05274-107">[xaml]</span><span class="sxs-lookup"><span data-stu-id="05274-107">[xaml]</span></span>  
  
 <span data-ttu-id="05274-108">İçinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], bir yolu açıklamak için öznitelik sözdizimini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05274-108">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you can use attribute syntax to describe a path.</span></span>  
  
 [!code-xaml[GeometrySample#56](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#56)]  
  
 <span data-ttu-id="05274-109">[xaml]</span><span class="sxs-lookup"><span data-stu-id="05274-109">[xaml]</span></span>  
  
 <span data-ttu-id="05274-110">(Bu öznitelik sözdizimi gerçekte oluşturur Not bir <xref:System.Windows.Media.StreamGeometry>, hafifletilmiş sürümü bir <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="05274-110">(Note that this attribute syntax actually creates a <xref:System.Windows.Media.StreamGeometry>, a lighter-weight version of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="05274-111">Daha fazla bilgi için bkz: [biçimlendirme sözdizimi yolu](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) sayfası.)</span><span class="sxs-lookup"><span data-stu-id="05274-111">For more information, see the [Path Markup Syntax](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) page.)</span></span>  
  
 <span data-ttu-id="05274-112">İçinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], açıkça nesne etiketleri kullanılarak elips yay çizebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05274-112">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can also draw an elliptical arc by explicitly using object tags.</span></span> <span data-ttu-id="05274-113">Aşağıdaki önceki eşdeğerdir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirme.</span><span class="sxs-lookup"><span data-stu-id="05274-113">The following is equivalent to the preceding [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup.</span></span>  
  
 [!code-xaml[GeometrySample#36](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#36)]  
  
 <span data-ttu-id="05274-114">Bu örnek daha büyük bir örneğin parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="05274-114">This example is part of a larger sample.</span></span> <span data-ttu-id="05274-115">Tam bir örnek için bkz: [geometri örneği](http://go.microsoft.com/fwlink/?LinkID=159989).</span><span class="sxs-lookup"><span data-stu-id="05274-115">For the complete sample, see the [Geometries Sample](http://go.microsoft.com/fwlink/?LinkID=159989).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05274-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="05274-116">See Also</span></span>  
 [<span data-ttu-id="05274-117">İkinci dereceden Bezier eğrisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="05274-117">Create a Quadratic Bezier Curve</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md)  
 [<span data-ttu-id="05274-118">Küp Bezier eğrisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="05274-118">Create a Cubic Bezier Curve</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md)
