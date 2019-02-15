---
title: İstemciler İçin UI Otomasyon Olayları
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, events for clients
- events, UI Automation clients
ms.assetid: b909e388-3f24-4997-b6d4-bd9c35c2dc27
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: b4ab95470a1b377d1768cf30b32f170b544d225e
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56305798"
---
# <a name="ui-automation-events-for-clients"></a>İstemciler İçin UI Otomasyon Olayları
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu açıklar nasıl [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] olayları UI Otomasyon istemcileri tarafından kullanılır.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] İlgilendiğiniz olaylara abone etmesine olanak tanır. Bu özellik tüm sürekli yoklama yapma ihtiyacını ortadan kaldırarak performansını geliştirir [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] sistemde herhangi bir bilgi, yapı veya durumu değişip değişmediğini öğeleri.  
  
 Verimliliği tarafından tanımlanan kapsam içinde yalnızca olayları dinler olanağı da gelişmiştir. Örneğin, bir istemci tüm odak değişiklik olayları dinleyebilirsiniz [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] öğeleri ağacında ya da yalnızca bir öğe ve alt öğeleri.  
  
> [!NOTE]
>  Tüm olası olayları tarafından yükseltilir varsaymayın bir [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] sağlayıcısı. Örneğin, tüm özellik değişiklikleri için standart proxy sağlayıcıları tarafından harekete geçirilen olayları neden [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] ve [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] kontrol eder.  
  
 Daha geniş bir görünüm için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayları görmek [UI Otomasyonu olaylarına genel bakış](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
<a name="Subscribing_to_Events"></a>   
## <a name="subscribing-to-events"></a>Olaylara abone olma  
 İstemci uygulamaları, belirli türde olaylar için aşağıdaki yöntemlerden birini kullanarak bir olay işleyicisi kaydederek abone olun.  
  
|Yöntem|Olay türü|Olay bağımsız değişkenleri|Temsilci türü|  
|------------|----------------|--------------------------|-------------------|  
|<xref:System.Windows.Automation.Automation.AddAutomationFocusChangedEventHandler%2A>|Odak Değiştir|<xref:System.Windows.Automation.AutomationFocusChangedEventArgs>|<xref:System.Windows.Automation.AutomationFocusChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A>|Özellik değişikliği|<xref:System.Windows.Automation.AutomationPropertyChangedEventArgs>|<xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddStructureChangedEventHandler%2A>|Yapı değişiklik|<xref:System.Windows.Automation.StructureChangedEventArgs>|<xref:System.Windows.Automation.StructureChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>|Tarafından tanımlanan tüm diğer olaylar bir <xref:System.Windows.Automation.AutomationEvent>|<xref:System.Windows.Automation.AutomationEventArgs> veya <xref:System.Windows.Automation.WindowClosedEventArgs>|<xref:System.Windows.Automation.AutomationEventHandler>|  
  
 Yöntemini çağırmadan önce olayı işlemek için bir temsilci yöntemi oluşturmanız gerekir. İsterseniz, farklı türde tek bir yöntem olayları işlemek ve bu yöntem yöntemlerinden tablosunda birden çok çağrı geçirin. Örneğin, bir tek <xref:System.Windows.Automation.AutomationEventHandler> farklı aşağıdakilere göre çeşitli olayları işlemek için ayarlanabilir <xref:System.Windows.Automation.AutomationEventArgs.EventId%2A>.  
  
> [!NOTE]
>  Pencere kapalı olayları işlemek için olay işleyicisi olarak geçirilen bağımsız değişken türü dönüştürme <xref:System.Windows.Automation.WindowClosedEventArgs>. Çünkü [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] için pencere öğesi artık geçerli değil; kullanamazsınız `sender` ; bilgi almak için parametre kullanmak <xref:System.Windows.Automation.WindowClosedEventArgs.GetRuntimeId%2A> yerine.  
  
> [!CAUTION]
>  Uygulamanızı olayları kendi alabilirse [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], uygulamanızın kullanmayın [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] olaylara abone veya aboneliğinizi iptal etmek için iş parçacığı. Bunun yapılması, beklenmedik davranışa neden olabilir. Daha fazla bilgi için [UI Otomasyon iş parçacığı oluşturma sorunları](../../../docs/framework/ui-automation/ui-automation-threading-issues.md).  
  
 Kapatma sırasında veya [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayları artık uygulama ilgi, UI Otomasyon istemcileri aşağıdaki yöntemlerden birini çağırmalıdır.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationEventHandler%2A>|Kullanılarak kaydedilen bir olay işleyicisi kaydını siler <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>.|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationFocusChangedEventHandler%2A>|Kullanılarak kaydedilen bir olay işleyicisi kaydını siler <xref:System.Windows.Automation.Automation.AddAutomationFocusChangedEventHandler%2A>.|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>|Kullanılarak kaydedilen bir olay işleyicisi kaydını siler <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A>.|  
|<xref:System.Windows.Automation.Automation.RemoveAllEventHandlers%2A>|Tüm kayıtlı olay işleyicilerinin kaydını siler.|  
  
 Örnek kod için bkz: [UI Otomasyon olaylarına abone olma](../../../docs/framework/ui-automation/subscribe-to-ui-automation-events.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [UI Otomasyonu Olaylarına Abone Olma](../../../docs/framework/ui-automation/subscribe-to-ui-automation-events.md)
- [UI Otomasyonu Olaylarına Genel Bakış](../../../docs/framework/ui-automation/ui-automation-events-overview.md)
- [UI Otomasyonu Özelliklerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-properties-overview.md)
- [TrackFocus örnek](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/FocusTracker)
