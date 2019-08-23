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
ms.openlocfilehash: f17f3ad25f137bbf8d7cf88b43cc52dfdeeb3fd4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923733"
---
# <a name="invoke-a-control-using-ui-automation"></a>UI Otomasyonu Kullanarak Denetim Çağırma
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir. Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu başlığı altında, aşağıdaki görevlerin nasıl gerçekleştirileceği gösterilmektedir:  
  
- Hedef uygulama için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacın denetim görünümünü yürüyerek belirli özellik koşullarıyla eşleşen bir denetim bulun.  
  
- Her denetim <xref:System.Windows.Automation.AutomationElement> için oluşturun.  
  
- Denetim modelini <xref:System.Windows.Automation.InvokePattern> destekleyen, <xref:System.Windows.Automation.InvokePattern> bulunan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] herhangi bir öğeden bir nesne elde edin.  
  
- Bir <xref:System.Windows.Automation.InvokePattern.Invoke%2A> istemci olay işleyicisinden denetimi çağırmak için kullanın.  
  
## <a name="example"></a>Örnek  
 Bu <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> örnek, <xref:System.Windows.Automation.AutomationElement> yöntemini<xref:System.Windows.Automation.InvokePattern.Invoke%2A> kullanarak bir <xref:System.Windows.Automation.InvokePattern> nesnesi oluşturmak ve bir denetimi çağırmak için sınıfının yöntemini kullanır.  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
[!code-csharp[InvokePatternApp#1102](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1102)]
[!code-vb[InvokePatternApp#1102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1102)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Invokemodel, ExpandCollapsePattern ve Togglemodel örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InvokePattern)
