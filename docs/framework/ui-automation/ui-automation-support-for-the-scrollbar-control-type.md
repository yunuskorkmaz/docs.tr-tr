---
title: ScrollBar Denetim Türü için UI Otomasyon Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Scroll Bar control type
- control types, Scroll Bar
- Scroll Bar control type
ms.assetid: 329891d7-b609-49e6-920a-09ea8a627d07
ms.openlocfilehash: 7a8371f46bb81410b653a7ba830605ec11c5b7f3
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75741161"
---
# <a name="ui-automation-support-for-the-scrollbar-control-type"></a>ScrollBar Denetim Türü için UI Otomasyon Desteği
> [!NOTE]
> Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konuda, ScrollBar denetim türü için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] desteği hakkında bilgi verilmektedir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], denetim türü, bir denetimin <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> özelliğini kullanmak için karşılaması gereken koşullar kümesidir. Koşullar, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısına yönelik özel yönergeler, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerleri ve Denetim desenleri içerir.  
  
 Kaydırma çubuğu denetimleri, bir kullanıcının bir pencere veya öğe kapsayıcısı içindeki içeriği kaymasını sağlar. Denetim, bir düğme kümesinden ve Thumb denetiminden oluşur.  
  
 Aşağıdaki bölümler, kaydırma çubuğu denetim türü için gerekli [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısını, özellikleri, denetim desenlerini ve olayları tanımlar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gereksinimleri, [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], Win32 veya [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]bakılmaksızın tüm liste denetimlerine uygulanır.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyonu ağaç yapısı  
 Aşağıdaki tabloda, kaydırma çubuğu denetimleriyle ilgili [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacının denetim görünümü ve içerik görünümü gösterilmektedir ve her görünümde nelerin yer aldığı açıklanmaktadır. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı hakkında daha fazla bilgi için bkz. [UI Otomasyon ağacına genel bakış](ui-automation-tree-overview.md).  
  
|Denetim görünümü|İçerik görünümü|  
|------------------|------------------|  
|ScrollBar<br /><br /> -Düğme (2 veya 4)<br />-Thumb (0 i:<0)|Yok. Kaydırma çubuğu denetimi içerik içermiyor.|  
  
 Kaydırma çubuğu denetiminin her zaman üç ila beş alt öğesi vardır. Alt ağaçta birden çok düğme denetimi olduğundan, test otomasyon araçları için, her öğeye belirli bir <xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty> değeri ayarlamanız gerekir.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon Özellikleri  
 Aşağıdaki tabloda, değeri veya tanımı özellikle kaydırma çubuğu denetimleriyle ilgili olan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri listelenmektedir. Kaydırma çubuğu denetiminin hiçbir şekilde içerik olmadığına unutmayın; işlevi, kaydırılan kapsayıcıda desteklenen kaydırma denetimi düzeniyle gösterilir.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri hakkında daha fazla bilgi için bkz. [istemciler Için UI Otomasyon özellikleri](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özelliği|Değer|Notlar|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlara bakın.|Bu özelliğin değerinin bir uygulamadaki tüm denetimlerde benzersiz olması gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlara bakın.|Tüm denetimi içeren en dıştaki dikdörtgen.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Notlara bakın.|Denetim, klavye odağı alamıyorsa, bu özelliği desteklemesi gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|`Null`|Kaydırma çubuğu denetiminin içerik öğeleri yok ve `NameProperty` ayarlanması gerekli değil.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Bir sayı değil.|Kaydırma çubuğu denetiminin tıklatılabilir noktaları yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Kaydırma çubuklarının etiketleri yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|ScrollBar|Bu değer tüm çerçeveler için aynıdır. Kaydırıcılar olarak işlev gösteren kaydırma çubuklarının kaydırıcı denetim türünü kullanması gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"kaydırma çubuğu"|Düğme denetim türüne karşılık gelen yerelleştirilmiş dize.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|False|Kaydırma çubuğu denetimi hiçbir şekilde bir içerik öğesidir. Kaydırma çubuğu tek başına bir denetimdir, kaydırıcı denetim türünü yerine getirmek ve `ControlType` özelliği için `ControlType.Slider` döndürmesi gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Doğru|Kaydırma çubuğunun her zaman bir denetim olması gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.OrientationProperty>|Doğru|Kaydırma çubuğu denetimi her zaman yatay veya dikey yönünü kullanıma sunmalıdır.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Gerekli UI Otomasyonu Denetim desenleri  
 Aşağıdaki tabloda, kaydırma çubuğu denetimleri tarafından desteklenmesi gereken [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Denetim desenleri listelenmektedir. Denetim desenleri hakkında daha fazla bilgi için bkz. [UI Otomasyonu Denetim desenlerine genel bakış](ui-automation-control-patterns-overview.md). Bir kaydırma çubuğu yalnızca fare düzenleme için denetim olarak kullanıldığında, denetim düzenlerini desteklemez. Bir uygulama içinde kaydırıcı denetimi olarak kullanılırsa, kaydırıcı denetim türü verilmelidir.  
  
|Denetim deseninin|Destek|Notlar|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|hiçbir zaman|Kaydırma çubuğunda kaydırma denetim deseninin hiçbir şekilde doğrudan desteklenmemesi.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Şekline|Bu işlevselliğin yalnızca, kaydırma çubuğu içeren kapsayıcıda Scroll Control deseninin desteklenmediği durumlarda desteklenmesi gerekir.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyon olayları  
 Aşağıdaki tabloda, tüm kaydırma çubuğu denetimleri tarafından desteklenmesi gereken [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayları listelenmektedir. Olaylar hakkında daha fazla bilgi için bkz. [UI Otomasyonu olaylarına genel bakış](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayı|Destek/değer|Notlar|  
|---------------------------------------------------------------------------------|--------------------|-----------|  
|özellik değişti olayı <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>.|Gerekli|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>.|Gerekli|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>.|Gerekli|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>.|hiçbir zaman|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty>.|hiçbir zaman|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty>.|hiçbir zaman|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty>.|hiçbir zaman|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>.|hiçbir zaman|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty>.|hiçbir zaman|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.RangeValuePatternIdentifiers.ValueProperty>.|Şekline|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|Yok.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.ControlType.ScrollBar>
- [UI Otomasyonu Denetim Türlerine Genel Bakış](ui-automation-control-types-overview.md)
- [UI Otomasyonuna Genel Bakış](ui-automation-overview.md)
