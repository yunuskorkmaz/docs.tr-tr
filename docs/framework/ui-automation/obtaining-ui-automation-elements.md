---
title: UI Otomasyon Öğelerini Alma
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, obtaining elements
- elements, UI Automation, obtaining
ms.assetid: c2caaf45-e59c-42a1-bc9b-77a6de520171
ms.openlocfilehash: 8c222cb2cf70502024a5934c4c527334c9f24165
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966381"
---
# <a name="obtaining-ui-automation-elements"></a>UI Otomasyon Öğelerini Alma
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir. Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu, öğeler için <xref:System.Windows.Automation.AutomationElement> [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] nesneleri almanın çeşitli yollarını açıklamaktadır.  
  
> [!CAUTION]
>  İstemci uygulamanız kendi Kullanıcı arabirimindeki öğeleri bulmaya çalışıyorsa, tüm [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] çağrıları ayrı bir iş parçacığında yapmanız gerekir. Daha fazla bilgi için bkz. [UI Otomasyonu Iş parçacığı sorunları](../../../docs/framework/ui-automation/ui-automation-threading-issues.md).  
  
<a name="The_Root_Element"></a>   
## <a name="root-element"></a>Kök öğe  
 Tüm <xref:System.Windows.Automation.AutomationElement> nesneler aramalarının bir başlangıç yerinde olması gerekir. Bu, Masaüstü, uygulama penceresi veya denetim dahil olmak üzere herhangi bir öğe olabilir.  
  
 Tüm öğelerin alt öğe olduğu masaüstü için kök öğe, statik <xref:System.Windows.Automation.AutomationElement.RootElement%2A?displayProperty=nameWithType> özelliğinden alınır.  
  
> [!CAUTION]
>  Genel olarak, yalnızca kendi doğrudan alt öğelerini <xref:System.Windows.Automation.AutomationElement.RootElement%2A>edinmeye çalışırsınız. Alt öğeler için arama yüzlerce veya hatta binlerce öğe aracılığıyla yineleyebilir ve muhtemelen yığın taşmasına neden olabilir. Daha düşük bir düzeyde belirli bir öğe edinmeye çalışıyorsanız, aramanızı uygulama penceresinden veya bir kapsayıcıdan daha düşük bir düzeyde başlatmanız gerekir.  
  
<a name="Using_Conditions"></a>   
## <a name="conditions"></a>Koşullar  
 Öğeleri almak [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] için kullanabileceğiniz çoğu teknik için, hangi öğelerin almak istediğinizi tanımlayan bir <xref:System.Windows.Automation.Condition>ölçüt kümesi olan bir belirtmeniz gerekir.  
  
 En basit koşul <xref:System.Windows.Automation.Condition.TrueCondition>, arama kapsamındaki tüm öğelerin döndürülüp döndürülmeyeceğini belirten önceden tanımlanmış bir nesnedir. <xref:System.Windows.Automation.Condition.FalseCondition>, ' ın <xref:System.Windows.Automation.Condition.TrueCondition>dönüştürüleyi, öğelerin değiştirilmesini önleyecağından daha az yararlıdır.  
  
 Önceden tanımlanmış üç koşul tek başına veya diğer koşullarla birlikte kullanılabilir: <xref:System.Windows.Automation.Automation.ContentViewCondition>, <xref:System.Windows.Automation.Automation.ControlViewCondition>, ve <xref:System.Windows.Automation.Automation.RawViewCondition>. <xref:System.Windows.Automation.Automation.RawViewCondition>, öğeleri <xref:System.Windows.Automation.Condition.TrueCondition> <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> veya özelliklerinegörefiltrelemediğindenkendisitarafındankullanılan,öğesineeşdeğerdir.<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A>  
  
 Diğer koşullar, her biri bir özellik değeri belirten <xref:System.Windows.Automation.PropertyCondition> bir veya daha fazla nesneden oluşturulmuştur. Örneğin, bir <xref:System.Windows.Automation.PropertyCondition> , öğesinin etkin olduğunu veya belirli bir denetim modelini desteklediğini belirtebilir.  
  
 Koşullar, <xref:System.Windows.Automation.AndCondition> <xref:System.Windows.Automation.OrCondition>ve türündekinesneleroluşturarakBooleanLogickullanılarakbirleştirilebilir.<xref:System.Windows.Automation.NotCondition>  
  
<a name="Search_Scope"></a>   
## <a name="search-scope"></a>Arama kapsamı  
 <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> Veya<xref:System.Windows.Automation.AutomationElement.FindAll%2A> kullanılarak gerçekleştirilen aramaların yanı sıra bir başlangıç yeri de olmalıdır.  
  
 Kapsam, Aranmak üzere başlangıç yeri etrafında yer alan alanı tanımlar. Bu, öğenin kendisini, onun eşdüzey öğelerini, üst öğelerini, alt öğelerini ve alt öğelerini içerebilir.  
  
 Bir aramanın kapsamı, <xref:System.Windows.Automation.TreeScope> Numaralandırmadaki değerlerin bit düzeyinde birleşimine göre tanımlanır.  
  
<a name="Finding_a_Known_Element"></a>   
## <a name="finding-a-known-element"></a>Bilinen bir öğeyi bulma  
 , Ya da başka bir özellik ya da özelliklerin <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>birleşimiyle <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AutomationId%2A>tanımlanan bilinen bir öğeyi bulmak için, <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> yönteminin kullanılması en kolay yoldur. Aranan öğe bir uygulama penceresuysa, aramanın başlangıç noktası olabilir <xref:System.Windows.Automation.AutomationElement.RootElement%2A>.  
  
 Öğeleri bulmanın [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bu yolu, otomatikleştirilmiş test senaryolarında en yararlı seçenektir.  
  
<a name="Finding_Elements_in_a_Subtree"></a>   
## <a name="finding-elements-in-a-subtree"></a>Alt ağaçtaki öğeleri bulma  
 Bilinen bir öğeyle ilgili belirli ölçütlere uyan tüm öğeleri bulmak için kullanabilirsiniz <xref:System.Windows.Automation.AutomationElement.FindAll%2A>. Örneğin, liste öğelerini veya menü öğelerini bir listeden veya menüden almak ya da bir iletişim kutusundaki tüm denetimleri tanımlamak için bu yöntemi kullanabilirsiniz.  
  
<a name="Walking_a_Subtree"></a>   
## <a name="walking-a-subtree"></a>Alt ağaç yürüme  
 İstemcinizin ile birlikte kullanılabilecek uygulamalar hakkında daha önce bilginiz yoksa, <xref:System.Windows.Automation.TreeWalker> sınıfını kullanarak ilgilendiğiniz tüm öğelerin bir alt ağacını oluşturabilirsiniz. Uygulamanız bunu bir odak değişikliği olayına yanıt olarak gerektirebilir; Yani, bir uygulama veya denetim giriş odağını aldığında, UI Otomasyonu istemcisi alt öğeleri ve belki de odaklanmış öğenin tüm alt öğelerini inceler.  
  
 ' De <xref:System.Windows.Automation.TreeWalker> kullanılabilecek başka bir yol, bir öğenin üst öğelerinden birini tanımlamaktır. Örneğin, ağacı izleyerek bir denetimin üst penceresini belirleyebilirsiniz.  
  
 Sınıfının bir nesnesini <xref:System.Windows.Automation.TreeWalker> oluşturarak (bir ' a <xref:System.Windows.Automation.Condition>geçirerek ilgilendiğiniz öğeleri tanımlayarak) ya da alanları <xref:System.Windows.Automation.TreeWalker>olarak tanımlanan aşağıdaki önceden tanımlanmış nesnelerden birini kullanarak kullanabilirsiniz.  
  
|||  
|-|-|  
|<xref:System.Windows.Automation.TreeWalker.ContentViewWalker>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> Yalnızca`true`özelliği olan öğeleri bulur.|  
|<xref:System.Windows.Automation.TreeWalker.ControlViewWalker>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> Yalnızca`true`özelliği olan öğeleri bulur.|  
|<xref:System.Windows.Automation.TreeWalker.RawViewWalker>|Tüm öğeleri bulur.|  
  
 Bir <xref:System.Windows.Automation.TreeWalker>elde ettikten sonra, kullanımı basittir. Alt ağacın öğeleri `Get` arasında gezinmek için yöntemleri çağırmanız yeterlidir.  
  
 <xref:System.Windows.Automation.TreeWalker.Normalize%2A> Yöntemi, alt ağaçtaki bir öğenin, görünümün parçası olmayan başka bir öğeden gezinmek için kullanılabilir. Örneğin, kullanarak <xref:System.Windows.Automation.TreeWalker.ContentViewWalker>bir alt ağacın görünümünü oluşturduğunuzu varsayalım. Uygulamanız daha sonra bir kaydırma çubuğunun giriş odağını aldığını belirten bir bildirim alır. Bir kaydırma çubuğu bir içerik öğesi olmadığından, alt ağacının görünümünde mevcut değildir. Ancak, kaydırma <xref:System.Windows.Automation.AutomationElement> <xref:System.Windows.Automation.TreeWalker.Normalize%2A> çubuğunu temsil eder ve içerik görünümündeki en yakın üst öğeye sahip olursunuz.  
  
<a name="Other_Ways_to_Retrieve_an_Element"></a>   
## <a name="other-ways-to-retrieve-an-element"></a>Bir öğeyi almanın diğer yolları  
 Aramalara ve gezinmeye ek olarak, aşağıdaki yollarla bir <xref:System.Windows.Automation.AutomationElement> alabilirsiniz.  
  
### <a name="from-an-event"></a>Bir olaydan  
 Uygulamanız bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olay aldığında, olay işleyicinizde geçirilen kaynak nesne bir <xref:System.Windows.Automation.AutomationElement>olur. Örneğin, odak değiştirilen olaylara abone olduysa, içine geçirilen <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> kaynak odağı alan öğedir.  
  
 Daha fazla bilgi için bkz. [UI Otomasyon olaylarına abone olma](../../../docs/framework/ui-automation/subscribe-to-ui-automation-events.md).  
  
### <a name="from-a-point"></a>Bir noktadan  
 Ekran koordinatlarına sahipseniz (örneğin, bir imleç konumu), statik <xref:System.Windows.Automation.AutomationElement> <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> yöntemini kullanarak bir alabilirsiniz.  
  
### <a name="from-a-window-handle"></a>Pencere tanıtıcısından  
 HWND <xref:System.Windows.Automation.AutomationElement> 'den almak için statik <xref:System.Windows.Automation.AutomationElement.FromHandle%2A> yöntemi kullanın.  
  
### <a name="from-the-focused-control"></a>Odaklanmış denetimden  
 <xref:System.Windows.Automation.AutomationElement> Statik<xref:System.Windows.Automation.AutomationElement.FocusedElement%2A> özelliğinden odaklanmış denetimi temsil eden bir ' i alabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Özellik Koşulunu Temel Alan UI Otomasyonu Öğesi Bulma](../../../docs/framework/ui-automation/find-a-ui-automation-element-based-on-a-property-condition.md)
- [TreeWalker ile UI Otomasyonu Öğeleri Arasında Gezinme](../../../docs/framework/ui-automation/navigate-among-ui-automation-elements-with-treewalker.md)
- [UI Otomasyon Ağacına Genel Bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
