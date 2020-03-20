---
title: ListItem Denetim Türü için UI Otomasyon Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- control types, List
- List Item control type
- UI Automation, List Item control type
ms.assetid: 34f533bf-fc14-4e78-8fee-fb7107345fab
ms.openlocfilehash: 245f9030897d54a2f1c95d5ce6369b67d23cb319
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179694"
---
# <a name="ui-automation-support-for-the-listitem-control-type"></a>ListItem Denetim Türü için UI Otomasyon Desteği
> [!NOTE]
> Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır. Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu <xref:System.Windows.Automation.ControlType.ListItem> konu, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] denetim türü için destek hakkında bilgi sağlar. Denetim [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]türü, <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> özelliği kullanmak için denetimin karşılaması gereken koşullar kümesidir. Koşullar, ağaç yapısı, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerleri ve denetim desenleri için özel yönergeler içerir.  
  
 Liste öğesi denetimleri, ListItem denetim türünü uygulayan denetimlerin bir örneğidir.  
  
 Aşağıdaki bölümler, ListItem denetim türü için gerekli [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısını, özelliklerini, denetim desenlerini ve olaylarını tanımlar. Gereksinimler, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Win32 veya [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]Windows Forms olsun, tüm liste denetimleri için geçerlidir.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyon Ağaç Yapısı  
 Aşağıdaki tablo, liste öğesi denetimleri ile [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ilgili denetim görünümünü ve ağacın içerik görünümünü görüntüler ve her görünümde nelerin bulunabileceğini açıklar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ağaç hakkında daha fazla bilgi için [UI Automation Tree Genel Bakış'a](ui-automation-tree-overview.md)bakın.  
  
|Kontrol Görünümü|İçerik Görünümü|  
|------------------|------------------|  
|Listıtem<br /><br /> - Resim (0 veya daha fazla)<br />- Metin (0 veya daha fazla)<br />- Edit (0 veya daha fazla)|Listıtem|  
  
 Ağacın içerik görünümündeki liste öğesi denetiminin [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] çocukları her zaman "0" olmalıdır. Denetimin yapısı, liste öğesinin altında diğer öğelerin de yer aldığı şekildeyse, TreeItem Denetim Türü denetim türü [için UI Otomasyon Desteği](ui-automation-support-for-the-treeitem-control-type.md) gereksinimlerini izlemelidir.  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon Özellikleri  
 Aşağıdaki tablo, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] değeri veya tanımı özellikle liste öğesi denetimleri ile alakalı olan özellikleri listeler. Özellikler hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] daha fazla bilgi [için, Müşteriler için Kullanıcı Arabirimi Otomasyon Özellikleri'ne](ui-automation-properties-for-clients.md)bakın.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Özellik|Değer|Notlar|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlara bakın.|Bu özelliğin değeri, bir uygulamadaki tüm denetimler arasında benzersiz olmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlara bakın.|Bu özelliğin bu değeri, resim alanını ve liste öğesinin metin içeriğini içermelidir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|-sına bağ -lıdır|Liste denetiminde tıklanabilir bir nokta varsa (listenin odaklanmasına neden olmak için tıklanabilecek bir nokta) bu noktanın bu özellik aracılığıyla açıkta kalması gerekir. Liste denetimi tamamen soyundan gelen liste öğeleri <xref:System.Windows.Automation.NoClickablePointException> ile kaplanmışsa, istemcinin liste denetimindeki bir öğeyi tıklatılabilir bir nokta için istemesi gerektiğini belirtmek için bir öğe yi yükseltir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlara bakın.|Liste öğesi denetiminin değeri, öğenin metin içeriğinden gelir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Notlara bakın.|Statik bir metin etiketi varsa, bu özellik bu denetime bir başvuru göstermelidir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Listıtem|Bu değer tüm Ara bilgi arabirimi çerçeveleri için aynıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"liste öğesi"|ListItem denetim türüne karşılık gelen yerelleştirilmiş dize.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|Liste denetimi her zaman [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacın içerik görünümüne eklenir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Liste denetimi her zaman [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacın denetim görünümüne dahildir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|True|Kapsayıcı klavye girişini kabul edebiliyorsa, bu özellik değeri doğru olmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|""|Liste denetimleri için Yardım metni, kullanıcıdan neden bir araç ipucu aracılığıyla sunulan aynı bilgi türü olan seçenekler listesinden seçim yapmasının istendiğini açıklamalıdır. Örneğin, "Monitörünüzün ekran çözünürlüğünü ayarlamak için bir öğe seçin."|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemTypeProperty>|-sına bağ -lıdır|Bu özellik, altta yatan bir nesneyi temsil eden liste öğesi denetimleri için açıklanmalıdır. Bu liste öğesi denetimleri genellikle kullanıcıların temel nesne ile ilişkilendirmek denetimile ilişkili bir simge var.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>|-sına bağ -lıdır|Bu özellik, liste öğesinin kaydırma denetim deseni uygulayan üst kapsayıcıiçinde şu anda görünüme kaydırılıp kaydırılmadığına dair bir değer döndürmelidir.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>
## <a name="required-ui-automation-control-patterns"></a>Gerekli UI Otomasyon Kontrol Desenleri  
 Aşağıdaki tablo, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] liste öğesi denetimleri tarafından desteklenmesi gereken denetim desenlerini listeler. Denetim desenleri hakkında daha fazla bilgi için [UI Otomasyon Kontrol Modellerine Genel Bakış'a](ui-automation-control-patterns-overview.md)bakın.  
  
|Kontrol Deseni|Destek|Notlar|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Evet|Liste öğesi denetimi bu denetim deseni uygulamalıdır. Bu, liste öğeleri denetimlerinin seçildiğinde iletilmesine olanak tanır.|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|-sına bağ -lıdır|Liste öğesi kaydırılabilir bir kapsayıcı içinde yer alıyorsa, bu denetim deseni uygulanmalıdır.|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|-sına bağ -lıdır|Liste öğesi denetlenebilir sa yılabilir ve eylem bir seçim durumu değişikliği gerçekleştirmezse, bu denetim deseni uygulanmalıdır.|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|-sına bağ -lıdır|Öğe bilgileri göstermek veya gizlemek için manipüle edilebilirse, bu denetim deseni uygulanmalıdır.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|-sına bağ -lıdır|Öğe düzenlenebilirse, bu denetim deseni uygulanmalıdır. Liste öğesi denetiminde yapılan değişiklikler <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>, ve <xref:System.Windows.Automation.Provider.IValueProvider.Value%2A>.|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider>|-sına bağ -lıdır|Öğeden öğeye mekansal gezinti liste kapsayıcıiçinde desteklenir ve kapsayıcı satır lar ve sütunlar halinde düzenlenirse, Kılavuz Öğesi denetim deseni uygulanmalıdır.|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider>|-sına bağ -lıdır|Öğenin üzerinde seçimden ayrı olarak gerçekleştirilebilecek bir komut varsa, bu desen uygulanmalıdır. Bu genellikle liste öğesi denetimi çift tıklatma ile ilişkili bir eylemdir. Örnekler, Microsoft Windows Gezgini'nden bir belge başlatmak veya Microsoft Windows Media Player'da bir müzik dosyası çalmak olabilir.|  
  
<a name="Required_UI_Automation_Events"></a>
## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyon Etkinlikleri  
 Aşağıdaki tablo, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tüm liste öğesi denetimleri tarafından desteklenmesi gereken olayları listeler. Etkinlikler hakkında daha fazla bilgi için [UI Otomasyon Etkinliklerine Genel Bakış'a](ui-automation-events-overview.md)bakın.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Olay|Destek|Notlar|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|-sına bağ -lıdır|None|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>|Gerekli|None|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|Gerekli|None|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>özellik değiştirilen olay.|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>özellik değiştirilen olay.|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>özellik değiştirilen olay.|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemStatusProperty>özellik değiştirilen olay.|-sına bağ -lıdır|None|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty>özellik değiştirilen olay.|-sına bağ -lıdır|None|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty>özellik değiştirilen olay.|-sına bağ -lıdır|None|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>özellik değiştirilen olay.|-sına bağ -lıdır|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|None|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.ControlType.ListItem>
- [UI Otomasyonu Denetim Türlerine Genel Bakış](ui-automation-control-types-overview.md)
- [UI Otomasyonuna Genel Bakış](ui-automation-overview.md)
