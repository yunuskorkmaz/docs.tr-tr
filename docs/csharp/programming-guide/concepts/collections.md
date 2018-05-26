---
title: Koleksiyonlar (C#)
ms.date: 07/20/2015
ms.assetid: 317d7dc3-8587-4873-8b3e-556f86497939
ms.openlocfilehash: 7400d4eee4df99cb1e255e428f83028fddf481f4
ms.sourcegitcommit: 54231aa56fca059e9297888a96fbca1d4cf3746c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/25/2018
---
# <a name="collections-c"></a>Koleksiyonlar (C#)
Birçok uygulama için ilgili nesneleri, grupları oluşturmak ve yönetmek istediğiniz. Grup nesnelerine iki yolu vardır: nesne dizileri oluşturarak ve nesne koleksiyonları oluşturma.  
  
 Diziler oluşturmak ve sabit bir türü kesin belirlenmiş nesnelerin sayısı ile çalışmak için çok kullanışlıdır. Dizileri hakkında daha fazla bilgi için bkz: [diziler](../../../csharp/programming-guide/arrays/index.md).  
  
 Koleksiyonları nesneleri grupları ile çalışmak için daha esnek bir şekilde sağlar. Diziler nesneleri ile çalışma grubu büyür ve dinamik olarak uygulama değişikliği ihtiyaçları geliştikçe daraltma. Bazı koleksiyonlar için nesne anahtarı kullanarak hızlı bir şekilde alabilmeleri koleksiyona koymak nesnesine bir anahtar atayabilirsiniz.  
  
 Bu koleksiyona öğeleri ekleyebilmeniz için önce sınıfın örneğini bildirmeniz gerekir böylece bir sınıf koleksiyonudur.  
  
 Koleksiyonunuz yalnızca bir veri türündeki öğeler içeriyorsa, sınıflarda birini kullanabilirsiniz <xref:System.Collections.Generic?displayProperty=nameWithType> ad alanı. Böylece başka bir veri türü eklenebilir bir genel koleksiyon tür güvenliği zorlar. Genel bir koleksiyondaki bir öğe aldığınızda, kendi veri türü belirlenemiyor veya dönüştürmeden gerekmez.  
  
> [!NOTE]
>  Bu konudaki örnekler için dahil [kullanarak](../../../csharp/language-reference/keywords/using-directive.md) yönergeleri için `System.Collections.Generic` ve `System.Linq` ad alanları.  
  
 **Bu konudaki**  
  
-   [Basit bir koleksiyonun kullanma](#BKMK_SimpleCollection)  
  
-   [Koleksiyon türleri](#BKMK_KindsOfCollections)  
  
    -   [System.Collections.Generic sınıfları](#BKMK_Generic)  
  
    -   [System.Collections.Concurrent sınıfları](#BKMK_Concurrent)  
  
    -   [System.Collections sınıfları](#BKMK_Collections)  
  
-   [Anahtar/değer çiftleri koleksiyonu uygulama](#BKMK_KeyValuePairs)  
  
-   [Bir koleksiyon erişmek için LINQ kullanma](#BKMK_LINQ)  
  
-   [Koleksiyonda sıralama](#BKMK_Sorting)  
  
-   [Özel bir koleksiyona tanımlama](#BKMK_CustomCollection)  
  
-   [Yineleyiciler](#BKMK_Iterators)  
  
<a name="BKMK_SimpleCollection"></a>
## <a name="using-a-simple-collection"></a>Basit bir koleksiyonun kullanma  
 Bu bölümdeki örnekleri genel kullanmak <xref:System.Collections.Generic.List%601> sınıfı, türü kesin belirlenmiş nesnelerin listesini ile çalışmanıza olanak sağlar.  
  
 Aşağıdaki örnek dizelerinin listesini oluşturur ve ardından kullanarak dizeleri tekrarlanan bir ya da [foreach](../../../csharp/language-reference/keywords/foreach-in.md) deyimi.  
  
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
  
 Bir koleksiyonun içeriğini önceden biliniyorsa, kullanabileceğiniz bir *koleksiyon Başlatıcısı* koleksiyonu başlatılamadı. Daha fazla bilgi için bkz: [nesne ve koleksiyon başlatıcıları](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).  
  
 Koleksiyon Başlatıcısı öğeleri koleksiyona eklemek için kullanılan dışında aşağıdaki örnek önceki örnekte aynıdır.  
  
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
  
 Kullanabileceğiniz bir [için](../../../csharp/language-reference/keywords/for.md) deyimi yerine bir `foreach` bir koleksiyonda yinelemek için deyimi. Bunun için dizin konumu tarafından koleksiyon öğeleri erişerek. Öğe dizini 0'da başlar ve öğe sayısı eksi 1'konumundaki sona erer.  
  
 Aşağıdaki örnek bir koleksiyonun öğelerini kullanarak tekrarlanan `for` yerine `foreach`.  
  
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
  
 Aşağıdaki örnek kaldırılacak nesne belirterek öğeyi koleksiyondan kaldırır.  
  
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
  
 Aşağıdaki örnek öğeleri genel bir listeden kaldırır. Yerine bir `foreach` deyimi, bir [için](../../../csharp/language-reference/keywords/for.md) azalan sırada tekrarlanan deyimi kullanılır. Bunun nedeni, <xref:System.Collections.Generic.List%601.RemoveAt%2A> yöntemi bir alt dizin değerine sahip olacak şekilde kaldırılan bir öğeden sonra öğeleri neden olur.  
  
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
  
 Öğe türü için <xref:System.Collections.Generic.List%601>, ayrıca kendi sınıfı tanımlayabilirsiniz. Aşağıdaki örnekte, `Galaxy` tarafından kullanılan sınıf <xref:System.Collections.Generic.List%601> kodda tanımlanır.  
  
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
 Birçok ortak koleksiyonları, .NET Framework tarafından sağlanır. Her koleksiyon türünün belirli bir amaç için tasarlanmıştır.  
  
 Genel koleksiyon sınıfları bazıları, bu bölümde açıklanmaktadır:  
  
-   <xref:System.Collections.Generic> Sınıfları  
  
-   <xref:System.Collections.Concurrent> Sınıfları  
  
-   <xref:System.Collections> Sınıfları  
  
<a name="BKMK_Generic"></a>
### <a name="systemcollectionsgeneric-classes"></a>System.Collections.Generic sınıfları  
 Sınıflarda birini kullanarak genel bir koleksiyon oluşturabilirsiniz <xref:System.Collections.Generic> ad alanı. Koleksiyondaki her öğe aynı veri türüne sahip bir genel koleksiyon faydalıdır. Bir genel koleksiyon yalnızca istenen verilerin vererek güçlü yazmaya zorlar eklenecek türü.  
  
 Aşağıdaki tabloda bazı sık kullanılan sınıfları listeler <xref:System.Collections.Generic?displayProperty=nameWithType> ad alanı:  

|örneği|Açıklama| 
|---|---|  
|<xref:System.Collections.Generic.Dictionary%602>|Anahtarına göre düzenlenir anahtar/değer çiftlerinin koleksiyonunu temsil eder.|  
|<xref:System.Collections.Generic.List%601>|Dizini tarafından erişilebilecek nesnelerin bir listesini temsil eder. Arama, sıralama ve listelerini değiştirmek için yöntemler sağlar.|  
|<xref:System.Collections.Generic.Queue%601>|İlk gelen, nesnelerin giren ilk çıkar (FIFO) koleksiyonunu temsil eder.|  
|<xref:System.Collections.Generic.SortedList%602>|Anahtarıyla ilişkili üzerinde temel sıralı anahtar/değer çiftlerinin koleksiyonunu temsil eder <xref:System.Collections.Generic.IComparer%601> uygulaması.|  
|<xref:System.Collections.Generic.Stack%601>|Son olarak, nesnelerin ilk çıkar (LIFO) koleksiyonunu temsil eder.|  
  
 Ek bilgi için bkz: [yaygın olarak kullanılan koleksiyon türleri](../../../standard/collections/commonly-used-collection-types.md), [koleksiyon sınıfı seçme](../../../standard/collections/selecting-a-collection-class.md), ve <xref:System.Collections.Generic>.  
  
<a name="BKMK_Concurrent"></a>
### <a name="systemcollectionsconcurrent-classes"></a>System.Collections.Concurrent sınıfları  
 .NET Framework 4 veya daha yeni koleksiyonlardaki <xref:System.Collections.Concurrent> ad alanı koleksiyon öğeleri birden çok iş parçacığından erişmek için etkin iş parçacığı açısından güvenli işlemler sağlar.  
  
 Sınıflarda <xref:System.Collections.Concurrent> ad alanı, ilgili türler yerine kullanılmalıdır <xref:System.Collections.Generic?displayProperty=nameWithType> ve <xref:System.Collections?displayProperty=nameWithType> birden çok iş parçacığı aynı anda koleksiyonuna erişme her ad alanları. Daha fazla bilgi için bkz: [iş parçacığı koleksiyonları](../../../standard/collections/thread-safe/index.md) ve <xref:System.Collections.Concurrent>.  
  
 Dahil bazı sınıfları <xref:System.Collections.Concurrent> ad <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, ve <xref:System.Collections.Concurrent.ConcurrentStack%601>.  
  
<a name="BKMK_Collections"></a>
### <a name="systemcollections-classes"></a>System.Collections sınıfları  
 Sınıflarda <xref:System.Collections?displayProperty=nameWithType> özellikle yazılan nesnelerin, ancak nesne türü ad alanı öğeleri saklamayın `Object`.  
  
 Mümkün olduğunda, genel koleksiyonlarda kullanması gereken <xref:System.Collections.Generic?displayProperty=nameWithType> ad alanı veya <xref:System.Collections.Concurrent> eski türler yerine ad `System.Collections` ad alanı.  
  
 Aşağıdaki tabloda bazı sık kullanılan sınıfları listeler `System.Collections` ad alanı:  
  
|örneği|Açıklama|  
|---|---|  
|<xref:System.Collections.ArrayList>|Temsil nesneleri büyüklüğü dinamik olarak artan bir dizi gerekli.|  
|<xref:System.Collections.Hashtable>|Anahtar karma koduna göre düzenlenir anahtar/değer çiftlerinin koleksiyonunu temsil eder.|  
|<xref:System.Collections.Queue>|İlk gelen, nesnelerin giren ilk çıkar (FIFO) koleksiyonunu temsil eder.|  
|<xref:System.Collections.Stack>|Son olarak, nesnelerin ilk çıkar (LIFO) koleksiyonunu temsil eder.|  
  
 <xref:System.Collections.Specialized> Ad alanı, yalnızca dize koleksiyonlar ve bağlı listesi ve karma sözlükler gibi özelleştirilmiş ve kesin türü belirtilmiş koleksiyon sınıfları sağlar.  

<a name="BKMK_KeyValuePairs"></a>
## <a name="implementing-a-collection-of-keyvalue-pairs"></a>Anahtar/değer çiftleri koleksiyonu uygulama  
 <xref:System.Collections.Generic.Dictionary%602> Genel koleksiyon her öğenin anahtarı kullanarak bir koleksiyondaki öğelerin erişmesine olanak sağlar. Her ek sözlük için bir değer ve ilişkili anahtarını oluşur. Kendi anahtarını kullanarak bir değer alma olduğundan hızlı `Dictionary` sınıfı, bir karma tablosu olarak uygulanır.  
  
 Aşağıdaki örnekte bir `Dictionary` koleksiyonu ve kullanarak sözlükte yinelenen bir `foreach` deyimi.  
  
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
  
 Bunun yerine koleksiyon Başlatıcısı oluşturmak için kullanılacak `Dictionary` değiştirebileceğiniz koleksiyonu `BuildDictionary` ve `AddToDictionary` aşağıdaki yöntemi yöntemleriyle.  
  
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
  
 Aşağıdaki örnek kullanır <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> yöntemi ve <xref:System.Collections.Generic.Dictionary%602.Item%2A> özelliği `Dictionary` öğe anahtarı tarafından hızla bulmak için. `Item` Özellik bir öğeyi erişmenize olanak tanır `elements` kullanarak koleksiyon `elements[symbol]` C#.  
  
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
  
 Aşağıdaki örnek, bunun yerine kullanır <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> yöntemi anahtarının hızlı bir şekilde bir öğe bulunamıyor.  
  
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
## <a name="using-linq-to-access-a-collection"></a>Bir koleksiyon erişmek için LINQ kullanma  
 LINQ (dil ile tümleşik sorgu) koleksiyonları erişmek için kullanılabilir. LINQ sorgularını filtreleme, sıralama ve yetenekleri gruplandırma sağlar. Daha fazla bilgi için bkz: [C# üzerinde LINQ ile çalışmaya başlama](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md).  
  
 Aşağıdaki örnek, genel karşı LINQ sorgusu çalıştırır `List`. LINQ Sorgu sonuçlarını içeren farklı bir koleksiyon döndürür.  
  
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
 Aşağıdaki örnek, bir koleksiyon sıralamak için bir yordam gösterilmektedir. Örnek örneklerini sıralar `Car` depolanmış sınıfı bir <xref:System.Collections.Generic.List%601>. `Car` Uygulayan sınıf <xref:System.IComparable%601> gerektiren arabirimi <xref:System.IComparable%601.CompareTo%2A> uygulanan yöntemi.  
  
 Her çağrı <xref:System.IComparable%601.CompareTo%2A> yöntemi sıralama için kullanılan tek bir karşılaştırma yapar. Kullanıcı tarafından yazılan kodu `CompareTo` yöntemi başka bir nesnenin geçerli nesnenin her karşılaştırma için bir değer döndürür. Döndürülen değer olan geçerli nesne ise sıfırdan az diğerinden daha az nesne, geçerli nesne bir nesneden daha büyükse, sıfır ve sıfırdan büyük eşit olup olmadıkları. Bu, kodda daha fazla değerinden ölçütleri tanımlayın ve eşit olanak sağlar.  
  
 İçinde `ListCars` yöntemi, `cars.Sort()` deyimi listesini sıralar. Bu çağrıyı <xref:System.Collections.Generic.List%601.Sort%2A> yöntemi <xref:System.Collections.Generic.List%601> neden `CompareTo` yöntemi için otomatik olarak adlandırılan `Car` nesnelerini `List`.  
  
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
## <a name="defining-a-custom-collection"></a>Özel bir koleksiyona tanımlama  
 Bir koleksiyon uygulayarak tanımlayabilirsiniz <xref:System.Collections.Generic.IEnumerable%601> veya <xref:System.Collections.IEnumerable> arabirimi.  
  
 Özel bir koleksiyona tanımlayabilirsiniz rağmen şurada açıklanan .NET Framework içinde yer alan koleksiyonlar kullanmanız daha iyi [türleri, koleksiyonları](#BKMK_KindsOfCollections) bu konuda daha önce.  
  
 Aşağıdaki örnek adlı özel koleksiyon sınıfı tanımlar `AllColors`. Bu sınıf uygulayan <xref:System.Collections.IEnumerable> gerektiren arabirimi <xref:System.Collections.IEnumerable.GetEnumerator%2A> uygulanan yöntemi.  
  
 `GetEnumerator` Yöntem örneği `ColorEnumerator` sınıfı. `ColorEnumerator` uygulayan <xref:System.Collections.IEnumerator> gerektiren arabirimi <xref:System.Collections.IEnumerator.Current%2A> özelliği, <xref:System.Collections.IEnumerator.MoveNext%2A> yöntemi ve <xref:System.Collections.IEnumerator.Reset%2A> uygulanan yöntemi.  
  
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
 Bir *yineleyici* içinde bir koleksiyon özel bir yineleme yapmak için kullanılır. Yineleyici bir yöntem olabilir veya bir `get` erişimcisi. Yineleyici kullanan bir [verim return](../../../csharp/language-reference/keywords/yield.md) deyimi her birer birer koleksiyonun bir öğesi döndürür.  
  
 Yineleyici kullanarak çağırma bir [foreach](../../../csharp/language-reference/keywords/foreach-in.md) deyimi. Her yinelemesinden `foreach` döngü yineleyici çağırır. Zaman bir `yield return` deyimi yineleyici ulaşıldığında, bir ifade döndürülür ve kod geçerli konumda korunur. Yürütme o konumdan yineleyici adlı bir sonraki başlatılışında yeniden başlatılır.  
  
 Daha fazla bilgi için bkz: [yineleyiciler (C#)](../../../csharp/programming-guide/concepts/iterators.md).  
  
 Aşağıdaki örnek, bir yineleyici yöntemi kullanır. İterator yöntemi sahip bir `yield return` içinde deyimi bir [için](../../../csharp/language-reference/keywords/for.md) döngü. İçinde `ListEvenNumbers` yöntemi, her yinelemesinden `foreach` deyimi gövde oluşturur diğerine geçer yineleyici yöntemine bir çağrı `yield return` deyimi.  
  
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
 [Nesne ve Koleksiyon Başlatıcıları](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
 [Programlama Kavramları (C#)](../../../csharp/programming-guide/concepts/index.md)  
 [Option Strict Deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [LINQ to nesneler (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
 [Paralel LINQ (PLINQ)](../../../standard/parallel-programming/parallel-linq-plinq.md)  
 [Koleksiyonlar ve Veri Yapıları](../../../standard/collections/index.md)  
 [Oluşturma ve koleksiyonları düzenleme](http://msdn.microsoft.com/library/2065398e-eb1a-4821-9188-75f16e42e069)  
 [Koleksiyon Sınıfı Seçme](../../../standard/collections/selecting-a-collection-class.md)  
 [Koleksiyonlardaki Karşılaştırmalar ve Sıralamalar](../../../standard/collections/comparisons-and-sorts-within-collections.md)  
 [Genel Koleksiyonlar Ne Zaman Kullanılır?](../../../standard/collections/when-to-use-generic-collections.md)  
