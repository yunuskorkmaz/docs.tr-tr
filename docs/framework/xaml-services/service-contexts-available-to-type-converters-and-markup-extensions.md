---
title: Tür Dönüştürücülerinde ve İşaretleme Uzantılarında Kullanılabilir Hizmet Bağlamları
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], type converter services how-to
ms.assetid: b4dad00f-03da-4579-a4e9-d8d72d2ccbce
ms.openlocfilehash: 850e266aed6fc2d69722ba6dac3baa3e115678a8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59147803"
---
# <a name="service-contexts-available-to-type-converters-and-markup-extensions"></a>Tür Dönüştürücülerinde ve İşaretleme Uzantılarında Kullanılabilir Hizmet Bağlamları
Türü dönüştürücü ve biçimlendirme uzantısı kullanımı destekleyen türleri yazarları, genellikle bir kullanım işaretleme veya Nesne grafiği yapısı çevreleyen bulunduğu hakkında bağlamsal bilgiler olması gerekir. Bilgi sağlanan nesne doğru örneği veya Nesne grafiğini içinde varolan nesnelere nesne başvuruları hale getirilebilir, böylece gerekebilir. .NET Framework XAML hizmetlerinde kullanırken gerekli olabilecek bağlam Hizmet Arabirimleri bir dizi olarak kullanıma sunulur. Türü dönüştürücü veya biçimlendirme uzantısı desteği için kod, bir hizmet için geçilen gelen ve kullanılabilir bir hizmet sağlayıcısı bağlamı kullanarak sorgulayabilir <xref:System.Xaml.XamlObjectWriter> veya ilgili türler. XAML şema içeriği doğrudan bu tür bir hizmet aracılığıyla kullanılabilir. Bu konu, bir değer dönüştürücü uygulamasından hizmet bağlamları erişim açıklar ve genellikle kullanılabilir hizmetleri ve kendi rolleri listeler.  
  
<a name="obtaining_services"></a>   
## <a name="obtaining-services"></a>Hizmetleri edinme  
 Bir değer dönüştürücü Uygulayıcısı, genellikle bu bağlamda herhangi bir türde değer dönüştürücü uygulanan erişmeniz gerekir. Bu bağlam etkin XAML şema içeriği gibi bilgileri ekleyin, XAML şema içeriği ve XAML nesne yazıcısı sağlayan ve benzeri türü eşleme sistemine erişebilir. İşaretleme uzantısı ya da tür dönüştürücü uygulama hizmetleri, her sanal yöntem imzasının parçası olan bağlam parametreleri bildirilir. Her durumda, sahip olduğunuz <xref:System.IServiceProvider> bağlamda uygulanır ve çağırabilirsiniz <xref:System.IServiceProvider.GetService%2A?displayProperty=nameWithType> bir hizmet istemek için.  
  
<a name="services_for_a_markup_extension"></a>   
## <a name="services-for-a-markup-extension"></a>İşaretleme uzantısı Hizmetleri  
 <xref:System.Windows.Markup.MarkupExtension> yalnızca bir sanal yöntemi, <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>. Giriş `serviceProvider` parametredir işaretleme uzantısı XAML işlemcisi tarafından çağrıldığında hizmetler için uygulamaları nasıl bildirilir. İşaretleme uzantısı uygulama hizmetleri için nasıl bir sorgu, aşağıdaki sözde kod gösterir, <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>:  
  
```  
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
## <a name="services-for-a-type-converter"></a>Tür dönüştürücü Hizmetleri  
 <xref:System.ComponentModel.TypeConverter> Hizmet bağlamı kullanan ve XAML kullanımları destekleyen dört sanal yöntemler vardır. Bu yöntemlerin her biri giriş geçirir `context` parametresi. Bu parametre türüdür <xref:System.ComponentModel.ITypeDescriptorContext>, ancak bu arabirimi devralır <xref:System.IServiceProvider>ve bu nedenle, bir <xref:System.IServiceProvider.GetService%2A> yöntemi tür dönüştürücü uygulamaları kullanılabilir.  
  
 Aşağıdaki sözde kod nasıl bir tür dönüştürücüsü gerçeklemesi XAML kullanımlar için Hizmetleri, geçersiz kılmalar birinde bu durumda sorgusu gösterir <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>:  
  
```  
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
## <a name="services-for-a-value-serializer"></a>Hizmetler için bir değer seri hale getirici  
 Değeri serileştirici bağlamı için özel bir hizmet sağlayıcı türü kullanan <xref:System.Windows.Markup.ValueSerializer> sınıfı <xref:System.Windows.Markup.IValueSerializerContext>. Bu bağlamı dört geçersiz kılmalar için geçirilen <xref:System.Windows.Markup.ValueSerializer> sanal yöntemler. Çağrı <xref:System.IServiceProvider.GetService%2A> bağlamından Hizmetleri elde edilir.  
  
<a name="using_the_xaml_service_provider_contexts"></a>   
## <a name="using-the-xaml-service-provider-contexts"></a>XAML hizmet sağlayıcısı bağlamı kullanma  
 Hizmet sağlayıcısı için <xref:System.IServiceProvider.GetService%2A> biçimlendirme uzantıları veya tür dönüştürücüleri kullanılabilir XAML hizmetlerine erişim ile arabirimi ve ilgili bağlamına nasıl geçirildiğini aracılığıyla yalnızca bir iç sınıf olarak uygulanır. Bir XAML uygulamalarında varsayılan .NET Framework XAML hizmetlerinde işlem işleme yolu yük veya yolu bir hizmet bağlamı gerekli ilgili işaretleme uzantısı ya da türü dönüştürücü yöntemlerini çağırır olduğunda, bu iç nesne geçirilir. Durumda bağlı olarak ya da sistem hizmet bağlamı sağlar `MarkupExtensionContext` veya `TextSyntaxContext`, ancak bu sınıfların her ikisi de ayrıntılarını iç. Bu sınıflar ile etkileşim için istekte bulunan Hizmetleri kendilerinden aracılığıyla sınırlı <xref:System.IServiceProvider.GetService%2A>.  
  
<a name="available_systemxaml_services"></a>   
## <a name="available-services-from-the-net-framework-xaml-service-context"></a>.NET Framework XAML hizmeti bağlamından kullanılabilir hizmetler  
 .NET framework XAML hizmetlerinde Hizmetleri biçimlendirme uzantıları, tür dönüştürücüleri, değeri seri hale getiricileri genişletme ve büyük olasılıkla diğer kullanımları için tanımlar. Aşağıdaki bölümlerde, bu hizmetlerin her biri açıklamak ve uygulama hizmeti nasıl kullanılabileceğine hakkında rehberlik sağlar.  
  
### <a name="iserviceprovider"></a>IServiceProvider  
 **Başvuru belgeleri**: <xref:System.IServiceProvider>  
  
 **İlgili:** .NET Framework içinde hizmet tabanlı bir altyapı temek işleyişini çağırabilirsiniz böylece <xref:System.IServiceProvider.GetService%2A?displayProperty=nameWithType>.  
  
### <a name="itypedescriptorcontext"></a>ITypeDescriptorContext  
 **Başvuru belgeleri**: <xref:System.ComponentModel.ITypeDescriptorContext>  
  
 Öğesinden türetilen <xref:System.IServiceProvider>. Bu sınıf, standart bir bağlamda gösterir <xref:System.ComponentModel.TypeConverter> imzaları; <xref:System.ComponentModel.TypeConverter> bu yana .NET Framework 1.0 var bir sınıftır. XAML ve XAML öncülü <xref:System.ComponentModel.TypeConverter> senaryo için dize değeri tür dönüştürme. .NET Framework XAML hizmetlerinde bağlamında yöntemlerinin <xref:System.ComponentModel.TypeConverter> açıkça uygulanır. Arayanlara açık uygulama 's davranış gösterir, <xref:System.ComponentModel.ITypeDescriptorContext> API türü sistemlerinin XAML veya okuma veya XAML nesne yazmak için uygun değil. <xref:System.ComponentModel.ITypeDescriptorContext.Container%2A>, <xref:System.ComponentModel.ITypeDescriptorContext.Instance%2A>, ve <xref:System.ComponentModel.ITypeDescriptorContext.PropertyDescriptor%2A> genellikle iade `null` .NET Framework XAML hizmetlerinde bağlamları öğesinden.  
  
### <a name="ivalueserializercontext"></a>IValueSerializerContext  
 **Başvuru belgeleri**: <xref:System.Windows.Markup.IValueSerializerContext>  
  
 Öğesinden türetilen <xref:System.ComponentModel.ITypeDescriptorContext> ve XAML tür sistemi hakkında yanlış etkileri bastırmak için açık uygulamaları üzerinde de dayanır. Statik arama yardımcı yöntemler destekler <xref:System.Windows.Markup.ValueSerializer>.  
  
### <a name="ixamltyperesolver"></a>IXamlTypeResolver  
 **Başvuru belgeleri**: <xref:System.Windows.Markup.IXamlTypeResolver>  
  
 **Tanımlanır:** <xref:System.Windows.Markup> ad alanı, System.Xaml derleme  
  
 **İlgili:** Yükleme yolu senaryolarını ve XAML şema içeriği ile etkileşim  
  
 **Hizmet API'si:**  <xref:System.Windows.Markup.IXamlTypeResolver.Resolve%2A>  
  
 XAML yazan bir CLR nesnesini bir nesne grafiğinin yapılandırdığında, gerekli olan XAML CLR tür eşlemesi etkileyebilir. <xref:System.Windows.Markup.IXamlTypeResolver.Resolve%2A> XAML tür adı için karşılık gelen bir ön ek nitelikli potansiyel olarak dize işlemleri (<xref:System.Xaml.XamlType.Name%2A?displayProperty=nameWithType>) ve bir CLR döndürür <xref:System.Type>. Türleri çözme genellikle XAML şema içeriği üzerinde bağımlılığa sahiptir. Yalnızca XAML şema içeriği gibi hangi derlemelerin yüklü olduğundan ve bu derleme veya yapabilirsiniz için tür çözümlemesi erişilmesi gereken noktaları göz önünde bulundurun.  
  
### <a name="iuricontext"></a>IUriContext  
 **Başvuru belgeleri**: <xref:System.Windows.Markup.IUriContext>  
  
 **Tanımlanır:** <xref:System.Windows.Markup> ad alanı, System.Xaml derleme  
  
 **İlgili:** Yükleme yolu ve yol işleme URI'ler üye değerleri kaydedin veya `x:Uri` değerleri.  
  
 **Hizmet API'si:**  <xref:System.Windows.Markup.IUriContext.BaseUri%2A>  
  
 Bu hizmet, varsa küresel olarak kullanılabilir bir URI kök bildirir. URI Kökü mutlak bir URI'leri ya da tam tersi göreli URI'ler gidermek için kullanılabilir. Bu senaryo genellikle belirli bir çerçeve veya bir sık kullanılan kök öğe sınıfı bir Framework yeteneklerini tarafından kullanıma sunulan uygulama hizmetleri için geçerlidir. Taban URI ardından için XAML nesne yazıcısı geçtiğini ve bu hizmeti tarafından raporlanan ayarını bir XAML okuyucu olarak kurulur.  
  
### <a name="iambientprovider"></a>IAmbientProvider  
 **Başvuru belgeleri**: <xref:System.Xaml.IAmbientProvider>  
  
 **Tanımlanır:** <xref:System.Xaml> ad alanı, System.Xaml derleme  
  
 **İlgili:** Yol türü ve işleme arama gönderilemeyenler veya en iyi duruma getirme yükleyin.  
  
 **Hizmet API'lerini:**<xref:System.Xaml.IAmbientProvider.GetAllAmbientValues%2A>, diğer 3.  
  
 XAML içinde çevre kavramı, belirli bir tür olarak ortam üyesi işaretlemek için kullanılan bir tekniktir. Alternatif olarak, böylece ortam özellikleri, türün bir örneğini barındıran tüm özellik değerlerini düşünülmesi gereken bir tür ortam olabilir. Biçimlendirme uzantıları veya XAML düğümü akışı başka olan ve alt nesne grafiğini olan tür dönüştürücüleri ortam özellik veya türü örneği yükleme zamanında erişebilir; veya ortam yapı zaman kazandırır bilgi kullanabilirler. Bu diğer hizmetler için türleri gibi çözmek için gerekli nitelik derecesini etkileyebilir <xref:System.Windows.Markup.IXamlTypeResolver> veya `x:Type`. Ayrıca bkz: <xref:System.Xaml.AmbientPropertyValue>.  
  
### <a name="ixamlschemacontextprovider"></a>IXamlSchemaContextProvider  
 **Başvuru belgeleri**: <xref:System.Xaml.IXamlSchemaContextProvider>  
  
 **Tanımlanır:** <xref:System.Xaml> ad alanı, System.Xaml derleme  
  
 **İlgili:** Yükleme yolu ve herhangi bir işlem bir XAML türü için bir yedekleme türü çözmeniz gerekir.  
  
 **Hizmet API'si:**  <xref:System.Xaml.IXamlSchemaContextProvider.SchemaContext%2A>  
  
 Ertelenmiş içerik tümleştirmek için aynı şema içeriği ertelenmiş alan davranmalıdır XAML şema içeriği defer yükleme işlemleri için gereklidir. XAML şema içeriği rolü hakkında daha fazla bilgi için bkz. [XAML Hizmetleri](index.md).  
  
### <a name="irootobjectprovider"></a>IRootObjectProvider  
 **Başvuru belgeleri**: <xref:System.Xaml.IRootObjectProvider>  
  
 **Tanımlanır:** <xref:System.Xaml> ad alanı, System.Xaml derleme  
  
 **İlgili:** Yükleme yolu.  
  
 **Hizmet API'si:**  <xref:System.Xaml.IRootObjectProvider.RootObject%2A>  
  
 Hizmet, belirli bir çerçeve veya bir sık kullanılan kök öğe sınıfı bir Framework yeteneklerini tarafından kullanıma sunulan uygulama hizmetleri için geçerlidir. Kök nesnesi almak için bir senaryo, arka plan kod ve olay kablolama bağlanıyor. Örneğin, WPF uygulaması `x:Class` kullanılan biçimlendirmesi derleme ve kablolama, XAML biçimlendirmede diğer herhangi bir konumda bulunan herhangi bir olay işleyicisi öznitelik. Biçimlendirme derleme kök öğe için kısmi sınıflar biçimlendirme arka plan kod ve bağlantı noktası tanımlanır.  
  
### <a name="ixamlnamespaceresolver"></a>IXamlNamespaceResolver  
 **Başvuru belgeleri**: <xref:System.Xaml.IXamlNamespaceResolver>  
  
 **Tanımlanır:** <xref:System.Xaml> ad alanı, System.Xaml derleme  
  
 **İlgili:** Kaydetme yolu yükleme yolu.  
  
 **Hizmet API'si:** <xref:System.Xaml.IXamlNamespaceResolver.GetNamespace%2A> yükleme yolu için <xref:System.Xaml.IXamlNamespaceResolver.GetNamespacePrefixes%2A> için kaydetme yolu.  
  
 <xref:System.Xaml.IXamlNamespaceResolver> XAML ad alanı tanımlayıcısı döndüren bir hizmet / URI kaynak XAML biçimlendirmede eşlenmiş olarak kendi ön ek tabanlı.  
  
### <a name="iprovidevaluetarget"></a>IProvideValueTarget  
 **Başvuru belgeleri**: <xref:System.Windows.Markup.IProvideValueTarget>  
  
 **Tanımlanır:** <xref:System.Windows.Markup> ad alanı, System.Xaml derleme  
  
 **İlgili:** Yükleme yolu ve yol kaydedin.  
  
 **Hizmet API'lerini:**<xref:System.Windows.Markup.IProvideValueTarget.TargetObject%2A>, <xref:System.Windows.Markup.IProvideValueTarget.TargetProperty%2A>.  
  
 <xref:System.Windows.Markup.IProvideValueTarget> Yükleme zamanında burada davrandığı hakkında bağlam elde etmek bir tür dönüştürücüsü veya işaretleme uzantısı sağlar. Uygulamaları bu bağlamda bir kullanım geçersiz kılmak için kullanabilirsiniz. Örneğin, WPF gibi bazı biçimlendirme uzantıları içinde mantığının sahip <xref:System.Windows.DynamicResourceExtension>. Mantık denetimlerini <xref:System.Windows.Markup.IProvideValueTarget.TargetProperty%2A> uzantı bağımlılık özellikleri (veya diğer bağımlılık olmayan özellikleri kısa listesi) ayarlamak için yalnızca kullanıldığından emin olmak için.  
  
### <a name="ixamlnameresolver"></a>IXamlNameResolver  
 **Başvuru belgeleri**: <xref:System.Xaml.IXamlNameResolver>  
  
 **Tanımlanır:** <xref:System.Xaml> ad alanı, System.Xaml derleme  
  
 **İlgili:** Yükleme yolu Nesne grafiği tanımı tarafından tanımlanan nesneleri çözümleniyor, `x:Name`, `x:Reference`, veya çerçeveye özgü teknikleri.  
  
 **Hizmet API'lerini:**<xref:System.Xaml.IXamlNameResolver.Resolve%2A>; diğer API'ler İleri başvurulara uğraşmanızı gibi daha Gelişmiş senaryolar için.  
  
 .NET Framework XAML hizmetlerinde uygulamasını `x:Reference` işleme bu hizmeti kullanır. Belirli çerçeveleri ya da çerçevesini destekleyen araçları kullanmak için bu hizmeti `x:Name` işleme veya eşdeğeri (<xref:System.Windows.Markup.RuntimeNamePropertyAttribute> öznitelikli) özelliği işleme.  
  
### <a name="idestinationtypeprovider"></a>IDestinationTypeProvider  
 **Başvuru belgeleri**: <xref:System.Xaml.IDestinationTypeProvider>  
  
 **Tanımlanır:** <xref:System.Xaml> ad alanı, System.Xaml derleme  
  
 **İlgili:** Yol çözümlemesi dolaylı CLR türü bilgilerinin yükleyin.  
  
 **Hizmet API'si:** <xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A>  
  
 Daha fazla bilgi için bkz. <xref:System.Xaml.IDestinationTypeProvider>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Markup.MarkupExtension>
- <xref:System.Xaml.XamlObjectWriter>
- [XAML İşaretleme Uzantılarına Genel Bakış](markup-extensions-for-xaml-overview.md)
- [XAML Tür Dönüştürücülerine Genel Bakış](type-converters-for-xaml-overview.md)
