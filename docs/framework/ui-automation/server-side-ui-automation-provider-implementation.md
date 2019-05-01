---
title: Sunucu Tarafı UI Otomasyonu Sağlayıcıyı Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- server-side UI Automation provider implementation
- UI Automation, server-side provider implementation
- provider implementation, UI Automation
ms.assetid: 6acc6d08-bd67-4e2e-915c-9c1d34eb86fe
ms.openlocfilehash: 3b3e69d1c52b98822a4cf3b75de74466e1dc68f0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62033203"
---
# <a name="server-side-ui-automation-provider-implementation"></a>Sunucu Tarafı UI Otomasyonu Sağlayıcıyı Uygulama
> [!NOTE]
>  Bu belge yönetilen kullanmak isteyen .NET Framework için tasarlanan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tanımlanan sınıflar <xref:System.Windows.Automation> ad alanı. En son bilgileri [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], bkz: [Windows Automation API: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Bu bölümde, nasıl özel bir denetim için bir sunucu tarafı UI Otomasyon sağlayıcısında uygulanacağı açıklanmaktadır.  
  
 Windows Presentation Foundation (WPF) öğeleri ve olmayan uygulama-[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] öğeleri (olanlar için tasarlanmış gibi [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]) tamamen farklıdır. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] öğeleri için destek sağlar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] türetilmiş sınıf aracılığıyla <xref:System.Windows.Automation.Peers.AutomationPeer>. Olmayan[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] öğeleri uygulamaları sağlayıcısı arabirimleri aracılığıyla destek sağlar.  
  
<a name="Security_Considerations"></a>   
## <a name="security-considerations"></a>Güvenlik Değerlendirmeleri  
 Kısmi güven ortamında çalışabilmeniz için sağlayıcıları yazılması gerekir. Kısmi güven altında çalıştırılacak UIAutomationClient.dll yapılandırılmadığından, sağlayıcı kodunuzu derlemeye başvurmamalıdır. Bunu yapar, kod tam güven ortamında çalıştırmak ancak ardından bir kısmi güven ortamında başarısız.  
  
 Özellikle, sınıflardan UIAutomationClient.dll olanlar gibi alanları kullanmayın <xref:System.Windows.Automation.AutomationElement>. Bunun yerine, eşdeğer alanlara UIAutomationTypes.dll, sınıflarda gibi kullanın <xref:System.Windows.Automation.AutomationElementIdentifiers>.  
  
<a name="Provider_Implementation_by_WPF_Elements"></a>   
## <a name="provider-implementation-by-windows-presentation-foundation-elements"></a>Windows Presentation Foundation öğelerine tarafından sağlayıcı uygulaması  
 Bu konu hakkında daha fazla bilgi için lütfen bkz [WPF özel denetiminin UI Otomasyonu](../../../docs/framework/wpf/controls/ui-automation-of-a-wpf-custom-control.md).  
  
<a name="Provider_Implementation_by_non_WPF_Elements"></a>   
## <a name="provider-implementation-by-non-wpf-elements"></a>WPF olmayan öğeler tarafından sağlayıcı uygulaması  
 Özel denetimleri parçası değildir [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] framework ancak, yönetilen kodda yazılır (bunlar genellikle [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] denetimleri), için destek sağlayan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] arabirimlerini uygulayarak. Her öğe, ilk tablonun sonraki bölümde listelenen arabirimler en az birini uygulamalıdır. Ayrıca, bir veya daha fazla denetim düzenleri öğe destekliyorsa, her denetim düzeni için uygun arabirimi uygulamalıdır.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Sağlayıcısı proje aşağıdaki derlemelerine başvurmalıdır:  
  
- UIAutomationProviders.dll  
  
- UIAutomationTypes.dll  
  
- WindowsBase.dll  

<a name="Provider_Interfaces"></a>   
### <a name="provider-interfaces"></a>Sağlayıcısı arabirimleri  
 Her [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sağlayıcısı aşağıdaki arabirimlerinden birini uygulaması gerekir.  
  
|Arabirim|Açıklama|  
|---------------|-----------------|  
|<xref:System.Windows.Automation.Provider.IRawElementProviderSimple>|Denetim desenleri ve özellikleri için destek dahil olmak üzere penceresinde barındırılan basit bir denetim için işlevsellik sağlar.|  
|<xref:System.Windows.Automation.Provider.IRawElementProviderFragment>|Devralınan <xref:System.Windows.Automation.Provider.IRawElementProviderSimple>. Parça içinde gezinme de dahil olmak üzere, odak ayarlama ve öğe dikdörtgen döndüren bir karmaşık denetiminde bir öğe için işlevsellik ekler.|  
|<xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>|Devralınan <xref:System.Windows.Automation.Provider.IRawElementProviderFragment>. Bir alt öğesi belirtilen koordinatlarda bulma ve eksiksiz bir denetim için odak durumu ayarlama dahil bir karmaşık denetimindeki kök öğesi için işlevsellik ekler.|  
  
 Aşağıdaki arabirimlerinden işlevsellik sağlamak ancak uygulanması gerekli değildir.  
  
|Arabirim|Açıklama|  
|---------------|-----------------|  
|<xref:System.Windows.Automation.Provider.IRawElementProviderAdviseEvents>|Olaylar için istekleri izlemek sağlayıcı sağlar.|  
|<xref:System.Windows.Automation.Provider.IRawElementProviderHwndOverride>|Pencere tabanlı öğelerin yeniden konumlandırma sağlayan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacının bir parçası.|  
  
 Diğer tüm arabirimler <xref:System.Windows.Automation.Provider> ad alanı olan denetim deseni desteği.  
  
<a name="Requirements_for_Non_WPF_Providers"></a>   
### <a name="requirements-for-non-wpf-providers"></a>WPF olmayan sağlayıcıları için gereksinimleri  
 İle iletişim kurmak için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], Denetim işlevselliğini aşağıdaki ana alanlarını uygulamanız gerekir:  
  
|İşlevi|Uygulama|  
|-------------------|--------------------|  
|İçin sağlayıcıyı gösterme [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Denetim penceresine gönderilen WM_GETOBJECT iletiye yanıt olarak, uygulayan nesnenin dönüş <xref:System.Windows.Automation.Provider.IRawElementProviderSimple> (veya türetilmiş bir arabirim). Parçaları için bu sağlayıcı için parça kök olması gerekir.|  
|Özellik değerlerini belirtin|Uygulama <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPropertyValue%2A> sağlayabilir veya geçersiz kılma değerleri.|  
|İstemci denetimi ile etkileşim kurmak etkinleştirin|Uygulama Denetim düzenleri gibi destekleyen arabirimleri <xref:System.Windows.Automation.Provider.IInvokeProvider>. Bu desen sağlayıcılarını uygulamanızda döndüren <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A>.|  
|Olay|Statik yöntemlerinden birini çağırın <xref:System.Windows.Automation.Provider.AutomationInteropProvider> istemci dinlediği bir olay oluşturabilmelidir.|  
|Gezinti ve bir parça içinde odaklanarak etkinleştir|Uygulama <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> parça içindeki her öğe için. (Gerekli bir parça parçası olmayan öğeler için.)|  
|Odaklanma ve bir parça içindeki alt öğenin konumunu etkinleştir|Uygulama <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>. (Gerekli olmayan öğeleri kökleri bölmeyin için.)|  
  
<a name="Property_Values_in_Non_WPF_Providers"></a>   
### <a name="property-values-in-non-wpf-providers"></a>WPF olmayan sağlayıcıları özellik değerleri  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özel denetimler için sağlayıcıları Otomasyon sistemi tarafından yanı sıra istemci uygulamalar tarafından kullanılan bazı özellikleri desteklemesi gerekir. Windows (Cwnd'lerden) barındırılan öğelerin [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bazı özellikler varsayılan pencere sağlayıcısından alabilir, ancak diğerleri özel sağlayıcısından edinmeniz gerekir.  
  
 HWND bağlı denetimler için sağlayıcıları (alan değerlerine göre tanımlanır) aşağıdaki özellikleri sağlamak genellikle gerekmez:  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.ProcessIdProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.ClassNameProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.HasKeyboardFocusProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.IsPasswordProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.RuntimeIdProperty>  
  
> [!NOTE]
>  <xref:System.Windows.Automation.AutomationElementIdentifiers.RuntimeIdProperty> Basit bir öğe veya parça barındırılan bir pencerede kök penceresinden alınır; ancak, parça öğeleri (örneğin, bir liste kutusu liste öğeleri) kökünün altındaki kendi tanımlayıcıları sağlamanız gerekir. Daha fazla bilgi için bkz. <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.GetRuntimeId%2A>.  
>   
>  <xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty> Barındırılan sağlayıcıları için döndürülmesi gereken bir [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] denetimi. Bu durumda, varsayılan pencere sağlayıcısı, doğru değeri alınamıyor olabilir.  
>   
>  <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty> Genellikle ana sağlayıcısı tarafından sağlanır. Örneğin, bir özel denetim türetilir <xref:System.Windows.Forms.Control>, ad alanından türetilir `Text` denetiminin özelliği.  
  
 Örnek kod için bkz: [UI Otomasyon sağlayıcı dönüş özellikleri](../../../docs/framework/ui-automation/return-properties-from-a-ui-automation-provider.md).  
  
<a name="Events_in_Non_WPF_Providers"></a>   
### <a name="events-in-non-wpf-providers"></a>WPF olmayan sağlayıcı olayları  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sağlayıcıları kullanıcı arabiriminin durumundaki değişiklikler, istemci uygulamaları bildirmek için olayları tetiklemelidir. Olayları yükseltmek için aşağıdaki yöntemleri kullanılır.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Windows.Automation.Provider.AutomationInteropProvider.RaiseAutomationEvent%2A>|Denetim desenleri tarafından tetiklenen olayları gibi çeşitli etkinlikler başlatır.|  
|<xref:System.Windows.Automation.Provider.AutomationInteropProvider.RaiseAutomationPropertyChangedEvent%2A>|Bir olay başlatır, bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özelliği değişti.|  
|<xref:System.Windows.Automation.Provider.AutomationInteropProvider.RaiseStructureChangedEvent%2A>|Bir olay başlatır, yapısını [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç değişti; Örneğin, bir öğenin eklenmesi veya kaldırılması tarafından.|  
  
 Bir şeyin gerçekleşen istemci bildirmek için bir olay amacı olan [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)], etkinliği tetikleyen olup olmadığını [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sisteminin kendisi. Örneğin, tarafından tanımlanan olay <xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent> doğrudan kullanıcı girişi veya istemci uygulaması çağırarak denetim çağrılan zaman bu harekete Geçirilmemesi gereken <xref:System.Windows.Automation.InvokePattern.Invoke%2A>.  
  
 Performansı iyileştirmek için bir sağlayıcı seçmeli olarak olay veya bunları almak için hiçbir istemci uygulaması kayıtlıysa hiçbir hiç olay. Aşağıdaki yöntemlerden iyileştirme için kullanılır.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Windows.Automation.Provider.AutomationInteropProvider.ClientsAreListening%2A>|Bu statik özelliği, tüm istemci uygulamaları için abone olup olmadığını belirtir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayları.|  
|<xref:System.Windows.Automation.Provider.IRawElementProviderAdviseEvents>|Sağlayıcının uygulama bu arabirimin bir parça kök istemcileri kaydetmek ve parça olayları için olay işleyicileri kaydını belirlemeleri için etkinleştirir.|  
  
<a name="Non_WPF_Provider_Navigation"></a>   
### <a name="non-wpf-provider-navigation"></a>WPF olmayan sağlayıcısı Gezinti  
 Bir pencere (HWND) barındırılan özel bir düğme gibi basit denetimler için sağlayıcıları içinde gezinme desteklemek gerekli değildir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç. Gezinti öğesi gelen ve giden uygulamasında belirtilen ana penceresi için varsayılan sağlayıcı tarafından işlenir <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.HostRawElementProvider%2A>. Ancak, karmaşık bir özel denetim için bir sağlayıcı uyguladığınızda, parça kök düğümü ve alt öğeleri arasında ve Eşdüzey düğümler arasında gezinti desteklemesi gerekir.  
  
> [!NOTE]
>  Kök dışında bir parça öğeler döndürmelidir bir `null` başvuru <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.HostRawElementProvider%2A>, doğrudan bir pencerede barındırılmamaktadır ve bunlara gelen ve giden Gezinti hiçbir varsayılan sağlayıcı destekleyebilir.  
  
 Parça yapısını uygulamanız tarafından belirlenir <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A>. İçin olası her yönden geliyormuş her parça gibi bu yöntem, bu yönde öğe için sağlayıcı nesne döndürür. Varsa herhangi bir öğe o yönde, yöntem döndürür bir `null` başvuru.  
  
 Parça kök yalnızca alt öğeleri için Gezinti destekler. Yönü olduğunda bir liste kutusu listedeki ilk öğe gibi döndürür <xref:System.Windows.Automation.Provider.NavigateDirection.FirstChild>ve yönü olduğunda son öğeyi <xref:System.Windows.Automation.Provider.NavigateDirection.LastChild>. Parça kök Gezinti üst veya eşdüzey desteklemiyor; Bu ana penceresi sağlayıcı tarafından işlenir.  
  
 Bir parça kök olmayan öğeleri herhangi bir eşdüzey ve sahip oldukları alt ve üst gezinti desteklemesi gerekir.  
  
<a name="Non_WPF_Provider_Reparenting"></a>   
### <a name="non-wpf-provider-reparenting"></a>WPF olmayan sağlayıcısı üst öğeleri yeniden ayarlama  
 Açılır pencereler gerçekten üst düzey pencereleri ve varsayılan olarak bu nedenle görünür [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] masaüstünün alt ağacı. Çoğu durumda, ancak açılır pencereleri mantıksal diğer denetimler alt öğeleri olarak. Örneğin, bir açılan kutunun açılır listesi, mantıksal olarak birleşik giriş kutusunun alt olan. Benzer şekilde, bir menü açılır pencere, mantıksal olarak menüsünün alt öğesidir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ilişkili denetiminin alt olmasını görünecekleri açılır pencereleri yeniden üst öğe yap için destek sağlar.  
  
 Bir açılır pencereyi yeniden üst öğe yap için:  
  
1. Açılır pencere için bir sağlayıcı oluşturma. Bu açılır pencere sınıfının önceden bilindiği gerektirir.  
  
2. İşlevmiş gibi bir denetimin kendi tüm özellikleri ve her zaman olduğu gibi bu açılır pencere desenlerini uygulayın.  
  
3. Uygulama <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.HostRawElementProvider%2A> BT'nin alınan değeri döndürür. Bu nedenle özelliği <xref:System.Windows.Automation.Provider.AutomationInteropProvider.HostProviderFromHandle%2A>parametresi bir açılır pencere tanıtıcısı olduğu.  
  
4. Uygulama <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A> açılır pencere ve kendi üst öğesi, gezinti doğru mantıksal üst mantıksal alt ve eşdüzey alt öğeleri arasında işlenecek şekilde.  
  
 Zaman [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] açılır pencere karşılaştığında Gezinti varsayılan geçersiz kılındı ve Masaüstü alt sitesi olarak karşılaşıldığında açılır pencere üzerinde atlar tanır. Bunun yerine, düğüm yalnızca parça erişilebilir olacaktır.  
  
 Üst öğeleri yeniden ayarlama, denetim bir pencere herhangi bir sınıfın burada barındırabilir çalışmaları için uygun değil. Örneğin, bir çubuk barınağı HWND, bantları içinde herhangi bir türde barındırabilirsiniz. Bu durumları idare etmek [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] HWND yeniden konumlandırma, alternatif bir biçimi sonraki bölümde açıklandığı gibi destekler.  
  
<a name="Non_WPF_Provider_Repositioning"></a>   
### <a name="non-wpf-provider-repositioning"></a>WPF olmayan sağlayıcısı yeniden konumlandırma  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] parçalar, her bir pencere (HWND) bulunan iki veya daha fazla öğe içerebilir. Her bir HWND içeren bir HWND alt HWND göz önünde bulundurur, kendi varsayılan sağlayıcı olduğundan [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı varsayılan olarak gösterilir Cwnd'lerden parçasında ana penceresinin alt öğesi. Çoğu zaman istenen davranış budur ancak bazen mantıksal yapısı eşleşmediğinden, Karışıklığı önlemek için açabilir [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
 Bunun iyi bir örneği, bir çubuk barınağı denetimidir. Bir rebar bantları, her biri bir HWND tabanlı denetimi araç çubuğu, bir düzenleme kutusuna veya bir birleşik giriş kutusu gibi sırayla içerebilir içerir. Çubuk barınağı HWND için varsayılan pencere sağlayıcı bant denetim Cwnd'lerden alt öğe olarak görür ve çubuk barınağı sağlayıcısı bantları alt öğe olarak görür. HWND sağlayıcısı ve çubuk barınağı sağlayıcısı dağıtımınızla çalışma ve bunların alt öğeleri birleştirme olduğundan bantları hem HWND tabanlı denetimler çubuk barınağı alt öğe olarak görünür. Mantıksal olarak, ancak yalnızca bantları çubuk barınağı alt öğe olarak görünmelidir ve her bant sağlayıcısı içerdiği denetimi için varsayılan HWND sağlayıcısıyla bağlanmış olmalıdır.  
  
 Bunu gerçekleştirmek için çubuk barınağı parça kök sağlayıcı kümesi bantları temsil eden alt öğeyi kullanıma sunar. Her bant özellikleri ve düzenleri ortaya çıkarabilir, tek bir sağlayıcı sahiptir. Uygulamaya <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.HostRawElementProvider%2A>, bant sağlayıcı çağırarak alır HWND, denetim için varsayılan pencere sağlayıcıyı döndürür <xref:System.Windows.Automation.Provider.AutomationInteropProvider.HostProviderFromHandle%2A>, geçen olarak denetim pencere tanıtıcısı. Son olarak, çubuk barınağı parça kök sağlayıcı uygulayan <xref:System.Windows.Automation.Provider.IRawElementProviderHwndOverride> arabirimi ve uygulamaya <xref:System.Windows.Automation.Provider.IRawElementProviderHwndOverride.GetOverrideProviderForHwnd%2A> belirtilen HWND içinde yer alan denetim için uygun bant sağlayıcı döndürür.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Sağlayıcılara Genel Bakış](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)
- [Sunucu Tarafı UI Otomasyonu Sağlayıcıyı Gösterme](../../../docs/framework/ui-automation/expose-a-server-side-ui-automation-provider.md)
- [UI Otomasyonu Sağlayıcı Dönüş Özellikleri](../../../docs/framework/ui-automation/return-properties-from-a-ui-automation-provider.md)
- [UI Otomasyonu Sağlayıcıda Olay Tetikleme](../../../docs/framework/ui-automation/raise-events-from-a-ui-automation-provider.md)
- [UI Otomasyonu Parça Sağlayıcıyıda Gezinmeyi Etkinleştirme](../../../docs/framework/ui-automation/enable-navigation-in-a-ui-automation-fragment-provider.md)
- [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
