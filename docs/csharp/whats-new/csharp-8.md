---
title: İçindeki yenilikler C# 8.0 - C# Kılavuzu
description: Uygulamasında kullanılabilen yeni özellikleri genel bakış C# 8.0. Bu makalede, preview 5 ile güncel durumda.
ms.date: 02/12/2019
ms.openlocfilehash: 962829b68c5d02c3a7e563a00d391c4698024d47
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67397766"
---
# <a name="whats-new-in-c-80"></a>İçindeki yenilikler C# 8.0

İçin birçok geliştirme vardır C# zaten deneyebileceğiniz dili. 

- [Salt okunur üyeler](#readonly-members)
- [Varsayılan arabirim üyeleri](#default-interface-members)
- [Desen eşleştirme geliştirmeleri](#more-patterns-in-more-places):
  * [Anahtar ifadeler](#switch-expressions)
  * [Özellik desenleri](#property-patterns)
  * [Kayıt düzenleri](#tuple-patterns)
  * [Konumsal desenleri](#positional-patterns)
- [Bildirimi kullanarak](#using-declarations)
- [Statik yerel işlevler](#static-local-functions)
- [Atılabilir başvuru yapı birimleri](#disposable-ref-structs)
- [Boş değer atanabilir başvuru türleri](#nullable-reference-types)
- [Zaman uyumsuz akışlar](#asynchronous-streams)
- [Dizinleri ve aralıkları](#indices-and-ranges)

> [!NOTE]
> Bu makale için en son güncelleştirildiği C# 8.0 Önizleme 5.

Bu makalenin geri kalanında bu özelliklere kısaca açıklanmaktadır. Ayrıntılı makaleleri kullanılabiliyorsa, bu öğreticileri ve genel bakışlar bağlantılar verilmiştir. Bu özellikleri kullanarak ortamınıza keşfedebilirsiniz `dotnet try` genel aracı:

1. Yükleme [dotnet deneyin](https://github.com/dotnet/try/blob/master/README.md#setup) genel aracı.
1. Kopya [dotnet/try-samples](https://github.com/dotnet/try-samples) depo.
1. Geçerli dizin kümesine *csharp8* alt *deneyin-samples* depo.
1. `dotnet try`'i çalıştırın.

## <a name="readonly-members"></a>Salt okunur üyeler

Uygulayabileceğiniz `readonly` değiştiricisi bir yapının herhangi bir üyesi. Üyenin durumu değiştirmez gösterir. Uygulama daha fazla ayrıntılı `readonly` değiştiriciyi bir `struct` bildirimi.  Aşağıdaki değişebilir yapısı göz önünde bulundurun:

```csharp
public struct Point
{
    public double X { get; set; }
    public double Y { get; set; }
    public double Distance => Math.Sqrt(X * X + Y * Y);

    public override string ToString() =>
        $"({X}, {Y}) is {Distance} from the origin";
}
```

Çoğu yapılar gibi `ToString()` yöntemi durumu değiştirmez. Ekleyerek olduğunu gösterebilecek `readonly` değiştiricisi bildirimine `ToString()`:

```csharp
public readonly override string ToString() =>
    $"({X}, {Y}) is {Distance} from the origin";
```

Yukarıdaki değişikliği bir derleyici uyarısı oluşturur çünkü `ToString` erişen `Distance` işaret konulmadıysa özelliği `readonly`:

```console
warning CS8656: Call to non-readonly member 'Point.Distance.get' from a 'readonly' member results in an implicit copy of 'this'
```

Savunma kopyası oluşturmak gerektiğinde derleyici sizi uyarır.  `Distance` Özelliği ekleyerek bu uyarıyı giderebilmemiz durumunu değiştirmez `readonly` bildirimine değiştiricisi:

```csharp
public readonly double Distance => Math.Sqrt(X * X + Y * Y);
```

Dikkat `readonly` değiştiricisi salt okunur bir özellik gereklidir. Derleyici varsayılmaz `get` bildirmeniz gerekir; erişimcileri durumu değiştirmeyin `readonly` açıkça. Derleyici kuralını uygulamak, `readonly` üyeleri durumu değiştirmeyin. Kaldırdığınız sürece aşağıdaki yöntemi derlemeyecektir `readonly` değiştiricisi:

```csharp
public readonly void Translate(int xOffset, int yOffset)
{
    X += xOffset;
    Y += yOffset;
}
```

Bu özellik, derleyici onu zorla ve en iyi duruma getirme, amacına olun tasarım amacınızla belirtmenizi sağlar.

## <a name="default-interface-members"></a>Varsayılan arabirim üyeleri

Artık üyeleri arabirimler ve bu üyeler için bir uygulama sağlayın. Bu dil özelliği kaynak ya da o arabirimin mevcut uygulamaları ile ikili uyumluluk bozup olmadan yöntemleri sonraki sürümlerinde bir arabirim eklemek API yazarlar sağlar. Mevcut uygulamaları *devral* varsayılan uygulaması. Bu özellik ayrıca sağlar C# hedef Android API'leri veya benzer özellikleri destekleyen Swift ile çalışmak için. Varsayılan arabirim üyeleri, ayrıca bir "Nitelikler" dil özelliğe benzer senaryolara olanak tanır.

Varsayılan arabirim üyeleri birçok senaryoları ve Dil öğelerini etkiler. İlk öğreticimize kapsayan [bir arabirimi varsayılan uygulamaları ile güncelleştiriliyor](../tutorials/default-interface-members-versions.md). Diğer öğreticiler ve başvuru güncelleştirmeleri genel yayın süreliğine geliyor.

## <a name="more-patterns-in-more-places"></a>Daha fazla yerde daha fazla desenleri

**Desen eşleştirme** ilgili ancak farklı türde veriler arasında şekil bağlı işlevler sağlamak için Araçlar verir. C#7.0 sunulan tür kalıpları ve sabit desenler sözdizimi kullanarak [ `is` ](../language-reference/keywords/is.md) ifade ve [ `switch` ](../language-reference/keywords/switch.md) deyimi. Bu özellikler veri ve işlevsellik burada parçalayın Canlı programlama paradigmalarını destekleme doğru ilk belirsiz adımları temsil edilir. Daha fazla mikro Hizmetleri ve diğer bulut tabanlı mimariler doğru sektör hareket ettikçe diğer dil araçları gereklidir.

C#Daha fazla yerde daha fazla desen ifade kodunuzda kullanabilmeniz için bu sözlük 8.0 genişletir. Veri ve işlevsellik ayrı olduğunda bu özellikleri göz önünde bulundurun. Bir nesnenin çalışma zamanı türü dışında bir olgu algoritmalarınızı bağımlı olduğunda desen eşleştirme göz önünde bulundurun. Bu teknikler tasarımları ifade etmek için başka bir yol sağlar.

Yeni yerde yeni desenler yanı sıra C# 8.0 ekler **özyinelemeli desenleri**. Bir ifade deseni herhangi bir ifade sonucudur. Yalnızca başka bir desen ifadesi çıkışına uygulanan bir desen ifadesi özyinelemeli modelidir.

### <a name="switch-expressions"></a>Anahtar ifadeler

Genellikle, bir [ `switch` ](../language-reference/keywords/switch.md) deyimi, her bir değer oluşturuyor, `case` engeller. **Anahtar ifadeler** , daha kısa ifade sözdizimini kullanacak şekilde etkinleştirin. Vardır daha az tekrarlı `case` ve `break` anahtar sözcükleri ve daha az küme ayraçları.  Örneğin, rainbow renklerini listeleyen aşağıdaki enum göz önünde bulundurun:

```csharp
public enum Rainbow
{
    Red,
    Orange,
    Yellow,
    Green,
    Blue,
    Indigo,
    Violet
}
```

Uygulama tanımlı değilse bir `RGBColor` nesnesinden oluşturulan türü `R`, `G` ve `B` bileşenleri dönüştürme bir `Rainbow` switch ifadesi içeren aşağıdaki yöntemi kullanarak kendi RGB değerleri için değer:

```csharp
public static RGBColor FromRainbow(Rainbow colorBand) =>
    colorBand switch
    {
        Rainbow.Red    => new RGBColor(0xFF, 0x00, 0x00),
        Rainbow.Orange => new RGBColor(0xFF, 0x7F, 0x00),
        Rainbow.Yellow => new RGBColor(0xFF, 0xFF, 0x00),
        Rainbow.Green  => new RGBColor(0x00, 0xFF, 0x00),
        Rainbow.Blue   => new RGBColor(0x00, 0x00, 0xFF),
        Rainbow.Indigo => new RGBColor(0x4B, 0x00, 0x82),
        Rainbow.Violet => new RGBColor(0x94, 0x00, 0xD3),
        _              => throw new ArgumentException(message: "invalid enum value", paramName: nameof(colorBand)),
    };
```

Burada birkaç söz dizimi geliştirmeleri vardır:

- Değişken önce gelen `switch` anahtar sözcüğü. Farklı sıra switch ifadesi switch deyiminden ayırt görsel olarak kolay hale getirir.
- `case` Ve `:` öğeleri yerine `=>`. Bu daha kısa ve kolay anlaşılır olur.
- `default` Çalışması ile değiştirildiği bir `_` atın.
- Gövdeleri, değil deyimleri ifadelerdir.

Klasik kullanarak eşdeğer kodla, Karşıtlık `switch` deyimi:

```csharp
public static RGBColor FromRainbowClassic(Rainbow colorBand)
{
    switch (colorBand)
    {
        case Rainbow.Red:
            return new RGBColor(0xFF, 0x00, 0x00);
        case Rainbow.Orange:
            return new RGBColor(0xFF, 0x7F, 0x00);
        case Rainbow.Yellow:
            return new RGBColor(0xFF, 0xFF, 0x00);
        case Rainbow.Green:
            return new RGBColor(0x00, 0xFF, 0x00);
        case Rainbow.Blue:
            return new RGBColor(0x00, 0x00, 0xFF);
        case Rainbow.Indigo:
            return new RGBColor(0x4B, 0x00, 0x82);
        case Rainbow.Violet:
            return new RGBColor(0x94, 0x00, 0xD3);
        default:
            throw new ArgumentException(message: "invalid enum value", paramName: nameof(colorBand));
    };
}
```

### <a name="property-patterns"></a>Özellik desenleri

**Özelliği desenini** incelenirken nesnenin özellikleri eşleştirilecek sağlar. Alıcının adresine göre vergi hesaplamanız gerekir bir e-ticaret sitesi göz önünde bulundurun. Hesaplama çekirdeği sorumluluğunda değil bir `Address` sınıfı. Zamanla, büyük olasılıkla adresi biçim değişikliklerini daha sık değişir. Vergi tutarı bağımlı `State` adresinin özelliği. Aşağıdaki yöntem özelliği desenini vergi adresi ve fiyat hesaplamak için kullanır:

```csharp
public static decimal ComputeSalesTax(Address location, decimal salePrice) =>
    location switch
    {
        { State: "WA" } => salePrice * 0.06M,
        { State: "MN" } => salePrice * 0.75M,
        { State: "MI" } => salePrice * 0.05M,
        // other cases removed for brevity...
        _ => 0M
    };
```

Desen eşleştirme bu algoritma ifade etmek için kısa bir söz dizimi oluşturur.

### <a name="tuple-patterns"></a>Kayıt düzenleri

Birden çok girişler bazı algoritmalar bağlıdır. **Kayıt düzenleri** olarak ifade edilen birden çok değerlere göre geçiş yapmanıza izin bir [demet](../tuples.md).  Aşağıdaki kod oyun için bir switch ifadesi gösterir *rock, inceleme, Makas*:

```csharp
public static string RockPaperScissors(string first, string second)
    => (first, second) switch
    {
        ("rock", "paper") => "rock is covered by paper. Paper wins.",
        ("rock", "scissors") => "rock breaks scissors. Rock wins.",
        ("paper", "rock") => "paper covers rock. Paper wins.",
        ("paper", "scissors") => "paper is cut by scissors. Scissors wins.",
        ("scissors", "rock") => "scissors is broken by rock. Rock wins.",
        ("scissors", "paper") => "scissors cuts paper. Scissors wins.",
        (_, _) => "tie"
    };
```

Birinci iletileri gösterir. Atma durum TIES veya diğer metin girişi için üç birleşimleri temsil eder.

### <a name="positional-patterns"></a>Konumsal desenleri

Bazı türler bir `Deconstruct` özelliklerini ayrık değişkenlere deconstructs yöntemi. Olduğunda bir `Deconstruct` yöntemi erişilebilir, kullanabileceğiniz **konumsal desenleri** nesnenin özelliklerini inceleyin ve bu özellikler için bir düzen kullanın.  Aşağıdakileri göz önünde bulundurun `Point` içeren sınıf bir `Deconstruct` ayrık değişkenleri yöntemini `X` ve `Y`:

```csharp
public class Point
{
    public int X { get; }
    public int Y { get; }

    public Point(int x, int y) => (X, Y) = (x, y);

    public void Deconstruct(out int x, out int y) =>
        (x, y) = (X, Y);
}
```

Ayrıca, bir Çeyreğin çeşitli konumlarını temsil eden aşağıdaki enum göz önünde bulundurun:

```csharp
public enum Quadrant
{
    Unknown,
    Origin,
    One,
    Two,
    Three,
    Four,
    OnBorder
}
```

Aşağıdaki yöntemi kullanan **konumsal deseni** değerlerini ayıklamak için `x` ve `y`. Ardından, kullanan bir `when` belirlemek için yan tümcesi `Quadrant` noktasının:

```csharp
static Quadrant GetQuadrant(Point point) => point switch
{
    (0, 0) => Quadrant.Origin,
    var (x, y) when x > 0 && y > 0 => Quadrant.One,
    var (x, y) when x < 0 && y > 0 => Quadrant.Two,
    var (x, y) when x < 0 && y < 0 => Quadrant.Three,
    var (x, y) when x > 0 && y < 0 => Quadrant.Four,
    var (_, _) => Quadrant.OnBorder,
    _ => Quadrant.Unknown
};
```

Eşleşen atma deseni önceki anahtarda ya da `x` veya `y` 0, ancak ikisine birden değil. Bir switch ifadesi bir değer üreten veya bir özel durum. Servis taleplerini hiçbiri eşleşen switch ifadesi bir özel durum oluşturur. Tüm olası durumların anahtar İfadenizde kapsamaz varsa derleyici bir uyarı oluşturur.

Bu teknikler desen keşfedebilirsiniz [desen eşleştirme Gelişmiş öğretici](../tutorials/pattern-matching.md).

## <a name="using-declarations"></a>Bildirimi kullanarak

A **using bildirimi** bir Değişken bildiriminde öncesinde `using` anahtar sözcüğü. Bu, derleyiciye bildirilen değişkenin kapsayan kapsamı sona atılmalıdır bildirir. Örneğin, bir metin dosyasına yazan aşağıdaki kodu düşünün:

```csharp
static void WriteLinesToFile(IEnumerable<string> lines)
{
    using var file = new System.IO.StreamWriter("WriteLines2.txt");
    foreach (string line in lines)
    {
        // If the line doesn't contain the word 'Second', write the line to the file.
        if (!line.Contains("Second"))
        {
            file.WriteLine(line);
        }
    }
// file is disposed here
}
```

Önceki örnekte, yöntemi için kapanış ayracı ulaşıldığında Dosya atıldı. Kapsamda sonuna olan `file` bildirilir. Yukarıdaki kod, Klasik kullanarak aşağıdaki koda eşdeğerdir [using deyimlerini](../language-reference/keywords/using-statement.md) deyimi:

```csharp
static void WriteLinesToFile(IEnumerable<string> lines)
{
    using (var file = new System.IO.StreamWriter("WriteLines2.txt"))
    {
        foreach (string line in lines)
        {
            // If the line doesn't contain the word 'Second', write the line to the file.
            if (!line.Contains("Second"))
            {
                file.WriteLine(line);
            }
        }
    } // file is disposed here
}
```

Kapanış küme ayracı ile ilişkili olduğunda önceki örnekte, dosyanın elden `using` deyimine ulaşıldığında.

Her iki durumda da, derleyici çağrısı oluşturur `Dispose()`. Derleyici bir hata oluşturur kullanarak ifade deyimi atılabilir değil.

## <a name="static-local-functions"></a>Statik yerel işlevler

Artık ekleyebilirsiniz `static` değiştiricisi yerel bu işlevi sağlamak için yerel işlevler için değil (başvuru) yakalama kapsayan kapsamdan gelen tüm değişkenler. Bunun yapılması oluşturur `CS8421`, "statik bir yerel işleve başvuru içeremez \<değişken >." 

Aşağıdaki kodu düşünün. Yerel işlev `LocalFunction` değişkeni erişen `y`kapsayan kapsamda bildirilen (yöntemi `M`). Bu nedenle, `LocalFunction` ile bildirilemez `static` değiştiricisi:

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

Aşağıdaki kod, statik bir yerel işlev içerir. Tüm kapsayan kapsamda değişkenlere erişim yoktur çünkü statik olabilir:

```csharp
int M()
{
    int y = 5;
    int x = 7;
    return Add(x, y);

    static int Add(int left, int right) => left + right;
}
```

## <a name="disposable-ref-structs"></a>Atılabilir başvuru yapı birimleri

A `struct` ile bildirilen `ref` değiştiricisi hiçbir arabirim uygulayamaz ve bu nedenle uygulayamaz <xref:System.IDisposable>. Bu nedenle, etkinleştirmek için bir `ref struct` çıkarılması için bunu bir erişilebilir olmalıdır `void Dispose()` yöntemi. Bu durum için de geçerlidir `readonly ref struct` bildirimleri.

## <a name="nullable-reference-types"></a>Boş değer atanabilir başvuru türleri

Boş değer atanabilir bir ek açıklama bir bağlam içinde bir başvuru türünün herhangi bir değişken olarak kabul edilir bir **nonnullable başvuru türü**. Bir değişken null olabilir belirtmek istiyorsanız, tür adıyla ekleme `?` değişken olarak bildirmek için bir **boş değer atanabilir bir başvuru türü**.

Nonnullable başvuru türleri için derleyici yerel değişkenler bir null olmayan değer bildirildiğinde başlatılır emin olmak için akış analizini kullanır. Oluşturma sırasında alanları yeniden başlatılması gerekir. Değişkeni bir başlatıcıya veya kullanılabilir oluşturucular herhangi bir çağrı tarafından ayarlanmamışsa, derleyici bir uyarı oluşturur. Ayrıca, nonnullable başvuru türleri null olabilir bir değer atanamaz.

Null başvuru türlerine atanan olmayan veya null'a emin olmak için denetlenmez. Ancak derleyici, erişilen veya nonnullable başvuru türüne atanan önce herhangi bir değişken bir boş değer atanabilir bir başvuru türünün null karşı seçeneğinin işaretli olduğundan emin olmak için akış analizini kullanır.

Genel Bakış özelliği hakkında daha fazla bilgi [null başvuru türleri](../nullable-references.md). Bu yeni bir uygulamada kendiniz denemek [null başvuru türleri öğretici](../tutorials/nullable-reference-types.md). Hakkında bilgi edinin yapmak için var olan bir geçiş adımlarını codebase null başvuru türlerinde kullanımı [öğretici türleri null yapılabilir başvurusu kullanmak için bir uygulamayı geçirme](../tutorials/upgrade-to-nullable-references.md).

## <a name="asynchronous-streams"></a>Zaman uyumsuz akışlar

İle başlayarak C# 8.0, oluşturabilir ve akışları zaman uyumsuz olarak kullanır. Zaman uyumsuz bir akışa döndüren bir yöntem üç özelliğe sahiptir:

1. İle bildirilen `async` değiştiricisi.
1. Döndürür bir <xref:System.Collections.Generic.IAsyncEnumerable%601>.
1. Contains yöntemi `yield return` deyimleri zaman uyumsuz akışın ardışık öğeleri döndürmek için.

Zaman uyumsuz bir akışa kullanma, gerektirir eklemeyi `await` anahtar sözcüğünün önüne `foreach` akış öğelerini numaralandırıldığında anahtar sözcüğü. Ekleme `await` anahtar sözcüğü ile bildirilen zaman uyumsuz akış numaralandırır yöntemi gerektiren `async` değiştiricisi ve bir tür için izin verilecek bir `async` yöntemi. Genellikle döndüren anlamına bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601>. Ayrıca olabilir bir <xref:System.Threading.Tasks.ValueTask> veya <xref:System.Threading.Tasks.ValueTask%601>. Bir yöntem hem kullanabilir ve şunu döndürür anlamına gelir zaman uyumsuz bir akışa üreten bir <xref:System.Collections.Generic.IAsyncEnumerable%601>. Aşağıdaki kod, her bir sayının oluşturma arasında 100 ms bekleniyor 19 için 0'dan bir sıra üretir:

```csharp
public static async System.Collections.Generic.IAsyncEnumerable<int> GenerateSequence()
{
    for (int i = 0; i < 20; i++)
    {
        await Task.Delay(100);
        yield return i;
    }
}
```

Dizisi kullanarak listeleme `await foreach` deyimi:

```csharp
await foreach (var number in GenerateSequence())
{
    Console.WriteLine(number);
}
```

Zaman uyumsuz akışlar kendiniz müşterilerimize öğreticide deneyebilirsiniz [oluşturma ve zaman uyumsuz akışlar tüketen](../tutorials/generate-consume-asynchronous-stream.md).

## <a name="indices-and-ranges"></a>Dizinleri ve aralıkları

Aralıkları ve dizinlerini sağlayan bir kısa sözdizimleri bir dizi içinde alt aralıklara belirtmek için <xref:System.Span%601>, veya <xref:System.ReadOnlySpan%601>.

Bu dil desteği, iki yeni türler ve iki yeni işleç kullanır.
- <xref:System.Index?displayProperty=nameWithType> Dizin bir dizisi temsil eder.
- `^` İşleci bir dizin sonuna göreli olduğunu belirtir.
- <xref:System.Range?displayProperty=nameWithType> bir dizi alt aralığını temsil eder.
- Aralık işleci (`..`) başlangıç belirtir ve bir aralığın işlenen olduğu.

Dizinler için kuralları başlayalım. Bir dizi göz önünde bulundurun `sequence`. `0` Dizin aynıdır `sequence[0]`. `^0` Dizin aynıdır `sequence[sequence.Length]`. Unutmayın `sequence[^0]` gibi bir özel durum `sequence[sequence.Length]` yapar. Herhangi bir sayı için `n`, dizin `^n` aynı `sequence.Length - n`.

Bir aralığı belirtir *Başlat* ve *son* aralığının. Aralığın başlangıcını dahil, ancak aralığın özel anlamı *Başlat* aralığa dahil olan ancak *son* aralığında yer almaz. Aralığın `[0..^0]` gibi tüm aralığını temsil eden `[0..sequence.Length]` tüm aralığını temsil eder. 

Bazı örneklere bakalım. Aşağıdaki dizinin başından ve sonundan dizinini ile açıklanan göz önünde bulundurun:

```csharp
var words = new string[]
{
                // index from start    index from end
    "The",      // 0                   ^9
    "quick",    // 1                   ^8
    "brown",    // 2                   ^7
    "fox",      // 3                   ^6
    "jumped",   // 4                   ^5
    "over",     // 5                   ^4
    "the",      // 6                   ^3
    "lazy",     // 7                   ^2
    "dog"       // 8                   ^1
};              // 9 (or words.Length) ^0
```

Son sözcüğü alabilirsiniz `^1` dizini:

```csharp
Console.WriteLine($"The last word is {words[^1]}");
// writes "dog"
```

Aşağıdaki kod, bir alt aralığı sözcükler "Hızlı", "brown" ile ve "fox" oluşturur. İçerdiği `words[1]` aracılığıyla `words[3]`. Öğe `words[4]` aralığında değil.

```csharp
var quickBrownFox = words[1..4];
```

Aşağıdaki kod, "geç" ve "köpek" alt oluşturur. İçerdiği `words[^2]` ve `words[^1]`. Bitiş dizini `words[^0]` dahil edilmez:

```csharp
var lazyDog = words[^2..^0];
```

Aşağıdaki örnekler, açık olan başında, sonunda ya da her ikisi için bitiş aralıkları oluşturur:

```csharp
var allWords = words[..]; // contains "The" through "dog".
var firstPhrase = words[..4]; // contains "The" through "fox"
var lastPhrase = words[6..]; // contains "the", "lazy" and "dog"
```

De aralık değişkenleri olarak bildirebilirsiniz:

```csharp
Range phrase = 1..4;
```

Aralık içinde sonra kullanılabilir `[` ve `]` karakter:

```csharp
var text = words[phrase];
```

Üzerinde öğreticide dizinleri ve aralıkları hakkında daha fazla keşfedebilirsiniz [dizinleri ve aralıkları](../tutorials/ranges-indexes.md).
