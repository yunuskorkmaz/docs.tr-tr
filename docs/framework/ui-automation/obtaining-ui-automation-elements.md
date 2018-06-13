---
title: UI Otomasyon Öğelerini Alma
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, obtaining elements
- elements, UI Automation, obtaining
ms.assetid: c2caaf45-e59c-42a1-bc9b-77a6de520171
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 3e700e7e726b5cb71d3b7d863bdb31951aacd885
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33399214"
---
# <a name="obtaining-ui-automation-elements"></a>UI Otomasyon Öğelerini Alma
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu almanın çeşitli yollarını açıklar <xref:System.Windows.Automation.AutomationElement> için nesneleri [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] öğeleri.  
  
> [!CAUTION]
>  İstemci uygulamanız kendi kullanıcı arabirimi öğeleri bulmak deneyebilir gerekirse, tüm yapmanız gereken [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ayrı bir iş parçacığı üzerinde çağırır. Daha fazla bilgi için bkz: [UI Otomasyon iş parçacığı oluşturma sorunları](../../../docs/framework/ui-automation/ui-automation-threading-issues.md).  
  
<a name="The_Root_Element"></a>   
## <a name="root-element"></a>Kök öğesi  
 Tüm arar <xref:System.Windows.Automation.AutomationElement> nesneleri başlatma yerinde olması gerekir. Bu Masaüstü, bir uygulama penceresi veya bir denetimi dahil olmak üzere herhangi bir öğe olabilir.  
  
 İçinden tüm öğeleri descended, masaüstü, kök öğe statik elde <xref:System.Windows.Automation.AutomationElement.RootElement%2A?displayProperty=nameWithType> özelliği.  
  
> [!CAUTION]
>  Genel olarak, sadece doğrudan alt edinme denemelisiniz <xref:System.Windows.Automation.AutomationElement.RootElement%2A>. Alt öğeleri için bir arama yüzlerce veya binlerce büyük olasılıkla bir yığın taşması kaynaklanan öğelerinin bile yinelemek. Belirli bir öğenin alt düzeyde edinme çalışıyorsanız, Uygulama penceresinden veya daha düşük düzeydeki bir kapsayıcı aramanızı başlamanız gerekir.  
  
<a name="Using_Conditions"></a>   
## <a name="conditions"></a>Koşullar  
 Çoğu teknikleri almak için kullanabileceğiniz [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] öğeleri belirtmelisiniz. bir <xref:System.Windows.Automation.Condition>, almak istediğiniz hangi öğelerin tanımlama ölçüt olduğu.  
  
 En basit koşul <xref:System.Windows.Automation.Condition.TrueCondition>, arama kapsamı içindeki tüm öğeler döndürülecek olan belirtme önceden tanımlanmış bir nesne. <xref:System.Windows.Automation.Condition.FalseCondition>, ters, <xref:System.Windows.Automation.Condition.TrueCondition>, herhangi bir öğe bulundu gelen önleyen gibi daha az yararlı olur.  
  
 Üç önceden tanımlanmış koşullara tek başına veya diğer koşullar ile birlikte kullanılabilir: <xref:System.Windows.Automation.Automation.ContentViewCondition>, <xref:System.Windows.Automation.Automation.ControlViewCondition>, ve <xref:System.Windows.Automation.Automation.RawViewCondition>. <xref:System.Windows.Automation.Automation.RawViewCondition>, tek başına kullanılan, eşdeğer olan <xref:System.Windows.Automation.Condition.TrueCondition>öğeleri tarafından filtre değil çünkü bunların <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> veya <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> özellikleri.  
  
 Diğer koşullar bir veya daha fazla yerleşik olan <xref:System.Windows.Automation.PropertyCondition> nesneleri, her biri bir özellik değeri belirtir. Örneğin, bir <xref:System.Windows.Automation.PropertyCondition> öğesi etkin olduğunu veya belirli bir denetim düzenini destekler belirtebilir.  
  
 Koşullar türden nesneler oluşturarak Boolean mantığı kullanılarak birleştirilebilir <xref:System.Windows.Automation.AndCondition>, <xref:System.Windows.Automation.OrCondition>, ve <xref:System.Windows.Automation.NotCondition>.  
  
<a name="Search_Scope"></a>   
## <a name="search-scope"></a>Arama kapsamı  
 Kullanılarak yapılan arama <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> veya <xref:System.Windows.Automation.AutomationElement.FindAll%2A> başlangıç yeri yanı sıra bir kapsamı olmalıdır.  
  
 Kapsam başlangıç aranacak olan yerinde boşluk tanımlar. Bu öğe, eşdüzey, kendi üst, alt öğelerinden, hemen alt ve alt öğeleri içerebilir.  
  
 Arama kapsamı değerlerin Bitsel bir birleşimi tarafından tanımlanan <xref:System.Windows.Automation.TreeScope> numaralandırması.  
  
<a name="Finding_a_Known_Element"></a>   
## <a name="finding-a-known-element"></a>Bilinen bir öğesi bulma  
 Tarafından tanımlanan bilinen bir öğeyi bulmak için kendi <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AutomationId%2A>, ya da diğer bazı özellik veya özellikleri birleşimi, kullanılacak kolay <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> yöntemi. Aranan öğesi bir uygulama penceresi ise, başlangıç noktası arama olabilir <xref:System.Windows.Automation.AutomationElement.RootElement%2A>.  
  
 Bulma, bu şekilde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] öğeleri otomatikleştirilmiş test senaryolarda en yararlı.  
  
<a name="Finding_Elements_in_a_Subtree"></a>   
## <a name="finding-elements-in-a-subtree"></a>Bir alt ağacı öğeleri bulma  
 Bilinen bir öğeye ilgili belirli bir ölçüte toplantı tüm öğeleri bulmak için kullanabileceğiniz <xref:System.Windows.Automation.AutomationElement.FindAll%2A>. Örneğin, liste öğelerini veya menü öğelerini bir liste veya menü almak veya bir iletişim kutusu içindeki tüm denetimler belirlemek için bu yöntemi kullanabilirsiniz.  
  
<a name="Walking_a_Subtree"></a>   
## <a name="walking-a-subtree"></a>Bir alt ağacı taramasını  
 Önceki istemci ile kullanılabilir uygulamalar olanağıyla varsa, kullanarak ilgilendiğiniz tüm öğeler bir alt ağacı oluşturabileceğiniz <xref:System.Windows.Automation.TreeWalker> sınıfı. Uygulamanızı odak değiştirilmiş bir olaya yanıt olarak bunu yapabilirsiniz; diğer bir deyişle, bir uygulama veya denetim giriş odağını aldığında, UI Otomasyonu istemci alt ve belki de tüm alt odaklanılan öğeyi inceler.  
  
 Başka bir yolla <xref:System.Windows.Automation.TreeWalker> kullanılabilir üst öğenin öğelerinin belirlemektir. Örneğin, bu ağaca adım adım ilerlemenizi sağlayarak bir denetimin üst pencere tanımlayabilirsiniz.  
  
 Kullanabileceğiniz <xref:System.Windows.Automation.TreeWalker> sınıfın bir nesnesi oluşturarak ya da (geçirerek ilgi öğelerini tanımlama bir <xref:System.Windows.Automation.Condition>), ya da aşağıdakilerden birini kullanarak alanları olarak tanımlanan nesneler önceden <xref:System.Windows.Automation.TreeWalker>.  
  
|||  
|-|-|  
|<xref:System.Windows.Automation.TreeWalker.ContentViewWalker>|Yalnızca öğeleri bulur, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A> özelliği `true`.|  
|<xref:System.Windows.Automation.TreeWalker.ControlViewWalker>|Yalnızca öğeleri bulur, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A> özelliği `true`.|  
|<xref:System.Windows.Automation.TreeWalker.RawViewWalker>|Tüm öğeleri bulur.|  
  
 Elde ettikten sonra bir <xref:System.Windows.Automation.TreeWalker>, bunu kullanarak basit. Basit Arama `Get` alt öğeler arasında gezinmek için yöntemleri.  
  
 <xref:System.Windows.Automation.TreeWalker.Normalize%2A> Yöntemi, bir öğeye ağaçtaki görünüme parçası olmayan başka bir öğeden gezinmek için kullanılabilir. Örneğin, oluşturduğunuz bir alt ağaç görünümünü kullanarak varsayalım <xref:System.Windows.Automation.TreeWalker.ContentViewWalker>. Ardından, uygulamanızın bir kaydırma çubuğunun giriş odağını aldı bildirimi alır. Bir kaydırma çubuğunun içerik öğesi olmadığından alt ağacı görünümünüzde mevcut değil. Ancak, geçirebilirsiniz <xref:System.Windows.Automation.AutomationElement> kaydırma çubuğuna temsil eden <xref:System.Windows.Automation.TreeWalker.Normalize%2A> ve içerik görünümünde olan en yakın üst öğede alır.  
  
<a name="Other_Ways_to_Retrieve_an_Element"></a>   
## <a name="other-ways-to-retrieve-an-element"></a>Bir öğenin almanın diğer yolları  
 Aramaları ve gezinti ek olarak, alabileceğiniz bir <xref:System.Windows.Automation.AutomationElement> aşağıdaki yollarla.  
  
### <a name="from-an-event"></a>Bir olay  
 Uygulamanızın ne zaman alan bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olaydır, olay işleyicisine geçirilen kaynak nesnesi bir <xref:System.Windows.Automation.AutomationElement>. Odağı değiştirilen olaylarına abone, örneğin, kaynak için geçirilen, <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> odağı alınan öğedir.  
  
 Daha fazla bilgi için bkz: [UI Otomasyon olaylarına abone](../../../docs/framework/ui-automation/subscribe-to-ui-automation-events.md).  
  
### <a name="from-a-point"></a>Bir noktadan  
 Ekran koordinatları (örneğin, bir imleç konumu) varsa, alabileceğiniz bir <xref:System.Windows.Automation.AutomationElement> statik kullanarak <xref:System.Windows.Automation.AutomationElement.FromPoint%2A> yöntemi.  
  
### <a name="from-a-window-handle"></a>Bir pencere tanıtıcının  
 Alınacak bir <xref:System.Windows.Automation.AutomationElement> statik bir HWND'den kullanmak <xref:System.Windows.Automation.AutomationElement.FromHandle%2A> yöntemi.  
  
### <a name="from-the-focused-control"></a>Odaklanmış denetiminden  
 Alabileceğiniz bir <xref:System.Windows.Automation.AutomationElement> odaklı denetimin statik temsil eden <xref:System.Windows.Automation.AutomationElement.FocusedElement%2A> özelliği.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özellik Koşulunu Temel Alan UI Otomasyonu Öğesi Bulma](../../../docs/framework/ui-automation/find-a-ui-automation-element-based-on-a-property-condition.md)  
 [TreeWalker ile UI Otomasyonu Öğeleri Arasında Gezinme](../../../docs/framework/ui-automation/navigate-among-ui-automation-elements-with-treewalker.md)  
 [UI Otomasyon Ağacına Genel Bakış](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
