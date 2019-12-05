---
title: TreeItem Denetim Türü için UI Otomasyon Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Tree Item
- Tree Item control type
- UI Automation, Tree Item control type
ms.assetid: 229f341a-477f-434e-b877-4db9973068eb
ms.openlocfilehash: 0a1bb128c91af1a2d654fdffe288d8510f463903
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74801417"
---
# <a name="ui-automation-support-for-the-treeitem-control-type"></a>TreeItem Denetim Türü için UI Otomasyon Desteği
> [!NOTE]
> Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu, TreeItem denetim türü için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] desteği hakkında bilgi sağlar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], denetim türü, bir denetimin <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> özelliğini kullanmak için karşılaması gereken koşullar kümesidir. Koşullar, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısına yönelik özel yönergeler, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerleri ve Denetim desenleri içerir.  
  
 TreeItem denetim türü bir ağaç kapsayıcısı içindeki bir düğümü temsil eder. Her düğüm, alt düğümler olarak adlandırılan diğer düğümleri içerebilir. Üst düğümler veya alt düğümler içeren düğümler genişletilmiş veya daraltılmış olarak görüntülenebilir.  
  
 Aşağıdaki bölümler TreeItem denetim türü için gerekli [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısını, özellikleri, denetim desenlerini ve olayları tanımlar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gereksinimleri, [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]veya [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]bakılmaksızın tüm ağaç öğesi denetimlerine uygulanır.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyonu ağaç yapısı  
 Aşağıdaki tabloda, ağaç öğesi denetimleriyle ilgili [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacının denetim görünümü ve içerik görünümü gösterilmektedir ve her görünümde nelerin yer aldığı açıklanmaktadır. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı hakkında daha fazla bilgi için bkz. [UI Otomasyon ağacına genel bakış](ui-automation-tree-overview.md).  
  
|Denetim görünümü|İçerik görünümü|  
|------------------|------------------|  
|TreeItem<br /><br /> -CheckBox (0 veya 1)<br />-Görüntü (0 veya 1)<br />-Düğme (0 veya 1)<br />-TreeItem (0 veya daha fazla)|TreeItem<br /><br /> -TreeItem (0 veya daha fazla)|  
  
 Ağaç öğe denetimleri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacının içerik görünümünde sıfır veya daha fazla ağaç öğesi alt öğesine sahip olabilir. Ağaç öğesi denetimi aşağıda listelenen denetim desenlerinde gösterilenlerin ötesinde işlevsellik içeriyorsa, denetim veri öğesi denetim türünü temel almalıdır.  
  
 Daraltılmış ağaç öğeleri, genişletilene ve görünene kadar (veya görünüme kaydırılabilse) denetim görünümünde veya içerik görünümünde görüntülenmez.  
  
 Denetim görünümü, ilişkili bir görüntü veya düğme dahil olmak üzere bir denetim için ek ayrıntılar içerebilir. Örneğin, bir ana hat görünümündeki bir öğe bir görüntünün yanı sıra ana hattı genişletmek veya daraltmak için de bir düğme içerebilir. Bu ayrıntı nesneleri içerik görünümünde görünmez, çünkü bilgiler zaten üst ağaç öğesi tarafından temsil edilir. Ekrandan kaydırılan ağaç öğeleri, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacının hem denetim hem de içerik görünümlerinde görünür ve <xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty> true olarak ayarlanmalıdır.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon Özellikleri  
 Aşağıdaki tabloda, değeri veya tanımı özellikle liste denetimleriyle ilgili olan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri listelenmektedir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri hakkında daha fazla bilgi için bkz. [istemciler Için UI Otomasyon özellikleri](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özelliği|Değer|Notlar|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlara bakın.|Bu özelliğin değerinin bir uygulamadaki tüm denetimlerde benzersiz olması gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlara bakın.|Tüm denetimi içeren en dıştaki dikdörtgen.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Notlara bakın.|Bu özellik öğenin seçim durumunu değiştirmesine veya odaklanmış olmaya başlamasına neden olacak bir konum döndürmelidir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|TreeItem|Bu değer tüm UI çerçeveleri için aynıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Doğru|Liste denetimi her zaman [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacının içerik görünümüne dahil edilmiştir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Doğru|Liste denetimi her zaman [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacının denetim görünümüne dahil edilmiştir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>|Notlara bakın.|Bu özellik, ekranda bir ağaç öğe denetiminin kaydırıldığında görüntülenecek şekilde ayarlanır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Notlara bakın.|Denetim, klavye odağı alamıyorsa, bu özelliği desteklemesi gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemTypeProperty>|Notlara bakın.|Ağaç öğesi denetimi, belirli bir nesne türü olduğunu göstermek için bir görsel simge kullanıyorsa, bu özellik desteklenmeli ve nesnenin ne olduğunu göstermelidir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Ağaç öğe denetimleri kendi kendine etiketleniyor.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"ağaç öğesi"|TreeItem denetim türüne karşılık gelen yerelleştirilmiş dize.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlara bakın.|Bu özellik her ağaç öğesi denetimi için görünen metni gösterir.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Gerekli UI Otomasyonu Denetim desenleri  
 Aşağıdaki tabloda liste denetimleri tarafından desteklenmesi gereken [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Denetim desenleri listelenmektedir. Denetim desenleri hakkında daha fazla bilgi için bkz. [UI Otomasyonu Denetim desenlerine genel bakış](ui-automation-control-patterns-overview.md).  
  
|Denetim deseninin/deseninin özelliği|Destek/değer|Notlar|  
|---------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Şekline|Ağaç öğesi ayrı, eyleme dönüştürülebilir bir komuta sahipse bu denetim modelini uygulayın.|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Evet|Tüm ağaç öğeleri genişletilebilir veya daraltılabilirler.|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider.ExpandCollapseState%2A>|Genişletilmiş, daraltılmış veya yaprak düğüm|Ağaç öğeleri genişletilmemişse veya daraltıladıklarında yaprak düğümleri olacaktır.|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|Şekline|Ağaç kapsayıcısı Scroll Control modelini destekliyorsa bu denetim modelini uygulayın.|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Şekline|Kullanıcı ağaç kapsayıcısına döndüğünde korunan etkin bir seçim olması mümkün olursa bu denetim modelini uygulayın.|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider.SelectionContainer%2A>|Evet|Bu özellik, kapsayıcıdaki tüm öğeler için aynı kapsayıcıyı kullanıma sunacaktır.|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|Şekline|Ağaç öğesinin ilişkili bir onay kutusu varsa, bu denetim modelini uygulayın.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyon olayları  
 Aşağıdaki tabloda, tüm ağaç öğesi denetimleri tarafından desteklenmesi gereken [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayları listelenmektedir. Olaylar hakkında daha fazla bilgi için bkz. [UI Otomasyonu olaylarına genel bakış](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayı|Destek|Notlar|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>.|Gerekli|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>.|Gerekli|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>.|Gerekli|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.AutomationElementIdentifiers.ItemStatusProperty>.|Şekline|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty>.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Şekline|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.MultipleViewPatternIdentifiers.CurrentViewProperty>.|Şekline|Yok.|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>|Şekline|Yok.|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|Şekline|Yok.|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Şekline|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>.|Şekline|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty>.|Şekline|Yok.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.ControlType.TreeItem>
- [UI Otomasyonu Denetim Türlerine Genel Bakış](ui-automation-control-types-overview.md)
- [UI Otomasyonuna Genel Bakış](ui-automation-overview.md)
