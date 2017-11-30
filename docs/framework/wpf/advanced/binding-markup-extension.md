---
title: "Biçimlendirme Uzantısı Bağlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Binding
helpviewer_keywords:
- Binding markup extensions [WPF]
- XAML [WPF], Binding markup extension
ms.assetid: 83d6e2a4-1b0c-4fc8-bd96-b5e98800ab63
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7d2bbca799e1eda1abae3d199dd71e004b17c4c9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="binding-markup-extension"></a>Biçimlendirme Uzantısı Bağlama
Bir ara ifade nesnesi oluşturma ve öğesi ve kendi bağlama çalışma zamanında uygulanır veri bağlamı yorumlama verilere bağlı değeri, özellik değeri erteler.  
  
## <a name="binding-expression-usage"></a>Bağlama ifadesinin kullanımı  
  
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
  
## <a name="syntax-notes"></a>Sözdizimi notları  
 Bu sözdizimleri de `[]` ve `*` değişmez değer değildir. Olduğunu belirten bir gösterim parçasıdır sıfır veya daha fazla *bindProp*`=`*değeri* çiftleri kullanılabilir, ile bir `,` onlar ve önceki arasında ayırıcı *bindProp*  `=` *değeri* çiftleri.  
  
 "Bağlama uzantısı ile Ayarlanabilen Bağlama Özellikleri" bölümünde listelenen özelliklerden herhangi birini yerine özniteliklerini kullanarak ayarlanabilir bir <xref:System.Windows.Data.Binding> object öğesi. Ancak, olmayan gerçekten biçimlendirme uzantısı'nın kullanımını <xref:System.Windows.Data.Binding>, yalnızca genel XAML işlenmesini CLR özellik kümesinin öznitelikleri olan <xref:System.Windows.Data.Binding> sınıfı. Diğer bir deyişle, `<Binding` *bindProp1*`="`*value1* `"[` *bindPropN*`="`*valueN* `"]*/>` öznitelikleri için eşdeğer bir sözdizimi <xref:System.Windows.Data.Binding> nesne öğesi kullanımı yerine bir `Binding` ifade kullanımı. Belirli özelliklerini XAML öznitelik kullanımı hakkında bilgi edinmek için <xref:System.Windows.Data.Binding>, ilgili özelliğinin "XAML öznitelik kullanımı" bölümüne bakın <xref:System.Windows.Data.Binding> .NET Framework Sınıf Kitaplığı'nda.  
  
## <a name="xaml-values"></a>XAML Değerleri  
  
|||  
|-|-|  
|`bindProp1, bindPropN`|Adını <xref:System.Windows.Data.Binding> veya <xref:System.Windows.Data.BindingBase> ayarlamak için özellik. Tüm <xref:System.Windows.Data.Binding> ayarlanabilir ile `Binding` uzantısı ve bazı özellikler içinde ayarlanabilir bir `Binding` yalnızca kullanarak daha fazla ifade biçimlendirme uzantıları iç içe geçmiş. "Bağlama uzantısı ile Ayarlanabilen Bağlama Özellikleri" bölümüne bakın.|  
|`value1, valueN`|Özellik ayarlanacak değer. Öznitelik değeri işleme için türünü ve belirli mantığı sonuçta belirli <xref:System.Windows.Data.Binding> ayarlanan özelliği.|  
|`path`|Örtük ayarlar yol dizesi <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> özelliği. Ayrıca bkz. [PropertyPath XAML sözdizimi](../../../../docs/framework/wpf/advanced/propertypath-xaml-syntax.md).|  
  
## <a name="unqualified-binding"></a>Nitelenmemiş {bağlama}  
 `{Binding}` "İfadesi kullanım bağlama" gösterilen kullanım oluşturur bir <xref:System.Windows.Data.Binding> nesnesi varsayılan değerlerle bir ilk içeren <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> , `null`. Birçok senaryoda yine yararlıdır çünkü oluşturulan <xref:System.Windows.Data.Binding> anahtar veri bağlama özellikleri gibi bağlı <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> ve <xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType> çalışma zamanı veri içeriğinde ayarlanan. Veri bağlamı kavramı hakkında daha fazla bilgi için bkz: [veri bağlama](../../../../docs/framework/wpf/data/data-binding-wpf.md).  
  
## <a name="implicit-path"></a>Örtük yolu  
 `Binding` Biçimlendirme uzantısı kullanır <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> kavramsal olarak "varsayılan özellik", burada `Path=` ifadesinin görünmesi gerekmez. Belirtirseniz bir `Binding` ifade örtülü yol ile örtülü yol ilk olarak görünmelidir diğer önce ifade `bindProp` = `value` çiftleri nereye <xref:System.Windows.Data.Binding> özelliği adıyla belirtilen. Örneğin: `{Binding PathString}`, burada `PathString` değeri olarak değerlendirilen bir dizedir <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> içinde <xref:System.Windows.Data.Binding> biçimlendirme uzantısı kullanımı tarafından oluşturuldu. Örneğin, virgül ayırıcısını sonra diğer adlandırılmış özelliklerle örtülü yol ekleyebilirsiniz `{Binding LastName, Mode=TwoWay}`.  
  
## <a name="binding-properties-that-can-be-set-with-the-binding-extension"></a>Bağlama uzantısı ile ayarlayabilirsiniz bağlama özellikleri  
 Bu konudaki sözdizimini genel kullanır `bindProp` = `value` yaklaşık, birçok okuma/yazma özellikleri olduğundan <xref:System.Windows.Data.BindingBase> veya <xref:System.Windows.Data.Binding> aracılığıyla ayarlanabilir `Binding` biçimlendirme uzantısı / deyim sözdizimi. Örtülü dışında herhangi bir sırada ayarlanabilir <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>. (Açıkça belirtmek için seçeneğiniz `Path=`, bu durumda herhangi bir sırada ayarlanabilir). Temel olarak, sıfır veya daha fazla özellik listesinde aşağıdaki kullanarak ayarlayabileceğiniz `bindProp` = `value` çifti virgülle ayrılmış.  
  
 Bu özellik değerlerini çeşitli değil yerel tür dönüştürme metin sözdiziminden XAML'de destekler ve bu nedenle öznitelik değeri olarak ayarlanması için işaretleme uzantıları gerekiyor nesne türlerini gerektirir. Daha fazla bilgi için her bir özellik için .NET Framework sınıf kitaplığı XAML Öznitelik Kullanımı bölümünde; denetleyin. XAML öznitelik sözdizimi ile kullandığınız dize ya da daha fazla biçimlendirme uzantısı kullanımı temel olarak belirttiğiniz değerle aynı bir `Binding` tırnak içine her yerleştirmeyin özel ifade `bindProp` = `value` içinde `Binding` ifade.  
  
-   <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>: olası bağlama grubunu tanımlayan bir dize. Bu bir göreceli olarak Gelişmiş bağlama kavramıdır; başvuru sayfası için bkz: <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>.  
  
-   <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A>: Ya da Boolean, olabilir `true` veya `false`. Varsayılan, `false` değeridir.  
  
-   <xref:System.Windows.Data.Binding.Converter%2A>: olarak ayarlanmış bir `bindProp` = `value` dize ifadesi, ancak bunu yapmak için bir nesne başvurusu gibi değeri, gerektirir bir [StaticResource biçimlendirme uzantısı](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md). Bu durumda özel dönüştürücü sınıfının bir örneği değerdir.  
  
-   <xref:System.Windows.Data.Binding.ConverterCulture%2A>: standartlara dayalı bir tanımlayıcı; olarak ifadede ayarlanabilir başvuru konusuna bakın <xref:System.Windows.Data.Binding.ConverterCulture%2A>.  
  
-   <xref:System.Windows.Data.Binding.ConverterParameter%2A>: olarak ayarlanmış bir `bindProp` = `value` dize ifadesi, ancak bu geçirilen parametre türüne bağlıdır. Değer için bir başvuru türü geçirilirse, bu kullanım gibi bir iç içe nesne başvurusu gerektiren [StaticResource biçimlendirme uzantısı](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md).  
  
-   <xref:System.Windows.Data.Binding.ElementName%2A>: karşılaştırması <xref:System.Windows.Data.Binding.RelativeSource%2A> ve <xref:System.Windows.Data.Binding.Source%2A>; her bunlardan bağlama özellikleri belirli bağlama metodolojisini temsil eder. Bkz: [veri genel bakış bağlama](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
-   <xref:System.Windows.Data.BindingBase.FallbackValue%2A>: olarak ayarlanmış bir `bindProp` = `value` dize ifadesi, ancak bu geçirilen değerin türüne bağlıdır. Bir başvuru türü geçirme gerektiriyorsa, bir nesne başvurusu bir iç içe gibi [StaticResource biçimlendirme uzantısı](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md).  
  
-   <xref:System.Windows.Data.Binding.IsAsync%2A>: Ya da Boolean, olabilir `true` veya `false`. Varsayılan, `false` değeridir.  
  
-   <xref:System.Windows.Data.Binding.Mode%2A>: *değeri* bir sabit adıdır <xref:System.Windows.Data.BindingMode> numaralandırması. Örneğin, `{Binding Mode=OneWay}`.  
  
-   <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A>: Ya da Boolean, olabilir `true` veya `false`. Varsayılan, `false` değeridir.  
  
-   <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A>: Ya da Boolean, olabilir `true` veya `false`. Varsayılan, `false` değeridir.  
  
-   <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A>: Ya da Boolean, olabilir `true` veya `false`. Varsayılan, `false` değeridir.  
  
-   <xref:System.Windows.Data.Binding.Path%2A>: bir veri nesnesi veya bir genel nesne modeline yolu açıklayan bir dize. Biçim yeterli bu konuda açıklanan olamaz bir nesne modeline geçmek için birkaç farklı kuralları sağlar. Bkz: [PropertyPath XAML sözdizimi](../../../../docs/framework/wpf/advanced/propertypath-xaml-syntax.md).  
  
-   <xref:System.Windows.Data.Binding.RelativeSource%2A>: ile karşılaştırması birbirini dışlayan <xref:System.Windows.Data.Binding.ElementName%2A> ve <xref:System.Windows.Data.Binding.Source%2A>; her bunlardan bağlama özellikleri belirli bağlama metodolojisini temsil eder. Bkz: [veri genel bakış bağlama](../../../../docs/framework/wpf/data/data-binding-overview.md). İç içe bir gerektirir [RelativeSource MarkupExtension](../../../../docs/framework/wpf/advanced/relativesource-markupextension.md) kullanım değeri belirtin.  
  
-   <xref:System.Windows.Data.Binding.Source%2A>: karşılaştırması <xref:System.Windows.Data.Binding.RelativeSource%2A> ve <xref:System.Windows.Data.Binding.ElementName%2A>; her bunlardan bağlama özellikleri belirli bağlama metodolojisini temsil eder. Bkz: [veri genel bakış bağlama](../../../../docs/framework/wpf/data/data-binding-overview.md). Bir iç içe geçmiş uzantısı kullanımı genellikle gerektiren bir [StaticResource biçimlendirme uzantısı](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) anahtarlı kaynak sözlükten bir nesneyi veri kaynağına başvuruyor.  
  
-   <xref:System.Windows.Data.BindingBase.StringFormat%2A>: bağlı veriler için dize biçimi kuralını tanımlayan bir dize. Bu bir göreceli olarak Gelişmiş bağlama kavramıdır; başvuru sayfası için bkz: <xref:System.Windows.Data.BindingBase.StringFormat%2A>.  
  
-   <xref:System.Windows.Data.BindingBase.TargetNullValue%2A>: olarak ayarlanmış bir `bindProp` = `value` dize ifadesi, ancak bu geçirilen parametre türüne bağlıdır. Bir başvuru türü değerin geçirme gerektiriyorsa, bir nesne başvurusu bir iç içe gibi [StaticResource biçimlendirme uzantısı](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md).  
  
-   <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>: *değeri* bir sabit adıdır <xref:System.Windows.Data.UpdateSourceTrigger> numaralandırması. Örneğin, `{Binding UpdateSourceTrigger=LostFocus}`. Özel denetimler, büyük olasılıkla bu bağlama özelliği için farklı varsayılan değerler atanmıştır. Bkz: <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.  
  
-   <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A>: Ya da Boolean, olabilir `true` veya `false`. Varsayılan, `false` değeridir. Açıklamalar bakın.  
  
-   <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A>: Ya da Boolean, olabilir `true` veya `false`. Varsayılan, `false` değeridir. Açıklamalar bakın.  
  
-   <xref:System.Windows.Data.Binding.XPath%2A>: XML veri kaynağının XMLDOM'a yolu açıklayan bir dize. Bkz: [bir XMLDataProvider ve XPath sorgularını kullanarak XML verilere bağlama](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).  
  
 Aşağıdaki özellikleridir <xref:System.Windows.Data.Binding> , ayarlanamaz kullanarak `Binding` biçimlendirme uzantısı /`{Binding}` ifade formu.  
  
-   <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>: Bu özellik bir geri çağırma uygulaması bir başvuruyu bekler. Olay işleyicileri dışındaki geri çağırmalar/yöntemler XAML sözdiziminde başvurulamaz.  
  
-   <xref:System.Windows.Data.Binding.ValidationRules%2A>: özelliği genel topluluğunu alır <xref:System.Windows.Controls.ValidationRule> nesneleri. Bu özellik öğesi olarak ifade edilebilir bir <xref:System.Windows.Data.Binding> nesne öğesinde, ancak hiçbir hazır öznitelik ayrıştırma tekniği kullanım için sahip bir `Binding` ifade. Başvuru konusuna bakın <xref:System.Windows.Data.Binding.ValidationRules%2A>.  
  
-   <xref:System.Windows.Data.Binding.XmlNamespaceManager%2A>  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!IMPORTANT]
>  Bağımlılık özelliği önceliği açısından bir `Binding` ifadesidir yerel olarak ayarlanmış eşdeğer değeri. Daha önce sahip bir özellik için yerel bir değer ayarlarsanız bir `Binding` ifadesi `Binding` tamamen kaldırılır. Ayrıntılar için bkz [bağımlılık özelliği değeri önceliği](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md).  
  
 Veri bağlama temel düzeyde açıklayan bu konuda ele alınmamıştır. Bkz: [veri genel bakış bağlama](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
> [!NOTE]
>  <xref:System.Windows.Data.MultiBinding>ve <xref:System.Windows.Data.PriorityBinding> desteklemeyen bir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] uzantısı sözdizimi. Bunun yerine özellik öğelerini kullanırsınız. Başvuru konuları için bkz: <xref:System.Windows.Data.MultiBinding> ve <xref:System.Windows.Data.PriorityBinding>.  
  
 XAML için Boole değerleri büyük küçük harfe duyarlı. Örneğin şunları belirtebilirsiniz `{Binding NotifyOnValidationError=true}` veya `{Binding NotifyOnValidationError=True}`.  
  
 Veri doğrulama içeren bağlar genellikle açık bir tarafından belirtilir `Binding` öğesi yerine bir `{Binding ...}` ifadesi ve ayar <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> veya <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> bir ifadede seyrek değil. Bunun nedeni, eşlik özelliği <xref:System.Windows.Data.Binding.ValidationRules%2A> taşımalarına ifade formunda olacak şekilde ayarlanamaz. Daha fazla bilgi için bkz: [uygulama bağlama doğrulama](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md).  
  
 `Binding`bir biçimlendirme uzantısıdır. Biçimlendirme uzantıları genellikle değişmez değerler veya işleyici dışında adları öznitelik değerleri kaçınmak için bir gereksinimi yoktur ve belirli türler veya özellikler öznitelikli tür dönüştürücüleri daha genel bir gereksinimdir uygulanır. XAML Kullanımdaki tüm biçimlendirme uzantıları `{` ve `}` olarak XAML işlemci tanıdığı biçimlendirme uzantısı dize içeriklerini işlemelidir kuralı kendi öznitelik sözdiziminde karakterler. Daha fazla bilgi için bkz: [biçimlendirme uzantıları ve WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
 `Binding`uygulamasındaki alışılmadık biçimlendirme uzantısı <xref:System.Windows.Data.Binding> WPF'ın XAML uygulama uzantısı işlevselliğini uygulayan sınıf de diğer çeşitli yöntemleri ve XAML ile ilgili olmayan özellikler uygular. Diğer üyeler sağlamak üzere tasarlanmıştır <xref:System.Windows.Data.Binding> XAML biçimlendirme uzantısı olarak işlev ek olarak, birçok veri bağlama senaryosu olan çok yönlü ve kendi başına bir sınıf.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Data.Binding>  
 [Veri bağlama genel bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [XAML genel bakış (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Biçimlendirme uzantıları ve WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
