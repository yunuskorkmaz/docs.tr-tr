---
title: İş - C# başvurusu
ms.custom: seodec18
ms.date: 06/21/2019
f1_keywords:
- is_CSharpKeyword
- is
helpviewer_keywords:
- is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
ms.openlocfilehash: 45e37dcb15e178fe37907e00cc14ef48c1bf230d
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/21/2019
ms.locfileid: "67306588"
---
# <a name="is-c-reference"></a>is (C# Başvurusu)

`is` İşleci denetleyen bir ifade sonucunu belirli bir tür ile uyumlu olup olmadığını veya (başlayarak C# 7.0) belirli bir desene göre bir ifade eder. Tür testi hakkında bilgi için `is` işleci bakın [işleci](../operators/type-testing-and-conversion-operators.md#is-operator) bölümünü [türünü test etme ve dönüştürme işleçleri](../operators/type-testing-and-conversion-operators.md) makalesi.

## <a name="pattern-matching-with-is"></a>İle desen eşleştirme `is`

C# 7.0 ile başlayan `is` ve [geçiş](switch.md) ifadeleri desen eşleştirme desteği. `is` Anahtar sözcüğü aşağıdaki düzenini destekler:

- [Tür deseni](#type-pattern), bir ifadenin belirtilen bir türe dönüştürülüp dönüştürülemeyeceğini test eder ve, olabilir, bu türden bir değişkene çevirir.

- [Sabit desen](#constant-pattern), belirtilen bir sabit değer için bir ifadeyi değerlendirir olup olmadığını sınar.

- [değişken desen](#var-pattern), her zaman yeni bir yerel değişken bir ifadenin değerine bağlar ve başarılı bir eşleşme.

### <a name="type-pattern"></a>Tür deseni

Desen eşleştirme, gerçekleştirmek için tür deseni kullanılırken `is` bir ifadenin belirtilen bir türe dönüştürülüp dönüştürülemeyeceğini test eder ve bu olabilir, bu türden bir değişkene çevirir. Basit bir uzantısıdır `is` kısa türü değerlendirme ve dönüştürme sağlayan deyimi. Genel formu `is` türü modelidir:

```csharp
   expr is type varname
```

Burada *expr* bazı türünde bir örnek için değerlendirilen bir ifade olan *türü* türün adı sonucunu *expr* Boolean'a dönüştürülecek ve *varname* hangi nesne sonucu *expr* aralığındaysa dönüştürülür `is` test `true`. 

`is` İfade `true` varsa *expr* değil `null`, ve aşağıdakilerden birini doğrudur:

- *Expr* örneği aynı türde olan *türü*.

- *Expr* türetilen türün bir örneği *türü*. Diğer bir deyişle, sonucunu *expr* örneğine başvurmanıza olabilir *türü*.

- *Expr* temel bir sınıfı olan bir derleme zamanı türü sahip *türü*, ve *expr* sahip olan bir çalışma zamanı türü *türü* veya türetilmiş *türü*. *Derleme zamanı tür* değişkeninin Değişken bildiriminde tanımlanan türüdür. *Çalışma zamanı türü* bir değişken, bu değişkene atanan örnek türüdür.

- *Expr* uygulayan bir tür örneğidir *türü* arabirimi.

İle başlayarak C# 7.1, *expr* genel tür parametresi kısıtlamaları ile tanımlanan bir derleme zamanı türü olabilir.

Varsa *expr* olduğu `true` ve `is` ile kullanılan bir `if` deyimi, *varname* içinde atanan `if` deyimi yalnızca. Kapsamı *varname* dandır `is` ifade kapsayan blok bitişi `if` deyimi. Kullanarak *varname* içindeki herhangi bir konumda değil atanmış olan bir değişkenin kullanım için bir derleme zamanı hatası oluşturur.

Aşağıdaki örnekte `is` türün uygulamasını sağlamak üzere tür deseni <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> yöntemi.

[!code-csharp[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]

Desen eşleştirme olmadan, bu kod şu şekilde yazılmış olabilir. Kullanım türü desen eşleştirme bir dönüştürmenin sonucu olup olmadığını sınamak için gereksinimini ortadan kaldırarak daha kompakt ve okunabilir bir kod oluşturur bir `null`.  

[!code-csharp[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]

`is` Türü desen türü bir değer türü tespit edilirken daha küçük kod ayrıca oluşturur. Aşağıdaki örnekte `is` türü desen, bir nesne olup olmadığını belirlemek için bir `Person` veya `Dog` uygun bir özelliğin değerini göstermeden önce örneği.

[!code-csharp[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]

Desen eşleştirme olmadan eşdeğer kod, bir açık tür dönüştürme içeren ayrı bir atama gerektirir.

[!code-csharp[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]

### <a name="constant-pattern"></a>Sabit desen

Sabit desen ile eşleşen deseni gerçekleştirirken `is` belirtilen sabit bir ifade eşit olup olmadığını test eder. C# 6 ve önceki sürümleri, sabit desen tarafından desteklenen [geçiş](switch.md) deyimi. İle başlayarak C# 7.0, onu tarafından desteklenen `is` deyimi de. Kendi sözdizimi aşağıdaki gibidir:

```csharp
   expr is constant
```

Burada *expr* değerlendirmek için ifade ve *sabit* sınamak için değer. *Sabit* aşağıdaki sabit ifadeler biri olabilir:

- Değişmez değer.

- Bildirilen bir adı `const` değişkeni.

- Bir numaralandırma sabiti.

Sabit ifade gibi değerlendirilir:

- Varsa *expr* ve *sabit* integral türleri, C# eşitlik işlecini ifade döndürüp döndürmediğini belirler `true` (olup, diğer bir deyişle, `expr == constant`).

- Aksi takdirde, ifadenin değerini statik bir çağrı tarafından belirlenir [Object.Equals (ifade, sabit)](xref:System.Object.Equals(System.Object,System.Object)) yöntemi.  

Aşağıdaki örnek bir nesne olup olmadığını sınamak için tür ve sabit desenler birleştiren bir `Dice` örneği ve ise, belirlemek için bir zar değerini olup 6.

[!code-csharp[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]

Denetleme `null` sabit deseni kullanılarak gerçekleştirilebilir. `null` Anahtar sözcüğü tarafından desteklenen `is` deyimi. Kendi sözdizimi aşağıdaki gibidir:

```csharp
   expr is null
```

Aşağıdaki örnek, bir karşılaştırmasını gösterir `null` denetler:

[!code-csharp[is#11](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern11.cs#11)]

### <a name="var-pattern"></a>değişken deseni

`var` Herhangi bir türü veya değer için bir catch tüm modelidir. Değerini *expr* derleme zamanı türünü aynı türe her zaman yerel bir değişkene atanan *expr*. Sonucu `is` ifadesidir her zaman `true`. Kendi sözdizimi aşağıdaki gibidir:

```csharp
   expr is var varname
```

Aşağıdaki örnek, bir ifade adlı bir değişkene atayın için değişken deseni kullanır. `obj`. Ardından değerine ve türüne görüntüler `obj`.

[!code-csharp[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]

## <a name="c-language-specification"></a>C# dili belirtimi
  
Daha fazla bilgi için [işleci](~/_csharplang/spec/expressions.md#the-is-operator) bölümünü [ C# dil belirtimi](~/_csharplang/spec/introduction.md) ve aşağıdaki C# dil teklifleri:

- [Desen eşleştirme](~/_csharplang/proposals/csharp-7.0/pattern-matching.md)
- [Genel türler ile desen eşleştirme](~/_csharplang/proposals/csharp-7.1/generics-pattern-match.md)
  
## <a name="see-also"></a>Ayrıca bkz.

- [C#başvuru](../index.md)
- [C# anahtar sözcükleri](index.md)
- [Tür test etme ve dönüştürme işleçleri](../operators/type-testing-and-conversion-operators.md)
