---
title: İçindeki yenilikler C# 8.0 - C# Kılavuzu
description: Uygulamasında kullanılabilen yeni özellikleri genel bakış C# 8.0. Bu makalede, preview 2'ile güncel durumda.
ms.date: 02/12/2019
ms.openlocfilehash: 1aa5a200f84b35fda3c33a900655249d07000e8e
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2019
ms.locfileid: "56835440"
---
# <a name="whats-new-in-c-80"></a><span data-ttu-id="dabc0-104">İçindeki yenilikler C# 8.0</span><span class="sxs-lookup"><span data-stu-id="dabc0-104">What's new in C# 8.0</span></span>

<span data-ttu-id="dabc0-105">İçin birçok geliştirme vardır C# Önizleme 2 ile deneyebileceğiniz dili.</span><span class="sxs-lookup"><span data-stu-id="dabc0-105">There are many enhancements to the C# language that you can try out already with preview 2.</span></span> <span data-ttu-id="dabc0-106">Preview 2 sürümünde eklenen yeni özellikleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="dabc0-106">The new features added in preview 2 are:</span></span>

- <span data-ttu-id="dabc0-107">[Desen eşleştirme geliştirmeleri](#more-patterns-in-more-places):</span><span class="sxs-lookup"><span data-stu-id="dabc0-107">[Pattern matching enhancements](#more-patterns-in-more-places):</span></span>
  * [<span data-ttu-id="dabc0-108">Anahtar ifadeler</span><span class="sxs-lookup"><span data-stu-id="dabc0-108">Switch expressions</span></span>](#switch-expressions)
  * [<span data-ttu-id="dabc0-109">Özellik desenleri</span><span class="sxs-lookup"><span data-stu-id="dabc0-109">Property patterns</span></span>](#property-patterns)
  * [<span data-ttu-id="dabc0-110">Kayıt düzenleri</span><span class="sxs-lookup"><span data-stu-id="dabc0-110">Tuple patterns</span></span>](#tuple-patterns)
  * [<span data-ttu-id="dabc0-111">Konumsal desenleri</span><span class="sxs-lookup"><span data-stu-id="dabc0-111">Positional patterns</span></span>](#positional-patterns)
- [<span data-ttu-id="dabc0-112">Bildirimi kullanarak</span><span class="sxs-lookup"><span data-stu-id="dabc0-112">Using declarations</span></span>](#using-declarations)
- [<span data-ttu-id="dabc0-113">Statik yerel işlevler</span><span class="sxs-lookup"><span data-stu-id="dabc0-113">Static local functions</span></span>](#static-local-functions)
- [<span data-ttu-id="dabc0-114">Atılabilir başvuru yapı birimleri</span><span class="sxs-lookup"><span data-stu-id="dabc0-114">Disposable ref structs</span></span>](#disposable-ref-structs)

<span data-ttu-id="dabc0-115">Aşağıdaki dil özellikleri ilk göründüğü C# 8.0 Önizleme 1:</span><span class="sxs-lookup"><span data-stu-id="dabc0-115">The following language features first appeared in C# 8.0 preview 1:</span></span>

- [<span data-ttu-id="dabc0-116">Boş değer atanabilir başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="dabc0-116">Nullable reference types</span></span>](#nullable-reference-types)
- [<span data-ttu-id="dabc0-117">Zaman uyumsuz akışlar</span><span class="sxs-lookup"><span data-stu-id="dabc0-117">Asynchronous streams</span></span>](#asynchronous-streams)
- [<span data-ttu-id="dabc0-118">Dizinleri ve aralıkları</span><span class="sxs-lookup"><span data-stu-id="dabc0-118">Indices and ranges</span></span>](#indices-and-ranges)

> [!NOTE]
> <span data-ttu-id="dabc0-119">Bu makale için en son güncelleştirildiği C# 8.0 Önizleme 2.</span><span class="sxs-lookup"><span data-stu-id="dabc0-119">This article was last updated for C# 8.0 preview 2.</span></span>

<span data-ttu-id="dabc0-120">Bu makalenin geri kalanında bu özelliklere kısaca açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dabc0-120">The remainder of this article briefly describes these features.</span></span> <span data-ttu-id="dabc0-121">Ayrıntılı makaleleri kullanılabiliyorsa, bu öğreticileri ve genel bakışlar bağlantılar verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="dabc0-121">Where in-depth articles are available, links to those tutorials and overviews are provided.</span></span>

## <a name="more-patterns-in-more-places"></a><span data-ttu-id="dabc0-122">Daha fazla yerde daha fazla desenleri</span><span class="sxs-lookup"><span data-stu-id="dabc0-122">More patterns in more places</span></span>

<span data-ttu-id="dabc0-123">**Desen eşleştirme** ilgili ancak farklı türde veriler arasında şekil bağlı işlevler sağlamak için Araçlar verir.</span><span class="sxs-lookup"><span data-stu-id="dabc0-123">**Pattern matching** gives tools to provide shape-dependent functionality across related but different kinds of data.</span></span> <span data-ttu-id="dabc0-124">C#7.0 sunulan tür kalıpları ve sabit desenler sözdizimi kullanarak [ `is` ](../language-reference/keywords/is.md) ifade ve [ `switch` ](../language-reference/keywords/switch.md) deyimi.</span><span class="sxs-lookup"><span data-stu-id="dabc0-124">C# 7.0 introduced syntax for type patterns and constant patterns by using the [`is`](../language-reference/keywords/is.md) expression and the [`switch`](../language-reference/keywords/switch.md) statement.</span></span> <span data-ttu-id="dabc0-125">Bu özellikler veri ve işlevsellik burada parçalayın Canlı programlama paradigmalarını destekleme doğru ilk belirsiz adımları temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="dabc0-125">These features represented the first tentative steps toward supporting programming paradigms where data and functionality live apart.</span></span> <span data-ttu-id="dabc0-126">Daha fazla mikro Hizmetleri ve diğer bulut tabanlı mimariler doğru sektör hareket ettikçe diğer dil araçları gereklidir.</span><span class="sxs-lookup"><span data-stu-id="dabc0-126">As the industry moves toward more microservices and other cloud-based architectures, other language tools are needed.</span></span>

<span data-ttu-id="dabc0-127">C#Daha fazla yerde daha fazla desen ifade kodunuzda kullanabilmeniz için bu sözlük 8.0 genişletir.</span><span class="sxs-lookup"><span data-stu-id="dabc0-127">C# 8.0 expands this vocabulary so you can use more pattern expressions in more places in your code.</span></span> <span data-ttu-id="dabc0-128">Veri ve işlevsellik ayrı olduğunda bu özellikleri göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="dabc0-128">Consider these features when your data and functionality are separate.</span></span> <span data-ttu-id="dabc0-129">Bir nesnenin çalışma zamanı türü dışında bir olgu algoritmalarınızı bağımlı olduğunda desen eşleştirme göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="dabc0-129">Consider pattern matching when your algorithms depend on a fact other than the runtime type of an object.</span></span> <span data-ttu-id="dabc0-130">Bu teknikler tasarımları ifade etmek için başka bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="dabc0-130">These techniques provide another way to express designs.</span></span>

<span data-ttu-id="dabc0-131">Yeni yerde yeni desenler yanı sıra C# 8.0 ekler **özyinelemeli desenleri**.</span><span class="sxs-lookup"><span data-stu-id="dabc0-131">In addition to new patterns in new places, C# 8.0 adds **recursive patterns**.</span></span> <span data-ttu-id="dabc0-132">Bir ifade deseni herhangi bir ifade sonucudur.</span><span class="sxs-lookup"><span data-stu-id="dabc0-132">The result of any pattern expression is an expression.</span></span> <span data-ttu-id="dabc0-133">Yalnızca başka bir desen ifadesi çıkışına uygulanan bir desen ifadesi özyinelemeli modelidir.</span><span class="sxs-lookup"><span data-stu-id="dabc0-133">A recursive pattern is simply a pattern expression applied to the output of another pattern expression.</span></span>

### <a name="switch-expressions"></a><span data-ttu-id="dabc0-134">Anahtar ifadeler</span><span class="sxs-lookup"><span data-stu-id="dabc0-134">switch expressions</span></span>

<span data-ttu-id="dabc0-135">Genellikle, bir [ `switch` ](../language-reference/keywords/switch.md) deyimi, her bir değer oluşturuyor, `case` engeller.</span><span class="sxs-lookup"><span data-stu-id="dabc0-135">Often, a [`switch`](../language-reference/keywords/switch.md) statement produces a value in each of its `case` blocks.</span></span> <span data-ttu-id="dabc0-136">**Anahtar ifadeler** , daha kısa ifade sözdizimini kullanacak şekilde etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="dabc0-136">**Switch expressions** enable you to use more concise expression syntax.</span></span> <span data-ttu-id="dabc0-137">Vardır daha az tekrarlı `case` ve `break` anahtar sözcükleri ve daha az küme ayraçları.</span><span class="sxs-lookup"><span data-stu-id="dabc0-137">There are fewer repetitive `case` and `break` keywords, and fewer curly braces.</span></span>  <span data-ttu-id="dabc0-138">Örneğin, rainbow renklerini listeleyen aşağıdaki enum göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="dabc0-138">As an example, consider the following enum that lists the colors of the rainbow:</span></span>

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

<span data-ttu-id="dabc0-139">Dönüştürme bir `Rainbow` switch ifadesi içeren aşağıdaki yöntemi kullanarak kendi RGB değerleri için değer:</span><span class="sxs-lookup"><span data-stu-id="dabc0-139">You could convert a `Rainbow` value to its RGB values using the following method containing a switch expression:</span></span>

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

<span data-ttu-id="dabc0-140">Burada birkaç söz dizimi geliştirmeleri vardır:</span><span class="sxs-lookup"><span data-stu-id="dabc0-140">There are several syntax improvements here:</span></span>

- <span data-ttu-id="dabc0-141">Değişken önce gelen `switch` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="dabc0-141">The variable comes before the `switch` keyword.</span></span> <span data-ttu-id="dabc0-142">Farklı sıra switch ifadesi switch deyiminden ayırt görsel olarak kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="dabc0-142">The different order makes it visually easy to distinguish the switch expression from the switch statement.</span></span>
- <span data-ttu-id="dabc0-143">`case` Ve `:` öğeleri yerine `=>`.</span><span class="sxs-lookup"><span data-stu-id="dabc0-143">The `case` and `:` elements are replaced with `=>`.</span></span> <span data-ttu-id="dabc0-144">Bu daha kısa ve kolay anlaşılır olur.</span><span class="sxs-lookup"><span data-stu-id="dabc0-144">It's more concise and intuitive.</span></span>
- <span data-ttu-id="dabc0-145">`default` Çalışması ile değiştirildiği bir `_` atın.</span><span class="sxs-lookup"><span data-stu-id="dabc0-145">The `default` case is replaced with a `_` discard.</span></span>
- <span data-ttu-id="dabc0-146">Gövdeleri, değil deyimleri ifadelerdir.</span><span class="sxs-lookup"><span data-stu-id="dabc0-146">The bodies are expressions, not statements.</span></span>

<span data-ttu-id="dabc0-147">Klasik kullanarak eşdeğer kodla, Karşıtlık `switch` deyimi:</span><span class="sxs-lookup"><span data-stu-id="dabc0-147">Contrast that with the equivalent code using the classic `switch` statement:</span></span>

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

### <a name="property-patterns"></a><span data-ttu-id="dabc0-148">Özellik desenleri</span><span class="sxs-lookup"><span data-stu-id="dabc0-148">Property patterns</span></span>

<span data-ttu-id="dabc0-149">**Özelliği desenini** incelenirken nesnenin özellikleri eşleştirilecek sağlar.</span><span class="sxs-lookup"><span data-stu-id="dabc0-149">The **property pattern** enables you to match on properties of the object examined.</span></span> <span data-ttu-id="dabc0-150">Alıcının adresine göre vergi hesaplamanız gerekir bir e-ticaret sitesi göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="dabc0-150">Consider an eCommerce site that must compute sales tax based on the buyer's address.</span></span> <span data-ttu-id="dabc0-151">Hesaplama çekirdeği sorumluluğunda değil bir `Address` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="dabc0-151">That computation is not a core responsibility of an `Address` class.</span></span> <span data-ttu-id="dabc0-152">Zamanla, büyük olasılıkla adresi biçim değişikliklerini daha sık değişir.</span><span class="sxs-lookup"><span data-stu-id="dabc0-152">It will change over time, likely more often than address format changes.</span></span> <span data-ttu-id="dabc0-153">Vergi tutarı bağımlı `State` adresinin özelliği.</span><span class="sxs-lookup"><span data-stu-id="dabc0-153">The amount of sales tax depends on the `State` property of the address.</span></span> <span data-ttu-id="dabc0-154">Aşağıdaki yöntem özelliği desenini vergi adresi ve fiyat hesaplamak için kullanır:</span><span class="sxs-lookup"><span data-stu-id="dabc0-154">The following method uses the property pattern to compute the sales tax from the address and the price:</span></span>

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

<span data-ttu-id="dabc0-155">Desen eşleştirme bu algoritma ifade etmek için kısa bir söz dizimi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dabc0-155">Pattern matching creates a concise syntax for expressing this algorithm.</span></span>

### <a name="tuple-patterns"></a><span data-ttu-id="dabc0-156">Kayıt düzenleri</span><span class="sxs-lookup"><span data-stu-id="dabc0-156">Tuple patterns</span></span>

<span data-ttu-id="dabc0-157">Birden çok girişler bazı algoritmalar bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="dabc0-157">Some algorithms depend on multiple inputs.</span></span> <span data-ttu-id="dabc0-158">**Kayıt düzenleri** olarak ifade edilen birden çok değerlere göre geçiş yapmanıza izin bir [demet](../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="dabc0-158">**Tuple patterns** allow you to switch based on multiple values expressed as a [tuple](../tuples.md).</span></span>  <span data-ttu-id="dabc0-159">Aşağıdaki kod oyun için bir switch ifadesi gösterir *rock, inceleme, Makas*:</span><span class="sxs-lookup"><span data-stu-id="dabc0-159">The following code shows a switch expression for the game *rock, paper, scissors*:</span></span>

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

<span data-ttu-id="dabc0-160">Birinci iletileri gösterir.</span><span class="sxs-lookup"><span data-stu-id="dabc0-160">The messages indicate the winner.</span></span> <span data-ttu-id="dabc0-161">Atma durum TIES veya diğer metin girişi için üç birleşimleri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="dabc0-161">The discard case represents the three combinations for ties, or other text inputs.</span></span>

### <a name="positional-patterns"></a><span data-ttu-id="dabc0-162">Konumsal desenleri</span><span class="sxs-lookup"><span data-stu-id="dabc0-162">Positional patterns</span></span>

<span data-ttu-id="dabc0-163">Bazı türler bir `Deconstruct` özelliklerini ayrık değişkenlere deconstructs yöntemi.</span><span class="sxs-lookup"><span data-stu-id="dabc0-163">Some types include a `Deconstruct` method that deconstructs its properties into discrete variables.</span></span> <span data-ttu-id="dabc0-164">Olduğunda bir `Deconstruct` yöntemi erişilebilir, kullanabileceğiniz **konumsal desenleri** nesnenin özelliklerini inceleyin ve bu özellikler için bir düzen kullanın.</span><span class="sxs-lookup"><span data-stu-id="dabc0-164">When a `Deconstruct` method is accessible, you can use **positional patterns** to inspect properties of the object and use those properties for a pattern.</span></span>  <span data-ttu-id="dabc0-165">Aşağıdakileri göz önünde bulundurun `Point` içeren sınıf bir `Deconstruct` ayrık değişkenleri yöntemini `X` ve `Y`:</span><span class="sxs-lookup"><span data-stu-id="dabc0-165">Consider the following `Point` class that includes a `Deconstruct` method to create discrete variables for `X` and `Y`:</span></span>

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

<span data-ttu-id="dabc0-166">Aşağıdaki yöntemi kullanan **konumsal deseni** değerlerini ayıklamak için `x` ve `y`.</span><span class="sxs-lookup"><span data-stu-id="dabc0-166">The following method uses the **positional pattern** to extract the values of `x` and `y`.</span></span> <span data-ttu-id="dabc0-167">Ardından, kullanan bir `when` yan tümcesi noktasının quadrant belirlemek için:</span><span class="sxs-lookup"><span data-stu-id="dabc0-167">Then, it uses a `when` clause to determine the quadrant of the point:</span></span>

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

<span data-ttu-id="dabc0-168">Eşleşen atma deseni önceki anahtarda ya da `x` veya `y`, iki değil, 0'dır.</span><span class="sxs-lookup"><span data-stu-id="dabc0-168">The discard pattern in the preceding switch matches when either `x` or `y`, but not both, is 0.</span></span> <span data-ttu-id="dabc0-169">Bir switch ifadesi bir değer üreten veya bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="dabc0-169">A switch expression must either produce a value or throw an exception.</span></span> <span data-ttu-id="dabc0-170">Servis taleplerini hiçbiri eşleşen switch ifadesi bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dabc0-170">If none of the cases match, the switch expression throws an exception.</span></span> <span data-ttu-id="dabc0-171">Tüm olası durumların anahtar İfadenizde kapsamaz varsa derleyici bir uyarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dabc0-171">The compiler generates a warning for you if you do not cover all possible cases in your switch expression.</span></span>

## <a name="using-declarations"></a><span data-ttu-id="dabc0-172">Bildirimi kullanarak</span><span class="sxs-lookup"><span data-stu-id="dabc0-172">using declarations</span></span>

<span data-ttu-id="dabc0-173">A **using bildirimi** bir Değişken bildiriminde öncesinde `using` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="dabc0-173">A **using declaration** is a variable declaration preceded by the `using` keyword.</span></span> <span data-ttu-id="dabc0-174">Bu, derleyiciye bildirilen değişkenin kapsayan kapsamı sona atılmalıdır bildirir.</span><span class="sxs-lookup"><span data-stu-id="dabc0-174">It tells the compiler that the variable being declared should be disposed at the end of the enclosing scope.</span></span> <span data-ttu-id="dabc0-175">Örneğin, bir metin dosyasına yazan aşağıdaki kodu düşünün:</span><span class="sxs-lookup"><span data-stu-id="dabc0-175">For example, consider the following code that writes a text file:</span></span>

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

<span data-ttu-id="dabc0-176">Önceki örnekte, yöntemi için kapanış ayracı ulaşıldığında Dosya atıldı.</span><span class="sxs-lookup"><span data-stu-id="dabc0-176">In the preceding example, the file is disposed when the closing brace for the method is reached.</span></span> <span data-ttu-id="dabc0-177">Kapsamda sonuna olan `file` bildirilir.</span><span class="sxs-lookup"><span data-stu-id="dabc0-177">That's the end of the scope in which `file` is declared.</span></span> <span data-ttu-id="dabc0-178">Yukarıdaki kod, Klasik kullanarak aşağıdaki koda eşdeğerdir [using deyimlerini](../language-reference/keywords/using-statement.md) deyimi:</span><span class="sxs-lookup"><span data-stu-id="dabc0-178">The preceding code is equivalent to the following code using the classic [using statements](../language-reference/keywords/using-statement.md) statement:</span></span>


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

<span data-ttu-id="dabc0-179">Kapanış küme ayracı ile ilişkili olduğunda önceki örnekte, dosyanın elden `using` deyimine ulaşıldığında.</span><span class="sxs-lookup"><span data-stu-id="dabc0-179">In the preceding example, the file is disposed when the closing brace associated with the `using` statement is reached.</span></span>

<span data-ttu-id="dabc0-180">Her iki durumda da, derleyici çağrısı oluşturur `Dispose()`.</span><span class="sxs-lookup"><span data-stu-id="dabc0-180">In both cases, the compiler generates the call to `Dispose()`.</span></span> <span data-ttu-id="dabc0-181">Derleyici bir hata oluşturur kullanarak ifade deyimi atılabilir değil.</span><span class="sxs-lookup"><span data-stu-id="dabc0-181">The compiler generates an error if the expression in the using statement is not disposable.</span></span>

## <a name="static-local-functions"></a><span data-ttu-id="dabc0-182">Statik yerel işlevler</span><span class="sxs-lookup"><span data-stu-id="dabc0-182">Static local functions</span></span>

<span data-ttu-id="dabc0-183">Artık ekleyebilirsiniz `static` değiştiricisi yerel bu işlevi sağlamak için yerel işlevler için değil (başvuru) yakalama kapsayan kapsamdan gelen tüm değişkenler.</span><span class="sxs-lookup"><span data-stu-id="dabc0-183">You can now add the `static` modifier to local functions to ensure that local function doesn't capture (reference) any variables from the enclosing scope.</span></span> <span data-ttu-id="dabc0-184">Bunun yapılması oluşturur `CS8421`, "statik bir yerel işleve başvuru içeremez <variable>."</span><span class="sxs-lookup"><span data-stu-id="dabc0-184">Doing so generates `CS8421`, "A static local function can't contain a reference to <variable>."</span></span> 

<span data-ttu-id="dabc0-185">Aşağıdaki kodu düşünün.</span><span class="sxs-lookup"><span data-stu-id="dabc0-185">Consider the following code.</span></span> <span data-ttu-id="dabc0-186">Yerel işlev `LocalFunction` değişkeni erişen `y`kapsayan kapsamda bildirilen (yöntemi `M`).</span><span class="sxs-lookup"><span data-stu-id="dabc0-186">The local function `LocalFunction` accesses the variable `y`, declared in the enclosing scope (the method `M`).</span></span> <span data-ttu-id="dabc0-187">Bu nedenle, `LocalFunction` ile bildirilemez `static` değiştiricisi:</span><span class="sxs-lookup"><span data-stu-id="dabc0-187">Therefore, `LocalFunction` can't be declared with the `static` modifier:</span></span>

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

<span data-ttu-id="dabc0-188">Aşağıdaki kod, statik bir yerel işlev içerir.</span><span class="sxs-lookup"><span data-stu-id="dabc0-188">The following code contains a static local function.</span></span> <span data-ttu-id="dabc0-189">Tüm kapsayan kapsamda değişkenlere erişim yoktur çünkü statik olabilir:</span><span class="sxs-lookup"><span data-stu-id="dabc0-189">It can be static because it doesn't access any variables in the enclosing scope:</span></span>

```csharp
int M()
{
    int y = 5;
    int x = 7;
    return Add(x, y);

    static int Add(int left, int right) => left + right;
}
```

## <a name="disposable-ref-structs"></a><span data-ttu-id="dabc0-190">Atılabilir başvuru yapı birimleri</span><span class="sxs-lookup"><span data-stu-id="dabc0-190">Disposable ref structs</span></span>

<span data-ttu-id="dabc0-191">A `struct` ile bildirilen `ref` değiştiricisi hiçbir arabirim uygulayamaz ve bu nedenle uygulayamaz <xref:System.IDisposable>.</span><span class="sxs-lookup"><span data-stu-id="dabc0-191">A `struct` declared with the `ref` modifier may not implement any interfaces and so cannot implement <xref:System.IDisposable>.</span></span> <span data-ttu-id="dabc0-192">Bu nedenle, etkinleştirmek için bir `ref struct` çıkarılması için bunu bir erişilebilir olmalıdır `void Dispose()` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="dabc0-192">Therefore, to enable a `ref struct` to be disposed, it must have an accessible `void Dispose()` method.</span></span> <span data-ttu-id="dabc0-193">Bu durum için de geçerlidir `readonly ref struct` bildirimleri.</span><span class="sxs-lookup"><span data-stu-id="dabc0-193">This also applies to `readonly ref struct` declarations.</span></span>

## <a name="nullable-reference-types"></a><span data-ttu-id="dabc0-194">Null başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="dabc0-194">Nullable reference types</span></span>

<span data-ttu-id="dabc0-195">Boş değer atanabilir bir ek açıklama bir bağlam içinde bir başvuru türünün herhangi bir değişken olarak kabul edilir bir **nonnullable başvuru türü**.</span><span class="sxs-lookup"><span data-stu-id="dabc0-195">Inside a nullable annotation context, any variable of a reference type is considered to be a **nonnullable reference type**.</span></span> <span data-ttu-id="dabc0-196">Bir değişken null olabilir belirtmek istiyorsanız, tür adıyla ekleme `?` değişken olarak bildirmek için bir **boş değer atanabilir bir başvuru türü**.</span><span class="sxs-lookup"><span data-stu-id="dabc0-196">If you want to indicate that a variable may be null, you must append the type name with the `?` to declare the variable as a **nullable reference type**.</span></span>

<span data-ttu-id="dabc0-197">Nonnullable başvuru türleri için derleyici yerel değişkenler bir null olmayan değer bildirildiğinde başlatılır emin olmak için akış analizini kullanır.</span><span class="sxs-lookup"><span data-stu-id="dabc0-197">For nonnullable reference types, the compiler uses flow analysis to ensure that local variables are initialized to a non-null value when declared.</span></span> <span data-ttu-id="dabc0-198">Oluşturma sırasında alanları yeniden başlatılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="dabc0-198">Fields must be initialized during construction.</span></span> <span data-ttu-id="dabc0-199">Değişkeni bir başlatıcıya veya kullanılabilir oluşturucular herhangi bir çağrı tarafından ayarlanmamışsa, derleyici bir uyarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dabc0-199">The compiler generates a warning if the variable is not set by a call to any of the available constructors or by an initializer.</span></span> <span data-ttu-id="dabc0-200">Ayrıca, nonnullable başvuru türleri null olabilir bir değer atanamaz.</span><span class="sxs-lookup"><span data-stu-id="dabc0-200">Furthermore, nonnullable reference types can't be assigned a value that could be null.</span></span>

<span data-ttu-id="dabc0-201">Null başvuru türlerine atanan olmayan veya null'a emin olmak için denetlenmez.</span><span class="sxs-lookup"><span data-stu-id="dabc0-201">Nullable reference types aren't checked to ensure they aren't assigned or initialized to null.</span></span> <span data-ttu-id="dabc0-202">Ancak derleyici, erişilen veya nonnullable başvuru türüne atanan önce herhangi bir değişken bir boş değer atanabilir bir başvuru türünün null karşı seçeneğinin işaretli olduğundan emin olmak için akış analizini kullanır.</span><span class="sxs-lookup"><span data-stu-id="dabc0-202">However, the compiler uses flow analysis to ensure that any variable of a nullable reference type is checked against null before it's accessed or assigned to a nonnullable reference type.</span></span>

<span data-ttu-id="dabc0-203">Genel Bakış özelliği hakkında daha fazla bilgi [null başvuru türleri](../nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="dabc0-203">You can learn more about the feature in the overview of [nullable reference types](../nullable-references.md).</span></span> <span data-ttu-id="dabc0-204">Bu yeni bir uygulamada kendiniz denemek [null başvuru türleri öğretici](../tutorials/nullable-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="dabc0-204">Try it yourself in a new application in this [nullable reference types tutorial](../tutorials/nullable-reference-types.md).</span></span> <span data-ttu-id="dabc0-205">Hakkında bilgi edinin yapmak için var olan bir geçiş adımlarını codebase null başvuru türlerinde kullanımı [öğretici türleri null yapılabilir başvurusu kullanmak için bir uygulamayı geçirme](../tutorials/upgrade-to-nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="dabc0-205">Learn about the steps to migrate an existing codebase to make use of nullable reference types in the [migrating an application to use nullable reference types tutorial](../tutorials/upgrade-to-nullable-references.md).</span></span>

## <a name="asynchronous-streams"></a><span data-ttu-id="dabc0-206">Zaman uyumsuz akışlar</span><span class="sxs-lookup"><span data-stu-id="dabc0-206">Asynchronous streams</span></span>

<span data-ttu-id="dabc0-207">İle başlayarak C# 8.0, oluşturabilir ve akışları zaman uyumsuz olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="dabc0-207">Starting with C# 8.0, you can create and consume streams asynchronously.</span></span> <span data-ttu-id="dabc0-208">Zaman uyumsuz bir akışa döndüren bir yöntem üç özelliğe sahiptir:</span><span class="sxs-lookup"><span data-stu-id="dabc0-208">A method that returns an asynchronous stream has three properties:</span></span>

1. <span data-ttu-id="dabc0-209">İle bildirildi `async` değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="dabc0-209">It was declared with the `async` modifier.</span></span>
1. <span data-ttu-id="dabc0-210">Döndürür bir <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="dabc0-210">It returns an <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span></span>
1. <span data-ttu-id="dabc0-211">Contains yöntemi `yield return` deyimleri zaman uyumsuz akışın ardışık öğeleri döndürmek için.</span><span class="sxs-lookup"><span data-stu-id="dabc0-211">The method contains `yield return` statements to return successive elements in the asynchronous stream.</span></span>

<span data-ttu-id="dabc0-212">Zaman uyumsuz bir akışa kullanma, gerektirir eklemeyi `await` anahtar sözcüğünün önüne `foreach` akış öğelerini numaralandırıldığında anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="dabc0-212">Consuming an asynchronous stream requires you to add the `await` keyword before the `foreach` keyword when you enumerate the elements of the stream.</span></span> <span data-ttu-id="dabc0-213">Ekleme `await` anahtar sözcüğü ile bildirilen zaman uyumsuz akış numaralandırır yöntemi gerektiren `async` değiştiricisi ve bir tür için izin verilecek bir `async` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="dabc0-213">Adding the `await` keyword requires the method that enumerates the asynchronous stream to be declared with the `async` modifier and to return a type allowed for an `async` method.</span></span> <span data-ttu-id="dabc0-214">Genellikle döndüren anlamına bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="dabc0-214">Typically that means returning a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="dabc0-215">Ayrıca olabilir bir <xref:System.Threading.Tasks.ValueTask> veya <xref:System.Threading.Tasks.ValueTask%601>.</span><span class="sxs-lookup"><span data-stu-id="dabc0-215">It can also be a <xref:System.Threading.Tasks.ValueTask> or <xref:System.Threading.Tasks.ValueTask%601>.</span></span> <span data-ttu-id="dabc0-216">Bir yöntem hem kullanabilir ve şunu döndürür anlamına gelir zaman uyumsuz bir akışa üreten bir <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="dabc0-216">A method can both consume and produce an asynchronous stream, which means it would return an <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span></span> <span data-ttu-id="dabc0-217">Aşağıdaki kod, her bir sayının oluşturma arasında 100 ms bekleniyor 20 1'den bir sıra üretir:</span><span class="sxs-lookup"><span data-stu-id="dabc0-217">The following code generates a sequence from 1 to 20, waiting 100 ms between generating each number:</span></span>

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

<span data-ttu-id="dabc0-218">Dizisi kullanarak listeleme `await foreach` deyimi:</span><span class="sxs-lookup"><span data-stu-id="dabc0-218">You would enumerate the sequence using the `await foreach` statement:</span></span>

```csharp
await foreach (var number in GenerateSequence())
{
    Console.WriteLine(number);
}
```

<span data-ttu-id="dabc0-219">Zaman uyumsuz akışlar kendiniz müşterilerimize öğreticide deneyebilirsiniz [oluşturma ve zaman uyumsuz akışlar tüketen](../tutorials/generate-consume-asynchronous-stream.md).</span><span class="sxs-lookup"><span data-stu-id="dabc0-219">You can try asynchronous streams yourself in our tutorial on [creating and consuming async streams](../tutorials/generate-consume-asynchronous-stream.md).</span></span>

## <a name="indices-and-ranges"></a><span data-ttu-id="dabc0-220">Dizinleri ve aralıkları</span><span class="sxs-lookup"><span data-stu-id="dabc0-220">Indices and ranges</span></span>

<span data-ttu-id="dabc0-221">Aralıkları ve dizinlerini sağlayan bir kısa sözdizimleri bir dizi içinde alt aralıklara belirtmek için <xref:System.Span%601>, veya <xref:System.ReadOnlySpan%601>.</span><span class="sxs-lookup"><span data-stu-id="dabc0-221">Ranges and indices provide a succinct syntax for specifying subranges in an array, <xref:System.Span%601>, or <xref:System.ReadOnlySpan%601>.</span></span>

<span data-ttu-id="dabc0-222">Dizin belirtebilirsiniz **sonundan**.</span><span class="sxs-lookup"><span data-stu-id="dabc0-222">You can specify an index **from the end**.</span></span> <span data-ttu-id="dabc0-223">Belirttiğiniz **sonundan** kullanarak `^` işleci.</span><span class="sxs-lookup"><span data-stu-id="dabc0-223">You specify **from the end** using the `^` operator.</span></span> <span data-ttu-id="dabc0-224">Bilginiz `array[2]` öğe "başından itibaren 2" anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="dabc0-224">You are familiar with `array[2]` meaning the element "2 from the start".</span></span> <span data-ttu-id="dabc0-225">Şimdi, `array[^2]` öğe "2 sonundan" anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="dabc0-225">Now, `array[^2]` means the element "2 from the end".</span></span> <span data-ttu-id="dabc0-226">Dizin `^0` "Bitiş" ya da son öğeyi izleyen dizini anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="dabc0-226">The index `^0` means "the end", or the index that follows the last element.</span></span>

<span data-ttu-id="dabc0-227">Belirtebileceğiniz bir **aralığı** ile **aralık işleci**: `..`.</span><span class="sxs-lookup"><span data-stu-id="dabc0-227">You can specify a **range** with the **range operator**: `..`.</span></span> <span data-ttu-id="dabc0-228">Örneğin, `0..^0` dizi aralığının tamamı belirtir: 0'ın başından itibaren en fazla, ancak son 0 dahil değil.</span><span class="sxs-lookup"><span data-stu-id="dabc0-228">For example, `0..^0` specifies the entire range of the array: 0 from the start up to, but not including 0 from the end.</span></span> <span data-ttu-id="dabc0-229">İki işlenenden "Başlangıç" veya "sonuna" kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="dabc0-229">Either operand may use "from the start" or "from the end".</span></span> <span data-ttu-id="dabc0-230">Ayrıca, iki işlenenden atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="dabc0-230">Furthermore, either operand may be omitted.</span></span> <span data-ttu-id="dabc0-231">Varsayılanlar `0` başlangıç dizini ve `^0` son dizini.</span><span class="sxs-lookup"><span data-stu-id="dabc0-231">The defaults are `0` for the start index, and `^0` for the end index.</span></span>

<span data-ttu-id="dabc0-232">Bazı örneklere bakalım.</span><span class="sxs-lookup"><span data-stu-id="dabc0-232">Let's look at a few examples.</span></span> <span data-ttu-id="dabc0-233">Aşağıdaki dizinin başından ve sonundan dizinini ile açıklanan göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="dabc0-233">Consider the following array, annotated with its index from the start and from the end:</span></span>

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

<span data-ttu-id="dabc0-234">Her öğenin dizini "Başlat" ve "Kimden"son kavramı güçlendirir ve aralığın sonunu fiyatlara aralıktır.</span><span class="sxs-lookup"><span data-stu-id="dabc0-234">The index of each element reinforces the concept of "from the start", and "from the end", and that ranges are exclusive of the end of the range.</span></span> <span data-ttu-id="dabc0-235">"Başlangıç" tüm dizinin ilk öğedir.</span><span class="sxs-lookup"><span data-stu-id="dabc0-235">The "start" of the entire array is the first element.</span></span> <span data-ttu-id="dabc0-236">Tüm dizi "End" *geçmiş* son öğe.</span><span class="sxs-lookup"><span data-stu-id="dabc0-236">The "end" of the entire array is *past* the last element.</span></span>

<span data-ttu-id="dabc0-237">Son sözcüğü alabilirsiniz `^1` dizini:</span><span class="sxs-lookup"><span data-stu-id="dabc0-237">You can retrieve the last word with the `^1` index:</span></span>

```csharp
Console.WriteLine($"The last word is {words[^1]}");
// writes "dog"
```

<span data-ttu-id="dabc0-238">Aşağıdaki kod, bir alt aralığı sözcükler "Hızlı", "brown" ile ve "fox" oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dabc0-238">The following code creates a subrange with the words "quick", "brown", and "fox".</span></span> <span data-ttu-id="dabc0-239">İçerdiği `words[1]` aracılığıyla `words[3]`.</span><span class="sxs-lookup"><span data-stu-id="dabc0-239">It includes `words[1]` through `words[3]`.</span></span> <span data-ttu-id="dabc0-240">Öğe `words[4]` aralığında değil.</span><span class="sxs-lookup"><span data-stu-id="dabc0-240">The element `words[4]` is not in the range.</span></span>

```csharp
var brownFox = words[1..4];
```

<span data-ttu-id="dabc0-241">Aşağıdaki kod, "geç" ve "köpek" alt oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dabc0-241">The following code creates a subrange with "lazy" and "dog".</span></span> <span data-ttu-id="dabc0-242">İçerdiği `words[^2]` ve `words[^1]`.</span><span class="sxs-lookup"><span data-stu-id="dabc0-242">It includes `words[^2]` and `words[^1]`.</span></span> <span data-ttu-id="dabc0-243">Bitiş dizini `words[^0]` dahil edilmez:</span><span class="sxs-lookup"><span data-stu-id="dabc0-243">The end index `words[^0]` is not included:</span></span>

```csharp
var lazyDog = words[^2..^0];
```

<span data-ttu-id="dabc0-244">Aşağıdaki örnekler, açık olan başında, sonunda ya da her ikisi için bitiş aralıkları oluşturur:</span><span class="sxs-lookup"><span data-stu-id="dabc0-244">The following examples create ranges that are open ended for the start, end, or both:</span></span>

```csharp
var allWords = words[..]; // contains "The" through "dog".
var firstPhrase = words[..4]; // contains "The" through "fox"
var lastPhrase = words[6..]; // contains "the, "lazy" and "dog"
```

<span data-ttu-id="dabc0-245">De aralık değişkenleri olarak bildirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="dabc0-245">You can also declare ranges as variables:</span></span>

```csharp
Range phrase = 1..4;
```

<span data-ttu-id="dabc0-246">Aralık içinde sonra kullanılabilir `[` ve `]` karakter:</span><span class="sxs-lookup"><span data-stu-id="dabc0-246">The range can then be used inside the `[` and `]` characters:</span></span>

```csharp
var text = words[phrase];
```
