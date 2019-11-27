---
title: C#Switch deyimleri
ms.date: 04/09/2019
f1_keywords:
- switch_CSharpKeyword
- switch
- case
- case_CSharpKeyword
helpviewer_keywords:
- switch statement [C#]
- switch keyword [C#]
- case statement [C#]
- default keyword [C#]
ms.assetid: 44bae8b8-8841-4d85-826b-8a94277daecb
ms.openlocfilehash: 012fa5b4d5f39b4dfa4d1c77bc3d6fbe181e78a6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428494"
---
# <a name="switch-c-reference"></a>anahtar (C# başvuru)

`switch`, *Match ifadesiyle*bir model eşleşmesi temelinde aday listesinden yürütülecek tek bir *anahtar bölümü* seçen bir seçim deyimidir.

[!code-csharp[switch#1](~/samples/snippets/csharp/language-reference/keywords/switch/switch1.cs#1)]

Tek bir ifade üç veya daha fazla koşula göre test edildiğinde, `switch` deyimi genellikle [If-Else](if-else.md) yapısına alternatif olarak kullanılır. Örneğin, aşağıdaki `switch` ifade, `Color` türünde bir değişkenin üç değerden birine sahip olup olmadığını belirler:

[!code-csharp[switch#3](~/samples/snippets/csharp/language-reference/keywords/switch/switch3.cs#1)]

Bir `if`-`else` yapısını kullanan aşağıdaki örneğe eşdeğerdir.

[!code-csharp[switch#3a](~/samples/snippets/csharp/language-reference/keywords/switch/switch3a.cs#1)]

## <a name="the-match-expression"></a>Match ifadesi

Match ifadesi `case` etiketlerindeki desenlerle eşleşecek değeri sağlar. Sözdizimi şöyledir:

```csharp
   switch (expr)
```

C# 6 ve önceki sürümlerde, Match ifadesi aşağıdaki türlerde bir değer döndüren bir ifade olmalıdır:

- bir [char](../builtin-types/char.md).
- bir [dize](../builtin-types/reference-types.md).
- bir [bool](bool.md).
- `int` veya `long`gibi bir [integral](../builtin-types/integral-numeric-types.md) değeri.
- bir [sabit listesi](enum.md) değeri.

7,0 ile C# başlayarak, Match ifadesi null olmayan herhangi bir ifade olabilir.

## <a name="the-switch-section"></a>Anahtar bölümü

`switch` bir ifade bir veya daha fazla anahtar bölümü içerir. Her anahtar bölümü bir veya daha fazla *durum etiketi* (bir Case veya default etiketi) ve ardından bir veya daha fazla deyimi içerir. `switch` deyiminiz, herhangi bir switch bölümüne yerleştirilmiş en çok bir varsayılan etiket içerebilir. Aşağıdaki örnek, her biri iki deyim içeren üç anahtar bölümü olan basit bir `switch` deyimini gösterir. İkinci anahtar bölümü `case 2:` ve `case 3:` etiketlerini içerir.

`switch` bir ifade herhangi bir sayıda anahtar bölümü içerebilir ve aşağıdaki örnekte gösterildiği gibi her bölümde bir veya daha fazla Case etiketi olabilir. Ancak, iki durum etiketi de aynı ifadeyi içeremez.

[!code-csharp[switch#2](~/samples/snippets/csharp/language-reference/keywords/switch/switch2.cs#1)]

Switch deyimindeki yalnızca bir switch bölümü yürütülür. C#yürütmenin bir geçiş bölümünden bir sonrakine devam etmesine izin vermez. Bu nedenle, aşağıdaki kod bir derleyici hatası oluşturuyor, CS0163: "Denetim bir case etiketinden (\<Case Label >) başka bir şekilde geçemez."

```csharp
switch (caseSwitch)
{
    // The following switch section causes an error.
    case 1:
        Console.WriteLine("Case 1...");
        // Add a break or other jump statement here.
    case 2:
        Console.WriteLine("... and/or Case 2");
        break;
}
```

Bu gereksinim, genellikle bir [Break](break.md), [goto](goto.md)veya [Return](return.md) ifadesiyle Switch bölümünden açıkça çıkarken karşılanır. Ancak, program denetiminin `default` Switch bölümüne dönememesini sağladığından aşağıdaki kod da geçerlidir.

[!code-csharp[switch#4](~/samples/snippets/csharp/language-reference/keywords/switch/switch4.cs#1)]

Eşleştirme ifadesiyle eşleşen bir Case etiketi ile Switch bölümündeki deyim listesinin yürütülmesi ilk deyimle başlar ve genellikle bir `break`, `goto case`, `goto label`, `return`veya `throw`gibi bir sıçrama deyimine ulaşılana kadar deyim listesini ilerler. Bu noktada denetim `switch` deyimin dışına veya başka bir Case etiketine aktarılır. `goto` bir deyimin kullanılması, denetimin bir sabit etikete aktarılmalıdır. Bu kısıtlama gereklidir, çünkü denetimi sabit olmayan bir etikete aktarmaya çalışmak, denetimi kodda istenmeyen bir konuma aktarmak veya sonsuz bir döngü oluşturmak gibi istenmeyen yan etkilere sahip olabilir.

## <a name="case-labels"></a>Case etiketleri

Her Case etiketi, Match ifadesiyle Karşılaştırılacak bir model belirtir (önceki örneklerde `caseSwitch` değişkeni). Eşleşiyorsa denetim, **ilk** eşleşen Case etiketini içeren Switch bölümüne aktarılır. Hiçbir Case etiket deseninin eşleşme ifadesiyle eşleşmesi halinde, denetim varsa `default` Case etiketiyle birlikte bölümüne aktarılır. `default` bir durum yoksa, herhangi bir anahtar bölümünde hiçbir deyim yürütülmez ve denetim `switch` deyimi dışında aktarılır.

`switch` deyimleri ve model eşleştirme hakkında daha fazla bilgi için, [`switch` deyimiyle eşleşen düzende eşleşme](#pattern) bölümüne bakın.

C# 6 yalnızca sabit bir stili desteklediğinden ve sabit değerlerin yinelenmesinde izin vermediğinden, Case etiketleri birbirini dışlayan değerleri tanımlar ve yalnızca bir desenler eşleştirme ifadesiyle eşleştirebilir. Sonuç olarak, `case` deyimlerinin göründüğü sıra önemli değildir.

Ancak C# 7,0 ' de, diğer desenler desteklendiğinden, büyük/küçük harf etiketlerinin birbirini dışlayan değerler tanımlamamalıdır ve birden çok desen eşleştirme ifadesiyle eşleşemez. Yalnızca eşleşen düzeni içeren ilk anahtar bölümündeki deyimler yürütüldüğü için `case` deyimlerinin göründüğü sıra artık önemlidir. Case C# deyimi veya deyimleri önceki deyimlerin alt kümelerine eşit olan bir switch bölümü algılarsa, "switch case zaten önceki bir durum tarafından işlenmiştir." bir derleyici hatası oluşturur.

Aşağıdaki örnek, birbirini dışlayan farklı desenler kullanan bir `switch` ifadesini gösterir. `case 0:` Switch bölümünü `switch` deyimindeki ilk bölüm olmayacak şekilde taşırsanız, C# değeri sıfır olan bir tamsayı, `case int val` ifadesiyle tanımlanan bir alt küme olan tüm tamsayıların bir alt kümesi olan bir derleyici hatası oluşturur.

[!code-csharp[switch#5](~/samples/snippets/csharp/language-reference/keywords/switch/switch5.cs#1)]

Bu sorunu düzeltebilir ve iki şekilde derleyici uyarısını ortadan kaldırabilirsiniz:

- Anahtar bölümlerinin sırasını değiştirerek.

- `case` etiketinde bir [WHERE yan tümcesi](#when) kullanarak.

## <a name="the-default-case"></a>`default` durumu

`default` Case, Match ifadesi başka bir `case` etiketiyle eşleşmezse yürütülecek Switch bölümünü belirtir. `default` bir durum yoksa ve eşleştirme ifadesi başka bir `case` etiketiyle eşleşmezse, program akışı `switch` ifadesiyle geçer.

`default` durum, `switch` deyimindeki herhangi bir sırada görünebilir. Kaynak kodundaki sıralarından bağımsız olarak, tüm `case` etiketleri değerlendirildikten sonra her zaman son değerlendirilir.

## <a name="a-namepattern--pattern-matching-with-the-switch-statement"></a>`switch` ifadesiyle <a name="pattern" /> desenli eşleme

Her `case` deyimi, eşleşme ifadesiyle eşleşiyorsa, kapsayan anahtar bölümünün yürütülmesine neden olan bir model tanımlar. Tüm sürümleri sabit C# düzende desteklenir. Kalan desenler C# 7,0 tarihinden itibaren desteklenmektedir.

### <a name="constant-pattern"></a>Sabit model

Sabit model, eşleşme ifadesinin belirtilen bir sabit değere eşit olup olmadığını sınar. Sözdizimi şöyledir:

```csharp
   case constant:
```

Burada *Constant* , test edilecek değerdir. *sabit* , aşağıdaki sabit ifadelerden herhangi biri olabilir:

- `true` veya `false`[bool](bool.md) sabit değeri.
- `int`, `long`veya `byte`gibi herhangi bir [integral](../builtin-types/integral-numeric-types.md) sabiti.
- Belirtilen bir `const` değişkeninin adı.
- Bir numaralandırma sabiti.
- Bir [char](../builtin-types/char.md) sabit değeri.
- [Dize](../builtin-types/reference-types.md) sabit değeri.

Sabit ifade aşağıdaki gibi değerlendirilir:

- *Expr* ve *Constant* integral türse, C# eşitlik işleci ifadenin `true` (yani `expr == constant`) döndürüp döndürmeyeceğini belirler.

- Aksi takdirde, ifadenin değeri static [Object. Equals (Expr, Constant)](xref:System.Object.Equals(System.Object,System.Object)) yöntemi çağrısıyla belirlenir.

Aşağıdaki örnek, belirli bir tarihin hafta sonu, çalışma haftasının ilk günü mi, çalışma haftasının son günü mi yoksa çalışma haftasının ortasında mi olduğunu anlamak için sabit bir düzende kullanılır. Geçerli günün <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> özelliğini <xref:System.DayOfWeek> numaralandırmanın üyelerine göre değerlendirir.

[!code-csharp[switch#7](~/samples/snippets/csharp/language-reference/keywords/switch/const-pattern.cs#1)]

Aşağıdaki örnek, bir otomatik kahve makinesine benzetim yapan bir konsol uygulamasında kullanıcı girişini işlemek için sabit bir model kullanır.

[!code-csharp[switch#6](~/samples/snippets/csharp/language-reference/keywords/switch/switch6.cs)]

### <a name="type-pattern"></a>Tür stili

Tür stili, kısa tür değerlendirmesi ve dönüştürmeyi mümkün bir şekilde sunar. Model eşleştirmeyi gerçekleştirmek için `switch` ifadesiyle birlikte kullanıldığında, bir ifadenin belirtilen bir türe dönüştürülüp dönüştürülmeyeceğini ve olup olmadığını test eder. Sözdizimi şöyledir:

```csharp
   case type varname
```

Burada *tür* , *Expr* 'nin sonucunun dönüştürülecek türün adı ve *varname* , eşleşme başarılı olursa *ifadenin* sonucunun dönüştürüldüğü nesnedir. *İfadenin* derleme zamanı türü, 7,1 ile C# başlayan genel bir tür parametresi olabilir.

Aşağıdakilerden biri doğruysa `case` ifadesi `true`:

- *Expr* , *türü*ile aynı türde bir örneğidir.

- *Expr* *türünden*türetilen bir türün örneğidir. Diğer bir deyişle, *ifadenin* sonucu *türünde*bir örneğe eklenebilir.

- *ifadenin* *türünde bir*temel sınıf olan bir derleme zamanı türü vardır ve *Expr* *türü* *veya türünden türetilmiş*bir çalışma zamanı türü vardır. Bir değişkenin *derleme zamanı türü* , tür bildiriminde tanımlanan değişkenin türüdür. Bir değişkenin *çalışma zamanı türü* , bu değişkene atanan örneğin türüdür.

- *Expr* , *tür* arabirimini uygulayan bir türün örneğidir.

Case ifadesi true ise, *varname* kesinlikle atanır ve yalnızca switch bölümü içinde yerel kapsama sahiptir.

`null` bir türle eşleşmediğini unutmayın. Bir `null`eşleştirmek için aşağıdaki `case` etiketini kullanın:

```csharp
case null:
```

Aşağıdaki örnek, çeşitli türlerdeki koleksiyon türleri hakkında bilgi sağlamak için tür modelini kullanır.

[!code-csharp[type-pattern#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern.cs#1)]

`object`yerine, aşağıdaki kodda gösterildiği gibi koleksiyonun türünü tür parametresi olarak kullanarak genel bir yöntem yapabilirsiniz:

[!code-csharp[type-pattern#3](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern3.cs#1)]

Genel sürüm, ilk örnekten iki şekilde farklıdır. İlk olarak `null` örneğini kullanamazsınız. Derleyici herhangi bir rastgele tür `T` `object`dışında herhangi bir türe dönüştüremediğinden herhangi bir sabit durumu kullanamazsınız. `default` durumu artık null olmayan bir `object`sınar. Diğer bir deyişle, `default` durum testleri yalnızca `null`için geçerlidir.

Model eşleştirmesi olmadan bu kod aşağıdaki gibi yazılabilir. Tür deseninin kullanımı, bir dönüştürmenin sonucunun `null` olup olmadığını test etme veya yinelenen yayınlar gerçekleştirme gereksinimini ortadan kaldırarak daha kompakt, okunabilir kod üretir.

[!code-csharp[type-pattern2#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern2.cs#1)]

## <a name="a-namewhen--the-case-statement-and-the-when-clause"></a>`case` deyimi ve `when` yan tümcesini <a name="when" />

7,0 ' C# den itibaren, Case deyimlerinin birbirini dışlanması gerektiğinden, Case ifadesinin true olarak değerlendirilmesi için karşılanması gereken ek bir koşul belirtmek üzere bir `when` yan tümcesi ekleyebilirsiniz. `when` yan tümcesi, Boolean değer döndüren herhangi bir ifade olabilir.

Aşağıdaki örnek, bir temel `Shape` sınıfını, `Shape`türetilen bir `Rectangle` sınıfını ve `Rectangle`türetilen bir `Square` sınıfını tanımlar. `ShowShapeInfo`, `Square` bir nesne olarak örneği oluşturulmasa bile, eşit uzunlukta ve genişliklerin `Square` olarak atanmış bir `Rectangle` nesnesine davrandığından emin olmak için `when` yan tümcesini kullanır. Yöntemi, `null` bir nesne veya alanı sıfır olan bir şekil hakkında bilgi görüntülemeyi denemez.

[!code-csharp[when-clause#1](~/samples/snippets/csharp/language-reference/keywords/switch/when-clause.cs#1)]

Örnekteki bir `Shape` nesnesinin `null` yürütülüp yürütülmediğini test girişiminde bulunan `when` yan tümcesinin olduğunu unutmayın. `null` için test edilecek doğru tür deseninin `case null:`.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Switch ifadesine](~/_csharplang/spec/statements.md#the-switch-statement) bakın. Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [if-else](if-else.md)
- [Desen Eşleştirme](../../pattern-matching.md)
