---
title: 'Nasıl yapılır: Birleşik Geometri Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- combining geometries [WPF]
- graphics [WPF], combining geometries
- geometries [WPF], combining
ms.assetid: 54c3277c-6b6e-4b25-91be-fda0bbc706b4
ms.openlocfilehash: c5ebe87abd4c2cf70f8fa17f1fcc773293f3ad27
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61910111"
---
# <a name="how-to-create-a-combined-geometry"></a><span data-ttu-id="a9989-102">Nasıl yapılır: Birleşik Geometri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a9989-102">How to: Create a Combined Geometry</span></span>
<span data-ttu-id="a9989-103">Bu örnek nasıl geometriler birleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a9989-103">This example shows how to combine geometries.</span></span> <span data-ttu-id="a9989-104">İki geometri birleştirmek için kullanın. bir <xref:System.Windows.Media.CombinedGeometry> nesne.</span><span class="sxs-lookup"><span data-stu-id="a9989-104">To combine two geometries, use a <xref:System.Windows.Media.CombinedGeometry> object.</span></span> <span data-ttu-id="a9989-105">Ayarlama, <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> ve <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> Özellikleri birleştirmek ve ayarlamak için iki geometriler ile <xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A> geometriler birlikte nasıl birleştirileceğini belirleyen, özelliği için `Union`, `Intersect`, `Exclude`, veya `Xor`.</span><span class="sxs-lookup"><span data-stu-id="a9989-105">Set its <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> properties  with the two geometries to combine, and set the <xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A> property, which determines how the geometries will be combined together, to `Union`, `Intersect`, `Exclude`, or `Xor`.</span></span>  
  
 <span data-ttu-id="a9989-106">Birleşik Geometri iki veya daha fazla geometri oluşturmak için bir <xref:System.Windows.Media.GeometryGroup>.</span><span class="sxs-lookup"><span data-stu-id="a9989-106">To create a composite geometry from two or more geometries, use a <xref:System.Windows.Media.GeometryGroup>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9989-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="a9989-107">Example</span></span>  
 <span data-ttu-id="a9989-108">Aşağıdaki örnekte, bir <xref:System.Windows.Media.CombinedGeometry> geometri birleştirme modu ile tanımlanan `Exclude`.</span><span class="sxs-lookup"><span data-stu-id="a9989-108">In the following example, a <xref:System.Windows.Media.CombinedGeometry> is defined with a geometry combine mode of `Exclude`.</span></span>  <span data-ttu-id="a9989-109">Her ikisi de <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> ve <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> daireler aynı RADIUS ancak merkezleri uzaklığı ile 50 tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="a9989-109">Both <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and the <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> are defined as circles of the same radius, but with centers offset by 50.</span></span>  
  
 [!code-xaml[GeometrySample#21](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#21)]  
  
 <span data-ttu-id="a9989-110">![Birleştirme modu sonuçları tut](./media/mil-task-combined-geometry-exclude.PNG "mil_task_combined_geometry_exclude")</span><span class="sxs-lookup"><span data-stu-id="a9989-110">![Results of the Exclude combine mode](./media/mil-task-combined-geometry-exclude.PNG "mil_task_combined_geometry_exclude")</span></span>  
<span data-ttu-id="a9989-111">Birleşik Geometri dışlama</span><span class="sxs-lookup"><span data-stu-id="a9989-111">Combined Geometry Exclude</span></span>  
  
 <span data-ttu-id="a9989-112">Aşağıdaki biçimlendirmede bir <xref:System.Windows.Media.CombinedGeometry> birleştirme modu ile tanımlanan `Intersect`.</span><span class="sxs-lookup"><span data-stu-id="a9989-112">In the following markup, a <xref:System.Windows.Media.CombinedGeometry> is defined with a combine mode of `Intersect`.</span></span>  <span data-ttu-id="a9989-113">Her ikisi de <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> ve <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> daireler aynı RADIUS ancak merkezleri uzaklığı ile 50 tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="a9989-113">Both <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and the <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> are defined as circles of the same radius, but with centers offset by 50.</span></span>  
  
 [!code-xaml[GeometrySample#22](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#22)]  
  
 <span data-ttu-id="a9989-114">![INTERSECT sonuçlarını birleştirmek modu](./media/mil-task-combined-geometry-intersect.PNG "mil_task_combined_geometry_intersect")</span><span class="sxs-lookup"><span data-stu-id="a9989-114">![Results of the Intersect combine mode](./media/mil-task-combined-geometry-intersect.PNG "mil_task_combined_geometry_intersect")</span></span>  
<span data-ttu-id="a9989-115">Birleşik Geometri kesişimi</span><span class="sxs-lookup"><span data-stu-id="a9989-115">Combined Geometry Intersect</span></span>  
  
 <span data-ttu-id="a9989-116">Aşağıdaki biçimlendirmede bir <xref:System.Windows.Media.CombinedGeometry> birleştirme modu ile tanımlanan `Union`.</span><span class="sxs-lookup"><span data-stu-id="a9989-116">In the following markup, a <xref:System.Windows.Media.CombinedGeometry> is defined with a combine mode of `Union`.</span></span>  <span data-ttu-id="a9989-117">Her ikisi de <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> ve <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> daireler aynı RADIUS ancak merkezleri uzaklığı ile 50 tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="a9989-117">Both <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and the <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> are defined as circles of the same radius, but with centers offset by 50.</span></span>  
  
 [!code-xaml[GeometrySample#23](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#23)]  
  
 <span data-ttu-id="a9989-118">![Birleştirme modu UNION sonuçları](./media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")</span><span class="sxs-lookup"><span data-stu-id="a9989-118">![Results of the Union combine mode](./media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")</span></span>  
<span data-ttu-id="a9989-119">Birleşik Geometri birleşim</span><span class="sxs-lookup"><span data-stu-id="a9989-119">Combined Geometry Union</span></span>  
  
 <span data-ttu-id="a9989-120">Aşağıdaki biçimlendirmede bir <xref:System.Windows.Media.CombinedGeometry> birleştirme modu ile tanımlanan `Xor`.</span><span class="sxs-lookup"><span data-stu-id="a9989-120">In the following markup, a <xref:System.Windows.Media.CombinedGeometry> is defined with a combine mode of `Xor`.</span></span>  <span data-ttu-id="a9989-121">Her ikisi de <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> ve <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> daireler aynı RADIUS ancak merkezleri uzaklığı ile 50 tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="a9989-121">Both <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> and the <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> are defined as circles of the same radius, but with centers offset by 50.</span></span>  
  
 [!code-xaml[GeometrySample#24](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#24)]  
  
 <span data-ttu-id="a9989-122">![Xor sonuçlarını birleştirmek modu](./media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")</span><span class="sxs-lookup"><span data-stu-id="a9989-122">![Results of the Xor combine mode](./media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")</span></span>  
<span data-ttu-id="a9989-123">Birleşik Geometri Xor</span><span class="sxs-lookup"><span data-stu-id="a9989-123">Combined Geometry Xor</span></span>
