---
title: C# İşleçleri
ms.date: 03/09/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
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
caps.latest.revision: ''
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 14ebd489c48f53c8618cadf91f9744bb30f582d3
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/28/2018
---
# <a name="c-operators"></a>C# İşleçleri
C# (matematik, dizin oluşturma, işlev çağrısı, vb.) bir ifadede gerçekleştirmek için hangi işlemleri belirtin simgelerdir birçok işleçleri sağlar. Yapabilecekleriniz [aşırı](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md) kullanıcı tanımlı bir tür uygulandığında anlamları değiştirmek için çok sayıda işleci.  
  
 Tam sayı türleri üzerinde işlemler (gibi `==`, `!=`, `<`, `>`, `&`, `|`) genellikle numaralandırma üzerinde izin verilir (`enum`) türleri.  
  
 Aşağıdaki bölümler en yüksek önceliği en düşük başlayarak C# işleçleri listeleyin. Her bölüm içerisindeki işleçleri aynı öncelik düzeyine paylaşır.  
 
## <a name="primary-operators"></a>Birincil Operatörler  
 En yüksek öncelik işleçleri bunlar.
  
 [x.y](../../../csharp/language-reference/operators/member-access-operator.md) – üye erişimi.  
  
 [x?. y](../../../csharp/language-reference/operators/null-conditional-operators.md) – null koşullu üye erişimi. Döndürür `null` sol işleneni değerlendirilirse `null`.  
 
 [x? [y] ](../../../csharp/language-reference/operators/null-conditional-operators.md) -null koşullu dizin erişim. Döndürür `null` sol işleneni değerlendirilirse `null`.
 
 [f(x)](../../../csharp/language-reference/operators/invocation-operator.md) – işlev çağırma.  
  
 [bir&#91;x&#93; ](../../../csharp/language-reference/operators/index-operator.md) – toplama bir nesne dizin oluşturma.  
   
 [x ++](../../../csharp/language-reference/operators/increment-operator.md) – sonek artırma. X değerini döndürür ve sonra depolama konumu büyük bir x değeri ile güncelleştirir (genellikle 1 tamsayı ekler).  
  
 [x--](../../../csharp/language-reference/operators/decrement-operator.md) – sonek azaltma. X değerini döndürür ve sonra depolama konumunu bir daha az x değeri ile güncelleştirir (genellikle 1 tamsayı çıkarır).  
  
 [Yeni](../../../csharp/language-reference/keywords/new-operator.md) – örneklemesi yazın.  
  
 [typeof](../../../csharp/language-reference/keywords/typeof.md) – döndürür <xref:System.Type> işleneni temsil eden nesne.  
  
 [işaretli](../../../csharp/language-reference/keywords/checked.md) – taşma denetimi tamsayı işlemleri için etkinleştirir.  
  
 [Unchecked](../../../csharp/language-reference/keywords/unchecked.md) – taşma denetimi tamsayı işlemleri için devre dışı bırakır. Varsayılan derleyici davranışı budur.  
  
 [Default(T)](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md) – t türünün varsayılan değeri döndürür `null` başvuru türleri için sıfır sayısal türler için ve sıfır /`null` üyeleri struct türleri için koyar.  
  
 [Temsilci](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) – bildirir ve temsilci örneğini döndürür.  
  
 [sizeof](../../../csharp/language-reference/keywords/sizeof.md) – tür işleneni bayt cinsinden boyutu döndürür.  
  
 [->](../../../csharp/language-reference/operators/dereference-operator.md) – işaretçi başvurusunun kaldırılmasının birleştirilmiş üye erişimi ile.  
  
## <a name="unary-operators"></a>Birli İşleçler  
 Bu işleçlere sonraki bölümde daha yüksek öncelikli ve önceki bölümde düşük önceliğe sahip.  
  
 [+ x](../../../csharp/language-reference/operators/addition-operator.md) – x değerini döndürür.  
  
 [-x](../../../csharp/language-reference/operators/subtraction-operator.md) – sayısal değilleme.  
  
 [\!x](../../../csharp/language-reference/operators/logical-negation-operator.md) – mantıksal değilleme.  
  
 [~ x](../../../csharp/language-reference/operators/bitwise-complement-operator.md) – bit düzeyinde tamamlama.  
  
 [++ x](../../../csharp/language-reference/operators/increment-operator.md) – önek artırma. Depolama konumu biridir x değerini güncelleştirdikten sonra x değerini büyük döndürür (genellikle 1 tamsayı ekler).  
  
 [--x](../../../csharp/language-reference/operators/decrement-operator.md) – azaltma önek. Depolama konumu daha az biridir x değerini güncelleştirdikten sonra x değeri döndürür (genellikle 1 tamsayı çıkarır).  
  
 [(T) x](../../../csharp/language-reference/operators/invocation-operator.md) – atama yazın.  
  
 [await](../../../csharp/language-reference/keywords/await.md) – bekler bir `Task`.  
  
 [& x](../../../csharp/language-reference/operators/and-operator.md) – adresidir.  
  
 [* x](../../../csharp/language-reference/operators/multiplication-operator.md) – bilgileri başvuru kaldırma.  
  
## <a name="multiplicative-operators"></a>Çarpma İşleçleri  
 Bu işleçlere sonraki bölümde daha yüksek öncelikli ve önceki bölümde düşük önceliğe sahip.  
  
 [x * y](../../../csharp/language-reference/operators/multiplication-operator.md) – çarpma.  
  
 [x / y](../../../csharp/language-reference/operators/division-operator.md) – bölme. İşlenen tamsayılar olursa, sonuç sıfır kesilmiş bir tamsayıdır (örneğin, `-7 / 2 is -3`).  
  
 [% y x](../../../csharp/language-reference/operators/modulus-operator.md) – mod. İşlenen tamsayılar varsa, bu y bölme x kalanı döndürür.  Varsa `q = x / y` ve `r = x % y`, ardından `x = q * y + r`.  
  
## <a name="additive-operators"></a>Toplama İşleçleri  
 Bu işleçlere sonraki bölümde daha yüksek öncelikli ve önceki bölümde düşük önceliğe sahip.  
  
 [x + y](../../../csharp/language-reference/operators/addition-operator.md) – toplama.  
  
 [x-y](../../../csharp/language-reference/operators/subtraction-operator.md) – çıkarma.  
  
## <a name="shift-operators"></a>Kaydırma İşleçleri  
 Bu işleçlere sonraki bölümde daha yüksek öncelikli ve önceki bölümde düşük önceliğe sahip.  
  
 [x <\< y](../../../csharp/language-reference/operators/left-shift-operator.md) – BITS sol kaydırma ve sağ taraftaki sıfır ile doldurun.  
  
 [x >> y](../../../csharp/language-reference/operators/right-shift-operator.md) – üst karakter sağa bit. Sol işleneni ise `int` veya `long`, sonra da sol BITS oturum bit ile doldurulur. Sol işleneni ise `uint` veya `ulong`, sonra da sol BITS sıfır ile doldurulur.  
  
## <a name="relational-and-type-testing-operators"></a>İlişkisel ve türü sınama işleçleri  
 Bu işleçlere sonraki bölümde daha yüksek öncelikli ve önceki bölümde düşük önceliğe sahip.  
  
 [x \< y](../../../csharp/language-reference/operators/less-than-operator.md) – (x, y değerinden ise true) küçüktür.  
  
 [x > y](../../../csharp/language-reference/operators/greater-than-operator.md) – (x, y büyükse true) büyüktür.  
  
 [x \<y =](../../../csharp/language-reference/operators/less-than-equal-operator.md) – küçük veya eşit.  
  
 [x > y =](../../../csharp/language-reference/operators/greater-than-equal-operator.md) – değerinden büyük veya eşit.  
  
 [olan](../../../csharp/language-reference/keywords/is.md) – uyumluluk yazın. Değerlendirilen sol işleneni sağ işleneni (statik türü) içinde belirtilen türe çevirebilirsiniz true değerini döndürür.  
  
 [olarak](../../../csharp/language-reference/keywords/as.md) – dönüştürme yazın. (Bir statik türü), sağ işleneni tarafından belirtilen tür cast sol işleneni verir ancak `as` döndürür `null` burada `(T)x` bir özel durum.  
  
## <a name="equality-operators"></a>Eşitlik İşleçleri  
 Bu işleçlere sonraki bölümde daha yüksek öncelikli ve önceki bölümde düşük önceliğe sahip.  
  
 [x y ==](../../../csharp/language-reference/operators/equality-comparison-operator.md) – eşitlik. Varsayılan olarak, başvuru türleri dışında `string`, bu başvuru eşitlik (kimlik test) döndürür. Ancak, türleri aşırı `==`, maksadınızı kimliğini sınamak istiyorsanız kullanmak en iyisidir `ReferenceEquals` yöntemi `object`.  
  
 [x! y =](../../../csharp/language-reference/operators/not-equal-operator.md) – eşit değil. Açıklama için bkz: `==`. Bir tür overloads varsa `==`, aşırı gerekir sonra `!=`.  
  
## <a name="logical-and-operator"></a>Mantıksal AND işleci  
 Bu işleç, sonraki bölümde daha yüksek önceliğe ve önceki bölümde düşük önceliğe sahiptir.  
  
 [x ve y](../../../csharp/language-reference/operators/and-operator.md) – mantıksal ve bit düzeyinde and Bu genellikle tamsayı türleriyle kullanabilirsiniz ve `enum` türleri.  
  
## <a name="logical-xor-operator"></a>Mantıksal XOR işleci  
 Bu işleç, sonraki bölümde daha yüksek önceliğe ve önceki bölümde düşük önceliğe sahiptir.  
  
 [x ^ y](../../../csharp/language-reference/operators/xor-operator.md) – mantıksal ve bit düzeyinde XOR. Bu genellikle tamsayı türleriyle kullanabilirsiniz ve `enum` türleri.  
  
## <a name="logical-or-operator"></a>Mantıksal OR işleci  
 Bu işleç, sonraki bölümde daha yüksek önceliğe ve önceki bölümde düşük önceliğe sahiptir.  
  
 [x &#124; y](../../../csharp/language-reference/operators/or-operator.md) – mantıksal ve bit düzeyinde OR. Bu genellikle tamsayı türleriyle kullanabilirsiniz ve `enum` türleri.  
  
## <a name="conditional-and-operator"></a>Koşullu AND işleci  
 Bu işleç, sonraki bölümde daha yüksek önceliğe ve önceki bölümde düşük önceliğe sahiptir.  
  
 [x & & y](../../../csharp/language-reference/operators/conditional-and-operator.md) – mantıksal and İlk işlenen false hesaplanırsa sonra C# ikinci işlenen değerlendirmez.  
  
## <a name="conditional-or-operator"></a>Koşullu OR işleci  
 Bu işleç, sonraki bölümde daha yüksek önceliğe ve önceki bölümde düşük önceliğe sahiptir.  
  
 [x &#124; &#124; y](../../../csharp/language-reference/operators/conditional-or-operator.md) – mantıksal OR. İlk işlenen doğru olarak değerlendirilirse, ardından C# ikinci işlenen değerlendirmez.  
  
## <a name="null-coalescing-operator"></a>Null birleşim işleci  
 Bu işleç, sonraki bölümde daha yüksek önceliğe ve önceki bölümde düşük önceliğe sahiptir.  
  
 [x?? y](../../../csharp/language-reference/operators/null-conditional-operator.md) – döndürür `x` olmayan ise`null`; Aksi halde döndürür `y`.  
  
## <a name="conditional-operator"></a>Koşullu işleç  
 Bu işleç, sonraki bölümde daha yüksek önceliğe ve önceki bölümde düşük önceliğe sahiptir.  
  
 [t? x: y](../../../csharp/language-reference/operators/conditional-operator.md) – varsa test `t` true, sonra değerlendirmek ve dönmek için değerlendirir `x`; Aksi halde, değerlendirmek ve dönüş `y`.  
  
## <a name="assignment-and-lambda-operators"></a>Atama ve Lambda işleçleri  
 Bu işleçlere sonraki bölümde daha yüksek öncelikli ve önceki bölümde düşük önceliğe sahip.  
  
 [x y =](../../../csharp/language-reference/operators/assignment-operator.md) – atama.  
  
 [x += y](../../../csharp/language-reference/operators/addition-assignment-operator.md) – artırma. Değeri eklemek `y` değerine `x`, sonuçta depolamak `x`ve yeni bir değer döndürür. Varsa `x` atayan bir `event`, ardından `y` C# olay işleyici ekler uygun bir işlev olmalıdır.  
  
 [x-= y](../../../csharp/language-reference/operators/subtraction-assignment-operator.md) – azaltma. Değerini çıkarma `y` değerinden `x`, sonuçta depolamak `x`ve yeni bir değer döndürür. Varsa `x` atayan bir `event`, ardından `y` C# olay işleyici kaldırır uygun bir işlev olmalıdır  
  
 [x * = y](../../../csharp/language-reference/operators/multiplication-assignment-operator.md) – çarpma atama. Değerini Çarp `y` değerine `x`, sonuçta depolamak `x`ve yeni bir değer döndürür.  
  
 [x / y =](../../../csharp/language-reference/operators/division-assignment-operator.md) – bölme atama. Değerini bölmek `x` değeriyle `y`, sonuçta depolamak `x`ve yeni bir değer döndürür.  
  
 [% x y =](../../../csharp/language-reference/operators/modulus-assignment-operator.md) – mod atama. Değerini bölmek `x` değeriyle `y`, kalanı depolamak `x`ve yeni bir değer döndürür.  
  
 [x & y =](../../../csharp/language-reference/operators/and-assignment-operator.md) – ve atama. DEĞERİNİ `y` değeriyle `x`, sonuçta depolamak `x`ve yeni bir değer döndürür.  
  
 [x &#124;y =](../../../csharp/language-reference/operators/or-assignment-operator.md) – OR ataması. VEYA değerini `y` değeriyle `x`, sonuçta depolamak `x`ve yeni bir değer döndürür.  
  
 [x ^ = y](../../../csharp/language-reference/operators/xor-assignment-operator.md) – XOR atama. XOR değeri, `y` değeriyle `x`, sonuçta depolamak `x`ve yeni bir değer döndürür.  
  
 [x << y =](../../../csharp/language-reference/operators/left-shift-assignment-operator.md) – sola kaydırma ataması. Değerini kaydırma `x` sol tarafından `y` bir yerde saklayın sonucunda `x`ve yeni bir değer döndürür.  
  
 [x >> y =](../../../csharp/language-reference/operators/right-shift-assignment-operator.md) – sağa kaydırma ataması. Değerini kaydırma `x` sağ tarafından `y` bir yerde saklayın sonucunda `x`ve yeni bir değer döndürür.  
  
 [=>](../../../csharp/language-reference/operators/lambda-operator.md) – lambda bildirimi.  
  
## <a name="arithmetic-overflow"></a>Aritmetik Taşma  
 Aritmetik işleçler ([+](../../../csharp/language-reference/operators/addition-operator.md), [ - ](../../../csharp/language-reference/operators/subtraction-operator.md), [ * ](../../../csharp/language-reference/operators/multiplication-operator.md), [ / ](../../../csharp/language-reference/operators/division-operator.md)) olabilir söz konusu sayısal tür için olası değerler aralığının dışında olan sonuçlar. Ayrıntılar için ancak genel olarak belirli bir işlecin bölümüne başvurun:  
  
- Tamsayı aritmetik taşma ya da atar bir <xref:System.OverflowException> veya sonucunun en önemli BITS atar. Tamsayı bölme her zaman sıfır atar bir <xref:System.DivideByZeroException>.  

   Tamsayı taşma oluştuğunda ne olacağı olabilen yürütme bağlamı bağlıdır [işaretli veya işaretsiz](../../../csharp/language-reference/keywords/checked-and-unchecked.md). Checked bağlamında bir <xref:System.OverflowException> oluşturulur. İşaretli bir bağlamda sonucunun en önemli BITS atılır ve yürütme devam eder. Bu nedenle, C#, işleme ya da taşma yoksayılıyor seçmenizi sağlar. Aritmetik işlemler varsayılan olarak, oluşan bir *denetlenmeyen* bağlamı. 

   Aritmetik işlemler yanı sıra integral türü için integral-tür atamaları taşmasına neden (zaman, cast gibi bir [uzun](../../../csharp/language-reference/keywords/long.md) için bir [int](../../../csharp/language-reference/keywords/int.md)) ve işaretli veya işaretsiz yürütme tabidir. Ancak, bit düzeyinde işleçler ve kaydırma işleçleri hiçbir zaman taşma neden olur.  
   
-   Kayan nokta aritmetik taşma ya da sıfıra bölme hiçbir zaman bir özel durum oluşturur, kayan nokta türleri IEEE 754 ve bunu temel aldığından sonsuz ve NaN (sayı değil) temsil eden hükümleri gerekir.  
  
-   [Ondalık](../../../csharp/language-reference/keywords/decimal.md) aritmetik taşma her zaman oluşturur bir <xref:System.OverflowException>. Ondalık bölme her zaman sıfır atar bir <xref:System.DivideByZeroException>.  
  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C#](../../../csharp/index.md) [fazla yüklenebilir işleçler](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)
