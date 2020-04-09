---
title: C# 8.0 -C# Guide'daki yenilikler
description: C# 8.0'da bulunan yeni özellikler hakkında genel bir bakış alın.
ms.date: 04/07/2020
ms.openlocfilehash: 1a005750751129969f2d1e9caf156330dbe61cb2
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989213"
---
# <a name="whats-new-in-c-80"></a>C# 8.0'daki yenilikler

C# 8.0, C# diline aşağıdaki özellikleri ve geliştirmeleri ekler:

- [Yalnızca üyeler okunur](#readonly-members)
- [Varsayılan arabirim metotları](#default-interface-methods)
- [Desen eşleştirme geliştirmeleri:](#more-patterns-in-more-places)
  - [İfadeleri değiştirme](#switch-expressions)
  - [Özellik desenleri](#property-patterns)
  - [Tuple desenleri](#tuple-patterns)
  - [Konumsal desenler](#positional-patterns)
- [Bildirimleri kullanma](#using-declarations)
- [Statik yerel fonksiyonlar](#static-local-functions)
- [Tek kullanımlık ref structs](#disposable-ref-structs)
- [Boş değer atanabilir başvuru türleri](#nullable-reference-types)
- [Asenkron akarsular](#asynchronous-streams)
- [Asynchronous tek kullanımlık](#asynchronous-disposable)
- [Endeksler ve aralıklar](#indices-and-ranges)
- [Null-coalescing atama](#null-coalescing-assignment)
- [Yönetilmeyen yapılı türler](#unmanaged-constructed-types)
- [İç içe ifadelerde Stackalloc](#stackalloc-in-nested-expressions)
- [Enterpolasyonlu harfi harfine dizelerin geliştirilmesi](#enhancement-of-interpolated-verbatim-strings)

C# 8.0 **.NET Core 3.x** ve **.NET Standart 2.1**üzerinde desteklenir. Daha fazla bilgi için [C# dil sürümüne](../language-reference/configure-language-version.md)bakın.

Bu makalenin geri kalanı kısaca bu özellikleri açıklar. Ayrıntılı makalelerin mevcut olduğu yerlerde, bu öğreticilere bağlantılar ve genel bakışlar sağlanır. `dotnet try` Bu özellikleri ortamınızda genel aracı kullanarak keşfedebilirsiniz:

1. [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global aracını yükleyin.
1. [Dotnet/try-samples](https://github.com/dotnet/try-samples) deposunu klonla.
1. *Deneme örnekleri* deposu için geçerli dizini *csharp8* alt dizinine ayarlayın.
1. `dotnet try` öğesini çalıştırın.

## <a name="readonly-members"></a>Yalnızca üyeler okunur

`readonly` Değiştiriciyi bir yapının üyelerine uygulayabilirsiniz. Üyenin durumu değiştirmediğini gösterir. `readonly` Değiştiriciyi bir `struct` bildirime uygulamaktan daha ayrıntılıdır.  Aşağıdaki mutable struct düşünün:

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

Çoğu yapı da, `ToString()` yöntem durumu değiştirmez. `readonly` Aşağıdakileri bildirgeye değiştirici ekleyerek şunları `ToString()`belirtebilirsiniz:

```csharp
public readonly override string ToString() =>
    $"({X}, {Y}) is {Distance} from the origin";
```

Önceki değişiklik derleyici uyarısı oluşturur, `ToString` çünkü işaretlenmemiş `Distance` `readonly`olan özelliğe erişir:

```console
warning CS8656: Call to non-readonly member 'Point.Distance.get' from a 'readonly' member results in an implicit copy of 'this'
```

Derleyici, savunma amaçlı bir kopya oluşturması gerektiğinde sizi uyarır.  Özellik `Distance` durumu değiştirmez, bu nedenle bildirime `readonly` değiştirici ekleyerek bu uyarıyı düzeltebilirsiniz:

```csharp
public readonly double Distance => Math.Sqrt(X * X + Y * Y);
```

Değiştiricinin `readonly` salt okunur bir özellik için gerekli olduğuna dikkat edin. Derleyici, erişimedenlerin `get` durumu değiştirmediğini varsaymaz; açıkça bildirmelisiniz. `readonly` Otomatik olarak uygulanan özellikler bir özel durumdur; derleyici tüm otomatik olarak uygulanan getters readonly olarak ele alacak, bu `readonly` nedenle burada ve `X` `Y` özellikleri değiştirici eklemek için gerek yoktur.

Derleyici, `readonly` üyelerin durumu değiştirmediği kuralı nı uygular. `readonly` Değiştiriciyi kaldırmadığınız sürece aşağıdaki yöntem derlenmez:

```csharp
public readonly void Translate(int xOffset, int yOffset)
{
    X += xOffset;
    Y += yOffset;
}
```

Bu özellik, derleyicinin bunu uygulayabilmesi ve bu amacla dayalı optimizasyonlar yapabilmesi için tasarım amacınızı belirtmenize olanak tanır. Dil referans makalesinde yalnızca okumuş üyeler [`readonly`](../language-reference/keywords/readonly.md#readonly-member-examples)hakkında daha fazla bilgi edinebilirsiniz.

## <a name="default-interface-methods"></a>Varsayılan arabirim metotları

Artık arabirimlere üye ekleyebilir ve bu üyeler için bir uygulama sağlayabilirsiniz. Bu dil özelliği, API yazarlarının kaynak veya bu arabirimin varolan uygulamalarıyla ikili uyumluluk bozmadan sonraki sürümlerde bir arabirime yöntem eklemelerine olanak tanır. Varolan uygulamalar varsayılan uygulamayı *devralır.* Bu özellik aynı zamanda C#'ın benzer özellikleri destekleyen Android veya Swift'i hedefleyen API'lerle birlikte çalışmasını da sağlar. Varsayılan arabirim yöntemleri de bir "özellikler" dil özelliğine benzer senaryolar sağlar.

Varsayılan arabirim yöntemleri birçok senaryoyu ve dil öğelerini etkiler. İlk öğreticimiz [varsayılan uygulamalarla bir arabirimi güncelleştirmeyi](../tutorials/default-interface-methods-versions.md)kapsar. Diğer öğreticiler ve referans güncellemeleri genel sürüm için zamanında geliyor.

## <a name="more-patterns-in-more-places"></a>Daha fazla yerde daha fazla desen

**Desen eşleştirme,** ilgili ancak farklı veri türleri arasında şekle bağımlı işlevsellik sağlamak için araçlar verir. C# 7.0 [`is`](../language-reference/keywords/is.md) ifade ve [`switch`](../language-reference/keywords/switch.md) deyimi kullanarak tür desenleri ve sabit desenler için sözdizimi tanıttı. Bu özellikler, veri ve işlevselliğin birbirinden ayrı yaşadığı programlama paradigmalarını desteklemeye yönelik ilk geçici adımları temsil eder. Endüstri daha fazla mikro hizmet ve diğer bulut tabanlı mimarilere doğru ilerlerken, diğer dil araçlarına ihtiyaç duyulur.

C# 8.0 bu kelime dağarcığını genişletir, böylece kodunuzda daha fazla yerde daha fazla desen ifadesi kullanabilirsiniz. Verileriniz ve işlevleriniz ayrı olduğunda bu özellikleri göz önünde bulundurun. Algoritmalarınız bir nesnenin çalışma zamanı türü nden başka bir gerçeğe bağlı olduğunda desen eşleştirmeyi göz önünde bulundurun. Bu teknikler tasarımları ifade etmek için başka bir yol sağlar.

Yeni yerlerde yeni desenlerek, C # 8.0 **özyinelemeli desenler**ekler. Herhangi bir desen ifadesinin sonucu bir ifadedir. Özyinelemeli desen, başka bir desen ifadesinin çıktısına uygulanan bir desen ifadesidir.

### <a name="switch-expressions"></a>İfadeleri değiştirme

Genellikle, [`switch`](../language-reference/keywords/switch.md) bir deyim bloklarının `case` her birinde bir değer üretir. **İfadeleri değiştirin,** daha kısa ifade sözdizimini kullanmanıza olanak tanır. Daha az yinelenen `case` ve `break` anahtar kelimeler ve daha az kıvırcık parantez vardır.  Örnek olarak, gökkuşağının renklerini listeleyen aşağıdaki enum'u göz önünde bulundurun:

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

Uygulamanız `RGBColor` `R`, ve `G` `B` bileşenlerinden oluşturulmuş bir tür tanımlıysa, bir anahtarı ifade içeren aşağıdaki yöntemi kullanarak bir `Rainbow` değeri RGB değerlerine dönüştürebilirsiniz:

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

Burada çeşitli sözdizimi geliştirmeleri vardır:

- Değişken anahtar kelimeden `switch` önce gelir. Farklı sıra, anahtar ifadesini anahtar deyiminden ayırt etmeyi görsel olarak kolaylaştırır.
- Ve `case` `:` elemanları ile `=>`değiştirilir. Daha kısa ve sezgisel.
- Servis `default` talebi bir `_` atma ile değiştirilir.
- Cesetler ifadelerdir, ifadeler değil.

Klasik `switch` deyimi kullanarak eşdeğer kod ile kontrast:

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

**Özellik deseni,** incelenen nesnenin özellikleriyle eşleşmenizi sağlar. Alıcının adresine göre satış vergisini hesaplaması gereken bir e-ticaret sitesi düşünün. Bu hesaplama bir `Address` sınıfın temel sorumluluğu değildir. Zaman içinde, büyük olasılıkla adres biçimi değişikliklerinden daha sık değişecektir. Satış vergisi nin tutarı adresin özelliğine `State` bağlıdır. Aşağıdaki yöntem, adresten ve fiyattan satış vergisini hesaplamak için özellik deseni kullanır:

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

Desen eşleştirme, bu algoritmayı ifade etmek için kısa bir sözdizimi oluşturur.

### <a name="tuple-patterns"></a>Tuple desenleri

Bazı algoritmalar birden çok girişe bağlıdır. **Tuple desenleri,** [tuple](../tuples.md)olarak ifade edilen birden çok değere göre geçiş yapmanızı sağlar.  Aşağıdaki kod oyun *kaya, kağıt, makas*için bir anahtar ifadesi gösterir:

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

İletiler kazananı gösterir. Atma örneği, bağlar veya diğer metin girişleri için üç birleşimi temsil eder.

### <a name="positional-patterns"></a>Konumsal desenler

Bazı türler, `Deconstruct` özelliklerini ayrı değişkenlere dönüştüren bir yöntem içerir. Bir `Deconstruct` yönteme erişilebilir olduğunda, nesnenin özelliklerini incelemek ve bu özellikleri bir desen için kullanmak için **konumsal desenlerk** kullanabilirsiniz.  Ayrı değişkenler `Point` oluşturmak `Deconstruct` için `X` bir yöntem içeren aşağıdaki `Y`sınıfı göz önünde bulundurun:

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

Ayrıca, bir çeyreğin çeşitli konumlarını temsil eden aşağıdaki enum düşünün:

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

Aşağıdaki yöntem ve değerlerini `x` ayıklamak için **konumsal desen** `y`kullanır. Daha sonra, `when` noktanın `Quadrant` belirlenmesi için bir yan tümce kullanır:

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

Önceki anahtardaki atma deseni, `x` 0 `y` olduğunda veya 0 olduğunda eşleşir, ancak her ikisi yle eşleşmez. Bir anahtar ifadesi bir değer oluşturmalı veya bir özel durum atmalıdır. Servis taleplerini hiçbiri eşleşmiyorsa, anahtar ifadesi bir özel durum atar. Derleyici, anahtar ifadenizdeki olası tüm durumları kapsamazsanız, sizin için bir uyarı oluşturur.

Desen eşleştirme bu gelişmiş [öğretici](../tutorials/pattern-matching.md)desen eşleştirme teknikleri keşfedebilirsiniz.

## <a name="using-declarations"></a>Bildirimleri kullanma

**Using declaration,** anahtar sözcüğün `using` önünde yer alan değişken bildirimidir. Derleyiciye, bildirilen değişkenin ilgili kapsamın sonunda atılması gerektiğini söyler. Örneğin, bir metin dosyası yazan aşağıdaki kodu göz önünde bulundurun:

```csharp
static int WriteLinesToFile(IEnumerable<string> lines)
{
    using var file = new System.IO.StreamWriter("WriteLines2.txt");
    // Notice how we declare skippedLines after the using statement.
    int skippedLines = 0;
    foreach (string line in lines)
    {
        if (!line.Contains("Second"))
        {
            file.WriteLine(line);
        }
        else
        {
            skippedLines++;
        }
    }
    // Notice how skippedLines is in scope here.
    return skippedLines;
    // file is disposed here
}
```

Önceki örnekte, yöntemin kapanış ayracına ulaşıldığında dosya atılır. Bu, beyan `file` edilen kapsamın sonudur. Önceki kod klasik [kullanarak deyimi](../language-reference/keywords/using-statement.md)kullanan aşağıdaki koda eşdeğerdir:

```csharp
static int WriteLinesToFile(IEnumerable<string> lines)
{
    // We must declare the variable outside of the using block
    // so that it is in scope to be returned.
    int skippedLines = 0;
    using (var file = new System.IO.StreamWriter("WriteLines2.txt"))
    {
        foreach (string line in lines)
        {
            if (!line.Contains("Second"))
            {
                file.WriteLine(line);
            }
            else
            {
                skippedLines++;
            }
        }
    } // file is disposed here
    return skippedLines;
}
```

Önceki örnekte, `using` deyimle ilişkili kapanış ayracına ulaşıldığında dosya atılır.

Her iki durumda da `Dispose()`derleyici. `using` İfadedeki ifade tek kullanımlık değilse derleyici bir hata oluşturur.

## <a name="static-local-functions"></a>Statik yerel fonksiyonlar

Artık yerel işlevin ilgili kapsamdan herhangi bir değişkeni yakalamadığından (başvuru) olmadığından emin olmak için değiştiriciyi yerel işlevlere ekleyebilirsiniz. `static` Bunu yapmak `CS8421`, "Statik yerel bir işlev değişken \<> bir başvuru içeremez" oluşturur.

Aşağıdaki kodu göz önünde bulundurun. Yerel işlev, `LocalFunction` ekkapsamda `y`bildirilen değişkene (yöntem) `M`erişer. Bu `LocalFunction` nedenle, `static` değiştirici ile ilan edilemez:

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

Aşağıdaki kod statik yerel bir işlev içerir. Statik olabilir, çünkü ekkapsamdaki herhangi bir değişkene erişemez:

```csharp
int M()
{
    int y = 5;
    int x = 7;
    return Add(x, y);

    static int Add(int left, int right) => left + right;
}
```

## <a name="disposable-ref-structs"></a>Tek kullanımlık ref structs

Değiştirici ile bildirilen bir `struct` arabirim uygulayamaz ve bu nedenle uygulayamaz. <xref:System.IDisposable> `ref` Bu nedenle, `ref struct` bir bertaraf sağlamak için, erişilebilir `void Dispose()` bir yöntem olmalıdır. Bu özellik bildirimler `readonly ref struct` için de geçerlidir.

## <a name="nullable-reference-types"></a>Boş değer atanabilir başvuru türleri

Geçersiz bir ek açıklama bağlamı içinde, başvuru türünün herhangi bir değişkeni geçersiz bir **başvuru türü**olarak kabul edilir. Bir değişkenin null olabileceğini belirtmek istiyorsanız, değişkeni geçersiz bir `?` **başvuru türü**olarak bildirmek için tür adını eklemelisiniz.

Nullable olmayan başvuru türleri için derleyici, yerel değişkenlerin beyan edildiğinde null olmayan bir değere başvurulmasını sağlamak için akış çözümlemesi kullanır. Alanlar inşaat sırasında başharfle alınmalıdır. Derleyici, değişken kullanılabilir yapıcılardan herhangi birini arayarak veya bir baş harfe çağırışla ayarlamıyorsa bir uyarı oluşturur. Ayrıca, geçersiz başvuru türleri null olabilir bir değer atanamaz.

Nullable başvuru türleri, null'a atanmadıklarından veya başharfe atanmadıklarından emin olmak için denetlenmez. Ancak derleyici, nullable başvuru türündeki herhangi bir değişkenin null'a erişilmeden veya nullable olmayan bir başvuru türüne atanmadan önce null'a karşı denetlenmesini sağlamak için akış çözümlemesi kullanır.

Nullable [başvuru türlerinin](../nullable-references.md)genel bakışında özellik hakkında daha fazla bilgi edinebilirsiniz. Bu [nullable referans türleri öğretici](../tutorials/nullable-reference-types.md)yeni bir uygulamada kendiniz deneyin. Geçersiz [başvuru türleri öğretici kullanmak için bir uygulama geçirinde](../tutorials/upgrade-to-nullable-references.md)geçersiz başvuru türlerini kullanmak için varolan bir kod tabanını geçirme adımları hakkında bilgi edinin.

## <a name="asynchronous-streams"></a>Asenkron akarsular

C# 8.0 ile başlayarak, akışları eşit bir şekilde oluşturabilir ve tüketebilirsiniz. Bir eşzamanlı akış döndüren bir yöntem üç özelliği vardır:

1. `async` Değiştirici ile ilan edildi.
1. Bir <xref:System.Collections.Generic.IAsyncEnumerable%601>.
1. Yöntem, `yield return` eşzamanlı akışta ardışık öğeleri döndürmek için ifadeler içerir.

Asenkron akışı tüketmek, akışın öğelerini sayısala rken `await` anahtar kelimeden `foreach` önce anahtar kelimeeklemenizi gerektirir. Anahtar `await` kelimenin eklenmesi, değiştirici ile `async` bildirilecek ve bir `async` yöntem için izin verilen bir türü döndürmek için eşzamanlı akışı sayısala getiren bir yöntem gerektirir. Genellikle bu bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601>. Ayrıca bir <xref:System.Threading.Tasks.ValueTask> veya <xref:System.Threading.Tasks.ValueTask%601>olabilir . Bir yöntem hem tüketebilir hem de bir eşzamanlı akış üretebilir, bu da bir <xref:System.Collections.Generic.IAsyncEnumerable%601>. Aşağıdaki kod, her sayı oluşturma arasında 100 ms bekleyen 0'dan 19'a kadar bir sıra oluşturur:

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

`await foreach` İfadeyi kullanarak sırayı sıralarsınız:

```csharp
await foreach (var number in GenerateSequence())
{
    Console.WriteLine(number);
}
```

Async [akışları oluşturma ve tüketme](../tutorials/generate-consume-asynchronous-stream.md)konusunda öğreticimizde asynchronous akışlarını kendiniz deneyebilirsiniz. Varsayılan olarak, akış öğeleri yakalanan bağlamında işlenir. Bağlamın ele geçirilmesini devre dışı kılmış <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> olmak istiyorsanız, uzantı yöntemini kullanın. Eşitleme bağlamları ve geçerli bağlamı yakalama hakkında daha fazla bilgi [için, Görev tabanlı eşzamanlı deseni tüketme makalesine](../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)bakın.

## <a name="asynchronous-disposable"></a>Asynchronous tek kullanımlık

C# 8.0 ile başlayarak, dil <xref:System.IAsyncDisposable?displayProperty=nameWithType> arabirimi uygulayan tek kullanımlık türleri destekler. Bir `using` ifadenin operand ya <xref:System.IDisposable> <xref:System.IAsyncDisposable>da uygulayabilirsiniz . Durumunda `IAsyncDisposable`, derleyici `await` <xref:System.Threading.Tasks.Task> döndürülen <xref:System.IAsyncDisposable.DisposeAsync%2A?displayProperty=nameWithType>kod oluşturur. Daha fazla bilgi için [ `using` ifadeye](../language-reference/keywords/using-statement.md)bakın.

## <a name="indices-and-ranges"></a>Endeksler ve aralıklar

Endeksler ve aralıklar, bir dizideki tek öğelere veya aralıklara erişmek için kısa bir sözdizimi sağlar.

Bu dil desteği iki yeni türe ve iki yeni işleçe dayanır:

- <xref:System.Index?displayProperty=nameWithType>diziye bir dizi içine bir dizi temsil eder.
- Bir dizin `^`dizinin dizinin sonuna göreolduğunu belirten son işleçten gelen dizin.
- <xref:System.Range?displayProperty=nameWithType>bir dizinin alt aralığını temsil eder.
- Aralık işleci, `..`bir aralığın başlangıcını ve sonunu operands olarak belirtir.

Dizinler için kurallarla başlayalım. Bir dizi `sequence`düşünün. Dizin `0` `sequence[0]`aynıdır. Dizin `^0` `sequence[sequence.Length]`aynıdır. Bu `sequence[^0]` bir özel durum atmak `sequence[sequence.Length]` yok unutmayın, tıpkı yok. Herhangi bir `n`sayı `^n` için dizin `sequence.Length - n`.

Aralık, bir aralığın *başlangıcını* ve *sonunu* belirtir. Aralığın başlangıcı dahildir, ancak aralığın sonu özeldir, yani *başlangıç* aralıkta yer alan ancak *sonu* aralıkta yer almıyor. Aralık, `[0..^0]` tüm aralığı `[0..sequence.Length]` temsil eder gibi tüm aralığı temsil eder.

Bazı örneklere bakalım. Başından ve sonundan itibaren diziniyle açıklamalı aşağıdaki diziyi düşünün:

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

`^1` Dizinile son sözcüğü alabilirsiniz:

```csharp
Console.WriteLine($"The last word is {words[^1]}");
// writes "dog"
```

Aşağıdaki kod ,"hızlı", "kahverengi" ve "tilki" sözcükleri içeren bir alt aralık oluşturur. Bu `words[1]` aracılığıyla `words[3]`içerir. Öğe `words[4]` aralıkta değil.

```csharp
var quickBrownFox = words[1..4];
```

Aşağıdaki kod "tembel" ve "köpek" ile bir alt aralığı oluşturur. Bu `words[^2]` içerir `words[^1]`ve . Bitiş dizini `words[^0]` dahil değildir:

```csharp
var lazyDog = words[^2..^0];
```

Aşağıdaki örnekler, başlangıç, bitiş veya her ikisi için açık uçlu aralıklar oluşturur:

```csharp
var allWords = words[..]; // contains "The" through "dog".
var firstPhrase = words[..4]; // contains "The" through "fox"
var lastPhrase = words[6..]; // contains "the", "lazy" and "dog"
```

Aralıkları değişken olarak da bildirebilirsiniz:

```csharp
Range phrase = 1..4;
```

Aralık daha sonra `[` `]` ve karakterler içinde kullanılabilir:

```csharp
var text = words[phrase];
```

Yalnızca diziler endeksleri ve aralıkları desteklemekle kalmıyor. Ayrıca [dize](../language-reference/builtin-types/reference-types.md#the-string-type)ile endeksleri ve aralıkları kullanabilirsiniz , <xref:System.Span%601>veya <xref:System.ReadOnlySpan%601>. Daha fazla bilgi [için, endeksler ve aralıklar için Tür desteğine](../tutorials/ranges-indexes.md#type-support-for-indices-and-ranges)bakın.

Endeksler ve aralıklarla ilgili öğreticide [endeksler ve aralıklar](../tutorials/ranges-indexes.md)hakkında daha fazla şey keşfedebilirsiniz.

## <a name="null-coalescing-assignment"></a>Null-coalescing atama

C# 8.0 null-coalescing atama `??=`işleci tanıttı. İşleç, `??=` sağ el operand değerini sol operand'ına atamak için kullanabilirsiniz ve yalnızca sol `null`operand'ın .'a değer biçerek.

```csharp
List<int> numbers = null;
int? i = null;

numbers ??= new List<int>();
numbers.Add(i ??= 17);
numbers.Add(i ??= 20);

Console.WriteLine(string.Join(" ", numbers));  // output: 17 17
Console.WriteLine(i);  // output: 17
```

Daha fazla bilgi için, bkz [?? = işleçler](../language-reference/operators/null-coalescing-operator.md) makale.

## <a name="unmanaged-constructed-types"></a>Yönetilmeyen yapılı türler

C# 7.3 ve daha önce, yapılandırılan bir tür (en az bir tür bağımsız değişken içeren bir tür) [yönetilmeyen](../language-reference/builtin-types/unmanaged-types.md)bir tür olamaz. C# 8.0 ile başlayarak, yalnızca yönetilmeyen türlerde alanlar içeriyorsa, yapılandırılan bir değer türü yönetilemez.

Örneğin, genel `Coords<T>` türün aşağıdaki tanımı göz önüne alındığında:

```csharp
public struct Coords<T>
{
    public T X;
    public T Y;
}
```

`Coords<int>` türü C# 8.0 ve sonraki yıllarda yönetilmeyen bir türdür. Herhangi bir yönetilmeyen tür için olduğu gibi, bu tür bir değişken için bir işaretçi oluşturabilir veya bu tür örnekleri için [yığınüzerinde bellek bloğu tahsis](../language-reference/operators/stackalloc.md) edebilirsiniz:

```csharp
Span<Coords<int>> coordinates = stackalloc[]
{
    new Coords<int> { X = 0, Y = 0 },
    new Coords<int> { X = 0, Y = 3 },
    new Coords<int> { X = 4, Y = 0 }
};
```

Daha fazla bilgi için [yönetilmeyen türlere](../language-reference/builtin-types/unmanaged-types.md)bakın.

## <a name="stackalloc-in-nested-expressions"></a>İç içe ifadelerde Stackalloc

C# 8.0 ile başlayarak, [stackalloc](../language-reference/operators/stackalloc.md) ifadesinin <xref:System.Span%601?displayProperty=nameWithType> sonucu <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> veya türündeise, diğer ifadelerdeki ifadeyi `stackalloc` kullanabilirsiniz:

```csharp
Span<int> numbers = stackalloc[] { 1, 2, 3, 4, 5, 6 };
var ind = numbers.IndexOfAny(stackalloc[] { 2, 4, 6 ,8 });
Console.WriteLine(ind);  // output: 1
```

## <a name="enhancement-of-interpolated-verbatim-strings"></a>Enterpolasyonlu harfi harfine dizelerin geliştirilmesi

[Enterpolasyonlu](../language-reference/tokens/interpolated.md) `$@"..."` kelime dizeleri `@$"..."` `$` ve `@` belirteçleri sırası herhangi olabilir: her ikisi de ve geçerli interpolated verbatim dizeleri vardır. Önceki C# sürümlerinde `$` belirteç belirteçten `@` önce görünmelidir.
