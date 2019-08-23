---
title: WPF'den System.Xaml'e Geçirilen Türler
ms.date: 03/30/2017
helpviewer_keywords:
- WPF XAML [XAML Services], migration to System.Xaml
- XAML [XAML Services], System.Xaml and WPF
- System.Xaml [XAML Services], types migrated from WPF
ms.assetid: d79dabf5-a2ec-4e8d-a37a-67c4ba8a2b91
ms.openlocfilehash: 943cdb2a21cbf2f95ef7fe2feefe6c0e71f57be4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939678"
---
# <a name="types-migrated-from-wpf-to-systemxaml"></a>WPF'den System.Xaml'e Geçirilen Türler
.NET Framework 3,5 ve .NET Framework 3,0 ' de, [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] hem hem de Windows Workflow Foundation xaml dil uygulamasına dahil edilmiştir. WPF XAML uygulaması için genişletilebilirlik sağlayan genel türlerin birçoğu WindowsBase, PresentationCore ve PresentationFramework derlemelerinde vardı. Benzer şekilde, Windows Workflow Foundation XAML için genişletilebilirlik sağlayan genel türler System. Workflow. ComponentModel derlemesinde vardı. .NET Framework 4 ' te, XAML ile ilgili türlerden bazıları System. xaml derlemesine geçirilir. XAML dil hizmetlerinin yaygın bir .NET Framework uygulanması, ilk olarak belirli bir Framework 'ün XAML uygulamasına göre tanımlanan ancak artık genel .NET Framework 4 XAML dil desteğinin bir parçası olan çok sayıda XAML genişletilebilirlik senaryosunu mümkün bir şekilde sunar. Bu konu, geçirilen türleri listeler ve geçişle ilgili sorunları açıklar.  
  
<a name="assemblies_and_namespaces"></a>   
## <a name="assemblies-and-namespaces"></a>Derlemeler ve ad alanları  
 .NET Framework 3,5 ve .NET Framework 3,0 ' de, WPF 'nin xaml 'yi desteklemek için uyguladığı türler genellikle <xref:System.Windows.Markup> ad alanında yer alan. Bu türlerin çoğu WindowsBase derlemesinde vardı.  
  
 .NET Framework 4 ' te, yeni <xref:System.Xaml> bir ad alanı ve yeni bir System. Xaml derlemesi vardır. WPF XAML için başlangıçta uygulanan türlerin çoğu, artık XAML uygulamaları için genişletilebilirlik noktaları veya hizmetleri olarak sunulmaktadır. Bunların daha genel senaryolar için kullanılabilir hale getirilmesi kapsamında türler, orijinal WPF derlemelerinden System. xaml derlemesine iletilir. Bu, diğer çerçevelerin derlemelerini (WPF ve Windows Workflow Foundation) dahil etmek zorunda kalmadan XAML genişletilebilirlik senaryolarına olanak sağlar.  
  
 Geçirilen türler için, türlerin çoğu <xref:System.Windows.Markup> ad alanında kalır. Bu, bir dosya temelinde mevcut uygulamalarda CLR ad alanı eşlemelerini bozmamak için kısmen oldu. Sonuç olarak, <xref:System.Windows.Markup> .NET Framework 4 ' teki ad alanı, genel xaml dil destek türlerinin (System. Xaml derlemesinden) ve WPF XAML uygulamasına özgü türlerin (WindowsBase ve diğer WPF derlemelerinden) bir karışımını içerir. System. xaml 'e geçirilmiş ancak daha önce bir WPF derlemesinde bulunan herhangi bir tür, WPF derlemesinin sürüm 4 ' te tür iletme desteğine sahiptir.  
  
### <a name="workflow-xaml-support-types"></a>Workflow XAML destek türleri  
 Windows Workflow Foundation Ayrıca XAML destek türleri de sağlamıştır ve birçok durumda, benzer kısa adlara sahip bir WPF eşdeğeri vardır. Windows Workflow Foundation XAML destek türlerinin bir listesi aşağıda verilmiştir:  
  
- <xref:System.Workflow.ComponentModel.Serialization.ContentPropertyAttribute>  
  
- <xref:System.Workflow.ComponentModel.Serialization.RuntimeNamePropertyAttribute>  
  
- <xref:System.Workflow.ComponentModel.Serialization.XmlnsPrefixAttribute>  
  
 Bu destek türleri, .NET Framework 4 için Windows Workflow Foundation derlemelerinden hala bulunur ve belirli Windows Workflow Foundation uygulamaları için yine de kullanılabilir; Ancak, bunlara Windows Workflow Foundation kullanmayan uygulamalar veya çerçeveler tarafından başvurulmamalıdır.  
  
<a name="markupextension"></a>   
## <a name="markupextension"></a>MarkupExtension  
 .NET Framework 3,5 ve .NET Framework 3,0 ' de, <xref:System.Windows.Markup.MarkupExtension> WPF sınıfı WindowsBase derlemeiydi. System. Workflow. ComponentModel derlemesinde <xref:System.Workflow.ComponentModel.Serialization.MarkupExtension>vardı Windows Workflow Foundation için paralel bir sınıf. .NET Framework 4 ' te, <xref:System.Windows.Markup.MarkupExtension> sınıfı System. xaml derlemesine geçirilir. .NET Framework 4 ' te, <xref:System.Windows.Markup.MarkupExtension> yalnızca belirli çerçeveler üzerinde derleme için değil, .NET Framework xaml Hizmetleri kullanan xaml genişletilebilirlik senaryosuna yöneliktir. Mümkün olduğunda, çerçevede belirli çerçeveler veya Kullanıcı kodu xaml uzantısı için <xref:System.Windows.Markup.MarkupExtension> sınıf üzerinde de derleme sağlamalıdır.  
  
<a name="markupextension_supporting_service_classes"></a>   
## <a name="markupextension-supporting-service-classes"></a>Hizmet sınıflarını destekleyen MarkupExtension  
 WPF için .NET Framework 3,5 ve .NET Framework 3,0, XAML 'de tür/özellik kullanımını <xref:System.Windows.Markup.MarkupExtension> desteklemek üzere <xref:System.ComponentModel.TypeConverter> uygulayıcıları ve uygulamalar tarafından kullanılabilen çeşitli hizmetler sağladı. Bu hizmetler şunlardır:  
  
- <xref:System.Windows.Markup.IProvideValueTarget>  
  
- <xref:System.Windows.Markup.IUriContext>  
  
- <xref:System.Windows.Markup.IXamlTypeResolver>  
  
> [!NOTE]
> Biçimlendirme uzantılarıyla <xref:System.Windows.Markup.IReceiveMarkupExtension> ilgili olan .NET Framework 3,5 ' den başka bir hizmet arabirimidir. <xref:System.Windows.Markup.IReceiveMarkupExtension>taşınmadı ve .NET Framework 4 için işaretlendi `[Obsolete]` . Daha önce kullanılan <xref:System.Windows.Markup.IReceiveMarkupExtension> senaryolar bunun yerine öznitelikli <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute> geri çağırmaları kullanmalıdır. <xref:System.Windows.Markup.AcceptedMarkupExtensionExpressionTypeAttribute>de işaretlenir `[Obsolete]`.  
  
<a name="xaml_language_features"></a>   
## <a name="xaml-language-features"></a>XAML dil özellikleri  
 Daha önce PresentationFramework derlemesinde bulunan WPF için birkaç XAML dil özelliği ve bileşeni var. Bunlar xaml biçimlendirmesinde biçimlendirme uzantısı <xref:System.Windows.Markup.MarkupExtension> kullanımlarını göstermek için bir alt sınıf olarak uygulandı. .NET Framework 4 ' te, WPF derlemeleri içermeyen projelerin bu XAML dil düzeyi özelliklerini kullanabilmesi için System. xaml derlemesinde bulunur. WPF, .NET Framework 4 uygulamaları için aynı uygulamaları kullanır. Bu konuda listelenen diğer durumlarda olduğu gibi, önceki başvuruların kesilmesini önlemek için destekleyici türler <xref:System.Windows.Markup> ad alanında mevcut olmaya devam eder.  
  
 Aşağıdaki tablo, System. xaml içinde tanımlanan XAML özellik desteği sınıflarının bir listesini içerir.  
  
|XAML dil özelliği|Kullanım|  
|---------------------------|-----------|  
|<xref:System.Windows.Markup.ArrayExtension>|`<x:Array ...>`|  
|<xref:System.Windows.Markup.NullExtension>|`{x:Null}`|  
|<xref:System.Windows.Markup.StaticExtension>|`{x:Static ...}`|  
|<xref:System.Windows.Markup.TypeExtension>|`{x:Type ...}`|  
  
 System. xaml belirli destek sınıflarına sahip olmayabilir, ancak XAML dilinin dil özelliklerini işlemek için genel mantık artık System. xaml ve uygulanan XAML okuyucuları ve XAML yazarları içinde bulunur. Örneğin, `x:TypeArguments` System. xaml uygulamalarından xaml okuyucuları ve XAML yazarları tarafından işlenen bir özniteliktir; xaml düğüm akışında, varsayılan (clr tabanlı) xaml şeması bağlamında işleme sahip olan bir xaml türü-sistemine sahip olabilir. temsili vb. Sonuç olarak, tüm XAML dil düzeyi özelliklerine ilişkin başvuru belgeleri, bir alt konu olarak (örneğin, WPF belgelerinin bir parçası olarak ayarlanan), bir [xaml Hizmetleri](index.md) ve .NET Framework belge kümesinin genel alanı için bir alt konudur [( Windows Presentation Foundation)](../wpf/advanced/index.md) (yine de 3,5 belge kümelerinde olduğu gibi).  
  
<a name="valueserializer_and_supporting_classes"></a>   
## <a name="valueserializer-and-supporting-classes"></a>ValueSerializer ve destekleme sınıfları  
 <xref:System.Windows.Markup.ValueSerializer> Sınıfı, özellikle serileştirme 'in çıktıda birden çok mod veya düğüm gerektirebileceği XAML serileştirme durumları için bir dizeye tür dönüştürmeyi destekler. .NET Framework 3,5 ve .NET Framework 3,0 ' <xref:System.Windows.Markup.ValueSerializer> de, WPF için WindowsBase derlemesi vardı. .NET Framework 4 ' te, <xref:System.Windows.Markup.ValueSerializer> sınıfı System. xaml içinde bulunur ve yalnızca WPF üzerinde derleme için değil xaml genişletilebilirlik senaryosuna yöneliktir. <xref:System.Windows.Markup.IValueSerializerContext>(bir destekleme hizmeti) ve <xref:System.Windows.Markup.DateTimeValueSerializer> (belirli bir alt sınıf) System. xaml 'e de geçirilir.  
  
<a name="xamlrelated_attributes"></a>   
## <a name="xaml-related-attributes"></a>XAML ile Ilgili öznitelikler  
 WPF XAML, XAML davranışları hakkında bir şeyi göstermek üzere CLR türlerine uygulanabilecek birkaç özniteliği içeriyordu. Aşağıda .NET Framework 3,5 ve .NET Framework 3,0 ' deki WPF derlemelerindeki özniteliklerin bir listesi verilmiştir. Bu öznitelikler .NET Framework 4 ' te System. xaml 'e geçirilir.  
  
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
## <a name="miscellaneous-classes"></a>Çeşitli sınıflar  
 <xref:System.Windows.Markup.IComponentConnector> Arabirim, 3,5 .NET Framework ve 3,0 .NET Framework ' de WindowsBase 'de vardı, ancak .NET Framework 4 ' te System. xaml içinde var. <xref:System.Windows.Markup.IComponentConnector>Öncelikle araç desteği ve XAML biçimlendirme derleyicileri için tasarlanmıştır.  
  
 <xref:System.Windows.Markup.INameScope> Arabirim, 3,5 .NET Framework ve 3,0 .NET Framework ' de WindowsBase 'de vardı, ancak .NET Framework 4 ' te System. xaml içinde var. <xref:System.Windows.Markup.INameScope>XAML namescope için temel işlemleri tanımlar.  
  
<a name="xamlrelated_classes_with_shared_names_that_exist_in_wpf_and_systemxaml"></a>   
## <a name="xaml-related-classes-with-shared-names-that-exist-in-wpf-and-systemxaml"></a>WPF ve System. xaml 'de bulunan paylaşılan adlara sahip XAML ile ilgili sınıflar  
 Aşağıdaki sınıflar hem WPF derlemelerinde hem de .NET Framework 4 ' te System. xaml derlemesinde mevcuttur:  
  
 `XamlReader`  
  
 `XamlWriter`  
  
 `XamlParseException`  
  
 WPF uygulama, <xref:System.Windows.Markup> ad alanında ve PresentationFramework derlemesinde bulunur. System. xaml uygulama <xref:System.Xaml> ad alanında bulunur. WPF türlerini kullanıyorsanız veya WPF türlerinden türetiliyorsanız, System. xaml uygulamaları yerine genellikle ve <xref:System.Windows.Markup.XamlReader> <xref:System.Windows.Markup.XamlWriter> ' nin WPF uygulamalarını kullanmanız gerekir. Daha fazla bilgi için ve <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> <xref:System.Windows.Markup.XamlWriter?displayProperty=nameWithType>içindeki açıklamalar bölümüne bakın.  
  
 Hem WPF derlemelerine hem de System. xaml 'e başvurular dahil ediyorsanız ve `include` <xref:System.Windows.Markup> hem <xref:System.Xaml> hem de ad alanları için deyimler kullanıyorsanız, türleri çözümlemek için bu API 'lerin çağrılarını tamamen nitelemeniz gerekebilir belirsizlik olmadan.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XAML Hizmetleri](index.md)
