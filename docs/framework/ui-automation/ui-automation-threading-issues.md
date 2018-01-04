---
title: "UI Otomasyon İş Parçacığı Oluşturma Sorunları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, threading issues
- threading issues with UI Automation
ms.assetid: 0ab8d42c-5b8b-481b-b788-2caecc2f0191
caps.latest.revision: "9"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 9e5c38f5c4681210a4f3be552a3f08be3962bc2b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ui-automation-threading-issues"></a>UI Otomasyon İş Parçacığı Oluşturma Sorunları
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Yol nedeniyle [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] kullanan Windows iletileri, çakışmaları kendi ile etkileşim kurmak bir istemci uygulaması çalıştığında oluşabilir [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] üzerinde [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] iş parçacığı. Bu çakışmalar için çok yavaş performans neden veya hatta uygulamasının yanıt vermemesine neden.  
  
 İstemci uygulamanız tüm öğeleri masaüstü ile etkileşimine izin amaçlanıyorsa, kendi dahil [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], tüm olmalısınız [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ayrı bir iş parçacığı üzerinde çağırır. Bu öğeleri bulma içerir (kullanarak örneğin, <xref:System.Windows.Automation.TreeWalker> veya <xref:System.Windows.Automation.AutomationElement.FindAll%2A> yöntemi) ve denetim düzenleri kullanma.  
  
 Olun güvenlidir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] içinde çağıran bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olay işleyicisi, olay işleyicisi her zaman olmayan bir üzerinde çağrıldığı için[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] iş parçacığı. Ancak, istemci uygulamanızın kaynaklanan olaylara abone olurken [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], çağrısı yapmak <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>, veya üzerinde olmayan bir ilgili bir yöntemi[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] iş parçacığı. İş parçacığı üzerinde olay işleyicileri kaldırın.
