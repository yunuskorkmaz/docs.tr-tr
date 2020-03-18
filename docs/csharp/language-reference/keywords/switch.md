---
title: C# anahtar deyimi
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
ms.openlocfilehash: e5580e81b9175cd95491fdba724bacbffa692a5e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345388"
---
# <a name="switch-c-reference"></a>anahtar (C# referansı)

`switch`*eşleşme ifadesi*ile bir desen eşleşmesi dayalı aday listesinden yürütmek için tek bir *anahtar bölümü* seçen bir seçim deyimidir.

[!code-csharp[switch#1](~/samples/snippets/csharp/language-reference/keywords/switch/switch1.cs#1)]

Tek `switch` bir ifade üç veya daha fazla koşula karşı test edilirse, deyim genellikle [if-else](if-else.md) yapısına alternatif olarak kullanılır. Örneğin, aşağıdaki `switch` deyim, tür `Color` değişkeninin üç değerden birine sahip olup olmadığını belirler:

[!code-csharp[switch#3](~/samples/snippets/csharp/language-reference/keywords/switch/switch3.cs#1)]

Bir `if` - `else` yapıyı kullanan aşağıdaki örneğe eşdeğerdir.

[!code-csharp[switch#3a](~/samples/snippets/csharp/language-reference/keywords/switch/switch3a.cs#1)]

## <a name="the-match-expression"></a>Maç ifadesi

Eşmatch ifadesi etiketlerdeki `case` desenlerle eşleşen değeri sağlar. Sözdizimi:

```csharp
   switch (expr)
```

C# 6 ve daha önce, eşleşme ifadesi aşağıdaki türlerin bir değeri döndüren bir ifade olmalıdır:

- bir [char](../builtin-types/char.md).
- bir [dize](../builtin-types/reference-types.md).
- bir [bool](../builtin-types/bool.md).
- gibi [integral](../builtin-types/integral-numeric-types.md) `int` bir integral değeri veya `long`bir .
- bir [enum](../builtin-types/enum.md) değeri.

C# 7.0 ile başlayarak, eşleşme ifadesi null olmayan herhangi bir ifade olabilir.

## <a name="the-switch-section"></a>Anahtar bölümü

Deyim, `switch` bir veya daha fazla anahtar bölümü içerir. Her geçiş bölümü bir veya daha fazla *büyük/küçük harf etiketi* (büyük/küçük harf veya varsayılan etiket) ve ardından bir veya daha fazla deyim içerir. İfade, `switch` herhangi bir anahtar bölümüne yerleştirilen en fazla bir varsayılan etiket içerebilir. Aşağıdaki örnekte, `switch` her biri iki deyim içeren üç geçiş bölümü içeren basit bir ifade gösterilmektedir. İkinci anahtar bölümü `case 2:` ve `case 3:` etiketleri içerir.

Bir `switch` deyim herhangi bir sayıda geçiş bölümü içerebilir ve her bölümde aşağıdaki örnekte gösterildiği gibi bir veya daha fazla servis talebi etiketi bulunabilir. Ancak, iki büyük/küçük harf etiketi aynı ifadeyi içeremez.

[!code-csharp[switch#2](~/samples/snippets/csharp/language-reference/keywords/switch/switch2.cs#1)]

Anahtar deyiminde yalnızca bir anahtar bölümü çalıştırır. C# yürütmenin bir anahtar bölümünden diğerine devam etmesine izin vermez. Bu nedenle, aşağıdaki kod bir derleyici hatası oluşturur, CS0163: "Denetim bir\<büyük/harf etiketinden (büyük/küçük harf etiketi>) diğerine düşemez."

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

Bu gereksinim genellikle bir [ara](break.md), [goto](goto.md)veya [iade](return.md) deyimi kullanılarak anahtar bölümünden açıkça çıkarılarak karşılanır. Ancak, program denetiminin `default` geçiş bölümüne girememesini sağladığından, aşağıdaki kod da geçerlidir.

[!code-csharp[switch#4](~/samples/snippets/csharp/language-reference/keywords/switch/switch4.cs#1)]

Eşmaç ifadesiyle eşleşen bir durum etiketiyle geçiş bölümündeki ifade listesinin yürütülmesi ilk deyimle başlar ve genellikle bir `break`atlama `goto case` `goto label`deyimi `return`, `throw`, , , , veya , gibi bir atlama deyimine ulaşılıncaya kadar, ekstre listesi boyunca ilerler. Bu noktada, denetim deyimi `switch` dışında veya başka bir servis talebi etiketine aktarılır. Bir `goto` deyim, kullanılırsa, denetimi sabit bir etikete aktarmalıdır. Denetimi sabit olmayan bir etikete aktarmaya çalışmak istenmeyen yan etkilere sahip olabileceğinden, denetimi kodda istenmeyen bir konuma aktarmak veya sonsuz bir döngü oluşturmak gibi bu kısıtlama gereklidir.

## <a name="case-labels"></a>Büyük/küçük harf etiketleri

Her servis talebi etiketi, eşleşme ifadesiyle (önceki `caseSwitch` örneklerdeki değişken) karşılaştırmak için bir desen belirtir. Eşleşirse, denetim **ilk** eşleşen servis talebi etiketini içeren anahtar bölümüne aktarılır. Büyük/küçük harf etiketi deseni eşleşme ifadesiyle eşleşmiyorsa, denetim varsa servis talebi etiketinin `default` olduğu bölüme aktarılır. Servis talebi yoksa, `default` herhangi bir anahtar bölümündeki ifadeler yürütülür `switch` ve denetim ifadenin dışına aktarılır.

Deyim ve `switch` desen eşleştirmesi hakkında bilgi için [deyim bölümüyle eşleşen Desen'e `switch` ](#pattern) bakın.

C# 6 yalnızca sabit deseni desteklediğinden ve sabit değerlerin tekrarına izin vermedığından, büyük/küçük harf etiketleri birbirini dışlayan değerleri tanımlar ve eşleç ifadesiyle yalnızca bir desen eşleşebilir. Sonuç olarak, deyimlerin `case` görüntülenme sırası önemsizdir.

Ancak C# 7.0'da, diğer desenler desteklendirildik, büyük/küçük harf etiketleri birbirini dışlayan değerler tanımlamaz ve birden çok desen eşleç ifadeyle eşleşebilir. Yalnızca eşleşen deseni içeren ilk anahtar bölümündeki ifadeler yürütüldünlü olduğundan, deyimlerin görüntülenme `case` sırası artık önemlidir. C#, servis talebi bildirimi veya deyimleri önceki deyimlerin alt kümelerine eşdeğer veya alt kümeleri olan bir anahtar bölümü algılarsa, bir derleyici hatası oluşturur, CS8120, "Anahtar durumu zaten önceki bir servis talebi tarafından işlenmiştir."

Aşağıdaki örnekte, `switch` birbirini dışlayan çeşitli desenler kullanan bir deyim gösterin. `case 0:` Anahtar bölümünü artık `switch` deyimdeki ilk bölüm olmayacak şekilde taşırsanız, Değeri sıfır olan bir tamsayı tüm tamsayılara ait bir alt küme olduğundan C# derleyici hatası oluşturur, bu `case int val` da deyimtarafından tanımlanan desendir.

[!code-csharp[switch#5](~/samples/snippets/csharp/language-reference/keywords/switch/switch5.cs#1)]

Bu sorunu düzeltebilir ve derleyici uyarısını iki şekilde ortadan kaldırabilirsiniz:

- Anahtar bölümlerinin sırasını değiştirerek.

- Etikette bir when `case` yan [tümcesi](#when) kullanarak.

## <a name="the-default-case"></a>Dava `default`

Servis `default` talebi, eşleşme ifadesi başka `case` bir etiketle eşleşmiyorsa, yürütülecek anahtar bölümünü belirtir. Bir `default` servis talebi yoksa ve eşleşme ifadesi başka `case` bir etiketle eşleşmiyorsa, program akışı deyimden `switch` düşer.

Servis `default` `switch` talebi, ifadedeki herhangi bir sırada görünebilir. Kaynak kodundaki sırası ne olursa olsun, tüm `case` etiketler değerlendirildikten sonra her zaman en son değerlendirilir.

## <a name="a-namepattern--pattern-matching-with-the-switch-statement"></a><a name="pattern" />`switch` Deyimle eşleşen desen

Her `case` deyim, eşleşme ifadesiyle eşleşirse, içerdiği anahtar bölümünün yürütülmesine neden olan bir desen tanımlar. C#'nin tüm sürümleri sabit deseni destekler. Kalan desenler C# 7.0 ile başlayarak desteklenir.

### <a name="constant-pattern"></a>Sabit desen

Sabit desen, eşleşme ifadesinin belirtilen bir sabite eşit olup olmadığını sınar. Sözdizimi:

```csharp
   case constant:
```

*sabit* için test etmek için değer olduğu. *sabit* aşağıdaki sabit ifadelerden biri olabilir:

- Bir [bool](../builtin-types/bool.md) literal: `false`ya da `true` .
- Herhangi [integral](../builtin-types/integral-numeric-types.md) bir `int`integral sabiti, `long`a `byte`, veya bir .
- Bildirilen `const` değişkenin adı.
- Numaralandırma sabiti.
- Bir [char](../builtin-types/char.md) edebi.
- Bir [dize](../builtin-types/reference-types.md) gerçek.

Sabit ifade aşağıdaki gibi değerlendirilir:

- *Expr* ve *constant* integral türleri ise, C# eşitlik işleci `true` ifadenin döndürüp döndürülmediğini (yani, olup olmadığını) `expr == constant`belirler.

- Aksi takdirde, ifadenin değeri statik [Object.Equals (expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) yöntemine yapılan bir çağrı ile belirlenir.

Aşağıdaki örnek, belirli bir tarihin hafta sonu, çalışma haftasının ilk günü, çalışma haftasının son günü veya çalışma haftasının ortası olup olmadığını belirlemek için sabit deseni kullanır. Bu numaralandırma <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> üyeleri <xref:System.DayOfWeek> nezdinde mevcut günün özelliğini değerlendirir.

[!code-csharp[switch#7](~/samples/snippets/csharp/language-reference/keywords/switch/const-pattern.cs#1)]

Aşağıdaki örnek, otomatik kahve makinesini taklit eden bir konsol uygulamasında kullanıcı girişini işlemek için sabit deseni kullanır.

[!code-csharp[switch#6](~/samples/snippets/csharp/language-reference/keywords/switch/switch6.cs)]

### <a name="type-pattern"></a>Tür deseni

Tür deseni kısa tür değerlendirme ve dönüştürme sağlar. Desen eşleştirmesi `switch` gerçekleştirmek için deyimle kullanıldığında, bir ifadenin belirli bir türe dönüştürülüp dönüştürülemeyeceğini sınar ve olabilirse, bu tür bir değişkene atar. Sözdizimi:

```csharp
   case type varname
```

*tür,* *expr* sonucunun dönüştürüldüğü türün adıdır ve *varname,* eşleşme başarılı olursa *expr* sonucunun dönüştürüldüğü nesnedir. Derleme zamanı *expr* türü, C# 7.1 ile başlayan genel bir tür parametresi olabilir.

İfade, `case` `true` aşağıdakilerden herhangi birinin doğru olup olmadığıdır:

- *expr* *türü*olarak aynı türde bir örnektir.

- *expr* *türünden*türetilen bir tür örneğidir. Başka bir deyişle, *expr* sonucu *türü*bir örnek için upcast olabilir.

- *expr* *türü*bir taban sınıf olan bir derleme-zaman türü vardır ve *expr* *türü* veya *türünden*türetilen bir çalışma zamanı türü vardır. Bir değişkenin *derleme zamanı türü,* değişkenin tür bildiriminde tanımlandığı şekilde türüdür. Bir değişkenin *çalışma zamanı türü,* bu değişkene atanan örneğin türüdür.

- *expr* *türü* arabirimi uygulayan bir tür örneğidir.

Servis talebi ifadesi doğruysa, *varname* kesinlikle atanır ve yalnızca geçiş bölümünde yerel kapsama sahiptir.

Bir `null` türle eşleşmediğini unutmayın. Bir `null`eşlemek için aşağıdaki `case` etiketi kullanın:

```csharp
case null:
```

Aşağıdaki örnek, çeşitli koleksiyon türleri hakkında bilgi sağlamak için tür deseni kullanır.

[!code-csharp[type-pattern#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern.cs#1)]

Bunun `object`yerine, aşağıdaki kodda gösterildiği gibi, tür parametresi olarak koleksiyonun türünü kullanarak genel bir yöntem yapabilirsiniz:

[!code-csharp[type-pattern#3](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern3.cs#1)]

Genel sürüm iki şekilde ilk örnek farklıdır. İlk olarak, çantayı `null` kullanamazsınız. Derleyici herhangi bir rasgele türü `T` `object`başka bir türe dönüştüremediğinden sabit bir servis talebi kullanamazsınız. Ne `default` durumda şimdi olmayan bir null `object`için testler olmuştu . Bu, `default` vaka testlerinin `null`yalnızca .

Desen eşleştirme olmadan, bu kod aşağıdaki gibi yazılabilir. Tür deseni eşleştirmesinin kullanımı, dönüştürme nin sonucunun bir `null` mi yoksa tekrarlanan dökümler mi olduğunu test etme gereksinimini ortadan kaldırarak daha kompakt, okunabilir kod üretir.

[!code-csharp[type-pattern2#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern2.cs#1)]

## <a name="a-namewhen--the-case-statement-and-the-when-clause"></a><a name="when" />İfade `case` ve `when` fıkra

C# 7.0 ile başlayarak, büyük/küçük harf deyimleri `when` birbirini dışlamadığıiçin, servis talebi bildiriminin doğru olarak değerlendirilmesi için tatmin edilmesi gereken ek bir koşul belirtmek için bir yan tümce ekleyebilirsiniz. Yan `when` tümce boolean değerini döndüren herhangi bir ifade olabilir.

Aşağıdaki örnekte bir `Shape` taban sınıf, `Rectangle` ve 'den `Shape`türeyen bir sınıf `Rectangle`ve .'den türeyen bir `Square` sınıf tanımlanır. Bir `Square` nesne `when` olarak anında `ShowShapeInfo` değil olsa `Rectangle` `Square` bile eşit uzunlukve genişlikleri atanmış bir nesneyi davranır sağlamak için yan tümceyi kullanır. Yöntem, alanı sıfır olan `null` bir nesne veya şekil hakkında bilgi görüntülemeye çalışmaz.

[!code-csharp[when-clause#1](~/samples/snippets/csharp/language-reference/keywords/switch/when-clause.cs#1)]

Örnekteki `when` `Shape` nesnenin yürütülüp uygulanmadığını sınamaya `null` çalışan yan tümcesinin yürütülmediğini unutmayın. Bir `null` için test etmek için `case null:`doğru tür deseni .

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# Dil Belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [geçiş deyimine](~/_csharplang/spec/statements.md#the-switch-statement) bakın. Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Kelimeler](index.md)
- [if-else](if-else.md)
- [Desen Eşleştirme](../../pattern-matching.md)
