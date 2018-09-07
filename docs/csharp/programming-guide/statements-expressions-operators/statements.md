---
title: Deyimler (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- statements [C#], about statements
- C# language, statements
ms.assetid: 901bcde7-87de-4e15-833c-f9cfd40c8ce3
ms.openlocfilehash: 515ae6bb6030e80c80289ff888f07ade2f341792
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44080091"
---
# <a name="statements-c-programming-guide"></a>Deyimler (C# Programlama Kılavuzu)
Bir programı alan eylemleri deyimlerinde ifade edilir. Ortak Eylemler değişkenleri bildirme, değerler atama, koleksiyonlar üzerinden döngü oluşturma ve bir ya da başka bir verili bir koşula bağlı kod bloğu için dallanma metotları çağırma içerir. Deyimleri bir programda yürütüldüğü sırada, denetim akışı veya, yürütmenin akışını çağrılır. Denetim akışı nasıl program çalışma zamanında aldığı giriş tepki verdiğini bağlı olarak bir program çalıştırıldığında her zaman değişiklik gösterebilir.  
  
 Bir ifade, tek satırlık bir noktalı virgülle biter kod ya da tek satırlı ifadeleri bir blok içinde bir dizi oluşabilir. Bir deyim bloğunu içine {} köşeli ayraçlar ve iç içe geçmiş blok içerebilir. Aşağıdaki kod, iki örnek tek satır deyimlerinin yanı sıra, çok satırlı deyim bloğunu gösterir:  
  
 [!code-csharp[csProgGuideStatements#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_1.cs)]  
  
## <a name="types-of-statements"></a>Tür ifadeleri  
 Aşağıdaki tablo, C# ve daha fazla bilgi içeren konulara bağlantılar ile bunların ilişkili anahtar sözcükleri deyimlerinde çeşitli türlerde listeler:  
  
|Kategori|C# anahtar sözcükleri / notları|  
|--------------|---------------------------|  
|[Bildirim deyimleri](#declaration-statements)|Yeni bir değişken veya sabit bir bildirim deyiminin tanıtır. Bir değişken bildirimi, isteğe bağlı olarak bir değişkene bir değer atayabilirsiniz. Sabit bir bildirimde atama gereklidir.|  
|[İfade deyimleri](expressions.md)|Bir değeri hesaplayabilir ifade deyimleri, bir değişken değeri depolamanız gerekir. Daha fazla bilgi için [ifade deyimleri](#expression-statements).|  
|[Seçim deyimleri](../../../csharp/language-reference/keywords/selection-statements.md)|Seçim deyimleri kod, bir veya daha fazla belirli koşullara bağlı olarak farklı bölümlerini dala olanak sağlar. Daha fazla bilgi için aşağıdaki konulara bakın:<br /><br /> [varsa](../../../csharp/language-reference/keywords/if-else.md), [başka](../../../csharp/language-reference/keywords/if-else.md), [geçiş](../../../csharp/language-reference/keywords/switch.md), [çalışması](../../../csharp/language-reference/keywords/switch.md)|  
|[Yineleme deyimleri](../../../csharp/language-reference/keywords/iteration-statements.md)|Yineleme deyimleri diziler gibi koleksiyonlar üzerinden döngü etkinleştirmeniz veya belirtilen bir koşul yerine getirilene kadar deyimleri aynı kümesini tekrar tekrar gerçekleştirin. Daha fazla bilgi için aşağıdaki konulara bakın:<br /><br /> [yapmak](../../../csharp/language-reference/keywords/do.md), [için](../../../csharp/language-reference/keywords/for.md), [foreach](../../../csharp/language-reference/keywords/foreach-in.md), [içinde](../../../csharp/language-reference/keywords/foreach-in.md), [sırada](../../../csharp/language-reference/keywords/while.md)|  
|[Atlama deyimleri](../../../csharp/language-reference/keywords/jump-statements.md)|Deyimleri Aktarım Denetimi başka bir bölüme atlayın. Daha fazla bilgi için aşağıdaki konulara bakın:<br /><br /> [Kesme](../../../csharp/language-reference/keywords/break.md), [devam](../../../csharp/language-reference/keywords/continue.md), [varsayılan](../../../csharp/language-reference/keywords/switch.md), [goto](../../../csharp/language-reference/keywords/goto.md), [dönüş](../../../csharp/language-reference/keywords/return.md), [yield](../../../csharp/language-reference/keywords/yield.md)|  
|[Özel durum işleme deyimleri](../../../csharp/language-reference/keywords/exception-handling-statements.md)|Özel durum işleme deyimleri düzgün bir şekilde çalışma zamanında gerçekleşen özel durumları kurtarmanıza olanak tanır. Daha fazla bilgi için aşağıdaki konulara bakın:<br /><br /> [throw](../../../csharp/language-reference/keywords/throw.md), [try-catch](../../../csharp/language-reference/keywords/try-catch.md), [try-finally](../../../csharp/language-reference/keywords/try-finally.md), [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)|  
|[Checked ve unchecked](../../../csharp/language-reference/keywords/checked-and-unchecked.md)|İşaretli ve işaretsiz ifadeler sayısal işlemleri sonucu sonuç değerini tutmak için çok küçük bir değişkende depolanan bir taşma zaman neden izin verilip verilmeyeceğini belirtmenizi sağlar. Daha fazla bilgi için [kullanıma](../../../csharp/language-reference/keywords/checked.md) ve [denetlenmeyen](../../../csharp/language-reference/keywords/unchecked.md).|  
|`await` Deyimi|Bir yöntem ile işaretlerseniz [zaman uyumsuz](../../../csharp/language-reference/keywords/async.md) kullanabileceğiniz değiştiricisi [await](../../../csharp/language-reference/keywords/await.md) yönteminde işleci. Ulaştığında denetlemek bir `await` zaman uyumsuz yöntemin ifadesinde, Denetim çağırana döner ve awaited görevi tamamlanıncaya kadar yöntemin ediyor askıya alındı. Görev tamamlandığında, yürütme yönteminde devam edebilir.<br /><br /> Basit bir örnek için bkz. "Zaman uyumsuz yöntemler" bölümünü [yöntemleri](../../../csharp/programming-guide/classes-and-structs/methods.md). Daha fazla bilgi için [Asynchronous Programming with async ve await](../../../csharp/programming-guide/concepts/async/index.md).|  
|`yield return` Deyimi|Bir yineleyici listesini veya bir dizi gibi bir koleksiyon üzerinde özel yineleme gerçekleştirir. Yineleyici [yield return](../../../csharp/language-reference/keywords/yield.md) her öğeyi bir defada döndürmek için deyimi. Olduğunda bir `yield return` deyimine ulaşıldığında, kodun geçerli konumu anımsanacak. Yürütme, yineleyici sonraki sefer çağrıldığında bu konumdan yeniden başlatılır.<br /><br /> Daha fazla bilgi için [yineleyiciler](../../../csharp/programming-guide/concepts/iterators.md).|  
|`fixed` Deyimi|Fixed deyimi, çöp toplayıcı taşınabilir bir değişken yerini değiştirme alanından engeller. Daha fazla bilgi için [sabit](../../../csharp/language-reference/keywords/fixed-statement.md).|  
|`lock` Deyimi|Lock deyimi, bir kerede yalnızca bir iş parçacığına kod bloklarını erişimi sınırlamak sağlar. Daha fazla bilgi için [kilit](../../../csharp/language-reference/keywords/lock-statement.md).|  
|Etiketli deyimler|Bir deyimi bir etiket verin ve ardından [goto](../../../csharp/language-reference/keywords/goto.md) etiketli deyime atlamak için anahtar sözcüğü. (Aşağıdaki satırı örneğe bakın.)|  
|[Boş deyim](#the-empty-statement)|Boş deyim tek noktalı virgül içerir. Bu, hiçbir şey yapmaz ve burada bir deyim gereklidir ancak herhangi bir işlem yapılması gerekiyor yerde kullanılabilir.|  
  
## <a name="declaration-statements"></a>Bildirim deyimleri

Aşağıdaki kod ilk ataması olmadan ve değişken bildirimleri ve sabit bir bildirimde ile gerekli başlatma örneklerini gösterir.

[!code-csharp[csProgGuideStatements#23](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_2.cs)]

## <a name="expression-statements"></a>İfade deyimleri

Aşağıdaki kod, ifade deyimleri, atama, atama ve yöntem çağrısının ile nesne oluşturma da dahil olmak üzere örneklerini gösterir.

[!code-csharp[csProgGuideStatements#24](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_3.cs)]

## <a name="the-empty-statement"></a>Boş deyim

Aşağıdaki örnekler, iki kullanım için boş bir deyimi göstermektedir:

[!code-csharp[csProgGuideStatements#25](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_4.cs)]

## <a name="embedded-statements"></a>Katıştırılmış ifadeler

 Dahil olmak üzere, bazı deyimleri [yapmak](../../../csharp/language-reference/keywords/do.md), [sırada](../../../csharp/language-reference/keywords/while.md), [için](../../../csharp/language-reference/keywords/for.md), ve [foreach](../../../csharp/language-reference/keywords/foreach-in.md), bunları izleyen bir katıştırılmış deyim her zaman vardır. Bu katıştırılmış deyimi tek bir deyim ya da birden çok deyim tarafından alınmış olabilir {} bir deyim bloğunu ayraç. Katıştırılmış deyimler bile tek satır içine {} köşeli ayraçlar, aşağıdaki örnekte gösterildiği gibi:  
  
 [!code-csharp[csProgGuideStatements#26](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_5.cs)]  
  
 İçinde içine alınmamış bir katıştırılmış deyim {} ayraçlar bir bildirim deyiminin veya etiketlenmiş deyim olamaz. Bu, aşağıdaki örnekte gösterilmiştir:  
  
 [!code-csharp[csProgGuideStatements#27](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_6.cs)]  
  
 Hatayı düzeltmek için bir blok içinde gömülü deyim koyun:  
  
 [!code-csharp[csProgGuideStatements#28](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_7.cs)]  
  
## <a name="nested-statement-blocks"></a>İç içe geçmiş deyim blokları  
 Aşağıdaki kodda gösterildiği gibi deyim blokları yuvalanabilir:  
  
 [!code-csharp[csProgGuideStatements#29](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_8.cs)]  
  
## <a name="unreachable-statements"></a>Erişilemeyen deyimleri  
 Derleyici denetim akışını belirli bir ifadenin tüm koşullar altında hiçbir zaman ulaşabilir belirlerse, bu CS0162, uyarı aşağıdaki örnekte gösterildiği gibi üretecektir:  
  
 [!code-csharp[csProgGuideStatements#22](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_9.cs)]  
  
## <a name="related-sections"></a>İlgili Bölümler  
  
-   [Deyim Anahtar Sözcükleri](../../../csharp/language-reference/keywords/statement-keywords.md)  
  
-   [İfadeler](../../../csharp/programming-guide/statements-expressions-operators/expressions.md)  
  
-   [İşleçler](../../../csharp/programming-guide/statements-expressions-operators/operators.md)  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
