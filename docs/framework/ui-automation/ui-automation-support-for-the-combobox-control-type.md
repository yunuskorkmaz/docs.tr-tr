---
title: ComboBox Denetim Türü için UI Otomasyon Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Combo Box
- UI Automation, Combo Box control type
- ComboBox controls
ms.assetid: bb321126-4770-41da-983a-67b7b89d45dd
ms.openlocfilehash: 2b1629adcc9e23294daa0512070089cc72ab5810
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179789"
---
# <a name="ui-automation-support-for-the-combobox-control-type"></a>ComboBox Denetim Türü için UI Otomasyon Desteği
> [!NOTE]
> Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır. Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ComboBox denetim türü için destek hakkında bilgi sağlar. Denetim [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]türü, <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> özelliği kullanmak için denetimin karşılaması gereken koşullar kümesidir. Koşullar, ağaç yapısı, özellik [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] değerleri, denetim desenleri ve [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olaylar için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özel yönergeler içerir.  
  
 Açılan kutu, açılan kutunun liste kutusu bölümünde şu anda seçili öğeyi görüntüleyen statik denetim veya bir edit denetimiyle birlikte bir liste kutusudur. Denetimin liste kutusu bölümü her zaman görüntülenir veya yalnızca kullanıcı denetimin yanındaki açılır ok (düğme olan) seçtiğinde görünür. Seçim alanı bir denetim denetimiise, kullanıcı listede olmayan bilgileri girebilir; aksi takdirde, kullanıcı yalnızca listedeki öğeleri seçebilir.  
  
 Aşağıdaki bölümler, ComboBox denetim türü için gerekli [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısını, özelliklerini, denetim modellerini ve olaylarını tanımlar. Gereksinimler, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Win32 veya Windows [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]Forms olsun, tüm açılan kutu denetimleri için geçerlidir.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyon Ağaç Yapısı  
 Aşağıdaki tablo, açılan kutu denetimleri ile [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ilgili ağacın denetim görünümünü ve içerik görünümünü görüntüler ve her görünümde nelerin bulunabileceğini açıklar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ağaç hakkında daha fazla bilgi için [UI Automation Tree Genel Bakış'a](ui-automation-tree-overview.md)bakın.  
  
|Kontrol Görünümü|İçerik Görünümü|  
|------------------|------------------|  
|ComboBox<br /><br /> - Edit (0 veya 1)<br />- Liste (1)<br />- Liste Öğesi (Listenin alt öğesi; 0'dan çok'a)<br />- Düğme (1)|ComboBox<br /><br /> - Liste Öğesi (0'dan çok'a)|  
  
 Açılan kutunun denetim görünümündeki düzenleme denetimi, yalnızca açılan kutu, Çalıştır iletişim kutusundaki açılan kutuda olduğu gibi herhangi bir giriş almak için düzenlenebilirse gereklidir.  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon Özellikleri  
 Aşağıdaki tabloda, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] değeri veya tanımı özellikle açılan kutu denetimleri ile ilgili özellikleri listelenir. Özellikler hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] daha fazla bilgi [için, Istemciler için Kullanıcı Arabirimi Otomasyon Özellikleri'ne](ui-automation-properties-for-clients.md)bakın.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Özellik|Değer|Notlar|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlara bakın.|Bu özelliğin değeri, bir uygulamadaki tüm denetimler arasında benzersiz olmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlara bakın.|Tüm denetimi içeren en dıştaki dikdörtgen.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Notlara bakın.|Sınırlayıcı bir dikdörtgen varsa desteklenir. Sınırlayıcı dikdörtgen içindeki her nokta tıklatılabilir değilse ve özel isabet testi gerçekleştirin, sonra geçersiz kılınve tıklanabilir bir nokta sağlayın.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|ComboBox|Bu değer tüm [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] çerçeveler için aynıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|Notlara bakın.|Açılan kutu denetimleri için yardım metni, kullanıcıdan neden açılan kutudan bir seçenek seçmesinin istendiğini açıklamalıdır. Metin, araç ipucu aracılığıyla sunulan bilgilere benzer. Örneğin, "Monitörünüzün ekran çözünürlüğünü ayarlamak için bir öğe seçin."|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|Açılan kutu denetimleri her zaman [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacın içerik görünümüne dahildir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Açılan kutu denetimleri her zaman [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacın denetim görünümüne dahildir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|True|Açılan kutu denetimleri, seçim kabından bir öğe kümesini ortaya çıkarır. Açılan kutu denetimi klavye odağı alabilir, ancak bir UI Automation istemcisi bir açılan kutuya odaklandığında, açılan kutu alt ağacındaki öğeler odaklayabilir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Notlara bakın.|Açılan kutu denetimleri genellikle bu özelliğin başvurulmuştettiği statik bir metin etiketine sahiptir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"açılan kutu"|ComboBox denetim türüne karşılık gelen yerelleştirilmiş dize.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlara bakın.|Açılan kutu denetimi genellikle adını statik metin denetiminden alır.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>
## <a name="required-ui-automation-control-patterns"></a>Gerekli UI Otomasyon Kontrol Desenleri  
 Aşağıdaki tablo, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tüm açılan kutu denetimleri tarafından desteklenmesi gereken denetim desenlerini listeler. Denetim desenleri hakkında daha fazla bilgi için [UI Otomasyon Kontrol Modellerine Genel Bakış'a](ui-automation-control-patterns-overview.md)bakın.  
  
|Kontrol Deseni|Destek|Notlar|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Evet|Açılan kutu denetimi, açılan kutu olabilmesi için her zaman açılır düğmeyi içermelidir.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Evet|Geçerli seçimi açılan kutuda görüntüler. Bu destek, açılan kutunun altındaki liste kutusuna devredilir.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|-sına bağ -lıdır|Açılan kutu rasgele metin değerlerini alma yeteneğine sahipse, Değer deseni desteklenmelidir. Bu desen, açılan kutunun dize içeriğini programlı olarak ayarlama olanağı sağlar. Değer deseni desteklenmezse, bu, kullanıcının açılan kutunun alt ağacındaki liste öğelerinden seçim yapması gerektiğini gösterir.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Hiçbir zaman|Kaydırma deseni hiçbir zaman doğrudan açılan kutuda desteklenmez. Açılan kutu içinde bulunan bir liste kutusu kaydırAbiliyorsa desteklenir. Yalnızca liste kutusu ekranda görünür olduğunda desteklenebilir.|  
  
<a name="Required_Events"></a>
## <a name="required-events"></a>Gerekli Olaylar  
 Aşağıdaki tabloda, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tüm açılan kutu denetimleri tarafından desteklenmesi gereken olaylar listelenmektedir. Etkinlikler hakkında daha fazla bilgi için [UI Otomasyon Etkinliklerine Genel Bakış'a](ui-automation-events-overview.md)bakın.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Olay|Destek|Notlar|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>özellik değiştirilen olay.|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>özellik değiştirilen olay.|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>özellik değiştirilen olay.|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|None|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty>özellik değiştirilen olay.|Gerekli|None|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty>özellik değiştirilen olay.|-sına bağ -lıdır|Denetim Değer deseni destekliyorsa, bu olayı desteklemesi gerekir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.ControlType.ComboBox>
- [UI Otomasyonu Denetim Türlerine Genel Bakış](ui-automation-control-types-overview.md)
- [UI Otomasyonuna Genel Bakış](ui-automation-overview.md)
