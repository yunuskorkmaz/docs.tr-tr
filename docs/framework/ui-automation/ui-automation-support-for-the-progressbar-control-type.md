---
title: ProgressBar Denetim Türü için UI Otomasyon Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Progress Bar
- ProgressBar control type
- UI Automation, Progress Bar control type
ms.assetid: 302e778c-24b0-4789-814a-c8d37cf53a5f
ms.openlocfilehash: 5c21bbae1db1c2bbb6c4bbf04cb2aa386907dcc2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179637"
---
# <a name="ui-automation-support-for-the-progressbar-control-type"></a>ProgressBar Denetim Türü için UI Otomasyon Desteği
> [!NOTE]
> Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır. Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ProgressBar denetim türü için destek hakkında bilgi sağlar. Denetim [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]türü, <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> özelliği kullanmak için denetimin karşılaması gereken koşullar kümesidir. Koşullar, ağaç yapısı, özellik [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] değerleri, denetim desenleri ve [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olaylar için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özel yönergeler içerir.  
  
 İlerleme çubuğu denetimleri, ProgressBar denetim türünü uygulayan denetimlerin bir örneğidir. İlerleme çubuğu denetimleri, uzun bir işlemin ilerlemesini belirtmek için kullanılır. Denetim, işlem ilerledikçe yavaş yavaş sistem vurgu sulamı rengiyle doldurulan bir dikdörtgenden oluşur.  
  
 Aşağıdaki bölümler, ProgressBar denetim türü için gerekli [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısını, özelliklerini, denetim desenlerini ve olaylarını tanımlar. Gereksinimler, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Win32 veya [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]Windows Forms olsun, tüm liste denetimleri için geçerlidir.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyon Ağaç Yapısı  
 Aşağıdaki tablo, ilerleme çubuğu denetimleri ile [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ilgili denetim görünümü ve ağacın içerik görünümünü görüntüler ve her görünümde nelerin bulunabileceğini açıklar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ağaç hakkında daha fazla bilgi için [UI Automation Tree Genel Bakış'a](ui-automation-tree-overview.md)bakın.  
  
|Kontrol Görünümü|İçerik Görünümü|  
|------------------|------------------|  
|ProgressBar|ProgressBar|  
  
 İlerleme çubuğu denetimlerinde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacın denetiminde veya içerik görünümünde herhangi bir çocuk yoktur.  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon Özellikleri  
 Aşağıdaki tabloda, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] değeri veya tanımı özellikle ilerleme çubuğu denetimleri ile ilgili özellikleri listelenir. Özellikler hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] daha fazla bilgi [için, Müşteriler için Kullanıcı Arabirimi Otomasyon Özellikleri'ne](ui-automation-properties-for-clients.md)bakın.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Özellik|Değer|Notlar|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlara bakın.|Bu özelliğin değeri, bir uygulamadaki tüm denetimler arasında benzersiz olmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlara bakın.|Tüm denetimi içeren en dıştaki dikdörtgen.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Notlara bakın.|Sınırlayıcı bir dikdörtgen varsa desteklenir. Sınırlayıcı dikdörtgen içindeki her nokta tıklatılabilir değilse ve özel isabet testi gerçekleştirin, sonra geçersiz kılınve tıklanabilir bir nokta sağlayın.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Notlara bakın.|Denetim klavye odağı alabiliyorsa, bu özelliği desteklemesi gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlara bakın.|İlerleme çubuğu denetimi genellikle adını statik bir metin etiketinden alır. Statik bir metin etiketi yoksa, uygulama geliştiricisinin `Name` özellik için bir değer ortaya çıkarması gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Notlara bakın.|Statik bir metin etiketi varsa, bu özellik bu denetime bir başvuru göstermelidir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|ProgressBar|Bu değer tüm Ara bilgi arabirimi çerçeveleri için aynıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"ilerleme çubuğu"|ProgressBar denetim türüne karşılık gelen yerelleştirilmiş dize.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|İlerleme çubuğu denetimi her zaman [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacın içerik görünümüne dahildir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|İlerleme çubuğu denetimi her zaman [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacın denetim görünümüne dahildir.|  
  
<a name="Required_UI_Automation_Control_Patterns_and_Properties"></a>
## <a name="required-ui-automation-control-patterns-and-properties"></a>Gerekli UI Otomasyon Kontrol Desenleri ve Özellikleri  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ilerleme çubuğu denetimleri tarafından desteklenmesi gereken denetim desenleri listelenir. Denetim desenleri hakkında daha fazla bilgi için [UI Otomasyon Kontrol Modellerine Genel Bakış'a](ui-automation-control-patterns-overview.md)bakın.  
  
|Kontrol Deseni/Desen Özelliği|Destek / Değer|Notlar|  
|---------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|-sına bağ -lıdır|İlerlemenin metinsel bir göstergesini veren ilerleme <xref:System.Windows.Automation.Provider.IValueProvider>çubuğu denetimleri uygulanmalıdır.|  
|<xref:System.Windows.Automation.Provider.IValueProvider.IsReadOnly%2A>|True|Bu özelliğin değeri her zaman Doğrudur.|  
|<xref:System.Windows.Automation.Provider.IValueProvider.Value%2A>|Notlara bakın.|Bu özellik, ilerleme çubuğu denetiminin metinsel ilerlemesini ortaya çıkarır.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|-sına bağ -lıdır|Sayısal aralık alan ilerleme çubuğu denetimleri uygulamalı<xref:System.Windows.Automation.Provider.IRangeValueProvider>|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.Minimum%2A>|0,0|Bu özelliğin değeri, denetimin ayarlanabileceği en küçük değerdir.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.Maximum%2A>|100.0|Bu özelliğin değeri, denetimin ayarlanabileceği en büyük değerdir.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.SmallChange%2A>|NaN|İlerleme çubuğu denetimleri salt okunur olduğundan bu özellik gerekli değildir.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.LargeChange%2A>|NaN|İlerleme çubuğu denetimleri salt okunur olduğundan bu özellik gerekli değildir.|  
  
<a name="Required_UI_Automation_Events"></a>
## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyon Etkinlikleri  
 Aşağıdaki tabloda, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tüm ilerleme çubuğu denetimleri tarafından desteklenmesi gereken olaylar listelenmektedir. Etkinlikler hakkında daha fazla bilgi için [UI Otomasyon Etkinliklerine Genel Bakış'a](ui-automation-events-overview.md)bakın.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Olay|Destek|Notlar|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>özellik değiştirilen olay.|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>özellik değiştirilen olay.|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>özellik değiştirilen olay.|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>özellik değiştirilen olay.|Gerekli|None|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty>özellik değiştirilen olay.|-sına bağ -lıdır|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|None|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.ControlType.ProgressBar>
- [UI Otomasyonu Denetim Türlerine Genel Bakış](ui-automation-control-types-overview.md)
- [UI Otomasyonuna Genel Bakış](ui-automation-overview.md)
