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
ms.openlocfilehash: 87740a215136863199d962a2704cf691f27fc3bc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776655"
---
# <a name="how-to-create-a-rollover-effect-using-events"></a><span data-ttu-id="2b031-102">Nasıl yapılır: Olayları Kullanarak Geçiş Efekti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2b031-102">How to: Create a Rollover Effect Using Events</span></span>
<span data-ttu-id="2b031-103">Bu örnek, fare işaretçisini girer ve öğe tarafından kapladığı alanı bırakır gibi bir öğenin rengini değiştirme gösterir.</span><span class="sxs-lookup"><span data-stu-id="2b031-103">This example shows how to change the color of an element as the mouse pointer enters and leaves the area occupied by the element.</span></span>  
  
 <span data-ttu-id="2b031-104">Bu örnekte oluşan bir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosyası ve bir arka plan kod dosyası.</span><span class="sxs-lookup"><span data-stu-id="2b031-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2b031-105">Bu örnek olayların nasıl gösterir, ancak bu aynı etkiyi elde etmek için önerilen yöntem kullanmaktır bir <xref:System.Windows.Trigger> stil.</span><span class="sxs-lookup"><span data-stu-id="2b031-105">This example demonstrates how to use events, but the recommended way to achieve this same effect is to use a <xref:System.Windows.Trigger> in a style.</span></span> <span data-ttu-id="2b031-106">Daha fazla bilgi için [stil ve şablon oluşturma](../controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="2b031-106">For more information, see [Styling and Templating](../controls/styling-and-templating.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b031-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="2b031-107">Example</span></span>  
 <span data-ttu-id="2b031-108">Aşağıdaki [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] oluşur kullanıcı arabirimi oluşturan <xref:System.Windows.Controls.Border> etrafında bir <xref:System.Windows.Controls.TextBlock>ve ekler <xref:System.Windows.Input.Mouse.MouseEnter> ve <xref:System.Windows.UIElement.MouseLeave> olay işleyicilerine <xref:System.Windows.Controls.Border>.</span><span class="sxs-lookup"><span data-stu-id="2b031-108">The following [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] creates the user interface, which consists of <xref:System.Windows.Controls.Border> around a <xref:System.Windows.Controls.TextBlock>, and attaches the <xref:System.Windows.Input.Mouse.MouseEnter> and <xref:System.Windows.UIElement.MouseLeave> event handlers to the <xref:System.Windows.Controls.Border>.</span></span>  
  
 [!code-xaml[mouseenterMouseleave#MouseEnterLeaveSampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml#mouseenterleavesamplexaml)]  
  
 <span data-ttu-id="2b031-109">Aşağıdaki kod oluşturur <xref:System.Windows.UIElement.MouseEnter> ve <xref:System.Windows.UIElement.MouseLeave> olay işleyicileri.</span><span class="sxs-lookup"><span data-stu-id="2b031-109">The following code behind creates the <xref:System.Windows.UIElement.MouseEnter> and <xref:System.Windows.UIElement.MouseLeave> event handlers.</span></span>  <span data-ttu-id="2b031-110">Fare işaretçisi girdiğinde <xref:System.Windows.Controls.Border>, arka planını <xref:System.Windows.Controls.Border> kırmızıya değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="2b031-110">When the mouse pointer enters the <xref:System.Windows.Controls.Border>, the background of the <xref:System.Windows.Controls.Border> is changed to red.</span></span>  <span data-ttu-id="2b031-111">Fare işaretçisi ayrıldığında <xref:System.Windows.Controls.Border>, arka planını <xref:System.Windows.Controls.Border> beyaz olarak değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="2b031-111">When the mouse pointer leaves the <xref:System.Windows.Controls.Border>, the background of the <xref:System.Windows.Controls.Border> is changed back to white.</span></span>  
  
 [!code-csharp[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml.cs#mouseenterleavesampleeventhandlers)]
 [!code-vb[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/mouseenterMouseleave/VisualBasic/Window1.xaml.vb#mouseenterleavesampleeventhandlers)]
