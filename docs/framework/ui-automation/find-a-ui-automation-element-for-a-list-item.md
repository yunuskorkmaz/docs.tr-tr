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
ms.openlocfilehash: ca4fdfabc4202ae9c9a36d4c511ebefc3ddd058d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969009"
---
# <a name="find-a-ui-automation-element-for-a-list-item"></a><span data-ttu-id="b3881-102">Liste Öğesi İçin UI Otomasyon Öğesi Bulma</span><span class="sxs-lookup"><span data-stu-id="b3881-102">Find a UI Automation Element for a List Item</span></span>
> [!NOTE]
> <span data-ttu-id="b3881-103">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="b3881-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="b3881-104">Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="b3881-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="b3881-105">Bu konu, öğenin dizini bilindiğinde <xref:System.Windows.Automation.AutomationElement> liste içindeki bir öğe için nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b3881-105">This topic shows how to retrieve an <xref:System.Windows.Automation.AutomationElement> for an item within a list when the index of the item is known.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3881-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="b3881-106">Example</span></span>  
 <span data-ttu-id="b3881-107">Aşağıdaki örnek, <xref:System.Windows.Automation.TreeWalker> bir listesinden ve <xref:System.Windows.Automation.AutomationElement.FindAll%2A>diğeri kullanılarak belirtilen bir öğeyi almanın iki yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="b3881-107">The following example shows two ways of retrieving a specified item from a list, one using <xref:System.Windows.Automation.TreeWalker> and the other using <xref:System.Windows.Automation.AutomationElement.FindAll%2A>.</span></span>  
  
 <span data-ttu-id="b3881-108">İlk teknik denetimler için [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] daha hızlı bir şekilde eğilimindedir, ancak İkincisi Windows Presentation Foundation (WPF) denetimleri için daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="b3881-108">The first technique tends to be faster for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls, but the second is faster for Windows Presentation Foundation (WPF) controls.</span></span>  
  
 [!code-csharp[UIAClient_snip#184](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#184)]
 [!code-vb[UIAClient_snip#184](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#184)]  
  
## <a name="see-also"></a><span data-ttu-id="b3881-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b3881-109">See also</span></span>

- [<span data-ttu-id="b3881-110">UI Otomasyonu Öğelerini Alma</span><span class="sxs-lookup"><span data-stu-id="b3881-110">Obtaining UI Automation Elements</span></span>](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)
