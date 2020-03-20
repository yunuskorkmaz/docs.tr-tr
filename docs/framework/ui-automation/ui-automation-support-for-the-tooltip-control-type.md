---
title: ToolTip Denetim Türü için UI Otomasyon Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, ToolTip control type
- ToolTip control type
- control types, ToolTip
ms.assetid: c3779d78-3164-43ae-8dae-bfaeafffdd65
ms.openlocfilehash: 8531270efb5a7bc5896c5d2fa04dd0632547cac7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179462"
---
# <a name="ui-automation-support-for-the-tooltip-control-type"></a>ToolTip Denetim Türü için UI Otomasyon Desteği
> [!NOTE]
> Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır. Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Araç İpucu denetim türü için destek hakkında bilgi sağlar. Denetim [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]türü, <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> özelliği kullanmak için denetimin karşılaması gereken koşullar kümesidir. Koşullar, ağaç yapısı, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerleri ve denetim desenleri için özel yönergeler içerir.  
  
 Araç ipucu denetimleri metin içeren açılır pencerelerdir.  
  
 Aşağıdaki bölümler, ToolTip denetim türü için gerekli [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısını, özelliklerini, denetim desenlerini ve olaylarını tanımlar. Gereksinimler, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Win32 veya [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]Windows Forms olsun, tüm araç ipucu denetimleri için geçerlidir.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyon Ağaç Yapısı  
 Aşağıdaki tablo, araç uç denetimiyle ilgili [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] denetim görünümünü ve ağacın içerik görünümünü görüntüler ve her görünümde nelerin bulunabileceğini açıklar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ağaç hakkında daha fazla bilgi için [UI Automation Tree Genel Bakış'a](ui-automation-tree-overview.md)bakın.  
  
|Kontrol Görünümü|İçerik Görünümü|  
|------------------|------------------|  
|ToolTip<br /><br /> - Metin (0 veya daha fazla)<br />- Resim (0 veya daha fazla)|ToolTip|  
  
 Araç ipucu denetimleri yalnızca klavye [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] odağı alabiliyorlarsa ağacın İçerik Görünümü'nde görünür. Aksi takdirde, araç ucunun tüm bilgileri, `HelpTextProperty` araç [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ucunun atıfta bulunduğu öğedeki bilgilerden elde edilir.  
  
 Araç ipuçları, bilgilerinin atıfta olduğu denetimin altında görünmelidir. İstemciler, `ToolTipOpenedEvent` araç ipuçlarında yer alan bilgileri sürekli olarak elde ettiklerinden emin olmak için dinlemelidir.  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon Özellikleri  
 Aşağıdaki tabloda, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] değeri veya tanımı özellikle araç ipucu denetimleri ile ilgili özellikleri listelenir. Özellikler hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] daha fazla bilgi [için, Istemciler için Kullanıcı Arabirimi Otomasyon Özellikleri'ne](ui-automation-properties-for-clients.md)bakın.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Özellik|Değer|Notlar|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlara bakın.|Bu özelliğin değeri, bir uygulamadaki tüm denetimler arasında benzersiz olmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlara bakın.|Tüm denetimi içeren en dıştaki dikdörtgen.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Notlara bakın.|Tıklanabilir nokta, araç ucunun denetimi kapatacak bölümü olmalıdır. Bazı araç ipuçları bu yeteneğe sahip değildir ve tıklanabilir bir noktaya sahip olmaz.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Notlara bakın.|Denetim klavye odağı alabiliyorsa, bu özelliği desteklemesi gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlara bakın.|Araç ipucu denetiminin adı, araç ipucuiçinde görüntülenen metindir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Araç ipucu denetimleri her zaman içeriği tarafından kendi kendine etiketlenir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|ToolTip|Bu değer tüm Ara bilgi arabirimi çerçeveleri için aynıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"araç ucu"|ToolTip denetim türüne karşılık gelen yerelleştirilmiş dize.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|-sına bağ -lıdır|Araç ipucu denetimi klavye odağı alabiliyorsa, ağacın İçerik Görünümü'nde olmalıdır. Yalnızca metin ise, onu yükselten denetimden HelpTextProperty olarak kullanılabilir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Takım ucu kontrolü her zaman bir kontrol olmalıdır.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>
## <a name="required-ui-automation-control-patterns"></a>Gerekli UI Otomasyon Kontrol Desenleri  
 Aşağıdaki tabloda, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] araç uç denetimleri tarafından desteklenmesi gereken denetim desenleri listelenir. Denetim desenleri hakkında daha fazla bilgi için [UI Otomasyon Kontrol Modellerine Genel Bakış'a](ui-automation-control-patterns-overview.md)bakın.  
  
|Kontrol Deseni|Destek|Notlar|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IWindowProvider>|-sına bağ -lıdır|Bir Ara Bilgi Öğesi'ni tıklatarak kapatılabilen araç ipuçları, otomatik olarak kapatılabilmeleri için WindowPattern'i desteklemelidir.|  
|<xref:System.Windows.Automation.Provider.ITextProvider>|-sına bağ -lıdır|Daha iyi erişilebilirlik için, bir araç ipucu denetimi gerekli olmasa da Metin denetim deseni destekleyebilir. Metin denetimi deseni, metin zengin stil ve özniteliklere (örneğin, renk, kalın ve italik) sahipolduğunda yararlıdır.|  
  
<a name="Required_UI_Automation_Events"></a>
## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyon Etkinlikleri  
 Araç ipucu denetimleri `ToolTipOpenedEvent` ekranda göründükleri zaman yükseltmek gerekir. Olay, araç ucunun [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] kendisi öğesine bir başvuru içerecektir.  
  
 Aşağıdaki tabloda, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tüm araç ipucu denetimleri tarafından desteklenmesi gereken olaylar listelenmektedir. Etkinlikler hakkında daha fazla bilgi için [UI Otomasyon Etkinliklerine Genel Bakış'a](ui-automation-events-overview.md)bakın.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Olay|Destek|Notlar|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.TextPatternIdentifiers.TextSelectionChangedEvent>|-sına bağ -lıdır|None|  
|<xref:System.Windows.Automation.TextPatternIdentifiers.TextChangedEvent>|-sına bağ -lıdır|None|  
|<xref:System.Windows.Automation.WindowPatternIdentifiers.WindowClosedEvent>|-sına bağ -lıdır|None|  
|<xref:System.Windows.Automation.WindowPatternIdentifiers.WindowOpenedEvent>|-sına bağ -lıdır|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ToolTipOpenedEvent>|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ToolTipClosedEvent>|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>özellik değiştirilen olay.|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>özellik değiştirilen olay.|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>özellik değiştirilen olay.|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>özellik değiştirilen olay.|Gerekli|None|  
|<xref:System.Windows.Automation.WindowPatternIdentifiers.WindowVisualStateProperty>özellik değiştirilen olay.|-sına bağ -lıdır|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|None|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.ControlType.ToolTip>
- [UI Otomasyonu Denetim Türlerine Genel Bakış](ui-automation-control-types-overview.md)
- [UI Otomasyonuna Genel Bakış](ui-automation-overview.md)
