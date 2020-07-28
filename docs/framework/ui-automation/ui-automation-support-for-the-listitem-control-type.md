---
title: ListItem Denetim Türü için UI Otomasyon Desteği
description: ListItem denetim türü için UI Otomasyonu desteği hakkında bilgi alın. Gerekli ağaç yapısını, özellikleri, denetim desenlerini ve olayları öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- control types, List
- List Item control type
- UI Automation, List Item control type
ms.assetid: 34f533bf-fc14-4e78-8fee-fb7107345fab
ms.openlocfilehash: bf1690b094e9d472fd4213f7fa3df545dca6ebac
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166055"
---
# <a name="ui-automation-support-for-the-listitem-control-type"></a>ListItem Denetim Türü için UI Otomasyon Desteği
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konuda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Denetim türü için destek hakkında bilgi verilmektedir <xref:System.Windows.Automation.ControlType.ListItem> . ' De [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , bir denetim türü, özelliği kullanmak için bir denetimin uyması gereken koşullar kümesidir <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> . Koşullar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , ağaç yapısı, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerleri ve Denetim desenleri için özel kurallar içerir.  
  
 Liste öğesi denetimleri, ListItem denetim türünü uygulayan denetimlerin bir örneğidir.  
  
 Aşağıdaki bölümler, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ListItem denetim türü için gerekli ağaç yapısını, özellikleri, denetim desenlerini ve olayları tanımlar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Gereksinimler, Win32 veya Windows Forms tüm liste denetimleri için geçerlidir [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] .  
  
<a name="Required_UI_Automation_Tree_Structure"></a>
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyonu ağaç yapısı  
 Aşağıdaki tabloda, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] liste öğesi denetimleriyle ilgili olan ağacın denetim görünümü ve içerik görünümü gösterilmektedir ve her görünümde nelerin yer aldığı açıklanmaktadır. Ağaç hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [UI Otomasyon ağacına genel bakış](ui-automation-tree-overview.md).  
  
|Denetim görünümü|İçerik görünümü|  
|------------------|------------------|  
|Liste<br /><br /> -Görüntü (0 veya daha fazla)<br />-Metin (0 veya daha fazla)<br />-Düzenle (0 veya daha fazla)|Liste|  
  
 Ağacın içerik görünümü içindeki bir liste öğesi denetiminin alt öğeleri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] her zaman "0" olmalıdır. Denetimin yapısı, diğer öğeler liste öğesinin altında yer alıyorsa, [ağaç öğesi denetim türü denetim türü Için UI Otomasyonu desteğinin](ui-automation-support-for-the-treeitem-control-type.md) gereksinimlerini izlemelidir.  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon Özellikleri  
 Aşağıdaki tabloda, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] değeri veya tanımı özellikle liste öğesi denetimleriyle ilgili olan özellikler listelenmiştir. Özellikler hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [Istemciler Için UI Otomasyon özellikleri](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Özelliði|Değer|Notlar|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlara bakın.|Bu özelliğin değerinin bir uygulamadaki tüm denetimlerde benzersiz olması gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlara bakın.|Bu özelliğin bu değeri, görüntü alanını ve liste öğesinin metin içeriğini içermelidir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Şekline|Liste denetiminin tıklatılabilir bir noktası varsa (listenin odaklanmasına neden olacak şekilde tıklanabilecek bir nokta), bu nokta bu özellik aracılığıyla gösterilmelidir. Liste denetimi, alt liste öğelerine tamamen kapalıyorsa, <xref:System.Windows.Automation.NoClickablePointException> istemcinin tıklatılabilir bir nokta için liste denetimi içinde bir öğe sormasını belirtmek üzere bir sağlar.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlara bakın.|Bir liste öğesi denetiminin Name özelliğinin değeri, öğenin metin içeriğinden gelir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Notlara bakın.|Statik bir metin etiketi varsa, bu özellik bu denetimin bir başvurusunu kullanıma sunmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Liste|Bu değer tüm UI çerçeveleri için aynıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"liste öğesi"|ListItem denetim türüne karşılık gelen yerelleştirilmiş dize.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Doğru|Liste denetimi her zaman ağacın içerik görünümüne dahil edilmiştir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Doğru|Liste denetimi her zaman ağacın denetim görünümüne dahil edilmiştir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Doğru|Kapsayıcı klavye girişini kabul edebiliyorsa, bu özellik değeri doğru olmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|""|Liste denetimleri için yardım metni, kullanıcıya, genellikle bir araç ipucuyla sunulan ve genellikle aynı türde bilgiler olan bir seçenek listesinden seçim yapma sorulduğunu açıklamalıdır. Örneğin, "monitörünüz için görüntü çözünürlüğünü ayarlamak için bir öğe seçin."|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemTypeProperty>|Şekline|Bu özellik, temel alınan bir nesneyi temsil eden liste öğesi denetimleri için sunulmalıdır. Bu liste öğesi denetimlerinde genellikle kullanıcıların temel alınan nesneyle ilişkili olan denetimle ilişkili bir simge vardır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>|Şekline|Bu özellik, liste öğesinin kaydırma denetim modelini uygulayan üst kapsayıcıda görünüm olarak kaydırılıp kaydırılmayacağını belirten bir değer döndürmelidir.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>
## <a name="required-ui-automation-control-patterns"></a>Gerekli UI Otomasyonu Denetim desenleri  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] liste öğesi denetimleri tarafından desteklenmesi gereken denetim desenleri listelenmektedir. Denetim desenleri hakkında daha fazla bilgi için bkz. [UI Otomasyonu Denetim desenlerine genel bakış](ui-automation-control-patterns-overview.md).  
  
|Denetim deseninin|Destek|Notlar|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Yes|Liste öğesi denetimi bu denetim deseninin uygulanması gerekir. Bu, liste öğeleri denetimlerinin seçildiklerinde yönetilmesine olanak sağlar.|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|Şekline|Liste öğesi kaydırılabilir bir kapsayıcı içinde yer alıyorsa, bu denetim deseninin uygulanması gerekir.|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|Şekline|Liste öğesi kullanıma alınabilir durumdaysa ve eylem bir seçim durumu değişikliği gerçekleştirmezse, bu denetim deseninin uygulanması gerekir.|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Şekline|Öğe bilgileri göstermek veya gizlemek için işlenebiliyorsanız, bu denetim deseninin uygulanması gerekir.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Şekline|Öğe düzenlenebilirse, bu denetim deseninin uygulanması gerekir. Liste öğesi denetimindeki değişiklikler, ve değerlerinde değişikliklere neden olur <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty> <xref:System.Windows.Automation.Provider.IValueProvider.Value%2A> .|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider>|Şekline|Öğe uzamsal gezinmede öğe liste kapsayıcısı içinde destekleniyorsa ve kapsayıcı satırlar ve sütunlar halinde düzenlenmişse, kılavuz öğesi denetim deseninin uygulanması gerekir.|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Şekline|Öğe üzerinde gerçekleştirilebilecek bir komuta sahipse, seçimden ayırın, bu düzenin uygulanması gerekir. Bu genellikle liste öğesi denetimine çift tıklanmakla ilişkili bir eylemdir. Örnekler, Microsoft Windows Explorer 'dan bir belge veya Microsoft Windows Media Player bir müzik dosyası oynamalıdır.|  
  
<a name="Required_UI_Automation_Events"></a>
## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyon olayları  
 Aşağıdaki tabloda, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Tüm liste öğesi denetimleri tarafından desteklenmesi gereken olaylar listelenmektedir. Olaylar hakkında daha fazla bilgi için bkz. [UI Otomasyonu olaylarına genel bakış](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Olay|Destek|Notlar|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Şekline|Hiçbiri|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>özellik değişti olayı.|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>özellik değişti olayı.|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>özellik değişti olayı.|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemStatusProperty>özellik değişti olayı.|Şekline|Hiçbiri|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty>özellik değişti olayı.|Şekline|Hiçbiri|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty>özellik değişti olayı.|Şekline|Hiçbiri|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>özellik değişti olayı.|Şekline|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|Hiçbiri|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.ControlType.ListItem>
- [UI Otomasyon Denetim Türlerine Genel Bakış](ui-automation-control-types-overview.md)
- [UI Otomasyonuna Genel Bakış](ui-automation-overview.md)
