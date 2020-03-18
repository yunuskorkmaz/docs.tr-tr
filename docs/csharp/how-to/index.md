---
title: Nasıl makaleler (C# Kılavuzu)
description: Hızlı ipuçları ve kısa, odaklı kod örnekleri koleksiyonu
ms.date: 12/20/2017
ms.openlocfilehash: e6cb657726b82a1710bbcd596fe48037b5c26352
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399324"
---
# <a name="how-to-c"></a>Nasıl yapılır (C#)

C# Kılavuzu'nun Nasıl Yapılacağını bölümünde, sık sorulan soruların hızlı yanıtlarını bulabilirsiniz. Bazı durumlarda, makaleler birden çok bölümde listelenebilir. Birden fazla arama yolu bulmalarını kolaylaştırmak istedik.

## <a name="general-c-concepts"></a>Genel C# kavramları

C# geliştirici uygulamalarının yaygın olduğu çeşitli ipuçları ve püf noktaları vardır:

- [Nesneleri bir nesne başlatma cıkullanarak başlatma.](../programming-guide/classes-and-structs/how-to-initialize-objects-by-using-an-object-initializer.md)
- [Bir yapı ve bir sınıfı bir yönteme geçirmek arasındaki farkları öğrenin.](../programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)
- [Operatör aşırı yükleme kullanın.](../language-reference/operators/operator-overloading.md)
- [Özel bir uzatma yöntemi uygulayın ve çağırın.](../programming-guide/classes-and-structs/how-to-implement-and-call-a-custom-extension-method.md)
- Hatta C# programcıları [Visual `My` Basic'teki ad alanını kullanmak](../programming-guide/namespaces/how-to-use-the-my-namespace.md)isteyebilir.
- [Uzantı yöntemlerini `enum` kullanarak bir tür için yeni bir yöntem oluşturun.](../programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md)

### <a name="class-and-struct-members"></a>Sınıf ve yapı üyeleri

Programınızı uygulamak için sınıflar ve structs oluşturursunuz. Bu teknikler genellikle sınıfları veya structs yazarken kullanılır.

- [Otomatik uygulanan özellikleri bildirin.](../programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md)
- [Okuma/yazma özelliklerini bildirin ve kullanın.](../programming-guide/classes-and-structs/how-to-declare-and-use-read-write-properties.md)
- [Sabitleri tanımlayın.](../programming-guide/classes-and-structs/how-to-define-constants.md)
- [Dize `ToString` çıktısını sağlamak için yöntemi geçersiz kılın.](../programming-guide/classes-and-structs/how-to-override-the-tostring-method.md)
- [Soyut özellikleri tanımlayın.](../programming-guide/classes-and-structs/how-to-define-abstract-properties.md)
- [Kodunuzu belgelemek için xml dokümantasyon özelliklerini kullanın.](../programming-guide/xmldoc/how-to-use-the-xml-documentation-features.md)
- Ortak [arabiriminizi](../programming-guide/interfaces/how-to-explicitly-implement-interface-members.md) kısa tutmak için arayüz üyelerini açıkça uygulayın.
- [İki arabirimin üyelerini açıkça uygulayın.](../programming-guide/interfaces/how-to-explicitly-implement-members-of-two-interfaces.md)

### <a name="working-with-collections"></a>Koleksiyonlarla çalışma

Bu makaleler, veri koleksiyonlarıyla çalışmanıza yardımcı olur.

- [Bir koleksiyon baş harfer ile bir sözlük başlatma](../programming-guide/classes-and-structs/how-to-initialize-a-dictionary-with-a-collection-initializer.md).

## <a name="working-with-strings"></a>Dizelerle çalışma

Dizeleri, metni görüntülemek veya işlemek için kullanılan temel veri türüdür. Bu makaleler dizeleri ile ortak uygulamaları göstermektedir.

- [Dizeleri karşılaştırın.](compare-strings.md)
- [Bir dizenin içeriğini değiştirin.](modify-string-contents.md)
- [Bir dize bir sayıyı temsil edip olmadığını belirleyin.](../programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
- [Dizeleri ayırmak `String.Split` için kullanın.](parse-strings-using-split.md)
- [Birden çok dizeleri tek bir olarak birleştirin.](concatenate-multiple-strings.md)
- [Dizedeki metni ara.](search-strings.md)

## <a name="convert-between-types"></a>Türler arasında dönüştürme

Bir nesneyi farklı bir türe dönüştürmeniz gerekebilir.

- [Bir dize bir sayıyı temsil edip olmadığını belirleyin.](../programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
- [Hexadecimal sayıları temsil eden dizeleri ve sayı arasında dönüştürün.](../programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)
- [Bir dizeyi `DateTime`bir ](../../standard/base-types/parsing-datetime.md).
- [Bayt dizisini int'e dönüştürün.](../programming-guide/types/how-to-convert-a-byte-array-to-an-int.md)
- [Bir dizeyi bir sayıya dönüştürün.](../programming-guide/types/how-to-convert-a-string-to-a-number.md)
- [Farklı bir `as` türe `is` güvenli bir şekilde döküm desen eşleştirme, ve operatörler kullanın.](../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [Özel tür dönüşümleri tanımlayın.](../language-reference/operators/user-defined-conversion-operators.md)
- [Bir türün nullable değer türü olup olmadığını belirleyin.](../language-reference/builtin-types/nullable-value-types.md#how-to-identify-a-nullable-value-type)
- [Nullable ve nullable değer türleri arasında dönüştürün.](../language-reference/builtin-types/nullable-value-types.md#conversion-from-a-nullable-value-type-to-an-underlying-type)

## <a name="equality-and-ordering-comparisons"></a>Eşitlik ve sıralama karşılaştırmaları

Eşitlik için kendi kurallarını tanımlayan veya bu tür nesneler arasında doğal bir sıralama tanımlayan türler oluşturabilirsiniz.

- [Referans tabanlı eşitlik için test.](../programming-guide/statements-expressions-operators/how-to-test-for-reference-equality-identity.md)
- [Bir tür için değer tabanlı eşitliği tanımlayın.](../programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md)

## <a name="exception-handling"></a>Özel durum işleme

.NET programları, yöntemlerin özel durumlar oluşturarak çalışmalarını başarıyla tamamlayamadığını bildirir. Bu makalelerde istisnalar dışında çalışmayı öğreneceksiniz.

- [Özel durumları `try` kullanarak `catch`ve ](../programming-guide/exceptions/how-to-handle-an-exception-using-try-catch.md).
- [Yan tümceleri kullanarak `finally` kaynakları temizleme.](../programming-guide/exceptions/how-to-execute-cleanup-code-using-finally.md)
- [CLS dışı (Ortak Dil Belirtimi) özel durumlarından kurtarın.](../programming-guide/exceptions/how-to-catch-a-non-cls-exception.md)

## <a name="delegates-and-events"></a>Delegeler ve etkinlikler

Temsilciler ve olaylar, gevşek birleştirilmiş kod bloklarını içeren stratejiler için bir yetenek sağlar.

- [Temsilcileri bildirin, anında kullanın ve kullanın.](../programming-guide/delegates/how-to-declare-instantiate-and-use-a-delegate.md)
- [Çok noktaya yayın temsilcilerini birleştirin.](../programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)

Olaylar, bildirimleri yayımlamak veya bunlara abone olmak için bir mekanizma sağlar.

- [Abone olun ve etkinliklerden aboneliğinizi iptal edin.](../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)
- [Arabirimlerde bildirilen olayları uygulayın.](../programming-guide/events/how-to-implement-interface-events.md)
- [Kodunuz olayları yayımladığında .NET Framework yönergelerine uyun.](../programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)
- [Taban sınıflarda tanımlanan olayları türemiş sınıflardan yükseltin.](../programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)
- [Özel olay erişime erişime uygulayın.](../programming-guide/events/how-to-implement-custom-event-accessors.md)

## <a name="linq-practices"></a>LINQ uygulamaları

LINQ, LINQ sorgu ifade deseni destekleyen herhangi bir veri kaynağını sorgulamak için kod yazmanızı sağlar. Bu makaleler deseni anlamanıza ve farklı veri kaynaklarıyla çalışmanıza yardımcı olur.

- [Bir koleksiyon sorgula](../programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md).
- [Bir sorguda lambda ifadelerini kullanın.](../programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-in-a-query.md)
- [Sorgu `var` ifadelerinde kullanın.](../programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)
- [Bir sorgudan öğe özelliklerinin alt kümelerini döndürün.](../programming-guide/classes-and-structs/how-to-return-subsets-of-element-properties-in-a-query.md)
- [Karmaşık filtreleme ile sorguyazın.](../programming-guide/concepts/linq/how-to-write-queries-with-complex-filtering.md)
- [Veri kaynağının öğelerini sırala.](../programming-guide/concepts/linq/how-to-sort-elements.md)
- [Öğeleri birden çok tuşa sıralayın.](../programming-guide/concepts/linq/how-to-sort-elements-on-multiple-keys.md)
- [Projeksiyon türünü kontrol edin.](../programming-guide/concepts/linq/how-to-control-the-type-of-a-projection.md)
- [Kaynak dizisindeki bir değerin oluşumlarını say.](../programming-guide/concepts/linq/how-to-count-occurrences-of-a-word-in-a-string-linq.md)
- [Ara değerleri hesaplayın.](../programming-guide/concepts/linq/how-to-calculate-intermediate-values.md)
- [Birden çok kaynaktan gelen verileri birleştirme.](../programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)
- [İki dizi arasındaki ayarfarkını bulun.](../programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)
- [Hata ayıklama boş sorgu sonuçları](../programming-guide/concepts/linq/how-to-debug-empty-query-results-sets.md).
- [LINQ sorgularına özel yöntemler ekleyin.](../programming-guide/concepts/linq/how-to-add-custom-methods-for-linq-queries.md)

## <a name="multiple-threads-and-async-processing"></a>Birden çok iş parçacığı ve async işleme

Modern programlar genellikle eşzamanlı işlemler kullanır. Bu makaleler bu teknikleri kullanmayı öğrenmenize yardımcı olacaktır.

- [Kullanarak async `System.Threading.Tasks.Task.WhenAll`performansını artırın. ](../programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
- [Kullanarak paralel olarak birden `async` `await`çok web isteği yapın ve. ](../programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
- [İş parçacığı havuzu kullanın.](../../standard/threading/the-managed-thread-pool.md#using-the-thread-pool)

## <a name="command-line-args-to-your-program"></a>Komut satırı programınıza args

Genellikle, C# programları komut satırı bağımsız değişkenleri vardır. Bu makaleler, bu komut satırı bağımsız değişkenlerine erişmenizi ve işlemenizi öğretir.

- [Tüm komut satırı `for`bağımsız değişkenlerini . ](../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
