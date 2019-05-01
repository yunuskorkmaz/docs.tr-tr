---
title: Değer Değiştirici Denetim Türü İçin UI Otomasyon Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Spinner control type
- Spinner control type
- control types, Spinner
ms.assetid: 3a29d185-65d8-42e3-bcc3-7f43e96f40c5
ms.openlocfilehash: c2e2c016da104119be564003196ccb3e3dd73959
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61996625"
---
# <a name="ui-automation-support-for-the-spinner-control-type"></a>Değer Değiştirici Denetim Türü İçin UI Otomasyon Desteği
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu hakkında bilgi sağlar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Spinner denetim türü için destek. İçinde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], Denetim türü bir denetim kullanmak için karşılaması gereken koşulları kümesidir <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> özelliği. Özel yönergeleri koşulları dahil [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısını [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerlerini ve denetim düzenleri.  
  
 Değer değiştirici denetim öğesi bir etki alanı ya da bir dizi numarası seçmek için kullanılır.  
  
 Aşağıdaki bölümlerde gerekli tanımlamak [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısı, özellikler, Denetim düzenleri ve değer değiştirici denetim türü için olayları. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Gereksinimler tüm değiştirici denetimleri için geçerli olup olmadığını [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], veya [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyon ağaç yapısı  
 Aşağıdaki tablo denetimi ve içerik görünümünde gösterir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] değiştiricisi için ilgilidir ağaç aralık değeri, değer ve seçim denetim düzenleri desteği denetler ve her bir görünümde bulunabilir açıklar. Daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç bkz [UI Otomasyon ağacına genel bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
 **Değer ya da değer aralığı denetim düzeni**  
  
|Denetim Görünüm|İçerik görünümü|  
|------------------|------------------|  
|Değer Değiştirici<br /><br /> -(0 veya 1) Düzenle<br />-Düğmesine (2)|Değer Değiştirici|  
  
 **Seçim denetim düzeni**  
  
|Denetim Görünüm|İçerik görünümü|  
|------------------|------------------|  
|Değer Değiştirici<br /><br /> -(0 veya 1) Düzenle<br />-Düğmesine (2)<br />-Liste öğesi (0 veya daha fazla)|Değer Değiştirici<br /><br /> -ListItem (0 veya daha fazla)|  
  
 İki düğme denetimi görünümü ağaçtaki otomatikleştirilmiş test araçları tarafından ayrıt edilebilen emin olmak için Ata `SmallIncrement` veya `SmallDecrement` `AutomationId` uygun şekilde. Bazı uygulamalar için bir eş değer değiştirici denetim ilişkili düzenleme denetimi olabilir.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon özellikleri  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , değer veya tanımı değiştiricisi denetimlere yakından ilgili özellikler. Daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri görmek [istemciler için UI Otomasyon özellikleri](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Özelliği|Değer|Notlar|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlara bakın.|Bu özelliğin değerini bir uygulamadaki tüm denetimler arasında benzersiz olması gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlara bakın.|Tam denetimi içeren en dıştaki dikdörtgen.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Notlara bakın.|Değer değiştirici denetim tıklanabilir noktası denetimi Düzenle bölümüne odaklanır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Notlara bakın.|Denetimin klavye odağı alamıyorsa, bu özelliği desteklemesi gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlara bakın.|Değer değiştirici denetim, genellikle bir statik metin etiketten adını alır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Notlara bakın.|Değer değiştirici denetim bir statik metin etiketi olması.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Değer Değiştirici|Bu değer tüm UI çerçeveleri için aynıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"değer"değiştirici|Değer değiştirici denetim türü için karşılık gelen yerelleştirilmiş bir dize.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Doğru|Değer değiştirici denetim her zaman içerik olmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Doğru|Değer değiştirici denetim her zaman bir denetim olmalıdır.|  
  
<a name="Required_UI_Automation_Control_Patterns_and_Properties"></a>   
## <a name="required-ui-automation-control-patterns-and-properties"></a>UI Otomasyon denetim düzenleri ve özellikleri gerekli  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] denetim değer değiştirici denetim tarafından desteklenmesi için gereken desenleri. Denetim desenleri hakkında daha fazla bilgi için bkz: [UI Otomasyon denetim düzenlerine genel bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Denetim düzeni/desen özelliği|Destek/değer|Notlar|  
|---------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Bağlıdır|Seçilecek öğeleri listesine sahip değer değiştirici denetim bu desenin desteklenmesi gerekir.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|False|Değer değiştirici denetim her zaman tek bir seçim kapsayıcılardır.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Bağlıdır|Bu düzen sayısal aralığı değer değiştirici denetim destekler.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Bağlıdır|Bu düzen span ayrık dizi seçenek veya sayı değer değiştiricinin denetimleri destekler.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyonu olayları  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayları tüm değiştirici denetimleri tarafından desteklenmesi gerekir. Olaylar hakkında daha fazla bilgi için bkz. [UI Otomasyonu olaylarına genel bakış](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Olay|Destek|Notlar|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Bağlıdır|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> özellik değişti olayı.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> özellik değişti olayı.|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> özellik değişti olayı.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> özellik değişti olayı.|Bağlıdır|Yok.|  
|<xref:System.Windows.Automation.RangeValuePatternIdentifiers.ValueProperty> özellik değişti olayı.|Bağlıdır|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|Yok.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.ControlType.Spinner>
- [UI Otomasyonu Denetim Türlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)
- [UI Otomasyonuna Genel Bakış](../../../docs/framework/ui-automation/ui-automation-overview.md)
