---
title: UI Otomasyonu Kullanarak Denetim Çağırma
description: UI otomasyonunu kullanarak belirli özellik koşullarına uyan bir denetim bulun, bir AutomationElement oluşturun, bir ınvokemodel alın ve denetimde Invoke kullanın.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- invoking controls
- UI Automation, invoking controls
- controls, invoking
ms.assetid: 5ee2de3f-256c-43ec-b64c-62ace91f9983
ms.openlocfilehash: 2347a620aab848bf6bcc649a9780aa5a3a520822
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168175"
---
# <a name="invoke-a-control-using-ui-automation"></a>UI Otomasyonu Kullanarak Denetim Çağırma
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu başlığı altında, aşağıdaki görevlerin nasıl gerçekleştirileceği gösterilmektedir:  
  
- Hedef uygulama için ağacın denetim görünümünü yürüyerek belirli özellik koşullarıyla eşleşen bir denetim bulun [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .  
  
- <xref:System.Windows.Automation.AutomationElement>Her denetim için oluşturun.  
  
- <xref:System.Windows.Automation.InvokePattern> [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Denetim modelini destekleyen, bulunan herhangi bir öğeden bir nesne elde edin <xref:System.Windows.Automation.InvokePattern> .  
  
- <xref:System.Windows.Automation.InvokePattern.Invoke%2A>Bir istemci olay işleyicisinden denetimi çağırmak için kullanın.  
  
## <a name="example"></a>Örnek  
 Bu örnek, <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> <xref:System.Windows.Automation.AutomationElement> <xref:System.Windows.Automation.InvokePattern> yöntemini kullanarak bir nesnesi oluşturmak ve bir denetimi çağırmak için sınıfının yöntemini kullanır <xref:System.Windows.Automation.InvokePattern.Invoke%2A> .  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
[!code-csharp[InvokePatternApp#1102](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1102)]
[!code-vb[InvokePatternApp#1102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1102)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Invokemodel, ExpandCollapsePattern ve Togglemodel örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InvokePattern)
