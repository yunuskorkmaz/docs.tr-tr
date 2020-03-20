---
title: UI Otomasyonda Önbelleğe Alma
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation caching in clients
- caching, UI Automation clients
ms.assetid: 94c15031-4975-43cc-bcd5-c9439ed21c9c
ms.openlocfilehash: 186ed77594aadab9e3f49ef30e559e159aee1b60
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180283"
---
# <a name="caching-in-ui-automation-clients"></a>UI Otomasyonda Önbelleğe Alma
> [!NOTE]
> Bu dokümantasyon, ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıfları kullanmak <xref:System.Windows.Automation> isteyen .NET Framework geliştiricileri için tasarlanmıştır. Hakkında en son [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]bilgi için [Bkz. Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu özellikleri ve [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] denetim desenleri önbelleğe getirin.  
  
 In [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], önbelleğe alma veri ön alma anlamına gelir. Verilere daha sonra daha fazla çapraz işlem iletişimi olmadan erişilebilir. Önbelleğe alma genellikle Kullanıcı Birleşik UI Automation istemci sürücü uygulamaları tarafından özellikleri ve denetim desenleri toplu olarak almak için kullanılır. Bilgiler daha sonra gerektiğinde önbellekten alınır. Uygulama, genellikle önbelleği, genellikle bir şeyin [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] değiştiğini gösteren olaylara yanıt olarak düzenli olarak güncelleştirir.  
  
 Önbelleğe almanın yararları en çok Windows Presentation Foundation (WPF) denetimleri ve sunucu tarafındaki Kullanıcı Arabirimi Otomasyon sağlayıcılarına sahip özel denetimlerde fark edilir. Win32 denetimleri için varsayılan sağlayıcılar gibi istemci tarafındaki sağlayıcılara erişirken daha az avantaj elde edilir.  
  
 Önbelleğe alma, uygulama a'yı <xref:System.Windows.Automation.CacheRequest> etkinleştirdiğinde ve sonra <xref:System.Windows.Automation.AutomationElement>bir yöntem veya özellik kullandığında oluşur; örneğin, <xref:System.Windows.Automation.AutomationElement.FindFirst%2A>. <xref:System.Windows.Automation.AutomationElement.FindAll%2A> <xref:System.Windows.Automation.TreeWalker> Sınıfın yöntemleri bir istisnadır; önbelleğe alma yalnızca <xref:System.Windows.Automation.CacheRequest> a parametresi olarak belirtilirse (örneğin, <xref:System.Windows.Automation.TreeWalker.GetFirstChild%28System.Windows.Automation.AutomationElement%2CSystem.Windows.Automation.CacheRequest%29?displayProperty=nameWithType>.  
  
 Önbelleğe alma, bir <xref:System.Windows.Automation.CacheRequest> olaya abone olduğunuzda da oluşur. Bir <xref:System.Windows.Automation.AutomationElement> olayın kaynağı olarak olay işleyicinize geçirilen önbelleğe alınmış özellikleri ve <xref:System.Windows.Automation.CacheRequest>desenleri özgün tarafından belirtilen içerir. Etkinliğe abone <xref:System.Windows.Automation.CacheRequest> olduktan sonra yapılan değişikliklerin hiçbir etkisi yoktur.  
  
 Bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] öğenin özellikleri ve denetim desenleri önbelleğe alınabilir.  
  
<a name="Options_for_Caching"></a>
## <a name="options-for-caching"></a>Önbelleğe Alma Seçenekleri  
 Önbelleğe <xref:System.Windows.Automation.CacheRequest> alma için aşağıdaki seçenekleri belirtir.  
  
<a name="Properties_to_Cache"></a>
### <a name="properties-to-cache"></a>Önbellek özellikleri  
 İsteği etkinleştirmeden önce <xref:System.Windows.Automation.CacheRequest.Add%28System.Windows.Automation.AutomationProperty%29> her özellik için çağrıda bulunarak önbelleğe özellikleri belirtebilirsiniz.  
  
<a name="Control_Patterns_to_Cache"></a>
### <a name="control-patterns-to-cache"></a>Önbelleğe Denetim Desenleri  
 İsteği etkinleştirmeden önce her <xref:System.Windows.Automation.CacheRequest.Add%28System.Windows.Automation.AutomationPattern%29> desen için çağrıda bulunarak önbelleğe almak için denetim desenleri belirtebilirsiniz. Bir desen önbelleğe alındığunda, özellikleri otomatik olarak önbelleğe alınmaz; kullanarak <xref:System.Windows.Automation.CacheRequest.Add%2A?displayProperty=nameWithType>önbelleğe alınmasını istediğiniz özellikleri belirtmeniz gerekir.  
  
<a name="Scope_of_the_Caching"></a>
### <a name="scope-and-filtering-of-caching"></a>Önbelleğe Alma kapsamı ve Filtreleme  
 İsteği etkinleştirmeden önce <xref:System.Windows.Automation.CacheRequest.TreeScope%2A?displayProperty=nameWithType> özelliği ayarlayarak önbelleğe almak istediğiniz öğeleri ve desenleri belirtebilirsiniz. Kapsam, istek etkinken alınan öğelerle görecelidir. Örneğin, yalnızca <xref:System.Windows.Automation.TreeScope.Children>, ve sonra bir <xref:System.Windows.Automation.AutomationElement>, bu öğenin çocukların özellikleri ve desenleri alırsanız önbelleğe alınır, ancak öğenin kendisi değil. Önbelleğe alma özelliğinin kendisi için yapıldığından emin <xref:System.Windows.Automation.TreeScope.Element> olmak <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> için, özelliğe eklemeniz gerekir. Kapsamı ayarlamak mümkün değildir <xref:System.Windows.Automation.TreeScope.Parent> veya <xref:System.Windows.Automation.TreeScope.Ancestors>. Ancak, bir alt öğe önbelleğe alındığında bir üst öğe önbelleğe alınabilir; bkz. Önbelleğe Alınmış Çocuk ve Ebeveynleri bu konuda alma.  
  
 Önbelleğe alma nın boyutu <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A?displayProperty=nameWithType> da özellikten etkilenir. Varsayılan olarak, önbelleğe alma yalnızca [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacın denetim görünümünde görünen öğeler için gerçekleştirilir. Ancak, önbelleğe alma özelliğini tüm öğelere veya yalnızca içerik görünümünde görünen öğelere uygulamak için değiştirebilirsiniz.  
  
<a name="Strength_of_the_Element_References"></a>
### <a name="strength-of-the-element-references"></a>Element Referanslarının Gücü  
 Bir <xref:System.Windows.Automation.AutomationElement>, varsayılan olarak aldığınızda, önbelleğe alınmamış olanlar da dahil olmak üzere, bu öğenin tüm özelliklerine ve desenlerine erişebilirsiniz. Ancak, daha fazla verimlilik için öğeye yapılan başvurunun yalnızca önbelleğe <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> alınmış verileri <xref:System.Windows.Automation.CacheRequest> <xref:System.Windows.Automation.AutomationElementMode.None>ifade ettiğini belirtebilirsiniz. Bu durumda, önbelleğe alınmayan özelliklere ve alınan öğelerin desenlerine erişiminiz yoktur. Bu, herhangi bir özelliğe <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> veya `Current` herhangi <xref:System.Windows.Automation.AutomationElement> bir denetim deseninin özelliğine erişemeyeceğiniz anlamına gelir; ne de kullanarak <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> bir desen <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A>alabilirsiniz ya da . Önbelleğe alınan desenlerde, dizi özelliklerini alan, <xref:System.Windows.Automation.SelectionPattern.SelectionPatternInformation.GetSelection%2A?displayProperty=nameWithType>ancak denetimde <xref:System.Windows.Automation.InvokePattern.Invoke%2A?displayProperty=nameWithType>eylem gerçekleştiren yöntemleri çağıramazsınız.  
  
 Nesnelere tam başvuru gerekmeyen bir uygulama örneği, bir penceredeki <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A> öğelerin <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> ve özelliklerinin önceden alınıp, nesnelerin kendilerine ihtiyaç duymayacağı <xref:System.Windows.Automation.AutomationElement> bir ekran okuyucudur.  
  
<a name="Activating_the_CacheRequest"></a>
## <a name="activating-the-cacherequest"></a>Önbellek İsteğini Etkinleştirme  
 Önbelleğe alma <xref:System.Windows.Automation.AutomationElement> işlemi yalnızca geçerli iş <xref:System.Windows.Automation.CacheRequest> parçacığı için etkin iken nesneler alınırken gerçekleştirilir. Bir <xref:System.Windows.Automation.CacheRequest>' yi etkinleştirmenin iki yolu vardır.  
  
 Her zamanki gibi <xref:System.Windows.Automation.CacheRequest.Activate%2A>aramaktır. Bu yöntem, uygulayan bir <xref:System.IDisposable>nesne döndürür. <xref:System.IDisposable> Nesne var olduğu sürece istek etkin kalır. Nesnenin kullanım ömrünü denetlemenin en kolay yolu, aramayı `using` (C#) `Using` veya (Visual Basic) bloğuna içine almaktır. Bu, bir özel durum yükseltilse bile isteğin yığından atılmasını sağlar.  
  
 Önbellek isteklerini yuvalamak istediğinizde yararlı olan başka <xref:System.Windows.Automation.CacheRequest.Push%2A>bir yol da. Bu, isteği bir yığına koyar ve etkinleştirir. İstek, yığından kaldırılına kadar etkin <xref:System.Windows.Automation.CacheRequest.Pop%2A>kalır. Başka bir istek yığına itilirse istek geçici olarak etkin değil olur; yığındaki yalnızca üst istek etkindir.  
  
<a name="Retrieving_Cached_Properties"></a>
## <a name="retrieving-cached-properties"></a>Önbelleğe Alınmış Özellikleri Alma  
 Aşağıdaki yöntemler ve özellikler aracılığıyla bir öğenin önbelleğe alınmış özelliklerini alabilirsiniz.  
  
- <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.Cached%2A>  
  
 İstenen özellik önbellekte değilse bir özel durum yükseltilir.  
  
 <xref:System.Windows.Automation.AutomationElement.Cached%2A>, <xref:System.Windows.Automation.AutomationElement.Current%2A>gibi, bir yapının üyeleri olarak tek tek özellikleri ortaya çıkarır. Ancak, bu yapıyı almanız gerekmez; tek tek özelliklere doğrudan erişebilirsiniz. Örneğin, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A> özellik elde edilebilir `element.Cached.Name`, `element` nerede <xref:System.Windows.Automation.AutomationElement>bir .  
  
<a name="Retrieving_Cached_Control_Patterns"></a>
## <a name="retrieving-cached-control-patterns"></a>Önbelleğe Alınmış Kontrol Desenlerini Alma  
 Aşağıdaki yöntemlerle bir öğenin önbelleğe alınmış denetim desenleri alabilirsiniz.  
  
- <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A>  
  
 Desen önbellekte değilse, <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> bir özel durum <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> yükseltir `false`ve döndürür.  
  
 Desen nesnesinin `Cached` özelliğini kullanarak bir denetim deseninin önbelleğe alınmış özelliklerini alabilirsiniz. Ayrıca, yalnızca ne zaman `Current` <xref:System.Windows.Automation.AutomationElementMode.None> <xref:System.Windows.Automation.AutomationElement> alındığı belirtilmemişse, özellik üzerinden geçerli değerleri de alabilirsiniz. (<xref:System.Windows.Automation.AutomationElementMode.Full> varsayılan değerdir ve bu geçerli değerlere erişime izin verir.)  
  
<a name="Retrieving_Cached_Children_and_Parents"></a>
## <a name="retrieving-cached-children-and-parents"></a>Önbelleğe Alınmış Çocuk ve Ebeveynlerin Alınması  
 İsteğin <xref:System.Windows.Automation.AutomationElement> <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> özelliği aracılığıyla bu öğenin alt öğeleri için bir önbelleğe alma ve istekte bulunduğunuzda, daha sonra alt öğeleri aldığınız öğenin <xref:System.Windows.Automation.AutomationElement.CachedChildren%2A> özelliğinden almak mümkündür.  
  
 Önbellek isteği kapsamına dahil edildiyse, <xref:System.Windows.Automation.TreeScope.Element> isteğin kök öğesi daha sonra <xref:System.Windows.Automation.AutomationElement.CachedParent%2A> alt öğelerden herhangi birinin özelliğinden kullanılabilir.  
  
> [!NOTE]
> İstek kök öğesinin ebeveynleri veya atalarını önbelleğe alamazsınız.  
  
<a name="Updating_the_Cache"></a>
## <a name="updating-the-cache"></a>Önbelleği Güncelleştirme  
 Önbellek yalnızca hiçbir şey değişmediği sürece [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]geçerlidir. Uygulamanız genellikle olaylara yanıt olarak önbelleği güncelleştirmekten sorumludur.  
  
 Etkin <xref:System.Windows.Automation.CacheRequest> ken bir olaya abone olursanız, <xref:System.Windows.Automation.AutomationElement> olay işleyicitemsilciniz çağrıldığında olayın kaynağı olarak güncelleştirilmiş bir önbellek elde elabilirsiniz. Önbelleğe alınan bilgileri de arayarak <xref:System.Windows.Automation.AutomationElement.GetUpdatedCache%2A>bir öğenin önbelleğe alınmış bilgilerini güncelleştirebilirsiniz. Daha önce önbelleğe alınmış tüm bilgileri güncelleştirmek için orijinalini <xref:System.Windows.Automation.CacheRequest> geçirebilirsiniz.  
  
 Önbelleğe göre güncelleştirilme, varolan <xref:System.Windows.Automation.AutomationElement> başvuruların özelliklerini değiştirmez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İstemciler İçin UI Otomasyonu Olayları](ui-automation-events-for-clients.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](use-caching-in-ui-automation.md)
- [FetchTimer Örnek](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771456(v=vs.90))
