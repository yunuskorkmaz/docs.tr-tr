---
title: UI Otomasyon Olaylarına Abone Olma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, subscribing to events
- subscribing to UI Automation events
- events, subscribing to
- listening for events
ms.assetid: b688effa-b3e8-4b05-944d-05ed89a245aa
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: c2f9ef01e4ba50e90a142c11eabd1bbb31f516b6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33400789"
---
# <a name="subscribe-to-ui-automation-events"></a><span data-ttu-id="e5c2f-102">UI Otomasyon Olaylarına Abone Olma</span><span class="sxs-lookup"><span data-stu-id="e5c2f-102">Subscribe to UI Automation Events</span></span>
> [!NOTE]
>  <span data-ttu-id="e5c2f-103">Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="e5c2f-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="e5c2f-104">Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="e5c2f-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="e5c2f-105">Bu konu, UI Otomasyon sağlayıcıları tarafından oluşturulan olaylara abone gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e5c2f-105">This topic shows how to subscribe to events raised by UI Automation providers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5c2f-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="e5c2f-106">Example</span></span>  
 <span data-ttu-id="e5c2f-107">Aşağıdaki örnek kod bir düğmesi gibi bir denetim çağrılır ve uygulama form kapandığında kaldırır olayı için bir olay işleyicisi kaydeder.</span><span class="sxs-lookup"><span data-stu-id="e5c2f-107">The following example code registers an event handler for the event that is raised when a control such as a button is invoked, and removes it when the application form closes.</span></span> <span data-ttu-id="e5c2f-108">Olay tarafından tanımlanan bir <xref:System.Windows.Automation.AutomationEvent> bir parametre olarak geçirilen <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>.</span><span class="sxs-lookup"><span data-stu-id="e5c2f-108">The event is identified by an <xref:System.Windows.Automation.AutomationEvent> passed as a parameter to <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>.</span></span>  
  
 [!code-csharp[UIAClient_snip#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#101)]
 [!code-vb[UIAClient_snip#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#101)]  
  
## <a name="example"></a><span data-ttu-id="e5c2f-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="e5c2f-109">Example</span></span>  
 <span data-ttu-id="e5c2f-110">Aşağıdaki örnekte nasıl kullanılacağını gösterir [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] odak değiştiğinde oluşan bir olaya abone olmak için.</span><span class="sxs-lookup"><span data-stu-id="e5c2f-110">The following example shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to subscribe to an event that is raised when the focus changes.</span></span> <span data-ttu-id="e5c2f-111">Olay işleyicisinin uygulaması kapatma veya bildirim UI olayların artık gerekli olduğunda çağrılabilir yönteminde kaydı.</span><span class="sxs-lookup"><span data-stu-id="e5c2f-111">The event handler is unregistered in a method that could be called on application shutdown, or when notification of UI events is no longer required.</span></span>  
  
 [!code-csharp[UIAClient_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#102)]
 [!code-vb[UIAClient_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#102)]  
  
## <a name="see-also"></a><span data-ttu-id="e5c2f-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e5c2f-112">See Also</span></span>  
 <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>  
 <xref:System.Windows.Automation.Automation.RemoveAllEventHandlers%2A>  
 <xref:System.Windows.Automation.Automation.RemoveAutomationEventHandler%2A>  
 [<span data-ttu-id="e5c2f-113">UI Otomasyonu Olaylarına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e5c2f-113">UI Automation Events Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-events-overview.md)
