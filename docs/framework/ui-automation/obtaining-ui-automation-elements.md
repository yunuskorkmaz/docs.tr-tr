---
title: UI Otomasyon Öğelerini Alma
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, obtaining elements
- elements, UI Automation, obtaining
ms.assetid: c2caaf45-e59c-42a1-bc9b-77a6de520171
ms.openlocfilehash: eab4e59ee219808a4c0ae9ca5331a14928b66b5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179992"
---
# <a name="obtaining-ui-automation-elements"></a>UI Otomasyon Öğelerini Alma
> [!NOTE]
> Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır. Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu, öğeler için <xref:System.Windows.Automation.AutomationElement> [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] nesneleri elde etmenin çeşitli yollarını açıklar.  
  
> [!CAUTION]
> İstemci uygulamanız kendi kullanıcı arabiriminde öğeleri bulmaya [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] çalışırsa, tüm aramaları ayrı bir iş parçacığı üzerinde yapmalısınız. Daha fazla bilgi için [UI Automation Threading Issues'a](ui-automation-threading-issues.md)bakın.  
  
<a name="The_Root_Element"></a>
## <a name="root-element"></a>Kök Öğesi  
 <xref:System.Windows.Automation.AutomationElement> Nesnelerin tüm aramalarının bir başlangıç noktası olmalıdır. Bu, masaüstü, uygulama penceresi veya denetim de dahil olmak üzere herhangi bir öğe olabilir.  
  
 Tüm öğelerin alnındığı masaüstünün kök öğesi statik <xref:System.Windows.Automation.AutomationElement.RootElement%2A?displayProperty=nameWithType> özellikten elde edilir.  
  
> [!CAUTION]
> Genel olarak, sadece doğrudan çocuk elde <xref:System.Windows.Automation.AutomationElement.RootElement%2A>etmek için çalışmalısınız . Soyundan gelenler için yapılan bir arama, yüzlerce hatta binlerce öğeyi yineleyebilir ve bu da büyük olasılıkla bir yığın taşmasına neden olabilir. Belirli bir öğeyi daha düşük bir düzeyde elde etmeye çalışıyorsanız, aramanızı uygulama penceresinden veya daha düşük bir düzeydeki bir kapsayıcıdan başlamalısınız.  
  
<a name="Using_Conditions"></a>
## <a name="conditions"></a>Koşullar  
 Öğeleri almak [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] için kullanabileceğiniz çoğu teknik için, almak istediğiniz öğeleri tanımlayan bir ölçüt kümesi olan bir <xref:System.Windows.Automation.Condition>, bir belirtmeniz gerekir.  
  
 En basit koşul, arama kapsamı içindeki tüm öğelerin döndürüleceğini belirten önceden tanımlanmış bir nesnedir. <xref:System.Windows.Automation.Condition.TrueCondition> <xref:System.Windows.Automation.Condition.FalseCondition>, <xref:System.Windows.Automation.Condition.TrueCondition>tersi, daha az yararlıdır, herhangi bir öğe nin bulunmasını önleyeceği için.  
  
 Diğer üç önceden tanımlanmış koşullar tek başına veya <xref:System.Windows.Automation.Automation.ContentViewCondition>diğer <xref:System.Windows.Automation.Automation.ControlViewCondition>koşullarla birlikte kullanılabilir: , , ve <xref:System.Windows.Automation.Automation.RawViewCondition>. <xref:System.Windows.Automation.Automation.RawViewCondition>, kendi başına kullanılan, <xref:System.Windows.Automation.Condition.TrueCondition>kendi <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> veya <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> özellikleri tarafından öğeleri filtre değil, çünkü eşdeğerdir.  
  
 Diğer koşullar, her biri <xref:System.Windows.Automation.PropertyCondition> bir özellik değeri belirten bir veya daha fazla nesneden oluşturulur. Örneğin, bir <xref:System.Windows.Automation.PropertyCondition> öğenin etkin olduğunu veya belirli bir denetim deseni desteklediğini belirtebilir.  
  
 Koşullar boolean mantığı kullanılarak, türleri <xref:System.Windows.Automation.AndCondition> <xref:System.Windows.Automation.OrCondition>, ve <xref:System.Windows.Automation.NotCondition>.  
  
<a name="Search_Scope"></a>
## <a name="search-scope"></a>Arama Kapsamı  
 Kullanılarak <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> yapılan aramalarda <xref:System.Windows.Automation.AutomationElement.FindAll%2A> bir kapsam ve başlangıç yeri olması gerekir.  
  
 Kapsam, aranacak başlangıç noktasının etrafındaki alanı tanımlar. Bu öğenin kendisi, kardeşleri, ebeveyni, ataları, yakın çocukları ve soyundan içerebilir.  
  
 Aramanın kapsamı, numaralandırmadaki <xref:System.Windows.Automation.TreeScope> değerlerin bitwise birleşimi ile tanımlanır.  
  
<a name="Finding_a_Known_Element"></a>
## <a name="finding-a-known-element"></a>Bilinen Öğeyi Bulma  
 Bilinen bir öğeyi bulmak <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>için, onun tarafından tanımlanan , <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AutomationId%2A>veya başka bir özellik <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> veya özellikleri kombinasyonu, bu yöntemi kullanmak en kolay. Aranan öğe bir uygulama penceresi ise, aramanın başlangıç noktası <xref:System.Windows.Automation.AutomationElement.RootElement%2A>.  
  
 Öğeleri bulma [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bu şekilde en otomatik sınama senaryolarında yararlıdır.  
  
<a name="Finding_Elements_in_a_Subtree"></a>
## <a name="finding-elements-in-a-subtree"></a>Alt Ağaçta Öğeleri Bulma  
 Bilinen bir öğeyle ilişkili belirli ölçütleri karşılayan tüm <xref:System.Windows.Automation.AutomationElement.FindAll%2A>öğeleri bulmak için kullanabilirsiniz. Örneğin, liste öğelerini veya menü öğelerini bir listeden veya menüden almak veya iletişim kutusundaki tüm denetimleri tanımlamak için bu yöntemi kullanabilirsiniz.  
  
<a name="Walking_a_Subtree"></a>
## <a name="walking-a-subtree"></a>Bir Subtree Yürüyüş  
 İstemcinizin birlikte kullanılabileceği uygulamalar hakkında önceden bilginiz yoksa, <xref:System.Windows.Automation.TreeWalker> sınıfı kullanarak tüm ilgi çekici öğelerin bir alt ağacını oluşturabilirsiniz. Uygulamanız bunu odak değiştirilen bir olaya yanıt olarak yapabilir; diğer bir deyişle, bir uygulama veya denetim girdi odağı aldığında, Kullanıcı Aracı Otomasyon istemcisi çocukları ve belki de tüm odaklanmış öğenin torunlarını inceler.  
  
 <xref:System.Windows.Automation.TreeWalker> Kullanılabilen başka bir yol da bir öğenin atalarını tanımlamaktır. Örneğin, ağaca doğru yürüyerek denetimin üst penceresini tanımlayabilirsiniz.  
  
 Sınıfın bir <xref:System.Windows.Automation.TreeWalker> nesnesini oluşturarak (bir <xref:System.Windows.Automation.Condition>tane geçerek ilgi öğelerini tanımlayarak) veya <xref:System.Windows.Automation.TreeWalker>'nin alanları olarak tanımlanan aşağıdaki önceden tanımlanmış nesnelerden birini kullanarak) kullanabilirsiniz.  
  
|||  
|-|-|  
|<xref:System.Windows.Automation.TreeWalker.ContentViewWalker>|Yalnızca özelliği <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> olan `true`öğeleri bulur.|  
|<xref:System.Windows.Automation.TreeWalker.ControlViewWalker>|Yalnızca özelliği <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> olan `true`öğeleri bulur.|  
|<xref:System.Windows.Automation.TreeWalker.RawViewWalker>|Tüm öğeleri bulur.|  
  
 Bir elde ettikten <xref:System.Windows.Automation.TreeWalker>sonra , bunu kullanarak basittir. Alt ağacın `Get` öğeleri arasında gezinmek için yöntemleri aramanız yeterlidir.  
  
 Yöntem, <xref:System.Windows.Automation.TreeWalker.Normalize%2A> görünümün bir parçası olmayan başka bir öğeden alt ağaçtaki bir öğeye gezinmek için kullanılabilir. Örneğin, bir alt ağacın görünümünü kullanarak <xref:System.Windows.Automation.TreeWalker.ContentViewWalker>oluşturduğunuzu varsayalım. Uygulamanız daha sonra bir kaydırma çubuğunun giriş odağı aldığına dair bildirim alır. Kaydırma çubuğu bir içerik öğesi olmadığından, alt ağacı görünümünüzde bulunmaz. Ancak, <xref:System.Windows.Automation.AutomationElement> kaydırma çubuğunu temsil edeni <xref:System.Windows.Automation.TreeWalker.Normalize%2A> geçirebilir ve içerik görünümünde bulunan en yakın atayı alabilirsiniz.  
  
<a name="Other_Ways_to_Retrieve_an_Element"></a>
## <a name="other-ways-to-retrieve-an-element"></a>Öğe Almanın Diğer Yolları  
 Aramalar avesi ve gezinmeye <xref:System.Windows.Automation.AutomationElement> ek olarak, aşağıdaki yollarla bir alabilirsiniz.  
  
### <a name="from-an-event"></a>Bir Etkinlikten  
 Uygulamanız bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olay aldığında, olay işleyicinize geçen <xref:System.Windows.Automation.AutomationElement>kaynak nesne bir . Örneğin, odak değiştirilen olaylara abone olduysanız, size <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> geçen kaynak odağı alan öğedir.  
  
 Daha fazla bilgi için [bkz.](subscribe-to-ui-automation-events.md)  
  
### <a name="from-a-point"></a>Bir Noktadan  
 Ekran koordinatlarınız (örneğin, imleç konumu) varsa, statik <xref:System.Windows.Automation.AutomationElement> <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> yöntemi kullanarak bir tane alabilirsiniz.  
  
### <a name="from-a-window-handle"></a>Pencere Tutamacından  
 BIR HWND'den bir alma <xref:System.Windows.Automation.AutomationElement> <xref:System.Windows.Automation.AutomationElement.FromHandle%2A> yöntemini kullanın.  
  
### <a name="from-the-focused-control"></a>Odaklanmış Kontrol'den  
 Statik <xref:System.Windows.Automation.AutomationElement.FocusedElement%2A> özellikten <xref:System.Windows.Automation.AutomationElement> odaklanmış denetimi temsil eden bir şey alabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Özellik Koşulunu Temel Alan UI Otomasyon Öğesi Bulma](find-a-ui-automation-element-based-on-a-property-condition.md)
- [TreeWalker ile UI Otomasyon Öğeleri Arasında Gezinme](navigate-among-ui-automation-elements-with-treewalker.md)
- [UI Otomasyon Ağacına Genel Bakış](ui-automation-tree-overview.md)
