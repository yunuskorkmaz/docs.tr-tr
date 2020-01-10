---
title: Liste Denetim Türü İçin UI Otomasyon Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- control types, List
- List control type
- UI Automation, List control type
ms.assetid: 0e959fcb-50f2-413b-948d-7167d279bc11
ms.openlocfilehash: d870452348f8837ec6773fc066ed52844f7acccd
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75741614"
---
# <a name="ui-automation-support-for-the-list-control-type"></a>Liste Denetim Türü İçin UI Otomasyon Desteği
> [!NOTE]
> Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu liste denetim türü için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] desteği hakkında bilgi sağlar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], denetim türü, bir denetimin <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> özelliğini kullanmak için karşılaması gereken koşullar kümesidir. Koşullar, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç yapısına yönelik özel yönergeler, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerleri ve Denetim desenleri içerir.  
  
 Liste denetim türü, düz bir grup veya öğe gruplarını düzenlemek için bir yol sağlar ve bir kullanıcının bu öğelerden birini veya birkaçını seçmesini sağlar. Liste denetim türünün içerebileceği alt öğe türleri için gevşek bir kısıtlaması vardır. Bu, UI Otomasyon sağlayıcılarının seçim kapsayıcıları için iyi bilinen bir öğeyi desteklemesini sağlar.  
  
 Aşağıdaki bölümlerde yer alan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gereksinimleri, [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], Win32 veya [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]bakılmaksızın liste denetim türünü uygulayan tüm denetimler için geçerlidir. Liste kapsayıcı denetimleri, liste denetim türünü uygulayan denetimlerin bir örneğidir.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyonu ağaç yapısı  
 Aşağıdaki tabloda, liste denetimleriyle ilgili [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacının iki görünümü gösterilmektedir ve her görünümde nelerin yer aldığı açıklanmaktadır. Denetim görünümü yalnızca denetimler olan öğeleri içerir ve içerik görünümü ağaçtan gereksiz bilgileri kaldırır. Örneğin, Birleşik giriş kutusunu etiketlemek için kullanılan bir metin denetimi `ComboBox NameProperty`olarak kullanıma sunulacaktır. Metin denetimi bu şekilde denetim görünümü aracılığıyla zaten kullanıma sunulduğundan, iki kez kullanıma sunulması gereksizdir; Bu nedenle içerik görünümünden kaldırılır. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı hakkında daha fazla bilgi için bkz. [UI Otomasyon ağacına genel bakış](ui-automation-tree-overview.md).  
  
|Denetim görünümü|İçerik görünümü|  
|------------------|------------------|  
|Denetimlere karşılık gelen öğeleri içerir.|Yardımcı teknolojilerin son kullanıcıya en küçük anlamlı bilgiler kümesiyle çalışması için gereksiz bilgileri ağaçtan kaldırır.|  
|List<br /><br /> -DataItem (0 veya daha fazla)<br />-ListItem (0 veya daha fazla)<br />-Grup (0 veya daha fazla)<br />-Kaydırma çubuğu (0, 1 veya 2)|List<br /><br /> -DataItem (0 veya daha fazla)<br />-ListItem (0 veya daha fazla)<br />-Grup (0 veya daha fazla)|  
  
 Liste denetim türünü uygulayan bir denetimin denetim görünümü (liste denetimi gibi) aşağıdakilerden oluşur:  
  
- Liste denetimindeki sıfır veya daha fazla öğe (Öğeler liste öğesine veya veri öğesi denetim türlerine göre olabilir).
  
- Liste denetimi içinde sıfır veya daha fazla Grup denetimi.
  
- Sıfır, bir veya iki kaydırma çubuğu denetimi.
  
Liste denetim türünü uygulayan bir denetimin içerik görünümü (örneğin, bir liste denetimi) aşağıdakilerden oluşur:  
  
- Liste denetimindeki sıfır veya daha fazla öğe (Öğeler liste öğesine veya veri öğesi denetim türlerine göre olabilir).
  
- Liste denetimi içinde sıfır veya daha fazla grup.

Liste denetiminde, hiyerarşik ilişkiye sahip olan öğeler birlikte gruplandırılmamalıdır. Öğelerin [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaçta alt öğesi varsa, liste kapsayıcısı ağaç denetim türünü temel almalıdır.  
  
 Liste denetimindeki seçilebilir öğeler, liste denetiminin [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacındaki alt öğelerde kullanılabilir olacaktır. Liste denetimindeki tüm öğelerin aynı seçim grubuna ait olması gerekir. Listedeki seçilebilir öğeler, Denetim türleri olarak ListItem (DataItem yerine DataItem) olarak gösterilmelidir.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon Özellikleri  
 Aşağıdaki tabloda, değeri veya tanımı özellikle liste denetimleriyle ilgili olan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri listelenmektedir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri hakkında daha fazla bilgi için bkz. [istemciler Için UI Otomasyon özellikleri](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özelliği|Değer|Notlar|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlara bakın.|Bu özelliğin değerinin bir uygulamadaki tüm denetimlerde benzersiz olması gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlara bakın.|Tüm denetimi içeren en dıştaki dikdörtgen.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Notlara bakın.|Liste denetiminin tıklatılabilir bir noktası varsa (listenin odaklanmasına neden olacak şekilde tıklanabilecek bir nokta), bu nokta bu özellik aracılığıyla gösterilmelidir.<br /><br /> `IsOffScreen` özelliğinin değeri true ise, <xref:System.Windows.Automation.NoClickablePointException> tetiklenir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Notlara bakın.|Denetim, klavye odağı alamıyorsa, bu özelliği desteklemesi gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlara bakın.|Liste denetiminin ad özelliğinin değeri, kullanıcının seçmesi istenen seçenek kategorisini iletmelidir. Bu özellik genellikle adını statik bir metin etiketinden alır. Statik bir metin etiketi yoksa, uygulama geliştiricisi ad özelliği için bir değer kullanıma sunmalıdır.<br /><br /> Tek zaman bu özellik liste denetimleri için gerekli değildir çünkü denetim başka bir denetimin alt ağacı içinde kullanılır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Notlara bakın.|Statik bir metin etiketi varsa, bu özellik bu denetimin bir başvurusunu kullanıma sunmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|List|Bu değer tüm UI çerçeveleri için aynıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|Listele|Liste denetim türüne karşılık gelen yerelleştirilmiş dize.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Doğru|Liste denetimi her zaman [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacının içerik görünümüne dahil edilmiştir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Doğru|Liste denetimi her zaman [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacının denetim görünümüne dahil edilmiştir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Doğru|Kapsayıcı klavye girişini kabul edebiliyorsa, bu özellik değeri doğru olmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|Notlara bakın.|Liste denetimleri için yardım metni, kullanıcıdan neden bir seçenek listesinden seçim yapması istendiğini açıklamalıdır. Örneğin, "Bu listeden bir öğe seçimi, monitörünüzün ekran çözünürlüğünü ayarlar."|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns-and-properties"></a>Gerekli UI Otomasyonu Denetim desenleri ve özellikleri  
 Aşağıdaki tabloda liste denetimleri tarafından desteklenmesi gereken [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Denetim desenleri listelenmektedir. Denetim desenleri hakkında daha fazla bilgi için bkz. [UI Otomasyonu Denetim desenlerine genel bakış](ui-automation-control-patterns-overview.md).  
  
|Denetim deseninin/deseninin özelliği|Destek/değer|Notlar|  
|---------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Gerekli|Denetim türünü destekleyen tüm denetimlerin, bir seçim durumu denetimde bulunan öğeler arasında tutuluyorsa `ISelectionProvider` uygulaması gerekir. Kapsayıcıda bulunan öğeler seçilemez ise, Grup denetim türü kullanılmalıdır.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Şekline|Liste denetimleri her zaman bir öğenin seçili olmasını gerektirmez.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Şekline|Liste denetimleri tek veya birden çok seçimli kapsayıcı olabilir.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Şekline|Kapsayıcıdaki öğeler kaydırılabilir ise bu denetim modelini uygulayın.|  
|<xref:System.Windows.Automation.Provider.IGridProvider>|Şekline|Bu kalıbı, kılavuz gezintisi öğe temelinde bir öğe üzerinde kullanılabilir olması gerektiğinde uygulayın.|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider>|Şekline|Denetim, kapsayıcıdaki öğelerin birden çok görünümünü destekleyebiliyorsanız bu denetim modelini uygulayın.|  
|<xref:System.Windows.Automation.Provider.ITableProvider>|hiçbir zaman|`ITableProvider`, liste denetim türü için hiçbir şekilde desteklenmez. Denetimin bu denetim modelini desteklemesi gerekiyorsa, denetim veri kılavuzu denetim türünü temel almalıdır.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyon olayları  
 Aşağıdaki tabloda, tüm liste denetimleri tarafından desteklenmesi gereken [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayları listelenmektedir. Olaylar hakkında daha fazla bilgi için bkz. [UI Otomasyonu olaylarına genel bakış](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayı|Destek/değer|Notlar|  
|---------------------------------------------------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Şekline|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent>|Şekline|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>.|Gerekli|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>.|Gerekli|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>.|Gerekli|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.MultipleViewPatternIdentifiers.CurrentViewProperty>.|Şekline|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>.|Şekline|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty>.|Şekline|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty>.|Şekline|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty>.|Şekline|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>.|Şekline|Yok.|  
|özellik değişti olayı <xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty>.|Şekline|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|Yok.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|Yok.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.ControlType.List>
- [UI Otomasyonu Denetim Türlerine Genel Bakış](ui-automation-control-types-overview.md)
- [UI Otomasyonuna Genel Bakış](ui-automation-overview.md)
