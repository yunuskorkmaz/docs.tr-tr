---
title: Biçimlendirme Uzantısı Bağlama
ms.date: 03/30/2017
f1_keywords:
- Binding
helpviewer_keywords:
- Binding markup extensions [WPF]
- XAML [WPF], Binding markup extension
ms.assetid: 83d6e2a4-1b0c-4fc8-bd96-b5e98800ab63
ms.openlocfilehash: c6a424e085c7499db08d0a7e6b652f45fb2cdd70
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644078"
---
# <a name="binding-markup-extension"></a>Biçimlendirme Uzantısı Bağlama
Bir özellik değerini veriye bağlı bir değer olarak erteler, ara ifade nesnesi oluşturur ve çalışma zamanında öğe ve bağlamaiçin geçerli olan veri bağlamını yorumlar.  
  
## <a name="binding-expression-usage"></a>Bağlayıcı İfade Kullanımı  
  
```xaml  
<object property="{Binding}" .../>  
-or-  
<object property="{Binding  bindProp1=value1[, bindPropN=valueN]*}" ...  
/>  
-or-  
<object property="{Binding path}" .../>  
-or  
<object property="{Binding path[, bindPropN=valueN]*}" .../>  
```  
  
## <a name="syntax-notes"></a>Sözdizimi Notları  
 Bu `[]` sözdizimlerinde, `*` ve edebi değildir. Bunlar, aralarında bir ayırıcı ve önceki *bindProp*`=`*değer* çiftleri ile sıfır veya daha fazla *bindProp*`=`*değer* çiftleri kullanılabileceğini belirtmek için bir `,` gösterimin parçasıdır.  
  
 "Bağlama Uzantısı ile Ayarlanabilen Bağlama Özellikleri" bölümünde listelenen özelliklerden herhangi biri, <xref:System.Windows.Data.Binding> bunun yerine bir nesne öğesinin öznitelikleri kullanılarak ayarlanabilir. Ancak, bu gerçekten biçimlendirme uzantısı <xref:System.Windows.Data.Binding>kullanımı değil , clr <xref:System.Windows.Data.Binding> sınıfının özelliklerini ayarlamak öznitelikleri sadece genel XAML işleme. Başka bir `<Binding` deyişle, *bindProp1*`="` *valuedPropN*`="``"]*/>` <xref:System.Windows.Data.Binding> `Binding` *valueN,* *value1* `"[` ifade kullanımı yerine nesne öğesi kullanımıözleri için eşdeğer bir sözdizimidir. Belirli özelliklerin <xref:System.Windows.Data.Binding>XAML öznitelik kullanımı hakkında bilgi edinmek için .NET Framework Class Kitaplığı'ndaki ilgili özelliğin <xref:System.Windows.Data.Binding> "XAML Öznitelik Kullanımı" bölümüne bakın.  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|`bindProp1, bindPropN`|Ayarlanan <xref:System.Windows.Data.Binding> özelliğin <xref:System.Windows.Data.BindingBase> adı. Tüm <xref:System.Windows.Data.Binding> özellikler `Binding` uzantıyla ayarlanamaz ve bazı özellikler `Binding` yalnızca daha iç içe olan biçimlendirme uzantıları kullanılarak bir ifade içinde ayarlanabilir. Bkz. "Bağlama Uzantısı ile Ayarlanabilen Bağlama Özellikleri" bölümüne bakın.|  
|`value1, valueN`|Özelliği ayarlamak için değer. Öznitelik değerinin işlenmesi sonuçta ayarlanan belirli <xref:System.Windows.Data.Binding> özelliğin türüne ve mantığına özgüdür.|  
|`path`|Örtük <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> özelliği ayarlayan yol dizesi. Ayrıca bakınız [PropertyPath XAML Sözdizimi.](propertypath-xaml-syntax.md)|  
  
## <a name="unqualified-binding"></a>Niteliksiz {Bağlama}  
 "Bağlama İfadeSi Kullanımı"nda `{Binding}` gösterilen <xref:System.Windows.Data.Binding> kullanım, <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> `null`ilk harfini içeren varsayılan değerlere sahip bir nesne oluşturur. Oluşturulan <xref:System.Windows.Data.Binding> gibi anahtar veri bağlama özellikleri güvenerek <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> olabilir ve <xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType> çalışma zamanı veri bağlamında ayarlanması, çünkü bu, birçok senaryoda hala yararlıdır. Veri bağlamı kavramı hakkında daha fazla bilgi için [bkz.](../../../desktop-wpf/data/data-binding-overview.md)  
  
## <a name="implicit-path"></a>Örtük Yol  
 `Binding` Biçimlendirme uzantısı, <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> `Path=` ifadede görünmesi gerekmeyen kavramsal bir "varsayılan özellik" olarak kullanır. Örtük bir `Binding` yol ile bir ifade belirtirseniz, örtük yol özelliği `bindProp` = `value` ad ile <xref:System.Windows.Data.Binding> belirtilen diğer çiftleri önce, ifadede ilk görünmesi gerekir. Örneğin:, `{Binding PathString}`biçimlendirme uzantısı kullanımı tarafından `PathString` <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> <xref:System.Windows.Data.Binding> oluşturulan değeri olarak değerlendirilen bir dize nerede. Virgül ayırıcıdan sonra diğer adlandırılmış özellikleri ile örtülü bir `{Binding LastName, Mode=TwoWay}`yol ekleyebilirsiniz, örneğin.  
  
## <a name="binding-properties-that-can-be-set-with-the-binding-extension"></a>Bağlama Uzantısı ile Ayarlanabilen Bağlama Özellikleri  
 Bu konuda gösterilen sözdizimi, `bindProp` = `value` `Binding` biçimlendirme uzantısı / ifade sözdizimi <xref:System.Windows.Data.BindingBase> aracılığıyla <xref:System.Windows.Data.Binding> ayarlanabilen çok sayıda okuma/yazma özelliği olduğundan genel yaklaşım kullanır. Bunlar örtülü <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>bir istisna dışında, herhangi bir sırada ayarlanabilir. (Bu durumda herhangi bir sırada `Path=`ayarlanabileceğini açıkça belirtme seçeneğiniz vardır). Temel olarak, virgülle ayrılmış çiftleri kullanarak `bindProp` = `value` aşağıdaki listedeki özelliklerin sıfırveya daha fazlasını ayarlayabilirsiniz.  
  
 Bu özellik değerlerinden bazıları, XAML'deki bir metin sözdiziminden yerel tür dönüştürmesini desteklemeyen nesne türleri gerektirir ve bu nedenle öznitelik değeri olarak ayarlanabilmesi için biçimlendirme uzantıları gerektirir. Daha fazla bilgi için her özellik için .NET Framework Class Kitaplığı'ndaki XAML Öznitelik Kullanımı bölümünü kontrol edin; XAML öznitelik sözdizimi için kullandığınız dize, daha fazla biçimlendirme uzantısı kullanımı yla `Binding` veya daha fazla biçimlendirme uzantısı kullanımı olmadan `bindProp` = `value` temelde `Binding` ifadede belirttiğiniz değerle aynıdır, ancak ifadede her birinin etrafına tırnak işaretleri yerleştirmezsiniz.  
  
- <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>: olası bir bağlama grubunu tanımlayan bir dize. Bu nispeten gelişmiş bir bağlama kavramıdır; için <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>başvuru sayfasına bakın.  
  
- <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A>: Boolean, ya `true` `false`olabilir ya . Varsayılan değer: `false`.  
  
- <xref:System.Windows.Data.Binding.Converter%2A>: ifadede bir `bindProp` = `value` dize olarak ayarlanabilir, ancak bunu yapmak için statik kaynak [biçimlendirme uzantısı](staticresource-markup-extension.md)gibi değer için bir nesne başvurusu gerektirir. Bu durumda değer özel bir dönüştürücü sınıfının bir örneğidir.  
  
- <xref:System.Windows.Data.Binding.ConverterCulture%2A>: ifadede standartlara dayalı tanımlayıcı olarak ayarlanan; için <xref:System.Windows.Data.Binding.ConverterCulture%2A>başvuru konusuna bakın.  
  
- <xref:System.Windows.Data.Binding.ConverterParameter%2A>: ifadede bir `bindProp` = `value` dize olarak ayarlanabilir, ancak bu geçirilen parametrenin türüne bağlıdır. Değer için bir başvuru türü geçiyorsa, bu kullanım iç içe geçmiş [Statik Kaynak Biçimlendirme Uzantısı](staticresource-markup-extension.md)gibi bir nesne başvurusu gerektirir.  
  
- <xref:System.Windows.Data.Binding.ElementName%2A>: karşılıklı münhasır <xref:System.Windows.Data.Binding.RelativeSource%2A> <xref:System.Windows.Data.Binding.Source%2A>karşı ve ; bu bağlama özelliklerinin her biri belirli bir bağlama metodolojisini temsil eder. [Bkz. Veri Bağlama Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md).  
  
- <xref:System.Windows.Data.BindingBase.FallbackValue%2A>: ifadede bir `bindProp` = `value` dize olarak ayarlanabilir, ancak bu geçirilen değerin türüne bağlıdır. Bir başvuru türünü geçiyorsa, iç içe geçmiş [Statik Kaynak Biçimlendirme Uzantısı](staticresource-markup-extension.md)gibi bir nesne başvurusu gerektirir.  
  
- <xref:System.Windows.Data.Binding.IsAsync%2A>: Boolean, ya `true` `false`olabilir ya . Varsayılan değer: `false`.  
  
- <xref:System.Windows.Data.Binding.Mode%2A>: *değer* numaralandırmadan <xref:System.Windows.Data.BindingMode> sabit bir addır. Örneğin, `{Binding Mode=OneWay}`.  
  
- <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A>: Boolean, ya `true` `false`olabilir ya . Varsayılan değer: `false`.  
  
- <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A>: Boolean, ya `true` `false`olabilir ya . Varsayılan değer: `false`.  
  
- <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A>: Boolean, ya `true` `false`olabilir ya . Varsayılan değer: `false`.  
  
- <xref:System.Windows.Data.Binding.Path%2A>: bir veri nesnesine veya genel nesne modeline giden yolu açıklayan bir dize. Biçim, bu konuda yeterince açıklanamayan bir nesne modelinde geçiş için birkaç farklı kural sağlar. Bkz. [PropertyPath XAML Sözdizimi.](propertypath-xaml-syntax.md)  
  
- <xref:System.Windows.Data.Binding.RelativeSource%2A>: karşılıklı münhasır <xref:System.Windows.Data.Binding.ElementName%2A> karşı <xref:System.Windows.Data.Binding.Source%2A>ve ; bu bağlama özelliklerinin her biri belirli bir bağlama metodolojisini temsil eder. [Bkz. Veri Bağlama Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md). Değeri belirtmek için iç içe bir [RelativeSource MarkupExtension](relativesource-markupextension.md) kullanımı gerektirir.  
  
- <xref:System.Windows.Data.Binding.Source%2A>: karşılıklı münhasır <xref:System.Windows.Data.Binding.RelativeSource%2A> <xref:System.Windows.Data.Binding.ElementName%2A>karşı ve ; bu bağlama özelliklerinin her biri belirli bir bağlama metodolojisini temsil eder. [Bkz. Veri Bağlama Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md). Anahtarlı kaynak sözlüğünden bir nesne veri kaynağına başvuran bir statik kaynak [biçimlendirme uzantısı](staticresource-markup-extension.md) olan iç içe geçmiş bir uzantı kullanımı gerektirir.  
  
- <xref:System.Windows.Data.BindingBase.StringFormat%2A>: bağlı veriler için dize biçimi kuralını açıklayan bir dize. Bu nispeten gelişmiş bir bağlama kavramıdır; için <xref:System.Windows.Data.BindingBase.StringFormat%2A>başvuru sayfasına bakın.  
  
- <xref:System.Windows.Data.BindingBase.TargetNullValue%2A>: ifadede bir `bindProp` = `value` dize olarak ayarlanabilir, ancak bu geçirilen parametrenin türüne bağlıdır. Değer için bir başvuru türünü geçmek, iç içe geçmiş [Statik Kaynak Biçimlendirme Uzantısı](staticresource-markup-extension.md)gibi bir nesne başvurusu gerektirir.  
  
- <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>: *değer* numaralandırmadan <xref:System.Windows.Data.UpdateSourceTrigger> sabit bir addır. Örneğin, `{Binding UpdateSourceTrigger=LostFocus}`. Belirli denetimler, bu bağlama özelliği için farklı varsayılan değerlere sahip olabilir. Bkz. <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.  
  
- <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A>: Boolean, ya `true` `false`olabilir ya . Varsayılan değer: `false`. Bkz. Açıklamalar.  
  
- <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A>: Boolean, ya `true` `false`olabilir ya . Varsayılan değer: `false`. Bkz. Açıklamalar.  
  
- <xref:System.Windows.Data.Binding.XPath%2A>: Bir XML veri kaynağının XMLDOM içine bir yol açıklayan bir dize. [Bir XMLDataProvider ve XPath Sorguları kullanarak XML Veri Bind](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)bakın.  
  
 Aşağıda <xref:System.Windows.Data.Binding> `Binding` biçimlendirme uzantısı/`{Binding}` ifade formu kullanılarak ayarlanamayan özellikler verilmiştir.  
  
- <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>: bu özellik, geri arama uygulamasına bir başvuru bekliyor. XAML sözdiziminde olay işleyicileri dışındaki geri arama/yöntemler başvurulamaz.  
  
- <xref:System.Windows.Data.Binding.ValidationRules%2A>: özellik <xref:System.Windows.Controls.ValidationRule> nesnelerin genel bir koleksiyon alır. Bu, bir <xref:System.Windows.Data.Binding> nesne öğesinde özellik öğesi olarak ifade edilebilir, ancak bir `Binding` ifadede kullanım için hazır kullanılabilir öznitelik ayrıştırma tekniği yoktur. Bkz. başvuru <xref:System.Windows.Data.Binding.ValidationRules%2A>konusu.  
  
- <xref:System.Windows.Data.Binding.XmlNamespaceManager%2A>  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!IMPORTANT]
> Bağımlılık özelliği önceliği açısından, bir `Binding` ifade yerel olarak ayarlanmış bir değere eşdeğerdir. Daha önce bir ifadesi olan bir özellik `Binding` için yerel `Binding` bir değer ayarlarsanız, bu değer tamamen kaldırılır. Ayrıntılar için Bkz. [Bağımlılık Özelliği Değeri Önceliği.](dependency-property-value-precedence.md)  
  
 Temel düzeyde veri bağlama açıklayan bu konuda ele alınmaz. [Bkz. Veri Bağlama Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md).  
  
> [!NOTE]
> <xref:System.Windows.Data.MultiBinding>ve <xref:System.Windows.Data.PriorityBinding> bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] uzantı sözdizimini desteklemez. Bunun yerine özellik öğelerini kullanırsınız. Bkz. <xref:System.Windows.Data.MultiBinding> başvuru <xref:System.Windows.Data.PriorityBinding>konuları ve .  
  
 XAML için Boolean değerleri büyük/küçük harf duyarsızdır. Örneğin ya belirtebilirsiniz `{Binding NotifyOnValidationError=true}` `{Binding NotifyOnValidationError=True}`ya da .  
  
 Veri doğrulaması içeren bağlamalar genellikle ifade `Binding` olarak değil, `{Binding ...}` açık bir <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> öğe <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> tarafından belirtilir ve ayar veya bir ifade de nadirdir. Bunun nedeni, eşlik <xref:System.Windows.Data.Binding.ValidationRules%2A> eden özelliğin ifade biçiminde kolayca ayarlanamamasıdır. Daha fazla bilgi için [bkz.](../data/how-to-implement-binding-validation.md)  
  
 `Binding`biçimlendirme uzantısıdır. Biçimlendirme uzantıları genellikle öznitelik değerlerinden kaçma gereksinimi gerçek değerler veya işleyici adlarından başka bir gereksinim olduğunda uygulanır ve gereksinim, belirli türlerde veya özelliklere atfedilen tür dönüştürücülerinden daha geneldir. XAML'deki tüm biçimlendirme `{` uzantıları, bir XAML işlemcisinin bir biçimlendirme uzantısının dize içeriğini işlemesi gerektiğini kabul ettiği kural olan öznitelik sözdiziminde karakterleri ve `}` karakterleri kullanır. Daha fazla bilgi için [bkz: Biçimlendirme Uzantıları ve WPF XAML.](markup-extensions-and-wpf-xaml.md)  
  
 `Binding`WPF'nin XAML uygulaması <xref:System.Windows.Data.Binding> için uzantı işlevini uygulayan sınıfın XAML ile ilgili olmayan birkaç diğer yöntem ve özelliği de uyguladığı atipik bir biçimlendirme uzantısıdır. Diğer üyeler, XAML biçimlendirme uzantısı olarak işlev ine ek olarak birçok veri bağlama senaryosunu ele alabilecek daha çok yönlü ve bağımsız bir sınıf yapmak <xref:System.Windows.Data.Binding> için tasarlanmıştır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Data.Binding>
- [Veri Bağlama Genel Bakış](../../../desktop-wpf/data/data-binding-overview.md)
- [XAML'ye Genel Bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Biçimlendirme Uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md)
