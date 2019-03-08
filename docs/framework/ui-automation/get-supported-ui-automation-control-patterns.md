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
ms.openlocfilehash: 752a995cd8b0d1ad64accb7a230566e95b113916
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57676960"
---
# <a name="get-supported-ui-automation-control-patterns"></a>Desteklenen UI Otomasyon Denetim Düzenlerini Alma
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konuda, Denetim düzeni nesnelerden alma işlemi gösterilmektedir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] öğeleri.  
  
### <a name="obtain-all-control-patterns"></a>Tüm denetim düzenleri elde  
  
1.  Alma <xref:System.Windows.Automation.AutomationElement> , Denetim desenleri ilgilendiğiniz.  
  
2.  Çağrı <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> öğesinden tüm denetim desenlerini alma için.  
  
> [!CAUTION]
>  Bir istemci değil kullanmanızı önemle tavsiye edilir <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>. Performans ciddi bir şekilde etkilenecek bu yöntem çağrısı <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> mevcut her denetim düzeni için dahili olarak. Mümkünse, bir istemci çağırmalıdır <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> ilgilendiğiniz anahtar desenleri için.  
  
### <a name="obtain-a-specific-control-pattern"></a>Bir özel denetim düzeni alın  
  
1.  Alma <xref:System.Windows.Automation.AutomationElement> , Denetim desenleri ilgilendiğiniz.  
  
2.  Çağrı <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> veya <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> sorgulamak için belirli bir desen. Bu yöntemler benzerdir ancak deseni bulunamazsa <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> özel durum harekete ve <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> döndürür `false`.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek alır bir <xref:System.Windows.Automation.AutomationElement> bir liste öğesi için ve edinir bir <xref:System.Windows.Automation.SelectionItemPattern> bu öğeden.  
  
 [!code-csharp[UIAClient_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#103)]
 [!code-vb[UIAClient_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#103)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [İstemciler İçin UI Otomasyonu Denetim Düzenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
