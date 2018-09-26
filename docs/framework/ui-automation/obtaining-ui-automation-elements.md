---
title: UI Otomasyon Öğelerini Alma
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, obtaining elements
- elements, UI Automation, obtaining
ms.assetid: c2caaf45-e59c-42a1-bc9b-77a6de520171
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 16bc9475599510a5e55f246d49aaa0be19314979
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47208691"
---
# <a name="obtaining-ui-automation-elements"></a>UI Otomasyon Öğelerini Alma
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konuda edinme çeşitli yolları açıklar <xref:System.Windows.Automation.AutomationElement> için nesneleri [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] öğeleri.  
  
> [!CAUTION]
>  İstemci uygulamanızı kendi kullanıcı arabiriminde öğeleri bulmak deneyebilir, tüm yapmanız gereken [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ayrı bir iş parçacığında çağırır. Daha fazla bilgi için [UI Otomasyon iş parçacığı oluşturma sorunları](../../../docs/framework/ui-automation/ui-automation-threading-issues.md).  
  
<a name="The_Root_Element"></a>   
## <a name="root-element"></a>Kök öğe  
 Tüm arar <xref:System.Windows.Automation.AutomationElement> nesneleri başlatma bağlantısı olması gerekir. Bu, masaüstü, uygulama penceresinin veya denetim gibi herhangi bir öğe olabilir.  
  
 Kök öğesi içinden tüm öğeleri descended, masaüstü, statik alınır <xref:System.Windows.Automation.AutomationElement.RootElement%2A?displayProperty=nameWithType> özelliği.  
  
> [!CAUTION]
>  Genel olarak, yalnızca doğrudan alt öğeleri almak denemelisiniz <xref:System.Windows.Automation.AutomationElement.RootElement%2A>. Alt öğeleri için arama, yüzlerce veya binlerce büyük olasılıkla bir yığın taşması ile elde edilen öğelerin bile aracılığıyla yineleme. Daha düşük bir düzeyde belirli bir öğeyi edinme çalışıyorsanız, uygulama penceresinin veya daha düşük bir düzeyde bir kapsayıcı aramanızı başlamanız gerekir.  
  
<a name="Using_Conditions"></a>   
## <a name="conditions"></a>Koşullar  
 Çoğu teknikleri almak için kullanabileceğiniz [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] öğelerini belirtmelisiniz bir <xref:System.Windows.Automation.Condition>, almak istediğiniz hangi öğelere tanımlama ölçüt kümesine.  
  
 En basit koşul <xref:System.Windows.Automation.Condition.TrueCondition>döndürülecek olan tüm öğeler içinde arama kapsamını belirten önceden tanımlanmış bir nesne. <xref:System.Windows.Automation.Condition.FalseCondition>, listesiyse, <xref:System.Windows.Automation.Condition.TrueCondition>, herhangi bir öğe bulundu gelen önleyen gibi daha az yararlıdır.  
  
 Üç önceden tanımlanmış koşullar tek başına veya diğer koşullar ile birlikte kullanılabilir: <xref:System.Windows.Automation.Automation.ContentViewCondition>, <xref:System.Windows.Automation.Automation.ControlViewCondition>, ve <xref:System.Windows.Automation.Automation.RawViewCondition>. <xref:System.Windows.Automation.Automation.RawViewCondition>, eşdeğer olan tek başına kullanılan <xref:System.Windows.Automation.Condition.TrueCondition>öğeler tarafından filtre değil çünkü bunların <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> veya <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> özellikleri.  
  
 Diğer koşullar bir veya daha fazla yerleşik <xref:System.Windows.Automation.PropertyCondition> nesneleri, her biri bir özellik değeri belirtir. Örneğin, bir <xref:System.Windows.Automation.PropertyCondition> öğe etkin olduğunu veya belirli bir denetim desenini destekler belirtebilir.  
  
 Koşullar türlerindeki nesneler, oluşturarak Boole mantığı kullanılarak birleştirilebilir <xref:System.Windows.Automation.AndCondition>, <xref:System.Windows.Automation.OrCondition>, ve <xref:System.Windows.Automation.NotCondition>.  
  
<a name="Search_Scope"></a>   
## <a name="search-scope"></a>Arama kapsamı  
 Kullanılarak yapılan aramalar <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> veya <xref:System.Windows.Automation.AutomationElement.FindAll%2A> başlangıç yerde yanı sıra kapsamı olmalıdır.  
  
 Başlangıç-arama yapılacak olan yerde boşluk kapsamını tanımlar. Bu öğe, eşdüzey, üst, alt öğelerinden, hemen alt ve alt öğelerini içerebilir.  
  
 Bir arama kapsamı değerlerinden Bitsel bir birleşimi tarafından tanımlanan <xref:System.Windows.Automation.TreeScope> sabit listesi.  
  
<a name="Finding_a_Known_Element"></a>   
## <a name="finding-a-known-element"></a>Bilinen bir öğe bulma  
 Tarafından tanımlanan, bilinen bir öğeyi bulmak için onun <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AutomationId%2A>, ya da diğer bazı özellik veya özellikleri birleşimi, kullanılacak kolay <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> yöntemi. Aranan öğesi bir uygulama penceresi ise, başlangıç noktası arama olabilir <xref:System.Windows.Automation.AutomationElement.RootElement%2A>.  
  
 Bulma, bu şekilde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] öğeler, otomatik test senaryolarında en kullanışlıdır.  
  
<a name="Finding_Elements_in_a_Subtree"></a>   
## <a name="finding-elements-in-a-subtree"></a>Bir alt ağacı içinde öğeleri bulma  
 Bilinen bir öğe için ilgili belirli ölçütlere tüm öğeleri bulmak için kullanabileceğiniz <xref:System.Windows.Automation.AutomationElement.FindAll%2A>. Örneğin, liste öğeleri veya menü öğelerinin bir listesini ya da menü almak veya iletişim kutusunda tüm denetimleri tanımlamak için bu yöntemi kullanabilirsiniz.  
  
<a name="Walking_a_Subtree"></a>   
## <a name="walking-a-subtree"></a>Bir alt ağacı yürüyen  
 Önceki olanağıyla, istemci ile kullanılabilir uygulamalar varsa, kullanarak bir alt ağacı ilgilendiğiniz tüm öğelerin oluşturabilirsiniz <xref:System.Windows.Automation.TreeWalker> sınıfı. Uygulamanızı odak değiştirilmiş bir olaya yanıt olarak bunu yapabilirsiniz; diğer bir deyişle, bir uygulamanın veya denetimin giriş odağını aldığında, UI Otomasyonu istemci alt ve odaklanan öğeyi belki de tüm bağımlı öğelerini inceler.  
  
 Başka bir yolla <xref:System.Windows.Automation.TreeWalker> kullanılabilir bir öğe öncüleri belirlemektir. Örneğin, ağacın yürüyen tarafından denetiminin üst penceresine tanımlayabilirsiniz.  
  
 Kullanabileceğiniz <xref:System.Windows.Automation.TreeWalker> sınıfın bir nesnesi oluşturarak ya da (geçirerek ilgi öğelerini tanımlayan bir <xref:System.Windows.Automation.Condition>), veya önceden tanımlanmış alanları tanımlanan nesneleri aşağıdakilerden birini kullanarak <xref:System.Windows.Automation.TreeWalker>.  
  
|||  
|-|-|  
|<xref:System.Windows.Automation.TreeWalker.ContentViewWalker>|Yalnızca öğeleri bulan olan <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> özelliği `true`.|  
|<xref:System.Windows.Automation.TreeWalker.ControlViewWalker>|Yalnızca öğeleri bulan olan <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> özelliği `true`.|  
|<xref:System.Windows.Automation.TreeWalker.RawViewWalker>|Tüm öğeleri bulur.|  
  
 Elde ettikten sonra bir <xref:System.Windows.Automation.TreeWalker>, bunu kullanan basit. Yalnızca çağrı `Get` ağacın öğeler arasında gezinmek için yöntemleri.  
  
 <xref:System.Windows.Automation.TreeWalker.Normalize%2A> Yöntemi alt ağacı içinde bir öğeye görünümün bir parçası olmayan başka bir öğeden gezinmek için kullanılabilir. Örneğin, oluşturduğunuz bir alt ağacı görünümünü kullanarak varsayalım <xref:System.Windows.Automation.TreeWalker.ContentViewWalker>. Ardından, uygulamanızın bir kaydırma çubuğu Girintiyi aldığını bildirim alır. Bir kaydırma çubuğu bir içerik öğesi olmadığı için alt ağacı görünümünüzde mevcut değil. Ancak, geçirebilirsiniz <xref:System.Windows.Automation.AutomationElement> için kaydırma çubuğunu temsil eden <xref:System.Windows.Automation.TreeWalker.Normalize%2A> ve içerik görünümünde en yakın üst öğe alır.  
  
<a name="Other_Ways_to_Retrieve_an_Element"></a>   
## <a name="other-ways-to-retrieve-an-element"></a>Bir öğe almanın diğer yolları  
 Aramalar ve gezinti yanı sıra, alabileceğiniz bir <xref:System.Windows.Automation.AutomationElement> aşağıdaki yollarla.  
  
### <a name="from-an-event"></a>Bir olay  
 Uygulamanızı aldığında bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayı, olay işleyicisine geçirilen kaynak nesnesi olan bir <xref:System.Windows.Automation.AutomationElement>. Odak değişti olayları için abone olduğunuz, örneğin, kaynak geçirilen, <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> odağı alınan öğedir.  
  
 Daha fazla bilgi için [UI Otomasyon olaylarına abone olma](../../../docs/framework/ui-automation/subscribe-to-ui-automation-events.md).  
  
### <a name="from-a-point"></a>Bir noktasından  
 Ekran koordinatları (örneğin, bir imleç konumu) varsa, alabileceğiniz bir <xref:System.Windows.Automation.AutomationElement> statik kullanarak <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> yöntemi.  
  
### <a name="from-a-window-handle"></a>Bir pencere tutucu  
 Alınacak bir <xref:System.Windows.Automation.AutomationElement> statik bir HWND'den kullanın <xref:System.Windows.Automation.AutomationElement.FromHandle%2A> yöntemi.  
  
### <a name="from-the-focused-control"></a>Odaklanmış denetiminden  
 Alabileceğiniz bir <xref:System.Windows.Automation.AutomationElement> odaklı denetimin statik temsil eden <xref:System.Windows.Automation.AutomationElement.FocusedElement%2A> özelliği.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özellik Koşulunu Temel Alan UI Otomasyonu Öğesi Bulma](../../../docs/framework/ui-automation/find-a-ui-automation-element-based-on-a-property-condition.md)  
 [TreeWalker ile UI Otomasyonu Öğeleri Arasında Gezinme](../../../docs/framework/ui-automation/navigate-among-ui-automation-elements-with-treewalker.md)  
 [UI Otomasyon Ağacına Genel Bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
