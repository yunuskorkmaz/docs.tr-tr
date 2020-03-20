---
title: Liste Denetim Türü İçin UI Otomasyon Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- control types, List
- List control type
- UI Automation, List control type
ms.assetid: 0e959fcb-50f2-413b-948d-7167d279bc11
ms.openlocfilehash: 2926e06cfbe065ad8a5bccdb7ebaf16596721def
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179715"
---
# <a name="ui-automation-support-for-the-list-control-type"></a>Liste Denetim Türü İçin UI Otomasyon Desteği
> [!NOTE]
> Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır. Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Liste denetim türü için destek hakkında bilgi sağlar. Denetim [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]türü, <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> özelliği kullanmak için denetimin karşılaması gereken koşullar kümesidir. Koşullar, ağaç yapısı, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değerleri ve denetim desenleri için özel yönergeler içerir.  
  
 Liste denetim türü, düz bir grup veya öğe gruplarını düzenlemek için bir yol sağlar ve kullanıcının bu öğelerden birini veya daha fazlasını seçmesine olanak tanır. Liste denetim türü, ne tür alt öğeler içerebileceğikonusunda gevşek bir kısıtlamaya sahiptir. Bu, UI Automation sağlayıcılarının seçim kapsayıcıları için iyi bilinen bir öğeyi desteklemesini sağlar.  
  
 Aşağıdaki [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bölümlerdeki gereksinimler, Liste denetim türünü uygulayan tüm [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]denetimler için geçerlidir, bunlar olsun, Win32 veya Windows Formları. Liste kapsayıcı denetimleri, Liste denetim türünü uygulayan denetimlerin bir örneğidir.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>
## <a name="required-ui-automation-tree-structure"></a>Gerekli UI Otomasyon Ağaç Yapısı  
 Aşağıdaki tablo, liste denetimleri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ile ilgili ağacın iki görünümünü görüntüler ve her görünümde nelerin bulunabileceğini açıklar. Denetim görünümü yalnızca denetimleri öğeleri içerir ve içerik görünümü ağaçtan gereksiz bilgileri kaldırır. Örneğin, açılan kutuyu etiketlemek için kullanılan bir metin `ComboBox NameProperty`denetimi . Metin denetimi zaten denetim görünümü aracılığıyla bu şekilde açık olduğundan, iki kez maruz kalması gereksizdir; bu nedenle içerik görünümünden kaldırılır. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ağaç hakkında daha fazla bilgi için [UI Automation Tree Genel Bakış'a](ui-automation-tree-overview.md)bakın.  
  
|Kontrol Görünümü|İçerik Görünümü|  
|------------------|------------------|  
|Denetimlere karşılık gelen öğeleri içerir.|Yardımcı teknolojilerin son kullanıcıya en küçük anlamlı bilgi kümesiyle çalışması için ağaçtan gereksiz bilgileri kaldırır.|  
|Liste<br /><br /> - DataItem (0 veya daha fazla)<br />- ListItem (0 veya daha fazla)<br />- Grup (0 veya daha fazla)<br />- ScrollBar (0, 1 veya 2)|Liste<br /><br /> - DataItem (0 veya daha fazla)<br />- ListItem (0 veya daha fazla)<br />- Grup (0 veya daha fazla)|  
  
 Liste denetim türünü (liste denetimi gibi) uygulayan bir denetimin denetim görünümü aşağıdakilerden oluşur:  
  
- Liste denetimindeki sıfır veya daha fazla öğe (öğeler Liste Öğesi veya Veri Öğesi denetim türlerine dayalı olabilir).
  
- Liste denetimi içinde sıfır veya daha fazla grup denetimi.
  
- Sıfır, bir veya iki kaydırma çubuğu denetimi.
  
Liste denetim türünü (liste denetimi gibi) uygulayan bir denetimin içerik görünümü aşağıdakilerden oluşur:  
  
- Liste denetimindeki sıfır veya daha fazla öğe (öğeler Liste Öğesi veya Veri Öğesi denetim türlerine dayalı olabilir).
  
- Liste denetiminde sıfır veya daha fazla grup.

Liste denetiminde, birlikte gruplandırılmak dışında hiyerarşik ilişkisi olan öğeler olmamalıdır. Öğelerin [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaçta alt öğesi varsa, liste kapsayıcısı Ağaç denetim türüne dayalı olmalıdır.  
  
 Liste denetimindeki seçilebilir öğeler, liste denetiminin [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacındaki soyundan gelenlerden kullanılabilir. Liste denetimindeki tüm öğeler aynı seçim grubuna ait olmalıdır. Listedeki seçilebilir öğeler ListItem (DataItem yerine) denetim türleri olarak açıklanmalıdır.  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Gerekli UI Otomasyon Özellikleri  
 Aşağıdaki tablo, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] değeri veya tanımı özellikle liste denetimleri ile alakalı olan özellikleri listeler. Özellikler hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] daha fazla bilgi [için, Müşteriler için Kullanıcı Arabirimi Otomasyon Özellikleri'ne](ui-automation-properties-for-clients.md)bakın.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Özellik|Değer|Notlar|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Notlara bakın.|Bu özelliğin değeri, bir uygulamadaki tüm denetimler arasında benzersiz olmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Notlara bakın.|Tüm denetimi içeren en dıştaki dikdörtgen.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Notlara bakın.|Liste denetiminde tıklanabilir bir nokta varsa (listenin odaklanmasına neden olmak için tıklanabilecek bir nokta), bu noktanın bu özellik aracılığıyla açıkta kalması gerekir.<br /><br /> `IsOffScreen` Mülkün değeri doğruysa, o zaman <xref:System.Windows.Automation.NoClickablePointException> yükseltilecektir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Notlara bakın.|Denetim klavye odağı alabiliyorsa, bu özelliği desteklemesi gerekir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Notlara bakın.|Bir liste denetiminin Ad özelliğinin değeri, kullanıcıdan seçmesi istenen seçenekler kategorisini iletmelidir. Bu özellik genellikle adını statik bir metin etiketinden alır. Statik bir metin etiketi yoksa, uygulama geliştiricisinin Ad özelliği için bir değer ortaya çıkarması gerekir.<br /><br /> Bu özelliğin liste denetimleri için gerekli olmadığı tek zaman, denetimin başka bir denetimin alt ağacı içinde kullanılmasıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Notlara bakın.|Statik bir metin etiketi varsa, bu özellik bu denetime bir başvuru göstermelidir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Liste|Bu değer tüm Ara bilgi arabirimi çerçeveleri için aynıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"liste"|Liste denetim türüne karşılık gelen yerelleştirilmiş dize.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|Liste denetimi her zaman [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacın içerik görünümüne eklenir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Liste denetimi her zaman [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacın denetim görünümüne dahildir.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|True|Kapsayıcı klavye girişini kabul edebiliyorsa, bu özellik değeri doğru olmalıdır.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|Notlara bakın.|Liste denetimleri için Yardım metni, kullanıcıdan neden seçenekler listesinden seçim yapmasının istendiğini açıklamalıdır. Örneğin, "Bu listeden bir öğe seçin, monitörünüzün ekran çözünürlüğünü ayarlar."|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>
## <a name="required-ui-automation-control-patterns-and-properties"></a>Gerekli UI Otomasyon Kontrol Desenleri ve Özellikleri  
 Aşağıdaki tablo, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] liste denetimleri tarafından desteklenmesi gereken denetim desenlerini listeler. Denetim desenleri hakkında daha fazla bilgi için [UI Otomasyon Kontrol Modellerine Genel Bakış'a](ui-automation-control-patterns-overview.md)bakın.  
  
|Kontrol Deseni/Desen Özelliği|Destek / Değer|Notlar|  
|---------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Gerekli|Denetimde bulunan öğeler arasında bir `ISelectionProvider` seçim durumu korunduğunda Liste denetim türünü destekleyen tüm denetimler uygulanmalıdır. Kapsayıcıiçindeki öğeler seçilemiyorsa, Grup denetim türü kullanılmalıdır.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|-sına bağ -lıdır|Liste denetimleri her zaman bir öğenin seçilmesini gerektirmez.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|-sına bağ -lıdır|Liste denetimleri tek veya birden çok seçim kapsayıcısı olabilir.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|-sına bağ -lıdır|Kapsayıcıdaki öğeler kaydırılabilirse bu denetim deseni uygulayın.|  
|<xref:System.Windows.Automation.Provider.IGridProvider>|-sına bağ -lıdır|Kılavuz gezintisi madde bazında bir öğe üzerinde kullanılabilir olması gerektiğinde bu deseni uygulayın.|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider>|-sına bağ -lıdır|Denetim kapsayıcıdaki öğelerin birden çok kez görüntülenebilir, bu denetim deseni uygulayın.|  
|<xref:System.Windows.Automation.Provider.ITableProvider>|Hiçbir zaman|`ITableProvider`Liste denetim türü için hiçbir zaman desteklenmez. Denetim bu denetim deseni desteklemesi gerekiyorsa, denetim Veri Izgara denetim türüne dayalı olmalıdır.|  
  
<a name="Required_UI_Automation_Events"></a>
## <a name="required-ui-automation-events"></a>Gerekli UI Otomasyon Etkinlikleri  
 Aşağıdaki tablo, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tüm liste denetimleri tarafından desteklenmesi gereken olayları listeler. Etkinlikler hakkında daha fazla bilgi için [UI Otomasyon Etkinliklerine Genel Bakış'a](ui-automation-events-overview.md)bakın.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Olay|Destek / Değer|Notlar|  
|---------------------------------------------------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|-sına bağ -lıdır|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent>|-sına bağ -lıdır|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>özellik değiştirilen olay.|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>özellik değiştirilen olay.|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>özellik değiştirilen olay.|Gerekli|None|  
|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers.CurrentViewProperty>özellik değiştirilen olay.|-sına bağ -lıdır|None|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>özellik değiştirilen olay.|-sına bağ -lıdır|None|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty>özellik değiştirilen olay.|-sına bağ -lıdır|None|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty>özellik değiştirilen olay.|-sına bağ -lıdır|None|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty>özellik değiştirilen olay.|-sına bağ -lıdır|None|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>özellik değiştirilen olay.|-sına bağ -lıdır|None|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty>özellik değiştirilen olay.|-sına bağ -lıdır|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Gerekli|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Gerekli|None|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Automation.ControlType.List>
- [UI Otomasyonu Denetim Türlerine Genel Bakış](ui-automation-control-types-overview.md)
- [UI Otomasyonuna Genel Bakış](ui-automation-overview.md)
