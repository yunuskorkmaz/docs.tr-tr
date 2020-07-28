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
# <a name="get-the-toggle-state-of-a-check-box-using-ui-automation"></a>UI Otomasyonunu Kullanarak Onay Kutusunun Değiştir Durumunu Alma
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu başlığı altında [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] , bir denetimin geçiş durumunu almak için nasıl kullanılacağı gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Bu örnek, <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> <xref:System.Windows.Automation.AutomationElement> <xref:System.Windows.Automation.TogglePattern> bir denetimden bir nesne elde etmek ve özelliğini döndürmek için sınıfının yöntemini kullanır <xref:System.Windows.Automation.ToggleState> .  
  
 [!code-csharp[NavigatingWithTreeWalker#1200](../../../samples/snippets/csharp/VS_Snippets_Wpf/NavigatingWithTreeWalker/CSharp/ClientClass.cs#1200)]
 [!code-vb[NavigatingWithTreeWalker#1200](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/NavigatingWithTreeWalker/visualbasic/clientclass.vb#1200)]
