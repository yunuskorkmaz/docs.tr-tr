---
title: Biçimlendirme Uzantısı Bağlama
ms.date: 03/30/2017
f1_keywords:
- Binding
helpviewer_keywords:
- Binding markup extensions [WPF]
- XAML [WPF], Binding markup extension
ms.assetid: 83d6e2a4-1b0c-4fc8-bd96-b5e98800ab63
ms.openlocfilehash: 3455c7ccdedb432fc05c7dc9e80f0f7509f4fa0c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62010689"
---
# <a name="binding-markup-extension"></a>Biçimlendirme Uzantısı Bağlama
Bir ara ifade nesnesi oluşturma ve öğe ve çalışma zamanında bağlamasına uygulandığı veri bağlamı yorumlama verilere bağlı değeri, özellik değeri erteler.  
  
## <a name="binding-expression-usage"></a>Bağlama ifadesi kullanımı  
  
```  
<object property="{Binding}" .../>  
-or-  
<object property="{Binding  bindProp1=value1[, bindPropN=valueN]*}" ...  
/>  
-or-  
<object property="{Binding path}" .../>  
-or  
<object property="{Binding path[, bindPropN=valueN]*}" .../>  
```  
  
## <a name="syntax-notes"></a>Söz dizimi notları  
 Bu sözdizimlerinde `[]` ve `*` sabit değerler kullanılamaz. Belirtmek için bir gösterimi parçasıdır sıfır veya daha fazla *bindProp*`=`*değer* çiftleri kullanılabilir, ile bir `,` bunları ve daha önceki arasındaki ayırıcı *bindProp*  `=` *değer* çiftleri.  
  
 "Bağlama uzantısı ile Ayarlanabilen Bağlama Özellikleri" bölümünde listelenen özelliklerden herhangi birini yerine özniteliklerini kullanarak ayarlanabilir bir <xref:System.Windows.Data.Binding> nesne öğesi. Ancak, bu değil gerçek anlamda biçimlendirme uzantısı kullanımı <xref:System.Windows.Data.Binding>, yalnızca genel XAML işlenmesini CLR özellik kümesinin öznitelikleri olan <xref:System.Windows.Data.Binding> sınıfı. Diğer bir deyişle, `<Binding` *bindProp1*`="`*value1* `"[` *bindPropN*`="`*valueN* `"]*/>` öznitelikleri için eşdeğer bir söz dizimi <xref:System.Windows.Data.Binding> nesne öğesi kullanımı yerine bir `Binding` ifade kullanımı. XAML öznitelik kullanımı belirli özellikleri hakkında bilgi edinmek için <xref:System.Windows.Data.Binding>, ilgili özelliğinin "XAML öznitelik kullanımı" bölümüne bakın <xref:System.Windows.Data.Binding> .NET Framework Sınıf Kitaplığı'nda.  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|`bindProp1, bindPropN`|Adını <xref:System.Windows.Data.Binding> veya <xref:System.Windows.Data.BindingBase> ayarlamak için özellik. Tüm <xref:System.Windows.Data.Binding> özellikleri ile ayarlanabilir `Binding` uzantısı ve bazı özellikler içinde ayarlanabilir bir `Binding` ifade yalnızca kullanarak daha fazla iç içe biçimlendirme uzantıları. "Bağlama uzantısı ile Ayarlanabilen Bağlama Özellikleri" bölümüne bakın.|  
|`value1, valueN`|Özellik ayarlanacak değer. Öznitelik değeri işleme türünü ve belirli mantığı sonuçta belirli <xref:System.Windows.Data.Binding> ayarlanan özelliği.|  
|`path`|Örtük ayarlar yol dizesi <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> özelliği. Ayrıca bkz: [PropertyPath XAML söz dizimi](propertypath-xaml-syntax.md).|  
  
## <a name="unqualified-binding"></a>Nitelenmemiş {bağlama}  
 `{Binding}` "İfadesi kullanım bağlama" gösterilen kullanım oluşturur bir <xref:System.Windows.Data.Binding> varsayılan değerlerle nesne içeren bir ilk <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> , `null`. Bu birçok senaryoda yine de yararlı olur çünkü oluşturulan <xref:System.Windows.Data.Binding> anahtar veri bağlama özellikleri gibi bağlı <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> ve <xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType> çalışma zamanı veri bağlam içinde ayarlanan. Veri bağlamı kavramı hakkında daha fazla bilgi için bkz. [veri bağlama](../data/data-binding-wpf.md).  
  
## <a name="implicit-path"></a>Örtük yolu  
 `Binding` İşaretleme uzantısı kullanan <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> kavramsal olarak "varsayılan özellik" burada `Path=` bulunamaz gerekmez. Belirtirseniz bir `Binding` ifadesi örtük bir yola sahip örtülü yol görünmelidir ilk ifadede, diğer önce `bindProp` = `value` çiftlerini nerede <xref:System.Windows.Data.Binding> özellik adıyla belirtilir. Örneğin: `{Binding PathString}`burada `PathString` değeri olarak değerlendirilen bir dizedir <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> içinde <xref:System.Windows.Data.Binding> biçimlendirme uzantısı kullanımı tarafından oluşturuldu. Örneğin, virgül ayırıcısına sonra adlandırılmış diğer özelliklere sahip örtülü bir yolu ekleyebilir `{Binding LastName, Mode=TwoWay}`.  
  
## <a name="binding-properties-that-can-be-set-with-the-binding-extension"></a>Bağlama uzantısı ile ayarlanabilir bağlama özellikleri  
 Bu konuda gösterilen sözdizimi kullanan genel `bindProp` = `value` approximation, çok sayıda okuma/yazma özellikleri olduğundan <xref:System.Windows.Data.BindingBase> veya <xref:System.Windows.Data.Binding> aracılığıyla ayarlanabilir `Binding` işaretleme uzantısı / ifade söz dizimi. Örtük dışında herhangi bir sırada ayarlanabilir <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>. (Açıkça belirtin seçeneğine sahip `Path=`, bu durumda herhangi bir sırada ayarlanabilir). Temel olarak, sıfır veya daha fazla özellik listesinde aşağıdaki kullanarak ayarlayabilirsiniz `bindProp` = `value` çiftleri noktalı virgüllerle ayrılmış.  
  
 Bu özellik değerleri birkaç XAML içinde metin sözdiziminin bir yerel tür dönüştürme desteği, ve bu nedenle, bir öznitelik değeri ayarlanması için biçimlendirme uzantıları gerektirmez nesne türleri gerektirir. XAML Öznitelik Kullanımı bölümünde daha fazla bilgi için her bir özellik için .NET Framework sınıf kitaplığı; denetleyin. XAML öznitelik sözdizimi için kullandığınız dize veya başka bir işaretleme uzantısı kullanımı temel belirttiğiniz değerle aynı olan bir `Binding` her etrafında tırnak işareti yerleştirmeyin özel durum ile bir ifade `bindProp` = `value` içinde `Binding` ifade.  
  
- <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>: olası bağlama grubunu tanımlayan bir dize. Bu göreceli olarak Gelişmiş bağlama kavramdır; için başvuru sayfasına bakın <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>.  
  
- <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A>: Boolean, olabilir `true` veya `false`. Varsayılan, `false` değeridir.  
  
- <xref:System.Windows.Data.Binding.Converter%2A>: olarak ayarlanabilir bir `bindProp` = `value` dize ifadesi, ancak bunu yapmak için bir nesne başvurusu gibi değer için gerektiren bir [StaticResource işaretleme uzantısı](staticresource-markup-extension.md). Bu durumda özel dönüştürücü sınıfının bir örneğini değerdir.  
  
- <xref:System.Windows.Data.Binding.ConverterCulture%2A>: gibi standartlara dayalı bir tanımlayıcı; ifadede ayarlanabilir başvuru konusuna bakın <xref:System.Windows.Data.Binding.ConverterCulture%2A>.  
  
- <xref:System.Windows.Data.Binding.ConverterParameter%2A>: olarak ayarlanmış bir `bindProp` = `value` dize ifadesi, ancak bu, geçirilen parametre türüne bağlıdır. Bir başvuru türü için değer geçirilirse, bu kullanım, iç içe bir gibi bir nesne başvurusu gerektirir. [StaticResource işaretleme uzantısı](staticresource-markup-extension.md).  
  
- <xref:System.Windows.Data.Binding.ElementName%2A>: karşılaştırması <xref:System.Windows.Data.Binding.RelativeSource%2A> ve <xref:System.Windows.Data.Binding.Source%2A>; her Bu bağlama özellikleri belirli bağlama metodolojisini temsil eder. Bkz: [veri bağlama genel bakış](../data/data-binding-overview.md).  
  
- <xref:System.Windows.Data.BindingBase.FallbackValue%2A>: olarak ayarlanmış bir `bindProp` = `value` dize ifadesi, ancak bu, geçirilen değerin türüne bağlıdır. Bir başvuru türü geçirme gerektiriyorsa bir nesne başvurusu bir iç içe gibi [StaticResource işaretleme uzantısı](staticresource-markup-extension.md).  
  
- <xref:System.Windows.Data.Binding.IsAsync%2A>: Boolean, olabilir `true` veya `false`. Varsayılan, `false` değeridir.  
  
- <xref:System.Windows.Data.Binding.Mode%2A>: *değer* sabit bir adı olan <xref:System.Windows.Data.BindingMode> sabit listesi. Örneğin: `{Binding Mode=OneWay}`  
  
- <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A>: Boolean, olabilir `true` veya `false`. Varsayılan, `false` değeridir.  
  
- <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A>: Boolean, olabilir `true` veya `false`. Varsayılan, `false` değeridir.  
  
- <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A>: Boolean, olabilir `true` veya `false`. Varsayılan, `false` değeridir.  
  
- <xref:System.Windows.Data.Binding.Path%2A>: bir veri nesnesi veya bir genel nesne modeline yolu açıklayan bir dize. Biçim, bu konuda açıklanan olamaz yeterince bir nesne modeline geçmek için birkaç farklı kural sağlar. Bkz: [PropertyPath XAML söz dizimi](propertypath-xaml-syntax.md).  
  
- <xref:System.Windows.Data.Binding.RelativeSource%2A>: ile karşı birbirini dışlayan <xref:System.Windows.Data.Binding.ElementName%2A> ve <xref:System.Windows.Data.Binding.Source%2A>; her Bu bağlama özellikleri belirli bağlama metodolojisini temsil eder. Bkz: [veri bağlama genel bakış](../data/data-binding-overview.md). İç içe bir gerektirir [RelativeSource işaretleme uzantısı](relativesource-markupextension.md) kullanım değeri belirtin.  
  
- <xref:System.Windows.Data.Binding.Source%2A>: karşılaştırması <xref:System.Windows.Data.Binding.RelativeSource%2A> ve <xref:System.Windows.Data.Binding.ElementName%2A>; her Bu bağlama özellikleri belirli bağlama metodolojisini temsil eder. Bkz: [veri bağlama genel bakış](../data/data-binding-overview.md). Bir iç içe uzantısı kullanımı genellikle gerektiren bir [StaticResource işaretleme uzantısı](staticresource-markup-extension.md) anahtarlı kaynak sözlüğünden bir nesne veri kaynağına başvuruyor.  
  
- <xref:System.Windows.Data.BindingBase.StringFormat%2A>: bağlı veriler için dize biçim kuralını tanımlayan bir dize. Bu göreceli olarak Gelişmiş bağlama kavramdır; için başvuru sayfasına bakın <xref:System.Windows.Data.BindingBase.StringFormat%2A>.  
  
- <xref:System.Windows.Data.BindingBase.TargetNullValue%2A>: olarak ayarlanmış bir `bindProp` = `value` dize ifadesi, ancak bu, geçirilen parametre türüne bağlıdır. Bir başvuru türü için değer geçirme gerektiriyorsa bir nesne başvurusu bir iç içe gibi [StaticResource işaretleme uzantısı](staticresource-markup-extension.md).  
  
- <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>: *değer* sabit bir adı olan <xref:System.Windows.Data.UpdateSourceTrigger> sabit listesi. Örneğin: `{Binding UpdateSourceTrigger=LostFocus}` Belirli denetimler, büyük olasılıkla bu bağlama özelliği için farklı varsayılan değerlerine sahip. Bkz. <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.  
  
- <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A>: Boolean, olabilir `true` veya `false`. Varsayılan, `false` değeridir. Açıklamalara bakın.  
  
- <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A>: Boolean, olabilir `true` veya `false`. Varsayılan, `false` değeridir. Açıklamalara bakın.  
  
- <xref:System.Windows.Data.Binding.XPath%2A>: XML veri kaynağı XMLDOM bir yolu açıklayan bir dize. Bkz: [XMLDataProvider ve XPath sorgularını kullanarak XML verilerine bağlama](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).  
  
 Aşağıdaki özellikleri olan <xref:System.Windows.Data.Binding> ayarlanamayan kullanarak `Binding` işaretleme uzantısı /`{Binding}` ifade formu.  
  
- <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>: Bu özellik bir geri çağırma uygulaması başvurusu bekliyor. Geri çağırmaları/yöntemleri olay işleyicileri dışında XAML sözdizimi başvurulamaz.  
  
- <xref:System.Windows.Data.Binding.ValidationRules%2A>: Genel koleksiyonu özelliği alır <xref:System.Windows.Controls.ValidationRule> nesneleri. Bu özellik öğesi olarak ifade edilebilir bir <xref:System.Windows.Data.Binding> nesne öğesi, ancak hiçbir hazır özniteliği ayrıştırılırken tekniği kullanım için olan bir `Binding` ifade. Başvuru konusuna <xref:System.Windows.Data.Binding.ValidationRules%2A>.  
  
- <xref:System.Windows.Data.Binding.XmlNamespaceManager%2A>  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!IMPORTANT]
>  Bağımlılık özelliği önceliği açısından bir `Binding` ifadesidir yerel olarak ayarlanmış eşdeğer değeri. Daha önce sahip olan özellik için yerel bir değer ayarlarsanız bir `Binding` ifade `Binding` tamamen kaldırılır. Ayrıntılar için bkz [bağımlılık özelliği değer önceliği](dependency-property-value-precedence.md).  
  
 Bu konuda, temel düzeyde veri bağlamasını açıklama kapsamaz. Bkz: [veri bağlama genel bakış](../data/data-binding-overview.md).  
  
> [!NOTE]
>  <xref:System.Windows.Data.MultiBinding> ve <xref:System.Windows.Data.PriorityBinding> desteklemeyen bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] uzantısı sözdizimi. Bunun yerine, özellik öğelerini kullanırsınız. İçin başvuru konularına bakın <xref:System.Windows.Data.MultiBinding> ve <xref:System.Windows.Data.PriorityBinding>.  
  
 XAML Boole değerleri büyük küçük harfe duyarlı olur. Örneğin ya da belirtebilirsiniz `{Binding NotifyOnValidationError=true}` veya `{Binding NotifyOnValidationError=True}`.  
  
 Veri doğrulama içeren bağlamaları genellikle açık bir tarafından belirtilir `Binding` öğe yerine bir `{Binding ...}` ifade ve ayarı <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> veya <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> bir ifadede seyrek olur. Bunun nedeni, eşlik özelliği <xref:System.Windows.Data.Binding.ValidationRules%2A> ifade biçiminde kolayca ayarlanamaz. Daha fazla bilgi için [uygulama bağlama doğrulaması](../data/how-to-implement-binding-validation.md).  
  
 `Binding` bir işaretleme uzantısıdır. Biçimlendirme uzantıları, genellikle öznitelik değerlerinin değişmez değerler veya işleyici isimleri dışına çıkma gereksinimi olduğunda ve gereksinim belirli türler veya özellikler yalnızca tür dönüştürücülerini koymaktan daha genel olduğunda uygulanır. XAML kullanım içindeki tüm biçimlendirme uzantıları `{` ve `}` karakter olarak bir XAML işlemcisinin bir işaretleme uzantısı dize içeriklerini işlenmesi gerektiğini, kuralına göre kendi öznitelik sözdizimi. Daha fazla bilgi için [biçimlendirme uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
 `Binding` bir alışılmamış bir biçimlendirme uzantısıdır <xref:System.Windows.Data.Binding> WPF'nin XAML uygulama uzantısı işlevselliğini uygulayan sınıf ayrıca uygulayan diğer çeşitli yöntemleri ve özellikleri için XAML ilişkili değildir. Diğer üyeler oluşturmayı amaçlar <xref:System.Windows.Data.Binding> XAML işaretleme uzantısı olarak işlev yanı sıra çok sayıda veri bağlama senaryoları ele daha verimli ve kendi başına bir sınıf.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Data.Binding>
- [Veri Bağlamaya Genel Bakış](../data/data-binding-overview.md)
- [XAML'ye Genel Bakış (WPF)](xaml-overview-wpf.md)
- [İşaretleme Uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md)
