---
title: "Liste Denetim Türü İçin UI Otomasyon Desteği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control types, List
- List control type
- UI Automation, List control type
ms.assetid: 0e959fcb-50f2-413b-948d-7167d279bc11
caps.latest.revision: "20"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 63accfc3401bbfdd533f0fbbe8c17471182803cf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ui-automation-support-for-the-list-control-type"></a>Liste Denetim Türü İçin UI Otomasyon Desteği
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu aşağıdakiler hakkında bilgi sağlar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] liste denetim türü için destek. İçinde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], Denetim türü bir denetimi kullanmak için karşılaması gereken koşulları kümesidir <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> özelliği. Koşullar özel yönergeleri dahil [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısı, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerlerini ve denetim düzenleri.  
  
 Liste Denetim türü düz bir grup veya öğe gruplarını düzenlemek için bir yol sağlar ve bir kullanıcının bir veya daha fazla bu öğe seçmesini sağlar. Liste Denetim türü ne tür bir alt öğe içeriyor olabilir gevşek bir sınırlama vardır. Bu seçim kapsayıcıları için iyi bilinen öğe desteklemek UI Otomasyon sağlayıcıları sağlar.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Aşağıdaki bölümlerdeki gereksinimleri geçerlidir liste denetim türü olup olmadığını uygulayan tüm denetimler için [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], veya [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]. Liste kapsayıcı denetimleri liste denetim türü uygulamak denetimleri bir örnektir.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyon ağaç yapısı  
 Aşağıdaki tabloda iki görünümlerini gösterilmektedir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] listesine ait ağaç denetler ve her bir görünümde bulunabilir açıklar. Denetim görünüm yalnızca denetimler öğeler içeriyor ve içerik görünümü yedek bilgilerin ağacından kaldırır. Örneğin, bir birleşik giriş kutusu etiketlemek için kullanılan bir metin denetimi olarak ifşa edilip `ComboBox NameProperty`. Bu şekilde denetim görünümü aracılığıyla metin denetimi zaten açık olduğu için iki kez kullanıma sunulan gerekli değildir; Bu nedenle içerik görünümünden kaldırılır. Daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç bkz [UI Otomasyon ağacına genel bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Denetim Görünüm|İçerik görünümü|  
|------------------|------------------|  
|Denetimlere karşılık gelen öğeleri içerir.|Yardımcı teknolojiler en küçük kümesini son kullanıcının anlamlı bilgiler ile çalışmak üzere yedek bilgilerin ağacından kaldırır.|  
|List<br /><br /> -DataItem (0 veya daha fazla)<br />-ListItem (0 veya daha fazla)<br />-Group (0 veya daha fazla)<br />-ScrollBar (0, 1 veya 2)|List<br /><br /> -DataItem (0 veya daha fazla)<br />-ListItem (0 veya daha fazla)<br />-Group (0 veya daha fazla)|  
  
 Liste Denetim türü (örneğin, bir liste denetimini) uygulayan denetimi için denetim görünüm oluşur:  
  
-   Liste denetimi (öğeleri liste öğesi veya veri öğesi denetim türlerinde dayanabilir) içindeki sıfır veya daha fazla öğeler  
  
-   Liste denetimi içinde sıfır veya daha fazla grup denetimleri  
  
-   Sıfır, bir veya iki kaydırma çubuğu denetimleri  
  
-  
  
 Liste Denetim türü (örneğin, bir liste denetimini) uygulayan bir denetimin içerik görünümü oluşur:  
  
-   Liste denetimi (öğeleri liste öğesi veya veri öğesi denetim türlerinde dayanabilir) içindeki sıfır veya daha fazla öğeler  
  
-   Liste denetimi içindeki sıfır veya daha fazla grupları  
  
 Liste denetimi birlikte gruplandırılmış dışında hiyerarşik bir ilişki olan öğeler olmaması gerekir. Öğeleri alt öğe varsa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç listesi kapsayıcı ağaç denetim türü dayanmalıdır sonra.  
  
 Liste denetimi seçilebilir öğeleri descendants gelen kullanılabilecek [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] liste denetimi ağacı. Liste denetimi içindeki tüm öğeleri aynı seçim grubuna ait olmalıdır. Listedeki seçilebilir (yerine DataItem) ListItem denetim türü olarak açık olmamalıdır.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon özellikleri  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , değer veya tanımı liste denetimleri için özellikle ilgili özellikler. Daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri, görmek [istemciler için UI Otomasyon özellikleri](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Özelliği|Değer|Notlar|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlarına bakın.|Bu özelliğin değeri bir uygulamadaki tüm denetimler arasında benzersiz olması gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlarına bakın.|Tam denetimi içeren en dıştaki dikdörtgen.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Notlarına bakın.|Liste denetimi tıklanabilir noktası (odaklanması listeye neden için tıklattığınız noktası) varsa, o noktadan bu özelliği üzerinden sunulmalıdır.<br /><br /> Varsa değerini `IsOffScreen` özelliği doğruysa, sonra <xref:System.Windows.Automation.NoClickablePointException> gerçekleştirilecektir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Notlarına bakın.|Klavye odağı denetimi alamıyorsa, bu özelliği desteklemelidir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlarına bakın.|Bir liste denetimin adı özelliğinin değeri, kullanıcı arasından seçim isteniyor seçenekleri kategorisini iletmek. Bu özellik, genellikle bir statik metin etiketinden adını alır. Bir statik metin etiketi değilse uygulama geliştiricisi adı özelliği için bir değer kullanıma gerekir.<br /><br /> Bu özelliğin liste denetimleri için gerekli değil yalnızca bir kez denetimi başka bir denetim ağaçtaki varsa kullanılır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Notlarına bakın.|Bir statik metin etiketi ise bu özellik bu denetim için bir başvuru kullanıma gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|List|Bu değer tüm UI çerçeveler için aynıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"list"|Liste Denetim türü için karşılık gelen yerelleştirilmiş dize.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Doğru|Liste denetimi her zaman içerik görünümünde dahil [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Doğru|Liste denetimi her zaman denetim görünümünde dahil [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Doğru|Kapsayıcı klavye girdisi kabul edebilirsiniz, bu özellik değeri true olmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|Notlarına bakın.|Liste denetimleri için Yardım metni neden kullanıcı seçenekleri listesinden seçim yapmanız isteniyor açıklayan. Örneğin, "seçim bu listeden bir öğe ekran çözünürlüğünü, izleme için ayarlar."|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns-and-properties"></a>UI Otomasyon denetim düzenleri ve özellikleri gerekli  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] denetim düzenleri liste denetimleri tarafından desteklenmesi için gerekli. Denetim desenleri hakkında daha fazla bilgi için bkz: [UI Otomasyon denetim düzenlerine genel bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Denetim düzeni/deseni özelliği|Destek/değer|Notlar|  
|---------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Gerekli|Liste Denetim türü destekleyen tüm denetimleri uygulamalıdır `ISelectionProvider` ne zaman bir seçim durumu korunduğu denetiminde bulunan öğeler arasında. Kapsayıcı içindeki öğeleri seçilebilir emin değilseniz, Grup denetim türü kullanılması gerekir.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Bağlıdır|Liste denetimleri, bir öğenin seçilmesi her zaman gerektirmez.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Bağlıdır|Liste denetimleri tek veya çoklu seçim kapsayıcıları olabilir.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Bağlıdır|Kapsayıcı öğeler kaydırılabilir varsa bu denetim deseni uygular.|  
|<xref:System.Windows.Automation.Provider.IGridProvider>|Bağlıdır|Bir öğe tarafından temelinde kullanılabilir olması kılavuz Gezinti ihtiyacı olduğunda bu deseni uygular.|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider>|Bağlıdır|Denetim kapsayıcısında öğelerin birden çok görünüm destekliyorsa bu denetim deseni uygular.|  
|<xref:System.Windows.Automation.Provider.ITableProvider>|Hiçbir zaman|`ITableProvider`Liste Denetim türü için hiçbir zaman desteklenir. Bu denetim düzeni denetimi desteklemesi gerekiyorsa, denetim veri kılavuzu denetim türü dayanmalıdır.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyon olayları  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayları tüm liste denetimleri tarafından desteklenmesi gerekir. Olaylar hakkında daha fazla bilgi için bkz: [UI Otomasyonu olaylarına genel bakış](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Olay|Destek/değer|Notlar|  
|---------------------------------------------------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Bağlıdır|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent>|Bağlıdır|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>özellik değişti olayı.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>özellik değişti olayı.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>özellik değişti olayı.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers.CurrentViewProperty>özellik değişti olayı.|Bağlıdır|Yok.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>özellik değişti olayı.|Bağlıdır|Yok.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty>özellik değişti olayı.|Bağlıdır|Yok.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty>özellik değişti olayı.|Bağlıdır|Yok.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty>özellik değişti olayı.|Bağlıdır|Yok.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>özellik değişti olayı.|Bağlıdır|Yok.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty>özellik değişti olayı.|Bağlıdır|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|Yok.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Automation.ControlType.List>  
 [UI Otomasyon denetim türlerine genel bakış](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [UI Otomasyon genel bakış](../../../docs/framework/ui-automation/ui-automation-overview.md)
