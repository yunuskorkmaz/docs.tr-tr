---
title: Düzenleme Denetim Türü İçin UI Otomasyon Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Edit
- Edit control type
- UI Automation, Edit control type
ms.assetid: 6db9d231-c0a0-4e17-910e-ac80357f774f
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 0cd1744702448836e6b4e1eb04d14725a1baba39
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408552"
---
# <a name="ui-automation-support-for-the-edit-control-type"></a>Düzenleme Denetim Türü İçin UI Otomasyon Desteği
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu aşağıdakiler hakkında bilgi sağlar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Düzenle denetim türü için destek. İçinde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], Denetim türü bir denetimi kullanmak için karşılaması gereken koşulları kümesidir <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> özelliği. Koşullar özel yönergeleri dahil [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısı, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerlerini ve denetim düzenleri.  
  
 Düzenleme denetimleri görüntülemek ve basit bir metin satırının zengin biçimlendirme desteği düzenlemek bir kullanıcı etkinleştirin.  
  
 Aşağıdaki bölümlerde gerekli tanımlamak [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısı, özellikler, Denetim desenleri ve olayları düzenleme denetim türü için. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Gereksinimleri uygulamak için tüm olup denetimleri düzenlemek [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], veya [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyon ağaç yapısı  
 Denetim Görünüm ve içerik görünümünü aşağıdaki tabloda gösterilmektedir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , denetimleri düzenlemek için geçerlidir ve her bir görünümde bulunabilir açıklayan ağacı. Hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç bkz [UI Otomasyon ağacına genel bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Denetim Görünüm|İçerik görünümü|  
|------------------|------------------|  
|Düzenle|Düzenle|  
  
 Düzenleme denetim türü uygulamak denetimleri, her zaman sıfır kaydırma çubukları denetim görünümünde olacaktır [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tek satırlı denetim olduğundan ağacı. Tek satırlık metin bazı düzeni senaryolarda sarmalamak. Düzenleme denetim türü düzenlenebilir veya seçilebilir metni küçük miktarda tutmak için uygundur.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon özellikleri  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , değer veya tanımı düzenleme denetimleri özellikle ilgili özellikler. Hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri, görmek [istemciler için UI Otomasyon özellikleri](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Özelliği|Değer|Notlar|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlarına bakın.|Bu özelliğin değeri bir uygulamadaki tüm denetimler arasında benzersiz olması gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlarına bakın.|Tam denetimi içeren en dıştaki dikdörtgen.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Notlarına bakın.|Düzenleme denetimi, bir kullanıcı fare var. tıkladığında giriş odağı denetimi Düzenle bölümüne tıklanabilir bir noktası olması gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Notlarına bakın.|Klavye odağı denetimi alamıyorsa, bu özelliği desteklemelidir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlarına bakın.|Düzenleme denetimi adı, genellikle bir statik metin etiketinden oluşturulur. Bir statik metin etiketi değilse, bir özellik değeri için `Name` uygulama geliştiricisi tarafından atanması gerekir. `Name` Özelliği düzenleme denetimi metin içeriğini hiçbir zaman içermelidir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Notlarına bakın.|Denetimle ilişkili bir statik metin etiketi varsa, bu özellik bu denetim için bir başvuru kullanıma gerekir. Metin denetim başka bir denetimin bir alt bileşen ise değil olacaktır bir `LabeledBy` özellik kümesi.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Düzenle|Bu değer tüm aynıdır [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] çerçeveleri.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"Düzenle"|Düzenleme denetim türü için karşılık gelen yerelleştirilmiş dize.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Doğru|Düzenleme denetimi her zaman içerik görünümünde dahil [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Doğru|Düzenleme denetimi her zaman denetim görünümünde dahil [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsPasswordProperty>|Notlarına bakın.|Doğru üzerinde parolalar denetimleri düzenlemek için ayarlamanız gerekir. Düzenleme denetimi parola içeriği içeriyorsa, daha sonra bu özellik bir ekran okuyucusu tarafından tuş vuruşları kullanıcı türleri olarak bunları okunur olmalıdır olup olmadığını belirlemek için kullanılabilir.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns-and-properties"></a>UI Otomasyon denetim düzenleri ve özellikleri gerekli  
 Denetim desenleri tüm tarafından desteklenmesi için gereken aşağıdaki tabloda denetimleri düzenleyin. Denetim desenleri hakkında daha fazla bilgi için bkz: [UI Otomasyon denetim düzenlerine genel bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Denetim düzeni/denetim deseni özelliği|Destek/değer|Notlar|  
|-----------------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITextProvider>|Bağlıdır|Düzenleme denetimleri ayrıntılı metin bilgileri her zaman istemciler için kullanılabilir olması gerekir çünkü metin denetim düzeni desteklemelidir.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Bağlıdır|Bir dize olması tüm düzenleme denetimlerinde değer düzenini kullanıma gerekir.|  
|<xref:System.Windows.Automation.Provider.IValueProvider.IsReadOnly%2A>|Notlarına bakın.|Bu özellik denetimi programlı olarak ayarlanmış bir değer olabilir veya düzenlenebilir olup olmadığını belirtmek için kullanıcı tarafından ayarlanması gerekir.|  
|<xref:System.Windows.Automation.Provider.IValueProvider.Value%2A>|Notlarına bakın.|Bu özellik düzenleme denetimi metin içeriğini döndürür. Varsa `IsPasswordProperty` ayarlanır `true`, bu özellik artırmalısınız bir `InvalidOpertaionException` istendiğinde.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Bağlıdır|Sayısal bir aralık ele tüm düzenleme denetimlerinde aralık değeri denetim düzeni kullanıma gerekir.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.Minimum%2A>|Notlarına bakın.|Bu özellik düzenleme denetimin içeriği ayarlanabilir en küçük değeri olmalıdır.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.Maximum%2A>|Notlarına bakın.|Bu özellik düzenleme denetimin içeriği ayarlanabilir en büyük değeri olmalıdır.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.SmallChange%2A>|Notlarına bakın.|Bu özellik değeri olarak ayarlanabilir ondalık basamak sayısını belirtmeniz gerekir. Düzen yalnızca tamsayı, izlerseniz `SmallChangeProperty` 1 olmalıdır. Düzen 2.0 1.0 arasında bir aralık sürerse sonra `SmallChangeProperty` 0,1 olması gerekir. Düzenleme denetimi 2,00 1.00 arasında bir aralık sürerse sonra `SmallChangeProperty` 0,001 olması gerekir.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.LargeChange%2A>|`Null`|Bu özellik, bir düzenleme denetimi açığa çıkarılması gerekmez.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.Value%2A>|Notlarına bakın.|Bu özellik düzenleme denetimi sayısal içeriğini gösterir. Daha kesin bir değere ayarlandığında bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] istemci belirtilen aralıklarında `Minimum` ve `Maximum` özellikleri, özellik otomatik olarak yuvarlanmasını en yakın kabul edilebilir değere değeri.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyon olayları  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tüm tarafından desteklenmesi için gerekli olayları düzenleme denetimleri. Olaylar hakkında daha fazla bilgi için bkz: [UI Otomasyonu olaylarına genel bakış](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Olay|Destek|Notlar|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Gerekli|Yok.|  
|<xref:System.Windows.Automation.TextPatternIdentifiers.TextSelectionChangedEvent>|Gerekli|Yok.|  
|<xref:System.Windows.Automation.TextPatternIdentifiers.TextChangedEvent>|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> özellik değişti olayı.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> özellik değişti olayı.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> özellik değişti olayı.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty> özellik değişti olayı.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> özellik değişti olayı.|Bağlıdır|Yok.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> özellik değişti olayı.|Hiçbir zaman|Yok.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> özellik değişti olayı.|Hiçbir zaman|Yok.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> özellik değişti olayı.|Hiçbir zaman|Yok.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> özellik değişti olayı.|Hiçbir zaman|Yok.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> özellik değişti olayı.|Hiçbir zaman|Yok.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> özellik değişti olayı.|Hiçbir zaman|Yok.|  
|<xref:System.Windows.Automation.RangeValuePatternIdentifiers.ValueProperty> özellik değişti olayı.|Bağlıdır|Denetim aralık değeri denetim düzeni destekliyorsa, bu olay desteklemesi gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|Yok.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Automation.ControlType.Edit>  
 [UI Otomasyonu Denetim Türlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [UI Otomasyonuna Genel Bakış](../../../docs/framework/ui-automation/ui-automation-overview.md)
