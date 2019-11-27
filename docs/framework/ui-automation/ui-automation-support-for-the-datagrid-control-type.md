---
title: DataGrid Denetim Türü için UI Otomasyon Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- Data Grid control type
- control types, Data Grid
- UI Automation, Data Grid control type
ms.assetid: a3db4a3f-feb5-4e5f-9b42-aae7fa816e8a
ms.openlocfilehash: 8a991af5e8e48ce377acf1c1d8342d163d17c1e4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74441073"
---
# <a name="ui-automation-support-for-the-datagrid-control-type"></a>DataGrid Denetim Türü için UI Otomasyon Desteği
> [!NOTE]
> Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konuda, DataGrid denetim türü için [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] desteği hakkında bilgi verilmektedir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], denetim türü, bir denetimin `ControlType` özelliğini kullanmak için karşılaması gereken koşullar kümesidir. Koşullar, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısına yönelik özel yönergeler, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerleri ve Denetim desenleri içerir.  
  
 DataGrid denetim türü, bir kullanıcının sütunlarda temsil edilen meta verileri içeren öğelerle kolayca çalışmasına olanak sağlar. Veri kılavuzu denetimlerinde bu öğeler hakkındaki öğe ve bilgi sütunlarının satırları vardır. Microsoft Vista Explorer 'daki liste görünümü denetimi, DataGrid denetim türünü destekleyen bir örnektir.  
  
 Aşağıdaki bölümler, DataGrid denetim türü için gerekli [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısını, özellikleri, denetim desenlerini ve olayları tanımlar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gereksinimler, [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]veya [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]bakılmaksızın tüm veri kılavuzu denetimleri için geçerlidir.  
  
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyonu ağaç yapısı  
 Aşağıdaki tabloda, veri kılavuzu denetimleriyle ilgili [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacının denetim görünümü ve içerik görünümü gösterilmektedir ve her görünümde nelerin yer aldığı açıklanmaktadır. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı hakkında daha fazla bilgi için bkz. [UI Otomasyon ağacına genel bakış](ui-automation-tree-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç denetimi görünümü|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı-Içerik görünümü|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|DataGrid<br /><br /> <ul><li>Üst bilgi (0, 1 veya 2)<br /><br /> <ul><li>HeaderItem (sütun veya satır sayısı)</li></ul></li><li>DataItem (0 veya daha fazla; hiyerarşide yapılandırılabilir)</li></ul>|DataGrid<br /><br /> -DataItem (0 veya daha fazla; hiyerarşide yapılandırılabilir)|  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon Özellikleri  
 Aşağıdaki tabloda, değeri veya tanımı özellikle veri kılavuzu denetimleriyle ilgili olan özellikler listelenmiştir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri hakkında daha fazla bilgi için bkz. [istemciler Için UI Otomasyon özellikleri](ui-automation-properties-for-clients.md).  
  
|Özellik|Value|Notlar|  
|--------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlara bakın.|Bu özelliğin değerinin bir uygulamadaki tüm denetimlerde benzersiz olması gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlara bakın.|Tüm denetimi içeren en dıştaki dikdörtgen.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Notlara bakın.|Sınırlayıcı bir dikdörtgen varsa desteklenir. Sınırlayıcı dikdörtgenin içindeki her nokta tıklatılabilir ise ve özelleştirilmiş isabet testi gerçekleştirirseniz ve ardından tıklatılabilir bir nokta sağlayabilirsiniz.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|DataGrid|Bu değer tüm UI çerçeveleri için aynıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|Bu özelliğin değeri her zaman doğru olmalıdır. Bu, veri kılavuzu denetiminin her zaman [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacının içerik görünümünde olması gerektiği anlamına gelir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Bu özelliğin değeri her zaman doğru olmalıdır. Bu, veri kılavuzu denetiminin her zaman [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacının denetim görünümünde olması gerektiği anlamına gelir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Notlara bakın.|Denetim, klavye odağı alamıyorsa, bu özelliği desteklemesi gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Notlara bakın.|Statik bir metin etiketi varsa, bu özellik bu denetimin bir başvurusunu kullanıma sunmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"veri kılavuzu"|DataGrid denetim türüne karşılık gelen yerelleştirilmiş dize.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlara bakın.|Veri kılavuzu denetimi genellikle statik metin etiketinden `Name` özelliğinin değerini alır. Bir statik metin etiketi yoksa, uygulama geliştiricisi `Name` özelliği için bir değer atamalıdır. `Name` özelliğinin değeri hiçbir koşulda düzenleme denetiminin metin içeriği olmamalıdır.|  
  
## <a name="required-ui-automation-control-patterns"></a>Gerekli UI Otomasyonu Denetim desenleri  
 Aşağıdaki tabloda tüm veri kılavuzu denetimleri tarafından desteklenmesi gereken denetim desenleri listelenmektedir. Denetim desenleri hakkında daha fazla bilgi için bkz. [UI Otomasyonu Denetim desenlerine genel bakış](ui-automation-control-patterns-overview.md).  
  
|Denetim deseninin|Destek|Notlar|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider>|Evet|Veri kılavuzu denetimi her zaman kılavuz denetim modelini destekler çünkü bu öğe bir kılavuzda yer alan meta veriler içerir.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Şekline|Veri kılavuzunu kaydırma özelliği içeriğe ve kaydırma çubuklarının mevcut olup olmamasına bağlıdır.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Şekline|Veri kılavuzunu seçme özelliği içeriğe bağlıdır.|  
|<xref:System.Windows.Automation.Provider.ITableProvider>|Evet|Veri kılavuzu denetimi her zaman alt ağacı içinde bir üst bilgiye sahiptir, böylece tablo Denetim deseninin desteklenmesi gerekir.|  
  
 Veri kılavuzu kapsayıcıları içindeki veri öğeleri en az bir destekdir:  
  
- Seçim öğesi denetim deseninin (veri kılavuzu seçilebilir ise)  
  
- Kaydırma öğesi denetim deseninin (veri kılavuzu kaydırılabilir ise)  
  
- Grid öğesi denetim deseninin  
  
- Tablo Öğesi denetim deseni  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyon olayları  
 Aşağıdaki tabloda tüm veri kılavuzu denetimleri tarafından desteklenmesi gereken [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayları listelenmektedir. Olaylar hakkında daha fazla bilgi için bkz. [UI Otomasyonu olaylarına genel bakış](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayı|Destek|Notlar|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>.|Gerekli|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>.|Gerekli|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent>|Şekline|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.MultipleViewPatternIdentifiers.CurrentViewProperty>.|Şekline|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>.|Şekline|Denetim, kaydırma modelini destekliyorsa, bu olayı desteklemesi gerekir.|  
|özellik değişti olayı <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty>.|Şekline|Denetim, kaydırma modelini destekliyorsa, bu olayı desteklemesi gerekir.|  
|özellik değişti olayı <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty>.|Şekline|Denetim, kaydırma modelini destekliyorsa, bu olayı desteklemesi gerekir.|  
|özellik değişti olayı <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty>.|Şekline|Denetim, kaydırma modelini destekliyorsa, bu olayı desteklemesi gerekir.|  
|özellik değişti olayı <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>.|Şekline|Denetim, kaydırma modelini destekliyorsa, bu olayı desteklemesi gerekir.|  
|özellik değişti olayı <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty>.|Şekline|Denetim, kaydırma modelini destekliyorsa, bu olayı desteklemesi gerekir.|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Gerekli|Yok.|  
  
## <a name="date-grid-control-type-example"></a>Tarih kılavuz denetim türü örneği  
 Aşağıdaki görüntüde DataGrid denetim türünü uygulayan bir liste görünümü denetimi gösterilmektedir.  
  
 ![İki veri öğesi içeren liste görünümü denetiminin grafiği](./media/uiauto-data-grid-detailed.GIF "uiauto_data_grid_detailed")  
  
 Liste görünümü denetimiyle ilgili olan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacının denetim görünümü ve içerik görünümü aşağıda görüntülenmektedir. Her Otomasyon öğesi için Denetim desenleri parantez içinde gösterilir.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç denetimi görünümü|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı-Içerik görünümü|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|<ul><li>DataGrid (tablo, kılavuz, seçim)</li><li>Üst bilgi<br /><br /> <ul><li>HeaderItem "Name" (Invoke)</li><li>HeaderItem "değiştirilme tarihi" (Invoke)</li><li>HeaderItem "size" (Invoke)</li></ul></li><li>"Contoso" grubu (TableItem, GridItem, SelectionItem, Table *, Grid\*)<br /><br /> <ul><li>DataItem "accounts. doc" (SelectionItem, Invoke, TableItem\*, GridItem\*)</li><li>DataItem "accounts. doc" (SelectionItem, Invoke, TableItem\*, GridItem\*)</li></ul></li></ul>|<ul><li>DataGrid (tablo, kılavuz, seçim)</li><li>"Contoso" grubu (TableItem, GridItem, SelectionItem, Table *, Grid\*)<br /><br /> <ul><li>DataItem "accounts. doc" (SelectionItem, Invoke, TableItem\*, GridItem\*)</li><li>DataItem "accounts. doc" (SelectionItem, Invoke, TableItem\*, GridItem\*)</li></ul></li></ul>|  
  
 Önceki örnekte \* birden çok denetim düzeyi içeren bir DataGrid gösterilmektedir. Grup ("contoso") denetimi iki DataItem denetimi içerir ("accounts. doc" ve "accounts borçları. doc"). DataGrid/GridItem çifti, bir çiftin farklı bir düzeyde bağımsızdır. Bir grup altındaki DataItem denetimleri, basit veri öğeleri yerine seçilebilir nesneler olarak daha net bir şekilde sunulmasını sağlayan bir ListItem denetim türü olarak da gösterilebilir. Bu örnek, gruplandırılmış veri öğelerinin alt öğelerini içermez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.ControlType.DataGrid>
- [UI Otomasyonu Denetim Türlerine Genel Bakış](ui-automation-control-types-overview.md)
- [UI Otomasyonuna Genel Bakış](ui-automation-overview.md)
