---
title: UI Otomasyon İş Parçacığı Oluşturma Sorunları
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, threading issues
- threading issues with UI Automation
ms.assetid: 0ab8d42c-5b8b-481b-b788-2caecc2f0191
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 7d8df325d18c3657d4955fa534d29bb7fdbc595c
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2018
ms.locfileid: "48846506"
---
# <a name="ui-automation-threading-issues"></a>UI Otomasyon İş Parçacığı Oluşturma Sorunları
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Neden [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] kendi ile etkileşim kurmak bir istemci uygulama çalıştığında kullanan Windows iletileri, çakışmaları meydana gelebilir [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] üzerinde [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] iş parçacığı. Bu çakışmaları, müşteri adayı için çok yavaş performans veya bile uygulamanın yanıt vermemesine neden.  
  
 İstemci uygulamanızın tüm öğeleri masaüstü ile etkileşim kurmak için amaçlanıyorsa, kendi dahil [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], tüm yapmalısınız [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ayrı bir iş parçacığında çağırır. Bu öğeleri bulma içerir (kullanarak örneğin, <xref:System.Windows.Automation.TreeWalker> veya <xref:System.Windows.Automation.AutomationElement.FindAll%2A> yöntemi) ve denetim desenlerini kullanma.  
  
 Güvenli hale getirmek [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] içinde çağıran bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olay işleyicisi, olay işleyicisi her zaman olmayan bir adı verilir çünkü[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] iş parçacığı. Ancak, istemci uygulamanızın gelebilir olaylara abone olurken [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], çağrısı yapmalısınız <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>, ya da bir ilgili yöntem üzerinde olmayan bir[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] iş parçacığı. Olay işleyicileri aynı iş parçacığında kaldırın.
