---
title: 'Nasıl yapılır: Doğrusal Gradyan ile bir Alanı Boyama'
ms.date: 03/30/2017
helpviewer_keywords:
- linear gradients [WPF], painting with
- brushes [WPF], painting with linear gradients
- painting [WPF], with linear gradients
ms.assetid: 00e0cd04-48c0-4ec5-850e-d321beb37a34
ms.openlocfilehash: 76c491632911c48db34d932ba3895278591378a5
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452772"
---
# <a name="how-to-paint-an-area-with-a-linear-gradient"></a><span data-ttu-id="2b9ef-102">Nasıl yapılır: Doğrusal Gradyan ile bir Alanı Boyama</span><span class="sxs-lookup"><span data-stu-id="2b9ef-102">How to: Paint an Area with a Linear Gradient</span></span>
<span data-ttu-id="2b9ef-103">Bu örnek, doğrusal gradyan ile bir alanı boyamak için <xref:System.Windows.Media.LinearGradientBrush> sınıfını nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="2b9ef-103">This example shows how to use the <xref:System.Windows.Media.LinearGradientBrush> class to paint an area with a linear gradient.</span></span> <span data-ttu-id="2b9ef-104">Aşağıdaki örnekte, bir <xref:System.Windows.Shapes.Rectangle> <xref:System.Windows.Shapes.Shape.Fill%2A> sarıdan kırmızıya ve sıfırdan yeşil arasında geçiş yapan köşegen doğrusal gradyan ile boyanmıştır.</span><span class="sxs-lookup"><span data-stu-id="2b9ef-104">In the following example, the <xref:System.Windows.Shapes.Shape.Fill%2A> of a <xref:System.Windows.Shapes.Rectangle> is painted with a diagonal linear gradient that transitions from yellow to red to blue to lime green.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b9ef-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="2b9ef-105">Example</span></span>  
 [!code-xaml[GradientBrushExamples_snip#DiagonalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#diagonalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#DiagonalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#diagonalgradient1csharp)]  
  
 <span data-ttu-id="2b9ef-106">Aşağıdaki çizimde, önceki örnek tarafından oluşturulan gradyan gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2b9ef-106">The following illustration shows the gradient created by the previous example.</span></span>  
  
 <span data-ttu-id="2b9ef-107">![Köşegen doğrusal gradyan](./media/graphicsmm-diagonallgb.jpg "graphicsmm_DiagonalLGB")</span><span class="sxs-lookup"><span data-stu-id="2b9ef-107">![Diagonal linear gradient](./media/graphicsmm-diagonallgb.jpg "graphicsmm_DiagonalLGB")</span></span>  
  
 <span data-ttu-id="2b9ef-108">Yatay doğrusal gradyan oluşturmak için <xref:System.Windows.Media.LinearGradientBrush> <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> ve <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>, (0, 0,5) ve (1, 0,5) olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="2b9ef-108">To create a horizontal linear gradient, change the <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> and <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> of the <xref:System.Windows.Media.LinearGradientBrush> to (0,0.5) and (1,0.5).</span></span> <span data-ttu-id="2b9ef-109">Aşağıdaki örnekte, bir <xref:System.Windows.Shapes.Rectangle> Yatay doğrusal gradyan ile boyanmıştır.</span><span class="sxs-lookup"><span data-stu-id="2b9ef-109">In the following example, a <xref:System.Windows.Shapes.Rectangle> is painted with a horizontal linear gradient.</span></span>  
  
 [!code-xaml[GradientBrushExamples_snip#HorizontalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#horizontalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#HorizontalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#horizontalgradient1csharp)]  
  
 <span data-ttu-id="2b9ef-110">Aşağıdaki çizimde, önceki örnek tarafından oluşturulan gradyan gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2b9ef-110">The following illustration shows the gradient created by the previous example.</span></span>  
  
 <span data-ttu-id="2b9ef-111">![Yatay doğrusal gradyan](./media/graphicsmm-horizontallgb.jpg "graphicsmm_HorizontalLGB")</span><span class="sxs-lookup"><span data-stu-id="2b9ef-111">![A horizontal linear gradient](./media/graphicsmm-horizontallgb.jpg "graphicsmm_HorizontalLGB")</span></span>  
  
 <span data-ttu-id="2b9ef-112">Dikey bir doğrusal gradyan oluşturmak için <xref:System.Windows.Media.LinearGradientBrush> <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> ve <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>, (0,5, 0) ve (0,5, 1) olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="2b9ef-112">To create a vertical linear gradient, change the <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> and <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> of the <xref:System.Windows.Media.LinearGradientBrush> to (0.5,0) and (0.5,1).</span></span> <span data-ttu-id="2b9ef-113">Aşağıdaki örnekte, bir <xref:System.Windows.Shapes.Rectangle> Dikey doğrusal gradyan ile boyanmıştır.</span><span class="sxs-lookup"><span data-stu-id="2b9ef-113">In the following example, a <xref:System.Windows.Shapes.Rectangle> is painted with a vertical linear gradient.</span></span>  
  
 [!code-xaml[GradientBrushExamples_snip#VerticalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#verticalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#VerticalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#verticalgradient1csharp)]  
  
 <span data-ttu-id="2b9ef-114">Aşağıdaki çizimde, önceki örnek tarafından oluşturulan gradyan gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2b9ef-114">The following illustration shows the gradient created by the previous example.</span></span>  
  
 <span data-ttu-id="2b9ef-115">![Dikey doğrusal gradyan](./media/graphicsmm-verticallgb.jpg "graphicsmm_VerticalLGB")</span><span class="sxs-lookup"><span data-stu-id="2b9ef-115">![Vertical linear gradient](./media/graphicsmm-verticallgb.jpg "graphicsmm_VerticalLGB")</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2b9ef-116">Bu konudaki örneklerde, başlangıç noktalarını ve bitiş noktalarını ayarlamak için varsayılan koordinat sistemi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2b9ef-116">The examples in this topic use the default coordinate system for setting start points and end points.</span></span> <span data-ttu-id="2b9ef-117">Varsayılan koordinat sistemi bir sınırlayıcı kutuya göredir: 0 sınırlayıcı kutunun yüzde 0 ' ı gösterir ve 1 sınırlayıcı kutunun yüzde 100 ' unu gösterir.</span><span class="sxs-lookup"><span data-stu-id="2b9ef-117">The default coordinate system is relative to a bounding box: 0 indicates 0 percent of the bounding box, and 1 indicates 100 percent of the bounding box.</span></span> <span data-ttu-id="2b9ef-118"><xref:System.Windows.Media.GradientBrush.MappingMode%2A> özelliğini <xref:System.Windows.Media.BrushMappingMode.Absolute?displayProperty=nameWithType>değerine ayarlayarak bu koordinat sistemini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b9ef-118">You can change this coordinate system by setting the <xref:System.Windows.Media.GradientBrush.MappingMode%2A> property to the value <xref:System.Windows.Media.BrushMappingMode.Absolute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="2b9ef-119">Mutlak koordinat sistemi bir sınırlayıcı kutuya göreli değildir.</span><span class="sxs-lookup"><span data-stu-id="2b9ef-119">An absolute coordinate system is not relative to a bounding box.</span></span> <span data-ttu-id="2b9ef-120">Değerler doğrudan yerel alanda yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="2b9ef-120">Values are interpreted directly in local space.</span></span>  
  
 <span data-ttu-id="2b9ef-121">Daha fazla örnek için bkz. [fırçalar örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span><span class="sxs-lookup"><span data-stu-id="2b9ef-121">For additional examples, see [Brushes Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span></span> <span data-ttu-id="2b9ef-122">Degradeler ve diğer fırça türleri hakkında daha fazla bilgi için bkz. [düz renklerle boyama ve degradelere genel bakış](painting-with-solid-colors-and-gradients-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2b9ef-122">For more information about gradients and other types of brushes, see [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md).</span></span>
