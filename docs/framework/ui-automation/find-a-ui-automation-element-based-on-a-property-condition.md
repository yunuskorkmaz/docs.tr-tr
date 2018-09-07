---
title: Özellik Koşulunu Temel Alan UI Otomasyon Öğesi Bulma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- elements, finding by property conditions
- UI Automation, finding elements by property conditions
ms.assetid: 3acaee5a-6ce8-4c3e-81c8-67e59eb74477
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 4c4f14f79960b98618a4f6a3450b1e1a2c05f731
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44097145"
---
# <a name="find-a-ui-automation-element-based-on-a-property-condition"></a>Özellik Koşulunu Temel Alan UI Otomasyon Öğesi Bulma
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu, bir öğenin içine nasıl gösteren kod örneği içerir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç tabanlı belirli bir özellik veya özellikleri.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, bir dizi özellik koşullarına belirtilir ilgilendiğiniz belirli bir öğenin (veya öğeleri) tanımlamak <xref:System.Windows.Automation.AutomationElement> ağaç. Bir arama için tüm eşleşen öğeleri ile gerçekleştirilir <xref:System.Windows.Automation.AutomationElement.FindAll%2A> içeren bir dizi yöntem <xref:System.Windows.Automation.AndCondition> eşleşen öğe sayısını sınırlamak için boolean operations.  
  
> [!NOTE]
>  Gelen ararken <xref:System.Windows.Automation.AutomationElement.RootElement%2A>, yalnızca doğrudan alt öğeleri almak çalışmanız gerekir. Alt öğeleri için arama, yüzlerce veya binlerce büyük olasılıkla bir yığın taşması ile elde edilen öğelerin bile aracılığıyla yineleme. Daha düşük bir düzeyde belirli bir öğeyi edinme çalışıyorsanız, uygulama penceresinin veya daha düşük bir düzeyde bir kapsayıcı aramanızı başlamanız gerekir.  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [InvokePattern'ı ve ExpandCollapsePattern'ı menü öğesi örneği](https://msdn.microsoft.com/library/b7fa141c-e2d1-4da2-a27f-81a7d1172210)  
 [UI Otomasyonu Öğelerini Alma](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)  
 [AutomationID Özelliğini Kullanma](../../../docs/framework/ui-automation/use-the-automationid-property.md)
