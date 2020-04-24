---
title: Koleksiyonlar (C#)
ms.date: 07/20/2015
ms.assetid: 317d7dc3-8587-4873-8b3e-556f86497939
ms.openlocfilehash: d2996648690fc03b5f1d6a90e0be96155c5a24ed
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645476"
---
# <a name="collections-c"></a>Koleksiyonlar (C#)

Birçok uygulama için, ilgili nesnelerin grupları oluşturmak ve yönetmek istiyorsunuz. Nesneleri gruplandırmanın iki yolu vardır: nesne dizileri oluşturarak ve nesnelerin koleksiyonlarını oluşturarak.

Diziler, güçlü bir şekilde yazılan sabit sayıda nesne oluşturmak ve bunlarla çalışmak için en kullanışlıdır. Diziler hakkında daha fazla bilgi için [Diziler'e](../arrays/index.md)bakın.

Koleksiyonlar, nesne gruplarıyla çalışmak için daha esnek bir yol sağlar. Dizilerin aksine, birlikte çalıştığınız nesne grubu, uygulamanın gereksinimleri değiştikçe dinamik olarak büyüyebilir ve küçülebilir. Bazı koleksiyonlar için, anahtarı kullanarak nesneyi hızla alabilmeniz için koleksiyona koyduğunuz herhangi bir nesneye bir anahtar atayabilirsiniz.

Koleksiyon bir sınıftır, bu nedenle bu koleksiyona öğe eklemeden önce sınıfın bir örneğini bildirmeniz gerekir.

Koleksiyonunuz yalnızca bir veri türüöğeleri içeriyorsa, <xref:System.Collections.Generic?displayProperty=nameWithType> ad alanındaki sınıflardan birini kullanabilirsiniz. Genel bir koleksiyon, türü başka bir veri türünün eklenmeyecek şekilde tür güvenliğini zorlar. Genel bir koleksiyondan bir öğe aldığınızda, öğe türünü belirlemeniz veya dönüştürmeniz gerekmez.

> [!NOTE]
> Bu konudaki örnekler için, ve `System.Linq` ad `System.Collections.Generic` alanları için yönergeleri [niçin kullanma](../../language-reference/keywords/using-directive.md) içerir.

 **Bu konuda**

- [Basit Bir Koleksiyon Kullanma](#BKMK_SimpleCollection)

- [Koleksiyon Çeşitleri](#BKMK_KindsOfCollections)

  - [System.Collections.Generic Sınıflar](#BKMK_Generic)

  - [System.Collections.Eşzamanlı Sınıflar](#BKMK_Concurrent)

  - [System.Collections Sınıfları](#BKMK_Collections)

- [Anahtar/Değer Çiftleri Koleksiyonunu Uygulama](#BKMK_KeyValuePairs)

- [Koleksiyona Erişmek için LINQ kullanma](#BKMK_LINQ)

- [Koleksiyonu Sıralama](#BKMK_Sorting)

- [Özel Koleksiyon Tanımlama](#BKMK_CustomCollection)

- [Yineleyiciler](#BKMK_Iterators)

<a name="BKMK_SimpleCollection"></a>

## <a name="using-a-simple-collection"></a>Basit Bir Koleksiyon Kullanma

Bu bölümdeki örnekler, <xref:System.Collections.Generic.List%601> güçlü bir şekilde yazılan nesneler listesiyle çalışmanızı sağlayan genel sınıfı kullanır.

Aşağıdaki örnek, dizeleri bir listesini oluşturur ve sonra [foreach](../../language-reference/keywords/foreach-in.md) deyimi kullanarak dizeleri ile yineler.

```csharp
// Create a list of strings.
var salmons = new List<string>();
salmons.Add("chinook");
salmons.Add("coho");
salmons.Add("pink");
salmons.Add("sockeye");

// Iterate through the list.
foreach (var salmon in salmons)
{
    Console.Write(salmon + " ");
}
// Output: chinook coho pink sockeye
```

Bir koleksiyonun içeriği önceden biliniyorsa, koleksiyonun başlatılması için bir *koleksiyon başlatılması* nı kullanabilirsiniz. Daha fazla bilgi için [Object ve Collection Initializers'a](../classes-and-structs/object-and-collection-initializers.md)bakın.

Aşağıdaki örnek, koleksiyona öğe eklemek için bir koleksiyon başlatılması nın kullanılması dışında, önceki örnekle aynıdır.

```csharp
// Create a list of strings by using a
// collection initializer.
var salmons = new List<string> { "chinook", "coho", "pink", "sockeye" };

// Iterate through the list.
foreach (var salmon in salmons)
{
    Console.Write(salmon + " ");
}
// Output: chinook coho pink sockeye
```

[Bir](../../language-reference/keywords/for.md) koleksiyon aracılığıyla yinelemek `foreach` için deyim yerine for deyimi kullanabilirsiniz. Bunu dizin konumuna göre koleksiyon öğelerine erişerek gerçekleştirirsiniz. Elementlerin dizini 0 ile başlar ve eksi 1 öğe sayısıyla biter.

Aşağıdaki örnek, bir koleksiyonun öğelerini yerine `for` kullanarak `foreach`yineler.

```csharp
// Create a list of strings by using a
// collection initializer.
var salmons = new List<string> { "chinook", "coho", "pink", "sockeye" };

for (var index = 0; index < salmons.Count; index++)
{
    Console.Write(salmons[index] + " ");
}
// Output: chinook coho pink sockeye
```

Aşağıdaki örnek, kaldırılacak nesneyi belirterek bir öğeyi koleksiyondan kaldırır.

```csharp
// Create a list of strings by using a
// collection initializer.
var salmons = new List<string> { "chinook", "coho", "pink", "sockeye" };

// Remove an element from the list by specifying
// the object.
salmons.Remove("coho");

// Iterate through the list.
foreach (var salmon in salmons)
{
    Console.Write(salmon + " ");
}
// Output: chinook pink sockeye
```

Aşağıdaki örnek, öğeleri genel bir listeden kaldırır. Bir `foreach` deyim yerine, azalan sırada yineleyen [bir](../../language-reference/keywords/for.md) ifade kullanılır. Bunun nedeni, <xref:System.Collections.Generic.List%601.RemoveAt%2A> yöntemin kaldırılan öğeden sonraki öğelerin daha düşük bir dizin değerine sahip olmasıdır.

```csharp
var numbers = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };

// Remove odd numbers.
for (var index = numbers.Count - 1; index >= 0; index--)
{
    if (numbers[index] % 2 == 1)
    {
        // Remove the element by specifying
        // the zero-based index in the list.
        numbers.RemoveAt(index);
    }
}

// Iterate through the list.
// A lambda expression is placed in the ForEach method
// of the List(T) object.
numbers.ForEach(
    number => Console.Write(number + " "));
// Output: 0 2 4 6 8
```

Öğelerin türü <xref:System.Collections.Generic.List%601>için, kendi sınıf tanımlayabilirsiniz. Aşağıdaki örnekte, `Galaxy` kodda <xref:System.Collections.Generic.List%601> kullanılan sınıf tanımlanır.

```csharp
private static void IterateThroughList()
{
    var theGalaxies = new List<Galaxy>
        {
            new Galaxy() { Name="Tadpole", MegaLightYears=400},
            new Galaxy() { Name="Pinwheel", MegaLightYears=25},
            new Galaxy() { Name="Milky Way", MegaLightYears=0},
            new Galaxy() { Name="Andromeda", MegaLightYears=3}
        };

    foreach (Galaxy theGalaxy in theGalaxies)
    {
        Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears);
    }

    // Output:
    //  Tadpole  400
    //  Pinwheel  25
    //  Milky Way  0
    //  Andromeda  3
}

public class Galaxy
{
    public string Name { get; set; }
    public int MegaLightYears { get; set; }
}
```

<a name="BKMK_KindsOfCollections"></a>

## <a name="kinds-of-collections"></a>Koleksiyon Çeşitleri

Birçok ortak koleksiyon .NET Framework tarafından sağlanır. Her koleksiyon türü belirli bir amaç için tasarlanmıştır.

Ortak toplama sınıflarından bazıları bu bölümde açıklanmıştır:

- <xref:System.Collections.Generic> sınıflar

- <xref:System.Collections.Concurrent> sınıflar

- <xref:System.Collections> sınıflar

<a name="BKMK_Generic"></a>

### <a name="systemcollectionsgeneric-classes"></a>System.Collections.Generic Sınıflar

<xref:System.Collections.Generic> Ad alanındaki sınıflardan birini kullanarak genel bir koleksiyon oluşturabilirsiniz. Genel bir koleksiyon, koleksiyondaki her öğe aynı veri türüne sahipse yararlıdır. Genel bir koleksiyon, yalnızca istenen veri türünün eklenmesine izin vererek güçlü yazmayı zorlar.

Aşağıdaki tabloda ad alanının sık kullanılan <xref:System.Collections.Generic?displayProperty=nameWithType> sınıflarından bazıları listelenebvardır:

|Sınıf|Açıklama|
|---|---|
|<xref:System.Collections.Generic.Dictionary%602>|Anahtara göre düzenlenmiş anahtar/değer çiftleri koleksiyonunu temsil eder.|
|<xref:System.Collections.Generic.List%601>|Dizin tarafından erişilebilen nesnelerin listesini temsil eder. Listeleri aramak, sıralamak ve değiştirmek için yöntemler sağlar.|
|<xref:System.Collections.Generic.Queue%601>|Nesnelerin ilk, ilk çıkan (FIFO) koleksiyonunu temsil eder.|
|<xref:System.Collections.Generic.SortedList%602>|İlişkili <xref:System.Collections.Generic.IComparer%601> uygulamaya göre anahtara göre sıralanmış anahtar/değer çiftleri koleksiyonunu temsil eder.|
|<xref:System.Collections.Generic.Stack%601>|Nesnelerin son, ilk çıkan (LIFO) koleksiyonunu temsil eder.|

Ek bilgi için, [Sık Kullanılan Koleksiyon Türleri](../../../standard/collections/commonly-used-collection-types.md), Toplama Sınıfı [Seçme](../../../standard/collections/selecting-a-collection-class.md)ve <xref:System.Collections.Generic>.

<a name="BKMK_Concurrent"></a>

### <a name="systemcollectionsconcurrent-classes"></a>System.Collections.Eşzamanlı Sınıflar

.NET Framework 4 veya daha yeni, <xref:System.Collections.Concurrent> ad alanındaki koleksiyonlar, birden çok iş parçacığından koleksiyon öğelerine erişmek için verimli iş parçacığı güvenli işlemler sağlar.

<xref:System.Collections.Concurrent> Birden çok iş parçacığı aynı anda koleksiyona <xref:System.Collections.Generic?displayProperty=nameWithType> erişirken ad alanında ve <xref:System.Collections?displayProperty=nameWithType> ad alanlarındaki karşılık gelen türler yerine ad alanındaki sınıflar kullanılmalıdır. Daha fazla bilgi için İş Parçacığı <xref:System.Collections.Concurrent>Güvenli [Koleksiyonları](../../../standard/collections/thread-safe/index.md) ve .

<xref:System.Collections.Concurrent> Ad alanına dahil edilen bazı <xref:System.Collections.Concurrent.BlockingCollection%601> <xref:System.Collections.Concurrent.ConcurrentDictionary%602>sınıflar <xref:System.Collections.Concurrent.ConcurrentQueue%601>, <xref:System.Collections.Concurrent.ConcurrentStack%601>, , ve .

<a name="BKMK_Collections"></a>

### <a name="systemcollections-classes"></a>System.Collections Sınıfları

<xref:System.Collections?displayProperty=nameWithType> Ad alanındaki sınıflar öğeleri özel olarak yazılan nesneler olarak değil, tür `Object`nesneleri olarak depolar.

Mümkün olduğunda, <xref:System.Collections.Generic?displayProperty=nameWithType> <xref:System.Collections.Concurrent> `System.Collections` ad alanındaki eski türler yerine ad alanında veya ad alanında genel koleksiyonları kullanmanız gerekir.

Aşağıdaki tabloda ad alanında sık kullanılan `System.Collections` sınıflardan bazıları listelenemektedir:

|Sınıf|Açıklama|
|---|---|
|<xref:System.Collections.ArrayList>|Boyutu gerektiği gibi dinamik olarak artırılmış bir nesne dizisini temsil eder.|
|<xref:System.Collections.Hashtable>|Anahtarın karma koduna göre düzenlenen anahtar/değer çiftleri koleksiyonunu temsil eder.|
|<xref:System.Collections.Queue>|Nesnelerin ilk, ilk çıkan (FIFO) koleksiyonunu temsil eder.|
|<xref:System.Collections.Stack>|Nesnelerin son, ilk çıkan (LIFO) koleksiyonunu temsil eder.|

Ad <xref:System.Collections.Specialized> alanı, yalnızca dize koleksiyonları ve bağlantılı liste ve karma sözlükler gibi özel ve güçlü bir şekilde yazılan koleksiyon sınıfları sağlar.

<a name="BKMK_KeyValuePairs"></a>

## <a name="implementing-a-collection-of-keyvalue-pairs"></a>Anahtar/Değer Çiftleri Koleksiyonunu Uygulama

Genel <xref:System.Collections.Generic.Dictionary%602> koleksiyon, her öğenin anahtarını kullanarak koleksiyondaki öğelere erişmenizi sağlar. Sözlükteki her ek bir değer ve ilişkili anahtardan oluşur. `Dictionary` Sınıf karma tablo olarak uygulandığından, anahtarını kullanarak bir değer almak hızlıdır.

Aşağıdaki örnek bir `Dictionary` koleksiyon oluşturur ve bir `foreach` deyim kullanarak sözlük teyidi.

```csharp
private static void IterateThruDictionary()
{
    Dictionary<string, Element> elements = BuildDictionary();

    foreach (KeyValuePair<string, Element> kvp in elements)
    {
        Element theElement = kvp.Value;

        Console.WriteLine("key: " + kvp.Key);
        Console.WriteLine("values: " + theElement.Symbol + " " +
            theElement.Name + " " + theElement.AtomicNumber);
    }
}

private static Dictionary<string, Element> BuildDictionary()
{
    var elements = new Dictionary<string, Element>();

    AddToDictionary(elements, "K", "Potassium", 19);
    AddToDictionary(elements, "Ca", "Calcium", 20);
    AddToDictionary(elements, "Sc", "Scandium", 21);
    AddToDictionary(elements, "Ti", "Titanium", 22);

    return elements;
}

private static void AddToDictionary(Dictionary<string, Element> elements,
    string symbol, string name, int atomicNumber)
{
    Element theElement = new Element();

    theElement.Symbol = symbol;
    theElement.Name = name;
    theElement.AtomicNumber = atomicNumber;

    elements.Add(key: theElement.Symbol, value: theElement);
}

public class Element
{
    public string Symbol { get; set; }
    public string Name { get; set; }
    public int AtomicNumber { get; set; }
}
```

Bunun `Dictionary` yerine, koleksiyonu oluşturmak için bir koleksiyon baş `BuildDictionary` harflerini kullanmak için, aşağıdaki yöntemle ve `AddToDictionary` yöntemleri değiştirebilirsiniz.

```csharp
private static Dictionary<string, Element> BuildDictionary2()
{
    return new Dictionary<string, Element>
    {
        {"K",
            new Element() { Symbol="K", Name="Potassium", AtomicNumber=19}},
        {"Ca",
            new Element() { Symbol="Ca", Name="Calcium", AtomicNumber=20}},
        {"Sc",
            new Element() { Symbol="Sc", Name="Scandium", AtomicNumber=21}},
        {"Ti",
            new Element() { Symbol="Ti", Name="Titanium", AtomicNumber=22}}
    };
}
```

Aşağıdaki örnekte, <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> bir <xref:System.Collections.Generic.Dictionary%602.Item%2A> öğeyi `Dictionary` anahtarla hızlı bir şekilde bulmak için yöntem ve özellik kullanır. Özellik, `Item` `elements` `elements[symbol]` c#'daki öğeyi kullanarak koleksiyondaki bir öğeye erişmenizi sağlar.

```csharp
private static void FindInDictionary(string symbol)
{
    Dictionary<string, Element> elements = BuildDictionary();

    if (elements.ContainsKey(symbol) == false)
    {
        Console.WriteLine(symbol + " not found");
    }
    else
    {
        Element theElement = elements[symbol];
        Console.WriteLine("found: " + theElement.Name);
    }
}
```

Aşağıdaki örnek yerine <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> yöntemi hızlı bir şekilde anahtara göre bir öğe bulmak kullanır.

```csharp
private static void FindInDictionary2(string symbol)
{
    Dictionary<string, Element> elements = BuildDictionary();

    Element theElement = null;
    if (elements.TryGetValue(symbol, out theElement) == false)
        Console.WriteLine(symbol + " not found");
    else
        Console.WriteLine("found: " + theElement.Name);
}
```

<a name="BKMK_LINQ"></a>

## <a name="using-linq-to-access-a-collection"></a>Koleksiyona Erişmek için LINQ kullanma

LINQ (Dil-Tümleşik Sorgu) koleksiyonlara erişmek için kullanılabilir. LINQ sorguları filtreleme, sıralama ve gruplandırma özellikleri sağlar. Daha fazla bilgi için [C# içinde LINQ ile Başlarken'e](linq/index.md)bakın.

Aşağıdaki örnek, genel `List`bir karşı bir LINQ sorgusu çalıştırın. LINQ sorgusu sonuçları içeren farklı bir koleksiyon döndürür.

```csharp
private static void ShowLINQ()
{
    List<Element> elements = BuildList();

    // LINQ Query.
    var subset = from theElement in elements
                 where theElement.AtomicNumber < 22
                 orderby theElement.Name
                 select theElement;

    foreach (Element theElement in subset)
    {
        Console.WriteLine(theElement.Name + " " + theElement.AtomicNumber);
    }

    // Output:
    //  Calcium 20
    //  Potassium 19
    //  Scandium 21
}

private static List<Element> BuildList()
{
    return new List<Element>
    {
        { new Element() { Symbol="K", Name="Potassium", AtomicNumber=19}},
        { new Element() { Symbol="Ca", Name="Calcium", AtomicNumber=20}},
        { new Element() { Symbol="Sc", Name="Scandium", AtomicNumber=21}},
        { new Element() { Symbol="Ti", Name="Titanium", AtomicNumber=22}}
    };
}

public class Element
{
    public string Symbol { get; set; }
    public string Name { get; set; }
    public int AtomicNumber { get; set; }
}
```

<a name="BKMK_Sorting"></a>

## <a name="sorting-a-collection"></a>Koleksiyonu Sıralama

Aşağıdaki örnek, bir koleksiyonu sıralama yordamını göstermektedir. Örnek, bir <xref:System.Collections.Generic.List%601>' `Car` de depolanan sınıfın örneklerini sıralar Sınıf, `Car` yöntemin <xref:System.IComparable%601> <xref:System.IComparable%601.CompareTo%2A> uygulanmasını gerektiren arabirimi uygular.

Yönteme <xref:System.IComparable%601.CompareTo%2A> yapılan her çağrı, sıralama için kullanılan tek bir karşılaştırma yapar. `CompareTo` Yöntemdeki kullanıcı tarafından yazılan kod, geçerli nesnenin başka bir nesneyle her karşılaştırılması için bir değer döndürür. Dönen değer, geçerli nesne diğer nesneden küçükse, geçerli nesne diğer nesneden büyükse sıfırdan büyük, eşitse sıfırdır. Bu, kodda daha büyük, daha az ve eşit ölçütleri tanımlamanızı sağlar.

`ListCars` Yöntemde, `cars.Sort()` deyim listeyi sıralar. Bu çağrı <xref:System.Collections.Generic.List%601.Sort%2A> yöntemine <xref:System.Collections.Generic.List%601> neden `CompareTo` olan `Car` yöntemin `List`nesneler için otomatik olarak çağrılması.

```csharp
private static void ListCars()
{
    var cars = new List<Car>
    {
        { new Car() { Name = "car1", Color = "blue", Speed = 20}},
        { new Car() { Name = "car2", Color = "red", Speed = 50}},
        { new Car() { Name = "car3", Color = "green", Speed = 10}},
        { new Car() { Name = "car4", Color = "blue", Speed = 50}},
        { new Car() { Name = "car5", Color = "blue", Speed = 30}},
        { new Car() { Name = "car6", Color = "red", Speed = 60}},
        { new Car() { Name = "car7", Color = "green", Speed = 50}}
    };

    // Sort the cars by color alphabetically, and then by speed
    // in descending order.
    cars.Sort();

    // View all of the cars.
    foreach (Car thisCar in cars)
    {
        Console.Write(thisCar.Color.PadRight(5) + " ");
        Console.Write(thisCar.Speed.ToString() + " ");
        Console.Write(thisCar.Name);
        Console.WriteLine();
    }

    // Output:
    //  blue  50 car4
    //  blue  30 car5
    //  blue  20 car1
    //  green 50 car7
    //  green 10 car3
    //  red   60 car6
    //  red   50 car2
}

public class Car : IComparable<Car>
{
    public string Name { get; set; }
    public int Speed { get; set; }
    public string Color { get; set; }

    public int CompareTo(Car other)
    {
        // A call to this method makes a single comparison that is
        // used for sorting.

        // Determine the relative order of the objects being compared.
        // Sort by color alphabetically, and then by speed in
        // descending order.

        // Compare the colors.
        int compare;
        compare = String.Compare(this.Color, other.Color, true);

        // If the colors are the same, compare the speeds.
        if (compare == 0)
        {
            compare = this.Speed.CompareTo(other.Speed);

            // Use descending order for speed.
            compare = -compare;
        }

        return compare;
    }
}
```

<a name="BKMK_CustomCollection"></a>

## <a name="defining-a-custom-collection"></a>Özel Koleksiyon Tanımlama

Bir koleksiyonu <xref:System.Collections.Generic.IEnumerable%601> veya <xref:System.Collections.IEnumerable> arabirimi uygulayarak tanımlayabilirsiniz.

Özel bir koleksiyon tanımlayabiliyor olsanız da, bu konunun başlarında [Koleksiyon Türleri'nde](#BKMK_KindsOfCollections) açıklanan .NET Framework'de yer alan koleksiyonları kullanmak genellikle daha iyidir.

Aşağıdaki örnek, adlı `AllColors`özel bir koleksiyon sınıfı tanımlar. Bu sınıf, <xref:System.Collections.IEnumerable> yöntemin <xref:System.Collections.IEnumerable.GetEnumerator%2A> uygulanmasını gerektiren arabirimi uygular.

Yöntem `GetEnumerator` sınıfın bir örneğini `ColorEnumerator` döndürür. `ColorEnumerator`özelliğin, <xref:System.Collections.IEnumerator> <xref:System.Collections.IEnumerator.MoveNext%2A> yöntemin ve <xref:System.Collections.IEnumerator.Reset%2A> <xref:System.Collections.IEnumerator.Current%2A> yöntemin uygulanmasını gerektiren arabirimi uygular.

```csharp
private static void ListColors()
{
    var colors = new AllColors();

    foreach (Color theColor in colors)
    {
        Console.Write(theColor.Name + " ");
    }
    Console.WriteLine();
    // Output: red blue green
}

// Collection class.
public class AllColors : System.Collections.IEnumerable
{
    Color[] _colors =
    {
        new Color() { Name = "red" },
        new Color() { Name = "blue" },
        new Color() { Name = "green" }
    };

    public System.Collections.IEnumerator GetEnumerator()
    {
        return new ColorEnumerator(_colors);

        // Instead of creating a custom enumerator, you could
        // use the GetEnumerator of the array.
        //return _colors.GetEnumerator();
    }

    // Custom enumerator.
    private class ColorEnumerator : System.Collections.IEnumerator
    {
        private Color[] _colors;
        private int _position = -1;

        public ColorEnumerator(Color[] colors)
        {
            _colors = colors;
        }

        object System.Collections.IEnumerator.Current
        {
            get
            {
                return _colors[_position];
            }
        }

        bool System.Collections.IEnumerator.MoveNext()
        {
            _position++;
            return (_position < _colors.Length);
        }

        void System.Collections.IEnumerator.Reset()
        {
            _position = -1;
        }
    }
}

// Element class.
public class Color
{
    public string Name { get; set; }
}
```

<a name="BKMK_Iterators"></a>

## <a name="iterators"></a>Yineleyiciler

Bir *yineleme,* bir koleksiyon üzerinde özel yineleme gerçekleştirmek için kullanılır. Bir yineleyici bir yöntem veya `get` erişimci olabilir. Bir yineleyici, koleksiyonun her öğesini birer birer döndürmek için [bir verim iade](../../language-reference/keywords/yield.md) deyimi kullanır.

[Her](../../language-reference/keywords/foreach-in.md) bir ifade yi kullanarak bir yineleyici çağırırsınız. Döngünün `foreach` her yinelemesi yineleyiciyi çağırır. Bir `yield return` deyim yineleyicide ulaşıldığında, bir ifade döndürülür ve koddaki geçerli konum korunur. Yürütme, yineleyici çağrıldığında bu konumdan yeniden başlatılır.

Daha fazla bilgi için [Bkz. Yineleyiciler (C#)](./iterators.md).

Aşağıdaki örnekte bir yineleyici yöntemi kullanır. Yineleyici yöntemi, [for](../../language-reference/keywords/for.md) `yield return` döngüsü içinde bir deyim vardır. `ListEvenNumbers` Yöntemde, deyim gövdesinin `foreach` her yinelemesi, bir sonraki `yield return` deyime devam eden yineleyici yöntemine bir çağrı oluşturur.

```csharp
private static void ListEvenNumbers()
{
    foreach (int number in EvenSequence(5, 18))
    {
        Console.Write(number.ToString() + " ");
    }
    Console.WriteLine();
    // Output: 6 8 10 12 14 16 18
}

private static IEnumerable<int> EvenSequence(
    int firstNumber, int lastNumber)
{
    // Yield even numbers in the range.
    for (var number = firstNumber; number <= lastNumber; number++)
    {
        if (number % 2 == 0)
        {
            yield return number;
        }
    }
}
```

## <a name="see-also"></a>Ayrıca bkz.

- [Nesne ve Koleksiyon Başlatıcıları](../classes-and-structs/object-and-collection-initializers.md)
- [Programlama Kavramları (C#)](./index.md)
- [Option Strict Deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Nesnelere LINQ (C#)](./linq/linq-to-objects.md)
- [Paralel LINQ (PLINQ)](../../../standard/parallel-programming/introduction-to-plinq.md)
- [Koleksiyonlar ve Veri Yapıları](../../../standard/collections/index.md)
- [Koleksiyon Sınıfı Seçme](../../../standard/collections/selecting-a-collection-class.md)
- [Koleksiyonlar İçindeKi Karşılaştırmalar ve Sıralamalar](../../../standard/collections/comparisons-and-sorts-within-collections.md)
- [Genel Koleksiyonlar Ne Zaman Kullanılır?](../../../standard/collections/when-to-use-generic-collections.md)
