---
title: Sunucu Tarafı UI Otomasyonu Sağlayıcıyı Uygulama
description: .NET 'teki özel bir denetim için sunucu tarafı UI Otomasyon sağlayıcısının nasıl uygulanacağını anlayın. WPF ve WPF olmayan öğeler için uygulama farklıdır.
ms.date: 03/30/2017
helpviewer_keywords:
- server-side UI Automation provider implementation
- UI Automation, server-side provider implementation
- provider implementation, UI Automation
ms.assetid: 6acc6d08-bd67-4e2e-915c-9c1d34eb86fe
ms.openlocfilehash: ea1b5e668e29d854233d4dde4c0e6152d591da97
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903902"
---
# <a name="server-side-ui-automation-provider-implementation"></a>Sunucu Tarafı UI Otomasyonu Sağlayıcıyı Uygulama

> [!NOTE]
> Bu belge, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ad alanında tanımlanan yönetilen sınıfları kullanmak isteyen .NET Framework geliştiricilere yöneliktir <xref:System.Windows.Automation> . Hakkında en son bilgiler için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] bkz. [WINDOWS Otomasyonu API: UI Otomasyonu](/windows/win32/winauto/entry-uiauto-win32).

Bu bölümde, özel bir denetim için sunucu tarafı UI Otomasyon sağlayıcısının nasıl uygulanacağı açıklanmaktadır.

Windows Presentation Foundation (WPF) öğeleri ve WPF olmayan öğeler (Windows Forms için tasarlanan gibi) için uygulama temelde farklıdır. WPF öğeleri, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] öğesinden türetilmiş bir sınıf aracılığıyla destek sağlar <xref:System.Windows.Automation.Peers.AutomationPeer> . WPF olmayan öğeler, sağlayıcı arabirimlerinin uygulamaları aracılığıyla destek sağlar.

<a name="Security_Considerations"></a>

## <a name="security-considerations"></a>Güvenlikle İlgili Dikkat Edilmesi Gerekenler

Sağlayıcılar, kısmi güven ortamında çalışabilmek için yazılmalıdır. UIAutomationClient.dll kısmi güven altında çalışacak şekilde yapılandırılmadığından, sağlayıcı kodunuz bu derlemeye başvurmamalıdır. Bu durumda, kod tam güven ortamında çalıştırılabilir, ancak kısmi güven ortamında başarısız olabilir.

Özellikle, ' deki gibi UIAutomationClient.dll sınıflardan alan kullanmayın <xref:System.Windows.Automation.AutomationElement> . Bunun yerine, UIAutomationTypes.dll içindeki sınıflardan eşdeğer alanları kullanın (örneğin,) <xref:System.Windows.Automation.AutomationElementIdentifiers> .

<a name="Provider_Implementation_by_WPF_Elements"></a>

## <a name="provider-implementation-by-windows-presentation-foundation-elements"></a>Windows Presentation Foundation öğelerine göre sağlayıcı uygulama

Bu konu hakkında daha fazla bilgi için lütfen [WPF özel denetiminin UI Otomasyonu](../wpf/controls/ui-automation-of-a-wpf-custom-control.md)' na bakın.

<a name="Provider_Implementation_by_non_WPF_Elements"></a>

## <a name="provider-implementation-by-non-wpf-elements"></a>WPF olmayan öğelere göre sağlayıcı uygulama

WPF çerçevesinin parçası olmayan, ancak yönetilen kodda yazılmış olan özel denetimler (çoğunlukla bunlar Windows Forms denetimleridir), arabirimleri uygulayarak için destek sağlar [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] . Her öğe, sonraki bölümde ilk tabloda listelenen arabirimlerden en az birini uygulamalıdır. Ayrıca, öğe bir veya daha fazla denetim desenini destekliyorsa, her denetim deseni için uygun arabirimi uygulamalıdır.

[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Sağlayıcı projeniz aşağıdaki derlemelere başvurmalıdır:

- UIAutomationProviders.dll

- UIAutomationTypes.dll

- WindowsBase.dll

<a name="Provider_Interfaces"></a>

### <a name="provider-interfaces"></a>Sağlayıcı arabirimleri

Her [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sağlayıcının aşağıdaki arabirimlerden birini uygulaması gerekir.

|Arabirim|Description|
|---------------|-----------------|
|<xref:System.Windows.Automation.Provider.IRawElementProviderSimple>|Denetim desenleri ve özellikleri için destek de dahil olmak üzere, pencerede barındırılan basit bir denetim için işlevsellik sağlar.|
|<xref:System.Windows.Automation.Provider.IRawElementProviderFragment>|Öğesinden devralır <xref:System.Windows.Automation.Provider.IRawElementProviderSimple> . Karmaşık bir denetimdeki bir öğe için, parça içinde gezinme, odağı ayarlama ve öğenin sınırlayıcı dikdörtgenini döndürme dahil olmak üzere işlevsellik ekler.|
|<xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>|Öğesinden devralır <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> . Belirli koordinatlarda bir alt öğe bulmak ve tüm denetimin odak durumunu ayarlamak dahil olmak üzere, karmaşık bir denetimdeki kök öğe için işlevsellik ekler.|

Aşağıdaki arabirimler ek işlevsellik sağlar, ancak uygulanması gerekmez.

|Arabirim|Description|
|---------------|-----------------|
|<xref:System.Windows.Automation.Provider.IRawElementProviderAdviseEvents>|Sağlayıcının olay isteklerini izlemesini sağlar.|
|<xref:System.Windows.Automation.Provider.IRawElementProviderHwndOverride>|Bir parçanın ağacı içerisindeki pencere tabanlı öğelerin yeniden konumlandırmalarını mümkün [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|

Ad alanındaki diğer tüm arabirimler <xref:System.Windows.Automation.Provider> Denetim deseninin desteği içindir.

<a name="Requirements_for_Non_WPF_Providers"></a>

### <a name="requirements-for-non-wpf-providers"></a>WPF olmayan sağlayıcılar için gereksinimler

İle iletişim kurmak için [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] denetiminizin aşağıdaki ana işlevleri uygulaması gerekir:

|İşlev|Uygulama|
|-------------------|--------------------|
|Sağlayıcıyı şu şekilde kullanıma sunun[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Denetim penceresine gönderilen WM_GETOBJECT iletisine yanıt olarak, uygulayan nesneyi <xref:System.Windows.Automation.Provider.IRawElementProviderSimple> (veya türetilmiş bir arabirimi) döndürün. Parçalar için bu, parça kökünün sağlayıcısı olmalıdır.|
|Özellik değerlerini sağla|<xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPropertyValue%2A>Değerleri sağlamak veya geçersiz kılmak için uygulayın.|
|İstemcinin denetimle etkileşime geçmesini sağlama|Gibi denetim desenlerini destekleyen arabirimler uygulayın <xref:System.Windows.Automation.Provider.IInvokeProvider> . Uygulamanızda bu model sağlayıcılarını döndürün <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A> .|
|Olay oluştur|<xref:System.Windows.Automation.Provider.AutomationInteropProvider>Bir istemcinin dinleyebildiğini bir olay yükseltmek için statik yöntemlerinden birini çağırın.|
|Bir parça içinde gezinmeyi ve odayı etkinleştir|<xref:System.Windows.Automation.Provider.IRawElementProviderFragment>Parçaların içindeki her öğe için uygulayın. (Bir parçanın parçası olmayan öğeler için gerekli değildir.)|
|Bir parçadaki alt öğenin odaklama ve konumunu etkinleştir|Uygulayın <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot> . (Parçalama kökleri olmayan öğeler için gerekli değildir.)|

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
> <xref:System.Windows.Automation.AutomationElementIdentifiers.RuntimeIdProperty>Pencerede barındırılan basit bir öğe veya parça kökü pencereden alınır; ancak, kök altındaki parçalara ayırma öğeleri (liste kutusu içindeki liste öğeleri gibi) kendi tanımlayıcılarını sağlamalıdır. Daha fazla bilgi için bkz. <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.GetRuntimeId%2A>.
>
> <xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>Windows Forms denetiminde barındırılan sağlayıcılar için döndürülmelidir. Bu durumda, varsayılan pencere sağlayıcısı doğru değeri alamıyor olabilir.
>
> <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>Genellikle ana bilgisayar sağlayıcısı tarafından sağlanır. Örneğin, bir özel denetim öğesinden türetildiyse <xref:System.Windows.Forms.Control> , ad `Text` denetimin özelliğinden türetilir.

Örneğin, bkz. [BIR UI Otomasyon sağlayıcısından geri dönüş özellikleri](return-properties-from-a-ui-automation-provider.md).

<a name="Events_in_Non_WPF_Providers"></a>

### <a name="events-in-non-wpf-providers"></a>WPF olmayan sağlayıcılardaki olaylar

[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]sağlayıcılar, istemci uygulamalarının Kullanıcı arabirimi durumunda değişiklik bildirmesi için olayları tetiklemelidir. Aşağıdaki yöntemler olayları yükseltmek için kullanılır.

|Yöntem|Description|
|------------|-----------------|
|<xref:System.Windows.Automation.Provider.AutomationInteropProvider.RaiseAutomationEvent%2A>|Denetim desenleri tarafından tetiklenen olaylar da dahil olmak üzere çeşitli olaylar oluşturur.|
|<xref:System.Windows.Automation.Provider.AutomationInteropProvider.RaiseAutomationPropertyChangedEvent%2A>|Bir özellik değiştiğinde bir olay oluşturur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|
|<xref:System.Windows.Automation.Provider.AutomationInteropProvider.RaiseStructureChangedEvent%2A>|Ağacın yapısı değiştiğinde bir olay oluşturur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ; Örneğin, bir öğenin kaldırılması veya eklenmesi.|

Bir olayın amacı, [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] etkinliğin sistem tarafından tetiklendiğine bakılmaksızın, içinde bir şeyin gerçekleşmediğini bildirmektir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] . Örneğin, tarafından tanımlanan olay <xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent> , doğrudan Kullanıcı girişi veya çağıran istemci uygulaması tarafından her çağrıldığında oluşturulur <xref:System.Windows.Automation.InvokePattern.Invoke%2A> .

Bir sağlayıcı, performansı iyileştirmek için olayları seçmeli olarak oluşturabilir veya hiçbir istemci uygulama kayıtlı değilse hiçbir olay oluşturmaz. İyileştirme için aşağıdaki yöntemler kullanılır.

|Yöntem|Description|
|------------|-----------------|
|<xref:System.Windows.Automation.Provider.AutomationInteropProvider.ClientsAreListening%2A>|Bu statik özellik, herhangi bir istemci uygulamasının olaylara abone olup olmadığını belirtir [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|
|<xref:System.Windows.Automation.Provider.IRawElementProviderAdviseEvents>|Sağlayıcının bir parça kökünde bu arabirimin uygulanması, istemcilerin parçadaki olaylar için olay işleyicilerini kaydetmesi ve kaydını silme sırasında önermesine olanak sağlar.|

<a name="Non_WPF_Provider_Navigation"></a>

### <a name="non-wpf-provider-navigation"></a>WPF olmayan sağlayıcı gezintisi

Bir pencerede (HWND) barındırılan özel bir düğme gibi basit denetimlerin sağlayıcılarının ağaç içinde gezinmeyi desteklemesi gerekmez [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] . Öğesinden ve öğesinden gezinti, uygulamasının uygulamasında belirtilen konak penceresi için varsayılan sağlayıcı tarafından işlenir <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.HostRawElementProvider%2A> . Ancak karmaşık bir özel denetim için bir sağlayıcı uyguladığınızda, parçanın kök düğümü ve alt öğeleri arasında ve eşdüzey düğümler arasında gezinmeyi desteketmeniz gerekir.

> [!NOTE]
> Kök dışındaki bir parçanın öğeleri `null` <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.HostRawElementProvider%2A> doğrudan bir pencerede barındırıldığından ve bunlardan gelen ve onlardan gezinmeyi destekleyebildiğinden, öğesinden bir başvuru döndürmelidir.

Parçanın yapısı, uygulamanız tarafından belirlenir <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A> . Her bir parçanın olası her bir yönü için, bu yöntem bu yöndeki öğe için sağlayıcı nesnesini döndürür. Bu yönde bir öğe yoksa, yöntem bir `null` başvuru döndürür.

Parça kökü yalnızca alt öğelere gezinmeyi destekler. Örneğin, bir liste kutusu yön olduğunda listedeki ilk öğeyi <xref:System.Windows.Automation.Provider.NavigateDirection.FirstChild> ve yön olduğunda son öğeyi döndürür <xref:System.Windows.Automation.Provider.NavigateDirection.LastChild> . Parça kökü üst veya Eşdüzey öğe üzerinde gezinmeyi desteklemez; Bu, ana bilgisayar pencere sağlayıcısı tarafından işlenir.

Kök olmayan bir parçanın öğelerinin üst öğeye ve sahip oldukları tüm eşdüzey öğelere ve alt öğelerine gezinmeyi desteklemesi gerekir.

<a name="Non_WPF_Provider_Reparenting"></a>

### <a name="non-wpf-provider-reparenting"></a>WPF olmayan sağlayıcının yeniden konumlandırması

Açılır pencereler aslında en üst düzey Windows, bu nedenle varsayılan olarak [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağacın alt öğesi olarak görüntülenir. Ancak, çoğu durumda, açılır pencereler bazı diğer bir denetimin mantıksal alt öğeleri. Örneğin, Birleşik giriş kutusunun aşağı açılan listesi, Birleşik giriş kutusunun mantıksal olarak bir alt öğesidir. Benzer şekilde, bir menü açılır penceresi, mantıksal olarak menünün bir alt öğesidir. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], ilişkili denetimin alt öğeleri gibi görünmesi için açılır pencereler için destek sağlar.

Bir açılır pencereyi yeniden üst üste eklemek için:

1. Açılır pencere için bir sağlayıcı oluşturun. Bu, açılır pencere sınıfının önceden bilinmesi gerekir.

2. Bu açılan pencere için her zamanki gibi tüm özellikleri ve desenleri, kendi sağında bir denetim olmasına rağmen uygulayın.

3. Özelliği, <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.HostRawElementProvider%2A> öğesinden elde edilen değeri döndürmesi için uygulayın <xref:System.Windows.Automation.Provider.AutomationInteropProvider.HostProviderFromHandle%2A> , burada parametresi, açılır pencerenin pencere tanıtıcıdır.

4. <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A>Açılır pencere ve üst öğesi için, gezintinin mantıksal üst öğeden mantıksal alt öğelere doğru şekilde işlenmesini sağlamak için ve eşdüzey alt öğeler arasında uygulayın.

[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Açılır pencereyle karşılaştığında, gezinmenin varsayılan olarak geçersiz kılındığını algılar ve masaüstünün bir alt öğesi olarak karşılaşıldığında açılan pencereyi atlar. Bunun yerine, düğüm yalnızca parça aracılığıyla erişilebilir olacaktır.

Bir denetimin herhangi bir sınıfın penceresini barındırabileceği durumlar için yeniden Konumlandırıcı uygun değildir. Örneğin, bir yeniden çubuk bantlarındaki herhangi bir HWND türünü barındırabilir. Bu durumları işlemek için, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] sonraki bölümde açıklandığı gıbı HWND konum değişikliği alternatif bir biçimini destekler.

<a name="Non_WPF_Provider_Repositioning"></a>

### <a name="non-wpf-provider-repositioning"></a>WPF olmayan sağlayıcı yeniden konumlandırma

[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]parçalar, her biri bir pencerede (HWND) bulunan iki veya daha fazla öğe içerebilir. Her HWND, HWND 'yi kapsayan bir HWND 'nin bir alt öğesi olacak şekilde niteleyerek kendi varsayılan sağlayıcısına sahip olduğundan, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ağaç varsayılan olarak ana pencerenin alt öğesi olarak parçadaki HWND NDS 'yi gösterir. Çoğu durumda bu, istenen davranıştır, ancak bazen ' ın mantıksal yapısıyla eşleşmediğinden karışıklıklara yol açabilir [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] .

Bunun iyi bir örneği bir Rebar denetimidir. Bir Rebar, her biri bir araç çubuğu, düzenleme kutusu veya Birleşik giriş kutusu gibi HWND tabanlı bir denetim içerebilen şeritler içerir. Rebar HWND için varsayılan pencere sağlayıcısı, bant denetimi olan HWNDs 'i alt öğe olarak görür ve yeniden çubuk sağlayıcı bantları alt öğe olarak görür. HWND sağlayıcısı ve Rebar sağlayıcı, çocuklarını ve alt öğelerini birleştirmeye çalışırken, hem şeritler hem de HWND tabanlı denetimler yeniden çubuğun alt öğesi olarak görünür. Ancak, mantıksal olarak yalnızca bantların alt çubuğun alt öğesi olarak görünmesi gerekir ve her bant sağlayıcısı, içerdiği denetimin varsayılan HWND sağlayıcısıyla birlikte yazılmalıdır.

Bunu gerçekleştirmek için, Rebar için parça kök sağlayıcısı bantları temsil eden bir alt öğe kümesi sunar. Her bant, özellikleri ve desenleri açığa çıkaran tek bir sağlayıcıya sahiptir. Uygulamasının uygulamasında <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.HostRawElementProvider%2A> , bant sağlayıcısı, denetimin pencere tanıtıcısını geçirerek çağırarak, DENETIM HWND 'si için varsayılan pencere sağlayıcıyı döndürür <xref:System.Windows.Automation.Provider.AutomationInteropProvider.HostProviderFromHandle%2A> . Son olarak, yeniden çubuk için parça kök sağlayıcısı <xref:System.Windows.Automation.Provider.IRawElementProviderHwndOverride> arabirimini uygular ve kendi uygulamasında, <xref:System.Windows.Automation.Provider.IRawElementProviderHwndOverride.GetOverrideProviderForHwnd%2A> belirtilen HWND 'de bulunan denetim için uygun bant sağlayıcısını döndürür.

## <a name="see-also"></a>Ayrıca bkz.

- [UI Otomasyon Sağlayıcılara Genel Bakış](ui-automation-providers-overview.md)
- [Sunucu Tarafı UI Otomasyon Sağlayıcıyı Gösterme](expose-a-server-side-ui-automation-provider.md)
- [UI Otomasyonu Sağlayıcı Dönüş Özellikleri](return-properties-from-a-ui-automation-provider.md)
- [UI Otomasyonu Sağlayıcıda Olay Tetikleme](raise-events-from-a-ui-automation-provider.md)
- [UI Otomasyonu Parça Sağlayıcıyıda Gezinmeyi Etkinleştirme](enable-navigation-in-a-ui-automation-fragment-provider.md)
- [UI Otomasyonu Sağlayıcıda Denetim Düzenleri Desteği](support-control-patterns-in-a-ui-automation-provider.md)
