---
title: Kaydırıcı Denetim Türü İçin UI Otomasyon Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Slider
- UI Automation, Slider control type
- Slider control type
ms.assetid: 045ea62f-7b50-46cf-a5a9-8eb97704355f
ms.openlocfilehash: b6d44b3f855410a524875ac2a43e21cb51d68e11
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61996638"
---
# <a name="ui-automation-support-for-the-slider-control-type"></a>Kaydırıcı Denetim Türü İçin UI Otomasyon Desteği
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu hakkında bilgi sağlar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] kaydırıcı denetim türü için destek. İçinde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], Denetim türü bir denetim kullanmak için karşılaması gereken koşulları kümesidir <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> özelliği. Özel yönergeleri koşulları dahil [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısını [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerlerini ve Denetim türleri.  
  
 Sayısal Aralık ayarlayın veya bir dizi öğesini seçmek bir kullanıcı fare ile etkinleştirme düğmeleri ile bileşik denetim kaydırıcı denetimidir.  
  
 Aşağıdaki bölümlerde gerekli tanımlamak [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısı, özellikler, Denetim düzenleri ve kaydırıcı denetim türü için olayları. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Gereksinimler tüm kaydırıcı denetimleri için geçerli olup olmadığını [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], veya [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyon ağaç yapısı  
 Aşağıdaki tablo denetimi ve içerik görünümünde gösterir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] kaydırıcısını ilgilidir ağaç denetler ve her bir görünümde bulunabilir açıklar. Daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç bkz [UI Otomasyon ağacına genel bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Denetim Görünüm|İçerik görünümü|  
|------------------|------------------|  
|Kaydırıcı<br /><br /> -Düğme (2 veya 4)<br />-Thumb (yalnızca 1)<br />-Liste öğesi (0 veya daha fazla)|Kaydırıcı<br /><br /> -Liste öğesi (0 veya daha fazla)|  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon özellikleri  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri olan bir değer veya tanımı kaydırıcısını yakından ilgili denetim türü. Daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri görmek [istemciler için UI Otomasyon özellikleri](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Özelliği|Değer|Notlar|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlara bakın.|Bu özelliğin değerini bir uygulamadaki tüm denetimler arasında benzersiz olması gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlara bakın.|Tam denetimi içeren en dıştaki dikdörtgen.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Notlara bakın|Kaydırıcı denetimleri çoğunu oluşturmalıdır <xref:System.Windows.Automation.NoClickablePointException> tüm sınırlayıcı dikdörtgenini kaydırıcı denetiminde alt denetimleri tarafından dolu olduğundan.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Notlara bakın.|Denetimin klavye odağı alamıyorsa, bu özelliği desteklemesi gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlara bakın.|Düzenleme denetiminin adını, genellikle bir statik metin etiketi oluşturulur. Bir statik metin etiketi yoksa, bir özellik değeri için `Name` uygulama geliştiricisi tarafından atanmalıdır. `Name` Özellik düzenleme denetiminin metin içeriğini hiçbir zaman içermelidir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Notlara bakın.|Denetimle ilişkili bir statik metin etiketi varsa, bu özellik bu denetime başvuru göstermesi gerekir. Metin denetimini başka bir denetimin alt ise değil olması bir `LabeledBy` özellik kümesi.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Kaydırıcı|Bu değer için aynı olan [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] çerçeveleri.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"kaydırıcı"|Düzenle denetim türü için karşılık gelen yerelleştirilmiş bir dize.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Doğru|Düzenleme denetimi her zaman içerik görünümünde bulunan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Doğru|Düzenleme denetimi her zaman denetim görünümünde bulunan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Gerekli UI Otomasyon denetim düzenleri  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] denetim desenleri tüm kaydırıcı denetimleri tarafından desteklenmesi gerekir. Denetim desenleri hakkında daha fazla bilgi için bkz. [UI Otomasyon denetim düzenlerine genel bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Denetim düzeni|Destek|Notlar|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Bağlıdır|İçerik ayrı bir seçenek kümesi arasında bir değeri temsil ediyorsa, bir Kaydırıcıyı seçim denetim düzeni desteklemelidir. Karşılık gelen seçimi, seçim denetim düzeni desteklendiğinde, bir veya daha fazla alt Lise öğelerini kaydırıcının sunulmalıdır.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Bağlıdır|İçeriği bir sayısal aralık içinde bir değere ayarlarsanız, bir Kaydırıcıyı RangeValue denetim düzeni desteklemelidir.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Bağlıdır|İçerik ayrı bir seçenek kümesi arasında bir değeri temsil ediyorsa, bir kaydırıcı değeri denetim düzeni desteklemelidir.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyonu olayları  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayları tüm kaydırıcı denetimleri tarafından desteklenmesi gerekir.  
  
 Olaylar hakkında daha fazla bilgi için bkz. [UI Otomasyonu olaylarına genel bakış](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Olay|Destek|Notlar|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Bağlıdır|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> özellik değişti olayı|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> özellik değişti olayı|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> özellik değişti olayı|Gerekli|None|  
|<xref:System.Windows.Automation.RangeValuePatternIdentifiers.ValueProperty> özellik değişti olayı|Bağlıdır|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|Yok.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.ControlType.Slider>
- [UI Otomasyonu Denetim Türlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)
- [UI Otomasyonuna Genel Bakış](../../../docs/framework/ui-automation/ui-automation-overview.md)
