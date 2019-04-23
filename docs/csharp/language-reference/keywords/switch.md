---
title: C# switch deyimi
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
ms.openlocfilehash: 960394bd61f9e9163fe93c4324bf708d50ec3e08
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59481463"
---
# <a name="switch-c-reference"></a>geçiş (C# Başvurusu)

`switch` tek bir seçtiği bir seçim deyimi *geçiş bölümüne* bir desen eşleştirme ile temel adaylar listesinden yürütülecek *eşleşen ifade*.

[!code-csharp[switch#1](~/samples/snippets/csharp/language-reference/keywords/switch/switch1.cs#1)]

`switch` Deyimi bir alternatifi olarak kullanılan genellikle bir [if-else](if-else.md) tek bir ifade, üç veya daha fazla koşul karşı test edildiyse oluşturun. Örneğin, aşağıdaki `switch` ifadesi bir değişken türü olup olmadığını belirler `Color` üç değerden birine sahiptir:

[!code-csharp[switch#3](~/samples/snippets/csharp/language-reference/keywords/switch/switch3.cs#1)]

Kullanan aşağıdaki örneğe eşdeğerdir bir `if` - `else` oluşturun.

[!code-csharp[switch#3a](~/samples/snippets/csharp/language-reference/keywords/switch/switch3a.cs#1)]

## <a name="the-match-expression"></a>Eşleştirme ifadesi

Eşleşme ifade desenlerinde eşleştirilecek değer sağlar `case` etiketler. Kendi sözdizimi aşağıdaki gibidir:

```csharp
   switch (expr)
```

İçinde C# 6 ve önceki sürümlerde eşleştirme ifadesi bir değer türlerinden birini döndüren bir ifade olması gerekir:

- bir [char](char.md).
- bir [dize](string.md).
- bir [bool](bool.md).
- bir tamsayı değeri olan gibi bir [int](int.md) veya [uzun](long.md).
- bir [enum](enum.md) değeri.

C# 7.0 ile başlayarak, eşleştirme ifadesi null olmayan herhangi bir ifade olabilir.

## <a name="the-switch-section"></a>Anahtar bölümü

A `switch` deyimi bir veya daha fazla anahtar bölüm içerebilir. Her anahtar bölümü bir veya daha fazla içeren *case etiketleri* (bir case veya default etiketi) ve ardından bir veya daha fazla deyim tarafından. `switch` Deyimi herhangi bir anahtar bölümü yerleştirilen en fazla bir varsayılan etiket içerebilir. Aşağıdaki örnek, basit bir gösterir `switch` üç anahtar bölümü, her iki deyim içeren olan ifade. İkinci bölüm anahtarını içeren `case 2:` ve `case 3:` etiketler.

A `switch` deyimi anahtar bölümlerinin sayısını içerir ve her bölüm aşağıdaki örnekte gösterildiği gibi bir veya daha fazla durum etiketi olabilir. Ancak, hiçbir iki durum etiketi aynı ifadesi içeriyor olabilir.

[!code-csharp[switch#2](~/samples/snippets/csharp/language-reference/keywords/switch/switch2.cs#1)]

Switch deyimi içinde yalnızca bir anahtar bölümü yürütür. C#bir geçiş bölümünden diğerine devam etmek için yürütmeye izin vermez. Bu nedenle, aşağıdaki kod bir Derleyici Hatası CS0163 oluşturur: "Denetim olamaz atlayabilir bir case etiketinden (\<case etiketi >) diğerine."

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

Bu gereksinim, genellikle açıkça kullanarak switch bölümüne çıkarak karşılanır bir [sonu](break.md), [goto](goto.md), veya [dönüş](return.md) deyimi. Program denetimi için geçemez sağlar ancak, aşağıdaki kod Ayrıca, geçersiz çünkü `default` bölümüne geçin.

[!code-csharp[switch#4](~/samples/snippets/csharp/language-reference/keywords/switch/switch4.cs#1)]

Eşleştirme ifadesi ile eşleşen bir durum etiketi ile anahtar bölümdeki ifade listesinin yürütülmesi ilk deyimden başlar ve deyim listesi boyunca genellikle bir atlama deyimine ulaşılıncaya kadar devam eder bir `break`, `goto case`, `goto label`, `return`, veya `throw`, ulaşıldı. Bu noktada, denetimi dışında aktarılan `switch` deyimi veya başka bir case etiketi. A `goto` deyimi kullanılırsa, gerekir aktarım denetimi için sabit bir etiket. Sabit olmayan etiketine denetim aktarmaya çalışırken istenmeyen yan etkileri, bu tür istenmeyen bir kod konumuna denetimi aktarma veya sonsuz bir döngüye oluşturma olabileceği için bu kısıtlama gereklidir.

## <a name="case-labels"></a>Durum etiketi

Her durum etiketi eşleşen ifade karşılaştırmak için bir desen belirtir ( `caseSwitch` önceki örneklerde değişken). Eşleşiyorlarsa denetimi içeren anahtar bölüme aktarılır **ilk** eşleşen case etiketi. Hiçbir durum etiketi desen eşleştirme ifadesi eşleşirse denetimi ile bölümüne aktarılır `default` varsa durum etiketi. Yoksa hiçbir `default` çalışması, her anahtar bölümü yok deyimlerinde yürütülür ve denetimin dışına aktarılır `switch` deyimi.

Hakkında bilgi için `switch` deyimi ve desen eşleştirme, [ile desen eşleştirme `switch` deyimi](#pattern) bölümü.

Çünkü C# 6 yalnızca sabit desen destekler ve sabit değerleri tekrarını izin vermez, case etiketleri birbirini dışlayan değerleri tanımlayın ve yalnızca bir desen eşleştirme ifadesi eşleşebilir. Sonuç olarak, bir sırayı `case` deyimlerinizin önemli olduğu.

C# 7.0, ancak diğer desenleri desteklendiğinden, case etiketleri birbirini dışlayan değerleri tanımlamanız gerekir değil ve eşleştirme ifadesi birden çok desen eşleştiğinde. Yalnızca eşleşen desen içeren ilk geçiş bölümündeki deyimlerin yürütülme nedeni sırayı `case` deyimlerinizin'ın, artık önemlidir. C#, case deyimi veya deyimler eşdeğerdir veya önceki deyimlerin kümeleridir switch bölümüne algılarsa, "anahtar durumu önceki bir case tarafından zaten işlendi." bir derleyici hatası, CS8120, oluşturur.

Aşağıdaki örnekte bir `switch` olmayan-birbirini dışlayan desenleri çeşitli kullanan deyimi. Taşırsanız `case 0:` artık ilk bölümü olması bölüm anahtarı `switch` deyimi C# tarafındantanımlananörnekleolduğubirtamsayıdeğerisıfırolantümtamsayılarınbiraltkümesiolduğuiçinbirderleyicihatasınanedenolur.`case int val` deyimi.

[!code-csharp[switch#5](~/samples/snippets/csharp/language-reference/keywords/switch/switch5.cs#1)]

Bu sorunu gidermek ve iki yoldan biriyle derleyici uyarısı ortadan kaldırır:

- Anahtar bölümlerin sırası değiştirerek.

- Kullanarak bir [zaman yan tümcesi](#when) içinde `case` etiketi.

## <a name="the-default-case"></a>`default` Çalışması

`default` Çalışması belirtir eşleştirme ifadesi diğer eşleşmiyorsa yürütmek için anahtar bölümü `case` etiketi. Varsa bir `default` durumu mevcut değil ve diğer eşleştirme ifadesi eşleşmeyen `case` program akışı etiketi geçmez `switch` deyimi.

`default` Çalışması herhangi bir sırada görünebilir `switch` deyimi. Kaynak kodunda kendi sırasını ne olursa olsun, her zaman son olarak, tüm değerlendirilmeden `case` etiketleri değerlendirilir.

## <a name="a-namepattern--pattern-matching-with-the-switch-statement"></a><a name="pattern" /> İle desen eşleştirme `switch` deyimi

Her `case` eşleşme ifadesi eşleşirse, yürütülecek içeren anahtar bölümü neden olan bir desen tanımlar. Sabit desen C# ' in tüm sürümleri destekler. Kalan desenleri, C# 7. 0'den itibaren desteklenir.

### <a name="constant-pattern"></a>Sabit desen

Sabit desen eşleştirme ifadesi belirtilen bir sabit eşit olup olmadığını sınar. Kendi sözdizimi aşağıdaki gibidir:

```csharp
   case constant:
```

Burada *sabit* sınamak için değer. *Sabit* aşağıdaki sabit ifadeler biri olabilir:

- A [bool](bool.md) değişmez değer, ya da `true` veya `false`.
- Herhangi bir integral sabit gibi bir [int](int.md), [uzun](long.md), veya bir [bayt](byte.md).
- Bildirilen bir adı `const` değişkeni.
- Bir numaralandırma sabiti.
- A [char](char.md) değişmez.
- A [dize](string.md) değişmez.

Sabit ifade gibi değerlendirilir:

- Varsa *expr* ve *sabit* integral türleri, C# eşitlik işlecini ifade döndürüp döndürmediğini belirler `true` (olup, diğer bir deyişle, `expr == constant`).

- Aksi takdirde, ifadenin değerini statik bir çağrı tarafından belirlenir [Object.Equals (ifade, sabit)](xref:System.Object.Equals(System.Object,System.Object)) yöntemi.

Aşağıdaki örnek, belirli bir tarihin hafta, çalışma haftası ya da ikinci iş haftanın son gününü iş haftanın ilk günü olup olmadığını belirlemek için sabit bir desen kullanır. Bu hesaplar <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> üyelerinin göre geçerli günün özelliği <xref:System.DayOfWeek> sabit listesi.

[!code-csharp[switch#7](~/samples/snippets/csharp/language-reference/keywords/switch/const-pattern.cs#1)]

Aşağıdaki örnek, kullanıcı girişini otomatik kahve makine taklit eden bir konsol uygulamasında işlemek için sabit desen kullanır.

[!code-csharp[switch#6](~/samples/snippets/csharp/language-reference/keywords/switch/switch6.cs)]

### <a name="type-pattern"></a>Tür deseni

Tür düzeni kısa türü değerlendirme ve dönüştürme sağlar. İle kullanıldığında `switch` desen eşleştirme, gerçekleştirmek için deyimi, bir ifadenin belirtilen bir türe dönüştürülüp dönüştürülemeyeceğini test eder ve olabilir, bu türden bir değişkene çevirir. Kendi sözdizimi aşağıdaki gibidir:

```csharp
   case type varname
```

Burada *türü* türün adı sonucunu *expr* Boolean'a dönüştürülecek ve *varname* hangi nesne sonucu *expr*eşleşmenin başarılı olursa dönüştürülür. Derleme zamanı türü *expr* ile başlayarak, bir genel tür parametresi olabilir C# 7.1.

`case` İfade `true` herhangi biri doğru ise:

- *Expr* örneği aynı türde olan *türü*.

- *Expr* türetilen türün bir örneği *türü*. Diğer bir deyişle, sonucunu *expr* örneğine başvurmanıza olabilir *türü*.

- *Expr* temel bir sınıfı olan bir derleme zamanı türü sahip *türü*, ve *expr* sahip olan bir çalışma zamanı türü *türü* veya türetilmiş *türü*. *Derleme zamanı tür* değişkeninin değişkenin türü bildiriminde tanımlanan türüdür. *Çalışma zamanı türü* bir değişken, bu değişkene atanan örnek türüdür.

- *Expr* uygulayan bir tür örneğidir *türü* arabirimi.

Case ifadesi true ise *varname* kesinlikle atanır ve yalnızca anahtarı bölüm içinde yerel kapsama sahiptir.

Unutmayın `null` bir türü ile eşleşmiyor. Eşleştirilecek bir `null`, kullanarak aşağıdaki `case` etiketi:

```csharp
case null:
```

Aşağıdaki örnek, çeşitli koleksiyon türleri hakkında bilgi sağlamak için tür deseni kullanır.

[!code-csharp[type-pattern#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern.cs#1)]

Yerine `object`, genel bir yöntem tür parametresi, aşağıdaki kodda gösterildiği gibi toplama türünü kullanarak yapabilirsiniz:

[!code-csharp[type-pattern#3](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern3.cs#1)]

Genel sürüm, iki yolla ilk örnek farklıdır. İlk olarak, kullanamazsınız `null` çalışması. Herhangi bir sabit çalışması kullanamazsınız, çünkü rastgele her türlü derleyici dönüştürülemiyor `T` dışındaki birine yazın `object`. Çürütülen `default` artık testler için null olmayan bir durumda `object`. Anlamına `default` case yalnızca testleri `null`.

Desen eşleştirme olmadan, bu kod şu şekilde yazılmış olabilir. Kullanım türü desen eşleştirme bir dönüştürmenin sonucu olup olmadığını sınamak için gereksinimini ortadan kaldırarak daha kompakt ve okunabilir bir kod oluşturur bir `null` veya yinelenen atamalar gerçekleştirmek için.

[!code-csharp[type-pattern2#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern2.cs#1)]

## <a name="a-namewhen--the-case-statement-and-the-when-clause"></a><a name="when" /> `case` Deyimi ve `when` yan tümcesi

Ekleyebileceğiniz Case deyimleri birbirini dışlayan olması gerekmez çünkü C# 7.0 ile başlayarak, bir `when` ek bir koşulu belirtmek için yan tümcesi memnun, doğru olarak değerlendirilebilmesi case deyimi için. `when` Yan tümcesi, bir Boole değeri döndüren herhangi bir ifade olabilir.

Aşağıdaki örnek, bir taban tanımlar `Shape` sınıfı, bir `Rectangle` türetilen sınıf `Shape`ve `Square` türetilen sınıf `Rectangle`. Kullandığı `when` emin olmak için yan `ShowShapeInfo` değerlendirir bir `Rectangle` eşit uzunlukta ve genişlikleri olarak atanmış olan bir nesne bir `Square` bile bunu olarak örneği edilmemiş bir `Square` nesne. Yöntem bilgileri görüntülemek çalışmaz herhangi bir nesne hakkında `null` veya bir şekil, alan sıfırdır.

[!code-csharp[when-clause#1](~/samples/snippets/csharp/language-reference/keywords/switch/when-clause.cs#1)]

Unutmayın `when` yan tümcesinde test dener örnek olup olmadığını bir `Shape` nesnedir `null` yürütülmez. Test etmek için doğru türde deseni bir `null` olduğu `case null:`.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [switch deyimi](~/_csharplang/spec/statements.md#the-switch-statement) içinde [C# dil belirtimi](../language-specification/index.md). Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [if-else](if-else.md)
- [Desen Eşleştirme](../../pattern-matching.md)
