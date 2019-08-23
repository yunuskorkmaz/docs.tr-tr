---
title: UI Otomasyon İş Parçacığı Oluşturma Sorunları
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, threading issues
- threading issues with UI Automation
ms.assetid: 0ab8d42c-5b8b-481b-b788-2caecc2f0191
ms.openlocfilehash: f4820d2db6275e3c1ae9b55754b8cb6fec6fcc56
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69954057"
---
# <a name="ui-automation-threading-issues"></a>UI Otomasyon İş Parçacığı Oluşturma Sorunları
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir. Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu şekilde [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] Windows iletilerini kullanırken çakışmalar, bir istemci uygulaması [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] iş parçacığında kendi [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] kendine etkileşim kurmaya çalıştığında meydana gelebilir. Bu çakışmalar çok yavaş performansa yol açabilir, hatta uygulamanın yanıt vermemesine neden olabilir.  
  
 İstemci uygulamanızın, kendi [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]masaüstündeki tüm öğelerle etkileşim kurması amaçlanıyorsa, her türlü [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] çağrısı ayrı bir iş parçacığında yapmanız gerekir. Bu, öğeleri konumlandırmayı (örneğin, <xref:System.Windows.Automation.TreeWalker> <xref:System.Windows.Automation.AutomationElement.FindAll%2A> veya yöntemini kullanarak) ve denetim düzenlerini kullanmayı içerir.  
  
 Olay işleyicisi her zaman [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] iş parçacığı olmayan bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] şekilde çağrıldığı için, bir olay işleyicisi içinde çağrı yapmak güvenlidir. Ancak, istemci uygulamanızdan [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]kaynaklanacak olaylara abone olurken, veya[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] iş parçacığı olmayan bir ilgili Yöntem <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>çağrısı yapmanız gerekir. Aynı iş parçacığında olay işleyicilerini kaldırın.
