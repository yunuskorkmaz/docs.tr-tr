---
title: Nasıl yapılır makaleleri (C# kılavuz)
description: Hızlı ipuçları ve kısa, odaklanmış kod örnekleri koleksiyonu
ms.date: 12/20/2017
ms.openlocfilehash: 09e39e3c9bea5d4b9240039e37d2a5998fe1ebf8
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400743"
---
# <a name="how-to-c"></a>Nasıl yapılır (C#)

C# Kılavuzun nasıl yapılır bölümünde yaygın soruların hızlı yanıtlarını bulabilirsiniz. Bazı durumlarda, makaleler birden çok bölümde listelenebilir. Birden çok arama yolu için bulmayı kolay hale getirmek istiyorduk.

## <a name="general-c-concepts"></a>Genel C# kavramlar

Yaygın C# geliştirici uygulamaları olan çeşitli ipuçları ve püf noktaları vardır.

- [Nesne Başlatıcısı kullanarak nesneleri başlatın](../programming-guide/classes-and-structs/how-to-initialize-objects-by-using-an-object-initializer.md).
- Bir [Yapı ve sınıfı bir yönteme geçirme arasındaki farkları öğrenin](../programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md).
- [Genel ad alanı diğer adını kullanarak tür adı çakışmalarını çözün](../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md).
- [İşleç aşırı yüklemesi kullanın](../language-reference/operators/operator-overloading.md).
- [Özel bir genişletme yöntemi uygulayın ve çağırın](../programming-guide/classes-and-structs/how-to-implement-and-call-a-custom-extension-method.md).
- Programcılar C# [, hatta, `My` vb. ad alanını kullanmak](../programming-guide/namespaces/how-to-use-the-my-namespace.md)isteyebilir.
- [Uzantı `enum` yöntemleri kullanarak bir tür için yeni bir yöntem oluşturun](../programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).

### <a name="class-and-struct-members"></a>Sınıf ve yapı üyeleri

Programınızı uygulamak için sınıflar ve yapılar oluşturursunuz. Bu teknikler, sınıfları veya yapıları yazarken yaygın olarak kullanılır.

- [Otomatik uygulanan özellikler bildirin](../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).
- [Okuma/yazma özelliklerini bildirin ve kullanın](../programming-guide/classes-and-structs/how-to-declare-and-use-read-write-properties.md).
- [Sabitleri tanımlayın](../programming-guide/classes-and-structs/how-to-define-constants.md).
- [Dize çıktısı sağlamak için yönteminigeçersizkılın.`ToString` ](../programming-guide/classes-and-structs/how-to-override-the-tostring-method.md)
- [Soyut özellikleri tanımlayın](../programming-guide/classes-and-structs/how-to-define-abstract-properties.md).
- [Kodunuzu belgelemek için XML belge özelliklerini kullanın](../programming-guide/xmldoc/how-to-use-the-xml-documentation-features.md).
- Genel arabiriminizi kısa tutmak için [arabirim üyelerini açık](../programming-guide/interfaces/how-to-explicitly-implement-interface-members.md) bir şekilde uygulayın.
- [İki arabirimin üyelerini açıkça uygulayın](../programming-guide/interfaces/how-to-explicitly-implement-members-of-two-interfaces.md).

### <a name="working-with-collections"></a>Koleksiyonlarla çalışma

Bu makaleler, veri koleksiyonlarıyla çalışmanıza yardımcı olur.

- [Koleksiyon başlatıcısı ile bir sözlük başlatın](../programming-guide/classes-and-structs/how-to-initialize-a-dictionary-with-a-collection-initializer.md).

## <a name="working-with-strings"></a>Dizelerle çalışma

Dizeler, metni göstermek veya işlemek için kullanılan temel veri türüdür. Bu makaleler, dizelerin bulunduğu yaygın uygulamaları gösterir.

- [Dizeleri karşılaştırın](compare-strings.md).
- [Bir dizenin Içeriğini değiştirme](modify-string-contents.md).
- [Bir dizenin bir sayıyı temsil edip etmediğini belirleme](../programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md).
- [Dizeleri `String.Split` ayırmak için kullanın](parse-strings-using-split.md).
- [Birden çok dizeyi bir Içinde birleştirin](concatenate-multiple-strings.md).
- [Dizede metin arayın](search-strings.md).

## <a name="convert-between-types"></a>Türler arasında dönüştürme

Bir nesneyi farklı bir türe dönüştürmeniz gerekebilir.

- [Bir dizenin bir sayıyı temsil edip etmediğini belirleme](../programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md).
- [Onaltılık sayıları ve sayıyı temsil eden dizeler arasında dönüştürme](../programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md).
- Bir [ `DateTime`dizeyi öğesine dönüştürün ](../../standard/base-types/parsing-datetime.md).
- [Bir Byte dizisini int 'e dönüştürün](../programming-guide/types/how-to-convert-a-byte-array-to-an-int.md).
- [Bir dizeyi sayıya dönüştürür](../programming-guide/types/how-to-convert-a-string-to-a-number.md).
- [Farklı bir türe güvenle dönüştürmek `as` için `is` , ve işleçlerini kullanarak model eşleştirmeyi kullanın](../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md).
- [Özel tür dönüştürmeleri tanımlayın](../language-reference/operators/user-defined-conversion-operators.md).
- [Türün null yapılabilir bir değer türü](../programming-guide/nullable-types/how-to-identify-a-nullable-type.md)olup olmadığını belirleme.
- [Null yapılabilen ve null yapılamayan değer türleri arasında dönüştürme](../programming-guide/nullable-types/using-nullable-types.md#conversion-from-a-nullable-type-to-an-underlying-type).

## <a name="equality-and-ordering-comparisons"></a>Eşitlik ve sıralama karşılaştırmaları

Eşitlik için kendi kurallarını tanımlayan türler oluşturabilir veya bu tür nesneler arasında doğal bir sıralama tanımlayabilirsiniz.

- [Başvuru tabanlı eşitlik Için test](../programming-guide/statements-expressions-operators/how-to-test-for-reference-equality-identity.md).
- [Bir tür için değer tabanlı eşitlik tanımlayın](../programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md).

## <a name="exception-handling"></a>Özel durum işleme

.NET programları, özel durumlar oluşturarak bu yöntemlerin çalışmalarını başarıyla tamamlamamış olduğunu bildirir. Bu makalelerde, özel durumlarla çalışmayı öğreneceksiniz.

- [ `try` Ve kullanarak`catch`özel durumları işleyin ](../programming-guide/exceptions/how-to-handle-an-exception-using-try-catch.md).
- [Yan tümceleri kullanarak `finally` Kaynakları Temizleme](../programming-guide/exceptions/how-to-execute-cleanup-code-using-finally.md).
- [CLS olmayan (ortak dil belirtimi) özel durumlarından kurtarın](../programming-guide/exceptions/how-to-catch-a-non-cls-exception.md).

## <a name="delegates-and-events"></a>Temsilciler ve olaylar

Temsilciler ve olaylar, gevşek olarak bağlanmış kod bloklarını içeren stratejiler için bir yetenek sağlar.

- [Temsilcileri bildirin, oluşturun ve kullanın](../programming-guide/delegates/how-to-declare-instantiate-and-use-a-delegate.md).
- [Çok noktaya yayın temsilcileri birleştirin](../programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md).

Olaylar, bildirimleri yayınlamak veya bunlara abone olmak için bir mekanizma sağlar.

- [Olaylara abone olma ve aboneliği kaldırma](../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).
- [Arabirimlerde belirtilen olayları uygulayın](../programming-guide/events/how-to-implement-interface-events.md).
- [Kodunuz olayları yayımladığında .NET Framework yönergelerine uygun](../programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md).
- [Türetilmiş sınıflardan temel sınıflarda tanımlı olayları yükseltir](../programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md).
- [Özel olay erişimcileri uygulayın](../programming-guide/events/how-to-implement-custom-event-accessors.md).

## <a name="linq-practices"></a>LINQ uygulamaları

LINQ, LINQ sorgu ifadesi modelini destekleyen herhangi bir veri kaynağını sorgulamak için kod yazmanıza olanak sağlar. Bu makaleler, stili anlamanıza ve farklı veri kaynaklarıyla çalışmanıza yardımcı olur.

- [Bir koleksiyonu sorgulayın](../programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md).
- [Bir sorguda lambda Ifadeleri kullanın](../programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-in-a-query.md).
- [Sorgu `var` ifadelerinde kullanın](../programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).
- [Bir sorgudan öğe özelliklerinin alt kümelerini döndürün](../programming-guide/classes-and-structs/how-to-return-subsets-of-element-properties-in-a-query.md).
- [Karmaşık filtrelemeye sahip sorgular yazın](../programming-guide/concepts/linq/how-to-write-queries-with-complex-filtering.md).
- [Bir veri kaynağının öğelerini sıralayın](../programming-guide/concepts/linq/how-to-sort-elements.md).
- [Öğeleri birden çok anahtar üzerinde sıralayın](../programming-guide/concepts/linq/how-to-sort-elements-on-multiple-keys.md).
- [Projeksiyon türünü denetleyin](../programming-guide/concepts/linq/how-to-control-the-type-of-a-projection.md).
- [Kaynak dizisindeki bir değerin tekrarlamalarını say](../programming-guide/concepts/linq/how-to-count-occurrences-of-a-word-in-a-string-linq.md).
- [Ara değerleri hesaplayın](../programming-guide/concepts/linq/how-to-calculate-intermediate-values.md).
- [Birden çok kaynaktaki verileri birleştirin](../programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md).
- [İki sıra arasında ayarlanan farkı bulur](../programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md).
- [Boş sorgu sonuçlarında hata ayıklayın](../programming-guide/concepts/linq/how-to-debug-empty-query-results-sets.md).
- [LINQ Sorgularına özel yöntemler ekleyin](../programming-guide/concepts/linq/how-to-add-custom-methods-for-linq-queries.md).

## <a name="multiple-threads-and-async-processing"></a>Birden çok iş parçacığı ve zaman uyumsuz işleme

Modern programlar genellikle zaman uyumsuz işlemler kullanır. Bu makaleler, bu teknikleri kullanmayı öğrenmenize yardımcı olur.

- [ Kullanarak`System.Threading.Tasks.Task.WhenAll`zaman uyumsuz performansı geliştirir ](../programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).
- [ `async` Ve kullanarak`await`birden çok web isteğini paralel hale getirin ](../programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md).
- [Bir iş parçacığı havuzu kullanın](../../standard/threading/the-managed-thread-pool.md#using-the-thread-pool).

## <a name="command-line-args-to-your-program"></a>Programınızın komut satırı bağımsız değişkenleri

Genellikle, C# programların komut satırı bağımsız değişkenleri vardır. Bu makaleler, bu komut satırı bağımsız değişkenlerine erişmek ve bunları işlemek için size öğretir.

- [Tüm komut satırı bağımsız değişkenlerini Ile `for`alın ](../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md).
