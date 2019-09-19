---
title: Tür Dönüştürücülerinde ve İşaretleme Uzantılarında Kullanılabilir Hizmet Bağlamları
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], type converter services how-to
ms.assetid: b4dad00f-03da-4579-a4e9-d8d72d2ccbce
ms.openlocfilehash: 0d4e274ad7b64820e74347908c08c7726e96bbe8
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053839"
---
# <a name="service-contexts-available-to-type-converters-and-markup-extensions"></a>Tür Dönüştürücülerinde ve İşaretleme Uzantılarında Kullanılabilir Hizmet Bağlamları
Tür dönüştürücüsü ve biçimlendirme uzantısı kullanımlarını destekleyen türlerin yazarları, genellikle bir kullanımın İşaretlemede bulunduğu konum veya çevreleyen nesne grafik yapısında yer alan bağlama bilgilerine sahip olmalıdır. Belirtilen nesnenin doğru şekilde örneklendiği veya nesne grafiğindeki var olan nesnelere başvuruları yapılabilmesi için bilgi gerekebilir. .NET Framework XAML Hizmetleri kullanılırken, gerekli olabilecek bağlam bir dizi hizmet arabirimi olarak sunulur. Tür dönüştürücüsü veya biçimlendirme uzantısı destek kodu, bir hizmet sağlayıcı bağlamını kullanarak bir hizmeti sorgulayabilir ve içinden <xref:System.Xaml.XamlObjectWriter> veya ilgili türlerden üzerinden geçirilir. XAML şeması bağlamı, bu tür bir hizmet aracılığıyla doğrudan kullanılabilir. Bu konu, bir değer Dönüştürücüsü uygulamasından hizmet bağlamlarının nasıl erişebileceğini ve genellikle kullanılabilir hizmetleri ve rollerinin listesini listeler.  
  
<a name="obtaining_services"></a>   
## <a name="obtaining-services"></a>Hizmetleri edinme  
 Değer dönüştürücünün bir uygulayıcısı olarak, genellikle değer dönüştürücünün uygulandığı bazı bağlam türlerine erişmeniz gerekir. Bu bağlam, etkin XAML şema bağlamı, XAML şema bağlamı ve XAML nesne yazıcısının sağladığı tür eşleme sistemine erişim gibi bilgileri içerebilir. Biçimlendirme uzantısı veya tür dönüştürücüsü uygulamasıyla kullanılabilen hizmetler, her sanal yöntemin imzasının bir parçası olan bağlam parametreleriyle iletilir. Her durumda, bağlamını uyguladık <xref:System.IServiceProvider> ve bir hizmet istemek için çağrı <xref:System.IServiceProvider.GetService%2A?displayProperty=nameWithType> yapabilirsiniz.  
  
<a name="services_for_a_markup_extension"></a>   
## <a name="services-for-a-markup-extension"></a>Biçimlendirme uzantısı için hizmetler  
 <xref:System.Windows.Markup.MarkupExtension>yalnızca bir sanal yöntemi <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>vardır. Giriş `serviceProvider` parametresi, biçimlendirme uzantısı bir XAML işlemcisi tarafından çağrıldığında hizmetlerin uygulamalara nasıl iletildiğini öğrenin. Aşağıdaki sözde kod, bir işaretleme uzantısı uygulamasının kendi <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>Hizmetleri için nasıl sorgu olabileceğini göstermektedir:  
  
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
  
<a name="services_for_a_type_converter"></a>   
## <a name="services-for-a-type-converter"></a>Tür Dönüştürücüsü için hizmetler  
 <xref:System.ComponentModel.TypeConverter>, bir hizmet bağlamı kullanan ve XAML kullanımlarını destekleyen dört sanal yönteme sahiptir. Bu yöntemlerin her biri bir giriş `context` parametresi geçirir. Bu parametre türündedir <xref:System.ComponentModel.ITypeDescriptorContext>, ancak bu arabirim devralır <xref:System.IServiceProvider>ve bu nedenle, dönüştürücü uygulamaları yazmak için kullanabileceğiniz <xref:System.IServiceProvider.GetService%2A> bir yöntem vardır.  
  
 Aşağıdaki sözde kod, XAML kullanımları için bir tür dönüştürücü uygulamasının, geçersiz kılmalardan birindeki hizmetleri nasıl sorgulayabileceğini gösterir, bu durumda <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>:  
  
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
  
<a name="services_for_a_value_serializer"></a>   
## <a name="services-for-a-value-serializer"></a>Bir değer seri hale getirici için hizmetler  
 Değer seri hale getirici bağlamı için, <xref:System.Windows.Markup.ValueSerializer> <xref:System.Windows.Markup.IValueSerializerContext>sınıfına özgü bir hizmet sağlayıcı türü kullanırsınız. Bu bağlam dört <xref:System.Windows.Markup.ValueSerializer> sanal yöntemin geçersiz kılmalarına geçirilir. Hizmetleri <xref:System.IServiceProvider.GetService%2A> almak için bağlamdan çağırın.  
  
<a name="using_the_xaml_service_provider_contexts"></a>   
## <a name="using-the-xaml-service-provider-contexts"></a>XAML hizmeti sağlayıcısı bağlamlarını kullanma  
 Biçimlendirme uzantıları veya tür <xref:System.IServiceProvider.GetService%2A> dönüştürücülerinin kullanabildiği xaml hizmetlerine erişim için hizmet sağlayıcısı, yalnızca arabirim üzerinden pozlama ve ilgili bağlama nasıl geçirildiği bir iç sınıf olarak uygulanır. Her bir XAML işleme işlemi, yük yolu veya kayıt yolu .NET Framework XAML Hizmetleri uygulamalarında ilgili biçimlendirme uzantısını veya bir hizmet bağlamı gerektiren tür dönüştürücüsü yöntemlerini çağırdığında, bu iç nesne geçirilir. Durumunuza bağlı olarak, sistem hizmeti bağlamı ya da `MarkupExtensionContext` `TextSyntaxContext`sağlar, ancak bu sınıfların her ikisinin de özellikleri iç. Bu sınıflarla etkileşim, üzerinden <xref:System.IServiceProvider.GetService%2A>hizmet isteme ile sınırlıdır.  
  
<a name="available_systemxaml_services"></a>   
## <a name="available-services-from-the-net-framework-xaml-service-context"></a>.NET Framework XAML hizmet bağlamından kullanılabilir hizmetler  
 .NET Framework XAML Hizmetleri, biçimlendirme uzantıları, tür dönüştürücüler, değer serileştiriciler ve potansiyel olarak diğer kullanımlar için hizmetleri tanımlar. Aşağıdaki bölümler bu hizmetlerin her birini açıklamaktadır ve hizmetin bir uygulamada nasıl kullanılabileceği hakkında rehberlik sağlar.  
  
### <a name="iserviceprovider"></a>IServiceProvider  
 **Başvuru belgeleri**:<xref:System.IServiceProvider>  
  
 **İlgili:** Çağırabilmeniz <xref:System.IServiceProvider.GetService%2A?displayProperty=nameWithType>için .NET Framework bir hizmet tabanlı altyapının temel işlemi.  
  
### <a name="itypedescriptorcontext"></a>ITypeDescriptorContext  
 **Başvuru belgeleri**:<xref:System.ComponentModel.ITypeDescriptorContext>  
  
 Türetiliyor <xref:System.IServiceProvider>. Bu sınıf, standart <xref:System.ComponentModel.TypeConverter> imzalarda bağlamı temsil eder; <xref:System.ComponentModel.TypeConverter> , 1,0 .NET Framework sonrasında var olan bir sınıftır. Dize-değer türü dönüştürmesi için XAML <xref:System.ComponentModel.TypeConverter> ve xaml senaryosu ön tarihleridir. .NET Framework xaml Hizmetleri bağlamında, yöntemleri <xref:System.ComponentModel.TypeConverter> açıkça uygulanır. Açık uygulamanın davranışı, <xref:System.ComponentModel.ITypeDescriptorContext> API 'nin, API 'nin xaml tür sistemleri için ilgili olmadığını veya xaml 'den nesneleri okuma veya yazma için uygun olmadığını belirtir. <xref:System.ComponentModel.ITypeDescriptorContext.Container%2A>, <xref:System.ComponentModel.ITypeDescriptorContext.Instance%2A>, ve <xref:System.ComponentModel.ITypeDescriptorContext.PropertyDescriptor%2A> genellikle .NET Framework `null` xaml Hizmetleri bağlamlarından geri döner.  
  
### <a name="ivalueserializercontext"></a>IValueSerializerContext  
 **Başvuru belgeleri**:<xref:System.Windows.Markup.IValueSerializerContext>  
  
 ' Den <xref:System.ComponentModel.ITypeDescriptorContext> türetilir ve ayrıca xaml tür sistemi hakkındaki hatalı etkileri bastırmak için açık uygulamalara bağımlıdır. , Üzerindeki <xref:System.Windows.Markup.ValueSerializer>statik Arama Yardımcısı yöntemlerini destekler.  
  
### <a name="ixamltyperesolver"></a>IXamlTypeResolver  
 **Başvuru belgeleri**:<xref:System.Windows.Markup.IXamlTypeResolver>  
  
 **Tanımladığı:** <xref:System.Windows.Markup> Namespace, System. Xaml derlemesi  
  
 **İlgili:** Yükleme yolu senaryoları ve XAML şema bağlamı ile etkileşim  
  
 **Hizmet API 'SI:**  <xref:System.Windows.Markup.IXamlTypeResolver.Resolve%2A>  
  
 , XAML yazıcı bir nesne grafiğinde CLR nesnesi oluştururken gerekli olan XAML-CLR tür eşlemesini etkileyebilir. <xref:System.Windows.Markup.IXamlTypeResolver.Resolve%2A>bir xaml tür adına (<xref:System.Xaml.XamlType.Name%2A?displayProperty=nameWithType>) karşılık gelen ön ek nitelenmiş bir dizeyi işler ve bir clr <xref:System.Type>döndürür. Türleri çözümlemek, genellikle XAML şema bağlamına yoğun olarak bağımlıdır. Yalnızca XAML şeması bağlamı, hangi derlemelerin yüklendiği ve bu derlemelerin ne tür çözümleme için erişilmesi gerektiği gibi hususlar hakkında farklardır.  
  
### <a name="iuricontext"></a>IUriContext  
 **Başvuru belgeleri**:<xref:System.Windows.Markup.IUriContext>  
  
 **Tanımladığı:** <xref:System.Windows.Markup> Namespace, System. Xaml derlemesi  
  
 **İlgili:** URI veya `x:Uri` değer olan üye değerlerinin yük yolunu ve kayıt yolunu kaydetme.  
  
 **Hizmet API 'SI:**  <xref:System.Windows.Markup.IUriContext.BaseUri%2A>  
  
 Bu hizmet, varsa, genel olarak kullanılabilir bir URI kökünü bildirir. URI kökü, göreli URI 'Leri mutlak URI 'lere çözümlemek veya bunun tersini yapmak için kullanılabilir. Bu senaryo, özellikle belirli bir Framework tarafından sunulan uygulama hizmetleri veya bir çerçevede sık kullanılan bir kök öğe sınıfının yetenekleri ile ilgilidir. Temel URI bir XAML okuyucu ayarı olarak kurulabilir, bu, daha sonra XAML nesne yazıcısına geçirilir ve bu hizmet tarafından raporlanır.  
  
### <a name="iambientprovider"></a>IAmbientProvider  
 **Başvuru belgeleri**:<xref:System.Xaml.IAmbientProvider>  
  
 **Tanımladığı:** <xref:System.Xaml> Namespace, System. Xaml derlemesi  
  
 **İlgili:** Yük yol işleme ve tür arama erteleme veya iyileştirmeler.  
  
 **Hizmet API 'leri:** <xref:System.Xaml.IAmbientProvider.GetAllAmbientValues%2A>, 3 kişi.  
  
 XAML 'de Ambience kavramı, bir türün belirli bir üyesini çevresel olarak işaretlemek için bir tekniktir. Alternatif olarak, türü bir örneği tutan tüm özellik değerlerinin çevresel özellikler olarak kabul edilmesi için bir tür çevresel olabilir. Biçimlendirme uzantıları veya XAML düğüm akışı üzerinde daha fazla olan ve nesne grafiğinde alt öğeler bulunan tür dönüştürücüler, yükleme zamanında çevresel özelliğe veya tür örneğine erişebilir; ya da kaydetme zamanında çevresel Yapı bilgisini kullanabilir. Bu, <xref:System.Windows.Markup.IXamlTypeResolver> veya için `x:Type`gibi diğer hizmetlere yönelik türleri çözümlemek için gereken niteliğin derecesini etkileyebilir. Ayrıca <xref:System.Xaml.AmbientPropertyValue>bkz.  
  
### <a name="ixamlschemacontextprovider"></a>IXamlSchemaContextProvider  
 **Başvuru belgeleri**:<xref:System.Xaml.IXamlSchemaContextProvider>  
  
 **Tanımladığı:** <xref:System.Xaml> Namespace, System. Xaml derlemesi  
  
 **İlgili:** Yükleme yolu ve bir XAML türünü bir yedekleme türüne çözülmesi gereken herhangi bir işlem.  
  
 **Hizmet API 'SI:**  <xref:System.Xaml.IXamlSchemaContextProvider.SchemaContext%2A>  
  
 Her türlü yükleme işlemini erteleme için XAML şeması bağlamı gerekir, çünkü ertelenmiş içeriği bütünleştirmek için aynı şema bağlamı ertelenmiş alanı üzerinde çalışır olmalıdır. XAML şeması bağlamının rolü hakkında daha fazla bilgi için bkz. [xaml Hizmetleri](index.md).  
  
### <a name="irootobjectprovider"></a>IRootObjectProvider  
 **Başvuru belgeleri**:<xref:System.Xaml.IRootObjectProvider>  
  
 **Tanımladığı:** <xref:System.Xaml> Namespace, System. Xaml derlemesi  
  
 **İlgili:** Yükleme yolu.  
  
 **Hizmet API 'SI:**  <xref:System.Xaml.IRootObjectProvider.RootObject%2A>  
  
 Hizmet, belirli bir çerçeve tarafından veya bir çerçevede sık kullanılan bir kök öğe sınıfının özellikleri tarafından sunulan uygulama hizmetleri ile ilgilidir. Kök nesneyi elde etmek için bir senaryo, arka plan kod ve olay kablolaması bağlanıyor. Örneğin WPF uygulamasının `x:Class` , xaml biçimlendirmesinde herhangi bir konumda bulunan herhangi bir olay işleyicisi özniteliği için biçimlendirme derlemesi ve kablolama için kullanılır. Biçimlendirme derlemesi için biçimlendirme ve arka plan kodlu kısmi sınıfların bağlantı noktası kök öğedir.  
  
### <a name="ixamlnamespaceresolver"></a>IXamlNamespaceResolver  
 **Başvuru belgeleri**:<xref:System.Xaml.IXamlNamespaceResolver>  
  
 **Tanımladığı:** <xref:System.Xaml> Namespace, System. Xaml derlemesi  
  
 **İlgili:** Yükleme yolu, yolu Kaydet.  
  
 **Hizmet API 'si:** yükleme yolu için, <xref:System.Xaml.IXamlNamespaceResolver.GetNamespacePrefixes%2A> yolu Kaydet için. <xref:System.Xaml.IXamlNamespaceResolver.GetNamespace%2A>  
  
 <xref:System.Xaml.IXamlNamespaceResolver>, bir XAML ad alanı tanımlayıcısı/URI 'sini, ön ekine bağlı XAML biçimlendirmesinde eşlenmiş olarak döndürebilir bir hizmettir.  
  
### <a name="iprovidevaluetarget"></a>IProvideValueTarget  
 **Başvuru belgeleri**:<xref:System.Windows.Markup.IProvideValueTarget>  
  
 **Tanımladığı:** <xref:System.Windows.Markup> Namespace, System. Xaml derlemesi  
  
 **İlgili:** Yolu yükle ve yolu Kaydet.  
  
 **Hizmet API 'Leri:** <xref:System.Windows.Markup.IProvideValueTarget.TargetObject%2A>, <xref:System.Windows.Markup.IProvideValueTarget.TargetProperty%2A>.  
  
 <xref:System.Windows.Markup.IProvideValueTarget>bir tür dönüştürücüsünün veya biçimlendirme uzantısının yükleme zamanında hareket ettiği yere yönelik bağlamı almasını sağlar. Uygulamalar, bir kullanımı geçersiz kılmak için bu bağlamı kullanabilir. Örneğin WPF, gibi biçimlendirme uzantılarının <xref:System.Windows.DynamicResourceExtension>bazıları içinde Logic sahiptir. Mantığı, <xref:System.Windows.Markup.IProvideValueTarget.TargetProperty%2A> uzantının yalnızca bağımlılık özelliklerini (veya bağımlılık olmayan diğer özelliklerin kısa bir listesini) ayarlamak için kullanıldığından emin olmak için ' i denetler.  
  
### <a name="ixamlnameresolver"></a>IXamlNameResolver  
 **Başvuru belgeleri**:<xref:System.Xaml.IXamlNameResolver>  
  
 **Tanımladığı:** <xref:System.Xaml> Namespace, System. Xaml derlemesi  
  
 **İlgili:** Yük yolu nesne grafik tanımı,, veya çerçevesine özgü `x:Name`teknikler `x:Reference`tarafından tanımlanan nesneleri çözme.  
  
 **Hizmet API 'leri:** <xref:System.Xaml.IXamlNameResolver.Resolve%2A>; ileri başvurularla ilgili daha gelişmiş senaryolar için diğer API 'ler.  
  
 `x:Reference` İşleme .NET Framework xaml Hizmetleri uygulamasının bu hizmeti temel alır. Çerçeveyi destekleyen belirli çerçeveler veya Araçlar bu hizmeti işleme veya eşdeğer ( `x:Name` <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> öznitelikli) özellik işleme için kullanır.  
  
### <a name="idestinationtypeprovider"></a>IDestinationTypeProvider  
 **Başvuru belgeleri**:<xref:System.Xaml.IDestinationTypeProvider>  
  
 **Tanımladığı:** <xref:System.Xaml> Namespace, System. Xaml derlemesi  
  
 **İlgili:** Dolaylı CLR türü bilgilerinin yükleme yolu çözümlemesi.  
  
 **Hizmet API 'si:** <xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A>  
  
 Daha fazla bilgi için bkz. <xref:System.Xaml.IDestinationTypeProvider>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Markup.MarkupExtension>
- <xref:System.Xaml.XamlObjectWriter>
- [XAML İşaretleme Uzantılarına Genel Bakış](markup-extensions-for-xaml-overview.md)
- [XAML Tür Dönüştürücülerine Genel Bakış](type-converters-for-xaml-overview.md)
