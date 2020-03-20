---
title: Takvim Denetim Türü İçin UI Otomasyon Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Calendar control type
- Calendar control type
- control types, Calendar
ms.assetid: e91a7393-a7f9-4838-a1a6-857438b24bc9
ms.openlocfilehash: b9b7e999c20c97acd1da4d6afedbac9177996ebe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179826"
---
# <a name="ui-automation-support-for-the-calendar-control-type"></a>Takvim Denetim Türü İçin UI Otomasyon Desteği
> [!NOTE]
> Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır. Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Takvim denetim türü için destek hakkında bilgi sağlar. Denetim [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]türü, <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> özelliği kullanmak için denetimin karşılaması gereken koşullar kümesidir. Koşullar, ağaç yapısı, özellik [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] değerleri, denetim desenleri ve [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olaylar için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özel yönergeler içerir.  
  
 Takvim denetimleri, kullanıcının tarihi kolayca belirlemesine ve diğer tarihleri seçmesine olanak sağlar.  
  
 Aşağıdaki bölümler, Takvim [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] denetim türü için gerekli ağaç yapısını, özelliklerini, denetim modellerini ve olaylarını tanımlar. Gereksinimler, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Win32 veya [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]Windows Forms olsun, tüm takvim denetimleri için geçerlidir.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyon Ağaç Yapısı  
 Aşağıdaki tablo, takvim denetimleri ile ilgili [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] denetim görünümünü ve ağacın içerik görünümünü gösterir ve her görünümde nelerin bulunabileceğini açıklar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ağaç hakkında daha fazla bilgi için [UI Automation Tree Genel Bakış'a](ui-automation-tree-overview.md)bakın.  
  
|Kontrol Görünümü|İçerik Görünümü|  
|------------------|------------------|  
|Takvim<br /><br /> <ul><li>DataGrid<br /><br /> <ul><li>Üstbilgi (0 veya 1)</li><li>Üstbilgi Öğesi (0 veya 7; miktar sütunlarda kaç gün görüntülendiğine bağlıdır)</li><li>ListItem (miktar kaç gün görüntülendiğine bağlıdır)</li><li>Düğme (0 veya 2; takvim görünümü için)</li></ul></li></ul>|Takvim<br /><br /> - ListItem (miktar kaç gün görüntülendiğine bağlıdır)|  
  
 Takvim denetimleri kullanıcı arabirimi içinde birçok farklı biçimde temsil edilebilir. Ağacın denetim görünümünde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olması için tek garantili denetimler veri ızgarası, üstbilgi, üstbilgi öğesi ve liste öğesi denetimleridir.  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon Özellikleri  
 Aşağıdaki tablo, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] değeri veya tanımı özellikle takvim denetimleri ile ilgili özellikleri listeler. Özellikler hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] daha fazla bilgi [için, Müşteriler için Kullanıcı Arabirimi Otomasyon Özellikleri'ne](ui-automation-properties-for-clients.md)bakın.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Özellik|Değer|Notlar|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlara bakın.|Bu özelliğin değeri, bir uygulamadaki tüm denetimler arasında benzersiz olmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlara bakın.|Tüm denetimi içeren en dıştaki dikdörtgen.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Notlara bakın.|Sınırlayıcı bir dikdörtgen varsa desteklenir. Sınırlayıcı dikdörtgen içindeki her nokta tıklatılabilir değilse ve özel isabet testi gerçekleştirin, sonra geçersiz kılınve tıklanabilir bir nokta sağlayın.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Takvim|Bu değer tüm [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] çerçeveler için aynıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|Takvim denetimi her zaman [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacın içerik görünümüne eklenir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Takvim denetimi her zaman [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacın denetim görünümüne eklenir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Notlara bakın.|Denetim klavye odağı alabiliyorsa, bu özelliği desteklemesi gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Notlara bakın.|Belge denetiminin etiketi. Genellikle, belgenin başlığı kullanılır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"takvim"|Takvim denetim türüne karşılık gelen yerelleştirilmiş dize.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlara bakın.|Takvim denetimi genellikle adını geçerli günün tarihinden alır.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>
## <a name="required-ui-automation-control-patterns"></a>Gerekli UI Otomasyon Kontrol Desenleri  
 Aşağıdaki tablo, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tüm takvim denetimleri tarafından desteklenmesi gereken denetim desenleri listeler. Denetim desenleri hakkında daha fazla bilgi için [UI Otomasyon Kontrol Modellerine Genel Bakış'a](ui-automation-control-patterns-overview.md)bakın.  
  
|Kontrol Deseni/Desen Özelliği|Destek|Notlar|  
|---------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider>|Evet|Takvim denetimi her zaman Izgara deseni destekler, çünkü bir ay içindeki günler uzamsal olarak gezinilebilen öğelerdir.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|-sına bağ -lıdır|Takvim denetimlerin çoğu görünümü sayfaya çevirmeyi destekler. Kaydırma deseni, kaydırma gezintisini desteklemek için önerilir.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|-sına bağ -lıdır|Çoğu takvim denetimi, alt öğenin seçimi olarak belirli bir günü, ayı veya yılı korur. Bazı takvimler çok seçilebilir ve diğerleri yalnızca tek seçilebilir.|  
|<xref:System.Windows.Automation.Provider.ITableProvider>|Evet|Takvim denetiminin her zaman alt ağacıiçinde haftanın günleri için bir üstbilgi vardır, bu nedenle Tablo deseni desteklenmelidir.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Hayır|Değeri doğrudan denetime ayarlayamadığından, takvim denetimleri için Değer denetimi deseni gerekli değildir. Denetimle belirli bir tarih ilişkilendirilirse, bilgiler Seçim denetim deseni tarafından sağlanmalıdır.|  
  
<a name="Required_UI_Automation_Events"></a>
## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyon Etkinlikleri  
 Aşağıdaki tablo, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tüm takvim denetimleri tarafından desteklenmesi gereken olayları listeler. Etkinlikler hakkında daha fazla bilgi için [UI Otomasyon Etkinliklerine Genel Bakış'a](ui-automation-events-overview.md)bakın.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Olay|Destek|Notlar|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>özellik değiştirilen olay.|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>özellik değiştirilen olay.|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>özellik değiştirilen olay.|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent>|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|None|  
|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers.CurrentViewProperty>özellik değiştirilen olay.|-sına bağ -lıdır|None|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>özellik değiştirilen olay.|-sına bağ -lıdır|Denetim Kaydırma denetim deseni destekliyorsa, bu olayı desteklemesi gerekir.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty>özellik değiştirilen olay.|-sına bağ -lıdır|Denetim Kaydırma denetim deseni destekliyorsa, bu olayı desteklemesi gerekir.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty>özellik değiştirilen olay.|-sına bağ -lıdır|Denetim Kaydırma denetim deseni destekliyorsa, bu olayı desteklemesi gerekir.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty>özellik değiştirilen olay.|-sına bağ -lıdır|Denetim Kaydırma denetim deseni destekliyorsa, bu olayı desteklemesi gerekir.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>özellik değiştirilen olay.|-sına bağ -lıdır|Denetim Kaydırma denetim deseni destekliyorsa, bu olayı desteklemesi gerekir.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty>özellik değiştirilen olay.|-sına bağ -lıdır|Denetim Kaydırma denetim deseni destekliyorsa, bu olayı desteklemesi gerekir.|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Gerekli|None|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.ControlType.Calendar>
- [UI Otomasyonu Denetim Türlerine Genel Bakış](ui-automation-control-types-overview.md)
- [UI Otomasyonuna Genel Bakış](ui-automation-overview.md)
