---
title: WPF'den System.Xaml'e Geçirilen Türler
ms.date: 03/30/2017
helpviewer_keywords:
- WPF XAML [XAML Services], migration to System.Xaml
- XAML [XAML Services], System.Xaml and WPF
- System.Xaml [XAML Services], types migrated from WPF
ms.assetid: d79dabf5-a2ec-4e8d-a37a-67c4ba8a2b91
ms.openlocfilehash: 5aa2d8a39be47d9affb97c3b60e53c4722c63cce
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249804"
---
# <a name="types-migrated-from-wpf-to-systemxaml"></a>WPF'den System.Xaml'a geçirilen türler

.NET Framework 3.5 ve .NET Framework 3.0'da hem Windows Presentation Foundation (WPF) hem de Windows İş Akışı Vakfı bir XAML dil uygulaması içeriyordu. WPF XAML uygulaması için genişletilebilirlik sağlayan ortak türlerin çoğu WindowsBase, PresentationCore ve PresentationFramework derlemelerinde mevcuttı. Aynı şekilde, System.Workflow.ComponentModel derlemesinde Windows İş Akışı Temeli XAML için genişletilebilirlik sağlayan ortak türler de vardı. .NET Framework 4'te, XAML ile ilgili bazı türler System.Xaml derlemesine geçirilmiştir. XAML dil hizmetlerinin ortak bir .NET Framework uygulaması, başlangıçta belirli bir çerçevenin XAML uygulaması tarafından tanımlanan ancak şimdi genel .NET Framework 4 XAML dil desteğinin bir parçası olan birçok XAML genişletilebilirlik senaryosuna olanak tanır. Bu makalede, geçirilen türleri listeler ve geçişle ilgili sorunları tartışır.

## <a name="assemblies-and-namespaces"></a>Derlemeler ve İsim Boşlukları

.NET Framework 3.5 ve .NET Framework 3.0'da, WPF'nin XAML'yi desteklemek için uyguladığı türler genellikle <xref:System.Windows.Markup> ad alanındaydı. Bu türlerin çoğu WindowsBase derlemesindeydi.

.NET Framework 4'te yeni <xref:System.Xaml> bir ad alanı ve yeni system.Xaml derlemesi vardır. Başlangıçta WPF XAML için uygulanan türlerin çoğu artık XAML herhangi bir uygulama için genişletilebilirlik noktaları veya hizmetleri olarak sağlanmaktadır. Bunları daha genel senaryolar için kullanılabilir hale getirmenin bir parçası olarak, türleri orijinal WPF derlemelerinden System.Xaml derlemesine tür iletilen dir. Bu, diğer çerçevelerin derlemelerini (WPF ve Windows İş Akışı Temeli gibi) dahil etmek zorunda kalmadan XAML genişletilebilirlik senaryolarını sağlar.

Geçirilen türler için, türlerin çoğu <xref:System.Windows.Markup> ad alanında kalır. Bu kısmen, dosya başına varolan uygulamalardaki CLR ad alanı eşlemelerini kırmayı önlemek içindi. Sonuç olarak, <xref:System.Windows.Markup> .NET Framework 4'teki ad alanı, genel XAML dil destek türlerinin (System.Xaml derlemesinden) ve WPF XAML uygulamasına (WindowsBase ve diğer WPF derlemelerinden) özgü türlerin in bir karışımını içerir. System.Xaml'a geçirilen, ancak daha önce bir WPF derlemesinde bulunan herhangi bir tür, WPF derlemesinin sürüm 4'ünde tür iletme desteğine sahiptir.

### <a name="workflow-xaml-support-types"></a>İş Akışı XAML Destek Türleri

Windows İş Akışı Temeli de XAML destek türleri sağladı ve çoğu durumda bu bir WPF eşdeğeri aynı kısa adlara sahipti. Aşağıda Windows İş Akışı Temeli XAML destek türlerinin bir listesi verilmiştir:

- <xref:System.Workflow.ComponentModel.Serialization.ContentPropertyAttribute>

- <xref:System.Workflow.ComponentModel.Serialization.RuntimeNamePropertyAttribute>

- <xref:System.Workflow.ComponentModel.Serialization.XmlnsPrefixAttribute>

Bu destek türleri ,NET Framework 4 için Windows İş Akışı Temel derlemelerinde hala mevcuttur ve belirli Windows İş Akışı Temeli uygulamaları için kullanılabilir; ancak, Windows İş Akışı Temeli'ni kullanmayan uygulamalar veya çerçeveler tarafından başvurulmamalıdır.

## <a name="markupextension"></a>MarkupExtension

.NET Framework 3.5 ve .NET Framework 3.0'da WPF <xref:System.Windows.Markup.MarkupExtension> sınıfı WindowsBase derlemesindeydi. System.Workflow.ComponentModel derlemesinde Windows İş Akışı Temeli <xref:System.Workflow.ComponentModel.Serialization.MarkupExtension>için paralel bir sınıf bulunmaktadır. .NET Framework 4'te <xref:System.Windows.Markup.MarkupExtension> sınıf System.Xaml derlemesine geçirilir. .NET Framework 4'te, yalnızca belirli çerçeveler üzerinde inşa edenler için değil, <xref:System.Windows.Markup.MarkupExtension> .NET XAML Hizmetlerini kullanan herhangi bir XAML genişletilebilirlik senaryosu için tasarlanmıştır. Mümkün olduğunda, çerçevedeki belirli çerçeveler veya kullanıcı <xref:System.Windows.Markup.MarkupExtension> kodu da XAML uzantısı için sınıf üzerine inşa etmelidir.

## <a name="markupextension-supporting-service-classes"></a>Biçimlendirme Destek Hizmeti Sınıfları

.NET Framework 3.5 ve .NET Framework 3.0 WPF <xref:System.Windows.Markup.MarkupExtension> için XAML'de tür/özellik kullanımını desteklemek için uygulayıcılar ve <xref:System.ComponentModel.TypeConverter> uygulamalar için kullanılabilen çeşitli hizmetler sağlamıştır. Bu hizmetler şunlardır:

- <xref:System.Windows.Markup.IProvideValueTarget>

- <xref:System.Windows.Markup.IUriContext>

- <xref:System.Windows.Markup.IXamlTypeResolver>

> [!NOTE]
> .NET Framework 3.5'in biçimlendirme uzantılarıyla ilgili <xref:System.Windows.Markup.IReceiveMarkupExtension> bir diğer hizmeti de arabirimidir. <xref:System.Windows.Markup.IReceiveMarkupExtension>geçirilemedi ve .NET Framework 4 için işaretlenmiştir. `[Obsolete]` Daha önce kullanılan <xref:System.Windows.Markup.IReceiveMarkupExtension> senaryolar <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute> bunun yerine atfedilen geri aramaları kullanmalıdır. <xref:System.Windows.Markup.AcceptedMarkupExtensionExpressionTypeAttribute>da işaretlenir. `[Obsolete]`

## <a name="xaml-language-features"></a>XAML Dil Özellikleri

WPF için daha önce PresentationFramework derlemesinde çeşitli XAML dil özellikleri ve bileşenleri vardı. Bunlar, XAML <xref:System.Windows.Markup.MarkupExtension> biçimlendirmesinde biçimlendirme uzantısı kullanımlarını ortaya çıkarmak için bir alt sınıf olarak uygulanmıştır. .NET Framework 4'te, WPF derlemelerini içermeyen projelerin bu XAML dil düzeyi özelliklerini kullanabilmesi için System.Xaml derlemesinde bulunur. WPF, .NET Framework 4 uygulamaları için de aynı uygulamaları kullanır. Bu konuda listelenen diğer durumlarda olduğu gibi, önceki başvuruları kırmayı <xref:System.Windows.Markup> önlemek için destek türleri ad alanında var olmaya devam edin.

Aşağıdaki tablo, System.Xaml'da tanımlanan XAML özellik destek sınıflarının bir listesini içerir.

|XAML Dil Özelliği|Kullanım|
|---------------------------|-----------|
|<xref:System.Windows.Markup.ArrayExtension>|`<x:Array ...>`|
|<xref:System.Windows.Markup.NullExtension>|`{x:Null}`|
|<xref:System.Windows.Markup.StaticExtension>|`{x:Static ...}`|
|<xref:System.Windows.Markup.TypeExtension>|`{x:Type ...}`|

System.Xaml belirli destek sınıfları olmayabilir, XAML dili için dil özelliklerini işlemek için genel mantık şimdi System.Xaml ve uygulanan XAML okuyucuları ve XAML yazarları bulunur. Örneğin, `x:TypeArguments` System.Xaml uygulamalarından XAML okuyucuları ve XAML yazarları tarafından işlenen bir özniteliktir; XAML düğüm akışında belirtilebilir, varsayılan (CLR tabanlı) XAML şema bağlamında işleme vardır, XAML tipi sistem gösterimi vardır, vb. Sonuç olarak, tüm XAML dil düzeyi özellikleri için başvuru [belgeleri, Windows Sunum Foundation (WPF) için Masaüstü Kılavuzu'ndaki](../../../desktop-wpf/overview/index.md) [XAML Hizmetleri](../../../desktop-wpf/xaml-services/index.md) için bir alt konudur.

## <a name="valueserializer-and-supporting-classes"></a>ValueSerializer ve Destekleyici Sınıflar

Sınıf, <xref:System.Windows.Markup.ValueSerializer> özellikle serileştirmenin çıktıda birden çok mod veya düğüm gerektirebileceği XAML serileştirme örnekleri için bir dize tür dönüştürmeyi destekler. .NET Framework 3.5 ve .NET Framework <xref:System.Windows.Markup.ValueSerializer> 3.0'da WPF için WindowsBase derlemesi vardı. .NET Framework 4'te <xref:System.Windows.Markup.ValueSerializer> sınıf System.Xaml'dadır ve sadece WPF'yi oluşturanlar için değil, herhangi bir XAML genişletilebilirlik senaryosu için tasarlanmıştır. <xref:System.Windows.Markup.IValueSerializerContext>(destekleyici bir hizmet) <xref:System.Windows.Markup.DateTimeValueSerializer> ve (belirli bir alt sınıf) da System.Xaml'a geçirilir.

## <a name="xaml-related-attributes"></a>XAML ile ilgili öznitelikler

WPF XAML, XAML davranışları hakkında bir şey belirtmek için CLR türlerine uygulanabilecek çeşitli öznitelikler içeriyordu. Aşağıda.NET Framework 3.5 ve .NET Framework 3.0'daki WPF derlemelerinde bulunan özniteliklerin bir listesi vebu özellikler yer almaktadır. Bu öznitelikler System.Xaml için .NET Framework 4 geçirilir.

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

## <a name="miscellaneous-classes"></a>Çeşitli Sınıflar

Arayüz <xref:System.Windows.Markup.IComponentConnector> WindowsBase'de .NET Framework 3.5 ve .NET Framework 3.0'da mevcut, ancak System.Xaml'da .NET Framework 4'te bulunmaktadır. <xref:System.Windows.Markup.IComponentConnector>öncelikle araç desteği ve XAML biçimlendirme derleyicileri için tasarlanmıştır.

Arayüz <xref:System.Windows.Markup.INameScope> WindowsBase'de .NET Framework 3.5 ve .NET Framework 3.0'da mevcut, ancak System.Xaml'da .NET Framework 4'te bulunmaktadır. <xref:System.Windows.Markup.INameScope>Bir XAML adskopu için temel işlemleri tanımlar.

## <a name="xaml-related-classes-with-shared-names-that-exist-in-wpf-and-systemxaml"></a>WPF ve System.Xaml'da Bulunan Paylaşılan Adlarla XAML ile ilgili Sınıflar

Aşağıdaki sınıflar hem WPF derlemelerinde hem de System.Xaml derlemesinde .NET Framework 4'te bulunur:

`XamlReader`

`XamlWriter`

`XamlParseException`

WPF uygulaması ad alanında <xref:System.Windows.Markup> ve PresentationFramework derlemesinde bulunur. System.Xaml uygulaması <xref:System.Xaml> ad alanında bulunur. WPF türleri kullanıyorsanız veya WPF türlerinden türeyen iseniz, genellikle System.Xaml uygulamaları yerine <xref:System.Windows.Markup.XamlReader> <xref:System.Windows.Markup.XamlWriter> WPF uygulamalarını kullanmanız gerekir. Daha fazla bilgi için <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> <xref:System.Windows.Markup.XamlWriter?displayProperty=nameWithType>Bkz. Açıklamalar ve .

Hem WPF derlemelerine hem de System.Xaml'a başvurular da `include` dahil ediyorsanız <xref:System.Windows.Markup> <xref:System.Xaml> ve hem ad alanları hem de ad alanları için ifadeler kullanıyorsanız, türleri belirsizlik olmadan çözmek için bu API'lere yapılan çağrıları tam olarak nitelemeniz gerekebilir.
