---
title: İşleçler- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 04/30/2019
helpviewer_keywords:
- operators [C#]
- C# language, operators
- operators [C#], about operators
ms.assetid: 214e7b83-1a41-4f7c-9867-64e9c0bab39f
ms.openlocfilehash: 4870c744383205c2b7e3832c01fb838a545f085f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588612"
---
# <a name="operators-c-programming-guide"></a>İşleçler (C# Programlama Kılavuzu)

' C#De, bir *işleç* bir ifade veya deyimde bir veya daha fazla *işlenenlere* uygulanan bir program öğesidir. Artış işleci (`++`) veya `new`gibi bir işleneni alan operatörler *birli* işleçler olarak adlandırılır. Aritmetik işleçler`+`(,`-`,`*`,`/`) gibi iki işlenen işleç *ikili* işleçler olarak adlandırılır. Bir işleç, koşullu işleç (`?:`), üç işlenen alır ve ' de C#tek üçlü işleçtir.  
  
 Aşağıdaki C# deyimi tek bir birli işleç ve tek bir işlenen içerir. Artış işleci `++`, işlenenin `y`değerini değiştirir.  
  
 [!code-csharp[csProgGuideStatements#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#5)]  
  
 Aşağıdaki C# deyimi, her biri iki işlenenli iki ikili işleç alır. Atama işleci `=`,, işlenen olarak Integer değişkenine `y` ve ifadeye `2 + 3` sahiptir. İfade `2 + 3` , toplama işleci ve iki `2` işlenenden `3`oluşur.  
  
 [!code-csharp[csProgGuideStatements#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#6)]  
  
Bir işlenen, herhangi bir uzunlukta koddan oluşan geçerli bir ifade olabilir ve herhangi bir sayıda alt ifade içerebilir. Birden çok işleç içeren bir ifadede, işleçlerin uygulanma sırası, *işleç önceliği*, *ilişkilendirilebilirlik*ve parantezler tarafından belirlenir.  

## <a name="operator-precedence"></a>İşleç önceliği
  
Her işleç tanımlanmış bir önceliğe sahiptir. Farklı öncelik düzeyleri olan birden çok işleç içeren bir ifadede, işleçlerin önceliği, işleçlerin değerlendirilme sırasını belirler. Örneğin, aşağıdaki ifade 3 öğesine `n1`atar:

```csharp
n1 = 11 - 2 * 4;
```

Çarpma çıkarmaya göre öncelikli olduğundan, önce çarpma yürütülür.

Öncelik düzeyine göre sıralanan C# işleçlerin tüm listesi için bkz [ C# . işleçler](../../language-reference/operators/index.md).
  
## <a name="associativity"></a>İlişkilendirilebilirlik

 Aynı önceliğe sahip iki veya daha fazla işleç bir ifadede yer aldığında, ilişkilendirilebilirliğe dayalı olarak değerlendirilirler. Solla ilişkilendirilebilir işleçler, soldan sağa doğru değerlendirilir. Örneğin, `x * y / z` olarak `(x * y) / z`değerlendirilir. Sağla ilişkilendirilebilir işleçler, sağdan sola doğru değerlendirilir. Örneğin, atama işleci sağla ilişkilendirilebilir. Öyle olmasaydı, aşağıdaki kod bir hataya neden olurdu.  
  
```csharp  
int a, b, c;  
c = 1;  
// The following two lines are equivalent.  
a = b = c;  
a = (b = c);  
  
// The following line, which forces left associativity, causes an error.  
//(a = b) = c;  
```  
  
 Diğer bir örnek olarak, Üçlü işleç ([?:](../../language-reference/operators/conditional-operator.md)) doğru ilişkilendirilebilir. Çoğu ikili işleçler sola ilişkilendirilebilir.  
  
 Bir ifadedeki işleçler ister solla isterse sağla ilişkilendirilebilir olsun, her bir ifadenin işlenenleri ilk olarak, soldan sağa doğru ilişkilendirilir. Aşağıdaki örnekler, işleçlerin ve işlenenleri değerlendirilme sırasını gösterir.  
  
|Deyim|Değerlendirme sırası|  
|---------------|-------------------------|  
|`a = b`|a, b, =|  
|`a = b + c`|a, b, c, +, =|  
|`a = b + c * d`|a, b, c, d, *, +, =|  
|`a = b * c + d`|a, b, c, *, d, +, =|  
|`a = b - c + d`|a, b, c, -, d, +, =|  
|`a += b -= c`|a, b, c, -=, +=|  
  
## <a name="adding-parentheses"></a>Parantezler ekleme

 Parantezler kullanarak işleç önceliği ve ilişkilendirilebilirlik tarafından dayatılan sırayı değiştirebilirsiniz. Örneğin, çarpma `2 + 3 * 2` işleçleri toplamasız işleçlere göre öncelikli olduğundan, genellikle 8 olarak değerlendirilir. Ancak, ifadeyi olarak `(2 + 3) * 2`yazarsanız, toplama çarpmadan önce değerlendirilir ve sonuç 10 ' dur. Aşağıdaki örnekler, parantezli ifadelerdeki değerlendirme sırasını gösterir. Önceki örneklerde olduğu gibi, işlenenler işleç uygulanmadan önce değerlendirilir.  
  
|Deyim|Değerlendirme sırası|  
|---------------|-------------------------|  
|`a = (b + c) * d`|a, b, c, +, d, *, =|  
|`a = b - (c + d)`|a, b, c, d, +, -, =|  
|`a = (b + c) * (d - e)`|a, b, c, +, d, e, -, *, =|  
  
## <a name="operator-overloading"></a>İşleç aşırı yüklemesi

Özel sınıflar ve yapılar için belirli işleçlerin davranışını tanımlayabilirsiniz. Bu işleme *işleç aşırı yüklemesi*olarak başvurulur. Daha fazla bilgi için bkz. [operatör aşırı yüklemesi](../../language-reference/operators/operator-overloading.md).
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Deyimler, İfadeler ve İşleçler](index.md)
- [C# İşleçleri](../../language-reference/operators/index.md)
