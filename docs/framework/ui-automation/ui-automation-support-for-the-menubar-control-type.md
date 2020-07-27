---
title: MenuBar Denetim Türü için UI Otomasyon Desteği
description: Menü çubuğu denetim türü için UI Otomasyonu desteği hakkında bilgi alın. Gerekli ağaç yapısını, özellikleri, denetim desenlerini ve olayları öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Menu Bar control type
- control types, Menu Bar
- Menu Bar control type
ms.assetid: c1202b21-c1f0-4560-853c-7b99bd73ad97
ms.openlocfilehash: 923f8d9dc62a7175b2bcfe2b0839b1435bf83132
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166035"
---
# <a name="ui-automation-support-for-the-menubar-control-type"></a>MenuBar Denetim Türü için UI Otomasyon Desteği
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konuda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Denetim türü için destek hakkında bilgi verilmektedir <xref:System.Windows.Automation.ControlType.MenuBar> . ' De [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , bir denetim türü, özelliği kullanmak için bir denetimin uyması gereken koşullar kümesidir <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> . Koşullar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , ağaç yapısı, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerleri ve Denetim desenleri için özel kurallar içerir.  
  
 Menü çubuğu denetimleri, menü çubuğu denetim türünü uygulayan denetimlerin bir örneğidir. Menü çubukları, kullanıcıların bir uygulamada içerilen komutları ve seçenekleri etkinleştirmesi için bir yol sağlar.  
  
 Aşağıdaki bölümler, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] menü çubuğu denetim türü için gerekli ağaç yapısını, özellikleri, denetim desenlerini ve olayları tanımlar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Gereksinimler, Win32 veya Windows Forms tüm liste denetimleri için geçerlidir [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] .  
  
<a name="Required_UI_Automation_Tree_Structure"></a>
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyonu ağaç yapısı  
 Aşağıdaki tabloda, denetim görünümü ve [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] menü çubuğu denetimleriyle ilgili ağacın içerik görünümü gösterilmektedir ve her görünümde nelerin yer aldığı açıklanmaktadır. Ağaç hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [UI Otomasyon ağacına genel bakış](ui-automation-tree-overview.md).  
  
|Denetim görünümü|İçerik görünümü|  
|------------------|------------------|  
|Menü<br /><br /> -MenuItem (1 veya daha fazla)<br />-Diğer denetimler (0 veya çok)|Menü<br /><br /> -MenuItem (1 veya daha fazla)<br />-Diğer denetimler (0 veya çok)|  
  
 Menü çubuğu denetimleri, yapısı içinde denetimleri ve Birleşik giriş kutularını düzenleme gibi diğer denetimleri içerebilir. Bu ek denetimler, denetim ve içerik görünümlerinde yukarıda listelenen "diğer denetimlere" karşılık gelir.  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon Özellikleri  
 Aşağıdaki tabloda, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] değeri veya tanımı özellikle menü çubuğu denetimleriyle ilgili olan özellikler listelenmiştir. Özellikler hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [Istemciler Için UI Otomasyon özellikleri](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Özelliði|Değer|Notlar|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlara bakın.|Bu özelliğin açığa çıkarılan değeri, içinde yer alan tüm denetimleri içermelidir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlara bakın.|Bir uygulamada birden fazla menü çubuğu yoksa, menü çubuğu denetimine bir ad gerekmez. Bir uygulamada birden fazla menü çubuğu varsa, bu özellik, "biçimlendirme" veya "anahat oluşturma" gibi ayrım adlarını açığa çıkarmak için kullanılmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Menü çubuğu denetimlerinin hiç bir etiketi yoktur.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Menü|Bu değer tüm UI çerçeveleri için aynıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"menü çubuğu"|Menü çubuğu denetim türüne karşılık gelen yerelleştirilmiş dize.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Doğru|Menü çubuğu denetimi her zaman ağacın içerik görünümüne dahil edilmiştir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Doğru|Menü çubuğu denetimi her zaman ağacın denetim görünümüne dahil edilir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>|Notlara bakın.|Bu özelliğin değeri, denetimin ekranda görüntülenebilir olup olmamasına bağlıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.OrientationProperty>|Şekline|Bu özellik menü çubuğu denetiminin yatay mı yoksa dikey mi olduğunu gösterir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Doğru|Menü çubuğu denetimleri, içerdikleri denetimler klavye odağı alabildiğinden klavye odaklanıyor.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|Notlara bakın.|Bir menü çubuğu denetimi için yardım metninin gerekli olduğu senaryo yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AcceleratorKeyProperty>|`Null`|Menü çubuklarında hiç kısayol tuşu yoktur.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AccessKeyProperty>|ALTERNATIF|ALT tuşuna basmak her zaman uygulamanın içindeki menü çubuğuna odaklanmalıdır.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>
## <a name="required-ui-automation-control-patterns"></a>Gerekli UI Otomasyonu Denetim desenleri  
 Aşağıdaki tabloda, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] menü çubuğu denetimleri tarafından desteklenmesi için gereken denetim desenleri listelenmektedir. Denetim desenleri hakkında daha fazla bilgi için bkz. [UI Otomasyonu Denetim desenlerine genel bakış](ui-automation-control-patterns-overview.md).  
  
|Denetim deseninin|Destek|Notlar|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Şekline|Denetim genişletilebilir veya daraltılabilse, uygulayın <xref:System.Windows.Automation.Provider.IExpandCollapseProvider> .|  
|<xref:System.Windows.Automation.Provider.IDockProvider>|Şekline|Denetim, ekranın farklı bölümlerine sabitlenebilir ise, uygulayın <xref:System.Windows.Automation.Provider.IDockProvider> .|  
|<xref:System.Windows.Automation.Provider.ITransformProvider>|Şekline|Denetim yeniden boyutlandırılabileceği, döndürülerek veya taşınırsa uygulamanız gerekir <xref:System.Windows.Automation.Provider.ITransformProvider> .|  
  
<a name="Required_UI_Automation_Events"></a>
## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyon olayları  
 Aşağıdaki tabloda, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tüm menü çubuğu denetimleri tarafından desteklenmesi gereken olaylar listelenmektedir. Olaylar hakkında daha fazla bilgi için bkz. [UI Otomasyonu olaylarına genel bakış](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Olay|Destek/değer|Notlar|  
|---------------------------------------------------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>özellik değişti olayı.|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>özellik değişti olayı.|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>özellik değişti olayı.|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty>özellik değişti olayı.|Şekline|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|Hiçbiri|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.ControlType.MenuBar>
- [UI Otomasyon Denetim Türlerine Genel Bakış](ui-automation-control-types-overview.md)
- [UI Otomasyonuna Genel Bakış](ui-automation-overview.md)
