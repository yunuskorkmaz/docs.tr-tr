---
title: 'Nasıl yapılır: Radyal Gradyan ile bir Alanı Boyama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], painting with radial gradients
- radial gradients [WPF], painting with
- painting [WPF], with radial gradients
ms.assetid: b5d0fc8a-8986-4796-b003-a75b41a48928
ms.openlocfilehash: 5762ef1a1526ba6f004917c8a947e35ce731c86d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916093"
---
# <a name="how-to-paint-an-area-with-a-radial-gradient"></a><span data-ttu-id="b4f45-102">Nasıl yapılır: Radyal Gradyan ile bir Alanı Boyama</span><span class="sxs-lookup"><span data-stu-id="b4f45-102">How to: Paint an Area with a Radial Gradient</span></span>
<span data-ttu-id="b4f45-103">Bu örnek, <xref:System.Windows.Media.RadialGradientBrush> bir radyal gradyan ile bir alanı boyamak için sınıfının nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b4f45-103">This example shows how to use the <xref:System.Windows.Media.RadialGradientBrush> class to paint an area with a radial gradient.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4f45-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="b4f45-104">Example</span></span>  
 <span data-ttu-id="b4f45-105">Aşağıdaki örnek, sarıdan <xref:System.Windows.Media.RadialGradientBrush> kırmızıya ve sıfırdan yeşil 'e geçiş yapan bir radyal degradeyle bir dikdörtgeni boyamak için bir kullanır.</span><span class="sxs-lookup"><span data-stu-id="b4f45-105">The following example uses a <xref:System.Windows.Media.RadialGradientBrush> to paint a rectangle with a radial gradient that transitions from yellow to red to blue to lime green.</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/RadialGradientBrushSnippet.cs#simpleradialgradientexamplewholepage)]
 [!code-vb[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/radialgradientbrushsnippet.vb#simpleradialgradientexamplewholepage)]
 [!code-xaml[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/RadialGradientBrushSnippet.xaml#simpleradialgradientexamplewholepage)]  
  
 <span data-ttu-id="b4f45-106">Aşağıdaki çizimde, önceki örnekteki gradyan gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b4f45-106">The following illustration shows the gradient from the preceding example.</span></span> <span data-ttu-id="b4f45-107">Degradenin duraklar vurgulandı.</span><span class="sxs-lookup"><span data-stu-id="b4f45-107">The gradient's stops have been highlighted.</span></span>  
  
 <span data-ttu-id="b4f45-108">![Radyal degradede gradyan duraklarının](./media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")</span><span class="sxs-lookup"><span data-stu-id="b4f45-108">![Gradient stops in a radial gradient](./media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b4f45-109">Bu konudaki örneklerde, denetim noktalarını ayarlamak için varsayılan koordinat sistemi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b4f45-109">The examples in this topic use the default coordinate system for setting control points.</span></span> <span data-ttu-id="b4f45-110">Varsayılan koordinat sistemi bir sınırlayıcı kutuya göredir: 0 sınırlayıcı kutunun yüzde 0 ' ı gösterir ve 1 sınırlayıcı kutunun yüzde 100 ' unu gösterir.</span><span class="sxs-lookup"><span data-stu-id="b4f45-110">The default coordinate system is relative to a bounding box: 0 indicates 0 percent of the bounding box, and 1 indicates 100 percent of the bounding box.</span></span> <span data-ttu-id="b4f45-111"><xref:System.Windows.Media.GradientBrush.MappingMode%2A> Özelliği değerine<xref:System.Windows.Media.BrushMappingMode.Absolute>ayarlayarak bu koordinat sistemini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b4f45-111">You can change this coordinate system by setting the <xref:System.Windows.Media.GradientBrush.MappingMode%2A> property to the value <xref:System.Windows.Media.BrushMappingMode.Absolute>.</span></span> <span data-ttu-id="b4f45-112">Mutlak koordinat sistemi bir sınırlayıcı kutuya göreli değildir.</span><span class="sxs-lookup"><span data-stu-id="b4f45-112">An absolute coordinate system is not relative to a bounding box.</span></span> <span data-ttu-id="b4f45-113">Değerler doğrudan yerel alanda yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="b4f45-113">Values are interpreted directly in local space.</span></span>  
  
 <span data-ttu-id="b4f45-114">Daha fazla <xref:System.Windows.Media.RadialGradientBrush> örnek için bkz. [fırçalar örneği](https://go.microsoft.com/fwlink/?LinkID=159973).</span><span class="sxs-lookup"><span data-stu-id="b4f45-114">For additional <xref:System.Windows.Media.RadialGradientBrush> examples, see the [Brushes Sample](https://go.microsoft.com/fwlink/?LinkID=159973).</span></span> <span data-ttu-id="b4f45-115">Degradeler ve diğer fırça türleri hakkında daha fazla bilgi için bkz. [düz renklerle boyama ve degradelere genel bakış](painting-with-solid-colors-and-gradients-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b4f45-115">For more information about gradients and other types of brushes, see [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md).</span></span>
