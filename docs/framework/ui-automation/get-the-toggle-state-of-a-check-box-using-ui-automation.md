---
title: UI Otomasyonunu Kullanarak Onay Kutusunun Değiştir Durumunu Alma
description: Microsoft UI Otomasyonu 'nu kullanarak bir denetimin (örneğin, onay kutusu) geçiş durumunun nasıl alınacağını gösteren bir kod örneğine bakın.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, getting toggle states of check boxes
- check boxes, getting toggle states of
- getting, toggle states of check boxes
ms.assetid: 84fc31a3-175f-4e93-90a0-dd29d89b77ce
ms.openlocfilehash: 36ec205a572fd6c9e52eec9d2c3e0618ddb0a07b
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164142"
---
# <a name="get-the-toggle-state-of-a-check-box-using-ui-automation"></a><span data-ttu-id="bd616-103">UI Otomasyonunu Kullanarak Onay Kutusunun Değiştir Durumunu Alma</span><span class="sxs-lookup"><span data-stu-id="bd616-103">Get the Toggle State of a Check Box Using UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="bd616-104">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> .</span><span class="sxs-lookup"><span data-stu-id="bd616-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="bd616-105">Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="bd616-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="bd616-106">Bu konu başlığı altında [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] , bir denetimin geçiş durumunu almak için nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bd616-106">This topic shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to get the toggle state of a control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd616-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="bd616-107">Example</span></span>  
 <span data-ttu-id="bd616-108">Bu örnek, <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> <xref:System.Windows.Automation.AutomationElement> <xref:System.Windows.Automation.TogglePattern> bir denetimden bir nesne elde etmek ve özelliğini döndürmek için sınıfının yöntemini kullanır <xref:System.Windows.Automation.ToggleState> .</span><span class="sxs-lookup"><span data-stu-id="bd616-108">This example uses the <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> method of the <xref:System.Windows.Automation.AutomationElement> class to obtain a <xref:System.Windows.Automation.TogglePattern> object from a control and return its <xref:System.Windows.Automation.ToggleState> property.</span></span>  
  
 [!code-csharp[NavigatingWithTreeWalker#1200](../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigatingWithTreeWalker/CSharp/ClientClass.cs#1200)]
 [!code-vb[NavigatingWithTreeWalker#1200](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigatingWithTreeWalker/visualbasic/clientclass.vb#1200)]
