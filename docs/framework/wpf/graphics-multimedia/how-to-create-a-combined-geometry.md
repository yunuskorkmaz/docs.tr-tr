---
title: 'Nasıl yapılır: Birleşik Geometri Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- combining geometries [WPF]
- graphics [WPF], combining geometries
- geometries [WPF], combining
ms.assetid: 54c3277c-6b6e-4b25-91be-fda0bbc706b4
ms.openlocfilehash: 107e0342b822633ccb4f51f256c121cc80c297f4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561127"
---
# <a name="how-to-create-a-combined-geometry"></a><span data-ttu-id="3672f-102">Nasıl yapılır: Birleşik Geometri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="3672f-102">How to: Create a Combined Geometry</span></span>
<span data-ttu-id="3672f-103">Bu örnek nasıl geometri birleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3672f-103">This example shows how to combine geometries.</span></span> <span data-ttu-id="3672f-104">İki geometri birleştirmek için kullanın bir <xref:System.Windows.Media.CombinedGeometry> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="3672f-104">To combine two geometries, use a <xref:System.Windows.Media.CombinedGeometry> object.</span></span> <span data-ttu-id="3672f-105">Ayarlama, <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> ve <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> birleştirmek ve ayarlamak için iki geometri özelliklerle <xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A> geometri birlikte nasıl birleştirileceğini belirleyen, özellik için `Union`, `Intersect`, `Exclude`, veya `Xor`.</span><span class="sxs-lookup"><span data-stu-id="3672f-105">Set its <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> properties  with the two geometries to combine, and set the <xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A> property, which determines how the geometries will be combined together, to `Union`, `Intersect`, `Exclude`, or `Xor`.</span></span>  
  
 <span data-ttu-id="3672f-106">İki veya daha fazla geometri bileşik geometri oluşturmak için bir <xref:System.Windows.Media.GeometryGroup>.</span><span class="sxs-lookup"><span data-stu-id="3672f-106">To create a composite geometry from two or more geometries, use a <xref:System.Windows.Media.GeometryGroup>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3672f-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="3672f-107">Example</span></span>  
 <span data-ttu-id="3672f-108">Aşağıdaki örnekte, bir <xref:System.Windows.Media.CombinedGeometry> geometri birleştirme modu ile tanımlanan `Exclude`.</span><span class="sxs-lookup"><span data-stu-id="3672f-108">In the following example, a <xref:System.Windows.Media.CombinedGeometry> is defined with a geometry combine mode of `Exclude`.</span></span>  <span data-ttu-id="3672f-109">Her ikisi de <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> ve <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> daireler aynı RADIUS ancak merkezleri uzaklıkları 50 tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="3672f-109">Both <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and the <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> are defined as circles of the same radius, but with centers offset by 50.</span></span>  
  
 [!code-xaml[GeometrySample#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#21)]  
  
 <span data-ttu-id="3672f-110">![Birleştirme modu sonuçları tut](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-exclude.PNG "mil_task_combined_geometry_exclude")</span><span class="sxs-lookup"><span data-stu-id="3672f-110">![Results of the Exclude combine mode](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-exclude.PNG "mil_task_combined_geometry_exclude")</span></span>  
<span data-ttu-id="3672f-111">Birleşik Geometri dışlama</span><span class="sxs-lookup"><span data-stu-id="3672f-111">Combined Geometry Exclude</span></span>  
  
 <span data-ttu-id="3672f-112">Aşağıdaki biçimlendirmede bir <xref:System.Windows.Media.CombinedGeometry> birleştirme modu ile tanımlanan `Intersect`.</span><span class="sxs-lookup"><span data-stu-id="3672f-112">In the following markup, a <xref:System.Windows.Media.CombinedGeometry> is defined with a combine mode of `Intersect`.</span></span>  <span data-ttu-id="3672f-113">Her ikisi de <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> ve <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> daireler aynı RADIUS ancak merkezleri uzaklıkları 50 tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="3672f-113">Both <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and the <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> are defined as circles of the same radius, but with centers offset by 50.</span></span>  
  
 [!code-xaml[GeometrySample#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#22)]  
  
 <span data-ttu-id="3672f-114">![Birleştirme modu INTERSECT sonuçları](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-intersect.PNG "mil_task_combined_geometry_intersect")</span><span class="sxs-lookup"><span data-stu-id="3672f-114">![Results of the Intersect combine mode](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-intersect.PNG "mil_task_combined_geometry_intersect")</span></span>  
<span data-ttu-id="3672f-115">Birleşik Geometri kesişimi</span><span class="sxs-lookup"><span data-stu-id="3672f-115">Combined Geometry Intersect</span></span>  
  
 <span data-ttu-id="3672f-116">Aşağıdaki biçimlendirmede bir <xref:System.Windows.Media.CombinedGeometry> birleştirme modu ile tanımlanan `Union`.</span><span class="sxs-lookup"><span data-stu-id="3672f-116">In the following markup, a <xref:System.Windows.Media.CombinedGeometry> is defined with a combine mode of `Union`.</span></span>  <span data-ttu-id="3672f-117">Her ikisi de <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> ve <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> daireler aynı RADIUS ancak merkezleri uzaklıkları 50 tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="3672f-117">Both <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and the <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> are defined as circles of the same radius, but with centers offset by 50.</span></span>  
  
 [!code-xaml[GeometrySample#23](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#23)]  
  
 <span data-ttu-id="3672f-118">![Birleştirme modu UNION sonuçları](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")</span><span class="sxs-lookup"><span data-stu-id="3672f-118">![Results of the Union combine mode](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")</span></span>  
<span data-ttu-id="3672f-119">Birleşik Geometri Birliği</span><span class="sxs-lookup"><span data-stu-id="3672f-119">Combined Geometry Union</span></span>  
  
 <span data-ttu-id="3672f-120">Aşağıdaki biçimlendirmede bir <xref:System.Windows.Media.CombinedGeometry> birleştirme modu ile tanımlanan `Xor`.</span><span class="sxs-lookup"><span data-stu-id="3672f-120">In the following markup, a <xref:System.Windows.Media.CombinedGeometry> is defined with a combine mode of `Xor`.</span></span>  <span data-ttu-id="3672f-121">Her ikisi de <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> ve <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> daireler aynı RADIUS ancak merkezleri uzaklıkları 50 tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="3672f-121">Both <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and the <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> are defined as circles of the same radius, but with centers offset by 50.</span></span>  
  
 [!code-xaml[GeometrySample#24](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#24)]  
  
 <span data-ttu-id="3672f-122">![Birleştirme modu Xor sonuçları](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")</span><span class="sxs-lookup"><span data-stu-id="3672f-122">![Results of the Xor combine mode](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")</span></span>  
<span data-ttu-id="3672f-123">Birleşik Geometri Xor</span><span class="sxs-lookup"><span data-stu-id="3672f-123">Combined Geometry Xor</span></span>
