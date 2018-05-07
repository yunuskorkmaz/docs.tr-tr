---
title: UI Otomasyonda Önbelleğe Alma
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation caching in clients
- caching, UI Automation clients
ms.assetid: 94c15031-4975-43cc-bcd5-c9439ed21c9c
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: fa96a12c92703430482b765d625067fbf08c3477
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="caching-in-ui-automation-clients"></a>UI Otomasyonda Önbelleğe Alma
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu, önbelleğe alınmasını tanıtır [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri ve denetim düzenleri.  
  
 İçinde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], önbelleğe alma veri önceden getirme anlamına gelir. Verileri daha fazla işlem içi iletişimi erişilebilir. Önbelleğe alma genellikle UI otomasyon istemci uygulamaları tarafından özellikleri ve denetim düzenleri toplu almak için kullanılır. Bilgi gerektiğinde önbellekten alınır. Uygulama önbellek düzenli aralıklarla, genellikle olaylarına yanıt olarak günceller gösterir bir içinde [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] değişti.  
  
 Önbelleğe alma avantajlarını Windows Presentation Foundation (WPF) denetimleri ve sunucu tarafı UI Otomasyon sağlayıcıları olan özel denetimler ile en dikkat çeken. Varsayılan sağlayıcı için gibi istemci tarafı sağlayıcıları erişirken küçük avantajı olan [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] kontrol eder.  
  
 Önbelleğe alma oluşur uygulama etkinleştirdiğinde bir <xref:System.Windows.Automation.CacheRequest> ve herhangi bir yöntemi veya döndüren özelliği kullanan bir <xref:System.Windows.Automation.AutomationElement>; Örneğin, <xref:System.Windows.Automation.AutomationElement.FindFirst%2A>, <xref:System.Windows.Automation.AutomationElement.FindAll%2A>. Yöntemlerinin <xref:System.Windows.Automation.TreeWalker> sınıfı bir özel durum; önbellek yalnızca yapılır, bir <xref:System.Windows.Automation.CacheRequest> parametre olarak belirtilen (örneğin, <xref:System.Windows.Automation.TreeWalker.GetFirstChild%28System.Windows.Automation.AutomationElement%2CSystem.Windows.Automation.CacheRequest%29?displayProperty=nameWithType>.  
  
 Bir olay işlenirken abone olduğunuzda ortaya de önbelleğe alma bir <xref:System.Windows.Automation.CacheRequest> etkindir. <xref:System.Windows.Automation.AutomationElement> Olay işleyicisine geçirilen bir olay kaynağı önbelleğe alınan özellikleri ve özgün tarafından belirtilen örneklerinin içerdiğinden <xref:System.Windows.Automation.CacheRequest>. Yapılan değişiklikler <xref:System.Windows.Automation.CacheRequest> olaya abone olduktan sonra herhangi bir etkisi yoktur.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Bir öğenin özellikleri ve denetim düzenleri önbelleğe alınır.  
  
<a name="Options_for_Caching"></a>   
## <a name="options-for-caching"></a>Önbelleğe alma seçenekleri  
 <xref:System.Windows.Automation.CacheRequest> Önbelleğe alma için aşağıdaki seçenekleri belirtir.  
  
<a name="Properties_to_Cache"></a>   
### <a name="properties-to-cache"></a>Önbellek özellikleri  
 Çağırarak önbelleğe özellikleri belirtebilirsiniz <xref:System.Windows.Automation.CacheRequest.Add%28System.Windows.Automation.AutomationProperty%29> isteği etkinleştirme önce her bir özellik için.  
  
<a name="Control_Patterns_to_Cache"></a>   
### <a name="control-patterns-to-cache"></a>Önbellek için Denetim desenleri  
 Önbellek için Denetim desenleri çağırarak belirtebilirsiniz <xref:System.Windows.Automation.CacheRequest.Add%28System.Windows.Automation.AutomationPattern%29> isteği etkinleştirme önce her deseni için. Bir desen önbelleğe alındığında özelliklerini otomatik olarak önbelleğe alınmamış; istediğiniz önbelleğe alınmış kullanarak özelliklerini belirtmelisiniz <xref:System.Windows.Automation.CacheRequest.Add%2A?displayProperty=nameWithType>.  
  
<a name="Scope_of_the_Caching"></a>   
### <a name="scope-and-filtering-of-caching"></a>Kapsam ve önbelleğe alma filtreleme  
 Özellikleri ve desenler ayarlayarak önbelleğine istediğiniz öğeleri belirtebilirsiniz <xref:System.Windows.Automation.CacheRequest.TreeScope%2A?displayProperty=nameWithType> isteği etkinleştirme önce özelliği. İstek etkin durumdayken, alınan öğeleri göre kapsamıdır. Örneğin, yalnızca ayarlarsanız <xref:System.Windows.Automation.TreeScope.Children>ve ardından almak bir <xref:System.Windows.Automation.AutomationElement>, özellikleri ve bu öğenin alt öğeleri desenlerini, olanları öğenin önbelleğe alınır. Önbelleğe alınan öğe için kendisini yapıldığından emin olmak için içermelidir <xref:System.Windows.Automation.TreeScope.Element> içinde <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> özelliği. Kapsamı ayarlayın mümkün değildir <xref:System.Windows.Automation.TreeScope.Parent> veya <xref:System.Windows.Automation.TreeScope.Ancestors>. Ancak, bir alt öğesi önbelleğe alındığında bir üst öğesi önbelleğe; Önbelleğe alma alt ve üst konusuna bakın.  
  
 Önbelleğe alma ölçüde da etkilenir <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A?displayProperty=nameWithType> özelliği. Varsayılan olarak, önbelleğe alma denetim görünümünde görüntülenen öğelerin gerçekleştirilir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı. Ancak, tüm öğeler veya içerik görünümünde görüntülenen öğelerin önbelleğe alma uygulamak için bu özelliği değiştirebilirsiniz.  
  
<a name="Strength_of_the_Element_References"></a>   
### <a name="strength-of-the-element-references"></a>Öğesi başvuruları gücünü  
 Aldığınızda bir <xref:System.Windows.Automation.AutomationElement>, varsayılan olarak tüm özellikleri ve desenler önbelleğe alınmamışsa olanlar da dahil, o öğenin erişebilirsiniz. Ancak, verimliliği için öğeye başvuru ayarlayarak yalnızca, önbelleğe alınan verilere başvuran belirleyebileceğiniz <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> özelliği <xref:System.Windows.Automation.CacheRequest> için <xref:System.Windows.Automation.AutomationElementMode.None>. Bu durumda, tüm önbelleğe alınmamış özellikleri ve alınan öğeleri desenlerini erişiminiz yok. Bu herhangi bir özellik aracılığıyla erişemeyeceğiniz anlamına gelir, <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> veya `Current` özelliği <xref:System.Windows.Automation.AutomationElement> veya herhangi bir denetim düzeni; veya bir desenle kullanarak alabilirsiniz <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> veya <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A>. Önbelleğe alınan düzenlerini esas dizisi özellikleri gibi almak yöntemleri çağırabilir <xref:System.Windows.Automation.SelectionPattern.SelectionPatternInformation.GetSelection%2A?displayProperty=nameWithType>, ancak hiçbir yapan denetiminde gibi eylemleri gerçekleştirmek değil <xref:System.Windows.Automation.InvokePattern.Invoke%2A?displayProperty=nameWithType>.  
  
 Nesnelere tam başvurular gerekmeyebilir bir uygulama, hazırlık bir ekran okuyucusu örneğidir <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A> ve <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> bir pencere öğelerinde özelliklerini değil gerekir, ancak <xref:System.Windows.Automation.AutomationElement> nesnelerinin kendilerini.  
  
<a name="Activating_the_CacheRequest"></a>   
## <a name="activating-the-cacherequest"></a>CacheRequest etkinleştirme  
 Önbelleğe alma gerçekleştirilir yalnızca <xref:System.Windows.Automation.AutomationElement> nesneleri alınır sırada bir <xref:System.Windows.Automation.CacheRequest> geçerli iş parçacığı için etkindir. Etkinleştirmek için iki yolla bir <xref:System.Windows.Automation.CacheRequest>.  
  
 Her zamanki gibi çağırmaktır <xref:System.Windows.Automation.CacheRequest.Activate%2A>. Bu yöntem uygulayan bir nesne döndürür <xref:System.IDisposable>. İstek etkin kaldığı sürece <xref:System.IDisposable> nesne yok. İçinde çağrısını için nesne ömrü denetlemek için en kolay yolu olan bir `using` (C#) veya `Using` (Visual Basic) engelle. Bu, özel durum oluşturuldu olsa bile, istek yığından Sil'i sağlar.  
  
 Önbellek isteği iç içe istediğinizde, yararlı olan, başka bir yolu çağırmaktır <xref:System.Windows.Automation.CacheRequest.Push%2A>. Bu istek bir yığında koyar ve etkinleştirir. İstek tarafından yığından kaldırılana kadar etkin kalır <xref:System.Windows.Automation.CacheRequest.Pop%2A>. Başka bir istek yığına gönderilen istek geçici olarak devre dışı haline gelir; yalnızca ilk istek yığında etkindir.  
  
<a name="Retrieving_Cached_Properties"></a>   
## <a name="retrieving-cached-properties"></a>Özellikleri önbelleğe alma  
 Bir öğenin önbelleğe alınmış özelliklerini aşağıdaki yöntemleri ve özellikleri alabilir.  
  
-   <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>  
  
-   <xref:System.Windows.Automation.AutomationElement.Cached%2A>  
  
 İstenen özellik önbellekte değilse, bir özel durum oluşturulur.  
  
 <xref:System.Windows.Automation.AutomationElement.Cached%2A>, gibi <xref:System.Windows.Automation.AutomationElement.Current%2A>, bir yapı üyeleri olarak tek tek özellikleri sunar. Ancak, bu yapıyı almak gerekmez; tek tek özellikleri doğrudan erişebilirsiniz. Örneğin, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A> özelliği elde edilebilir gelen `element.Cached.Name`, burada `element` olan bir <xref:System.Windows.Automation.AutomationElement>.  
  
<a name="Retrieving_Cached_Control_Patterns"></a>   
## <a name="retrieving-cached-control-patterns"></a>Denetim desenleri önbelleğe alma  
 Bir öğenin önbelleğe alınmış denetim desenleri aşağıdaki yöntemleri kullanarak alabilirsiniz.  
  
-   <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A>  
  
-   <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A>  
  
 Desen önbellekte değilse <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> bir özel durum oluşturur ve <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> döndürür `false`.  
  
 Denetim düzeni önbelleğe alınmış özelliklerini kullanarak alabilirsiniz `Cached` düzeni nesnesinin özelliği. Geçerli değerler üzerinden de alabilirsiniz `Current` özelliği, ancak yalnızca <xref:System.Windows.Automation.AutomationElementMode.None> zaman belirtilmedi <xref:System.Windows.Automation.AutomationElement> alınmadı. (<xref:System.Windows.Automation.AutomationElementMode.Full> varsayılan değerdir ve bu erişim geçerli değerlere izin verir.)  
  
<a name="Retrieving_Cached_Children_and_Parents"></a>   
## <a name="retrieving-cached-children-and-parents"></a>Alt ve üst önbelleğe alma  
 Aldığınızda bir <xref:System.Windows.Automation.AutomationElement> ve istek bu öğenin alt öğeleri için önbelleğe alma <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> özelliği isteği, alt öğelerini almak daha sonra mümkündür <xref:System.Windows.Automation.AutomationElement.CachedChildren%2A> , alınan öğesi özelliği.  
  
 Varsa <xref:System.Windows.Automation.TreeScope.Element> dahil edildiğinden önbellek isteği kapsamında istek kök öğesinin sonradan kullanılabilir <xref:System.Windows.Automation.AutomationElement.CachedParent%2A> herhangi bir alt öğe özelliği.  
  
> [!NOTE]
>  Üst veya üst isteğin kök öğesinin önbelleğe alamıyor.  
  
<a name="Updating_the_Cache"></a>   
## <a name="updating-the-cache"></a>Önbelleği güncelleştiriliyor  
 Yalnızca hiçbir şey değişiklikleri sürece geçerli önbelleğidir [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Uygulamanız, önbellekte, genellikle olaylarına yanıt olarak güncelleştirmek için sorumludur.  
  
 Bir olay işlenirken abone olursanız bir <xref:System.Windows.Automation.CacheRequest> olduğu etkin elde bir <xref:System.Windows.Automation.AutomationElement> olay işleyicisi temsilciniz çağrıldığında olay kaynağı olarak güncelleştirilmiş bir önbelleğe sahip. Çağırarak bir öğe için önbelleğe alınan bilgileri güncelleştirebilir <xref:System.Windows.Automation.AutomationElement.GetUpdatedCache%2A>. Özgün geçirebilirsiniz <xref:System.Windows.Automation.CacheRequest> önceden önbelleğe alınan tüm bilgileri güncelleştirmek için.  
  
 Önbellek güncelleştirme var olan özelliklerini değiştirmez <xref:System.Windows.Automation.AutomationElement> başvuruları.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İstemciler İçin UI Otomasyonu Olayları](../../../docs/framework/ui-automation/ui-automation-events-for-clients.md)  
 [UI Otomasyonunda Önbelleğe Almayı Kullanma](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)  
 [FetchTimer örnek](http://msdn.microsoft.com/library/5b7d3294-de22-4f24-b2d6-d4785a304b90)
