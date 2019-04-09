---
title: UI Otomasyonu Olaylarına Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, providers
- UI Automation, events
- clients, UI Automation
- events, UI Automation
- providers, UI Automation
- UI Automation, clients
ms.assetid: 69eebd8b-39ed-40e7-93cc-4457c4caf746
ms.openlocfilehash: ae780da7d6c6d45cb791333e5f0edcf0690f297b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59183748"
---
# <a name="ui-automation-events-overview"></a>UI Otomasyonu Olaylarına Genel Bakış
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] olay bildirimi, ekran okuyucuların ve ekran büyüteçleri gibi yardımcı teknolojiler için önemli bir özelliktir. UI Otomasyon sağlayıcıları tarafından bir şey olduğunda oluşan bu UI Otomasyonu istemcileri izleme olayları [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] ve son kullanıcılara bildirmek için bilgileri kullanın.  
  
 Verimliliği, olayları seçerek, hiçbir istemci için meydana gelen olayları dinleyen durumunda olup olmadığını istemciler bu olayları veya hiç, abone olduğunuz bağlı olarak yükseltmek sağlayıcı uygulamaların vererek geliştirildi.  
  
<a name="Types_of_Events"></a>   
## <a name="types-of-events"></a>Olay türleri  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayları aşağıdaki kategorilere ayrılır.  
  
|Olay|Açıklama|  
|-----------|-----------------|  
|Özellik değişikliği|Bir özellikte harekete geçirilen bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] öğe veya denetim desen değişiklikleri. Bir istemci uygulamanın onay kutusu denetimini izlemek gerekiyorsa, örneğin, bir özellik değişiklik olayı için dinleyecek şekilde kaydedebilirsiniz <xref:System.Windows.Automation.TogglePattern.TogglePatternInformation.ToggleState%2A> özelliği. Onay kutusu denetimi işaretli veya işaretsiz olduğunda Olay sağlayıcısı oluşturur ve istemci gerektiği gibi davranabilir.|  
|Öğesi eylem|Bir değişiklik olduğunda ortaya [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] son kullanıcı ya da programlı etkinlik sonuçlardan; Örneğin, bir düğmeye tıklandığında veya aracılığıyla çağrılan zaman <xref:System.Windows.Automation.InvokePattern>.|  
|Yapı değişiklik|Arandığında yapısını [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] değişiklikleri ağaç. Yapı değişiklikleri yeni [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] görünür, gizli ya da masaüstünde kaldırılan öğeler haline gelir.|  
|Genel Masaüstü Değiştir|Ne zaman odak bir öğeden diğerine geçer veya ne zaman bir pencereyi kapatır gibi eylemler istemciye genel ilgi gerçekleştiğinde oluşturulur.|  
  
 Bazı olaylar, UI durumu olarak değiştiğini mutlaka gelmez. Örneğin, kullanıcı sekmeler metin girişi alana ve ardından alanı güncelleştirmek için bir düğmeye tıkladığında bir `TextChangedEvent` kullanıcı metnini gerçekte değiştirmedi bile oluşturulur. Bir olay işleme sırasında herhangi bir şey gerçekten eylemi gerçekleştirmeden önce değişip değişmediğini denetlemek bir istemci uygulaması için gerekli olabilir.  
  
 Hatta kullanıcı arabiriminin durumu değişmediğinden, aşağıdaki olaylar oluşturulabilir.  
  
-   `AutomationPropertyChangedEvent` (değişti özelliği bağlı olarak)  
  
-   `ElementSelectedEvent`  
  
-   `InvalidatedEvent`  
  
-   `TextChangedEvent`  
  
<a name="UI_Automation_Event_Identifiers"></a>   
## <a name="ui-automation-event-identifiers"></a>UI Otomasyon olay tanımlayıcıları  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] olayları tanımlanır <xref:System.Windows.Automation.AutomationEvent> nesneleri. <xref:System.Windows.Automation.AutomationIdentifier.Id%2A> Özelliği, olay türü benzersiz olarak tanımlayan bir değer içerir.  
  
 Olası değerler için <xref:System.Windows.Automation.AutomationIdentifier.Id%2A> aşağıdaki tabloda, olay bağımsız değişkenleri için kullanılan türü ile birlikte verilir. İstemcileri ve sağlayıcıları tarafından kullanılan tanımlayıcıları alanları farklı sınıflardan aynı adlı olduğunu unutmayın.  
  
|İstemci tanımlayıcısı|Sağlayıcı tanımlayıcısı|Olay bağımsız değişkenleri|  
|-----------------------|-------------------------|--------------------------|  
|<xref:System.Windows.Automation.AutomationElement.AsyncContentLoadedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationElementIdentifiers.AsyncContentLoadedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AsyncContentLoadedEventArgs>|  
|<xref:System.Windows.Automation.SelectionItemPattern.ElementAddedToSelectionEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionItemPattern.ElementRemovedFromSelectionEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionPattern.InvalidatedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.InvokePattern.InvokedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.LayoutInvalidatedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.MenuClosedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.MenuOpenedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.TextPattern.TextChangedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.TextPattern.TextSelectionChangedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.ToolTipClosedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.ToolTipOpenedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.MenuClosedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.MenuOpenedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.TextPatternIdentifiers.TextChangedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.TextPatternIdentifiers.TextSelectionChangedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.ToolTipClosedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.ToolTipOpenedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.WindowPatternIdentifiers.WindowOpenedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationEventArgs>|  
|<xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationFocusChangedEventArgs>|  
|<xref:System.Windows.Automation.AutomationElement.AutomationPropertyChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationPropertyChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationPropertyChangedEventArgs>|  
|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.StructureChangedEventArgs>|  
|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.WindowPatternIdentifiers.WindowClosedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.WindowClosedEventArgs>|  
  
<a name="UI_Automation_Event_Arguments"></a>   
## <a name="ui-automation-event-arguments"></a>UI Otomasyon olay bağımsız değişkenleri  
 Aşağıdaki sınıflar, olay bağımsız değişkenleri kapsüller.  
  
|örneği|Açıklama|  
|-----------|-----------------|  
|<xref:System.Windows.Automation.AsyncContentLoadedEventArgs>|İçerik yükleme tamamlandı yüzdesi de dahil olmak üzere, zaman uyumsuz yükleme hakkında bilgi içerir.|  
|<xref:System.Windows.Automation.AutomationEventArgs>|Ek veri yok gerektiren basit bir olay hakkında bilgiler içerir.|  
|<xref:System.Windows.Automation.AutomationFocusChangedEventArgs>|Girintiyi bir öğeden diğerine değişikliği hakkında bilgi içerir. Bu tür olayları oluştuğunda tarafından [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] yok sağlayıcıları tarafından sistemi.|  
|<xref:System.Windows.Automation.AutomationPropertyChangedEventArgs>|Bir öğe ya da denetim desenini bir özellik değerinde bir değişiklik hakkında bilgiler içerir.|  
|<xref:System.Windows.Automation.StructureChangedEventArgs>|Bir değişiklik hakkında bilgi içeren [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç.|  
|<xref:System.Windows.Automation.WindowClosedEventArgs>|Pencereyi kapatma hakkında bilgi içerir.|  
  
 Tüm olay bağımsız değişkeni sınıflarını içeren bir <xref:System.Windows.Automation.AutomationEventArgs.EventId%2A> üyesi. Bu tanımlayıcı içinde kapsüllenir bir <xref:System.Windows.Automation.AutomationEvent>.  
  
 <xref:System.Windows.Automation.AutomationEvent> Olayları tanımlamak için kullanılan nesneleri elde edilen alanlarındaki sağlayıcıları tarafından <xref:System.Windows.Automation.AutomationElementIdentifiers> ve düzen tanımlayıcısı sınıflar gibi denetim <xref:System.Windows.Automation.DockPatternIdentifiers>. Eşdeğer alanlara alanlarındaki istemci uygulamalar tarafından elde edilen <xref:System.Windows.Automation.AutomationElement> ve desen sınıflar gibi denetim <xref:System.Windows.Automation.DockPattern>.  
  
 Olay tanımlayıcıların bir listesi için bkz. [istemciler için UI Otomasyonu olayları](../../../docs/framework/ui-automation/ui-automation-events-for-clients.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İstemciler İçin UI Otomasyon Olayları](../../../docs/framework/ui-automation/ui-automation-events-for-clients.md)
- [Sunucu Tarafı UI Otomasyonu Sağlayıcıyı Uygulama](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
- [UI Otomasyon Olaylarına Abone Olma](../../../docs/framework/ui-automation/subscribe-to-ui-automation-events.md)
