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
ms.openlocfilehash: d342e4382cfe227e477ab87c2ca428834010768e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71042156"
---
# <a name="ui-automation-events-overview"></a>UI Otomasyonu Olaylarına Genel Bakış
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir. Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]olay bildirimi, ekran okuyucular ve ekran büyüteçleri gibi yardımcı teknolojiler için önemli bir özelliktir. Bu UI Otomasyonu istemcileri, [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] içinde bir şeyler olduğunda UI Otomasyon sağlayıcıları tarafından oluşturulan olayları izler ve son kullanıcıları bilgilendirmek için bu bilgileri kullanır.  
  
 Herhangi bir istemcinin herhangi bir olayı dinlememesi durumunda, hiçbir istemcinin bu olaylara abone olup olmadığı veya hiç bir şekilde değil, herhangi bir istemciye etkinlik yapmasına izin vererek verimlilik geliştirilmiştir.  
  
<a name="Types_of_Events"></a>   
## <a name="types-of-events"></a>Olay türleri  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]olaylar aşağıdaki kategorilere ayrılır.  
  
|Olay|Açıklama|  
|-----------|-----------------|  
|Özellik değişikliği|Bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] öğe veya denetim deseninin bir özelliği değiştiğinde tetiklenir. Örneğin, bir istemcinin bir uygulamanın onay kutusu denetimini izlemesi gerekiyorsa, <xref:System.Windows.Automation.TogglePattern.TogglePatternInformation.ToggleState%2A> özellik üzerinde bir özellik değişiklik olayını dinlemek için kayıt yapabilir. Onay kutusu denetimi işaretli veya işaretlenmemiş olduğunda, sağlayıcı olayı başlatır ve istemci gerektiği gibi davranabilir.|  
|Öğe eylemi|Son Kullanıcı veya programlı etkinlikteki [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] sonuçlarda değişiklik yapıldığında, örneğin bir düğmeye tıklandığında veya aracılığıyla <xref:System.Windows.Automation.InvokePattern>çağrıldığında tetiklenir.|  
|Yapı değişikliği|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ağacın yapısı değiştiğinde harekete geçirilir. Yapı, yeni [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğeler görünür olduğunda, gizlendiği veya masaüstünde kaldırıldığında değişir.|  
|Genel masaüstü değişikliği|Odak bir öğeden diğerine kaydırıldığında veya bir pencere kapandığında olduğu gibi, istemci için genel ilgi çekici eylemler gerçekleştiğinde tetiklenir.|  
  
 Bazı olaylar, Kullanıcı arabiriminin durumunun değiştiği anlamına gelmez. Örneğin, Kullanıcı bir metin girişi alanını sekmeler ve sonra alanı güncelleştirmek için bir düğmeye tıkladığında, `TextChangedEvent` Kullanıcı gerçekten metni değiştirmese bile oluşturulur. Bir olayı işlerken, bir istemci uygulaması, işlem yapılmadan önce herhangi bir şeyin gerçekten değişip değişmediğini kontrol etmek için gerekli olabilir.  
  
 Aşağıdaki olaylar, Kullanıcı arabiriminin durumu değiştirilmese bile oluşturulabilir.  
  
- `AutomationPropertyChangedEvent`(değiştirilen özelliğe bağlı olarak)  
  
- `ElementSelectedEvent`  
  
- `InvalidatedEvent`  
  
- `TextChangedEvent`  
  
<a name="UI_Automation_Event_Identifiers"></a>   
## <a name="ui-automation-event-identifiers"></a>UI Otomasyonu olay tanımlayıcıları  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]olaylar nesneler tarafından <xref:System.Windows.Automation.AutomationEvent> tanımlanır. <xref:System.Windows.Automation.AutomationIdentifier.Id%2A> Özelliği, olay türünü benzersiz bir şekilde tanımlayan bir değer içerir.  
  
 İçin <xref:System.Windows.Automation.AutomationIdentifier.Id%2A> olası değerler aşağıdaki tabloda, olay bağımsız değişkenleri için kullanılan türle birlikte verilmiştir. İstemciler ve sağlayıcılar tarafından kullanılan tanımlayıcıların farklı sınıflardan aynı adlı alanları olduğunu unutmayın.  
  
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
  
|örneği|Açıklama|  
|-----------|-----------------|  
|<xref:System.Windows.Automation.AsyncContentLoadedEventArgs>|Tamamlanan yükleme yüzdesi de dahil olmak üzere içeriğin zaman uyumsuz yüklemesi hakkındaki bilgileri içerir.|  
|<xref:System.Windows.Automation.AutomationEventArgs>|Ek veri gerektirmeyen basit bir olayla ilgili bilgiler içerir.|  
|<xref:System.Windows.Automation.AutomationFocusChangedEventArgs>|Giriş odağıyla ilgili, bir öğeden diğerine değişiklik hakkındaki bilgileri içerir. Bu türün olayları, sağlayıcılar tarafından değil, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sistem tarafından tetiklenir.|  
|<xref:System.Windows.Automation.AutomationPropertyChangedEventArgs>|Bir öğenin veya denetim deseninin özellik değerindeki bir değişiklik hakkındaki bilgileri içerir.|  
|<xref:System.Windows.Automation.StructureChangedEventArgs>|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ağaçtaki bir değişiklik hakkındaki bilgileri içerir.|  
|<xref:System.Windows.Automation.WindowClosedEventArgs>|Bir pencere kapatma hakkında bilgi içerir.|  
  
 Tüm olay bağımsız değişkeni sınıfları bir <xref:System.Windows.Automation.AutomationEventArgs.EventId%2A> üye içerir. Bu tanımlayıcı bir <xref:System.Windows.Automation.AutomationEvent>içinde kapsüllenir.  
  
 Olayları <xref:System.Windows.Automation.AutomationEvent> tanımlamak için kullanılan nesneler, içindeki alanlar ve denetim <xref:System.Windows.Automation.DockPatternIdentifiers>deseninin tanımlayıcı sınıflarında <xref:System.Windows.Automation.AutomationElementIdentifiers> bulunan sağlayıcılar tarafından alınır. Eşdeğer alanlar, içindeki <xref:System.Windows.Automation.AutomationElement> alanlardan istemci uygulamalar tarafından ve gibi denetim deseninin <xref:System.Windows.Automation.DockPattern>elde edilir.  
  
 Olay tanımlayıcılarının listesi için bkz. [istemciler Için UI Otomasyon olayları](ui-automation-events-for-clients.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İstemciler İçin UI Otomasyonu Olayları](ui-automation-events-for-clients.md)
- [Sunucu Tarafı UI Otomasyonu Sağlayıcısı Uygulama](server-side-ui-automation-provider-implementation.md)
- [UI Otomasyonu Olaylarına Abone Olma](subscribe-to-ui-automation-events.md)
