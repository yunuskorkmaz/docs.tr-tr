---
title: RadioButton Denetim Türü için UI Otomasyon Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Radio Button
- UI Automation, Radio Button control type
- RadioButton control type
ms.assetid: 87170464-7857-41f1-bcf7-bb41be31cb53
ms.openlocfilehash: 741f2ef27ece7e9bfd10646b4c0ff1b6367a1261
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179671"
---
# <a name="ui-automation-support-for-the-radiobutton-control-type"></a>RadioButton Denetim Türü için UI Otomasyon Desteği
> [!NOTE]
> Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır. Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu RadioButton denetim türü için destek hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bilgi sağlar. Denetim [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]türü, <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> özelliği kullanmak için denetimin karşılaması gereken koşullar kümesidir. Koşullar, ağaç yapısı, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerleri ve denetim desenleri için özel yönergeler içerir.  
  
 Radyo düğmesi, yuvarlak bir düğme ve uygulama tanımlı metin (etiket), bir simge veya kullanıcının düğmeyi seçerek yapabileceğiniz bir seçimi gösteren bir bit eşlemeden oluşur. Bir uygulama genellikle bir grup kutusunda radyo düğmeleri kullanarak kullanıcının ilgili ancak birbirini dışlayan seçenekler kümesi arasından seçim yapmasını sağlar. Örneğin, uygulama, kullanıcının istemci alanında seçilen metin için biçim tercihi seçebileceği bir radyo düğmesi grubu sunabilir. Kullanıcı, ilgili radyo düğmesini seçerek sol ait, sağa hizalanmış veya ortalanmış bir biçim seçebilir. Genellikle, kullanıcı bir radyo düğmesi kümesinden aynı anda yalnızca bir seçenek seçebilir.  
  
 Aşağıdaki bölümlerde RadioButton denetim türü için gerekli [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısı, özellikleri, denetim desenleri ve olayları tanımlanır. Gereksinimler, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Win32 veya [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]Windows Forms olsun, tüm liste denetimleri için geçerlidir.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyon Ağaç Yapısı  
 Aşağıdaki tablo, radyo düğmesi denetimlerine ait [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olan ağacın denetim görünümünü ve içerik görünümünü görüntüler ve her görünümde nelerin bulunabileceğini açıklar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ağaç hakkında daha fazla bilgi için [UI Automation Tree Genel Bakış'a](ui-automation-tree-overview.md)bakın.  
  
|Kontrol Görünümü|İçerik Görünümü|  
|------------------|------------------|  
|RadioButton|RadioButton|  
  
 Denetim görünümünde veya içerik görünümünde çocuk yok.  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon Özellikleri  
 Aşağıdaki tabloda, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] değeri veya tanımı özellikle RadioButton denetim türüyle alakalı olan özellikleri listelenir. Özellikler hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] daha fazla bilgi [için, Müşteriler için Kullanıcı Arabirimi Otomasyon Özellikleri'ne](ui-automation-properties-for-clients.md)bakın.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Özellik|Değer|Notlar|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlara bakın.|Bu özelliğin değeri, bir uygulamadaki tüm denetimler arasında benzersiz olmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlara bakın.|Tüm denetimi içeren en dıştaki dikdörtgen.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Notlara bakın.|Denetim klavye odağı alabiliyorsa, bu özelliği desteklemesi gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlara bakın.|Radyo düğmesi denetiminin adı, seçim durumunu koruyan düğmenin yanında görüntülenen metindir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Notlara bakın.|Radyo düğmesi denetiminin tıklanabilir noktası, fare işaretçisi ile tıklandığında radyo düğmesinde seçimi ayarlayan bir nokta olmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Radyo düğmeleri kendi kendini etiketleme denetimleridir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|RadioButton|Bu değer tüm [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] çerçeveler için aynıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"radyo düğmesi"|RadioButton Denetim Türüne karşılık gelen yerelleştirilmiş dize.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|Radyo düğmesi denetimi her zaman [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacın içerik görünümüne dahildir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Radyo düğmesi denetimi her zaman [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacın denetim görünümüne dahildir.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>
## <a name="required-ui-automation-control-patterns"></a>Gerekli UI Otomasyon Kontrol Desenleri  
 Aşağıdaki tabloda, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tüm radyo düğmesi denetimleri tarafından desteklenmesi gereken denetim desenleri listelenir. Denetim desenleri hakkında daha fazla bilgi için [UI Otomasyon Kontrol Modellerine Genel Bakış'a](ui-automation-control-patterns-overview.md)bakın.  
  
|Kontrol Deseni/Kontrol Deseni Özelliği|Destek / Değer|Notlar|  
|-----------------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Evet|Tüm radyo düğmesi denetimleri, seçilmelerini sağlamak için Seçim Öğesi deseni desteklemelidir.|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider.SelectionContainer%2A>|Notlara bakın.|Kullanıcı `SelectionContainerProperty` Arabirimi Otomasyon istemcisinin belirli bir bağlam içindeki diğer radyo düğmelerinin birbiriyle ilişkili olduğunu belirleyebilmeleri için her zaman tamamlanması gerekir.  Radyo düğmesinin Win32 sürümü için bu özellik desteklenmez, çünkü bu eski çerçeveden bu bilgileri almak mümkün değildir.|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|Hiçbir zaman|Radyo düğmesi ayarlandıktan sonra durumu boyunca geçiş yapamaz.  Bu desen hiçbir zaman radyo düğmesinde desteklenmemelidir.|  
  
<a name="Required_UI_Automation_Events"></a>
## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyon Etkinlikleri  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tüm radyo düğmesi denetimleri tarafından desteklenmesi gereken olaylar listelenmektedir. Etkinlikler hakkında daha fazla bilgi için [UI Otomasyon Etkinliklerine Genel Bakış'a](ui-automation-events-overview.md)bakın.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Olay|Destek|Notlar|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|Gerekli|None|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Gerekli|None|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>özellik değiştirilen olay.|Hiçbir zaman|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>özellik değiştirilen olay.|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>özellik değiştirilen olay.|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>özellik değiştirilen olay.|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|None|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.ControlType.RadioButton>
- [UI Otomasyonu Denetim Türlerine Genel Bakış](ui-automation-control-types-overview.md)
- [UI Otomasyonuna Genel Bakış](ui-automation-overview.md)
