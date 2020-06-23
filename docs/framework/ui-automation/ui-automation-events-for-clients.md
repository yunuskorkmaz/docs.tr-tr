---
title: İstemciler İçin UI Otomasyon Olayları
description: Microsoft UI Otomasyonu olaylarının .NET 'teki UI Otomasyon istemcileri tarafından nasıl kullanıldığı hakkında bilgi edinin. UI Otomasyonu, istemcilerin ilgilendiğiniz olaylara abone olmalarını sağlar.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, events for clients
- events, UI Automation clients
ms.assetid: b909e388-3f24-4997-b6d4-bd9c35c2dc27
ms.openlocfilehash: 84568cf228a30535ec603cdad5bddbfd5697be0a
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903746"
---
# <a name="ui-automation-events-for-clients"></a>İstemciler İçin UI Otomasyon Olayları
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konuda [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] , OLAYLARıN UI Otomasyon istemcileri tarafından nasıl kullanıldığı açıklanmaktadır.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]istemcilerin ilgilendiğiniz olaylara abone olmalarını sağlar. Bu özellik [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] , herhangi bir bilgi, yapı veya durumun değişip değişmediğini görmek için sistemdeki tüm öğeleri sürekli olarak yoklamaya gerek gereksinimini ortadan kaldırarak performansı geliştirir.  
  
 Verimlilik Ayrıca yalnızca tanımlı bir kapsamdaki olayları dinlemek için de geliştirilmiştir. Örneğin, bir istemci, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç içindeki tüm öğelerde veya yalnızca bir öğe ve alt öğeleri üzerinde odak değişikliği olaylarını dinleyebilir.  
  
> [!NOTE]
> Tüm olası olayların bir sağlayıcı tarafından gerçekleştiğini varsaymayın [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] . Örneğin, tüm özellik değişiklikleri, olayların Windows Forms ve Win32 denetimleri için standart proxy sağlayıcıları tarafından oluşturulmasına neden olmaz.  
  
 Olayların daha geniş bir görünümü için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [UI Otomasyonu olaylarına genel bakış](ui-automation-events-overview.md).  
  
<a name="Subscribing_to_Events"></a>
## <a name="subscribing-to-events"></a>Olaylara abone olma  
 İstemci uygulamaları, aşağıdaki yöntemlerden birini kullanarak bir olay işleyicisini kaydederek belirli bir türdeki olaylara abone olur.  
  
|Yöntem|Olay Türü|Olay bağımsız değişkenleri türü|Temsilci türü|  
|------------|----------------|--------------------------|-------------------|  
|<xref:System.Windows.Automation.Automation.AddAutomationFocusChangedEventHandler%2A>|Odak değişikliği|<xref:System.Windows.Automation.AutomationFocusChangedEventArgs>|<xref:System.Windows.Automation.AutomationFocusChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A>|Özellik değişikliği|<xref:System.Windows.Automation.AutomationPropertyChangedEventArgs>|<xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddStructureChangedEventHandler%2A>|Yapı değişikliği|<xref:System.Windows.Automation.StructureChangedEventArgs>|<xref:System.Windows.Automation.StructureChangedEventHandler>|  
|<xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>|Tarafından tanımlanan tüm diğer olaylar<xref:System.Windows.Automation.AutomationEvent>|<xref:System.Windows.Automation.AutomationEventArgs> veya <xref:System.Windows.Automation.WindowClosedEventArgs>|<xref:System.Windows.Automation.AutomationEventHandler>|  
  
 Yöntemi çağırmadan önce, olayı işlemek için bir temsilci yöntemi oluşturmanız gerekir. İsterseniz, farklı türdeki olayları tek bir yöntemde işleyebilir ve bu yöntemi tablodaki yöntemlerden birine birden çok çağrıda geçirebilirsiniz. Örneğin, tek bir, <xref:System.Windows.Automation.AutomationEventHandler> çeşitli olayları öğesine göre farklı şekilde işlemek üzere ayarlanabilir <xref:System.Windows.Automation.AutomationEventArgs.EventId%2A> .  
  
> [!NOTE]
> Pencere kapalı olaylarını işlemek için, olay işleyicisine geçirilen bağımsız değişken türünü olarak atayın <xref:System.Windows.Automation.WindowClosedEventArgs> . [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]Pencerenin öğesi artık geçerli olmadığından, `sender` bilgileri almak için parametresini kullanamazsınız; <xref:System.Windows.Automation.WindowClosedEventArgs.GetRuntimeId%2A> bunun yerine kullanın.  
  
> [!CAUTION]
> Uygulamanız kendi etkinliklerini alabilir [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] , [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] olaylara abone olmak veya aboneliği kaldırmak için uygulamanızın iş parçacığını kullanmayın. Bunun yapılması öngörülemeyen davranışlara neden olabilirler. Daha fazla bilgi için bkz. [UI Otomasyonu Iş parçacığı sorunları](ui-automation-threading-issues.md).  
  
 Kapatılırken veya [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Olaylar uygulamaya artık ilgilenmeyen Kullanıcı Arabirimi Otomasyonu istemcileri aşağıdaki yöntemlerden birini çağırmalıdır.  
  
|Yöntem|Description|  
|------------|-----------------|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationEventHandler%2A>|Kullanılarak kaydedilmiş bir olay işleyicisinin kaydını siler <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A> .|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationFocusChangedEventHandler%2A>|Kullanılarak kaydedilmiş bir olay işleyicisinin kaydını siler <xref:System.Windows.Automation.Automation.AddAutomationFocusChangedEventHandler%2A> .|  
|<xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>|Kullanılarak kaydedilmiş bir olay işleyicisinin kaydını siler <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> .|  
|<xref:System.Windows.Automation.Automation.RemoveAllEventHandlers%2A>|Tüm kayıtlı olay işleyicilerinin kaydını siler.|  
  
 Örnek kod için bkz. [UI Otomasyon olaylarına abone olma](subscribe-to-ui-automation-events.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyon Olaylarına Abone Olma](subscribe-to-ui-automation-events.md)
- [UI Otomasyonu Olaylarına Genel Bakış](ui-automation-events-overview.md)
- [UI Otomasyon Özelliklerine Genel Bakış](ui-automation-properties-overview.md)
- [TrackFocus örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/FocusTracker)
