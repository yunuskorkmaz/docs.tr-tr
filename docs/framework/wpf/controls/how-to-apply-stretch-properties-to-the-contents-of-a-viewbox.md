---
title: 'Nasıl yapılır: Viewbox İçeriğine Uzatma Özellikleri Uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- StretchDirection properties [WPF]
- Stretch properties [WPF]
- controls [WPF], Viewbox
- Viewbox control [WPF]
ms.assetid: b9c22ef4-bce4-4300-9e0c-8260b7db83cc
ms.openlocfilehash: 3e81ec9fd045bb3fcf359943e455d2cce94aec55
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552811"
---
# <a name="how-to-apply-stretch-properties-to-the-contents-of-a-viewbox"></a><span data-ttu-id="32535-102">Nasıl yapılır: Viewbox İçeriğine Uzatma Özellikleri Uygulama</span><span class="sxs-lookup"><span data-stu-id="32535-102">How to: Apply Stretch Properties to the Contents of a Viewbox</span></span>
## <a name="example"></a><span data-ttu-id="32535-103">Örnek</span><span class="sxs-lookup"><span data-stu-id="32535-103">Example</span></span>  
 <span data-ttu-id="32535-104">Bu örnek değerini değiştirmek nasıl gösterir <xref:System.Windows.Controls.Viewbox.StretchDirection%2A> ve <xref:System.Windows.Controls.Viewbox.Stretch%2A> özelliklerini bir <xref:System.Windows.Controls.Viewbox>.</span><span class="sxs-lookup"><span data-stu-id="32535-104">This example shows how to change the value of the <xref:System.Windows.Controls.Viewbox.StretchDirection%2A> and <xref:System.Windows.Controls.Viewbox.Stretch%2A> properties of a <xref:System.Windows.Controls.Viewbox>.</span></span>  
  
 <span data-ttu-id="32535-105">İlk örnek kullanan [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] tanımlamak için bir <xref:System.Windows.Controls.Viewbox> öğesi.</span><span class="sxs-lookup"><span data-stu-id="32535-105">The first example uses [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to define a <xref:System.Windows.Controls.Viewbox> element.</span></span> <span data-ttu-id="32535-106">Atar bir <xref:System.Windows.FrameworkElement.MaxWidth%2A> ve <xref:System.Windows.FrameworkElement.MaxHeight%2A> 400.</span><span class="sxs-lookup"><span data-stu-id="32535-106">It assigns a <xref:System.Windows.FrameworkElement.MaxWidth%2A> and <xref:System.Windows.FrameworkElement.MaxHeight%2A> of 400.</span></span> <span data-ttu-id="32535-107">Örnek Yuvalar bir <xref:System.Windows.Controls.Image> öğesi içinde <xref:System.Windows.Controls.Viewbox>.</span><span class="sxs-lookup"><span data-stu-id="32535-107">The example nests an <xref:System.Windows.Controls.Image> element within the <xref:System.Windows.Controls.Viewbox>.</span></span> <span data-ttu-id="32535-108"><xref:System.Windows.Controls.Button> için özellik değerlerine karşılık gelen öğeler <xref:System.Windows.Controls.Viewbox.Stretch%2A> ve <xref:System.Windows.Controls.StretchDirection> sıralamaları iç içe uzatma davranışını <xref:System.Windows.Controls.Image>.</span><span class="sxs-lookup"><span data-stu-id="32535-108"><xref:System.Windows.Controls.Button> elements that correspond to the property values for the <xref:System.Windows.Controls.Viewbox.Stretch%2A> and <xref:System.Windows.Controls.StretchDirection> enumerations manipulate the stretching behavior of the nested <xref:System.Windows.Controls.Image>.</span></span>  
  
 [!code-xaml[viewboxStretchLayoutSamp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/viewboxStretchLayoutSamp/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="32535-109">Aşağıdaki arka plan kodu dosya tanıtıcıları <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayları, önceki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] örnek tanımlar.</span><span class="sxs-lookup"><span data-stu-id="32535-109">The following code-behind file handles the <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Primitives.ButtonBase.Click> events that the previous [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example defines.</span></span>  
  
 [!code-csharp[viewboxStretchLayoutSamp#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/viewboxStretchLayoutSamp/CSharp/Window1.xaml.cs#2)]
 [!code-vb[viewboxStretchLayoutSamp#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/viewboxStretchLayoutSamp/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="32535-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="32535-110">See Also</span></span>  
 <xref:System.Windows.Controls.Viewbox>  
 <xref:System.Windows.Media.Stretch>  
 <xref:System.Windows.Controls.StretchDirection>
