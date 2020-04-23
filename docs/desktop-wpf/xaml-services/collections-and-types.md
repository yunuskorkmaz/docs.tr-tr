---
title: XAML Koleksiyonları ve Koleksiyon Türleri
ms.date: 03/30/2017
ms.assetid: 58f8e7c6-9a41-4f25-8551-c042f1315baa
ms.openlocfilehash: 2ec58026c605df31489c8aab4c4cc714dab11474
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "82071299"
---
# <a name="collections-and-collection-types-for-xaml"></a>XAML için koleksiyonlar ve koleksiyon türleri

Bu makalede, bir koleksiyonu desteklemek için amaçlanan türlerin özelliklerinin nasıl tanımlanılıştırılması ve koleksiyon öğelerini bir üst nesne öğesi nin veya özellik öğesinin öğesi olarak anlık olarak etkinleştirmek için XAML sözdizimini nasıl destekleyeceğiaçıklanmaktadır.

## <a name="xaml-collection-concepts"></a>XAML Koleksiyon Kavramları

Kavramsal olarak, XAML nesne öğesi veya XAML özellik öğesi kapsamında birden çok alt öğe nin bulunduğu XAML'deki herhangi bir ilişki koleksiyon olarak uygulanmalıdır. Bu koleksiyon, bu ilişkide üst öğe olan XAML türünün belirli bir XAML özelliğiyle ilişkilendirilmelidir. Bir XAML işlemci, biçimlendirmedeki her öğeyi destek toplama özelliğinin yeni eklenen öğesi olarak atamayı beklediğinden, özellik bir koleksiyon olmalıdır.

XAML dil düzeyinde, toplama desteğinin tam gereksinimleri tam olarak tanımlanmamıştır. Koleksiyonun bir liste veya sözlük olabileceği (ancak her ikisi nin de olmadığı) Kavramı XAML dil düzeyinde tanımlanır, ancak destek türlerinin listeleri veya sözlükleri temsil ettiği kavram XAML dili tarafından tanımlanmaz.

.NET XAML Services'da XAML toplama desteği kavramı .NET destek türleri açısından daha açık bir şekilde tanımlanır. Özellikle, koleksiyonlar için XAML desteği, genel olarak .NET programlamada listeler ve sözlükler için kullanılan birkaç .NET kavramı ve API'yi temel alır.

1. Arabirim <xref:System.Collections.IList> bir liste koleksiyonunu gösterir.

2. Arabirim <xref:System.Collections.IDictionary> bir sözlük koleksiyonunu gösterir.

3. <xref:System.Array>bir dizitemsil eder ve <xref:System.Collections.IList> bir dizi yöntemleri destekler.

Bu toplama kavramlarının her birinde, bir .NET XAML Services `Add` XAML işlemcisi, toplama özelliğinin türüne ait belirli bir örnekte yöntemi aramayı bekler. Veya, bir serileştirme senaryosunda, bir XAML işlemci, liste, sözlük veya dizide bulunan her öğe için her koleksiyonun özel "Öğeler" kavramına dayalı ayrı ayrı XAML türü örnekleri üretir. Bu öğeler <xref:System.Collections.IList.Item%2A?displayProperty=nameWithType>şunlardır: ; <xref:System.Collections.IDictionary.Item%2A?displayProperty=nameWithType>; için <xref:System.Array> <xref:System.Array.System%23Collections%23IList%23Item%2A?displayProperty=nameWithType> açık .

## <a name="generic-collections"></a>Genel Koleksiyonlar

Genel koleksiyonlar genel .NET programlama için yararlı olabilir ve XAML toplama özellikleri için de kullanılabilir. Ancak, <xref:System.Collections.Generic.IList%601> genel arabirimler <xref:System.Collections.Generic.IDictionary%602> ve .NET XAML Services XAML işlemciler tarafından genel <xref:System.Collections.IList> olmayan <xref:System.Collections.IDictionary>veya eşdeğer olarak tanımlanmaz. Arabirimleri uygulamak yerine, genel koleksiyon özelliği türleri için önerilen bir yaklaşım <xref:System.Collections.Generic.List%601> <xref:System.Collections.Generic.Dictionary%602>sınıflardan türetmek veya . Bu sınıflar genel olmayan arabirimleri uygular ve böylece temel uygulamada XAML koleksiyonları için beklenen desteği içerir.

## <a name="read-only-collections-and-initialization-logic"></a>Salt Okunur Koleksiyonlar ve Başlatma Mantığı

.NET programlamada, yalnızca okunur koleksiyon olarak bir koleksiyon değeri tutan herhangi bir özellik yapmak için yaygın bir tasarım desenidir. Bu desen, koleksiyona ne olacağını daha iyi denetlemek için toplama özelliğine sahip olan örneğin izin verir... Özellikle, desen özelliği ayarlayarak tüm önceden varolan koleksiyonun yanlışlıkla değiştirilmesini önler. Bu desende, arayanlar tarafından koleksiyona herhangi bir erişim yerine toplama türü ve / veya ilgili toplama arabirimleri <xref:System.Collections.IList>tarafından desteklenen yöntemleri veya özellikleri çağırarak yapılmalıdır.

Bu deseni kullanmak, salt okunur toplama özelliğini ortaya çıkaran herhangi bir sınıfın, boş bir koleksiyon tutmak için önce bu özelliği başlatması gerektiği anlamına gelir. Genellikle başlatma sınıfıiçin yapı davranışının bir parçası olarak gerçekleştirilir. XAML için yararlı olması için, xaml genellikle özellikleri (toplama özellikleri veya başka) işlemeden önce parametresiz oluşturucu çağırır, çünkü bu tür mantık her zaman parametresiz oluşturucu tarafından başvurulan önemlidir.

## <a name="xaml-type-system-support-and-collections"></a>XAML Tipi Sistem Destek ve Koleksiyonları

XAML'yi ayrıştırma ve toplama özelliklerini doldurma veya serileştirme temel mekaniğinin ötesinde, .NET XAML Services'da uygulanan XAML türü sistem, XAML'deki koleksiyonlarla ilgili çeşitli tasarım özellikleri içerir.

1. <xref:System.Xaml.XamlType.IsCollection%2A>XAML türü XAML toplama desteği sağlayan bir tür tarafından desteklenirse doğru döndürür.

2. <xref:System.Xaml.XamlType.IsDictionary%2A>ve <xref:System.Xaml.XamlType.IsArray%2A> XAML türünün hangi toplama modunu desteklediğini daha da belirleyebilir. .NET XAML Hizmetleri ve XAML türü sistemini temel alan ancak varolan <xref:System.Xaml.XamlWriter> uygulamalara dayanmayan özel XAML işlemciler için, toplama işlemi için hangi yöntemin çağrıldığını bilmek için hangi toplama modunun kullanıldığını bilmek gerekebilir.

3. Önceki özellik değerlerinin her biri, XAML <xref:System.Xaml.XamlType.LookupCollectionKind%2A> türündeki geçersiz kılmalardan etkilenebilir.
