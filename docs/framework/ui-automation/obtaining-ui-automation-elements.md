---
title: UI Otomasyon Öğelerini Alma
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, obtaining elements
- elements, UI Automation, obtaining
ms.assetid: c2caaf45-e59c-42a1-bc9b-77a6de520171
ms.openlocfilehash: 0ae4694e2efb6f6c51b279adf2851baf38785c8b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446891"
---
# <a name="obtaining-ui-automation-elements"></a>UI Otomasyon Öğelerini Alma
> [!NOTE]
> Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu, [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] öğeleri için <xref:System.Windows.Automation.AutomationElement> nesneleri almanın çeşitli yollarını açıklamaktadır.  
  
> [!CAUTION]
> İstemci uygulamanız kendi Kullanıcı arabirimindeki öğeleri bulmaya çalışıyorsa, tüm [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] çağrılarını ayrı bir iş parçacığında yapmanız gerekir. Daha fazla bilgi için bkz. [UI Otomasyonu Iş parçacığı sorunları](ui-automation-threading-issues.md).  
  
<a name="The_Root_Element"></a>   
## <a name="root-element"></a>Kök öğe  
 <xref:System.Windows.Automation.AutomationElement> nesneleri için tüm aramalar bir başlangıç yerinde olmalıdır. Bu, Masaüstü, uygulama penceresi veya denetim dahil olmak üzere herhangi bir öğe olabilir.  
  
 Tüm öğelerin alt öğesi olduğu, statik <xref:System.Windows.Automation.AutomationElement.RootElement%2A?displayProperty=nameWithType> özelliğinden alınan Masaüstü için kök öğe.  
  
> [!CAUTION]
> Genel olarak, <xref:System.Windows.Automation.AutomationElement.RootElement%2A>yalnızca doğrudan alt öğelerini almaya çalışırsınız. Alt öğeler için arama yüzlerce veya hatta binlerce öğe aracılığıyla yineleyebilir ve muhtemelen yığın taşmasına neden olabilir. Daha düşük bir düzeyde belirli bir öğe edinmeye çalışıyorsanız, aramanızı uygulama penceresinden veya bir kapsayıcıdan daha düşük bir düzeyde başlatmanız gerekir.  
  
<a name="Using_Conditions"></a>   
## <a name="conditions"></a>Koşullar  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] öğelerini almak için kullanabileceğiniz çoğu teknik için, almak istediğiniz öğeleri tanımlayan bir ölçüt kümesi olan bir <xref:System.Windows.Automation.Condition>belirtmeniz gerekir.  
  
 En basit koşul <xref:System.Windows.Automation.Condition.TrueCondition>, arama kapsamındaki tüm öğelerin döndürülüp döndürülmeyeceğini belirten önceden tanımlanmış bir nesnedir. <xref:System.Windows.Automation.Condition.FalseCondition>, tüm öğelerin bulunmasını önleyecağından, <xref:System.Windows.Automation.Condition.TrueCondition>dönüştürmesi daha az yararlıdır.  
  
 Önceden tanımlanmış üç koşul, tek başına veya diğer koşullarla birlikte kullanılabilir: <xref:System.Windows.Automation.Automation.ContentViewCondition>, <xref:System.Windows.Automation.Automation.ControlViewCondition>ve <xref:System.Windows.Automation.Automation.RawViewCondition>. <xref:System.Windows.Automation.Automation.RawViewCondition>, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> veya <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> özelliklerine göre filtrelemediğinden, kendisi tarafından kullanılan <xref:System.Windows.Automation.Condition.TrueCondition>eşdeğerdir.  
  
 Diğer koşullar, her biri bir özellik değeri belirten bir veya daha fazla <xref:System.Windows.Automation.PropertyCondition> nesnesinden oluşturulmuştur. Örneğin, bir <xref:System.Windows.Automation.PropertyCondition> öğenin etkinleştirildiğini veya belirli bir denetim modelini desteklediğini belirtebilir.  
  
 Koşullar, <xref:System.Windows.Automation.AndCondition>, <xref:System.Windows.Automation.OrCondition>ve <xref:System.Windows.Automation.NotCondition>türlerin nesneleri oluşturarak Boolean Logic kullanılarak birleştirilebilir.  
  
<a name="Search_Scope"></a>   
## <a name="search-scope"></a>Arama kapsamı  
 <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> veya <xref:System.Windows.Automation.AutomationElement.FindAll%2A> kullanılarak gerçekleştirilen aramaların bir kapsamı ve bir başlangıç yerinde olması gerekir.  
  
 Kapsam, Aranmak üzere başlangıç yeri etrafında yer alan alanı tanımlar. Bu, öğenin kendisini, onun eşdüzey öğelerini, üst öğelerini, alt öğelerini ve alt öğelerini içerebilir.  
  
 Bir aramanın kapsamı, <xref:System.Windows.Automation.TreeScope> numaralandırmasından bir bit düzeyinde Değerler birleşimi tarafından tanımlanır.  
  
<a name="Finding_a_Known_Element"></a>   
## <a name="finding-a-known-element"></a>Bilinen bir öğeyi bulma  
 <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AutomationId%2A>veya başka bir özellik ya da özelliklerin birleşimiyle tanımlanan bilinen bir öğeyi bulmak için <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> yönteminin kullanılması en kolay yoldur. Aranan öğe bir uygulama penceresuysa, aramanın başlangıç noktası <xref:System.Windows.Automation.AutomationElement.RootElement%2A>olabilir.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] öğeleri bulmanın bu yolu, otomatikleştirilmiş test senaryolarında en yararlı seçenektir.  
  
<a name="Finding_Elements_in_a_Subtree"></a>   
## <a name="finding-elements-in-a-subtree"></a>Alt ağaçtaki öğeleri bulma  
 Bilinen bir öğeyle ilgili belirli ölçütlere uyan tüm öğeleri bulmak için <xref:System.Windows.Automation.AutomationElement.FindAll%2A>kullanabilirsiniz. Örneğin, liste öğelerini veya menü öğelerini bir listeden veya menüden almak ya da bir iletişim kutusundaki tüm denetimleri tanımlamak için bu yöntemi kullanabilirsiniz.  
  
<a name="Walking_a_Subtree"></a>   
## <a name="walking-a-subtree"></a>Alt ağaç yürüme  
 İstemcinizin ile birlikte kullanılabilecek uygulamalar hakkında daha önce bilginiz yoksa, <xref:System.Windows.Automation.TreeWalker> sınıfını kullanarak ilgilendiğiniz tüm öğelerin bir alt ağacını oluşturabilirsiniz. Uygulamanız bunu bir odak değişikliği olayına yanıt olarak gerektirebilir; Yani, bir uygulama veya denetim giriş odağını aldığında, UI Otomasyonu istemcisi alt öğeleri ve belki de odaklanmış öğenin tüm alt öğelerini inceler.  
  
 <xref:System.Windows.Automation.TreeWalker> kullanılabilecek başka bir yol da bir öğenin üst öğelerinden birini tanımlamaktır. Örneğin, ağacı izleyerek bir denetimin üst penceresini belirleyebilirsiniz.  
  
 <xref:System.Windows.Automation.TreeWalker>, sınıfın bir nesnesini oluşturarak (bir <xref:System.Windows.Automation.Condition>geçirerek ilgilendiğiniz öğeleri tanımlayarak) veya <xref:System.Windows.Automation.TreeWalker>alanları olarak tanımlanan aşağıdaki önceden tanımlanmış nesnelerden birini kullanarak kullanabilirsiniz.  
  
|||  
|-|-|  
|<xref:System.Windows.Automation.TreeWalker.ContentViewWalker>|Yalnızca <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> özelliği `true`olan öğeleri bulur.|  
|<xref:System.Windows.Automation.TreeWalker.ControlViewWalker>|Yalnızca <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> özelliği `true`olan öğeleri bulur.|  
|<xref:System.Windows.Automation.TreeWalker.RawViewWalker>|Tüm öğeleri bulur.|  
  
 Bir <xref:System.Windows.Automation.TreeWalker>elde ettikten sonra, kullanımı basittir. Alt ağacın öğeleri arasında gezinmek için `Get` yöntemlerini çağırmanız yeterlidir.  
  
 <xref:System.Windows.Automation.TreeWalker.Normalize%2A> yöntemi, alt ağaçtaki bir öğeye, görünümün parçası olmayan başka bir öğeden gitmek için kullanılabilir. Örneğin, <xref:System.Windows.Automation.TreeWalker.ContentViewWalker>kullanarak bir alt ağacın görünümünü oluşturduğunuzu varsayalım. Uygulamanız daha sonra bir kaydırma çubuğunun giriş odağını aldığını belirten bir bildirim alır. Bir kaydırma çubuğu bir içerik öğesi olmadığından, alt ağacının görünümünde mevcut değildir. Ancak, kaydırma <xref:System.Windows.Automation.TreeWalker.Normalize%2A> çubuğunu temsil eden <xref:System.Windows.Automation.AutomationElement> geçirebilir ve içerik görünümündeki en yakın üst öğeye sahip olabilirsiniz.  
  
<a name="Other_Ways_to_Retrieve_an_Element"></a>   
## <a name="other-ways-to-retrieve-an-element"></a>Bir öğeyi almanın diğer yolları  
 Aramalara ve gezinmeye ek olarak, aşağıdaki yollarla bir <xref:System.Windows.Automation.AutomationElement> alabilirsiniz.  
  
### <a name="from-an-event"></a>Bir olaydan  
 Uygulamanız bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayı aldığında, olay işleyicinizde geçirilen kaynak nesne bir <xref:System.Windows.Automation.AutomationElement>. Örneğin, odak değiştirilen olaylara abone olduysa, <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> geçirilen kaynak odağı alan öğedir.  
  
 Daha fazla bilgi için bkz. [UI Otomasyon olaylarına abone olma](subscribe-to-ui-automation-events.md).  
  
### <a name="from-a-point"></a>Bir noktadan  
 Ekran koordinatlarına sahipseniz (örneğin, bir imleç konumu), statik <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> metodunu kullanarak bir <xref:System.Windows.Automation.AutomationElement> alabilirsiniz.  
  
### <a name="from-a-window-handle"></a>Pencere tanıtıcısından  
 HWND 'den bir <xref:System.Windows.Automation.AutomationElement> almak için statik <xref:System.Windows.Automation.AutomationElement.FromHandle%2A> yöntemini kullanın.  
  
### <a name="from-the-focused-control"></a>Odaklanmış denetimden  
 Statik <xref:System.Windows.Automation.AutomationElement.FocusedElement%2A> özelliğinden odaklanmış denetimi temsil eden bir <xref:System.Windows.Automation.AutomationElement> alabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Özellik Koşulunu Temel Alan UI Otomasyonu Öğesi Bulma](find-a-ui-automation-element-based-on-a-property-condition.md)
- [TreeWalker ile UI Otomasyonu Öğeleri Arasında Gezinme](navigate-among-ui-automation-elements-with-treewalker.md)
- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
