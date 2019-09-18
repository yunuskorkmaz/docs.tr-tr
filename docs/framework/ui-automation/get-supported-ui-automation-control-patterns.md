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
ms.openlocfilehash: 133dabe861fbbcf5cac3fbb8669b78e582f8b87b
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043656"
---
# <a name="get-supported-ui-automation-control-patterns"></a>Desteklenen UI Otomasyon Denetim Düzenlerini Alma
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir. Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] öğelerinden denetim deseninin nesnelerinin nasıl alınacağını gösterir.  
  
### <a name="obtain-all-control-patterns"></a>Tüm denetim desenlerini al  
  
1. <xref:System.Windows.Automation.AutomationElement> İlgilendiğiniz denetim düzenlerini alın.  
  
2. Öğesinden <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> tüm denetim desenlerini almak için çağırın.  
  
> [!CAUTION]
> İstemcinin kullanmamaları <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>önemle önerilir. Bu yöntem, var olan her denetim deseninin dahili <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> olarak çağırdığı için performans ciddi bir şekilde etkilenebilir. Mümkünse, bir istemci ilgilendiğiniz önemli desenleri <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> çağırmalıdır.  
  
### <a name="obtain-a-specific-control-pattern"></a>Belirli bir denetim deseninin elde edileceği  
  
1. <xref:System.Windows.Automation.AutomationElement> İlgilendiğiniz denetim düzenlerini alın.  
  
2. Belirli <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> bir <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> model için bir çağrı yapın veya sorgulayın. Bu yöntemler benzerdir, ancak model bulunamazsa <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> bir özel durum oluşturur ve <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> döndürür `false`.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir liste öğesi <xref:System.Windows.Automation.AutomationElement> için alır ve bu öğeden bir <xref:System.Windows.Automation.SelectionItemPattern> alır.  
  
 [!code-csharp[UIAClient_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#103)]
 [!code-vb[UIAClient_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#103)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](ui-automation-control-patterns-for-clients.md)
