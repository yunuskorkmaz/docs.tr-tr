---
title: ListItem Denetim Türü için UI Otomasyon Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- control types, List
- List Item control type
- UI Automation, List Item control type
ms.assetid: 34f533bf-fc14-4e78-8fee-fb7107345fab
ms.openlocfilehash: 8664d7a4c26d69792a00eadfcb7b6d5f7082829c
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75741190"
---
# <a name="ui-automation-support-for-the-listitem-control-type"></a>ListItem Denetim Türü için UI Otomasyon Desteği
> [!NOTE]
> Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu, <xref:System.Windows.Automation.ControlType.ListItem> denetim türü için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] desteği hakkında bilgi sağlar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], denetim türü, bir denetimin <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> özelliğini kullanmak için karşılaması gereken koşullar kümesidir. Koşullar, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısına yönelik özel yönergeler, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerleri ve Denetim desenleri içerir.  
  
 Liste öğesi denetimleri, ListItem denetim türünü uygulayan denetimlerin bir örneğidir.  
  
 Aşağıdaki bölümler, ListItem denetim türü için gerekli [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısını, özellikleri, denetim desenlerini ve olayları tanımlar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gereksinimleri, [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], Win32 veya [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]bakılmaksızın tüm liste denetimlerine uygulanır.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyonu ağaç yapısı  
 Aşağıdaki tabloda, liste öğesi denetimleriyle ilgili [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacının denetim görünümü ve içerik görünümü gösterilmektedir ve her görünümde nelerin yer aldığı açıklanmaktadır. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı hakkında daha fazla bilgi için bkz. [UI Otomasyon ağacına genel bakış](ui-automation-tree-overview.md).  
  
|Denetim görünümü|İçerik görünümü|  
|------------------|------------------|  
|Liste<br /><br /> -Görüntü (0 veya daha fazla)<br />-Metin (0 veya daha fazla)<br />-Düzenle (0 veya daha fazla)|Liste|  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacının içerik görünümündeki liste öğesi denetiminin alt öğeleri her zaman "0" olmalıdır. Denetimin yapısı, diğer öğeler liste öğesinin altında yer alıyorsa, [ağaç öğesi denetim türü denetim türü Için UI Otomasyonu desteğinin](ui-automation-support-for-the-treeitem-control-type.md) gereksinimlerini izlemelidir.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon Özellikleri  
 Aşağıdaki tabloda, değeri veya tanımı özellikle liste öğesi denetimleriyle ilgili olan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri listelenmektedir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri hakkında daha fazla bilgi için bkz. [istemciler Için UI Otomasyon özellikleri](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özelliği|Değer|Notlar|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlara bakın.|Bu özelliğin değerinin bir uygulamadaki tüm denetimlerde benzersiz olması gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlara bakın.|Bu özelliğin bu değeri, görüntü alanını ve liste öğesinin metin içeriğini içermelidir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Şekline|Liste denetiminin tıklatılabilir bir noktası varsa (listenin odaklanmasına neden olacak şekilde tıklanabilecek bir nokta), bu nokta bu özellik aracılığıyla gösterilmelidir. Liste denetimi, alt liste öğelerine tamamen kapalıyorsa, istemcinin tıklatılabilir bir nokta için liste denetimi içinde bir öğe sormasını belirten bir <xref:System.Windows.Automation.NoClickablePointException> yükseltir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlara bakın.|Bir liste öğesi denetiminin Name özelliğinin değeri, öğenin metin içeriğinden gelir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Notlara bakın.|Statik bir metin etiketi varsa, bu özellik bu denetimin bir başvurusunu kullanıma sunmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Liste|Bu değer tüm UI çerçeveleri için aynıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"liste öğesi"|ListItem denetim türüne karşılık gelen yerelleştirilmiş dize.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Doğru|Liste denetimi her zaman [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacının içerik görünümüne dahil edilmiştir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Doğru|Liste denetimi her zaman [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacının denetim görünümüne dahil edilmiştir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Doğru|Kapsayıcı klavye girişini kabul edebiliyorsa, bu özellik değeri doğru olmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|""|Liste denetimleri için yardım metni, kullanıcıya, genellikle bir araç ipucuyla sunulan ve genellikle aynı türde bilgiler olan bir seçenek listesinden seçim yapma sorulduğunu açıklamalıdır. Örneğin, "monitörünüz için görüntü çözünürlüğünü ayarlamak için bir öğe seçin."|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemTypeProperty>|Şekline|Bu özellik, temel alınan bir nesneyi temsil eden liste öğesi denetimleri için sunulmalıdır. Bu liste öğesi denetimlerinde genellikle kullanıcıların temel alınan nesneyle ilişkili olan denetimle ilişkili bir simge vardır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>|Şekline|Bu özellik, liste öğesinin kaydırma denetim modelini uygulayan üst kapsayıcıda görünüm olarak kaydırılıp kaydırılmayacağını belirten bir değer döndürmelidir.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Gerekli UI Otomasyonu Denetim desenleri  
 Aşağıdaki tabloda liste öğesi denetimleri tarafından desteklenmesi gereken [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Denetim desenleri listelenmektedir. Denetim desenleri hakkında daha fazla bilgi için bkz. [UI Otomasyonu Denetim desenlerine genel bakış](ui-automation-control-patterns-overview.md).  
  
|Denetim deseninin|Destek|Notlar|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Evet|Liste öğesi denetimi bu denetim deseninin uygulanması gerekir. Bu, liste öğeleri denetimlerinin seçildiklerinde yönetilmesine olanak sağlar.|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|Şekline|Liste öğesi kaydırılabilir bir kapsayıcı içinde yer alıyorsa, bu denetim deseninin uygulanması gerekir.|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|Şekline|Liste öğesi kullanıma alınabilir durumdaysa ve eylem bir seçim durumu değişikliği gerçekleştirmezse, bu denetim deseninin uygulanması gerekir.|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Şekline|Öğe bilgileri göstermek veya gizlemek için işlenebiliyorsanız, bu denetim deseninin uygulanması gerekir.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Şekline|Öğe düzenlenebilirse, bu denetim deseninin uygulanması gerekir. Liste öğesi denetimindeki değişiklikler <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>değerlerinde değişikliklere neden olur ve <xref:System.Windows.Automation.Provider.IValueProvider.Value%2A>.|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider>|Şekline|Öğe uzamsal gezinmede öğe liste kapsayıcısı içinde destekleniyorsa ve kapsayıcı satırlar ve sütunlar halinde düzenlenmişse, kılavuz öğesi denetim deseninin uygulanması gerekir.|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Şekline|Öğe üzerinde gerçekleştirilebilecek bir komuta sahipse, seçimden ayırın, bu düzenin uygulanması gerekir. Bu genellikle liste öğesi denetimine çift tıklanmakla ilişkili bir eylemdir. Örnekler, Microsoft Windows Explorer 'dan bir belge veya Microsoft Windows Media Player bir müzik dosyası oynamalıdır.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyon olayları  
 Aşağıdaki tabloda, tüm liste öğesi denetimleri tarafından desteklenmesi gereken [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayları listelenmektedir. Olaylar hakkında daha fazla bilgi için bkz. [UI Otomasyonu olaylarına genel bakış](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayı|Destek|Notlar|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Şekline|Yok.|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>|Gerekli|Yok.|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|Gerekli|Yok.|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Gerekli|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>.|Gerekli|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>.|Gerekli|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>.|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Gerekli|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.AutomationElementIdentifiers.ItemStatusProperty>.|Şekline|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty>.|Şekline|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty>.|Şekline|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>.|Şekline|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|Yok.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.ControlType.ListItem>
- [UI Otomasyonu Denetim Türlerine Genel Bakış](ui-automation-control-types-overview.md)
- [UI Otomasyonuna Genel Bakış](ui-automation-overview.md)
