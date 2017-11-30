---
title: "UI Otomasyonu Olaylarına Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, providers
- UI Automation, events
- clients, UI Automation
- events, UI Automation
- providers, UI Automation
- UI Automation, clients
ms.assetid: 69eebd8b-39ed-40e7-93cc-4457c4caf746
caps.latest.revision: "22"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 9634c686d23503dcb4deae171f0023055c41ce2d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ui-automation-events-overview"></a>UI Otomasyonu Olaylarına Genel Bakış
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]olay bildirimi, ekran okuyucuların ve ekran büyüteçleri gibi yardımcı teknolojiler için önemli bir özelliktir. Bu UI Otomasyonu istemcileri izleme şey olduğunda UI Otomasyon sağlayıcıları tarafından oluşturulan olayları [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] ve son kullanıcılara bildirmek için bilgileri kullanın.  
  
 Verimlilik olayları, seçmeli olarak, hiçbir istemci için tüm olayları dinleme yapıyorsanız olup tüm istemciler bu olayları veya hiç, abone olduğunuz bağlı olarak yükseltmek sağlayıcı uygulamaları olanak sağlayarak geliştirilmiştir.  
  
<a name="Types_of_Events"></a>   
## <a name="types-of-events"></a>Olay türleri  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]olayları aşağıdaki kategorilere ayrılır.  
  
|Olay|Açıklama|  
|-----------|-----------------|  
|Özellik değişikliği|Bir özellik tetiklenir bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] öğesi veya denetim düzeni değişiklikleri. Bir istemci uygulamanın onay kutusu denetimi izlemek gerekirse, örneğin, bu özellik değişim olayı için dinlenecek kaydedebilirsiniz <xref:System.Windows.Automation.TogglePattern.TogglePatternInformation.ToggleState%2A> özelliği. Onay kutusu denetimi işaretli veya işaretsiz olduğunda, sağlayıcı olayını başlatır ve istemci gerektiği gibi çalışabilir.|  
|Öğesi eylem|Bir değişiklik olduğunda ortaya [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] son kullanıcı veya program etkinlik sonuçlarından; Örneğin, ne zaman bir düğmeye tıklandığında veya aracılığıyla çağrılan <xref:System.Windows.Automation.InvokePattern>.|  
|Yapı değişikliğine|Ne zaman yükseltilmiş yapısını [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç değişiklikleri. Yapısını değiştirir yeni [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] görünür, gizli veya masaüstünde kaldırılan öğeler haline gelir.|  
|Genel Masaüstü Değiştir|Ne zaman odak bir öğeden diğerine geçer, veya bir pencere kapattığı zaman gibi eylemleri istemciye genel ilgi oluştuğunda oluşturulur.|  
  
 Bazı olaylar UI durumu değişti mutlaka anlamına gelmez. Örneğin kullanıcı sekmeler metin girişi alanına ve alanını güncelleştirmek için bir düğmeye tıklar bir `TextChangedEvent` kullanıcı metni gerçekte değişmemiştir olsa bile tetiklenir. Bir olay işleme sırasında herhangi bir şey gerçekte eylemi gerçekleştirmeden önce değişip değişmediğini denetlemek bir istemci uygulaması için gerekli olabilir.  
  
 Aşağıdaki olaylar tetiklenir bile UI durumu değişmediğini.  
  
-   `AutomationPropertyChangedEvent`(değişti özelliği bağlı olarak)  
  
-   `ElementSelectedEvent`  
  
-   `InvalidatedEvent`  
  
-   `TextChangedEvent`  
  
<a name="UI_Automation_Event_Identifiers"></a>   
## <a name="ui-automation-event-identifiers"></a>UI Otomasyon olay tanımlayıcıları  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]olayları tanımlanır <xref:System.Windows.Automation.AutomationEvent> nesneleri. <xref:System.Windows.Automation.AutomationIdentifier.Id%2A> Özelliği, olay türü benzersiz olarak tanımlayan bir değer içerir.  
  
 Olası değerler için <xref:System.Windows.Automation.AutomationIdentifier.Id%2A> aşağıdaki tabloda, olay değişkenlerini kullanılan türü ile birlikte verilir. İstemcileri ve sağlayıcıları tarafından kullanılan tanımlayıcıları farklı sınıflardan alanları aynı adlı unutmayın.  
  
|İstemci tanımlayıcısı|Sağlayıcı tanımlayıcısı|Olay bağımsız değişken türü|  
|-----------------------|-------------------------|--------------------------|  
|<xref:System.Windows.Automation.AutomationElement.AsyncContentLoadedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationElementIdentifiers.AsyncContentLoadedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AsyncContentLoadedEventArgs>|  
|<xref:System.Windows.Automation.SelectionItemPattern.ElementAddedToSelectionEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionItemPattern.ElementRemovedFromSelectionEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionPattern.InvalidatedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.InvokePattern.InvokedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.LayoutInvalidatedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.MenuClosedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.MenuOpenedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.TextPattern.TextChangedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.TextPattern.TextSelectionChangedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.ToolTipClosedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.ToolTipOpenedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.MenuClosedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.MenuOpenedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.TextPatternIdentifiers.TextChangedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.TextPatternIdentifiers.TextSelectionChangedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.ToolTipClosedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.ToolTipOpenedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.WindowPatternIdentifiers.WindowOpenedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationEventArgs>|  
|<xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationFocusChangedEventArgs>|  
|<xref:System.Windows.Automation.AutomationElement.AutomationPropertyChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationPropertyChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationPropertyChangedEventArgs>|  
|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.StructureChangedEventArgs>|  
|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.WindowPatternIdentifiers.WindowClosedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.WindowClosedEventArgs>|  
  
<a name="UI_Automation_Event_Arguments"></a>   
## <a name="ui-automation-event-arguments"></a>UI Otomasyon olay bağımsız değişkenleri  
 Aşağıdaki sınıflar olay bağımsız kapsüller.  
  
|örneği|Açıklama|  
|-----------|-----------------|  
|<xref:System.Windows.Automation.AsyncContentLoadedEventArgs>|Yükleme Tamamlandı yüzdesi dahil olmak üzere içeriğinin zaman uyumsuz yükleme hakkında bilgi içerir.|  
|<xref:System.Windows.Automation.AutomationEventArgs>|Ek veri gerektiren basit olay hakkında bilgiler içerir.|  
|<xref:System.Windows.Automation.AutomationFocusChangedEventArgs>|Bir öğeden giriş odağını başka bir değişikliği hakkında bilgiler içerir. Bu tür olayları tarafından gerçekleştirilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sistem sağlayıcıları tarafından değil.|  
|<xref:System.Windows.Automation.AutomationPropertyChangedEventArgs>|Bir öğe veya denetim düzeni özellik değerinde bir değişiklik hakkında bilgiler içerir.|  
|<xref:System.Windows.Automation.StructureChangedEventArgs>|Bir değişiklik hakkında bilgi içeren [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı.|  
|<xref:System.Windows.Automation.WindowClosedEventArgs>|Pencereyi kapatma hakkında bilgi içerir.|  
  
 Tüm olay bağımsız değişkeni sınıflarını içeren bir <xref:System.Windows.Automation.AutomationEventArgs.EventId%2A> üye. Bu tanımlayıcı içinde kapsüllenir bir <xref:System.Windows.Automation.AutomationEvent>.  
  
 <xref:System.Windows.Automation.AutomationEvent> Olayları tanımlamak için kullanılan nesneleri elde edilir alanlarındaki sağlayıcıları tarafından <xref:System.Windows.Automation.AutomationElementIdentifiers> ve desen tanımlayıcı sınıfları denetimini <xref:System.Windows.Automation.DockPatternIdentifiers>. Eşdeğer alanları alanlarındaki istemci uygulamaları tarafından elde edilen <xref:System.Windows.Automation.AutomationElement> ve desen sınıfları denetimini <xref:System.Windows.Automation.DockPattern>.  
  
 Olay tanımlayıcılarının bir listesi için bkz: [istemciler için UI Otomasyon olayları](../../../docs/framework/ui-automation/ui-automation-events-for-clients.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İstemciler için UI Otomasyon olayları](../../../docs/framework/ui-automation/ui-automation-events-for-clients.md)  
 [Sunucu tarafı UI Otomasyon sağlayıcıyı uygulama](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)  
 [UI Otomasyon olaylarına abone olma](../../../docs/framework/ui-automation/subscribe-to-ui-automation-events.md)
