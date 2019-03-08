---
title: Liste Denetim Türü İçin UI Otomasyon Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- control types, List
- List control type
- UI Automation, List control type
ms.assetid: 0e959fcb-50f2-413b-948d-7167d279bc11
ms.openlocfilehash: 37506c7ec0bcd07d4f9b91da1f49104223840bc0
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57679248"
---
# <a name="ui-automation-support-for-the-list-control-type"></a>Liste Denetim Türü İçin UI Otomasyon Desteği
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu hakkında bilgi sağlar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] desteklemek için liste denetim türü. İçinde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], Denetim türü bir denetim kullanmak için karşılaması gereken koşulları kümesidir <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> özelliği. Özel yönergeleri koşulları dahil [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısını [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerlerini ve denetim düzenleri.  
  
 Liste Denetim türü, düz bir grup veya grupları öğeleri düzenlemek için bir yol sağlar ve bu öğeleri seçmek bir kullanıcı sağlar. Liste Denetim türü, hangi tür alt öğelerini içerebilir üzerinde gevşek bir kısıtlamaya sahiptir. Bu, iyi bilinen bir öğe seçimi kapsayıcılar için desteklemek UI Otomasyon sağlayıcıları sağlar.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Gereksinimler aşağıdaki bölümlerde geçerli liste denetim türü olup olmadığını uygulayan tüm denetimlere [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], veya [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]. Liste Denetim türü uygulayan denetim örneği listesi kapsayıcı denetimlerdir.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyon ağaç yapısı  
 Aşağıdaki tabloda iki görünümlerini gösterilmektedir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] listesine ait ağaç denetimleri ve her bir görünümde bulunabilir açıklar. Denetim görünüm denetimleri olan öğeleri içerir ve içerik görünümü yedekli bilgiler ağaçtan kaldırır. Örneğin, bir birleşik giriş kutusu etiketlemek için kullanılan bir metin denetimi olarak kullanıma sunulacak `ComboBox NameProperty`. Metin denetimi bu şekilde denetim görünüm aracılığıyla sunulur çünkü iki kez kullanıma sunulan gereksizdir; Bu nedenle içerik görünümünden kaldırılır. Daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç bkz [UI Otomasyon ağacına genel bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Denetim Görünüm|İçerik görünümü|  
|------------------|------------------|  
|Denetimler için karşılık gelen öğeleri içerir.|Yardımcı teknolojiler en küçük kümesini son kullanıcıya anlamlı bilgiler ile çalışmak üzere yedekli bilgiler ağaçtan kaldırır.|  
|List<br /><br /> -DataItem (0 veya daha fazla)<br />-ListItem (0 veya daha fazla)<br />-Grup (0 veya daha fazla)<br />-ScrollBar (0, 1 veya 2)|List<br /><br /> -DataItem (0 veya daha fazla)<br />-ListItem (0 veya daha fazla)<br />-Grup (0 veya daha fazla)|  
  
 Liste Denetim türü (örneğin, bir liste denetimini) uygulayan bir denetim için Denetim görünümü oluşur:  
  
- Sıfır veya daha fazla öğe içinde (öğeleri liste öğesi veya veri öğesi denetim türlerinde dayanabilir) liste denetimi.
  
- Liste denetimi içindeki sıfır veya daha fazla grup denetimleri.
  
- Sıfır, bir veya iki kaydırma çubuğu denetimi.
  
Liste Denetim türü (örneğin, bir liste denetimini) uygulayan bir denetim içerik görünümünü oluşur:  
  
- Sıfır veya daha fazla öğe içinde (öğeleri liste öğesi veya veri öğesi denetim türlerinde dayanabilir) liste denetimi.
  
- Liste denetimi içinde sıfır veya daha fazla gruplar.

Liste denetimi, birlikte gruplanmış dışında hiyerarşik bir ilişki olan öğeler olmaması gerekir. Öğeleri alt öğeleri varsa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç sonra liste kapsayıcı, ağaç denetimi türüne göre.  
  
 Liste denetimi içinde seçilebilir öğeleri alt gelen kullanıma sunulacak [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç listesi denetimi. Liste denetimi içindeki tüm öğeler aynı seçim grubuna ait olmalıdır. Seçilebilir öğeleri listesinde ListItem (yerine DataItem) denetim türlerini açılmamalıdır.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon özellikleri  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , değer veya tanımı liste denetimleri yakından ilgili özellikler. Daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri görmek [istemciler için UI Otomasyon özellikleri](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Özelliği|Değer|Notlar|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlara bakın.|Bu özelliğin değerini bir uygulamadaki tüm denetimler arasında benzersiz olması gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlara bakın.|Tam denetimi içeren en dıştaki dikdörtgen.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Notlara bakın.|Listesi denetimini tıklanabilir bir nokta (odağı alması için listeyi neden tıklanabilir bir nokta) varsa, bu noktadan bu özelliği aracılığıyla sunulmalıdır.<br /><br /> Varsa değerini `IsOffScreen` özelliği true ise sonra <xref:System.Windows.Automation.NoClickablePointException> gerçekleştirilecektir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Notlara bakın.|Denetimin klavye odağı alamıyorsa, bu özelliği desteklemesi gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlara bakın.|Liste denetimin adı özelliğinin değeri, kullanıcı seçmek için sorulmaktadır seçenekleri kategorisini iletmek. Bu özellik, genellikle bir statik metin etiketten adını alır. Uygulama geliştiricisi, bir statik metin etiketi ise Name özelliği için bir değer göstermesi gerekir.<br /><br /> Bu özellik, liste denetimleri için gerekli değildir. yalnızca bir kez denetimi başka bir denetimin alt ağacı içinde varsa kullanılır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Notlara bakın.|Bir statik metin etiketi ise bu özellik bu denetime başvuru göstermesi gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|List|Bu değer tüm UI çerçeveleri için aynıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"list"|Liste Denetim türü için karşılık gelen yerelleştirilmiş bir dize.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Doğru|Listesi denetimini her zaman içerik görünümünde bulunan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Doğru|Listesi denetimini her zaman denetim görünümünde bulunan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Doğru|Kapsayıcı klavye girdisi kabul edebilir, bu özellik değeri true olmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|Notlara bakın.|Liste denetimleri için Yardım metni, kullanıcı seçenekleri listesinden bir seçim yapmasını neden sorulmaktadır açıklayan. Örneğin, "seçimi bu listeden bir öğe ekran çözünürlüğünü, izleyici için ayarlar."|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns-and-properties"></a>UI Otomasyon denetim düzenleri ve özellikleri gerekli  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] denetim liste denetimleri tarafından desteklenmesi için gereken desenleri. Denetim desenleri hakkında daha fazla bilgi için bkz. [UI Otomasyon denetim düzenlerine genel bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Denetim düzeni/desen özelliği|Destek/değer|Notlar|  
|---------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Gerekli|Liste Denetim türü destekleyen tüm denetimleri uygulamalıdır `ISelectionProvider` ne zaman bir seçim durumu korunduğu denetiminde bulunan öğeler arasında. Kapsayıcı içindeki öğeleri seçilebilir emin değilseniz, Grup denetim türü kullanılmalıdır.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Bağlıdır|Her zaman liste denetimleri öğenin seçilmiş olması gerekmez.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Bağlıdır|Liste denetimleri, tek veya çoklu seçim kapsayıcı olabilir.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Bağlıdır|Kapsayıcı öğeler kaydırılabilir varsa bu denetim desenini uygular.|  
|<xref:System.Windows.Automation.Provider.IGridProvider>|Bağlıdır|Bir öğe tarafından temelinde kullanılabilir olması kılavuz Gezinti ihtiyacı olduğunda bu deseni uygular.|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider>|Bağlıdır|Denetim öğeleri birden çok görünüm kapsayıcıda destekliyorsa bu denetim desenini uygular.|  
|<xref:System.Windows.Automation.Provider.ITableProvider>|hiçbir zaman|`ITableProvider` Liste Denetim türü için hiçbir zaman desteklenir. Bu denetim düzeni denetim desteklemesi gerekiyorsa, denetim veri kılavuzu denetim türünde dayanmalıdır.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyonu olayları  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayları tüm liste denetimleri tarafından desteklenmesi gerekir. Olaylar hakkında daha fazla bilgi için bkz. [UI Otomasyonu olaylarına genel bakış](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Olay|Destek/değer|Notlar|  
|---------------------------------------------------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Bağlıdır|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent>|Bağlıdır|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> özellik değişti olayı.|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> özellik değişti olayı.|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> özellik değişti olayı.|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers.CurrentViewProperty> özellik değişti olayı.|Bağlıdır|Hiçbiri|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> özellik değişti olayı.|Bağlıdır|Hiçbiri|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> özellik değişti olayı.|Bağlıdır|Hiçbiri|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> özellik değişti olayı.|Bağlıdır|Hiçbiri|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> özellik değişti olayı.|Bağlıdır|Hiçbiri|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> özellik değişti olayı.|Bağlıdır|Hiçbiri|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> özellik değişti olayı.|Bağlıdır|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|Hiçbiri|  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Automation.ControlType.List>
- [UI Otomasyonu Denetim Türlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)
- [UI Otomasyonuna Genel Bakış](../../../docs/framework/ui-automation/ui-automation-overview.md)
