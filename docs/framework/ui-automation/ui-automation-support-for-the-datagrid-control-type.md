---
title: DataGrid Denetim Türü için UI Otomasyon Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- Data Grid control type
- control types, Data Grid
- UI Automation, Data Grid control type
ms.assetid: a3db4a3f-feb5-4e5f-9b42-aae7fa816e8a
ms.openlocfilehash: 45eaa66396049b619c9164b20eed798505d478a9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64607043"
---
# <a name="ui-automation-support-for-the-datagrid-control-type"></a>DataGrid Denetim Türü için UI Otomasyon Desteği
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu hakkında bilgi sağlar. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] DataGrid denetim türü için destek. İçinde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], Denetim türü bir denetim kullanmak için karşılaması gereken koşulları kümesidir `ControlType` özelliği. Özel yönergeleri koşulları dahil [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısını [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerlerini ve denetim düzenleri.  
  
 DataGrid denetim türü bir kullanıcı ile temsil edilen sütun meta verileri içeren öğelerini bir kolayca çalışmanıza olanak tanır. Veri kılavuzu denetim öğeleri satır ve sütun bu öğeler hakkında bilgi var. Bir liste görünümü denetimi Microsoft Vista Gezgini'nde DataGrid denetim türü destekleyen bir örnektir.  
  
 Aşağıdaki bölümlerde gerekli tanımlamak [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısı, özellikler, Denetim düzenleri ve olayları DataGrid denetim türü için. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Gereksinimler için tüm verileri olup olmadığını kılavuz denetimleri geçerli [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], veya [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyon ağaç yapısı  
 Aşağıdaki tablo denetimi ve içerik görünümünde gösterir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] veri kılavuzu ilgilidir ağaç denetler ve her bir görünümde bulunabilir açıklar. Hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç bkz [UI Otomasyon ağacına genel bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ağaç - görünüm denetimi|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ağaç - içerik görünümü|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|DataGrid<br /><br /> <ul><li>Başlık (0, 1 veya 2)<br /><br /> <ul><li>Headerıtem (sütun veya satır sayısı)</li></ul></li><li>DataItem (0 veya daha çok; hiyerarşisinde yapılandırılmış)</li></ul>|DataGrid<br /><br /> -DataItem (0 veya daha çok; hiyerarşisinde yapılandırılmış)|  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon özellikleri  
 Aşağıdaki tabloda, değer veya tanımı veri kılavuz denetimleri için özellikle ilgili özellikleri listeler. Daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri görmek [istemciler için UI Otomasyon özellikleri](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|Özellik|Değer|Notlar|  
|--------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlara bakın.|Bu özelliğin değerini bir uygulamadaki tüm denetimler arasında benzersiz olması gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlara bakın.|Tam denetimi içeren en dıştaki dikdörtgen.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Notlara bakın.|Sınırlayıcı bir dikdörtgen ise desteklenir. Değilse dikdörtgen içinde her bir nokta tıklanabilir ve özelleştirilmiş isabet sınaması, gerçekleştirmek sonra geçersiz kılmak ve tıklanabilir bir nokta sağlayamaz.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|DataGrid|Bu değer tüm UI çerçeveleri için aynıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Doğru|Bu özelliğin değeri her zaman True olması gerekir. Bu veri Kılavuzu denetimi, içerik görünümünde her zaman olması gerektiği anlamına gelir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Doğru|Bu özelliğin değeri her zaman True olması gerekir. Bu veri Kılavuzu denetimi, Denetim görünümünde her zaman olması gerektiği anlamına gelir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Notlara bakın.|Denetimin klavye odağı alamıyorsa, bu özelliği desteklemesi gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Notlara bakın.|Bir statik metin etiketi ise bu özellik bu denetime başvuru göstermesi gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"veri kılavuzu"|DataGrid denetim türü için karşılık gelen yerelleştirilmiş bir dize.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlara bakın.|Veri Kılavuzu denetimi genellikle değeri alır, `Name` bir statik metin etiketi özelliği. Bir statik metin etiketi değilse bir uygulama geliştiricisi için bir değer atamalısınız `Name` özelliği. Değerini `Name` özelliği, düzenleme denetiminin metin içeriğini hiçbir zaman olmalıdır.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Gerekli UI Otomasyon denetim düzenleri  
 Tüm veri kılavuz denetimleri tarafından desteklenmesi için gereken denetim desenleri aşağıdaki tabloda listelenmektedir. Denetim desenleri hakkında daha fazla bilgi için bkz: [UI Otomasyon denetim düzenlerine genel bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Denetim düzeni|Destek|Notlar|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider>|Evet|Öğeleri olan bir kılavuzda düzenlendiğini meta verileri içerdiğinden veri Kılavuzu denetimi kendisi her zaman kılavuz denetim düzenini destekler.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Bağlıdır|Veri Kılavuzu kaydırma olanağı, içerik ve kaydırma çubukları mevcut olup bağlıdır.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Bağlıdır|Veri Kılavuzu seçebilme içerik bağlıdır.|  
|<xref:System.Windows.Automation.Provider.ITableProvider>|Evet|Tablo denetim düzeni desteklenmesi gereken şekilde veri Kılavuzu denetimi her zaman bir üst bilgi, alt ağacı içinde sahiptir.|  
  
 En az veri ızgarası kapsayıcı içinde veri öğeleri destekler:  
  
- (Veri kılavuzu seçilebilir ise) seçim öğesi denetim düzeni  
  
- (Veri kılavuzu kaydırılabilir ise) öğesi denetim düzeni kaydırın.  
  
- Kılavuz öğesi denetim düzeni  
  
- Tablo Öğesi denetim deseni  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyonu olayları  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tüm veri kılavuz denetimleri tarafından desteklenmesi için gerekli olayları. Olaylar hakkında daha fazla bilgi için bkz. [UI Otomasyonu olaylarına genel bakış](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Olay|Destek|Notlar|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> özellik değişti olayı.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> özellik değişti olayı.|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> özellik değişti olayı.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent>|Bağlıdır|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|Yok.|  
|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers.CurrentViewProperty> özellik değişti olayı.|Bağlıdır|None|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> özellik değişti olayı.|Bağlıdır|Denetimin kaydırma düzeni destekliyorsa, bu olay desteklemesi gerekir.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> özellik değişti olayı.|Bağlıdır|Denetimin kaydırma düzeni destekliyorsa, bu olay desteklemesi gerekir.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> özellik değişti olayı.|Bağlıdır|Denetimin kaydırma düzeni destekliyorsa, bu olay desteklemesi gerekir.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> özellik değişti olayı.|Bağlıdır|Denetimin kaydırma düzeni destekliyorsa, bu olay desteklemesi gerekir.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> özellik değişti olayı.|Bağlıdır|Denetimin kaydırma düzeni destekliyorsa, bu olay desteklemesi gerekir.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> özellik değişti olayı.|Bağlıdır|Denetimin kaydırma düzeni destekliyorsa, bu olay desteklemesi gerekir.|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Gerekli|None|  
  
<a name="List_View_Control_Example"></a>   
## <a name="date-grid-control-type-example"></a>Tarih kılavuz denetim türü örneği  
 DataGrid denetim türü uygulayan bir liste görünümü denetimi aşağıda gösterilmektedir.  
  
 ![İki veri öğeleri ile bir liste görünümü denetimi grafik](../../../docs/framework/ui-automation/media/uiauto-data-grid-detailed.GIF "uiauto_data_grid_detailed")  
  
 Denetim ve içerik görünümünde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] liste görünümü denetimi ilgilidir ağacı altında görüntülenir. Her Otomasyon öğesi için Denetim desenleri parantez içinde gösterilmektedir.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ağaç - görünüm denetimi|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ağaç - içerik görünümü|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|<ul><li>DataGrid (tablo, kılavuz, seçim)</li><li>Üstbilgi<br /><br /> <ul><li>Headerıtem "Name" (çağırma)</li><li>Headerıtem "Değiştirilme tarihi" (çağırma)</li><li>Headerıtem "Boyutu" (çağırma)</li></ul></li><li>"Contoso" Grup (Tableıtem GridItem, SelectionItem, tablo *, kılavuz\*)<br /><br /> <ul><li>DataItem "Receivable.doc hesapları" (SelectionItem, çağırma Tableıtem\*, GridItem\*)</li><li>DataItem "Payable.doc hesapları" (SelectionItem, çağırma Tableıtem\*, GridItem\*)</li></ul></li></ul>|<ul><li>DataGrid (tablo, kılavuz, seçim)</li><li>"Contoso" Grup (Tableıtem GridItem, SelectionItem, tablo *, kılavuz\*)<br /><br /> <ul><li>DataItem "Receivable.doc hesapları" (SelectionItem, çağırma Tableıtem\*, GridItem\*)</li><li>DataItem "Payable.doc hesapları" (SelectionItem, çağırma Tableıtem\*, GridItem\*)</li></ul></li></ul>|  
  
 * Yukarıdaki örnekte, birden fazla seviyede denetimleri içeren bir DataGrid gösterir. Grup ("Contoso") denetimini iki DataItem denetim ("Hesapları Receivable.doc" ve "Hesapları Payable.doc") içeriyor. DataGrid/GridItem çifti çiftinin başka bir düzeyde bağımsızdır. DataItem denetim altında bir grup, bunları açıkça olarak seçilebilir daha fazla nesne sunulacak etkinleştirme ListItem denetim türü yerine basit veri öğeleri olarak sunulabilir. Bu örnekte, gruplandırılmış veri öğeleri alt öğelerinin içermez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.ControlType.DataGrid>
- [UI Otomasyonu Denetim Türlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)
- [UI Otomasyonuna Genel Bakış](../../../docs/framework/ui-automation/ui-automation-overview.md)
