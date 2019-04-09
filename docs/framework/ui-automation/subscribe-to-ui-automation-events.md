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
ms.openlocfilehash: 9c5308192ca122e9c25fa8e845f2b8f89345dda8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59168473"
---
# <a name="subscribe-to-ui-automation-events"></a>UI Otomasyon Olaylarına Abone Olma
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konuda, UI Otomasyon sağlayıcıları tarafından oluşturulan olaylara abone olunacağı gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, bir düğme gibi bir denetim çağrılır ve formunu kapandığında kaldırır, olayı için olay işleyicisi kaydeder. Olay tarafından tanımlanan bir <xref:System.Windows.Automation.AutomationEvent> bir parametre olarak geçirilen <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>.  
  
 [!code-csharp[UIAClient_snip#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#101)]
 [!code-vb[UIAClient_snip#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#101)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl kullanılacağını gösterir [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] odak her değiştiğinde başlatan bir olaya abone olmak için. Olay işleyicisi, uygulamayı kapatma veya kullanıcı Arabirimi olaylarının bildirim artık gerekli olmadığında çağrılabilen bir yöntem'kaydı silindi.  
  
 [!code-csharp[UIAClient_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#102)]
 [!code-vb[UIAClient_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#102)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>
- <xref:System.Windows.Automation.Automation.RemoveAllEventHandlers%2A>
- <xref:System.Windows.Automation.Automation.RemoveAutomationEventHandler%2A>
- [UI Otomasyonu Olaylarına Genel Bakış](../../../docs/framework/ui-automation/ui-automation-events-overview.md)
