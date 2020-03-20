---
title: TreeItem Denetim Türü için UI Otomasyon Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Tree Item
- Tree Item control type
- UI Automation, Tree Item control type
ms.assetid: 229f341a-477f-434e-b877-4db9973068eb
ms.openlocfilehash: 4dc55b4baaf42d22f0c7db1301a78672e739e757
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179431"
---
# <a name="ui-automation-support-for-the-treeitem-control-type"></a>TreeItem Denetim Türü için UI Otomasyon Desteği
> [!NOTE]
> Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır. Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] TreeItem denetim türü için destek hakkında bilgi sağlar. Denetim [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]türü, <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> özelliği kullanmak için denetimin karşılaması gereken koşullar kümesidir. Koşullar, ağaç yapısı, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerleri ve denetim desenleri için özel yönergeler içerir.  
  
 TreeItem denetim türü, ağaç kapsayıcısı içindeki bir düğümü temsil eder. Her düğüm, alt düğüm olarak adlandırılan diğer düğümler içerebilir. Alt düğümler veya alt düğümler içeren düğümler genişletilmiş veya daraltılmış olarak görüntülenebilir.  
  
 Aşağıdaki bölümlerde TreeItem denetim türü için gerekli [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısı, özellikleri, denetim desenleri ve olayları tanımlanır. Gereksinimler, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Win32 veya [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]Windows Forms olsun, tüm ağaç öğesi denetimleri için geçerlidir.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyon Ağaç Yapısı  
 Aşağıdaki tablo, ağaç öğesi denetimleri ile [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ilgili denetim görünümünü ve ağacın içerik görünümünü görüntüler ve her görünümde nelerin bulunabileceğini açıklar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ağaç hakkında daha fazla bilgi için [UI Automation Tree Genel Bakış'a](ui-automation-tree-overview.md)bakın.  
  
|Kontrol Görünümü|İçerik Görünümü|  
|------------------|------------------|  
|Treeıtem<br /><br /> - CheckBox (0 veya 1)<br />- Resim (0 veya 1)<br />- Düğme (0 veya 1)<br />- TreeItem (0 veya daha fazla)|Treeıtem<br /><br /> - TreeItem (0 veya daha fazla)|  
  
 Ağaç öğesi [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] denetimleri, ağacın içerik görünümünde sıfır veya daha fazla ağaç öğesi küçük olabilir. Ağaç öğesi denetimi, aşağıda listelenen denetim desenlerinde maruz kalınanın ötesinde işlevsellik varsa, denetim Veri Öğesi denetim türüne dayanmalıdır.  
  
 Daraltılmış ağaç öğeleri genişletilip görünür hale gelene (veya görünüme kaydırılanına kadar) denetim görünümünde veya içerik görünümünde görüntülenmez.  
  
 Denetim görünümü, ilişkili bir resim veya düğme de dahil olmak üzere denetim için ek ayrıntılar içerebilir. Örneğin, anahat görünümündeki bir öğe, anahattı genişletmek veya daraltmak için bir düğmenin yanı sıra bir görüntü de içerebilir. Bilgiler zaten ana ağaç öğesi tarafından temsil edildiğinden, bu ayrıntı nesneleri içerik görünümünde görünmez. Ekrandan kaydırılan ağaç [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] öğeleri, ağacın hem denetiminde hem de içerik <xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty> görünümlerinde görünür ve ayarın gerçek olması gerekir.  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon Özellikleri  
 Aşağıdaki tablo, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] değeri veya tanımı özellikle liste denetimleri ile alakalı olan özellikleri listeler. Özellikler hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] daha fazla bilgi [için, Müşteriler için Kullanıcı Arabirimi Otomasyon Özellikleri'ne](ui-automation-properties-for-clients.md)bakın.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Özellik|Değer|Notlar|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlara bakın.|Bu özelliğin değeri, bir uygulamadaki tüm denetimler arasında benzersiz olmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlara bakın.|Tüm denetimi içeren en dıştaki dikdörtgen.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Notlara bakın.|Bu özellik, öğenin seçim durumunu değiştirmesine veya odaklanmasına neden olacak bir öğenin konumunu döndürmelidir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Treeıtem|Bu değer tüm Ara bilgi arabirimi çerçeveleri için aynıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|Liste denetimi her zaman [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacın içerik görünümüne eklenir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Liste denetimi her zaman [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacın denetim görünümüne dahildir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>|Notlara bakın.|Bu özellik, bir ağaç öğesi denetiminin ekrandan ne zaman kaydırılmış olduğunu belirtmek üzere ayarlanmıştır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Notlara bakın.|Denetim klavye odağı alabiliyorsa, bu özelliği desteklemesi gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemTypeProperty>|Notlara bakın.|Ağaç öğesi denetimi, belirli bir nesne türünü belirtmek için görsel bir simge kullanıyorsa, bu özellik desteklenmeli ve nesnenin ne olduğunu belirtmelidir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Ağaç öğesi denetimleri kendi kendini etiketlemedir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"ağaç öğesi"|TreeItem denetim türüne karşılık gelen yerelleştirilmiş dize.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlara bakın.|Bu özellik, her ağaç öğesi denetimi için görüntülenen metni ortaya çıkarır.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>
## <a name="required-ui-automation-control-patterns"></a>Gerekli UI Otomasyon Kontrol Desenleri  
 Aşağıdaki tablo, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] liste denetimleri tarafından desteklenmesi gereken denetim desenlerini listeler. Denetim desenleri hakkında daha fazla bilgi için [UI Otomasyon Kontrol Modellerine Genel Bakış'a](ui-automation-control-patterns-overview.md)bakın.  
  
|Kontrol Deseni/Desen Özelliği|Destek / Değer|Notlar|  
|---------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider>|-sına bağ -lıdır|Ağaç öğesi ayrı, işlem işlenebilir bir komutvarsa bu denetim deseni uygulayın.|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Evet|Tüm ağaç öğeleri genişletilebilir veya daraltılabilir.|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider.ExpandCollapseState%2A>|Genişletilmiş, Daraltılmış veya Yaprak Düğümü|Ağaç öğeleri genişletilmediklerinde veya daraltılmadıkları zaman yaprak düğümleri olacaktır.|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|-sına bağ -lıdır|Ağaç kapsayıcı kaydırma denetim deseni destekliyorsa bu denetim deseni uygulayın.|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|-sına bağ -lıdır|Kullanıcı ağaç kapsayıcısına döndüğünde tutulan etkin bir seçim mümkünse bu denetim deseni uygulayın.|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider.SelectionContainer%2A>|Evet|Bu özellik, kapsayıcı içindeki tüm öğeler için aynı kapsayıcıortaya çıkar.|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|-sına bağ -lıdır|Ağaç öğesiilişkili bir onay kutusu varsa bu denetim deseni uygulayın.|  
  
<a name="Required_UI_Automation_Events"></a>
## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyon Etkinlikleri  
 Aşağıdaki tablo, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tüm ağaç öğesi denetimleri tarafından desteklenmesi gereken olayları listeler. Etkinlikler hakkında daha fazla bilgi için [UI Otomasyon Etkinliklerine Genel Bakış'a](ui-automation-events-overview.md)bakın.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Olay|Destek|Notlar|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>özellik değiştirilen olay.|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>özellik değiştirilen olay.|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>özellik değiştirilen olay.|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemStatusProperty>özellik değiştirilen olay.|-sına bağ -lıdır|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>özellik değiştirilen olay.|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|None|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty>özellik değiştirilen olay.|Gerekli|None|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|-sına bağ -lıdır|None|  
|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers.CurrentViewProperty>özellik değiştirilen olay.|-sına bağ -lıdır|None|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>|-sına bağ -lıdır|None|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|-sına bağ -lıdır|None|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|-sına bağ -lıdır|None|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>özellik değiştirilen olay.|-sına bağ -lıdır|None|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty>özellik değiştirilen olay.|-sına bağ -lıdır|None|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.ControlType.TreeItem>
- [UI Otomasyonu Denetim Türlerine Genel Bakış](ui-automation-control-types-overview.md)
- [UI Otomasyonuna Genel Bakış](ui-automation-overview.md)
