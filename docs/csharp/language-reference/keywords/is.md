---
title: C# başvuru
ms.custom: seodec18
ms.date: 06/21/2019
f1_keywords:
- is_CSharpKeyword
- is
helpviewer_keywords:
- is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
ms.openlocfilehash: a04105137fad7cd3a25b869c3aa7fcbe91ed20ab
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566314"
---
# <a name="is-c-reference"></a>is (C# Başvurusu)

İşleci, bir ifadenin sonucunun verilen türle uyumlu olup olmadığını denetler veya (7,0 ile C# başlayarak) bir ifadeyi bir düzene göre sınar. `is` Tür testi `is` işleci hakkında daha fazla bilgi için, [tür-test ve atama işleçleri](../operators/type-testing-and-cast.md) makalesinin [işleç](../operators/type-testing-and-cast.md#is-operator) bölümüne bakın.

## <a name="pattern-matching-with-is"></a>İle eşleşen desenler`is`

7,0 ile C# başlayarak, `is` ve [Switch](switch.md) deyimleri, model eşleştirmeyi destekler. `is` Anahtar sözcüğü aşağıdaki desenleri destekler:

- Bir ifadenin belirtilen türe dönüştürülüp dönüştürülebileceğini test eden [tür stili](#type-pattern), bu, bir ifadenin bu türden bir değişkene dönüştürülmesini sağlar.

- Bir ifadenin belirtilen sabit değer olarak değerlendirilip değerlendirilmediğini test eden [sabit bir model](#constant-pattern).

- [var olan model](#var-pattern), her zaman başarılı olan ve bir ifadenin değerini yeni bir yerel değişkene bağlayan bir eşleşme.

### <a name="type-pattern"></a>Tür stili

Model eşleştirmeyi gerçekleştirmek için tür modelini kullanırken, `is` bir ifadenin belirtilen bir türe dönüştürülüp dönüştürülebileceğini ve bu türden bir değişkene bir değişken verip etmediğini test eder. Bu, `is` kısa tür değerlendirmesi ve dönüştürmeyi sağlayan deyimin basit bir uzantısıdır. `is` Tür deseninin genel formu:

```csharp
   expr is type varname
```

Burada *Expr* , bir türün bir örneğini değerlendiren bir ifadedir, *tür* , *Expr* 'nin sonucunun dönüştürülecek türün adı, *varname* ise *ifadenin* sonucunun dönüştürüldüğü nesne, `is` test .`true` 

İfade, Expr`null`değilse ve aşağıdakilerden herhangi biri doğru ise geçerlidir: `is` `true`

- *Expr* , *türü*ile aynı türde bir örneğidir.

- *Expr* *türünden*türetilen bir türün örneğidir. Diğer bir deyişle, *ifadenin* sonucu *türünde*bir örneğe eklenebilir.

- *ifadenin* türünde bir temel sınıf olan bir derleme zamanı türü vardır ve *Expr* *türü* veya türünden türetilmiş bir çalışma zamanı türü vardır. Bir değişkenin *derleme zamanı türü* , bildiriminde tanımlanan değişkenin türüdür. Bir değişkenin *çalışma zamanı türü* , bu değişkene atanan örneğin türüdür.

- *Expr* , *tür* arabirimini uygulayan bir türün örneğidir.

7,1 ile C# başlayarak, *Expr* genel bir tür parametresi ve kısıtlamaları tarafından tanımlanan bir derleme zamanı türüne sahip olabilir.

*Expr* ise `true` ve `is` bir `if` ifadesiyle birlikte kullanılırsa, varname yalnızca deyimin içinde atanır. `if` *Varname* kapsamı, `is` ifadeden `if` deyimi kapsayan bloğun sonuna kadar olur. Başka bir konumda *varname* kullanılması atanmamış bir değişkenin kullanımı için derleme zamanı hatası oluşturur.

Aşağıdaki örnek, bir `is` <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> türün yönteminin uygulanmasını sağlamak için tür modelini kullanır.

[!code-csharp[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]

Model eşleştirmesi olmadan bu kod aşağıdaki gibi yazılabilir. Tür deseninin kullanımı, dönüştürmenin sonucunun bir `null`olup olmadığını test etme gereksinimini ortadan kaldırarak daha kompakt, okunabilir kod üretir.  

[!code-csharp[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]

`is` Tür deseninin de bir değer türünün türü belirlenirken daha kompakt kod üretir. Aşağıdaki örnek, uygun bir `is` özelliğin değerini görüntülemeden önce bir nesnenin bir `Person` mi `Dog` yoksa bir örnek mi olduğunu anlamak için tür modelini kullanır.

[!code-csharp[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]

Desenler eşleşmesi olmayan eşdeğer kod, açık bir dönüştürme içeren ayrı bir atama gerektirir.

[!code-csharp[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]

### <a name="constant-pattern"></a>Sabit model

Sabit örüntüyle eşleşen desenler gerçekleştirirken, `is` bir ifadenin belirtilen bir sabit değere eşit olup olmadığını sınar. C# 6 ve önceki sürümlerde, sabit model [Switch](switch.md) ifadesiyle desteklenir. 7,0 ' C# den başlayarak, bu, `is` bildiri tarafından da desteklenir. Sözdizimi şöyledir:

```csharp
   expr is constant
```

Burada *Expr* , değerlendirilecek ifadedir ve *sabitin* test edilecek değerdir. *sabit* , aşağıdaki sabit ifadelerden herhangi biri olabilir:

- Değişmez değer.

- Belirtilen `const` değişkenin adı.

- Bir numaralandırma sabiti.

Sabit ifade aşağıdaki gibi değerlendirilir:

- Eğer *Expr* ve *Constant* integral türse, C# eşitlik işleci ifadenin döndürülüp döndürülmeyeceğini `true` (yani, `expr == constant`ne olduğunu) belirler.

- Aksi takdirde, ifadenin değeri static [Object. Equals (Expr, Constant)](xref:System.Object.Equals(System.Object,System.Object)) yöntemi çağrısıyla belirlenir.  

Aşağıdaki örnek, bir nesnenin bir `Dice` örnek olup olmadığını test etmek için tür ve sabit desenleri ve bir zar rulosu değerinin 6 olup olmadığını anlamak için birleştirir.

[!code-csharp[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]

İçin `null` denetim, sabit model kullanılarak gerçekleştirilebilir. Anahtar sözcüğü, `is` ifadesiyle desteklenir. `null` Sözdizimi şöyledir:

```csharp
   expr is null
```

Aşağıdaki örnek, `null` denetimlerin karşılaştırmasını gösterir:

[!code-csharp[is#11](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern11.cs#11)]

### <a name="var-pattern"></a>var deseninin

Bu `var` , herhangi bir tür veya değer için bir catch-all ' dır. *Expr* 'nin değeri her zaman bir yerel değişkene, aynı türde *Expr*'nin derleme zamanı türüyle atanır. `is` İfadenin sonucu her zaman `true`olur. Sözdizimi şöyledir:

```csharp
   expr is var varname
```

Aşağıdaki örnek, adlı `obj`bir değişkene bir ifade atamak için var modelini kullanır. Daha sonra değerini ve türünü `obj`görüntüler.

[!code-csharp[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]

## <a name="c-language-specification"></a>C# dili belirtimi
  
Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) ve aşağıdaki C# dil tekliflerinin [işleç](~/_csharplang/spec/expressions.md#the-is-operator) bölümüne bakın:

- [Desen eşleştirme](~/_csharplang/proposals/csharp-7.0/pattern-matching.md)
- [Genel türler ile desen eşleştirme](~/_csharplang/proposals/csharp-7.1/generics-pattern-match.md)
  
## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [C# anahtar sözcükleri](index.md)
- [Tür testi ve atama işleçleri](../operators/type-testing-and-cast.md)
