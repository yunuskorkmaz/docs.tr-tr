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
ms.openlocfilehash: 495e7d29c814164f4235d18569477b856cb09045
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179891"
---
# <a name="ui-automation-events-overview"></a>UI Otomasyonu Olaylarına Genel Bakış
> [!NOTE]
> Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır. Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]olay bildirimi, ekran okuyucular ve ekran büyüteçleri gibi yardımcı teknolojiler için önemli bir özelliktir. Bu Kullanıcı Biru-OI Otomasyon istemcileri, kullanıcı yanında [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] bir şey olduğunda Kullanıcı Bira Otomasyonu sağlayıcıları tarafından yükseltilen olayları izler ve bilgileri son kullanıcıları bilgilendirmek için kullanır.  
  
 Sağlayıcı uygulamalarının, istemcilerin bu olaylara abone olup olmamasına bağlı olarak, herhangi bir istemcinin herhangi bir olayı dinlememesi durumunda, etkinlikleri seçici olarak yükseltmesine izin vererek verimlilik artırılır.  
  
<a name="Types_of_Events"></a>
## <a name="types-of-events"></a>Etkinlik Türleri  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]olaylar aşağıdaki kategorilere ayrılır.  
  
|Olay|Açıklama|  
|-----------|-----------------|  
|Özellik değişikliği|Bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] öğe veya denetim deseni üzerindeki bir özellik değiştiğinde yükseltilir. Örneğin, bir istemcinin bir uygulamanın onay kutusu denetimini izlemesi gerekiyorsa, <xref:System.Windows.Automation.TogglePattern.TogglePatternInformation.ToggleState%2A> özellikteki bir özellik değişikliği olayını dinlemek için kaydolabilir. Onay kutusu denetimi işaretlendiğinde veya işaretlenmediğinde, sağlayıcı olayı yükseltir ve istemci gerektiği gibi davranabilir.|  
|Öğe eylemi|Son kullanıcı veya [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] programlı etkinlikten elde edilen sonuçlarda bir değişiklik olduğunda yükseltilmiş; örneğin, bir düğme tıklatıldığında veya <xref:System.Windows.Automation.InvokePattern>çağrıldığınızda.|  
|Yapı değişikliği|Ağacın yapısı değiştiğinde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] yükseltilir. Yeni [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğeler görünür, gizlendiğinde veya masaüstünde kaldırıldığında yapı değişir.|  
|Genel masaüstü değişikliği|Odak bir öğeden diğerine kaydığında veya bir pencere kapandığında gibi, istemciye yönelik genel ilgi eylemleri gerçekleştiğinde yükseltilir.|  
  
 Bazı olaylar, UI'nin durumunun değiştiği anlamına gelmez. Örneğin, kullanıcı bir metin giriş alanına seker ve sonra alanı güncelleştirmek `TextChangedEvent` için bir düğmeyi tıklatırsa, kullanıcı metni gerçekten değiştirmemiş olsa bile bir yükseltilir. Bir olayı işlerken, bir istemci uygulamasının eyleme geçmeden önce gerçekten bir şeyin gerçekten değişip değişmediğini denetlemesi gerekebilir.  
  
 UI'nin durumu değişmemiş olsa bile aşağıdaki olaylar gündeme gelebilir.  
  
- `AutomationPropertyChangedEvent`(değiştirilen özelliğe bağlı olarak)  
  
- `ElementSelectedEvent`  
  
- `InvalidatedEvent`  
  
- `TextChangedEvent`  
  
<a name="UI_Automation_Event_Identifiers"></a>
## <a name="ui-automation-event-identifiers"></a>UI Otomasyon Olay Tanımlayıcıları  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]olaylar nesneler <xref:System.Windows.Automation.AutomationEvent> tarafından tanımlanır. Özellik, <xref:System.Windows.Automation.AutomationIdentifier.Id%2A> olayın türünü benzersiz olarak tanımlayan bir değer içerir.  
  
 Olası <xref:System.Windows.Automation.AutomationIdentifier.Id%2A> değerler, olay bağımsız değişkenleri için kullanılan türle birlikte aşağıdaki tabloda verilmiştir. İstemciler ve sağlayıcılar tarafından kullanılan tanımlayıcıların farklı sınıflardan aynı adlandırılmış alanlar olduğunu unutmayın.  
  
|İstemci Tanımlayıcı|Sağlayıcı tanımlayıcısı|Olay Bağımsız Değişkentürü|  
|-----------------------|-------------------------|--------------------------|  
|<xref:System.Windows.Automation.AutomationElement.AsyncContentLoadedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationElementIdentifiers.AsyncContentLoadedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AsyncContentLoadedEventArgs>|  
|<xref:System.Windows.Automation.SelectionItemPattern.ElementAddedToSelectionEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionItemPattern.ElementRemovedFromSelectionEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionPattern.InvalidatedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.InvokePattern.InvokedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.LayoutInvalidatedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.MenuClosedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.MenuOpenedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.TextPattern.TextChangedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.TextPattern.TextSelectionChangedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.ToolTipClosedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElement.ToolTipOpenedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.MenuClosedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.MenuOpenedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.TextPatternIdentifiers.TextChangedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.TextPatternIdentifiers.TextSelectionChangedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.ToolTipClosedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.AutomationElementIdentifiers.ToolTipOpenedEvent?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.WindowPatternIdentifiers.WindowOpenedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationEventArgs>|  
|<xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationFocusChangedEventArgs>|  
|<xref:System.Windows.Automation.AutomationElement.AutomationPropertyChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationPropertyChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationPropertyChangedEventArgs>|  
|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.StructureChangedEventArgs>|  
|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.WindowPatternIdentifiers.WindowClosedEvent?displayProperty=nameWithType>|<xref:System.Windows.Automation.WindowClosedEventArgs>|  
  
<a name="UI_Automation_Event_Arguments"></a>
## <a name="ui-automation-event-arguments"></a>UI Otomasyon Olay Bağımsız Değişkenleri  
 Aşağıdaki sınıflar olay bağımsız değişkenlerini kapsüller.  
  
|Sınıf|Açıklama|  
|-----------|-----------------|  
|<xref:System.Windows.Automation.AsyncContentLoadedEventArgs>|Tamamlanan yükleme yüzdesi de dahil olmak üzere içeriğin eşzamanlı yüklemesi hakkında bilgi içerir.|  
|<xref:System.Windows.Automation.AutomationEventArgs>|Ekstra veri gerektirmeden basit bir olay hakkında bilgi içerir.|  
|<xref:System.Windows.Automation.AutomationFocusChangedEventArgs>|Giriş odağındaki bir değişiklik hakkında bir öğeden diğerine bilgi içerir. Bu tür olaylar sağlayıcılar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tarafından değil, sistem tarafından yükseltilir.|  
|<xref:System.Windows.Automation.AutomationPropertyChangedEventArgs>|Bir öğenin veya denetim deseninin özellik değerindeki değişiklik hakkında bilgi içerir.|  
|<xref:System.Windows.Automation.StructureChangedEventArgs>|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ağaçtaki bir değişiklik hakkında bilgi içerir.|  
|<xref:System.Windows.Automation.WindowClosedEventArgs>|Pencere kapatma hakkında bilgi içerir.|  
  
 Tüm olay bağımsız değişken <xref:System.Windows.Automation.AutomationEventArgs.EventId%2A> sınıfları bir üye içerir. Bu tanımlayıcı bir <xref:System.Windows.Automation.AutomationEvent>.  
  
 Olayları <xref:System.Windows.Automation.AutomationEvent> tanımlamak için kullanılan nesneler, <xref:System.Windows.Automation.AutomationElementIdentifiers> 'deki ve denetim deseni tanımlayıcı sınıflarındaki <xref:System.Windows.Automation.DockPatternIdentifiers>sağlayıcılar tarafından elde edilir. Eşdeğer alanlar, <xref:System.Windows.Automation.AutomationElement> 've denetim desen sınıfları gibi <xref:System.Windows.Automation.DockPattern>alanlardan istemci uygulamaları tarafından elde edilir.  
  
 Olay tanımlayıcılarının listesi [için, Müşteriler için UI Otomasyon Etkinlikleri'ne](ui-automation-events-for-clients.md)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İstemciler İçin UI Otomasyonu Olayları](ui-automation-events-for-clients.md)
- [Sunucu Tarafı UI Otomasyonu Sağlayıcıyı Uygulama](server-side-ui-automation-provider-implementation.md)
- [UI Otomasyon Olaylarına Abone Olma](subscribe-to-ui-automation-events.md)
