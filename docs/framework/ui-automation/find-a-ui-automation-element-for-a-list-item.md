---
title: Liste Öğesi İçin UI Otomasyon Öğesi Bulma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- list items, finding elements for
- elements, finding for list items
- UI Automation, finding elements for List items
ms.assetid: c326ad2b-2144-4f64-ae4c-d850c74f95c5
ms.openlocfilehash: 2b9fb1ffe4b20074de66afe6d418a7cf5d39be0c
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043720"
---
# <a name="find-a-ui-automation-element-for-a-list-item"></a>Liste Öğesi İçin UI Otomasyon Öğesi Bulma
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir. Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu, öğenin dizini bilindiğinde <xref:System.Windows.Automation.AutomationElement> liste içindeki bir öğe için nasıl alınacağını gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.Windows.Automation.TreeWalker> bir listesinden ve <xref:System.Windows.Automation.AutomationElement.FindAll%2A>diğeri kullanılarak belirtilen bir öğeyi almanın iki yolunu gösterir.  
  
 İlk teknik denetimler için [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] daha hızlı bir şekilde eğilimindedir, ancak İkincisi Windows Presentation Foundation (WPF) denetimleri için daha hızlıdır.  
  
 [!code-csharp[UIAClient_snip#184](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#184)]
 [!code-vb[UIAClient_snip#184](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#184)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Öğelerini Alma](obtaining-ui-automation-elements.md)
