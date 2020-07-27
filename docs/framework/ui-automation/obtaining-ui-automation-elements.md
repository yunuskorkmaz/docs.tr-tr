---
title: UI Otomasyon Öğelerini Alma
description: Kullanıcı arabirimi (UI) öğeleri için UI Otomasyon öğesi (AutomationElement) nesneleri elde etmenin çeşitli yollarını gözden geçirin.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, obtaining elements
- elements, UI Automation, obtaining
ms.assetid: c2caaf45-e59c-42a1-bc9b-77a6de520171
ms.openlocfilehash: 2b741dde3b30334ba8fa990d73044da7e3bdd2da
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168160"
---
# <a name="obtaining-ui-automation-elements"></a>UI Otomasyon Öğelerini Alma
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu, <xref:System.Windows.Automation.AutomationElement> öğeler için nesneleri almanın çeşitli yollarını açıklamaktadır [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] .  
  
> [!CAUTION]
> İstemci uygulamanız kendi Kullanıcı arabirimindeki öğeleri bulmaya çalışıyorsa, tüm [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] çağrıları ayrı bir iş parçacığında yapmanız gerekir. Daha fazla bilgi için bkz. [UI Otomasyonu Iş parçacığı sorunları](ui-automation-threading-issues.md).  
  
<a name="The_Root_Element"></a>
## <a name="root-element"></a>Kök öğe  
 Tüm nesneler aramalarının <xref:System.Windows.Automation.AutomationElement> bir başlangıç yerinde olması gerekir. Bu, Masaüstü, uygulama penceresi veya denetim dahil olmak üzere herhangi bir öğe olabilir.  
  
 Tüm öğelerin alt öğe olduğu masaüstü için kök öğe, statik <xref:System.Windows.Automation.AutomationElement.RootElement%2A?displayProperty=nameWithType> özelliğinden alınır.  
  
> [!CAUTION]
> Genel olarak, yalnızca kendi doğrudan alt öğelerini edinmeye çalışırsınız <xref:System.Windows.Automation.AutomationElement.RootElement%2A> . Alt öğeler için arama yüzlerce veya hatta binlerce öğe aracılığıyla yineleyebilir ve muhtemelen yığın taşmasına neden olabilir. Daha düşük bir düzeyde belirli bir öğe edinmeye çalışıyorsanız, aramanızı uygulama penceresinden veya bir kapsayıcıdan daha düşük bir düzeyde başlatmanız gerekir.  
  
<a name="Using_Conditions"></a>
## <a name="conditions"></a>Koşullar  
 Öğeleri almak için kullanabileceğiniz çoğu teknik için, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation.Condition> hangi öğelerin almak istediğinizi tanımlayan bir ölçüt kümesi olan bir belirtmeniz gerekir.  
  
 En basit koşul <xref:System.Windows.Automation.Condition.TrueCondition> , arama kapsamındaki tüm öğelerin döndürülüp döndürülmeyeceğini belirten önceden tanımlanmış bir nesnedir. <xref:System.Windows.Automation.Condition.FalseCondition>, ' ın <xref:System.Windows.Automation.Condition.TrueCondition> dönüştürüleyi, öğelerin değiştirilmesini önleyecağından daha az yararlıdır.  
  
 Önceden tanımlanmış üç koşul tek başına veya diğer koşullarla birlikte kullanılabilir: <xref:System.Windows.Automation.Automation.ContentViewCondition> , <xref:System.Windows.Automation.Automation.ControlViewCondition> , ve <xref:System.Windows.Automation.Automation.RawViewCondition> . <xref:System.Windows.Automation.Automation.RawViewCondition>, <xref:System.Windows.Automation.Condition.TrueCondition> öğeleri veya özelliklerine göre filtrelemediğinden kendisi tarafından kullanılan, öğesine eşdeğerdir <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> .  
  
 Diğer koşullar <xref:System.Windows.Automation.PropertyCondition> , her biri bir özellik değeri belirten bir veya daha fazla nesneden oluşturulmuştur. Örneğin, bir, <xref:System.Windows.Automation.PropertyCondition> öğesinin etkin olduğunu veya belirli bir denetim modelini desteklediğini belirtebilir.  
  
 Koşullar, ve türündeki nesneler oluşturarak Boolean Logic kullanılarak birleştirilebilir <xref:System.Windows.Automation.AndCondition> <xref:System.Windows.Automation.OrCondition> <xref:System.Windows.Automation.NotCondition> .  
  
<a name="Search_Scope"></a>
## <a name="search-scope"></a>Arama kapsamı  
 Veya kullanılarak gerçekleştirilen aramaların <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> <xref:System.Windows.Automation.AutomationElement.FindAll%2A> yanı sıra bir başlangıç yeri de olmalıdır.  
  
 Kapsam, Aranmak üzere başlangıç yeri etrafında yer alan alanı tanımlar. Bu, öğenin kendisini, onun eşdüzey öğelerini, üst öğelerini, alt öğelerini ve alt öğelerini içerebilir.  
  
 Bir aramanın kapsamı, Numaralandırmadaki değerlerin bit düzeyinde birleşimine göre tanımlanır <xref:System.Windows.Automation.TreeScope> .  
  
<a name="Finding_a_Known_Element"></a>
## <a name="finding-a-known-element"></a>Bilinen bir öğeyi bulma  
 , Ya da başka bir özellik ya da özelliklerin birleşimiyle tanımlanan bilinen bir öğeyi bulmak için <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A> <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AutomationId%2A> , yönteminin kullanılması en kolay yoldur <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> . Aranan öğe bir uygulama penceresuysa, aramanın başlangıç noktası olabilir <xref:System.Windows.Automation.AutomationElement.RootElement%2A> .  
  
 Öğeleri bulmanın bu yolu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , otomatikleştirilmiş test senaryolarında en yararlı seçenektir.  
  
<a name="Finding_Elements_in_a_Subtree"></a>
## <a name="finding-elements-in-a-subtree"></a>Alt ağaçtaki öğeleri bulma  
 Bilinen bir öğeyle ilgili belirli ölçütlere uyan tüm öğeleri bulmak için kullanabilirsiniz <xref:System.Windows.Automation.AutomationElement.FindAll%2A> . Örneğin, liste öğelerini veya menü öğelerini bir listeden veya menüden almak ya da bir iletişim kutusundaki tüm denetimleri tanımlamak için bu yöntemi kullanabilirsiniz.  
  
<a name="Walking_a_Subtree"></a>
## <a name="walking-a-subtree"></a>Alt ağaç yürüme  
 İstemcinizin ile birlikte kullanılabilecek uygulamalar hakkında daha önce bilginiz yoksa, sınıfını kullanarak ilgilendiğiniz tüm öğelerin bir alt ağacını oluşturabilirsiniz <xref:System.Windows.Automation.TreeWalker> . Uygulamanız bunu bir odak değişikliği olayına yanıt olarak gerektirebilir; Yani, bir uygulama veya denetim giriş odağını aldığında, UI Otomasyonu istemcisi alt öğeleri ve belki de odaklanmış öğenin tüm alt öğelerini inceler.  
  
 ' De kullanılabilecek başka bir yol, <xref:System.Windows.Automation.TreeWalker> bir öğenin üst öğelerinden birini tanımlamaktır. Örneğin, ağacı izleyerek bir denetimin üst penceresini belirleyebilirsiniz.  
  
 <xref:System.Windows.Automation.TreeWalker>Sınıfının bir nesnesini oluşturarak (bir ' a geçirerek ilgilendiğiniz öğeleri tanımlayarak <xref:System.Windows.Automation.Condition> ) ya da alanları olarak tanımlanan aşağıdaki önceden tanımlanmış nesnelerden birini kullanarak kullanabilirsiniz <xref:System.Windows.Automation.TreeWalker> .  
  
|||  
|-|-|  
|<xref:System.Windows.Automation.TreeWalker.ContentViewWalker>|Yalnızca özelliği olan öğeleri bulur <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> `true` .|  
|<xref:System.Windows.Automation.TreeWalker.ControlViewWalker>|Yalnızca özelliği olan öğeleri bulur <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> `true` .|  
|<xref:System.Windows.Automation.TreeWalker.RawViewWalker>|Tüm öğeleri bulur.|  
  
 Bir elde ettikten sonra <xref:System.Windows.Automation.TreeWalker> , kullanımı basittir. `Get`Alt ağacın öğeleri arasında gezinmek için yöntemleri çağırmanız yeterlidir.  
  
 <xref:System.Windows.Automation.TreeWalker.Normalize%2A>Yöntemi, alt ağaçtaki bir öğenin, görünümün parçası olmayan başka bir öğeden gezinmek için kullanılabilir. Örneğin, kullanarak bir alt ağacın görünümünü oluşturduğunuzu varsayalım <xref:System.Windows.Automation.TreeWalker.ContentViewWalker> . Uygulamanız daha sonra bir kaydırma çubuğunun giriş odağını aldığını belirten bir bildirim alır. Bir kaydırma çubuğu bir içerik öğesi olmadığından, alt ağacının görünümünde mevcut değildir. Ancak, <xref:System.Windows.Automation.AutomationElement> kaydırma çubuğunu temsil eder <xref:System.Windows.Automation.TreeWalker.Normalize%2A> ve içerik görünümündeki en yakın üst öğeye sahip olursunuz.  
  
<a name="Other_Ways_to_Retrieve_an_Element"></a>
## <a name="other-ways-to-retrieve-an-element"></a>Bir öğeyi almanın diğer yolları  
 Aramalara ve gezinmeye ek olarak, <xref:System.Windows.Automation.AutomationElement> aşağıdaki yollarla bir alabilirsiniz.  
  
### <a name="from-an-event"></a>Bir olaydan  
 Uygulamanız bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olay aldığında, olay işleyicinizde geçirilen kaynak nesne bir olur <xref:System.Windows.Automation.AutomationElement> . Örneğin, odak değiştirilen olaylara abone olduysa, içine geçirilen kaynak <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> odağı alan öğedir.  
  
 Daha fazla bilgi için bkz. [UI Otomasyon olaylarına abone olma](subscribe-to-ui-automation-events.md).  
  
### <a name="from-a-point"></a>Bir noktadan  
 Ekran koordinatlarına sahipseniz (örneğin, bir imleç konumu), <xref:System.Windows.Automation.AutomationElement> statik yöntemini kullanarak bir alabilirsiniz <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> .  
  
### <a name="from-a-window-handle"></a>Pencere tanıtıcısından  
 <xref:System.Windows.Automation.AutomationElement>HWND 'den almak için statik <xref:System.Windows.Automation.AutomationElement.FromHandle%2A> yöntemi kullanın.  
  
### <a name="from-the-focused-control"></a>Odaklanmış denetimden  
 <xref:System.Windows.Automation.AutomationElement>Statik özelliğinden odaklanmış denetimi temsil eden bir ' i alabilirsiniz <xref:System.Windows.Automation.AutomationElement.FocusedElement%2A> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Özellik Koşulunu Temel Alan UI Otomasyon Öğesi Bulma](find-a-ui-automation-element-based-on-a-property-condition.md)
- [TreeWalker ile UI Otomasyon Öğeleri Arasında Gezinme](navigate-among-ui-automation-elements-with-treewalker.md)
- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
