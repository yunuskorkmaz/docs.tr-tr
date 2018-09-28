---
title: ScrollBar Denetim Türü için UI Otomasyon Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Scroll Bar control type
- control types, Scroll Bar
- Scroll Bar control type
ms.assetid: 329891d7-b609-49e6-920a-09ea8a627d07
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 666f8f60e27a2e513d9d33ddb6ca09c312e40126
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47421761"
---
# <a name="ui-automation-support-for-the-scrollbar-control-type"></a>ScrollBar Denetim Türü için UI Otomasyon Desteği
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu hakkında bilgi sağlar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] kaydırma çubuğu denetim türü için destek. İçinde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], Denetim türü bir denetim kullanmak için karşılaması gereken koşulları kümesidir <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> özelliği. Özel yönergeleri koşulları dahil [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısını [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerlerini ve denetim düzenleri.  
  
 Kaydırma çubuğu denetimleri içerik penceresi veya öğesi bir kapsayıcı içinde kaydırmak bir kullanıcı etkinleştirin. Denetim, bir dizi düğme ve bir thumb denetimi yapılır.  
  
 Aşağıdaki bölümlerde gerekli tanımlamak [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısı, özellikler, Denetim düzenleri ve kaydırma çubuğu denetim türü için olayları. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Gereksinimler tüm liste denetimleri için geçerli olup olmadığını [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], veya [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyon ağaç yapısı  
 Aşağıdaki tablo denetimi ve içerik görünümünde gösterir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , kaydırma denetimleri ilgilidir ve her bir görünümde bulunabilir açıklayan ağaç. Daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç bkz [UI Otomasyon ağacına genel bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Denetim Görünüm|İçerik görünümü|  
|------------------|------------------|  
|ScrollBar<br /><br /> -Düğme (2 veya 4)<br />-Küçük resim (0 veya 1)|Yok. Kaydırma çubuğu denetimi içeriği içermiyor.|  
  
 Kaydırma çubuğu denetimi her zaman üç ile beş alt sahiptir. Alt ağaçta birden fazla düğme denetimi olduğundan, belirli bir ayarlamalısınız <xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty> test otomasyon araçları bulunabilir hale getirmek için her bir öğenin değeri.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon özellikleri  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , değer veya tanımı kaydırma denetimleri yakından ilgili özellikler. Bir kaydırma çubuğu denetimi, içerik hiçbir zaman sahip olduğunu unutmayın; kaydırılan kapsayıcıdaki desteklenen kaydırma denetim düzeni aracılığıyla işlevselliği kullanıma sunulur.  
  
 Hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri görmek [istemciler için UI Otomasyon özellikleri](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Özelliği|Değer|Notlar|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlara bakın.|Bu özelliğin değerini bir uygulamadaki tüm denetimler arasında benzersiz olması gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlara bakın.|Tam denetimi içeren en dıştaki dikdörtgen.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Notlara bakın.|Denetimin klavye odağı alamıyorsa, bu özelliği desteklemesi gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|`Null`|Kaydırma çubuğu denetimi içerik öğeleri yok ve `NameProperty` ayarlamak için gerekli değildir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Sayı değil.|Kaydırma çubuğu denetimi tıklanabilir bir nokta yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Kaydırma çubukları etiketleri yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|ScrollBar|Bu değer, tüm çerçeveler için aynıdır. Kaydırıcı denetim türü kaydırıcıları kullanmanız gerektiği gibi bu işlev kaydırma çubukları.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"kaydırma çubuğu"|Düğme denetim türü için karşılık gelen yerelleştirilmiş dize arar.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|False|Kaydırma çubuğu denetimi hiçbir zaman içerik bir öğedir. Kaydırma çubuğu tek başına bir denetimdir sonra kaydırıcı denetim türü yerine getirmek gerekir ve dönüş `ControlType.Slider` için `ControlType` özelliği.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Doğru|Kaydırma çubuğunu her zaman bir denetim olmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.OrientationProperty>|Doğru|Kaydırma çubuğu denetimi her zaman yatay veya dikey yönünü kullanıma sunması gerekir.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Gerekli UI Otomasyon denetim düzenleri  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] denetim desenleri kaydırma çubuğu denetimleri tarafından desteklenmesi gerekir. Denetim desenleri hakkında daha fazla bilgi için bkz. [UI Otomasyon denetim düzenlerine genel bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md). Bir kaydırma çubuğu denetimi olarak yalnızca fare işleme için kullanıldığında, bu denetim düzenleri desteklemediğini unutmayın. Bir uygulamadaki bir kaydırıcı denetimi olarak kullanılıyorsa, kaydırıcı denetim türü verilmelidir.  
  
|Denetim düzeni|Destek|Notlar|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|hiçbir zaman|Kaydırma denetim düzeni hiçbir zaman doğrudan kaydırma çubuğundaki desteklenir.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Bağlıdır|Bu işlev yalnızca kaydırma denetim düzeni kaydırma çubuğu içeren kapsayıcıdaki desteklenmiyorsa desteklenmesi için gereklidir.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyonu olayları  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayları tüm kaydırma çubuğu denetimleri tarafından desteklenmesi gerekir. Olaylar hakkında daha fazla bilgi için bkz. [UI Otomasyonu olaylarına genel bakış](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Olay|Destek/değer|Notlar|  
|---------------------------------------------------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> özellik değişti olayı.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> özellik değişti olayı.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> özellik değişti olayı.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> özellik değişti olayı.|hiçbir zaman|Yok.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> özellik değişti olayı.|hiçbir zaman|Yok.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> özellik değişti olayı.|hiçbir zaman|Yok.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> özellik değişti olayı.|hiçbir zaman|Yok.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> özellik değişti olayı.|hiçbir zaman|Yok.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> özellik değişti olayı.|hiçbir zaman|Yok.|  
|<xref:System.Windows.Automation.RangeValuePatternIdentifiers.ValueProperty> özellik değişti olayı.|Bağlıdır|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|Yok.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Automation.ControlType.ScrollBar>  
 [UI Otomasyonu Denetim Türlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [UI Otomasyonuna Genel Bakış](../../../docs/framework/ui-automation/ui-automation-overview.md)
