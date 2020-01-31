---
title: Sunucu Tarafı UI Otomasyonu Sağlayıcıyı Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- server-side UI Automation provider implementation
- UI Automation, server-side provider implementation
- provider implementation, UI Automation
ms.assetid: 6acc6d08-bd67-4e2e-915c-9c1d34eb86fe
ms.openlocfilehash: 8a52d84f7152b9cb431ad0aa97c88b143463be2d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789619"
---
# <a name="server-side-ui-automation-provider-implementation"></a>Sunucu Tarafı UI Otomasyonu Sağlayıcıyı Uygulama

> [!NOTE]
> Bu belge, <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sınıflarını kullanmak isteyen .NET Framework geliştiricilere yöneliktir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]hakkında en son bilgiler için bkz. [Windows Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).

Bu bölümde, özel bir denetim için sunucu tarafı UI Otomasyon sağlayıcısının nasıl uygulanacağı açıklanmaktadır.

Windows Presentation Foundation (WPF) öğeleri ve WPF olmayan öğeler (Windows Forms için tasarlanan gibi) için uygulama temelde farklıdır. WPF öğeleri, <xref:System.Windows.Automation.Peers.AutomationPeer>türetilmiş bir sınıf aracılığıyla [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] için destek sağlar. WPF olmayan öğeler, sağlayıcı arabirimlerinin uygulamaları aracılığıyla destek sağlar.

<a name="Security_Considerations"></a>

## <a name="security-considerations"></a>Güvenlik Konuları

Sağlayıcılar, kısmi güven ortamında çalışabilmek için yazılmalıdır. UIAutomationClient. dll kısmi güven altında çalışacak şekilde yapılandırılmadığından, sağlayıcı kodunuz bu derlemeye başvurmamalıdır. Bu durumda, kod tam güven ortamında çalıştırılabilir, ancak kısmi güven ortamında başarısız olabilir.

Özellikle, <xref:System.Windows.Automation.AutomationElement>gibi UIAutomationClient. dll içindeki sınıflardan alanları kullanmayın. Bunun yerine, UIAutomationTypes. dll içindeki sınıflardan eşdeğer alanları <xref:System.Windows.Automation.AutomationElementIdentifiers>gibi kullanın.

<a name="Provider_Implementation_by_WPF_Elements"></a>

## <a name="provider-implementation-by-windows-presentation-foundation-elements"></a>Windows Presentation Foundation öğelerine göre sağlayıcı uygulama

Bu konu hakkında daha fazla bilgi için lütfen [WPF özel denetiminin UI Otomasyonu](../wpf/controls/ui-automation-of-a-wpf-custom-control.md)' na bakın.

<a name="Provider_Implementation_by_non_WPF_Elements"></a>

## <a name="provider-implementation-by-non-wpf-elements"></a>WPF olmayan öğelere göre sağlayıcı uygulama

WPF çerçevesinin parçası olmayan, ancak yönetilen kodda yazılan özel denetimler (çoğunlukla bunlar Windows Forms denetimlerdir), arabirimleri uygulayarak [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] için destek sağlar. Her öğe, sonraki bölümde ilk tabloda listelenen arabirimlerden en az birini uygulamalıdır. Ayrıca, öğe bir veya daha fazla denetim desenini destekliyorsa, her denetim deseni için uygun arabirimi uygulamalıdır.

[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sağlayıcısı projenizin aşağıdaki derlemelere başvurması gerekir:

- Uıautomationproviders. dll

- UIAutomationTypes. dll

- WindowsBase.dll

<a name="Provider_Interfaces"></a>

### <a name="provider-interfaces"></a>Sağlayıcı arabirimleri

Her [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sağlayıcı aşağıdaki arabirimlerden birini uygulamalıdır.

|Arabirim|Açıklama|
|---------------|-----------------|
|<xref:System.Windows.Automation.Provider.IRawElementProviderSimple>|Denetim desenleri ve özellikleri için destek de dahil olmak üzere, pencerede barındırılan basit bir denetim için işlevsellik sağlar.|
|<xref:System.Windows.Automation.Provider.IRawElementProviderFragment>|<xref:System.Windows.Automation.Provider.IRawElementProviderSimple>devralır. Karmaşık bir denetimdeki bir öğe için, parça içinde gezinme, odağı ayarlama ve öğenin sınırlayıcı dikdörtgenini döndürme dahil olmak üzere işlevsellik ekler.|
|<xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>|<xref:System.Windows.Automation.Provider.IRawElementProviderFragment>devralır. Belirli koordinatlarda bir alt öğe bulmak ve tüm denetimin odak durumunu ayarlamak dahil olmak üzere, karmaşık bir denetimdeki kök öğe için işlevsellik ekler.|

Aşağıdaki arabirimler ek işlevsellik sağlar, ancak uygulanması gerekmez.

|Arabirim|Açıklama|
|---------------|-----------------|
|<xref:System.Windows.Automation.Provider.IRawElementProviderAdviseEvents>|Sağlayıcının olay isteklerini izlemesini sağlar.|
|<xref:System.Windows.Automation.Provider.IRawElementProviderHwndOverride>|Bir parçanın [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı içinde pencere tabanlı öğelerin yeniden konumlandırmalarını mümkün.|

<xref:System.Windows.Automation.Provider> ad alanındaki diğer tüm arabirimler denetim deseninin desteği içindir.

<a name="Requirements_for_Non_WPF_Providers"></a>

### <a name="requirements-for-non-wpf-providers"></a>WPF olmayan sağlayıcılar için gereksinimler

[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]ile iletişim kurmak için denetiminizin aşağıdaki ana işlevleri uygulaması gerekir:

|İşlevi|Uygulama|
|-------------------|--------------------|
|Sağlayıcıyı [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] için kullanıma sunun|Denetim penceresine gönderilen bir WM_GETOBJECT iletisine yanıt olarak, <xref:System.Windows.Automation.Provider.IRawElementProviderSimple> uygulayan nesneyi (veya türetilmiş bir arabirimi) döndürün. Parçalar için bu, parça kökünün sağlayıcısı olmalıdır.|
|Özellik değerlerini sağla|Değerleri sağlamak veya geçersiz kılmak için <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPropertyValue%2A> uygulayın.|
|İstemcinin denetimle etkileşime geçmesini sağlama|<xref:System.Windows.Automation.Provider.IInvokeProvider>gibi denetim desenlerini destekleyen arabirimler uygulayın. <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A>uygulamanızda bu model sağlayıcılarını döndürün.|
|Olay oluştur|Bir istemcinin dinleyebildiğini bir olay yükseltmek için <xref:System.Windows.Automation.Provider.AutomationInteropProvider> statik yöntemlerinden birini çağırın.|
|Bir parça içinde gezinmeyi ve odayı etkinleştir|Parçaların içindeki her öğe için <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> uygulayın. (Bir parçanın parçası olmayan öğeler için gerekli değildir.)|
|Bir parçadaki alt öğenin odaklama ve konumunu etkinleştir|<xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>uygulayın. (Parçalama kökleri olmayan öğeler için gerekli değildir.)|

<a name="Property_Values_in_Non_WPF_Providers"></a>

### <a name="property-values-in-non-wpf-providers"></a>WPF olmayan sağlayıcılardaki özellik değerleri

özel denetimler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sağlayıcılar, otomasyon sisteminin yanı sıra istemci uygulamaları tarafından kullanılabilen belirli özellikleri desteklemelidir. Windows 'da (HWNDs) barındırılan öğeler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] varsayılan pencere sağlayıcısından bazı özellikler alabilir, ancak diğerlerini özel sağlayıcıdan elde etmelidir.

HWND tabanlı denetim sağlayıcılarının genellikle aşağıdaki özellikleri sağlaması gerekmez (alan değerleriyle tanımlanır):

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
> Bir pencerede barındırılan basit bir öğe veya parça kökünün <xref:System.Windows.Automation.AutomationElementIdentifiers.RuntimeIdProperty> pencereden elde edilir; Ancak, kök altındaki parça öğeleri (liste kutusu içindeki liste öğeleri gibi) kendi tanımlayıcılarını sağlamalıdır. Daha fazla bilgi için bkz. <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.GetRuntimeId%2A>.
>
> <xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>, bir Windows Forms denetiminde barındırılan sağlayıcılar için döndürülmelidir. Bu durumda, varsayılan pencere sağlayıcısı doğru değeri alamıyor olabilir.
>
> <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>, genellikle ana bilgisayar sağlayıcısı tarafından sağlanır. Örneğin, özel bir denetim <xref:System.Windows.Forms.Control>türetilirse, ad denetimin `Text` özelliğinden türetilir.

Örneğin, bkz. [BIR UI Otomasyon sağlayıcısından geri dönüş özellikleri](return-properties-from-a-ui-automation-provider.md).

<a name="Events_in_Non_WPF_Providers"></a>

### <a name="events-in-non-wpf-providers"></a>WPF olmayan sağlayıcılardaki olaylar

[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sağlayıcılar, istemci uygulamalarının Kullanıcı arabirimi durumunda yaptığı bildirimde bulunan olayları tetiklemelidir. Aşağıdaki yöntemler olayları yükseltmek için kullanılır.

|Yöntem|Açıklama|
|------------|-----------------|
|<xref:System.Windows.Automation.Provider.AutomationInteropProvider.RaiseAutomationEvent%2A>|Denetim desenleri tarafından tetiklenen olaylar da dahil olmak üzere çeşitli olaylar oluşturur.|
|<xref:System.Windows.Automation.Provider.AutomationInteropProvider.RaiseAutomationPropertyChangedEvent%2A>|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özelliği değiştiğinde bir olay oluşturur.|
|<xref:System.Windows.Automation.Provider.AutomationInteropProvider.RaiseStructureChangedEvent%2A>|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacının yapısı değiştirildiğinde bir olay oluşturur; Örneğin, bir öğesinin kaldırılmasına veya eklenmesine göre.|

Bir olayın amacı, etkinliğin [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sisteminin kendisi tarafından tetiklenip tetiklenmediğine bakılmaksızın [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)]bir şeyi istemciye bildirmektir. Örneğin, <xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent> tarafından tanımlanan olay, doğrudan Kullanıcı girişi veya <xref:System.Windows.Automation.InvokePattern.Invoke%2A>çağıran istemci uygulaması tarafından her çağrıldığında, denetim her çağrıldığında oluşturulmalıdır.

Bir sağlayıcı, performansı iyileştirmek için olayları seçmeli olarak oluşturabilir veya hiçbir istemci uygulama kayıtlı değilse hiçbir olay oluşturmaz. İyileştirme için aşağıdaki yöntemler kullanılır.

|Yöntem|Açıklama|
|------------|-----------------|
|<xref:System.Windows.Automation.Provider.AutomationInteropProvider.ClientsAreListening%2A>|Bu statik özellik, herhangi bir istemci uygulamasının [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olayına abone olup olmadığını belirtir.|
|<xref:System.Windows.Automation.Provider.IRawElementProviderAdviseEvents>|Sağlayıcının bir parça kökünde bu arabirimin uygulanması, istemcilerin parçadaki olaylar için olay işleyicilerini kaydetmesi ve kaydını silme sırasında önermesine olanak sağlar.|

<a name="Non_WPF_Provider_Navigation"></a>

### <a name="non-wpf-provider-navigation"></a>WPF olmayan sağlayıcı gezintisi

Bir pencerede (HWND) barındırılan özel bir düğme gibi basit denetimlerin sağlayıcılarının [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı içinde gezinmeyi desteklemesi gerekmez. Öğesinden ve öğesinden gezinti, <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.HostRawElementProvider%2A>uygulamasında belirtilen konak penceresi için varsayılan sağlayıcı tarafından işlenir. Ancak karmaşık bir özel denetim için bir sağlayıcı uyguladığınızda, parçanın kök düğümü ve alt öğeleri arasında ve eşdüzey düğümler arasında gezinmeyi desteketmeniz gerekir.

> [!NOTE]
> Kök dışındaki bir parçanın öğeleri doğrudan bir pencerede barındırıldığından ve bunlardan gelen ve onlardan gezinmeyi destekleyebildiğinden, <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.HostRawElementProvider%2A>`null` başvuru döndürmelidir.

Parçanın yapısı, <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A>uygulamanız tarafından belirlenir. Her bir parçanın olası her bir yönü için, bu yöntem bu yöndeki öğe için sağlayıcı nesnesini döndürür. Bu yönde hiç öğe yoksa, yöntem bir `null` başvurusu döndürür.

Parça kökü yalnızca alt öğelere gezinmeyi destekler. Örneğin, bir liste kutusu, yön <xref:System.Windows.Automation.Provider.NavigateDirection.FirstChild>ve yön <xref:System.Windows.Automation.Provider.NavigateDirection.LastChild>son öğe olduğunda listedeki ilk öğeyi döndürür. Parça kökü üst veya Eşdüzey öğe üzerinde gezinmeyi desteklemez; Bu, ana bilgisayar pencere sağlayıcısı tarafından işlenir.

Kök olmayan bir parçanın öğelerinin üst öğeye ve sahip oldukları tüm eşdüzey öğelere ve alt öğelerine gezinmeyi desteklemesi gerekir.

<a name="Non_WPF_Provider_Reparenting"></a>

### <a name="non-wpf-provider-reparenting"></a>WPF olmayan sağlayıcının yeniden konumlandırması

Açılır pencereler aslında en üst düzey Windows, varsayılan olarak [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacında masaüstünün alt öğesi olarak görüntülenir. Ancak, çoğu durumda, açılır pencereler bazı diğer bir denetimin mantıksal alt öğeleri. Örneğin, Birleşik giriş kutusunun aşağı açılan listesi, Birleşik giriş kutusunun mantıksal olarak bir alt öğesidir. Benzer şekilde, bir menü açılır penceresi, mantıksal olarak menünün bir alt öğesidir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], açılan pencereler için, ilişkili denetimin alt öğesi olarak görünmeleri için destek sağlar.

Bir açılır pencereyi yeniden üst üste eklemek için:

1. Açılır pencere için bir sağlayıcı oluşturun. Bu, açılır pencere sınıfının önceden bilinmesi gerekir.

2. Bu açılan pencere için her zamanki gibi tüm özellikleri ve desenleri, kendi sağında bir denetim olmasına rağmen uygulayın.

3. <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.HostRawElementProvider%2A> özelliğini, parametrenin açılan pencerenin pencere tutamacı olduğu <xref:System.Windows.Automation.Provider.AutomationInteropProvider.HostProviderFromHandle%2A>elde edilen değeri döndürmesi için uygulayın.

4. Açılır pencere ve üst öğesi için <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A> uygulayıp, gezintinin mantıksal üst öğeden mantıksal alt öğelere doğru şekilde işlenmesini sağlar ve eşdüzey alt öğeler arasında.

[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] açılır pencere ile karşılaştığında, gezinmenin varsayılan olarak geçersiz kılındığını algılar ve masaüstünün bir alt öğesi olarak karşılaşıldığında açılan pencereyi atlar. Bunun yerine, düğüm yalnızca parça aracılığıyla erişilebilir olacaktır.

Bir denetimin herhangi bir sınıfın penceresini barındırabileceği durumlar için yeniden Konumlandırıcı uygun değildir. Örneğin, bir yeniden çubuk bantlarındaki herhangi bir HWND türünü barındırabilir. Bu durumları işlemek için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], sonraki bölümde açıklandığı gibi, farklı bir HWND konum biçimini destekler.

<a name="Non_WPF_Provider_Repositioning"></a>

### <a name="non-wpf-provider-repositioning"></a>WPF olmayan sağlayıcı yeniden konumlandırma

[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] parçalar, her biri bir pencerede (HWND) bulunan iki veya daha fazla öğe içerebilir. Her HWND, HWND 'yi kapsayan bir HWND 'nin bir alt öğesi olacak şekilde niteleyerek kendi varsayılan sağlayıcısına sahip olduğundan, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı varsayılan olarak ana pencerenin alt öğesi olarak parçadaki HWND NDS 'yi gösterir. Çoğu durumda bu istenen davranıştır, ancak bazen [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]mantıksal yapısıyla eşleşmediğinden karışıklıklara neden olabilir.

Bunun iyi bir örneği bir Rebar denetimidir. Bir Rebar, her biri bir araç çubuğu, düzenleme kutusu veya Birleşik giriş kutusu gibi HWND tabanlı bir denetim içerebilen şeritler içerir. Rebar HWND için varsayılan pencere sağlayıcısı, bant denetimi olan HWNDs 'i alt öğe olarak görür ve yeniden çubuk sağlayıcı bantları alt öğe olarak görür. HWND sağlayıcısı ve Rebar sağlayıcı, çocuklarını ve alt öğelerini birleştirmeye çalışırken, hem şeritler hem de HWND tabanlı denetimler yeniden çubuğun alt öğesi olarak görünür. Ancak, mantıksal olarak yalnızca bantların alt çubuğun alt öğesi olarak görünmesi gerekir ve her bant sağlayıcısı, içerdiği denetimin varsayılan HWND sağlayıcısıyla birlikte yazılmalıdır.

Bunu gerçekleştirmek için, Rebar için parça kök sağlayıcısı bantları temsil eden bir alt öğe kümesi sunar. Her bant, özellikleri ve desenleri açığa çıkaran tek bir sağlayıcıya sahiptir. <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.HostRawElementProvider%2A>uygulamasında bant sağlayıcısı, denetimin pencere tanıtıcısını geçirerek <xref:System.Windows.Automation.Provider.AutomationInteropProvider.HostProviderFromHandle%2A>çağırarak, bir denetim HWND 'si için varsayılan pencere sağlayıcısını döndürür. Son olarak, Rebar için parça kök sağlayıcısı <xref:System.Windows.Automation.Provider.IRawElementProviderHwndOverride> arabirimini uygular ve <xref:System.Windows.Automation.Provider.IRawElementProviderHwndOverride.GetOverrideProviderForHwnd%2A> uygulamasında belirtilen HWND 'de bulunan denetimin uygun bant sağlayıcısını döndürür.

## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Sağlayıcılara Genel Bakış](ui-automation-providers-overview.md)
- [Sunucu Tarafı UI Otomasyonu Sağlayıcıyı Gösterme](expose-a-server-side-ui-automation-provider.md)
- [UI Otomasyonu Sağlayıcı Dönüş Özellikleri](return-properties-from-a-ui-automation-provider.md)
- [UI Otomasyonu Sağlayıcıda Olay Tetikleme](raise-events-from-a-ui-automation-provider.md)
- [UI Otomasyonu Parça Sağlayıcıyıda Gezinmeyi Etkinleştirme](enable-navigation-in-a-ui-automation-fragment-provider.md)
- [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](support-control-patterns-in-a-ui-automation-provider.md)
