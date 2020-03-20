---
title: DataGrid Denetim Türü için UI Otomasyon Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- Data Grid control type
- control types, Data Grid
- UI Automation, Data Grid control type
ms.assetid: a3db4a3f-feb5-4e5f-9b42-aae7fa816e8a
ms.openlocfilehash: 69532c9836876c25e9f31395213b1a89e0307dcd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179796"
---
# <a name="ui-automation-support-for-the-datagrid-control-type"></a>DataGrid Denetim Türü için UI Otomasyon Desteği
> [!NOTE]
> Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır. Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu, [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] DataGrid denetim türü için destek hakkında bilgi sağlar. Denetim [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]türü, `ControlType` özelliği kullanmak için denetimin karşılaması gereken koşullar kümesidir. Koşullar, ağaç yapısı, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerleri ve denetim desenleri için özel yönergeler içerir.  
  
 DataGrid denetim türü, kullanıcının sütunlarda temsil edilen meta verileri içeren öğelerle kolayca çalışmasını sağlar. Veri ızgarası denetimlerinde bu öğelerle ilgili öğeler ve bilgi sütunları satırları vardır. Microsoft Vista Explorer'daki Liste Görünümü denetimi, DataGrid denetim türünü destekleyen bir örnektir.  
  
 Aşağıdaki bölümlerde DataGrid denetim türü için gerekli [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısı, özellikleri, denetim desenleri ve olayları tanımlanır. Gereksinimler, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Win32 veya [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]Windows Forms olsun, tüm veri ızgara denetimleri için geçerlidir.  
  
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyon Ağaç Yapısı  
 Aşağıdaki tablo, veri ızgara denetimleri ile [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ilgili denetim görünümü ve ağacın içerik görünümünü görüntüler ve her görünümde nelerin bulunabileceğini açıklar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ağaç hakkında daha fazla bilgi için [UI Automation Tree Genel Bakış'a](ui-automation-tree-overview.md)bakın.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Ağaç - Kontrol Görünümü|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Ağaç - İçerik Görünümü|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|DataGrid<br /><br /> <ul><li>Üstbilgi (0, 1 veya 2)<br /><br /> <ul><li>Üstbilgi Öğesi (sütun veya satır sayısı)</li></ul></li><li>DataItem (0 veya daha fazla; hiyerarşi içinde yapılandırılabilir)</li></ul>|DataGrid<br /><br /> - DataItem (0 veya daha fazla; hiyerarşi içinde yapılandırılabilir)|  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon Özellikleri  
 Aşağıdaki tablo, değeri veya tanımı özellikle veri ızgara denetimleri ile ilgili özellikleri listeler. Özellikler hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] daha fazla bilgi [için, Müşteriler için Kullanıcı Arabirimi Otomasyon Özellikleri'ne](ui-automation-properties-for-clients.md)bakın.  
  
|Özellik|Değer|Notlar|  
|--------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlara bakın.|Bu özelliğin değeri, bir uygulamadaki tüm denetimler arasında benzersiz olmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlara bakın.|Tüm denetimi içeren en dıştaki dikdörtgen.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Notlara bakın.|Sınırlayıcı bir dikdörtgen varsa desteklenir. Sınırlayıcı dikdörtgen içindeki her nokta tıklatılabilir değilse ve özel isabet testi gerçekleştirin, sonra geçersiz kılınve tıklanabilir bir nokta sağlayın.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|DataGrid|Bu değer tüm Ara bilgi arabirimi çerçeveleri için aynıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|Bu özelliğin değeri her zaman Doğru olmalıdır. Bu, veri ızgaradenetiminin her zaman [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacın içerik görünümünde olması gerektiği anlamına gelir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Bu özelliğin değeri her zaman Doğru olmalıdır. Bu, veri ızgaradenetiminin her zaman [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacın denetim görünümünde olması gerektiği anlamına gelir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Notlara bakın.|Denetim klavye odağı alabiliyorsa, bu özelliği desteklemesi gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Notlara bakın.|Statik bir metin etiketi varsa, bu özellik bu denetime bir başvuru göstermelidir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"veri ızgarası"|DataGrid denetim türüne karşılık gelen yerelleştirilmiş dize.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlara bakın.|Veri ızgarası denetimi genellikle statik `Name` bir metin etiketinden özelliğinin değerini alır. Statik metin etiketi yoksa, uygulama geliştiricisinin özellik için bir `Name` değer ataması gerekir. `Name` Özelliğin değeri hiçbir zaman edit denetiminin metin içeriği olmamalıdır.|  
  
## <a name="required-ui-automation-control-patterns"></a>Gerekli UI Otomasyon Kontrol Desenleri  
 Aşağıdaki tablo, tüm veri ızgara denetimleri tarafından desteklenmesi gereken denetim desenleri listeler. Denetim desenleri hakkında daha fazla bilgi için [UI Otomasyon Denetim Modellerine Genel Bakış'a](ui-automation-control-patterns-overview.md)bakın.  
  
|Kontrol Deseni|Destek|Notlar|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider>|Evet|Veri ızgarası denetimi nin kendisi her zaman Izgara denetim deseni destekler, çünkü bir ızgarada ortaya konan meta verileri içeren öğeler.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|-sına bağ -lıdır|Veri ızgarasını kaydırma yeteneği içeriğe ve kaydırma çubuklarının bulunup bulunmadığına bağlıdır.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|-sına bağ -lıdır|Veri ızgarasını seçebilme özelliği içeriğe bağlıdır.|  
|<xref:System.Windows.Automation.Provider.ITableProvider>|Evet|Veri ızgarası denetiminin her zaman alt ağacıiçinde bir üstbilgi vardır, bu nedenle Tablo denetim deseni desteklenmelidir.|  
  
 Veri ızgara kapsayıcıları içindeki veri öğeleri en azından destekleyecektir:  
  
- Seçim Öğesi denetim deseni (veri ızgarası seçilebilirse)  
  
- Öğe denetim deseni kaydırma (veri ızgarası kaydırılabilirse)  
  
- Izgara Öğesi kontrol deseni  
  
- Tablo Öğesi denetim deseni  
  
<a name="Required_UI_Automation_Events"></a>
## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyon Etkinlikleri  
 Aşağıdaki tablo, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tüm veri ızgara denetimleri tarafından desteklenmesi gereken olayları listeler. Etkinlikler hakkında daha fazla bilgi için [UI Otomasyon Etkinliklerine Genel Bakış'a](ui-automation-events-overview.md)bakın.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Olay|Destek|Notlar|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>özellik değiştirilen olay.|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>özellik değiştirilen olay.|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>özellik değiştirilen olay.|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent>|-sına bağ -lıdır|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|None|  
|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers.CurrentViewProperty>özellik değiştirilen olay.|-sına bağ -lıdır|None|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>özellik değiştirilen olay.|-sına bağ -lıdır|Denetim Kaydırma deseni destekliyorsa, bu olayı desteklemesi gerekir.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty>özellik değiştirilen olay.|-sına bağ -lıdır|Denetim Kaydırma deseni destekliyorsa, bu olayı desteklemesi gerekir.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty>özellik değiştirilen olay.|-sına bağ -lıdır|Denetim Kaydırma deseni destekliyorsa, bu olayı desteklemesi gerekir.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty>özellik değiştirilen olay.|-sına bağ -lıdır|Denetim Kaydırma deseni destekliyorsa, bu olayı desteklemesi gerekir.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>özellik değiştirilen olay.|-sına bağ -lıdır|Denetim Kaydırma deseni destekliyorsa, bu olayı desteklemesi gerekir.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty>özellik değiştirilen olay.|-sına bağ -lıdır|Denetim Kaydırma deseni destekliyorsa, bu olayı desteklemesi gerekir.|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Gerekli|None|  
  
## <a name="date-grid-control-type-example"></a>Tarih Grid Kontrol Türü Örneği  
 Aşağıdaki resimde, DataGrid denetim türünü uygulayan bir Liste Görünümü denetimi gösterin.  
  
 ![İki veri öğesiyle Liste Görünümü denetiminin grafiği](./media/uiauto-data-grid-detailed.GIF "uiauto_data_grid_detailed")  
  
 Liste Görünümü denetimiyle ilgili [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacın denetim görünümü ve içerik görünümü aşağıda gösterilmiştir. Her otomasyon öğesi için kontrol desenleri parantez içinde gösterilir.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Ağaç - Kontrol Görünümü|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Ağaç - İçerik Görünümü|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|<ul><li>DataGrid (Tablo, Kılavuz, Seçim)</li><li>Üst bilgi<br /><br /> <ul><li>HeaderItem "Ad" (Çağırma)</li><li>Üstbilgi Öğe "Değiştirilen Tarih" (Çağrıl)</li><li>HeaderItem "Boyut" (Çağırma)</li></ul></li><li>Grup "Contoso" (TableItem, GridItem, SelectionItem,\*Tablo*, Izgara)<br /><br /> <ul><li>DataItem "Alacak Hesapları.doc" (SelectionItem, Invoke, TableItem\*, GridItem\*)</li><li>DataItem "Accounts Payable.doc" (SelectionItem,\*Invoke,\*TableItem , GridItem )</li></ul></li></ul>|<ul><li>DataGrid (Tablo, Kılavuz, Seçim)</li><li>Grup "Contoso" (TableItem, GridItem, SelectionItem,\*Tablo*, Izgara)<br /><br /> <ul><li>DataItem "Alacak Hesapları.doc" (SelectionItem, Invoke, TableItem\*, GridItem\*)</li><li>DataItem "Accounts Payable.doc" (SelectionItem,\*Invoke,\*TableItem , GridItem )</li></ul></li></ul>|  
  
 \*Önceki örnek, birden çok denetim düzeyi içeren bir DataGrid gösterir. Grup ("Contoso") denetimi iki DataItem denetimi ("Alacak Hesapları.doc" ve "Ödenecek Hesaplar.doc") içerir. DataGrid/GridItem çifti başka bir düzeydeki bir çiftden bağımsızdır. Grup altındaki DataItem denetimleri, basit veri öğeleri olarak değil, seçilebilir nesneler olarak daha açık bir şekilde sunulmasını sağlayan bir ListItem denetim türü olarak da ortaya çıkabilir. Bu örnek, gruplanmış veri öğelerinin alt öğelerini içermez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.ControlType.DataGrid>
- [UI Otomasyonu Denetim Türlerine Genel Bakış](ui-automation-control-types-overview.md)
- [UI Otomasyonuna Genel Bakış](ui-automation-overview.md)
