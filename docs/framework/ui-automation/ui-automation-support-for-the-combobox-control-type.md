---
title: ComboBox Denetim Türü için UI Otomasyon Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Combo Box
- UI Automation, Combo Box control type
- ComboBox controls
ms.assetid: bb321126-4770-41da-983a-67b7b89d45dd
ms.openlocfilehash: 7e458d95f81893d61bcf19f7fe611e3424f27e37
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59126743"
---
# <a name="ui-automation-support-for-the-combobox-control-type"></a>ComboBox Denetim Türü için UI Otomasyon Desteği
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu hakkında bilgi sağlar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ComboBox denetim türü için destek. İçinde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], Denetim türü bir denetim kullanmak için karşılaması gereken koşulları kümesidir <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> özelliği. Özel yönergeleri koşulları dahil [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısını [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerleri, Denetim düzenleri ve [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayları.  
  
 Bir birleşik giriş kutusu statik bir denetimi veya birleşik giriş kutusu liste kutusunun bölümünde seçili olan öğe görüntüleyen bir düzenleme denetimi ile birlikte bir liste kutusudur. Denetim listesi kutusu kısmı kullanıcı (bir düğme olan) açılan liste okunu seçtiğinde denetim bitişiğinde yalnızca görünen veya her zaman görüntülenir. Bir düzenleme denetimi seçim alanı ise kullanıcı listesinde olmayan bilgiler girebilir; Aksi takdirde, kullanıcı listesinde yalnızca öğeleri seçebilirsiniz.  
  
 Aşağıdaki bölümlerde gerekli tanımlamak [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısı, özellikler, Denetim düzenleri ve olayları ComboBox denetim türü için. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Gereksinimler tüm birleşik giriş kutusu denetimleri için geçerli olup olmadığını [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], veya [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyon ağaç yapısı  
 Aşağıdaki tablo denetimi ve içerik görünümünde gösterir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] birleşik giriş kutusu ilgilidir ağaç denetler ve her bir görünümde bulunabilir açıklar. Hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç bkz [UI Otomasyon ağacına genel bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Denetim Görünüm|İçerik görünümü|  
|------------------|------------------|  
|ComboBox<br /><br /> -(0 veya 1) Düzenle<br />-LIST (1)<br />-Liste öğesi (alt listesinin; çoğu 0)<br />-Düğmesine (1)|ComboBox<br /><br /> -Liste öğesi (0-çok)|  
  
 Birleşik giriş kutusu denetim görünümünde düzenleme denetimi Çalıştır iletişim kutusunu birleşik giriş kutusunun olduğu gibi yalnızca Birleşik giriş kutusu herhangi bir giriş yapılacak düzenlenebilir gerek yoktur.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon özellikleri  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , değer veya tanımı birleşik giriş kutusuna yakından ilgili özellikler kutusu denetimleri. Hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri görmek [istemciler için UI Otomasyon özellikleri](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Özelliği|Değer|Notlar|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlara bakın.|Bu özelliğin değerini bir uygulamadaki tüm denetimler arasında benzersiz olması gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlara bakın.|Tam denetimi içeren en dıştaki dikdörtgen.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Notlara bakın.|Sınırlayıcı bir dikdörtgen ise desteklenir. Değilse dikdörtgen içinde her bir nokta tıklanabilir ve özelleştirilmiş isabet sınaması, gerçekleştirmek sonra geçersiz kılmak ve tıklanabilir bir nokta sağlayamaz.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|ComboBox|Bu değer için aynı olan [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] çerçeveleri.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|Notlara bakın.|Birleşik giriş kutusu denetimleri için Yardım metni, birleşik giriş kutusundan bir seçenek belirlemek için kullanıcı neden sorulmaktadır açıklayan. Metin bir araç ipucu sunulan bilgilere benzer. Örneğin, "ekranınız, ekran çözünürlüğünü ayarlamak için bir öğe seçin."|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Doğru|Birleşik giriş kutusu denetimleri her zaman içerik görünümünde bulunan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Doğru|Birleşik giriş kutusu denetimleri denetim görünümünde bulunan her zaman [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Doğru|Birleşik giriş kutusu denetimleri seçimi kapsayıcısından öğelerin kümesi kullanıma sunar. UI Otomasyonu istemci bir birleşik giriş kutusu odağı ayarladığında, birleşik giriş kutusu ağaçtaki tüm öğeler odağı alabilirsiniz ancak Kombo kutusu denetiminin klavye odağı alabilir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Notlara bakın.|Birleşik giriş kutusu denetimleri genellikle, bu özellik başvuran bir statik metin etiketi de sahiptir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"Birleşik giriş kutusunun"|ComboBox denetim türü için karşılık gelen yerelleştirilmiş bir dize.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlara bakın.|Birleşik giriş kutusu denetimi, genellikle bir statik metin denetimi adını alır.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Gerekli UI Otomasyon denetim düzenleri  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] denetim tüm birleşik giriş kutusu denetimleri tarafından desteklenmesi için gereken desenleri. Denetim desenleri hakkında daha fazla bilgi için bkz. [UI Otomasyon denetim düzenlerine genel bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Denetim düzeni|Destek|Notlar|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Evet|Birleşik giriş kutusu denetimi her zaman bir birleşik giriş kutusu olması için açılan düğmeyi içermesi gerekir.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Evet|Geçerli seçimi birleşik giriş kutusunda görüntüler. Bu destek, birleşik giriş kutusunun altındaki liste kutusu için temsilci.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Bağlıdır|Birleşik giriş kutusu rastgele metin değerlerini alma özelliği varsa, değer desenin desteklenmesi gerekir. Bu düzen, birleşik giriş kutusunun dize içeriklerini programlı olarak ayarlama olanağı sağlar. Değer düzeni desteklenmiyor, kullanıcı bir açılan kutunun alt ağacı içinde liste öğelerini seçimden yapmaması gerektiğini gösterir.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|hiçbir zaman|Kaydırma düzeni hiçbir zaman doğrudan bir açılan kutunun üzerinde desteklenir. Bir açılan kutunun içinde yer alan bir liste kutusunda kaydırma durumunda desteklenir. Yalnızca liste kutusunun ekranda görünür olduğunda desteklenebilir.|  
  
<a name="Required_Events"></a>   
## <a name="required-events"></a>Gerekli olayları  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayları tüm birleşik giriş kutusu denetimleri tarafından desteklenmesi gerekir. Olaylar hakkında daha fazla bilgi için bkz. [UI Otomasyonu olaylarına genel bakış](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Olay|Destek|Notlar|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> özellik değişti olayı.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> özellik değişti olayı.|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> özellik değişti olayı.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|Yok.|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty> özellik değişti olayı.|Gerekli|None|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> özellik değişti olayı.|Bağlıdır|Denetimin değer deseni destekliyorsa, bu olay desteklemesi gerekir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.ControlType.ComboBox>
- [UI Otomasyonu Denetim Türlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)
- [UI Otomasyonuna Genel Bakış](../../../docs/framework/ui-automation/ui-automation-overview.md)
