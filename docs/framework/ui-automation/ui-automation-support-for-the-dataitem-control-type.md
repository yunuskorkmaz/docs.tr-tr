---
title: "DataItem Denetim Türü için UI Otomasyon Desteği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, Data Item control type
- Data Item control type
- control types, Data Item
ms.assetid: 181708fd-2595-4c43-9abd-75811627d64c
caps.latest.revision: "36"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 937a75a229685f76816a123ad863f5a22f6043a6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ui-automation-support-for-the-dataitem-control-type"></a>DataItem Denetim Türü için UI Otomasyon Desteği
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu aşağıdakiler hakkında bilgi sağlar [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] DataItem denetim türü için destek. İçinde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] denetim türü bir denetimi kullanmak için karşılaması gereken koşulları kümesidir <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> özelliği. Koşullar özel yönergeleri dahil [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısı, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerlerini ve denetim düzenleri.  
  
 Kişiler listesindeki bir girdi, bir veri öğesi denetimini örneğidir. Bir veri öğesi denetimini son kullanıcının ilgi bilgilerini içerir. Daha zengin bilgi içerdiği için basit bir liste öğesi daha karmaşıktır.  
  
 Aşağıdaki bölümlerde gerekli tanımlamak [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısı, özellikleri, Denetim desenleri ve olayları DataItem denetim türü için. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Gereksinimleri tüm verilerin olup öğesi denetimlerini geçerlidir [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], veya [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyon ağaç yapısı  
 Denetim Görünüm ve içerik görünümünü aşağıdaki tabloda gösterilmektedir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] veri öğesi için ilgili ağaç denetler ve her bir görünümde bulunabilir açıklar. Hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç bkz [UI Otomasyon ağacına genel bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Ağaç - denetim görünümü|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Ağaç - içerik görünümü|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|DataItem<br /><br /> -Değişir (0 veya daha çok; hiyerarşisinde yapılandırılmış)|DataItem<br /><br /> -Değişir (0 veya daha çok; hiyerarşisinde yapılandırılmış)|  
  
 Bir veri öğesi öğesi bir veri kılavuzunda çeşitli nesneleri başka bir katman veri öğeleri ya da metin, görüntü gibi belirli kılavuz öğeleri dahil olmak üzere, ana bilgisayar veya denetimleri düzenleyin. Veri öğesi öğesi belirli nesne rolü varsa, belirli bir denetim türünü öğe açılmamalıdır; Örneğin, bir ListItem denetim türü için kılavuzundaki seçilebilir veri öğesi.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon özellikleri  
 Aşağıdaki tabloda, değer veya tanımı veri öğesi denetimleri için özellikle ilgili özellikleri listeler. Hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri, görmek [istemciler için UI Otomasyon özellikleri](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|Özellik|Değer|Notlar|  
|--------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlarına bakın.|Bu özelliğin değeri bir uygulamadaki tüm denetimler arasında benzersiz olması gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlarına bakın.|Tam denetimi içeren en dıştaki dikdörtgen.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Notlarına bakın.|Bir sınırlayıcı dikdörtgenini ise desteklenir. Yoksa her sınırlayıcı dikdörtgenini içinde tıklanabilir noktasıdır ve özelleştirilmiş isabet testleri, gerçekleştirme sonra geçersiz kılabilir ve tıklatılabilir noktası sağlar.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|DataItem|Bu değer tüm UI çerçeveler için aynıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Doğru|Veri öğesi denetim her zaman içerik olmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Doğru|Veri öğesi denetimi her zaman bir denetim olmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Notlarına bakın.|Klavye odağı denetimi alamıyorsa, bu özelliği desteklemelidir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemStatusProperty>|Notlarına bakın.|Dinamik olarak güncelleştirilen durumu denetimi içeriyorsa, bu özellik öğe durumunun değiştiğini yardımcı teknoloji güncelleştirmeleri alabilmesi desteklenmelidir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemTypeProperty>|Notlarına bakın.|Bu öğeyi temsil eden nesnesini son kullanıcıya ilettiği dize değeridir. Örnek "Medya dosyası" veya "Başvurun" verilebilir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Veri öğesi denetimleri statik metin etiketi yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"veri öğesi"|DataItem denetim türü için karşılık gelen yerelleştirilmiş dize.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlarına bakın.|Veri öğesi denetimi her zaman hangi kullanıcı öğesinin en anlamsal tanımlayıcısı olarak ilişkilendirirsiniz için ilişkili bir birincil metin öğesi içeriyor.|  
  
<a name="_Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Gerekli UI Otomasyon denetim düzenleri  
 Aşağıdaki tabloda [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] denetim düzenleri tüm veri öğesi denetimleri tarafından desteklenmesi için gerekli. Denetim desenleri hakkında daha fazla bilgi için bkz: [UI Otomasyon denetim düzenlerine genel bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Denetim düzeni|Destek|Notlar|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Bağlıdır|Veri öğesi genişletilmiş ya da göstermek ve bilgi gizlemek için daraltılmış, genişletme daraltma desenin desteklenmesi gerekir.|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider>|Bağlıdır|Veri öğeleri koleksiyonu dağınık şekilde gittiğinizde için-öğe olabilecek bir kapsayıcıya kullanılabilir olduğunda veri öğeleri kılavuz öğesi düzenini destekler.|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|Bağlıdır|Tüm veri öğelerinin kendi veri kapsayıcısı ekranda sığmayacak daha fazla öğe varsa kaydırma öğesi düzeni görünümüyle içine kaydırılan becerisini de destekler.|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Evet|Tüm veri öğelerinin öğe seçildiğinde belirtmek için seçim öğesi desen desteklemesi gerekir.|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider>|Bağlıdır|Veri öğesi içinde veri kılavuzu denetim türü içeriyorsa bu deseni destekleyecektir.|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|Bağlıdır|Veri öğesi aracılığıyla geçiş sırasında bir durum içeriyorsa.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Bağlıdır|Veri öğesi'nin birincil metin düzenlenebilir ise değer düzenini desteklenmelidir.|  
  
<a name="Working_with_Data_Items_in_Large_Lists"></a>   
## <a name="working-with-data-items-in-large-lists"></a>Büyük listelerdeki veri öğeleri ile çalışma  
 Büyük listeleridir genellikle içinde sanallaştırılmış veri [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] performans yardımcı olmak için çerçeveler. UI Otomasyonu istemci bu nedeniyle kullanamazsınız [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] diğer öğe kapsayıcılarını için aynı şekilde tam ağaç içeriğini scrape için sorgu özelliği. Bir istemci öğe görünümüne gidin (veya tüm değerli seçenekleri göstermek için Denetim genişletin) veri öğesinden bilgileri tam kümesi erişme önce.  
  
 Çağrılırken `SetFocus` üzerinde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] öğesi veri öğesi için [!INCLUDE[TLA#tla_winexpl](../../../includes/tlasharptla-winexpl-md.md)] durumu başarıyla dönün ve veri öğesi alt ağacı içinde düzenleme için ayarlanacak odak neden.  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyon olayları  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayları tüm veri öğesi denetimleri tarafından desteklenmesi gerekir. Olaylar hakkında daha fazla bilgi için bkz: [UI Otomasyonu olaylarına genel bakış](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Olay|Destek|Notlar|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>özellik değişti olayı.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>özellik değişti olayı.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>özellik değişti olayı.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>özellik değişti olayı.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|Yok.|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Bağlıdır|Yok.|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty>özellik değişti olayı.|Bağlıdır|Yok.|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>|Gerekli|Yok.|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|Gerekli|Yok.|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Gerekli|Yok.|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>özellik değişti olayı.|Bağlıdır|Yok.|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty>özellik değişti olayı.|Bağlıdır|Yok.|  
  
<a name="Data_Item_Control_Type_Example"></a>   
## <a name="dataitem-control-type-example"></a>DataItem denetim türü örneği  
 Aşağıdaki resimde bir liste görünümü denetiminde sütunları için zengin bilgi desteğiyle DataItem denetim türü gösterilmektedir.  
  
 ![İki veri öğeleri içeren bir liste görünümü denetimi, grafik](../../../docs/framework/ui-automation/media/uiauto-data-grid-detailed.GIF "uiauto_data_grid_detailed")  
  
 Denetim ve içerik görünümünde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] veri öğesi denetimine ilgilidir ağacı altında görüntülenir. Her Otomasyon öğesi için Denetim desenleri parantez içinde görüntülenir. "Contoso" grubu ayrıca veri kılavuzu konak kontrolü kılavuzunun parçasıdır.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Ağaç - denetim görünümü|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Ağaç - içerik görünümü|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|-Grup "Contoso" (tablo, Kılavuzu)<br />-DataItem "Receivable.doc hesapları" (Tableıtem, GridItem, SelectionItem, çağırma)<br />-İmage "Hesapları Receivable.doc"<br />-"Name" (Tableıtem, GridItem, değer "Hesapları Receivable.doc") Düzenle<br />-Düzenle "Değiştirilme tarihi" (Tableıtem, GridItem, değer "25/8/2006 3:29 PM")<br />-"Boyutu" (GridItem, Tableıtem, değer "11.0 KB) Düzenle<br />-DataItem "Payable.doc hesapları" (Tableıtem, GridItem, SelectionItem, çağırma)<br />-   ...|-Grup "Contoso" (tablo, Kılavuzu)<br />-DataItem "Receivable.doc hesapları" (Tableıtem, GridItem, SelectionItem, çağırma)<br />-İmage "Hesapları Receivable.doc"<br />-"Name" (Tableıtem, GridItem, değer "Hesapları Receivable.doc") Düzenle<br />-Düzenle "Değiştirilme tarihi" (Tableıtem, GridItem, değer "25/8/2006 3:29 PM")<br />-"Boyutu" (GridItem, Tableıtem, değer "11.0 KB) Düzenle<br />-DataItem "Payable.doc hesapları" (Tableıtem, GridItem, SelectionItem, çağırma)<br />-   …|  
  
 Bir kılavuz seçilebilir öğelerin listesini temsil ediyorsa, karşılık gelen kullanıcı Arabirimi öğeleri DataItem denetim türü yerine ListItem denetim türü ile gösterilebilir. Önceki örnekte, bu tür SelectionItem denetim düzeni desteklediğinden bunları ListItem denetim türü olarak göstererek DataItem öğeleri ("Hesapları Receivable.doc" ve "Hesapları Payable.doc") grubu ("Contoso") altında geliştirilebilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Automation.ControlType.DataItem>  
 [UI Otomasyon denetim türlerine genel bakış](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [UI Otomasyon genel bakış](../../../docs/framework/ui-automation/ui-automation-overview.md)
