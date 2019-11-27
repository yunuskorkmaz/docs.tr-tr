---
title: Desteklenen UI Otomasyon Denetim Düzenlerini Alma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- control patterns, getting
- UI Automation, getting control patterns
- getting, control patterns
ms.assetid: 006c54c9-50bf-48d9-a855-9d62eb95603a
ms.openlocfilehash: b1da13cf5eb39a61f40848a5f199cfd39b16d7c7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435644"
---
# <a name="get-supported-ui-automation-control-patterns"></a>Desteklenen UI Otomasyon Denetim Düzenlerini Alma
> [!NOTE]
> Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] öğelerinden denetim deseninin nesnelerinin nasıl alınacağını gösterir.  
  
### <a name="obtain-all-control-patterns"></a>Tüm denetim desenlerini al  
  
1. Denetim desenlerini ilgilendiğiniz <xref:System.Windows.Automation.AutomationElement> alın.  
  
2. Öğeden tüm denetim desenlerini almak için <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> çağırın.  
  
> [!CAUTION]
> İstemcinin <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>kullanmamaları önemle önerilir. Bu yöntem, var olan her denetim deseninin dahili <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> çağırdığı için performans ciddi bir şekilde etkilenebilir. Mümkünse, bir istemci ilgilendiğiniz önemli desenler için <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> çağırmalıdır.  
  
### <a name="obtain-a-specific-control-pattern"></a>Belirli bir denetim deseninin elde edileceği  
  
1. Denetim desenlerini ilgilendiğiniz <xref:System.Windows.Automation.AutomationElement> alın.  
  
2. Belirli bir kalıbı sorgulamak için <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> veya <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> çağırın. Bu yöntemler benzerdir, ancak model bulunmazsa <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> bir özel durum oluşturur ve <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> `false`döndürür.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir liste öğesi için bir <xref:System.Windows.Automation.AutomationElement> alır ve bu öğeden bir <xref:System.Windows.Automation.SelectionItemPattern> edinir.  
  
 [!code-csharp[UIAClient_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#103)]
 [!code-vb[UIAClient_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#103)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
