---
title: Kaydırıcı Denetim Türü İçin UI Otomasyon Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Slider
- UI Automation, Slider control type
- Slider control type
ms.assetid: 045ea62f-7b50-46cf-a5a9-8eb97704355f
ms.openlocfilehash: 34a093fa0be68ddab75d78c0113fe110d4332773
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76786060"
---
# <a name="ui-automation-support-for-the-slider-control-type"></a>Kaydırıcı Denetim Türü İçin UI Otomasyon Desteği
> [!NOTE]
> Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konuda kaydırıcı denetim türü için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] desteği hakkında bilgi verilmektedir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], denetim türü, bir denetimin <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> özelliğini kullanmak için karşılaması gereken koşullar kümesidir. Koşullar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısına yönelik belirli yönergeleri, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerlerini ve denetim türlerini içerir.  
  
 Kaydırıcı denetimi, fare ile bir kullanıcının sayısal bir Aralık ayarlaması veya bir dizi öğe arasından seçim yapmak için fare sağlayan düğmeleri içeren bileşik bir denetimdir.  
  
 Aşağıdaki bölümler kaydırıcı denetim türü için gerekli [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısını, özellikleri, denetim desenlerini ve olayları tanımlar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gereksinimleri, [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], Win32 veya Windows Forms gibi tüm kaydırıcı denetimleri için geçerlidir.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyonu ağaç yapısı  
 Aşağıdaki tabloda, kaydırıcı denetimleriyle ilgili [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacının denetim görünümü ve Içerik görünümü gösterilmektedir ve her görünümde nelerin yer aldığı açıklanmaktadır. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı hakkında daha fazla bilgi için bkz. [UI Otomasyon ağacına genel bakış](ui-automation-tree-overview.md).  
  
|Denetim görünümü|İçerik görünümü|  
|------------------|------------------|  
|Kaydırıcı<br /><br /> -Düğme (2 veya 4)<br />-Thumb (yalnızca 1)<br />-Liste öğesi (0 veya daha fazla)|Kaydırıcı<br /><br /> -Liste öğesi (0 veya daha fazla)|  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon Özellikleri  
 Aşağıdaki tabloda, değeri veya tanımı özellikle kaydırıcı denetim türüyle ilgili olan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri listelenmektedir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri hakkında daha fazla bilgi için bkz. [istemciler Için UI Otomasyon özellikleri](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özelliği|Değer|Notlar|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlara bakın.|Bu özelliğin değerinin bir uygulamadaki tüm denetimlerde benzersiz olması gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlara bakın.|Tüm denetimi içeren en dıştaki dikdörtgen.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Notlara bakın|Kaydırıcı denetiminin tüm sınırlayıcı dikdörtgeninin alt denetimler tarafından yer aldığı için kaydırıcı denetimlerinin çoğu <xref:System.Windows.Automation.NoClickablePointException> yükseltmelidir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Notlara bakın.|Denetim, klavye odağı alamıyorsa, bu özelliği desteklemesi gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlara bakın.|Düzenleme denetiminin adı genellikle statik bir metin etiketinden oluşturulur. Statik bir metin etiketi yoksa, `Name` için bir özellik değeri uygulama geliştiricisi tarafından atanmalıdır. `Name` özelliği asla düzenleme denetiminin metin içeriğini içermemelidir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Notlara bakın.|Denetimle ilişkili bir statik metin etiketi varsa, bu özellik bu denetimin bir başvurusunu kullanıma sunmalıdır. Metin denetimi başka bir denetimin alt bileşeni ise, `LabeledBy` özellik kümesine sahip olmaz.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Kaydırıcı|Bu değer tüm [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] çerçeveleri için aynıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|sürgü|Düzenleme denetim türüne karşılık gelen yerelleştirilmiş dize.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Doğru|Düzenleme denetimi her zaman [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacının içerik görünümüne dahil edilmiştir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Doğru|Düzenleme denetimi her zaman [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacının denetim görünümüne dahil edilmiştir.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Gerekli UI Otomasyonu Denetim desenleri  
 Aşağıdaki tabloda, tüm kaydırıcı denetimleri tarafından desteklenmesi gereken [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Denetim desenleri listelenmektedir. Denetim desenleri hakkında daha fazla bilgi için bkz. [UI Otomasyonu Denetim desenlerine genel bakış](ui-automation-control-patterns-overview.md).  
  
|Denetim deseninin|Destek|Notlar|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Şekline|İçerik, farklı bir seçenek kümesi arasında bir değeri temsil ediyorsa, kaydırıcı seçim denetim deseninin desteklenmesi gerekir. Seçim Denetim deseninin desteklenmesinde, ilgili seçim kaydırıcının bir veya daha fazla alt liste öğesi olarak gösterilmelidir.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Şekline|İçerik, sayısal bir aralıktaki bir değere ayarlanbiliyorsanız, bir kaydırıcı RangeValue denetim deseninin desteklenmesi gerekir.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Şekline|İçerik, ayrı bir seçenek kümesi arasında bir değeri temsil ediyorsa, kaydırıcı değer denetim deseninin desteklenmesi gerekir.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyon olayları  
 Aşağıdaki tabloda, tüm kaydırıcı denetimleri tarafından desteklenmesi gereken [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayları listelenmektedir.  
  
 Olaylar hakkında daha fazla bilgi için bkz. [UI Otomasyonu olaylarına genel bakış](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayı|Destek|Notlar|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Şekline|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> özelliği değiştirildi olayı|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> özelliği değiştirildi olayı|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> özelliği değiştirildi olayı|Gerekli|Yok.|  
|<xref:System.Windows.Automation.RangeValuePatternIdentifiers.ValueProperty> özelliği değiştirildi olayı|Şekline|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|Yok.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.ControlType.Slider>
- [UI Otomasyonu Denetim Türlerine Genel Bakış](ui-automation-control-types-overview.md)
- [UI Otomasyonuna Genel Bakış](ui-automation-overview.md)
