---
title: Biçimlendirme Uzantısı Bağlama
ms.date: 03/30/2017
f1_keywords:
- Binding
helpviewer_keywords:
- Binding markup extensions [WPF]
- XAML [WPF], Binding markup extension
ms.assetid: 83d6e2a4-1b0c-4fc8-bd96-b5e98800ab63
ms.openlocfilehash: 6776c89db474668b3aed0e38a3e18359bf93399d
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991476"
---
# <a name="binding-markup-extension"></a>Biçimlendirme Uzantısı Bağlama
Bir özellik değerini veri bağlantılı değer olacak şekilde erteler, bir ara ifade nesnesi oluşturma ve çalışma zamanında öğe ve bağlama için geçerli olan veri bağlamını yorumlama.  
  
## <a name="binding-expression-usage"></a>Bağlama Ifadesi kullanımı  
  
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
  
## <a name="syntax-notes"></a>Söz dizimi notları  
 Bu sözdizimlerde, `[]` ve `*` değişmez değer değildir. Bu değerler, sıfır veya daha fazla *bindProp*`=`*değer* çiftlerinin kullanılabileceğini belirten, aralarında ve önünde *bindProp*`=`*değer* çiftleri arasında `,` bir ayırıcı olan bir gösterimin parçasıdır.  
  
 "Bağlama uzantısı ile ayarlanabilir olan bağlama özellikleri" bölümünde listelenen özelliklerden herhangi biri bunun yerine bir <xref:System.Windows.Data.Binding> nesne öğesinin öznitelikleri kullanılarak ayarlanabilir. Bununla birlikte, yalnızca biçimlendirme uzantısı kullanımı <xref:System.Windows.Data.Binding>, clr <xref:System.Windows.Data.Binding> sınıfının özelliklerini ayarlamış olan özniteliklerin yalnızca genel xaml işlemesinin değildir. Diğer bir deyişle, `<Binding` *bindProp1*`="`*değer1*bindpropn`="` <xref:System.Windows.Data.Binding> valueN,nesneöğesikullanımınınöznitelikleriiçineşdeğerbirsözdizimidir`"]*/>` `"[` yerine bir `Binding` ifade kullanımı. Belirli özelliklerinin <xref:System.Windows.Data.Binding>xaml öznitelik kullanımı hakkında bilgi edinmek için, .NET Framework sınıf kitaplığındaki ilgili <xref:System.Windows.Data.Binding> özelliğinin "xaml öznitelik kullanımı" bölümüne bakın.  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|`bindProp1, bindPropN`|Ayarlanacak <xref:System.Windows.Data.Binding> veya<xref:System.Windows.Data.BindingBase> özelliğin adı. Tüm <xref:System.Windows.Data.Binding> Özellikler `Binding` uzantı ile ayarlanamaz ve bazı özellikler yalnızca daha fazla iç içe biçimlendirme uzantıları kullanılarak bir `Binding` ifade içinde ayarlanabilir. "Bağlama uzantısı ile ayarlanabilir Özellikler" bölümüne bakın.|  
|`value1, valueN`|Özelliği ayarlanacak değer. Öznitelik değerinin işlenmesi, sonunda ayarlanan belirli <xref:System.Windows.Data.Binding> özelliğin türüne ve mantığına özgüdür.|  
|`path`|Örtük <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> özelliği ayarlayan yol dizesi. Ayrıca bkz. [PROPERTYPATH XAML sözdizimi](propertypath-xaml-syntax.md).|  
  
## <a name="unqualified-binding"></a>Nitelenmemiş {Binding}  
 "Bağlama ifadesi kullanımı" içinde gösterilen <xref:System.Windows.Data.Binding> <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> `null` `{Binding}` kullanım, bir başlangıç içeren varsayılan değerlerle bir nesne oluşturur. Bu, çok sayıda senaryoda hala yararlıdır, çünkü oluşturulan <xref:System.Windows.Data.Binding> , çalışma zamanı veri bağlamında ayarlanmakta olan <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> ve <xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType> gibi önemli veri bağlama özelliklerine bağlı olabilir. Veri bağlamı kavramı hakkında daha fazla bilgi için bkz. [veri bağlama](../data/data-binding-wpf.md).  
  
## <a name="implicit-path"></a>Örtük yol  
 Biçimlendirme Uzantısı kavramsal " <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> varsayılan özellik" olarak kullanılır, burada `Path=` ifadede görünmesi gerekmez. `Binding` Örtük bir yol içeren `Binding` bir ifade belirtirseniz, <xref:System.Windows.Data.Binding> özelliğin ada göre belirttiği diğer `bindProp` = `value` çiftler öncesinde örtük yol, ifadede ilk olarak görünmelidir. Örneğin: `{Binding PathString}` <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> ,, <xref:System.Windows.Data.Binding> biçimlendirme uzantısı kullanımı tarafından oluşturulan içinde değeri olarak değerlendirilen bir dizedir. `PathString` Virgül ayırıcısından sonra diğer adlandırılmış özelliklerle örtük bir yol ekleyebilirsiniz, örneğin, `{Binding LastName, Mode=TwoWay}`.  
  
## <a name="binding-properties-that-can-be-set-with-the-binding-extension"></a>Bağlama uzantısıyla ayarlanabilir Özellikler bağlama  
 Bu konuda gösterilen sözdizimi `bindProp` , ' `value` <xref:System.Windows.Data.BindingBase> = ınveya<xref:System.Windows.Data.Binding> biçimlendirme uzantısı aracılığıyla ayarlanabileceğinden birçok okuma/yazma özelliği olduğundan genel bir yaklaşık değer kullanır. `Binding` ifade sözdizimi. Örtülü <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>dışında, herhangi bir sırada ayarlanabilir. (Herhangi bir sırada ayarlanmamanız durumunda, `Path=`açıkça belirtme seçeneğiniz vardır). Temel olarak, virgülle ayrılmış çiftleri kullanarak `bindProp` = `value` aşağıdaki listede bulunan özelliklerden sıfır veya daha fazlasını ayarlayabilirsiniz.  
  
 Bu özellik değerlerinin birkaçı XAML içindeki bir metin sözdiziminden yerel tür dönüştürmeyi desteklemeyen nesne türleri gerektirir ve bu nedenle bir öznitelik değeri olarak ayarlanmaları için biçimlendirme uzantıları gerektirir. Daha fazla bilgi için her bir özelliğin .NET Framework sınıf kitaplığındaki XAML öznitelik kullanımı bölümüne bakın; daha fazla biçimlendirme uzantısı kullanımı olan veya olmadan xaml öznitelik sözdizimi için kullandığınız dize, her birinin `Binding` `bindProp` =çevresinetırnakişaretiyerleştirmeyinözeldurumiletemeldebelirttiğinizdeğerleaynıdır.ifadesi. `value` `Binding`  
  
- <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>: olası bir bağlama grubunu tanımlayan bir dize. Bu görece gelişmiş bir bağlama kavramıdır; için <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>başvuru sayfasına bakın.  
  
- <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A>: Boolean, ya da `true` `false`olabilir. Varsayılan, `false` değeridir.  
  
- <xref:System.Windows.Data.Binding.Converter%2A>: `bindProp` ifadede bir = dize`value` olarak ayarlanabilir, ancak bunu yapmak için değer için bir [StaticResource İşaretleme uzantısı](staticresource-markup-extension.md)gibi bir nesne başvurusu gerekir. Bu örnekteki değer bir özel dönüştürücü sınıfının örneğidir.  
  
- <xref:System.Windows.Data.Binding.ConverterCulture%2A>: ifadede standartlara dayalı bir tanımlayıcı olarak ayarlanabilir; için <xref:System.Windows.Data.Binding.ConverterCulture%2A>başvuru konusuna bakın.  
  
- <xref:System.Windows.Data.Binding.ConverterParameter%2A>: ifadede bir `bindProp` = dizeolarakayarlanabilir,ancakbu,geçirilenparametrenintürünebağlıdır.`value` Değer için bir başvuru türü geçirilirse, bu kullanım iç içe bir [StaticResource biçimlendirme uzantısı](staticresource-markup-extension.md)gibi bir nesne başvurusu gerektirir.  
  
- <xref:System.Windows.Data.Binding.ElementName%2A>: birbirini dışlamalı <xref:System.Windows.Data.Binding.RelativeSource%2A> ve <xref:System.Windows.Data.Binding.Source%2A>; bu bağlama özelliklerinin her biri belirli bir bağlama yöntemini temsil eder. Bkz. [veri bağlamaya genel bakış](../data/data-binding-overview.md).  
  
- <xref:System.Windows.Data.BindingBase.FallbackValue%2A>: ifadede bir `bindProp` = dizeolarakayarlanabilir,ancakbu,geçirilendeğerintürünebağlıdır.`value` Bir başvuru türü geçirilirse, iç içe bir [StaticResource biçimlendirme uzantısı](staticresource-markup-extension.md)gibi bir nesne başvurusu gerekir.  
  
- <xref:System.Windows.Data.Binding.IsAsync%2A>: Boolean, ya da `true` `false`olabilir. Varsayılan, `false` değeridir.  
  
- <xref:System.Windows.Data.Binding.Mode%2A>: *değer* , <xref:System.Windows.Data.BindingMode> Numaralandırmadaki sabit bir addır. Örneğin: `{Binding Mode=OneWay}`.  
  
- <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A>: Boolean, ya da `true` `false`olabilir. Varsayılan, `false` değeridir.  
  
- <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A>: Boolean, ya da `true` `false`olabilir. Varsayılan, `false` değeridir.  
  
- <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A>: Boolean, ya da `true` `false`olabilir. Varsayılan, `false` değeridir.  
  
- <xref:System.Windows.Data.Binding.Path%2A>: bir veri nesnesine veya genel nesne modeline bir yolu tanımlayan bir dize. Biçim, bu konuda yeterince açıklanamaz bir nesne modelinde geçiş için birkaç farklı kural sağlar. Bkz. [PROPERTYPATH XAML sözdizimi](propertypath-xaml-syntax.md).  
  
- <xref:System.Windows.Data.Binding.RelativeSource%2A>: ve <xref:System.Windows.Data.Binding.ElementName%2A> <xref:System.Windows.Data.Binding.Source%2A>ile karşılıklı dışlamalı, bu bağlama özelliklerinin her biri belirli bir bağlama yöntemini temsil eder. Bkz. [veri bağlamaya genel bakış](../data/data-binding-overview.md). Değeri belirtmek için iç içe bir [RelativeSource MarkupExtension](relativesource-markupextension.md) kullanımı gerektirir.  
  
- <xref:System.Windows.Data.Binding.Source%2A>: birbirini dışlamalı <xref:System.Windows.Data.Binding.RelativeSource%2A> ve <xref:System.Windows.Data.Binding.ElementName%2A>; bu bağlama özelliklerinin her biri belirli bir bağlama yöntemini temsil eder. Bkz. [veri bağlamaya genel bakış](../data/data-binding-overview.md). Yalnızca bir anahtarlı kaynak sözlüğünden bir nesne veri kaynağına başvuran bir [StaticResource Işaretleme uzantısı](staticresource-markup-extension.md) olan iç içe geçmiş uzantı kullanımı gerektirir.  
  
- <xref:System.Windows.Data.BindingBase.StringFormat%2A>: bağlanan veriler için bir dize biçimi kuralını tanımlayan bir dize. Bu görece gelişmiş bir bağlama kavramıdır; için <xref:System.Windows.Data.BindingBase.StringFormat%2A>başvuru sayfasına bakın.  
  
- <xref:System.Windows.Data.BindingBase.TargetNullValue%2A>: ifadede bir `bindProp` = dizeolarakayarlanabilir,ancakbu,geçirilenparametrenintürünebağlıdır.`value` Değer için bir başvuru türü geçirilirse, iç içe bir [StaticResource biçimlendirme uzantısı](staticresource-markup-extension.md)gibi bir nesne başvurusu gerektirir.  
  
- <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>: *değer* , <xref:System.Windows.Data.UpdateSourceTrigger> Numaralandırmadaki sabit bir addır. Örneğin: `{Binding UpdateSourceTrigger=LostFocus}`. Belirli denetimler, bu bağlama özelliği için muhtemelen farklı varsayılan değerlere sahip olabilir. Bkz. <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.  
  
- <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A>: Boolean, ya da `true` `false`olabilir. Varsayılan, `false` değeridir. Bkz. açıklamalar.  
  
- <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A>: Boolean, ya da `true` `false`olabilir. Varsayılan, `false` değeridir. Bkz. açıklamalar.  
  
- <xref:System.Windows.Data.Binding.XPath%2A>: bir XML veri kaynağının XMLDOM 'ına bir yol tanımlayan bir dize. Bkz. [XMLDataProvider ve XPath sorgularını kullanarak XML verilerine bağlama](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).  
  
 Aşağıda, `Binding` biçimlendirme uzantısı/ <xref:System.Windows.Data.Binding> `{Binding}` ifade formu kullanılarak ayarlanamaz özellikleri verilmiştir.  
  
- <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>: Bu özellik, geri çağırma uygulamasına bir başvuru bekliyor. Olay işleyicileri dışındaki geri çağırmaları/yöntemlere XAML sözdiziminde başvurulamaz.  
  
- <xref:System.Windows.Data.Binding.ValidationRules%2A>: özelliği <xref:System.Windows.Controls.ValidationRule> nesnenin genel koleksiyonunu alır. Bu bir <xref:System.Windows.Data.Binding> nesne öğesinde bir özellik öğesi olarak ifade edilebilir, ancak bir `Binding` ifadede kullanım için uygun bir öznitelik ayrıştırma tekniği yok. İçin <xref:System.Windows.Data.Binding.ValidationRules%2A>başvuru konusuna bakın.  
  
- <xref:System.Windows.Data.Binding.XmlNamespaceManager%2A>  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!IMPORTANT]
> Bağımlılık özelliği önceliği açısından, bir `Binding` ifade yerel olarak ayarlanan değere eşdeğerdir. Daha önce bir `Binding` ifadeye sahip olan bir özellik için yerel bir değer ayarlarsanız, `Binding` tamamen kaldırılır. Ayrıntılar için bkz. [bağımlılık özelliği değer önceliği](dependency-property-value-precedence.md).  
  
 Temel düzeyde veri bağlamayı açıklama bu konuda ele alınmıyor. Bkz. [veri bağlamaya genel bakış](../data/data-binding-overview.md).  
  
> [!NOTE]
> <xref:System.Windows.Data.MultiBinding>uzantısöz[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dizimini desteklemez. <xref:System.Windows.Data.PriorityBinding> Bunun yerine özellik öğelerini kullanmanız gerekir. <xref:System.Windows.Data.MultiBinding> Ve<xref:System.Windows.Data.PriorityBinding>için başvuru konularına bakın.  
  
 XAML için Boole değerleri büyük/küçük harfe duyarlıdır. Örneğin, ya `{Binding NotifyOnValidationError=true}` `{Binding NotifyOnValidationError=True}`da belirtebilirsiniz.  
  
 Veri `Binding` doğrulamayı içeren bağlamalar genellikle `{Binding ...}` ifade olarak değil açık bir öğe tarafından belirtilir ve bir ifadede veya <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> bir ifadede ayarlanması <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> çok seyrek olur. Bunun nedeni, yardımcı özelliğin <xref:System.Windows.Data.Binding.ValidationRules%2A> ifade biçiminde kolayca ayarlanamamasıdır. Daha fazla bilgi için bkz. [bağlama doğrulamasını uygulama](../data/how-to-implement-binding-validation.md).  
  
 `Binding`bir biçimlendirme uzantısıdır. Biçimlendirme uzantıları genellikle öznitelik değerlerinin sabit değerler veya işleyici adlarından farklı olması için bir gereksinim olduğunda uygulanır ve gereksinim, belirli tür veya özelliklere sahip tür dönüştürücülerden daha geneldir. Xaml 'deki tüm biçimlendirme uzantıları, `{` öznitelik sözdiziminde ve `}` karakterlerini kullanır. Bu, XAML işlemcisinin bir biçimlendirme uzantısının dize içeriğini işlemesi gerektiğini tanıdığı bir kuraldır. Daha fazla bilgi için bkz. [Biçimlendirme uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
 `Binding`, WPF 'nin xaml uygulamasına yönelik uzantı işlevselliğini uygulayan <xref:System.Windows.Data.Binding> sınıfın Ayrıca XAML ile ilgili olmayan diğer birçok yöntemi ve özelliği de uyguladığı bir tipik biçimlendirme uzantısıdır. Diğer Üyeler, XAML biçimlendirme uzantısı olarak <xref:System.Windows.Data.Binding> çalışmaya ek olarak birçok veri bağlama senaryosunu ele alan daha çok yönlü ve kendi kendine içerilen bir sınıf oluşturmak için tasarlanmıştır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Data.Binding>
- [Veri Bağlamaya Genel Bakış](../data/data-binding-overview.md)
- [XAML'ye Genel Bakış (WPF)](xaml-overview-wpf.md)
- [İşaretleme Uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md)
