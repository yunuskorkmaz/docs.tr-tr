---
title: Deyimler (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- statements [C#], about statements
- C# language, statements
ms.assetid: 901bcde7-87de-4e15-833c-f9cfd40c8ce3
ms.openlocfilehash: 68f7f799ebbfe52c99820083eb22761c79f66483
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="statements-c-programming-guide"></a>Deyimler (C# Programlama Kılavuzu)
Bir programın sürüyor Eylemler deyimlerinde ifade edilir. Ortak Eylemler değişkenleri bildirme, değerler atama, koleksiyonlar üzerinden döngü oluşturma ve verilen bir koşul bağlı olarak kod bloğu bir ya da başka bir dal oluşturma yöntemleri çağırma içerir. Deyimleri bir programda yürütülme sırasını denetim akışı veya akışını çağrılır. Denetim akışını nasıl programın çalışma zamanında aldığını giriş tepki verdiğini bağlı olarak bir program çalıştırıldığında her zaman değişebilir.  
  
 Bir deyim tek satırlık bir noktalı virgül ile biten kod veya tek satırlık ifadeleri bir blok içinde bir dizi oluşabilir. Bir ifade bloğu sınırlanan {} köşeli ayraçlar ve iç içe geçmiş blokları içerebilir. Aşağıdaki kod iki örnek tek satırlı deyimlerinin ve çok satırlı deyimi bloğu gösterir:  
  
 [!code-csharp[csProgGuideStatements#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_1.cs)]  
  
## <a name="types-of-statements"></a>Deyimleri türleri  
 Aşağıdaki tabloda çeşitli deyimleri C# ve daha fazla bilgi içeren konulara bağlantılar ile bunların ilişkili anahtar sözcükleri listeler:  
  
|Kategori|C# anahtar sözcükleri / Notlar|  
|--------------|---------------------------|  
|Bildirim deyimleri|Bir bildirim deyimi yeni değişken ya da sabiti tanıtır. Bir değişken bildirimi isteğe bağlı olarak değişkeni için bir değer atayabilirsiniz. Bir sabit bildiriminde atama gereklidir.<br /><br /> [!code-csharp[csProgGuideStatements#23](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_2.cs)]|  
|İfade deyimleri|Bir değeri hesaplamak ifade deyimleri değer bir değişkende saklamanız gerekir.<br /><br /> [!code-csharp[csProgGuideStatements#24](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_3.cs)]|  
|[Seçim deyimleri](../../../csharp/language-reference/keywords/selection-statements.md)|Seçim deyimleri bir veya daha fazla belirtilen koşullara bağlı olarak kod farklı bölümlerini dallanma olanak sağlar. Daha fazla bilgi için aşağıdaki konulara bakın:<br /><br /> [varsa](../../../csharp/language-reference/keywords/if-else.md), [başka](../../../csharp/language-reference/keywords/if-else.md), [geçiş](../../../csharp/language-reference/keywords/switch.md), [durumu](../../../csharp/language-reference/keywords/switch.md)|  
|[Yineleme deyimleri](../../../csharp/language-reference/keywords/iteration-statements.md)|Yineleme deyimleri diziler gibi koleksiyonlar üzerinden döngü sağlamak veya belirtilen koşul yerine getirilene kadar deyimleri aynı kümesini tekrar tekrar gerçekleştirin. Daha fazla bilgi için aşağıdaki konulara bakın:<br /><br /> [yapmak](../../../csharp/language-reference/keywords/do.md), [için](../../../csharp/language-reference/keywords/for.md), [foreach](../../../csharp/language-reference/keywords/foreach-in.md), [içinde](../../../csharp/language-reference/keywords/foreach-in.md), [sırada](../../../csharp/language-reference/keywords/while.md)|  
|[Atlama deyimleri](../../../csharp/language-reference/keywords/jump-statements.md)|Aktarım Denetim ifadeleri kodunun başka bir bölüme geçin. Daha fazla bilgi için aşağıdaki konulara bakın:<br /><br /> [BREAK](../../../csharp/language-reference/keywords/break.md), [devam](../../../csharp/language-reference/keywords/continue.md), [varsayılan](../../../csharp/language-reference/keywords/switch.md), [goto](../../../csharp/language-reference/keywords/goto.md), [dönmek](../../../csharp/language-reference/keywords/return.md), [verim](../../../csharp/language-reference/keywords/yield.md)|  
|[Özel durum işleme deyimleri](../../../csharp/language-reference/keywords/exception-handling-statements.md)|Özel durum işleme deyimleri gerçekleşen çalışma zamanında gerçekleşen özel durumları rahat olanak sağlar. Daha fazla bilgi için aşağıdaki konulara bakın:<br /><br /> [throw](../../../csharp/language-reference/keywords/throw.md), [try-catch](../../../csharp/language-reference/keywords/try-catch.md), [try-finally](../../../csharp/language-reference/keywords/try-finally.md), [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)|  
|[Checked ve unchecked](../../../csharp/language-reference/keywords/checked-and-unchecked.md)|Checked ve Denetlenmeyen ifadeler sayısal işlem sonucu elde edilen değer tutamayacak kadar küçük bir değişkende depolanan taşma neden izin verilip verilmeyeceğini belirtmenizi sağlar. Daha fazla bilgi için bkz: [işaretli](../../../csharp/language-reference/keywords/checked.md) ve [denetlenmeyen](../../../csharp/language-reference/keywords/unchecked.md).|  
|`await` Deyimi|Bir yöntem ile işaretlerseniz [zaman uyumsuz](../../../csharp/language-reference/keywords/async.md) kullanabileceğiniz değiştiricisi, [await](../../../csharp/language-reference/keywords/await.md) yönteminde işleci. Ulaştığında denetlemek bir `await` async yöntemi ifadesinde, Denetim çağırana döndürür ve awaited görevi tamamlanana kadar yöntemi ediyor askıya alındı. Görev tamamlandığında, yürütme yönteminde devam edebilirsiniz.<br /><br /> Basit bir örnek için "Zaman uyumsuz yöntemleri" bölümüne bakın [yöntemleri](../../../csharp/programming-guide/classes-and-structs/methods.md). Daha fazla bilgi için bkz: [zaman uyumsuz programlama ile async ve await](../../../csharp/programming-guide/concepts/async/index.md).|  
|`yield return` Deyimi|Yineleyici özel bir yineleme listesini veya bir dizi gibi bir koleksiyon üzerinden gerçekleştirir. Yineleyici kullanan [verim return](../../../csharp/language-reference/keywords/yield.md) her öğeye aynı anda geri dönmek için deyimi. Zaman bir `yield return` deyimi ulaşıldığında geçerli kod konumda anımsanacak. Yineleyici sonraki çağrıldığında yürütme o konumdan yeniden başlatılır.<br /><br /> Daha fazla bilgi için bkz: [yineleyiciler](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).|  
|`fixed` Deyimi|Fixed deyimi taşınabilir bir değişken yerini değiştirme atık toplayıcı engeller. Daha fazla bilgi için bkz: [sabit](../../../csharp/language-reference/keywords/fixed-statement.md).|  
|`lock` Deyimi|Lock deyimi, aynı anda yalnızca bir iş parçacığı için kod blokları erişimi sınırlamak sağlar. Daha fazla bilgi için bkz: [kilit](../../../csharp/language-reference/keywords/lock-statement.md).|  
|Etiketli deyimler|Bir deyim bir etiket verin ve ardından [goto](../../../csharp/language-reference/keywords/goto.md) etiketli deyim atlamak için anahtar sözcüğü. (Aşağıdaki satırı örneğe bakın.)|  
|Boş deyim|Boş deyim, tek bir noktalı virgül oluşur. Hiçbir şey yapmaz ve burada bir deyim gereklidir ancak herhangi bir işlem yapılması gerekiyor yerde kullanılabilir. Aşağıdaki örnekler, boş bir deyimi iki kullanımları gösterir:<br /><br /> [!code-csharp[csProgGuideStatements#25](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_4.cs)]|  
  
## <a name="embedded-statements"></a>Katıştırılmış ifadeler  
 Dahil olmak üzere bazı deyimleri [yapmak](../../../csharp/language-reference/keywords/do.md), [sırada](../../../csharp/language-reference/keywords/while.md), [için](../../../csharp/language-reference/keywords/for.md), ve [foreach](../../../csharp/language-reference/keywords/foreach-in.md), onları izleyen bir katıştırılmış deyimi her zaman vardır. Bu katıştırılmış deyimi tek bir deyimde veya birden çok deyime kapsadığı olabilir {} deyimi blok köşeli. Tek satırlı bile katıştırılmış ifadeler içine {} , aşağıdaki örnekte gösterildiği gibi köşeli ayraçlar:  
  
 [!code-csharp[csProgGuideStatements#26](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_5.cs)]  
  
 İçinde içine alınmamış bir katıştırılmış deyimi {} köşeli bildirimi deyimi veya etiketli deyim olamaz. Bu aşağıdaki örnekte gösterilmiştir:  
  
 [!code-csharp[csProgGuideStatements#27](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_6.cs)]  
  
 Katıştırılmış deyimi hatayı düzeltmek için bir blok koyun:  
  
 [!code-csharp[csProgGuideStatements#28](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_7.cs)]  
  
## <a name="nested-statement-blocks"></a>İç içe geçmiş deyim blokları  
 Deyim blokları, aşağıdaki kodda gösterildiği gibi iç içe olabilir:  
  
 [!code-csharp[csProgGuideStatements#29](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_8.cs)]  
  
## <a name="unreachable-statements"></a>Ulaşılamaz deyimleri  
 Denetim akışı hiçbir koşulda belirli bir ifadenin hiçbir zaman ulaşabilir derleyici belirlerse, bu CS0162, uyarı aşağıdaki örnekte gösterildiği gibi üretir:  
  
 [!code-csharp[csProgGuideStatements#22](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/statements_9.cs)]  
  
## <a name="related-sections"></a>İlgili Bölümler  
  
-   [Deyim Anahtar Sözcükleri](../../../csharp/language-reference/keywords/statement-keywords.md)  
  
-   [İfadeler](../../../csharp/programming-guide/statements-expressions-operators/expressions.md)  
  
-   [İşleçler](../../../csharp/programming-guide/statements-expressions-operators/operators.md)  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
