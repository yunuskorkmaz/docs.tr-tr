---
title: İçindeki yenilikler C# 8.0 - C# Kılavuzu
description: Uygulamasında kullanılabilen yeni özellikleri genel bakış C# 8.0. Bu makalede, preview 2'ile güncel durumda.
ms.date: 02/12/2019
ms.openlocfilehash: c04ea514c1730de8e4ceabbd6fc0e9a12fdbfb3c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57376513"
---
# <a name="whats-new-in-c-80"></a>İçindeki yenilikler C# 8.0

İçin birçok geliştirme vardır C# Önizleme 2 ile deneyebileceğiniz dili. Preview 2 sürümünde eklenen yeni özellikleri şunlardır:

- [Desen eşleştirme geliştirmeleri](#more-patterns-in-more-places):
  * [Anahtar ifadeler](#switch-expressions)
  * [Özellik desenleri](#property-patterns)
  * [Kayıt düzenleri](#tuple-patterns)
  * [Konumsal desenleri](#positional-patterns)
- [Bildirimi kullanarak](#using-declarations)
- [Statik yerel işlevler](#static-local-functions)
- [Atılabilir başvuru yapı birimleri](#disposable-ref-structs)

Aşağıdaki dil özellikleri ilk göründüğü C# 8.0 Önizleme 1:

- [Boş değer atanabilir başvuru türleri](#nullable-reference-types)
- [Zaman uyumsuz akışlar](#asynchronous-streams)
- [Dizinleri ve aralıkları](#indices-and-ranges)

> [!NOTE]
> Bu makale için en son güncelleştirildiği C# 8.0 Önizleme 2.

Bu makalenin geri kalanında bu özelliklere kısaca açıklanmaktadır. Ayrıntılı makaleleri kullanılabiliyorsa, bu öğreticileri ve genel bakışlar bağlantılar verilmiştir.

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
    Blue,
    Indigo,
    Violet
}
```

Dönüştürme bir `Rainbow` switch ifadesi içeren aşağıdaki yöntemi kullanarak kendi RGB değerleri için değer:

```csharp
public static RGBColor FromRainbow(Rainbow colorBand) =>
    colorBand switch
    {
        Rainbow.Red    => new RGBColor(0xFF, 0x00, 0x00),
        Rainbow.Orange => new RGBColor(0xFF, 0x7F, 0x00),
        Rainbow.Yellow => new RGBColor(0xFF, 0xFF, 0x00),
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
public static RGBColor fromRainbowClassic(Rainbow colorBand)
{
    switch (colorBand)
    {
        case Rainbow.Red:
            return new RGBColor(0xFF, 0x00, 0x00);
        case Rainbow.Orange:
            return new RGBColor(0xFF, 0x7F, 0x00);
        case Rainbow.Yellow:
            return new RGBColor(0xFF, 0xFF, 0x00);
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

Aşağıdaki yöntemi kullanan **konumsal deseni** değerlerini ayıklamak için `x` ve `y`. Ardından, kullanan bir `when` yan tümcesi noktasının quadrant belirlemek için:

```csharp
static string Quadrant(Point p) => p switch
{
    (0, 0) => "origin",
    (var x, var y) when x > 0 && y > 0 => "Quadrant 1",
    (var x, var y) when x < 0 && y > 0 => "Quadrant 2",
    (var x, var y) when x < 0 && y < 0 => "Quadrant 3",
    (var x, var y) when x > 0 && y < 0 => "Quadrant 4",
    (var x, var y) => "on a border",
    _ => "unknown"
};
```

Eşleşen atma deseni önceki anahtarda ya da `x` veya `y`, iki değil, 0'dır. Bir switch ifadesi bir değer üreten veya bir özel durum. Servis taleplerini hiçbiri eşleşen switch ifadesi bir özel durum oluşturur. Tüm olası durumların anahtar İfadenizde kapsamaz varsa derleyici bir uyarı oluşturur.

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

Artık ekleyebilirsiniz `static` değiştiricisi yerel bu işlevi sağlamak için yerel işlevler için değil (başvuru) yakalama kapsayan kapsamdan gelen tüm değişkenler. Bunun yapılması oluşturur `CS8421`, "statik bir yerel işleve başvuru içeremez <variable>." 

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

## <a name="nullable-reference-types"></a>Null başvuru türleri

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

Dizin belirtebilirsiniz **sonundan**. Belirttiğiniz **sonundan** kullanarak `^` işleci. Bilginiz `array[2]` öğe "başından itibaren 2" anlamına gelir. Şimdi, `array[^2]` öğe "2 sonundan" anlamına gelir. Dizin `^0` "Bitiş" ya da son öğeyi izleyen dizini anlamına gelir.

Belirtebileceğiniz bir **aralığı** ile **aralık işleci**: `..`. Örneğin, `0..^0` dizi aralığının tamamı belirtir: 0'ın başından itibaren en fazla, ancak son 0 dahil değil. İki işlenenden "Başlangıç" veya "sonuna" kullanabilir. Ayrıca, iki işlenenden atlanabilir. Varsayılanlar `0` başlangıç dizini ve `^0` son dizini.

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
};
```

Her öğenin dizini "Başlat" ve "Kimden"son kavramı güçlendirir ve aralığın sonunu fiyatlara aralıktır. "Başlangıç" tüm dizinin ilk öğedir. Tüm dizi "End" *geçmiş* son öğe.

Son sözcüğü alabilirsiniz `^1` dizini:

```csharp
Console.WriteLine($"The last word is {words[^1]}");
// writes "dog"
```

Aşağıdaki kod, bir alt aralığı sözcükler "Hızlı", "brown" ile ve "fox" oluşturur. İçerdiği `words[1]` aracılığıyla `words[3]`. Öğe `words[4]` aralığında değil.

```csharp
var brownFox = words[1..4];
```

Aşağıdaki kod, "geç" ve "köpek" alt oluşturur. İçerdiği `words[^2]` ve `words[^1]`. Bitiş dizini `words[^0]` dahil edilmez:

```csharp
var lazyDog = words[^2..^0];
```

Aşağıdaki örnekler, açık olan başında, sonunda ya da her ikisi için bitiş aralıkları oluşturur:

```csharp
var allWords = words[..]; // contains "The" through "dog".
var firstPhrase = words[..4]; // contains "The" through "fox"
var lastPhrase = words[6..]; // contains "the, "lazy" and "dog"
```

De aralık değişkenleri olarak bildirebilirsiniz:

```csharp
Range phrase = 1..4;
```

Aralık içinde sonra kullanılabilir `[` ve `]` karakter:

```csharp
var text = words[phrase];
```
