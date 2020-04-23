---
title: Tür Dönüştürücülerinde ve İşaretleme Uzantılarında Kullanılabilir Hizmet Bağlamları
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], type converter services how-to
ms.assetid: b4dad00f-03da-4579-a4e9-d8d72d2ccbce
ms.openlocfilehash: 59c4385eb4df8c622be6164cdb0a1a911c445ca8
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071663"
---
# <a name="service-contexts-available-to-type-converters-and-markup-extensions"></a>Tür Dönüştürücülerinde ve İşaretleme Uzantılarında Kullanılabilir Hizmet Bağlamları
Tür dönüştürücü ve biçimlendirme uzantısı kullanımlarını destekleyen türlerin yazarlarıgenellikle biçimlendirmede veya çevreleyen nesne grafiği yapısında bir kullanımın nerede bulunduğu hakkında bağlamsal bilgilere sahip olmalıdır. Sağlanan nesnenin doğru bir şekilde anlık olarak anlık olarak veya nesne grafiğindeki varolan nesnelere nesne başvuruları yapılabilecek şekilde bilgi gerekebilir. .NET XAML Hizmetleri kullanırken, gerekli olabilecek bağlam bir dizi hizmet arabirimi olarak ortaya çıkarır. Tür dönüştürücü veya biçimlendirme uzantısı destek kodu, kullanılabilir ve kullanılabilir ve ilgili <xref:System.Xaml.XamlObjectWriter> türler veya ilgili türler aracılığıyla geçirilen bir hizmet sağlayıcı bağlamı kullanarak bir hizmet için sorgulayabilirsiniz. XAML şeması bağlamı doğrudan böyle bir hizmet aracılığıyla kullanılabilir. Bu konu, bir değer dönüştürücü uygulamasından hizmet bağlamlarına nasıl erişilenleri açıklar ve genellikle kullanılabilir hizmetleri ve bunların rollerini listeler.

## <a name="obtaining-services"></a>Hizmet Alma

Bir değer dönüştürücüsünün uygulayıcısı olarak, genellikle değer dönüştürücünün uygulandığı bir tür içeriğe erişmeniz gerekir. Bu bağlam, etkin XAML şeması bağlamı, XAML şema bağlamı ve XAML nesne yazarının sağladığı tür eşleme sistemine erişim ve benzeri bilgileri içerebilir. Biçimlendirme uzantısı veya tür dönüştürücü uygulaması için kullanılabilen hizmetler, her sanal yöntemin imzasının bir parçası olan bağlam parametreleri aracılığıyla iletilir. Her durumda, bağlamında <xref:System.IServiceProvider> uyguladınız ve bir hizmet <xref:System.IServiceProvider.GetService%2A?displayProperty=nameWithType> istemek için arayabilirsiniz.

## <a name="services-for-a-markup-extension"></a>Biçimlendirme Uzantısı Için Hizmetler

<xref:System.Windows.Markup.MarkupExtension>yalnızca bir sanal <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>yöntemi vardır. Giriş `serviceProvider` parametresi, biçimlendirme uzantısı xaml işlemci tarafından çağrıldığında hizmetlerin uygulamalara nasıl iletildiğidir. Aşağıdaki pseudocode, biçimlendirme uzantısı uygulamasının aşağıdaki <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>hizmetler için nasıl sorgulayabildiğini göstermektedir:

```csharp
public override object ProvideValue(IServiceProvider serviceProvider)
{
...
    // Get the IXamlTypeResolver from the service provider
    if (serviceProvider == null)
    {
        throw new ArgumentNullException("serviceProvider");
    }
    IXamlTypeResolver xamlTypeResolver = serviceProvider.GetService(typeof(IXamlTypeResolver)) as IXamlTypeResolver;
    if (xamlTypeResolver == null)
   {
        throw new ArgumentException("IXamlTypeResolver"));
    }
...
}
```

## <a name="services-for-a-type-converter"></a>Tip Dönüştürücü için Hizmetler

<xref:System.ComponentModel.TypeConverter>bir hizmet bağlamı kullanan ve XAML kullanımlarını destekleyen dört sanal yöntem vardır. Bu yöntemlerin her biri `context` bir giriş parametresi geçer. Bu parametre türü, <xref:System.ComponentModel.ITypeDescriptorContext>ancak bu <xref:System.IServiceProvider>arabirim devralır , <xref:System.IServiceProvider.GetService%2A> ve bu nedenle, dönüştürücü uygulamaları yazmak için kullanılabilir bir yöntem vardır.

Aşağıdaki pseudocode, XAML kullanımları için bir tür dönüştürücü uygulamasının, bu durumda, <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>geçersiz kılardan birinde hizmetleri nasıl sorgulayabildiğini göstermektedir:

```csharp
public override object ConvertFrom(ITypeDescriptorContext typeDescriptorContext,
  CultureInfo cultureInfo,
  object source)
{
    IRootObjectProvider rootProvider = typeDescriptorContext.GetService(typeof(IRootObjectProvider)) as IRootObjectProvider;
    if (rootProvider != null && source is String)
    {
        //return something, else ...
    }
    throw GetConvertFromException(source);
}
```

## <a name="services-for-a-value-serializer"></a>Değer Serializer için Hizmetler

Değer serileştirici bağlamı için, <xref:System.Windows.Markup.ValueSerializer> sınıfa özgü bir hizmet <xref:System.Windows.Markup.IValueSerializerContext>sağlayıcı türü kullanırsınız. Bu bağlam, dört <xref:System.Windows.Markup.ValueSerializer> sanal yöntemin geçersiz kılmalarına aktarılır. Hizmet <xref:System.IServiceProvider.GetService%2A> almak için bağlamdan arayın.

## <a name="using-the-xaml-service-provider-contexts"></a>XAML Servis Sağlayıcı Bağlamlarını Kullanma

Uzantıları veya <xref:System.IServiceProvider.GetService%2A> tür dönüştürücüleri işaretlemek için kullanılabilen XAML hizmetlerine erişim için hizmet sağlayıcısı, yalnızca arabirim üzerinden ve ilgili içeriğe nasıl aktarılan bir iç sınıf olarak uygulanır. Yük yolunun varsayılan .NET XAML Hizmetleri uygulamalarında bir XAML işleme işlemi, bir hizmet bağlamı gerektiren ilgili biçimlendirme uzantısı veya tür dönüştürücü yöntemlerini çağırdığında, bu iç nesne geçirilir. Duruma bağlı olarak, sistem hizmeti bağlamı sağlar `MarkupExtensionContext` ya da `TextSyntaxContext`, ancak bu sınıfların her ikisinin özellikleri iç. Bu sınıflarla etkileşiminiz, onlardan hizmet istemekle <xref:System.IServiceProvider.GetService%2A>sınırlıdır.

## <a name="available-services-from-the-net-xaml-service-context"></a>.NET XAML Hizmet Bağlamından Mevcut Hizmetler

.NET XAML Hizmetleri, biçimlendirme uzantıları, tür dönüştürücüler, değer serileştiricileri ve potansiyel olarak diğer kullanımlar için hizmetleri tanımlar. Aşağıdaki bölümler, bu hizmetlerin her birini açıklar ve hizmetin bir uygulamada nasıl kullanılabileceği hakkında rehberlik sağlar.

### <a name="iserviceprovider"></a>ıserviceprovider

**Referans belgeleri**:<xref:System.IServiceProvider>

**İlgili:** .NET'te hizmet tabanlı bir altyapının temel <xref:System.IServiceProvider.GetService%2A?displayProperty=nameWithType>çalışması, böylece .

### <a name="itypedescriptorcontext"></a>ıtypedescriptorcontext

**Referans belgeleri**:<xref:System.ComponentModel.ITypeDescriptorContext>

<xref:System.IServiceProvider>Türetilmiştir. Bu sınıf, standart <xref:System.ComponentModel.TypeConverter> imzalarda bağlamı temsil eder; <xref:System.ComponentModel.TypeConverter> .NET Framework 1.0'dan beri var olan bir sınıftır. Dize değeri türü dönüştürme için <xref:System.ComponentModel.TypeConverter> XAML ve XAML senaryosundan önce uzanır. .NET XAML Hizmetleri bağlamında, <xref:System.ComponentModel.TypeConverter> yöntemleri açıkça uygulanır. Açık uygulamanın davranışı, arayanlara API'nin <xref:System.ComponentModel.ITypeDescriptorContext> XAML türü sistemleri yle veya XAML'den nesneleri okumak veya yazmak için uygun olmadığını gösterir. <xref:System.ComponentModel.ITypeDescriptorContext.Container%2A>, <xref:System.ComponentModel.ITypeDescriptorContext.Instance%2A>ve <xref:System.ComponentModel.ITypeDescriptorContext.PropertyDescriptor%2A> genellikle `null` .NET XAML Hizmetleri bağlamlarından döner.

### <a name="ivalueserializercontext"></a>ıvalueserializercontext

**Referans belgeleri**:<xref:System.Windows.Markup.IValueSerializerContext>

XAML <xref:System.ComponentModel.ITypeDescriptorContext> türü sistemi hakkında yanlış etkileri bastırmak için açık uygulamalardan türetilmiştir ve ayrıca dayanır. Statik arama yardımcı yöntemlerini <xref:System.Windows.Markup.ValueSerializer>destekler.

### <a name="ixamltyperesolver"></a>ıxamltyperesolver

**Referans belgeleri**:<xref:System.Windows.Markup.IXamlTypeResolver>

**Tanım:** <xref:System.Windows.Markup> namespace, System.Xaml assembly  

**İlgili:** Yol senaryolarını yükleme ve XAML şeması bağlamıyla etkileşim

**Hizmet API'si:**  <xref:System.Windows.Markup.IXamlTypeResolver.Resolve%2A>

XAML yazarı bir nesne grafiğinde bir CLR nesnesi yaptığında gerekli olan XAML-CLR türü eşlemi etkileyebilir. <xref:System.Windows.Markup.IXamlTypeResolver.Resolve%2A>bir XAML türü ada karşılık gelen potansiyel olarak önek nitelikli dize işler ( ),<xref:System.Xaml.XamlType.Name%2A?displayProperty=nameWithType>ve bir CLR <xref:System.Type>döndürür. Türleri çözme genellikle büyük ölçüde XAML şema bağlamına bağlıdır. Yalnızca XAML şeması bağlamı, hangi derlemelerin yüklendiği ve bu derlemelerden hangisine tür çözümlemesi için erişilebildiği veya erişilmesi gerektiği gibi hususların farkındadır.

### <a name="iuricontext"></a>ıuricontext

**Referans belgeleri**:<xref:System.Windows.Markup.IUriContext>

**Tanım:** <xref:System.Windows.Markup> namespace, System.Xaml assembly  

**İlgili:** Yolu yükleyin ve URI veya `x:Uri` değer olan üye değerlerin yol işleme kaydedin.

**Hizmet API'si:**  <xref:System.Windows.Markup.IUriContext.BaseUri%2A>

Bu hizmet, varsa, genel olarak kullanılabilir bir URI kökünü bildirir. URI kökü, göreli URI'leri mutlak URI'lere veya tam tersi olarak çözmek için kullanılabilir. Bu senaryo esas olarak belirli bir çerçeve tarafından maruz kalan uygulama hizmetleri veya bir çerçevede sık kullanılan kök öğe sınıfının yetenekleri yle ilgilidir. Temel URI, xaml nesne swriter geçirilir ve bu hizmet tarafından bildirilen bir XAML okuyucu ayarı olarak kurulabilir.

### <a name="iambientprovider"></a>ıambientprovider

**Referans belgeleri**:<xref:System.Xaml.IAmbientProvider>

**Tanım:** <xref:System.Xaml> namespace, System.Xaml assembly  

**İlgili:** Yol işleme ve tip arama ertelemeleri veya optimizasyonlar yükleyin.

**Hizmet API'leri:**  <xref:System.Xaml.IAmbientProvider.GetAllAmbientValues%2A>, üç diğer.

XAML'deki ortam kavramı, bir türün belirli bir üyesini ortam olarak işaretlemek için yapılan bir tekniktir. Alternatif olarak, bir tür ortam olabilir, böylece türün bir örneğini tutan tüm özellik değerleri ortam özellikleri olarak kabul edilmelidir. XAML düğüm akışı boyunca daha fazla olan ve nesne grafiğindeki soyundan gelen biçimlendirme uzantıları veya tür dönüştürücüleri, yükleme zamanında ortam özelliğine veya yazı örneğine erişebilir; ya da zaman tasarrufu ortam yapısı bilgi kullanabilirsiniz. Bu, diğer hizmetler için veya için <xref:System.Windows.Markup.IXamlTypeResolver> `x:Type`türleri çözmek için gereken yeterlilik derecesini etkileyebilir. Ayrıca <xref:System.Xaml.AmbientPropertyValue>bakınız.

### <a name="ixamlschemacontextprovider"></a>ıxamlschemacontextprovider

**Referans belgeleri**:<xref:System.Xaml.IXamlSchemaContextProvider>

**Tanım:** <xref:System.Xaml> namespace, System.Xaml assembly  

**İlgili:** Yükleme yolu ve bir XAML türünü destek türüne çözmesi gereken herhangi bir işlem.

**Hizmet API'si:**  <xref:System.Xaml.IXamlSchemaContextProvider.SchemaContext%2A>

XAML şeması bağlamı herhangi bir erteleme yük işlemleri için gereklidir, çünkü aynı şema bağlamı ertelenmiş içeriği tümleştirmek için ertelenmiş alanda hareket etmelidir. XAML şema bağlamının rolü hakkında daha fazla bilgi için Bkz. [XAML Hizmetleri.](../../../api/index.md)

### <a name="irootobjectprovider"></a>ırootobjectprovider

**Referans belgeleri**:<xref:System.Xaml.IRootObjectProvider>

**Tanım:** <xref:System.Xaml> namespace, System.Xaml assembly  

**İlgili:** Yük yolu.

**Hizmet API'si:**  <xref:System.Xaml.IRootObjectProvider.RootObject%2A>

Hizmet, belirli bir çerçeve tarafından veya bir çerçevede sık kullanılan kök öğe sınıfının yetenekleri tarafından ortaya çıkarılan uygulama hizmetleriyle ilgilidir. Kök nesneyi elde etmek için bir senaryo kod arkasında ve olay kablolama bağlamaktır. Örneğin, WPF uygulaması, `x:Class` XAML biçimlendirmesinde başka bir konumda bulunan herhangi bir olay işleyiciözünün biçimlendirme derlemesi ve kablolama için kullanılır. Biçimlendirme derlemesi için biçimlendirme ve kod arkası tanımlı kısmi sınıfların bağlantı noktası kök öğededir.

### <a name="ixamlnamespaceresolver"></a>ıxamlnamespaceresolver

**Referans belgeleri**:<xref:System.Xaml.IXamlNamespaceResolver>

**Tanım:** <xref:System.Xaml> namespace, System.Xaml assembly  

**İlgili:** Yolu yükleyin, yolu kaydedin.

**Servis API:** <xref:System.Xaml.IXamlNamespaceResolver.GetNamespace%2A> yük <xref:System.Xaml.IXamlNamespaceResolver.GetNamespacePrefixes%2A> yolu için, kaydet yolu için.

<xref:System.Xaml.IXamlNamespaceResolver>bir XAML ad alanı tanımlayıcısı / URI kökenli XAML işaretleme eşlenen olarak öneki dayalı döndürebilir bir hizmettir.

### <a name="iprovidevaluetarget"></a>ıprovidevaluetarget

**Referans belgeleri**:<xref:System.Windows.Markup.IProvideValueTarget>

**Tanım:** <xref:System.Windows.Markup> namespace, System.Xaml assembly  

**İlgili:** Yolu yükleyin ve yolu kaydedin.

**Servis API'leri:**<xref:System.Windows.Markup.IProvideValueTarget.TargetObject%2A>, <xref:System.Windows.Markup.IProvideValueTarget.TargetProperty%2A>.  

<xref:System.Windows.Markup.IProvideValueTarget>yük zamanında nerede hareket ettiği neresinde olduğu hakkında bağlam elde etmek için bir tür dönüştürücü veya biçimlendirme uzantısı sağlar. Uygulamalar, kullanımı geçersiz ksaymak için bu bağlamı kullanabilir. Örneğin, WPF gibi bazı biçimlendirme uzantıları içinde <xref:System.Windows.DynamicResourceExtension>mantık vardır. Mantık, uzantının yalnızca bağımlılık özelliklerini (veya diğer bağımlılık dışı özelliklerin kısa bir listesini) ayarlamak için kullanıldığından emin olmak için denetimi <xref:System.Windows.Markup.IProvideValueTarget.TargetProperty%2A> denetler.

### <a name="ixamlnameresolver"></a>ıxamlnameresolver

**Referans belgeleri**:<xref:System.Xaml.IXamlNameResolver>

**Tanım:** <xref:System.Xaml> namespace, System.Xaml assembly  

**İlgili:** Yol nesnesi grafik tanımını yükleyin, "veya `x:Name` `x:Reference`çerçeveye özgü tekniklerle" tanımlanan nesneleri çözümle.

**Hizmet API'leri:**  <xref:System.Xaml.IXamlNameResolver.Resolve%2A>; ileri referanslarla başa çıkma gibi daha gelişmiş senaryolar için diğer API'ler.

.NET XAML Hizmetleri'nin `x:Reference` işleme uygulaması bu hizmete dayanır. Çerçeveyi destekleyen belirli çerçeveler veya araçlar, bu<xref:System.Windows.Markup.RuntimeNamePropertyAttribute> hizmeti işleme veya eşdeğer (atfedilen) mülk işleme için `x:Name` kullanır.

### <a name="idestinationtypeprovider"></a>IDestinationTypeProvider

**Referans belgeleri**:<xref:System.Xaml.IDestinationTypeProvider>

**Tanım:** <xref:System.Xaml> namespace, System.Xaml assembly  

**İlgili:** Dolaylı CLR türü bilgilerin yük yolu çözünürlüğü.

**Hizmet API'si:**<xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A>

Daha fazla bilgi için bkz. <xref:System.Xaml.IDestinationTypeProvider>.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Markup.MarkupExtension>
- <xref:System.Xaml.XamlObjectWriter>
- [XAML Biçimlendirme Uzantılarına Genel Bakış](markup-extensions-overview.md)
- [XAML Tür Dönüştürücülerine Genel Bakış](type-converters-overview.md)
