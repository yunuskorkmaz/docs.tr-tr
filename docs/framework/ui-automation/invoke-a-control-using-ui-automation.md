---
title: UI Otomasyonu Kullanarak Denetim Çağırma
description: UI otomasyonunu kullanarak belirli özellik koşullarına uyan bir denetim bulun, bir AutomationElement oluşturun, bir ınvokemodel alın ve denetimde Invoke kullanın.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- invoking controls
- UI Automation, invoking controls
- controls, invoking
ms.assetid: 5ee2de3f-256c-43ec-b64c-62ace91f9983
ms.openlocfilehash: 2347a620aab848bf6bcc649a9780aa5a3a520822
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168175"
---
# <a name="invoke-a-control-using-ui-automation"></a><span data-ttu-id="541fb-103">UI Otomasyonu Kullanarak Denetim Çağırma</span><span class="sxs-lookup"><span data-stu-id="541fb-103">Invoke a Control Using UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="541fb-104">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> .</span><span class="sxs-lookup"><span data-stu-id="541fb-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="541fb-105">Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="541fb-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="541fb-106">Bu konu başlığı altında, aşağıdaki görevlerin nasıl gerçekleştirileceği gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="541fb-106">This topic demonstrates how to perform the following tasks:</span></span>  
  
- <span data-ttu-id="541fb-107">Hedef uygulama için ağacın denetim görünümünü yürüyerek belirli özellik koşullarıyla eşleşen bir denetim bulun [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="541fb-107">Find a control that matches specific property conditions by walking the control view of the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree for the target application.</span></span>  
  
- <span data-ttu-id="541fb-108"><xref:System.Windows.Automation.AutomationElement>Her denetim için oluşturun.</span><span class="sxs-lookup"><span data-stu-id="541fb-108">Create an <xref:System.Windows.Automation.AutomationElement> for each control.</span></span>  
  
- <span data-ttu-id="541fb-109"><xref:System.Windows.Automation.InvokePattern> [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Denetim modelini destekleyen, bulunan herhangi bir öğeden bir nesne elde edin <xref:System.Windows.Automation.InvokePattern> .</span><span class="sxs-lookup"><span data-stu-id="541fb-109">Obtain an <xref:System.Windows.Automation.InvokePattern> object from any [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element found that supports the <xref:System.Windows.Automation.InvokePattern> control pattern.</span></span>  
  
- <span data-ttu-id="541fb-110"><xref:System.Windows.Automation.InvokePattern.Invoke%2A>Bir istemci olay işleyicisinden denetimi çağırmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="541fb-110">Use <xref:System.Windows.Automation.InvokePattern.Invoke%2A> to invoke the control from a client event handler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="541fb-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="541fb-111">Example</span></span>  
 <span data-ttu-id="541fb-112">Bu örnek, <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> <xref:System.Windows.Automation.AutomationElement> <xref:System.Windows.Automation.InvokePattern> yöntemini kullanarak bir nesnesi oluşturmak ve bir denetimi çağırmak için sınıfının yöntemini kullanır <xref:System.Windows.Automation.InvokePattern.Invoke%2A> .</span><span class="sxs-lookup"><span data-stu-id="541fb-112">This example uses the <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> method of the <xref:System.Windows.Automation.AutomationElement> class to generate an <xref:System.Windows.Automation.InvokePattern> object and invoke a control by using the <xref:System.Windows.Automation.InvokePattern.Invoke%2A> method.</span></span>  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
[!code-csharp[InvokePatternApp#1102](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1102)]
[!code-vb[InvokePatternApp#1102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1102)]  
  
## <a name="see-also"></a><span data-ttu-id="541fb-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="541fb-113">See also</span></span>

- [<span data-ttu-id="541fb-114">Invokemodel, ExpandCollapsePattern ve Togglemodel örneği</span><span class="sxs-lookup"><span data-stu-id="541fb-114">InvokePattern, ExpandCollapsePattern, and TogglePattern Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InvokePattern)
