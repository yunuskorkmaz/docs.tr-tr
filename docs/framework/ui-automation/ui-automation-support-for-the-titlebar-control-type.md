---
title: TitleBar Denetim Türü için UI Otomasyon Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Title Bar
- Title Bar control type
- UI Automation, Title Bar control type
ms.assetid: 3b7a4e13-0305-45d5-bc33-1f4133c50782
ms.openlocfilehash: 19c203151956ae17dbcf608c135e7fe97a2b4389
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179472"
---
# <a name="ui-automation-support-for-the-titlebar-control-type"></a>TitleBar Denetim Türü için UI Otomasyon Desteği
> [!NOTE]
> Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır. Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] TitleBar denetim türü için destek hakkında bilgi sağlar. Denetim [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]türü, <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> özelliği kullanmak için denetimin karşılaması gereken koşullar kümesidir. Koşullar, ağaç yapısı, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerleri ve denetim desenleri için özel yönergeler içerir.  
  
 Başlık çubuğu denetimleri, penceredeki başlıkları veya resim yazısı çubuklarını temsil eder.  
  
 Aşağıdaki bölümlerde, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] TitleBar denetim türü için gerekli ağaç yapısı, özellikleri, denetim desenleri ve olayları tanımlanır. Gereksinimler, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Win32 veya [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]Windows Forms olsun, tüm başlık çubuğu denetimleri için geçerlidir.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyon Ağaç Yapısı  
 Aşağıdaki tablo, başlık çubuğu denetimleri ile [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ilgili ağacın denetim görünümünü ve içerik görünümünü görüntüler ve her görünümde nelerin bulunabileceğini açıklar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ağaç hakkında daha fazla bilgi için [UI Automation Tree Genel Bakış'a](ui-automation-tree-overview.md)bakın.  
  
|Kontrol Görünümü|İçerik Görünümü|  
|------------------|------------------|  
|Titlebar<br /><br /> - Menü (0 veya 1)<br />- Düğme (0 veya daha fazla)|Geçerli değildir. (başlık çubuğu denetiminde içerik yoktur.)|  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon Özellikleri  
 Aşağıdaki tabloda, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] değeri veya tanımı özellikle TitleBar denetimleri ile ilgili özellikleri listelenir. Özellikler hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] daha fazla bilgi [için, Istemciler için Kullanıcı Arabirimi Otomasyon Özellikleri'ne](ui-automation-properties-for-clients.md)bakın.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Özellik|Değer|Notlar|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlara bakın.|Bu özelliğin değeri, bir uygulamadaki tüm denetimler arasında benzersiz olmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlara bakın.|Bir başlık çubuğunun sınırlayıcı dikdörtgeni, içinde bulunan tüm denetimleri kapsamalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Notlara bakın.|Sınırlayıcı bir dikdörtgen varsa desteklenir. Sınırlayıcı dikdörtgen içindeki her nokta tıklatılabilir değilse ve özel isabet testi gerçekleştirin, sonra geçersiz kılınve tıklanabilir bir nokta sağlayın.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|False|Başlık çubuklarının klavye odağı asla yoktur.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|""|Başlık çubuğu içerikli değildir; metin bilgileri üst pencerede açıklanır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Notlara bakın.|Başlık çubuğu denetimigenellikle bir etiket ekideğildir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Titlebar|Bu değer tüm Ara bilgi arabirimi çerçeveleri için aynıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"başlık çubuğu"|TitleBar denetim türüne karşılık gelen yerelleştirilmiş dize.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|False|Başlık çubuğu denetimi hiçbir zaman içerik değildir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Başlık çubuğu denetimi her zaman bir denetim olmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>|-sına bağ -lıdır|Bu denetim, başlık çubuğunun ekranda görünür olup olmadığına bağlı olarak bir değer döndürecektir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|""|Yardım metnini ortaya çıkarmak gerekli değildir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AcceleratorKeyProperty>|""|Başlık çubuklarının hızlandırıcı anahtarları asla yoktur.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AccessKeyProperty>|""|Başlık çubuğu denetiminde erişim anahtarı yoktur.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>
## <a name="required-ui-automation-control-patterns"></a>Gerekli UI Otomasyon Kontrol Desenleri  
 Başlık Çubuğu denetim türü herhangi bir denetim desenleri desteklemek için gerekli değildir. İşlevselliği, Pencere denetimindeki Pencere denetim deseni aracılığıyla ortaya çıkarır.  
  
## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyon Etkinlikleri  
 Aşağıdaki tabloda, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tüm başlık çubuğu denetimleri tarafından desteklenmesi gereken olaylar listelenmektedir. Etkinlikler hakkında daha fazla bilgi için [UI Otomasyon Etkinliklerine Genel Bakış'a](ui-automation-events-overview.md)bakın.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Olay|Destek|Notlar|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>özellik değiştirilen olay.|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>özellik değiştirilen olay.|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>özellik değiştirilen olay.|Hiçbir zaman|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Hiçbir zaman|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|None|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.ControlType.TitleBar>
- [UI Otomasyonu Denetim Türlerine Genel Bakış](ui-automation-control-types-overview.md)
- [UI Otomasyonuna Genel Bakış](ui-automation-overview.md)
