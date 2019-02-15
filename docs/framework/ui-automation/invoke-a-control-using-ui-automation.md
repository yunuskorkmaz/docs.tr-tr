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
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: b630e98390ac5ffbbb503bc618aeb3f648129a53
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56304628"
---
# <a name="invoke-a-control-using-ui-automation"></a><span data-ttu-id="4fea7-102">UI Otomasyonu Kullanarak Denetim Çağırma</span><span class="sxs-lookup"><span data-stu-id="4fea7-102">Invoke a Control Using UI Automation</span></span>
> [!NOTE]
>  <span data-ttu-id="4fea7-103">Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="4fea7-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="4fea7-104">En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="4fea7-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="4fea7-105">Bu konu aşağıdaki görevlerin nasıl gerçekleştirileceğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="4fea7-105">This topic demonstrates how to perform the following tasks:</span></span>  
  
-   <span data-ttu-id="4fea7-106">Denetimin görünümünü walking tarafından belirli özellik koşullara uyan bir denetimi bulmak [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] hedef uygulama için ağacı.</span><span class="sxs-lookup"><span data-stu-id="4fea7-106">Find a control that matches specific property conditions by walking the control view of the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree for the target application.</span></span>  
  
-   <span data-ttu-id="4fea7-107">Oluşturma bir <xref:System.Windows.Automation.AutomationElement> her denetim için.</span><span class="sxs-lookup"><span data-stu-id="4fea7-107">Create an <xref:System.Windows.Automation.AutomationElement> for each control.</span></span>  
  
-   <span data-ttu-id="4fea7-108">Elde bir <xref:System.Windows.Automation.InvokePattern> herhangi bir nesneden [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] öğe bulundu destekleyen <xref:System.Windows.Automation.InvokePattern> denetim düzeni.</span><span class="sxs-lookup"><span data-stu-id="4fea7-108">Obtain an <xref:System.Windows.Automation.InvokePattern> object from any [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element found that supports the <xref:System.Windows.Automation.InvokePattern> control pattern.</span></span>  
  
-   <span data-ttu-id="4fea7-109">Kullanım <xref:System.Windows.Automation.InvokePattern.Invoke%2A> istemci olay işleyicisi denetiminden çağırmak için.</span><span class="sxs-lookup"><span data-stu-id="4fea7-109">Use <xref:System.Windows.Automation.InvokePattern.Invoke%2A> to invoke the control from a client event handler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4fea7-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="4fea7-110">Example</span></span>  
 <span data-ttu-id="4fea7-111">Bu örnekte <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> yöntemi <xref:System.Windows.Automation.AutomationElement> sınıfı oluşturmak için bir <xref:System.Windows.Automation.InvokePattern> nesne ve kullanarak denetim çağırma <xref:System.Windows.Automation.InvokePattern.Invoke%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4fea7-111">This example uses the <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> method of the <xref:System.Windows.Automation.AutomationElement> class to generate an <xref:System.Windows.Automation.InvokePattern> object and invoke a control by using the <xref:System.Windows.Automation.InvokePattern.Invoke%2A> method.</span></span>  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
[!code-csharp[InvokePatternApp#1102](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1102)]
[!code-vb[InvokePatternApp#1102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1102)]  
  
## <a name="see-also"></a><span data-ttu-id="4fea7-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4fea7-112">See also</span></span>
- [<span data-ttu-id="4fea7-113">InvokePattern'ı, ExpandCollapsePattern'ı ve TogglePattern'ı örneği</span><span class="sxs-lookup"><span data-stu-id="4fea7-113">InvokePattern, ExpandCollapsePattern, and TogglePattern Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InvokePattern)
