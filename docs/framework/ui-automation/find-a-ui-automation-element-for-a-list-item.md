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
ms.openlocfilehash: ec6464bc0ec504fd34ed113c9bed1a54a7d4eaec
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168410"
---
# <a name="find-a-ui-automation-element-for-a-list-item"></a>Liste Öğesi İçin UI Otomasyon Öğesi Bulma
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu, <xref:System.Windows.Automation.AutomationElement> öğenin dizini bilindiğinde liste içindeki bir öğe için nasıl alınacağını gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir listesinden ve diğeri kullanılarak belirtilen bir öğeyi almanın iki yolunu gösterir <xref:System.Windows.Automation.TreeWalker> <xref:System.Windows.Automation.AutomationElement.FindAll%2A> .  
  
 İlk teknik, Win32 denetimleri için daha hızlı bir şekilde eğilimindedir, ancak İkincisi Windows Presentation Foundation (WPF) denetimleri için daha hızlıdır.  
  
 [!code-csharp[UIAClient_snip#184](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#184)]
 [!code-vb[UIAClient_snip#184](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#184)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyon Öğelerini Alma](obtaining-ui-automation-elements.md)
