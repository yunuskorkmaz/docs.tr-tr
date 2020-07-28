---
title: UI Otomasyonu Olaylarına Genel Bakış
description: Bkz. Microsoft UI Otomasyonu olay bildirimine genel bakış. Olay türlerini, UI Otomasyonu olay tanımlayıcılarını ve UI Otomasyonu olay bağımsız değişkenlerini gözden geçirin.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, providers
- UI Automation, events
- clients, UI Automation
- events, UI Automation
- providers, UI Automation
- UI Automation, clients
ms.assetid: 69eebd8b-39ed-40e7-93cc-4457c4caf746
ms.openlocfilehash: 4f51a31a433986822a9dba22bf8f17ade00bbb76
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168100"
---
# <a name="ui-automation-events-overview"></a>UI Otomasyonu Olaylarına Genel Bakış
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]olay bildirimi, ekran okuyucular ve ekran büyüteçleri gibi yardımcı teknolojiler için önemli bir özelliktir. Bu UI Otomasyonu istemcileri, içinde bir şeyler olduğunda UI Otomasyon sağlayıcıları tarafından oluşturulan olayları izler [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] ve son kullanıcıları bilgilendirmek için bu bilgileri kullanır.  
  
 Herhangi bir istemcinin herhangi bir olayı dinlememesi durumunda, hiçbir istemcinin bu olaylara abone olup olmadığı veya hiç bir şekilde değil, herhangi bir istemciye etkinlik yapmasına izin vererek verimlilik geliştirilmiştir.  
  
<a name="Types_of_Events"></a>
## <a name="types-of-events"></a>Olay türleri  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]olaylar aşağıdaki kategorilere ayrılır.  
  
|Olay|Açıklama|  
|-----------|-----------------|  
|Özellik değişikliği|Bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] öğe veya denetim deseninin bir özelliği değiştiğinde tetiklenir. Örneğin, bir istemcinin bir uygulamanın onay kutusu denetimini izlemesi gerekiyorsa, özellik üzerinde bir özellik değişiklik olayını dinlemek için kayıt yapabilir <xref:System.Windows.Automation.TogglePattern.TogglePatternInformation.ToggleState%2A> . Onay kutusu denetimi işaretli veya işaretlenmemiş olduğunda, sağlayıcı olayı başlatır ve istemci gerektiği gibi davranabilir.|  
|Öğe eylemi|[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]Son Kullanıcı veya programlı etkinlikteki sonuçlarda değişiklik yapıldığında, örneğin bir düğmeye tıklandığında veya aracılığıyla çağrıldığında tetiklenir <xref:System.Windows.Automation.InvokePattern> .|  
|Yapı değişikliği|Ağacın yapısı değiştiğinde harekete geçirilir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] . Yapı, yeni [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğeler görünür olduğunda, gizlendiği veya masaüstünde kaldırıldığında değişir.|  
|Genel masaüstü değişikliği|Odak bir öğeden diğerine kaydırıldığında veya bir pencere kapandığında olduğu gibi, istemci için genel ilgi çekici eylemler gerçekleştiğinde tetiklenir.|  
  
 Bazı olaylar, Kullanıcı arabiriminin durumunun değiştiği anlamına gelmez. Örneğin, Kullanıcı bir metin girişi alanını sekmeler ve sonra alanı güncelleştirmek için bir düğmeye tıkladığında, `TextChangedEvent` Kullanıcı gerçekten metni değiştirmese bile oluşturulur. Bir olayı işlerken, bir istemci uygulaması, işlem yapılmadan önce herhangi bir şeyin gerçekten değişip değişmediğini kontrol etmek için gerekli olabilir.  
  
 Aşağıdaki olaylar, Kullanıcı arabiriminin durumu değiştirilmese bile oluşturulabilir.  
  
- `AutomationPropertyChangedEvent`(değiştirilen özelliğe bağlı olarak)  
  
- `ElementSelectedEvent`  
  
- `InvalidatedEvent`  
  
- `TextChangedEvent`  
  
<a name="UI_Automation_Event_Identifiers"></a>
## <a name="ui-automation-event-identifiers"></a>UI Otomasyonu olay tanımlayıcıları  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]olaylar nesneler tarafından tanımlanır <xref:System.Windows.Automation.AutomationEvent> . <xref:System.Windows.Automation.AutomationIdentifier.Id%2A>Özelliği, olay türünü benzersiz bir şekilde tanımlayan bir değer içerir.  
  
 İçin olası değerler <xref:System.Windows.Automation.AutomationIdentifier.Id%2A> Aşağıdaki tabloda, olay bağımsız değişkenleri için kullanılan türle birlikte verilmiştir. İstemciler ve sağlayıcılar tarafından kullanılan tanımlayıcıların farklı sınıflardan aynı adlı alanları olduğunu unutmayın.  
  
|İstemci tanımlayıcısı|Sağlayıcı tanımlayıcısı|Olay bağımsız değişkenleri türü|  
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
  
|Sınıf|Açıklama|  
|-----------|-----------------|  
|<xref:System.Windows.Automation.AsyncContentLoadedEventArgs>|Tamamlanan yükleme yüzdesi de dahil olmak üzere içeriğin zaman uyumsuz yüklemesi hakkındaki bilgileri içerir.|  
|<xref:System.Windows.Automation.AutomationEventArgs>|Ek veri gerektirmeyen basit bir olayla ilgili bilgiler içerir.|  
|<xref:System.Windows.Automation.AutomationFocusChangedEventArgs>|Giriş odağıyla ilgili, bir öğeden diğerine değişiklik hakkındaki bilgileri içerir. Bu türün olayları, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sağlayıcılar tarafından değil, sistem tarafından tetiklenir.|  
|<xref:System.Windows.Automation.AutomationPropertyChangedEventArgs>|Bir öğenin veya denetim deseninin özellik değerindeki bir değişiklik hakkındaki bilgileri içerir.|  
|<xref:System.Windows.Automation.StructureChangedEventArgs>|Ağaçtaki bir değişiklik hakkındaki bilgileri içerir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
|<xref:System.Windows.Automation.WindowClosedEventArgs>|Bir pencere kapatma hakkında bilgi içerir.|  
  
 Tüm olay bağımsız değişkeni sınıfları bir <xref:System.Windows.Automation.AutomationEventArgs.EventId%2A> üye içerir. Bu tanımlayıcı bir içinde kapsüllenir <xref:System.Windows.Automation.AutomationEvent> .  
  
 <xref:System.Windows.Automation.AutomationEvent>Olayları tanımlamak için kullanılan nesneler, içindeki alanlar <xref:System.Windows.Automation.AutomationElementIdentifiers> ve denetim deseninin tanımlayıcı sınıflarında bulunan sağlayıcılar tarafından alınır <xref:System.Windows.Automation.DockPatternIdentifiers> . Eşdeğer alanlar, içindeki alanlardan istemci uygulamalar tarafından <xref:System.Windows.Automation.AutomationElement> ve gibi denetim deseninin elde edilir <xref:System.Windows.Automation.DockPattern> .  
  
 Olay tanımlayıcılarının listesi için bkz. [istemciler Için UI Otomasyon olayları](ui-automation-events-for-clients.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İstemciler İçin UI Otomasyon Olayları](ui-automation-events-for-clients.md)
- [Sunucu Tarafı UI Otomasyonu Sağlayıcıyı Uygulama](server-side-ui-automation-provider-implementation.md)
- [UI Otomasyon Olaylarına Abone Olma](subscribe-to-ui-automation-events.md)
