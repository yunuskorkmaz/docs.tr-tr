---
title: Özellik Koşulunu Temel Alan UI Otomasyon Öğesi Bulma
description: Özellik koşulunu temel alan UI Otomasyonu öğesi bulun. Belirli bir özelliği veya özellikleri temel alan UI Otomasyon ağacı içindeki bir öğeyi bulun.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- elements, finding by property conditions
- UI Automation, finding elements by property conditions
ms.assetid: 3acaee5a-6ce8-4c3e-81c8-67e59eb74477
ms.openlocfilehash: 5e5fa4fde9049bd87b2722fa9b7d084d96ff6f42
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168437"
---
# <a name="find-a-ui-automation-element-based-on-a-property-condition"></a>Özellik Koşulunu Temel Alan UI Otomasyon Öğesi Bulma
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] belirli bir özellik veya özelliklere göre ağaç içindeki bir öğenin nasıl bulunacağını gösteren örnek kodu içerir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, ağaçta ilgilendiğiniz belirli bir öğeyi (veya öğeleri) tanımlayan bir özellik koşulları kümesi belirtilmiştir <xref:System.Windows.Automation.AutomationElement> . Daha sonra eşleşen <xref:System.Windows.Automation.AutomationElement.FindAll%2A> <xref:System.Windows.Automation.AndCondition> öğelerin sayısını sınırlamak için bir dizi Boole işlemi içeren yöntemiyle, tüm eşleşen öğeler için arama yapılır.  
  
> [!NOTE]
> ' Dan arama yaparken <xref:System.Windows.Automation.AutomationElement.RootElement%2A> , yalnızca doğrudan alt öğe edinmeyi denemeniz gerekir. Alt öğeler için arama yüzlerce veya hatta binlerce öğe aracılığıyla yineleyebilir ve muhtemelen yığın taşmasına neden olabilir. Daha düşük bir düzeyde belirli bir öğe edinmeye çalışıyorsanız, aramanızı uygulama penceresinden veya bir kapsayıcıdan daha düşük bir düzeyde başlatmanız gerekir.  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Invokemodel ve ExpandCollapsePattern menü öğesi örneği](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771636(v=vs.90))
- [UI Otomasyon Öğelerini Alma](obtaining-ui-automation-elements.md)
- [AutomationID Özelliğini Kullanma](use-the-automationid-property.md)
