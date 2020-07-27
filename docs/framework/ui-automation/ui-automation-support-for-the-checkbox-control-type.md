---
title: CheckBox Denetim Türü için UI Otomasyon Desteği
description: CheckBox denetim türü için UI Otomasyonu desteği hakkında bilgi alın. Gerekli ağaç yapısını, özellikleri ve denetim desenlerini öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- CheckBox control type
- control types, CheckBox
- UI Automation, CheckBox control type
ms.assetid: 9c2a0e70-3a39-4ba9-96ea-a7fe531fae9f
ms.openlocfilehash: 787642f34ab50a08bb2f525e6ff11443bb356d27
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167956"
---
# <a name="ui-automation-support-for-the-checkbox-control-type"></a>CheckBox Denetim Türü için UI Otomasyon Desteği
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] , CheckBox denetim türü için destek hakkında bilgi sağlar. ' De [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , bir denetim türü, özelliği kullanmak için bir denetimin uyması gereken koşullar kümesidir <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> . Koşullar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , ağaç yapısı, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerleri ve Denetim desenleri için özel kurallar içerir.  
  
 Onay kutusu, kullanıcıların bu durum boyunca geçiş yapmak için etkileşime girebileceği bir durumu belirtmek için kullanılan bir nesnedir. Onay kutuları, kullanıcıya bir ikili (Evet/Hayır), (açık/kapalı) veya üçüncül (açık, kapalı, belirsiz) seçeneğini sunar.  
  
 Aşağıdaki bölümler, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] CheckBox denetim türü için gerekli ağaç yapısını, özellikleri, denetim desenlerini ve olayları tanımlar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Gereksinimler, Win32 veya Windows Forms tüm onay kutusu denetimlerine uygulanır [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] .  
  
<a name="Required_UI_Automation_Tree_Structure"></a>
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyonu ağaç yapısı  
 Aşağıdaki tabloda, onay kutusu denetimleriyle ilgili ağacın denetim görünümü ve içerik görünümü gösterilmektedir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ve her görünümde nelerin yer aldığı açıklanmaktadır. Ağaç hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [UI Otomasyon ağacına genel bakış](ui-automation-tree-overview.md).  
  
|Denetim görünümü|İçerik görünümü|  
|------------------|------------------|  
|CheckBox|CheckBox|  
  
> [!NOTE]
> Onay kutularının denetim veya içerik görünümünde hiç alt öğesi yok. Denetimin alt öğeler içermesi gerekiyorsa bu, başka bir denetim türünün kullanılması gerektiğini gösterir.  
  
### <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon Özellikleri  
 Aşağıdaki tabloda, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] değeri veya tanımı özellikle onay kutusu denetimleriyle ilgili olan özellikler listelenmiştir. Özellikler hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [Istemciler Için UI Otomasyon özellikleri](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Özelliði|Değer|Notlar|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlara bakın.|Bu özelliğin değerinin bir uygulamadaki tüm denetimlerde benzersiz olması gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlara bakın.|Tüm denetimi içeren en dıştaki dikdörtgen.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Notlara bakın.|Sınırlayıcı bir dikdörtgen varsa desteklenir. Sınırlayıcı dikdörtgenin içindeki her nokta tıklatılabilir ise ve özelleştirilmiş isabet testi gerçekleştirirseniz ve ardından tıklatılabilir bir nokta sağlayabilirsiniz.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|CheckBox|Bu değer tüm UI çerçeveleri için aynıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Doğru|Bu özelliğin değeri her zaman doğru olmalıdır. Bu, onay kutusu denetiminin her zaman ağacın içerik görünümüne dahil olması gerektiği anlamına gelir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Doğru|Bu özelliğin değeri her zaman doğru olmalıdır. Bu, onay kutusu denetiminin her zaman ağacın denetim görünümüne dahil olması gerektiği anlamına gelir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Notlara bakın.|Denetim, klavye odağı alamıyorsa, bu özelliği desteklemesi gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Onay kutuları, kendi kendine etiketleme denetimleridir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"onay kutusu"|CheckBox denetim türüne karşılık gelen yerelleştirilmiş dize.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlara bakın.|Onay kutusu denetiminin özelliğinin değeri, `Name` geçiş durumunu tutan kutunun yanında görüntülenen metindir.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>
## <a name="required-ui-automation-control-patterns"></a>Gerekli UI Otomasyonu Denetim desenleri  
 Aşağıdaki tabloda, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tüm onay kutusu denetimleri tarafından desteklenmesi gereken denetim desenleri listelenmektedir. Denetim desenleri hakkında daha fazla bilgi için bkz. [UI Otomasyonu Denetim desenlerine genel bakış](ui-automation-control-patterns-overview.md).  
  
|Denetim deseninin|Destek|Notlar|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|Gerekli|Onay kutusunun iç durumları aracılığıyla programlı olarak kullanılmasına izin verir.|  
  
<a name="Required_UI_Automation_Events"></a>
## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyon olayları  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tüm onay kutusu denetimleri tarafından desteklenmesi gereken olaylar listelenmektedir. Olaylar hakkında daha fazla bilgi için bkz. [UI Otomasyonu olaylarına genel bakış](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Olay|Destek|Notlar|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>özellik değişti olayı.|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>özellik değişti olayı.|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>özellik değişti olayı.|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>özellik değişti olayı.|Gerekli|Hiçbiri|  
  
<a name="Default_Action"></a>
## <a name="default-action"></a>Varsayılan Eylem  
 Onay kutusunun varsayılan eylemi, bir radyo düğmesinin odaklanmış hale gelmesine ve geçerli durumunu değiştirme durumuna neden olur. Daha önce belirtildiği gibi onay kutuları, kullanıcıya ya da bir üçüncül (açık, kapalı, belirsiz) için bir ikili (Evet/Hayır) kararı (açık/kapalı) bir şekilde sunar. Onay kutusu ikili ise, varsayılan eylem "açık" durumunun "kapalı" veya "kapalı" durumunun "açık" olmasını sağlar. Bir üçüncül durumu onay kutusunda varsayılan eylem, kullanıcının denetime art arda fare tıklaması gibi, onay kutusunun durumları arasında geçiş yapar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.ControlType.CheckBox>
- [UI Otomasyon Denetim Türlerine Genel Bakış](ui-automation-control-types-overview.md)
- [UI Otomasyonuna Genel Bakış](ui-automation-overview.md)
