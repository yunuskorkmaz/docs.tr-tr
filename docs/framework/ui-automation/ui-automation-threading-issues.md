---
title: UI Otomasyon İş Parçacığı Oluşturma Sorunları
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, threading issues
- threading issues with UI Automation
ms.assetid: 0ab8d42c-5b8b-481b-b788-2caecc2f0191
ms.openlocfilehash: 83b8ec67cff7006e736e0f65a7339b340b20d458
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57678598"
---
# <a name="ui-automation-threading-issues"></a>UI Otomasyon İş Parçacığı Oluşturma Sorunları
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Neden [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] kendi ile etkileşim kurmak bir istemci uygulama çalıştığında kullanan Windows iletileri, çakışmaları meydana gelebilir [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] üzerinde [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] iş parçacığı. Bu çakışmaları, müşteri adayı için çok yavaş performans veya bile uygulamanın yanıt vermemesine neden.  
  
 İstemci uygulamanızın tüm öğeleri masaüstü ile etkileşim kurmak için amaçlanıyorsa, kendi dahil [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], tüm yapmalısınız [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ayrı bir iş parçacığında çağırır. Bu öğeleri bulma içerir (kullanarak örneğin, <xref:System.Windows.Automation.TreeWalker> veya <xref:System.Windows.Automation.AutomationElement.FindAll%2A> yöntemi) ve denetim desenlerini kullanma.  
  
 Güvenli hale getirmek [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] içinde çağıran bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olay işleyicisi, olay işleyicisi her zaman olmayan bir adı verilir çünkü[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] iş parçacığı. Ancak, istemci uygulamanızın gelebilir olaylara abone olurken [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], çağrısı yapmalısınız <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>, ya da bir ilgili yöntem üzerinde olmayan bir[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] iş parçacığı. Olay işleyicileri aynı iş parçacığında kaldırın.
