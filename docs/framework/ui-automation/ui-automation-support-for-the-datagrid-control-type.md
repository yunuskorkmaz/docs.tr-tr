---
title: DataGrid Denetim Türü için UI Otomasyon Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- Data Grid control type
- control types, Data Grid
- UI Automation, Data Grid control type
ms.assetid: a3db4a3f-feb5-4e5f-9b42-aae7fa816e8a
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: fa898064a3b2930499a5d3b4a8c409f562162e34
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33410260"
---
# <a name="ui-automation-support-for-the-datagrid-control-type"></a>DataGrid Denetim Türü için UI Otomasyon Desteği
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu aşağıdakiler hakkında bilgi sağlar [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] DataGrid denetim türü için destek. İçinde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], Denetim türü bir denetimi kullanmak için karşılaması gereken koşulları kümesidir `ControlType` özelliği. Koşullar özel yönergeleri dahil [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısı, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerlerini ve denetim düzenleri.  
  
 DataGrid denetim türü sütunlarda temsil meta veriler içeren öğeleri ile kolayca çalışmanızı sağlar. Veri Kılavuzu denetimlerinin öğelerinin satırları ve sütunları bu öğeler hakkında bilgi vardır. Bir liste görünümü denetimi Microsoft Vista Gezgini'nde DataGrid denetim türü destekleyen bir örnektir.  
  
 Aşağıdaki bölümlerde gerekli tanımlamak [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısı, özellikleri, Denetim desenleri ve olayları DataGrid denetim türü için. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Gereksinimleri tüm verilerin olup kılavuz denetimleri geçerlidir [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], veya [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyon ağaç yapısı  
 Denetim Görünüm ve içerik görünümünü aşağıdaki tabloda gösterilmektedir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] veri kılavuza ilgilidir ağaç denetler ve her bir görünümde bulunabilir açıklar. Hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç bkz [UI Otomasyon ağacına genel bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ağaç - denetim görünümü|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ağaç - içerik görünümü|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|DataGrid<br /><br /> <ul><li>Üstbilgi (0, 1 veya 2)<br /><br /> <ul><li>Headerıtem (sütun veya satır sayısı)</li></ul></li><li>DataItem (0 veya daha çok; hiyerarşisinde yapılandırılmış)</li></ul>|DataGrid<br /><br /> -DataItem (0 veya daha çok; hiyerarşisinde yapılandırılmış)|  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon özellikleri  
 Aşağıdaki tabloda, değer veya tanımı veri kılavuz denetimleri için özellikle ilgili özellikleri listeler. Daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri, görmek [istemciler için UI Otomasyon özellikleri](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|Özellik|Değer|Notlar|  
|--------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlarına bakın.|Bu özelliğin değeri bir uygulamadaki tüm denetimler arasında benzersiz olması gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlarına bakın.|Tam denetimi içeren en dıştaki dikdörtgen.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Notlarına bakın.|Bir sınırlayıcı dikdörtgenini ise desteklenir. Yoksa her sınırlayıcı dikdörtgenini içinde tıklanabilir noktasıdır ve özelleştirilmiş isabet testleri, gerçekleştirme sonra geçersiz kılabilir ve tıklatılabilir noktası sağlar.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|DataGrid|Bu değer tüm UI çerçeveler için aynıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Doğru|Bu özelliğin değeri her zaman True olması gerekir. Bu veri kılavuz denetimi her zaman içerik görünümünde olması gerektiği anlamına gelir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Doğru|Bu özelliğin değeri her zaman True olması gerekir. Bu veri kılavuz denetimi denetim görünümünde her zaman olması gerektiği anlamına gelir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Notlarına bakın.|Klavye odağı denetimi alamıyorsa, bu özelliği desteklemelidir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Notlarına bakın.|Bir statik metin etiketi ise bu özellik bu denetim için bir başvuru kullanıma gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"veri kılavuzu"|DataGrid denetim türü için karşılık gelen yerelleştirilmiş dize.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlarına bakın.|Veri kılavuzu denetim genellikle değerini alır, `Name` statik metin etiketi özelliğinden. Bir statik metin etiketi değilse uygulama geliştiricisi için için bir değer atamalısınız `Name` özelliği. Değeri `Name` özellik düzenleme denetimi metin içeriğini hiçbir zaman olması gerekir.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Gerekli UI Otomasyon denetim düzenleri  
 Aşağıdaki tabloda, tüm veri kılavuz denetimleri tarafından desteklenmesi için gereken denetim düzenleri listeler. Denetim desenleri hakkında daha fazla bilgi için bkz: [UI Otomasyon denetim düzenlerine genel bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Denetim düzeni|Destek|Notlar|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider>|Evet|Öğeleri olan bir kılavuzunda yerleştirilmeden meta veriler içerdiğinden veri kılavuzu denetim kendisi her zaman kılavuz denetim düzenini destekler.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Bağlıdır|Veri Kılavuzu kaydırma yeteneği, içerik ve kaydırma çubukları mevcut olup bağlıdır.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Bağlıdır|Veri Kılavuzu seçebilme içeriğine bağlıdır.|  
|<xref:System.Windows.Automation.Provider.ITableProvider>|Evet|Veri kılavuzu denetim her zaman üst bilgi, alt ağacı içinde sahiptir, böylece tablo denetim düzenini desteklenmesi gerekir.|  
  
 Veri öğelerini veri kılavuz kapsayıcıları içinde en az destekler:  
  
-   (Veri kılavuzu seçilebilir ise) seçim öğesi denetim deseni  
  
-   (Veri kılavuzu kaydırılabilir ise) kaydırma öğesi denetim deseni  
  
-   Kılavuz öğesi denetim deseni  
  
-   Tablo Öğesi denetim düzeni  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyon olayları  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayları tüm veri kılavuz denetimleri tarafından desteklenmesi gerekir. Olaylar hakkında daha fazla bilgi için bkz: [UI Otomasyonu olaylarına genel bakış](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Olay|Destek|Notlar|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> özellik değişti olayı.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> özellik değişti olayı.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> özellik değişti olayı.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent>|Bağlıdır|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|Yok.|  
|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers.CurrentViewProperty> özellik değişti olayı.|Bağlıdır|Yok.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> özellik değişti olayı.|Bağlıdır|Denetimin kaydırma düzeni destekliyorsa, bu olay desteklemesi gerekir.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> özellik değişti olayı.|Bağlıdır|Denetimin kaydırma düzeni destekliyorsa, bu olay desteklemesi gerekir.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> özellik değişti olayı.|Bağlıdır|Denetimin kaydırma düzeni destekliyorsa, bu olay desteklemesi gerekir.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> özellik değişti olayı.|Bağlıdır|Denetimin kaydırma düzeni destekliyorsa, bu olay desteklemesi gerekir.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> özellik değişti olayı.|Bağlıdır|Denetimin kaydırma düzeni destekliyorsa, bu olay desteklemesi gerekir.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> özellik değişti olayı.|Bağlıdır|Denetimin kaydırma düzeni destekliyorsa, bu olay desteklemesi gerekir.|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Gerekli|Yok.|  
  
<a name="List_View_Control_Example"></a>   
## <a name="date-grid-control-type-example"></a>Tarih kılavuz denetim türü örneği  
 Aşağıdaki resimde DataGrid denetim türü uygulayan bir liste görünümü denetimi gösterilmektedir.  
  
 ![İki veri öğeleri içeren bir liste görünümü denetimi, grafik](../../../docs/framework/ui-automation/media/uiauto-data-grid-detailed.GIF "uiauto_data_grid_detailed")  
  
 Denetim ve içerik görünümünde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] liste görünümü denetimi ilgilidir ağacı altında görüntülenir. Her Otomasyon öğesi için Denetim desenleri parantez içinde görüntülenir.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ağaç - denetim görünümü|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ağaç - içerik görünümü|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|<ul><li>DataGrid (tablo, kılavuz, seçim)</li><li>Üstbilgi<br /><br /> <ul><li>Headerıtem "Name" (çağırma)</li><li>Headerıtem "Değiştirilme tarihi" (çağırma)</li><li>Headerıtem "Boyutu" (çağırma)</li></ul></li><li>Grup "Contoso" (Tableıtem GridItem, SelectionItem, tablo *, kılavuz\*)<br /><br /> <ul><li>DataItem "Receivable.doc hesapları" (SelectionItem, çağırma, Tableıtem\*, GridItem\*)</li><li>DataItem "Payable.doc hesapları" (SelectionItem, çağırma, Tableıtem\*, GridItem\*)</li></ul></li></ul>|<ul><li>DataGrid (tablo, kılavuz, seçim)</li><li>Grup "Contoso" (Tableıtem GridItem, SelectionItem, tablo *, kılavuz\*)<br /><br /> <ul><li>DataItem "Receivable.doc hesapları" (SelectionItem, çağırma, Tableıtem\*, GridItem\*)</li><li>DataItem "Payable.doc hesapları" (SelectionItem, çağırma, Tableıtem\*, GridItem\*)</li></ul></li></ul>|  
  
 * Yukarıdaki örnekteki denetimleri birden çok düzeyi içeren DataGrid gösterir. Grup ("Contoso") denetimini iki DataItem denetimleri ("Hesapları Receivable.doc" ve "Hesapları Payable.doc") içeriyor. DataGrid/GridItem çifti, başka bir düzeyinde çiftinin bağımsızdır. DataItem denetimleri bir grup altında daha fazla açıkça olarak seçilebilir nesneleri sunulacak etkinleştirmeden ListItem denetim türü olarak yerine basit veri öğeleri olarak gösterilebilir. Bu örnek gruplandırılmış veri öğelerini alt öğelerini içermez.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Automation.ControlType.DataGrid>  
 [UI Otomasyonu Denetim Türlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [UI Otomasyonuna Genel Bakış](../../../docs/framework/ui-automation/ui-automation-overview.md)
