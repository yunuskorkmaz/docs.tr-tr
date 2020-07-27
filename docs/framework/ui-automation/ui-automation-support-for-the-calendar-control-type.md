---
title: Takvim Denetim Türü İçin UI Otomasyon Desteği
description: Takvim denetim türü için UI Otomasyonu desteği hakkında bilgi alın. Gerekli ağaç yapısını, özellikleri, denetim desenlerini ve olayları öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Calendar control type
- Calendar control type
- control types, Calendar
ms.assetid: e91a7393-a7f9-4838-a1a6-857438b24bc9
ms.openlocfilehash: 0b21ac23fd87516a815b4b4c75516499d60c7b46
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166104"
---
# <a name="ui-automation-support-for-the-calendar-control-type"></a>Takvim Denetim Türü İçin UI Otomasyon Desteği
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , Takvim denetim türü desteği hakkında bilgi sağlar. ' De [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , bir denetim türü, özelliği kullanmak için bir denetimin uyması gereken koşullar kümesidir <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> . Koşullar, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısı, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerleri, Denetim desenleri ve olaylar için özel kurallar içerir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .  
  
 Takvim denetimleri, bir kullanıcının tarihi kolayca belirlemesine ve diğer tarihleri seçmesine izin verir.  
  
 Aşağıdaki bölümler, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Takvim denetim türü için gerekli ağaç yapısını, özellikleri, denetim desenlerini ve olayları tanımlar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Gereksinimler, Win32 veya Windows Forms tüm takvim denetimleri için geçerlidir [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] .  
  
<a name="Required_UI_Automation_Tree_Structure"></a>
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyonu ağaç yapısı  
 Aşağıdaki tabloda, takvim denetimleriyle ilgili ağacın denetim görünümü ve içerik görünümü gösterilmektedir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ve her görünümde nelerin yer aldığı açıklanmaktadır. Ağaç hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [UI Otomasyon ağacına genel bakış](ui-automation-tree-overview.md).  
  
|Denetim görünümü|İçerik görünümü|  
|------------------|------------------|  
|Takvim<br /><br /> <ul><li>DataGrid<br /><br /> <ul><li>Üst bilgi (0 veya 1)</li><li>HeaderItem (0 veya 7; miktar, sütunlarda kaç gün gösterileceğini gösterir)</li><li>ListItem (miktar, kaç gün görüntülenmiş olarak değişir)</li><li>Düğme (0 veya 2; sayfalama takvim görünümü için)</li></ul></li></ul>|Takvim<br /><br /> -ListItem (miktar kaç gün görüntülenirken değişir)|  
  
 Takvim denetimleri, Kullanıcı arabirimi içinde birçok farklı biçimde gösterilebilir. Ağacın denetim görünümünde olması için garantili denetimler [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , veri kılavuzu, üst bilgi, üstbilgi öğesi ve liste öğesi denetimleridir.  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon Özellikleri  
 Aşağıdaki tabloda, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] değeri veya tanımı özellikle takvim denetimleriyle ilgili olan özellikler listelenmiştir. Özellikler hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [Istemciler Için UI Otomasyon özellikleri](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Özelliði|Değer|Notlar|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlara bakın.|Bu özelliğin değerinin bir uygulamadaki tüm denetimlerde benzersiz olması gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlara bakın.|Tüm denetimi içeren en dıştaki dikdörtgen.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Notlara bakın.|Sınırlayıcı bir dikdörtgen varsa desteklenir. Sınırlayıcı dikdörtgenin içindeki her nokta tıklatılabilir ise ve özelleştirilmiş isabet testi gerçekleştirirseniz ve ardından tıklatılabilir bir nokta sağlayabilirsiniz.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Takvim|Bu değer tüm çerçeveler için aynıdır [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] .|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Doğru|Takvim denetimi her zaman ağacın içerik görünümüne dahil edilmiştir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Doğru|Takvim denetimi her zaman ağacın denetim görünümüne dahil edilmiştir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Notlara bakın.|Denetim, klavye odağı alamıyorsa, bu özelliği desteklemesi gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Notlara bakın.|Belge denetiminin etiketi. Genellikle, belgenin başlığı kullanılır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|Takviminizde|Takvim denetim türüne karşılık gelen yerelleştirilmiş dize.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlara bakın.|Takvim denetimi genellikle adını geçerli günün tarihinden alır.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>
## <a name="required-ui-automation-control-patterns"></a>Gerekli UI Otomasyonu Denetim desenleri  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Tüm Takvim denetimleri tarafından desteklenmesi gereken denetim desenleri listelenmektedir. Denetim desenleri hakkında daha fazla bilgi için bkz. [UI Otomasyonu Denetim desenlerine genel bakış](ui-automation-control-patterns-overview.md).  
  
|Denetim deseninin/deseninin özelliği|Destek|Notlar|  
|---------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider>|Yes|Takvim denetimi her zaman kılavuz düzenlerini destekler çünkü bir ayın içindeki günler, istenmeyen olarak gezinilebilirler.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Şekline|Çoğu Takvim denetimi, görünümü sayfaya göre ters çevirme desteğini destekler. Disk belleği gezintisini desteklemek için kaydırma düzeni önerilir.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Şekline|Çoğu Takvim denetimi, alt öğe seçimi olarak belirli bir günü, ayı veya yılı korur. Bazı takvimler çoklu seçilebilir ve diğerleri yalnızca tek seçilebilir.|  
|<xref:System.Windows.Automation.Provider.ITableProvider>|Yes|Takvim denetimi her zaman alt ağacı içinde haftanın günleri için bir üst bilgiye sahiptir, bu nedenle tablo deseninin desteklenmesi gerekir.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Hayır|Değer denetim deseninin Takvim denetimleri için gerekli değildir çünkü değeri doğrudan denetimde ayarlayamazsınız. Belirli bir tarih denetimle ilişkiliyse, bilgilerin seçim denetim düzeniyle sağlanması gerekir.|  
  
<a name="Required_UI_Automation_Events"></a>
## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyon olayları  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Tüm Takvim denetimleri tarafından desteklenmesi gereken olaylar listelenmektedir. Olaylar hakkında daha fazla bilgi için bkz. [UI Otomasyonu olaylarına genel bakış](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Olay|Destek|Notlar|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>özellik değişti olayı.|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>özellik değişti olayı.|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>özellik değişti olayı.|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent>|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|Hiçbiri|  
|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers.CurrentViewProperty>özellik değişti olayı.|Şekline|Hiçbiri|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>özellik değişti olayı.|Şekline|Denetim, kaydırma denetim modelini destekliyorsa, bu olayı desteklemelidir.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty>özellik değişti olayı.|Şekline|Denetim, kaydırma denetim modelini destekliyorsa, bu olayı desteklemelidir.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty>özellik değişti olayı.|Şekline|Denetim, kaydırma denetim modelini destekliyorsa, bu olayı desteklemelidir.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty>özellik değişti olayı.|Şekline|Denetim, kaydırma denetim modelini destekliyorsa, bu olayı desteklemelidir.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>özellik değişti olayı.|Şekline|Denetim, kaydırma denetim modelini destekliyorsa, bu olayı desteklemelidir.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty>özellik değişti olayı.|Şekline|Denetim, kaydırma denetim modelini destekliyorsa, bu olayı desteklemelidir.|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Gerekli|Hiçbiri|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.ControlType.Calendar>
- [UI Otomasyon Denetim Türlerine Genel Bakış](ui-automation-control-types-overview.md)
- [UI Otomasyonuna Genel Bakış](ui-automation-overview.md)
