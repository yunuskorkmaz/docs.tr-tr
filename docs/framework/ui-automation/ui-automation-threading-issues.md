---
title: UI Otomasyon İş Parçacığı Oluşturma Sorunları
description: UI Otomasyonu iş parçacığı sorunları hakkında bilgi edinin. Örneğin, bir istemci uygulaması kullanıcı arabirimi iş parçacığında kendi Kullanıcı arabirimiyle etkileşime geçmeye çalışırsa çakışmalar oluşabilir.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, threading issues
- threading issues with UI Automation
ms.assetid: 0ab8d42c-5b8b-481b-b788-2caecc2f0191
ms.openlocfilehash: 290c26981d5eb993e2a9ab387f8d106aafa54efb
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86924545"
---
# <a name="ui-automation-threading-issues"></a>UI Otomasyon İş Parçacığı Oluşturma Sorunları
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu şekilde [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] Windows iletilerini kullanırken çakışmalar, bir istemci uygulaması [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] iş parçacığında kendi kendine etkileşim kurmaya çalıştığında meydana gelebilir [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] . Bu çakışmalar çok yavaş performansa yol açabilir, hatta uygulamanın yanıt vermemesine neden olabilir.  
  
 İstemci uygulamanızın, kendi masaüstündeki tüm öğelerle etkileşim kurması amaçlanıyorsa, [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] her türlü [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] çağrısı ayrı bir iş parçacığında yapmanız gerekir. Bu, öğeleri konumlandırmayı (örneğin, <xref:System.Windows.Automation.TreeWalker> veya <xref:System.Windows.Automation.AutomationElement.FindAll%2A> yöntemini kullanarak) ve denetim düzenlerini kullanmayı içerir.  
  
 Olay [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] işleyicisi her zaman iş parçacığı olmayan bir şekilde çağrıldığı için, bir olay işleyicisi içinde çağrı yapmak güvenlidir [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] . Ancak, istemci uygulamanızdan kaynaklanacak olaylara abone olurken, [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A> veya iş parçacığı olmayan bir ilgili yöntem çağrısı yapmanız gerekir [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] . Aynı iş parçacığında olay işleyicilerini kaldırın.
