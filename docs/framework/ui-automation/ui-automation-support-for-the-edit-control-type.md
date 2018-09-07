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
ms.openlocfilehash: 39804f7a525a45a4de37e7dded9ac4998280755f
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44070634"
---
# <a name="ui-automation-support-for-the-edit-control-type"></a>Düzenleme Denetim Türü İçin UI Otomasyon Desteği
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu hakkında bilgi sağlar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] düzenleme denetim türü için destek. İçinde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], Denetim türü bir denetim kullanmak için karşılaması gereken koşulları kümesidir <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> özelliği. Özel yönergeleri koşulları dahil [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısını [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerlerini ve denetim düzenleri.  
  
 Düzenleme denetimleri görüntülemek ve zengin biçimlendirme desteği basit bir metin satırı düzenlemek bir kullanıcı etkinleştirin.  
  
 Aşağıdaki bölümlerde gerekli tanımlamak [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısı, özellikler, Denetim düzenleri ve düzenleme denetim türü için olayları. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Gereksinimleri uygulamak için tüm denetimleri düzenleme [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], veya [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyon ağaç yapısı  
 Aşağıdaki tablo denetimi ve içerik görünümünde gösterir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç denetimleri düzenlemek için ilgilidir ve her bir görünümde bulunabilir açıklar. Hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç bkz [UI Otomasyon ağacına genel bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Denetim Görünüm|İçerik görünümü|  
|------------------|------------------|  
|Düzenle|Düzenle|  
  
 Edit denetim türü uygulama denetimleri denetim görünümünde her zaman sıfır kaydırma çubukları olacaktır [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tek satır denetimi olduğu için ağaç. Tek satırlık metin, bazı Düzen senaryolarda sarmalamanız. Edit denetim türü küçük miktarda metni düzenlenebilir veya seçilebilir tutmak için idealdir.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon özellikleri  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , değer veya tanımı düzenleme denetimleri yakından ilgili özellikler. Hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri görmek [istemciler için UI Otomasyon özellikleri](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Özelliği|Değer|Notlar|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlara bakın.|Bu özelliğin değerini bir uygulamadaki tüm denetimler arasında benzersiz olması gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlara bakın.|Tam denetimi içeren en dıştaki dikdörtgen.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Notlara bakın.|Düzenleme denetiminin, kullanıcı fare var. tıkladığında, giriş odağı denetimi Düzenle bölümüne tıklanabilir bir nokta olmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Notlara bakın.|Denetimin klavye odağı alamıyorsa, bu özelliği desteklemesi gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlara bakın.|Düzenleme denetiminin adını, genellikle bir statik metin etiketi oluşturulur. Bir statik metin etiketi yoksa, bir özellik değeri için `Name` uygulama geliştiricisi tarafından atanmalıdır. `Name` Özellik düzenleme denetiminin metin içeriğini hiçbir zaman içermelidir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Notlara bakın.|Denetimle ilişkili bir statik metin etiketi varsa, bu özellik bu denetime başvuru göstermesi gerekir. Metin denetimini başka bir denetimin alt ise değil olması bir `LabeledBy` özellik kümesi.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Düzenle|Bu değer için aynı olan [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] çerçeveleri.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"EDIT"|Edit denetim türü için karşılık gelen yerelleştirilmiş bir dize.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Doğru|Düzenleme denetimi her zaman içerik görünümünde bulunan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Doğru|Düzenleme denetimi her zaman denetim görünümünde bulunan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsPasswordProperty>|Notlara bakın.|Doğru üzerinde parolalar denetimleri düzenlemek için ayarlamanız gerekir. Bir düzenleme denetimi parola içeriği içermiyorsa, ardından bu özellik ekran okuyucu tarafından tuş vuruşları kullanıcı türleri olarak bunları okunmalıdır olup olmadığını belirlemek için kullanılabilir.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns-and-properties"></a>UI Otomasyon denetim düzenleri ve özellikleri gerekli  
 Denetim desenlerini tüm tarafından desteklenmesi için gereken aşağıdaki tabloda, denetimleri düzenleyin. Denetim desenleri hakkında daha fazla bilgi için bkz: [UI Otomasyon denetim düzenlerine genel bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Denetim düzeni/denetim düzeni özelliği|Destek/değer|Notlar|  
|-----------------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITextProvider>|Bağlıdır|Ayrıntılı metin bilgileri her zaman istemciler için kullanılabilir olmalıdır çünkü düzenleme denetimlerinin metin denetim düzenini desteklemelidir.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Bağlıdır|Bir dize olması tüm düzenleme denetimleri değer deseni kullanıma sunması gerekir.|  
|<xref:System.Windows.Automation.Provider.IValueProvider.IsReadOnly%2A>|Notlara bakın.|Bu özellik, denetimin program üzerinden ayarlamak için bir değer olabilir veya düzenlenebilir olduğunu belirtmek için kullanıcı tarafından ayarlanmalıdır.|  
|<xref:System.Windows.Automation.Provider.IValueProvider.Value%2A>|Notlara bakın.|Bu özellik düzenleme denetiminin metin içeriğini döndürür. Varsa `IsPasswordProperty` ayarlanır `true`, bu özellik oluşturmalıdır bir `InvalidOpertaionException` istendiğinde.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Bağlıdır|Sayısal Aralık Süren tüm düzenleme denetimlerinde aralık değeri denetim düzeni kullanıma sunması gerekir.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.Minimum%2A>|Notlara bakın.|Bu özellik düzenleme denetiminin içeriği için ayarlanabilen en küçük değeri olmalıdır.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.Maximum%2A>|Notlara bakın.|Bu özellik düzenleme denetiminin içeriği için ayarlanabilen en büyük değeri olmalıdır.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.SmallChange%2A>|Notlara bakın.|Bu özellik değeri için ayarlanabilen bir ondalık basamak sayısını belirtmeniz gerekir. Düzen yalnızca tamsayılar alırsanız `SmallChangeProperty` 1 olmalıdır. Düzen 1.0 bir aralıktan 2.0, uzun sürerse sonra `SmallChangeProperty` 0,1 olması gerekir. Düzenleme denetimi 1,00 bir aralıktan 2,00 için uzun sürerse sonra `SmallChangeProperty` 0,001 olması gerekir.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.LargeChange%2A>|`Null`|Bu özellik bir düzenleme denetimi açığa gerekmez.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.Value%2A>|Notlara bakın.|Bu özellik, sayısal düzenleme denetiminin içeriğini gösterir. Daha kesin bir değere ayarlandığında bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] istemci belirtilen aralıklar dahilinde `Minimum` ve `Maximum` özellikleri, özellik otomatik olarak yuvarlanır en yakın kabul edilen değeri için değer.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyonu olayları  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tüm tarafından desteklenmesi için gerekli olayları düzenleme denetimleri. Olaylar hakkında daha fazla bilgi için bkz. [UI Otomasyonu olaylarına genel bakış](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
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
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> özellik değişti olayı.|hiçbir zaman|Yok.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> özellik değişti olayı.|hiçbir zaman|Yok.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> özellik değişti olayı.|hiçbir zaman|Yok.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> özellik değişti olayı.|hiçbir zaman|Yok.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> özellik değişti olayı.|hiçbir zaman|Yok.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> özellik değişti olayı.|hiçbir zaman|Yok.|  
|<xref:System.Windows.Automation.RangeValuePatternIdentifiers.ValueProperty> özellik değişti olayı.|Bağlıdır|Aralık değeri denetim düzeni denetimini destekliyorsa, bu olay desteklemesi gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|Yok.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Automation.ControlType.Edit>  
 [UI Otomasyonu Denetim Türlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [UI Otomasyonuna Genel Bakış](../../../docs/framework/ui-automation/ui-automation-overview.md)
