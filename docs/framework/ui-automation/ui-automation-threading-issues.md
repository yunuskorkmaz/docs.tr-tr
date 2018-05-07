---
title: UI Otomasyon İş Parçacığı Oluşturma Sorunları
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, threading issues
- threading issues with UI Automation
ms.assetid: 0ab8d42c-5b8b-481b-b788-2caecc2f0191
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: a9f49a99db7a4f7d118bd86bbe723a633c1b10ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="ui-automation-threading-issues"></a>UI Otomasyon İş Parçacığı Oluşturma Sorunları
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Yol nedeniyle [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] kullanan Windows iletileri, çakışmaları kendi ile etkileşim kurmak bir istemci uygulaması çalıştığında oluşabilir [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] üzerinde [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] iş parçacığı. Bu çakışmalar için çok yavaş performans neden veya hatta uygulamasının yanıt vermemesine neden.  
  
 İstemci uygulamanız tüm öğeleri masaüstü ile etkileşimine izin amaçlanıyorsa, kendi dahil [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], tüm olmalısınız [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ayrı bir iş parçacığı üzerinde çağırır. Bu öğeleri bulma içerir (kullanarak örneğin, <xref:System.Windows.Automation.TreeWalker> veya <xref:System.Windows.Automation.AutomationElement.FindAll%2A> yöntemi) ve denetim düzenleri kullanma.  
  
 Olun güvenlidir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] içinde çağıran bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olay işleyicisi, olay işleyicisi her zaman olmayan bir üzerinde çağrıldığı için[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] iş parçacığı. Ancak, istemci uygulamanızın kaynaklanan olaylara abone olurken [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], çağrısı yapmak <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>, veya üzerinde olmayan bir ilgili bir yöntemi[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] iş parçacığı. İş parçacığı üzerinde olay işleyicileri kaldırın.
