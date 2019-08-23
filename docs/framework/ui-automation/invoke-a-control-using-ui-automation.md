---
title: UI Otomasyonu Kullanarak Denetim Çağırma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- invoking controls
- UI Automation, invoking controls
- controls, invoking
ms.assetid: 5ee2de3f-256c-43ec-b64c-62ace91f9983
ms.openlocfilehash: f17f3ad25f137bbf8d7cf88b43cc52dfdeeb3fd4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923733"
---
# <a name="invoke-a-control-using-ui-automation"></a><span data-ttu-id="89057-102">UI Otomasyonu Kullanarak Denetim Çağırma</span><span class="sxs-lookup"><span data-stu-id="89057-102">Invoke a Control Using UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="89057-103">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="89057-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="89057-104">Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="89057-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="89057-105">Bu konu başlığı altında, aşağıdaki görevlerin nasıl gerçekleştirileceği gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="89057-105">This topic demonstrates how to perform the following tasks:</span></span>  
  
- <span data-ttu-id="89057-106">Hedef uygulama için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacın denetim görünümünü yürüyerek belirli özellik koşullarıyla eşleşen bir denetim bulun.</span><span class="sxs-lookup"><span data-stu-id="89057-106">Find a control that matches specific property conditions by walking the control view of the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree for the target application.</span></span>  
  
- <span data-ttu-id="89057-107">Her denetim <xref:System.Windows.Automation.AutomationElement> için oluşturun.</span><span class="sxs-lookup"><span data-stu-id="89057-107">Create an <xref:System.Windows.Automation.AutomationElement> for each control.</span></span>  
  
- <span data-ttu-id="89057-108">Denetim modelini <xref:System.Windows.Automation.InvokePattern> destekleyen, <xref:System.Windows.Automation.InvokePattern> bulunan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] herhangi bir öğeden bir nesne elde edin.</span><span class="sxs-lookup"><span data-stu-id="89057-108">Obtain an <xref:System.Windows.Automation.InvokePattern> object from any [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element found that supports the <xref:System.Windows.Automation.InvokePattern> control pattern.</span></span>  
  
- <span data-ttu-id="89057-109">Bir <xref:System.Windows.Automation.InvokePattern.Invoke%2A> istemci olay işleyicisinden denetimi çağırmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="89057-109">Use <xref:System.Windows.Automation.InvokePattern.Invoke%2A> to invoke the control from a client event handler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="89057-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="89057-110">Example</span></span>  
 <span data-ttu-id="89057-111">Bu <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> örnek, <xref:System.Windows.Automation.AutomationElement> yöntemini<xref:System.Windows.Automation.InvokePattern.Invoke%2A> kullanarak bir <xref:System.Windows.Automation.InvokePattern> nesnesi oluşturmak ve bir denetimi çağırmak için sınıfının yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="89057-111">This example uses the <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> method of the <xref:System.Windows.Automation.AutomationElement> class to generate an <xref:System.Windows.Automation.InvokePattern> object and invoke a control by using the <xref:System.Windows.Automation.InvokePattern.Invoke%2A> method.</span></span>  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
[!code-csharp[InvokePatternApp#1102](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1102)]
[!code-vb[InvokePatternApp#1102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1102)]  
  
## <a name="see-also"></a><span data-ttu-id="89057-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="89057-112">See also</span></span>

- [<span data-ttu-id="89057-113">Invokemodel, ExpandCollapsePattern ve Togglemodel örneği</span><span class="sxs-lookup"><span data-stu-id="89057-113">InvokePattern, ExpandCollapsePattern, and TogglePattern Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InvokePattern)
