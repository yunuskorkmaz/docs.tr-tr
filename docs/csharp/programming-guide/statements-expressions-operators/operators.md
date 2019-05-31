---
title: Operators - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 04/30/2019
helpviewer_keywords:
- operators [C#]
- C# language, operators
- operators [C#], about operators
ms.assetid: 214e7b83-1a41-4f7c-9867-64e9c0bab39f
ms.openlocfilehash: 60e7f7c25b525c6db856731bd16c1c0e60efe6d6
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422931"
---
# <a name="operators-c-programming-guide"></a>İşleçler (C# Programlama Kılavuzu)

C# ' ta, bir *işleci* uygulanan bir program öğesi için bir veya daha fazla olan *işlenenler* bir deyim veya ifade. Artırım işleci gibi tek bir işlenen alan işleçler (`++`) veya `new`, denir *birli* işleçleri. Aritmetik işleçleri gibi iki işlene alan işleçler (`+`,`-`,`*`,`/`), denir *ikili* işleçleri. Bir işleç, koşullu işleç (`?:`) üç işlenen alır ve C# ' deki tek Üçlü işleç.  
  
 Aşağıdaki C# deyimi tek bir birli işleç ve tek bir işlenen içerir. Artırım işleci `++`, işleneninin değerini değiştirir `y`.  
  
 [!code-csharp[csProgGuideStatements#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#5)]  
  
 Aşağıdaki C# deyimi, her biri iki işlenenli iki ikili işleç alır. Atama işleci `=`, tamsayı değişkeni sahip `y` ve ifade `2 + 3` işlenen olarak. İfade `2 + 3` kendisi, toplama işleci ve iki işlenenden oluşur `2` ve `3`.  
  
 [!code-csharp[csProgGuideStatements#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#6)]  
  
Bir işlenen, herhangi bir uzunlukta koddan oluşan geçerli bir ifade olabilir ve herhangi bir sayıda alt ifade içerebilir. Birden çok işleç içeren bir ifadede, işleçlerin uygulanma sırası tarafından belirlenir *İşleç önceliği*, *ilişkilendirilebilirliği*ve parantezler.  

## <a name="operator-precedence"></a>İşleç önceliği
  
Her işleç tanımlanmış bir önceliğe sahiptir. Farklı öncelik düzeyleri olan birden çok işleç içeren bir ifadede, işleçlerin önceliği, işleçlerin değerlendirilme sırasını belirler. Örneğin, aşağıdaki deyim 3 atar `n1`:

```csharp
n1 = 11 - 2 * 4;
```

Çarpma çıkarmaya göre öncelikli olduğundan, önce çarpma yürütülür.

Tam listesi için C# işleçler, öncelik düzeyine göre sıralanmış bkz [ C# işleçleri](../../language-reference/operators/index.md).
  
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

Özel sınıflar ve yapılar için belirli işleçlerin davranışını tanımlayabilirsiniz. Bu işlem olarak adlandırılır *İşleç aşırı yüklemesi*. Daha fazla bilgi için [fazla yüklenebilir işleçler](overloadable-operators.md) ve [işleci](../../language-reference/keywords/operator.md) anahtar sözcüğü makalesi.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Deyimler, İfadeler ve İşleçler](index.md)
- [C# İşleçleri](../../language-reference/operators/index.md)
