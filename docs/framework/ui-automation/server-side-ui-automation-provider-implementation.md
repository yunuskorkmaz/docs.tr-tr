---
title: Sunucu Tarafı UI Otomasyonu Sağlayıcıyı Uygulama
ms.date: 03/30/2017
helpviewer_keywords:
- server-side UI Automation provider implementation
- UI Automation, server-side provider implementation
- provider implementation, UI Automation
ms.assetid: 6acc6d08-bd67-4e2e-915c-9c1d34eb86fe
ms.openlocfilehash: 5fd17f9ca9d83ab3b226ce9fc0a4aebca4f9352a
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044153"
---
# <a name="server-side-ui-automation-provider-implementation"></a>Sunucu Tarafı UI Otomasyonu Sağlayıcıyı Uygulama

> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation> ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir. Hakkında [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]en son bilgiler için bkz [. Windows Otomasyonu API 'si: UI Otomasyonu](https://go.microsoft.com/fwlink/?LinkID=156746).

Bu bölümde, özel bir denetim için sunucu tarafı UI Otomasyon sağlayıcısının nasıl uygulanacağı açıklanmaktadır.

Windows Presentation Foundation (WPF) öğeleri ve[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] öğe olmayan (için [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]tasarlanan gibi) uygulama, temelde farklıdır. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]öğeleri, öğesinden <xref:System.Windows.Automation.Peers.AutomationPeer>türetilmiş [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bir sınıf aracılığıyla destek sağlar. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] Öğe olmayan öğeler, sağlayıcı arabirimlerinin uygulamaları aracılığıyla destek sağlar.

<a name="Security_Considerations"></a>

## <a name="security-considerations"></a>Güvenlik Değerlendirmeleri

Sağlayıcılar, kısmi güven ortamında çalışabilmek için yazılmalıdır. UIAutomationClient. dll kısmi güven altında çalışacak şekilde yapılandırılmadığından, sağlayıcı kodunuz bu derlemeye başvurmamalıdır. Bu durumda, kod tam güven ortamında çalıştırılabilir, ancak kısmi güven ortamında başarısız olabilir.

Özellikle, UIAutomationClient. dll ' de yer <xref:System.Windows.Automation.AutomationElement>alan sınıflardan alanları kullanmayın. Bunun yerine, UIAutomationTypes. dll içindeki sınıflardan eşdeğer alanları kullanın, örneğin <xref:System.Windows.Automation.AutomationElementIdentifiers>.

<a name="Provider_Implementation_by_WPF_Elements"></a>

## <a name="provider-implementation-by-windows-presentation-foundation-elements"></a>Windows Presentation Foundation öğelerine göre sağlayıcı uygulama

Bu konu hakkında daha fazla bilgi için lütfen [WPF özel denetiminin UI Otomasyonu](../../../docs/framework/wpf/controls/ui-automation-of-a-wpf-custom-control.md)' na bakın.

<a name="Provider_Implementation_by_non_WPF_Elements"></a>

## <a name="provider-implementation-by-non-wpf-elements"></a>WPF olmayan öğelere göre sağlayıcı uygulama

[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] Framework 'ün parçası olmayan, ancak yönetilen kodda yazılmış olan özel denetimler (çoğunlukla bunlar denetimlerdir [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] ), arabirimleri uygulayarak için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] destek sağlar. Her öğe, sonraki bölümde ilk tabloda listelenen arabirimlerden en az birini uygulamalıdır. Ayrıca, öğe bir veya daha fazla denetim desenini destekliyorsa, her denetim deseni için uygun arabirimi uygulamalıdır.

[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Sağlayıcı projeniz aşağıdaki derlemelere başvurmalıdır:

- Uıautomationproviders. dll

- UIAutomationTypes. dll

- WindowsBase.dll

<a name="Provider_Interfaces"></a>

### <a name="provider-interfaces"></a>Sağlayıcı arabirimleri

Her [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sağlayıcının aşağıdaki arabirimlerden birini uygulaması gerekir.

|Arabirim|Açıklama|
|---------------|-----------------|
|<xref:System.Windows.Automation.Provider.IRawElementProviderSimple>|Denetim desenleri ve özellikleri için destek de dahil olmak üzere, pencerede barındırılan basit bir denetim için işlevsellik sağlar.|
|<xref:System.Windows.Automation.Provider.IRawElementProviderFragment>|Öğesinden <xref:System.Windows.Automation.Provider.IRawElementProviderSimple>devralır. Karmaşık bir denetimdeki bir öğe için, parça içinde gezinme, odağı ayarlama ve öğenin sınırlayıcı dikdörtgenini döndürme dahil olmak üzere işlevsellik ekler.|
|<xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>|Öğesinden <xref:System.Windows.Automation.Provider.IRawElementProviderFragment>devralır. Belirli koordinatlarda bir alt öğe bulmak ve tüm denetimin odak durumunu ayarlamak dahil olmak üzere, karmaşık bir denetimdeki kök öğe için işlevsellik ekler.|

Aşağıdaki arabirimler ek işlevsellik sağlar, ancak uygulanması gerekmez.

|Arabirim|Açıklama|
|---------------|-----------------|
|<xref:System.Windows.Automation.Provider.IRawElementProviderAdviseEvents>|Sağlayıcının olay isteklerini izlemesini sağlar.|
|<xref:System.Windows.Automation.Provider.IRawElementProviderHwndOverride>|Bir parçanın [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacı içerisindeki pencere tabanlı öğelerin yeniden konumlandırmalarını mümkün.|

<xref:System.Windows.Automation.Provider> Ad alanındaki diğer tüm arabirimler denetim deseninin desteği içindir.

<a name="Requirements_for_Non_WPF_Providers"></a>

### <a name="requirements-for-non-wpf-providers"></a>WPF olmayan sağlayıcılar için gereksinimler

İle [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]iletişim kurmak için denetiminizin aşağıdaki ana işlevleri uygulaması gerekir:

|İşlevi|Uygulama|
|-------------------|--------------------|
|Sağlayıcıyı şu şekilde kullanıma sunun[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Denetim penceresine gönderilen bir WM_GETOBJECT iletisine yanıt olarak, (veya türetilmiş bir arabirim) uygulayan <xref:System.Windows.Automation.Provider.IRawElementProviderSimple> nesneyi döndürün. Parçalar için bu, parça kökünün sağlayıcısı olmalıdır.|
|Özellik değerlerini sağla|Değerleri <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPropertyValue%2A> sağlamak veya geçersiz kılmak için uygulayın.|
|İstemcinin denetimle etkileşime geçmesini sağlama|Gibi denetim desenlerini <xref:System.Windows.Automation.Provider.IInvokeProvider>destekleyen arabirimler uygulayın. Uygulamanızda bu model sağlayıcılarını döndürün <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A>.|
|Olay oluştur|Bir istemcinin dinleyebildiğini bir olay <xref:System.Windows.Automation.Provider.AutomationInteropProvider> yükseltmek için statik yöntemlerinden birini çağırın.|
|Bir parça içinde gezinmeyi ve odayı etkinleştir|Parçaların <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> içindeki her öğe için uygulayın. (Bir parçanın parçası olmayan öğeler için gerekli değildir.)|
|Bir parçadaki alt öğenin odaklama ve konumunu etkinleştir|Uygulayın <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>. (Parçalama kökleri olmayan öğeler için gerekli değildir.)|

<a name="Property_Values_in_Non_WPF_Providers"></a>

### <a name="property-values-in-non-wpf-providers"></a>WPF olmayan sağlayıcılardaki özellik değerleri

[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]özel denetimler için sağlayıcılar, otomasyon sisteminin yanı sıra istemci uygulamaları tarafından kullanılabilen bazı özellikleri desteklemelidir. Windows 'da (HWNDs) barındırılan öğeler için, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] varsayılan pencere sağlayıcısından bazı özellikler alabilir, ancak diğerlerini özel sağlayıcıdan almaları gerekir.

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
> <xref:System.Windows.Automation.AutomationElementIdentifiers.RuntimeIdProperty> Pencerede barındırılan basit bir öğe veya parça kökü pencereden alınır; ancak, kök altındaki parçalara ayırma öğeleri (liste kutusu içindeki liste öğeleri gibi) kendi tanımlayıcılarını sağlamalıdır. Daha fazla bilgi için bkz. <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.GetRuntimeId%2A>.
>
> <xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty> Bir[!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)] denetimde barındırılan sağlayıcılar için döndürülmelidir. Bu durumda, varsayılan pencere sağlayıcısı doğru değeri alamıyor olabilir.
>
> <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty> Genellikle ana bilgisayar sağlayıcısı tarafından sağlanır. Örneğin, bir özel denetim öğesinden <xref:System.Windows.Forms.Control>türetildiyse, ad denetimin `Text` özelliğinden türetilir.

Örneğin, bkz. [BIR UI Otomasyon sağlayıcısından geri dönüş özellikleri](../../../docs/framework/ui-automation/return-properties-from-a-ui-automation-provider.md).

<a name="Events_in_Non_WPF_Providers"></a>

### <a name="events-in-non-wpf-providers"></a>WPF olmayan sağlayıcılardaki olaylar

[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]sağlayıcılar, istemci uygulamalarının Kullanıcı arabirimi durumunda değişiklik bildirmesi için olayları tetiklemelidir. Aşağıdaki yöntemler olayları yükseltmek için kullanılır.

|Yöntem|Açıklama|
|------------|-----------------|
|<xref:System.Windows.Automation.Provider.AutomationInteropProvider.RaiseAutomationEvent%2A>|Denetim desenleri tarafından tetiklenen olaylar da dahil olmak üzere çeşitli olaylar oluşturur.|
|<xref:System.Windows.Automation.Provider.AutomationInteropProvider.RaiseAutomationPropertyChangedEvent%2A>|Bir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] özellik değiştiğinde bir olay oluşturur.|
|<xref:System.Windows.Automation.Provider.AutomationInteropProvider.RaiseStructureChangedEvent%2A>|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Ağacın yapısı değiştiğinde bir olay oluşturur; örneğin, bir öğenin kaldırılması veya eklenmesi.|

Bir olayın amacı, etkinliğin [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sistem tarafından tetiklendiğine bakılmaksızın, içinde bir şeyin gerçekleşmediğini bildirmektir. Örneğin, tarafından <xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent> tanımlanan olay, doğrudan Kullanıcı girişi veya çağıran <xref:System.Windows.Automation.InvokePattern.Invoke%2A>istemci uygulaması tarafından her çağrıldığında oluşturulur.

Bir sağlayıcı, performansı iyileştirmek için olayları seçmeli olarak oluşturabilir veya hiçbir istemci uygulama kayıtlı değilse hiçbir olay oluşturmaz. İyileştirme için aşağıdaki yöntemler kullanılır.

|Yöntem|Açıklama|
|------------|-----------------|
|<xref:System.Windows.Automation.Provider.AutomationInteropProvider.ClientsAreListening%2A>|Bu statik özellik, herhangi bir istemci uygulamasının [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] olaylara abone olup olmadığını belirtir.|
|<xref:System.Windows.Automation.Provider.IRawElementProviderAdviseEvents>|Sağlayıcının bir parça kökünde bu arabirimin uygulanması, istemcilerin parçadaki olaylar için olay işleyicilerini kaydetmesi ve kaydını silme sırasında önermesine olanak sağlar.|

<a name="Non_WPF_Provider_Navigation"></a>

### <a name="non-wpf-provider-navigation"></a>WPF olmayan sağlayıcı gezintisi

Bir pencerede (hwnd) barındırılan özel bir düğme gibi basit denetimlerin sağlayıcılarının [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç içinde gezinmeyi desteklemesi gerekmez. Öğesinden ve öğesinden gezinti, uygulamasının uygulamasında <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.HostRawElementProvider%2A>belirtilen konak penceresi için varsayılan sağlayıcı tarafından işlenir. Ancak karmaşık bir özel denetim için bir sağlayıcı uyguladığınızda, parçanın kök düğümü ve alt öğeleri arasında ve eşdüzey düğümler arasında gezinmeyi desteketmeniz gerekir.

> [!NOTE]
> Kök dışındaki bir parçanın öğeleri doğrudan bir pencerede barındırıldığından ve `null` bunlardan gelen <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.HostRawElementProvider%2A>ve onlardan gezinmeyi destekleyebildiğinden, öğesinden bir başvuru döndürmelidir.

Parçanın yapısı, uygulamanız <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A>tarafından belirlenir. Her bir parçanın olası her bir yönü için, bu yöntem bu yöndeki öğe için sağlayıcı nesnesini döndürür. Bu yönde bir öğe yoksa, yöntem bir `null` başvuru döndürür.

Parça kökü yalnızca alt öğelere gezinmeyi destekler. Örneğin, bir liste kutusu yön <xref:System.Windows.Automation.Provider.NavigateDirection.FirstChild>olduğunda listedeki ilk öğeyi ve <xref:System.Windows.Automation.Provider.NavigateDirection.LastChild>yön olduğunda son öğeyi döndürür. Parça kökü üst veya Eşdüzey öğe üzerinde gezinmeyi desteklemez; Bu, ana bilgisayar pencere sağlayıcısı tarafından işlenir.

Kök olmayan bir parçanın öğelerinin üst öğeye ve sahip oldukları tüm eşdüzey öğelere ve alt öğelerine gezinmeyi desteklemesi gerekir.

<a name="Non_WPF_Provider_Reparenting"></a>

### <a name="non-wpf-provider-reparenting"></a>WPF olmayan sağlayıcının yeniden konumlandırması

Açılır pencereler aslında en üst düzey Windows, bu nedenle varsayılan olarak [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacın alt öğesi olarak görüntülenir. Ancak, çoğu durumda, açılır pencereler bazı diğer bir denetimin mantıksal alt öğeleri. Örneğin, Birleşik giriş kutusunun aşağı açılan listesi, Birleşik giriş kutusunun mantıksal olarak bir alt öğesidir. Benzer şekilde, bir menü açılır penceresi, mantıksal olarak menünün bir alt öğesidir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], ilişkili denetimin alt öğeleri gibi görünmesi için açılır pencereler için destek sağlar.

Bir açılır pencereyi yeniden üst üste eklemek için:

1. Açılır pencere için bir sağlayıcı oluşturun. Bu, açılır pencere sınıfının önceden bilinmesi gerekir.

2. Bu açılan pencere için her zamanki gibi tüm özellikleri ve desenleri, kendi sağında bir denetim olmasına rağmen uygulayın.

3. Özelliği, öğesinden <xref:System.Windows.Automation.Provider.AutomationInteropProvider.HostProviderFromHandle%2A>elde edilen değeri döndürmesi için uygulayın, burada parametresi, açılır pencerenin pencere tanıtıcıdır. <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.HostRawElementProvider%2A>

4. Açılır <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A> pencere ve üst öğesi için, gezintinin mantıksal üst öğeden mantıksal alt öğelere doğru şekilde işlenmesini sağlamak için ve eşdüzey alt öğeler arasında uygulayın.

Açılır [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pencereyle karşılaştığında, gezinmenin varsayılan olarak geçersiz kılındığını algılar ve masaüstünün bir alt öğesi olarak karşılaşıldığında açılan pencereyi atlar. Bunun yerine, düğüm yalnızca parça aracılığıyla erişilebilir olacaktır.

Bir denetimin herhangi bir sınıfın penceresini barındırabileceği durumlar için yeniden Konumlandırıcı uygun değildir. Örneğin, bir yeniden çubuk bantlarındaki herhangi bir HWND türünü barındırabilir. Bu durumları işlemek için, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sonraki bölümde açıklandığı gibi HWND konum değişikliği alternatif bir biçimini destekler.

<a name="Non_WPF_Provider_Repositioning"></a>

### <a name="non-wpf-provider-repositioning"></a>WPF olmayan sağlayıcı yeniden konumlandırma

[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]parçalar, her biri bir pencerede (HWND) bulunan iki veya daha fazla öğe içerebilir. Her HWND, HWND 'yi kapsayan bir HWND [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 'nin bir alt öğesi olacak şekilde niteleyerek kendi varsayılan sağlayıcısına sahip olduğundan, ağaç varsayılan olarak ana pencerenin alt öğesi olarak parçadaki HWND NDS 'yi gösterir. Çoğu durumda bu, istenen davranıştır, ancak bazen ' ın [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]mantıksal yapısıyla eşleşmediğinden karışıklıklara yol açabilir.

Bunun iyi bir örneği bir Rebar denetimidir. Bir Rebar, her biri bir araç çubuğu, düzenleme kutusu veya Birleşik giriş kutusu gibi HWND tabanlı bir denetim içerebilen şeritler içerir. Rebar HWND için varsayılan pencere sağlayıcısı, bant denetimi olan HWNDs 'i alt öğe olarak görür ve yeniden çubuk sağlayıcı bantları alt öğe olarak görür. HWND sağlayıcısı ve Rebar sağlayıcı, çocuklarını ve alt öğelerini birleştirmeye çalışırken, hem şeritler hem de HWND tabanlı denetimler yeniden çubuğun alt öğesi olarak görünür. Ancak, mantıksal olarak yalnızca bantların alt çubuğun alt öğesi olarak görünmesi gerekir ve her bant sağlayıcısı, içerdiği denetimin varsayılan HWND sağlayıcısıyla birlikte yazılmalıdır.

Bunu gerçekleştirmek için, Rebar için parça kök sağlayıcısı bantları temsil eden bir alt öğe kümesi sunar. Her bant, özellikleri ve desenleri açığa çıkaran tek bir sağlayıcıya sahiptir. Uygulamasının uygulamasında, bant <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.HostRawElementProvider%2A>sağlayıcısı, denetimin pencere tanıtıcısını geçirerek çağırarak <xref:System.Windows.Automation.Provider.AutomationInteropProvider.HostProviderFromHandle%2A>, denetim HWND 'si için varsayılan pencere sağlayıcıyı döndürür. Son olarak, yeniden çubuk için parça kök sağlayıcısı <xref:System.Windows.Automation.Provider.IRawElementProviderHwndOverride> arabirimini uygular ve kendi <xref:System.Windows.Automation.Provider.IRawElementProviderHwndOverride.GetOverrideProviderForHwnd%2A> uygulamasında, belirtilen HWND 'de bulunan denetim için uygun bant sağlayıcısını döndürür.

## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyonu Sağlayıcılara Genel Bakış](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)
- [Sunucu Tarafı UI Otomasyonu Sağlayıcıyı Gösterme](../../../docs/framework/ui-automation/expose-a-server-side-ui-automation-provider.md)
- [UI Otomasyonu Sağlayıcı Dönüş Özellikleri](../../../docs/framework/ui-automation/return-properties-from-a-ui-automation-provider.md)
- [UI Otomasyonu Sağlayıcıda Olay Tetikleme](../../../docs/framework/ui-automation/raise-events-from-a-ui-automation-provider.md)
- [UI Otomasyonu Parça Sağlayıcıyıda Gezinmeyi Etkinleştirme](../../../docs/framework/ui-automation/enable-navigation-in-a-ui-automation-fragment-provider.md)
- [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
