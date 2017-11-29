---
title: "Nasıl yapılır: Doğrusal Gradyan ile bir Alanı Boyama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- linear gradients [WPF], painting with
- brushes [WPF], painting with linear gradients
- painting [WPF], with linear gradients
ms.assetid: 00e0cd04-48c0-4ec5-850e-d321beb37a34
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dcc37651d6f1f304f15d3244c2504517a2a9fb76
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-paint-an-area-with-a-linear-gradient"></a><span data-ttu-id="4b293-102">Nasıl yapılır: Doğrusal Gradyan ile bir Alanı Boyama</span><span class="sxs-lookup"><span data-stu-id="4b293-102">How to: Paint an Area with a Linear Gradient</span></span>
<span data-ttu-id="4b293-103">Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.LinearGradientBrush> doğrusal gradyan ile bir alanı boyamak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="4b293-103">This example shows how to use the <xref:System.Windows.Media.LinearGradientBrush> class to paint an area with a linear gradient.</span></span> <span data-ttu-id="4b293-104">Aşağıdaki örnekte, <xref:System.Windows.Shapes.Shape.Fill%2A> , bir <xref:System.Windows.Shapes.Rectangle> yeşile mavi ve kırmızı sarı geçiş çapraz bir doğrusal gradyan ile boyanır.</span><span class="sxs-lookup"><span data-stu-id="4b293-104">In the following example, the <xref:System.Windows.Shapes.Shape.Fill%2A> of a <xref:System.Windows.Shapes.Rectangle> is painted with a diagonal linear gradient that transitions from yellow to red to blue to lime green.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b293-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="4b293-105">Example</span></span>  
 [!code-xaml[GradientBrushExamples_snip#DiagonalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#diagonalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#DiagonalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#diagonalgradient1csharp)]  
  
 <span data-ttu-id="4b293-106">Aşağıdaki çizimde önceki örnek tarafından oluşturulan gradyanı gösterir.</span><span class="sxs-lookup"><span data-stu-id="4b293-106">The following illustration shows the gradient created by the previous example.</span></span>  
  
 <span data-ttu-id="4b293-107">![Çapraz doğrusal gradyan](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-diagonallgb.jpg "graphicsmm_DiagonalLGB")</span><span class="sxs-lookup"><span data-stu-id="4b293-107">![Diagonal linear gradient](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-diagonallgb.jpg "graphicsmm_DiagonalLGB")</span></span>  
  
 <span data-ttu-id="4b293-108">Değişiklik Yatay doğrusal gradyan oluşturmak için <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> ve <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> , <xref:System.Windows.Media.LinearGradientBrush> ' ini (0,0.5) ve (1,0.5)'e.</span><span class="sxs-lookup"><span data-stu-id="4b293-108">To create a horizontal linear gradient, change the <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> and <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> of the <xref:System.Windows.Media.LinearGradientBrush> to (0,0.5) and (1,0.5).</span></span> <span data-ttu-id="4b293-109">Aşağıdaki örnekte, bir <xref:System.Windows.Shapes.Rectangle> Yatay doğrusal gradyan ile boyanır.</span><span class="sxs-lookup"><span data-stu-id="4b293-109">In the following example, a <xref:System.Windows.Shapes.Rectangle> is painted with a horizontal linear gradient.</span></span>  
  
 [!code-xaml[GradientBrushExamples_snip#HorizontalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#horizontalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#HorizontalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#horizontalgradient1csharp)]  
  
 <span data-ttu-id="4b293-110">Aşağıdaki çizimde önceki örnek tarafından oluşturulan gradyanı gösterir.</span><span class="sxs-lookup"><span data-stu-id="4b293-110">The following illustration shows the gradient created by the previous example.</span></span>  
  
 <span data-ttu-id="4b293-111">![Yatay doğrusal gradyan](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-horizontallgb.jpg "graphicsmm_HorizontalLGB")</span><span class="sxs-lookup"><span data-stu-id="4b293-111">![A horizontal linear gradient](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-horizontallgb.jpg "graphicsmm_HorizontalLGB")</span></span>  
  
 <span data-ttu-id="4b293-112">Değişiklik dikey doğrusal gradyan oluşturmak için <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> ve <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> , <xref:System.Windows.Media.LinearGradientBrush> ' ini (0.5,0) ve (0.5,1)'e.</span><span class="sxs-lookup"><span data-stu-id="4b293-112">To create a vertical linear gradient, change the <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> and <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> of the <xref:System.Windows.Media.LinearGradientBrush> to (0.5,0) and (0.5,1).</span></span> <span data-ttu-id="4b293-113">Aşağıdaki örnekte, bir <xref:System.Windows.Shapes.Rectangle> dikey doğrusal gradyan ile boyanır.</span><span class="sxs-lookup"><span data-stu-id="4b293-113">In the following example, a <xref:System.Windows.Shapes.Rectangle> is painted with a vertical linear gradient.</span></span>  
  
 [!code-xaml[GradientBrushExamples_snip#VerticalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#verticalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#VerticalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#verticalgradient1csharp)]  
  
 <span data-ttu-id="4b293-114">Aşağıdaki çizimde önceki örnek tarafından oluşturulan gradyanı gösterir.</span><span class="sxs-lookup"><span data-stu-id="4b293-114">The following illustration shows the gradient created by the previous example.</span></span>  
  
 <span data-ttu-id="4b293-115">![Dikey doğrusal gradyan](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-verticallgb.jpg "graphicsmm_VerticalLGB")</span><span class="sxs-lookup"><span data-stu-id="4b293-115">![Vertical linear gradient](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-verticallgb.jpg "graphicsmm_VerticalLGB")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4b293-116">Bu konudaki örnekler, başlangıç ve bitiş noktalarını ayarlamak için varsayılan koordinat sistemi kullanır.</span><span class="sxs-lookup"><span data-stu-id="4b293-116">The examples in this topic use the default coordinate system for setting start points and end points.</span></span> <span data-ttu-id="4b293-117">Varsayılan koordinat sistemi göreli bir sınırlama kutusudur: 0 gösterir sınırlayıcı kutusunun yüzde 0 ve 1 sınırlayıcı kutusunun yüzde 100 gösterir.</span><span class="sxs-lookup"><span data-stu-id="4b293-117">The default coordinate system is relative to a bounding box: 0 indicates 0 percent of the bounding box, and 1 indicates 100 percent of the bounding box.</span></span> <span data-ttu-id="4b293-118">Ayarlayarak bu koordinat sistemini değiştirebilirsiniz <xref:System.Windows.Media.GradientBrush.MappingMode%2A> özelliğinin değeri <xref:System.Windows.Media.BrushMappingMode.Absolute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4b293-118">You can change this coordinate system by setting the <xref:System.Windows.Media.GradientBrush.MappingMode%2A> property to the value <xref:System.Windows.Media.BrushMappingMode.Absolute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4b293-119">Mutlak koordinat sistemi sınırlayıcı kutu göre değil.</span><span class="sxs-lookup"><span data-stu-id="4b293-119">An absolute coordinate system is not relative to a bounding box.</span></span> <span data-ttu-id="4b293-120">Değerleri, doğrudan yerel uzayda yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="4b293-120">Values are interpreted directly in local space.</span></span>  
  
 <span data-ttu-id="4b293-121">Ek örnekler için bkz: [Fırçalar örnek](http://go.microsoft.com/fwlink/?LinkID=159973).</span><span class="sxs-lookup"><span data-stu-id="4b293-121">For additional examples, see [Brushes Sample](http://go.microsoft.com/fwlink/?LinkID=159973).</span></span> <span data-ttu-id="4b293-122">Gradyan ve diğer fırça türleri hakkında daha fazla bilgi için bkz: [gradyan genel bakış ve düz renk ile Boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span><span class="sxs-lookup"><span data-stu-id="4b293-122">For more information about gradients and other types of brushes, see [Painting with Solid Colors and Gradients Overview](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span></span>
