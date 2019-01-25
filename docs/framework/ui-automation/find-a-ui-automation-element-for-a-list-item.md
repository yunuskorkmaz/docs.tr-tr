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
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: a958e136d61a596640f1435b48701c4054105698
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54654795"
---
# <a name="find-a-ui-automation-element-for-a-list-item"></a><span data-ttu-id="1f7b1-102">Liste Öğesi İçin UI Otomasyon Öğesi Bulma</span><span class="sxs-lookup"><span data-stu-id="1f7b1-102">Find a UI Automation Element for a List Item</span></span>
> [!NOTE]
>  <span data-ttu-id="1f7b1-103">Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="1f7b1-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="1f7b1-104">En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="1f7b1-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="1f7b1-105">Bu konu nasıl alınacağını gösterir. bir <xref:System.Windows.Automation.AutomationElement> öğenin dizinini bilindiğinde listesindeki bir öğe için.</span><span class="sxs-lookup"><span data-stu-id="1f7b1-105">This topic shows how to retrieve an <xref:System.Windows.Automation.AutomationElement> for an item within a list when the index of the item is known.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f7b1-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="1f7b1-106">Example</span></span>  
 <span data-ttu-id="1f7b1-107">Belirtilen öğe bir listeden birini kullanarak almanın iki yolu aşağıdaki örnekte <xref:System.Windows.Automation.TreeWalker> ve diğer kullanma <xref:System.Windows.Automation.AutomationElement.FindAll%2A>.</span><span class="sxs-lookup"><span data-stu-id="1f7b1-107">The following example shows two ways of retrieving a specified item from a list, one using <xref:System.Windows.Automation.TreeWalker> and the other using <xref:System.Windows.Automation.AutomationElement.FindAll%2A>.</span></span>  
  
 <span data-ttu-id="1f7b1-108">İlk yöntem için daha hızlı olma eğilimindedir [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] kontrol eder, ancak ikinci Windows Presentation Foundation (WPF) denetimler için daha hızlı.</span><span class="sxs-lookup"><span data-stu-id="1f7b1-108">The first technique tends to be faster for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls, but the second is faster for Windows Presentation Foundation (WPF) controls.</span></span>  
  
 [!code-csharp[UIAClient_snip#184](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#184)]
 [!code-vb[UIAClient_snip#184](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#184)]  
  
## <a name="see-also"></a><span data-ttu-id="1f7b1-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f7b1-109">See also</span></span>
- [<span data-ttu-id="1f7b1-110">UI Otomasyonu Öğelerini Alma</span><span class="sxs-lookup"><span data-stu-id="1f7b1-110">Obtaining UI Automation Elements</span></span>](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)
