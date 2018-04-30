---
title: Liste Öğesi İçin UI Otomasyon Öğesi Bulma
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- list items, finding elements for
- elements, finding for list items
- UI Automation, finding elements for List items
ms.assetid: c326ad2b-2144-4f64-ae4c-d850c74f95c5
caps.latest.revision: 5
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: 727610b910cecbfa2b4c2eb1064fc357be822d42
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="find-a-ui-automation-element-for-a-list-item"></a><span data-ttu-id="9fdf5-102">Liste Öğesi İçin UI Otomasyon Öğesi Bulma</span><span class="sxs-lookup"><span data-stu-id="9fdf5-102">Find a UI Automation Element for a List Item</span></span>
> [!NOTE]
>  <span data-ttu-id="9fdf5-103">Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="9fdf5-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="9fdf5-104">Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="9fdf5-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="9fdf5-105">Bu konuda nasıl alınacağını gösteren bir <xref:System.Windows.Automation.AutomationElement> öğenin dizini bilindiğinde listesindeki bir öğeye ait.</span><span class="sxs-lookup"><span data-stu-id="9fdf5-105">This topic shows how to retrieve an <xref:System.Windows.Automation.AutomationElement> for an item within a list when the index of the item is known.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9fdf5-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="9fdf5-106">Example</span></span>  
 <span data-ttu-id="9fdf5-107">Aşağıdaki örnek, belirli bir öğeyi listeden birini kullanarak almanın iki yolu gösterir <xref:System.Windows.Automation.TreeWalker> ve diğer kullanma <xref:System.Windows.Automation.AutomationElement.FindAll%2A>.</span><span class="sxs-lookup"><span data-stu-id="9fdf5-107">The following example shows two ways of retrieving a specified item from a list, one using <xref:System.Windows.Automation.TreeWalker> and the other using <xref:System.Windows.Automation.AutomationElement.FindAll%2A>.</span></span>  
  
 <span data-ttu-id="9fdf5-108">İlk teknik için daha hızlı olma eğilimindedir [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] denetimleri, ancak ikinci Windows Presentation Foundation (WPF) denetimleri için daha hızlı.</span><span class="sxs-lookup"><span data-stu-id="9fdf5-108">The first technique tends to be faster for [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] controls, but the second is faster for Windows Presentation Foundation (WPF) controls.</span></span>  
  
 [!code-csharp[UIAClient_snip#184](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#184)]
 [!code-vb[UIAClient_snip#184](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#184)]  
  
## <a name="see-also"></a><span data-ttu-id="9fdf5-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9fdf5-109">See Also</span></span>  
 [<span data-ttu-id="9fdf5-110">UI Otomasyonu Öğelerini Alma</span><span class="sxs-lookup"><span data-stu-id="9fdf5-110">Obtaining UI Automation Elements</span></span>](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)
