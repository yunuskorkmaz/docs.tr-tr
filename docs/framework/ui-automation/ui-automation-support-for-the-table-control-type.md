---
title: Tablo Denetim Türü İçin UI Otomasyon Desteği
description: Tablo denetim türü için UI Otomasyonu desteği hakkında bilgi alın. Gerekli ağaç yapısını, özellikleri, denetim desenlerini ve olayları öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- TableControl type
- control types, Table
- UI Automation, Table control type
ms.assetid: 9050dde5-6469-4c83-abb7-f861c24ff985
ms.openlocfilehash: 13790d601b370f60a0e9a998effcbf4744b63712
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163621"
---
# <a name="ui-automation-support-for-the-table-control-type"></a>Tablo Denetim Türü İçin UI Otomasyon Desteği
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konuda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Tablo denetim türü için destek hakkında bilgi sağlanır. ' De [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , bir denetim türü, özelliği kullanmak için bir denetimin uyması gereken koşullar kümesidir <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> . Koşullar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , ağaç yapısı, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerleri ve Denetim desenleri için özel kurallar içerir.  
  
 Tablo denetimleri, metin satırları ve sütunları ve isteğe bağlı olarak satır üst bilgileri ve sütun üst bilgileri içerir.  
  
 Aşağıdaki bölümler [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Tablo denetim türü için gerekli ağaç yapısını, özellikleri, denetim desenlerini ve olayları tanımlar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Gereksinimler, Win32 veya Windows Forms tüm tablo denetimleri için geçerlidir [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] .  
  
<a name="Required_UI_Automation_Tree_Structure"></a>
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyonu ağaç yapısı  
 Aşağıdaki tabloda, tablo denetimleriyle ilgili ağacın denetim görünümü ve içerik görünümü gösterilmektedir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ve her görünümde nelerin yer aldığı açıklanmaktadır. Ağaç hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [UI Otomasyon ağacına genel bakış](ui-automation-tree-overview.md).  
  
|Denetim görünümü|İçerik görünümü|  
|------------------|------------------|  
|Tablo<br /><br /> -Üst bilgi (0 veya 1)<br />-Metin (0 veya 1)<br />-Çeşitli denetimler (0 veya daha fazla)|Tablo<br /><br /> -Metin (0 veya daha fazla)<br />-Çeşitli denetimler (0 veya daha fazla)|  
  
 Bir tablo denetiminde satır veya sütun başlıkları varsa, UI Otomasyon ağacının denetim görünümünde gösterilmeleri gerekir. Tablemodel kullanılarak erişilebildiğinden Içerik görünümü bu bilgileri açığa çıkarmak zorunda değildir.  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon Özellikleri  
 Aşağıdaki tabloda, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] değeri veya tanımı özellikle tablo denetimleriyle ilgili olan özellikler listelenmiştir. Özellikler hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [Istemciler Için UI Otomasyon özellikleri](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Özelliði|Değer|Notlar|  
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
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tablo denetimleri tarafından desteklenmesi için gereken denetim desenleri listelenmektedir. Denetim desenleri hakkında daha fazla bilgi için bkz. [UI Otomasyonu Denetim desenlerine genel bakış](ui-automation-control-patterns-overview.md).  
  
|Denetim deseninin|Destek|Notlar|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider>|Yes|Tablo denetimi her zaman bu denetim modelini destekler çünkü içerdiği öğelerin bir kılavuzda sunulan verileri vardır.|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider>|Evet (alt nesnelerle gereklidir)|Bir tablonun iç nesneleri hem GridItem hem de TableItem denetim düzenlerini desteklemelidir. Tablo başka bir tablonun parçası değilse tablonun kendisi GridItem veya TableItem denetim düzenlerini desteklemezler.|  
|<xref:System.Windows.Automation.Provider.ITableProvider>|Yes|Tablo denetimi her zaman içerikle ilişkili üst bilgilerin yer aldığı özelliğe sahiptir.|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider>|Evet (alt nesnelerle gereklidir)|Bir tablonun iç nesneleri hem GridItem hem de TableItem denetim düzenlerini desteklemelidir. Tablo başka bir tablonun parçası değilse tablonun kendisi GridItem veya TableItem denetim düzenlerini desteklemezler.|  
  
<a name="Required_UI_Automation_Events"></a>
## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyon olayları  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tüm tablo denetimleri tarafından desteklenmesi gereken olaylar listelenmektedir. Olaylar hakkında daha fazla bilgi için bkz. [UI Otomasyonu olaylarına genel bakış](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Olay|Destek|Notlar|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>özellik değişti olayı.|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>özellik değişti olayı.|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>özellik değişti olayı.|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|Hiçbiri|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.ControlType.Table>
- [UI Otomasyon Denetim Türlerine Genel Bakış](ui-automation-control-types-overview.md)
- [UI Otomasyonuna Genel Bakış](ui-automation-overview.md)
