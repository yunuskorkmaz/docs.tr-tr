---
title: 'Nasıl yapılır: Olayları Kullanarak Geçiş Efekti Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors of elements [WPF], changing
- rollover effect [WPF]
- element colors [WPF], changing
ms.assetid: 3b20d028-6f1c-4b25-95d2-fa68cefbdb4c
ms.openlocfilehash: 3996a3b9bb976dd5f2e5b675de3894bbaba7d9d3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960381"
---
# <a name="how-to-create-a-rollover-effect-using-events"></a><span data-ttu-id="5771f-102">Nasıl yapılır: Olayları Kullanarak Geçiş Efekti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5771f-102">How to: Create a Rollover Effect Using Events</span></span>
<span data-ttu-id="5771f-103">Bu örnek, fare işaretçisi öğe tarafından dolu olan alana girdiğinde bir öğenin renginin nasıl değiştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5771f-103">This example shows how to change the color of an element as the mouse pointer enters and leaves the area occupied by the element.</span></span>  
  
 <span data-ttu-id="5771f-104">Bu örnek, bir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosya ve arka plan kod dosyasından oluşur.</span><span class="sxs-lookup"><span data-stu-id="5771f-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5771f-105">Bu örnek, olayların nasıl kullanılacağını gösterir, ancak aynı etkiyi elde etmek için önerilen yol, bir <xref:System.Windows.Trigger> stilde kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="5771f-105">This example demonstrates how to use events, but the recommended way to achieve this same effect is to use a <xref:System.Windows.Trigger> in a style.</span></span> <span data-ttu-id="5771f-106">Daha fazla bilgi için bkz. [Stil oluşturma ve şablon](../controls/styling-and-templating.md)oluşturma.</span><span class="sxs-lookup"><span data-stu-id="5771f-106">For more information, see [Styling and Templating](../controls/styling-and-templating.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5771f-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="5771f-107">Example</span></span>  
 <span data-ttu-id="5771f-108">Aşağıdaki [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] <xref:System.Windows.UIElement.MouseLeave> , <xref:System.Windows.Controls.Border> bir<xref:System.Windows.Controls.TextBlock>öğesininetrafında oluşan Kullanıcı arabirimini oluşturur ve<xref:System.Windows.Controls.Border>ve olay işleyicilerini öğesine ekler. <xref:System.Windows.Input.Mouse.MouseEnter></span><span class="sxs-lookup"><span data-stu-id="5771f-108">The following [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] creates the user interface, which consists of <xref:System.Windows.Controls.Border> around a <xref:System.Windows.Controls.TextBlock>, and attaches the <xref:System.Windows.Input.Mouse.MouseEnter> and <xref:System.Windows.UIElement.MouseLeave> event handlers to the <xref:System.Windows.Controls.Border>.</span></span>  
  
 [!code-xaml[mouseenterMouseleave#MouseEnterLeaveSampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml#mouseenterleavesamplexaml)]  
  
 <span data-ttu-id="5771f-109">Aşağıdaki kod arkasında <xref:System.Windows.UIElement.MouseEnter> ve <xref:System.Windows.UIElement.MouseLeave> olay işleyicileri oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5771f-109">The following code behind creates the <xref:System.Windows.UIElement.MouseEnter> and <xref:System.Windows.UIElement.MouseLeave> event handlers.</span></span>  <span data-ttu-id="5771f-110">Fare işaretçisi öğesine girdiğinde <xref:System.Windows.Controls.Border>, <xref:System.Windows.Controls.Border> öğesinin arka planı kırmızı olarak değişir.</span><span class="sxs-lookup"><span data-stu-id="5771f-110">When the mouse pointer enters the <xref:System.Windows.Controls.Border>, the background of the <xref:System.Windows.Controls.Border> is changed to red.</span></span>  <span data-ttu-id="5771f-111">Fare işaretçisi <xref:System.Windows.Controls.Border>' den çıktığında, <xref:System.Windows.Controls.Border> öğesinin arka planı tekrar beyaza değişir.</span><span class="sxs-lookup"><span data-stu-id="5771f-111">When the mouse pointer leaves the <xref:System.Windows.Controls.Border>, the background of the <xref:System.Windows.Controls.Border> is changed back to white.</span></span>  
  
 [!code-csharp[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml.cs#mouseenterleavesampleeventhandlers)]
 [!code-vb[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/mouseenterMouseleave/VisualBasic/Window1.xaml.vb#mouseenterleavesampleeventhandlers)]
