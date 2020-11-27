---
title: Liste Öğesi İçin UI Otomasyon Öğesi Bulma
description: Öğenin dizini bilindiğinde, bir liste öğesi için bir UI Otomasyonu öğesinin nasıl bulunacağını gösteren bir örneğe bakın.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- list items, finding elements for
- elements, finding for list items
- UI Automation, finding elements for List items
ms.assetid: c326ad2b-2144-4f64-ae4c-d850c74f95c5
ms.openlocfilehash: 95f6b558cc53b00701232f247f8de7f8c603e3ac
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276483"
---
# <a name="find-a-ui-automation-element-for-a-list-item"></a><span data-ttu-id="a2b3f-103">Liste Öğesi İçin UI Otomasyon Öğesi Bulma</span><span class="sxs-lookup"><span data-stu-id="a2b3f-103">Find a UI Automation Element for a List Item</span></span>

> [!NOTE]
> <span data-ttu-id="a2b3f-104">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> .</span><span class="sxs-lookup"><span data-stu-id="a2b3f-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="a2b3f-105">Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="a2b3f-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="a2b3f-106">Bu konu, <xref:System.Windows.Automation.AutomationElement> öğenin dizini bilindiğinde liste içindeki bir öğe için nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a2b3f-106">This topic shows how to retrieve an <xref:System.Windows.Automation.AutomationElement> for an item within a list when the index of the item is known.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2b3f-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="a2b3f-107">Example</span></span>  

 <span data-ttu-id="a2b3f-108">Aşağıdaki örnek, bir listesinden ve diğeri kullanılarak belirtilen bir öğeyi almanın iki yolunu gösterir <xref:System.Windows.Automation.TreeWalker> <xref:System.Windows.Automation.AutomationElement.FindAll%2A> .</span><span class="sxs-lookup"><span data-stu-id="a2b3f-108">The following example shows two ways of retrieving a specified item from a list, one using <xref:System.Windows.Automation.TreeWalker> and the other using <xref:System.Windows.Automation.AutomationElement.FindAll%2A>.</span></span>  
  
 <span data-ttu-id="a2b3f-109">İlk teknik, Win32 denetimleri için daha hızlı bir şekilde eğilimindedir, ancak İkincisi Windows Presentation Foundation (WPF) denetimleri için daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="a2b3f-109">The first technique tends to be faster for Win32 controls, but the second is faster for Windows Presentation Foundation (WPF) controls.</span></span>  
  
 [!code-csharp[UIAClient_snip#184](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#184)]
 [!code-vb[UIAClient_snip#184](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#184)]  
  
## <a name="see-also"></a><span data-ttu-id="a2b3f-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a2b3f-110">See also</span></span>

- [<span data-ttu-id="a2b3f-111">UI Otomasyon Öğelerini Alma</span><span class="sxs-lookup"><span data-stu-id="a2b3f-111">Obtaining UI Automation Elements</span></span>](obtaining-ui-automation-elements.md)
