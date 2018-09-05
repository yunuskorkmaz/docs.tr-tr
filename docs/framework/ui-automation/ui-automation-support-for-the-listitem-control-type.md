---
title: ListItem Denetim Türü için UI Otomasyon Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- control types, List
- List Item control type
- UI Automation, List Item control type
ms.assetid: 34f533bf-fc14-4e78-8fee-fb7107345fab
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 69fe598fc38d9a82d0b95318774d16a49bbdf49f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43673933"
---
# <a name="ui-automation-support-for-the-listitem-control-type"></a>ListItem Denetim Türü için UI Otomasyon Desteği
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu hakkında bilgi sağlar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] desteği <xref:System.Windows.Automation.ControlType.ListItem> denetim türü. İçinde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], Denetim türü bir denetim kullanmak için karşılaması gereken koşulları kümesidir <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> özelliği. Özel yönergeleri koşulları dahil [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısını [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerlerini ve denetim düzenleri.  
  
 Liste öğesi denetimleri ListItem denetim türü denetimlerini bir örnektir.  
  
 Aşağıdaki bölümlerde gerekli tanımlamak [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısı, özellikler, Denetim düzenleri ve olayları ListItem denetim türü için. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Gereksinimler tüm liste denetimleri için geçerli olup olmadığını [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], veya [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyon ağaç yapısı  
 Aşağıdaki tablo denetimi ve içerik görünümünde gösterir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] liste öğesine aittir ağaç denetler ve her bir görünümde bulunabilir açıklar. Daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç bkz [UI Otomasyon ağacına genel bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Denetim Görünüm|İçerik görünümü|  
|------------------|------------------|  
|ListItem<br /><br /> -Görüntü (0 veya daha fazla)<br />-Metin (0 veya daha fazla)<br />-Düzenle (0 veya daha fazla)|ListItem|  
  
 Liste öğesi denetimi içerik görünümü içinde alt [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç her zaman "0" olmalıdır. Gereksinimleri izlemelidir sonra diğer öğeler liste öğesinin altında yer alır, denetimin yapısını ise [Treeıtem denetim türü için UI Otomasyon desteği](../../../docs/framework/ui-automation/ui-automation-support-for-the-treeitem-control-type.md) denetim türü.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon özellikleri  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , değer veya tanımı liste öğesi denetimleri için özellikle ilgili özellikler. Daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri görmek [istemciler için UI Otomasyon özellikleri](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Özelliği|Değer|Notlar|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlara bakın.|Bu özelliğin değerini bir uygulamadaki tüm denetimler arasında benzersiz olması gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlara bakın.|Bu özelliğin bu değeri liste öğesi resim ve metin içeriğini alan içermelidir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Bağlıdır|Listesi denetimini tıklanabilir bir nokta (odağı alması için listeyi neden tıklanabilir bir nokta) varsa, bu noktadan bu özelliği aracılığıyla sunulmalıdır. Listesi denetimini tamamen alt liste öğeleri tarafından kapsanan varsa oluşturacak bir <xref:System.Windows.Automation.NoClickablePointException> istemci liste denetiminde bir öğe için tıklanabilir bir nokta kaldırmasını belirtmek için.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlara bakın.|Bir liste öğesi denetimin adı özelliğinin değeri, öğenin metin içeriğini gelir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Notlara bakın.|Bir statik metin etiketi ise bu özellik bu denetime başvuru göstermesi gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|ListItem|Bu değer tüm UI çerçeveleri için aynıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"liste öğesi"|ListItem denetim türü için karşılık gelen yerelleştirilmiş bir dize.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Doğru|Listesi denetimini her zaman içerik görünümünde bulunan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Doğru|Listesi denetimini her zaman denetim görünümünde bulunan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Doğru|Kapsayıcı klavye girdisi kabul edebilir, bu özellik değeri true olmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|""|Liste denetimleri için Yardım metni, kullanıcı, genellikle bir araç ipucu sunulan bilgi aynı türde olan bir seçeneklerini listeden bir seçim yapmasını neden sorulmaktadır açıklayan. Örneğin, ", izleme için ekran çözünürlüğünü ayarlamak için bir öğe seçin."|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemTypeProperty>|Bağlıdır|Bu özellik, temel alınan nesneyi gösteren liste öğesi denetimleri için açılmamalıdır. Bu liste öğesi denetimleri genellikle kullanıcıların temel alınan nesnenin ilişkilendirileceği denetimi ile ilişkili bir simge var.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>|Bağlıdır|Bu özellik, yoksa liste öğesi şu anda görünümde kaydırma denetim düzeni uygulayan üst kapsayıcı içindeki kaydırılan için bir değer döndürmesi gerekir.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Gerekli UI Otomasyon denetim düzenleri  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] denetim desenleri liste öğesi denetimleri tarafından desteklenmesi gerekir. Denetim desenleri hakkında daha fazla bilgi için bkz. [UI Otomasyon denetim düzenlerine genel bakış](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Denetim düzeni|Destek|Notlar|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Evet|Liste öğesi denetimi, bu denetim düzeni uygulamalıdır. Bu liste seçildiklerinde iletmek öğe denetimleri sağlar.|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|Bağlıdır|Liste öğesi kaydırılabilir bir kapsayıcıda yer alıyorsa bu denetim düzeni uygulanmalıdır.|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|Bağlıdır|Liste öğesi checkable ise ve eylem seçimi durum değişikliği gerçekleştirmez bu denetim düzeni uygulanmalıdır.|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Bağlıdır|Öğe bilgilerini göstermek veya gizlemek için yönetilebilir, bu denetim düzeni uygulanmalıdır.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Bağlıdır|Öğesi düzenlenebilir, bu denetim düzeni uygulanmalıdır. Liste öğesi denetimi değişiklikleri değerlerini değişiklikleri neden <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>, ve <xref:System.Windows.Automation.Provider.IValueProvider.Value%2A>.|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider>|Bağlıdır|Öğe için uzamsal Gezinti listesi kapsayıcı içinde desteklenir ve kapsayıcı satırlar ve sütunlar düzenlenmiş kılavuz öğesi denetim düzeni uygulanmalıdır.|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Bağlıdır|Öğenin üzerinde gerçekleştirilebilen bir komut yoksa ayrı seçimden, ardından bu düzen uygulanmalıdır. Liste öğesi denetimi çift ile ilişkili bir eylem genellikle budur. Örnek Belge başlatma [!INCLUDE[TLA#tla_winexpl](../../../includes/tlasharptla-winexpl-md.md)], veya bir müzik dosyası oynayan [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)].|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyonu olayları  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayları tüm liste öğesi denetimleri tarafından desteklenmesi gerekir. Olaylar hakkında daha fazla bilgi için bkz. [UI Otomasyonu olaylarına genel bakış](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Olay|Destek|Notlar|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Bağlıdır|Yok.|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>|Gerekli|Yok.|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|Gerekli|Yok.|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> özellik değişti olayı.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> özellik değişti olayı.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> özellik değişti olayı.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemStatusProperty> özellik değişti olayı.|Bağlıdır|Yok.|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty> özellik değişti olayı.|Bağlıdır|Yok.|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> özellik değişti olayı.|Bağlıdır|Yok.|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty> özellik değişti olayı.|Bağlıdır|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|Yok.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Automation.ControlType.ListItem>  
 [UI Otomasyonu Denetim Türlerine Genel Bakış](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [UI Otomasyonuna Genel Bakış](../../../docs/framework/ui-automation/ui-automation-overview.md)
