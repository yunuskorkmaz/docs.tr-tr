---
title: Desteklenen UI Otomasyon Denetim Düzenlerini Alma
description: UI Otomasyon öğelerinden desteklenen denetim deseninin nesnelerinin nasıl alınacağını gösteren bir örnek okuyun.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- control patterns, getting
- UI Automation, getting control patterns
- getting, control patterns
ms.assetid: 006c54c9-50bf-48d9-a855-9d62eb95603a
ms.openlocfilehash: f2905b81a1af2f86c78b082f0241e2181c384d25
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164158"
---
# <a name="get-supported-ui-automation-control-patterns"></a>Desteklenen UI Otomasyon Denetim Düzenlerini Alma
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu, öğelerinden denetim deseninin nesnelerinin nasıl alınacağını gösterir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .  
  
### <a name="obtain-all-control-patterns"></a>Tüm denetim desenlerini al  
  
1. <xref:System.Windows.Automation.AutomationElement>İlgilendiğiniz denetim düzenlerini alın.  
  
2. <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>Öğesinden tüm denetim desenlerini almak için çağırın.  
  
> [!CAUTION]
> İstemcinin kullanmamaları önemle önerilir <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> . Bu yöntem, <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> var olan her denetim deseninin dahili olarak çağırdığı için performans ciddi bir şekilde etkilenebilir. Mümkünse, bir istemci <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> ilgilendiğiniz önemli desenleri çağırmalıdır.  
  
### <a name="obtain-a-specific-control-pattern"></a>Belirli bir denetim deseninin elde edileceği  
  
1. <xref:System.Windows.Automation.AutomationElement>İlgilendiğiniz denetim düzenlerini alın.  
  
2. <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> Belirli bir model için bir çağrı yapın veya sorgulayın. Bu yöntemler benzerdir, ancak model bulunamazsa <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> bir özel durum oluşturur ve <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> döndürür `false` .  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir <xref:System.Windows.Automation.AutomationElement> liste öğesi için alır ve bu öğeden bir alır <xref:System.Windows.Automation.SelectionItemPattern> .  
  
 [!code-csharp[UIAClient_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#103)]
 [!code-vb[UIAClient_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#103)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İstemciler İçin UI Otomasyon Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
