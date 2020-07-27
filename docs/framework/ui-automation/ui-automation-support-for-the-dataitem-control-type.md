---
title: DataItem Denetim Türü için UI Otomasyon Desteği
description: DataItem denetim türü için UI Otomasyonu desteği hakkında bilgi alın. Gerekli ağaç yapısını, özellikleri, denetim desenlerini ve olayları öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Data Item control type
- Data Item control type
- control types, Data Item
ms.assetid: 181708fd-2595-4c43-9abd-75811627d64c
ms.openlocfilehash: c1b149e1033303e98bd150e62c6344b60eec1f93
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167986"
---
# <a name="ui-automation-support-for-the-dataitem-control-type"></a>DataItem Denetim Türü için UI Otomasyon Desteği
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konuda [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] , DataItem denetim türü için destek hakkında bilgi verilmektedir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Denetim türünde, bir denetimin özelliği kullanabilmesi için uyması gereken koşullar kümesidir <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> . Koşullar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , ağaç yapısı, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerleri ve Denetim desenleri için özel kurallar içerir.  
  
 Kişiler listesindeki bir giriş, veri öğesi denetimine bir örnektir. Bir veri öğesi denetimi, son kullanıcıya ilgi çekici bilgiler içerir. Daha zengin bilgiler içerdiğinden basit liste öğesinden daha karmaşıktır.  
  
 Aşağıdaki bölümler, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] DataItem denetim türü için gerekli ağaç yapısını, özellikleri, denetim desenlerini ve olayları tanımlar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Gereksinimler, Win32 veya Windows Forms tüm veri öğesi denetimlerine uygulanır [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] .  
  
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyonu ağaç yapısı  
 Aşağıdaki tabloda, veri öğesi denetimleriyle ilgili ağacın denetim görünümü ve içerik görünümü gösterilmektedir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ve her görünümde nelerin yer aldığı açıklanmaktadır. Ağaç hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [UI Otomasyon ağacına genel bakış](ui-automation-tree-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Ağaç denetimi görünümü|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Ağaç-Içerik görünümü|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|Çağrılabilir<br /><br /> -Değişir (0 veya daha fazla; hiyerarşide yapısal olarak yapılandırılabilir)|Çağrılabilir<br /><br /> -Değişir (0 veya daha fazla; hiyerarşide yapısal olarak yapılandırılabilir)|  
  
 Bir veri kılavuzundaki veri öğesi öğesi, başka bir veri öğeleri katmanı veya metin, resim veya düzenleme denetimleri gibi belirli kılavuz öğeleri dahil olmak üzere çeşitli nesneleri barındırabilirler. Veri öğesi öğesinin belirli bir nesne rolü varsa, öğe belirli bir denetim türü olarak kullanıma sunulmalıdır; Örneğin, kılavuzdaki seçilebilir bir veri öğesi için bir ListItem denetim türü.  
  
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon Özellikleri  
 Aşağıdaki tabloda, değeri veya tanımı özellikle veri öğesi denetimleriyle ilgili olan özellikler listelenmiştir. Özellikler hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [Istemciler Için UI Otomasyon özellikleri](ui-automation-properties-for-clients.md).  
  
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
 Aşağıdaki tabloda [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] tüm veri öğesi denetimleri tarafından desteklenmesi gereken denetim desenleri listelenmektedir. Denetim desenleri hakkında daha fazla bilgi için bkz. [UI Otomasyonu Denetim desenlerine genel bakış](ui-automation-control-patterns-overview.md).  
  
|Denetim deseninin|Destek|Notlar|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Şekline|Bilgileri göstermek ve gizlemek için veri öğesi genişletilirse veya daraltılabilse, genişletme ve daraltma modelinin desteklenmesinin olması gerekir.|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider>|Şekline|Veri öğeleri, bir kapsayıcıda bir veri öğeleri koleksiyonu kullanıma hazır olan öğe ve öğe arasında gezilebilir olduğunda kılavuz öğe modelini destekleyecektir.|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|Şekline|Tüm veri öğeleri, veri kapsayıcısı ekrana sığmayacak kadar çok öğe olduğunda kaydırma öğesi düzeniyle görünüm içine kaydırılabilme özelliğini destekler.|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Yes|Tüm veri öğeleri, öğenin ne zaman seçili olduğunu göstermek için seçim öğesi deseninin desteklenmesi gerekir.|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider>|Şekline|Veri öğesi bir veri kılavuzu denetim türü içinde yer alıyorsa, bu kalıbı destekleyecektir.|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|Şekline|Veri öğesi üzerinden geçiş yapılabilir bir durum içeriyorsa.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Şekline|Veri öğesinin birincil metni düzenlenebilir ise, değer deseninin desteklenmesi gerekir.|  
  
## <a name="working-with-data-items-in-large-lists"></a>Büyük listelerde veri öğeleriyle çalışma  
 Büyük listeler genellikle [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] performansta yardımcı olmak için çerçeveler içinde sanallaştırılır. Bu nedenle, bir UI Otomasyon istemcisi, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Tam ağacın içeriğini diğer öğe kapsayıcılarıyla aynı şekilde hurdaya çıkarılamıyor ve sorgu özelliğini kullanamaz. Bir istemci, veri öğesinden tüm bilgi kümesine erişmeden önce öğeyi görünüm içine kaydırabilmelidir (veya tüm değerli seçenekleri göstermek için denetimi genişletmelidir).  
  
 `SetFocus` [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Veri öğesi için öğesinde çağrılırken, Microsoft Windows Explorer durumu başarıyla döndürülür ve odağın veri öğesi alt ağacı içinde düzenleme olarak ayarlanmasına neden olur.  
  
## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyon olayları  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tüm veri öğesi denetimleri tarafından desteklenmesi gereken olaylar listelenmektedir. Olaylar hakkında daha fazla bilgi için bkz. [UI Otomasyonu olaylarına genel bakış](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Olay|Destek|Notlar|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>özellik değişti olayı.|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>özellik değişti olayı.|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>özellik değişti olayı.|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>özellik değişti olayı.|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Şekline|Hiçbiri|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty>özellik değişti olayı.|Şekline|Hiçbiri|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>özellik değişti olayı.|Şekline|Hiçbiri|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty>özellik değişti olayı.|Şekline|Hiçbiri|  
  
## <a name="dataitem-control-type-example"></a>DataItem denetim türü örneği  
 Aşağıdaki görüntüde, sütunlar için zengin bilgi desteğiyle bir liste görünümü denetimindeki bir DataItem denetim türü gösterilmektedir.  
  
 ![İki veri öğesi içeren liste görünümü denetiminin grafiği](./media/uiauto-data-grid-detailed.GIF "uiauto_data_grid_detailed")  
  
 Denetim görünümü ve [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] veri öğesi denetimiyle ilgili ağacın Içerik görünümü aşağıda görüntülenmektedir. Her Otomasyon öğesi için Denetim desenleri parantez içinde gösterilir. "Contoso" grubu, veri kılavuzu konak denetimi kılavuzunun de bir parçasıdır.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Ağaç denetimi görünümü|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Ağaç-Içerik görünümü|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|-Grup "contoso" (tablo, kılavuz)<br />-DataItem "accounts Receivable.doc" (TableItem, GridItem, SelectionItem, Invoke)<br />-Görüntü "hesaplar Receivable.doc"<br />-"Name" (TableItem, GridItem, value "hesapları Receivable.doc") öğelerini düzenleyin<br />-Düzenle "değiştirilme tarihi" (TableItem, GridItem, değer "8/25/2006 3:29 PM")<br />-Düzenle "size" (GridItem, TableItem, değer "11,0 KB)<br />-DataItem "accounts Payable.doc" (TableItem, GridItem, SelectionItem, Invoke)<br />-   ...|-Grup "contoso" (tablo, kılavuz)<br />-DataItem "accounts Receivable.doc" (TableItem, GridItem, SelectionItem, Invoke)<br />-Görüntü "hesaplar Receivable.doc"<br />-"Name" (TableItem, GridItem, value "hesapları Receivable.doc") öğelerini düzenleyin<br />-Düzenle "değiştirilme tarihi" (TableItem, GridItem, değer "8/25/2006 3:29 PM")<br />-Düzenle "size" (GridItem, TableItem, değer "11,0 KB)<br />-DataItem "accounts Payable.doc" (TableItem, GridItem, SelectionItem, Invoke)<br />-   …|  
  
 Bir ızgara seçilebilir öğelerin listesini temsil ediyorsa, karşılık gelen kullanıcı arabirimi öğeleri, DataItem denetim türü yerine ListItem denetim türü ile gösterilebilir. Yukarıdaki örnekte, Grup ("contoso") altındaki DataItem öğeleri ("hesaplar Receivable.doc" ve "hesaplar Payable.doc"), bu tür zaten SelectionItem denetim modelini desteklediğinden, bu öğeler, ListItem denetim türü olarak ortaya çıkarılacağından artırılabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.ControlType.DataItem>
- [UI Otomasyon Denetim Türlerine Genel Bakış](ui-automation-control-types-overview.md)
- [UI Otomasyonuna Genel Bakış](ui-automation-overview.md)
