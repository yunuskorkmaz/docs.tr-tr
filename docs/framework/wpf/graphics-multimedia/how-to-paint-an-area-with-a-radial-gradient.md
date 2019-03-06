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
ms.openlocfilehash: c3bcc11dea4b1f223f629415591ab03588881dde
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57379789"
---
# <a name="how-to-paint-an-area-with-a-radial-gradient"></a><span data-ttu-id="f2043-102">Nasıl yapılır: Radyal Gradyan ile bir Alanı Boyama</span><span class="sxs-lookup"><span data-stu-id="f2043-102">How to: Paint an Area with a Radial Gradient</span></span>
<span data-ttu-id="f2043-103">Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.RadialGradientBrush> Radyal gradyan ile bir alanı boyama için sınıf.</span><span class="sxs-lookup"><span data-stu-id="f2043-103">This example shows how to use the <xref:System.Windows.Media.RadialGradientBrush> class to paint an area with a radial gradient.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2043-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="f2043-104">Example</span></span>  
 <span data-ttu-id="f2043-105">Aşağıdaki örnekte bir <xref:System.Windows.Media.RadialGradientBrush> sarı kırmızı, mavi yeşile geçiş Radyal gradyan ile bir dikdörtgen boyamak için.</span><span class="sxs-lookup"><span data-stu-id="f2043-105">The following example uses a <xref:System.Windows.Media.RadialGradientBrush> to paint a rectangle with a radial gradient that transitions from yellow to red to blue to lime green.</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/RadialGradientBrushSnippet.cs#simpleradialgradientexamplewholepage)]
 [!code-vb[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/radialgradientbrushsnippet.vb#simpleradialgradientexamplewholepage)]
 [!code-xaml[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/RadialGradientBrushSnippet.xaml#simpleradialgradientexamplewholepage)]  
  
 <span data-ttu-id="f2043-106">Önceki örnekte gradyan aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f2043-106">The following illustration shows the gradient from the preceding example.</span></span> <span data-ttu-id="f2043-107">Gradyan duraklarını vurgulanır.</span><span class="sxs-lookup"><span data-stu-id="f2043-107">The gradient's stops have been highlighted.</span></span>  
  
 <span data-ttu-id="f2043-108">![Radyal gradyan gradyan duraklarının](./media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")</span><span class="sxs-lookup"><span data-stu-id="f2043-108">![Gradient stops in a radial gradient](./media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f2043-109">Bu konudaki örnekler varsayılan koordinat sistemi denetim noktalarını ayarlamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="f2043-109">The examples in this topic use the default coordinate system for setting control points.</span></span> <span data-ttu-id="f2043-110">Varsayılan koordinat sistemi göreli bir sınırlayıcı kutu şöyledir: 0 gösterir sınırlayıcı kutusunun yüzde 0 ve 1, sınırlayıcı kutunun yüzde 100 gösterir.</span><span class="sxs-lookup"><span data-stu-id="f2043-110">The default coordinate system is relative to a bounding box: 0 indicates 0 percent of the bounding box, and 1 indicates 100 percent of the bounding box.</span></span> <span data-ttu-id="f2043-111">Ayarlayarak bu koordinat sistemini değiştirebilirsiniz <xref:System.Windows.Media.GradientBrush.MappingMode%2A> özellik değerine <xref:System.Windows.Media.BrushMappingMode.Absolute>.</span><span class="sxs-lookup"><span data-stu-id="f2043-111">You can change this coordinate system by setting the <xref:System.Windows.Media.GradientBrush.MappingMode%2A> property to the value <xref:System.Windows.Media.BrushMappingMode.Absolute>.</span></span> <span data-ttu-id="f2043-112">Mutlak koordinat sistemi bir sınırlayıcı kutu göreli değil.</span><span class="sxs-lookup"><span data-stu-id="f2043-112">An absolute coordinate system is not relative to a bounding box.</span></span> <span data-ttu-id="f2043-113">Değerleri, doğrudan yerel alan yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="f2043-113">Values are interpreted directly in local space.</span></span>  
  
 <span data-ttu-id="f2043-114">İçin ek <xref:System.Windows.Media.RadialGradientBrush> örnekler [Fırçalar örnek](https://go.microsoft.com/fwlink/?LinkID=159973).</span><span class="sxs-lookup"><span data-stu-id="f2043-114">For additional <xref:System.Windows.Media.RadialGradientBrush> examples, see the [Brushes Sample](https://go.microsoft.com/fwlink/?LinkID=159973).</span></span> <span data-ttu-id="f2043-115">Gradyanlar ve diğer türleri Fırçalar hakkında daha fazla bilgi için bkz: [düz renkler ve gradyanlar genel bakış boyama](painting-with-solid-colors-and-gradients-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f2043-115">For more information about gradients and other types of brushes, see [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md).</span></span>
