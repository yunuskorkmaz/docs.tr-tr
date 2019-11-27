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
ms.openlocfilehash: 5f9362814eb671a6d7a111cadb96be6d06f5cb3d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74441500"
---
# <a name="ui-automation-events-overview"></a>UI Otomasyonu Olaylarına Genel Bakış
> [!NOTE]
> Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] olay bildirimi, ekran okuyucular ve ekran büyüteçleri gibi yardımcı teknolojiler için önemli bir özelliktir. Bu UI Otomasyonu istemcileri, [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] bir şeyler olduğunda UI Otomasyon sağlayıcıları tarafından oluşturulan olayları izler ve son kullanıcıları bilgilendirmek için bu bilgileri kullanır.  
  
 Herhangi bir istemcinin herhangi bir olayı dinlememesi durumunda, hiçbir istemcinin bu olaylara abone olup olmadığı veya hiç bir şekilde değil, herhangi bir istemciye etkinlik yapmasına izin vererek verimlilik geliştirilmiştir.  
  
<a name="Types_of_Events"></a>   
## <a name="types-of-events"></a>Olay türleri  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olaylar aşağıdaki kategorilere ayrılır.  
  
|Olay|Açıklama|  
|-----------|-----------------|  
|Özellik değişikliği|Bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] öğesinde veya denetim düzeninde bir özellik değiştiğinde tetiklenir. Örneğin, bir istemcinin bir uygulamanın onay kutusu denetimini izlemesi gerekiyorsa, <xref:System.Windows.Automation.TogglePattern.TogglePatternInformation.ToggleState%2A> özelliğindeki bir özellik değişiklik olayını dinlemek için kayıt yapabilir. Onay kutusu denetimi işaretli veya işaretlenmemiş olduğunda, sağlayıcı olayı başlatır ve istemci gerektiği gibi davranabilir.|  
|Öğe eylemi|[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] bir değişiklik Son Kullanıcı veya programlı etkinlikten sonuçlanırsa tetiklenir; Örneğin, bir düğmeye tıklandığında veya <xref:System.Windows.Automation.InvokePattern>aracılığıyla çağrıldığında.|  
|Yapı değişikliği|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacının yapısı değiştiğinde tetiklenir. Yeni [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğeler, masaüstünde görünür, gizli hale geldiğinde veya kaldırıldığında yapı değişir.|  
|Genel masaüstü değişikliği|Odak bir öğeden diğerine kaydırıldığında veya bir pencere kapandığında olduğu gibi, istemci için genel ilgi çekici eylemler gerçekleştiğinde tetiklenir.|  
  
 Bazı olaylar, Kullanıcı arabiriminin durumunun değiştiği anlamına gelmez. Örneğin, Kullanıcı bir metin girişi alanını sekmeler ve sonra alanı güncelleştirmek için bir düğmeye tıkladığında, Kullanıcı gerçekten metni değiştirmese bile bir `TextChangedEvent` tetiklenir. Bir olayı işlerken, bir istemci uygulaması, işlem yapılmadan önce herhangi bir şeyin gerçekten değişip değişmediğini kontrol etmek için gerekli olabilir.  
  
 Aşağıdaki olaylar, Kullanıcı arabiriminin durumu değiştirilmese bile oluşturulabilir.  
  
- `AutomationPropertyChangedEvent` (değiştirilen özelliğe bağlı olarak)  
  
- `ElementSelectedEvent`  
  
- `InvalidatedEvent`  
  
- `TextChangedEvent`  
  
<a name="UI_Automation_Event_Identifiers"></a>   
## <a name="ui-automation-event-identifiers"></a>UI Otomasyonu olay tanımlayıcıları  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] olaylar <xref:System.Windows.Automation.AutomationEvent> nesneler tarafından tanımlanır. <xref:System.Windows.Automation.AutomationIdentifier.Id%2A> özelliği, olay türünü benzersiz bir şekilde tanımlayan bir değer içerir.  
  
 <xref:System.Windows.Automation.AutomationIdentifier.Id%2A> için olası değerler aşağıdaki tabloda, olay bağımsız değişkenleri için kullanılan türle birlikte verilmiştir. İstemciler ve sağlayıcılar tarafından kullanılan tanımlayıcıların farklı sınıflardan aynı adlı alanları olduğunu unutmayın.  
  
|İstemci Tanımlayıcısı|Sağlayıcı tanımlayıcısı|Olay bağımsız değişkenleri türü|  
|-----------------------|-------------------------|--------------------------|  
|<xref:System.Windows.Automation.AutomationElement.AsyncContentLoadedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationElementIdentifiers.AsyncContentLoadedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AsyncContentLoadedEventArgs>|  
|<xref:System.Windows.Automation.SelectionItemPattern.ElementAddedToSelectionEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionItemPattern.ElementRemovedFromSelectionEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionPattern.InvalidatedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.InvokePattern.InvokedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.LayoutInvalidatedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.MenuClosedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.MenuOpenedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.TextPattern.TextChangedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.TextPattern.TextSelectionChangedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.ToolTipClosedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.ToolTipOpenedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.MenuClosedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.MenuOpenedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.TextPatternIdentifiers.TextChangedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.TextPatternIdentifiers.TextSelectionChangedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.ToolTipClosedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.ToolTipOpenedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.WindowPatternIdentifiers.WindowOpenedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationEventArgs>|  
|<xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationFocusChangedEventArgs>|  
|<xref:System.Windows.Automation.AutomationElement.AutomationPropertyChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationPropertyChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationPropertyChangedEventArgs>|  
|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.StructureChangedEventArgs>|  
|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.WindowPatternIdentifiers.WindowClosedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.WindowClosedEventArgs>|  
  
<a name="UI_Automation_Event_Arguments"></a>   
## <a name="ui-automation-event-arguments"></a>UI Otomasyonu olay bağımsız değişkenleri  
 Aşağıdaki sınıflar olay bağımsız değişkenlerini kapsüller.  
  
|örneği|Açıklama|  
|-----------|-----------------|  
|<xref:System.Windows.Automation.AsyncContentLoadedEventArgs>|Tamamlanan yükleme yüzdesi de dahil olmak üzere içeriğin zaman uyumsuz yüklemesi hakkındaki bilgileri içerir.|  
|<xref:System.Windows.Automation.AutomationEventArgs>|Ek veri gerektirmeyen basit bir olayla ilgili bilgiler içerir.|  
|<xref:System.Windows.Automation.AutomationFocusChangedEventArgs>|Giriş odağıyla ilgili, bir öğeden diğerine değişiklik hakkındaki bilgileri içerir. Bu türden olaylar, sağlayıcılar tarafından değil [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sistem tarafından oluşturulur.|  
|<xref:System.Windows.Automation.AutomationPropertyChangedEventArgs>|Bir öğenin veya denetim deseninin özellik değerindeki bir değişiklik hakkındaki bilgileri içerir.|  
|<xref:System.Windows.Automation.StructureChangedEventArgs>|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacındaki bir değişiklik hakkındaki bilgileri içerir.|  
|<xref:System.Windows.Automation.WindowClosedEventArgs>|Bir pencere kapatma hakkında bilgi içerir.|  
  
 Tüm olay bağımsız değişkeni sınıfları bir <xref:System.Windows.Automation.AutomationEventArgs.EventId%2A> üyesi içerir. Bu tanımlayıcı bir <xref:System.Windows.Automation.AutomationEvent>kapsüllenir.  
  
 Olayları tanımlamak için kullanılan <xref:System.Windows.Automation.AutomationEvent> nesneleri, <xref:System.Windows.Automation.AutomationElementIdentifiers> ve <xref:System.Windows.Automation.DockPatternIdentifiers>gibi denetim deseninin tanımlayıcı sınıflarında yer alan sağlayıcılar tarafından alınır. Eşdeğer alanlar, <xref:System.Windows.Automation.AutomationElement> ve <xref:System.Windows.Automation.DockPattern>gibi denetim deseninin içindeki alanlardan istemci uygulamaları tarafından alınır.  
  
 Olay tanımlayıcılarının listesi için bkz. [istemciler Için UI Otomasyon olayları](ui-automation-events-for-clients.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İstemciler İçin UI Otomasyonu Olayları](ui-automation-events-for-clients.md)
- [Sunucu Tarafı UI Otomasyonu Sağlayıcısı Uygulama](server-side-ui-automation-provider-implementation.md)
- [UI Otomasyonu Olaylarına Abone Olma](subscribe-to-ui-automation-events.md)
