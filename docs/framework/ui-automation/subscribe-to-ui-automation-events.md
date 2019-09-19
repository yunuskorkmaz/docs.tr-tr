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
ms.openlocfilehash: 1e148869f619729c72eae67892d4767eed9f8fb3
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71042637"
---
# <a name="subscribe-to-ui-automation-events"></a><span data-ttu-id="75e0a-102">UI Otomasyon Olaylarına Abone Olma</span><span class="sxs-lookup"><span data-stu-id="75e0a-102">Subscribe to UI Automation Events</span></span>
> [!NOTE]
> <span data-ttu-id="75e0a-103">Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="75e0a-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="75e0a-104">Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="75e0a-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="75e0a-105">Bu konu başlığı altında, UI Otomasyon sağlayıcıları tarafından oluşturulan olaylara nasıl abone olunacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="75e0a-105">This topic shows how to subscribe to events raised by UI Automation providers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="75e0a-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="75e0a-106">Example</span></span>  
 <span data-ttu-id="75e0a-107">Aşağıdaki örnek kod, düğme gibi bir denetim çağrıldığında oluşturulan olay için bir olay işleyicisini kaydeder ve uygulama formu kapandığında onu kaldırır.</span><span class="sxs-lookup"><span data-stu-id="75e0a-107">The following example code registers an event handler for the event that is raised when a control such as a button is invoked, and removes it when the application form closes.</span></span> <span data-ttu-id="75e0a-108">Olay, öğesine <xref:System.Windows.Automation.AutomationEvent> <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>parametresi olarak geçirilmiş tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="75e0a-108">The event is identified by an <xref:System.Windows.Automation.AutomationEvent> passed as a parameter to <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>.</span></span>  
  
 [!code-csharp[UIAClient_snip#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#101)]
 [!code-vb[UIAClient_snip#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#101)]  
  
## <a name="example"></a><span data-ttu-id="75e0a-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="75e0a-109">Example</span></span>  
 <span data-ttu-id="75e0a-110">Aşağıdaki örnek, odak değiştiğinde oluşan bir [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] olaya abone olmak için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="75e0a-110">The following example shows how to use [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] to subscribe to an event that is raised when the focus changes.</span></span> <span data-ttu-id="75e0a-111">Olay işleyicisi, uygulama kapatılırken çağrılabilecek bir yöntemde veya Kullanıcı arabirimi olaylarının bildirilmesi artık gerekli olmadığında kaydı silindi.</span><span class="sxs-lookup"><span data-stu-id="75e0a-111">The event handler is unregistered in a method that could be called on application shutdown, or when notification of UI events is no longer required.</span></span>  
  
 [!code-csharp[UIAClient_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#102)]
 [!code-vb[UIAClient_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#102)]  
  
## <a name="see-also"></a><span data-ttu-id="75e0a-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75e0a-112">See also</span></span>

- <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>
- <xref:System.Windows.Automation.Automation.RemoveAllEventHandlers%2A>
- <xref:System.Windows.Automation.Automation.RemoveAutomationEventHandler%2A>
- [<span data-ttu-id="75e0a-113">UI Otomasyonu Olaylarına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="75e0a-113">UI Automation Events Overview</span></span>](ui-automation-events-overview.md)
