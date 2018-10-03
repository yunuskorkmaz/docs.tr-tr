---
title: UI Otomasyonu ve Microsoft Active Accessibility
ms.date: 03/30/2017
helpviewer_keywords:
- Active Accessibility
- UI Automation, Active Accessibility compared to
- UI Automation, Microsoft Active Accessibility
- Active Accessibility, UI Automation compared to
ms.assetid: 87bee662-0a3e-4232-a421-20e7a5968321
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 1b7dbc8dffb15485ec035049d2da7aac6915eb58
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48036220"
---
# <a name="ui-automation-and-microsoft-active-accessibility"></a>UI Otomasyonu ve Microsoft Active Accessibility
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)] erişilebilir uygulamalar oluşturmaya yönelik önceki çözümü oldu. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] için yeni erişilebilirlik modelidir [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)] otomatik test araçları ve yardımcı teknoloji ürünlerinin ihtiyaçlarınızı karşılamak üzere tasarlanmıştır. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] üzerinden birçok geliştirme sunar [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)].  
  
 Bu konu, ana özelliklerini içerir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ve bu özelliklerin nasıl farklılık açıklanmaktadır [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)].  
  
<a name="Programming_Languages_compare"></a>   
## <a name="programming-languages"></a>Programlama dilleri  
<[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] dayanır [!INCLUDE[TLA#tla_com](../../../includes/tlasharptla-com-md.md)] çift arabirim desteği ile ve bu nedenle C/C++, programlanabilir [!INCLUDE[TLA#tla_vb6](../../../includes/tlasharptla-vb6-md.md)]ve komut dosyası dili. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] (Standart denetimler için istemci tarafı sağlayıcı kitaplığını dahil), yönetilen kodda yazılır ve C# veya Visual Basic .NET kullanarak UI otomasyon istemci uygulamaları en kolay programlanmıştır. Arabirim uygulamalarıdır, UI Otomasyonu sağlayıcıları, yönetilen kodda veya C/C++ yazılabilir.  
  
<a name="Support_in_Windows_Presentation_Foundation_"></a>   
## <a name="support-in-windows-presentation-foundation"></a>Windows Presentation Foundation'da desteği  
 Windows Presentation Foundation (WPF), kullanıcı arabirimleri oluşturmak için yeni bir modeldir. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] öğeleri için yerel destek içermez [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]; ancak, destekledikleri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], köprü oluşturma desteği içeren [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] istemciler. Yalnızca özel olarak yazılmış istemciler [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] erişilebilirlik özelliklerinden yararlanabilirsiniz [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]gibi zengin metin için destek.  
  
<a name="Servers_and_Clients_compare"></a>   
## <a name="servers-and-clients"></a>Sunucular ve istemciler  
 İçinde [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)], sunucular ve istemciler iletişim doğrudan büyük ölçüde sunucu uygulaması `IAccessible`.  
  
 İçinde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], core hizmeti (bir sağlayıcı olarak adlandırılır) sunucu ve istemci arasında arasındadır. Çekirdek hizmet sağlayıcıları tarafından uygulanan arabirimler çağrılar ve benzersiz bir çalışma zamanı tanımlayıcılarının öğeleri için oluşturma gibi ek hizmetler sağlar. İstemci uygulamaları kullanın kitaplık işlevleri çağırmak için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] hizmeti.  
  
 UI Otomasyonu sağlayıcıları için bilgi sağlayabilir [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] istemcileri ve [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] sunucuları UI otomasyon istemci uygulamaları için bilgi sağlar. Ancak, çünkü [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] kadar bilgi olarak kullanıma sunmuyor [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], iki modeli tam olarak uyumlu değildir.  
  
<a name="UI_Elements_compare"></a>   
## <a name="ui-elements"></a>Kullanıcı Arabirimi öğeleri  
 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] sunan [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğeleri ya da farklı bir `IAccessible` arabirimi veya bir alt tanımlayıcı olarak. İki karşılaştırmak zordur `IAccessible` aynı öğeye başvuruyorsa, belirlemek için işaretçi.  
  
 İçinde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], her bir öğe olarak temsil edilen bir <xref:System.Windows.Automation.AutomationElement> nesne. Karşılaştırma eşitlik işleci kullanılarak yapılır veya <xref:System.Windows.Automation.AutomationElement.Equals%2A> yöntemi, öğelerin benzersiz bir çalışma zamanı tanımlayıcılarının ikisi de karşılaştırın.  
  
<a name="Tree_Views_and_Navigation_compare"></a>   
## <a name="tree-views-and-navigation"></a>Ağaç görünümleri ve gezinti  
 [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] Öğeler ekranda görülebilir bir ağaç yapısı masaüstü ile windows uygulaması, kök yakınındaki alt öğeleri ve uygulamalar içindeki öğeleri olarak daha fazla alt öğesi.  
  
 İçinde [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)], son kullanıcılara ilgisi olmayan birçok Otomasyon öğe ağacında sunulur. Anlamlı olduğu belirlemek için tüm öğeler aramak istemci uygulamaları vardır.  
  
 UI Otomasyonu istemci uygulamaları [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] filtrelenmiş bir görünüm aracılığıyla. Görünümü yalnızca ilgilendiğiniz öğeleri içerir: etkileşimi etkinleştirmek veya kullanıcıya bilgi verilir. Yalnızca denetim öğeleri ve içerik öğeleri yalnızca önceden tanımlanmış görünümleri bulunur; Ayrıca, uygulamaları özel görünümler tanımlayabilirsiniz. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] açıklayan görevini kolaylaştıran [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] kullanıcı ve uygulama ile etkileşin kullanıcı yardımcı olur.  
  
 Öğeleri arasında gezinme içinde [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)], ya da uzamsal (örneğin, ekranda solunda kalan öğeye taşıma), mantıksal (örneğin, bir sonraki menü öğesini ya da bir iletişim kutusu içindeki sekme sırası'na taşıma) veya hiyerarşik (için ilk alt kapsayıcıda ya da alt kendi üst öğeye taşıma tarih gibi). Hiyerarşik gezinme alt öğeleri her zaman uygulayan nesneler olmadığını olgusu karmaşık `IAccessible`.  
  
 İçinde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]tüm [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğeler <xref:System.Windows.Automation.AutomationElement> aynı temel işlevlerini destekleyen nesneleri. (Devralınan bir arabirimi uygulayan nesneler sağlayıcı bakış açısına ait oldukları <xref:System.Windows.Automation.Provider.IRawElementProviderSimple>.) Gezinti çoğunlukla hiyerarşik: üst öğenin alt öğelerine ve sonraki bir eşdüzey. (Sekme sırasını takip Eşdüzey öğeleri arasında gezinme mantıksal bir öğe yok.) Filtrelenen herhangi ağaç görünümünü kullanarak tüm başlatma-noktasından gidebilirsiniz <xref:System.Windows.Automation.TreeWalker> sınıfı. Kullanarak belirli alt öğeleri veya alt öğeleri de gidebilirsiniz <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> ve <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; Örneğin, bir iletişim kutusu içinde belirtilen denetim düzenini destekleyen tüm öğeleri almak çok kolaydır.  
  
 Gezinti bölmesinde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] içinde daha fazla tutarlı [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]. Bazı öğeleri açılan listeler ve açılır pencereleri gibi iki kez şekilde görünmesi [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] ağaç ve bunları gelen Gezinti beklenmeyen sonuçlar. Düzgün bir şekilde uygulamak gerçekten olanaksızdır [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] çubuk barınağı denetimi. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] üst öğeleri yeniden ayarlama ve böylece bir öğe herhangi bir windows sahipliğini tarafından uygulanan hiyerarşi rağmen ağacında yerleştirilebilir, yeniden konumlandırma sağlar.  
  
<a name="Roles_and_Control_Types"></a>   
## <a name="roles-and-control-types"></a>Rolleri ve Denetim türleri  
 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] kullanan `accRole` özelliği (`IAccessible::get_actRole`) öğenin rol açıklamasını alınacak [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]ROLE_SYSTEM_SLIDER veya ROLE_SYSTEM_MENUITEM gibi. Bir öğenin kullanılabilir işlevselliğini ana ipucu rolüdür. Bir denetimle etkileşim sabit yöntemleri gibi kullanılarak gerçekleştirilir `IAccessible::accSelect` ve `IAccessible::accDoDefaultAction`. İstemci uygulama arasındaki etkileşim ve [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] ne aracılığıyla yapılabilir için sınırlı `IAccessible`.  
  
 Buna karşılık, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] büyük ölçüde öğenin denetim türünü ayırır (tarafından açıklanan <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> özelliği) öğesinden beklenen işlevselliği. İşlevi, özel arabirimler uygulaması aracılığıyla sağlayıcı tarafından desteklenen denetim desenleri tarafından belirlenir. Belirli bir tarafından desteklenen işlevlerin tam kümesini tanımlamak için Denetim desenleri birleştirilebilir [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğesi. Bazı sağlayıcıların özel denetim düzenini desteklemek için gerekli olan; Örneğin, sağlayıcı için bir onay kutusu değiştirme denetim düzenini desteklemelidir. Diğer sağlayıcıları bir veya daha fazla denetim desenleri desteklemek için gerekli olan; Örneğin, bir düğme, geçiş veya Invoke desteklemesi gerekir. Yine de diğer hiçbir denetim düzenleri hiç desteği; Örneğin, herhangi bir denetim düzenleri, yeniden boyutlandırılmış, yerleşik veya taşınamaz bölme yok.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tarafından tanımlanan özel denetimleri destekler <xref:System.Windows.Automation.ControlType.Custom> özelliği ve tarafından açıklanan <xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty> özelliği.  
  
 Aşağıdaki tabloda eşleme gösterilmektedir [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] rollere [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] denetim türlerinin.  
  
|[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] Rol|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Denetim türü|  
|----------------------------------------------------------------------|----------------------------------------------------------------------------------------|  
|ROLE_SYSTEM_PUSHBUTTON|Düğme|  
|ROLE_SYSTEM_CLIENT|Takvim|  
|ROLE_SYSTEM_CHECKBUTTON|Onay kutusu|  
|ROLE_SYSTEM_COMBOBOX|Birleşik giriş kutusu|  
|ROLE_SYSTEM_CLIENT|Özel|  
|ROLE_SYSTEM_LIST|Veri Kılavuzu|  
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
  
 Farklı denetim türleri hakkında daha fazla bilgi için bkz. [UI Otomasyon denetim türleri](../../../docs/framework/ui-automation/ui-automation-control-types.md).  
  
<a name="States_and_Properties"></a>   
## <a name="states-and-properties"></a>Durumları ve özellikleri  
 İçinde [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)], özellikleri ve bazı özellikleri ortak bir dizi öğeleri destekler (gibi `accState`) öğenin rolüne bağlı olarak çok farklı şeyi açıklamanız gerekir. Sunucuları, tüm yöntemleri uygulanmalı `IAccessible` bir özelliği, öğe için ilgili olmayan olanlar bile döndürür.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Bazı durumlarda için karşılık gelen çok daha fazla özellik tanımlar [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]. Bazı tüm öğeler için ortaktır, ancak diğer denetim türlerini ve denetim düzenleri özgüdür. Özellikleri benzersiz tanımlayıcıları ile ayırt edici ve özelliklerin çoğu, tek bir yöntem kullanılarak alınabilir <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> veya <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>. Birçok özellikleri de kolayca alınabilir gelen <xref:System.Windows.Automation.AutomationElement.Current%2A> ve <xref:System.Windows.Automation.AutomationElement.Cached%2A> özellik erişimcileri.  
  
 UI Otomasyon sağlayıcısında ilgisiz özellikleri uygulamak zorunda değildir, ancak yalnızca döndürebilirsiniz bir `null` bunu desteklemiyor herhangi bir özellik için değer. Ayrıca, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] core hizmeti varsayılan pencere sağlayıcısından bazı özellikleri elde edebilirsiniz ve bu sağlayıcı tarafından açıkça uygulanan özelliklerle amalgamated.  
  
 Daha fazla özellikleri destekleyen yanı sıra [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] kaynakları daha iyi performans birden çok özellik tek çapraz işlem çağrısı ile alınmasına izin vererek.  
  
 Aşağıdaki tabloda iki model özellikleri arasındaki ilişkiyi gösterir.  
  
|[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] özellik erişimcisi|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik kimliği|Açıklamalar|  
|-----------------------------------------------------------------------------------|---------------------------------------------------------------------------------------|-------------|  
|`get_accKeyboardShortcut`|<xref:System.Windows.Automation.AutomationElement.AccessKeyProperty> veya <xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>|`AccessKeyProperty` her ikisi de varsa önceliklidir.|  
|`get_accName`|<xref:System.Windows.Automation.AutomationElement.NameProperty>||  
|`get_accRole`|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>|Denetim türleri rollere eşlemesi için önceki tabloya bakın.|  
|`get_accValue`|<xref:System.Windows.Automation.ValuePattern.ValueProperty?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.RangeValuePattern.ValueProperty?displayProperty=nameWithType>|ValuePattern'ı veya RangeValuePattern'ı destekleyen denetim türleri için geçerlidir. RangeValue değerleri MSAA davranışı ile tutarlı olması için 0-100, normalleştirilir. Bir dize değeri öğeleri kullanın.|  
|`get_accHelp`|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>||  
|`accLocation`|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>||  
|`get_accDescription`|Desteklenmiyor [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|`accDescription` Bu özellikte farklı bilgi parçasını yerleştirme sağlayıcıları sonuçlandı MSAA içinde bir açık belirtimi yoktu.|  
|`get_accHelpTopic`|Desteklenmiyor [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]||  
  
 Aşağıdaki tabloda gösterir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri karşılık [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] durum sabitler.  
  
|[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] durumu|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Özelliği|Tetikleyici durumu değişikliği?|  
|-----------------------------------------------------------------------|------------------------------------------------------------------------------------|----------------------------|  
|STATE_SYSTEM_CHECKED|Onay kutusu <xref:System.Windows.Automation.TogglePattern.ToggleStateProperty><br /><br /> Radyo düğmesi <xref:System.Windows.Automation.SelectionItemPattern.IsSelectedProperty>|Y|  
|STATE_SYSTEM_COLLAPSED|<xref:System.Windows.Automation.ExpandCollapsePattern.ExpandCollapsePatternInformation.ExpandCollapseState%2A> = <xref:System.Windows.Automation.ExpandCollapseState.Collapsed>|Y|  
|STATE_SYSTEM_EXPANDED|<xref:System.Windows.Automation.ExpandCollapsePattern.ExpandCollapsePatternInformation.ExpandCollapseState%2A> = <xref:System.Windows.Automation.ExpandCollapseState.Expanded> veya <xref:System.Windows.Automation.ExpandCollapseState.PartiallyExpanded>|Y|  
|STATE_SYSTEM_FOCUSABLE|<xref:System.Windows.Automation.AutomationElement.IsKeyboardFocusableProperty>|N|  
|STATE_SYSTEM_FOCUSED|<xref:System.Windows.Automation.AutomationElement.HasKeyboardFocusProperty>|N|  
|STATE_SYSTEM_HASPOPUP|<xref:System.Windows.Automation.ExpandCollapsePattern> menü öğeleri için|N|  
|STATE_SYSTEM_INVISIBLE|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty> = True ve <xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A> neden olur <xref:System.Windows.Automation.NoClickablePointException>|N|  
|STATE_SYSTEM_LINKED|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> =<br /><br /> <xref:System.Windows.Automation.ControlType.Hyperlink>|N|  
|STATE_SYSTEM_MIXED|<xref:System.Windows.Automation.TogglePattern.TogglePatternInformation.ToggleState%2A> = <xref:System.Windows.Automation.ToggleState.Indeterminate>|N|  
|STATE_SYSTEM_MOVEABLE|<xref:System.Windows.Automation.TransformPattern.CanMoveProperty>|N|  
|STATE_SYSTEM_MUTLISELECTABLE|<xref:System.Windows.Automation.SelectionPattern.CanSelectMultipleProperty>|N|  
|STATE_SYSTEM_OFFSCREEN|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty> = True|N|  
|STATE_SYSTEM_PROTECTED|<xref:System.Windows.Automation.AutomationElement.IsPasswordProperty>|N|  
|STATE_SYSTEM_READONLY|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty?displayProperty=nameWithType> ve <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty?displayProperty=nameWithType>|N|  
|STATE_SYSTEM_SELECTABLE|<xref:System.Windows.Automation.SelectionItemPattern> desteklenir|N|  
|STATE_SYSTEM_SELECTED|<xref:System.Windows.Automation.SelectionItemPattern.IsSelectedProperty>|N|  
|STATE_SYSTEM_SIZEABLE|<xref:System.Windows.Automation.TransformPattern.TransformPatternInformation.CanResize%2A>|N|  
|STATE_SYSTEM_UNAVAILABLE|<xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>|Y|  
  
 Ya da uygulanmadı çoğu tarafından şu durumlar [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] denetim sunucuları veya eşdeğeri olmayan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
|[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] durumu|Açıklamalar|  
|-----------------------------------------------------------------------|-------------|  
|STATE_SYSTEM_BUSY|Kullanılamaz [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_DEFAULT|Kullanılamaz [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_ANIMATED|Kullanılamaz [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_EXTSELECTABLE|Tarafından değil, yaygın olarak uygulanan [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] sunucuları|  
|STATE_SYSTEM_MARQUEED|Tarafından değil, yaygın olarak uygulanan [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] sunucuları|  
|STATE_SYSTEM_SELFVOICING|Tarafından değil, yaygın olarak uygulanan [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] sunucuları|  
|STATE_SYSTEM_TRAVERSED|Kullanılamaz [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_ALERT_HIGH|Tarafından değil, yaygın olarak uygulanan [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] sunucuları|  
|STATE_SYSTEM_ALERT_MEDIUM|Tarafından değil, yaygın olarak uygulanan [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] sunucuları|  
|STATE_SYSTEM_ALERT_LOW|Tarafından değil, yaygın olarak uygulanan [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] sunucuları|  
|STATE_SYSTEM_FLOATING|Tarafından değil, yaygın olarak uygulanan [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] sunucuları|  
|STATE_SYSTEM_HOTTRACKED|Kullanılamaz [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_PRESSED|Kullanılamaz [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
  
 Tam bir listesi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özelliği tanımlayıcılarını [UI Otomasyon özelliklerine genel bakış](../../../docs/framework/ui-automation/ui-automation-properties-overview.md).  
  
<a name="uiautomation_events_compare"></a>   
## <a name="events"></a>Olaylar  
 Olay mekanizmasında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], aksine, [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)], Windows olay (Bu yakından oturum penceresi tanıtıcıları bağlıdır) yönlendirme üzerinde kullanmayan ve bağlar ayarlamak için istemci uygulaması gerektirmez. Olaylara abonelikler yalnızca belirli olaylar ancak ağaç belirli bölümlerini ince ayar. Sağlayıcıları, ayrıca hangi olayların için dinledik izleyen tarafından oluşturma, olayları ince ayar yapabilirsiniz.  
  
 Ayrıca, istemcilerin doğrudan olay geri çağırma geçirilen bu olay, öğeleri almak daha kolay olur. Öğenin özelliklerini otomatik olarak önceden getirilmiş olan istemci olaya abone olduğunuzda, bir önbellek isteği etkindi.  
  
 İlişkiyi aşağıdaki tabloda gösterilmektedir [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] WinEvents ve [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayları.  
  
|WinEvent|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Olay tanımlayıcı|  
|--------------|--------------------------------------------------------------------------------------------|  
|EVENT_OBJECT_ACCELERATORCHANGE|<xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty> Özellik değişikliği|  
|EVENT_OBJECT_CONTENTSCROLLED|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty> veya <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> özellik değişikliğini ilişkili kaydırma çubukları hakkında|  
|EVENT_OBJECT_CREATE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_DEFACTIONCHANGE|Eşdeğeri|  
|EVENT_OBJECT_DESCRIPTIONCHANGE|Tam eşdeğeri; belki de <xref:System.Windows.Automation.AutomationElement.HelpTextProperty> veya <xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty> özellik değişikliği|  
|EVENT_OBJECT_DESTROY|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_FOCUS|<xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent>|  
|EVENT_OBJECT_HELPCHANGE|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty> Değişiklik|  
|EVENT_OBJECT_HIDE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_LOCATIONCHANGE|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty> Özellik değişikliği|  
|EVENT_OBJECT_NAMECHANGE|<xref:System.Windows.Automation.AutomationElement.NameProperty> Özellik değişikliği|  
|EVENT_OBJECT_PARENTCHANGE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_REORDER|Tutarlı bir şekilde kullanılan değil [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]. Doğrudan karşılık gelen bir olay tanımlanır [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].|  
|EVENT_OBJECT_SELECTION|<xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent>|  
|EVENT_OBJECT_SELECTIONADD|<xref:System.Windows.Automation.SelectionItemPattern.ElementAddedToSelectionEvent>|  
|EVENT_OBJECT_SELECTIONREMOVE|<xref:System.Windows.Automation.SelectionItemPattern.ElementRemovedFromSelectionEvent>|  
|EVENT_OBJECT_SELECTIONWITHIN|Eşdeğeri|  
|EVENT_OBJECT_SHOW|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_STATECHANGE|Çeşitli özellik değişti olayları|  
|EVENT_OBJECT_VALUECHANGE|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty?displayProperty=nameWithType> ve <xref:System.Windows.Automation.ValuePattern.ValueProperty?displayProperty=nameWithType> değiştirildi|  
|EVENT_SYSTEM_ALERT|Eşdeğeri|  
|EVENT_SYSTEM_CAPTUREEND|Eşdeğeri|  
|EVENT_SYSTEM_CAPTURESTART|Eşdeğeri|  
|EVENT_SYSTEM_CONTEXTHELPEND|Eşdeğeri|  
|EVENT_SYSTEM_CONTEXTHELPSTART|Eşdeğeri|  
|EVENT_SYSTEM_DIALOGEND|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|  
|EVENT_SYSTEM_DIALOGSTART|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|  
|EVENT_SYSTEM_DRAGDROPEND|Eşdeğeri|  
|EVENT_SYSTEM_DRAGDROPSTART|Eşdeğeri|  
|EVENT_SYSTEM_FOREGROUND|<xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent>|  
|EVENT_SYSTEM_MENUEND|<xref:System.Windows.Automation.AutomationElement.MenuClosedEvent>|  
|EVENT_SYSTEM_MENUPOPUPEND|<xref:System.Windows.Automation.AutomationElement.MenuClosedEvent>|  
|EVENT_SYSTEM_MENUPOPUPSTART|<xref:System.Windows.Automation.AutomationElement.MenuOpenedEvent>|  
|EVENT_SYSTEM_MENUSTART|<xref:System.Windows.Automation.AutomationElement.MenuOpenedEvent>|  
|EVENT_SYSTEM_MINIMIZEEND|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty> Özellik değişikliği|  
|EVENT_SYSTEM_MINIMIZESTART|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty> Özellik değişikliği|  
|EVENT_SYSTEM_MOVESIZEEND|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty> Özellik değişikliği|  
|EVENT_SYSTEM_MOVESIZESTART|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty> Özellik değişikliği|  
|EVENT_SYSTEM_SCROLLINGEND|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty> veya <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> özellik değişikliği|  
|EVENT_SYSTEM_SCROLLINGSTART|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty> veya <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> özellik değişikliği|  
|EVENT_SYSTEM_SOUND|Eşdeğeri|  
|EVENT_SYSTEM_SWITCHEND|Eşdeğeri yoktur, ancak bir <xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent> olay sinyalini verir yeni bir uygulama odağı aldı|  
|EVENT_SYSTEM_SWITCHSTART|Eşdeğeri|  
|Eşdeğeri|<xref:System.Windows.Automation.MultipleViewPattern.CurrentViewProperty> Özellik değişikliği|  
|Eşdeğeri|<xref:System.Windows.Automation.ScrollPattern.HorizontallyScrollableProperty> Özellik değişikliği|  
|Eşdeğeri|<xref:System.Windows.Automation.ScrollPattern.VerticallyScrollableProperty> Özellik değişikliği|  
|Eşdeğeri|<xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> Özellik değişikliği|  
|Eşdeğeri|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty> Özellik değişikliği|  
|Eşdeğeri|<xref:System.Windows.Automation.ScrollPattern.HorizontalViewSizeProperty> Özellik değişikliği|  
|Eşdeğeri|<xref:System.Windows.Automation.ScrollPattern.VerticalViewSizeProperty> Özellik değişikliği|  
|Eşdeğeri|<xref:System.Windows.Automation.TogglePattern.ToggleStateProperty> Özellik değişikliği|  
|Eşdeğeri|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty> Özellik değişikliği|  
|Eşdeğeri|<xref:System.Windows.Automation.AutomationElement.AsyncContentLoadedEvent> Olay|  
|Eşdeğeri|<xref:System.Windows.Automation.AutomationElement.ToolTipOpenedEvent>|  
  
<a name="Security_compare"></a>   
## <a name="security"></a>Güvenlik  
 Bazı `IAccessible` özelleştirme senaryosu gerektirir temel sarmalama `IAccessible` ve aracılığıyla için çağırma. Kısmen güvenilen bileşen verirler bir kod yolunda olmamalıdır olduğundan bu güvenlik etkileri vardır.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Modeli aracılığıyla diğer sağlayıcısı kodu çağırmak sağlayıcıları gereksinimini ortadan kaldırır. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Çekirdek hizmeti tüm gerekli toplama yapar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UI Otomasyonu Temelleri](../../../docs/framework/ui-automation/index.md)
