---
title: Nasıl yapılır makaleleri (C# Kılavuzu)
description: Hızlı ipuçları ve kısa, odaklanmış kod örnekleri koleksiyonu
ms.date: 12/20/2017
ms.openlocfilehash: 77b68af5802f79060e30b2817661de4cb5e46942
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65879023"
---
# <a name="how-to-c"></a>Nasıl yapılır (C#)

C# Kılavuzu bölümünü nasıl sık sorulan sorulara hızlı yanıtlar bulabilirsiniz. Bazı durumlarda, makaleler birden çok bölümlerinde listelenen. Birden çok arama yolunu bulmayı kolaylaştırmak istedik. 

## <a name="general-c-concepts"></a>Genel C# Kavramları

Bazı ipuçları ve ortak C# Geliştirici Practices püf noktaları vardır.

- [Nesne Başlatıcı kullanarak nesneleri başlatma](../programming-guide/classes-and-structs/how-to-initialize-objects-by-using-an-object-initializer.md).
- [Bir yapı ile bir sınıf için bir yöntem geçirme arasındaki farkları öğrenin](../programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md).
- [Lambda ifadeleri kullanma](../programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-outside-linq.md).
- [Tür adı genel ad alanı diğer adlarını kullanarak çakışmaları](../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md).
- [Kullanım İşleç aşırı yüklemesi](../language-reference/keywords/operator.md).
- [Özel bir genişletme yöntemi uygulama ve arama](../programming-guide/classes-and-structs/how-to-implement-and-call-a-custom-extension-method.md).
- Hatta C# programcıları isteyebilirsiniz [kullanın `My` ad alanından VB](../programming-guide/namespaces/how-to-use-the-my-namespace.md).
- [İçin yeni bir yöntem oluşturma bir `enum` genişletme yöntemleri kullanarak yazın](../programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).

### <a name="class-and-struct-members"></a>Sınıf ile yapı üyeleri

Sınıflar ve yapılar, programınızın uygulamak için oluşturduğunuz. Bu teknikler, sınıflar veya yapılar yazarken sık kullanılan bloblardır.

- [Otomatik uygulanan Özellikler](../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).
- [Okuma/yazma özellikleri bildirme ve kullanma](../programming-guide/classes-and-structs/how-to-declare-and-use-read-write-properties.md).
- [Sabitleri tanımla](../programming-guide/classes-and-structs/how-to-define-constants.md).
- [Geçersiz kılma `ToString` dize çıktısı sağlamak için yöntemi](../programming-guide/classes-and-structs/how-to-override-the-tostring-method.md).
- [Soyut özellikleri tanımlama](../programming-guide/classes-and-structs/how-to-define-abstract-properties.md).
- [Kodunuzu belgelemek için xml belgeleri özelliklerini kullanma](../programming-guide/xmldoc/how-to-use-the-xml-documentation-features.md).
- [Arabirim üyelerini açıkça uygulama](../programming-guide/interfaces/how-to-explicitly-implement-interface-members.md) , ortak arabirim kısa tutmak için.
- [İki arabirimin üyelerini açıkça uygulama](../programming-guide/interfaces/how-to-explicitly-implement-members-of-two-interfaces.md).

### <a name="working-with-collections"></a>Koleksiyonlar ile çalışma

Bu makaleler, veri koleksiyonları ile çalışmanıza yardımcı olur.

- [Koleksiyon Başlatıcısı ile bir sözlük başlatma](../programming-guide/classes-and-structs/how-to-initialize-a-dictionary-with-a-collection-initializer.md).

## <a name="working-with-strings"></a>Dizeler ile çalışma

Görüntülemek veya metin işlemek için kullanılan temel veri türü dizelerdir. Bu makaleler dizeleriyle genel yöntemler gösterilmektedir.

- [Dizeleri karşılaştırma](compare-strings.md).
- [Dize içeriklerini değiştirme](modify-string-contents.md).
- [Bir dizeyi bir sayıyı temsil edip etmediğini belirleme](../programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md).
- [Kullanım `String.Split` dizeleri ayırmak için](parse-strings-using-split.md).
- [Tek bir komutta birden çok dizeyi birleştirme](concatenate-multiple-strings.md).
- [Bir dizede metin arama](search-strings.md).

## <a name="convert-between-types"></a>Türleri arasında dönüştürme

Nesneyi farklı bir türe dönüştürmeniz gerekebilir.

- [Bir dizeyi bir sayıyı temsil edip etmediğini belirleme](../programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md).
- [Onaltılık sayıları temsil eden dizeleri ve sayı arasında dönüştürme](../programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md).
- [Bir dizeye Dönüştür bir `DateTime` ](../../standard/base-types/parsing-datetime.md).
- [Bir bayt dizisini int'e dönüştürme](../programming-guide/types/how-to-convert-a-byte-array-to-an-int.md).
- [Bir dizeyi sayıya dönüştürme](../programming-guide/types/how-to-convert-a-string-to-a-number.md).
- [Desen eşleştirme kullan `as` ve `is` güvenli bir şekilde farklı bir türe dönüştürme yapmak işleçleri](../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md).
- [Dönüştürme işleçleri tanımlama `struct` türleri](../programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md).
- [Bir türü null bir değer türü olup olmadığını](../programming-guide/nullable-types/how-to-identify-a-nullable-type.md).
- [Boş değer atanabilir ve NULL olmayan değer türleri arasında dönüştürme](../programming-guide/nullable-types/using-nullable-types.md#conversion-from-a-nullable-type-to-an-underlying-type).

## <a name="equality-and-ordering-comparisons"></a>Eşitlik ve sıralama karşılaştırmaları

Eşitlik için kendi kuralları tanımlayın veya doğal bir sıralama türü bir nesne arasında tanımlama türleri oluşturabilir.

- [Tabanlı başvuru eşitliği testi](../programming-guide/statements-expressions-operators/how-to-test-for-reference-equality-identity.md).
- [Bir tür için değer tabanlı eşitliği tanımlama](../programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md).

## <a name="exception-handling"></a>Özel durum işleme

.NET programlarının yöntemleri başarıyla işlerini özel durumları atma tarafından tamamlamadığını bildirin. Aşağıdaki makalelerde, özel durum ile birlikte çalışmak öğreneceksiniz.

- [Özel durum kullanarak işlemek `try` ve `catch` ](../programming-guide/exceptions/how-to-handle-an-exception-using-try-catch.md).
- [Temizleme kaynakları kullanarak `finally` yan tümceleri](../programming-guide/exceptions/how-to-execute-cleanup-code-using-finally.md).
- [CLS olmayan (ortak dil belirtimi) özel durumlarından kurtulmak](../programming-guide/exceptions/how-to-catch-a-non-cls-exception.md).

## <a name="delegates-and-events"></a>Temsilciler ve olaylar

Temsilciler ve olaylar gevşek ilgili stratejiler için bir özellik kod bloklarını eşleşmiş sağlar.

- [Bildirme, oluşturma ve temsilcileri kullanın](../programming-guide/delegates/how-to-declare-instantiate-and-use-a-delegate.md).
- [Çok noktaya yayın temsilcileri birleştirme](../programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md).

Olayları yayımlamak veya Bildirimlere abone için bir mekanizma sağlar.

- [Abone olma ve aboneliği olaylardan](../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).
- [Arabirimde bildirilen olaylarını uygulama](../programming-guide/events/how-to-implement-interface-events.md).
- [Kodunuzu olayları yayımlarken .NET Framework yönergeleriyle uyumlu](../programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md).
- [Temel sınıftan türetilmiş sınıflar içinde tanımlanan olay](../programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md).
- [Olay örnekleri bir sözlükte Store](../programming-guide/events/how-to-use-a-dictionary-to-store-event-instances.md).
- [Özel olay erişimcilerini uygulama](../programming-guide/events/how-to-implement-custom-event-accessors.md).

## <a name="linq-practices"></a>LINQ yöntemleri

LINQ Sorgu LINQ Sorgu ifade deseninin destekleyen herhangi bir veri kaynağı için kod yazmanıza olanak sağlar. Bu makaleler, deseni anlamanıza ve farklı veri kaynaklarıyla çalışma sorunlarını ortadan kaldırmaya yardımcı olur.

- [Koleksiyonu sorgulama](../programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md).
- [Bir sorguda lambda ifadeleri kullanma](../programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-in-a-query.md).
- [Kullanım `var` sorgu ifadelerinde](../programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).
- [Sorgu öğe özelliklerinin alt kümelerini döndürme](../programming-guide/classes-and-structs/how-to-return-subsets-of-element-properties-in-a-query.md).
- [Karmaşık filtreleme ile sorgu yazma](../programming-guide/concepts/linq/how-to-write-queries-with-complex-filtering.md).
- [Bir veri kaynağının öğeleri sıralama](../programming-guide/concepts/linq/how-to-sort-elements.md).
- [Birden çok anahtarda öğeleri sıralama](../programming-guide/concepts/linq/how-to-sort-elements-on-multiple-keys.md).
- [Bir projeksiyon türünü denetleme](../programming-guide/concepts/linq/how-to-control-the-type-of-a-projection.md).
- [Bir kaynak dizisi içindeki bir değerin yinelemeleri Say](../programming-guide/concepts/linq/how-to-count-occurrences-of-a-word-in-a-string-linq.md).
- [Ara değerleri hesaplama](../programming-guide/concepts/linq/how-to-calculate-intermediate-values.md).
- [Birden çok kaynaktan veri birleştirme](../programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md).
- [İki sıranın arasında ayarlanmış farkı bulma](../programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md).
- [Boş sorgu sonuçları hata ayıklama](../programming-guide/concepts/linq/how-to-debug-empty-query-results-sets.md).
- [LINQ sorguları için özel yöntemler](../programming-guide/concepts/linq/how-to-add-custom-methods-for-linq-queries.md).

## <a name="multiple-threads-and-async-processing"></a>Birden çok iş parçacığı ve zaman uyumsuz işleme

Modern programlar genellikle zaman uyumsuz işlemler kullanın. Bu makaleler bu teknikler kullanmayı öğrenmenize yardımcı olur.

- [Async kullanma performansını artırmak `System.Threading.Tasks.Task.WhenAll` ](../programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).
- [Birden çok web isteğini kullanılarak paralel hale `async` ve `await` ](../programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md).
- [İş parçacığı havuzu kullanma](../../standard/threading/the-managed-thread-pool.md#using-the-thread-pool).

## <a name="command-line-args-to-your-program"></a>Programınız için komut satırı değişkenleri

Genellikle, C# programlarının komut satırı bağımsız değişkenleri vardır. Bu makaleler, erişmek ve bu komut satırı bağımsız değişkenleri işleme öğretin.

- [İle tüm komut satırı bağımsız değişkenlerini almak `for` ](../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md).
