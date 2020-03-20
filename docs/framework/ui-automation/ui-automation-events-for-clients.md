---
title: İstemciler İçin UI Otomasyon Olayları
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, events for clients
- events, UI Automation clients
ms.assetid: b909e388-3f24-4997-b6d4-bd9c35c2dc27
ms.openlocfilehash: d7105e9211c35e7d6125c3017e8b4b829a25b128
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179900"
---
# <a name="ui-automation-events-for-clients"></a>İstemciler İçin UI Otomasyon Olayları
> [!NOTE]
> Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır. Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu, [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] olayların UI Automation istemcileri tarafından nasıl kullanıldığını açıklar.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]müşterilerin ilgi çekici olaylara abone olmasını sağlar. Bu özellik, herhangi bir bilginin, yapının [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] veya devletin değişip değişmediğini görmek için sistemdeki tüm öğeleri sürekli olarak yoklama gereksinimini ortadan kaldırarak performansı artırır.  
  
 Verimlilik, yalnızca tanımlanmış bir kapsam dahilindeki olayları dinleme yeteneği yle de geliştirilir. Örneğin, istemci, ağaçtaki tüm [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] öğelerdeki odak değişikliği olaylarını veya yalnızca bir öğe ve onun torunlarını dinleyebilir.  
  
> [!NOTE]
> Tüm olası olayların bir [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] sağlayıcı tarafından yükseltildiğine varmayın. Örneğin, tüm özellik değişiklikleri, windows formları ve Win32 denetimleri için standart proxy sağlayıcıları tarafından olayların yükseltilmesine neden olmaz.  
  
 Olayların daha geniş [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bir görünümü [için, UI Otomasyon Etkinlikleri genel bakış](ui-automation-events-overview.md)bölümüne bakın.  
  
<a name="Subscribing_to_Events"></a>
## <a name="subscribing-to-events"></a>Etkinliklere Abone Olma  
 İstemci uygulamaları, aşağıdaki yöntemlerden birini kullanarak bir olay işleyicisini kaydederek belirli bir türdeki olaylara abone olur.  
  
|Yöntem|Olay Türü|Olay Bağımsız Değişkentürü|Temsilci Türü|  
|------------|----------------|--------------------------|-------------------|  
|<xref:System.Windows.Automation.Automation.AddAutomationFocusChangedEventHandler%2A>|Odak değişikliği|<xref:System.Windows.Automation.AutomationFocusChangedEventArgs>|<xref:System.Windows.Automation.AutomationFocusChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A>|Özellik değişikliği|<xref:System.Windows.Automation.AutomationPropertyChangedEventArgs>|<xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddStructureChangedEventHandler%2A>|Yapı değişikliği|<xref:System.Windows.Automation.StructureChangedEventArgs>|<xref:System.Windows.Automation.StructureChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>|Diğer tüm olaylar, bir<xref:System.Windows.Automation.AutomationEvent>|<xref:System.Windows.Automation.AutomationEventArgs> veya <xref:System.Windows.Automation.WindowClosedEventArgs>|<xref:System.Windows.Automation.AutomationEventHandler>|  
  
 Yöntemi aramadan önce, olayı işlemek için bir temsilci yöntemi oluşturmanız gerekir. İsterseniz, tek bir yöntemde farklı türde olayları işleyebilir ve bu yöntemi birden çok çağrıda tablodaki yöntemlerden birine geçirebilirsiniz. Örneğin, tek <xref:System.Windows.Automation.AutomationEventHandler> bir farklı olaylara göre farklı işlemek <xref:System.Windows.Automation.AutomationEventArgs.EventId%2A>için ayarlanabilir.  
  
> [!NOTE]
> Pencere kapalı olayları işlemek için, olay işleyicisi için <xref:System.Windows.Automation.WindowClosedEventArgs>geçirilen bağımsız değişken türünü ' olarak döküm Pencere [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] öğesi artık geçerli olmadığından, bilgi almak `sender` için parametreyi kullanamazsınız; bunun <xref:System.Windows.Automation.WindowClosedEventArgs.GetRuntimeId%2A> yerine kullanın.  
  
> [!CAUTION]
> Uygulamanız kendi etkinliklerinden etkinlik [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]alabiliyorsa, etkinliklere [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] abone olmak veya aboneliğinizi iptal etmek için uygulamanızın iş parçacığıkullanmayın. Bunu yapmak öngörülemeyen davranışlara yol açabilir. Daha fazla bilgi için [UI Automation Threading Issues'a](ui-automation-threading-issues.md)bakın.  
  
 Kapatma da veya [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayların artık uygulamanın ilgisini çeken bir şey olmadığında, Kullanıcı Arabirimi Otomasyonu istemcileri aşağıdaki yöntemlerden birini aramalıdır.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationEventHandler%2A>|'yi kullanarak <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>kayıtlı bir olay işleyicisi kaydını boşaltıyor.|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationFocusChangedEventHandler%2A>|'yi kullanarak <xref:System.Windows.Automation.Automation.AddAutomationFocusChangedEventHandler%2A>kayıtlı bir olay işleyicisi kaydını boşaltıyor.|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>|'yi kullanarak <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A>kayıtlı bir olay işleyicisi kaydını boşaltıyor.|  
|<xref:System.Windows.Automation.Automation.RemoveAllEventHandlers%2A>|Tüm kayıtlı olay işleyicilerinin kaydını silindiri.|  
  
 Örneğin kod, [bkz.](subscribe-to-ui-automation-events.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyon Olaylarına Abone Olma](subscribe-to-ui-automation-events.md)
- [UI Otomasyonu Olaylarına Genel Bakış](ui-automation-events-overview.md)
- [UI Otomasyon Özelliklerine Genel Bakış](ui-automation-properties-overview.md)
- [TrackFocus Örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/FocusTracker)
