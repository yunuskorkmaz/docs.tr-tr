---
title: Operators - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- operators [C#]
- C# language, operators
- operators [C#], about operators
ms.assetid: 214e7b83-1a41-4f7c-9867-64e9c0bab39f
ms.openlocfilehash: 109298a7945a6b76b35970b7b9c42e159bad8f90
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59979387"
---
# <a name="operators-c-programming-guide"></a>İşleçler (C# Programlama Kılavuzu)

C# ' ta, bir *işleci* uygulanan bir program öğesi için bir veya daha fazla olan *işlenenler* bir deyim veya ifade. Artırım işleci gibi tek bir işlenen alan işleçler (`++`) veya `new`, denir *birli* işleçleri. Aritmetik işleçleri gibi iki işlene alan işleçler (`+`,`-`,`*`,`/`), denir *ikili* işleçleri. Bir işleç, koşullu işleç (`?:`) üç işlenen alır ve C# ' deki tek Üçlü işleç.  
  
 Aşağıdaki C# deyimi tek bir birli işleç ve tek bir işlenen içerir. Artırım işleci `++`, işleneninin değerini değiştirir `y`.  
  
 [!code-csharp[csProgGuideStatements#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#5)]  
  
 Aşağıdaki C# deyimi, her biri iki işlenenli iki ikili işleç alır. Atama işleci `=`, tamsayı değişkeni sahip `y` ve ifade `2 + 3` işlenen olarak. İfade `2 + 3` kendisi, toplama işleci ve iki işlenenden oluşur `2` ve `3`.  
  
 [!code-csharp[csProgGuideStatements#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#6)]  
  
## <a name="operators-evaluation-and-operator-precedence"></a>İşleçler, değerlendirme ve İşleç önceliği

 Bir işlenen, herhangi bir uzunlukta koddan oluşan geçerli bir ifade olabilir ve herhangi bir sayıda alt ifade içerebilir. Birden çok işleç içeren bir ifadede, işleçlerin uygulanma sırası tarafından belirlenir *İşleç önceliği*, *ilişkilendirilebilirliği*ve parantezler.  
  
 Her işleç tanımlanmış bir önceliğe sahiptir. Farklı öncelik düzeyleri olan birden çok işleç içeren bir ifadede, işleçlerin önceliği, işleçlerin değerlendirilme sırasını belirler. Örneğin, aşağıdaki deyim 3 atar `n1`.  
  
 `n1 = 11 - 2 * 4;`  
  
 Çarpma çıkarmaya göre öncelikli olduğundan, önce çarpma yürütülür.  
  
 Aşağıdaki tablo, yaptıkları işleme dayalı olarak, işleçleri kategorilere ayırır. Kategoriler, öncelik sırasına göre listelenir.  
  
 **Birincil operatörler**  
  
|İfade|Açıklama|  
|----------------|-----------------|  
|x[.](../../../csharp/language-reference/operators/member-access-operator.md)y<br /><br /> x?.y|Üye erişimi<br /><br /> Koşullu üye erişimi|  
|f[(x)](../../../csharp/language-reference/operators/invocation-operator.md)|Yöntem ve temsilci çağırma|  
|bir[&#91;x&#93;](../../../csharp/language-reference/operators/index-operator.md)<br /><br /> a?[x]|Dizi ve dizinleyici erişimi<br /><br /> Koşullu dizi ve dizinleyici erişimi|  
|x[++](../../../csharp/language-reference/operators/arithmetic-operators.md#increment-operator-)|Artırım sonrası|  
|x[--](../../../csharp/language-reference/operators/arithmetic-operators.md#decrement-operator---)|Azaltım sonrası|  
|[Yeni](../../../csharp/language-reference/keywords/new-operator.md) T(...)|Nesne ve temsilci oluşturma|  
|`new` T(...) {...}|Başlatıcı ile nesne oluşturma. Bkz: [nesne ve koleksiyon başlatıcıları](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).|  
|`new` {...}|Anonim nesne başlatıcı. Bkz: [anonim türler](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).|  
|`new` T [...]|Dizi oluşturma. Bkz: [diziler](../../../csharp/programming-guide/arrays/index.md).|  
|[typeof](../../../csharp/language-reference/keywords/typeof.md)(T)|T için System.Type nesnesi elde etme|  
|[işaretli](../../../csharp/language-reference/keywords/checked.md)(x)|İşaretli bağlamında ifade değerlendirme|  
|[denetlenmeyen](../../../csharp/language-reference/keywords/unchecked.md)(x)|İşaretlenmemiş bağlamında ifade değerlendirme|  
|[Varsayılan](../../../csharp/language-reference/keywords/default.md) (T)|T türü varsayılan değerini elde etme|  
|[Temsilci](../../../csharp/language-reference/keywords/delegate.md) {}|Anonim işlevi (anonim yöntemi)|  
  
 **Birli işleçler**  
  
|İfade|Açıklama|  
|----------------|-----------------|  
|[+](../../../csharp/language-reference/operators/addition-operator.md)x|Kimlik|  
|[-](../../../csharp/language-reference/operators/subtraction-operator.md)x|Olumsuzlama|  
|[\!](../../../csharp/language-reference/operators/boolean-logical-operators.md#logical-negation-operator-)x|Mantıksal olumsuzlama|  
|[~](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#bitwise-complement-operator-)x|Bitwise olumsuzlama|  
|[++](../../../csharp/language-reference/operators/arithmetic-operators.md#increment-operator-)x|Artırım öncesi|  
|[--](../../../csharp/language-reference/operators/arithmetic-operators.md#decrement-operator---)x|Azaltım öncesi|  
|[(T)](../../../csharp/language-reference/operators/invocation-operator.md)x|x'i açıkça T türüne dönüştürme|  
  
 **Çarpma işleçleri**  
  
|İfade|Açıklama|  
|----------------|-----------------|  
|[*](../../../csharp/language-reference/operators/arithmetic-operators.md#multiplication-operator-)|Çarpma|  
|[/](../../../csharp/language-reference/operators/arithmetic-operators.md#division-operator-)|Bölme|  
|[%](../../../csharp/language-reference/operators/arithmetic-operators.md#remainder-operator-)|Kalan|  
  
 **Toplama işleçleri**  
  
|İfade|Açıklama|  
|----------------|-----------------|  
|x [ + ](../../../csharp/language-reference/operators/addition-operator.md) y|Toplama, dize bitiştirme, temsilci birleşimi|  
|x [ - ](../../../csharp/language-reference/operators/subtraction-operator.md) y|Çıkarma, temsilci kaldırma|  
  
 **Kaydırma işleçleri**  
  
|İfade|Açıklama|
|----------------|-----------------|
|x [ < \< ](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#left-shift-operator-) y|Sola kaydırma|
|x [ >> ](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#right-shift-operator-) y|Sağa kaydırma|
  
 **İlişkisel ve tür işleçleri**  
  
|İfade|Açıklama|  
|----------------|-----------------|  
|x [ \< ](../../../csharp/language-reference/operators/less-than-operator.md) y|Küçüktür|  
|x [ > ](../../../csharp/language-reference/operators/greater-than-operator.md) y|Büyüktür|  
|x [ \< = ](../../../csharp/language-reference/operators/less-than-equal-operator.md) y|Küçük veya eşittir|  
|x [ >= ](../../../csharp/language-reference/operators/greater-than-equal-operator.md) y|Büyük veya eşittir|  
|x [olduğu](../../../csharp/language-reference/keywords/is.md) T|x bir T ise doğru döndür, tersi durumda yanlış döndür|  
|x [olarak](../../../csharp/language-reference/keywords/as.md) T|T olarak yazdırılan x döndür ya da T değilse null döndür|  
  
 **Eşitlik İşleçleri**  
  
|İfade|Açıklama|  
|----------------|-----------------|  
|x [ == ](../../../csharp/language-reference/operators/equality-operators.md#equality-operator-) y|Eşittir|  
|x [! =](../../../csharp/language-reference/operators/equality-operators.md#inequality-operator-) y|Eşit değildir|  
  
 **Mantıksal, koşullu ve Null işleçleri**  
  
|Kategori|İfade|Açıklama|
|--------------|----------------|-----------------|
|Mantıksal VE|`x & y`|[Tamsayı bitwise ve](../../language-reference/operators/bitwise-and-shift-operators.md#logical-and-operator-), [Boolean mantıksal ve](../../language-reference/operators/boolean-logical-operators.md#logical-and-operator-)|
|Mantıksal XOR|`x ^ y`|[Tamsayı bitwise XOR](../../language-reference/operators/bitwise-and-shift-operators.md#logical-exclusive-or-operator-), [Boolean mantıksal XOR](../../language-reference/operators/boolean-logical-operators.md#logical-exclusive-or-operator-)|
|Mantıksal VEYA|`x | y`|[Tamsayı bitwise OR](../../language-reference/operators/bitwise-and-shift-operators.md#logical-or-operator-), [Boolean mantıksal veya](../../language-reference/operators/boolean-logical-operators.md#logical-or-operator-)|
|Koşullu VE|x [ && ](../../../csharp/language-reference/operators/boolean-logical-operators.md#conditional-logical-and-operator-) y|Yalnızca x doğruysa y değerlendirilir|
|Koşullu VEYA|x [&#124;&#124;](../../../csharp/language-reference/operators/boolean-logical-operators.md#conditional-logical-or-operator-) y|Yalnızca x yanlışsa y değerlendirilir|
|Null birleşim|x [??](../../../csharp/language-reference/operators/null-coalescing-operator.md) y|x null ise y olarak değerlendirilir, tersi durumda x olarak değerlendirilir|
|Koşullu|x [?](../../../csharp/language-reference/operators/conditional-operator.md) y: z|x doğruysa Y olarak değerlendirilir, x yanlışsa z olarak değerlendirilir|
  
 **Atama ve anonim işleçleri**  
  
|İfade|Açıklama|
|----------------|-----------------|
|[=](../../../csharp/language-reference/operators/assignment-operator.md)|Atama|
|x iş= y|Bileşen atama Bu işleçleri destekler: [ += ](../../../csharp/language-reference/operators/addition-assignment-operator.md), [ -= ](../../../csharp/language-reference/operators/subtraction-assignment-operator.md), [ *= ](../../../csharp/language-reference/operators/arithmetic-operators.md#compound-assignment), [ /= ](../../../csharp/language-reference/operators/arithmetic-operators.md#compound-assignment), [ %= ](../../../csharp/language-reference/operators/arithmetic-operators.md#compound-assignment) , [&=](../../../csharp/language-reference/operators/boolean-logical-operators.md#compound-assignment), [&#124;=](../../../csharp/language-reference/operators/boolean-logical-operators.md#compound-assignment), [^=](../../../csharp/language-reference/operators/boolean-logical-operators.md#compound-assignment), [<\<=](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#compound-assignment), [>>=](../../../csharp/language-reference/operators/bitwise-and-shift-operators.md#compound-assignment)|
|(T x) [ => ](../../../csharp/language-reference/operators/lambda-operator.md) y|Anonim işlevi (lambda ifadesi)|
  
## <a name="associativity"></a>İlişkilendirilebilirlik

 Aynı önceliğe sahip iki veya daha fazla işleç bir ifadede yer aldığında, ilişkilendirilebilirliğe dayalı olarak değerlendirilirler. Solla ilişkilendirilebilir işleçler, soldan sağa doğru değerlendirilir. Örneğin, `x * y / z` değerlendirmesinde `(x * y) / z`. Sağla ilişkilendirilebilir işleçler, sağdan sola doğru değerlendirilir. Örneğin, atama işleci sağla ilişkilendirilebilir. Öyle olmasaydı, aşağıdaki kod bir hataya neden olurdu.  
  
```csharp  
int a, b, c;  
c = 1;  
// The following two lines are equivalent.  
a = b = c;  
a = (b = c);  
  
// The following line, which forces left associativity, causes an error.  
//(a = b) = c;  
```  
  
 Başka bir örnek Üçlü işleç ([?:](../../../csharp/language-reference/operators/conditional-operator.md)) sağla ilişkilendirilebilir. Çoğu ikili işleçler solla ilişkilendirilebilir.  
  
 Bir ifadedeki işleçler ister solla isterse sağla ilişkilendirilebilir olsun, her bir ifadenin işlenenleri ilk olarak, soldan sağa doğru ilişkilendirilir. Aşağıdaki örnekler, işleçlerin ve işlenenleri değerlendirilme sırasını gösterir.  
  
|Deyim|Değerlendirme sırası|  
|---------------|-------------------------|  
|`a = b`|a, b, =|  
|`a = b + c`|a, b, c, +, =|  
|`a = b + c * d`|a, b, c, d, *, +, =|  
|`a = b * c + d`|a, b, c, *, d, +, =|  
|`a = b - c + d`|a, b, c, -, d, +, =|  
|`a += b -= c`|a, b, c, -=, +=|  
  
## <a name="adding-parentheses"></a>Ayraç ekleme

 Parantezler kullanarak işleç önceliği ve ilişkilendirilebilirlik tarafından dayatılan sırayı değiştirebilirsiniz. Örneğin, `2 + 3 * 2` çarpma işleçleri toplama işleçlerine göre öncelikli olduğundan, normalde 8 olarak değerlendirilir. Ancak, bir ifade olarak yazarsanız `(2 + 3) * 2`eklenmesi çarpımdan önce değerlendirilir ve sonucu 10'dur. Aşağıdaki örnekler, parantezli ifadelerdeki değerlendirme sırasını gösterir. Önceki örneklerde olduğu gibi, işlenenler işleç uygulanmadan önce değerlendirilir.  
  
|Deyim|Değerlendirme sırası|  
|---------------|-------------------------|  
|`a = (b + c) * d`|a, b, c, +, d, *, =|  
|`a = b - (c + d)`|a, b, c, d, +, -, =|  
|`a = (b + c) * (d - e)`|a, b, c, +, d, e, -, *, =|  
  
## <a name="operator-overloading"></a>İşleç aşırı yüklemesi

 Özel sınıflar ve yapılar için işleçlerin davranışını değiştirebilirsiniz. Bu işlem olarak adlandırılır *İşleç aşırı yüklemesi*. Daha fazla bilgi için [fazla yüklenebilir işleçler](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md) ve [işleci](../../../csharp/language-reference/keywords/operator.md) anahtar sözcüğü makalesi.  
  
## <a name="related-sections"></a>İlgili bölümler

 Daha fazla bilgi için [işleç anahtar sözcükleri](../../../csharp/language-reference/keywords/operator-keywords.md) ve [C# işleçleri](../../../csharp/language-reference/operators/index.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Deyimler, İfadeler ve İşleçler](../../../csharp/programming-guide/statements-expressions-operators/index.md)
