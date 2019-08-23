---
title: UI Otomasyonda Önbelleğe Alma
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation caching in clients
- caching, UI Automation clients
ms.assetid: 94c15031-4975-43cc-bcd5-c9439ed21c9c
ms.openlocfilehash: 05738fae72d11e66b28acdc22fa1a8745ca7a083
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932695"
---
# <a name="caching-in-ui-automation-clients"></a>UI Otomasyonda Önbelleğe Alma
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir. Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özelliklerin ve denetim desenlerinin önbelleğe alınmasını tanıtır.  
  
 ' [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]De, önbelleğe alma verilerin ön getirme anlamına gelir. Verilere daha sonra çapraz işlem sonrası iletişim olmadan erişilebilir. Önbelleğe alma, genellikle özellikleri ve denetim düzenlerini toplu olarak almak için UI Otomasyonu istemci uygulamaları tarafından kullanılır. Daha sonra bilgiler, gerektiğinde önbellekten alınır. Uygulama, genellikle içindeki [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] bir şeyin değiştiğini belirten olaylara yanıt olarak önbelleği düzenli olarak güncelleştirir.  
  
 Önbelleğe almanın avantajları, Windows Presentation Foundation (WPF) denetimleri ve sunucu tarafı UI Otomasyon sağlayıcılarının bulunduğu özel denetimlerle görülür. Denetimler için [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] varsayılan sağlayıcılar gibi istemci tarafı sağlayıcılarına erişirken daha az avantaj vardır.  
  
 Önbelleğe alma <xref:System.Windows.Automation.CacheRequest> , uygulama bir öğesini etkinleşdiğinde ve sonra bir <xref:System.Windows.Automation.AutomationElement>yöntemi veya döndüren özelliği (örneğin <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> <xref:System.Windows.Automation.AutomationElement.FindAll%2A>,) kullandığında oluşur. <xref:System.Windows.Automation.TreeWalker> Sınıfının yöntemleri bir istisnadır; önbelleğe alma işlemi yalnızca bir <xref:System.Windows.Automation.CacheRequest> parametre (örneğin, <xref:System.Windows.Automation.TreeWalker.GetFirstChild%28System.Windows.Automation.AutomationElement%2CSystem.Windows.Automation.CacheRequest%29?displayProperty=nameWithType>) olarak belirtilmişse yapılır.  
  
 Önbelleğe alma <xref:System.Windows.Automation.CacheRequest> işlemi, etkin durumdayken bir olaya abone olduğunuzda da oluşur. Olay işleyiciniz bir olayın kaynağı olarak <xref:System.Windows.Automation.CacheRequest> geçildi,orijinaltarafındanbelirtilenönbelleğealınmışözelliklerivedesenleriiçerir.<xref:System.Windows.Automation.AutomationElement> Olaya abone <xref:System.Windows.Automation.CacheRequest> olduktan sonra üzerinde yapılan tüm değişiklikler etkisizdir.  
  
 Bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] öğenin özellikler ve Denetim desenleri önbelleğe alınabilir.  
  
<a name="Options_for_Caching"></a>   
## <a name="options-for-caching"></a>Önbelleğe alma seçenekleri  
 , <xref:System.Windows.Automation.CacheRequest> Önbelleğe alma için aşağıdaki seçenekleri belirtir.  
  
<a name="Properties_to_Cache"></a>   
### <a name="properties-to-cache"></a>Önbelleğe eklenecek özellikler  
 İsteği etkinleştirmeden önce her bir özellik için çağırarak <xref:System.Windows.Automation.CacheRequest.Add%28System.Windows.Automation.AutomationProperty%29> önbelleğe almak için özellikleri belirtebilirsiniz.  
  
<a name="Control_Patterns_to_Cache"></a>   
### <a name="control-patterns-to-cache"></a>Önbelleğe almak için Denetim desenleri  
 İsteği etkinleştirmeden önce her bir deseni çağırarak <xref:System.Windows.Automation.CacheRequest.Add%28System.Windows.Automation.AutomationPattern%29> önbelleğe almak için Denetim desenleri belirtebilirsiniz. Bir model önbelleğe alındığında, özellikleri otomatik olarak önbelleğe alınmaz; kullanarak <xref:System.Windows.Automation.CacheRequest.Add%2A?displayProperty=nameWithType>, önbelleğe alınmasını istediğiniz özellikleri belirtmeniz gerekir.  
  
<a name="Scope_of_the_Caching"></a>   
### <a name="scope-and-filtering-of-caching"></a>Önbelleğe almayı kapsam ve filtreleme  
 İsteği etkinleştirmeden önce <xref:System.Windows.Automation.CacheRequest.TreeScope%2A?displayProperty=nameWithType> özelliğini ayarlayarak özelliklerini ve desenlerini önbelleğe almak istediğiniz öğeleri belirtebilirsiniz. Kapsam, istek etkinken alınan öğelere görelidir. Örneğin, yalnızca <xref:System.Windows.Automation.TreeScope.Children>ayarlarsanız ve sonra bir <xref:System.Windows.Automation.AutomationElement>öğesi alırsanız, bu öğenin alt öğelerinin özellikleri ve desenleri önbelleğe alınır, ancak öğenin kendisidir. Alınan öğenin kendisi için önbelleğe alma işleminin yapıldığından emin olmak için, <xref:System.Windows.Automation.TreeScope.Element> <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> özelliğine dahil etmeniz gerekir. Kapsamı veya <xref:System.Windows.Automation.TreeScope.Parent> <xref:System.Windows.Automation.TreeScope.Ancestors>olarak ayarlamak mümkün değildir. Ancak, bir alt öğe önbelleğe alındığında bir üst öğe önbelleğe alınabilir; bkz. bu konuda önbelleğe alınmış alt öğeleri ve üst öğeleri alma.  
  
 Önbelleğe almanın kapsamı <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A?displayProperty=nameWithType> özellikten de etkilenir. Varsayılan olarak, önbelleğe alma yalnızca [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacın denetim görünümünde görünen öğeler için gerçekleştirilir. Ancak, bu özelliği, tüm öğelere önbelleğe alma uygulamak veya yalnızca içerik görünümünde görünen öğelere dönüştürmek için değiştirebilirsiniz.  
  
<a name="Strength_of_the_Element_References"></a>   
### <a name="strength-of-the-element-references"></a>Öğe başvurularının gücü  
 <xref:System.Windows.Automation.AutomationElement>' I aldığınızda, varsayılan olarak, önbelleğe alınmamış olanlar dahil olmak üzere, bu öğenin tüm özelliklerine ve desenlerine erişebilirsiniz. Ancak, daha fazla verimlilik için, <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> <xref:System.Windows.Automation.CacheRequest> öğesinin özelliğini olarak <xref:System.Windows.Automation.AutomationElementMode.None>ayarlayarak, öğesine yönelik başvurunun yalnızca önbelleğe alınmış verileri ifade eder. Bu durumda, önbelleğe alınmamış özelliklere ve alınan öğelerin desenlerine erişiminiz yok. Bu, ya da herhangi bir denetim deseninin özelliği <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> <xref:System.Windows.Automation.AutomationElement> ya da `Current` ya da ya da ya da veya <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A>kullanarak <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> bir model elde edemeyeceğiniz anlamına gelir. Önbelleğe alınmış desenler ' de, gibi dizi özelliklerini <xref:System.Windows.Automation.SelectionPattern.SelectionPatternInformation.GetSelection%2A?displayProperty=nameWithType>alan, ancak denetim <xref:System.Windows.Automation.InvokePattern.Invoke%2A?displayProperty=nameWithType>üzerinde eylem gerçekleştirmeyen yöntemler çağırabilirsiniz.  
  
 Nesnelere tam başvurular gerektirebilecek bir uygulama örneği, bir penceredeki öğelerin <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A> ve özelliklerini önceden ve <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> <xref:System.Windows.Automation.AutomationElement> nesnelerin kendileri için gerekli olmayan bir ekran okuyucudır.  
  
<a name="Activating_the_CacheRequest"></a>   
## <a name="activating-the-cacherequest"></a>CacheRequest etkinleştiriliyor  
 Önbelleğe alma yalnızca <xref:System.Windows.Automation.AutomationElement> , geçerli iş parçacığı için etkin <xref:System.Windows.Automation.CacheRequest> durumdayken nesneler alındığında gerçekleştirilir. ' Yi etkinleştirmenin <xref:System.Windows.Automation.CacheRequest>iki yolu vardır.  
  
 Her zamanki şekilde çağrmanız <xref:System.Windows.Automation.CacheRequest.Activate%2A>önerilir. Bu yöntem, uygulayan <xref:System.IDisposable>bir nesne döndürür. <xref:System.IDisposable> Nesne mevcut olduğu sürece istek etkin kalır. Nesnenin ömrünü denetlemek için en kolay yol, çağrıyı bir `using` (C#) veya `Using` (Visual Basic) bloğu içine allemektir. Bu, bir özel durum oluşsa bile, isteğin yığından ortaya çıkarılmasını sağlar.  
  
 Önbellek isteklerini iç içe aktarmak istediğinizde yararlı olan başka bir yol da çağrıladır <xref:System.Windows.Automation.CacheRequest.Push%2A>. Bu, isteği bir yığına koyar ve etkinleştirir. İstek tarafından <xref:System.Windows.Automation.CacheRequest.Pop%2A>yığından kaldırılana kadar istek etkin kalır. Yığın üzerine başka bir istek itilmesi durumunda istek geçici olarak devre dışı olur; yalnızca Yığındaki en üstteki istek etkindir.  
  
<a name="Retrieving_Cached_Properties"></a>   
## <a name="retrieving-cached-properties"></a>Önbelleğe alınmış Özellikler alınıyor  
 Aşağıdaki yöntemler ve özellikler aracılığıyla bir öğenin önbelleğe alınmış özelliklerini alabilirsiniz.  
  
- <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.Cached%2A>  
  
 İstenen özellik önbellekte değilse bir özel durum oluşur.  
  
 <xref:System.Windows.Automation.AutomationElement.Cached%2A>, gibi <xref:System.Windows.Automation.AutomationElement.Current%2A>, tek tek özellikleri bir yapının üyesi olarak kullanıma sunar. Ancak, bu yapıyı almanız gerekmez; tek tek özelliklere doğrudan erişebilirsiniz. Örneğin, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A> özelliği öğesinden `element.Cached.Name` `element` elde edilebilir .<xref:System.Windows.Automation.AutomationElement>  
  
<a name="Retrieving_Cached_Control_Patterns"></a>   
## <a name="retrieving-cached-control-patterns"></a>Önbelleğe alınmış denetim desenlerini alma  
 Bir öğenin önbelleğe alınmış denetim desenlerini aşağıdaki yöntemlerle alabilirsiniz.  
  
- <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A>  
  
 Desenler önbellekte değilse, <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> bir özel durum oluşturur ve <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> döndürür `false`.  
  
 Bir denetim deseninin önbelleğe alınmış özelliklerini, model nesnesinin `Cached` özelliğini kullanarak elde edebilirsiniz. Ayrıca, `Current` özelliği aracılığıyla geçerli değerleri de alabilirsiniz, ancak <xref:System.Windows.Automation.AutomationElementMode.None> yalnızca alındığı zaman <xref:System.Windows.Automation.AutomationElement> belirtilmemişse. (<xref:System.Windows.Automation.AutomationElementMode.Full> varsayılan değerdir ve bu, geçerli değerlere erişime izin verir.)  
  
<a name="Retrieving_Cached_Children_and_Parents"></a>   
## <a name="retrieving-cached-children-and-parents"></a>Önbelleğe alınmış alt öğeler ve ebeveynler alınıyor  
 İsteğin <xref:System.Windows.Automation.AutomationElement> özelliği<xref:System.Windows.Automation.CacheRequest.TreeScope%2A> aracılığıyla o öğenin alt öğeleri için bir ve isteği önbelleğe alma işlemi gerçekleştirdiğinizde, daha sonra, aldığınız öğenin <xref:System.Windows.Automation.AutomationElement.CachedChildren%2A> özelliğinden alt öğeler elde etmek mümkündür.  
  
 Önbellek isteğinin kapsamına dahil edilmişse, isteğin kök öğesi bundan sonra alt öğelerin herhangi birinin <xref:System.Windows.Automation.AutomationElement.CachedParent%2A> özelliğinden kullanılabilir. <xref:System.Windows.Automation.TreeScope.Element>  
  
> [!NOTE]
> İsteğin kök öğesinin üst öğelerini veya üst öğelerini önbelleğe alamaz.  
  
<a name="Updating_the_Cache"></a>   
## <a name="updating-the-cache"></a>Önbellek güncelleştiriliyor  
 Önbellek yalnızca içinde [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]hiçbir değişiklik olmadığı sürece geçerlidir. Uygulamanız, genellikle olaylara yanıt olarak önbelleğin güncelleştirilmesinden sorumludur.  
  
 Bir <xref:System.Windows.Automation.CacheRequest> etkinlik etkinken bir olaya abone olduğunuzda, olay işleyicisi temsilciniz her çağrıldığında etkinliğin <xref:System.Windows.Automation.AutomationElement> kaynağı olarak güncelleştirilmiş bir önbellek ile elde edersiniz. Ayrıca, çağırarak <xref:System.Windows.Automation.AutomationElement.GetUpdatedCache%2A>bir öğe için önbelleğe alınmış bilgileri güncelleştirebilirsiniz. Daha önce önbelleğe alınmış tüm bilgileri <xref:System.Windows.Automation.CacheRequest> güncelleştirmek için özgün olarak geçiş yapabilirsiniz.  
  
 Önbelleğin güncelleştirilmesi varolan <xref:System.Windows.Automation.AutomationElement> başvuruların özelliklerini değiştirmez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İstemciler İçin UI Otomasyonu Olayları](../../../docs/framework/ui-automation/ui-automation-events-for-clients.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
- [FetchTimer örneği](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771456(v=vs.90))
