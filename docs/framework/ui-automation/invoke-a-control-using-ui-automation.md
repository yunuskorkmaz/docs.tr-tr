---
title: UI Otomasyonu Kullanarak Denetim Çağırma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- invoking controls
- UI Automation, invoking controls
- controls, invoking
ms.assetid: 5ee2de3f-256c-43ec-b64c-62ace91f9983
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: b4ee4b4929d5aa80ccfb91d07031b4ab195d311e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54654782"
---
# <a name="invoke-a-control-using-ui-automation"></a>UI Otomasyonu Kullanarak Denetim Çağırma
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu aşağıdaki görevlerin nasıl gerçekleştirileceğini gösterir:  
  
-   Denetimin görünümünü walking tarafından belirli özellik koşullara uyan bir denetimi bulmak [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] hedef uygulama için ağacı.  
  
-   Oluşturma bir <xref:System.Windows.Automation.AutomationElement> her denetim için.  
  
-   Elde bir <xref:System.Windows.Automation.InvokePattern> herhangi bir nesneden [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] öğe bulundu destekleyen <xref:System.Windows.Automation.InvokePattern> denetim düzeni.  
  
-   Kullanım <xref:System.Windows.Automation.InvokePattern.Invoke%2A> istemci olay işleyicisi denetiminden çağırmak için.  
  
## <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> yöntemi <xref:System.Windows.Automation.AutomationElement> sınıfı oluşturmak için bir <xref:System.Windows.Automation.InvokePattern> nesne ve kullanarak denetim çağırma <xref:System.Windows.Automation.InvokePattern.Invoke%2A> yöntemi.  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
[!code-csharp[InvokePatternApp#1102](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1102)]
[!code-vb[InvokePatternApp#1102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1102)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [InvokePattern'ı ve ExpandCollapsePattern'ı menü öğesi örneği](https://msdn.microsoft.com/library/b7fa141c-e2d1-4da2-a27f-81a7d1172210)
