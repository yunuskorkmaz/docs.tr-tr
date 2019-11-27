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
ms.openlocfilehash: e1b489e8daaaf9f5b8c0cb46374fa54bf165d49c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447006"
---
# <a name="invoke-a-control-using-ui-automation"></a><span data-ttu-id="17bd5-102">UI Otomasyonu Kullanarak Denetim Çağırma</span><span class="sxs-lookup"><span data-stu-id="17bd5-102">Invoke a Control Using UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="17bd5-103">Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="17bd5-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="17bd5-104">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="17bd5-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="17bd5-105">Bu konu başlığı altında, aşağıdaki görevlerin nasıl gerçekleştirileceği gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="17bd5-105">This topic demonstrates how to perform the following tasks:</span></span>  
  
- <span data-ttu-id="17bd5-106">Hedef uygulama için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacının denetim görünümünü yürüyerek belirli özellik koşullarıyla eşleşen bir denetim bulun.</span><span class="sxs-lookup"><span data-stu-id="17bd5-106">Find a control that matches specific property conditions by walking the control view of the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree for the target application.</span></span>  
  
- <span data-ttu-id="17bd5-107">Her denetim için bir <xref:System.Windows.Automation.AutomationElement> oluşturun.</span><span class="sxs-lookup"><span data-stu-id="17bd5-107">Create an <xref:System.Windows.Automation.AutomationElement> for each control.</span></span>  
  
- <span data-ttu-id="17bd5-108"><xref:System.Windows.Automation.InvokePattern> denetim modelini destekleyen, bulunan herhangi bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] öğesinden bir <xref:System.Windows.Automation.InvokePattern> nesnesi elde edin.</span><span class="sxs-lookup"><span data-stu-id="17bd5-108">Obtain an <xref:System.Windows.Automation.InvokePattern> object from any [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element found that supports the <xref:System.Windows.Automation.InvokePattern> control pattern.</span></span>  
  
- <span data-ttu-id="17bd5-109">Bir istemci olay işleyicisinden denetimi çağırmak için <xref:System.Windows.Automation.InvokePattern.Invoke%2A> kullanın.</span><span class="sxs-lookup"><span data-stu-id="17bd5-109">Use <xref:System.Windows.Automation.InvokePattern.Invoke%2A> to invoke the control from a client event handler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17bd5-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="17bd5-110">Example</span></span>  
 <span data-ttu-id="17bd5-111">Bu örnek, bir <xref:System.Windows.Automation.InvokePattern> nesnesi oluşturmak ve <xref:System.Windows.Automation.InvokePattern.Invoke%2A> metodunu kullanarak bir denetimi çağırmak için <xref:System.Windows.Automation.AutomationElement> sınıfının <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="17bd5-111">This example uses the <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> method of the <xref:System.Windows.Automation.AutomationElement> class to generate an <xref:System.Windows.Automation.InvokePattern> object and invoke a control by using the <xref:System.Windows.Automation.InvokePattern.Invoke%2A> method.</span></span>  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
[!code-csharp[InvokePatternApp#1102](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1102)]
[!code-vb[InvokePatternApp#1102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1102)]  
  
## <a name="see-also"></a><span data-ttu-id="17bd5-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="17bd5-112">See also</span></span>

- [<span data-ttu-id="17bd5-113">Invokemodel, ExpandCollapsePattern ve Togglemodel örneği</span><span class="sxs-lookup"><span data-stu-id="17bd5-113">InvokePattern, ExpandCollapsePattern, and TogglePattern Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InvokePattern)
