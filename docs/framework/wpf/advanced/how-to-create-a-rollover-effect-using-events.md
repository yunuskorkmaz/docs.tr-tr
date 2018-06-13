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
ms.openlocfilehash: d458d87586614093b35fcd73969dea04fe620351
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543016"
---
# <a name="how-to-create-a-rollover-effect-using-events"></a><span data-ttu-id="d1040-102">Nasıl yapılır: Olayları Kullanarak Geçiş Efekti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d1040-102">How to: Create a Rollover Effect Using Events</span></span>
<span data-ttu-id="d1040-103">Bu örnek, fare işaretçisini girer ve öğe tarafından kapladığı alanı terk gibi bir öğesinin rengini değiştirmek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d1040-103">This example shows how to change the color of an element as the mouse pointer enters and leaves the area occupied by the element.</span></span>  
  
 <span data-ttu-id="d1040-104">Bu örnek oluşan bir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosyası ve bir arka plan kod dosyası.</span><span class="sxs-lookup"><span data-stu-id="d1040-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d1040-105">Örnek olaylar kullanmayı gösterir, ancak bu aynı sonucu elde etmek için önerilen yöntem kullanmaktır bir <xref:System.Windows.Trigger> stilinde.</span><span class="sxs-lookup"><span data-stu-id="d1040-105">This example demonstrates how to use events, but the recommended way to achieve this same effect is to use a <xref:System.Windows.Trigger> in a style.</span></span> <span data-ttu-id="d1040-106">Daha fazla bilgi için bkz: [stil ve şablon](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="d1040-106">For more information, see [Styling and Templating](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1040-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="d1040-107">Example</span></span>  
 <span data-ttu-id="d1040-108">Aşağıdaki [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] oluşan kullanıcı arabirimi oluşturan <xref:System.Windows.Controls.Border> geçici bir <xref:System.Windows.Controls.TextBlock>ve ekler <xref:System.Windows.Input.Mouse.MouseEnter> ve <xref:System.Windows.UIElement.MouseLeave> olay işleyicilerine <xref:System.Windows.Controls.Border>.</span><span class="sxs-lookup"><span data-stu-id="d1040-108">The following [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] creates the user interface, which consists of <xref:System.Windows.Controls.Border> around a <xref:System.Windows.Controls.TextBlock>, and attaches the <xref:System.Windows.Input.Mouse.MouseEnter> and <xref:System.Windows.UIElement.MouseLeave> event handlers to the <xref:System.Windows.Controls.Border>.</span></span>  
  
 [!code-xaml[mouseenterMouseleave#MouseEnterLeaveSampleXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml#mouseenterleavesamplexaml)]  
  
 <span data-ttu-id="d1040-109">Aşağıdaki arka plan kodu oluşturur <xref:System.Windows.UIElement.MouseEnter> ve <xref:System.Windows.UIElement.MouseLeave> olay işleyicileri.</span><span class="sxs-lookup"><span data-stu-id="d1040-109">The following code behind creates the <xref:System.Windows.UIElement.MouseEnter> and <xref:System.Windows.UIElement.MouseLeave> event handlers.</span></span>  <span data-ttu-id="d1040-110">Fare işaretçisini girdiğinde <xref:System.Windows.Controls.Border>, arka planını <xref:System.Windows.Controls.Border> kırmızı değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="d1040-110">When the mouse pointer enters the <xref:System.Windows.Controls.Border>, the background of the <xref:System.Windows.Controls.Border> is changed to red.</span></span>  <span data-ttu-id="d1040-111">Fare işaretçisini ayrıldığında <xref:System.Windows.Controls.Border>, arka planını <xref:System.Windows.Controls.Border> beyaza geri değişir.</span><span class="sxs-lookup"><span data-stu-id="d1040-111">When the mouse pointer leaves the <xref:System.Windows.Controls.Border>, the background of the <xref:System.Windows.Controls.Border> is changed back to white.</span></span>  
  
 [!code-csharp[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml.cs#mouseenterleavesampleeventhandlers)]
 [!code-vb[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/mouseenterMouseleave/VisualBasic/Window1.xaml.vb#mouseenterleavesampleeventhandlers)]
