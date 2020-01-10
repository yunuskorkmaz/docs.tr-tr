---
title: İstemciler İçin UI Otomasyon Olayları
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, events for clients
- events, UI Automation clients
ms.assetid: b909e388-3f24-4997-b6d4-bd9c35c2dc27
ms.openlocfilehash: 6d4525aeea458e1ec810efa659f373a2b5f21f57
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75741314"
---
# <a name="ui-automation-events-for-clients"></a>İstemciler İçin UI Otomasyon Olayları
> [!NOTE]
> Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu, [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] olaylarının UI Otomasyon istemcileri tarafından nasıl kullanıldığını açıklar.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], istemcilerin ilgilendiğiniz olaylara abone olmalarını sağlar. Bu özellik, herhangi bir bilgi, yapı veya durumun değişip değişmediğini görmek için sistemdeki tüm [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğelerini sürekli olarak yoklamaya gerek gereksinimini ortadan kaldırarak performansı geliştirir.  
  
 Verimlilik Ayrıca yalnızca tanımlı bir kapsamdaki olayları dinlemek için de geliştirilmiştir. Örneğin, bir istemci, ağaçtaki tüm [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] öğelerinde veya yalnızca bir öğe ve onun alt öğeleri üzerinde odak değişikliği olaylarını dinleyebilir.  
  
> [!NOTE]
> Tüm olası olayların bir [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] sağlayıcısı tarafından gerçekleştiğini varsaymayın. Örneğin, tüm özellik değişiklikleri, olayların [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] ve Win32 denetimleri için standart proxy sağlayıcıları tarafından oluşturulmasına neden olmaz.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olaylarının daha geniş bir görünümü için bkz. [UI Otomasyonu olaylarına genel bakış](ui-automation-events-overview.md).  
  
<a name="Subscribing_to_Events"></a>   
## <a name="subscribing-to-events"></a>Olaylara abone olma  
 İstemci uygulamaları, aşağıdaki yöntemlerden birini kullanarak bir olay işleyicisini kaydederek belirli bir türdeki olaylara abone olur.  
  
|Yöntem|Olay Türü|Olay bağımsız değişkenleri türü|Temsilci türü|  
|------------|----------------|--------------------------|-------------------|  
|<xref:System.Windows.Automation.Automation.AddAutomationFocusChangedEventHandler%2A>|Odak değişikliği|<xref:System.Windows.Automation.AutomationFocusChangedEventArgs>|<xref:System.Windows.Automation.AutomationFocusChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A>|Özellik değişikliği|<xref:System.Windows.Automation.AutomationPropertyChangedEventArgs>|<xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddStructureChangedEventHandler%2A>|Yapı değişikliği|<xref:System.Windows.Automation.StructureChangedEventArgs>|<xref:System.Windows.Automation.StructureChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>|<xref:System.Windows.Automation.AutomationEvent> tarafından tanımlanan diğer tüm olaylar|<xref:System.Windows.Automation.AutomationEventArgs> veya <xref:System.Windows.Automation.WindowClosedEventArgs>|<xref:System.Windows.Automation.AutomationEventHandler>|  
  
 Yöntemi çağırmadan önce, olayı işlemek için bir temsilci yöntemi oluşturmanız gerekir. İsterseniz, farklı türdeki olayları tek bir yöntemde işleyebilir ve bu yöntemi tablodaki yöntemlerden birine birden çok çağrıda geçirebilirsiniz. Örneğin, tek bir <xref:System.Windows.Automation.AutomationEventHandler> <xref:System.Windows.Automation.AutomationEventArgs.EventId%2A>göre farklı olayları işlemek üzere ayarlanabilir.  
  
> [!NOTE]
> Pencere kapalı olaylarını işlemek için, olay işleyicisine geçirilen bağımsız değişken türünü <xref:System.Windows.Automation.WindowClosedEventArgs>olarak atayın. Pencerenin [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] öğesi artık geçerli olmadığından, bilgileri almak için `sender` parametresini kullanamazsınız; Bunun yerine <xref:System.Windows.Automation.WindowClosedEventArgs.GetRuntimeId%2A> kullanın.  
  
> [!CAUTION]
> Uygulamanız kendi [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]olayları alabiliyorsanız, olaylara abone olmak veya aboneliğinizi kaldırmak için uygulamanızın [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] iş parçacığını kullanmayın. Bunun yapılması öngörülemeyen davranışlara neden olabilirler. Daha fazla bilgi için bkz. [UI Otomasyonu Iş parçacığı sorunları](ui-automation-threading-issues.md).  
  
 Kapatılırken veya [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayları uygulamaya artık ilgilenmeyen Kullanıcı Arabirimi Otomasyonu istemcileri aşağıdaki yöntemlerden birini çağırmalıdır.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationEventHandler%2A>|<xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>kullanılarak kaydedilmiş bir olay işleyicisinin kaydını siler.|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationFocusChangedEventHandler%2A>|<xref:System.Windows.Automation.Automation.AddAutomationFocusChangedEventHandler%2A>kullanılarak kaydedilmiş bir olay işleyicisinin kaydını siler.|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>|<xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A>kullanılarak kaydedilmiş bir olay işleyicisinin kaydını siler.|  
|<xref:System.Windows.Automation.Automation.RemoveAllEventHandlers%2A>|Tüm kayıtlı olay işleyicilerinin kaydını siler.|  
  
 Örnek kod için bkz. [UI Otomasyon olaylarına abone olma](subscribe-to-ui-automation-events.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Olaylarına Abone Olma](subscribe-to-ui-automation-events.md)
- [UI Otomasyonu Olaylarına Genel Bakış](ui-automation-events-overview.md)
- [UI Otomasyonu Özelliklerine Genel Bakış](ui-automation-properties-overview.md)
- [TrackFocus örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/FocusTracker)
