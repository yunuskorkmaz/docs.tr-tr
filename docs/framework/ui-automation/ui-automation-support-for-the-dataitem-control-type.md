---
title: DataItem Denetim Türü için UI Otomasyon Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Data Item control type
- Data Item control type
- control types, Data Item
ms.assetid: 181708fd-2595-4c43-9abd-75811627d64c
ms.openlocfilehash: d950783b91252f1bcbb1ff818aff5cf8472218b7
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789526"
---
# <a name="ui-automation-support-for-the-dataitem-control-type"></a>DataItem Denetim Türü için UI Otomasyon Desteği
> [!NOTE]
> Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu, DataItem denetim türü için [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] desteği hakkında bilgi sağlar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bir denetim türü, bir denetimin <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> özelliğini kullanmak için karşılaması gereken koşullar kümesidir. Koşullar, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısına yönelik özel yönergeler, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerleri ve Denetim desenleri içerir.  
  
 Kişiler listesindeki bir giriş, veri öğesi denetimine bir örnektir. Bir veri öğesi denetimi, son kullanıcıya ilgi çekici bilgiler içerir. Daha zengin bilgiler içerdiğinden basit liste öğesinden daha karmaşıktır.  
  
 Aşağıdaki bölümler, DataItem denetim türü için gerekli [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısını, özellikleri, denetim desenlerini ve olayları tanımlar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gereksinimler, [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], Win32 veya Windows Forms bakılmaksızın tüm veri öğesi denetimlerine uygulanır.  
  
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyonu ağaç yapısı  
 Aşağıdaki tabloda, veri öğesi denetimleriyle ilgili [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacının denetim görünümü ve içerik görünümü gösterilmektedir ve her görünümde nelerin yer aldığı açıklanmaktadır. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı hakkında daha fazla bilgi için bkz. [UI Otomasyon ağacına genel bakış](ui-automation-tree-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç denetimi görünümü|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı-Içerik görünümü|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|Çağrılabilir<br /><br /> -Değişir (0 veya daha fazla; hiyerarşide yapısal olarak yapılandırılabilir)|Çağrılabilir<br /><br /> -Değişir (0 veya daha fazla; hiyerarşide yapısal olarak yapılandırılabilir)|  
  
 Bir veri kılavuzundaki veri öğesi öğesi, başka bir veri öğeleri katmanı veya metin, resim veya düzenleme denetimleri gibi belirli kılavuz öğeleri dahil olmak üzere çeşitli nesneleri barındırabilirler. Veri öğesi öğesinin belirli bir nesne rolü varsa, öğe belirli bir denetim türü olarak kullanıma sunulmalıdır; Örneğin, kılavuzdaki seçilebilir bir veri öğesi için bir ListItem denetim türü.  
  
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon Özellikleri  
 Aşağıdaki tabloda, değeri veya tanımı özellikle veri öğesi denetimleriyle ilgili olan özellikler listelenmiştir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri hakkında daha fazla bilgi için bkz. [istemciler Için UI Otomasyon özellikleri](ui-automation-properties-for-clients.md).  
  
|Özellik|Değer|Notlar|  
|--------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlara bakın.|Bu özelliğin değerinin bir uygulamadaki tüm denetimlerde benzersiz olması gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlara bakın.|Tüm denetimi içeren en dıştaki dikdörtgen.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Notlara bakın.|Sınırlayıcı bir dikdörtgen varsa desteklenir. Sınırlayıcı dikdörtgenin içindeki her nokta tıklatılabilir ise ve özelleştirilmiş isabet testi gerçekleştirirseniz ve ardından tıklatılabilir bir nokta sağlayabilirsiniz.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Çağrılabilir|Bu değer tüm UI çerçeveleri için aynıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Doğru|Veri öğesi denetimi her zaman içerik olmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Doğru|Veri öğesi denetimi her zaman bir denetim olmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Notlara bakın.|Denetim, klavye odağı alamıyorsa, bu özelliği desteklemesi gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemStatusProperty>|Notlara bakın.|Denetim dinamik olarak güncelleştirilmekte olan durum içeriyorsa, bu özellik, öğenin durumu değiştiğinde yardımcı teknolojinin güncelleştirmeleri alabilmesi için desteklenmelidir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemTypeProperty>|Notlara bakın.|Bu, öğenin temsil ettiği temel nesneyi son kullanıcıya ileten dize değeridir. Örnekler şunlardır "medya dosyası" veya "kişi".|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Veri öğesi denetimlerinde statik metin etiketi yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"veri öğesi"|DataItem denetim türüne karşılık gelen yerelleştirilmiş dize.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlara bakın.|Veri öğesi denetimi her zaman, kullanıcının öğe için en anlamlı tanımlayıcı olarak ilişkilendirilebilmesi ile ilişkili bir birincil metin öğesi içerir.|  
  
## <a name="required-ui-automation-control-patterns"></a>Gerekli UI Otomasyonu Denetim desenleri  
 Aşağıdaki tabloda tüm veri öğesi denetimleri tarafından desteklenmesi gereken [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] Denetim desenleri listelenmektedir. Denetim desenleri hakkında daha fazla bilgi için bkz. [UI Otomasyonu Denetim desenlerine genel bakış](ui-automation-control-patterns-overview.md).  
  
|Denetim deseninin|Destek|Notlar|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Şekline|Bilgileri göstermek ve gizlemek için veri öğesi genişletilirse veya daraltılabilse, genişletme ve daraltma modelinin desteklenmesinin olması gerekir.|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider>|Şekline|Veri öğeleri, bir kapsayıcıda bir veri öğeleri koleksiyonu kullanıma hazır olan öğe ve öğe arasında gezilebilir olduğunda kılavuz öğe modelini destekleyecektir.|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|Şekline|Tüm veri öğeleri, veri kapsayıcısı ekrana sığmayacak kadar çok öğe olduğunda kaydırma öğesi düzeniyle görünüm içine kaydırılabilme özelliğini destekler.|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Evet|Tüm veri öğeleri, öğenin ne zaman seçili olduğunu göstermek için seçim öğesi deseninin desteklenmesi gerekir.|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider>|Şekline|Veri öğesi bir veri kılavuzu denetim türü içinde yer alıyorsa, bu kalıbı destekleyecektir.|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|Şekline|Veri öğesi üzerinden geçiş yapılabilir bir durum içeriyorsa.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Şekline|Veri öğesinin birincil metni düzenlenebilir ise, değer deseninin desteklenmesi gerekir.|  
  
## <a name="working-with-data-items-in-large-lists"></a>Büyük listelerde veri öğeleriyle çalışma  
 Büyük listeler genellikle [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] çerçeveler dahilinde veri sanallaştırılır ve bu da performansa yardımcı olur. Bu nedenle, bir UI Otomasyon istemcisi, tam ağacın içeriğini diğer öğe kapsayıcılarıyla aynı şekilde hurdaya çıkaralmak için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sorgu özelliğini kullanamaz. Bir istemci, veri öğesinden tüm bilgi kümesine erişmeden önce öğeyi görünüm içine kaydırabilmelidir (veya tüm değerli seçenekleri göstermek için denetimi genişletmelidir).  
  
 Veri öğesi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] öğesinde `SetFocus` çağrılırken, Microsoft Windows Explorer durumu başarıyla döndürülür ve odağın veri öğesi alt ağacı içinde düzenleme olarak ayarlanmış olmasına neden olur.  
  
## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyon olayları  
 Aşağıdaki tabloda tüm veri öğesi denetimleri tarafından desteklenmesi gereken [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayları listelenmektedir. Olaylar hakkında daha fazla bilgi için bkz. [UI Otomasyonu olaylarına genel bakış](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayı|Destek|Notlar|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>.|Gerekli|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>.|Gerekli|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>.|Gerekli|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|Yok.|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Şekline|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty>.|Şekline|Yok.|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>|Gerekli|Yok.|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|Gerekli|Yok.|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Gerekli|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>.|Şekline|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty>.|Şekline|Yok.|  
  
## <a name="dataitem-control-type-example"></a>DataItem denetim türü örneği  
 Aşağıdaki görüntüde, sütunlar için zengin bilgi desteğiyle bir liste görünümü denetimindeki bir DataItem denetim türü gösterilmektedir.  
  
 ![İki veri öğesi içeren liste görünümü denetiminin grafiği](./media/uiauto-data-grid-detailed.GIF "uiauto_data_grid_detailed")  
  
 Denetim görünümü ve veri öğesi denetimiyle ilgili [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacının Içerik görünümü aşağıda görüntülenmektedir. Her Otomasyon öğesi için Denetim desenleri parantez içinde gösterilir. "Contoso" grubu, veri kılavuzu konak denetimi kılavuzunun de bir parçasıdır.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç denetimi görünümü|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı-Içerik görünümü|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|-Grup "contoso" (tablo, kılavuz)<br />-DataItem "accounts. doc" (TableItem, GridItem, SelectionItem, Invoke)<br />-Görüntü "alacak belgeleri. doc"<br />-"Name" (TableItem, GridItem, value "accounts. doc") öğesini düzenleyin<br />-Düzenle "değiştirilme tarihi" (TableItem, GridItem, değer "8/25/2006 3:29 PM")<br />-Düzenle "size" (GridItem, TableItem, değer "11,0 KB)<br />-DataItem "accounts. doc" (TableItem, GridItem, SelectionItem, Invoke)<br />-   ...|-Grup "contoso" (tablo, kılavuz)<br />-DataItem "accounts. doc" (TableItem, GridItem, SelectionItem, Invoke)<br />-Görüntü "alacak belgeleri. doc"<br />-"Name" (TableItem, GridItem, value "accounts. doc") öğesini düzenleyin<br />-Düzenle "değiştirilme tarihi" (TableItem, GridItem, değer "8/25/2006 3:29 PM")<br />-Düzenle "size" (GridItem, TableItem, değer "11,0 KB)<br />-DataItem "accounts. doc" (TableItem, GridItem, SelectionItem, Invoke)<br />-   …|  
  
 Bir ızgara seçilebilir öğelerin listesini temsil ediyorsa, karşılık gelen kullanıcı arabirimi öğeleri, DataItem denetim türü yerine ListItem denetim türü ile gösterilebilir. Yukarıdaki örnekte, Grup ("contoso") altındaki DataItem öğeleri ("accounts. doc" ve "accounts borçları. doc"), bu tür zaten SelectionItem denetim modelini desteklediğinden ListItem denetim türü olarak açığa çıkarılacağından artırılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.ControlType.DataItem>
- [UI Otomasyonu Denetim Türlerine Genel Bakış](ui-automation-control-types-overview.md)
- [UI Otomasyonuna Genel Bakış](ui-automation-overview.md)
