---
title: UI Otomasyon İş Parçacığı Oluşturma Sorunları
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, threading issues
- threading issues with UI Automation
ms.assetid: 0ab8d42c-5b8b-481b-b788-2caecc2f0191
ms.openlocfilehash: 8dc21a680a19933e9db8d52a0e6b7e6ffdd333f8
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74800831"
---
# <a name="ui-automation-threading-issues"></a>UI Otomasyon İş Parçacığı Oluşturma Sorunları
> [!NOTE]
> Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] Windows iletilerini kullandığı şekilde, bir istemci uygulaması [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] iş parçacığında kendi [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] etkileşimde bulunmak istediğinde çakışmalar meydana gelebilir. Bu çakışmalar çok yavaş performansa yol açabilir, hatta uygulamanın yanıt vermemesine neden olabilir.  
  
 İstemci uygulamanızın, kendi [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]dahil olmak üzere masaüstündeki tüm öğelerle etkileşim kurması amaçlanıyorsa, tüm [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] çağrılarını ayrı bir iş parçacığında yapmanız gerekir. Bu, öğeleri konumlandırmayı (örneğin, <xref:System.Windows.Automation.TreeWalker> veya <xref:System.Windows.Automation.AutomationElement.FindAll%2A> yöntemini kullanarak) ve denetim düzenlerini kullanmayı içerir.  
  
 Olay işleyicisi her zaman[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] olmayan bir iş parçacığında çağrıldığından, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olay işleyicisi içinde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] çağrıları yapmak güvenlidir. Ancak, istemci uygulamanızın [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]kaynaklı olaylara abone olurken[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] olmayan bir iş parçacığında <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>veya ilgili bir yöntem çağrısı yapmanız gerekir. Aynı iş parçacığında olay işleyicilerini kaldırın.
