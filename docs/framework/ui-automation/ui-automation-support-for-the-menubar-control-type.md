---
title: MenuBar Denetim Türü için UI Otomasyon Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Menu Bar control type
- control types, Menu Bar
- Menu Bar control type
ms.assetid: c1202b21-c1f0-4560-853c-7b99bd73ad97
ms.openlocfilehash: a6727b298c6289297fe049ffa4e64623bc9b711a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76778452"
---
# <a name="ui-automation-support-for-the-menubar-control-type"></a>MenuBar Denetim Türü için UI Otomasyon Desteği
> [!NOTE]
> Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu, <xref:System.Windows.Automation.ControlType.MenuBar> denetim türü için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] desteği hakkında bilgi sağlar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], denetim türü, bir denetimin <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> özelliğini kullanmak için karşılaması gereken koşullar kümesidir. Koşullar, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısına yönelik özel yönergeler, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerleri ve Denetim desenleri içerir.  
  
 Menü çubuğu denetimleri, menü çubuğu denetim türünü uygulayan denetimlerin bir örneğidir. Menü çubukları, kullanıcıların bir uygulamada içerilen komutları ve seçenekleri etkinleştirmesi için bir yol sağlar.  
  
 Aşağıdaki bölümler, menü çubuğu denetim türü için gerekli [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısını, özellikleri, denetim desenlerini ve olayları tanımlar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gereksinimleri, [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], Win32 veya Windows Forms bakılmaksızın tüm liste denetimlerine uygulanır.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyonu ağaç yapısı  
 Aşağıdaki tabloda, denetim görünümü ve menü çubuğu denetimleriyle ilgili [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacının içerik görünümü gösterilmektedir ve her görünümde nelerin yer aldığı açıklanmaktadır. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı hakkında daha fazla bilgi için bkz. [UI Otomasyon ağacına genel bakış](ui-automation-tree-overview.md).  
  
|Denetim görünümü|İçerik görünümü|  
|------------------|------------------|  
|Menü<br /><br /> -MenuItem (1 veya daha fazla)<br />-Diğer denetimler (0 veya çok)|Menü<br /><br /> -MenuItem (1 veya daha fazla)<br />-Diğer denetimler (0 veya çok)|  
  
 Menü çubuğu denetimleri, yapısı içinde denetimleri ve Birleşik giriş kutularını düzenleme gibi diğer denetimleri içerebilir. Bu ek denetimler, denetim ve içerik görünümlerinde yukarıda listelenen "diğer denetimlere" karşılık gelir.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon Özellikleri  
 Aşağıdaki tabloda, değeri veya tanımı özellikle menü çubuğu denetimleriyle ilgili olan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri listelenmektedir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri hakkında daha fazla bilgi için bkz. [istemciler Için UI Otomasyon özellikleri](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özelliği|Değer|Notlar|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlara bakın.|Bu özelliğin açığa çıkarılan değeri, içinde yer alan tüm denetimleri içermelidir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlara bakın.|Bir uygulamada birden fazla menü çubuğu yoksa, menü çubuğu denetimine bir ad gerekmez. Bir uygulamada birden fazla menü çubuğu varsa, bu özellik, "biçimlendirme" veya "anahat oluşturma" gibi ayrım adlarını açığa çıkarmak için kullanılmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Menü çubuğu denetimlerinin hiç bir etiketi yoktur.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Menü|Bu değer tüm UI çerçeveleri için aynıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"menü çubuğu"|Menü çubuğu denetim türüne karşılık gelen yerelleştirilmiş dize.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Doğru|Menü çubuğu denetimi her zaman [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacının içerik görünümüne dahil edilmiştir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Doğru|Menü çubuğu denetimi her zaman [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacının denetim görünümüne dahil edilir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>|Notlara bakın.|Bu özelliğin değeri, denetimin ekranda görüntülenebilir olup olmamasına bağlıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.OrientationProperty>|Şekline|Bu özellik menü çubuğu denetiminin yatay mı yoksa dikey mi olduğunu gösterir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Doğru|Menü çubuğu denetimleri, içerdikleri denetimler klavye odağı alabildiğinden klavye odaklanıyor.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|Notlara bakın.|Bir menü çubuğu denetimi için yardım metninin gerekli olduğu senaryo yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AcceleratorKeyProperty>|`Null`|Menü çubuklarında hiç kısayol tuşu yoktur.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AccessKeyProperty>|ALTERNATIF|ALT tuşuna basmak her zaman uygulamanın içindeki menü çubuğuna odaklanmalıdır.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Gerekli UI Otomasyonu Denetim desenleri  
 Aşağıdaki tabloda, menü çubuğu denetimleri tarafından desteklenmesi gereken [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Denetim desenleri listelenmektedir. Denetim desenleri hakkında daha fazla bilgi için bkz. [UI Otomasyonu Denetim desenlerine genel bakış](ui-automation-control-patterns-overview.md).  
  
|Denetim deseninin|Destek|Notlar|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Şekline|Denetim genişletilebilir veya daraltılabilse <xref:System.Windows.Automation.Provider.IExpandCollapseProvider>uygulayın.|  
|<xref:System.Windows.Automation.Provider.IDockProvider>|Şekline|Denetim, ekranın farklı bölümlerine sabitlenebilir <xref:System.Windows.Automation.Provider.IDockProvider>uygulayın.|  
|<xref:System.Windows.Automation.Provider.ITransformProvider>|Şekline|Denetim yeniden boyutlandırılabileceği, döndürülerek veya taşınmışsa <xref:System.Windows.Automation.Provider.ITransformProvider>uygulaması gerekir.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyon olayları  
 Aşağıdaki tabloda, tüm menü çubuğu denetimleri tarafından desteklenmesi gereken [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayları listelenmektedir. Olaylar hakkında daha fazla bilgi için bkz. [UI Otomasyonu olaylarına genel bakış](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayı|Destek/değer|Notlar|  
|---------------------------------------------------------------------------------|--------------------|-----------|  
|özellik değişti olayı <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>.|Gerekli|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>.|Gerekli|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>.|Gerekli|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty>.|Şekline|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|Yok.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.ControlType.MenuBar>
- [UI Otomasyonu Denetim Türlerine Genel Bakış](ui-automation-control-types-overview.md)
- [UI Otomasyonuna Genel Bakış](ui-automation-overview.md)
