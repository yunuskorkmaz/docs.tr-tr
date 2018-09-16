---
title: Koleksiyonlar (C#)
ms.date: 07/20/2015
ms.assetid: 317d7dc3-8587-4873-8b3e-556f86497939
ms.openlocfilehash: 24b2155c07b6b66820d373d6310ff6b1c6ab224f
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45679180"
---
# <a name="collections-c"></a>Koleksiyonlar (C#)
Birçok uygulama için ilgili nesnelerin gruplarını oluşturmak ve yönetmek istersiniz. Grup nesnelerini iki yolu vardır: nesne dizileri oluşturarak ve veya nesne koleksiyonu oluşturarak.  
  
 Dizileri oluşturmak ve nesneleri türü kesin olarak belirtilmiş sabit sayıdaki ile çalışmak için ekseriyetle faydalıdır. Diziler hakkında daha fazla bilgi için bkz: [diziler](../../../csharp/programming-guide/arrays/index.md).  
  
 Koleksiyonlar nesne grupları ile çalışmak için daha esnek bir yol sağlar. Dizilerden farklı olarak çalıştığınız nesne büyütme ve uygulamanın ihtiyacına göre dinamik olarak Daralt. Bazı koleksiyonlar için koleksiyona eklediğiniz ve böylece anahtarını kullanarak hızlı bir şekilde nesnesi alabilirsiniz herhangi bir nesneye bir anahtar atayabilirsiniz.  
  
 Bir koleksiyon bir sınıfı olduğundan bu koleksiyona öğeleri eklemeden önce sınıfının bir örneğini bildirmeniz gerekir.  
  
 Koleksiyonunuz tek bir veri türünde öğeler içeriyorsa, sınıflarda birini kullanabilirsiniz <xref:System.Collections.Generic?displayProperty=nameWithType> ad alanı. Genel koleksiyon tür güvenliği sağlar, böylece başka bir veri türü eklenebilir. Bir genel koleksiyondan öğe aldığınızda veri türünü belirlemeniz veya dönüştürmeniz gerekmez.  
  
> [!NOTE]
>  Bu konudaki örnekler için dahil [kullanarak](../../../csharp/language-reference/keywords/using-directive.md) yönergeleri `System.Collections.Generic` ve `System.Linq` ad alanları.  
  
 **Bu konudaki**  
  
-   [Basit bir koleksiyon kullanma](#BKMK_SimpleCollection)  
  
-   [Koleksiyon türleri](#BKMK_KindsOfCollections)  
  
    -   [System.Collections.Generic sınıfları](#BKMK_Generic)  
  
    -   [System.Collections.Concurrent sınıfları](#BKMK_Concurrent)  
  
    -   [System.Collections sınıfları](#BKMK_Collections)  
  
-   [Anahtar/değer çiftleri topluluğu uygulama](#BKMK_KeyValuePairs)  
  
-   [Koleksiyona erişmek için LINQ kullanma](#BKMK_LINQ)  
  
-   [Koleksiyonda sıralama](#BKMK_Sorting)  
  
-   [Özel koleksiyonu tanımlama](#BKMK_CustomCollection)  
  
-   [Yineleyiciler](#BKMK_Iterators)  
  
<a name="BKMK_SimpleCollection"></a>
## <a name="using-a-simple-collection"></a>Basit bir koleksiyon kullanma  
 Bu bölümdeki örneklerde genel kullanın <xref:System.Collections.Generic.List%601> sınıfını, bir türü kesin belirlenmiş nesneler listesiyle çalışmanıza olanak sağlar.  
  
 Aşağıdaki örnek bir dize listesi oluşturur ve ardından kullanarak dizeler arasında yinelenir. bir ya da [foreach](../../../csharp/language-reference/keywords/foreach-in.md) deyimi.  
  
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
  
 Bir koleksiyonun içeriği önceden biliniyorsa, kullanabileceğiniz bir *koleksiyon Başlatıcısı* koleksiyonu başlatmak için. Daha fazla bilgi için [nesne ve koleksiyon başlatıcıları](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).  
  
 Koleksiyona öğeleri eklemek için bir koleksiyon Başlatıcısı kullanılması dışında aşağıdaki örnek önceki örnekle aynıdır.  
  
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
  
 Kullanabileceğiniz bir [için](../../../csharp/language-reference/keywords/for.md) deyimi yerine bir `foreach` deyimi bir koleksiyon içinde yineleme için. Bu, bir koleksiyon öğelerine dizin konumundan erişerek gerçekleştirirsiniz. Öğelerin dizini 0'da başlar ve öğe sayısı eksi 1'de sona erer.  
  
 Aşağıdaki örneği kullanarak bir koleksiyonun öğeleri yinelenir `for` yerine `foreach`.  
  
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
  
 Aşağıdaki örnek, bir öğe kaldırmak için nesneyi belirterek koleksiyondan kaldırır.  
  
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
  
 Aşağıdaki örnek bir genel listeden öğeleri kaldırır. Yerine bir `foreach` deyimi, bir [için](../../../csharp/language-reference/keywords/for.md) azalan sırada yenileyen deyimi kullanılır. Bunun nedeni, <xref:System.Collections.Generic.List%601.RemoveAt%2A> yöntemi bir alt dizin değerine sahip olacak şekilde kaldırılmış bir öğeden sonra öğe neden olur.  
  
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
  
 İçindeki öğe türleri için <xref:System.Collections.Generic.List%601>, ayrıca kendi sınıfınızı tanımlayabilirsiniz. Aşağıdaki örnekte, `Galaxy` tarafından kullanılan sınıfı <xref:System.Collections.Generic.List%601> kodda tanımlanır.  
  
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
## <a name="kinds-of-collections"></a>Koleksiyon türleri 
 Ortak koleksiyonların çoğu .NET Framework tarafından sağlanır. Her koleksiyon türü belirli bir amaç için tasarlanmıştır.  
  
 Bazı ortak koleksiyon sınıfları, bu bölümde açıklanan:  
  
-   <xref:System.Collections.Generic> Sınıfları  
  
-   <xref:System.Collections.Concurrent> Sınıfları  
  
-   <xref:System.Collections> Sınıfları  
  
<a name="BKMK_Generic"></a>
### <a name="systemcollectionsgeneric-classes"></a>System.Collections.Generic sınıfları  
 Genel koleksiyon sınıfları birini kullanarak oluşturabileceğiniz <xref:System.Collections.Generic> ad alanı. Genel koleksiyon, koleksiyondaki her öğe aynı veri türüne sahip olduğunda yararlıdır. Yalnızca istenen veri sağlayarak güçlü yazmayı genel koleksiyon sağlar eklenecek türü.  
  
 Aşağıdaki tabloda sık kullanılan sınıflarından bazılarını listeler <xref:System.Collections.Generic?displayProperty=nameWithType> ad alanı:  

|örneği|Açıklama| 
|---|---|  
|<xref:System.Collections.Generic.Dictionary%602>|Anahtara göre düzenlenen anahtar/değer çifti koleksiyonunu temsil eder.|  
|<xref:System.Collections.Generic.List%601>|Dizin tarafından erişilebilecek nesnelerin bir listesini temsil eder. Arama, sıralama ve listelerini değiştirmek için yöntemler sağlar.|  
|<xref:System.Collections.Generic.Queue%601>|İlk giren ilk çıkar (FIFO) nesne koleksiyonunu temsil eder.|  
|<xref:System.Collections.Generic.SortedList%602>|Anahtarıyla ilişkili göre sıralanan anahtar/değer çiftlerinin koleksiyonunu temsil eder <xref:System.Collections.Generic.IComparer%601> uygulaması.|  
|<xref:System.Collections.Generic.Stack%601>|Son giren ilk çıkar (LIFO) nesne koleksiyonunu temsil eder.|  
  
 Ek bilgi için bkz: [yaygın olarak kullanılan koleksiyon türleri](../../../standard/collections/commonly-used-collection-types.md), [koleksiyon sınıfı seçme](../../../standard/collections/selecting-a-collection-class.md), ve <xref:System.Collections.Generic>.  
  
<a name="BKMK_Concurrent"></a>
### <a name="systemcollectionsconcurrent-classes"></a>System.Collections.Concurrent sınıfları  
 .NET Framework 4 veya daha yeni sürümü, koleksiyonlar <xref:System.Collections.Concurrent> ad alanı, koleksiyon öğelerine birden fazla iş parçacığından erişmek için verimli bir iş parçacığı açısından güvenli işlemler sağlar.  
  
 Sınıflarda <xref:System.Collections.Concurrent> ad alanı, karşılık gelen türler yerine kullanılmalıdır <xref:System.Collections.Generic?displayProperty=nameWithType> ve <xref:System.Collections?displayProperty=nameWithType> birden çok iş parçacığı koleksiyon eriştiği her seferde ad alanları. Daha fazla bilgi için [iş parçacığı güvenli koleksiyonları](../../../standard/collections/thread-safe/index.md) ve <xref:System.Collections.Concurrent>.  
  
 Eklenen bazı sınıflar <xref:System.Collections.Concurrent> ad <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, ve <xref:System.Collections.Concurrent.ConcurrentStack%601>.  
  
<a name="BKMK_Collections"></a>
### <a name="systemcollections-classes"></a>System.Collections sınıfları  
 Sınıflarda <xref:System.Collections?displayProperty=nameWithType> özellikle yazılmış nesneler, ancak nesne türü ad alanı öğeleri saklamayın `Object`.  
  
 Mümkün olduğunda genel koleksiyonları kullanması gereken <xref:System.Collections.Generic?displayProperty=nameWithType> ad alanı veya <xref:System.Collections.Concurrent> ad alanındaki eski türlerde yerine `System.Collections` ad alanı.  
  
 Aşağıdaki tabloda sık kullanılan sınıflarından bazılarını listeler `System.Collections` ad alanı:  
  
|örneği|Açıklama|  
|---|---|  
|<xref:System.Collections.ArrayList>|Bir dizi boyutu olarak dinamik olarak artırılan nesne dizilerini temsil gereklidir.|  
|<xref:System.Collections.Hashtable>|Anahtarın karma koduna göre düzenlenen anahtar/değer çifti koleksiyonunu temsil eder.|  
|<xref:System.Collections.Queue>|İlk giren ilk çıkar (FIFO) nesne koleksiyonunu temsil eder.|  
|<xref:System.Collections.Stack>|Son giren ilk çıkar (LIFO) nesne koleksiyonunu temsil eder.|  
  
 <xref:System.Collections.Specialized> Ad alanı yalnızca dize koleksiyonları ve bağlantılı liste ve melez sözlükler gibi özelleştirilmiş ve türü kesin belirlenmiş koleksiyon sınıfları sağlar.  

<a name="BKMK_KeyValuePairs"></a>
## <a name="implementing-a-collection-of-keyvalue-pairs"></a>Anahtar/değer çiftleri topluluğu uygulama  
 <xref:System.Collections.Generic.Dictionary%602> Genel koleksiyonu her öğenin anahtarını kullanarak bir koleksiyondaki öğelere erişmenize olanak sağlar. Her ek sözlük için bir değer ve ilişkili anahtarını oluşur. Bir değeri anahtarını kullanarak almak oldukça hızlıdır `Dictionary` sınıfı bir karma tablo olarak uygulanır.  
  
 Aşağıdaki örnek, oluşturur bir `Dictionary` koleksiyonu ve kullanarak sözlük yinelenir. bir `foreach` deyimi.  
  
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
  
 Bunun yerine bir koleksiyon Başlatıcısı oluşturmak için kullanılacak `Dictionary` koleksiyonu değiştirebilirsiniz `BuildDictionary` ve `AddToDictionary` yöntemlerini aşağıdaki yöntemle.  
  
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
  
 Aşağıdaki örnekte <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> yöntemi ve <xref:System.Collections.Generic.Dictionary%602.Item%2A> özelliği `Dictionary` öğeyi anahtara göre hızlı bir şekilde bulmak için. `Item` Özelliği bir öğeye erişmenize olanak tanır `elements` kullanarak koleksiyon `elements[symbol]` C#.  
  
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
  
 Aşağıdaki örnek, bunun yerine kullanır <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> yöntemi anahtara göre hızlı bir şekilde öğeyi bulun.  
  
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
## <a name="using-linq-to-access-a-collection"></a>Koleksiyona erişmek için LINQ kullanma  
 LINQ (dil ile tümleşik sorgu) koleksiyonlara erişmek için kullanılabilir. LINQ sorguları filtreleme, sıralama ve Gruplama yetenekler sağlar. Daha fazla bilgi için [C# üzerinde LINQ ile çalışmaya başlama](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md).  
  
 Aşağıdaki örnek, bir genel LINQ sorgusu çalıştırır `List`. LINQ sorgusu sonuçları içeren farklı bir koleksiyon döndürür.  
  
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
## <a name="sorting-a-collection"></a>Koleksiyonda sıralama  
 Aşağıdaki örnek bir koleksiyonu sıralamak için bir yordam gösterir. Örnek örneklerini sıralar `Car` depolanan sınıfı bir <xref:System.Collections.Generic.List%601>. `Car` Sınıfının Implements <xref:System.IComparable%601> gerektiren arabirimi <xref:System.IComparable%601.CompareTo%2A> yönteminin uygulanmasını.  
  
 Her çağrı <xref:System.IComparable%601.CompareTo%2A> yöntemi sıralama için kullanılan tek bir karşılaştırma yapar. Kullanıcı tarafından yazılan kodu `CompareTo` geçerli nesnenin başka bir nesneyle her karşılaştırılışında bir değer döndürür. Döndürülen değer daha az nesne geçerli nesneye sıfırdan küçük nesnesine, geçerli nesne diğer nesneden büyükse sıfır ve sıfır büyüktür eşit olmaları durumunda. Bu, kodda büyüktür, küçüktür ölçütleri tanımlayın ve eşit sağlar.  
  
 İçinde `ListCars` yöntemi `cars.Sort()` deyimi listeyi sıralar. Bu çağrıyı <xref:System.Collections.Generic.List%601.Sort%2A> yöntemi <xref:System.Collections.Generic.List%601> neden `CompareTo` otomatik olarak çağrılmasına yöntemi `Car` nesneler `List`.  
  
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
## <a name="defining-a-custom-collection"></a>Özel koleksiyonu tanımlama  
 Uygulayarak bir koleksiyon tanımlayabilirsiniz <xref:System.Collections.Generic.IEnumerable%601> veya <xref:System.Collections.IEnumerable> arabirimi.  
  
 Bir özel koleksiyon tanımlayabilirsiniz, bunun yerine açıklanan .NET Framework içinde yer koleksiyonların kullanılması daha iyi [tür, koleksiyonları](#BKMK_KindsOfCollections) bu konuda daha önce.  
  
 Aşağıdaki örnekte adlı bir özel koleksiyon tanımlar `AllColors`. Bu sınıfın uyguladığı <xref:System.Collections.IEnumerable> gerektiren arabirimi <xref:System.Collections.IEnumerable.GetEnumerator%2A> yönteminin uygulanmasını.  
  
 `GetEnumerator` Yöntemi kendinin bir örneğini döndürür `ColorEnumerator` sınıfı. `ColorEnumerator` uygulayan <xref:System.Collections.IEnumerator> gerektiren arabirimi <xref:System.Collections.IEnumerator.Current%2A> özelliği <xref:System.Collections.IEnumerator.MoveNext%2A> yöntemi ve <xref:System.Collections.IEnumerator.Reset%2A> yönteminin uygulanmasını.  
  
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
##  <a name="iterators"></a>Yineleyiciler  
 Bir *yineleyici* bir koleksiyon üzerinde özel yineleme yapmak için kullanılır. Bir yineleyiciyi bir yöntem olabilir veya bir `get` erişimcisi. Yineleyici bir [yield return](../../../csharp/language-reference/keywords/yield.md) deyimini her öğesini birer birer koleksiyonunun bir döndürür.  
  
 Kullanarak bir yineleyici çağırabilirsiniz bir [foreach](../../../csharp/language-reference/keywords/foreach-in.md) deyimi. Her bir yinelemesini `foreach` döngü yineleyiciyi çağırır. Olduğunda bir `yield return` yineleyicisi deyimine ulaşıldığında, bir ifade döndürülür ve kodun geçerli konumu korunur. Yürütme, yineleyicinin bir sonraki açışınızda bu konumdan başlatılır.  
  
 Daha fazla bilgi için [yineleyiciler (C#)](../../../csharp/programming-guide/concepts/iterators.md).  
  
 Aşağıdaki örnek yineleyici yöntemini kullanır. Yineleyici yöntem, bir `yield return` içindeki bir [için](../../../csharp/language-reference/keywords/for.md) döngü. İçinde `ListEvenNumbers` yöntemi, her bir yinelemesini `foreach` diğerine geçer yineleyici yöntem için bir çağrı oluşturur ve deyim gövdesi `yield return` deyimi.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.

- [Nesne ve Koleksiyon Başlatıcıları](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
- [Programlama Kavramları (C#)](../../../csharp/programming-guide/concepts/index.md)  
- [Option Strict Deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
- [LINQ to Objects'in (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
- [Paralel LINQ (PLINQ)](../../../standard/parallel-programming/parallel-linq-plinq.md)  
- [Koleksiyonlar ve Veri Yapıları](../../../standard/collections/index.md)  
- [Koleksiyon oluşturma ve düzenleme](https://msdn.microsoft.com/library/2065398e-eb1a-4821-9188-75f16e42e069)  
- [Koleksiyon Sınıfı Seçme](../../../standard/collections/selecting-a-collection-class.md)  
- [Koleksiyonlardaki Karşılaştırmalar ve Sıralamalar](../../../standard/collections/comparisons-and-sorts-within-collections.md)  
- [Genel Koleksiyonlar Ne Zaman Kullanılır?](../../../standard/collections/when-to-use-generic-collections.md)  
