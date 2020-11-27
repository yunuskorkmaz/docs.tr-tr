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
ms.openlocfilehash: 9005139be69621e83efc592721a238c28ea1f6e9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96252328"
---
# <a name="subscribe-to-ui-automation-events"></a>UI Otomasyon Olaylarına Abone Olma

> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu başlığı altında, UI Otomasyon sağlayıcıları tarafından oluşturulan olaylara nasıl abone olunacağı gösterilmektedir.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek kod, düğme gibi bir denetim çağrıldığında oluşturulan olay için bir olay işleyicisini kaydeder ve uygulama formu kapandığında onu kaldırır. Olay, <xref:System.Windows.Automation.AutomationEvent> öğesine parametresi olarak geçirilmiş tarafından tanımlanır <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A> .  
  
 [!code-csharp[UIAClient_snip#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#101)]
 [!code-vb[UIAClient_snip#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#101)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] odak değiştiğinde oluşan bir olaya abone olmak için nasıl kullanılacağını gösterir. Olay işleyicisi, uygulama kapatılırken çağrılabilecek bir yöntemde veya Kullanıcı arabirimi olaylarının bildirilmesi artık gerekli olmadığında kaydı silindi.  
  
 [!code-csharp[UIAClient_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#102)]
 [!code-vb[UIAClient_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#102)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>
- <xref:System.Windows.Automation.Automation.RemoveAllEventHandlers%2A>
- <xref:System.Windows.Automation.Automation.RemoveAutomationEventHandler%2A>
- [UI Otomasyonu Olaylarına Genel Bakış](ui-automation-events-overview.md)
