---
title: Bölme Denetim Türü İçin UI Otomasyon Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Pane control type
- Pane control type
- control types, Pane
ms.assetid: 79761191-4449-4630-899c-9cbdb8867d3f
ms.openlocfilehash: ab888c2ecfd516ae4e7ce5dab0dca3fde1a7b98e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179656"
---
# <a name="ui-automation-support-for-the-pane-control-type"></a>Bölme Denetim Türü İçin UI Otomasyon Desteği
> [!NOTE]
> Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır. Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Pane denetim türü için destek hakkında bilgi sağlar. Denetim [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]türü, <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> özelliği kullanmak için denetimin karşılaması gereken koşullar kümesidir. Koşullar, ağaç yapısı, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerleri ve denetim desenleri için özel yönergeler içerir.  
  
 Bölme denetim türü, çerçeve veya belge penceresi içindeki bir nesneyi temsil etmek için kullanılır. Kullanıcılar bölme denetimleri arasında ve geçerli bölmenin içeriği içinde gezinebilir, ancak farklı bölmelerde öğeler arasında gezinemez. Bu nedenle, bölme denetimleri, pencerelerden veya belgelerden daha düşük, ancak tek tek denetimlerin üzerinde bir gruplandırma düzeyini temsil eder. Kullanıcı, içeriğe bağlı olarak TAB, F6 veya CTRL+TAB tuşuna basarak bölmeler arasında gezinir. Bölme denetim türü tarafından belirli bir klavye gezintisi gerekmez.  
  
 Aşağıdaki bölümler, Bölmesi denetim türü için gerekli [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısını, özelliklerini, denetim modellerini ve olaylarını tanımlar. Gereksinimler, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Win32 veya [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]Windows Forms olsun, tüm liste denetimleri için geçerlidir.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyon Ağaç Yapısı  
 Aşağıdaki tablo, bölme denetimleri ile ilgili [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacın denetim görünümünü ve içerik görünümünü görüntüler ve her görünümde nelerin bulunabileceğini açıklar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ağaç hakkında daha fazla bilgi için [UI Automation Tree Genel Bakış'a](ui-automation-tree-overview.md)bakın.  
  
|Kontrol Görünümü|İçerik Görünümü|  
|------------------|------------------|  
|Bölme|Bölme|  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon Özellikleri  
 Aşağıdaki tablo, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] değeri veya tanımı özellikle bölme denetimleri ile ilgili özellikleri listeler. Özellikler hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] daha fazla bilgi [için, Müşteriler için Kullanıcı Arabirimi Otomasyon Özellikleri'ne](ui-automation-properties-for-clients.md)bakın.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Özellik|Değer|Notlar|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlara bakın.|Bu özelliğin değeri, bir uygulamadaki tüm denetimler arasında benzersiz olmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlara bakın.|Tüm denetimi içeren en dıştaki dikdörtgen.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Notlara bakın.|Denetim klavye odağı alabiliyorsa, bu özelliği desteklemesi gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlara bakın.|Bu özelliğin değeri her zaman açık, kısa ve anlamlı bir başlık olmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Notlara bakın.|Bu özellik, bölme denetiminin tıklatılabilir bir noktasını ortaya çıkarır ve bu nokta tıklatıldığında odaklandı.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Notlara bakın.|Bölme denetimleri genellikle statik bir etikete sahip değildir. Statik bir metin etiketi varsa, bu özellik aracılığıyla açıklanmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Bölme|Bu değer tüm [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] çerçeveler için aynıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"bölme"|Bölme denetim türüne karşılık gelen yerelleştirilmiş dize.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|Bölme denetimleri her zaman [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacın içerik görünümüne dahildir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Bölme denetimleri her zaman [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacın denetim görünümüne dahildir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|""|Bölme denetimleri için yardım metni, çerçevenin amacının neden ve diğer çerçevelerle nasıl ilişkili olduğunu açıklamalıdır. Çerçevelerin amacı ve ilişkisi' nin değerinden net olmaması durumunda `NameProperty`bir açıklama gereklidir. "|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AccessKeyProperty>|Notlara bakın.|Belirli bir anahtar birleşimi bölmeye odaklanma sağlıyorsa, bu bilgiler bu özellik aracılığıyla açıklanmalıdır.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>
## <a name="required-ui-automation-control-patterns"></a>Gerekli UI Otomasyon Kontrol Desenleri  
 Aşağıdaki tablo, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tüm bölme denetimleri tarafından desteklenmesi gereken denetim desenleri listeler. Denetim desenleri hakkında daha fazla bilgi için [UI Otomasyon Kontrol Modellerine Genel Bakış'a](ui-automation-control-patterns-overview.md)bakın.  
  
|Kontrol Deseni|Destek|Notlar|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITransformProvider>|-sına bağ -lıdır|Bölme denetimi ekranda taşınabiliyor, yeniden boyutlandırılabiliyor veya döndürülebiliyorsa bu denetim deseni uygulayın.|  
|<xref:System.Windows.Automation.Provider.IWindowProvider>|Hiçbir zaman|Bu denetim deseni uygulamanız gerekiyorsa, denetiminiz <xref:System.Windows.Automation.ControlType.Window> denetim türüne göre olmalıdır.|  
|<xref:System.Windows.Automation.Provider.IDockProvider>|-sına bağ -lıdır|Bölme denetimi kenetlenebiliyorsa bu denetim deseni uygulayın.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|-sına bağ -lıdır|Bölme denetimi kaydırılabilirse bu denetim deseni uygulayın.|  
  
<a name="Required_UI_Automation_Events"></a>
## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyon Etkinlikleri  
 Aşağıdaki tablo, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tüm bölme denetimleri tarafından desteklenmesi gereken olayları listeler. Etkinlikler hakkında daha fazla bilgi için [UI Otomasyon Etkinliklerine Genel Bakış'a](ui-automation-events-overview.md)bakın.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Olay|Destek / Değer|Notlar|  
|---------------------------------------------------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.WindowPatternIdentifiers.WindowClosedEvent>|Hiçbir zaman|None|  
|<xref:System.Windows.Automation.WindowPatternIdentifiers.WindowOpenedEvent>|Hiçbir zaman|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AsyncContentLoadedEvent>|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>özellik değiştirilen olay.|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>özellik değiştirilen olay.|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>özellik değiştirilen olay.|Gerekli|None|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>özellik değiştirilen olay.|-sına bağ -lıdır|None|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty>özellik değiştirilen olay.|-sına bağ -lıdır|None|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty>özellik değiştirilen olay.|-sına bağ -lıdır|None|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty>özellik değiştirilen olay.|-sına bağ -lıdır|None|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>özellik değiştirilen olay.|-sına bağ -lıdır|None|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty>özellik değiştirilen olay.|-sına bağ -lıdır|None|  
|<xref:System.Windows.Automation.WindowPatternIdentifiers.WindowVisualStateProperty>özellik değiştirilen olay.|Hiçbir zaman|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|None|  
  
<a name="Pane_Control_Type_Example"></a>
## <a name="pane-control-type-example"></a>Bölme Kontrol Türü Örneği  
 Aşağıdaki resimde Bölmesi denetim türünü uygulayan bir denetim gösterin.  
  
 ![İki bölmeli applet penceresinin ekran görüntüsü](./media/uiauto-pane.GIF "uiauto_pane")  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Ağaç - Kontrol Görünümü|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Ağaç - İçerik Görünümü|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|<ul><li>Bölme</li><li>Ağaç (Kaydırma Deseni)<br /><br /> <ul><li>Treeıtem</li><li>Bölme</li><li>Düzenle (Kaydırma Deseni</li></ul></li></ul>|- Bölme<br />- Ağaç (Kaydırma Deseni)<br />- Ağaç Öğesi<br />- ... Bölme<br />- Edit<br />- (Kaydırma Deseni)|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.ControlType.Pane>
- [UI Otomasyonu Denetim Türlerine Genel Bakış](ui-automation-control-types-overview.md)
- [UI Otomasyonuna Genel Bakış](ui-automation-overview.md)
