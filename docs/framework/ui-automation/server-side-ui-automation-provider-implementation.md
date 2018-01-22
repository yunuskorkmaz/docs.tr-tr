---
title: "Sunucu Tarafı UI Otomasyonu Sağlayıcıyı Uygulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- server-side UI Automation provider implementation
- UI Automation, server-side provider implementation
- provider implementation, UI Automation
ms.assetid: 6acc6d08-bd67-4e2e-915c-9c1d34eb86fe
caps.latest.revision: "39"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: d25f561444cd672e8842711025f4299c375d6bb4
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="server-side-ui-automation-provider-implementation"></a>Sunucu Tarafı UI Otomasyonu Sağlayıcıyı Uygulama
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. Hakkında en yeni bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Otomasyon API: UI Otomasyonu](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu bölüm, özel bir denetim için sunucu tarafı UI Otomasyonu sağlayıcıyı uygulama açıklar.  
  
 Uygulamasını [!INCLUDE[TLA#tla_wpf](../../../includes/tlasharptla-wpf-md.md)] öğeleri ve olmayan-[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] öğeleri (olanlar için tasarlanmış gibi [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]) temelde farklıdır. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]öğeleri için destek sağlar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] türetilmiş sınıf aracılığıyla <xref:System.Windows.Automation.Peers.AutomationPeer>. Olmayan[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] öğeleri uygulamaları sağlayıcısı arabirimleri aracılığıyla destek sağlar.  
  
<a name="Security_Considerations"></a>   
## <a name="security-considerations"></a>Güvenlik Değerlendirmeleri  
 Kısmi güven ortamında çalışabilmeniz için sağlayıcıları yazılması gerekir. UIAutomationClient.dll kısmi güven altında çalıştırmak için yapılandırılmadığından, sağlayıcı kodunuzu bu derleme başvuru vermemelisiniz. Bunu varsa, kodu bir tam güven ortamında çalıştırıldı ancak bir kısmi güven ortamında başarısız.  
  
 Özellikle, sınıflardan UIAutomationClient.dll de gibi alanları kullanmayın <xref:System.Windows.Automation.AutomationElement>. Bunun yerine, UIAutomationTypes.dll, sınıflarda eşdeğer alanları gibi kullandığınız <xref:System.Windows.Automation.AutomationElementIdentifiers>.  
  
<a name="Provider_Implementation_by_WPF_Elements"></a>   
## <a name="provider-implementation-by-windows-presentation-foundation-elements"></a>Windows Presentation Foundation öğeler tarafından sağlayıcı uygulaması  
 Bu konu hakkında daha fazla bilgi için lütfen bkz [bir WPF özel denetiminin UI Otomasyonu](../../../docs/framework/wpf/controls/ui-automation-of-a-wpf-custom-control.md).  
  
<a name="Provider_Implementation_by_non_WPF_Elements"></a>   
## <a name="provider-implementation-by-non-wpf-elements"></a>WPF olmayan öğeler tarafından sağlayıcı uygulaması  
 Özel denetimleri parçası olan [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] framework ancak, yönetilen kodda yazılır (çoğunlukla bunlar [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] denetimleri), için destek sağlayan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] arabirimleri uygulayarak. Her öğe bir sonraki bölüm ilk tabloda listelenen arabirimler en az birini uygulamanız gerekir. Buna ek olarak, öğenin bir veya daha fazla denetim düzenleri destekliyorsa, her denetim düzeni için uygun arabirimi uygulamalıdır.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Sağlayıcı projesini aşağıdaki derlemeler başvurmalıdır:  
  
-   UIAutomationProviders.dll  
  
-   UIAutomationTypes.dll  
  
-   WindowsBase.dll  
  
  
<a name="Provider_Interfaces"></a>   
### <a name="provider-interfaces"></a>Sağlayıcı arabirimleri  
 Her [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sağlayıcısı aşağıdaki arabirimlerinden biri, uygulamanız gerekir.  
  
|Arabirim|Açıklama|  
|---------------|-----------------|  
|<xref:System.Windows.Automation.Provider.IRawElementProviderSimple>|Denetim desenleri ve özellikler için destek dahil olmak üzere bir pencere içinde barındırılan basit bir denetim için işlevsellik sağlar.|  
|<xref:System.Windows.Automation.Provider.IRawElementProviderFragment>|Öğesinden devralınan <xref:System.Windows.Automation.Provider.IRawElementProviderSimple>. Parça içinde gezinme dahil olmak üzere, odak ayarlama ve sınırlayıcı dikdörtgenini öğenin döndürme karmaşık denetim içinde bir öğe için işlevsellik ekler.|  
|<xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>|Öğesinden devralınan <xref:System.Windows.Automation.Provider.IRawElementProviderFragment>. Bir alt öğesi belirtilen koordinatlarda bulma ve tüm denetim odağı durumunu ayarlama gibi karmaşık denetiminde, kök öğe için işlevsellik ekler.|  
  
 Aşağıdaki arabirimleri eklenmiş işlevi sağlar ancak uygulanması için gerekli değildir.  
  
|Arabirim|Açıklama|  
|---------------|-----------------|  
|<xref:System.Windows.Automation.Provider.IRawElementProviderAdviseEvents>|Olaylar için istekleri izlemek üzere sağlayıcıyı etkinleştirir.|  
|<xref:System.Windows.Automation.Provider.IRawElementProviderHwndOverride>|İçindeki Windows tabanlı öğelerin yeniden konumlandırma etkinleştirir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacının bir parçası.|  
  
 Diğer tüm arabirimlerde <xref:System.Windows.Automation.Provider> ad alanı olan denetim düzeni desteği.  
  
<a name="Requirements_for_Non_WPF_Providers"></a>   
### <a name="requirements-for-non-wpf-providers"></a>WPF olmayan sağlayıcıları için gereksinimleri  
 İle iletişim kurmak için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], denetim işlevleri aşağıdaki ana alanları uygulamanız gerekir:  
  
|İşlevi|Uygulama|  
|-------------------|--------------------|  
|Sağlayıcıyı gösterme[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Denetim penceresine gönderilen WM_GETOBJECT iletisine yanıt olarak, uygulayan nesnenin dönüş <xref:System.Windows.Automation.Provider.IRawElementProviderSimple> (veya türetilmiş bir arabirim). Parçaları için bu sağlayıcı için parça kök olmalıdır.|  
|Özellik değerlerini sağlayın|Uygulama <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPropertyValue%2A> sağlayabilir veya değerlerini geçersiz kılar.|  
|İstemci denetimi ile etkileşim kurmak etkinleştirin|Uygulama Denetim düzenleri gibi desteği arabirimleri <xref:System.Windows.Automation.Provider.IInvokeProvider>. Uygulamanızda bu deseni sağlayıcılarını döndüren <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A>.|  
|Olayları Yükselt|Statik yöntemlerinden birini çağrı <xref:System.Windows.Automation.Provider.AutomationInteropProvider> istemci dinlediği bir olay yükseltmek için.|  
|Gezinti ve bir parçası içinde odaklanan etkinleştir|Uygulama <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> parça içinde her öğe için. (Gerekli bir parçası olmayan öğeler için.)|  
|Odaklanma ve alt öğesi bir parçasında konumunu etkinleştir|Uygulama <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>. (Gerekli olmayan öğeleri kökleri parçalara değil için.)|  
  
<a name="Property_Values_in_Non_WPF_Providers"></a>   
### <a name="property-values-in-non-wpf-providers"></a>Özellik değerlerini WPF olmayan sağlayıcıları  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]özel denetimler için sağlayıcıları Otomasyon sistemi tarafından ve aynı zamanda istemci uygulamaları tarafından kullanılan belirli özellikleri desteklemesi gerekir. Windows (Cwnd'lerden) barındırılan öğelerin [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bazı özellikler varsayılan pencere sağlayıcıdan alabilir, ancak diğer özel sağlayıcıdan edinmeniz gerekir.  
  
 Sağlayıcıları temel HWND denetimleri için genellikle (alan değerlerini tarafından tanımlanan) aşağıdaki özellikleri sağlayan gerekmez:  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.ProcessIdProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.ClassNameProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.HasKeyboardFocusProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.IsPasswordProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>  
  
-   <xref:System.Windows.Automation.AutomationElementIdentifiers.RuntimeIdProperty>  
  
> [!NOTE]
>  <xref:System.Windows.Automation.AutomationElementIdentifiers.RuntimeIdProperty> Basit bir öğe veya parça bir pencerede barındırılan kök penceresinden alınır; ancak, parça öğeleri (örneğin, bir liste kutusu liste öğeleri) kök altındaki kendi tanımlayıcıları sağlamanız gerekir. Daha fazla bilgi için bkz. <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.GetRuntimeId%2A>.  
>   
>  <xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty> Sağlayıcıları barındırılan için döndürülmesi gereken bir [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] denetim. Bu durumda, varsayılan pencere sağlayıcısı doğru değeri alamadı olabilir.  
>   
>  <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty> Genellikle ana sağlayıcısı tarafından sağlanır. Örneğin, bir özel denetim türetilir <xref:System.Windows.Forms.Control>, adı türetildiği `Text` denetiminin özelliği.  
  
 Örnek kod, bkz: [UI Otomasyon sağlayıcı dönüş özelliklerinden](../../../docs/framework/ui-automation/return-properties-from-a-ui-automation-provider.md).  
  
<a name="Events_in_Non_WPF_Providers"></a>   
### <a name="events-in-non-wpf-providers"></a>WPF olmayan sağlayıcıları olayları  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]sağlayıcıları UI durumu değişiklikleri istemci uygulamalarının bildirmek için olayları tetiklemelidir. Aşağıdaki yöntemlerden olayları yükseltmek için kullanılır.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Windows.Automation.Provider.AutomationInteropProvider.RaiseAutomationEvent%2A>|Denetim desenleri tarafından tetiklenen olaylar dahil olmak üzere çeşitli olayları başlatır.|  
|<xref:System.Windows.Automation.Provider.AutomationInteropProvider.RaiseAutomationPropertyChangedEvent%2A>|Bir olay başlatır, bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özelliği değişti.|  
|<xref:System.Windows.Automation.Provider.AutomationInteropProvider.RaiseStructureChangedEvent%2A>|Bir olay başlatır, yapısını [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç değişti; Örneğin, kaldırma veya öğenin eklenmesi tarafından.|  
  
 İstemci, bir şeyin gerçekleşmesini bildirmek için bir olay amacı [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)], etkinlik tarafından tetiklenen olup olmadığına bakılmaksızın [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sisteminin kendisi. Örneğin, tarafından tanımlanan olay <xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent> denetimi, doğrudan kullanıcı girişi yoluyla veya istemci uygulaması arama tarafından çağrılan her oluşmalıdır <xref:System.Windows.Automation.InvokePattern.Invoke%2A>.  
  
 Performansı iyileştirmek için bir sağlayıcı seçmeli olarak olayları yükseltmek veya hiçbir istemci uygulaması bunları almak için kayıtlı olan olay yok hiç oluştur. Aşağıdaki yöntemlerden iyileştirme için kullanılır.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Windows.Automation.Provider.AutomationInteropProvider.ClientsAreListening%2A>|Statik bu özellik, tüm istemci uygulamaları için abone olup olmadığını belirtir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olaylar.|  
|<xref:System.Windows.Automation.Provider.IRawElementProviderAdviseEvents>|Bu arabirimde bir parça kök sağlayıcının uyarlamasını istemcileri kaydetmek ve parça olayları için olay işleyicileri kaydı tavsiye sağlar.|  
  
<a name="Non_WPF_Provider_Navigation"></a>   
### <a name="non-wpf-provider-navigation"></a>WPF olmayan sağlayıcı gezinme  
 Bir pencere (HWND) barındırılan özel bir düğme gibi basit denetimler için sağlayıcıları içinde gezinme desteklemek gerek yoktur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı. Gezinti öğesi gelen ve giden uygulamasında belirtilen konak penceresi için varsayılan sağlayıcıyı tarafından işlenir <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.HostRawElementProvider%2A>. Ancak, karmaşık bir özel denetim için bir sağlayıcı uyguladığınızda eşdüzey düğümleri arasında ve parça kök düğümünü ve alt öğeleri arasında gezinme desteklemesi gerekir.  
  
> [!NOTE]
>  Kök dışında başka bir parça öğeleri döndürmelidir bir `null` gelen başvuru <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.HostRawElementProvider%2A>, çünkü bunlar doğrudan bir pencerede barındırılan değil ve hiç varsayılan sağlayıcı Gezinti bunlara gelen ve giden destekleyebilir.  
  
 Parça yapısını uygulamanız tarafından belirlenir <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A>. Her olası yönünden için her parça, bu yöntem bu yönde öğesinin sağlayıcı nesnesi döndürür. Olup olmadığını hiçbir öğe bu yönde, yöntem bir `null` başvuru.  
  
 Parça kök gezinme yalnızca alt öğeleri destekler. Yönü olduğunda bir liste kutusu listesindeki ilk öğeyi örneğin döndürür <xref:System.Windows.Automation.Provider.NavigateDirection.FirstChild>ve yönü olduğunda son öğeyi <xref:System.Windows.Automation.Provider.NavigateDirection.LastChild>. Parça kök Gezinti bir üst veya eşdüzey desteklemiyor; Bu konak penceresi sağlayıcı tarafından işlenir.  
  
 Kök olmayan bir parça öğelerden herhangi bir eşdüzey ve sahip oldukları alt ve üst gezinti desteklemesi gerekir.  
  
<a name="Non_WPF_Provider_Reparenting"></a>   
### <a name="non-wpf-provider-reparenting"></a>WPF olmayan sağlayıcı Reparenting  
 Açılır pencereler gerçekten üst düzey Windows ve varsayılan olarak bu nedenle görüntülenmesini [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] masaüstünün alt öğeleri olarak ağacı. Çoğu durumda, ancak, açılır pencereleri mantıksal olarak başka bir denetim alt değildir. Örneğin, bir birleşik giriş kutusu açılan listesi mantıksal olarak bir alt birleşik giriş kutusu öğesi değil. Benzer şekilde, menüsü açılır pencere mantıksal olarak bir alt menü öğesi değil. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]ilişkili denetim alt olmasını görünecekleri açılır pencereleri üst öğesini değiştirme için destek sağlar.  
  
 Açılır pencere üst öğesini değiştirme için:  
  
1.  Açılır pencere için bir sağlayıcı oluşturun. Bu açılır pencere sınıfı önceden bilinen gerektirir.  
  
2.  Dizinindeymiş gibi kendi içinde bir denetim tüm özellikleri ve bu açılır pencere için her zamanki gibi desenleri uygular.  
  
3.  Uygulama <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.HostRawElementProvider%2A> şekilde alınan değeri döndürecek şekilde özelliği <xref:System.Windows.Automation.Provider.AutomationInteropProvider.HostProviderFromHandle%2A>, parametre açılır pencere pencere tanıtıcısı olduğu.  
  
4.  Uygulama <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A> açılır pencere ve mantıksal alt öğelerine ve eşdüzey alt öğeleri arasında gezinti düzgün mantıksal üst işlenir şekilde kendi üst için.  
  
 Zaman [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] açılır pencere karşılaştığında gezinti varsayılandan kılınır ve Masaüstü alt sitesi olarak karşılaşıldığında açılır pencere üzerinde atlar tanır. Bunun yerine, düğüm yalnızca parça ulaşılabilir olur.  
  
 Reparenting denetim herhangi bir sınıf pencerenin barındırabildiği durumları için uygun değil. Örneğin, bir rebar HWND kendi bantları içinde herhangi bir türde barındırabilir. Bu durumda, işlemek için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sonraki bölümde açıklandığı gibi HWND yeniden konumlandırma, alternatif bir biçimini destekler.  
  
<a name="Non_WPF_Provider_Repositioning"></a>   
### <a name="non-wpf-provider-repositioning"></a>WPF olmayan sağlayıcısı yeniden konumlandırma  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]parçaları her penceresinde (HWND) bulunan iki veya daha fazla öğe içeriyor olabilir. Her HWND içeren bir HWND alt HWND göz önünde bulundurur kendi varsayılan sağlayıcı olduğundan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç varsayılan olarak, gösterir Cwnd'lerden parçadaki üst penceresinin alt öğesi. Çoğu durumda bu arzu davranıştır, ancak mantıksal yapısı eşleşmediği için bazen bu karışıklığa yol açabilir [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
 Rebar denetimiyle bu iyi bir örneği bulunmaktadır. Bir rebar bantları, her biri bir HWND tabanlı denetim araç, bir düzenleme kutusu veya açılan kutu gibi sırayla içerebilir içerir. HWND rebar için varsayılan pencere sağlayıcı bant denetim Cwnd'lerden alt öğesi olarak görür ve rebar sağlayıcı bantları alt öğesi olarak görür. Olduğundan HWND sağlayıcısı ve rebar sağlayıcısı dağıtımınızla çalışma ve bunların alt öğeleri birleştirme bantları ve HWND tabanlı denetimler rebar alt öğesi olarak görünür. Mantıksal olarak, ancak yalnızca bantları rebar alt öğesi olarak görünmesi gereken ve her bant provider içerdiği denetimi için varsayılan HWND sağlayıcısıyla eşleştirilmek.  
  
 Bunu gerçekleştirmek için bantları temsil eden alt kümesi rebar parça kök sağlayıcısı kullanıma sunar. Her bant özellikleri ve desenler getirebilir tek bir sağlayıcı içeriyor. Uygulamaya <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.HostRawElementProvider%2A>, bant provider çağırarak edinir HWND denetimi için varsayılan pencere sağlayıcının döndürdüğü <xref:System.Windows.Automation.Provider.AutomationInteropProvider.HostProviderFromHandle%2A>, denetimin pencere tanıtıcının geçen. Son olarak, rebar için parça kök sağlayıcıyı uygular <xref:System.Windows.Automation.Provider.IRawElementProviderHwndOverride> arabirimi ve uygulamaya <xref:System.Windows.Automation.Provider.IRawElementProviderHwndOverride.GetOverrideProviderForHwnd%2A> belirtilen HWND içinde yer alan denetimi için uygun bant provider döndürür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [UI Otomasyonu Sağlayıcılara Genel Bakış](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)  
 [Sunucu Tarafı UI Otomasyonu Sağlayıcıyı Gösterme](../../../docs/framework/ui-automation/expose-a-server-side-ui-automation-provider.md)  
 [UI Otomasyonu Sağlayıcı Dönüş Özellikleri](../../../docs/framework/ui-automation/return-properties-from-a-ui-automation-provider.md)  
 [UI Otomasyonu Sağlayıcıda Olay Tetikleme](../../../docs/framework/ui-automation/raise-events-from-a-ui-automation-provider.md)  
 [UI Otomasyonu Parça Sağlayıcıyıda Gezinmeyi Etkinleştirme](../../../docs/framework/ui-automation/enable-navigation-in-a-ui-automation-fragment-provider.md)  
 [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Basit sağlayıcı örneği](http://msdn.microsoft.com/library/c10a6255-e8dc-494b-a051-15111b47984a)  
 [Parça sağlayıcı örneği](http://msdn.microsoft.com/library/778ef1bc-8610-4bc9-886e-aeff94a8a13e)
