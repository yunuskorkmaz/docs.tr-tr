---
title: TreeItem Denetim Türü için UI Otomasyon Desteği
description: TreeItem denetim türü için UI Otomasyonu desteği hakkında bilgi alın. Gerekli ağaç yapısını, özellikleri, denetim desenlerini ve olayları öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Tree Item
- Tree Item control type
- UI Automation, Tree Item control type
ms.assetid: 229f341a-477f-434e-b877-4db9973068eb
ms.openlocfilehash: 6b20e2ee6a54ad4f59f0f7d491c019bd8db24a80
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167821"
---
# <a name="ui-automation-support-for-the-treeitem-control-type"></a>TreeItem Denetim Türü için UI Otomasyon Desteği
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , TreeItem denetim türü için destek hakkında bilgi sağlar. ' De [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , bir denetim türü, özelliği kullanmak için bir denetimin uyması gereken koşullar kümesidir <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> . Koşullar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , ağaç yapısı, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerleri ve Denetim desenleri için özel kurallar içerir.  
  
 TreeItem denetim türü bir ağaç kapsayıcısı içindeki bir düğümü temsil eder. Her düğüm, alt düğümler olarak adlandırılan diğer düğümleri içerebilir. Üst düğümler veya alt düğümler içeren düğümler genişletilmiş veya daraltılmış olarak görüntülenebilir.  
  
 Aşağıdaki bölümler [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] TreeItem denetim türü için gerekli ağaç yapısını, özellikleri, denetim desenlerini ve olayları tanımlar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Gereksinimler, Win32 veya Windows Forms tüm ağaç öğesi denetimlerine uygulanır [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] .  
  
<a name="Required_UI_Automation_Tree_Structure"></a>
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyonu ağaç yapısı  
 Aşağıdaki tabloda, ağaç öğesi denetimleriyle ilgili ağacın denetim görünümü ve içerik görünümü gösterilmektedir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ve her görünümde nelerin yer aldığı açıklanmaktadır. Ağaç hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [UI Otomasyon ağacına genel bakış](ui-automation-tree-overview.md).  
  
|Denetim görünümü|İçerik görünümü|  
|------------------|------------------|  
|TreeItem<br /><br /> -CheckBox (0 veya 1)<br />-Görüntü (0 veya 1)<br />-Düğme (0 veya 1)<br />-TreeItem (0 veya daha fazla)|TreeItem<br /><br /> -TreeItem (0 veya daha fazla)|  
  
 Ağaç öğe denetimleri ağacın içerik görünümünde sıfır veya daha fazla ağaç öğesi alt öğesine sahip olabilir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] . Ağaç öğesi denetimi aşağıda listelenen denetim desenlerinde gösterilenlerin ötesinde işlevsellik içeriyorsa, denetim veri öğesi denetim türünü temel almalıdır.  
  
 Daraltılmış ağaç öğeleri, genişletilene ve görünene kadar (veya görünüme kaydırılabilse) denetim görünümünde veya içerik görünümünde görüntülenmez.  
  
 Denetim görünümü, ilişkili bir görüntü veya düğme dahil olmak üzere bir denetim için ek ayrıntılar içerebilir. Örneğin, bir ana hat görünümündeki bir öğe bir görüntünün yanı sıra ana hattı genişletmek veya daraltmak için de bir düğme içerebilir. Bu ayrıntı nesneleri içerik görünümünde görünmez, çünkü bilgiler zaten üst ağaç öğesi tarafından temsil edilir. Ekrandan kaydırılan ağaç öğeleri, ağacın hem denetim hem de içerik görünümlerinde görünür [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ve <xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty> true olarak ayarlanmalıdır.  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon Özellikleri  
 Aşağıdaki tabloda, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] değeri veya tanımı özellikle liste denetimleriyle ilgili olan özellikler listelenmiştir. Özellikler hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [Istemciler Için UI Otomasyon özellikleri](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Özelliði|Değer|Notlar|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlara bakın.|Bu özelliğin değerinin bir uygulamadaki tüm denetimlerde benzersiz olması gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlara bakın.|Tüm denetimi içeren en dıştaki dikdörtgen.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Notlara bakın.|Bu özellik öğenin seçim durumunu değiştirmesine veya odaklanmış olmaya başlamasına neden olacak bir konum döndürmelidir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|TreeItem|Bu değer tüm UI çerçeveleri için aynıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Doğru|Liste denetimi her zaman ağacın içerik görünümüne dahil edilmiştir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Doğru|Liste denetimi her zaman ağacın denetim görünümüne dahil edilmiştir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>|Notlara bakın.|Bu özellik, ekranda bir ağaç öğe denetiminin kaydırıldığında görüntülenecek şekilde ayarlanır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Notlara bakın.|Denetim, klavye odağı alamıyorsa, bu özelliği desteklemesi gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemTypeProperty>|Notlara bakın.|Ağaç öğesi denetimi, belirli bir nesne türü olduğunu göstermek için bir görsel simge kullanıyorsa, bu özellik desteklenmeli ve nesnenin ne olduğunu göstermelidir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Ağaç öğe denetimleri kendi kendine etiketleniyor.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"ağaç öğesi"|TreeItem denetim türüne karşılık gelen yerelleştirilmiş dize.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlara bakın.|Bu özellik her ağaç öğesi denetimi için görünen metni gösterir.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>
## <a name="required-ui-automation-control-patterns"></a>Gerekli UI Otomasyonu Denetim desenleri  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] liste denetimleri tarafından desteklenmesi için gereken denetim desenleri listelenmektedir. Denetim desenleri hakkında daha fazla bilgi için bkz. [UI Otomasyonu Denetim desenlerine genel bakış](ui-automation-control-patterns-overview.md).  
  
|Denetim deseninin/deseninin özelliği|Destek/değer|Notlar|  
|---------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Şekline|Ağaç öğesi ayrı, eyleme dönüştürülebilir bir komuta sahipse bu denetim modelini uygulayın.|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Yes|Tüm ağaç öğeleri genişletilebilir veya daraltılabilirler.|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider.ExpandCollapseState%2A>|Genişletilmiş, daraltılmış veya yaprak düğüm|Ağaç öğeleri genişletilmemişse veya daraltıladıklarında yaprak düğümleri olacaktır.|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|Şekline|Ağaç kapsayıcısı Scroll Control modelini destekliyorsa bu denetim modelini uygulayın.|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Şekline|Kullanıcı ağaç kapsayıcısına döndüğünde korunan etkin bir seçim olması mümkün olursa bu denetim modelini uygulayın.|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider.SelectionContainer%2A>|Yes|Bu özellik, kapsayıcıdaki tüm öğeler için aynı kapsayıcıyı kullanıma sunacaktır.|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|Şekline|Ağaç öğesinin ilişkili bir onay kutusu varsa, bu denetim modelini uygulayın.|  
  
<a name="Required_UI_Automation_Events"></a>
## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyon olayları  
 Aşağıdaki tabloda, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tüm ağaç öğesi denetimleri tarafından desteklenmesi gereken olaylar listelenmektedir. Olaylar hakkında daha fazla bilgi için bkz. [UI Otomasyonu olaylarına genel bakış](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Olay|Destek|Notlar|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>özellik değişti olayı.|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>özellik değişti olayı.|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>özellik değişti olayı.|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemStatusProperty>özellik değişti olayı.|Şekline|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>özellik değişti olayı.|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty>özellik değişti olayı.|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Şekline|Hiçbiri|  
|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers.CurrentViewProperty>özellik değişti olayı.|Şekline|Hiçbiri|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>|Şekline|Hiçbiri|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|Şekline|Hiçbiri|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Şekline|Hiçbiri|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>özellik değişti olayı.|Şekline|Hiçbiri|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty>özellik değişti olayı.|Şekline|Hiçbiri|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.ControlType.TreeItem>
- [UI Otomasyon Denetim Türlerine Genel Bakış](ui-automation-control-types-overview.md)
- [UI Otomasyonuna Genel Bakış](ui-automation-overview.md)
