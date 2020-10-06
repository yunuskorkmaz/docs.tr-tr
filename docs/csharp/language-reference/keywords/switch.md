---
description: Switch (C# Başvurusu)
title: C# anahtar ekstresi
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
ms.openlocfilehash: d8fae870bb3a6fdda735a028dc1da20213a68a31
ms.sourcegitcommit: a8a205034eeffc7c3e1bdd6f506a75b0f7099ebf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2020
ms.locfileid: "91756045"
---
# <a name="switch-c-reference"></a>Switch (C# Başvurusu)

Bu makale, `switch` ifadesini içerir. İfade hakkında daha fazla bilgi için `switch` (C# 8,0 ' de tanıtılan), [ifadeler ve işleçler](../operators/index.md) bölümündeki [ `switch` ifadelerde](../operators/switch-expression.md) bulunan makaleye bakın.

`switch`, *Match ifadesiyle*bir model eşleşmesi temelinde aday listesinden yürütülecek tek bir *anahtar bölümü* seçen bir seçim deyimidir.

[!code-csharp[switch#1](~/samples/snippets/csharp/language-reference/keywords/switch/switch1.cs#1)]

`switch`Tek bir ifade üç veya daha fazla koşula göre test edildiğinde deyim genellikle [If-Else](if-else.md) yapısına alternatif olarak kullanılır. Örneğin, aşağıdaki ifade, `switch` türünde bir değişkenin `Color` üç değerden birine sahip olup olmadığını belirler:

[!code-csharp[switch#3](~/samples/snippets/csharp/language-reference/keywords/switch/switch3.cs#1)]

Yapı kullanan aşağıdaki örneğe eşdeğerdir `if` - `else` .

[!code-csharp[switch#3a](~/samples/snippets/csharp/language-reference/keywords/switch/switch3a.cs#1)]

## <a name="the-match-expression"></a>Match ifadesi

Match ifadesi, etiketlerin desenleriyle eşleşecek değeri sağlar `case` . Sözdizimi şöyledir:

```csharp
   switch (expr)
```

C# 6 ve önceki sürümlerde, Match ifadesi aşağıdaki türlerde bir değer döndüren bir ifade olmalıdır:

- bir [char](../builtin-types/char.md).
- bir [dize](../builtin-types/reference-types.md).
- bir [bool](../builtin-types/bool.md).
- veya gibi bir [integral](../builtin-types/integral-numeric-types.md) değeri `int` `long` .
- bir [sabit listesi](../builtin-types/enum.md) değeri.

C# 7,0 ile başlayarak, Match ifadesi null olmayan herhangi bir ifade olabilir.

## <a name="the-switch-section"></a>Anahtar bölümü

Bir `switch` ifade bir veya daha fazla anahtar bölümü içerir. Her anahtar bölümü bir veya daha fazla *durum etiketi* (bir Case veya default etiketi) ve ardından bir veya daha fazla deyimi içerir. `switch`İfade, herhangi bir switch bölümüne yerleştirilmiş en çok bir varsayılan etiket içerebilir. Aşağıdaki örnek `switch` , her biri iki deyim içeren üç anahtar bölümü olan basit bir deyimi göstermektedir. İkinci anahtar bölümü `case 2:` ve `case 3:` etiketlerini içerir.

Bir `switch` ifade herhangi bir sayıda anahtar bölümü içerebilir ve aşağıdaki örnekte gösterildiği gibi her bölümde bir veya daha fazla Case etiketi olabilir. Ancak, iki durum etiketi de aynı ifadeyi içeremez.

[!code-csharp[switch#2](~/samples/snippets/csharp/language-reference/keywords/switch/switch2.cs#1)]

Switch deyimindeki yalnızca bir switch bölümü yürütülür. C#, yürütmenin bir geçiş bölümünden bir sonrakine devam etmesine izin vermez. Bu nedenle, aşağıdaki kod bir derleyici hatası oluşturuyor, CS0163: "Denetim bir case etiketinden () bir diğerine geçemez \<case label> ."

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

Bu gereksinim, genellikle bir [Break](break.md), [goto](goto.md)veya [Return](return.md) ifadesiyle Switch bölümünden açıkça çıkarken karşılanır. Ancak, program denetiminin Switch bölümüne dönememesini sağladığından aşağıdaki kod de geçerlidir `default` .

[!code-csharp[switch#4](~/samples/snippets/csharp/language-reference/keywords/switch/switch4.cs#1)]

Eşleştirme ifadesiyle eşleşen bir Case etiketi ile Switch bölümündeki deyim listesinin yürütülmesi ilk deyimle başlar ve genellikle,,, veya gibi bir sıçrama deyimine `break` `goto case` `goto label` `return` ulaşılana kadar deyim listesini ilerler `throw` . Bu noktada denetim `switch` deyimin dışına veya başka bir Case etiketine aktarılır. Bir `goto` ifade kullanılıyorsa, denetim bir sabit etikete aktarılmalıdır. Bu kısıtlama gereklidir, çünkü denetimi sabit olmayan bir etikete aktarmaya çalışmak, denetimi kodda istenmeyen bir konuma aktarmak veya sonsuz bir döngü oluşturmak gibi istenmeyen yan etkilere sahip olabilir.

## <a name="case-labels"></a>Case etiketleri

Her Case etiketi, Match ifadesiyle Karşılaştırılacak bir model belirtir ( `caseSwitch` Önceki örneklerde bulunan değişkeni). Eşleşiyorsa denetim, **ilk** eşleşen Case etiketini içeren Switch bölümüne aktarılır. Hiçbir Case etiket deseninin eşleşme ifadesiyle eşleşmesi halinde, denetim varsa Case etiketi ile bölüme aktarılır `default` . `default`Böyle bir durum yoksa, herhangi bir switch bölümünde hiçbir deyim yürütülmez ve denetim deyimin dışına aktarılır `switch` .

`switch`Deyimle ve model eşleştirme hakkında daha fazla bilgi için bkz. [ `switch` deyimle eşleşen model](#pattern-matching-with-the-switch-statement) bölümü.

C# 6 yalnızca sabit bir stili desteklediğinden ve sabit değerlerin yinelenmesinde izin vermediğinden, Case etiketleri birbirini dışlayan değerleri tanımlar ve yalnızca bir desenler eşleştirme ifadesiyle eşleştirebilir. Sonuç olarak, `case` deyimlerin görünme sırası önemli değildir.

Ancak C# 7,0 ' de, diğer desenler desteklendiğinden, büyük/küçük harf etiketlerinin birbirini dışlayan değerler tanımlamamalıdır ve birden çok desen eşleştirme ifadesiyle eşleşemez. Yalnızca eşleşen düzeni içeren ilk anahtar bölümündeki deyimler yürütülene göre, `case` deyimlerin göründüğü sıra artık önemlidir. C#, Case deyimi veya deyimleri önceki deyimlerin alt kümelerine eşit olan bir switch bölümü algılarsa, "switch case zaten önceki bir durum tarafından işlenmiştir." bir derleyici hatası oluşturur.

Aşağıdaki örnek, `switch` birbirini dışlayan farklı desenler kullanan bir ifadeyi gösterir. `case 0:`Switch bölümünü deyimdeki ilk bölüm olmayacak şekilde taşırsanız `switch` , C# bir derleyici hatası oluşturur, çünkü değeri sıfır olan bir tamsayı, deyimin tanımladığı model olan tüm tamsayıların alt kümesidir `case int val` .

[!code-csharp[switch#5](~/samples/snippets/csharp/language-reference/keywords/switch/switch5.cs#1)]

Bu sorunu düzeltebilir ve iki şekilde derleyici uyarısını ortadan kaldırabilirsiniz:

- Anahtar bölümlerinin sırasını değiştirerek.

- Etikette bir [WHERE yan tümcesi](#the-case-statement-and-the-when-clause) kullanarak `case` .

## <a name="the-default-case"></a>`default`Büyük/küçük harf

Bu `default` durumda, eşleşme ifadesi başka bir etiketle eşleşmezse yürütülecek Switch bölümü belirtilir `case` . Bir `default` servis talebi yoksa ve eşleştirme ifadesi başka bir `case` etiketle eşleşmiyorsa, program akışı deyim aracılığıyla geçer `switch` .

`default`Durum, deyimdeki herhangi bir sırada görünebilir `switch` . Kaynak kodundaki sıralarından bağımsız olarak, tüm Etiketler hesaplandıktan sonra her zaman son değerlendirilir `case` .

## <a name="pattern-matching-with-the-switch-statement"></a>Deyimle eşleşen desenler `switch`

Her `case` deyim, eşleşme ifadesiyle eşleşiyorsa, kapsayan anahtar bölümünün yürütülmesine neden olan bir model tanımlar. Tüm C# sürümleri sabit bir stili destekler. Kalan desenler C# 7,0 ' den başlayarak desteklenir.

### <a name="constant-pattern"></a>Sabit model

Sabit model, eşleşme ifadesinin belirtilen bir sabit değere eşit olup olmadığını sınar. Sözdizimi şöyledir:

```csharp
   case constant:
```

Burada *Constant* , test edilecek değerdir. *sabit* , aşağıdaki sabit ifadelerden herhangi biri olabilir:

- Bir [bool](../builtin-types/bool.md) sabit değeri: `true` ya da `false` .
- ,, Veya gibi herhangi bir [integral](../builtin-types/integral-numeric-types.md) sabiti `int` `long` `byte` .
- Belirtilen `const` değişkenin adı.
- Bir numaralandırma sabiti.
- Bir [char](../builtin-types/char.md) sabit değeri.
- [Dize](../builtin-types/reference-types.md) sabit değeri.

Sabit ifade aşağıdaki gibi değerlendirilir:

- *Expr* ve *Constant* Integral türse, C# eşitlik işleci ifadenin döndürülüp döndürülmeyeceğini `true` (yani, ne gibi `expr == constant` ) belirler.

- Aksi takdirde, ifadenin değeri static [Object. Equals (Expr, Constant)](xref:System.Object.Equals(System.Object,System.Object)) yöntemi çağrısıyla belirlenir.

Aşağıdaki örnek, belirli bir tarihin hafta sonu, çalışma haftasının ilk günü mi, çalışma haftasının son günü mi yoksa çalışma haftasının ortasında mi olduğunu anlamak için sabit bir düzende kullanılır. <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType>Geçerli günün özelliğini numaralandırmanın üyelerine göre değerlendirir <xref:System.DayOfWeek> .

[!code-csharp[switch#7](~/samples/snippets/csharp/language-reference/keywords/switch/const-pattern.cs#1)]

Aşağıdaki örnek, bir otomatik kahve makinesine benzetim yapan bir konsol uygulamasında kullanıcı girişini işlemek için sabit bir model kullanır.

[!code-csharp[switch#6](~/samples/snippets/csharp/language-reference/keywords/switch/switch6.cs)]

### <a name="type-pattern"></a>Tür stili

Tür stili, kısa tür değerlendirmesi ve dönüştürmeyi mümkün bir şekilde sunar. `switch`Model eşleştirmeyi gerçekleştirmek için ifadesiyle birlikte kullanıldığında, bir ifadenin belirtilen bir türe dönüştürülüp dönüştürülebileceğini sınar ve bu, mümkünse, bu türden bir değişkene bu değeri verebilir. Sözdizimi şöyledir:

```csharp
   case type varname
```

Burada *tür* , *Expr* 'nin sonucunun dönüştürülecek türün adı ve *varname* , eşleşme başarılı olursa *ifadenin* sonucunun dönüştürüldüğü nesnedir. *İfadenin* derleme zamanı türü, C# 7,1 ' den başlayarak genel bir tür parametresi olabilir.

`case`İfadesi `true` aşağıdakilerden herhangi biri doğru ise olur:

- *Expr* , *türü*ile aynı türde bir örneğidir.

- *Expr* *türünden*türetilen bir türün örneğidir. Diğer bir deyişle, *ifadenin* sonucu *türünde*bir örneğe eklenebilir.

- *ifadenin* *türünde bir*temel sınıf olan bir derleme zamanı türü vardır ve *Expr* *türü* *veya türünden türetilmiş*bir çalışma zamanı türü vardır. Bir değişkenin *derleme zamanı türü* , tür bildiriminde tanımlanan değişkenin türüdür. Bir değişkenin *çalışma zamanı türü* , bu değişkene atanan örneğin türüdür.

- *Expr* , *tür* arabirimini uygulayan bir türün örneğidir.

Case ifadesi true ise, *varname* kesinlikle atanır ve yalnızca switch bölümü içinde yerel kapsama sahiptir.

`null`Bir türle eşleşmez. Bir ile eşleştirmek için `null` aşağıdaki `case` etiketi kullanın:

```csharp
case null:
```

Aşağıdaki örnek, çeşitli türlerdeki koleksiyon türleri hakkında bilgi sağlamak için tür modelini kullanır.

[!code-csharp[type-pattern#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern.cs#1)]

Yerine, `object` aşağıdaki kodda gösterildiği gibi, tür parametresi olarak koleksiyonun türünü kullanarak genel bir yöntem oluşturabilirsiniz:

[!code-csharp[type-pattern#3](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern3.cs#1)]

Genel sürüm, ilk örnekten iki şekilde farklıdır. İlk olarak, bu durumu kullanamazsınız `null` . Derleyici herhangi bir rastgele türü dışında herhangi bir türe dönüştüremediği için herhangi bir sabit durumu kullanamazsınız `T` `object` . `default`Artık null olmayan bir durum için test edilmiş olabilir `object` . Bu, `default` yalnızca için büyük/küçük harf testleri anlamına gelir `null` .

Model eşleştirmesi olmadan bu kod aşağıdaki gibi yazılabilir. Tür deseninin kullanımı, dönüştürmenin sonucunun bir `null` veya yinelenen yayınlar gerçekleştirmesini sağlamak için bir veya daha fazla okunabilir kod üretir.

[!code-csharp[type-pattern2#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern2.cs#1)]

## <a name="the-case-statement-and-the-when-clause"></a>`case`Deyimi ve `when` yan tümcesi

C# 7,0 ' den itibaren, Case deyimlerinin birbirini `when` dışlanması gerektiğinden, Case ifadesinin true olarak değerlendirilmesi için karşılanması gereken ek bir koşul belirtmek üzere bir yan tümce ekleyebilirsiniz. `when`Yan tümce, Boolean değer döndüren herhangi bir ifade olabilir.

Aşağıdaki örnek, bir temel `Shape` sınıf, `Rectangle` öğesinden türetilen bir sınıf `Shape` ve `Square` öğesinden türetilen bir `Rectangle` sınıf tanımlar. `when` `ShowShapeInfo` `Rectangle` Bir nesne `Square` olarak örneği oluşturulmasa bile eşit uzunlukta ve genişlikler atanan bir nesneyi bir nesne olarak değerlendirdiğinden emin olmak için yan tümcesini kullanır `Square` . Yöntemi, `null` veya alanı sıfır olan bir şekil gibi bir nesne hakkında bilgi görüntülemeyi denemez.

[!code-csharp[when-clause#1](~/samples/snippets/csharp/language-reference/keywords/switch/when-clause.cs#1)]

`when`Örnekteki yan tümcesinin, bir `Shape` nesnenin yürütülüp yürütülmediğini test girişiminde bulunduğunu unutmayın `null` . Bir için test edilecek doğru tür deseninin türü `null` `case null:` .

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Switch ifadesine](~/_csharplang/spec/statements.md#the-switch-statement) bakın. Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# anahtar sözcükleri](index.md)
- [if-else](if-else.md)
- [Desen Eşleştirme](../../pattern-matching.md)
