---
title: "Tür Dönüştürücülerinde ve İşaretleme Uzantılarında Kullanılabilir Hizmet Bağlamları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: XAML [XAML Services], type converter services how-to
ms.assetid: b4dad00f-03da-4579-a4e9-d8d72d2ccbce
caps.latest.revision: "13"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 229601515442b5e84f6c4278b17db7ae25945a42
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="service-contexts-available-to-type-converters-and-markup-extensions"></a>Tür Dönüştürücülerinde ve İşaretleme Uzantılarında Kullanılabilir Hizmet Bağlamları
Tür dönüştürücü ve biçimlendirme uzantısı kullanımları destekleyen türler yazarları genellikle bir kullanım biçimlendirme veya Nesne grafiği yapısını çevreleyen bulunduğu hakkında bağlamsal bilgilerine sahip olması gerekir. Bilgi sağlanan nesne doğru örneği veya varolan nesneleri nesneyi grafikte nesne başvuruları yapılabilir böylece gerekli. .NET Framework XAML hizmetlerinde kullanırken gerekli olabilecek bağlamı Hizmet Arabirimleri bir dizi olarak sunulur. Türü dönüştürücü veya işaretleme uzantısı destek kodu, bir hizmet için kullanılabilir ve gelen aracılığıyla geçirilen bir hizmet sağlayıcısı bağlamı kullanarak sorgulayabilir <xref:System.Xaml.XamlObjectWriter> veya ilgili türleri. XAML şema içeriği böyle bir hizmeti üzerinden doğrudan kullanılabilir. Bu konu hizmet bağlamları bir değer dönüştürücüsü uygulamasından erişmek açıklar ve genellikle kullanılabilir hizmetleri ve kendi rolleri listeler.  
  
<a name="obtaining_services"></a>   
## <a name="obtaining-services"></a>Hizmetleri alma  
 Değer dönüştürücüsü Uygulayıcısı, genellikle bu bağlamda herhangi bir tür için değer dönüştürücüsü uygulanan Erişim gerekir. Bu bağlamda etkin XAML şema içeriği gibi bilgileri içerir, XAML şema içeriği ve XAML nesne yazıcısı sağlayan ve benzeri türü eşleme sisteme erişim. Biçimlendirme uzantısı veya türü dönüştürücü uygulaması için Hizmetleri, her sanal bir yöntem imzası parçası olan bağlam parametreleri bildirilir. Her durumda, sahip olduğunuz <xref:System.IServiceProvider> bağlamda uygulanan ve çağırabilir <xref:System.IServiceProvider.GetService%2A?displayProperty=nameWithType> bir hizmet isteği için.  
  
<a name="services_for_a_markup_extension"></a>   
## <a name="services-for-a-markup-extension"></a>Biçimlendirme uzantısı Hizmetleri  
 <xref:System.Windows.Markup.MarkupExtension>yalnızca bir sanal yöntemi sahip <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>. Giriş `serviceProvider` parametredir biçimlendirme uzantısı XAML işlemcisi tarafından çağrıldığında Hizmetleri için uygulamaları nasıl bildirilir. Biçimlendirme uzantısı uygulama hizmetleri için nasıl bir sorgu aşağıdaki yarı kodu gösterilmektedir, <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>:  
  
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
 <xref:System.ComponentModel.TypeConverter>bir hizmet bağlamı kullanan ve XAML kullanımları destekleyen dört sanal yöntemlerine sahiptir. Bu yöntemlerin her biri bir giriş geçirir `context` parametresi. Bu parametre türünde <xref:System.ComponentModel.ITypeDescriptorContext>, ancak bu arabirimi devralır <xref:System.IServiceProvider>ve bu nedenle, bir <xref:System.IServiceProvider.GetService%2A> yöntemi dönüştürücü uygulamaları yazmak kullanılabilir.  
  
 Aşağıdaki yarı kodu nasıl XAML kullanımlar için bir tür dönüştürücü uygulama hizmetleri, geçersiz kılmalar birinde bu durumda sorgulama gösterilmektedir <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>:  
  
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
## <a name="services-for-a-value-serializer"></a>Değer bir seri hale getirici Hizmetleri  
 Değer serileştirici bağlamı için kullandığınız özgü bir hizmet sağlayıcısı türü <xref:System.Windows.Markup.ValueSerializer> sınıfı, <xref:System.Windows.Markup.IValueSerializerContext>. Bu bağlam dört geçersiz kılmalar için geçirilen <xref:System.Windows.Markup.ValueSerializer> sanal yöntemler. Çağrı <xref:System.IServiceProvider.GetService%2A> services edinme bağlamından.  
  
<a name="using_the_xaml_service_provider_contexts"></a>   
## <a name="using-the-xaml-service-provider-contexts"></a>XAML hizmet sağlayıcısı bağlamları kullanma  
 Hizmet sağlayıcısı için <xref:System.IServiceProvider.GetService%2A> XAML Hizmetleri için işaretleme uzantıları veya tür dönüştürücüleri kullanılabilir erişimi yalnızca arabirimi ve ilgili bağlamına nasıl geçtiğini aracılığıyla Etkilenme ile bir iç sınıf olarak uygulanır. XAML işleme işlemi varsayılan .NET Framework XAML Hizmetleri uygulamalarında yolu yüklemek veya bir hizmet bağlamı gerektiren ilgili biçimlendirme uzantısı veya türü dönüştürücü yöntemleri yol çağırır olduğunda, bu bir iç nesne geçirilir. Koşul bağlı olarak ya da sistem hizmet bağlamı sağlar `MarkupExtensionContext` veya `TextSyntaxContext`, ancak bu sınıfların her ikisi de ayrıntılarını iç. Bu sınıfların ile etkileşim için istekte bulunan Hizmetleri kendilerinden aracılığıyla sınırlı <xref:System.IServiceProvider.GetService%2A>.  
  
<a name="available_systemxaml_services"></a>   
## <a name="available-services-from-the-net-framework-xaml-service-context"></a>.NET Framework XAML hizmet bağlamından kullanılabilir hizmetler  
 .NET framework XAML hizmetlerinde biçimlendirme uzantıları, tür dönüştürücüleri, değer serileştiricileri ve büyük olasılıkla diğer kullanımlar için hizmetleri tanımlar. Aşağıdaki bölümlerde bu hizmetlerin her birini açıklayan ve hizmet uygulama için nasıl kullanılabilir hakkında rehberlik sağlar.  
  
### <a name="iserviceprovider"></a>IServiceProvider  
 **Başvuru belgelerini**:<xref:System.IServiceProvider>  
  
 **İlgili:** .NET Framework hizmet tabanlı bir altyapıda temel işlemini çağırabilirsiniz böylece <xref:System.IServiceProvider.GetService%2A?displayProperty=nameWithType>.  
  
### <a name="itypedescriptorcontext"></a>ITypeDescriptorContext  
 **Başvuru belgelerini**:<xref:System.ComponentModel.ITypeDescriptorContext>  
  
 Türetilen <xref:System.IServiceProvider>. Bu sınıf bağlamını standart temsil eder <xref:System.ComponentModel.TypeConverter> imzalar; <xref:System.ComponentModel.TypeConverter> .NET Framework 1.0 itibaren var bir sınıftır. XAML ve XAML öncülü <xref:System.ComponentModel.TypeConverter> senaryo dize değeri tür dönüştürmeleri için. .NET Framework XAML Hizmetleri bağlamında yöntemlerini <xref:System.ComponentModel.TypeConverter> açıkça uygulanır. Arayanlara açık uygulama 's davranışını gösteren, <xref:System.ComponentModel.ITypeDescriptorContext> API XAML tür sistemler için veya Okuma ya da XAML nesne yazmak için uygun değil. <xref:System.ComponentModel.ITypeDescriptorContext.Container%2A>, <xref:System.ComponentModel.ITypeDescriptorContext.Instance%2A>, ve <xref:System.ComponentModel.ITypeDescriptorContext.PropertyDescriptor%2A> genellikle dönmek `null` .NET Framework XAML hizmetlerinde bağlamları gelen.  
  
### <a name="ivalueserializercontext"></a>IValueSerializerContext  
 **Başvuru belgelerini**:<xref:System.Windows.Markup.IValueSerializerContext>  
  
 Türetilen <xref:System.ComponentModel.ITypeDescriptorContext> ve ayrıca XAML tür sistemi hakkında false etkileri gizlemek için açık uygulamaları dayanır. Üzerinde statik Arama Yardımcısı yöntemleri destekler <xref:System.Windows.Markup.ValueSerializer>.  
  
### <a name="ixamltyperesolver"></a>IXamlTypeResolver  
 **Başvuru belgelerini**:<xref:System.Windows.Markup.IXamlTypeResolver>  
  
 **Tanımlanır:** <xref:System.Windows.Markup> ad alanı, System.Xaml derleme    
  
 **İlgili:** yükleme yolu senaryolarını ve XAML şema içeriği ile etkileşim  
  
 **Hizmeti API'si:**  <xref:System.Windows.Markup.IXamlTypeResolver.Resolve%2A>  
  
 XAML yazan bir CLR nesnesi bir nesne grafiğinin içinde yapılandırdığında, gerekli olan XAML CLR türü eşlemesi etkileyebilir. <xref:System.Windows.Markup.IXamlTypeResolver.Resolve%2A>XAML tür adı için karşılık gelen olası önek tam bir dizeyi işlediğinde (<xref:System.Xaml.XamlType.Name%2A?displayProperty=nameWithType>) ve bir CLR döndürür <xref:System.Type>. Türü çözülürken genellikle XAML şema içeriği yoğun bir şekilde bağlıdır. Yalnızca XAML şema içeriği hangi derlemelerin yüklü olduğundan ve bu derlemeler hangisinin olabilir veya türü çözümlemesi için erişilmesi gereken gibi hususlara bilmez.  
  
### <a name="iuricontext"></a>IUriContext  
 **Başvuru belgelerini**:<xref:System.Windows.Markup.IUriContext>  
  
 **Tanımlanır:** <xref:System.Windows.Markup> ad alanı, System.Xaml derleme    
  
 **İlgili:** yükleme yolunu ve yol işleme URI'ler üye değerleri kaydedin veya `x:Uri` değerleri.  
  
 **Hizmeti API'si:**  <xref:System.Windows.Markup.IUriContext.BaseUri%2A>  
  
 Bu hizmeti genel olarak kullanılabilir bir URI kökü varsa bildirir. URI Kökü göreli URI mutlak URI (veya tersi) gidermek için kullanılabilir. Bu senaryo, belirli bir çerçeve ya da bir çerçeve sık kullanılan kök öğe sınıfında yeteneklerini tarafından sunulan uygulama hizmetlerini esas geçerlidir. Taban URI sonra için XAML nesne yazıcısı geçtiğini ve bu hizmet tarafından raporlanan ayarı bir XAML okuyucu olarak kurulur.  
  
### <a name="iambientprovider"></a>IAmbientProvider  
 **Başvuru belgelerini**:<xref:System.Xaml.IAmbientProvider>  
  
 **Tanımlanır:** <xref:System.Xaml> ad alanı, System.Xaml derleme    
  
 **İlgili:** yolu işleme ve türü arama deferrals veya en iyi duruma getirme yükleme.  
  
 **Hizmet API'leri:**<xref:System.Xaml.IAmbientProvider.GetAllAmbientValues%2A>, diğerleri 3.    
  
 XAML'de çevre kavram, belirli bir tür ortam olarak üyesi işaretlemek için kullanılan bir tekniktir. Alternatif olarak, böylece türünün bir örneğini barındıran tüm özellik değerlerini ortam özelliklerine gerekenlerin bir türü ortam olabilir. Biçimlendirme uzantıları veya XAML düğümü akışı başka ve nesne grafikte alt öğeleri olan tür dönüştürücüleri ortam özelliği veya türü örneği yükleme zamanında erişebilir; veya zaman kazandırır ortam yapısı bilgisi kullanabilirsiniz. Bu diğer hizmetler için türleri gibi çözmek için gerekli nitelik derecesini etkileyebilir <xref:System.Windows.Markup.IXamlTypeResolver> veya `x:Type`. Ayrıca bkz. <xref:System.Xaml.AmbientPropertyValue>.  
  
### <a name="ixamlschemacontextprovider"></a>IXamlSchemaContextProvider  
 **Başvuru belgelerini**:<xref:System.Xaml.IXamlSchemaContextProvider>  
  
 **Tanımlanır:** <xref:System.Xaml> ad alanı, System.Xaml derleme    
  
 **İlgili:** yükleme yolunu ve XAML türü için bir yedekleme türü çözülmelidir herhangi bir işlem.  
  
 **Hizmeti API'si:**  <xref:System.Xaml.IXamlSchemaContextProvider.SchemaContext%2A>  
  
 Aynı şema bağlamı ertelenmiş içerik bütünleşmek için ertelenmiş alan davranmalıdır nedeniyle XAML şema içeriği defer yükleme işlemleri için gereklidir. XAML şema içeriği rolü hakkında daha fazla bilgi için bkz: [XAML Hizmetleri](../../../docs/framework/xaml-services/index.md).  
  
### <a name="irootobjectprovider"></a>IRootObjectProvider  
 **Başvuru belgelerini**:<xref:System.Xaml.IRootObjectProvider>  
  
 **Tanımlanır:** <xref:System.Xaml> ad alanı, System.Xaml derleme    
  
 **İlgili:** yükleme yolu.  
  
 **Hizmeti API'si:**  <xref:System.Xaml.IRootObjectProvider.RootObject%2A>  
  
 Hizmet çerçevesi sık kullanılan kök öğe sınıfında özelliklerini veya belirli bir çerçeve tarafından gösterilen uygulama hizmetleri için geçerlidir. Kök nesnede alma bir senaryo, arka plan kod ve olay kablolama bağlanıyor. Örneğin, WPF uygulaması `x:Class` kullanılan biçimlendirmesi derleme ve XAML biçimlendirme içinde başka bir konumda bulunan herhangi bir olay işleyicisi öznitelik kablolama. Biçimlendirme derleme kök öğe için bağlantı noktası biçimlendirme ve arka plan kodu kısmi sınıflar tanımlanan.  
  
### <a name="ixamlnamespaceresolver"></a>IXamlNamespaceResolver  
 **Başvuru belgelerini**:<xref:System.Xaml.IXamlNamespaceResolver>  
  
 **Tanımlanır:** <xref:System.Xaml> ad alanı, System.Xaml derleme    
  
 **İlgili:** kaydetme yolu yükleme yolu.  
  
 **Hizmeti API'si:** <xref:System.Xaml.IXamlNamespaceResolver.GetNamespace%2A> yükleme yolu için <xref:System.Xaml.IXamlNamespaceResolver.GetNamespacePrefixes%2A> için kaydetme yolu.  
  
 <xref:System.Xaml.IXamlNamespaceResolver>XAML ad alanı tanımlayıcı döndürebilirsiniz hizmetidir / URI kaynak XAML biçimlendirme eşlenmiş olarak kendi ön ekini temel alarak.  
  
### <a name="iprovidevaluetarget"></a>IProvideValueTarget  
 **Başvuru belgelerini**:<xref:System.Windows.Markup.IProvideValueTarget>  
  
 **Tanımlanır:** <xref:System.Windows.Markup> ad alanı, System.Xaml derleme    
  
 **İlgili:** yükleme yolunu ve yol kaydedin.  
  
 **Hizmet API'leri:**<xref:System.Windows.Markup.IProvideValueTarget.TargetObject%2A>, <xref:System.Windows.Markup.IProvideValueTarget.TargetProperty%2A>.    
  
 <xref:System.Windows.Markup.IProvideValueTarget>Yükleme zamanında davrandığı hakkında bağlamı elde etmek bir türü dönüştürücü veya işaretleme uzantısı sağlar. Uygulamaları bu bağlamda bir kullanımı geçersiz kılmak için kullanabilirsiniz. Örneğin, WPF içinde bazı biçimlendirme uzantıları mantığı gibi varsa <xref:System.Windows.DynamicResourceExtension>. Mantık denetimlerini <xref:System.Windows.Markup.IProvideValueTarget.TargetProperty%2A> uzantısı bağımlılık özellikleri (veya diğer bağımlılık olmayan özellikleri kısa bir listesi) ayarlamak için yalnızca kullanıldığından emin olmak için.  
  
### <a name="ixamlnameresolver"></a>IXamlNameResolver  
 **Başvuru belgelerini**:<xref:System.Xaml.IXamlNameResolver>  
  
 **Tanımlanır:** <xref:System.Xaml> ad alanı, System.Xaml derleme    
  
 **İlgili:** tarafından tanımlanan nesneler çözme yükleme yolu nesne grafik tanımı, `x:Name`, `x:Reference`, veya çerçeveye özel teknikleri.  
  
 **Hizmet API'leri:**<xref:System.Xaml.IXamlNameResolver.Resolve%2A>; İleri başvuruları yapılacağı gibi daha Gelişmiş senaryolar için diğer API'leri.    
  
 .NET Framework XAML hizmetlerinde uyarlamasını `x:Reference` işleme bu hizmete dayanır. Belirli çerçeveleri veya çerçevesini destekleyen araçlarını kullanmanız bu hizmet için `x:Name` işleme veya eşdeğer bir gruba (<xref:System.Windows.Markup.RuntimeNamePropertyAttribute> öznitelikli) özelliği işleme.  
  
### <a name="idestinationtypeprovider"></a>IDestinationTypeProvider  
 **Başvuru belgelerini**:<xref:System.Xaml.IDestinationTypeProvider>  
  
 **Tanımlanır:** <xref:System.Xaml> ad alanı, System.Xaml derleme    
  
 **İlgili:** yük dolaylı CLR türü bilgileri yolu çözünürlüğü.  
  
 **Hizmeti API'si:**<xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A>  
  
 Daha fazla bilgi için bkz. <xref:System.Xaml.IDestinationTypeProvider>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Markup.MarkupExtension>  
 <xref:System.Xaml.XamlObjectWriter>  
 [Biçimlendirme XAML uzantılarına genel bakış](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md)  
 [XAML genel bakış için tür dönüştürücüleri](../../../docs/framework/xaml-services/type-converters-for-xaml-overview.md)
