---
title: Tablo Denetim Türü İçin UI Otomasyon Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- TableControl type
- control types, Table
- UI Automation, Table control type
ms.assetid: 9050dde5-6469-4c83-abb7-f861c24ff985
ms.openlocfilehash: c66e5dd9b49f28d60fdec3563464bcb3a2fa8271
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793993"
---
# <a name="ui-automation-support-for-the-table-control-type"></a>Tablo Denetim Türü İçin UI Otomasyon Desteği
> [!NOTE]
> Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konuda tablo Denetim türü için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] desteği hakkında bilgi verilmektedir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], denetim türü, bir denetimin <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> özelliğini kullanmak için karşılaması gereken koşullar kümesidir. Koşullar, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısına yönelik özel yönergeler, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerleri ve Denetim desenleri içerir.  
  
 Tablo denetimleri, metin satırları ve sütunları ve isteğe bağlı olarak satır üst bilgileri ve sütun üst bilgileri içerir.  
  
 Aşağıdaki bölümler tablo Denetim türü için gerekli [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısını, özellikleri, denetim desenlerini ve olayları tanımlar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gereksinimler, [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], Win32 veya Windows Forms gibi tüm tablo denetimleri için geçerlidir.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyonu ağaç yapısı  
 Aşağıdaki tabloda, tablo denetimleriyle ilgili [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacının denetim görünümü ve içerik görünümü gösterilmektedir ve her görünümde nelerin yer aldığı açıklanmaktadır. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı hakkında daha fazla bilgi için bkz. [UI Otomasyon ağacına genel bakış](ui-automation-tree-overview.md).  
  
|Denetim görünümü|İçerik görünümü|  
|------------------|------------------|  
|Tablo<br /><br /> -Üst bilgi (0 veya 1)<br />-Metin (0 veya 1)<br />-Çeşitli denetimler (0 veya daha fazla)|Tablo<br /><br /> -Metin (0 veya daha fazla)<br />-Çeşitli denetimler (0 veya daha fazla)|  
  
 Bir tablo denetiminde satır veya sütun başlıkları varsa, UI Otomasyon ağacının denetim görünümünde gösterilmeleri gerekir. Tablemodel kullanılarak erişilebildiğinden Içerik görünümü bu bilgileri açığa çıkarmak zorunda değildir.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon Özellikleri  
 Aşağıdaki tabloda, değeri veya tanımı özellikle tablo denetimleriyle ilgili olan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri listelenmektedir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri hakkında daha fazla bilgi için bkz. [istemciler Için UI Otomasyon özellikleri](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özelliği|Değer|Notlar|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlara bakın.|Bu özelliğin değerinin bir uygulamadaki tüm denetimlerde benzersiz olması gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlara bakın.|Tüm denetimi içeren en dıştaki dikdörtgen.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Notlara bakın.|Sınırlayıcı bir dikdörtgen varsa desteklenir. Sınırlayıcı dikdörtgenin içindeki her nokta tıklatılabilir ise ve özelleştirilmiş isabet testi gerçekleştirirseniz ve ardından tıklatılabilir bir nokta sağlayabilirsiniz.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Notlara bakın.|Denetim, klavye odağı alamıyorsa, bu özelliği desteklemesi gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlara bakın.|Tablo denetimi genellikle adını statik bir metin etiketinden alır. Statik metin etiketi yoksa, tablonun amacını açıklamak için her zaman kullanılabilir olması gereken bir ad özelliği atamanız gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Notlara bakın.|Statik bir metin etiketi varsa, bu özellik denetimin Automation öğesine bir başvuru göstermelidir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Tablo|Bu değer tüm UI çerçeveleri için aynıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|tablosundan|Tablo denetim türüne karşılık gelen yerelleştirilmiş dize.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|Notlara bakın.|Tablonun amacı hakkında daha fazla ayrıntı, NameProperty öğesine erişerek yeterince açıklanmadığı durumlarda bu özellik aracılığıyla gösterilmelidir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Doğru|Tablo denetimi her zaman içerik olmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Doğru|Tablo denetimi her zaman bir denetim olmalıdır.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Gerekli UI Otomasyonu Denetim desenleri  
 Aşağıdaki tabloda tablo denetimleri tarafından desteklenmesi gereken [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Denetim desenleri listelenmektedir. Denetim desenleri hakkında daha fazla bilgi için bkz. [UI Otomasyonu Denetim desenlerine genel bakış](ui-automation-control-patterns-overview.md).  
  
|Denetim deseninin|Destek|Notlar|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider>|Evet|Tablo denetimi her zaman bu denetim modelini destekler çünkü içerdiği öğelerin bir kılavuzda sunulan verileri vardır.|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider>|Evet (alt nesnelerle gereklidir)|Bir tablonun iç nesneleri hem GridItem hem de TableItem denetim düzenlerini desteklemelidir. Tablo başka bir tablonun parçası değilse tablonun kendisi GridItem veya TableItem denetim düzenlerini desteklemezler.|  
|<xref:System.Windows.Automation.Provider.ITableProvider>|Evet|Tablo denetimi her zaman içerikle ilişkili üst bilgilerin yer aldığı özelliğe sahiptir.|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider>|Evet (alt nesnelerle gereklidir)|Bir tablonun iç nesneleri hem GridItem hem de TableItem denetim düzenlerini desteklemelidir. Tablo başka bir tablonun parçası değilse tablonun kendisi GridItem veya TableItem denetim düzenlerini desteklemezler.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyon olayları  
 Aşağıdaki tabloda tüm tablo denetimleri tarafından desteklenmesi gereken [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayları listelenmektedir. Olaylar hakkında daha fazla bilgi için bkz. [UI Otomasyonu olaylarına genel bakış](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayı|Destek|Notlar|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|özellik değişti olayı <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>.|Gerekli|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>.|Gerekli|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|Yok.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.ControlType.Table>
- [UI Otomasyonu Denetim Türlerine Genel Bakış](ui-automation-control-types-overview.md)
- [UI Otomasyonuna Genel Bakış](ui-automation-overview.md)
