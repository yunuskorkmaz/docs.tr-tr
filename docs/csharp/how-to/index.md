---
title: "Nasıl yapılır makaleleri (C# Kılavuzu)"
description: "Hızlı ipuçları ve kısa, odaklanmış kod örnekleri topluluğu"
author: billwagner
ms.author: wiwagn
ms.date: 12/20/2017
ms.topic: article
ms.prod: .net
ms.devlang: devlang-csharp
ms.openlocfilehash: d1bef5813df40fb5c6e6b96e0042a682022beb8d
ms.sourcegitcommit: dd6ea7f0e581ac84e0a90d9b23c463fcf1ec3ce7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2018
---
# <a name="how-to-c"></a>Nasıl yapılır (C#)

C# Kılavuzu bölümüne nasıl hızlı sık sorulan soruların yanıtlarını bulabilirsiniz. Bazı durumlarda, birden çok bölümünde makaleleri listelenebilir. Birden çok arama yolları için bulmayı kolaylaştırmak istedik. 

## <a name="general-c-concepts"></a>Genel C# Kavramları

Bazı ipuçları ve ortak C# Geliştirici yöntemleridir püf noktaları vardır.

- [Nesne Başlatıcı kullanarak nesneleri başlatma](../programming-guide/classes-and-structs/how-to-initialize-objects-by-using-an-object-initializer.md).
- [Yapı ve bir sınıf için bir yöntem geçirme arasındaki farklar öğrenin](../programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md).
- [Lambda ifadeleri kullanma](../programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-outside-linq.md).
- [Genel ad alanı diğer adı kullanarak türü adı çakışmalarını çözme](../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md).
- [Kullanım İşleç aşırı yüklemesi](../programming-guide/statements-expressions-operators/how-to-use-operator-overloading-to-create-a-complex-number-class.md).
- [Uygulama ve özel uzantı metodu çağırma](../programming-guide/classes-and-structs/how-to-implement-and-call-a-custom-extension-method.md).
- Hatta C# programcıları için isteyebilir [kullanmak `My` ad alanından VB](../programming-guide/namespaces/how-to-use-the-my-namespace.md).
- [İçin yeni bir yöntem oluşturma bir `enum` genişletme yöntemleri kullanarak yazın](../programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).

### <a name="class-and-struct-members"></a>Sınıf ve yapı üyeleri

Sınıflar ve yapılar programınızın uygulama oluşturun. Bu teknikler, sınıfları veya yapılar yazarken yaygın olarak kullanılır.

- [Otomatik uygulanan özellikler bildirme](../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).
- [Okuma/yazma özellikleri bildirme ve kullanma](../programming-guide/classes-and-structs/how-to-declare-and-use-read-write-properties.md).
- [Sabitleri tanımlama](../programming-guide/classes-and-structs/how-to-define-constants.md).
- [Geçersiz kılma `ToString` dize çıkış sağlamak üzere yöntemi](../programming-guide/classes-and-structs/how-to-override-the-tostring-method.md).
- [Soyut özellikleri tanımlama](../programming-guide/classes-and-structs/how-to-define-abstract-properties.md).
- [Kodunuzu belgelemek için xml belgeleri özelliklerini kullanma](../programming-guide/xmldoc/how-to-use-the-xml-documentation-features.md).
- [Arabirim üyelerini açıkça uygulama](../programming-guide/interfaces/how-to-explicitly-implement-interface-members.md) ortak arabirimi kısa tutmak için.
- [İki arabirimin üyelerini açıkça uygulama](../programming-guide/interfaces/how-to-explicitly-implement-members-of-two-interfaces.md).

### <a name="working-with-collections"></a>Koleksiyonları ile çalışma

Bu makaleler, veri toplulukları ile çalışmanıza yardımcı.

- [Koleksiyon Başlatıcısı ile bir sözlük başlatma](../programming-guide/classes-and-structs/how-to-initialize-a-dictionary-with-a-collection-initializer.md).
- [Kullanarak bir koleksiyon içindeki tüm öğeler erişim `foreach` ](../programming-guide/classes-and-structs/how-to-access-a-collection-class-with-foreach.md).

## <a name="strings"></a>dizeler

Görüntülemek veya metin işlemek için kullanılan temel bir veri türü dizelerdir. Bu makaleler dizeler yönelik yaygın yöntemleri gösterir.

- [Dizeleri karşılaştırmak](../programming-guide/strings/how-to-compare-strings.md).
- [Bir dize içeriklerini değiştirme](../programming-guide/strings/how-to-modify-string-contents.md).
- [Bir dizeyi bir sayı temsil edip etmediğini belirlemek](../programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md).
- [Kullanım `String.Split` dizeleri ayırmak için](parse-strings-using-split.md).
- [Birden çok dizenin bir nesnede birleştirme](concatenate-multiple-strings.md).
- [Metin dizesindeki arama](../programming-guide/strings/how-to-search-strings-using-string-methods.md).
- [Normal ifadeler kullanarak dizeleri arama](../programming-guide/strings/how-to-search-strings-using-regular-expressions.md).

## <a name="convert-between-types"></a>Türleri arasında dönüştürme

Bir nesne farklı bir türe dönüştürmeniz gerekebilir.

- [Bir dizeyi bir sayı temsil edip etmediğini belirlemek](../programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md).
- [Onaltılık sayıları temsil eden dizeleri ve sayı arasında dönüştürme](../programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md).
- [Bir dizeye dönüştürme bir <xref:System.DateTime> ](../programming-guide/strings/how-to-convert-a-string-to-a-datetime.md).
- [Bir bayt dizisi int'e dönüştürme](../programming-guide/types/how-to-convert-a-byte-array-to-an-int.md).
- [Bir dizeyi sayıya dönüştürme](../programming-guide/types/how-to-convert-a-string-to-a-number.md).
- [Kullanım `as` ve `is` farklı bir türe güvenli bir şekilde atama için](../programming-guide/types/how-to-safely-cast-by-using-as-and-is-operators.md).
- [Dönüştürme işleçleri tanımlayan `struct` türleri](../programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md).
- [Bir tür boş değer atanabilir değer türü olup olmadığını](../programming-guide/nullable-types/how-to-identify-a-nullable-type.md).
- [Boş değer atanabilir ve null değer türleri arasında dönüştürme](../programming-guide/nullable-types/how-to-safely-cast-from-bool-to-bool.md).

## <a name="equality-and-ordering-comparisons"></a>Eşitlik ve sıralama karşılaştırmaları

Eşitlik için kendi kurallarına tanımlayın veya doğal bu tür nesneleri arasında sıralama tanımlamak türleri oluşturabilir.

- [Başvuru tabanlı eşitlik için test](../programming-guide/statements-expressions-operators/how-to-test-for-reference-equality-identity.md).
- [Bir tür için değer tabanlı eşitliği tanımlama](../programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md).

## <a name="exception-handling"></a>Özel durum işleme

.NET programlar yöntemleri başarıyla işlerine özel durumları atma tamamlamadığını bildirin. Bu makalelerde istisnalar çalışmaya öğreneceksiniz.

- [Kullanarak özel durumları işleme `try` ve `catch` ](../programming-guide/exceptions/how-to-handle-an-exception-using-try-catch.md).
- [Temizleme kaynaklarını kullanarak `finally` yan tümceleri](../programming-guide/exceptions/how-to-execute-cleanup-code-using-finally.md).
- [CLS dışı (ortak dil belirtimi) özel durumlar kurtarmak](../programming-guide/exceptions/how-to-catch-a-non-cls-exception.md).

## <a name="delegates-and-events"></a>Temsilciler ve olaylar

Temsilciler ve olaylar geniş içeren stratejileri yeteneği kod bloklarını eşleşmiş sağlar.

- [Bildirme, oluşturma ve temsilciler kullanmak](../programming-guide/delegates/how-to-declare-instantiate-and-use-a-delegate.md).
- [Çok noktaya yayın temsilcileri birleştirme](../programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md).

Olayları yayımlamak veya Bildirimlere abone için bir mekanizma sağlar.

- [Abone olma ve aboneliği olaylarından](../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).
- [Uygulama arabirimlerde bildirilen olaylarda](../programming-guide/events/how-to-implement-interface-events.md).
- [Kodunuzu olaylar yayımladığında .NET Framework yönergeleriyle uyumlu](../programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md).
- [Türetilmiş sınıflar temel sınıflardan tanımlanan olaylarını](../programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md).
- [Olay örnekleri bir sözlükte depolama](../programming-guide/events/how-to-use-a-dictionary-to-store-event-instances.md).
- [Özel olay erişimcilerini uygulama](../programming-guide/events/how-to-implement-custom-event-accessors.md).

## <a name="linq-practices"></a>LINQ yöntemler

LINQ LINQ Sorgu ifade deseni destekleyen herhangi bir veri kaynağını sorgulamak için kod yazmanıza olanak sağlar. Bu makaleler düzeni anlamak ve farklı veri kaynakları ile çalışacak yardımcı olur.

- [Bir koleksiyon sorgu](../programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md).
- [Sorguda lambda ifadeleri kullanma](../programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-in-a-query.md).
- [Kullanım `var` sorgu ifadelerinde](../programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).
- [Bir öğe özelliklerinin alt kümelerini döndürdüğünüz](../programming-guide/classes-and-structs/how-to-return-subsets-of-element-properties-in-a-query.md).
- [Karmaşık filtreleme ile sorguları yazma](../programming-guide/concepts/linq/how-to-write-queries-with-complex-filtering.md).
- [Bir veri kaynağının öğeleri sıralama](../programming-guide/concepts/linq/how-to-sort-elements.md).
- [Birden çok anahtar öğeleri sıralama](../programming-guide/concepts/linq/how-to-sort-elements-on-multiple-keys.md).
- [Bir yansıtma türünü denetlemek](../programming-guide/concepts/linq/how-to-control-the-type-of-a-projection.md).
- [Bir kaynak dizisini içindeki bir değeri sayısı oluşum](../programming-guide/concepts/linq/how-to-count-occurrences-of-a-word-in-a-string-linq.md).
- [Ara değerleri hesaplamak](../programming-guide/concepts/linq/how-to-calculate-intermediate-values.md).
- [Birden çok kaynaktan veri birleştirme](../programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md).
- [İki sıraları arasında ayarlanmış farkı bulma](../programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md).
- [Boş sorgu sonuçları hata ayıklama](../programming-guide/concepts/linq/how-to-debug-empty-query-results-sets.md).
- [LINQ sorguları için özel yöntemler ekleme](../programming-guide/concepts/linq/how-to-add-custom-methods-for-linq-queries.md).

## <a name="multiple-threads-and-async-processing"></a>Birden çok iş parçacığı sayısı ve zaman uyumsuz işleme

Modern programlar genellikle zaman uyumsuz işlemleri kullanın. Bu makaleler, bu teknikler kullanmayı öğrenmenize yardımcı olur.

- [Zaman uyumsuz kullanımında artırmak `System.Threading.Tasks.Task.WhenAll` ](../programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).
- [Birden çok web isteğini paralel kullanarak hale `async` ve `await` ](../programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md).
- [İş parçacığı havuzu kullanma](../programming-guide/concepts/threading/how-to-use-a-thread-pool.md).

## <a name="command-line-args-to-your-program"></a>Program için komut satırı bağımsız değişken

Genellikle, C# programları komut satırı bağımsız değişkenleri vardır. Bu makaleler erişmek ve bu komut satırı bağımsız değişkenleri işlemek için öğretir.

- [Tüm komut satırı bağımsız değişkenleri ile almak `for` ](../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md).
- [Tüm komut satırı bağımsız değişkenleri ile almak `foreach` ](../programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md).
