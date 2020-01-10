---
title: C# başvuru
ms.date: 06/21/2019
f1_keywords:
- is_CSharpKeyword
- is
helpviewer_keywords:
- is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
ms.openlocfilehash: 1a1f539e80f8d843f40640fa798cf6122f316a9f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715231"
---
# <a name="is-c-reference"></a>is (C# Başvurusu)

`is` işleci, bir ifadenin sonucunun verilen türle uyumlu olup olmadığını denetler veya (7,0 ile C# başlayarak) bir ifadeyi bir düzene göre sınar. Tür-test `is` işleci hakkında daha fazla bilgi için, [tür-test ve atama işleçleri](../operators/type-testing-and-cast.md) makalesinin [işleç](../operators/type-testing-and-cast.md#is-operator) bölümüne bakın.

## <a name="pattern-matching-with-is"></a>`is` ile eşleşen desenler

7,0 ile C# başlayarak, `is` ve [Switch](switch.md) deyimleri, model eşleştirmeyi destekler. `is` anahtar sözcüğü aşağıdaki desenleri destekler:

- Bir ifadenin belirtilen türe dönüştürülüp dönüştürülebileceğini test eden [tür stili](#type-pattern), bu, bir ifadenin bu türden bir değişkene dönüştürülmesini sağlar.

- Bir ifadenin belirtilen sabit değer olarak değerlendirilip değerlendirilmediğini test eden [sabit bir model](#constant-pattern).

- [var olan model](#var-pattern), her zaman başarılı olan ve bir ifadenin değerini yeni bir yerel değişkene bağlayan bir eşleşme.

### <a name="type-pattern"></a>Tür stili

Model eşleştirmeyi gerçekleştirmek için tür deseninin kullanıldığı zaman `is`, bir ifadenin belirtilen bir türe dönüştürülüp dönüştürülmeyeceğini test eder ve bu şekilde, bu tür bir değişkene bu değeri verebilir. Bu, kısa tür değerlendirmesi ve dönüştürmeyi sağlayan `is` deyimin basit bir uzantısıdır. `is` Type deseninin genel formu:

```csharp
   expr is type varname
```

Burada *Expr* , bir türün bir örneğini değerlendiren bir ifadedir, *tür* , *ifadenin* sonucunun dönüştürülecek türün adı, *varname* ise `is` testi `true`olduğunda, *ifadenin* sonucunun dönüştürüldüğü nesnedir. 

`is` ifadesi, *expr* `null`değilse `true` ve aşağıdakilerden herhangi biri true 'dur:

- *Expr* , *türü*ile aynı türde bir örneğidir.

- *Expr* *türünden*türetilen bir türün örneğidir. Diğer bir deyişle, *ifadenin* sonucu *türünde*bir örneğe eklenebilir.

- *ifadenin* *türünde bir*temel sınıf olan bir derleme zamanı türü vardır ve *Expr* *türü* *veya türünden türetilmiş*bir çalışma zamanı türü vardır. Bir değişkenin *derleme zamanı türü* , bildiriminde tanımlanan değişkenin türüdür. Bir değişkenin *çalışma zamanı türü* , bu değişkene atanan örneğin türüdür.

- *Expr* , *tür* arabirimini uygulayan bir türün örneğidir.

7,1 ile C# başlayarak, *Expr* genel bir tür parametresi ve kısıtlamaları tarafından tanımlanan bir derleme zamanı türüne sahip olabilir.

*Expr* `true` ve `is` bir `if` ifadesiyle kullanılırsa, *varname* yalnızca `if` ifadesinde atanır. *Varname* kapsamı `is` ifadeden `if` deyimini kapsayan bloğun sonuna kadar olur. Başka bir konumda *varname* kullanılması atanmamış bir değişkenin kullanımı için derleme zamanı hatası oluşturur.

Aşağıdaki örnek, bir türün <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> yönteminin uygulanmasını sağlamak için `is` tür modelini kullanır.

[!code-csharp[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]

Model eşleştirmesi olmadan bu kod aşağıdaki gibi yazılabilir. Tür deseninin kullanımı, dönüştürmenin sonucunun `null`olup olmadığını test etme gereksinimini ortadan kaldırarak daha kompakt, okunabilir kod üretir.  

[!code-csharp[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]

`is` tür deseninin değeri, bir değer türünün türü belirlenirken daha Compact kod da üretir. Aşağıdaki örnek, uygun bir özelliğin değerini görüntülemeden önce bir nesnenin `Person` mi yoksa bir `Dog` örneği mi olduğunu anlamak için `is` tür modelini kullanır.

[!code-csharp[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]

Desenler eşleşmesi olmayan eşdeğer kod, açık bir dönüştürme içeren ayrı bir atama gerektirir.

[!code-csharp[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]

### <a name="constant-pattern"></a>Sabit model

Sabit örüntüyle eşleşen desenler gerçekleştirirken, bir ifadenin belirtilen bir sabit değere eşit olup olmadığını sınar `is`. C# 6 ve önceki sürümlerde, sabit model [Switch](switch.md) ifadesiyle desteklenir. 7,0 ' C# den başlayarak `is` bildiri de desteklenir. Sözdizimi şöyledir:

```csharp
   expr is constant
```

Burada *Expr* , değerlendirilecek ifadedir ve *sabitin* test edilecek değerdir. *sabit* , aşağıdaki sabit ifadelerden herhangi biri olabilir:

- Değişmez değer.

- Belirtilen bir `const` değişkeninin adı.

- Bir numaralandırma sabiti.

Sabit ifade aşağıdaki gibi değerlendirilir:

- *Expr* ve *Constant* integral türse, C# eşitlik işleci ifadenin `true` (yani `expr == constant`) döndürüp döndürmeyeceğini belirler.

- Aksi takdirde, ifadenin değeri static [Object. Equals (Expr, Constant)](xref:System.Object.Equals(System.Object,System.Object)) yöntemi çağrısıyla belirlenir.  

Aşağıdaki örnek, bir nesnenin `Dice` bir örnek olup olmadığını test etmek için tür ve sabit desenleri, bir zar rulosu değerinin 6 olup olmadığını anlamak için birleştirir.

[!code-csharp[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]

`null` denetimi, sabit model kullanılarak gerçekleştirilebilir. `null` anahtar sözcüğü `is` ifadesiyle desteklenir. Sözdizimi şöyledir:

```csharp
   expr is null
```

Aşağıdaki örnekte `null` denetimlerinin karşılaştırması gösterilmektedir:

[!code-csharp[is#11](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern11.cs#11)]

### <a name="var-pattern"></a>var deseninin

`var` model her tür veya değer için bir catch-all ' dır. *Expr* 'nin değeri her zaman bir yerel değişkene, aynı türde *Expr*'nin derleme zamanı türüyle atanır. `is` ifadesinin sonucu her zaman `true`. Sözdizimi şöyledir:

```csharp
   expr is var varname
```

Aşağıdaki örnek, `obj`adlı bir değişkene bir ifade atamak için var modelini kullanır. Sonra değeri ve `obj`türünü görüntüler.

[!code-csharp[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]

## <a name="c-language-specification"></a>C# dili belirtimi
  
Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) ve aşağıdaki C# dil tekliflerinin [işleç](~/_csharplang/spec/expressions.md#the-is-operator) bölümüne bakın:

- [Desen eşleştirme](~/_csharplang/proposals/csharp-7.0/pattern-matching.md)
- [Genel türler ile desen eşleştirme](~/_csharplang/proposals/csharp-7.1/generics-pattern-match.md)
  
## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [C# anahtar sözcükleri](index.md)
- [Tür testi ve atama işleçleri](../operators/type-testing-and-cast.md)
