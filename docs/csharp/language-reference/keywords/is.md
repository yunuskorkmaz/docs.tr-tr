---
description: -C# başvurusu
title: -C# başvurusu
ms.date: 06/21/2019
f1_keywords:
- is_CSharpKeyword
- is
helpviewer_keywords:
- is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
ms.openlocfilehash: 3508f08857f88fd34478f968a71bae0121d54d1c
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134516"
---
# <a name="is-c-reference"></a>is (C# Başvurusu)

`is`İşleci, bir ifadenin sonucunun verilen türle uyumlu olup olmadığını denetler veya (C# 7,0 ' den itibaren) bir ifadeyi bir düzene göre sınar. Tür testi işleci hakkında daha fazla bilgi için, `is` [tür-test ve atama işleçleri](../operators/type-testing-and-cast.md) makalesinin [işleç](../operators/type-testing-and-cast.md#is-operator) bölümüne bakın.

## <a name="pattern-matching-with-is"></a>İle eşleşen desenler `is`

C# 7,0 ile başlayarak, `is` ve [Switch](switch.md) deyimleri, model eşleştirmeyi destekler. `is`Anahtar sözcüğü aşağıdaki desenleri destekler:

- Bir ifadenin belirtilen türe dönüştürülüp dönüştürülebileceğini test eden [tür stili](#type-pattern), bu, bir ifadenin bu türden bir değişkene dönüştürülmesini sağlar.

- Bir ifadenin belirtilen sabit değer olarak değerlendirilip değerlendirilmediğini test eden [sabit bir model](#constant-pattern).

- [var olan model](#var-pattern), her zaman başarılı olan ve bir ifadenin değerini yeni bir yerel değişkene bağlayan bir eşleşme.

### <a name="type-pattern"></a>Tür stili

Model eşleştirmeyi gerçekleştirmek için tür modelini kullanırken, `is` bir ifadenin belirtilen bir türe dönüştürülüp dönüştürülebileceğini ve bu türden bir değişkene bir değişken verip etmediğini test eder. Bu, `is` kısa tür değerlendirmesi ve dönüştürmeyi sağlayan deyimin basit bir uzantısıdır. `is`Tür deseninin genel formu:

```csharp
   expr is type varname
```

Burada *Expr* , bir türün bir örneğini değerlendiren bir ifadedir, *tür* , *ifadenin* sonucunun dönüştürülecek türün adı ve *varname* , test ise *ifadenin* sonucunun dönüştürülebileceği nesnedir `is` `true` .

`is`İfade, `true` *Expr* değilse `null` ve aşağıdakilerden herhangi biri doğru ise geçerlidir:

- *Expr* , *türü*ile aynı türde bir örneğidir.

- *Expr* *türünden*türetilen bir türün örneğidir. Diğer bir deyişle, *ifadenin* sonucu *türünde*bir örneğe eklenebilir.

- *ifadenin* *türünde bir*temel sınıf olan bir derleme zamanı türü vardır ve *Expr* *türü* *veya türünden türetilmiş*bir çalışma zamanı türü vardır. Bir değişkenin *derleme zamanı türü* , bildiriminde tanımlanan değişkenin türüdür. Bir değişkenin *çalışma zamanı türü* , bu değişkene atanan örneğin türüdür.

- *Expr* , *tür* arabirimini uygulayan bir türün örneğidir.

C# 7,1 ile başlayarak, *Expr* genel bir tür parametresi ve kısıtlamaları tarafından tanımlanan bir derleme zamanı türüne sahip olabilir.

*Expr* ise `true` ve `is` bir ifadesiyle birlikte kullanılırsa `if` , *varname* `if` yalnızca deyimin içinde atanır. *Varname* kapsamı, `is` ifadeden deyimi kapsayan bloğun sonuna kadar olur `if` . Başka bir konumda *varname* kullanılması atanmamış bir değişkenin kullanımı için derleme zamanı hatası oluşturur.

Aşağıdaki örnek, `is` bir türün yönteminin uygulanmasını sağlamak için tür modelini kullanır <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> .

[!code-csharp[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]

Model eşleştirmesi olmadan bu kod aşağıdaki gibi yazılabilir. Tür deseninin kullanımı, dönüştürmenin sonucunun bir olup olmadığını test etme gereksinimini ortadan kaldırarak daha kompakt, okunabilir kod üretir `null` .  

[!code-csharp[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]

`is`Tür deseninin de bir değer türünün türü belirlenirken daha kompakt kod üretir. Aşağıdaki örnek, uygun bir `is` `Person` `Dog` özelliğin değerini görüntülemeden önce bir nesnenin bir mi yoksa bir örnek mi olduğunu anlamak için tür modelini kullanır.

[!code-csharp[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]

Desenler eşleşmesi olmayan eşdeğer kod, açık bir dönüştürme içeren ayrı bir atama gerektirir.

[!code-csharp[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]

### <a name="constant-pattern"></a>Sabit model

Sabit örüntüyle eşleşen desenler gerçekleştirirken, `is` bir ifadenin belirtilen bir sabit değere eşit olup olmadığını sınar. C# 6 ve önceki sürümlerinde, sabit model [Switch](switch.md) ifadesiyle desteklenir. C# 7,0 ' den başlayarak, bu ifade da desteklenir `is` . Sözdizimi şöyledir:

```csharp
   expr is constant
```

Burada *Expr* , değerlendirilecek ifadedir ve *sabitin* test edilecek değerdir. *sabit* , aşağıdaki sabit ifadelerden herhangi biri olabilir:

- Değişmez değer.

- Belirtilen `const` değişkenin adı.

- Bir numaralandırma sabiti.

Sabit ifade aşağıdaki gibi değerlendirilir:

- *Expr* ve *Constant* Integral türse, C# eşitlik işleci ifadenin döndürülüp döndürülmeyeceğini `true` (yani, ne gibi `expr == constant` ) belirler.

- Aksi takdirde, ifadenin değeri static [Object. Equals (Expr, Constant)](xref:System.Object.Equals(System.Object,System.Object)) yöntemi çağrısıyla belirlenir.  

Aşağıdaki örnek, bir nesnenin bir örnek olup olmadığını test etmek için tür ve sabit desenleri `Dice` ve bir zar rulosu değerinin 6 olup olmadığını anlamak için birleştirir.

[!code-csharp[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]

İçin Denetim `null` , sabit model kullanılarak gerçekleştirilebilir. `null`Anahtar sözcüğü, `is` ifadesiyle desteklenir. Sözdizimi şöyledir:

```csharp
   expr is null
```

Aşağıdaki örnek, denetimlerin karşılaştırmasını gösterir `null` :

[!code-csharp[is#11](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern11.cs#11)]

### <a name="var-pattern"></a>var deseninin

Desenli bir model eşleşmesi `var` her zaman başarılı olur. Sözdizimi şöyledir:

```csharp
   expr is var varname
```

Burada, *ifadenin* değeri her zaman *varname*adlı bir yerel değişkene atanır. *varname* , *Expr*'nin derleme zamanı türüyle aynı türde bir değişkendir.

Eğer *expr* ifadesi olarak değerlendirilirse `null` , `is` ifade, `true` `null` *varname*öğesini üretir ve atar. Var olan model, `is` `true` bir değer için üreten birkaç kullanımdır `null` .

`var`Aşağıdaki örnekte gösterildiği gibi, bir Boolean ifadesinde geçici bir değişken oluşturmak için, bu kalıbı kullanabilirsiniz:

[!code-csharp[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]

Önceki örnekte, geçici değişken pahalı bir işlemin sonucunu depolamak için kullanılır. Değişken daha sonra birden çok kez kullanılabilir.

## <a name="c-language-specification"></a>C# dili belirtimi
  
Daha fazla bilgi için [c# dil belirtiminin](~/_csharplang/spec/introduction.md) ve aşağıdaki c# dil tekliflerinin [, bkz.:](~/_csharplang/spec/expressions.md#the-is-operator)

- [Desen eşleştirme](~/_csharplang/proposals/csharp-7.0/pattern-matching.md)
- [Genel türler ile desen eşleştirme](~/_csharplang/proposals/csharp-7.1/generics-pattern-match.md)
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# anahtar sözcükleri](index.md)
- [Tür testi ve atama işleçleri](../operators/type-testing-and-cast.md)
