---
title: Değer Değiştirici Denetim Türü İçin UI Otomasyon Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Spinner control type
- Spinner control type
- control types, Spinner
ms.assetid: 3a29d185-65d8-42e3-bcc3-7f43e96f40c5
ms.openlocfilehash: 6bd080a2e95952bc2d11bd3c3bc9eaa28e72684a
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74801805"
---
# <a name="ui-automation-support-for-the-spinner-control-type"></a>Değer Değiştirici Denetim Türü İçin UI Otomasyon Desteği
> [!NOTE]
> Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu, değer değiştirici denetim türü için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] desteği hakkında bilgi sağlar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], denetim türü, bir denetimin <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> özelliğini kullanmak için karşılaması gereken koşullar kümesidir. Koşullar, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısına yönelik özel yönergeler, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerleri ve Denetim desenleri içerir.  
  
 Değer değiştirici denetimleri, öğelerin etki alanından veya bir dizi sayıdan seçim yapmak için kullanılır.  
  
 Aşağıdaki bölümler, değer değiştirici denetim türü için gerekli [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısını, özellikleri, denetim desenlerini ve olayları tanımlar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gereksinimleri, [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]veya [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]bakılmaksızın tüm değer değiştirici denetimleri için geçerlidir.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyonu ağaç yapısı  
 Aşağıdaki tabloda, Aralık değerini, değer ve seçim denetimi düzenlerini desteklediklerinde ve her görünümde nelerin yer abileceklerini açıklayan, değer değiştirici denetimlerine ait [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacının denetim görünümü ve içerik görünümü gösterilmektedir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı hakkında daha fazla bilgi için bkz. [UI Otomasyon ağacına genel bakış](ui-automation-tree-overview.md).  
  
 **Aralık değeri veya değer denetim stili**  
  
|Denetim görünümü|İçerik görünümü|  
|------------------|------------------|  
|Değer Değiştirici<br /><br /> -Düzenle (0 veya 1)<br />-Düğme (2)|Değer Değiştirici|  
  
 **Seçim denetimi KALIBI**  
  
|Denetim görünümü|İçerik görünümü|  
|------------------|------------------|  
|Değer Değiştirici<br /><br /> -Düzenle (0 veya 1)<br />-Düğme (2)<br />-Liste öğesi (0 veya daha fazla)|Değer Değiştirici<br /><br /> -ListItem (0 veya daha fazla)|  
  
 Denetim görünümü alt ağacındaki iki düğmenin otomatik test araçlarıyla ayırt edilebilir olmasını sağlamak için `SmallIncrement` veya `SmallDecrement` `AutomationId` uygun şekilde atayın. Bazı uygulamalarda, ilişkili düzenleme denetimi değer değiştirici denetiminin bir eşi olabilir.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon Özellikleri  
 Aşağıdaki tabloda, değeri veya tanımı özellikle değer değiştirici denetimleriyle ilgili olan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri listelenmektedir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri hakkında daha fazla bilgi için bkz. [istemciler Için UI Otomasyon özellikleri](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özelliği|Değer|Notlar|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlara bakın.|Bu özelliğin değerinin bir uygulamadaki tüm denetimlerde benzersiz olması gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlara bakın.|Tüm denetimi içeren en dıştaki dikdörtgen.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Notlara bakın.|Değer değiştirici denetiminin tıklatılabilir noktası odağı denetimin düzenleme bölümüne verir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Notlara bakın.|Denetim, klavye odağı alamıyorsa, bu özelliği desteklemesi gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlara bakın.|Değer değiştirici denetimi genellikle adını statik metin etiketinden alır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Notlara bakın.|Değer değiştirici denetimlerinin statik metin etiketi vardır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Değer Değiştirici|Bu değer tüm UI çerçeveleri için aynıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|dönüş|Değer değiştirici denetim türüne karşılık gelen yerelleştirilmiş dize.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Doğru|Değer değiştirici denetimi her zaman içerik olmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Doğru|Değer değiştirici denetimi her zaman bir denetim olmalıdır.|  
  
<a name="Required_UI_Automation_Control_Patterns_and_Properties"></a>   
## <a name="required-ui-automation-control-patterns-and-properties"></a>Gerekli UI Otomasyonu Denetim desenleri ve özellikleri  
 Aşağıdaki tabloda, değer değiştirici denetimleri tarafından desteklenmesi gereken [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Denetim desenleri listelenmektedir. Denetim desenleri hakkında daha fazla bilgi için bkz. [UI Otomasyonu Denetim desenlerine genel bakış](ui-automation-control-patterns-overview.md).  
  
|Denetim deseninin/deseninin özelliği|Destek/değer|Notlar|  
|---------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Şekline|Seçilecek öğe listesi olan değer değiştirici denetimleri bu kalıbı desteklemelidir.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|False|Değer değiştirici denetimleri her zaman tek seçim kapsayıcılarıdır.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Şekline|Değer değiştirici denetimleri, bir sayısal aralığı yayan bu kalıbı destekleyebilir.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Şekline|Değer değiştirici bir seçenek veya sayı kümesini kapsayan değiştirici denetimleri bu kalıbı destekleyebilir.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyon olayları  
 Aşağıdaki tabloda, tüm değer değiştirici denetimleri tarafından desteklenmesi gereken [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayları listelenmektedir. Olaylar hakkında daha fazla bilgi için bkz. [UI Otomasyonu olaylarına genel bakış](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayı|Destek|Notlar|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Şekline|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>.|Gerekli|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>.|Gerekli|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>.|Gerekli|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty>.|Şekline|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.RangeValuePatternIdentifiers.ValueProperty>.|Şekline|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|Yok.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.ControlType.Spinner>
- [UI Otomasyonu Denetim Türlerine Genel Bakış](ui-automation-control-types-overview.md)
- [UI Otomasyonuna Genel Bakış](ui-automation-overview.md)
