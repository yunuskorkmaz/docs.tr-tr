---
title: "TreeItem Denetim Türü için UI Otomasyon Desteği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control types, Tree Item
- Tree Item control type
- UI Automation, Tree Item control type
ms.assetid: 229f341a-477f-434e-b877-4db9973068eb
caps.latest.revision: "22"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: cafc47d168e46eb0ab99ee988ea6f0c6c3f80b1e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ui-automation-support-for-the-treeitem-control-type"></a>TreeItem Denetim Türü için UI Otomasyon Desteği
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu hakkında bilgi sağlar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Treeıtem denetim türü için destek. İçinde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], Denetim türü bir denetimi kullanmak için karşılaması gereken koşulları kümesidir <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> özelliği. Koşullar özel yönergeleri dahil [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısı, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerlerini ve denetim düzenleri.  
  
 Treeıtem denetim türü bir ağaç kapsayıcı içindeki bir düğümü temsil eder. Her düğümün alt düğümleri olarak adlandırılan, diğer düğümler içerebilir. Üst düğüm ya da alt düğümleri içeren düğümleri görüntülenebilir genişletilmiş olarak veya daraltılmış.  
  
 Aşağıdaki bölümlerde gerekli tanımlamak [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısı, özellikleri, Denetim desenleri ve olayları Treeıtem denetim türü için. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Gereksinimleri tüm ağaç öğesi denetimleri için geçerli olup olmadığını [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], veya [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyon ağaç yapısı  
 Denetim Görünüm ve içerik görünümünü aşağıdaki tabloda gösterilmektedir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç öğesine ilgilidir ağaç denetler ve her bir görünümde bulunabilir açıklar. Daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç bkz [UI Otomasyon ağacına genel bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Denetim Görünüm|İçerik görünümü|  
|------------------|------------------|  
|Treeıtem<br /><br /> -Onay kutusu (0 veya 1)<br />-İmage (0 veya 1)<br />-Düğmesi (0 veya 1)<br />-Treeıtem (0 veya daha fazla)|Treeıtem<br /><br /> -Treeıtem (0 veya daha fazla)|  
  
 Ağaç öğesi denetimlerini içerik görünümünde sıfır veya daha fazla ağaç öğesi alt olabilir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı. Ağaç öğesi denetim varsa işlevselliği denetim düzenleri kullanıma sunulan ötesine aşağıda listelenen sonra denetimi veri öğesi denetim türüne göre.  
  
 Bunlar genişletilmiş ve görünür hale (veya görünüme kaydırılabileceğini kadar) daraltılmış ağaç öğeleri denetim veya içerik görünümünde görüntülenmez.  
  
 Denetim görünüm ilişkili bir görüntü veya düğmesi de dahil olmak üzere bir denetim için ek ayrıntılar içerebilir. Örneğin, bir anahat görünümde bir öğe genişletmek veya anahattı daraltmak için bir düğmeye yanı sıra bir görüntü içerebilir. Bilgileri zaten üst ağaç öğesi tarafından temsil edilen çünkü bu ayrıntı nesneleri içerik görünümünde görüntülenmez. Ekranı kaydırılan ağaç öğeleri, Denetim ve içerik görünümlerinde görünür [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı ve olmalıdır <xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty> true olarak ayarlanmış.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon özellikleri  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , değer veya tanımı liste denetimleri için özellikle ilgili özellikler. Daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri, görmek [istemciler için UI Otomasyon özellikleri](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Özelliği|Değer|Notlar|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlarına bakın.|Bu özelliğin değeri bir uygulamadaki tüm denetimler arasında benzersiz olması gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlarına bakın.|Tam denetimi içeren en dıştaki dikdörtgen.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Notlarına bakın.|Bu özellik seçimi durumunun değişmesine veya odaklanmış olur öğesi neden olur öğenin konumunu döndürmesi gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Treeıtem|Bu değer tüm UI çerçeveler için aynıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Doğru|Liste denetimi her zaman içerik görünümünde dahil [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Doğru|Liste denetimi her zaman denetim görünümünde dahil [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>|Notlarına bakın.|Ağaç öğesi denetim ekranı zaman kaydırılan belirtmek için bu özelliği ayarlayın.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Notlarına bakın.|Klavye odağı denetimi alamıyorsa, bu özelliği desteklemelidir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemTypeProperty>|Notlarına bakın.|Ağaç öğesi denetim, belirli bir nesne türü olduğunu göstermek için görsel bir simge kullanıyorsa, bu özellik desteklenmesi gerekir ve nesne belirtmek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Ağaç öğesi kendi kendine etiketleme denetimleridir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"ağaç öğesi"|Treeıtem denetim türü için karşılık gelen yerelleştirilmiş dize.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlarına bakın.|Bu özellik her ağaç öğesi denetim için görüntülenen metin kullanıma sunar.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Gerekli UI Otomasyon denetim düzenleri  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] denetim düzenleri liste denetimleri tarafından desteklenmesi için gerekli. Denetim desenleri hakkında daha fazla bilgi için bkz: [UI Otomasyon denetim düzenlerine genel bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Denetim düzeni/deseni özelliği|Destek/değer|Notlar|  
|---------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Bağlıdır|Ağaç öğesi ayrı, işlem yapılabilir komut varsa, bu denetim deseni uygular.|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Evet|Tüm öğeleri ağacı genişletilmiş veya daraltılmış.|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider.ExpandCollapseState%2A>|Genişletilmiş daraltılmış veya yaprak düğümü|Bunlar genişletilmiş daraltılmış veya ağaç öğeleri yaprak düğümlerin olacaktır.|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|Bağlıdır|Kaydırma denetim düzenini ağaç kapsayıcı destekliyorsa, bu denetim deseni uygular.|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Bağlıdır|Kullanıcı ağaç kapsayıcıya döndüğünde korunur etkin bir seçim olması mümkündür, bu denetim deseni uygular.|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider.SelectionContainer%2A>|Evet|Bu özellik kapsayıcıdaki tüm öğeler için aynı kapsayıcı açığa çıkarır.|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|Bağlıdır|Ağaç öğesi ilişkili bir onay kutusu varsa, bu denetim deseni uygular.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyon olayları  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayları tüm ağaç öğesi denetimleri tarafından desteklenmesi gerekir. Olaylar hakkında daha fazla bilgi için bkz: [UI Otomasyonu olaylarına genel bakış](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Olay|Destek|Notlar|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>özellik değişti olayı.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>özellik değişti olayı.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>özellik değişti olayı.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemStatusProperty>özellik değişti olayı.|Bağlıdır|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>özellik değişti olayı.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|Yok.|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty>özellik değişti olayı.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Bağlıdır|Yok.|  
|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers.CurrentViewProperty>özellik değişti olayı.|Bağlıdır|Yok.|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>|Bağlıdır|Yok.|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|Bağlıdır|Yok.|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Bağlıdır|Yok.|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>özellik değişti olayı.|Bağlıdır|Yok.|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty>özellik değişti olayı.|Bağlıdır|Yok.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Automation.ControlType.TreeItem>  
 [UI Otomasyonu Denetim Türlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [UI Otomasyonuna Genel Bakış](../../../docs/framework/ui-automation/ui-automation-overview.md)
