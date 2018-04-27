---
title: Ağaç Denetim Türü İçin UI Otomasyon Desteği
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- control types, Tree
- Tree control type
- UI Automation, Tree control type
ms.assetid: 312dd04d-a86b-4072-8b12-2beeabdff5e3
caps.latest.revision: 20
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: 3eece614368bb35cda5d7345daebb540b1ae1d95
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="ui-automation-support-for-the-tree-control-type"></a>Ağaç Denetim Türü İçin UI Otomasyon Desteği
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu aşağıdakiler hakkında bilgi sağlar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç denetim türü için destek. İçinde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], Denetim türü bir denetimi kullanmak için karşılaması gereken koşulları kümesidir <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> özelliği. Koşullar özel yönergeleri dahil [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısı, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerlerini ve denetim düzenleri.  
  
 İşlemleriyle dosya ve klasörleri'nin sol bölmesinde görüntülendiği gibi ağaç denetim türü içerikleri sahip bir hiyerarşi düğüm olarak ilgi kapsayıcıları için kullanılan [!INCLUDE[TLA#tla_winexpl](../../../includes/tlasharptla-winexpl-md.md)]. Her düğümün alt düğümleri olarak adlandırılan, diğer düğümleri içerecek şekilde olasılığı vardır. Üst düğüm ya da alt düğümleri içeren düğümleri görüntülenebilir genişletilmiş olarak veya daraltılmış.  
  
 Aşağıdaki bölümlerde gerekli tanımlamak [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısı, özellikler, Denetim desenleri ve olayları ağaç denetim türü için. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Gereksinimleri tüm ağaç denetimleri için geçerli olup olmadığını [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], veya [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyon ağaç yapısı  
 Denetim Görünüm ve içerik görünümünü aşağıdaki tabloda gösterilmektedir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , ağaç denetimleri için geçerlidir ve her bir görünümde bulunabilir açıklayan ağacı. Daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç bkz [UI Otomasyon ağacına genel bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Denetim Görünüm|İçerik görünümü|  
|------------------|------------------|  
|Ağaç<br /><br /> <ul><li>DataItem (0 veya daha fazla)</li><li>Treeıtem (0 veya daha fazla)<br /><br /> <ul><li>Treeıtem (0 veya daha fazla) •...</li></ul></li><li>ScrollBar (0, 1, 2)</li></ul>|Ağaç<br /><br /> <ul><li>DataItem (0 veya daha fazla)</li><li>Treeıtem (0 veya daha fazla)<br /><br /> <ul><li>Treeıtem (0 veya daha fazla) •...</li></ul></li></ul>|  
  
 Denetim görünümünü [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç oluşur:  
  
-   (Öğeleri ağaç öğesi, veri öğesi veya diğer denetim türü dayanabilir) kapsayıcı içinde birçok sıfır öğe.  
  
-   Sıfır, bir veya iki kaydırma çubukları.  
  
 İçerik görünümünü [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sıfır veya daha çok öğeleri (öğeleri temel alabilir ağaç öğesi, veri öğesi veya diğer denetim türü) kapsayıcıdaki ağaç oluşur.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon özellikleri  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , değer veya tanımı liste denetimleri için özellikle ilgili özellikler. Hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri, görmek [istemciler için UI Otomasyon özellikleri](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Özelliği|Değer|Notlar|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlarına bakın.|Bu özelliğin değeri bir uygulamadaki tüm denetimler arasında benzersiz olması gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlarına bakın.|Tam denetimi içeren en dıştaki dikdörtgen.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Notlarına bakın.|Ağaç denetimleri ağaçtaki veya veya bir öğeleri ağaç bunlarda ayarlı odağa sahip kapsayıcıya neden olacak bir tıklanabilir noktasına sahip. Seçili get odağı öğelerden birini neden olmaz bir yere tıklayın yalnızca, bir ağaç için tıklanabilir noktası alın.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Ağaç|Bu değer tüm UI çerçeveler için aynıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Doğru|Ağaç denetimi her zaman içerik görünümünde dahil [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Doğru|Ağaç denetimi her zaman denetim görünümünde dahil [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Notlarına bakın.|Klavye odağı denetimi alamıyorsa, bu özelliği desteklemelidir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Notlarına bakın.|Ağaç denetimi ile ilişkili bir etiket varsa, bu özellik döndürülecek bir <xref:System.Windows.Automation.AutomationElement> etiket için. Aksi takdirde, özellik null bir başvuru döndürür (`Nothing` Microsoft Visual Basic .NET içinde).|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"Ağaç"|Liste Denetim türü için karşılık gelen yerelleştirilmiş dize.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlarına bakın.|Ağaç denetim adı özelliğinin değeri genellikle denetimi etiketler metinden gelir. Metin etiketi ise, uygulama geliştiricisi bu özellik için bir değer girmelisiniz.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Gerekli UI Otomasyon denetim düzenleri  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] denetim düzenleri liste denetimleri tarafından desteklenmesi için gerekli. Denetim desenleri hakkında daha fazla bilgi için bkz: [UI Otomasyon denetim düzenlerine genel bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Denetim düzeni/deseni özelliği|Destek/değer|Notlar|  
|---------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Bağlıdır|Bu denetim düzeni seçilebilir öğeleri kümesi içeren bir ağaç denetimleri uygulamalıdır. Bu denetim düzeni öğeyi seçerek kullanıcıya anlamlı bilgiler iletmek değil, uygulanacak yok.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Notlarına bakın.|Ağaç denetimi (çoğu ağaç denetimleri çoklu seçim desteklemez) birden çok seçim destekliyorsa bu özellik uygulayın.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Notlarına bakın.|Bir öğenin seçilmesi denetimi gerektiriyorsa, bu özelliğin değeri açıktır.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Bağlıdır|Ağaç kapsayıcı içeriğini kaydırılabileceğini varsa bu denetim deseni uygular.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyon olayları  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayları tüm ağaç denetimleri tarafından desteklenmesi gerekir. Olaylar hakkında daha fazla bilgi için bkz: [UI Otomasyonu olaylarına genel bakış](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Olay|Destek|Notlar|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Bağlıdır|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> özellik değişti olayı.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> özellik değişti olayı.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> özellik değişti olayı.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> özellik değişti olayı.|Bağlıdır|Yok.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> özellik değişti olayı.|Bağlıdır|Yok.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> özellik değişti olayı.|Bağlıdır|Yok.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> özellik değişti olayı.|Bağlıdır|Yok.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> özellik değişti olayı.|Bağlıdır|Yok.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> özellik değişti olayı.|Bağlıdır|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|Yok.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Automation.ControlType.Tree>  
 [UI Otomasyonu Denetim Türlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [UI Otomasyonuna Genel Bakış](../../../docs/framework/ui-automation/ui-automation-overview.md)
