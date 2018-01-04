---
title: "ProgressBar Denetim Türü için UI Otomasyon Desteği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control types, Progress Bar
- ProgressBar control type
- UI Automation, Progress Bar control type
ms.assetid: 302e778c-24b0-4789-814a-c8d37cf53a5f
caps.latest.revision: "21"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 8a3fafdde2583f84ff8b5240346a9f62ccf95655
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ui-automation-support-for-the-progressbar-control-type"></a>ProgressBar Denetim Türü için UI Otomasyon Desteği
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu aşağıdakiler hakkında bilgi sağlar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ProgressBar denetim türü için destek. İçinde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], Denetim türü bir denetimi kullanmak için karşılaması gereken koşulları kümesidir <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> özelliği. Koşullar özel yönergeleri dahil [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısı, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerleri, Denetim desenleri ve [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olaylar.  
  
 İlerleme çubuğu denetimleri ProgressBar denetim türü uygulamak denetimleri bir örnektir. İlerleme çubuğu denetimleri, uzun bir işlem ilerlemesini belirtmek için kullanılır. Denetim sistem vurgulama rengiyle bir işlem ilerledikçe kademeli olarak doldurulan bir dikdörtgen oluşur.  
  
 Aşağıdaki bölümlerde gerekli tanımlamak [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısı, özellikleri, Denetim desenleri ve olayları ProgressBar denetim türü için. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Gereksinimleri tüm liste denetimleri için geçerli olup olmadığını [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], veya [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyon ağaç yapısı  
 Denetim Görünüm ve içerik görünümünü aşağıdaki tabloda gösterilmektedir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ilerleme çubuğu ilgilidir ağaç denetler ve her bir görünümde bulunabilir açıklar. Daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç bkz [UI Otomasyon ağacına genel bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Denetim Görünüm|İçerik görünümü|  
|------------------|------------------|  
|ProgressBar|ProgressBar|  
  
 İlerleme çubuğu denetimleri herhangi bir alt denetim veya içerik görünümünde olmayan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon özellikleri  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , değer veya tanımı ilerleme çubuğu denetimleri için özellikle ilgili özellikler. Daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri, görmek [istemciler için UI Otomasyon özellikleri](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Özelliği|Değer|Notlar|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlarına bakın.|Bu özelliğin değeri bir uygulamadaki tüm denetimler arasında benzersiz olması gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlarına bakın.|Tam denetimi içeren en dıştaki dikdörtgen.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Notlarına bakın.|Bir sınırlayıcı dikdörtgenini ise desteklenir. Yoksa her sınırlayıcı dikdörtgenini içinde tıklanabilir noktasıdır ve özelleştirilmiş isabet testleri, gerçekleştirme sonra geçersiz kılabilir ve tıklatılabilir noktası sağlar.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Notlarına bakın.|Klavye odağı denetimi alamıyorsa, bu özelliği desteklemelidir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlarına bakın.|İlerleme çubuğu denetimi, genellikle bir statik metin etiketinden adını alır. Bir statik metin etiketi değilse uygulama geliştiricisi için bir değer kullanıma `Name` özelliği.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Notlarına bakın.|Bir statik metin etiketi ise bu özellik bu denetim için bir başvuru kullanıma gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|ProgressBar|Bu değer tüm UI çerçeveler için aynıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"ilerleme çubuğu"|ProgressBar denetim türü için karşılık gelen yerelleştirilmiş dize.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Doğru|İlerleme çubuğu denetimi her zaman içerik görünümünde dahil [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Doğru|İlerleme çubuğu denetimi her zaman denetim görünümünde dahil [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı.|  
  
<a name="Required_UI_Automation_Control_Patterns_and_Properties"></a>   
## <a name="required-ui-automation-control-patterns-and-properties"></a>UI Otomasyon denetim düzenleri ve özellikleri gerekli  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] denetim düzenleri ilerleme çubuğu denetimleri tarafından desteklenmesi için gerekli. Denetim desenleri hakkında daha fazla bilgi için bkz: [UI Otomasyon denetim düzenlerine genel bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Denetim düzeni/deseni özelliği|Destek/değer|Notlar|  
|---------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Bağlıdır|İlerleme çubuğu denetimleri metinsel bir İlerleme göstergesi uygulanmalı bu verin <xref:System.Windows.Automation.Provider.IValueProvider>.|  
|<xref:System.Windows.Automation.Provider.IValueProvider.IsReadOnly%2A>|Doğru|Bu özellik için değer her zaman True olur.|  
|<xref:System.Windows.Automation.Provider.IValueProvider.Value%2A>|Notlarına bakın.|Bu özellik bir ilerleme çubuğu denetiminin metinsel ilerlemesini gösterir.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Bağlıdır|Sayısal bir aralık ele ilerleme çubuğu denetimleri uygulamalıdır<xref:System.Windows.Automation.Provider.IRangeValueProvider>|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.Minimum%2A>|0.0|Bu özelliğin değeri denetimi için ayarlanabilen en küçük değerdir.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.Maximum%2A>|100.0|Bu özellik denetimi ayarlanabilir en büyük değer değeridir.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.SmallChange%2A>|NaN|İlerleme çubuğu denetimleri salt okunur olduğundan bu özellik gerekli değildir.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.LargeChange%2A>|NaN|İlerleme çubuğu denetimleri salt okunur olduğundan bu özellik gerekli değildir.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyon olayları  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayları tüm ilerleme çubuğu denetimleri tarafından desteklenmesi gerekir. Olaylar hakkında daha fazla bilgi için bkz: [UI Otomasyonu olaylarına genel bakış](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Olay|Destek|Notlar|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>özellik değişti olayı.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>özellik değişti olayı.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>özellik değişti olayı.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>özellik değişti olayı.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty>özellik değişti olayı.|Bağlıdır|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|Yok.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Automation.ControlType.ProgressBar>  
 [UI Otomasyonu Denetim Türlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [UI Otomasyonuna Genel Bakış](../../../docs/framework/ui-automation/ui-automation-overview.md)
