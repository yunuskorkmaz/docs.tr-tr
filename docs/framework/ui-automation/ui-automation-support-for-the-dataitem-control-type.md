---
title: DataItem Denetim Türü için UI Otomasyon Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Data Item control type
- Data Item control type
- control types, Data Item
ms.assetid: 181708fd-2595-4c43-9abd-75811627d64c
ms.openlocfilehash: ebc5f9a5b50766b9a49a9772469f8ae731f3aa4c
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57679404"
---
# <a name="ui-automation-support-for-the-dataitem-control-type"></a>DataItem Denetim Türü için UI Otomasyon Desteği
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu hakkında bilgi sağlar. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] DataItem denetim türü için destek. İçinde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] denetim türü bir denetim kullanmak için karşılaması gereken koşulları kümesidir <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> özelliği. Özel yönergeleri koşulları dahil [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısını [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerlerini ve denetim düzenleri.  
  
 Bir kişi listesindeki bir girdinin veri öğesi denetimi örneğidir. Bir veri öğesi denetimi bir son kullanıcının ilgi bilgileri içerir. Daha zengin bilgi içerdiğinden basit bir liste öğesi daha karmaşık bir işlemdir.  
  
 Aşağıdaki bölümlerde gerekli tanımlamak [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısı, özellikler, Denetim düzenleri ve olayları DataItem denetim türü için. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Gereksinimler için tüm veri olup olmadığını öğe denetimleri geçerli [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], veya [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyon ağaç yapısı  
 Aşağıdaki tablo denetimi ve içerik görünümünde gösterir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] veri öğesine aittir ağaç denetler ve her bir görünümde bulunabilir açıklar. Hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç bkz [UI Otomasyon ağacına genel bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ağaç - görünüm denetimi|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ağaç - içerik görünümü|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|DataItem<br /><br /> -Değişir (0 veya daha çok; hiyerarşisinde yapılandırılmış)|DataItem<br /><br /> -Değişir (0 veya daha çok; hiyerarşisinde yapılandırılmış)|  
  
 Bir veri öğesi öğesi bir veri kılavuzunda, çeşitli veri öğeleri veya metin, görüntü gibi belirli kılavuz öğeleri başka bir katmanı da dahil olmak üzere nesneleri, konak veya düzenleme denetimleri. Veri öğesi öğe belirli nesne rol varsa öğesi denetim türü olarak açılmamalıdır; Örneğin, bir ListItem denetim türü için kılavuzdaki seçilebilir veri öğesi.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon özellikleri  
 Aşağıdaki tabloda, değer veya tanımı veri öğesi denetimleri için özellikle ilgili özellikleri listeler. Hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri görmek [istemciler için UI Otomasyon özellikleri](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|Özellik|Değer|Notlar|  
|--------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlara bakın.|Bu özelliğin değerini bir uygulamadaki tüm denetimler arasında benzersiz olması gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlara bakın.|Tam denetimi içeren en dıştaki dikdörtgen.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Notlara bakın.|Sınırlayıcı bir dikdörtgen ise desteklenir. Değilse dikdörtgen içinde her bir nokta tıklanabilir ve özelleştirilmiş isabet sınaması, gerçekleştirmek sonra geçersiz kılmak ve tıklanabilir bir nokta sağlayamaz.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|DataItem|Bu değer tüm UI çerçeveleri için aynıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Doğru|Veri öğesi denetimi her zaman içerik olmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Doğru|Veri öğesi denetimi her zaman bir denetim olmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Notlara bakın.|Denetimin klavye odağı alamıyorsa, bu özelliği desteklemesi gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemStatusProperty>|Notlara bakın.|Bir denetimi dinamik olarak güncelleştirilen durumu içeriyorsa, bu özellik öğe durumu değiştiğinde bir yardımcı teknolojinin güncelleştirmelerini alabilmesi desteklenmelidir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemTypeProperty>|Notlara bakın.|Bu öğeyi temsil eden nesnesini son kullanıcıya ilettiği dize değeridir. "Medya dosyası" veya "Kişi" verilebilir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Veri öğesi denetimlerini bir statik metin etiketi yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"veri öğesi"|DataItem denetim türü için karşılık gelen yerelleştirilmiş bir dize.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlara bakın.|Veri öğesi denetimi her zaman hangi kullanıcı öğesinin en anlam tanımlayıcısı olarak ilişkilendirirsiniz için ilişkili bir birincil metin öğesi içerir.|  
  
<a name="_Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Gerekli UI Otomasyon denetim düzenleri  
 Aşağıdaki tabloda [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] denetim tüm veri öğesi denetimleri tarafından desteklenmesi için gereken desenleri. Denetim desenleri hakkında daha fazla bilgi için bkz: [UI Otomasyon denetim düzenlerine genel bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Denetim düzeni|Destek|Notlar|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Bağlıdır|Veri öğesi genişletilmiş veya daraltılmış göstermek ve gizlemek için genişletme daraltma desenin desteklenmesi gerekir.|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider>|Bağlıdır|Veri öğeleri koleksiyonu mekan taşınabilecek öğesi öğesi olan bir kapsayıcı içinde kullanılabilir duruma geldiğinde veri öğeleri kılavuz öğesi düzeni destekler.|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|Bağlıdır|Tüm veri öğeleri, kendi veri kapsayıcısı ekranda sığmazsa daha fazla öğe olduğunda görünümde kaydırma öğesi düzeni ile kaydırılan olanağını desteklemektedir.|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Evet|Tüm veri öğeleri bir öğe seçildiğinde belirtmek için seçim öğesi düzeni desteklemesi gerekir.|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider>|Bağlıdır|Veri öğesi bir veri kılavuzu denetim türü içinde yer alıyorsa bu düzen destekleyecektir.|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|Bağlıdır|Veri öğesi aracılığıyla geçiş sırasında uygulamaları bir durum varsa.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Bağlıdır|Birincil veri öğenin metni düzenlenebilir ise değer deseni desteklenmelidir.|  
  
<a name="Working_with_Data_Items_in_Large_Lists"></a>   
## <a name="working-with-data-items-in-large-lists"></a>Büyük listelerdeki veri öğeleri ile çalışma  
 Büyük listeleri, genellikle veri içinde sanallaştırıldı [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] performans yardımcı olmak için çerçeveleri. Bu nedenle, bir UI Otomasyonu istemci kullanamazsınız [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] diğer öğesi kapsayıcılarda alabilir ve aynı şekilde tam ağaç içeriğini scrape için sorgu özelliği. Bir istemci öğesi görünüme gidin (veya denetimin değerli tüm seçenekleri göstermek için genişletin) önce veri öğesi kümesini bilgi erişme.  
  
 Çağrılırken `SetFocus` üzerinde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] veri öğesi için öğe [!INCLUDE[TLA#tla_winexpl](../../../includes/tlasharptla-winexpl-md.md)] çalışması başarıyla dönün ve veri öğesi alt ağacı içinde düzenleme için ayarlanacak odak neden olur.  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyonu olayları  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayları tüm veri öğesi denetimleri tarafından desteklenmesi gerekir. Olaylar hakkında daha fazla bilgi için bkz. [UI Otomasyonu olaylarına genel bakış](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Olay|Destek|Notlar|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> özellik değişti olayı.|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> özellik değişti olayı.|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> özellik değişti olayı.|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty> özellik değişti olayı.|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Bağlıdır|Hiçbiri|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty> özellik değişti olayı.|Bağlıdır|Hiçbiri|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty> özellik değişti olayı.|Bağlıdır|Hiçbiri|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> özellik değişti olayı.|Bağlıdır|Hiçbiri|  
  
<a name="Data_Item_Control_Type_Example"></a>   
## <a name="dataitem-control-type-example"></a>DataItem denetim türü örneği  
 DataItem denetim türü sütunlar için zengin bilgiler desteği ile bir liste görünümü denetimi aşağıdaki resimde gösterilmektedir.  
  
 ![İki veri öğeleri ile bir liste görünümü denetimi grafik](../../../docs/framework/ui-automation/media/uiauto-data-grid-detailed.GIF "uiauto_data_grid_detailed")  
  
 Denetim ve içerik görünümünde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] veri öğesi denetimi için ilgili ağacı altında görüntülenir. Her Otomasyon öğesi için Denetim desenleri parantez içinde gösterilmektedir. "Contoso" Grup ayrıca veri Kılavuzu denetimi kılavuzunun bir parçasıdır.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ağaç - görünüm denetimi|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ağaç - içerik görünümü|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|-Grup "Contoso" (tablo, Kılavuzu)<br />-DataItem "Receivable.doc hesapları" (Tableıtem, GridItem SelectionItem, çağırma)<br />-İmage "Hesapları Receivable.doc"<br />-"Name" (Tableıtem, GridItem, değer "Hesapları Receivable.doc") Düzenle<br />-Düzenle "Değiştirilme tarihi" (Tableıtem, GridItem, değeri "25/8/2006 3:29 PM")<br />-"Boyutu" (GridItem, Tableıtem, değer "11.0 KB) Düzenle<br />-DataItem "Payable.doc hesapları" (Tableıtem, GridItem SelectionItem, çağırma)<br />-   ...|-Grup "Contoso" (tablo, Kılavuzu)<br />-DataItem "Receivable.doc hesapları" (Tableıtem, GridItem SelectionItem, çağırma)<br />-İmage "Hesapları Receivable.doc"<br />-"Name" (Tableıtem, GridItem, değer "Hesapları Receivable.doc") Düzenle<br />-Düzenle "Değiştirilme tarihi" (Tableıtem, GridItem, değeri "25/8/2006 3:29 PM")<br />-"Boyutu" (GridItem, Tableıtem, değer "11.0 KB) Düzenle<br />-DataItem "Payable.doc hesapları" (Tableıtem, GridItem SelectionItem, çağırma)<br />-   …|  
  
 Bir kılavuz seçilebilir öğeleri listesini temsil ediyorsa, karşılık gelen kullanıcı Arabirimi öğeleri DataItem denetim türü yerine ListItem denetim türüyle sunulabilir. Önceki örnekte, bu tür SelectionItem denetim düzeni desteklediğinden bunları ListItem denetim türlerini göstererek DataItem öğeleri ("Hesapları Receivable.doc" ve "Hesapları Payable.doc") grubu ("Contoso") altında geliştirilebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Automation.ControlType.DataItem>
- [UI Otomasyonu Denetim Türlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)
- [UI Otomasyonuna Genel Bakış](../../../docs/framework/ui-automation/ui-automation-overview.md)
