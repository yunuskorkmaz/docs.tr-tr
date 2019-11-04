---
title: Biçimlendirme Uzantısı Bağlama
ms.date: 03/30/2017
f1_keywords:
- Binding
helpviewer_keywords:
- Binding markup extensions [WPF]
- XAML [WPF], Binding markup extension
ms.assetid: 83d6e2a4-1b0c-4fc8-bd96-b5e98800ab63
ms.openlocfilehash: d0a437e756da16db978d8074c4355fd83d211b67
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73453605"
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
 Bu sözdizimlerde `[]` ve `*` değişmez değer değildir. Bu değerler, sıfır veya daha fazla *bindprop*`=`*değer* çiftlerinin kullanılabileceğini belirten, aralarında ve önünde *bindProp*`=`*değer* çiftleri arasında `,` bir ayırıcıyla birlikte bir gösterimin parçasıdır.  
  
 "Bağlama uzantısı ile ayarlanabilir olan bağlama özellikleri" bölümünde listelenen özelliklerden herhangi biri bunun yerine <xref:System.Windows.Data.Binding> nesne öğesinin öznitelikleri kullanılarak ayarlanabilir. Ancak, <xref:System.Windows.Data.Binding>biçimlendirme uzantısının kullanımı gerçek değildir, yalnızca CLR <xref:System.Windows.Data.Binding> sınıfının özelliklerini ayarlamış olan özniteliklerin Genel XAML işlemesiyle aynıdır. Diğer bir deyişle, `<Binding` *bindProp1*`="`*değer1*`"[` *Bindpropn*`="`*valueN*`"]*/>`, <xref:System.Windows.Data.Binding> ifade kullanımı yerine `Binding` nesne öğesi kullanımı öznitelikleri için eşdeğer bir sözdizimidir. <xref:System.Windows.Data.Binding>belirli özelliklerinin XAML öznitelik kullanımı hakkında bilgi edinmek için .NET Framework sınıf kitaplığındaki <xref:System.Windows.Data.Binding> ilgili özelliğin "XAML öznitelik kullanımı" bölümüne bakın.  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|`bindProp1, bindPropN`|Ayarlanacak <xref:System.Windows.Data.Binding> veya <xref:System.Windows.Data.BindingBase> özelliğinin adı. <xref:System.Windows.Data.Binding> özelliklerinin hepsi `Binding` uzantısıyla ayarlanamaz ve bazı özellikler yalnızca daha fazla iç içe biçimlendirme uzantıları kullanılarak `Binding` ifadesinde ayarlanabilir. "Bağlama uzantısı ile ayarlanabilir Özellikler" bölümüne bakın.|  
|`value1, valueN`|Özelliği ayarlanacak değer. Öznitelik değerinin işlenmesi, son olarak ayarlanan <xref:System.Windows.Data.Binding> özelliğin türüne ve mantığına özgüdür.|  
|`path`|Örtük <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> özelliğini ayarlayan yol dizesi. Ayrıca bkz. [PROPERTYPATH XAML sözdizimi](propertypath-xaml-syntax.md).|  
  
## <a name="unqualified-binding"></a>Nitelenmemiş {Binding}  
 "Bağlama Ifadesi kullanımı" içinde gösterilen `{Binding}` kullanımı, `null`ilk <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> içeren varsayılan değerler içeren bir <xref:System.Windows.Data.Binding> nesnesi oluşturur. Oluşturulan <xref:System.Windows.Data.Binding>, <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> ve çalışma zamanı veri bağlamında ayarlanan <xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType> gibi anahtar veri bağlama özelliklerine bağlı olabileceğinden, bu pek çok senaryoda hala yararlıdır. Veri bağlamı kavramı hakkında daha fazla bilgi için bkz. [veri bağlama](../data/data-binding-wpf.md).  
  
## <a name="implicit-path"></a>Örtük yol  
 `Binding` biçimlendirme uzantısı kavramsal bir "varsayılan özellik" olarak <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> kullanır, burada `Path=` ifadede görünmesine gerek kalmaz. Örtük bir yol içeren bir `Binding` ifadesi belirtirseniz, <xref:System.Windows.Data.Binding> özelliğinin ada göre belirttiği diğer `bindProp``value` =önce, ifadede ilk olarak örtük yol görünmelidir. Örneğin: `{Binding PathString}`, `PathString`, biçimlendirme uzantısı kullanımı tarafından oluşturulan <xref:System.Windows.Data.Binding> <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> değeri olarak değerlendirilen bir dizedir. Virgül ayırıcısından sonra diğer adlandırılmış özelliklerle örtük bir yol ekleyebilirsiniz, örneğin, `{Binding LastName, Mode=TwoWay}`.  
  
## <a name="binding-properties-that-can-be-set-with-the-binding-extension"></a>Bağlama uzantısıyla ayarlanabilir Özellikler bağlama  
 Bu konuda gösterilen sözdizimi, <xref:System.Windows.Data.Binding> biçimlendirme uzantısı/ifade sözdizimi aracılığıyla ayarlanabileceğinden <xref:System.Windows.Data.BindingBase> veya `Binding` birçok okuma/yazma özelliği olduğundan, genel `bindProp`=`value` yaklaşık olarak kullanır. Örtük bir <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>özel durumu ile herhangi bir sırada ayarlanabilir. (Bu durumda, herhangi bir sırada ayarlanabilir olan `Path=`açıkça belirtme seçeneğiniz vardır. Temel olarak, virgülle ayrılmış `bindProp`=`value` çiftleri kullanarak aşağıdaki listede bulunan özelliklerden sıfır veya daha fazlasını ayarlayabilirsiniz.  
  
 Bu özellik değerlerinin birkaçı XAML içindeki bir metin sözdiziminden yerel tür dönüştürmeyi desteklemeyen nesne türleri gerektirir ve bu nedenle bir öznitelik değeri olarak ayarlanmaları için biçimlendirme uzantıları gerektirir. Daha fazla bilgi için her bir özelliğin .NET Framework sınıf kitaplığındaki XAML öznitelik kullanımı bölümüne bakın; daha fazla biçimlendirme uzantısı kullanımı olan veya olmayan XAML öznitelik sözdizimi için kullandığınız dize, her `Binding` bir `bindProp`=`value` içinde tırnak işareti yerleştirmeyin. `Binding` ifadesi.  
  
- <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>: olası bir bağlama grubunu tanımlayan bir dize. Bu görece gelişmiş bir bağlama kavramıdır; <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>için başvuru sayfasına bakın.  
  
- <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A>: Boolean, `true` ya da `false`olabilir. Varsayılan, `false` değeridir.  
  
- <xref:System.Windows.Data.Binding.Converter%2A>: ifadede bir `bindProp`=`value` dize olarak ayarlanabilir, ancak bunu yapmak için değer için bir [StaticResource Işaretleme uzantısı](staticresource-markup-extension.md)gibi bir nesne başvurusu gerekir. Bu örnekteki değer bir özel dönüştürücü sınıfının örneğidir.  
  
- <xref:System.Windows.Data.Binding.ConverterCulture%2A>: ifadede standartlara dayalı bir tanımlayıcı olarak ayarlanabilir; <xref:System.Windows.Data.Binding.ConverterCulture%2A>için başvuru konusuna bakın.  
  
- <xref:System.Windows.Data.Binding.ConverterParameter%2A>: ifadede bir `bindProp`=`value` dize olarak ayarlanabilir, ancak bu, geçirilen parametrenin türüne bağlıdır. Değer için bir başvuru türü geçirilirse, bu kullanım iç içe bir [StaticResource biçimlendirme uzantısı](staticresource-markup-extension.md)gibi bir nesne başvurusu gerektirir.  
  
- <xref:System.Windows.Data.Binding.ElementName%2A>: birbirini dışlamalı <xref:System.Windows.Data.Binding.RelativeSource%2A> ve <xref:System.Windows.Data.Binding.Source%2A>; Bu bağlama özelliklerinin her biri belirli bir bağlama metodolojisini temsil eder. Bkz. [veri bağlamaya genel bakış](../data/data-binding-overview.md).  
  
- <xref:System.Windows.Data.BindingBase.FallbackValue%2A>: ifadede bir `bindProp`=`value` dize olarak ayarlanabilir, ancak bu, geçirilmekte olan değerin türüne bağlıdır. Bir başvuru türü geçirilirse, iç içe bir [StaticResource biçimlendirme uzantısı](staticresource-markup-extension.md)gibi bir nesne başvurusu gerekir.  
  
- <xref:System.Windows.Data.Binding.IsAsync%2A>: Boolean, `true` ya da `false`olabilir. Varsayılan, `false` değeridir.  
  
- <xref:System.Windows.Data.Binding.Mode%2A>: *değer* <xref:System.Windows.Data.BindingMode> Numaralandırmadaki sabit bir addır. Örneğin, `{Binding Mode=OneWay}`.  
  
- <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A>: Boolean, `true` ya da `false`olabilir. Varsayılan, `false` değeridir.  
  
- <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A>: Boolean, `true` ya da `false`olabilir. Varsayılan, `false` değeridir.  
  
- <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A>: Boolean, `true` ya da `false`olabilir. Varsayılan, `false` değeridir.  
  
- <xref:System.Windows.Data.Binding.Path%2A>: bir veri nesnesi veya genel nesne modeli için bir yolu tanımlayan bir dize. Biçim, bu konuda yeterince açıklanamaz bir nesne modelinde geçiş için birkaç farklı kural sağlar. Bkz. [PROPERTYPATH XAML sözdizimi](propertypath-xaml-syntax.md).  
  
- <xref:System.Windows.Data.Binding.RelativeSource%2A>: <xref:System.Windows.Data.Binding.ElementName%2A> ve <xref:System.Windows.Data.Binding.Source%2A>birlikte birbirini dışlamalı; Bu bağlama özelliklerinin her biri belirli bir bağlama metodolojisini temsil eder. Bkz. [veri bağlamaya genel bakış](../data/data-binding-overview.md). Değeri belirtmek için iç içe bir [RelativeSource MarkupExtension](relativesource-markupextension.md) kullanımı gerektirir.  
  
- <xref:System.Windows.Data.Binding.Source%2A>: birbirini dışlamalı <xref:System.Windows.Data.Binding.RelativeSource%2A> ve <xref:System.Windows.Data.Binding.ElementName%2A>; Bu bağlama özelliklerinin her biri belirli bir bağlama metodolojisini temsil eder. Bkz. [veri bağlamaya genel bakış](../data/data-binding-overview.md). Yalnızca bir anahtarlı kaynak sözlüğünden bir nesne veri kaynağına başvuran bir [StaticResource Işaretleme uzantısı](staticresource-markup-extension.md) olan iç içe geçmiş uzantı kullanımı gerektirir.  
  
- <xref:System.Windows.Data.BindingBase.StringFormat%2A>: bağlanan veriler için bir dize biçimi kuralını açıklayan bir dize. Bu görece gelişmiş bir bağlama kavramıdır; <xref:System.Windows.Data.BindingBase.StringFormat%2A>için başvuru sayfasına bakın.  
  
- <xref:System.Windows.Data.BindingBase.TargetNullValue%2A>: ifadede bir `bindProp`=`value` dize olarak ayarlanabilir, ancak bu, geçirilen parametrenin türüne bağlıdır. Değer için bir başvuru türü geçirilirse, iç içe bir [StaticResource biçimlendirme uzantısı](staticresource-markup-extension.md)gibi bir nesne başvurusu gerektirir.  
  
- <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>: *değer* <xref:System.Windows.Data.UpdateSourceTrigger> Numaralandırmadaki sabit bir addır. Örneğin, `{Binding UpdateSourceTrigger=LostFocus}`. Belirli denetimler, bu bağlama özelliği için muhtemelen farklı varsayılan değerlere sahip olabilir. Bkz. <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.  
  
- <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A>: Boolean, `true` ya da `false`olabilir. Varsayılan, `false` değeridir. Bkz. açıklamalar.  
  
- <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A>: Boolean, `true` ya da `false`olabilir. Varsayılan, `false` değeridir. Bkz. açıklamalar.  
  
- <xref:System.Windows.Data.Binding.XPath%2A>: bir XML veri kaynağının XMLDOM 'ına bir yol tanımlayan bir dize. Bkz. [XMLDataProvider ve XPath sorgularını kullanarak XML verilerine bağlama](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).  
  
 Aşağıda, `Binding` işaretleme uzantısı/`{Binding}` ifade formu kullanılarak ayarlanamaz <xref:System.Windows.Data.Binding> özellikleri verilmiştir.  
  
- <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>: Bu özellik, geri çağırma uygulamasına bir başvuru bekliyor. Olay işleyicileri dışındaki geri çağırmaları/yöntemlere XAML sözdiziminde başvurulamaz.  
  
- <xref:System.Windows.Data.Binding.ValidationRules%2A>: özellik, <xref:System.Windows.Controls.ValidationRule> nesnelerin genel bir koleksiyonunu alır. Bu, bir <xref:System.Windows.Data.Binding> nesne öğesinde bir özellik öğesi olarak ifade edilebilir, ancak bir `Binding` ifadesinde kullanım için uygun bir öznitelik ayrıştırma teknii yok. <xref:System.Windows.Data.Binding.ValidationRules%2A>için başvuru konusuna bakın.  
  
- <xref:System.Windows.Data.Binding.XmlNamespaceManager%2A>  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!IMPORTANT]
> Bağımlılık özelliği önceliği açısından, bir `Binding` ifadesi yerel olarak ayarlanan değere eşdeğerdir. Daha önce `Binding` ifadeye sahip olan bir özellik için yerel bir değer ayarlarsanız, `Binding` tamamen kaldırılır. Ayrıntılar için bkz. [bağımlılık özelliği değer önceliği](dependency-property-value-precedence.md).  
  
 Temel düzeyde veri bağlamayı açıklama bu konuda ele alınmıyor. Bkz. [veri bağlamaya genel bakış](../data/data-binding-overview.md).  
  
> [!NOTE]
> <xref:System.Windows.Data.MultiBinding> ve <xref:System.Windows.Data.PriorityBinding> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] uzantısı söz dizimini desteklemez. Bunun yerine özellik öğelerini kullanmanız gerekir. <xref:System.Windows.Data.MultiBinding> ve <xref:System.Windows.Data.PriorityBinding>için başvuru konularına bakın.  
  
 XAML için Boole değerleri büyük/küçük harfe duyarlıdır. Örneğin, `{Binding NotifyOnValidationError=true}` ya da `{Binding NotifyOnValidationError=True}`belirtebilirsiniz.  
  
 Veri doğrulamayı içeren bağlamalar genellikle `{Binding ...}` ifadesi yerine açık bir `Binding` öğesi tarafından belirtilir ve bir ifadede <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> veya <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> ayarı çok seyrek olur. Bunun nedeni, yardımcı özelliğin <xref:System.Windows.Data.Binding.ValidationRules%2A> ifade formunda kolayca ayarlanamamasıdır. Daha fazla bilgi için bkz. [bağlama doğrulamasını uygulama](../data/how-to-implement-binding-validation.md).  
  
 `Binding`, biçimlendirme uzantısıdır. Biçimlendirme uzantıları genellikle öznitelik değerlerinin sabit değerler veya işleyici adlarından farklı olması için bir gereksinim olduğunda uygulanır ve gereksinim, belirli tür veya özelliklere sahip tür dönüştürücülerden daha geneldir. XAML 'deki tüm biçimlendirme uzantıları, `{` ve `}` karakterlerini öznitelik sözdiziminde kullanır. Bu, XAML işlemcisinin bir biçimlendirme uzantısının dize içeriğini işlemesi gerektiğini tanıdığı bir kuraldır. Daha fazla bilgi için bkz. [Biçimlendirme uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
 `Binding`, WPF 'nin XAML uygulamasına yönelik uzantı işlevlerini uygulayan <xref:System.Windows.Data.Binding> sınıfının Ayrıca XAML ile ilgili olmayan çeşitli diğer yöntemleri ve özellikleri de uyguladığı bir tipik biçimlendirme uzantısıdır. Diğer üyelerin, XAML biçimlendirme uzantısı olarak çalışmaya ek olarak birçok veri bağlama senaryosunu ele alan daha çok yönlü ve kendi kendine içerilen bir sınıf <xref:System.Windows.Data.Binding> yapması amaçlanmıştır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Data.Binding>
- [Veri Bağlamaya Genel Bakış](../data/data-binding-overview.md)
- [XAML'ye Genel Bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [İşaretleme Uzantıları ve WPF XAML](markup-extensions-and-wpf-xaml.md)
