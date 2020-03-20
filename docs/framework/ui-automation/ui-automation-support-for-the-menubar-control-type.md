---
title: MenuBar Denetim Türü için UI Otomasyon Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Menu Bar control type
- control types, Menu Bar
- Menu Bar control type
ms.assetid: c1202b21-c1f0-4560-853c-7b99bd73ad97
ms.openlocfilehash: c50c5abb450ae44fcc08507354ea73f3a780afdf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179644"
---
# <a name="ui-automation-support-for-the-menubar-control-type"></a>MenuBar Denetim Türü için UI Otomasyon Desteği
> [!NOTE]
> Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır. Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu <xref:System.Windows.Automation.ControlType.MenuBar> konu, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] denetim türü için destek hakkında bilgi sağlar. Denetim [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]türü, <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> özelliği kullanmak için denetimin karşılaması gereken koşullar kümesidir. Koşullar, ağaç yapısı, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerleri ve denetim desenleri için özel yönergeler içerir.  
  
 Menü çubuğu denetimleri, MenuBar denetim türünü uygulayan denetimlerin bir örneğidir. Menü çubukları, kullanıcıların bir uygulamada bulunan komutları ve seçenekleri etkinleştirmeleri için bir araç sağlar.  
  
 Aşağıdaki bölümlerde MenuBar denetim türü için gerekli [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısı, özellikleri, denetim desenleri ve olayları tanımlanır. Gereksinimler, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Win32 veya [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]Windows Forms olsun, tüm liste denetimleri için geçerlidir.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyon Ağaç Yapısı  
 Aşağıdaki tablo, menü çubuğu denetimleri ile [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ilgili denetim görünümünü ve ağacın içerik görünümünü görüntüler ve her görünümde nelerin bulunabileceğini açıklar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ağaç hakkında daha fazla bilgi için [UI Automation Tree Genel Bakış'a](ui-automation-tree-overview.md)bakın.  
  
|Kontrol Görünümü|İçerik Görünümü|  
|------------------|------------------|  
|Menubar<br /><br /> - MenuItem (1 veya daha fazla)<br />- Diğer kontroller (0 veya çok)|Menubar<br /><br /> - MenuItem (1 veya daha fazla)<br />- Diğer kontroller (0 veya çok)|  
  
 Menü çubuğu denetimleri, yapısı içinde denetimleri ve açılan kutular gibi diğer denetimleri içerebilir. Bu ek denetimler, denetim ve içerik görünümlerinde yukarıda listelenen "diğer denetimlere" karşılık gelir.  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon Özellikleri  
 Aşağıdaki tabloda, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] değeri veya tanımı özellikle menü çubuğu denetimleri ile ilgili özellikleri listelenir. Özellikler hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] daha fazla bilgi [için, Müşteriler için Kullanıcı Arabirimi Otomasyon Özellikleri'ne](ui-automation-properties-for-clients.md)bakın.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Özellik|Değer|Notlar|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlara bakın.|Bu özellik tarafından maruz kalan değer, içerdiği tüm denetimleri içermelidir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlara bakın.|Bir uygulamada birden fazla menü çubuğu yoksa menü çubuğu denetiminin bir ad gerektirmemesi gerekir. Bir uygulamada birden fazla menü çubuğu varsa, bu özellik "Biçimlendirme" veya "Anahat Oluşturma" gibi ayırt edici adları ortaya çıkarmak için kullanılmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Menü çubuğu denetimleri hiçbir zaman bir etikete sahip olmaz.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Menubar|Bu değer tüm Ara bilgi arabirimi çerçeveleri için aynıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"menü çubuğu"|MenuBar denetim türüne karşılık gelen yerelleştirilmiş dize.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|Menü çubuğu denetimi her zaman [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacın içerik görünümüne dahildir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Menü çubuğu denetimi her zaman [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacın denetim görünümüne dahildir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>|Notlara bakın.|Bu özelliğin değeri, denetimin ekranda görüntülenip görüntülenmediğine bağlıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.OrientationProperty>|-sına bağ -lıdır|Bu özellik, menü çubuğu denetiminin yatay veya dikey olup olmadığını ortaya çıkarır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|True|Menü çubuğu denetimleri klavye ye odaklanabiliyor, çünkü içerdikleri denetimler klavye odağı alabilir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|Notlara bakın.|Menü çubuğu denetimi için Yardım metni nin gerekli olduğu senaryolar yoktur.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AcceleratorKeyProperty>|`Null`|Menü çubuklarında hiçbir zaman hızlandırıcı tuşları yoktur.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AccessKeyProperty>|"ALT"|ALT tuşuna basıldığında her zaman uygulama içindeki menü çubuğuna odak getirmelidir.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>
## <a name="required-ui-automation-control-patterns"></a>Gerekli UI Otomasyon Kontrol Desenleri  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] menü çubuğu denetimleri tarafından desteklenmesi gereken denetim desenleri listelenir. Denetim desenleri hakkında daha fazla bilgi için [UI Otomasyon Kontrol Modellerine Genel Bakış'a](ui-automation-control-patterns-overview.md)bakın.  
  
|Kontrol Deseni|Destek|Notlar|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|-sına bağ -lıdır|Denetim genişletilebilir veya daraltılabilirse, uygulayın. <xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|  
|<xref:System.Windows.Automation.Provider.IDockProvider>|-sına bağ -lıdır|Denetim ekranın farklı bölümlerine sabitlenebilirse, <xref:System.Windows.Automation.Provider.IDockProvider>uygulayın.|  
|<xref:System.Windows.Automation.Provider.ITransformProvider>|-sına bağ -lıdır|Denetim yeniden boyutlandırılabilir, döndürülebilir veya <xref:System.Windows.Automation.Provider.ITransformProvider>taşınabiliyorsa.|  
  
<a name="Required_UI_Automation_Events"></a>
## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyon Etkinlikleri  
 Aşağıdaki tabloda, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tüm menü çubuğu denetimleri tarafından desteklenmesi gereken olaylar listelenmektedir. Etkinlikler hakkında daha fazla bilgi için [UI Otomasyon Etkinliklerine Genel Bakış'a](ui-automation-events-overview.md)bakın.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Olay|Destek / Değer|Notlar|  
|---------------------------------------------------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>özellik değiştirilen olay.|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>özellik değiştirilen olay.|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>özellik değiştirilen olay.|Gerekli|None|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty>özellik değiştirilen olay.|-sına bağ -lıdır|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|None|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.ControlType.MenuBar>
- [UI Otomasyonu Denetim Türlerine Genel Bakış](ui-automation-control-types-overview.md)
- [UI Otomasyonuna Genel Bakış](ui-automation-overview.md)
