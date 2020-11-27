---
title: UI Otomasyon Sağlayıcıda Olay Tetikleme
description: UI Otomasyon sağlayıcısından bir olayın nasıl oluşturulacağını gösteren bir örnek görürsünüz. Özel bir düğme denetimi uygulamasında bir UI Otomasyonu olayını başlatır.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, raising events
- raising UI Automation events
ms.assetid: 9fe2f01b-f7d8-49a8-a185-d4472b9976c0
ms.openlocfilehash: 73be7fd92f3fde90255326c51bed03427fd68e8d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96250495"
---
# <a name="raise-events-from-a-ui-automation-provider"></a>UI Otomasyon Sağlayıcıda Olay Tetikleme

> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu, bir UI Otomasyon sağlayıcısından bir olayın nasıl oluşturulacağını gösteren örnek kodu içerir.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnekte, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özel bir düğme denetimi uygulamasında bir olay tetiklenir. Uygulama, bir Kullanıcı Arabirimi Otomasyonu istemci uygulamasının bir düğme tıklamalarını benzetimini sağlar.  
  
 Gereksiz işleme engel olmak için örnek, <xref:System.Windows.Automation.Provider.AutomationInteropProvider.ClientsAreListening%2A> olayların yapılıp yapılmayacağını görmek için kontrol eder.  
  
 [!code-csharp[UIAProvider_snip#150](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAProvider_snip/CSharp/FragmentRoot.cs#150)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyon Sağlayıcılara Genel Bakış](ui-automation-providers-overview.md)
