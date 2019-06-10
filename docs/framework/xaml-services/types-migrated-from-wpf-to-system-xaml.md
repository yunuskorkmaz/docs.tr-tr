---
title: WPF'den System.Xaml'e Geçirilen Türler
ms.date: 03/30/2017
helpviewer_keywords:
- WPF XAML [XAML Services], migration to System.Xaml
- XAML [XAML Services], System.Xaml and WPF
- System.Xaml [XAML Services], types migrated from WPF
ms.assetid: d79dabf5-a2ec-4e8d-a37a-67c4ba8a2b91
ms.openlocfilehash: 37433768c1bca3c013fb1e505d55bd7295f34933
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758019"
---
# <a name="types-migrated-from-wpf-to-systemxaml"></a>WPF'den System.Xaml'e Geçirilen Türler
.NET Framework 3.5 ve .NET Framework 3. 0'da, her ikisi de [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] ve Windows Workflow Foundation XAML dil uygulaması eklenir. Birçok genişletilebilirlik WPF XAML uygulaması için sağlanan genel tür WindowsBase ve PresentationCore PresentationFramework derlemelerde vardı. Benzer şekilde, Windows Workflow Foundation XAML için genişletilebilirlik sağlayan genel türleri System.Workflow.ComponentModel derlemede vardı. .NET Framework 4'te bazı XAML ile ilgili türleri System.Xaml derlemeye geçirilir. XAML dil Hizmetleri ortak bir .NET Framework uygulamasını ilk olarak belirli bir framework'ün XAML uygulama tarafından tanımlanan, ancak artık .NET Framework 4 XAML dil desteği genel bir parçası olan birçok XAML genişletilebilirlik senaryolara olanak sağlar. Bu konuda, geçirilir ve geçişle ilgili sorunlar ele alınmıştır türlerini listeler.  
  
<a name="assemblies_and_namespaces"></a>   
## <a name="assemblies-and-namespaces"></a>Derlemeler ve ad alanları  
 .NET Framework 3.5 ve .NET Framework 3.0, WPF XAML desteklemek için uygulanan türleri içinde genel olarak <xref:System.Windows.Markup> ad alanı. Bu türlerin çoğu WindowsBase derlemesinde bulunmaktadır.  
  
 .NET Framework 4'te var. yeni bir <xref:System.Xaml> ad alanı ve yeni bir System.Xaml derleme. WPF XAML için ilk olarak uygulanan türleri birçoğu artık genişletilebilirlik noktaları veya herhangi bir XAML uygulaması için hizmet olarak sağlanır. Bunları daha genel senaryolar için kullanılabilir hale getirme bir parçası olarak, türü-kendi özgün WPF derlemesinden System.Xaml derlemesine iletilen türleridir. Bu, XAML genişletilebilirlik senaryoları diğer çerçeveleri (örneğin, WPF ve Windows Workflow Foundation) derlemeleri eklemek zorunda kalmadan sağlar.  
  
 Türlerin çoğu geçirilen türler için kalan <xref:System.Windows.Markup> ad alanı. Bu dosya başına temelinde mevcut uygulamalarında CLR ad uzayı eşlemelerinden bozmayı önlemek için kısmen değildi. Sonuç olarak, <xref:System.Windows.Markup> ad alanı .NET Framework 4'te genel XAML dil desteği türleri (System.Xaml derlemesinden) bir karışımını içeren ve WPF XAML uygulaması için (WindowsBase ve diğer WPF derlemelerine) özgü türleri. System.xaml'e geçirilen, ancak daha önce bir WPF derlemede varolan herhangi bir tür sürüm WPF derleme 4 tür iletme desteği vardır.  
  
### <a name="workflow-xaml-support-types"></a>İş akışı XAML destek türleri  
 Windows Workflow Foundation XAML destek türleri de sağlanır ve çoğu durumda bu eşdeğer WPF özdeş kısa adlarına sahip. Windows Workflow Foundation XAML destek türlerinin bir listesi verilmiştir:  
  
- <xref:System.Workflow.ComponentModel.Serialization.ContentPropertyAttribute>  
  
- <xref:System.Workflow.ComponentModel.Serialization.RuntimeNamePropertyAttribute>  
  
- <xref:System.Workflow.ComponentModel.Serialization.XmlnsPrefixAttribute>  
  
 Belirli Windows Workflow Foundation uygulamaları için kullanılan türleri hala Windows Workflow Foundation derlemeler .NET Framework 4 için mevcut ve hala bu desteği; Ancak, bunlar uygulamaları veya Windows Workflow Foundation'ı kullanmayın çerçeveleri başvurulmaması gereken.  
  
<a name="markupextension"></a>   
## <a name="markupextension"></a>MarkupExtension  
 .NET Framework 3.5 ve .NET Framework 3. 0'da, <xref:System.Windows.Markup.MarkupExtension> WPF WindowsBase derlemesinde için sınıf. Windows Workflow Foundation için paralel bir sınıf <xref:System.Workflow.ComponentModel.Serialization.MarkupExtension>, önceden System.Workflow.ComponentModel derlemedeki. .NET Framework 4'te <xref:System.Windows.Markup.MarkupExtension> sınıfı System.Xaml derlemeye geçirilir. .NET Framework 4'te <xref:System.Windows.Markup.MarkupExtension> yalnızca bu belirli çerçevelerini temel yapı için .NET Framework XAML hizmetlerinde kullanan herhangi bir XAML genişletilebilirlik senaryo için tasarlanmıştır. Mümkün olduğunda, belirli çerçeveleri ya da Framework'te kullanıcı kodu aynı zamanda Sysprep.inf'in <xref:System.Windows.Markup.MarkupExtension> XAML uzantısı için sınıf.  
  
<a name="markupextension_supporting_service_classes"></a>   
## <a name="markupextension-supporting-service-classes"></a>MarkupExtension destekleyen hizmet sınıfları  
 .NET framework 3.5 ve .NET Framework 3. 0'wpf için kullanabileceği birkaç hizmet sağlanan <xref:System.Windows.Markup.MarkupExtension> uygulayıcılar ve <xref:System.ComponentModel.TypeConverter> XAML içinde türü/özellik kullanımı desteklemek için uygulamaları. Bu hizmetler şunlardır:  
  
- <xref:System.Windows.Markup.IProvideValueTarget>  
  
- <xref:System.Windows.Markup.IUriContext>  
  
- <xref:System.Windows.Markup.IXamlTypeResolver>  
  
> [!NOTE]
>  Biçimlendirme uzantıları için ilgili .NET Framework 3.5 başka bir hizmet mi <xref:System.Windows.Markup.IReceiveMarkupExtension> arabirimi. <xref:System.Windows.Markup.IReceiveMarkupExtension> geçirilmemiş ve işaretlenmiş `[Obsolete]` için .NET Framework 4. Daha önce kullanılan senaryoları <xref:System.Windows.Markup.IReceiveMarkupExtension> kullanmalısınız <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute> geri çağırmaları öznitelikli. <xref:System.Windows.Markup.AcceptedMarkupExtensionExpressionTypeAttribute> Ayrıca işaretlenmiş `[Obsolete]`.  
  
<a name="xaml_language_features"></a>   
## <a name="xaml-language-features"></a>XAML dil özellikleri  
 Daha önce birkaç XAML dil özelliklerini ve WPF bileşenlerini PresentationFramework derlemesinde vardı. Bunlar olarak uygulanan bir <xref:System.Windows.Markup.MarkupExtension> XAML biçimlendirmede biçimlendirme uzantısı kullanımı göstermek için alt sınıfı. WPF derlemeleri içermeyen projeler bu XAML dili düzeyinde özellikleri kullanabilmesi için .NET Framework 4'te bu System.Xaml bütünleştirilmiş kodda mevcut. WPF, .NET Framework 4 uygulamaları için aynı bu uygulamalar kullanır. Bu konuda listelenen diğer durumlarda ile destekleyen türler devam mevcut <xref:System.Windows.Markup> önceki başvuruları bozmayı önlemek için ad alanı.  
  
 Aşağıdaki tabloda, System.Xaml içinde tanımlanan XAML özellik desteği sınıfları listesini içerir.  
  
|XAML dil özelliği|Kullanım|  
|---------------------------|-----------|  
|<xref:System.Windows.Markup.ArrayExtension>|`<x:Array ...>`|  
|<xref:System.Windows.Markup.NullExtension>|`{x:Null}`|  
|<xref:System.Windows.Markup.StaticExtension>|`{x:Static ...}`|  
|<xref:System.Windows.Markup.TypeExtension>|`{x:Type ...}`|  
  
 System.Xaml belirli destek sınıfları olmayabilir rağmen XAML dili için dil özellikleri artık işleme için genel mantığı System.Xaml ve uygulanan XAML okuyucular ve yazıcılar XAML içinde yer alıyor. Örneğin, `x:TypeArguments` XAML okuyucular ve System.Xaml uygulamalardan; XAML yazıcılar tarafından işlenen bir özniteliktir, XAML düğüm akış içinde belirtilen, varsayılan (CLR tabanlı) XAML şema içeriği içinde işleme sahip, bir XAML tür sistemi vardır gösterim ve benzeri. Sonuç olarak, tüm XAML dili düzeyinde özellikler için başvuru belgeleri için alt konu olan [XAML Hizmetleri](index.md) ve genel olarak WPF belgeler parçası olmak yerine .NET Framework belgeleri kümesi alanı bir alt konu, [Gelişmiş (Windows Presentation Foundation)](../wpf/advanced/index.md) (yine de 3,5 belge kümeleri durumda olduğu gibi).  
  
<a name="valueserializer_and_supporting_classes"></a>   
## <a name="valueserializer-and-supporting-classes"></a>ValueSerializer ve Destek sınıfları  
 <xref:System.Windows.Markup.ValueSerializer> Sınıfı, özellikle, burada serileştirme gerektirebilir birden çok modları veya düğümleri çıktısında XAML serileştirme çalışmaları için tür dönüştürme bir dizeye destekler. .NET Framework 3.5 ve .NET Framework 3. 0'da, <xref:System.Windows.Markup.ValueSerializer> WPF WindowsBase derlemesinde için. .NET Framework 4'te <xref:System.Windows.Markup.ValueSerializer> sınıfı System.Xaml içinde olan ve herhangi bir XAML genişletilebilirlik senaryo için yalnızca, WPF, derleme için tasarlanmıştır. <xref:System.Windows.Markup.IValueSerializerContext> (bir destek hizmeti) ve <xref:System.Windows.Markup.DateTimeValueSerializer> (belirli bir alt sınıf) System.xaml'e da geçirilir.  
  
<a name="xamlrelated_attributes"></a>   
## <a name="xaml-related-attributes"></a>XAML ile ilgili öznitelikleri  
 WPF XAML CLR türleri, XAML davranışları hakkında bir şey belirtmek için uygulanabilecek bazı öznitelikler dahildir. .NET Framework 3.5 ve .NET Framework 3. 0'ın WPF derlemelerde varolan özniteliklerin bir listesi verilmiştir. Bu öznitelikler, .NET Framework 4'te System.XAML'ye geçirilir.  
  
- <xref:System.Windows.Markup.AmbientAttribute>  
  
- <xref:System.Windows.Markup.ContentPropertyAttribute>  
  
- <xref:System.Windows.Markup.ContentWrapperAttribute>  
  
- <xref:System.Windows.Markup.DependsOnAttribute>  
  
- <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>  
  
- <xref:System.Windows.Markup.NameScopePropertyAttribute>  
  
- <xref:System.Windows.Markup.RootNamespaceAttribute>  
  
- <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>  
  
- <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>  
  
- <xref:System.Windows.Markup.ValueSerializerAttribute>  
  
- <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>  
  
- <xref:System.Windows.Markup.XmlLangPropertyAttribute>  
  
- <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>  
  
- <xref:System.Windows.Markup.XmlnsDefinitionAttribute>  
  
- <xref:System.Windows.Markup.XmlnsPrefixAttribute>  
  
<a name="miscellaneous_classes"></a>   
## <a name="miscellaneous-classes"></a>Çeşitli sınıfları  
 <xref:System.Windows.Markup.IComponentConnector> Arabirimi içinde .NET Framework 3.5 ve .NET Framework 3.0 WindowsBase var, ancak .NET Framework 4'te System.Xaml bulunmaktadır. <xref:System.Windows.Markup.IComponentConnector> öncelikle desteği ve XAML biçimlendirme derleyicileri araç kullanımı için tasarlanmıştır.  
  
 <xref:System.Windows.Markup.INameScope> Arabirimi içinde .NET Framework 3.5 ve .NET Framework 3.0 WindowsBase var, ancak .NET Framework 4'te System.Xaml bulunmaktadır. <xref:System.Windows.Markup.INameScope> temel XAML namescope işlemlerinde tanımlar.  
  
<a name="xamlrelated_classes_with_shared_names_that_exist_in_wpf_and_systemxaml"></a>   
## <a name="xaml-related-classes-with-shared-names-that-exist-in-wpf-and-systemxaml"></a>System.Xaml ve WPF ile mevcut paylaşılan adları ile XAML ile ilgili sınıflar  
 Hem WPF derlemeleri, hem de .NET Framework 4 System.Xaml derlemede aşağıdaki sınıflar mevcut:  
  
 `XamlReader`  
  
 `XamlWriter`  
  
 `XamlParseException`  
  
 WPF uygulaması bulunan <xref:System.Windows.Markup> ad alanını ve PresentationFramework derleme. System.Xaml uygulaması bulunan <xref:System.Xaml> ad alanı. WPF türleri kullanarak ya da WPF türlerden türetilen, WPF uygulamaları kullanmalısınız <xref:System.Windows.Markup.XamlReader> ve <xref:System.Windows.Markup.XamlWriter> System.Xaml uygulamaları yerine. Daha fazla bilgi için konusundaki yorumlara bakın <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> ve <xref:System.Windows.Markup.XamlWriter?displayProperty=nameWithType>.  
  
 System.Xaml ve WPF derlemelerine başvurular dahil olmak üzere ve ayrıca kullanmakta olduğunuz `include` hem deyimleri <xref:System.Windows.Markup> ve <xref:System.Xaml> ad alanlarını, türleri çözümlemek için bu API çağrıları tam olarak nitelemek gerekebilir belirsizlik.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XAML Hizmetleri](index.md)
