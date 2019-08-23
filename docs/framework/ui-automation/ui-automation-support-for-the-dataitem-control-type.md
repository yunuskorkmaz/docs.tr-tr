---
title: DataItem Denetim Türü için UI Otomasyon Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Data Item control type
- Data Item control type
- control types, Data Item
ms.assetid: 181708fd-2595-4c43-9abd-75811627d64c
ms.openlocfilehash: 7ba338a2eeb222dc8c807bc3a2bb4d1baf7de39d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912004"
---
# <a name="ui-automation-support-for-the-dataitem-control-type"></a>DataItem Denetim Türü için UI Otomasyon Desteği
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir. Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konuda, DataItem denetim [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] türü için destek hakkında bilgi verilmektedir. Denetim türünde, bir denetimin <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> özelliği kullanabilmesi için uyması gereken koşullar kümesidir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Koşullar, ağaç yapısı, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerleri ve Denetim desenleri için özel kurallar içerir.  
  
 Kişiler listesindeki bir giriş, veri öğesi denetimine bir örnektir. Bir veri öğesi denetimi, son kullanıcıya ilgi çekici bilgiler içerir. Daha zengin bilgiler içerdiğinden basit liste öğesinden daha karmaşıktır.  
  
 Aşağıdaki bölümler, DataItem denetim türü [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] için gerekli ağaç yapısını, özellikleri, denetim desenlerini ve olayları tanımlar. Gereksinimler,, [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]veya [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] şeklinde[!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]tüm veri öğesi denetimlerine uygulanır. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]  
  
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyonu ağaç yapısı  
 Aşağıdaki tabloda, veri öğesi denetimleriyle ilgili [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacın denetim görünümü ve içerik görünümü gösterilmektedir ve her görünümde nelerin yer aldığı açıklanmaktadır. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ağaç hakkında daha fazla bilgi için bkz. [UI Otomasyon ağacına genel bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Ağaç denetimi görünümü|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Ağaç-Içerik görünümü|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|Çağrılabilir<br /><br /> -Değişir (0 veya daha fazla; hiyerarşide yapısal olarak yapılandırılabilir)|Çağrılabilir<br /><br /> -Değişir (0 veya daha fazla; hiyerarşide yapısal olarak yapılandırılabilir)|  
  
 Bir veri kılavuzundaki veri öğesi öğesi, başka bir veri öğeleri katmanı veya metin, resim veya düzenleme denetimleri gibi belirli kılavuz öğeleri dahil olmak üzere çeşitli nesneleri barındırabilirler. Veri öğesi öğesinin belirli bir nesne rolü varsa, öğe belirli bir denetim türü olarak kullanıma sunulmalıdır; Örneğin, kılavuzdaki seçilebilir bir veri öğesi için bir ListItem denetim türü.  
  
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon Özellikleri  
 Aşağıdaki tabloda, değeri veya tanımı özellikle veri öğesi denetimleriyle ilgili olan özellikler listelenmiştir. Özellikler hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] daha fazla bilgi için bkz. [istemciler için UI Otomasyon özellikleri](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
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
 Aşağıdaki tabloda tüm veri öğesi [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] denetimleri tarafından desteklenmesi gereken denetim desenleri listelenmektedir. Denetim desenleri hakkında daha fazla bilgi için bkz. [UI Otomasyonu Denetim desenlerine genel bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
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
 Büyük listeler genellikle performansta yardımcı olmak için [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] çerçeveler içinde sanallaştırılır. Bu nedenle, bir UI Otomasyon istemcisi, tam ağacın içeriğini [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] diğer öğe kapsayıcılarıyla aynı şekilde hurdaya çıkarılamıyor ve sorgu özelliğini kullanamaz. Bir istemci, veri öğesinden tüm bilgi kümesine erişmeden önce öğeyi görünüm içine kaydırabilmelidir (veya tüm değerli seçenekleri göstermek için denetimi genişletmelidir).  
  
 Veri öğesi `SetFocus` için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] öğesinde çağrılırken, [!INCLUDE[TLA#tla_winexpl](../../../includes/tlasharptla-winexpl-md.md)] bu durum başarıyla döndürülür ve odağın veri öğesi alt ağacı içinde düzenleme olarak ayarlanmış olmasına neden olur.  
  
## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyon olayları  
 Aşağıdaki tabloda tüm veri öğesi [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] denetimleri tarafından desteklenmesi gereken olaylar listelenmektedir. Olaylar hakkında daha fazla bilgi için bkz. [UI Otomasyonu olaylarına genel bakış](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Olay|Destek|Notlar|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>özellik değişti olayı.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>özellik değişti olayı.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>özellik değişti olayı.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>özellik değişti olayı.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|Yok.|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Şekline|Yok.|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty>özellik değişti olayı.|Şekline|Yok.|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>|Gerekli|Yok.|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|Gerekli|Yok.|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Gerekli|Yok.|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>özellik değişti olayı.|Şekline|Yok.|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty>özellik değişti olayı.|Şekline|Yok.|  
  
## <a name="dataitem-control-type-example"></a>DataItem denetim türü örneği  
 Aşağıdaki görüntüde, sütunlar için zengin bilgi desteğiyle bir liste görünümü denetimindeki bir DataItem denetim türü gösterilmektedir.  
  
 ![İki veri öğesi Içeren liste görünümü denetiminin grafiği](../../../docs/framework/ui-automation/media/uiauto-data-grid-detailed.GIF "uiauto_data_grid_detailed")  
  
 Denetim görünümü ve veri öğesi denetimiyle ilgili [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacın içerik görünümü aşağıda görüntülenmektedir. Her Otomasyon öğesi için Denetim desenleri parantez içinde gösterilir. "Contoso" grubu, veri kılavuzu konak denetimi kılavuzunun de bir parçasıdır.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Ağaç denetimi görünümü|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Ağaç-Içerik görünümü|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|-Grup "contoso" (tablo, kılavuz)<br />-DataItem "accounts. doc" (TableItem, GridItem, SelectionItem, Invoke)<br />-Görüntü "alacak belgeleri. doc"<br />-"Name" (TableItem, GridItem, value "accounts. doc") öğesini düzenleyin<br />-Düzenle "değiştirilme tarihi" (TableItem, GridItem, değer "8/25/2006 3:29 PM")<br />-Düzenle "size" (GridItem, TableItem, değer "11,0 KB)<br />-DataItem "accounts. doc" (TableItem, GridItem, SelectionItem, Invoke)<br />-   ...|-Grup "contoso" (tablo, kılavuz)<br />-DataItem "accounts. doc" (TableItem, GridItem, SelectionItem, Invoke)<br />-Görüntü "alacak belgeleri. doc"<br />-"Name" (TableItem, GridItem, value "accounts. doc") öğesini düzenleyin<br />-Düzenle "değiştirilme tarihi" (TableItem, GridItem, değer "8/25/2006 3:29 PM")<br />-Düzenle "size" (GridItem, TableItem, değer "11,0 KB)<br />-DataItem "accounts. doc" (TableItem, GridItem, SelectionItem, Invoke)<br />-   …|  
  
 Bir ızgara seçilebilir öğelerin listesini temsil ediyorsa, karşılık gelen kullanıcı arabirimi öğeleri, DataItem denetim türü yerine ListItem denetim türü ile gösterilebilir. Yukarıdaki örnekte, Grup ("contoso") altındaki DataItem öğeleri ("accounts. doc" ve "accounts borçları. doc"), bu tür zaten SelectionItem denetim modelini desteklediğinden ListItem denetim türü olarak açığa çıkarılacağından artırılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.ControlType.DataItem>
- [UI Otomasyonu Denetim Türlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)
- [UI Otomasyonuna Genel Bakış](../../../docs/framework/ui-automation/ui-automation-overview.md)
