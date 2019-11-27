---
title: Liste Öğesi İçin UI Otomasyon Öğesi Bulma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- list items, finding elements for
- elements, finding for list items
- UI Automation, finding elements for List items
ms.assetid: c326ad2b-2144-4f64-ae4c-d850c74f95c5
ms.openlocfilehash: 63181de26f7d8efda99d5b5d71b006cde44823a3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433553"
---
# <a name="find-a-ui-automation-element-for-a-list-item"></a><span data-ttu-id="2f87f-102">Liste Öğesi İçin UI Otomasyon Öğesi Bulma</span><span class="sxs-lookup"><span data-stu-id="2f87f-102">Find a UI Automation Element for a List Item</span></span>
> [!NOTE]
> <span data-ttu-id="2f87f-103">Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="2f87f-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="2f87f-104">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="2f87f-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="2f87f-105">Bu konu, öğenin dizini bilindiğinde liste içindeki bir öğe için <xref:System.Windows.Automation.AutomationElement> nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2f87f-105">This topic shows how to retrieve an <xref:System.Windows.Automation.AutomationElement> for an item within a list when the index of the item is known.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f87f-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="2f87f-106">Example</span></span>  
 <span data-ttu-id="2f87f-107">Aşağıdaki örnek, bir listeden belirtilen öğeyi almanın iki yolunu gösterir, biri <xref:System.Windows.Automation.TreeWalker> ve diğeri <xref:System.Windows.Automation.AutomationElement.FindAll%2A>kullanarak.</span><span class="sxs-lookup"><span data-stu-id="2f87f-107">The following example shows two ways of retrieving a specified item from a list, one using <xref:System.Windows.Automation.TreeWalker> and the other using <xref:System.Windows.Automation.AutomationElement.FindAll%2A>.</span></span>  
  
 <span data-ttu-id="2f87f-108">İlk yöntem [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] denetimleri için daha hızlı bir şekilde eğilimindedir, ancak İkincisi Windows Presentation Foundation (WPF) denetimleri için daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="2f87f-108">The first technique tends to be faster for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls, but the second is faster for Windows Presentation Foundation (WPF) controls.</span></span>  
  
 [!code-csharp[UIAClient_snip#184](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#184)]
 [!code-vb[UIAClient_snip#184](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#184)]  
  
## <a name="see-also"></a><span data-ttu-id="2f87f-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2f87f-109">See also</span></span>

- [<span data-ttu-id="2f87f-110">UI Otomasyonu Öğelerini Alma</span><span class="sxs-lookup"><span data-stu-id="2f87f-110">Obtaining UI Automation Elements</span></span>](obtaining-ui-automation-elements.md)
