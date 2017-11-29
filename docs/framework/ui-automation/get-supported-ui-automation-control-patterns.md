---
title: "Desteklenen UI Otomasyon Denetim Düzenlerini Alma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- control patterns, getting
- UI Automation, getting control patterns
- getting, control patterns
ms.assetid: 006c54c9-50bf-48d9-a855-9d62eb95603a
caps.latest.revision: "10"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 8917890d86f059d85ad9b6a0bcf6d9a41d65585a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="get-supported-ui-automation-control-patterns"></a>Desteklenen UI Otomasyon Denetim Düzenlerini Alma
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konuda denetim düzeni nesneleri almak nasıl gösterilmektedir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] öğeleri.  
  
### <a name="obtain-all-control-patterns"></a>Tüm denetim düzenleri alın  
  
1.  Alma <xref:System.Windows.Automation.AutomationElement> olan denetim düzenleri ilgilendiğiniz.  
  
2.  Çağrı <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> öğesinden tüm denetim düzenlerini alma için.  
  
> [!CAUTION]
>  Bir istemci kullanmaz kesinlikle önerilir <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>. Performans ciddi bir şekilde etkilenmiş bu yöntemi çağırır <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> varolan her denetim düzeni için dahili olarak. Mümkünse, bir istemci çağırmalıdır <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> ilgi anahtar desenler için.  
  
### <a name="obtain-a-specific-control-pattern"></a>Bir özel denetim düzeni alın  
  
1.  Alma <xref:System.Windows.Automation.AutomationElement> olan denetim düzenleri ilgilendiğiniz.  
  
2.  Çağrı <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> veya <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> sorgulamak için belirli bir desen. Bu yöntemlere benzer, ancak düzeni bulunmazsa <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> bir özel durum oluşturur ve <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> döndürür `false`.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek alır bir <xref:System.Windows.Automation.AutomationElement> bir liste öğesi için ve edinir bir <xref:System.Windows.Automation.SelectionItemPattern> bu öğeden.  
  
 [!code-csharp[UIAClient_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#103)]
 [!code-vb[UIAClient_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#103)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İstemciler için UI Otomasyon denetim düzenleri](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
