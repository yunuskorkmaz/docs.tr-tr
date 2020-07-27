---
title: UI Otomasyon Olaylarına Abone Olma
description: Bkz. UI Otomasyon sağlayıcıları tarafından oluşturulan olaylara abone olma. Örnek kod, bir denetim çağrıldığında harekete geçirilen olay için bir olay işleyicisi kaydeder.
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
ms.openlocfilehash: 8f456702657c70837c6137e3e60335110361bcd9
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163540"
---
# <a name="subscribe-to-ui-automation-events"></a><span data-ttu-id="17775-104">UI Otomasyon Olaylarına Abone Olma</span><span class="sxs-lookup"><span data-stu-id="17775-104">Subscribe to UI Automation Events</span></span>
> [!NOTE]
> <span data-ttu-id="17775-105">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> .</span><span class="sxs-lookup"><span data-stu-id="17775-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="17775-106">Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="17775-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="17775-107">Bu konu başlığı altında, UI Otomasyon sağlayıcıları tarafından oluşturulan olaylara nasıl abone olunacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="17775-107">This topic shows how to subscribe to events raised by UI Automation providers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17775-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="17775-108">Example</span></span>  
 <span data-ttu-id="17775-109">Aşağıdaki örnek kod, düğme gibi bir denetim çağrıldığında oluşturulan olay için bir olay işleyicisini kaydeder ve uygulama formu kapandığında onu kaldırır.</span><span class="sxs-lookup"><span data-stu-id="17775-109">The following example code registers an event handler for the event that is raised when a control such as a button is invoked, and removes it when the application form closes.</span></span> <span data-ttu-id="17775-110">Olay, <xref:System.Windows.Automation.AutomationEvent> öğesine parametresi olarak geçirilmiş tarafından tanımlanır <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A> .</span><span class="sxs-lookup"><span data-stu-id="17775-110">The event is identified by an <xref:System.Windows.Automation.AutomationEvent> passed as a parameter to <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>.</span></span>  
  
 [!code-csharp[UIAClient_snip#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#101)]
 [!code-vb[UIAClient_snip#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#101)]  
  
## <a name="example"></a><span data-ttu-id="17775-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="17775-111">Example</span></span>  
 <span data-ttu-id="17775-112">Aşağıdaki örnek, [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] odak değiştiğinde oluşan bir olaya abone olmak için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="17775-112">The following example shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to subscribe to an event that is raised when the focus changes.</span></span> <span data-ttu-id="17775-113">Olay işleyicisi, uygulama kapatılırken çağrılabilecek bir yöntemde veya Kullanıcı arabirimi olaylarının bildirilmesi artık gerekli olmadığında kaydı silindi.</span><span class="sxs-lookup"><span data-stu-id="17775-113">The event handler is unregistered in a method that could be called on application shutdown, or when notification of UI events is no longer required.</span></span>  
  
 [!code-csharp[UIAClient_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#102)]
 [!code-vb[UIAClient_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#102)]  
  
## <a name="see-also"></a><span data-ttu-id="17775-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="17775-114">See also</span></span>

- <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>
- <xref:System.Windows.Automation.Automation.RemoveAllEventHandlers%2A>
- <xref:System.Windows.Automation.Automation.RemoveAutomationEventHandler%2A>
- [<span data-ttu-id="17775-115">UI Otomasyonu Olaylarına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="17775-115">UI Automation Events Overview</span></span>](ui-automation-events-overview.md)
