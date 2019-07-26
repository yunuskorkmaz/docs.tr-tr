---
title: UI Otomasyonu ve Microsoft Active Accessibility
ms.date: 03/30/2017
helpviewer_keywords:
- Active Accessibility
- UI Automation, Active Accessibility compared to
- UI Automation, Microsoft Active Accessibility
- Active Accessibility, UI Automation compared to
ms.assetid: 87bee662-0a3e-4232-a421-20e7a5968321
ms.openlocfilehash: ef00c80cd51551fe12283835b3c3d51317c2aa6d
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68434029"
---
# <a name="ui-automation-and-microsoft-active-accessibility"></a>UI Otomasyonu ve Microsoft Active Accessibility
> [!NOTE]
>  Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir. Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Microsoft Etkin Erişilebilirlik, uygulamaları erişilebilir hale getirmek için daha önceki bir çözümdür. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)], için [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)] yeni erişilebilirlik modelidir ve yardımcı teknoloji ürünlerinin ve otomatikleştirilmiş test araçlarının ihtiyaçlarını karşılamak üzere tasarlanmıştır. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Etkin Erişilebilirlik üzerinde birçok geliştirme sunar.  
  
 Bu konu, öğesinin [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ana özelliklerini içerir ve bu özelliklerin etkin erişilebilirlik 'ten nasıl farklı olduğunu açıklar.  
  
<a name="Programming_Languages_compare"></a>   
## <a name="programming-languages"></a>Programlama Dilleri  
Etkin Erişilebilirlik <, çift arabirimler için destek içeren bileşen nesne modeli (com) tabanlıdır ve bu nedenle C/C++, [!INCLUDE[TLA#tla_vb6](../../../includes/tlasharptla-vb6-md.md)]ve komut dosyası dillerinde programlanabilir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)](Standart denetimler için istemci tarafı sağlayıcı kitaplığı dahil) yönetilen kodda yazılır ve UI Otomasyonu istemci uygulamaları, veya Visual Basic .NET kullanılarak C# kolayca programlanabilir. Arabirim uygulamaları olan UI Otomasyon sağlayıcıları yönetilen kodda veya C/C++dilinde yazılabilir.  
  
<a name="Support_in_Windows_Presentation_Foundation_"></a>   
## <a name="support-in-windows-presentation-foundation"></a>Windows Presentation Foundation desteği  
 Windows Presentation Foundation (WPF), Kullanıcı arabirimleri oluşturmak için yeni bir modeldir. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]öğeler, etkin erişilebilirlik için yerel destek içermez; Ancak, Etkin Erişilebilirlik istemcileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]için köprü oluşturma desteğini içeren destek içerirler. Yalnızca için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özel olarak yazılan istemciler, metin için zengin destek gibi, uygulamasının [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]erişilebilirlik özelliklerinden tamamen faydalanabilir.  
  
<a name="Servers_and_Clients_compare"></a>   
## <a name="servers-and-clients"></a>Sunucular ve Istemciler  
 Etkin Erişilebilirlik 'de, sunucular ve istemciler büyük ölçüde sunucunun uygulamasını `IAccessible`kullanarak doğrudan iletişim kurar.  
  
 ' [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]De, bir çekirdek hizmet sunucu (sağlayıcı adı verilir) ve istemci arasında yer alır. Çekirdek hizmet, sağlayıcılar tarafından uygulanan arabirimlere çağrı yapar ve öğeler için benzersiz çalışma zamanı tanımlayıcıları oluşturma gibi ek hizmetler sağlar. İstemci uygulamaları [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] hizmeti çağırmak için kitaplık işlevlerini kullanır.  
  
 UI Otomasyon sağlayıcıları Etkin Erişilebilirlik istemcilerine bilgi sağlayabilir ve Etkin Erişilebilirlik sunucuları UI Otomasyonu istemci uygulamalarına bilgi sağlayabilir. Ancak, Etkin Erişilebilirlik çok fazla bilgi [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]sunmadığından, iki model tamamen uyumlu değildir.  
  
<a name="UI_Elements_compare"></a>   
## <a name="ui-elements"></a>UI öğeleri  
 Etkin Erişilebilirlik, [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğeleri bir `IAccessible` arabirim veya alt tanımlayıcı olarak sunar. Aynı öğeye başvurup başvurmadığını `IAccessible` belirlemek için iki işaretçiyi karşılaştırmak zordur.  
  
 ' [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]De, her öğe bir <xref:System.Windows.Automation.AutomationElement> nesne olarak temsil edilir. Karşılaştırma, her ikisi de öğelerin benzersiz çalışma zamanı tanımlayıcılarını <xref:System.Windows.Automation.AutomationElement.Equals%2A> karşılaştıran eşitlik işleci veya yöntemi kullanılarak yapılır.  
  
<a name="Tree_Views_and_Navigation_compare"></a>   
## <a name="tree-views-and-navigation"></a>Ağaç görünümleri ve gezintisi  
 Ekrandaki [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] öğeler, kök olarak masaüstüne sahip bir ağaç yapısı, hemen alt öğe olarak uygulama penceresi ve uygulamalar içindeki öğeleri daha ileri alt öğeler olarak görülebilir.  
  
 Etkin Erişilebilirlik 'de, son kullanıcılar için ilgisiz çok sayıda Otomasyon öğesi ağaçta kullanıma sunulur. İstemci uygulamalarının anlamlı olduğunu belirleyebilmek için tüm öğelere bakmamız gerekir.  
  
 UI Otomasyonu istemci uygulamaları filtrelenmiş bir [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] görünüm üzerinden bkz. Görünüm yalnızca ilgilendiğiniz öğeleri içerir: kullanıcıya bilgi veren veya etkileşimi etkinleştiren kişiler. Yalnızca denetim öğelerinin ve yalnızca içerik öğelerinin önceden tanımlanmış görünümleri mevcuttur; Ayrıca, uygulamalar özel görünümleri tanımlayabilir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] kullanıcısını kullanıcıya açıklama ve kullanıcı uygulamayla etkileşime geçme görevini basitleştirir.  
  
 Etkin Erişilebilirlik 'de öğeler arasında gezinme, uzamsal (örneğin, ekranda sol tarafta yer alan öğeye geçme), mantıksal (örneğin, bir sonraki menü öğesine geçme veya bir iletişim kutusu içindeki sekme düzeninde bulunan bir sonraki öğe) ya da sıradüzenli ( Örneğin, bir kapsayıcıdaki ilk çocuğu veya alt öğeden üst öğesine taşıma). Hiyerarşik gezinti, alt öğelerin her zaman uygulayan `IAccessible`nesneler olmadığı konusunda karmaşıktır.  
  
 ' [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]De, [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] tüm öğeler <xref:System.Windows.Automation.AutomationElement> aynı temel işlevselliği destekleyen nesnelerdir. (Sağlayıcının açısından, öğesinden <xref:System.Windows.Automation.Provider.IRawElementProviderSimple>devralınan bir arabirimi uygulayan nesnelerdir.) Gezinti temel olarak hiyerarşik olarak, üst ve alt öğeler arasında ve bir eşdüzey bir sonrakine. (Eşdüzey öğeler arasında gezinme bir mantıksal öğe olur, çünkü sekme sırasını takip edebilir.) <xref:System.Windows.Automation.TreeWalker> Sınıfını kullanarak, ağacın filtrelenmiş görünümünü kullanarak herhangi bir başlangıç noktasından gidebilirsiniz. Ayrıca, ve <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> <xref:System.Windows.Automation.AutomationElement.FindAll%2A>kullanarak belirli alt öğelere da gidebilirsiniz; Örneğin, belirli bir denetim modelini destekleyen bir iletişim kutusu içindeki tüm öğeleri almak çok kolaydır.  
  
 ' De [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gezinti, etkin erişilebilirlikle daha tutarlıdır. Açılır listeler ve açılır pencereler gibi bazı öğeler, Etkin Erişilebilirlik ağacında iki kez görünür ve onlardan gezinmede beklenmedik sonuçlara neden olabilir. Bir Rebar denetimi için etkin erişilebilirliği düzgün bir şekilde uygulamak olanaksızdır. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bir öğenin, Windows 'un sahipliğini tarafından konulan hiyerarşiye rağmen ağacın herhangi bir yere yerleştirilebileceği şekilde, yeniden konumlandırma ve yeniden konumlandırma imkanı sunar.  
  
<a name="Roles_and_Control_Types"></a>   
## <a name="roles-and-control-types"></a>Roller ve denetim türleri  
 Etkin Erişilebilirlik, ROLE_SYSTEM_SLIDER `accRole` veya ROLE_SYSTEM_MENUITEM`IAccessible::get_actRole`gibi [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]öğe rolünün bir açıklamasını almak için özelliğini () kullanır. Bir öğenin rolü, kullanılabilir işlevselliğine ana Clue ' dir. Bir denetimle etkileşim, `IAccessible::accSelect` ve `IAccessible::accDoDefaultAction`gibi sabit yöntemler kullanılarak elde edilir. İstemci uygulaması ve [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] ile arasındaki etkileşim, tarafından `IAccessible`yapılabilecekleri ile sınırlıdır.  
  
 Buna karşılık, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] büyük ölçüde öğenin denetim türünü ( <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> özelliği tarafından açıklananlar) beklenen işlevden ayırır. İşlevselliği, sağlayıcı tarafından özelleştirilmiş arabirimlerin uygulanmasıyla desteklenen denetim desenleri tarafından belirlenir. Denetim desenleri, belirli [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] bir öğe tarafından desteklenen işlevlerin tam kümesini betimleyerek birleştirilebilir. Belirli bir denetim modelini desteklemek için bazı sağlayıcılar gereklidir; Örneğin, bir onay kutusu için sağlayıcı Iki durumlu denetim deseninin desteklenmesi gerekir. Diğer sağlayıcılar bir veya daha fazla denetim deseni kümesini desteklemek için gereklidir; Örneğin, bir düğme Iki durumlu veya Invoke desteklemelidir. Hala diğerleri hiç denetim deseni desteklemez; Örneğin, taşınamayan, yeniden boyutlandırılan veya sabitlenemez bir bölme herhangi bir denetim desenine sahip değildir.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], <xref:System.Windows.Automation.ControlType.Custom> özelliği tarafından tanımlanan ve <xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty> özelliği tarafından açıklanabilecek özel denetimleri destekler.  
  
 Aşağıdaki tabloda, denetim türlerini denetlemek için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Etkin Erişilebilirlik rollerinin eşlemesi gösterilmektedir.  
  
|Etkin Erişilebilirlik rolü|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Denetim türü|  
|----------------------------------------------------------------------|----------------------------------------------------------------------------------------|  
|ROLE_SYSTEM_PUSHBUTTON|Düğme|  
|ROLE_SYSTEM_CLIENT|Takvim|  
|ROLE_SYSTEM_CHECKBUTTON|Onay kutusu|  
|ROLE_SYSTEM_COMBOBOX|Birleşik giriş kutusu|  
|ROLE_SYSTEM_CLIENT|Özel|  
|ROLE_SYSTEM_LIST|Veri kılavuzu|  
|ROLE_SYSTEM_LISTITEM|Veri öğesi|  
|ROLE_SYSTEM_DOCUMENT|Belge|  
|ROLE_SYSTEM_TEXT|Düzenle|  
|ROLE_SYSTEM_GROUPING|Grup|  
|ROLE_SYSTEM_LIST|Üstbilgi|  
|ROLE_SYSTEM_COLUMNHEADER|Üstbilgi öğesi|  
|ROLE_SYSTEM_LINK|Köprü|  
|ROLE_SYSTEM_GRAPHIC|Image|  
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
|ROLE_SYSTEM_STATICTEXT|Text|  
|ROLE_SYSTEM_INDICATOR|Parmak|  
|ROLE_SYSTEM_TITLEBAR|Başlık çubuğu|  
|ROLE_SYSTEM_TOOLBAR|Araç çubuğu|  
|ROLE_SYSTEM_TOOLTIP|ToolTip|  
|ROLE_SYSTEM_OUTLINE|Ağaç|  
|ROLE_SYSTEM_OUTLINEITEM|Ağaç öğesi|  
|ROLE_SYSTEM_WINDOW|Pencere|  
  
 Farklı denetim türleri hakkında daha fazla bilgi için bkz. [UI Automation Denetim türleri](../../../docs/framework/ui-automation/ui-automation-control-types.md).  
  
<a name="States_and_Properties"></a>   
## <a name="states-and-properties"></a>Durumlar ve Özellikler  
 Etkin Erişilebilirlik 'de, öğeler ortak bir özellikler kümesini destekler ve bazı özellikler ( `accState`gibi), öğenin rolüne bağlı olarak çok farklı şeyleri anlamalıdır. Sunucular, öğe ile ilgili olmayan `IAccessible` bir özelliği döndüren tüm yöntemleri uygulamalıdır.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Bazıları Etkin Erişilebilirlik 'deki durumlara karşılık gelen birçok daha fazla özelliği tanımlar. Bazıları tüm öğeler için ortaktır, ancak diğerleri denetim türlerine ve denetim düzenlerine özeldir. Özellikler benzersiz tanımlayıcılarla ayırt edilir ve çoğu özellik tek bir yöntem veya ya <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>da kullanılarak alınabilir. Birçok özellik ayrıca <xref:System.Windows.Automation.AutomationElement.Current%2A> ve <xref:System.Windows.Automation.AutomationElement.Cached%2A> Özellik erişimcilerine de kolayca alınabilir.  
  
 Bir UI Otomasyon sağlayıcısının ilgisiz Özellikler uygulaması gerekmez, ancak desteklemediği özellikler için yalnızca bir `null` değer döndürebilir. Ayrıca, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] çekirdek hizmet varsayılan pencere sağlayıcısından bazı özellikler alabilir ve bunlar, sağlayıcı tarafından açıkça uygulanan özelliklerle kaynaştırılabilir.  
  
 Daha fazla özelliği desteklemenin yanı sıra, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] birden fazla özelliği tek bir çapraz işlem çağrısıyla alınmasına izin vererek daha iyi performans sağlar.  
  
 Aşağıdaki tabloda, iki modelde özellikler arasındaki yazışma gösterilmektedir.  
  
|Etkin erişilebilirlik özelliği erişimcisi|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]özellik KIMLIĞI|Açıklamalar|  
|-----------------------------------------------------------------------------------|---------------------------------------------------------------------------------------|-------------|  
|`get_accKeyboardShortcut`|<xref:System.Windows.Automation.AutomationElement.AccessKeyProperty> veya <xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>|`AccessKeyProperty`her ikisi de varsa öncelik alır.|  
|`get_accName`|<xref:System.Windows.Automation.AutomationElement.NameProperty>||  
|`get_accRole`|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>|Denetim türlerini denetlemek için önceki tabloya bakın.|  
|`get_accValue`|<xref:System.Windows.Automation.ValuePattern.ValueProperty?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.RangeValuePattern.ValueProperty?displayProperty=nameWithType>|Yalnızca Valuemodel veya Rangevaluemodel destekleyen denetim türleri için geçerlidir. RangeValue değerleri, MSAA davranışıyla tutarlı olacak şekilde 0-100 olarak normalleştirilmelidir. Değer öğeleri bir dize kullanır.|  
|`get_accHelp`|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>||  
|`accLocation`|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>||  
|`get_accDescription`|İçinde desteklenmez[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|`accDescription`, bu özellikte farklı bilgi parçaları yerleştirmekte olan MSAA içinde açık bir belirtim yoktu.|  
|`get_accHelpTopic`|İçinde desteklenmez[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]||  
  
 Aşağıdaki tabloda, Etkin Erişilebilirlik [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] durumu sabitlerine karşılık gelen özellikler gösterilmektedir.  
  
|Etkin Erişilebilirlik durumu|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]özelliði|Tetikleyiciler durum değişikliği mi?|  
|-----------------------------------------------------------------------|------------------------------------------------------------------------------------|----------------------------|  
|STATE_SYSTEM_CHECKED|Onay kutusu için,<xref:System.Windows.Automation.TogglePattern.ToggleStateProperty><br /><br /> Radyo düğmesi için,<xref:System.Windows.Automation.SelectionItemPattern.IsSelectedProperty>|E|  
|STATE_SYSTEM_COLLAPSED|<xref:System.Windows.Automation.ExpandCollapsePattern.ExpandCollapsePatternInformation.ExpandCollapseState%2A> = <xref:System.Windows.Automation.ExpandCollapseState.Collapsed>|E|  
|STATE_SYSTEM_EXPANDED|<xref:System.Windows.Automation.ExpandCollapsePattern.ExpandCollapsePatternInformation.ExpandCollapseState%2A> = <xref:System.Windows.Automation.ExpandCollapseState.Expanded>veya<xref:System.Windows.Automation.ExpandCollapseState.PartiallyExpanded>|E|  
|STATE_SYSTEM_FOCUSABLE|<xref:System.Windows.Automation.AutomationElement.IsKeyboardFocusableProperty>|N|  
|STATE_SYSTEM_FOCUSED|<xref:System.Windows.Automation.AutomationElement.HasKeyboardFocusProperty>|N|  
|STATE_SYSTEM_HASPOPUP|<xref:System.Windows.Automation.ExpandCollapsePattern>menü öğeleri için|N|  
|STATE_SYSTEM_INVISIBLE|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty>= True ve <xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A> nedenler<xref:System.Windows.Automation.NoClickablePointException>|N|  
|STATE_SYSTEM_LINKED|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> =<br /><br /> <xref:System.Windows.Automation.ControlType.Hyperlink>|N|  
|STATE_SYSTEM_MIXED|<xref:System.Windows.Automation.TogglePattern.TogglePatternInformation.ToggleState%2A> = <xref:System.Windows.Automation.ToggleState.Indeterminate>|N|  
|STATE_SYSTEM_MOVEABLE|<xref:System.Windows.Automation.TransformPattern.CanMoveProperty>|N|  
|STATE_SYSTEM_MUTLISELECTABLE|<xref:System.Windows.Automation.SelectionPattern.CanSelectMultipleProperty>|N|  
|STATE_SYSTEM_OFFSCREEN|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty>= True|N|  
|STATE_SYSTEM_PROTECTED|<xref:System.Windows.Automation.AutomationElement.IsPasswordProperty>|N|  
|STATE_SYSTEM_READONLY|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty?displayProperty=nameWithType> ve <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty?displayProperty=nameWithType>|N|  
|STATE_SYSTEM_SELECTABLE|<xref:System.Windows.Automation.SelectionItemPattern>desteklenir|N|  
|STATE_SYSTEM_SELECTED|<xref:System.Windows.Automation.SelectionItemPattern.IsSelectedProperty>|N|  
|STATE_SYSTEM_SIZEABLE|<xref:System.Windows.Automation.TransformPattern.TransformPatternInformation.CanResize%2A>|N|  
|STATE_SYSTEM_UNAVAILABLE|<xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>|E|  
  
 Aşağıdaki durumlar, çoğu Etkin Erişilebilirlik denetimi sunucusu tarafından uygulanmadı ya da hiçbir eşdeğeri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]yoktur.  
  
|Etkin Erişilebilirlik durumu|Açıklamalar|  
|-----------------------------------------------------------------------|-------------|  
|STATE_SYSTEM_BUSY|İçinde kullanılamaz[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_DEFAULT|İçinde kullanılamaz[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_ANIMATED|İçinde kullanılamaz[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_EXTSELECTABLE|Etkin Erişilebilirlik sunucuları tarafından yaygın olarak uygulanmadı|  
|STATE_SYSTEM_MARQUEED|Etkin Erişilebilirlik sunucuları tarafından yaygın olarak uygulanmadı|  
|STATE_SYSTEM_SELFVOICING|Etkin Erişilebilirlik sunucuları tarafından yaygın olarak uygulanmadı|  
|STATE_SYSTEM_TRAVERSED|İçinde kullanılamaz[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_ALERT_HIGH|Etkin Erişilebilirlik sunucuları tarafından yaygın olarak uygulanmadı|  
|STATE_SYSTEM_ALERT_MEDIUM|Etkin Erişilebilirlik sunucuları tarafından yaygın olarak uygulanmadı|  
|STATE_SYSTEM_ALERT_LOW|Etkin Erişilebilirlik sunucuları tarafından yaygın olarak uygulanmadı|  
|STATE_SYSTEM_FLOATING|Etkin Erişilebilirlik sunucuları tarafından yaygın olarak uygulanmadı|  
|STATE_SYSTEM_HOTTRACKED|İçinde kullanılamaz[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_PRESSED|İçinde kullanılamaz[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Özellik tanımlayıcılarının tüm listesi için bkz. [UI Otomasyon özelliklerine genel bakış](../../../docs/framework/ui-automation/ui-automation-properties-overview.md).  
  
<a name="uiautomation_events_compare"></a>   
## <a name="events"></a>Events  
 İçindeki [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]olay mekanizması, Etkin Erişilebilirlik 'in aksine, Windows olay yönlendirme 'yi (pencere tutamaçlarıyla yakından ilişkilidir) kullanmaz ve istemci uygulamasının kancaları ayarlaması gerekmez. Olaylara yönelik abonelikler, yalnızca belirli olaylara değil ağacın belirli bölümlerine göre hassas bir şekilde ayarlanabilir. Sağlayıcılar, hangi olayların dinleneceği ile ilgili olayları izleyerek olayların kendi etkinliklerini de ayrıntılı olarak ayarlayabilir.  
  
 Ayrıca, bunlar doğrudan olay geri çağırmaya geçirildiğinden, istemcilerin olayları oluşturan öğeleri alması de kolaylaşır. İstemci olaya abone olduğunda bir önbellek isteği etkinse, öğesinin özellikleri otomatik olarak önceden getirilir.  
  
 Aşağıdaki tabloda Etkin Erişilebilirlik winEvents ve [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olaylarının yazışmaları gösterilmektedir.  
  
|WinEvent|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]olay tanımlayıcısı|  
|--------------|--------------------------------------------------------------------------------------------|  
|EVENT_OBJECT_ACCELERATORCHANGE|<xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>Özellik değişikliği|  
|EVENT_OBJECT_CONTENTSCROLLED|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty>ya <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> da ilişkili kaydırma çubuklarındaki özellik değişikliği|  
|EVENT_OBJECT_CREATE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_DEFACTIONCHANGE|Eşdeğer değil|  
|EVENT_OBJECT_DESCRIPTIONCHANGE|Tam eşdeğer değildir; Belki <xref:System.Windows.Automation.AutomationElement.HelpTextProperty> veya<xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty> özellik değişikliği|  
|EVENT_OBJECT_DESTROY|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_FOCUS|<xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent>|  
|EVENT_OBJECT_HELPCHANGE|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>değişebilir|  
|EVENT_OBJECT_HIDE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_LOCATIONCHANGE|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>Özellik değişikliği|  
|EVENT_OBJECT_NAMECHANGE|<xref:System.Windows.Automation.AutomationElement.NameProperty>Özellik değişikliği|  
|EVENT_OBJECT_PARENTCHANGE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_REORDER|Etkin Erişilebilirlik 'de tutarlı olarak kullanılmadı. İçinde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]doğrudan karşılık gelen olay tanımlı değildir.|  
|EVENT_OBJECT_SELECTION|<xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent>|  
|EVENT_OBJECT_SELECTIONADD|<xref:System.Windows.Automation.SelectionItemPattern.ElementAddedToSelectionEvent>|  
|EVENT_OBJECT_SELECTIONREMOVE|<xref:System.Windows.Automation.SelectionItemPattern.ElementRemovedFromSelectionEvent>|  
|EVENT_OBJECT_SELECTIONWITHIN|Eşdeğer değil|  
|EVENT_OBJECT_SHOW|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_STATECHANGE|Özellik tarafından değiştirilen çeşitli olaylar|  
|EVENT_OBJECT_VALUECHANGE|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty?displayProperty=nameWithType>ve <xref:System.Windows.Automation.ValuePattern.ValueProperty?displayProperty=nameWithType> değiştirildi|  
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
|EVENT_SYSTEM_MINIMIZEEND|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty>Özellik değişikliği|  
|EVENT_SYSTEM_MINIMIZESTART|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty>Özellik değişikliği|  
|EVENT_SYSTEM_MOVESIZEEND|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>Özellik değişikliği|  
|EVENT_SYSTEM_MOVESIZESTART|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>Özellik değişikliği|  
|EVENT_SYSTEM_SCROLLINGEND|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty>veya <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> özellik değişikliği|  
|EVENT_SYSTEM_SCROLLINGSTART|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty>veya <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> özellik değişikliği|  
|EVENT_SYSTEM_SOUND|Eşdeğer değil|  
|EVENT_SYSTEM_SWITCHEND|Eşdeğer değildir, ancak yeni <xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent> bir uygulamanın odağı aldığını belirten bir olay sinyalidir|  
|EVENT_SYSTEM_SWITCHSTART|Eşdeğer değil|  
|Eşdeğer değil|<xref:System.Windows.Automation.MultipleViewPattern.CurrentViewProperty>Özellik değişikliği|  
|Eşdeğer değil|<xref:System.Windows.Automation.ScrollPattern.HorizontallyScrollableProperty>Özellik değişikliği|  
|Eşdeğer değil|<xref:System.Windows.Automation.ScrollPattern.VerticallyScrollableProperty>Özellik değişikliği|  
|Eşdeğer değil|<xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty>Özellik değişikliği|  
|Eşdeğer değil|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty>Özellik değişikliği|  
|Eşdeğer değil|<xref:System.Windows.Automation.ScrollPattern.HorizontalViewSizeProperty>Özellik değişikliği|  
|Eşdeğer değil|<xref:System.Windows.Automation.ScrollPattern.VerticalViewSizeProperty>Özellik değişikliği|  
|Eşdeğer değil|<xref:System.Windows.Automation.TogglePattern.ToggleStateProperty>Özellik değişikliği|  
|Eşdeğer değil|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty>Özellik değişikliği|  
|Eşdeğer değil|<xref:System.Windows.Automation.AutomationElement.AsyncContentLoadedEvent>olay|  
|Eşdeğer değil|<xref:System.Windows.Automation.AutomationElement.ToolTipOpenedEvent>|  
  
<a name="Security_compare"></a>   
## <a name="security"></a>Güvenlik  
 Bazı `IAccessible` özelleştirme senaryolarında temel `IAccessible` sarmalama ve ile çağrı yapılması gerekir. Kısmen güvenilen bir bileşen bir kod yolunda ara bir aracı olmaması gerektiğinden, bu güvenlik etkilerine sahiptir.  
  
 Model [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , diğer sağlayıcı koduna çağrı yapmak için sağlayıcıların gereksinimini ortadan kaldırır. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Çekirdek hizmet tüm gerekli toplamayı yapar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Temelleri](../../../docs/framework/ui-automation/index.md)
