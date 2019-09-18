---
title: İstemciler İçin UI Otomasyon Olayları
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, events for clients
- events, UI Automation clients
ms.assetid: b909e388-3f24-4997-b6d4-bd9c35c2dc27
ms.openlocfilehash: f4ce2d996d5a1a6ecd149118b7499650882a732f
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71042286"
---
# <a name="ui-automation-events-for-clients"></a>İstemciler İçin UI Otomasyon Olayları
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir. Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konuda, olayların [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] UI Otomasyon istemcileri tarafından nasıl kullanıldığı açıklanmaktadır.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]istemcilerin ilgilendiğiniz olaylara abone olmalarını sağlar. Bu özellik, herhangi bir bilgi, yapı veya durumun değişip değişmediğini görmek [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] için sistemdeki tüm öğeleri sürekli olarak yoklamaya gerek gereksinimini ortadan kaldırarak performansı geliştirir.  
  
 Verimlilik Ayrıca yalnızca tanımlı bir kapsamdaki olayları dinlemek için de geliştirilmiştir. Örneğin, bir istemci, ağaç içindeki tüm [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] öğelerde veya yalnızca bir öğe ve alt öğeleri üzerinde odak değişikliği olaylarını dinleyebilir.  
  
> [!NOTE]
> Tüm olası olayların bir [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] sağlayıcı tarafından gerçekleştiğini varsaymayın. Örneğin, tüm özellik değişiklikleri, olayların standart proxy sağlayıcıları [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] ve [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] denetimleri tarafından oluşturulmasına neden olmaz.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Olayların daha geniş bir görünümü için bkz. [UI Otomasyonu olaylarına genel bakış](ui-automation-events-overview.md).  
  
<a name="Subscribing_to_Events"></a>   
## <a name="subscribing-to-events"></a>Olaylara abone olma  
 İstemci uygulamaları, aşağıdaki yöntemlerden birini kullanarak bir olay işleyicisini kaydederek belirli bir türdeki olaylara abone olur.  
  
|Yöntem|Olay türü|Olay bağımsız değişkenleri türü|Temsilci türü|  
|------------|----------------|--------------------------|-------------------|  
|<xref:System.Windows.Automation.Automation.AddAutomationFocusChangedEventHandler%2A>|Odak değişikliği|<xref:System.Windows.Automation.AutomationFocusChangedEventArgs>|<xref:System.Windows.Automation.AutomationFocusChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A>|Özellik değişikliği|<xref:System.Windows.Automation.AutomationPropertyChangedEventArgs>|<xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddStructureChangedEventHandler%2A>|Yapı değişikliği|<xref:System.Windows.Automation.StructureChangedEventArgs>|<xref:System.Windows.Automation.StructureChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>|Tarafından tanımlanan tüm diğer olaylar<xref:System.Windows.Automation.AutomationEvent>|<xref:System.Windows.Automation.AutomationEventArgs> veya <xref:System.Windows.Automation.WindowClosedEventArgs>|<xref:System.Windows.Automation.AutomationEventHandler>|  
  
 Yöntemi çağırmadan önce, olayı işlemek için bir temsilci yöntemi oluşturmanız gerekir. İsterseniz, farklı türdeki olayları tek bir yöntemde işleyebilir ve bu yöntemi tablodaki yöntemlerden birine birden çok çağrıda geçirebilirsiniz. Örneğin, tek <xref:System.Windows.Automation.AutomationEventHandler> bir, çeşitli olayları <xref:System.Windows.Automation.AutomationEventArgs.EventId%2A>öğesine göre farklı şekilde işlemek üzere ayarlanabilir.  
  
> [!NOTE]
> Pencere kapalı olaylarını işlemek için, olay işleyicisine geçirilen bağımsız değişken türünü olarak <xref:System.Windows.Automation.WindowClosedEventArgs>atayın. Pencerenin öğesi artık geçerli olmadığından, bilgileri almak için `sender` parametresini kullanamazsınız; bunun yerine kullanın <xref:System.Windows.Automation.WindowClosedEventArgs.GetRuntimeId%2A>. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]  
  
> [!CAUTION]
> Uygulamanız kendi [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]etkinliklerini alabilir, olaylara abone olmak veya aboneliği kaldırmak için [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] uygulamanızın iş parçacığını kullanmayın. Bunun yapılması öngörülemeyen davranışlara neden olabilirler. Daha fazla bilgi için bkz. [UI Otomasyonu Iş parçacığı sorunları](ui-automation-threading-issues.md).  
  
 Kapatılırken veya [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olaylar uygulamaya artık ilgilenmeyen Kullanıcı Arabirimi Otomasyonu istemcileri aşağıdaki yöntemlerden birini çağırmalıdır.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationEventHandler%2A>|Kullanılarak <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>kaydedilmiş bir olay işleyicisinin kaydını siler.|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationFocusChangedEventHandler%2A>|Kullanılarak <xref:System.Windows.Automation.Automation.AddAutomationFocusChangedEventHandler%2A>kaydedilmiş bir olay işleyicisinin kaydını siler.|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>|Kullanılarak <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A>kaydedilmiş bir olay işleyicisinin kaydını siler.|  
|<xref:System.Windows.Automation.Automation.RemoveAllEventHandlers%2A>|Tüm kayıtlı olay işleyicilerinin kaydını siler.|  
  
 Örnek kod için bkz. [UI Otomasyon olaylarına abone olma](subscribe-to-ui-automation-events.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Olaylarına Abone Olma](subscribe-to-ui-automation-events.md)
- [UI Otomasyonu Olaylarına Genel Bakış](ui-automation-events-overview.md)
- [UI Otomasyonu Özelliklerine Genel Bakış](ui-automation-properties-overview.md)
- [TrackFocus örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/FocusTracker)
