---
title: UI Otomasyonu ve Microsoft Active Accessibility
ms.date: 03/30/2017
helpviewer_keywords:
- Active Accessibility
- UI Automation, Active Accessibility compared to
- UI Automation, Microsoft Active Accessibility
- Active Accessibility, UI Automation compared to
ms.assetid: 87bee662-0a3e-4232-a421-20e7a5968321
ms.openlocfilehash: f9fc7e2e1a6d5ee26f04b239723c6b7d4283dbce
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75632330"
---
# <a name="ui-automation-and-microsoft-active-accessibility"></a>UI Otomasyonu ve Microsoft Active Accessibility
> [!NOTE]
> Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Microsoft Etkin Erişilebilirlik, uygulamaları erişilebilir hale getirmek için daha önceki bir çözümdür. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)], Microsoft Windows için yeni erişilebilirlik modelidir ve yardımcı teknoloji ürünlerinin ve otomatikleştirilmiş test araçlarının ihtiyaçlarını karşılamak üzere tasarlanmıştır. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], etkin erişilebilirlik üzerinde birçok geliştirme sunar.  
  
 Bu konu, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ana özelliklerini içerir ve bu özelliklerin etkin erişilebilirlik 'ten nasıl farklı olduğunu açıklar.  
  
<a name="Programming_Languages_compare"></a>   
## <a name="programming-languages"></a>Programlama Dilleri  
Etkin Erişilebilirlik <, çift arabirimler desteğiyle bileşen nesne modeli (COM) tabanlıdır ve bu nedenle C/C++, Microsoft Visual Basic 6,0 ve komut dosyası dillerinde programlanabilir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] (Standart denetimler için istemci tarafı sağlayıcı kitaplığı dahil) yönetilen kodda yazılır ve UI Otomasyonu istemci uygulamaları, veya Visual Basic .NET kullanılarak C# kolayca programlanabilir. Arabirim uygulamaları olan UI Otomasyon sağlayıcıları yönetilen kodda veya C/C++dilinde yazılabilir.  
  
<a name="Support_in_Windows_Presentation_Foundation_"></a>   
## <a name="support-in-windows-presentation-foundation"></a>Windows Presentation Foundation desteği  
 Windows Presentation Foundation (WPF), Kullanıcı arabirimleri oluşturmak için yeni bir modeldir. WPF öğeleri, etkin erişilebilirlik için yerel destek içermez; Ancak, Etkin Erişilebilirlik istemcileri için köprü oluşturma desteğini içeren [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]destekler. Yalnızca [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] için özel olarak yazılan istemciler, zengin metin desteği gibi WPF 'nin erişilebilirlik özelliklerinden tam olarak yararlanabilmenizi sağlayabilir.  
  
<a name="Servers_and_Clients_compare"></a>   
## <a name="servers-and-clients"></a>Sunucular ve Istemciler  
 Etkin Erişilebilirlik 'de, sunucular ve istemciler büyük ölçüde sunucunun `IAccessible`uygulamasıyla doğrudan iletişim kurar.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], çekirdek hizmet sunucu (sağlayıcı olarak adlandırılır) ve istemci arasında yer alır. Çekirdek hizmet, sağlayıcılar tarafından uygulanan arabirimlere çağrı yapar ve öğeler için benzersiz çalışma zamanı tanımlayıcıları oluşturma gibi ek hizmetler sağlar. İstemci uygulamaları [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] hizmetini çağırmak için kitaplık işlevlerini kullanır.  
  
 UI Otomasyon sağlayıcıları Etkin Erişilebilirlik istemcilerine bilgi sağlayabilir ve Etkin Erişilebilirlik sunucuları UI Otomasyonu istemci uygulamalarına bilgi sağlayabilir. Ancak, Etkin Erişilebilirlik [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]kadar çok bilgi sunmadığından, iki model tamamen uyumlu değildir.  
  
<a name="UI_Elements_compare"></a>   
## <a name="ui-elements"></a>UI öğeleri  
 Etkin Erişilebilirlik [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğeleri `IAccessible` arabirimi ya da bir alt tanımlayıcı olarak sunar. Aynı öğeye başvurup başvurmadığını belirlemek için iki `IAccessible` işaretçileri karşılaştırmak zordur.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], her öğe bir <xref:System.Windows.Automation.AutomationElement> nesnesi olarak temsil edilir. Karşılaştırma, her ikisi de öğelerin benzersiz çalışma zamanı tanımlayıcılarını karşılaştıran eşitlik işleci veya <xref:System.Windows.Automation.AutomationElement.Equals%2A> yöntemi kullanılarak yapılır.  
  
<a name="Tree_Views_and_Navigation_compare"></a>   
## <a name="tree-views-and-navigation"></a>Ağaç görünümleri ve gezintisi  
 Ekrandaki [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] öğeleri, kök olarak masaüstüne sahip bir ağaç yapısı, hemen alt öğe olarak uygulama penceresi ve uygulamalar içindeki öğeleri daha ileri alt öğeler olarak görülebilir.  
  
 Etkin Erişilebilirlik 'de, son kullanıcılar için ilgisiz çok sayıda Otomasyon öğesi ağaçta kullanıma sunulur. İstemci uygulamalarının anlamlı olduğunu belirleyebilmek için tüm öğelere bakmamız gerekir.  
  
 UI Otomasyonu istemci uygulamaları filtrelenmiş bir görünüm üzerinden [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] görüntülenir. Görünüm yalnızca ilgilendiğiniz öğeleri içerir: kullanıcıya bilgi veren veya etkileşimi etkinleştiren kişiler. Yalnızca denetim öğelerinin ve yalnızca içerik öğelerinin önceden tanımlanmış görünümleri mevcuttur; Ayrıca, uygulamalar özel görünümleri tanımlayabilir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], kullanıcıya [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] açıklama ve kullanıcı uygulamayla etkileşime geçme görevini basitleştirir.  
  
 Etkin Erişilebilirlik 'de öğeler arasında gezinme, uzamsal (örneğin, ekranda sol tarafta yer alan öğeye geçme), mantıksal (örneğin, bir sonraki menü öğesine geçme veya bir iletişim kutusu içindeki sekme düzeninde bulunan bir sonraki öğe) ya da sıradüzenli ( Örneğin, bir kapsayıcıdaki ilk çocuğu veya alt öğeden üst öğesine taşıma). Hiyerarşik gezinti, alt öğelerin her zaman `IAccessible`uygulayan nesneler olmadığı gerçeşinde karmaşıktır.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], tüm [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğeleri aynı temel işlevselliği destekleyen nesneler <xref:System.Windows.Automation.AutomationElement>. (Sağlayıcının açısından, <xref:System.Windows.Automation.Provider.IRawElementProviderSimple>devralınan bir arabirimi uygulayan nesnelerdir.) Gezinti temel olarak hiyerarşik olarak, üst ve alt öğeler arasında ve bir eşdüzey bir sonrakine. (Eşdüzey öğeler arasında gezinme bir mantıksal öğe olur, çünkü sekme sırasını takip edebilir.) <xref:System.Windows.Automation.TreeWalker> sınıfını kullanarak, ağacın filtrelenmiş görünümünü kullanarak herhangi bir başlangıç noktasından gidebilirsiniz. Ayrıca, <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> ve <xref:System.Windows.Automation.AutomationElement.FindAll%2A>kullanarak belirli alt öğelere veya alt öğelere gidebilirsiniz; Örneğin, belirli bir denetim modelini destekleyen bir iletişim kutusu içindeki tüm öğeleri almak çok kolaydır.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gezinti, etkin erişilebilirlikle daha tutarlıdır. Açılır listeler ve açılır pencereler gibi bazı öğeler, Etkin Erişilebilirlik ağacında iki kez görünür ve onlardan gezinmede beklenmedik sonuçlara neden olabilir. Bir Rebar denetimi için etkin erişilebilirliği düzgün bir şekilde uygulamak olanaksızdır. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], yeniden konumlandırma ve konumlandırmayı etkinleştirerek, hiyerarşinin Windows 'un sahipliğini tarafından yerleştirilmesine rağmen ağacın herhangi bir yere yerleştirilebileceği şekilde.  
  
<a name="Roles_and_Control_Types"></a>   
## <a name="roles-and-control-types"></a>Roller ve denetim türleri  
 Etkin Erişilebilirlik, [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]ROLE_SYSTEM_SLIDER veya ROLE_SYSTEM_MENUITEM gibi öğe rolünün bir açıklamasını almak için `accRole` özelliğini (`IAccessible::get_actRole`) kullanır. Bir öğenin rolü, kullanılabilir işlevselliğine ana Clue ' dir. Denetim ile etkileşim, `IAccessible::accSelect` ve `IAccessible::accDoDefaultAction`gibi sabit yöntemler kullanılarak elde edilir. İstemci uygulaması ve [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] arasındaki etkileşim, `IAccessible`üzerinden yapılabilecekleri ile sınırlıdır.  
  
 Buna karşılık [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], öğenin denetim türünü (<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> özelliği tarafından tanımlanan) beklenen işlevden büyük ölçüde ayırır. İşlevselliği, sağlayıcı tarafından özelleştirilmiş arabirimlerin uygulanmasıyla desteklenen denetim desenleri tarafından belirlenir. Denetim desenleri, belirli bir [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğesi tarafından desteklenen işlevlerin tamamını tanımlayacak şekilde birleştirilebilir. Belirli bir denetim modelini desteklemek için bazı sağlayıcılar gereklidir; Örneğin, bir onay kutusu için sağlayıcı Iki durumlu denetim deseninin desteklenmesi gerekir. Diğer sağlayıcılar bir veya daha fazla denetim deseni kümesini desteklemek için gereklidir; Örneğin, bir düğme Iki durumlu veya Invoke desteklemelidir. Hala diğerleri hiç denetim deseni desteklemez; Örneğin, taşınamayan, yeniden boyutlandırılan veya sabitlenemez bir bölme herhangi bir denetim desenine sahip değildir.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], <xref:System.Windows.Automation.ControlType.Custom> özelliği tarafından tanımlanan ve <xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty> özelliği tarafından açıklanabilecek özel denetimleri destekler.  
  
 Aşağıdaki tabloda, Etkin Erişilebilirlik rollerinin [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] denetim türlerine eşlenmesi gösterilmektedir.  
  
|Etkin Erişilebilirlik rolü|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] denetim türü|  
|----------------------------------------------------------------------|----------------------------------------------------------------------------------------|  
|ROLE_SYSTEM_PUSHBUTTON|Düğme|  
|ROLE_SYSTEM_CLIENT|Takvim|  
|ROLE_SYSTEM_CHECKBUTTON|Onay kutusu|  
|ROLE_SYSTEM_COMBOBOX|Açılan kutu|  
|ROLE_SYSTEM_CLIENT|Özel|  
|ROLE_SYSTEM_LIST|Veri kılavuzu|  
|ROLE_SYSTEM_LISTITEM|Veri öğesi|  
|ROLE_SYSTEM_DOCUMENT|Belge|  
|ROLE_SYSTEM_TEXT|Düzenle|  
|ROLE_SYSTEM_GROUPING|Grup|  
|ROLE_SYSTEM_LIST|Üstbilgi|  
|ROLE_SYSTEM_COLUMNHEADER|Üstbilgi öğesi|  
|ROLE_SYSTEM_LINK|Köprü|  
|ROLE_SYSTEM_GRAPHIC|Görüntü|  
|ROLE_SYSTEM_LIST|List|  
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
|ROLE_SYSTEM_SPLITBUTTON|Bölünmüş düğme|  
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
  
 Farklı denetim türleri hakkında daha fazla bilgi için bkz. [UI Automation Denetim türleri](ui-automation-control-types.md).  
  
<a name="States_and_Properties"></a>   
## <a name="states-and-properties"></a>Durumlar ve Özellikler  
 Etkin Erişilebilirlik 'de, öğeler ortak bir özellikler kümesini destekler ve bazı özellikler (örneğin `accState`), öğenin rolüne bağlı olarak çok farklı şeyleri anlamalıdır. Sunucular, öğe ile ilgili olmayan bir özelliği döndüren tüm `IAccessible` yöntemlerini uygulamalıdır.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bazıları Etkin Erişilebilirlik 'deki durumlara karşılık gelen birçok daha fazla özelliği tanımlar. Bazıları tüm öğeler için ortaktır, ancak diğerleri denetim türlerine ve denetim düzenlerine özeldir. Özellikler benzersiz tanımlayıcılarla ayırt edilir ve çoğu özellik tek bir yöntem, <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> veya <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>kullanılarak alınabilir. Birçok özellik ayrıca <xref:System.Windows.Automation.AutomationElement.Current%2A> ve <xref:System.Windows.Automation.AutomationElement.Cached%2A> Özellik erişimcilerine de kolayca alınabilir.  
  
 Bir UI Otomasyon sağlayıcısının ilgisiz Özellikler uygulaması gerekmez, ancak desteklemediği özellikler için yalnızca bir `null` değeri döndürebilir. Ayrıca, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] çekirdek hizmeti, varsayılan pencere sağlayıcısından bazı özellikler edinebilir ve bunlar, sağlayıcı tarafından açıkça uygulanan özelliklerle kaynaştırılabilir.  
  
 Birçok daha fazla özelliği de destekleyerek [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], birden fazla özelliği tek bir çapraz işlem çağrısıyla alınmasına izin vererek daha iyi bir performans sağlar.  
  
 Aşağıdaki tabloda, iki modelde özellikler arasındaki yazışma gösterilmektedir.  
  
|Etkin erişilebilirlik özelliği erişimcisi|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik KIMLIĞI|Açıklamalar|  
|-----------------------------------------------------------------------------------|---------------------------------------------------------------------------------------|-------------|  
|`get_accKeyboardShortcut`|<xref:System.Windows.Automation.AutomationElement.AccessKeyProperty> veya <xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>|her ikisi de varsa `AccessKeyProperty` önceliği alır.|  
|`get_accName`|<xref:System.Windows.Automation.AutomationElement.NameProperty>||  
|`get_accRole`|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>|Denetim türlerini denetlemek için önceki tabloya bakın.|  
|`get_accValue`|<xref:System.Windows.Automation.ValuePattern.ValueProperty?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.RangeValuePattern.ValueProperty?displayProperty=nameWithType>|Yalnızca Valuemodel veya Rangevaluemodel destekleyen denetim türleri için geçerlidir. RangeValue değerleri, MSAA davranışıyla tutarlı olacak şekilde 0-100 olarak normalleştirilmelidir. Değer öğeleri bir dize kullanır.|  
|`get_accHelp`|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>||  
|`accLocation`|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>||  
|`get_accDescription`|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] desteklenmez|`accDescription`, bu özellikte farklı bilgi parçaları yerleştirmekte olan MSAA içinde açık bir belirtim içermiyordu.|  
|`get_accHelpTopic`|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] desteklenmez||  
  
 Aşağıdaki tabloda, hangi [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özelliklerinin etkin Erişilebilirlik durumu sabitlerine karşılık geldiği gösterilmektedir.  
  
|Etkin Erişilebilirlik durumu|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özelliği|Tetikleyiciler durum değişikliği mi?|  
|-----------------------------------------------------------------------|------------------------------------------------------------------------------------|----------------------------|  
|STATE_SYSTEM_CHECKED|Onay kutusu için <xref:System.Windows.Automation.TogglePattern.ToggleStateProperty><br /><br /> Radyo düğmesi için <xref:System.Windows.Automation.SelectionItemPattern.IsSelectedProperty>|Y|  
|STATE_SYSTEM_COLLAPSED|<xref:System.Windows.Automation.ExpandCollapsePattern.ExpandCollapsePatternInformation.ExpandCollapseState%2A> = <xref:System.Windows.Automation.ExpandCollapseState.Collapsed>|Y|  
|STATE_SYSTEM_EXPANDED|<xref:System.Windows.Automation.ExpandCollapsePattern.ExpandCollapsePatternInformation.ExpandCollapseState%2A> = <xref:System.Windows.Automation.ExpandCollapseState.Expanded> veya <xref:System.Windows.Automation.ExpandCollapseState.PartiallyExpanded>|Y|  
|STATE_SYSTEM_FOCUSABLE|<xref:System.Windows.Automation.AutomationElement.IsKeyboardFocusableProperty>|N|  
|STATE_SYSTEM_FOCUSED|<xref:System.Windows.Automation.AutomationElement.HasKeyboardFocusProperty>|N|  
|STATE_SYSTEM_HASPOPUP|menü öğeleri için <xref:System.Windows.Automation.ExpandCollapsePattern>|N|  
|STATE_SYSTEM_INVISIBLE|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty> = true ve <xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A> nedenler <xref:System.Windows.Automation.NoClickablePointException>|N|  
|STATE_SYSTEM_LINKED|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> =<br /><br /> <xref:System.Windows.Automation.ControlType.Hyperlink>|N|  
|STATE_SYSTEM_MIXED|<xref:System.Windows.Automation.TogglePattern.TogglePatternInformation.ToggleState%2A> = <xref:System.Windows.Automation.ToggleState.Indeterminate>|N|  
|STATE_SYSTEM_MOVEABLE|<xref:System.Windows.Automation.TransformPattern.CanMoveProperty>|N|  
|STATE_SYSTEM_MUTLISELECTABLE|<xref:System.Windows.Automation.SelectionPattern.CanSelectMultipleProperty>|N|  
|STATE_SYSTEM_OFFSCREEN|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty> = true|N|  
|STATE_SYSTEM_PROTECTED|<xref:System.Windows.Automation.AutomationElement.IsPasswordProperty>|N|  
|STATE_SYSTEM_READONLY|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty?displayProperty=nameWithType> ve <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty?displayProperty=nameWithType>|N|  
|STATE_SYSTEM_SELECTABLE|<xref:System.Windows.Automation.SelectionItemPattern> destekleniyor|N|  
|STATE_SYSTEM_SELECTED|<xref:System.Windows.Automation.SelectionItemPattern.IsSelectedProperty>|N|  
|STATE_SYSTEM_SIZEABLE|<xref:System.Windows.Automation.TransformPattern.TransformPatternInformation.CanResize%2A>|N|  
|STATE_SYSTEM_UNAVAILABLE|<xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>|Y|  
  
 Aşağıdaki durumlar, çoğu Etkin Erişilebilirlik denetimi sunucusu tarafından uygulanmadı veya [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]eşdeğer değildir.  
  
|Etkin Erişilebilirlik durumu|Açıklamalar|  
|-----------------------------------------------------------------------|-------------|  
|STATE_SYSTEM_BUSY|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 'de yok|  
|STATE_SYSTEM_DEFAULT|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 'de yok|  
|STATE_SYSTEM_ANIMATED|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 'de yok|  
|STATE_SYSTEM_EXTSELECTABLE|Etkin Erişilebilirlik sunucuları tarafından yaygın olarak uygulanmadı|  
|STATE_SYSTEM_MARQUEED|Etkin Erişilebilirlik sunucuları tarafından yaygın olarak uygulanmadı|  
|STATE_SYSTEM_SELFVOICING|Etkin Erişilebilirlik sunucuları tarafından yaygın olarak uygulanmadı|  
|STATE_SYSTEM_TRAVERSED|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 'de yok|  
|STATE_SYSTEM_ALERT_HIGH|Etkin Erişilebilirlik sunucuları tarafından yaygın olarak uygulanmadı|  
|STATE_SYSTEM_ALERT_MEDIUM|Etkin Erişilebilirlik sunucuları tarafından yaygın olarak uygulanmadı|  
|STATE_SYSTEM_ALERT_LOW|Etkin Erişilebilirlik sunucuları tarafından yaygın olarak uygulanmadı|  
|STATE_SYSTEM_FLOATING|Etkin Erişilebilirlik sunucuları tarafından yaygın olarak uygulanmadı|  
|STATE_SYSTEM_HOTTRACKED|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 'de yok|  
|STATE_SYSTEM_PRESSED|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 'de yok|  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik tanımlayıcılarının listesi için bkz. [UI Otomasyon özelliklerine genel bakış](ui-automation-properties-overview.md).  
  
<a name="uiautomation_events_compare"></a>   
## <a name="events"></a>Olaylar  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]içindeki olay mekanizması, Etkin Erişilebilirlik ' in aksine, Windows olay yönlendirme 'yi (pencere tutamaçlarıyla yakından ilişkilidir) kullanmaz ve istemci uygulamasının kancaları ayarlaması gerekmez. Olaylara yönelik abonelikler, yalnızca belirli olaylara değil ağacın belirli bölümlerine göre hassas bir şekilde ayarlanabilir. Sağlayıcılar, hangi olayların dinleneceği ile ilgili olayları izleyerek olayların kendi etkinliklerini de ayrıntılı olarak ayarlayabilir.  
  
 Ayrıca, bunlar doğrudan olay geri çağırmaya geçirildiğinden, istemcilerin olayları oluşturan öğeleri alması de kolaylaşır. İstemci olaya abone olduğunda bir önbellek isteği etkinse, öğesinin özellikleri otomatik olarak önceden getirilir.  
  
 Aşağıdaki tabloda Etkin Erişilebilirlik WinEvents ve [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olaylarının yazışmaları gösterilmektedir.  
  
|WinEvent|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olay tanımlayıcısı|  
|--------------|--------------------------------------------------------------------------------------------|  
|EVENT_OBJECT_ACCELERATORCHANGE|<xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty> özelliği değişikliği|  
|EVENT_OBJECT_CONTENTSCROLLED|ilişkili kaydırma çubuklarında <xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty> veya <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> özelliği değişikliği|  
|EVENT_OBJECT_CREATE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_DEFACTIONCHANGE|Eşdeğer değil|  
|EVENT_OBJECT_DESCRIPTIONCHANGE|Tam eşdeğer değildir; Belki <xref:System.Windows.Automation.AutomationElement.HelpTextProperty> veya <xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty> özelliği değişikliği|  
|EVENT_OBJECT_DESTROY|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_FOCUS|<xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent>|  
|EVENT_OBJECT_HELPCHANGE|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty> değişikliği|  
|EVENT_OBJECT_HIDE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_LOCATIONCHANGE|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty> özelliği değişikliği|  
|EVENT_OBJECT_NAMECHANGE|<xref:System.Windows.Automation.AutomationElement.NameProperty> özelliği değişikliği|  
|EVENT_OBJECT_PARENTCHANGE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_REORDER|Etkin Erişilebilirlik 'de tutarlı olarak kullanılmadı. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]içinde doğrudan karşılık gelen olay tanımlı değildir.|  
|EVENT_OBJECT_SELECTION|<xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent>|  
|EVENT_OBJECT_SELECTIONADD|<xref:System.Windows.Automation.SelectionItemPattern.ElementAddedToSelectionEvent>|  
|EVENT_OBJECT_SELECTIONREMOVE|<xref:System.Windows.Automation.SelectionItemPattern.ElementRemovedFromSelectionEvent>|  
|EVENT_OBJECT_SELECTIONWITHIN|Eşdeğer değil|  
|EVENT_OBJECT_SHOW|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_STATECHANGE|Özellik tarafından değiştirilen çeşitli olaylar|  
|EVENT_OBJECT_VALUECHANGE|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty?displayProperty=nameWithType> ve <xref:System.Windows.Automation.ValuePattern.ValueProperty?displayProperty=nameWithType> değişti|  
|EVENT_SYSTEM_ALERT|Eşdeğer değil|  
|EVENT_SYSTEM_CAPTUREEND|Eşdeğer değil|  
|EVENT_SYSTEM_CAPTURESTART|Eşdeğer değil|  
|EVENT_SYSTEM_CONTEXTHELPEND|Eşdeğer değil|  
|EVENT_SYSTEM_CONTEXTHELPSTART|Eşdeğer değil|  
|EVENT_SYSTEM_DIALOGEND|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|  
|EVENT_SYSTEM_DIALOGSTART|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|  
|EVENT_SYSTEM_DRAGDROPEND|Eşdeğer değil|  
|EVENT_SYSTEM_DRAGDROPSTART|Eşdeğer değil|  
|EVENT_SYSTEM_FOREGROUND|<xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent>|  
|EVENT_SYSTEM_MENUEND|<xref:System.Windows.Automation.AutomationElement.MenuClosedEvent>|  
|EVENT_SYSTEM_MENUPOPUPEND|<xref:System.Windows.Automation.AutomationElement.MenuClosedEvent>|  
|EVENT_SYSTEM_MENUPOPUPSTART|<xref:System.Windows.Automation.AutomationElement.MenuOpenedEvent>|  
|EVENT_SYSTEM_MENUSTART|<xref:System.Windows.Automation.AutomationElement.MenuOpenedEvent>|  
|EVENT_SYSTEM_MINIMIZEEND|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty> özelliği değişikliği|  
|EVENT_SYSTEM_MINIMIZESTART|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty> özelliği değişikliği|  
|EVENT_SYSTEM_MOVESIZEEND|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty> özelliği değişikliği|  
|EVENT_SYSTEM_MOVESIZESTART|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty> özelliği değişikliği|  
|EVENT_SYSTEM_SCROLLINGEND|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty> veya <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> özelliği değişikliği|  
|EVENT_SYSTEM_SCROLLINGSTART|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty> veya <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> özelliği değişikliği|  
|EVENT_SYSTEM_SOUND|Eşdeğer değil|  
|EVENT_SYSTEM_SWITCHEND|Denk değildir, ancak <xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent> bir olay yeni bir uygulamanın odağı aldığını bildirir|  
|EVENT_SYSTEM_SWITCHSTART|Eşdeğer değil|  
|Eşdeğer değil|<xref:System.Windows.Automation.MultipleViewPattern.CurrentViewProperty> özelliği değişikliği|  
|Eşdeğer değil|<xref:System.Windows.Automation.ScrollPattern.HorizontallyScrollableProperty> özelliği değişikliği|  
|Eşdeğer değil|<xref:System.Windows.Automation.ScrollPattern.VerticallyScrollableProperty> özelliği değişikliği|  
|Eşdeğer değil|<xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> özelliği değişikliği|  
|Eşdeğer değil|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty> özelliği değişikliği|  
|Eşdeğer değil|<xref:System.Windows.Automation.ScrollPattern.HorizontalViewSizeProperty> özelliği değişikliği|  
|Eşdeğer değil|<xref:System.Windows.Automation.ScrollPattern.VerticalViewSizeProperty> özelliği değişikliği|  
|Eşdeğer değil|<xref:System.Windows.Automation.TogglePattern.ToggleStateProperty> özelliği değişikliği|  
|Eşdeğer değil|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty> özelliği değişikliği|  
|Eşdeğer değil|<xref:System.Windows.Automation.AutomationElement.AsyncContentLoadedEvent> olayı|  
|Eşdeğer değil|<xref:System.Windows.Automation.AutomationElement.ToolTipOpenedEvent>|  
  
<a name="Security_compare"></a>   
## <a name="security"></a>Güvenlik  
 Bazı `IAccessible` özelleştirme senaryoları, temel `IAccessible` sarmalama ve ona çağırma gerektirir. Kısmen güvenilen bir bileşen bir kod yolunda ara bir aracı olmaması gerektiğinden, bu güvenlik etkilerine sahiptir.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] modeli, diğer sağlayıcı koduna çağrı yapmak için sağlayıcıların gereksinimini ortadan kaldırır. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] çekirdek hizmeti tüm gerekli toplamayı yapar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Temelleri](index.md)
