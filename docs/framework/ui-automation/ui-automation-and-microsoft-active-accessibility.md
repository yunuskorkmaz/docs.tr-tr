---
title: UI Otomasyonu ve Microsoft Active Accessibility
ms.date: 03/30/2017
helpviewer_keywords:
- Active Accessibility
- UI Automation, Active Accessibility compared to
- UI Automation, Microsoft Active Accessibility
- Active Accessibility, UI Automation compared to
ms.assetid: 87bee662-0a3e-4232-a421-20e7a5968321
ms.openlocfilehash: 9a84c344ffabdaaa9d0aed68b05b7a4449776789
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179987"
---
# <a name="ui-automation-and-microsoft-active-accessibility"></a>UI Otomasyonu ve Microsoft Active Accessibility
> [!NOTE]
> Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır. Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Microsoft Active Accessibility, uygulamaları erişilebilir hale getirmek için daha önceki çözümdü. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]Microsoft Windows için yeni erişilebilirlik modelidir ve yardımcı teknoloji ürünlerinin ve otomatik test araçlarının gereksinimlerini karşılamayı amaçlamaktadır. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Etkin Erişilebilirlik üzerinde birçok iyileştirme sunar.  
  
 Bu konu, bu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özelliklerin Etkin Erişilebilirlik'ten nasıl farklı olduğunu temel özellikleri içerir ve açıklar.  
  
<a name="Programming_Languages_compare"></a>
## <a name="programming-languages"></a>Programlama Dilleri  
<Active Accessibility, çift arabirim desteğine sahip Bileşen Nesne Modeli'ni (COM) temel almaktadır ve bu nedenle C/C++, Microsoft Visual Basic 6.0 ve komut dosyası dillerinde programlanabilir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)](standart denetimler için istemci tarafı sağlayıcı kitaplığı dahil) yönetilen kodla yazılır ve Kullanıcı Arabirimi Otomasyonistemci uygulamaları en kolay C# veya Visual Basic .NET kullanılarak programlanır. Arayüz uygulamaları olan Kullanıcı Arabirimi Otomasyon sağlayıcıları yönetilen kodla veya C/C++ olarak yazılabilir.  
  
<a name="Support_in_Windows_Presentation_Foundation_"></a>
## <a name="support-in-windows-presentation-foundation"></a>Windows Presentation Foundation'da Destek  
 Windows Presentation Foundation (WPF), kullanıcı arabirimleri oluşturmak için yeni bir modeldir. WPF öğeleri Etkin Erişilebilirlik için yerel destek içermez; ancak, Etkin [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Erişilebilirlik istemcileri için köprüleme desteği içeren destek yaparlar. Yalnızca özel olarak [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] yazılmış istemciler, metin için zengin destek gibi WPF'nin erişilebilirlik özelliklerinden tam olarak yararlanabilir.  
  
<a name="Servers_and_Clients_compare"></a>
## <a name="servers-and-clients"></a>Sunucular ve İstemciler  
 Etkin Erişilebilirlik'te sunucular ve istemciler, büyük ölçüde sunucunun `IAccessible`'.  
  
 In, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bir çekirdek hizmet sunucu (sağlayıcı olarak adlandırılır) ve istemci arasında yatıyor. Temel hizmet, sağlayıcılar tarafından uygulanan arabirimlere çağrılar yapar ve öğeler için benzersiz çalışma zamanı tanımlayıcıları oluşturma gibi ek hizmetler sağlar. İstemci uygulamaları hizmeti aramak [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] için kitaplık işlevlerini kullanır.  
  
 Kullanıcı BirLeşme Otomasyonu sağlayıcıları Etkin Erişilebilirlik istemcilerine bilgi sağlayabilir ve Etkin Erişilebilirlik sunucuları UI Automation istemci uygulamalarına bilgi sağlayabilir. Ancak, Etkin Erişilebilirlik kadar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]çok bilgi açığa olmadığından, iki model tam olarak uyumlu değildir.  
  
<a name="UI_Elements_compare"></a>
## <a name="ui-elements"></a>UI Elemanları  
 Etkin Erişilebilirlik [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğeleri arabirim `IAccessible` olarak veya alt tanımlayıcı olarak sunar. Aynı öğeye başvurup başvurmadıklarını belirlemek için iki `IAccessible` işaretçiyi karşılaştırmak zordur.  
  
 In [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], her öğe bir <xref:System.Windows.Automation.AutomationElement> nesne olarak temsil edilir. Karşılaştırma eşitlik işleci veya <xref:System.Windows.Automation.AutomationElement.Equals%2A> her ikisi de elemanların benzersiz çalışma zamanı tanımlayıcıları karşılaştırın yöntemi kullanılarak yapılır.  
  
<a name="Tree_Views_and_Navigation_compare"></a>
## <a name="tree-views-and-navigation"></a>Ağaç Görünümleri ve Gezinme  
 Ekrandaki [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] öğeler, kökü olarak masaüstü, hemen alt olarak uygulama pencereleri ve daha fazla torun olarak uygulamalar içinde öğeleri ile bir ağaç yapısı olarak görülebilir.  
  
 Etkin Erişilebilirlik'te, son kullanıcılarla ilgisi olmayan birçok otomasyon öğesi ağaçta görünür. İstemci uygulamaları anlamlı olduğunu belirlemek için tüm öğeleri bakmak zorunda.  
  
 UI Automation istemci uygulamaları [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] filtrelenmiş bir görünüme bakın. Görünüm yalnızca ilgi çekici öğeler içerir: kullanıcıya bilgi veren veya etkileşimi sağlayan öğeler. Yalnızca denetim elemanlarının önceden tanımlanmış görünümleri ve yalnızca içerik öğeleri mevcuttur; ayrıca, uygulamalar özel görünümler tanımlayabilir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)][!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] kullanıcıya açıklayan ve kullanıcının uygulamayla etkileşime geçmesine yardımcı olmak görevini basitleştirir.  
  
 Etkin Erişilebilirlik'te öğeler arasında gezinme, uzamsal (örneğin, ekranda solda yatan öğeye taşıma), mantıksal (örneğin, bir sonraki menü öğesine veya iletişim kutusu içindeki sekme sırasına göre bir sonraki öğeye taşıma) veya hiyerarşiktir ( örneğin, ilk çocuğu bir kapta veya alttan ebeveynine taşımak). Hiyerarşik gezinme, alt öğelerin her zaman uygulayan `IAccessible`nesneler olmaması yla karmaşıktır.  
  
 Tüm [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğeler aynı <xref:System.Windows.Automation.AutomationElement> temel işlevselliği destekleyen nesnelerdir. (Sağlayıcı açısından bakıldığında, bunlar bir arabirim devralınan uygulayan <xref:System.Windows.Automation.Provider.IRawElementProviderSimple>nesnelerdir.) Gezinme çoğunlukla hiyerarşiktir: ebeveynlerden çocuklara ve bir kardeşten diğerine. (Sekme sırasını izleyebilecek şekilde kardeşler arasında gezinmenin mantıksal bir öğesi vardır.) Sınıfı kullanarak ağacın filtrelenmiş herhangi bir görünümünü kullanarak herhangi bir <xref:System.Windows.Automation.TreeWalker> başlangıç noktasından gezinebilirsiniz. Ayrıca kullanarak <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> belirli çocuklar veya torunları için <xref:System.Windows.Automation.AutomationElement.FindAll%2A>gidebilirsiniz ve; örneğin, belirli bir denetim deseni destekleyen bir iletişim kutusu içindeki tüm öğeleri almak çok kolaydır.  
  
 Gezinme, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Etkin Erişilebilirlik'ten daha tutarlıdır. Açılır listeler ve açılır pencereler gibi bazı öğeler Etkin Erişilebilirlik ağacında iki kez görünür ve bunlardan gezinme beklenmeyen sonuçlar doğurabilir. Aslında bir çubuk denetimi için Etkin Erişilebilirliği düzgün bir şekilde uygulamak mümkün değildir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]pencerelerin sahiplenilmesitarafından dayatılan hiyerarşiye rağmen bir öğenin ağacın herhangi bir yerine yerleştirilebilmesini sağlayarak yeniden ebeveynlik ve yeniden konumlandırmayı sağlar.  
  
<a name="Roles_and_Control_Types"></a>
## <a name="roles-and-control-types"></a>Roller ve Kontrol Türleri  
 Etkin Erişilebilirlik , `accRole` ROLE_SYSTEM_SLIDER`IAccessible::get_actRole`veya ROLE_SYSTEM_MENUITEM gibi öğenin rolünün [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]açıklamasını almak için özelliği ( ) kullanır. Bir öğenin rolü, kullanılabilir işlevselliğinin ana ipucudur. Bir kontrol ile etkileşim gibi `IAccessible::accSelect` sabit yöntemler `IAccessible::accDoDefaultAction`kullanılarak elde edilir ve . İstemci uygulaması ve [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] etkileşim ilerler. `IAccessible`  
  
 Buna karşılık, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] büyük ölçüde öğenin denetim türünü <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> (özellik tarafından açıklanan) beklenen işlevselliği ayırın. İşlevsellik, özel arabirimlerin uygulanması yoluyla sağlayıcı tarafından desteklenen denetim desenleri tarafından belirlenir. Denetim desenleri, belirli [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] bir öğe tarafından desteklenen işlevselliğin tam kümesini tanımlamak için birleştirilebilir. Bazı sağlayıcıların belirli bir denetim deseni desteklemesi gerekir; örneğin, bir onay kutusu sağlayıcısı toggle denetim deseni desteklemesi gerekir. Diğer sağlayıcılar bir dizi denetim deleklerini desteklemeli; örneğin, bir düğme toggle veya Invoke'ı desteklemelidir. Yine de diğerleri hiçbir kontrol desenleri destek; örneğin, taşınamayan, yeniden boyutlandırılamayan veya kenetlenemeyen bir bölmenin denetim desenleri yoktur.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<xref:System.Windows.Automation.ControlType.Custom> özellik tarafından tanımlanan ve özellik tarafından açıklanabilecek <xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty> özel denetimleri destekler.  
  
 Aşağıdaki tablo, etkin erişilebilirlik rollerinin [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] denetim türlerine eşlenemesini gösterir.  
  
|Etkin Erişilebilirlik rolü|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]kontrol türü|  
|----------------------------------------------------------------------|----------------------------------------------------------------------------------------|  
|ROLE_SYSTEM_PUSHBUTTON|Düğme|  
|ROLE_SYSTEM_CLIENT|Takvim|  
|ROLE_SYSTEM_CHECKBUTTON|Onay kutusu|  
|ROLE_SYSTEM_COMBOBOX|Açılır kutu|  
|ROLE_SYSTEM_CLIENT|Özel|  
|ROLE_SYSTEM_LIST|Veri ızgarası|  
|ROLE_SYSTEM_LISTITEM|Veri öğesi|  
|ROLE_SYSTEM_DOCUMENT|Belge|  
|ROLE_SYSTEM_TEXT|Düzenle|  
|ROLE_SYSTEM_GROUPING|Grup|  
|ROLE_SYSTEM_LIST|Üst bilgi|  
|ROLE_SYSTEM_COLUMNHEADER|Üstbilgi öğesi|  
|ROLE_SYSTEM_LINK|Köprü|  
|ROLE_SYSTEM_GRAPHIC|Görüntü|  
|ROLE_SYSTEM_LIST|Liste|  
|ROLE_SYSTEM_LISTITEM|Liste öğesi|  
|ROLE_SYSTEM_MENUPOPUP|Menü|  
|ROLE_SYSTEM_MENUBAR|Menü çubuğu|  
|ROLE_SYSTEM_MENUITEM|Menü öğesi|  
|ROLE_SYSTEM_PANE|Bölme|  
|ROLE_SYSTEM_PROGRESSBAR|İlerleme çubuğu|  
|ROLE_SYSTEM_RADIOBUTTON|Radyo düğmesi|  
|ROLE_SYSTEM_SCROLLBAR|Kaydırma çubuğu|  
|ROLE_SYSTEM_SEPARATOR|Ayırıcı|  
|ROLE_SYSTEM_SLIDER|Kaydırıcı|  
|ROLE_SYSTEM_SPINBUTTON|Değer Değiştirici|  
|ROLE_SYSTEM_SPLITBUTTON|Bölme düğmesi|  
|ROLE_SYSTEM_STATUSBAR|Durum çubuğu|  
|ROLE_SYSTEM_PAGETABLIST|Tab|  
|ROLE_SYSTEM_PAGETAB|Sekme öğesi|  
|ROLE_SYSTEM_TABLE|Tablo|  
|ROLE_SYSTEM_STATICTEXT|Metin|  
|ROLE_SYSTEM_INDICATOR|Parmak|  
|ROLE_SYSTEM_TITLEBAR|Başlık çubuğu|  
|ROLE_SYSTEM_TOOLBAR|Araç çubuğu|  
|ROLE_SYSTEM_TOOLTIP|ToolTip|  
|ROLE_SYSTEM_OUTLINE|Ağaç|  
|ROLE_SYSTEM_OUTLINEITEM|Ağaç öğesi|  
|ROLE_SYSTEM_WINDOW|Pencere|  
  
 Farklı denetim türleri hakkında daha fazla bilgi için [UI Otomasyon Kontrol Türleri'ne](ui-automation-control-types.md)bakın.  
  
<a name="States_and_Properties"></a>
## <a name="states-and-properties"></a>Durumlar ve Özellikler  
 Etkin Erişilebilirlik'te, öğeler ortak bir özellik kümesini destekler `accState`ve bazı özellikler (örneğin) öğenin rolüne bağlı olarak çok farklı şeyleri tanımlamalıdır. Sunucular, öğeyle `IAccessible` ilgili olmayanlar da olsa, bir özelliği döndüren tüm yöntemleri uygulamalıdır.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bazıları Etkin Erişilebilirlik'teki durumlara karşılık gelen çok daha fazla özellik tanımlar. Bazıları tüm öğeler için ortak, ancak diğerleri denetim türleri ve denetim desenleri için özeldir. Özellikler benzersiz tanımlayıcılarla ayırt edilir ve çoğu özellik tek bir yöntem kullanılarak alınabilir <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>veya . Birçok özellik de kolayca <xref:System.Windows.Automation.AutomationElement.Current%2A> ve <xref:System.Windows.Automation.AutomationElement.Cached%2A> özellik erişimci alınır.  
  
 Bir UI Automation sağlayıcısı alakasız özellikleri uygulamak zorunda değildir, `null` ancak desteklemiyor herhangi bir özellik için bir değer döndürebilir. Ayrıca, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] temel hizmet varsayılan pencere sağlayıcısından bazı özellikler alabilir ve bunlar sağlayıcı tarafından açıkça uygulanan özelliklerle birleştirilmiştir.  
  
 Çok daha fazla özelliği desteklemenin yanı sıra, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] birden çok özelliğin tek bir çapraz işlem çağrısıyla alınmasına izin vererek daha iyi performans sağlar.  
  
 Aşağıdaki tablo, iki modeldeki özellikler arasındaki yazışmaları gösterir.  
  
|Etkin Erişilebilirlik özellik erişimcisi|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]özellik kimliği|Açıklamalar|  
|-----------------------------------------------------------------------------------|---------------------------------------------------------------------------------------|-------------|  
|`get_accKeyboardShortcut`|<xref:System.Windows.Automation.AutomationElement.AccessKeyProperty> veya <xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>|`AccessKeyProperty`her ikisi de varsa önceliklidir.|  
|`get_accName`|<xref:System.Windows.Automation.AutomationElement.NameProperty>||  
|`get_accRole`|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>|Rolleri denetlemek türlerine eşleme için önceki tabloya bakın.|  
|`get_accValue`|<xref:System.Windows.Automation.ValuePattern.ValueProperty?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.RangeValuePattern.ValueProperty?displayProperty=nameWithType>|Yalnızca ValuePattern veya RangeValuePattern'i destekleyen denetim türleri için geçerlidir. RangeValue değerleri, MSAA davranışıyla tutarlı olacak şekilde 0-100'e normalleştirilmiştir. Değer öğeleri bir dize kullanır.|  
|`get_accHelp`|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>||  
|`accLocation`|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>||  
|`get_accDescription`|Desteklenmiyor[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|`accDescription`msaa içinde net bir belirtim yoktu, bu da sağlayıcıların bu özelliğe farklı bilgi parçaları yerleştirmesi ile sonuçlandı.|  
|`get_accHelpTopic`|Desteklenmiyor[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]||  
  
 Aşağıdaki tabloda [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] hangi özelliklerin Etkin Erişilebilirlik durumu sabitlerine karşılık gelir gösterilmektedir.  
  
|Etkin Erişilebilirlik durumu|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Özellik|Durum Değişimini Tetikler mi?|  
|-----------------------------------------------------------------------|------------------------------------------------------------------------------------|----------------------------|  
|STATE_SYSTEM_CHECKED|Onay kutusu için,<xref:System.Windows.Automation.TogglePattern.ToggleStateProperty><br /><br /> Radyo düğmesi için,<xref:System.Windows.Automation.SelectionItemPattern.IsSelectedProperty>|E|  
|STATE_SYSTEM_COLLAPSED|<xref:System.Windows.Automation.ExpandCollapsePattern.ExpandCollapsePatternInformation.ExpandCollapseState%2A> = <xref:System.Windows.Automation.ExpandCollapseState.Collapsed>|E|  
|STATE_SYSTEM_EXPANDED|<xref:System.Windows.Automation.ExpandCollapsePattern.ExpandCollapsePatternInformation.ExpandCollapseState%2A> = <xref:System.Windows.Automation.ExpandCollapseState.Expanded>Veya<xref:System.Windows.Automation.ExpandCollapseState.PartiallyExpanded>|E|  
|STATE_SYSTEM_FOCUSABLE|<xref:System.Windows.Automation.AutomationElement.IsKeyboardFocusableProperty>|N|  
|STATE_SYSTEM_FOCUSED|<xref:System.Windows.Automation.AutomationElement.HasKeyboardFocusProperty>|N|  
|STATE_SYSTEM_HASPOPUP|<xref:System.Windows.Automation.ExpandCollapsePattern>menü öğeleri için|N|  
|STATE_SYSTEM_INVISIBLE|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty>= Doğru <xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A> ve nedenleri<xref:System.Windows.Automation.NoClickablePointException>|N|  
|STATE_SYSTEM_LINKED|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> =<br /><br /> <xref:System.Windows.Automation.ControlType.Hyperlink>|N|  
|STATE_SYSTEM_MIXED|<xref:System.Windows.Automation.TogglePattern.TogglePatternInformation.ToggleState%2A> = <xref:System.Windows.Automation.ToggleState.Indeterminate>|N|  
|STATE_SYSTEM_MOVEABLE|<xref:System.Windows.Automation.TransformPattern.CanMoveProperty>|N|  
|STATE_SYSTEM_MUTLISELECTABLE|<xref:System.Windows.Automation.SelectionPattern.CanSelectMultipleProperty>|N|  
|STATE_SYSTEM_OFFSCREEN|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty>= Doğru|N|  
|STATE_SYSTEM_PROTECTED|<xref:System.Windows.Automation.AutomationElement.IsPasswordProperty>|N|  
|STATE_SYSTEM_READONLY|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty?displayProperty=nameWithType> ve <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty?displayProperty=nameWithType>|N|  
|STATE_SYSTEM_SELECTABLE|<xref:System.Windows.Automation.SelectionItemPattern>desteklenir|N|  
|STATE_SYSTEM_SELECTED|<xref:System.Windows.Automation.SelectionItemPattern.IsSelectedProperty>|N|  
|STATE_SYSTEM_SIZEABLE|<xref:System.Windows.Automation.TransformPattern.TransformPatternInformation.CanResize%2A>|N|  
|STATE_SYSTEM_UNAVAILABLE|<xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>|E|  
  
 Aşağıdaki durumlar ya çoğu Etkin Erişilebilirlik denetim sunucuları tarafından uygulanmadı ya da ''ın ''ın eşdeğeri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]yok.  
  
|Etkin Erişilebilirlik durumu|Açıklamalar|  
|-----------------------------------------------------------------------|-------------|  
|STATE_SYSTEM_BUSY|Şu anda kullanılamıyor[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_DEFAULT|Şu anda kullanılamıyor[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_ANIMATED|Şu anda kullanılamıyor[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_EXTSELECTABLE|Etkin Erişilebilirlik sunucuları tarafından yaygın olarak uygulanmaz|  
|STATE_SYSTEM_MARQUEED|Etkin Erişilebilirlik sunucuları tarafından yaygın olarak uygulanmaz|  
|STATE_SYSTEM_SELFVOICING|Etkin Erişilebilirlik sunucuları tarafından yaygın olarak uygulanmaz|  
|STATE_SYSTEM_TRAVERSED|Şu anda kullanılamıyor[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_ALERT_HIGH|Etkin Erişilebilirlik sunucuları tarafından yaygın olarak uygulanmaz|  
|STATE_SYSTEM_ALERT_MEDIUM|Etkin Erişilebilirlik sunucuları tarafından yaygın olarak uygulanmaz|  
|STATE_SYSTEM_ALERT_LOW|Etkin Erişilebilirlik sunucuları tarafından yaygın olarak uygulanmaz|  
|STATE_SYSTEM_FLOATING|Etkin Erişilebilirlik sunucuları tarafından yaygın olarak uygulanmaz|  
|STATE_SYSTEM_HOTTRACKED|Şu anda kullanılamıyor[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_PRESSED|Şu anda kullanılamıyor[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
  
 Özellik tanımlayıcılarının [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tam listesi için [UI Otomasyon Özellikleri Genel Bakış](ui-automation-properties-overview.md)bölümüne bakın.  
  
<a name="uiautomation_events_compare"></a>
## <a name="events"></a>Olaylar  
 Etkin Erişilebilirlik'tekinin [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]aksine, Windows olay yönlendirmesine (pencere tutamaçlarıyla yakından bağlanmış olan) olay mekanizması güvenmez ve istemci uygulamasının kancaları ayarlamasını gerektirmez. Etkinliklere abonelikler sadece belirli olaylara değil, ağacın belirli bölümlerine de ince ayar yapılabilir. Sağlayıcılar ayrıca, hangi olayların dinlendiğini takip ederek etkinlikleri yükseltmelerinde ince ayar yapabilir.  
  
 Bunlar doğrudan olay geri çağırmasına geçirildiği için, istemcilerin olayları yükselten öğeleri almak da daha kolaydır. İstemci olaya abone olduğunda önbellek isteği etkinse, öğenin özellikleri otomatik olarak önceden alınır.  
  
 Aşağıdaki tabloda Etkin Erişilebilirlik WinEvents ve [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayların yazışmaları gösterilmektedir.  
  
|WinEvent|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]olay tanımlayıcısı|  
|--------------|--------------------------------------------------------------------------------------------|  
|EVENT_OBJECT_ACCELERATORCHANGE|<xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>özellik değişikliği|  
|EVENT_OBJECT_CONTENTSCROLLED|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty>veya <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> ilişkili kaydırma çubuklarında özellik değişikliği|  
|EVENT_OBJECT_CREATE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_DEFACTIONCHANGE|Eşdeğeri yok|  
|EVENT_OBJECT_DESCRIPTIONCHANGE|Kesin bir eşdeğeri yoktur; belki <xref:System.Windows.Automation.AutomationElement.HelpTextProperty> <xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty> veya mülkiyet değişikliği|  
|EVENT_OBJECT_DESTROY|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_FOCUS|<xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent>|  
|EVENT_OBJECT_HELPCHANGE|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>Değiştirmek|  
|EVENT_OBJECT_HIDE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_LOCATIONCHANGE|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>özellik değişikliği|  
|EVENT_OBJECT_NAMECHANGE|<xref:System.Windows.Automation.AutomationElement.NameProperty>özellik değişikliği|  
|EVENT_OBJECT_PARENTCHANGE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_REORDER|Etkin Erişilebilirlik'te sürekli olarak kullanılmaz. Doğrudan karşılık gelen olay [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]tanımlanır.|  
|EVENT_OBJECT_SELECTION|<xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent>|  
|EVENT_OBJECT_SELECTIONADD|<xref:System.Windows.Automation.SelectionItemPattern.ElementAddedToSelectionEvent>|  
|EVENT_OBJECT_SELECTIONREMOVE|<xref:System.Windows.Automation.SelectionItemPattern.ElementRemovedFromSelectionEvent>|  
|EVENT_OBJECT_SELECTIONWITHIN|Eşdeğeri yok|  
|EVENT_OBJECT_SHOW|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_STATECHANGE|Çeşitli özellik değiştirilen olaylar|  
|EVENT_OBJECT_VALUECHANGE|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty?displayProperty=nameWithType>ve <xref:System.Windows.Automation.ValuePattern.ValueProperty?displayProperty=nameWithType> değişti|  
|EVENT_SYSTEM_ALERT|Eşdeğeri yok|  
|EVENT_SYSTEM_CAPTUREEND|Eşdeğeri yok|  
|EVENT_SYSTEM_CAPTURESTART|Eşdeğeri yok|  
|EVENT_SYSTEM_CONTEXTHELPEND|Eşdeğeri yok|  
|EVENT_SYSTEM_CONTEXTHELPSTART|Eşdeğeri yok|  
|EVENT_SYSTEM_DIALOGEND|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|  
|EVENT_SYSTEM_DIALOGSTART|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|  
|EVENT_SYSTEM_DRAGDROPEND|Eşdeğeri yok|  
|EVENT_SYSTEM_DRAGDROPSTART|Eşdeğeri yok|  
|EVENT_SYSTEM_FOREGROUND|<xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent>|  
|EVENT_SYSTEM_MENUEND|<xref:System.Windows.Automation.AutomationElement.MenuClosedEvent>|  
|EVENT_SYSTEM_MENUPOPUPEND|<xref:System.Windows.Automation.AutomationElement.MenuClosedEvent>|  
|EVENT_SYSTEM_MENUPOPUPSTART|<xref:System.Windows.Automation.AutomationElement.MenuOpenedEvent>|  
|EVENT_SYSTEM_MENUSTART|<xref:System.Windows.Automation.AutomationElement.MenuOpenedEvent>|  
|EVENT_SYSTEM_MINIMIZEEND|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty>özellik değişikliği|  
|EVENT_SYSTEM_MINIMIZESTART|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty>özellik değişikliği|  
|EVENT_SYSTEM_MOVESIZEEND|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>özellik değişikliği|  
|EVENT_SYSTEM_MOVESIZESTART|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>özellik değişikliği|  
|EVENT_SYSTEM_SCROLLINGEND|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty>veya <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> özellik değişikliği|  
|EVENT_SYSTEM_SCROLLINGSTART|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty>veya <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> özellik değişikliği|  
|EVENT_SYSTEM_SOUND|Eşdeğeri yok|  
|EVENT_SYSTEM_SWITCHEND|Eşdeğeri yok, <xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent> ancak bir olay yeni bir uygulamanın odak noktasını aldığının sinyallerini veriyor|  
|EVENT_SYSTEM_SWITCHSTART|Eşdeğeri yok|  
|Eşdeğeri yok|<xref:System.Windows.Automation.MultipleViewPattern.CurrentViewProperty>özellik değişikliği|  
|Eşdeğeri yok|<xref:System.Windows.Automation.ScrollPattern.HorizontallyScrollableProperty>özellik değişikliği|  
|Eşdeğeri yok|<xref:System.Windows.Automation.ScrollPattern.VerticallyScrollableProperty>özellik değişikliği|  
|Eşdeğeri yok|<xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty>özellik değişikliği|  
|Eşdeğeri yok|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty>özellik değişikliği|  
|Eşdeğeri yok|<xref:System.Windows.Automation.ScrollPattern.HorizontalViewSizeProperty>özellik değişikliği|  
|Eşdeğeri yok|<xref:System.Windows.Automation.ScrollPattern.VerticalViewSizeProperty>özellik değişikliği|  
|Eşdeğeri yok|<xref:System.Windows.Automation.TogglePattern.ToggleStateProperty>özellik değişikliği|  
|Eşdeğeri yok|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty>özellik değişikliği|  
|Eşdeğeri yok|<xref:System.Windows.Automation.AutomationElement.AsyncContentLoadedEvent>Olay|  
|Eşdeğeri yok|<xref:System.Windows.Automation.AutomationElement.ToolTipOpenedEvent>|  
  
<a name="Security_compare"></a>
## <a name="security"></a>Güvenlik  
 Bazı `IAccessible` özelleştirme senaryoları, bir `IAccessible` tabanı sarmave ona çağrı gerektirir. Kısmen güvenilen bir bileşen kod yolunda aracı olmaması gerektiğinden, bunun güvenlik etkileri vardır.  
  
 Model, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sağlayıcıların diğer sağlayıcı koduna arama gereksinimini ortadan kaldırır. Çekirdek [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] hizmet gerekli tüm toplama yapar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyon Temelleri](index.md)
