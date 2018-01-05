---
title: "Nasıl yapılır: Radyal Gradyan ile bir Alanı Boyama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], painting with radial gradients
- radial gradients [WPF], painting with
- painting [WPF], with radial gradients
ms.assetid: b5d0fc8a-8986-4796-b003-a75b41a48928
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f1da933a2ee7c179a55da7d33c61539d440eabc3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-paint-an-area-with-a-radial-gradient"></a><span data-ttu-id="a7119-102">Nasıl yapılır: Radyal Gradyan ile bir Alanı Boyama</span><span class="sxs-lookup"><span data-stu-id="a7119-102">How to: Paint an Area with a Radial Gradient</span></span>
<span data-ttu-id="a7119-103">Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.RadialGradientBrush> Radyal gradyan ile bir alanı boyamak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="a7119-103">This example shows how to use the <xref:System.Windows.Media.RadialGradientBrush> class to paint an area with a radial gradient.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7119-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="a7119-104">Example</span></span>  
 <span data-ttu-id="a7119-105">Aşağıdaki örnek kullanan bir <xref:System.Windows.Media.RadialGradientBrush> yeşile mavi ve kırmızı sarı geçiş Radyal gradyan ile bir dikdörtgen boyamak için.</span><span class="sxs-lookup"><span data-stu-id="a7119-105">The following example uses a <xref:System.Windows.Media.RadialGradientBrush> to paint a rectangle with a radial gradient that transitions from yellow to red to blue to lime green.</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/RadialGradientBrushSnippet.cs#simpleradialgradientexamplewholepage)]
 [!code-vb[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/radialgradientbrushsnippet.vb#simpleradialgradientexamplewholepage)]
 [!code-xaml[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/RadialGradientBrushSnippet.xaml#simpleradialgradientexamplewholepage)]  
  
 <span data-ttu-id="a7119-106">Aşağıdaki çizimde, önceki örnekten gradyanı gösterir.</span><span class="sxs-lookup"><span data-stu-id="a7119-106">The following illustration shows the gradient from the preceding example.</span></span> <span data-ttu-id="a7119-107">Vurgulanan gradyan durdurur.</span><span class="sxs-lookup"><span data-stu-id="a7119-107">The gradient's stops have been highlighted.</span></span>  
  
 <span data-ttu-id="a7119-108">![Radyal gradyan gradyan duraklarının](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")</span><span class="sxs-lookup"><span data-stu-id="a7119-108">![Gradient stops in a radial gradient](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a7119-109">Bu konudaki örnekler denetim noktalarını ayarlamak için varsayılan koordinat sistemi kullanır.</span><span class="sxs-lookup"><span data-stu-id="a7119-109">The examples in this topic use the default coordinate system for setting control points.</span></span> <span data-ttu-id="a7119-110">Varsayılan koordinat sistemi göreli bir sınırlama kutusudur: 0 gösterir sınırlayıcı kutusunun yüzde 0 ve 1 sınırlayıcı kutusunun yüzde 100 gösterir.</span><span class="sxs-lookup"><span data-stu-id="a7119-110">The default coordinate system is relative to a bounding box: 0 indicates 0 percent of the bounding box, and 1 indicates 100 percent of the bounding box.</span></span> <span data-ttu-id="a7119-111">Ayarlayarak bu koordinat sistemini değiştirebilirsiniz <xref:System.Windows.Media.GradientBrush.MappingMode%2A> özelliğinin değeri <xref:System.Windows.Media.BrushMappingMode.Absolute>.</span><span class="sxs-lookup"><span data-stu-id="a7119-111">You can change this coordinate system by setting the <xref:System.Windows.Media.GradientBrush.MappingMode%2A> property to the value <xref:System.Windows.Media.BrushMappingMode.Absolute>.</span></span> <span data-ttu-id="a7119-112">Mutlak koordinat sistemi sınırlayıcı kutu göre değil.</span><span class="sxs-lookup"><span data-stu-id="a7119-112">An absolute coordinate system is not relative to a bounding box.</span></span> <span data-ttu-id="a7119-113">Değerleri, doğrudan yerel uzayda yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="a7119-113">Values are interpreted directly in local space.</span></span>  
  
 <span data-ttu-id="a7119-114">İçin ek <xref:System.Windows.Media.RadialGradientBrush> örnekler, bkz: [Fırçalar örnek](http://go.microsoft.com/fwlink/?LinkID=159973).</span><span class="sxs-lookup"><span data-stu-id="a7119-114">For additional <xref:System.Windows.Media.RadialGradientBrush> examples, see the [Brushes Sample](http://go.microsoft.com/fwlink/?LinkID=159973).</span></span> <span data-ttu-id="a7119-115">Gradyan ve diğer fırça türleri hakkında daha fazla bilgi için bkz: [gradyan genel bakış ve düz renk ile Boyama](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a7119-115">For more information about gradients and other types of brushes, see [Painting with Solid Colors and Gradients Overview](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span></span>
