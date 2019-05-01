---
title: RadioButton Denetim Türü için UI Otomasyon Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Radio Button
- UI Automation, Radio Button control type
- RadioButton control type
ms.assetid: 87170464-7857-41f1-bcf7-bb41be31cb53
ms.openlocfilehash: b437e19b10b534ce1c1dfae8ef0cca083cac2d61
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61996716"
---
# <a name="ui-automation-support-for-the-radiobutton-control-type"></a>RadioButton Denetim Türü için UI Otomasyon Desteği
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu hakkında bilgi sağlar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] destekler RadioButton denetim türü için. İçinde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], Denetim türü bir denetim kullanmak için karşılaması gereken koşulları kümesidir <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> özelliği. Özel yönergeleri koşulları dahil [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısını [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerlerini ve denetim düzenleri.  
  
 Bir radyo düğmesi, bir yuvarlak düğmesini ve uygulama tanımlı metin (bir etiketi), bir simge oluşur veya bir seçim kullanıcı gösteren bir bit eşlem düğmesini seçerek yapabilirsiniz. Bir uygulama grubu kutusundaki radyo düğmelerini bir dizi ilgili ancak birbirini dışlayan seçenekleri seçmesine izin vermek için genellikle kullanır. Örneğin, uygulama kullanıcının istemci alanında seçilen metin biçimi mutfağından seçebileceği radyo düğmelerinden oluşan bir grubu sunabilir. Kullanıcı, karşılık gelen radyo düğmesini seçerek bir sola hizalanmış, sağa hizalı veya ortalanmış biçiminde seçebilirsiniz. Genellikle, kullanıcı aynı anda yalnızca bir seçenek radyo düğmeleri kümesinden seçebilirsiniz.  
  
 Aşağıdaki bölümlerde gerekli tanımlamak [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısı, özellikler, Denetim düzenleri ve olayları RadioButton denetim türü için. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Gereksinimler tüm liste denetimleri için geçerli olup olmadığını [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], veya [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyon ağaç yapısı  
 Aşağıdaki tablo denetimi ve içerik görünümünde gösterir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] radyo düğmesini ilgilidir ağaç denetler ve her bir görünümde bulunabilir açıklar. Daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç bkz [UI Otomasyon ağacına genel bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Denetim Görünüm|İçerik görünümü|  
|------------------|------------------|  
|RadioButton|RadioButton|  
  
 Alt öğe kontrol görünümündeki veya içerik görünümü vardır.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon özellikleri  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri olan bir değer veya tanımı için RadioButton yakından ilgili denetim türü. Daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri görmek [istemciler için UI Otomasyon özellikleri](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Özelliği|Değer|Notlar|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlara bakın.|Bu özelliğin değerini bir uygulamadaki tüm denetimler arasında benzersiz olması gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlara bakın.|Tam denetimi içeren en dıştaki dikdörtgen.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Notlara bakın.|Denetimin klavye odağı alamıyorsa, bu özelliği desteklemesi gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlara bakın.|Seçim durumu tutan bir düğme görüntülenen metin radyo düğmesi denetimin adıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Notlara bakın.|Radyo düğmesini denetimin tıklanabilir noktası gereken bir fare işaretçisini tıkladıysanız radyo düğmesi seçimi bir noktası olması.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Radyo düğmeleri, denetimleri Self etiketleme.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|RadioButton|Bu değer için aynı olan [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] çerçeveleri.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"radyo düğmesini"|RadioButton denetim türü için karşılık gelen yerelleştirilmiş bir dize.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Doğru|Radyo düğmesi denetimini her zaman içerik görünümünde bulunan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Doğru|Radyo düğmesi denetimini her zaman denetim görünümünde bulunan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Gerekli UI Otomasyon denetim düzenleri  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] denetim radyo düğmesi denetimleri tarafından desteklenmesi için gereken desenleri. Denetim desenleri hakkında daha fazla bilgi için bkz. [UI Otomasyon denetim düzenlerine genel bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Denetim düzeni/denetim düzeni özelliği|Destek/değer|Notlar|  
|-----------------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Evet|Seçim öğesi düzeni kendilerini seçilmiş olması etkinleştirmek için tüm radyo düğmesi denetimini desteklemelidir.|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider.SelectionContainer%2A>|Notlara bakın.|`SelectionContainerProperty` Her zaman bir UI Otomasyonu istemci ne belirli bir bağlam içinde diğer radyo düğmeleri birbirleriyle belirleyebilirsiniz tamamlanmalıdır.  İçin [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] bu eski Framework'ten bu bilgileri almak mümkün olmadığından bu özellik radyo düğmesini sürümü desteklenmeyecek.|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|hiçbir zaman|Ayarlandıktan sonra radyo düğmesini durumuna geçiş yapılamıyor.  Bu düzen, hiçbir zaman radyo düğmesini desteklenmelidir.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyonu olayları  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tüm radyo düğmesi denetimleri tarafından desteklenmesi için gerekli olayları. Olaylar hakkında daha fazla bilgi için bkz. [UI Otomasyonu olaylarına genel bakış](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Olay|Destek|Notlar|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|Gerekli|None|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Gerekli|None|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty> özellik değişti olayı.|hiçbir zaman|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> özellik değişti olayı.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> özellik değişti olayı.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> özellik değişti olayı.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|Yok.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.ControlType.RadioButton>
- [UI Otomasyonu Denetim Türlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)
- [UI Otomasyonuna Genel Bakış](../../../docs/framework/ui-automation/ui-automation-overview.md)
