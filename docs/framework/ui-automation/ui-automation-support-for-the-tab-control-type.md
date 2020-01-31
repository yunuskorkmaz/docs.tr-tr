---
title: Sekme Denetim Türü İçin UI Otomasyon Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- TabControl type
- UI Automation, Tab control type
- control types, Tab
ms.assetid: f8be2732-836d-4e4d-85e2-73aa39479bf4
ms.openlocfilehash: 6bbb6487db915d4544bdb7f0b584301b3b759bbe
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793999"
---
# <a name="ui-automation-support-for-the-tab-control-type"></a>Sekme Denetim Türü İçin UI Otomasyon Desteği
> [!NOTE]
> Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu, sekme denetim türü için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] desteği hakkında bilgi sağlar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], denetim türü, bir denetimin <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> özelliğini kullanmak için karşılaması gereken koşullar kümesidir. Koşullar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısına yönelik belirli yönergeleri, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerlerini ve [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]içerir. Denetim desenleri.  
  
 Sekme denetimi bir not defterindeki bölücülerin veya dosya dolabdaki etiketlerin benzerdir. Bir uygulama bir sekme denetimi kullanarak bir pencere veya iletişim kutusunun aynı alanı için birden çok sayfa tanımlayabilir.  
  
 Aşağıdaki bölümler sekme denetim türü için gerekli [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısını, özellikleri, denetim desenlerini ve olayları tanımlar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gereksinimleri, [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], Win32 veya Windows Forms gibi tüm sekme denetimleri için geçerlidir.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyonu ağaç yapısı  
 Aşağıdaki tabloda, sekme denetimleriyle ilgili [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacının denetim görünümü ve içerik görünümü gösterilmektedir ve her görünümde nelerin yer aldığı açıklanmaktadır. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı hakkında daha fazla bilgi için bkz. [UI Otomasyon ağacına genel bakış](ui-automation-tree-overview.md).  
  
|Denetim görünümü|İçerik görünümü|  
|------------------|------------------|  
|Tab<br /><br /> <ul><li>TabItem (1 veya daha fazla)</li><li>Kaydırma çubuğu (0 veya 1)<br /><br /> <ul><li>Düğme (0 veya 2)</li></ul></li></ul>|Tab<br /><br /> -TabItem (1 veya daha fazla)|  
  
 Sekme denetimlerinin sekme öğesi denetim türüne göre alt [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] öğeleri vardır. Sekme öğeleri gruplandırılırken (örneğin, Microsoft Office 2007 uygulamalarında olduğu gibi), aşağıdaki ağaç yapısında gösterildiği gibi Tab denetim türü gruplanmış sekme öğeleri için gruplar denetim türlerini de barındırabilir.  
  
|Denetim görünümü|İçerik görünümü|  
|------------------|------------------|  
|Tab<br /><br /> <ul><li>TabItem (1 veya daha fazla)</li><li>Grup (0 veya daha fazla)<br /><br /> <ul><li>TabItem (0 veya daha fazla)</li></ul></li><li>Kaydırma çubuğu (0 veya daha fazla)<br /><br /> <ul><li>Düğme (0 veya 2)</li></ul></li></ul>|Tab<br /><br /> <ul><li>TabItem (1 veya daha fazla)</li><li>Grup (0 veya daha fazla)<br /><br /> <ul><li>TabItem (0 veya daha fazla)</li></ul></li></ul>|  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon Özellikleri  
 Aşağıdaki tabloda, değeri veya tanımı özellikle sekme denetim türüyle ilgili olan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri listelenmektedir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri hakkında daha fazla bilgi için bkz. [istemciler Için UI Otomasyon özellikleri](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özelliği|Değer|Notlar|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlara bakın.|Bu özelliğin değerinin bir uygulamadaki tüm denetimlerde benzersiz olması gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlara bakın.|Tüm denetimi içeren en dıştaki dikdörtgen.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Notlara bakın.|Denetim, klavye odağı alamıyorsa, bu özelliği desteklemesi gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlara bakın.|Sekme denetimi nadiren bir ad özelliği gerektirir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Hayır|Sekme denetiminin tıklatılabilir bir noktası yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Notlara bakın.|Sekme denetimleri genellikle bu özellik aracılığıyla gösterilen statik bir metin etiketine sahiptir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Tab|Bu değer tüm UI çerçeveleri için aynıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|sekmesinde|Sekme denetim türüne karşılık gelen yerelleştirilmiş dize.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Doğru|Sekme Denetim türü klavye odağını alabilmelidir. Genellikle, bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] istemci bir sekme denetiminde SetFocus çağırır ve öğelerinden biri klavye odağını Sekme denetimine iletir. Bazı sekme kapsayıcıları, öğelerinden birine odaklanmadan odağı almak mümkündür.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Doğru|Sekme denetimi her zaman [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacının içerik görünümüne dahil edilir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Doğru|Sekme denetimi her zaman [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacının denetim görünümüne dahil edilir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.OrientationProperty>|Notlara bakın.|Sekme denetimi her zaman yatay veya dikey olarak konumlandırılıp yerleştirilmeyeceğini göstermelidir.|  
  
<a name="Required_UI_Automation_Control_Patterns_and_Properties"></a>   
## <a name="required-ui-automation-control-patterns-and-properties"></a>Gerekli UI Otomasyonu Denetim desenleri ve özellikleri  
 Aşağıdaki tabloda, tüm sekme denetimleri tarafından desteklenmesi gereken [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Denetim desenleri listelenmektedir. Denetim desenleri hakkında daha fazla bilgi için bkz. [UI Otomasyonu Denetim desenlerine genel bakış](ui-automation-control-patterns-overview.md).  
  
|Denetim deseninin/deseninin özelliği|Destek/değer|Notlar|  
|---------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Evet|Tüm sekme denetimleri seçim düzenlerini desteklemelidir.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Doğru|Sekme denetimleri her zaman bir seçim yapılmasını gerektirir.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|False|Sekme denetimleri her zaman tek seçim kapsayıcılarıdır.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Şekline|Tab denetiminde, kaydırma deseninin, bir dizi sekme öğesinin kaydırılacağını sağlayan pencere öğeleri olması gerekir.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyon olayları  
 Aşağıdaki tabloda, tüm sekme denetimleri tarafından desteklenmesi gereken [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayları listelenmektedir. Olaylar hakkında daha fazla bilgi için bkz. [UI Otomasyonu olaylarına genel bakış](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayı|Destek|Notlar|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|özellik değişti olayı <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>.|Gerekli|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>.|Gerekli|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>.|Gerekli|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>.|Şekline|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty>.|Şekline|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>.|Şekline|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty>.|Şekline|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty>.|Şekline|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty>.|Şekline|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|Yok.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.ControlType.Tab>
- [UI Otomasyonu Denetim Türlerine Genel Bakış](ui-automation-control-types-overview.md)
- [UI Otomasyonuna Genel Bakış](ui-automation-overview.md)
