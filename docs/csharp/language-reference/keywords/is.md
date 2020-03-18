---
title: is - C# Referans
ms.date: 06/21/2019
f1_keywords:
- is_CSharpKeyword
- is
helpviewer_keywords:
- is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
ms.openlocfilehash: e64b690482419963a92764b2c97a42dbb231fbfc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399639"
---
# <a name="is-c-reference"></a>is (C# Başvurusu)

İşleç, `is` bir ifadenin sonucunun belirli bir türle uyumlu olup olmadığını denetler veya (C# 7.0 ile başlayarak) bir ifadeyi desenle test eder. Tür testi `is` işleci hakkında daha fazla bilgi [için, Tür testi ve döküm işleçleri](../operators/type-testing-and-cast.md) makalesinin [operatör](../operators/type-testing-and-cast.md#is-operator) bölümüne bakın.

## <a name="pattern-matching-with-is"></a>Desen ile eşleşen`is`

C# 7.0 ile `is` başlayarak, ve [anahtar](switch.md) ifadeleri deseni eşleştirmeyi destekler. Anahtar `is` kelime aşağıdaki desenleri destekler:

- Bir ifadenin belirli bir türe dönüştürülüp dönüştürülemeyeceğini sınayan ve olabilirse, bu tür bir değişkene dönüştüren [tür deseni.](#type-pattern)

- Bir ifadenin belirli bir sabit değere değerlendirilip değerlendirmediğini sınayan [sabit desen.](#constant-pattern)

- [var deseni,](#var-pattern)her zaman başarılı olan ve bir ifadenin değerini yeni bir yerel değişkene bağlayan bir eşleşmedir.

### <a name="type-pattern"></a>Tür deseni

Desen eşleştirmesini gerçekleştirmek için tür `is` deseni kullanırken, bir ifadenin belirli bir türe dönüştürülüp dönüştürülemeyeceğini sınar ve olabilirse, bu tür bir değişkene dönüştürür. Kısa tür değerlendirmesi ve `is` dönüştürme sağlayan ifadenin basit bir uzantısıdır. Tür deseninin `is` genel biçimi:

```csharp
   expr is type varname
```

*Expr'ın* bazı türde bir örneği değerlendiren bir ifade olduğu durumlarda, *tür,* *expr* sonucunun dönüştürüldüğü türün adıdır ve *varname,* `is` test ise *expr* sonucunun dönüştürüldüğü `true`nesnedir.

`is` İfade, `true` *expr* değilse `null`ve aşağıdakilerden herhangi biri doğrudur:

- *expr* *türü*olarak aynı türde bir örnektir.

- *expr* *türünden*türetilen bir tür örneğidir. Başka bir deyişle, *expr* sonucu *türü*bir örnek için upcast olabilir.

- *expr* *türü*bir taban sınıf olan bir derleme-zaman türü vardır ve *expr* *türü* veya *türünden*türetilen bir çalışma zamanı türü vardır. Bir değişkenin *derleme zamanı türü,* değişkenin bildiriminde tanımlandığı şekilde türüdür. Bir değişkenin *çalışma zamanı türü,* bu değişkene atanan örneğin türüdür.

- *expr* *türü* arabirimi uygulayan bir tür örneğidir.

C# 7.1 ile başlayarak, *expr* genel bir tür parametresi ve kısıtlamaları tarafından tanımlanan bir derleme-zaman türü ne olabilir.

*Expr* bir `true` `if` `is` deyimle kullanılıyorsa ve deyimle `if` kullanılıyorsa, *varname* yalnızca deyim içinde atanır. *Varnamenin* kapsamı `is` ifadeden `if` ifadeyi çevreleyen bloğun sonuna kadardır. *Varname'nin* başka bir konumda kullanılması, atanmamış bir değişkenin kullanımı için derleme zamanı hatası oluşturur.

Aşağıdaki örnek, `is` bir tür <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> yönteminin uygulanmasını sağlamak için tür deseni kullanır.

[!code-csharp[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]

Desen eşleştirme olmadan, bu kod aşağıdaki gibi yazılabilir. Tür deseni eşleştirmekullanımı, bir dönüştürmenin sonucunun bir `null`.  

[!code-csharp[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]

Tür `is` deseni, değer türünün türünü belirlerken daha kompakt kod da üretir. Aşağıdaki örnek, `is` uygun bir özelliğin değerini `Person` görüntülemeden `Dog` önce bir nesnenin bir örnek mi yoksa örnek mi olduğunu belirlemek için tür deseni kullanır.

[!code-csharp[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]

Desen eşleştirmesi olmayan eşdeğer kod, açık bir döküm içeren ayrı bir atama gerektirir.

[!code-csharp[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]

### <a name="constant-pattern"></a>Sabit desen

Sabit desenle eşleşen desen `is` gerçekleştirirken, bir ifadenin belirtilen bir sabite eşit olup olmadığını sınar. C# 6 ve önceki sürümlerde, sabit desen [anahtar](switch.md) deyimi tarafından desteklenir. C# 7.0 ile başlayarak, `is` ifade tarafından da desteklenir. Sözdizimi:

```csharp
   expr is constant
```

*expr* değerlendirmek için ifade ve *sabit* için test etmek için değerdir. *sabit* aşağıdaki sabit ifadelerden biri olabilir:

- Gerçek bir değer.

- Bildirilen `const` değişkenin adı.

- Numaralandırma sabiti.

Sabit ifade aşağıdaki gibi değerlendirilir:

- *Expr* ve *constant* integral türleri ise, C# eşitlik işleci `true` ifadenin döndürüp döndürülmediğini (yani, olup olmadığını) `expr == constant`belirler.

- Aksi takdirde, ifadenin değeri statik [Object.Equals (expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) yöntemine yapılan bir çağrı ile belirlenir.  

Aşağıdaki örnek, bir nesnenin bir `Dice` örnek olup olmadığını sınamak ve bir zar rulosu değerinin 6 olup olmadığını belirlemek için türü ve sabit desenleri birleştirir.

[!code-csharp[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]

Kontrol `null` sabit desen kullanılarak yapılabilir. Anahtar `null` kelime `is` deyim tarafından desteklenir. Sözdizimi:

```csharp
   expr is null
```

Aşağıdaki örnek, denetimlerin `null` karşılaştırılmasını gösterir:

[!code-csharp[is#11](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern11.cs#11)]

### <a name="var-pattern"></a>var deseni

Desenile eşleşen `var` bir desen her zaman başarılı dır. Sözdizimi:

```csharp
   expr is var varname
```

Expr değeri *expr* her zaman *varname*adlı yerel bir değişkene atanır nerede. *varname,* *expr*derleme-zaman türü ile aynı türde bir değişkendir.

*Expr* değerlendirirse `null`, `is` ifade `true` üretir `null` ve *varname*ye atar. Var deseni, bir `is` `true` `null` değer için üreten birkaç kullanımdan biridir.

Aşağıdaki örnekte `var` görüldüğü gibi, Boolean ifadesi içinde geçici bir değişken oluşturmak için deseni kullanabilirsiniz:

[!code-csharp[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]

Önceki örnekte, geçici değişken pahalı bir işlemin sonucunu depolamak için kullanılır. Değişken daha sonra birden çok kez kullanılabilir.

## <a name="c-language-specification"></a>C# dili belirtimi
  
Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [operatör](~/_csharplang/spec/expressions.md#the-is-operator) bölümüne ve aşağıdaki C# dil önerilerine bakın:

- [Desen eşleştirme](~/_csharplang/proposals/csharp-7.0/pattern-matching.md)
- [Genel türler ile desen eşleştirme](~/_csharplang/proposals/csharp-7.1/generics-pattern-match.md)
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# anahtar sözcükleri](index.md)
- [Tür testi ve atama işleçleri](../operators/type-testing-and-cast.md)
