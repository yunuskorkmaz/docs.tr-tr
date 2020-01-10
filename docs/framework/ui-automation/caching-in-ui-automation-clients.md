---
title: UI Otomasyonda Önbelleğe Alma
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation caching in clients
- caching, UI Automation clients
ms.assetid: 94c15031-4975-43cc-bcd5-c9439ed21c9c
ms.openlocfilehash: 5c0c92f40ae60785f780cb573bb7faa77a31f273
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75741784"
---
# <a name="caching-in-ui-automation-clients"></a>UI Otomasyonda Önbelleğe Alma
> [!NOTE]
> Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özelliklerinin ve denetim desenlerinin önbelleğe alınmasını tanıtır.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], önbelleğe alma işlemi verileri önceden getirme anlamına gelir. Verilere daha sonra çapraz işlem sonrası iletişim olmadan erişilebilir. Önbelleğe alma, genellikle özellikleri ve denetim düzenlerini toplu olarak almak için UI Otomasyonu istemci uygulamaları tarafından kullanılır. Daha sonra bilgiler, gerektiğinde önbellekten alınır. Uygulama, genellikle [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] değiştiği bir şeyi belirten olaylara yanıt olarak önbelleği düzenli olarak güncelleştirir.  
  
 Önbelleğe almanın avantajları, Windows Presentation Foundation (WPF) denetimleri ve sunucu tarafı UI Otomasyon sağlayıcılarının bulunduğu özel denetimlerle görülür. Win32 denetimleri için varsayılan sağlayıcılar gibi istemci tarafı sağlayıcılarına erişirken daha az avantaj vardır.  
  
 Önbelleğe alma, uygulama bir <xref:System.Windows.Automation.CacheRequest> etkinleşdiğinde ve sonra bir <xref:System.Windows.Automation.AutomationElement>döndüren herhangi bir yöntemi veya özelliği kullandığında oluşur; Örneğin, <xref:System.Windows.Automation.AutomationElement.FindFirst%2A><xref:System.Windows.Automation.AutomationElement.FindAll%2A>. <xref:System.Windows.Automation.TreeWalker> sınıfının yöntemleri bir istisnadır; önbelleğe alma işlemi, yalnızca bir parametre olarak bir <xref:System.Windows.Automation.CacheRequest> belirtilirse yapılır (örneğin, <xref:System.Windows.Automation.TreeWalker.GetFirstChild%28System.Windows.Automation.AutomationElement%2CSystem.Windows.Automation.CacheRequest%29?displayProperty=nameWithType>.  
  
 Önbelleğe alma işlemi, bir <xref:System.Windows.Automation.CacheRequest> etkinken bir olaya abone olduğunuzda da oluşur. Olay işleyicinizde bir olayın kaynağı olarak geçirilen <xref:System.Windows.Automation.AutomationElement>, özgün <xref:System.Windows.Automation.CacheRequest>tarafından belirtilen önbelleğe alınmış özellikleri ve desenleri içerir. Olaya abone olduktan sonra <xref:System.Windows.Automation.CacheRequest> yapılan tüm değişiklikler etkisizdir.  
  
 Öğenin [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri ve Denetim desenleri önbelleğe alınabilir.  
  
<a name="Options_for_Caching"></a>   
## <a name="options-for-caching"></a>Önbelleğe alma seçenekleri  
 <xref:System.Windows.Automation.CacheRequest>, önbelleğe alma için aşağıdaki seçenekleri belirtir.  
  
<a name="Properties_to_Cache"></a>   
### <a name="properties-to-cache"></a>Önbelleğe eklenecek özellikler  
 İsteği etkinleştirmeden önce her bir özellik için <xref:System.Windows.Automation.CacheRequest.Add%28System.Windows.Automation.AutomationProperty%29> çağırarak önbelleğe almak için özellikleri belirtebilirsiniz.  
  
<a name="Control_Patterns_to_Cache"></a>   
### <a name="control-patterns-to-cache"></a>Önbelleğe almak için Denetim desenleri  
 İsteği etkinleştirmeden önce her bir desen için <xref:System.Windows.Automation.CacheRequest.Add%28System.Windows.Automation.AutomationPattern%29> çağırarak, önbelleğe almak için Denetim desenleri belirtebilirsiniz. Bir model önbelleğe alındığında, özellikleri otomatik olarak önbelleğe alınmaz; <xref:System.Windows.Automation.CacheRequest.Add%2A?displayProperty=nameWithType>kullanarak, önbelleğe alınmasını istediğiniz özellikleri belirtmeniz gerekir.  
  
<a name="Scope_of_the_Caching"></a>   
### <a name="scope-and-filtering-of-caching"></a>Önbelleğe almayı kapsam ve filtreleme  
 İsteği etkinleştirmeden önce <xref:System.Windows.Automation.CacheRequest.TreeScope%2A?displayProperty=nameWithType> özelliğini ayarlayarak, özelliklerini ve desenlerini önbelleğe almak istediğiniz öğeleri belirtebilirsiniz. Kapsam, istek etkinken alınan öğelere görelidir. Örneğin, yalnızca <xref:System.Windows.Automation.TreeScope.Children>ayarlarsanız ve sonra bir <xref:System.Windows.Automation.AutomationElement>alırsanız, bu öğenin alt öğelerinin özellikleri ve desenleri önbelleğe alınır, ancak öğenin kendisidir. Alınan öğenin kendisi için önbelleğe alma işleminin yapıldığından emin olmak için, <xref:System.Windows.Automation.TreeScope.Element> <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> özelliğine dahil etmeniz gerekir. Kapsamı <xref:System.Windows.Automation.TreeScope.Parent> veya <xref:System.Windows.Automation.TreeScope.Ancestors>olarak ayarlamak mümkün değildir. Ancak, bir alt öğe önbelleğe alındığında bir üst öğe önbelleğe alınabilir; bkz. bu konuda önbelleğe alınmış alt öğeleri ve üst öğeleri alma.  
  
 Önbelleğe almanın kapsamı <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A?displayProperty=nameWithType> özelliğinden da etkilenir. Varsayılan olarak, önbelleğe alma yalnızca [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacının denetim görünümünde görünen öğeler için gerçekleştirilir. Ancak, bu özelliği, tüm öğelere önbelleğe alma uygulamak veya yalnızca içerik görünümünde görünen öğelere dönüştürmek için değiştirebilirsiniz.  
  
<a name="Strength_of_the_Element_References"></a>   
### <a name="strength-of-the-element-references"></a>Öğe başvurularının gücü  
 Bir <xref:System.Windows.Automation.AutomationElement>aldığınızda, varsayılan olarak, önbelleğe alınmamış olanlar dahil olmak üzere, bu öğenin tüm özelliklerine ve desenlerine erişebilirsiniz. Ancak, daha fazla verimlilik için, öğe başvurusunun, <xref:System.Windows.Automation.CacheRequest> <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> özelliğini <xref:System.Windows.Automation.AutomationElementMode.None>olarak ayarlayarak, yalnızca önbelleğe alınmış verilere başvurduğunu belirtebilirsiniz. Bu durumda, önbelleğe alınmamış özelliklere ve alınan öğelerin desenlerine erişiminiz yok. Bu, <xref:System.Windows.Automation.AutomationElement> veya herhangi bir denetim deseninin <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> veya `Current` özelliği aracılığıyla herhangi bir özelliğe erişemeyeceğiniz anlamına gelir; ya da <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> ya da <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A>kullanarak bir model elde edebilirsiniz. Önbelleğe alınmış desenler ' de, <xref:System.Windows.Automation.SelectionPattern.SelectionPatternInformation.GetSelection%2A?displayProperty=nameWithType>gibi dizi özelliklerini alan yöntemler çağırabilirsiniz, ancak <xref:System.Windows.Automation.InvokePattern.Invoke%2A?displayProperty=nameWithType>gibi denetim üzerinde herhangi bir eylem gerçekleştirmez.  
  
 Nesnelere tam başvurular gerektirebilecek bir uygulama örneği, bir penceredeki öğelerin <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A> ve <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> özelliklerini önceden ve <xref:System.Windows.Automation.AutomationElement> nesneleri için gerekli olmayan bir ekran okuyucudur.  
  
<a name="Activating_the_CacheRequest"></a>   
## <a name="activating-the-cacherequest"></a>CacheRequest etkinleştiriliyor  
 Önbelleğe alma yalnızca, geçerli iş parçacığı için bir <xref:System.Windows.Automation.CacheRequest> etkinken <xref:System.Windows.Automation.AutomationElement> nesneleri alındığında gerçekleştirilir. <xref:System.Windows.Automation.CacheRequest>etkinleştirmenin iki yolu vardır.  
  
 Her zamanki yol <xref:System.Windows.Automation.CacheRequest.Activate%2A>çağırmanız olur. Bu yöntem <xref:System.IDisposable>uygulayan bir nesne döndürür. <xref:System.IDisposable> nesnesi mevcut olduğu sürece istek etkin kalır. Nesnenin ömrünü denetlemek için en kolay yol, çağrıyı bir `using` (C#) veya `Using` (Visual Basic) bloğunun içine kullanmaktır. Bu, bir özel durum oluşsa bile, isteğin yığından ortaya çıkarılmasını sağlar.  
  
 Önbellek isteklerini iç içe aktarmak istediğinizde yararlı olan başka bir yol da <xref:System.Windows.Automation.CacheRequest.Push%2A>çağırıladır. Bu, isteği bir yığına koyar ve etkinleştirir. <xref:System.Windows.Automation.CacheRequest.Pop%2A>tarafından yığından kaldırılana kadar istek etkin kalır. Yığın üzerine başka bir istek itilmesi durumunda istek geçici olarak devre dışı olur; yalnızca Yığındaki en üstteki istek etkindir.  
  
<a name="Retrieving_Cached_Properties"></a>   
## <a name="retrieving-cached-properties"></a>Önbelleğe alınmış Özellikler alınıyor  
 Aşağıdaki yöntemler ve özellikler aracılığıyla bir öğenin önbelleğe alınmış özelliklerini alabilirsiniz.  
  
- <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.Cached%2A>  
  
 İstenen özellik önbellekte değilse bir özel durum oluşur.  
  
 <xref:System.Windows.Automation.AutomationElement.Current%2A>gibi <xref:System.Windows.Automation.AutomationElement.Cached%2A>, tek tek özellikleri bir yapının üyesi olarak kullanıma sunar. Ancak, bu yapıyı almanız gerekmez; tek tek özelliklere doğrudan erişebilirsiniz. Örneğin, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A> özelliği, `element` bir <xref:System.Windows.Automation.AutomationElement>olduğu `element.Cached.Name`elde edilebilir.  
  
<a name="Retrieving_Cached_Control_Patterns"></a>   
## <a name="retrieving-cached-control-patterns"></a>Önbelleğe alınmış denetim desenlerini alma  
 Bir öğenin önbelleğe alınmış denetim desenlerini aşağıdaki yöntemlerle alabilirsiniz.  
  
- <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A>  
  
 Desenler önbellekte değilse, <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> bir özel durum harekete geçirir ve <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> `false`döndürür.  
  
 Bir denetim deseninin önbelleğe alınmış özelliklerini, model nesnesinin `Cached` özelliğini kullanarak elde edebilirsiniz. Ayrıca, `Current` özelliği aracılığıyla geçerli değerleri alabilirsiniz, ancak yalnızca <xref:System.Windows.Automation.AutomationElement> alındığında <xref:System.Windows.Automation.AutomationElementMode.None> belirtilmemişse. (<xref:System.Windows.Automation.AutomationElementMode.Full> varsayılan değerdir ve bu, geçerli değerlere erişime izin verir.)  
  
<a name="Retrieving_Cached_Children_and_Parents"></a>   
## <a name="retrieving-cached-children-and-parents"></a>Önbelleğe alınmış alt öğeler ve ebeveynler alınıyor  
 Bir <xref:System.Windows.Automation.AutomationElement> alıp, bu öğenin alt öğeleri için isteğin <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> özelliği aracılığıyla önbelleğe alma isteği aldığınızda, daha sonra, aldığınız öğenin <xref:System.Windows.Automation.AutomationElement.CachedChildren%2A> özelliğinden alt öğeleri almak mümkündür.  
  
 <xref:System.Windows.Automation.TreeScope.Element>, önbellek isteğinin kapsamına dahil edilmişse, isteğin kök öğesi bundan sonra alt öğelerin herhangi birinin <xref:System.Windows.Automation.AutomationElement.CachedParent%2A> özelliğinden kullanılabilir.  
  
> [!NOTE]
> İsteğin kök öğesinin üst öğelerini veya üst öğelerini önbelleğe alamaz.  
  
<a name="Updating_the_Cache"></a>   
## <a name="updating-the-cache"></a>Önbellek güncelleştiriliyor  
 Önbellek yalnızca [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]hiçbir değişiklik olmadığı sürece geçerlidir. Uygulamanız, genellikle olaylara yanıt olarak önbelleğin güncelleştirilmesinden sorumludur.  
  
 Bir <xref:System.Windows.Automation.CacheRequest> etkinken bir olaya abone olduğunuzda, olay işleyicisi temsilciniz her çağrıldığında etkinliğin kaynağı olarak güncelleştirilmiş bir önbellek ile <xref:System.Windows.Automation.AutomationElement> elde edersiniz. Ayrıca, <xref:System.Windows.Automation.AutomationElement.GetUpdatedCache%2A>çağırarak bir öğe için önbelleğe alınmış bilgileri güncelleştirebilirsiniz. Daha önce önbelleğe alınmış tüm bilgileri güncelleştirmek için özgün <xref:System.Windows.Automation.CacheRequest> geçirebilirsiniz.  
  
 Önbelleğin güncelleştirilmesi, varolan <xref:System.Windows.Automation.AutomationElement> başvurularının özelliklerini değiştirmez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İstemciler İçin UI Otomasyonu Olayları](ui-automation-events-for-clients.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](use-caching-in-ui-automation.md)
- [FetchTimer örneği](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771456(v=vs.90))
