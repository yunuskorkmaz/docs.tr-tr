---
title: UI Otomasyonda Önbelleğe Alma
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation caching in clients
- caching, UI Automation clients
ms.assetid: 94c15031-4975-43cc-bcd5-c9439ed21c9c
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 4571af701ea28c3b7dbecbb1b1a82e7093c2831e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54646467"
---
# <a name="caching-in-ui-automation-clients"></a>UI Otomasyonda Önbelleğe Alma
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu konu, önbelleğe alma tanıtır [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellikleri ve denetim desenleri.  
  
 İçinde [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], önbelleğe alma verileri önceden getirme anlamına gelir. Verileri daha fazla çapraz proses haberleşmesi erişilebilir. Önbelleğe alma genellikle UI Otomasyonu istemci uygulamalar tarafından özellikleri ve denetim düzenleri toplu almak için kullanılır. Bilgi ardından önbellekten gerektiği gibi alınır. Uygulama önbelleği düzenli olarak, genellikle olaylara yanıt olarak güncelleştirir gösteren bir içinde [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] değişti.  
  
 Önbelleğe alma avantajlarını Windows Presentation Foundation (WPF) denetimleri ve sunucu tarafı UI Otomasyonu sağlayıcıları özel denetimler ile en belirgin görüntüleniyor. İçin varsayılan sağlayıcıları gibi istemci tarafı sağlayıcı erişirken daha az avantajı olan [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] kontrol eder.  
  
 Önbelleğe alma oluşur uygulamayı etkinleştirir bir <xref:System.Windows.Automation.CacheRequest> ve ardından herhangi bir yöntemi veya döndüren bir özelliği kullanan bir <xref:System.Windows.Automation.AutomationElement>; Örneğin, <xref:System.Windows.Automation.AutomationElement.FindFirst%2A>, <xref:System.Windows.Automation.AutomationElement.FindAll%2A>. Yöntemlerinin <xref:System.Windows.Automation.TreeWalker> sınıfı bir özel durum; önbellek yalnızca yapılır, bir <xref:System.Windows.Automation.CacheRequest> parametre olarak belirtilen (örneğin, <xref:System.Windows.Automation.TreeWalker.GetFirstChild%28System.Windows.Automation.AutomationElement%2CSystem.Windows.Automation.CacheRequest%29?displayProperty=nameWithType>.  
  
 Ayrıca önbelleğe alma sırasında bir olaya abone olduğunuzda oluşur bir <xref:System.Windows.Automation.CacheRequest> etkindir. <xref:System.Windows.Automation.AutomationElement> , Olay işleyicisine geçirilen bir olayının kaynağı, özgün tarafından belirtilen desenleri ve önbelleğe alınan özellikler içerdiğinden <xref:System.Windows.Automation.CacheRequest>. Yapılan tüm değişiklikler <xref:System.Windows.Automation.CacheRequest> olaya abone olduktan sonra herhangi bir etkisi yoktur.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Öğesinin özelliklerini ve denetim desenleri önbelleğe alınır.  
  
<a name="Options_for_Caching"></a>   
## <a name="options-for-caching"></a>Önbelleğe alma seçenekleri  
 <xref:System.Windows.Automation.CacheRequest> Önbelleğe almak için aşağıdaki seçenekleri belirtir.  
  
<a name="Properties_to_Cache"></a>   
### <a name="properties-to-cache"></a>Önbellek özellikleri  
 Çağırarak önbellek özellikleri belirtebilirsiniz <xref:System.Windows.Automation.CacheRequest.Add%28System.Windows.Automation.AutomationProperty%29> etkinleştirme isteği önce her bir özellik için.  
  
<a name="Control_Patterns_to_Cache"></a>   
### <a name="control-patterns-to-cache"></a>Önbellek için Denetim desenleri  
 Önbellek için Denetim desenleri çağırarak belirleyebilirsiniz <xref:System.Windows.Automation.CacheRequest.Add%28System.Windows.Automation.AutomationPattern%29> etkinleştirme isteği önce her desen için. Bir deseni önbelleğe alınır, özelliklerini otomatik olarak önbelleğe alınmaz; istediğiniz önbelleğe alınmış kullanarak özellikleri belirtmelisiniz <xref:System.Windows.Automation.CacheRequest.Add%2A?displayProperty=nameWithType>.  
  
<a name="Scope_of_the_Caching"></a>   
### <a name="scope-and-filtering-of-caching"></a>Kapsamı ve önbelleğe alma filtreleme  
 Özellikleri ve desenleri ayarlayarak önbelleğine istediğiniz öğeleri belirtebilirsiniz <xref:System.Windows.Automation.CacheRequest.TreeScope%2A?displayProperty=nameWithType> önce istek etkinleştirme özelliği. İsteği etkin durumdayken, alınan öğelerin göreli kapsamıdır. Örneğin, yalnızca ayarlarsanız <xref:System.Windows.Automation.TreeScope.Children>ve ardından bir <xref:System.Windows.Automation.AutomationElement>, özellikleri ve bu öğenin alt öğeleri desenlerini olanları öğesi, önbelleğe alınır. Önbelleğe alınan öğe için kendisini yapıldığından emin olmak için içermelidir <xref:System.Windows.Automation.TreeScope.Element> içinde <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> özelliği. Kapsamını ayarlamak mümkün değildir <xref:System.Windows.Automation.TreeScope.Parent> veya <xref:System.Windows.Automation.TreeScope.Ancestors>. Bir alt öğesi önbelleğe alınır, ancak bir üst öğenin önbelleğe alınabilir; Alınırken önbelleğe alt ve üst öğeler bu konusuna bakın.  
  
 Önbelleğe alma ölçüde da etkilenir <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A?displayProperty=nameWithType> özelliği. Varsayılan olarak, önbelleğe alma denetim görünümünde görüntülenen öğelerin gerçekleştirilir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç. Ancak, tüm öğeleri veya içerik görünümünde görüntülenen öğelerin önbelleğe alma uygulamak için bu özelliği değiştirebilirsiniz.  
  
<a name="Strength_of_the_Element_References"></a>   
### <a name="strength-of-the-element-references"></a>Öğe başvurularını gücü  
 Aldığınızda bir <xref:System.Windows.Automation.AutomationElement>, varsayılan olarak tüm özelliklerini ve önbelleğe alınmadığını olanlar da dahil, o öğenin desenleri erişebilirsiniz. Ancak, daha fazla verimlilik için öğeye başvuru ayarlayarak yalnızca önbelleğe alınmış verilere başvuran belirtebilirsiniz <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> özelliği <xref:System.Windows.Automation.CacheRequest> için <xref:System.Windows.Automation.AutomationElementMode.None>. Bu durumda, önbelleğe alınmamış özeliklerini ve alınan öğelerin desenleri erişiminiz yok. Bu herhangi bir özelliği aracılığıyla erişemeyeceğiniz anlamına gelir, <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> veya `Current` özelliği <xref:System.Windows.Automation.AutomationElement> veya herhangi bir denetim düzeni; ya da bir desen kullanarak alabilirsiniz <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> veya <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A>. Önbelleğe alınan eğilimlere dizi özellikleri gibi almak yöntemleri çağırabilirsiniz <xref:System.Windows.Automation.SelectionPattern.SelectionPatternInformation.GetSelection%2A?displayProperty=nameWithType>, ancak tüm eylemler gerçekleştiren denetimde gibi değil <xref:System.Windows.Automation.InvokePattern.Invoke%2A?displayProperty=nameWithType>.  
  
 Uygulamanın tam nesnelere başvurular gerekmeyebilir, önceden getirme bir ekran okuyucu örneğidir <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A> ve <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> pencerede öğelerin özelliklerini değil gerekir ancak <xref:System.Windows.Automation.AutomationElement> nesnelerinin kendileri.  
  
<a name="Activating_the_CacheRequest"></a>   
## <a name="activating-the-cacherequest"></a>CacheRequest etkinleştirme  
 Önbelleğe alma işlemi gerçekleştirildiğinde yalnızca <xref:System.Windows.Automation.AutomationElement> nesneleri alındığı sırada bir <xref:System.Windows.Automation.CacheRequest> geçerli iş parçacığı için etkin. Etkinleştirmek için iki yolla bir <xref:System.Windows.Automation.CacheRequest>.  
  
 Her zamanki şekilde çağırmaktır <xref:System.Windows.Automation.CacheRequest.Activate%2A>. Bu yöntem uygulayan bir nesne döndürür <xref:System.IDisposable>. İstek etkin kaldığı sürece <xref:System.IDisposable> nesne yok. İçinde çağrısını için nesnenin ömrünü denetlemek için en kolay yolu olan bir `using` (C#) veya `Using` (Visual Basic) blok. Bu isteği bir özel durum olsa bile yığından POP, sağlar.  
  
 Önbellek isteği'iç içe yerleştirmek istediğinizde kullanışlıdır, başka bir yol çağırmaktır <xref:System.Windows.Automation.CacheRequest.Push%2A>. Bu isteği bir yığında koyar ve etkinleştirir. İstek tarafından yığından kaldırılana kadar etkin kalır <xref:System.Windows.Automation.CacheRequest.Pop%2A>. Başka bir istek yığın üstüne itilir, istek, geçici olarak devre dışı olur; yalnızca üst istek yığın üzerinde etkin değil.  
  
<a name="Retrieving_Cached_Properties"></a>   
## <a name="retrieving-cached-properties"></a>Özellikleri önbelleğe alma  
 Aşağıdaki yöntemleri ve özellikleri öğenin önbelleğe alınmış özelliklerini alabilir.  
  
-   <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>  
  
-   <xref:System.Windows.Automation.AutomationElement.Cached%2A>  
  
 İstenen özellik önbellekte değilse bir özel durum oluşturulur.  
  
 <xref:System.Windows.Automation.AutomationElement.Cached%2A>, gibi <xref:System.Windows.Automation.AutomationElement.Current%2A>, bir yapının üyelerine ayrı ayrı özellikler sunar. Ancak, bu yapı almak gerekmez; tek tek özellikler doğrudan erişebilirsiniz. Örneğin, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A> özelliği, gelen edinilebilir `element.Cached.Name`burada `element` olduğu bir <xref:System.Windows.Automation.AutomationElement>.  
  
<a name="Retrieving_Cached_Control_Patterns"></a>   
## <a name="retrieving-cached-control-patterns"></a>Denetim desenlerini önbelleğe alma  
 Bir öğenin önbelleğe alınmış denetim düzenleri aşağıdaki yöntemleri kullanarak alabilirsiniz.  
  
-   <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A>  
  
-   <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A>  
  
 Desen önbellekte değilse <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> özel durum harekete ve <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> döndürür `false`.  
  
 Önbelleğe alınan bir denetim düzeni özelliklerini kullanarak alabilirsiniz `Cached` deseni nesnesinin özelliği. Geçerli değerler üzerinden de alabilirsiniz `Current` özelliği, ancak yalnızca <xref:System.Windows.Automation.AutomationElementMode.None> zaman belirtilmedi <xref:System.Windows.Automation.AutomationElement> alınmadı. (<xref:System.Windows.Automation.AutomationElementMode.Full> varsayılan değerdir ve bu erişim geçerli değerlere izin verir.)  
  
<a name="Retrieving_Cached_Children_and_Parents"></a>   
## <a name="retrieving-cached-children-and-parents"></a>Önbelleğe alma alt ve üst öğeler  
 Aldığınızda bir <xref:System.Windows.Automation.AutomationElement> ve isteği bu öğenin alt öğeleri için önbelleğe alma <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> özelliği isteği, alt öğeleri almak başvurmanın mümkün olması <xref:System.Windows.Automation.AutomationElement.CachedChildren%2A> aldığınız öğesinin özelliği.  
  
 Varsa <xref:System.Windows.Automation.TreeScope.Element> gelen önbellek isteği kapsamında, isteğin kök öğe daha sonra kullanılabilir <xref:System.Windows.Automation.AutomationElement.CachedParent%2A> herhangi bir alt öğelerinin özelliği.  
  
> [!NOTE]
>  Üst öğeleri veya üst öğelerinden oluşan isteğin kök öğe önbelleğe alamıyor.  
  
<a name="Updating_the_Cache"></a>   
## <a name="updating-the-cache"></a>Önbelleği güncelleştiriliyor  
 Yalnızca bir şey de değişiklikleri sürece geçerli önbellektir [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Uygulama, önbellek, genellikle olaylara yanıt olarak güncelleştirmek için sorumludur.  
  
 Bir olay işlenirken abone olursanız bir <xref:System.Windows.Automation.CacheRequest> olan etkin elde bir <xref:System.Windows.Automation.AutomationElement> , olay işletici temsilcisi çağrıldığında, olay kaynağı olarak güncelleştirilmiş bir önbellek. Çağırarak bir öğe için önbelleğe alınan bilgileri güncelleştirebilir <xref:System.Windows.Automation.AutomationElement.GetUpdatedCache%2A>. Özgün geçirebilirsiniz <xref:System.Windows.Automation.CacheRequest> önceden önbelleğe alınan tüm bilgileri güncelleştirilecek.  
  
 Önbellek güncelleştirme var olan tüm özelliklerini değiştirmez <xref:System.Windows.Automation.AutomationElement> başvuruları.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [İstemciler İçin UI Otomasyonu Olayları](../../../docs/framework/ui-automation/ui-automation-events-for-clients.md)
- [UI Otomasyonunda Önbelleğe Almayı Kullanma](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
- [FetchTimer örnek](https://msdn.microsoft.com/library/5b7d3294-de22-4f24-b2d6-d4785a304b90)
