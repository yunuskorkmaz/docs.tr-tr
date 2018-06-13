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
ms.openlocfilehash: da455b10425c9e0b20a644679358dde469ed92e5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33400763"
---
# <a name="find-a-ui-automation-element-based-on-a-property-condition"></a>Özellik Koşulunu Temel Alan UI Otomasyon Öğesi Bulma
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu, bir öğenin içine bulun gösteren kod örneği içerir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç dayalı belirli bir özellik veya özellikleri.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, bir dizi özellik koşulları belirtilir ilgi belirli bir öğenin (veya öğeleri) tanımlamak <xref:System.Windows.Automation.AutomationElement> ağacı. İle eşleşen tüm öğeleri için bir arama sonra gerçekleştirilen <xref:System.Windows.Automation.AutomationElement.FindAll%2A> bir dizi içerir yöntemi <xref:System.Windows.Automation.AndCondition> eşleşen öğe sayısını sınırlamak için boolean işlemleri.  
  
> [!NOTE]
>  Gelen ararken <xref:System.Windows.Automation.AutomationElement.RootElement%2A>, sadece doğrudan alt edinmeye. Alt öğeleri için bir arama yüzlerce veya binlerce büyük olasılıkla bir yığın taşması kaynaklanan öğelerinin bile yinelemek. Belirli bir öğenin alt düzeyde edinme çalışıyorsanız, Uygulama penceresinden veya daha düşük düzeydeki bir kapsayıcı aramanızı başlamanız gerekir.  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [InvokePattern'ı ve ExpandCollapsePattern'ı menü öğesi örneği](http://msdn.microsoft.com/library/b7fa141c-e2d1-4da2-a27f-81a7d1172210)  
 [UI Otomasyonu Öğelerini Alma](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)  
 [AutomationID Özelliğini Kullanma](../../../docs/framework/ui-automation/use-the-automationid-property.md)
