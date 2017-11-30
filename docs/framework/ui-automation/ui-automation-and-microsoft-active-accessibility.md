---
title: UI Otomasyonu ve Microsoft Active Accessibility
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Active Accessibility
- UI Automation, Active Accessibility compared to
- UI Automation, Microsoft Active Accessibility
- Active Accessibility, UI Automation compared to
ms.assetid: 87bee662-0a3e-4232-a421-20e7a5968321
caps.latest.revision: "24"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: dd3adbeebc0cc2a9e201bbe6492eb311f18a711d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ui-automation-and-microsoft-active-accessibility"></a>UI Otomasyonu ve Microsoft Active Accessibility
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)]uygulamaları erişilebilir hale getirme için önceki çözüm bulunuyordu. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]Yeni erişilebilirlik model için [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)] yardımcı teknoloji ürünlerinin gereksinimlerini ele almak için tasarlanmıştır ve test araçları otomatik. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]üzerinden birçok gelişme sunan [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)].  
  
 Bu konu, ana özelliklerini içerir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ve bu özelliklerin nasıl farklı açıklar [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)].  
  
<a name="Programming_Languages_compare"></a>   
## <a name="programming-languages"></a>Programlama dilleri  
 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]dayanır [!INCLUDE[TLA#tla_com](../../../includes/tlasharptla-com-md.md)] çift arabirim desteği ve bu nedenle C/C++'da programlanabilir [!INCLUDE[TLA#tla_vb6](../../../includes/tlasharptla-vb6-md.md)]ve komut dosyası dili. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)](Standart denetimler için istemci tarafı sağlayıcı kitaplığı dahil) yönetilen kodda yazılır ve UI otomasyon istemci uygulamaları en kolay programlanmış kullanarak [!INCLUDE[TLA#tla_vcshrp](../../../includes/tlasharptla-vcshrp-md.md)] veya [!INCLUDE[TLA#tla_visualbnet](../../../includes/tlasharptla-visualbnet-md.md)]. Arabirim uygulamaları olan UI Otomasyon sağlayıcıları, yönetilen kod veya C/C++ yazılabilir.  
  
<a name="Support_in_Windows_Presentation_Foundation_"></a>   
## <a name="support-in-windows-presentation-foundation"></a>Windows Presentation Foundation desteği  
 [!INCLUDE[TLA#tla_wpf](../../../includes/tlasharptla-wpf-md.md)]kullanıcı arabirimleri oluşturmak için yeni modelidir. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]öğeleri için yerel destek içermez [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]; ancak, destekledikleri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], içeren desteği köprüleme [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] istemciler. Yalnızca özel olarak yazılmış istemciler [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] erişilebilirlik özelliklerinden tam anlamıyla yararlanabilmek [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)], zengin metin için destek gibi.  
  
<a name="Servers_and_Clients_compare"></a>   
## <a name="servers-and-clients"></a>Sunucular ve istemciler  
 İçinde [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)], sunucular ve istemciler iletişim doğrudan büyük ölçüde sunucunun uygulaması `IAccessible`.  
  
 İçinde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bir çekirdek hizmet (bir sağlayıcı adı verilir) sunucusu ve istemci arasında arasındadır. Çekirdek hizmet sağlayıcıları tarafından uygulanan arabirimler çağrılar ve öğeleri için benzersiz çalışma zamanı tanımlayıcıları oluşturma gibi ek hizmetler sağlar. İstemci uygulamalarını kullanan kitaplık işlevleri çağırmak için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] hizmet.  
  
 UI Otomasyon sağlayıcıları için bilgi sağlayabilir [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] istemcileri ve [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] sunucuları UI otomasyon istemci uygulamaları için bilgi sağlayabilir. Ancak, çünkü [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] kadar bilgi olarak kullanıma sunmuyor [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], iki modeli tam olarak uyumlu değildir.  
  
<a name="UI_Elements_compare"></a>   
## <a name="ui-elements"></a>Kullanıcı Arabirimi öğeleri  
 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]sunan [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğeleri ya da farklı bir `IAccessible` arabirimi ya da bir alt tanımlayıcı gibi. İki karşılaştırmak zor `IAccessible` aynı öğeye başvuruda belirlemek için işaretçi.  
  
 İçinde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], her bir öğe olarak temsil edilen bir <xref:System.Windows.Automation.AutomationElement> nesnesi. Karşılaştırma eşitlik işleci kullanılarak yapılır veya <xref:System.Windows.Automation.AutomationElement.Equals%2A> yöntemi, her ikisi de öğeleri benzersiz çalışma zamanı tanımlayıcıların karşılaştırın.  
  
<a name="Tree_Views_and_Navigation_compare"></a>   
## <a name="tree-views-and-navigation"></a>Ağaç görünümleri ve gezinme  
 [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] Öğeleri ekranda görülme ağaç yapısı olarak masaüstü ile uygulama windows, kök yakınındaki alt öğeleri ve uygulama içinden öğeleri olarak daha fazla alt öğeleri.  
  
 İçinde [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)], son kullanıcılara ilgisiz birçok Otomasyon öğeleri ağacında sunulur. İstemci uygulamaları anlamlı olan belirlemek için tüm öğeler bakmanız gerekir.  
  
 UI Otomasyonu istemci uygulamaları görmek [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] filtre uygulanmış bir görünüm üzerinden. Görünüm yalnızca ilgilendiğiniz öğeler içeriyor: etkileşimi etkinleştirmek ya da kullanıcıya bilgi verilir. Yalnızca denetim öğeleri ve yalnızca içerik öğeleri önceden tanımlanmış görünümleri kullanılabilir; Ayrıca, uygulamaları özel görünümler tanımlayabilirsiniz. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]açıklayan görevini basitleştirir [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] kullanıcı ve uygulama ile etkileşim kullanıcı yardımcı olur.  
  
 Öğeleri arasında gezinme, [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)], da (örneğin, ekranda solunda kalan öğesine taşıma) uzamsal, mantıksal (örneğin, bir sonraki menü öğesini ya da bir iletişim kutusu içindeki sekme sırası'na taşıma) veya (için hiyerarşik üst için bir kapsayıcı veya alt ilk alt taşıma örnek,). Hiyerarşik gezinti alt öğelerini her zaman uygulayan nesneler olmadığını gerçeğiyle karmaşık `IAccessible`.  
  
 İçinde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], tüm [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğeler <xref:System.Windows.Automation.AutomationElement> aynı temel işlevleri desteklemek nesneleri. (Sağlayıcının bakış açısına ait oldukları devralınan bir arabirimi uygulayan nesneler <xref:System.Windows.Automation.Provider.IRawElementProviderSimple>.) Gezinti çoğunlukla hiyerarşik: üst alt öğelerine ve sonraki bir eşdüzeyi. (Sekme sırasını takip eşdüzey arasında gezinme mantıksal bir öğeye sahip.) Ağacın filtre uygulanmış bir görünüm kullanarak tüm başlangıç-noktasından gidebilirsiniz <xref:System.Windows.Automation.TreeWalker> sınıfı. Kullanarak belirli bir alt öğe veya alt öğeleri de gidebilirsiniz <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> ve <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; Örneğin, bir iletişim kutusu içinde belirtilen denetim deseni destekleyen tüm öğeleri almak çok kolaydır.  
  
 Gezinti bölmesinde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] içinde daha fazla tutarlı [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]. Aşağı açılır listeler ve açılır pencereleri gibi bazı öğeler iki kez şekilde görünmesi [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] ağaç ve onlardan Gezinti olabilir beklenmeyen sonuçlar. Düzgün bir şekilde uygulamak gerçekten olanaksızdır [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] rebar denetimi için. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Böylece öğeyi windows sahipliğini tarafından uygulanan hiyerarşi rağmen ağacındaki herhangi bir yere yerleştirilebilir, yeniden konumlandırma ve reparenting etkinleştirir.  
  
<a name="Roles_and_Control_Types"></a>   
## <a name="roles-and-control-types"></a>Rolleri ve Denetim türleri  
 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]kullanan `accRole` özelliği (`IAccessible::get_actRole`) öğenin rolünde açıklamasını almak için [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]ROLE_SYSTEM_SLIDER veya ROLE_SYSTEM_MENUITEM gibi. Bir öğenin ana ipucu kullanılabilir işlevselliğini rolüdür. Bir denetim ile etkileşimi gibi sabit yöntemler kullanılarak gerçekleştirilir `IAccessible::accSelect` ve `IAccessible::accDoDefaultAction`. İstemci uygulaması arasındaki etkileşimi ve [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] ne aracılığıyla yapılabilir için sınırlı `IAccessible`.  
  
 Buna karşılık, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] büyük ölçüde öğesi denetim türü ayrıştırır (tarafından açıklanan <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> özelliği) beklenen işlevselliğini gelen. İşlev uygulaması özel arabirimleri aracılığıyla sağlayıcısı tarafından desteklenen denetim düzenleri tarafından belirlenir. Denetim desenleri, belirli bir tarafından desteklenen işlevleri kümesini tanımlamak için birleştirilebilir [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] öğesi. Bazı sağlayıcılar belirli denetim düzenini desteklemek için gereklidir; Örneğin, sağlayıcı bir onay kutusu için değiştirme denetim düzenini desteklemesi gerekir. Diğer sağlayıcıları bir veya daha fazla denetim desenleri desteklemek için gereklidir; Örneğin, bir düğme, geçiş veya Invoke desteklemesi gerekir. Hala başkalarının hiçbir denetim düzenleri hiç desteği; Örneğin, yeniden boyutlandırılabilir, yerleşik veya taşınamaz bölme tüm denetim düzenleri yok.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]tarafından tanımlanan özel denetimlerini destekleyen <xref:System.Windows.Automation.ControlType.Custom> özelliği ve tarafından açıklanan <xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty> özelliği.  
  
 Aşağıdaki tablo eşleme gösterir [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] rollere [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] denetim türleri.  
  
|[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]rolü|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Denetim türü|  
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
  
 Farklı denetim türleri hakkında daha fazla bilgi için bkz: [UI Otomasyon denetim türleri](../../../docs/framework/ui-automation/ui-automation-control-types.md).  
  
<a name="States_and_Properties"></a>   
## <a name="states-and-properties"></a>Durumları ve özellikleri  
 İçinde [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)], öğeleri destek özellikleri ve bazı özellikleri ortak bir dizi (gibi `accState`) öğenin rolüne bağlı olarak çok farklı şeyleri açıklamak gerekir. Sunucuları, tüm yöntemleri uygulanmalı `IAccessible` bir özellik öğesine ilgili olmayan olanlar bile döndürür.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bazıları karşılık Devletleri'nde pek çok daha fazla özellik tanımlar [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]. Bazı tüm öğeleri için ortak olan, ancak diğer denetim türleri ve denetim düzenleri özgüdür. Benzersiz tanımlayıcıları tarafından özellikleri ayırt edici ve tek bir yöntemi kullanarak çoğu özellikler alınabilir <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> veya <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>. Birçok özelliği de kolayca alınabilir gelen <xref:System.Windows.Automation.AutomationElement.Current%2A> ve <xref:System.Windows.Automation.AutomationElement.Cached%2A> özellik erişimcisi.  
  
 UI Otomasyon sağlayıcı ilgisiz özellikleri uygulamak gerekmez, ancak yalnızca döndürebilirsiniz bir `null` bunu desteklemiyor herhangi bir özellik için değer. Ayrıca, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] çekirdek hizmet bazı özellikler varsayılan pencere sağlayıcıdan elde edebilirsiniz ve bu açıkça sağlayıcı tarafından uygulanan özelliklerle amalgamated.  
  
 Pek çok daha fazla özellik destekleme yanı sıra [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] kaynakları daha iyi performans tek çapraz işlem çağrısı ile alınması birden çok özellikleri sağlayarak.  
  
 Aşağıdaki tabloda iki model özelliklerinde arasındaki ilişkiyi gösterir.  
  
|[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]özellik erişimcisi|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]özellik kimliği|Açıklamalar|  
|-----------------------------------------------------------------------------------|---------------------------------------------------------------------------------------|-------------|  
|`get_accKeyboardShortcut`|<xref:System.Windows.Automation.AutomationElement.AccessKeyProperty>veya<xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>|`AccessKeyProperty`her ikisi de varsa önceliklidir.|  
|`get_accName`|<xref:System.Windows.Automation.AutomationElement.NameProperty>||  
|`get_accRole`|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>|Denetim türleri rollere eşlemesi için önceki tabloya bakın.|  
|`get_accValue`|<xref:System.Windows.Automation.ValuePattern.ValueProperty?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.RangeValuePattern.ValueProperty?displayProperty=nameWithType>|ValuePattern'ı veya RangeValuePattern'ı destekleyen denetim türü için geçerlidir. RangeValue değerleri, MSAA davranışı ile tutarlı olacak şekilde 0-100, normalleştirilmiş. Bir dize değeri öğelerini kullanın.|  
|`get_accHelp`|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>||  
|`accLocation`|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>||  
|`get_accDescription`|Desteklenmiyor[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|`accDescription`Bu özellik farklı bilgi parçalarını yerleştirme sağlayıcıları ile sonuçlandı MSAA içinde Temizle belirtimi sahip değil.|  
|`get_accHelpTopic`|Desteklenmiyor[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]||  
  
 Aşağıdaki tabloda gösterir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri karşılık [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] sabitleri belirtin.  
  
|[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]durumu|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]özelliği|Tetikleyiciler durumu değişikliği?|  
|-----------------------------------------------------------------------|------------------------------------------------------------------------------------|----------------------------|  
|STATE_SYSTEM_CHECKED|Onay kutusu için<xref:System.Windows.Automation.TogglePattern.ToggleStateProperty><br /><br /> Radyo düğmesi<xref:System.Windows.Automation.SelectionItemPattern.IsSelectedProperty>|Y|  
|STATE_SYSTEM_COLLAPSED|<xref:System.Windows.Automation.ExpandCollapsePattern.ExpandCollapsePatternInformation.ExpandCollapseState%2A> = <xref:System.Windows.Automation.ExpandCollapseState.Collapsed>|Y|  
|STATE_SYSTEM_EXPANDED|<xref:System.Windows.Automation.ExpandCollapsePattern.ExpandCollapsePatternInformation.ExpandCollapseState%2A> = <xref:System.Windows.Automation.ExpandCollapseState.Expanded>veya<xref:System.Windows.Automation.ExpandCollapseState.PartiallyExpanded>|Y|  
|STATE_SYSTEM_FOCUSABLE|<xref:System.Windows.Automation.AutomationElement.IsKeyboardFocusableProperty>|N|  
|STATE_SYSTEM_FOCUSED|<xref:System.Windows.Automation.AutomationElement.HasKeyboardFocusProperty>|N|  
|STATE_SYSTEM_HASPOPUP|<xref:System.Windows.Automation.ExpandCollapsePattern>menü öğeleri|N|  
|STATE_SYSTEM_INVISIBLE|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty>= True ve <xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A> neden olur.<xref:System.Windows.Automation.NoClickablePointException>|N|  
|STATE_SYSTEM_LINKED|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> =<br /><br /> <xref:System.Windows.Automation.ControlType.Hyperlink>|N|  
|STATE_SYSTEM_MIXED|<xref:System.Windows.Automation.TogglePattern.TogglePatternInformation.ToggleState%2A> = <xref:System.Windows.Automation.ToggleState.Indeterminate>|N|  
|STATE_SYSTEM_MOVEABLE|<xref:System.Windows.Automation.TransformPattern.CanMoveProperty>|N|  
|STATE_SYSTEM_MUTLISELECTABLE|<xref:System.Windows.Automation.SelectionPattern.CanSelectMultipleProperty>|N|  
|STATE_SYSTEM_OFFSCREEN|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty>= True|N|  
|STATE_SYSTEM_PROTECTED|<xref:System.Windows.Automation.AutomationElement.IsPasswordProperty>|N|  
|STATE_SYSTEM_READONLY|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty?displayProperty=nameWithType>ve<xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty?displayProperty=nameWithType>|N|  
|STATE_SYSTEM_SELECTABLE|<xref:System.Windows.Automation.SelectionItemPattern>desteklenir|N|  
|STATE_SYSTEM_SELECTED|<xref:System.Windows.Automation.SelectionItemPattern.IsSelectedProperty>|N|  
|STATE_SYSTEM_SIZEABLE|<xref:System.Windows.Automation.TransformPattern.TransformPatternInformation.CanResize%2A>|N|  
|STATE_SYSTEM_UNAVAILABLE|<xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>|Y|  
  
 Ya da uygulanmadı çoğu tarafından aşağıdaki durumları [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] kontrol sunucuları veya eşdeğeri olmayan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
|[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]durumu|Açıklamalar|  
|-----------------------------------------------------------------------|-------------|  
|STATE_SYSTEM_BUSY|Mevcut değil[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_DEFAULT|Mevcut değil[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_ANIMATED|Mevcut değil[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_EXTSELECTABLE|Tarafından geniş ölçüde uygulanan [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] sunucuları|  
|STATE_SYSTEM_MARQUEED|Tarafından geniş ölçüde uygulanan [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] sunucuları|  
|STATE_SYSTEM_SELFVOICING|Tarafından geniş ölçüde uygulanan [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] sunucuları|  
|STATE_SYSTEM_TRAVERSED|Mevcut değil[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_ALERT_HIGH|Tarafından geniş ölçüde uygulanan [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] sunucuları|  
|STATE_SYSTEM_ALERT_MEDIUM|Tarafından geniş ölçüde uygulanan [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] sunucuları|  
|STATE_SYSTEM_ALERT_LOW|Tarafından geniş ölçüde uygulanan [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] sunucuları|  
|STATE_SYSTEM_FLOATING|Tarafından geniş ölçüde uygulanan [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] sunucuları|  
|STATE_SYSTEM_HOTTRACKED|Mevcut değil[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_PRESSED|Mevcut değil[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
  
 Tam bir listesi için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özelliği tanımlayıcıları Bkz [UI Otomasyon özelliklerine genel bakış](../../../docs/framework/ui-automation/ui-automation-properties-overview.md).  
  
<a name="uiautomation_events_compare"></a>   
## <a name="events"></a>Olaylar  
 Olay yönteminde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], aksine, [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)], Windows olay (hangi yakından pencere işleyicileri oturum bağlıdır) yönlendirme üzerinde bağlı değildir ve kancaları ayarlamak için istemci uygulaması gerektirmez. Olaylara abonelikleri yalnızca belirli olaylar ancak ağaç belirli bölümlerine için ince ayar. Sağlayıcıları, ayrıca bunların izlemek için hangi olayların kulak çoğunun tutarak, olaylar oluşturma ince ayar yapabilirsiniz.  
  
 Ayrıca, istemcilerin bu doğrudan olay geri çağırma geçirilen olaylarını, öğeleri almak daha kolay olur. İstemci olaya abone olduğunuzda önbellek isteği etkin ise, öğenin özelliklerini otomatik olarak prefetched.  
  
 Aşağıdaki tabloda iletişimi gösterir [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] WinEvents ve [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olaylar.  
  
|WinEvent|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Olay tanımlayıcısı|  
|--------------|--------------------------------------------------------------------------------------------|  
|EVENT_OBJECT_ACCELERATORCHANGE|<xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>özellik değişikliği|  
|EVENT_OBJECT_CONTENTSCROLLED|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty>veya <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> özellik değişikliği ilişkili kaydırma çubukları hakkında|  
|EVENT_OBJECT_CREATE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_DEFACTIONCHANGE|Eşdeğeri|  
|EVENT_OBJECT_DESCRIPTIONCHANGE|Tam eşdeğeri yok; belki de <xref:System.Windows.Automation.AutomationElement.HelpTextProperty> veya <xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty> özellik değişikliği|  
|EVENT_OBJECT_DESTROY|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_FOCUS|<xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent>|  
|EVENT_OBJECT_HELPCHANGE|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>değiştirme|  
|EVENT_OBJECT_HIDE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_LOCATIONCHANGE|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>özellik değişikliği|  
|EVENT_OBJECT_NAMECHANGE|<xref:System.Windows.Automation.AutomationElement.NameProperty>özellik değişikliği|  
|EVENT_OBJECT_PARENTCHANGE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_REORDER|Tutarlı bir şekilde kullanılan değil [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]. Doğrudan karşılık gelen bir olay tanımlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].|  
|EVENT_OBJECT_SELECTION|<xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent>|  
|EVENT_OBJECT_SELECTIONADD|<xref:System.Windows.Automation.SelectionItemPattern.ElementAddedToSelectionEvent>|  
|EVENT_OBJECT_SELECTIONREMOVE|<xref:System.Windows.Automation.SelectionItemPattern.ElementRemovedFromSelectionEvent>|  
|EVENT_OBJECT_SELECTIONWITHIN|Eşdeğeri|  
|EVENT_OBJECT_SHOW|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_STATECHANGE|Çeşitli özellik değişti olayları|  
|EVENT_OBJECT_VALUECHANGE|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty?displayProperty=nameWithType>ve <xref:System.Windows.Automation.ValuePattern.ValueProperty?displayProperty=nameWithType> değiştirildi|  
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
|EVENT_SYSTEM_MINIMIZEEND|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty>özellik değişikliği|  
|EVENT_SYSTEM_MINIMIZESTART|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty>özellik değişikliği|  
|EVENT_SYSTEM_MOVESIZEEND|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>özellik değişikliği|  
|EVENT_SYSTEM_MOVESIZESTART|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>özellik değişikliği|  
|EVENT_SYSTEM_SCROLLINGEND|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty>veya <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> özellik değişikliği|  
|EVENT_SYSTEM_SCROLLINGSTART|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty>veya <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> özellik değişikliği|  
|EVENT_SYSTEM_SOUND|Eşdeğeri|  
|EVENT_SYSTEM_SWITCHEND|Hiçbir eşdeğeri ancak bir <xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent> olay sinyalleri yeni bir uygulama odağı aldı|  
|EVENT_SYSTEM_SWITCHSTART|Eşdeğeri|  
|Eşdeğeri|<xref:System.Windows.Automation.MultipleViewPattern.CurrentViewProperty>özellik değişikliği|  
|Eşdeğeri|<xref:System.Windows.Automation.ScrollPattern.HorizontallyScrollableProperty>özellik değişikliği|  
|Eşdeğeri|<xref:System.Windows.Automation.ScrollPattern.VerticallyScrollableProperty>özellik değişikliği|  
|Eşdeğeri|<xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty>özellik değişikliği|  
|Eşdeğeri|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty>özellik değişikliği|  
|Eşdeğeri|<xref:System.Windows.Automation.ScrollPattern.HorizontalViewSizeProperty>özellik değişikliği|  
|Eşdeğeri|<xref:System.Windows.Automation.ScrollPattern.VerticalViewSizeProperty>özellik değişikliği|  
|Eşdeğeri|<xref:System.Windows.Automation.TogglePattern.ToggleStateProperty>özellik değişikliği|  
|Eşdeğeri|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty>özellik değişikliği|  
|Eşdeğeri|<xref:System.Windows.Automation.AutomationElement.AsyncContentLoadedEvent>Olay|  
|Eşdeğeri|<xref:System.Windows.Automation.AutomationElement.ToolTipOpenedEvent>|  
  
<a name="Security_compare"></a>   
## <a name="security"></a>Güvenlik  
 Bazı `IAccessible` özelleştirme senaryolarını gerektiren bir taban kaydırma `IAccessible` ve aracılığıyla kendisine çağırma. Kısmen güvenilen bileşen bir aracı bir kod yolunda olmamalıdır beri bu güvenlik etkilere sahiptir.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Modeli aracılığıyla başka bir sağlayıcı kod çağırmak sağlayıcıları gereksinimini ortadan kaldırır. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Çekirdek hizmeti tüm gerekli toplama yapar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UI Otomasyon temelleri](../../../docs/framework/ui-automation/index.md)
