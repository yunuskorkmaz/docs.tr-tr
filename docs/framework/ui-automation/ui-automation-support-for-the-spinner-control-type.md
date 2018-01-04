---
title: "Değer Değiştirici Denetim Türü İçin UI Otomasyon Desteği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, Spinner control type
- Spinner control type
- control types, Spinner
ms.assetid: 3a29d185-65d8-42e3-bcc3-7f43e96f40c5
caps.latest.revision: "21"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 8a5c5fda5b3f29e8c91290e7dcb3de0635ee94b4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ui-automation-support-for-the-spinner-control-type"></a>Değer Değiştirici Denetim Türü İçin UI Otomasyon Desteği
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu aşağıdakiler hakkında bilgi sağlar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] değer değiştirici denetim türü için destek. İçinde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], Denetim türü bir denetimi kullanmak için karşılaması gereken koşulları kümesidir <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> özelliği. Koşullar özel yönergeleri dahil [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısı, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerlerini ve denetim düzenleri.  
  
 Değer değiştirici denetim öğeleri bir etki alanı veya bir dizi numarası seçmek için kullanılır.  
  
 Aşağıdaki bölümlerde gerekli tanımlamak [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısı, özellikleri, Denetim desenleri ve olayları değer değiştirici denetim türü için. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Gereksinimleri geçerlidir tüm değiştiricisi denetimlere olup olmadığını [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], veya [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyon ağaç yapısı  
 Denetim Görünüm ve içerik görünümünü aşağıdaki tabloda gösterilmektedir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] için değer değiştirici ilgilidir ağaç aralık değeri, değer ve seçim denetim düzenleri desteği denetler ve her bir görünümde bulunabilir açıklar. Daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç bkz [UI Otomasyon ağacına genel bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
 **Değer veya değer aralığı denetim düzeni**  
  
|Denetim Görünüm|İçerik görünümü|  
|------------------|------------------|  
|Değer Değiştirici<br /><br /> -Düzenleme (0 veya 1)<br />-Düğmesi (2)|Değer Değiştirici|  
  
 **Seçim denetim deseni**  
  
|Denetim Görünüm|İçerik görünümü|  
|------------------|------------------|  
|Değer Değiştirici<br /><br /> -Düzenleme (0 veya 1)<br />-Düğmesi (2)<br />-Liste öğesi (0 veya daha fazla)|Değer Değiştirici<br /><br /> -ListItem (0 veya daha fazla)|  
  
 Otomatikleştirilmiş test araçları tarafından iki düğme denetim görünüm ağaçtaki ayırt emin olmak için Ata `SmallIncrement` veya `SmallDecrement``AutomationId` uygun şekilde. Bazı uygulamalar için ilişkili düzenleme denetimi değer değiştirici denetim eşi olabilir.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon özellikleri  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , değer veya tanımı değer değiştirici denetimlere özellikle ilgili özellikler. Daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri, görmek [istemciler için UI Otomasyon özellikleri](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Özelliği|Değer|Notlar|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlarına bakın.|Bu özelliğin değeri bir uygulamadaki tüm denetimler arasında benzersiz olması gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlarına bakın.|Tam denetimi içeren en dıştaki dikdörtgen.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Notlarına bakın.|Değer değiştirici denetim tıklanabilir noktası odağı denetimi Düzenle bölümüne verir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Notlarına bakın.|Klavye odağı denetimi alamıyorsa, bu özelliği desteklemelidir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlarına bakın.|Değer değiştirici denetim genellikle bir statik metin etiketinden adını alır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Notlarına bakın.|Değer değiştirici denetim statik metin etiketine sahip.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Değer Değiştirici|Bu değer tüm UI çerçeveler için aynıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"değiştiricisi"|Değer değiştirici denetim türü için karşılık gelen yerelleştirilmiş dize.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Doğru|Değer değiştirici denetim her zaman içerik olmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Doğru|Değer değiştirici denetim her zaman bir denetim olmalıdır.|  
  
<a name="Required_UI_Automation_Control_Patterns_and_Properties"></a>   
## <a name="required-ui-automation-control-patterns-and-properties"></a>UI Otomasyon denetim düzenleri ve özellikleri gerekli  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] denetim düzenleri değer değiştirici denetim tarafından desteklenmesi için gerekli. Denetim desenleri hakkında daha fazla bilgi için bkz: [UI Otomasyon denetim düzenlerine genel bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Denetim düzeni/deseni özelliği|Destek/değer|Notlar|  
|---------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Bağlıdır|Seçilecek öğeleri listesine sahip değer değiştirici denetim bu desenin desteklenmesi gerekir.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|False|Değer değiştirici denetimleri her zaman tek seçim kapsayıcılardır.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Bağlıdır|Sayısal aralığı değiştiricisi denetimler bu deseni destekleyebilir.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Bağlıdır|Seçenekler veya numaraları ayrık bir dizi span değiştiricisi denetimler bu deseni destekleyebilir.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyon olayları  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayları tüm değiştiricisi denetimleri tarafından desteklenmesi gerekir. Olaylar hakkında daha fazla bilgi için bkz: [UI Otomasyonu olaylarına genel bakış](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Olay|Destek|Notlar|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Bağlıdır|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>özellik değişti olayı.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>özellik değişti olayı.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>özellik değişti olayı.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty>özellik değişti olayı.|Bağlıdır|Yok.|  
|<xref:System.Windows.Automation.RangeValuePatternIdentifiers.ValueProperty>özellik değişti olayı.|Bağlıdır|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|Yok.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Automation.ControlType.Spinner>  
 [UI Otomasyonu Denetim Türlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [UI Otomasyonuna Genel Bakış](../../../docs/framework/ui-automation/ui-automation-overview.md)
