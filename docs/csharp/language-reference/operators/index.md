---
title: C# İşleçleri
ms.date: 04/04/2018
f1_keywords:
- cs.operators
helpviewer_keywords:
- boolean operators [C#]
- expressions [C#], operators
- logical operators [C#]
- operators [C#]
- Visual C#, operators
- indirection operators [C#]
- assignment operators [C#]
- shift operators [C#]
- relational operators [C#]
- bitwise operators [C#]
- address operators [C#]
- keywords [C#], operators
- arithmetic operators [C#]
ms.assetid: 0301e31f-22ad-49af-ac3c-d5eae7f0ac43
ms.openlocfilehash: 2b0441dfebb6692cbea0d1ab7909d7b8f04490cb
ms.sourcegitcommit: 78bcb629abdbdbde0e295b4e81f350a477864aba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/08/2018
ms.locfileid: "34457615"
---
# <a name="c-operators"></a>C# İşleçleri
C# (matematik, dizin oluşturma, işlev çağrısı, vb.) bir ifadede gerçekleştirilecek işlemleri belirten simgelerdir birçok işleçleri sağlar. Yapabilecekleriniz [aşırı](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md) işleçlerinin çoğu kullanıcı tanımlı bir türe başvurulduğunda anlamının değiştirin.  
  
 Tamsayı türlerinde işlemler (gibi `==`, `!=`, `<`, `>`, `&`, `|`) genellikle numaralandırma üzerinde izin verilir (`enum`) türleri.  
  
 Aşağıdaki bölümlerde, en yüksek önceliğe düşüğe başlayarak C# işleçleri listeler. Her bölüm içerisindeki işleçler aynı öncelik düzeyine paylaşın.  
 
## <a name="primary-operators"></a>Birincil Operatörler  
 En yüksek öncelik işleçleri şunlardır.
  
 [x.y](../../../csharp/language-reference/operators/member-access-operator.md) – üye erişimi.  
  
 [x? y](../../../csharp/language-reference/operators/null-conditional-operators.md) – null koşullu üye erişimi. Döndürür `null` sol işlenen değerlendirilirse `null`.  
 
 [x? [y] ](../../../csharp/language-reference/operators/null-conditional-operators.md) -null koşullu dizin erişim. Döndürür `null` sol işlenen değerlendirilirse `null`.
 
 [f(x)](../../../csharp/language-reference/operators/invocation-operator.md) – işlev çağırma.  
  
 [bir&#91;x&#93; ](../../../csharp/language-reference/operators/index-operator.md) – toplama nesnesi dizin oluşturma.  
   
 [x ++](../../../csharp/language-reference/operators/increment-operator.md) – sonek artırma. X değerini döndürür ve ardından depolama konumu büyük bir x değeri ile güncelleştirir (genellikle 1 tamsayı ekler).  
  
 [x--](../../../csharp/language-reference/operators/decrement-operator.md) – son ek azaltma. X değerini döndürür ve ardından depolama konumu bir daha az x değeri ile güncelleştirir (genellikle 1 tamsayı çıkarır).  
  
 [Yeni](../../../csharp/language-reference/keywords/new-operator.md) – oluşturmada yazın.  
  
 [typeof](../../../csharp/language-reference/keywords/typeof.md) – döndürür <xref:System.Type> işlenen temsil eden nesne.  
  
 [işaretli](../../../csharp/language-reference/keywords/checked.md) – taşma denetimi için tamsayı işlemleri sağlar.  
  
 [denetlenmeyen](../../../csharp/language-reference/keywords/unchecked.md) – taşma tamsayı işlemlerinde denetimini devre dışı bırakır. Varsayılan derleyici davranışı budur.  
  
 [Default(T)](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md) – t türü varsayılan değerini üretir  
  
 [Temsilci](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) – bildirir ve temsilci örneği döndürür.  
  
 [sizeof](../../../csharp/language-reference/keywords/sizeof.md) -türü işlenen bayt cinsinden boyutunu döndürür.  
  
 [->](../../../csharp/language-reference/operators/dereference-operator.md) – Birleştirilmiş üye erişimi ile işaretçiye başvuruluyor.  
  
## <a name="unary-operators"></a>Birli İşleçler  
 Bu işleçler, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahip.  
  
 [+ x](../../../csharp/language-reference/operators/addition-operator.md) – x değerini döndürür.  
  
 [-x](../../../csharp/language-reference/operators/subtraction-operator.md) – sayısal olumsuzlama.  
  
 [\!x](../../../csharp/language-reference/operators/logical-negation-operator.md) – mantıksal olumsuzlama.  
  
 [~ x](../../../csharp/language-reference/operators/bitwise-complement-operator.md) – bit düzeyinde tamamlayıcı.  
  
 [++ x](../../../csharp/language-reference/operators/increment-operator.md) – önek artırma. Depolama konumu bir x değeriyle güncelleştirdikten sonra x değerini büyük döndürür (genellikle 1 tamsayı ekler).  
  
 [--x](../../../csharp/language-reference/operators/decrement-operator.md) – önek azaltma. Depolama konumu daha az bir x değeriyle güncelleştirdikten sonra x değeri döndürür (genelde tam sayı 1 çıkarır).  
  
 [(T) x](../../../csharp/language-reference/operators/invocation-operator.md) – atama yazın.  
  
 [await](../../../csharp/language-reference/keywords/await.md) – bekler bir `Task`.  
  
 [& x](../../../csharp/language-reference/operators/and-operator.md) – adresidir.  
  
 [* x](../../../csharp/language-reference/operators/multiplication-operator.md) – başvurusunu kaldırma.  
  
## <a name="multiplicative-operators"></a>Çarpma İşleçleri  
 Bu işleçler, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahip.  
  
 [x * y](../../../csharp/language-reference/operators/multiplication-operator.md) – çarpma.  
  
 [x / y](../../../csharp/language-reference/operators/division-operator.md) – bölme. İşlenenler tamsayılar, sonuç sıfıra yakınsayarak kesilmiş bir tamsayıdır (örneğin, `-7 / 2 is -3`).  
  
 [% y x](../../../csharp/language-reference/operators/remainder-operator.md) – kalan. İşlenen tamsayılar olursa bu y bölme x geri kalanı döndürür.  Varsa `q = x / y` ve `r = x % y`, ardından `x = q * y + r`.  
  
## <a name="additive-operators"></a>Toplama İşleçleri  
 Bu işleçler, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahip.  
  
 [x + y](../../../csharp/language-reference/operators/addition-operator.md) – ekleme.  
  
 [x-y](../../../csharp/language-reference/operators/subtraction-operator.md) – çıkarma.  
  
## <a name="shift-operators"></a>Kaydırma İşleçleri  
 Bu işleçler, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahip.  
  
 [x <\< y](../../../csharp/language-reference/operators/left-shift-operator.md) – bitlerini sola kaydırma ve sağ taraftaki sıfır ile doldurun.  
  
 [x >> y](../../../csharp/language-reference/operators/right-shift-operator.md) – sağ shift bitleri. Sol işlenen ise `int` veya `long`, sonra da sol bit imza biti ile doldurulur. Sol işlenen ise `uint` veya `ulong`, sonra da sol bitler sıfır ile doldurulur.  
  
## <a name="relational-and-type-testing-operators"></a>İlişkisel ve tür testi işleçleri  
 Bu işleçler, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahip.  
  
 [x \< y](../../../csharp/language-reference/operators/less-than-operator.md) – (x, y değerinden ise true) küçüktür.  
  
 [x > y](../../../csharp/language-reference/operators/greater-than-operator.md) – büyük (x, y büyükse true).  
  
 [x \<y =](../../../csharp/language-reference/operators/less-than-equal-operator.md) – küçük veya eşittir.  
  
 [x > y =](../../../csharp/language-reference/operators/greater-than-equal-operator.md) – büyüktür veya eşittir.  
  
 [olan](../../../csharp/language-reference/keywords/is.md) – uyumluluk yazın. Değerlendirilen sol işlenen sağ işlenen (statik türü) belirtilen türe dönüştürülebilir ise true döndürür.  
  
 [olarak](../../../csharp/language-reference/keywords/as.md) – dönüştürmesi yazın. (Bir statik türü), sağ işlenen tarafından belirtilen tür için sol işlenen döndürür ancak `as` döndürür `null` burada `(T)x` bir özel durum oluşturması.  
  
## <a name="equality-operators"></a>Eşitlik İşleçleri  
 Bu işleçler, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahip.  
  
 [x == y](../../../csharp/language-reference/operators/equality-comparison-operator.md) – eşitlik. Varsayılan olarak, başvuru için türleri dışındaki `string`, bu başvuru eşitliği (kimlik test) döndürür. Ancak, türleri aşırı yüklenebilir `==`, amacınız kimliğini test etmek için ise kullanmak en iyisidir `ReferenceEquals` metodunda `object`.  
  
 [x! = y](../../../csharp/language-reference/operators/not-equal-operator.md) – eşit değil. Açıklama için bkz. `==`. Bir tür aşırı `==`, aşırı gerekir sonra `!=`.  
  
## <a name="logical-and-operator"></a>Mantıksal AND işleci  
 Bu işleç, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahiptir.  
  
 [x ve y](../../../csharp/language-reference/operators/and-operator.md) – mantıksal ve bit düzeyinde and Bu genellikle tamsayı türleri ile kullanabilirsiniz ve `enum` türleri.  
  
## <a name="logical-xor-operator"></a>Mantıksal XOR işleci  
 Bu işleç, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahiptir.  
  
 [x ^ y](../../../csharp/language-reference/operators/xor-operator.md) – mantıksal ve bit düzeyinde XOR. Bu genellikle tamsayı türleri ile kullanabilirsiniz ve `enum` türleri.  
  
## <a name="logical-or-operator"></a>Mantıksal OR işleci  
 Bu işleç, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahiptir.  
  
 [x &#124; y](../../../csharp/language-reference/operators/or-operator.md) – mantıksal ve bit düzeyinde OR. Bu genellikle tamsayı türleri ile kullanabilirsiniz ve `enum` türleri.  
  
## <a name="conditional-and-operator"></a>Koşullu AND işleci  
 Bu işleç, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahiptir.  
  
 [x & & y](../../../csharp/language-reference/operators/conditional-and-operator.md) – mantıksal and İlk işlenen false olarak değerlendirilirse, ardından C# ikinci işlenenin değerlendirmez.  
  
## <a name="conditional-or-operator"></a>Koşullu OR işleci  
 Bu işleç, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahiptir.  
  
 [x &#124; &#124; y](../../../csharp/language-reference/operators/conditional-or-operator.md) – mantıksal OR. İlk işlenen true olarak değerlendirilirse, ardından C# ikinci işlenenin değerlendirmez.  
  
## <a name="null-coalescing-operator"></a>Null birleşim işleci  
 Bu işleç, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahiptir.  
  
 [x?? y](../../../csharp/language-reference/operators/null-coalescing-operator.md) – döndürür `x` olmayan ise`null`; Aksi halde döndürür `y`.  
  
## <a name="conditional-operator"></a>Koşullu işleç  
 Bu işleç, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahiptir.  
  
 [t? x: y](../../../csharp/language-reference/operators/conditional-operator.md) – test `t` true, ardından değerlendirilip döndürülecek değerlendirir `x`; Aksi takdirde, değerlendirilip döndürülecek `y`.  
  
## <a name="assignment-and-lambda-operators"></a>Atama ve Lambda işleçleri  
 Bu işleçler, sonraki bölümde daha yüksek bir önceliğe ve önceki bölümde daha düşük önceliğe sahip.  
  
 [x = y](../../../csharp/language-reference/operators/assignment-operator.md) – atama.  
  
 [x += y](../../../csharp/language-reference/operators/addition-assignment-operator.md) – artırma. Değerini ekleme `y` değerine `x`, sonuçta depolamak `x`ve yeni bir değer. Varsa `x` atayan bir `event`, ardından `y` C# bir olay işleyicisi ekler uygun bir işlev olmalıdır.  
  
 [x-= y](../../../csharp/language-reference/operators/subtraction-assignment-operator.md) – azaltma. Değerini çıkarma `y` değerinden `x`, sonuçta depolamak `x`ve yeni bir değer. Varsa `x` atayan bir `event`, ardından `y` C# kaldıran bir olay işleyicisi uygun bir işlev olmalıdır  
  
 [x * y =](../../../csharp/language-reference/operators/multiplication-assignment-operator.md) – çarpma atama. Çarp değeri `y` değerine `x`, sonuçta depolamak `x`ve yeni bir değer.  
  
 [x / y =](../../../csharp/language-reference/operators/division-assignment-operator.md) – bölme ataması. Değerini ayırmak `x` değeriyle `y`, sonuçta depolamak `x`ve yeni bir değer.  
  
 [%x y =](../../../csharp/language-reference/operators/remainder-assignment-operator.md) – kalanını atama. Değerini ayırmak `x` değeriyle `y`, kalanı depolamak `x`ve yeni bir değer.  
  
 [x & y =](../../../csharp/language-reference/operators/and-assignment-operator.md) – ve atama. DEĞERİ `y` değeriyle `x`, sonuçta depolamak `x`ve yeni bir değer.  
  
 [x &#124;y =](../../../csharp/language-reference/operators/or-assignment-operator.md) – OR ataması. YA da değerini `y` değeriyle `x`, sonuçta depolamak `x`ve yeni bir değer.  
  
 [x ^ y =](../../../csharp/language-reference/operators/xor-assignment-operator.md) – XOR atama. XOR değeri, `y` değeriyle `x`, sonuçta depolamak `x`ve yeni bir değer.  
  
 [x << y =](../../../csharp/language-reference/operators/left-shift-assignment-operator.md) – sola kaydırma ataması. Değerini kaydırma `x` sol tarafından `y` yerde depolamak sonucunda `x`ve yeni bir değer.  
  
 [x >> y =](../../../csharp/language-reference/operators/right-shift-assignment-operator.md) – sağa kaydırma ataması. Değerini kaydırma `x` sağa `y` yerde depolamak sonucunda `x`ve yeni bir değer.  
  
 [=>](../../../csharp/language-reference/operators/lambda-operator.md) – lambda bildirimi.  
  
## <a name="arithmetic-overflow"></a>Aritmetik Taşma  
 Aritmetik işleçler ([+](../../../csharp/language-reference/operators/addition-operator.md), [ - ](../../../csharp/language-reference/operators/subtraction-operator.md), [ * ](../../../csharp/language-reference/operators/multiplication-operator.md), [ / ](../../../csharp/language-reference/operators/division-operator.md)) can sayısal tür için olası değerler aralığının dışında olan sonuçlar üretir. Ayrıntılar için ancak genel olarak belirli bir işlecin bölümüne bakabilir:  
  
- Tamsayı aritmetik taşma da bir <xref:System.OverflowException> ya da sonucun en önemli bitlerini atar. Sıfır ile tamsayı bölme her zaman oluşturur bir <xref:System.DivideByZeroException>.  

   Tamsayı taşması oluştuğunda olabilen yürütme bağlamında ne olacağı bağlıdır [işaretli veya işaretsiz](../../../csharp/language-reference/keywords/checked-and-unchecked.md). Denetlenen bir bağlamda bir <xref:System.OverflowException> oluşturulur. İşaretlenmemiş bir bağlamda, sonucun en önemli bitleri atılır ve yürütme devam eder. Bu nedenle, C#, işleme veya taşmayı yoksayma seçmenizi sağlar. Varsayılan olarak, aritmetik işlemler oluşan bir *denetlenmeyen* bağlamı. 

   Aritmetik işlemler ek olarak, integral türünden integral türü atamaları taşmaya neden olabilir (olduğunda cast gibi'bir [uzun](../../../csharp/language-reference/keywords/long.md) için bir [int](../../../csharp/language-reference/keywords/int.md)) ve işaretli veya işaretsiz yürütme tabidir. Ancak, bit düzeyinde işleçler ve kaydırma işleçleri asla taşmaya neden olmaz.  
   
-   Kayan nokta aritmetik taşma ya da sıfıra bölme hiçbir zaman bir özel durum oluşturur, kayan nokta türleri IEEE 754 ve bunu temel aldığından, sonsuzluk ve NaN (sayı değil) temsil eden hükümlerine vardır.  
  
-   [Ondalık](../../../csharp/language-reference/keywords/decimal.md) aritmetik taşma her zaman oluşturur bir <xref:System.OverflowException>. Sıfır ile ondalık bölme her zaman oluşturur bir <xref:System.DivideByZeroException>.  
  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C#](../../../csharp/index.md) [fazla yüklenebilir işleçler](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)
