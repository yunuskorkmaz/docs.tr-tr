---
title: UI Otomasyonda Önbelleğe Alma
description: .NET 'teki UI Otomasyonu istemcilerinde önbelleğe alma hakkında ayrıntılı bilgi alın. Önbelleğe alma, verileri önceden getirme olarak tanımlanır.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation caching in clients
- caching, UI Automation clients
ms.assetid: 94c15031-4975-43cc-bcd5-c9439ed21c9c
ms.openlocfilehash: 4fbb4acabebea54015b11cefdf8a37c7e2dc93f5
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168253"
---
# <a name="caching-in-ui-automation-clients"></a>UI Otomasyonda Önbelleğe Alma
> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).  
  
 Bu konu, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özelliklerin ve denetim desenlerinin önbelleğe alınmasını tanıtır.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]' De, önbelleğe alma verilerin ön getirme anlamına gelir. Verilere daha sonra çapraz işlem sonrası iletişim olmadan erişilebilir. Önbelleğe alma, genellikle özellikleri ve denetim düzenlerini toplu olarak almak için UI Otomasyonu istemci uygulamaları tarafından kullanılır. Daha sonra bilgiler, gerektiğinde önbellekten alınır. Uygulama, genellikle içindeki bir şeyin değiştiğini belirten olaylara yanıt olarak önbelleği düzenli olarak güncelleştirir [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] .  
  
 Önbelleğe almanın avantajları, Windows Presentation Foundation (WPF) denetimleri ve sunucu tarafı UI Otomasyon sağlayıcılarının bulunduğu özel denetimlerle görülür. Win32 denetimleri için varsayılan sağlayıcılar gibi istemci tarafı sağlayıcılarına erişirken daha az avantaj vardır.  
  
 Önbelleğe alma, uygulama bir öğesini etkinleşdiğinde <xref:System.Windows.Automation.CacheRequest> ve sonra bir yöntemi veya döndüren özelliği (örneğin,) kullandığında oluşur <xref:System.Windows.Automation.AutomationElement> <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> <xref:System.Windows.Automation.AutomationElement.FindAll%2A> . <xref:System.Windows.Automation.TreeWalker>Sınıfının yöntemleri bir istisnadır; önbelleğe alma işlemi yalnızca bir <xref:System.Windows.Automation.CacheRequest> parametre (örneğin,) olarak belirtilmişse yapılır <xref:System.Windows.Automation.TreeWalker.GetFirstChild%28System.Windows.Automation.AutomationElement%2CSystem.Windows.Automation.CacheRequest%29?displayProperty=nameWithType> .  
  
 Önbelleğe alma işlemi, etkin durumdayken bir olaya abone olduğunuzda da oluşur <xref:System.Windows.Automation.CacheRequest> . Olay <xref:System.Windows.Automation.AutomationElement> işleyiciniz bir olayın kaynağı olarak geçildi, orijinal tarafından belirtilen önbelleğe alınmış özellikleri ve desenleri içerir <xref:System.Windows.Automation.CacheRequest> . <xref:System.Windows.Automation.CacheRequest>Olaya abone olduktan sonra üzerinde yapılan tüm değişiklikler etkisizdir.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Bir öğenin özellikler ve Denetim desenleri önbelleğe alınabilir.  
  
<a name="Options_for_Caching"></a>
## <a name="options-for-caching"></a>Önbelleğe alma seçenekleri  
 , <xref:System.Windows.Automation.CacheRequest> Önbelleğe alma için aşağıdaki seçenekleri belirtir.  
  
<a name="Properties_to_Cache"></a>
### <a name="properties-to-cache"></a>Önbelleğe eklenecek özellikler  
 <xref:System.Windows.Automation.CacheRequest.Add%28System.Windows.Automation.AutomationProperty%29>İsteği etkinleştirmeden önce her bir özellik için çağırarak önbelleğe almak için özellikleri belirtebilirsiniz.  
  
<a name="Control_Patterns_to_Cache"></a>
### <a name="control-patterns-to-cache"></a>Önbelleğe almak için Denetim desenleri  
 İsteği etkinleştirmeden önce her bir deseni çağırarak önbelleğe almak için Denetim desenleri belirtebilirsiniz <xref:System.Windows.Automation.CacheRequest.Add%28System.Windows.Automation.AutomationPattern%29> . Bir model önbelleğe alındığında, özellikleri otomatik olarak önbelleğe alınmaz; kullanarak, önbelleğe alınmasını istediğiniz özellikleri belirtmeniz gerekir <xref:System.Windows.Automation.CacheRequest.Add%2A?displayProperty=nameWithType> .  
  
<a name="Scope_of_the_Caching"></a>
### <a name="scope-and-filtering-of-caching"></a>Önbelleğe almayı kapsam ve filtreleme  
 İsteği etkinleştirmeden önce özelliğini ayarlayarak özelliklerini ve desenlerini önbelleğe almak istediğiniz öğeleri belirtebilirsiniz <xref:System.Windows.Automation.CacheRequest.TreeScope%2A?displayProperty=nameWithType> . Kapsam, istek etkinken alınan öğelere görelidir. Örneğin, yalnızca ayarlarsanız <xref:System.Windows.Automation.TreeScope.Children> ve sonra bir öğesi alırsanız, <xref:System.Windows.Automation.AutomationElement> Bu öğenin alt öğelerinin özellikleri ve desenleri önbelleğe alınır, ancak öğenin kendisidir. Alınan öğenin kendisi için önbelleğe alma işleminin yapıldığından emin olmak için, özelliğine dahil etmeniz gerekir <xref:System.Windows.Automation.TreeScope.Element> <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> . Kapsamı veya olarak ayarlamak mümkün değildir <xref:System.Windows.Automation.TreeScope.Parent> <xref:System.Windows.Automation.TreeScope.Ancestors> . Ancak, bir alt öğe önbelleğe alındığında bir üst öğe önbelleğe alınabilir; bkz. bu konuda önbelleğe alınmış alt öğeleri ve üst öğeleri alma.  
  
 Önbelleğe almanın kapsamı özellikten de etkilenir <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A?displayProperty=nameWithType> . Varsayılan olarak, önbelleğe alma yalnızca ağacın denetim görünümünde görünen öğeler için gerçekleştirilir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] . Ancak, bu özelliği, tüm öğelere önbelleğe alma uygulamak veya yalnızca içerik görünümünde görünen öğelere dönüştürmek için değiştirebilirsiniz.  
  
<a name="Strength_of_the_Element_References"></a>
### <a name="strength-of-the-element-references"></a>Öğe başvurularının gücü  
 <xref:System.Windows.Automation.AutomationElement>' I aldığınızda, varsayılan olarak, önbelleğe alınmamış olanlar dahil olmak üzere, bu öğenin tüm özelliklerine ve desenlerine erişebilirsiniz. Ancak, daha fazla verimlilik için, öğesinin özelliğini olarak ayarlayarak, öğesine yönelik başvurunun yalnızca önbelleğe alınmış verileri ifade eder <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> <xref:System.Windows.Automation.CacheRequest> <xref:System.Windows.Automation.AutomationElementMode.None> . Bu durumda, önbelleğe alınmamış özelliklere ve alınan öğelerin desenlerine erişiminiz yok. Bu, ya da <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> herhangi bir denetim deseninin özelliği ya da ya da ya da `Current` <xref:System.Windows.Automation.AutomationElement> ya da veya kullanarak bir model elde edemeyeceğiniz anlamına gelir <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> . Önbelleğe alınmış desenler ' de, gibi dizi özelliklerini alan <xref:System.Windows.Automation.SelectionPattern.SelectionPatternInformation.GetSelection%2A?displayProperty=nameWithType> , ancak denetim üzerinde eylem gerçekleştirmeyen yöntemler çağırabilirsiniz <xref:System.Windows.Automation.InvokePattern.Invoke%2A?displayProperty=nameWithType> .  
  
 Nesnelere tam başvurular gerektirebilecek bir uygulama örneği, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A> <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> bir penceredeki öğelerin ve özelliklerini önceden ve nesnelerin kendileri için gerekli olmayan bir ekran okuyucudır <xref:System.Windows.Automation.AutomationElement> .  
  
<a name="Activating_the_CacheRequest"></a>
## <a name="activating-the-cacherequest"></a>CacheRequest etkinleştiriliyor  
 Önbelleğe alma yalnızca, <xref:System.Windows.Automation.AutomationElement> <xref:System.Windows.Automation.CacheRequest> geçerli iş parçacığı için etkin durumdayken nesneler alındığında gerçekleştirilir. ' Yi etkinleştirmenin iki yolu vardır <xref:System.Windows.Automation.CacheRequest> .  
  
 Her zamanki şekilde çağrmanız önerilir <xref:System.Windows.Automation.CacheRequest.Activate%2A> . Bu yöntem, uygulayan bir nesne döndürür <xref:System.IDisposable> . Nesne mevcut olduğu sürece istek etkin kalır <xref:System.IDisposable> . Nesnenin ömrünü denetlemek için en kolay yol, çağrıyı bir `using` (C#) veya `Using` (Visual Basic) bloğu içine allemektir. Bu, bir özel durum oluşsa bile, isteğin yığından ortaya çıkarılmasını sağlar.  
  
 Önbellek isteklerini iç içe aktarmak istediğinizde yararlı olan başka bir yol da çağrıladır <xref:System.Windows.Automation.CacheRequest.Push%2A> . Bu, isteği bir yığına koyar ve etkinleştirir. İstek tarafından yığından kaldırılana kadar istek etkin kalır <xref:System.Windows.Automation.CacheRequest.Pop%2A> . Yığın üzerine başka bir istek itilmesi durumunda istek geçici olarak devre dışı olur; yalnızca Yığındaki en üstteki istek etkindir.  
  
<a name="Retrieving_Cached_Properties"></a>
## <a name="retrieving-cached-properties"></a>Önbelleğe alınmış Özellikler alınıyor  
 Aşağıdaki yöntemler ve özellikler aracılığıyla bir öğenin önbelleğe alınmış özelliklerini alabilirsiniz.  
  
- <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.Cached%2A>  
  
 İstenen özellik önbellekte değilse bir özel durum oluşur.  
  
 <xref:System.Windows.Automation.AutomationElement.Cached%2A>, gibi <xref:System.Windows.Automation.AutomationElement.Current%2A> , tek tek özellikleri bir yapının üyesi olarak kullanıma sunar. Ancak, bu yapıyı almanız gerekmez; tek tek özelliklere doğrudan erişebilirsiniz. Örneğin, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A> özelliği öğesinden elde edilebilir `element.Cached.Name` `element` <xref:System.Windows.Automation.AutomationElement> .  
  
<a name="Retrieving_Cached_Control_Patterns"></a>
## <a name="retrieving-cached-control-patterns"></a>Önbelleğe alınmış denetim desenlerini alma  
 Bir öğenin önbelleğe alınmış denetim desenlerini aşağıdaki yöntemlerle alabilirsiniz.  
  
- <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A>  
  
 Desenler önbellekte değilse, <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> bir özel durum oluşturur ve <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> döndürür `false` .  
  
 Bir denetim deseninin önbelleğe alınmış özelliklerini, model nesnesinin özelliğini kullanarak elde edebilirsiniz `Cached` . Ayrıca, özelliği aracılığıyla geçerli değerleri de alabilirsiniz `Current` , ancak yalnızca alındığı <xref:System.Windows.Automation.AutomationElementMode.None> zaman belirtilmemişse <xref:System.Windows.Automation.AutomationElement> . ( <xref:System.Windows.Automation.AutomationElementMode.Full> varsayılan değerdir ve bu, geçerli değerlere erişime izin verir.)  
  
<a name="Retrieving_Cached_Children_and_Parents"></a>
## <a name="retrieving-cached-children-and-parents"></a>Önbelleğe alınmış alt öğeler ve ebeveynler alınıyor  
 <xref:System.Windows.Automation.AutomationElement>İsteğin özelliği aracılığıyla o öğenin alt öğeleri için bir ve isteği önbelleğe alma <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> işlemi gerçekleştirdiğinizde, daha sonra, aldığınız öğenin özelliğinden alt öğeler elde etmek mümkündür <xref:System.Windows.Automation.AutomationElement.CachedChildren%2A> .  
  
 <xref:System.Windows.Automation.TreeScope.Element>Önbellek isteğinin kapsamına dahil edilmişse, isteğin kök öğesi bundan sonra <xref:System.Windows.Automation.AutomationElement.CachedParent%2A> alt öğelerin herhangi birinin özelliğinden kullanılabilir.  
  
> [!NOTE]
> İsteğin kök öğesinin üst öğelerini veya üst öğelerini önbelleğe alamaz.  
  
<a name="Updating_the_Cache"></a>
## <a name="updating-the-cache"></a>Önbellek güncelleştiriliyor  
 Önbellek yalnızca içinde hiçbir değişiklik olmadığı sürece geçerlidir [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] . Uygulamanız, genellikle olaylara yanıt olarak önbelleğin güncelleştirilmesinden sorumludur.  
  
 Bir etkinlik etkinken bir olaya abone olduğunuzda <xref:System.Windows.Automation.CacheRequest> , <xref:System.Windows.Automation.AutomationElement> olay işleyicisi temsilciniz her çağrıldığında etkinliğin kaynağı olarak güncelleştirilmiş bir önbellek ile elde edersiniz. Ayrıca, çağırarak bir öğe için önbelleğe alınmış bilgileri güncelleştirebilirsiniz <xref:System.Windows.Automation.AutomationElement.GetUpdatedCache%2A> . <xref:System.Windows.Automation.CacheRequest>Daha önce önbelleğe alınmış tüm bilgileri güncelleştirmek için özgün olarak geçiş yapabilirsiniz.  
  
 Önbelleğin güncelleştirilmesi varolan başvuruların özelliklerini değiştirmez <xref:System.Windows.Automation.AutomationElement> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İstemciler İçin UI Otomasyon Olayları](ui-automation-events-for-clients.md)
- [UI Otomasyonda Önbelleğe Almayı Kullanma](use-caching-in-ui-automation.md)
- [FetchTimer örneği](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771456(v=vs.90))
