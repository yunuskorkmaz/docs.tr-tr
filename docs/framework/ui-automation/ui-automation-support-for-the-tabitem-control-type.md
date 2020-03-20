---
title: TabItem Denetim Türü için UI Otomasyon Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- Tab Item control type
- control types, Tab Item
- UI Automation, Tab Item control type
ms.assetid: 9b21160d-e1c2-468b-9275-26e4369ae40d
ms.openlocfilehash: 285df51123a144673d513841852b53a96e6b8a7f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179536"
---
# <a name="ui-automation-support-for-the-tabitem-control-type"></a>TabItem Denetim Türü için UI Otomasyon Desteği
> [!NOTE]
> Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır. Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] TabItem denetim türü için destek hakkında bilgi sağlar. Denetim [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]türü, <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> özelliği kullanmak için denetimin karşılaması gereken koşullar kümesidir. Koşullar, ağaç yapısı, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerleri ve denetim desenleri için özel yönergeler içerir.  
  
 Sekme öğesi denetimi, bir pencerede gösterilecek belirli bir sayfayı seçen sekme denetiminde denetim olarak kullanılır.  
  
 Aşağıdaki bölümler, TabItem denetim türü için gerekli [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısını, özelliklerini, denetim desenlerini ve olaylarını tanımlar. Gereksinimler, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Win32 veya [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]Windows Forms olsun, tüm sekme öğesi denetimleri için geçerlidir.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyon Ağaç Yapısı  
 Aşağıdaki tablo, sekme öğesi denetimleri ile [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ilgili denetim görünümünü ve ağacın içerik görünümünü görüntüler ve her görünümde nelerin bulunabileceğini açıklar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ağaç hakkında daha fazla bilgi için [UI Automation Tree Genel Bakış'a](ui-automation-tree-overview.md)bakın.  
  
|Kontrol Görünümü|İçerik Görünümü|  
|------------------|------------------|  
|Tabıtem<br /><br /> <ul><li>Resim (0 veya 1)</li><li>Metin</li><li>Bölme<br /><br /> <ul><li>Çeşitli denetimler (0 veya daha fazla)</li></ul></li></ul>|Tabıtem<br /><br /> <ul><li>Bölme<br /><br /> <ul><li>Çeşitli denetimler (0 veya daha fazla)</li></ul></li></ul>|  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon Özellikleri  
 Aşağıdaki tablo, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] değeri veya tanımı özellikle sekme öğesi denetimleri ile ilgili özellikleri listeler. Özellikler hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] daha fazla bilgi [için, Müşteriler için Kullanıcı Arabirimi Otomasyon Özellikleri'ne](ui-automation-properties-for-clients.md)bakın.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Özellik|Değer|Notlar|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlara bakın.|Bu özelliğin değeri, bir uygulamadaki tüm denetimler arasında benzersiz olmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlara bakın.|Tüm denetimi içeren en dıştaki dikdörtgen.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Notlara bakın.|Sekme öğesi denetimi, öğenin seçilmesine neden olan tıklatılabilir bir noktaya sahip olmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Notlara bakın.|Denetim klavye odağı alabiliyorsa, bu özelliği desteklemesi gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlara bakın.|Sekme öğesi denetimi kendi kendine etiketlenir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Sekme öğesi denetiminde statik metin etiketi yoktur.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Tabıtem|Bu değer tüm Ara bilgi arabirimi çerçeveleri için aynıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"sekme öğesi"|Bu denetim türüne karşılık gelen yerelleştirilmiş dize.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|Sekme öğesi denetimi her zaman içerik olmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Sekme öğesi denetimi her zaman bir denetim olmalıdır.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>
## <a name="required-ui-automation-control-patterns"></a>Gerekli UI Otomasyon Kontrol Desenleri  
 Aşağıdaki tablo, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sekme öğesi denetimleri tarafından desteklenmesi gereken denetim desenlerini listeler. Denetim desenleri hakkında daha fazla bilgi için [UI Otomasyon Kontrol Modellerine Genel Bakış'a](ui-automation-control-patterns-overview.md)bakın.  
  
|Kontrol Deseni|Destek|Notlar|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Evet|Sekme öğesi denetimi SelectionItemPattern'i desteklemelidir.|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Hayır|Sekme öğesi denetimi InvokePattern'i asla desteklemez.|  
  
<a name="Required_UI_Automation_Events"></a>
## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyon Etkinlikleri  
 Aşağıdaki tablo, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tüm sekme öğesi denetimleri tarafından desteklenmesi gereken olayları listeler. Etkinlikler hakkında daha fazla bilgi için [UI Otomasyon Etkinliklerine Genel Bakış'a](ui-automation-events-overview.md)bakın.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Olay|Destek|Notlar|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>özellik değiştirilen olay.|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>özellik değiştirilen olay.|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>özellik değiştirilen olay.|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|None|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Gerekli|None|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|None|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.ControlType.TabItem>
- [UI Otomasyonu Denetim Türlerine Genel Bakış](ui-automation-control-types-overview.md)
- [UI Otomasyonuna Genel Bakış](ui-automation-overview.md)
