---
title: DataGrid Denetim Türü için UI Otomasyon Desteği
description: DataGrid denetim türü için UI Otomasyonu desteği hakkında bilgi alın. Gerekli ağaç yapısını, özellikleri, denetim desenlerini ve olayları öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- Data Grid control type
- control types, Data Grid
- UI Automation, Data Grid control type
ms.assetid: a3db4a3f-feb5-4e5f-9b42-aae7fa816e8a
ms.openlocfilehash: 13f265e414383e646f3e138feb890661fa01e2de
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167999"
---
# <a name="ui-automation-support-for-the-datagrid-control-type"></a>DataGrid Denetim Türü için UI Otomasyon Desteği
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konuda [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] , DataGrid denetim türü için destek hakkında bilgi sağlanır. ' De [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , bir denetim türü, özelliği kullanmak için bir denetimin uyması gereken koşullar kümesidir `ControlType` . Koşullar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , ağaç yapısı, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerleri ve Denetim desenleri için özel kurallar içerir.  
  
 DataGrid denetim türü, bir kullanıcının sütunlarda temsil edilen meta verileri içeren öğelerle kolayca çalışmasına olanak sağlar. Veri kılavuzu denetimlerinde bu öğeler hakkındaki öğe ve bilgi sütunlarının satırları vardır. Microsoft Vista Explorer 'daki liste görünümü denetimi, DataGrid denetim türünü destekleyen bir örnektir.  
  
 Aşağıdaki bölümler, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] DataGrid denetim türü için gerekli ağaç yapısını, özellikleri, denetim desenlerini ve olayları tanımlar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Gereksinimler, Win32 veya Windows Forms tüm veri kılavuzu denetimleri için geçerlidir [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] .  
  
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyonu ağaç yapısı  
 Aşağıdaki tabloda, veri kılavuzu denetimleriyle ilgili ağacın denetim görünümü ve içerik görünümü gösterilmektedir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ve her görünümde nelerin yer aldığı açıklanmaktadır. Ağaç hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [UI Otomasyon ağacına genel bakış](ui-automation-tree-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Ağaç denetimi görünümü|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Ağaç-Içerik görünümü|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|DataGrid<br /><br /> <ul><li>Üst bilgi (0, 1 veya 2)<br /><br /> <ul><li>HeaderItem (sütun veya satır sayısı)</li></ul></li><li>DataItem (0 veya daha fazla; hiyerarşide yapılandırılabilir)</li></ul>|DataGrid<br /><br /> -DataItem (0 veya daha fazla; hiyerarşide yapılandırılabilir)|  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon Özellikleri  
 Aşağıdaki tabloda, değeri veya tanımı özellikle veri kılavuzu denetimleriyle ilgili olan özellikler listelenmiştir. Özellikler hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [Istemciler Için UI Otomasyon özellikleri](ui-automation-properties-for-clients.md).  
  
|Özellik|Değer|Notlar|  
|--------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlara bakın.|Bu özelliğin değerinin bir uygulamadaki tüm denetimlerde benzersiz olması gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlara bakın.|Tüm denetimi içeren en dıştaki dikdörtgen.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Notlara bakın.|Sınırlayıcı bir dikdörtgen varsa desteklenir. Sınırlayıcı dikdörtgenin içindeki her nokta tıklatılabilir ise ve özelleştirilmiş isabet testi gerçekleştirirseniz ve ardından tıklatılabilir bir nokta sağlayabilirsiniz.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|DataGrid|Bu değer tüm UI çerçeveleri için aynıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Doğru|Bu özelliğin değeri her zaman doğru olmalıdır. Bu, veri kılavuzu denetiminin her zaman ağacın içerik görünümünde olması gerektiği anlamına gelir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Doğru|Bu özelliğin değeri her zaman doğru olmalıdır. Bu, veri kılavuzu denetiminin her zaman ağacın denetim görünümünde olması gerektiği anlamına gelir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Notlara bakın.|Denetim, klavye odağı alamıyorsa, bu özelliği desteklemesi gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Notlara bakın.|Statik bir metin etiketi varsa, bu özellik bu denetimin bir başvurusunu kullanıma sunmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"veri kılavuzu"|DataGrid denetim türüne karşılık gelen yerelleştirilmiş dize.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlara bakın.|Veri kılavuzu denetimi genellikle `Name` bir statik metin etiketinden özelliğin değerini alır. Bir statik metin etiketi yoksa, uygulama geliştiricisi özelliği için bir değer atamanız gerekir `Name` . Özelliğin değeri hiçbir koşulda `Name` düzenleme denetiminin metin içeriği olmamalıdır.|  
  
## <a name="required-ui-automation-control-patterns"></a>Gerekli UI Otomasyonu Denetim desenleri  
 Aşağıdaki tabloda tüm veri kılavuzu denetimleri tarafından desteklenmesi gereken denetim desenleri listelenmektedir. Denetim desenleri hakkında daha fazla bilgi için bkz. [UI Otomasyonu Denetim desenlerine genel bakış](ui-automation-control-patterns-overview.md).  
  
|Denetim deseninin|Destek|Notlar|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider>|Yes|Veri kılavuzu denetimi her zaman kılavuz denetim modelini destekler çünkü bu öğe bir kılavuzda yer alan meta veriler içerir.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Şekline|Veri kılavuzunu kaydırma özelliği içeriğe ve kaydırma çubuklarının mevcut olup olmamasına bağlıdır.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Şekline|Veri kılavuzunu seçme özelliği içeriğe bağlıdır.|  
|<xref:System.Windows.Automation.Provider.ITableProvider>|Yes|Veri kılavuzu denetimi her zaman alt ağacı içinde bir üst bilgiye sahiptir, böylece tablo Denetim deseninin desteklenmesi gerekir.|  
  
 Veri kılavuzu kapsayıcıları içindeki veri öğeleri en az bir destekdir:  
  
- Seçim öğesi denetim deseninin (veri kılavuzu seçilebilir ise)  
  
- Kaydırma öğesi denetim deseninin (veri kılavuzu kaydırılabilir ise)  
  
- Grid öğesi denetim deseninin  
  
- Tablo Öğesi denetim deseni  
  
<a name="Required_UI_Automation_Events"></a>
## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyon olayları  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tüm veri kılavuzu denetimleri tarafından desteklenmesi gereken olaylar listelenmektedir. Olaylar hakkında daha fazla bilgi için bkz. [UI Otomasyonu olaylarına genel bakış](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Olay|Destek|Notlar|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>özellik değişti olayı.|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>özellik değişti olayı.|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>özellik değişti olayı.|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent>|Şekline|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers.CurrentViewProperty>özellik değişti olayı.|Şekline|Hiçbiri|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>özellik değişti olayı.|Şekline|Denetim, kaydırma modelini destekliyorsa, bu olayı desteklemesi gerekir.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty>özellik değişti olayı.|Şekline|Denetim, kaydırma modelini destekliyorsa, bu olayı desteklemesi gerekir.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty>özellik değişti olayı.|Şekline|Denetim, kaydırma modelini destekliyorsa, bu olayı desteklemesi gerekir.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty>özellik değişti olayı.|Şekline|Denetim, kaydırma modelini destekliyorsa, bu olayı desteklemesi gerekir.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>özellik değişti olayı.|Şekline|Denetim, kaydırma modelini destekliyorsa, bu olayı desteklemesi gerekir.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty>özellik değişti olayı.|Şekline|Denetim, kaydırma modelini destekliyorsa, bu olayı desteklemesi gerekir.|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Gerekli|Hiçbiri|  
  
## <a name="date-grid-control-type-example"></a>Tarih kılavuz denetim türü örneği  
 Aşağıdaki görüntüde DataGrid denetim türünü uygulayan bir liste görünümü denetimi gösterilmektedir.  
  
 ![İki veri öğesi içeren liste görünümü denetiminin grafiği](./media/uiauto-data-grid-detailed.GIF "uiauto_data_grid_detailed")  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Liste görünümü denetimiyle ilgili olan ağacın denetim görünümü ve içerik görünümü aşağıda gösterilir. Her Otomasyon öğesi için Denetim desenleri parantez içinde gösterilir.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Ağaç denetimi görünümü|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Ağaç-Içerik görünümü|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|<ul><li>DataGrid (tablo, kılavuz, seçim)</li><li>Üst bilgi<br /><br /> <ul><li>HeaderItem "Name" (Invoke)</li><li>HeaderItem "değiştirilme tarihi" (Invoke)</li><li>HeaderItem "size" (Invoke)</li></ul></li><li>"Contoso" grubu (TableItem, GridItem, SelectionItem, Table *, Grid \* )<br /><br /> <ul><li>DataItem "accounts Receivable.doc" (SelectionItem, Invoke, TableItem \* , GridItem \* )</li><li>DataItem "accounts Payable.doc" (SelectionItem, Invoke, TableItem \* , GridItem \* )</li></ul></li></ul>|<ul><li>DataGrid (tablo, kılavuz, seçim)</li><li>"Contoso" grubu (TableItem, GridItem, SelectionItem, Table *, Grid \* )<br /><br /> <ul><li>DataItem "accounts Receivable.doc" (SelectionItem, Invoke, TableItem \* , GridItem \* )</li><li>DataItem "accounts Payable.doc" (SelectionItem, Invoke, TableItem \* , GridItem \* )</li></ul></li></ul>|  
  
 \*Önceki örnekte, birden çok denetim düzeyi içeren bir DataGrid gösterilmektedir. Grup ("contoso") denetimi iki DataItem denetimi içerir ("hesaplar Receivable.doc" ve "hesaplar Payable.doc"). DataGrid/GridItem çifti, bir çiftin farklı bir düzeyde bağımsızdır. Bir grup altındaki DataItem denetimleri, basit veri öğeleri yerine seçilebilir nesneler olarak daha net bir şekilde sunulmasını sağlayan bir ListItem denetim türü olarak da gösterilebilir. Bu örnek, gruplandırılmış veri öğelerinin alt öğelerini içermez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.ControlType.DataGrid>
- [UI Otomasyon Denetim Türlerine Genel Bakış](ui-automation-control-types-overview.md)
- [UI Otomasyonuna Genel Bakış](ui-automation-overview.md)
