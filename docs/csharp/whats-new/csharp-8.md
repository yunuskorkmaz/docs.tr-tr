---
title: C# 8,0 C# kılavuzundaki yenilikler
description: 8,0 ' de C# bulunan yeni özelliklere genel bakış alın.
ms.date: 09/20/2019
ms.openlocfilehash: 95331c8dd8e8b5e0d5af242752565d8e93120937
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216484"
---
# <a name="whats-new-in-c-80"></a>C# 8,0 sürümündeki yenilikler

C#8,0 aşağıdaki özellikleri ve geliştirmeleri C# dile ekler:

- [Salt okunur Üyeler](#readonly-members)
- [Varsayılan arabirim üyeleri](#default-interface-members)
- [Desenler eşleşen geliştirmeler](#more-patterns-in-more-places):
  - [Anahtar ifadeleri](#switch-expressions)
  - [Özellik desenleri](#property-patterns)
  - [Demet desenleri](#tuple-patterns)
  - [Konumsal desenler](#positional-patterns)
- [Bildirimleri kullanma](#using-declarations)
- [Statik yerel işlevler](#static-local-functions)
- [Atılabilir ref yapıları](#disposable-ref-structs)
- [Boş değer atanabilir başvuru türleri](#nullable-reference-types)
- [Zaman uyumsuz akışlar](#asynchronous-streams)
- [Dizinler ve aralıklar](#indices-and-ranges)
- [Null birleştirme ataması](#null-coalescing-assignment)
- [Yönetilmeyen oluşturulmuş türler](#unmanaged-constructed-types)
- [iç içe ifadelerde stackalloc](#stackalloc-in-nested-expressions)
- [Ara değerli tam dizelerin geliştirilmesi](#enhancement-of-interpolated-verbatim-strings)

Bu makalenin geri kalanında bu özellikler kısaca açıklanmaktadır. Ayrıntılı makalelerin nerede kullanılabildiği, bu öğreticiler ve genel bakışların bağlantıları sağlanmıştır. `dotnet try` Genel aracı kullanarak ortamınızdaki bu özellikleri keşfedebilirsiniz:

1. [DotNet-TRY](https://github.com/dotnet/try/blob/master/README.md#setup) küresel aracını yükler.
1. [DotNet/TRY-Samples](https://github.com/dotnet/try-samples) deposunu kopyalayın.
1. *TRY-Samples* deposu için geçerli dizini *csharp8* alt dizinine ayarlayın.
1. `dotnet try`'i çalıştırın.

## <a name="readonly-members"></a>Salt okunur Üyeler

`readonly` Değiştiricisini bir yapının herhangi bir üyesine uygulayabilirsiniz. Üyenin durumu değiştirmediğini belirtir. Bu, `readonly` değiştiricinin bir bildirime uygulanmasıyla daha ayrıntılı bir `struct` hale gelir.  Aşağıdaki kesilebilir yapıyı göz önünde bulundurun:

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

Çoğu yapı gibi, `ToString()` yöntemi durumunu değiştirmez. `readonly` Şu`ToString()`bildirime değiştiricisini ekleyerek belirtebilirsiniz:

```csharp
public readonly override string ToString() =>
    $"({X}, {Y}) is {Distance} from the origin";
```

Önceki değişiklik bir derleyici uyarısı oluşturur, çünkü `ToString` bu, işaretlenmeyen `Distance` `readonly`özelliğe erişir:

```console
warning CS8656: Call to non-readonly member 'Point.Distance.get' from a 'readonly' member results in an implicit copy of 'this'
```

Derleyici, savunma kopyası oluşturması gerektiğinde sizi uyarır.  Özelliği durumu değiştirmez, bu nedenle, bildirime `readonly` değiştiricisini ekleyerek bu uyarıyı giderebilirsiniz: `Distance`

```csharp
public readonly double Distance => Math.Sqrt(X * X + Y * Y);
```

`readonly` Değiştiricinin salt okuma özelliğinde gerekli olduğuna dikkat edin. Derleyici erişimcileri durumu değiştirmez `get` olarak kabul etmez; açıkça bildirmeniz `readonly` gerekir. Derleyici, `readonly` üyelerin durumu değiştirmediğinden kuralı zorunlu tutar. `readonly` Değiştirici kaldırmadığınız takdirde aşağıdaki yöntem derlenmeyecektir:

```csharp
public readonly void Translate(int xOffset, int yOffset)
{
    X += xOffset;
    Y += yOffset;
}
```

Bu özellik, tasarım amacınızı derleyicinin uygulamayı zorunlu kılabilir ve bu amaca göre iyileştirmeler yapabilmesini sağlar.

## <a name="default-interface-members"></a>Varsayılan arabirim üyeleri

Artık, arabirimlere Üyeler ekleyebilir ve bu üyeler için bir uygulama sağlayabilirsiniz. Bu dil özelliği, API yazarlarının, bu arabirimin var olan uygulamalarıyla kaynak veya ikili uyumluluğu bozmadan sonraki sürümlerde bir arabirime Yöntemler eklemesine olanak sağlar. Mevcut uygulamalar varsayılan uygulamayı *devralınır* . Bu özellik aynı zamanda C# , benzer özellikleri destekleyen Android veya Swift 'Ları hedefleyen API 'Lerle birlikte çalışmaya de olanak sağlar. Varsayılan arabirim üyeleri, "nitelikler" dil özelliğine benzer senaryolara de olanak tanır.

Varsayılan arabirim üyeleri birçok senaryoyu ve dil öğelerini etkiler. İlk öğreticimiz [, bir arabirimin varsayılan uygulamalarla güncelleştirilmesini](../tutorials/default-interface-members-versions.md)kapsamaktadır. Diğer öğreticiler ve başvuru güncelleştirmeleri genel sürüm için zaman içinde geliyor.

## <a name="more-patterns-in-more-places"></a>Daha fazla yerde daha fazla desen

**Model eşleştirme** , ilişkili ancak farklı veri türleri arasında şekle bağımlı işlevsellik sağlamaya yönelik araçlar sağlar. C#7,0, [`is`](../language-reference/keywords/is.md) ifade [`switch`](../language-reference/keywords/switch.md) ve deyimi kullanılarak tür desenleri ve sabit desenler için sözdizimi sunmuştur. Bu özellikler, verileri ve işlevselliği birbirinden canlı olarak programlama paradigmalarına desteklemeye yönelik ilk belirsiz adımları temsil eder. Sektör daha fazla mikro hizmete ve diğer bulut tabanlı mimarilere doğru hareket ederken diğer dil araçları gerekir.

C#8,0, kodunuzda daha fazla yerde daha fazla model ifadesi kullanabilmeniz için bu sözlüğü genişletir. Verileriniz ve işlevselliklerinizin ayrı olması durumunda bu özellikleri göz önünde bulundurun. Algoritmalarınız nesnenin çalışma zamanı türü dışında bir olgusuna bağımlıysa, model eşleştirmeyi düşünün. Bu teknikler, hızlı tasarımlar için başka bir yol sağlar.

Yeni yerlerdeki yeni desenlere ek olarak C# 8,0 **özyinelemeli desenler**ekler. Herhangi bir model ifadesinin sonucu bir ifadedir. Özyinelemeli bir model, sadece başka bir model ifadesinin çıktısına uygulanan bir model ifadesi olur.

### <a name="switch-expressions"></a>anahtar ifadeleri

Genellikle, bir [`switch`](../language-reference/keywords/switch.md) ifade `case` blokların her birinde bir değer üretir. **Anahtar ifadeleri** , daha kısa ifade sözdizimi kullanmanıza olanak sağlar. Daha az yinelenen `case` ve `break` anahtar sözcük ve daha az küme ayraçları vardır.  Örnek olarak, gökkuşağı renklerini listeleyen aşağıdaki sabit listesini göz önünde bulundurun:

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

Uygulamanız; `R`, `G` ve `B` bileşenlerinden oluşturulmuş bir `RGBColor` türü tanımladıysa bir `Rainbow` değerini, switch ifadesi içeren aşağıdaki yöntemi kullanarak RGB değerlerine dönüştürebilirsiniz:

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

Burada birkaç sözdizimi geliştirmesi vardır:

- Değişkeni, `switch` anahtar sözcüğünden önce gelir. Farklı sıra, switch ifadesinin Switch deyiminin ayırt edilmesini görsel açıdan kolaylaştırır.
- `case` Ve öğeleri`:` ile`=>`değiştirilmiştir. Daha kısa ve sezgisel.
- Durum `default` , bir `_` atma ile değiştirilmiştir.
- Gövdeler deyimlerdir, deyimler değildir.

Klasik `switch` deyimin kullanıldığı denk kodla kontrast:

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

**Özellik deseninin** incelenen nesnenin özellikleriyle eşleştirmenize olanak sağlar. Alıcının adresine göre satış vergisini hesaplamak zorunda olan bir eCommerce sitesini düşünün. Bu hesaplama, bir `Address` sınıfın temel sorumluluğu değildir. Büyük olasılıkla, adres biçimi değişikliklerinden daha fazla sıklıkta değişecektir. Satış vergisi miktarı adresin `State` özelliğine bağlıdır. Aşağıdaki yöntem, adresten ve fiyattan satış vergisini hesaplamak için özellik modelini kullanır:

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

Model eşleştirme, bu algoritmayı ifade etmek için kısa bir sözdizimi oluşturur.

### <a name="tuple-patterns"></a>Demet desenleri

Bazı algoritmalar birden fazla girişe bağımlıdır. **Demet desenleri** , [kayıt düzeni](../tuples.md)olarak ifade edilen birden çok değere göre geçiş yapmanıza olanak sağlar.  Aşağıdaki kod, oyun *rock, Paper, makas*için bir switch ifadesi gösterir:

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

İletiler kazanan kişiyi gösterir. Atma durumu, TIES veya diğer metin girişleri için üç birleşimi temsil eder.

### <a name="positional-patterns"></a>Konumsal desenler

Bazı türler, özelliklerini `Deconstruct` ayrı değişkenlere oluşturan bir yöntemi içerir. Bir `Deconstruct` Yöntem erişilebilir olduğunda, nesnenin özelliklerini incelemek ve bu özellikleri bir desen için kullanmak üzere **konumsal desenleri** kullanabilirsiniz.  `Point` `Deconstruct` Ve için`X`ayrık değişkenler oluşturmak üzere bir yöntemi içeren aşağıdaki sınıfı göz önünde bulundurun: `Y`

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

Ayrıca, bir Çeyrekli konumların çeşitli konumlarını temsil eden aşağıdaki sabit listesini göz önünde bulundurun:

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

Aşağıdaki yöntem, `x` ve `y`değerlerini ayıklamak için **konumsal model** kullanır. Sonra, noktanın `Quadrant` konumunu tespit `when` etmek için bir yan tümce kullanır:

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

Önceki anahtardaki atma deseninin ya `x` `y` da 0 olduğunda eşleşir ancak ikisi birden değildir. Switch ifadesinin bir değer üretmesi veya bir özel durum oluşturması gerekir. Durumlardan hiçbiri eşleşmezse, switch ifadesi bir özel durum oluşturur. Anahtar ifadenizde olası tüm durumları kapsamıyordıysanız, derleyici sizin için bir uyarı oluşturur.

Bu [Gelişmiş öğreticide, model eşleştirme](../tutorials/pattern-matching.md)tekniklerini inceleyebilirsiniz.

## <a name="using-declarations"></a>bildirimleri kullanma

**Using bildirimi** , `using` anahtar sözcüğünün önünde yer aldığı bir değişken bildirimidir. Derleyiciye, bildirildiği değişkenin kapsayan kapsamın sonunda atılmasını söyler. Örneğin, bir metin dosyası yazan aşağıdaki kodu göz önünde bulundurun:

```csharp
static void WriteLinesToFile(IEnumerable<string> lines)
{
    using var file = new System.IO.StreamWriter("WriteLines2.txt");
    foreach (string line in lines)
    {
        if (!line.Contains("Second"))
        {
            file.WriteLine(line);
        }
    }
// file is disposed here
}
```

Yukarıdaki örnekte, yöntemi için kapanış ayracı ne zaman ulaşıldığında dosya atıldı. İçinde `file` bildirildiği kapsamın sonu. Yukarıdaki kod, klasik [using ifadesini](../language-reference/keywords/using-statement.md)kullanan aşağıdaki koda eşdeğerdir:

```csharp
static void WriteLinesToFile(IEnumerable<string> lines)
{
    using (var file = new System.IO.StreamWriter("WriteLines2.txt"))
    {
        foreach (string line in lines)
        {
            if (!line.Contains("Second"))
            {
                file.WriteLine(line);
            }
        }
    } // file is disposed here
}
```

Önceki örnekte, `using` ifadesiyle ilişkilendirilen kapanış ayracı aşıldığında dosya atıldı.

Her iki durumda da derleyici çağrısını `Dispose()`oluşturur. `using` Deyimdeki ifade atılabilir değilse, derleyici bir hata oluşturur.

## <a name="static-local-functions"></a>Statik yerel işlevler

Yerel işlevin kapsayan kapsamdaki herhangi `static` bir değişkeni yakalamamasına (başvuru) izin vermek için artık yerel işlevlere değiştiricisini ekleyebilirsiniz. Bunu yapmak \<, "statik yerel bir işlev > değişkenine bir başvuru içeremez." `CS8421` 

Aşağıdaki kodu göz önünde bulundurun. Yerel işlev `LocalFunction` , kapsayan kapsamda ( `y`yöntemi `M`) belirtilen değişkenine erişir. Bu nedenle `LocalFunction` , `static` değiştiriciyle bildirilemez:

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

Aşağıdaki kod statik bir yerel işlev içerir. Bu, kapsayan kapsamdaki herhangi bir değişkene erişemediğinden statik olabilir:

```csharp
int M()
{
    int y = 5;
    int x = 7;
    return Add(x, y);

    static int Add(int left, int right) => left + right;
}
```

## <a name="disposable-ref-structs"></a>Atılabilir ref yapıları

Değiştiriciyle birlikte tanımlanan bir `struct` arabirim uygulayamaz, bu nedenle uygulayamaz <xref:System.IDisposable>. `ref` Bu nedenle, bir `ref struct` 'nin atılbilmesini sağlamak için erişilebilir `void Dispose()` bir yöntemi olmalıdır. Bu, bildirimler için `readonly ref struct` de geçerlidir.

## <a name="nullable-reference-types"></a>Boş değer atanabilir başvuru türleri

Null olabilen bir ek açıklama bağlamında, başvuru türündeki herhangi bir değişken **null yapılamayan bir başvuru türü**olarak kabul edilir. Bir değişkenin null olabileceğini belirtmek istiyorsanız, değişkeni null olabilen bir `?` **başvuru türü**olarak bildirmek için ile tür adını eklemeniz gerekir.

Null yapılamayan başvuru türleri için derleyici, yerel değişkenlerin bildirildiği sırada null olmayan bir değere başlatıldığından emin olmak için akış analizini kullanır. Alanlar oluşturma sırasında başlatılmalıdır. Değişken, kullanılabilir oluşturuculardan herhangi birine veya bir başlatıcı tarafından ayarlanmamışsa, derleyici bir uyarı oluşturur. Ayrıca, null olamayan başvuru türlerine null olabilecek bir değer atanamaz.

Null yapılabilir başvuru türleri atanmamış veya null olarak başlatılmamış olduğundan emin olmak için denetlenmez. Ancak, derleyici, null olabilen bir başvuru türü değişkeninin erişilebilir olması veya null yapılamayan bir başvuruya atanmadan önce null olarak denetlendiğinden emin olmak için akış analizini kullanır.

Özelliği hakkında daha fazla bilgiyi [null yapılabilir başvuru türlerine](../nullable-references.md)genel bakış bölümünde bulabilirsiniz. Bu [null yapılabilir başvuru türleri öğreticisindeki](../tutorials/nullable-reference-types.md)yeni bir uygulamada kendiniz deneyin. [Bir uygulamayı, null yapılabilir başvuru türlerini kullanmak için geçirme](../tutorials/upgrade-to-nullable-references.md)bölümünde null yapılabilir başvuru türlerini kullanmak için mevcut bir kod temeli geçirme adımları hakkında bilgi edinin.

## <a name="asynchronous-streams"></a>Zaman uyumsuz akışlar

8,0 ile C# başlayarak akışları zaman uyumsuz olarak oluşturabilir ve kullanabilirsiniz. Zaman uyumsuz akış döndüren bir yöntem üç özelliğe sahiptir:

1. `async` Değiştiriciyle birlikte bildirilmiştir.
1. Döndürür <xref:System.Collections.Generic.IAsyncEnumerable%601>.
1. Yöntemi, zaman `yield return` uyumsuz akıştaki birbirini izleyen öğeleri döndürecek deyimleri içerir.

Zaman uyumsuz bir akışın kullanılması, akışın öğelerini Numaralandırdığınızda `await` `foreach` anahtar kelimeden önce anahtar sözcüğünü eklemenizi gerektirir. Anahtar sözcüğü eklemek, zaman uyumsuz akışı belirten ve `async` değiştirici ile belirtilecek ve bir `async` Yöntem için izin verilen bir tür döndürecek yöntemi gerektirir. `await` Genellikle, <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601>döndürme anlamına gelir. Ayrıca, <xref:System.Threading.Tasks.ValueTask> veya <xref:System.Threading.Tasks.ValueTask%601>olabilir. Bir yöntem, zaman uyumsuz bir akış tüketebilir ve üretebilir, yani dönecektir <xref:System.Collections.Generic.IAsyncEnumerable%601>. Aşağıdaki kod, 0 ile 19 arasında bir sıra üretir, her bir sayı üretilmeden 100 ms bekler:

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

Şu `await foreach` ifadeyi kullanarak sırayı numaralandırabilirsiniz:

```csharp
await foreach (var number in GenerateSequence())
{
    Console.WriteLine(number);
}
```

Zaman uyumsuz akışları [oluşturma ve](../tutorials/generate-consume-asynchronous-stream.md)kullanma öğreticimizde, zaman uyumsuz akışları kendiniz deneyebilirsiniz.

## <a name="indices-and-ranges"></a>Dizinler ve aralıklar

Aralıklar ve dizinler, bir dizi, [dize](../language-reference/builtin-types/reference-types.md#the-string-type), <xref:System.Span%601>veya <xref:System.ReadOnlySpan%601>alt aralıkları belirtmek için bir kısa sözdizimi sağlar.

Bu dil desteği iki yeni türe ve iki yeni işleçlere dayanır:

- <xref:System.Index?displayProperty=nameWithType>bir dizinin dizisini temsil eder.
- Bir dizinin sıranın sonuna göreli olduğunu belirten işleç.`^`
- <xref:System.Range?displayProperty=nameWithType>bir dizinin alt aralığını temsil eder.
- Aralık işleci (`..`), bir aralığın işlenenleri olarak başlangıcını ve sonunu belirtir.

Dizin kurallarıyla başlayalım. Bir dizi `sequence`düşünün. Dizin, ile `sequence[0]`aynıdır. `0` Dizin, ile `sequence[sequence.Length]`aynıdır. `^0` `sequence[^0]` Bunun gibi`sequence[sequence.Length]` bir özel durum oluşturur. Herhangi bir sayı `n`için Dizin `^n` aynı `sequence.Length - n`olur.

Aralık, bir aralığın *başlangıcını* ve *sonunu* belirtir. Aralığın başlangıcı dahil, ancak aralığın sonu dışlamalı, ancak *Başlangıç* aralığa dahil değildir ancak *bitiş* aralığa eklenmez. Aralık, tüm aralığı temsil eden tüm `[0..sequence.Length]` aralığı temsileder.`[0..^0]` 

Birkaç örneğe bakalım. Başlangıç ve bitişten dizin ile açıklana ek olarak, aşağıdaki diziyi göz önünde bulundurun:

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

Son sözcüğü `^1` şu dizine alabilirsiniz:

```csharp
Console.WriteLine($"The last word is {words[^1]}");
// writes "dog"
```

Aşağıdaki kod, "hızlı", "kahverengi" ve "Fox" sözcüklerinin bulunduğu bir alt Aralık oluşturur. `words[1]` İle`words[3]`içerir. Öğe `words[4]` Aralık içinde değil.

```csharp
var quickBrownFox = words[1..4];
```

Aşağıdaki kod, "Lazy" ve "köpek" ile bir alt Aralık oluşturur. `words[^2]` Ve`words[^1]`içerir. Son dizin `words[^0]` dahil değildir:

```csharp
var lazyDog = words[^2..^0];
```

Aşağıdaki örnekler, başlangıç, bitiş veya her ikisi için açık olarak biten aralıklar oluşturur:

```csharp
var allWords = words[..]; // contains "The" through "dog".
var firstPhrase = words[..4]; // contains "The" through "fox"
var lastPhrase = words[6..]; // contains "the", "lazy" and "dog"
```

Aralıkları, değişkenler olarak da bildirebilirsiniz:

```csharp
Range phrase = 1..4;
```

Aralık daha sonra `[` ve `]` karakterleri içinde kullanılabilir:

```csharp
var text = words[phrase];
```

Dizinler ve [aralıklar](../tutorials/ranges-indexes.md)hakkında öğreticide dizinler ve aralıklar hakkında daha fazla bilgi bulabilirsiniz.

## <a name="null-coalescing-assignment"></a>Null birleştirme ataması

C#8,0, null birleşim atama işlecini `??=`tanıtır. Sağ işleneninin değerini `??=` , sol taraftaki işlenenin değerini yalnızca sol taraftaki işlenen olarak `null`değerlendirdiğinde atamak için işlecini kullanabilirsiniz.

```csharp
List<int> numbers = null;
int? i = null;

numbers ??= new List<int>();
numbers.Add(i ??= 17);
numbers.Add(i ??= 20);

Console.WriteLine(string.Join(' ', numbers));  // output: 17 17
Console.WriteLine(i);  // output: 17
```

Daha fazla bilgi için?? [ve?? = operatörler](../language-reference/operators/null-coalescing-operator.md) makalesi.

## <a name="unmanaged-constructed-types"></a>Yönetilmeyen oluşturulmuş türler

7,3 ve önceki sürümlerde, oluşturulmuş bir tür (en az bir tür bağımsız değişkeni içeren bir tür) yönetilmeyen bir tür olamaz. [](../language-reference/builtin-types/unmanaged-types.md) C# 8,0 ile C# başlayarak, oluşturulmuş bir değer türü yalnızca yönetilmeyen türlerin alanlarını içeriyorsa yönetilmez.

Örneğin, genel `Coords<T>` türün aşağıdaki tanımı verildiğinde:

```csharp
public struct Coords<T>
{
    public T X;
    public T Y;
}
```

türü, C# 8,0 ve üzeri bir yönetilmeyen türdür. `Coords<int>` Herhangi bir yönetilmeyen tür için olduğu gibi, bu türden bir değişkene bir işaretçi oluşturabilir veya bu türün örnekleri için [yığında bir bellek bloğu ayırabilirsiniz](../language-reference/operators/stackalloc.md) :

```csharp
Span<Coords<int>> coordinates = stackalloc[]
{
    new Coords<int> { X = 0, Y = 0 },
    new Coords<int> { X = 0, Y = 3 },
    new Coords<int> { X = 4, Y = 0 }
};
```

Daha fazla bilgi için bkz. [yönetilmeyen türler](../language-reference/builtin-types/unmanaged-types.md).

## <a name="stackalloc-in-nested-expressions"></a>iç içe ifadelerde stackalloc

8,0 ile C# başlayarak, bir [stackalloc](../language-reference/operators/stackalloc.md) ifadesinin <xref:System.Span%601?displayProperty=nameWithType> sonucu veya <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> türü ise, `stackalloc` ifadeyi diğer ifadelerde kullanabilirsiniz:

```csharp
Span<int> numbers = stackalloc[] { 1, 2, 3, 4, 5, 6 };
var ind = numbers.IndexOfAny(stackalloc[] { 2, 4, 6 ,8 });
Console.WriteLine(ind);  // output: 1
```

## <a name="enhancement-of-interpolated-verbatim-strings"></a>Ara değerli tam dizelerin geliştirilmesi

`@` Birliktebulunan`$@"..."` [](../language-reference/tokens/interpolated.md) tam`@$"..."` dizelerde ve belirteçlerin sırası herhangi biri olabilir: her ikisi de geçerli bir ara tür dizelerdir. `$` Önceki C# sürümlerde, `$` belirtecin `@` belirteçten önce görünmesi gerekir.
