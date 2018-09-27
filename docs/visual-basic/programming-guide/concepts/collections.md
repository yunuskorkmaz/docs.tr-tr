---
title: Koleksiyonlar (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 5f7749f3-aaf2-4319-b63c-bfa72e1e2b7a
ms.openlocfilehash: 60519de1f580bf1cfa4aa067d4a999b20ea8d54d
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2018
ms.locfileid: "47399404"
---
# <a name="collections-visual-basic"></a>Koleksiyonlar (Visual Basic)
Birçok uygulama için ilgili nesnelerin gruplarını oluşturmak ve yönetmek istersiniz. Grup nesnelerini iki yolu vardır: nesne dizileri oluşturarak ve veya nesne koleksiyonu oluşturarak.  
  
 Dizileri oluşturmak ve nesneleri türü kesin olarak belirtilmiş sabit sayıdaki ile çalışmak için ekseriyetle faydalıdır. Diziler hakkında daha fazla bilgi için bkz: [diziler](../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
 Koleksiyonlar nesne grupları ile çalışmak için daha esnek bir yol sağlar. Dizilerden farklı olarak çalıştığınız nesne büyütme ve uygulamanın ihtiyacına göre dinamik olarak Daralt. Bazı koleksiyonlar için koleksiyona eklediğiniz ve böylece anahtarını kullanarak hızlı bir şekilde nesnesi alabilirsiniz herhangi bir nesneye bir anahtar atayabilirsiniz.  
  
 Bir koleksiyon bir sınıfı olduğundan bu koleksiyona öğeleri eklemeden önce sınıfının bir örneğini bildirmeniz gerekir.  
  
 Koleksiyonunuz tek bir veri türünde öğeler içeriyorsa, sınıflarda birini kullanabilirsiniz <xref:System.Collections.Generic?displayProperty=nameWithType> ad alanı. Genel koleksiyon tür güvenliği sağlar, böylece başka bir veri türü eklenebilir. Bir genel koleksiyondan öğe aldığınızda veri türünü belirlemeniz veya dönüştürmeniz gerekmez.  
  
> [!NOTE]
>  Bu konudaki örnekler için dahil [içeri aktarmalar](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) deyimleri için `System.Collections.Generic` ve `System.Linq` ad alanları.  
  
 **Bu konudaki**  
  
-   [Basit bir koleksiyon kullanma](#BKMK_SimpleCollection)  
  
-   [Koleksiyon türleri](#BKMK_KindsOfCollections)  
  
    -   [System.Collections.Generic sınıfları](#BKMK_Generic)  
  
    -   [System.Collections.Concurrent sınıfları](#BKMK_Concurrent)  
  
    -   [System.Collections sınıfları](#BKMK_Collections)  
  
    -   [Visual Basic Collection sınıfı](#BKMK_VisualBasic)  
  
-   [Anahtar/değer çiftleri topluluğu uygulama](#BKMK_KeyValuePairs)  
  
-   [Koleksiyona erişmek için LINQ kullanma](#BKMK_LINQ)  
  
-   [Koleksiyonda sıralama](#BKMK_Sorting)  
  
-   [Özel koleksiyonu tanımlama](#BKMK_CustomCollection)  
  
-   [Yineleyiciler](#BKMK_Iterators)  
  
<a name="BKMK_SimpleCollection"></a>
## <a name="using-a-simple-collection"></a>Basit bir koleksiyon kullanma  
 Bu bölümdeki örneklerde genel kullanın <xref:System.Collections.Generic.List%601> sınıfını, bir türü kesin belirlenmiş nesneler listesiyle çalışmanıza olanak sağlar.  
  
 Aşağıdaki örnek bir dize listesi oluşturur ve ardından kullanarak dizeler arasında dolaşır bir [her biri için... Sonraki](../../../visual-basic/language-reference/statements/for-each-next-statement.md) deyimi.  
  
```vb  
' Create a list of strings.  
Dim salmons As New List(Of String)  
salmons.Add("chinook")  
salmons.Add("coho")  
salmons.Add("pink")  
salmons.Add("sockeye")  
  
' Iterate through the list.  
For Each salmon As String In salmons  
    Console.Write(salmon & " ")  
Next  
'Output: chinook coho pink sockeye  
```  
  
 Bir koleksiyonun içeriği önceden biliniyorsa, kullanabileceğiniz bir *koleksiyon Başlatıcısı* koleksiyonu başlatmak için. Daha fazla bilgi için [koleksiyon başlatıcıları](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).  
  
 Koleksiyona öğeleri eklemek için bir koleksiyon Başlatıcısı kullanılması dışında aşağıdaki örnek önceki örnekle aynıdır.  
  
```vb  
' Create a list of strings by using a  
' collection initializer.  
Dim salmons As New List(Of String) From  
    {"chinook", "coho", "pink", "sockeye"}  
  
For Each salmon As String In salmons  
    Console.Write(salmon & " ")  
Next  
'Output: chinook coho pink sockeye  
```  
  
 Kullanabileceğiniz bir [için... Sonraki](../../../visual-basic/language-reference/statements/for-next-statement.md) deyimi yerine bir `For Each` deyimi bir koleksiyon içinde yineleme için. Bu, bir koleksiyon öğelerine dizin konumundan erişerek gerçekleştirirsiniz. Öğelerin dizini 0'da başlar ve öğe sayısı eksi 1'de sona erer.  
  
 Aşağıdaki örneği kullanarak bir koleksiyonun öğeleri yinelenir `For…Next` yerine `For Each`.  
  
```vb  
Dim salmons As New List(Of String) From  
    {"chinook", "coho", "pink", "sockeye"}  
  
For index = 0 To salmons.Count - 1  
    Console.Write(salmons(index) & " ")  
Next  
'Output: chinook coho pink sockeye  
```  
  
 Aşağıdaki örnek, bir öğe kaldırmak için nesneyi belirterek koleksiyondan kaldırır.  
  
```vb  
' Create a list of strings by using a  
' collection initializer.  
Dim salmons As New List(Of String) From  
    {"chinook", "coho", "pink", "sockeye"}  
  
' Remove an element in the list by specifying  
' the object.  
salmons.Remove("coho")  
  
For Each salmon As String In salmons  
    Console.Write(salmon & " ")  
Next  
'Output: chinook pink sockeye  
```  
  
 Aşağıdaki örnek bir genel listeden öğeleri kaldırır. Yerine bir `For Each` deyimi, bir [için... Sonraki](../../../visual-basic/language-reference/statements/for-next-statement.md) azalan sırada yenileyen deyimi kullanılır. Bunun nedeni, <xref:System.Collections.Generic.List%601.RemoveAt%2A> yöntemi bir alt dizin değerine sahip olacak şekilde kaldırılmış bir öğeden sonra öğe neden olur.  
  
```vb  
Dim numbers As New List(Of Integer) From  
    {0, 1, 2, 3, 4, 5, 6, 7, 8, 9}  
  
' Remove odd numbers.  
For index As Integer = numbers.Count - 1 To 0 Step -1  
    If numbers(index) Mod 2 = 1 Then  
        ' Remove the element by specifying  
        ' the zero-based index in the list.  
        numbers.RemoveAt(index)  
    End If  
Next  
  
' Iterate through the list.  
' A lambda expression is placed in the ForEach method  
' of the List(T) object.  
numbers.ForEach(  
    Sub(number) Console.Write(number & " "))  
' Output: 0 2 4 6 8  
```  
  
 İçindeki öğe türleri için <xref:System.Collections.Generic.List%601>, ayrıca kendi sınıfınızı tanımlayabilirsiniz. Aşağıdaki örnekte, `Galaxy` tarafından kullanılan sınıfı <xref:System.Collections.Generic.List%601> kodda tanımlanır.  
  
```vb  
Private Sub IterateThroughList()  
    Dim theGalaxies As New List(Of Galaxy) From  
        {  
            New Galaxy With {.Name = "Tadpole", .MegaLightYears = 400},  
            New Galaxy With {.Name = "Pinwheel", .MegaLightYears = 25},  
            New Galaxy With {.Name = "Milky Way", .MegaLightYears = 0},  
            New Galaxy With {.Name = "Andromeda", .MegaLightYears = 3}  
        }  
  
    For Each theGalaxy In theGalaxies  
        With theGalaxy  
            Console.WriteLine(.Name & "  " & .MegaLightYears)  
        End With  
    Next  
  
    ' Output:  
    '  Tadpole  400  
    '  Pinwheel  25  
    '  Milky Way  0  
    '  Andromeda  3  
End Sub  
  
Public Class Galaxy  
    Public Property Name As String  
    Public Property MegaLightYears As Integer  
End Class  
```  
  
<a name="BKMK_KindsOfCollections"></a>
## <a name="kinds-of-collections"></a>Koleksiyon türleri   
 Ortak koleksiyonların çoğu .NET Framework tarafından sağlanır. Her koleksiyon türü belirli bir amaç için tasarlanmıştır.  
  
 Bazı ortak koleksiyon sınıfları, bu bölümde açıklanan:  
  
-   <xref:System.Collections.Generic> Sınıfları  
  
-   <xref:System.Collections.Concurrent> Sınıfları  
  
-   <xref:System.Collections> Sınıfları  
  
-   Visual Basic `Collection` sınıfı  
  
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
  
 Ek bilgi için bkz: [yaygın olarak kullanılan koleksiyon türleri](../../../standard/collections/commonly-used-collection-types.md), [koleksiyon sınıfı seçme](../../../standard/collections/selecting-a-collection-class.md), ve <xref:System.Collections.Generic?displayProperty=nameWithType>.  
  
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

<a name="BKMK_VisualBasic"></a> 
###  <a name="visual-basic-collection-class"></a>Visual Basic Collection sınıfı  
 Visual Basic kullanabileceğiniz <xref:Microsoft.VisualBasic.Collection> erişimi öğesi sayısal dizin kullanarak koleksiyon veya bir sınıf `String` anahtarı. Bir koleksiyon nesnesi ile veya bir anahtar belirtmeden öğe ekleyebilirsiniz. Bir anahtar olmadan bir öğe eklerseniz, erişmek için sayısal dizinini kullanmanız gerekir.  
  
 Visual Basic `Collection` sınıf türü olarak tüm öğelerini depolar `Object`, herhangi bir veri türünde bir öğe ekleyebilirsiniz. Eklenen uygunsuz veri türleriyle yoktur.  
  
 Visual Basic kullandığınızda `Collection` sınıfı, bir koleksiyondaki ilk öğe dizini 1 vardır. Bu, başlangıç dizini 0 olduğu .NET Framework koleksiyon sınıflarından farklıdır.  
  
 Mümkün olduğunda genel koleksiyonları kullanması gereken <xref:System.Collections.Generic?displayProperty=nameWithType> ad alanı veya <xref:System.Collections.Concurrent> ad alanı Visual Basic yerine `Collection` sınıfı.  
  
 Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Collection>.  
  
<a name="BKMK_KeyValuePairs"></a>
## <a name="implementing-a-collection-of-keyvalue-pairs"></a>Anahtar/değer çiftleri topluluğu uygulama   
 <xref:System.Collections.Generic.Dictionary%602> Genel koleksiyonu her öğenin anahtarını kullanarak bir koleksiyondaki öğelere erişmenize olanak sağlar. Her ek sözlük için bir değer ve ilişkili anahtarını oluşur. Bir değeri anahtarını kullanarak almak oldukça hızlıdır `Dictionary` sınıfı bir karma tablo olarak uygulanır.  
  
 Aşağıdaki örnek, oluşturur bir `Dictionary` koleksiyonu ve kullanarak sözlük yinelenir. bir `For Each` deyimi.  
  
```vb  
Private Sub IterateThroughDictionary()  
    Dim elements As Dictionary(Of String, Element) = BuildDictionary()  
  
    For Each kvp As KeyValuePair(Of String, Element) In elements  
        Dim theElement As Element = kvp.Value  
  
        Console.WriteLine("key: " & kvp.Key)  
        With theElement  
            Console.WriteLine("values: " & .Symbol & " " &  
                .Name & " " & .AtomicNumber)  
        End With  
    Next  
End Sub  
  
Private Function BuildDictionary() As Dictionary(Of String, Element)  
    Dim elements As New Dictionary(Of String, Element)  
  
    AddToDictionary(elements, "K", "Potassium", 19)  
    AddToDictionary(elements, "Ca", "Calcium", 20)  
    AddToDictionary(elements, "Sc", "Scandium", 21)  
    AddToDictionary(elements, "Ti", "Titanium", 22)  
  
    Return elements  
End Function  
  
Private Sub AddToDictionary(ByVal elements As Dictionary(Of String, Element),  
ByVal symbol As String, ByVal name As String, ByVal atomicNumber As Integer)  
    Dim theElement As New Element  
  
    theElement.Symbol = symbol  
    theElement.Name = name  
    theElement.AtomicNumber = atomicNumber  
  
    elements.Add(Key:=theElement.Symbol, value:=theElement)  
End Sub  
  
Public Class Element  
    Public Property Symbol As String  
    Public Property Name As String  
    Public Property AtomicNumber As Integer  
End Class  
```  
  
 Bunun yerine bir koleksiyon Başlatıcısı oluşturmak için kullanılacak `Dictionary` koleksiyonu değiştirebilirsiniz `BuildDictionary` ve `AddToDictionary` yöntemlerini aşağıdaki yöntemle.  
  
```vb  
Private Function BuildDictionary2() As Dictionary(Of String, Element)  
    Return New Dictionary(Of String, Element) From  
        {  
            {"K", New Element With  
                {.Symbol = "K", .Name = "Potassium", .AtomicNumber = 19}},  
            {"Ca", New Element With  
                {.Symbol = "Ca", .Name = "Calcium", .AtomicNumber = 20}},  
            {"Sc", New Element With  
                {.Symbol = "Sc", .Name = "Scandium", .AtomicNumber = 21}},  
            {"Ti", New Element With  
                {.Symbol = "Ti", .Name = "Titanium", .AtomicNumber = 22}}  
        }  
End Function  
```  
  
 Aşağıdaki örnekte <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> yöntemi ve <xref:System.Collections.Generic.Dictionary%602.Item%2A> özelliği `Dictionary` öğeyi anahtara göre hızlı bir şekilde bulmak için. `Item` Özelliği bir öğeye erişmenize olanak tanır `elements` kullanarak koleksiyon `elements(symbol)` Visual Basic kod.  
  
```vb  
Private Sub FindInDictionary(ByVal symbol As String)  
    Dim elements As Dictionary(Of String, Element) = BuildDictionary()  
  
    If elements.ContainsKey(symbol) = False Then  
        Console.WriteLine(symbol & " not found")  
    Else  
        Dim theElement = elements(symbol)  
        Console.WriteLine("found: " & theElement.Name)  
    End If  
End Sub  
```  
  
 Aşağıdaki örnek, bunun yerine kullanır <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> yöntemi anahtara göre hızlı bir şekilde öğeyi bulun.  
  
```vb  
Private Sub FindInDictionary2(ByVal symbol As String)  
    Dim elements As Dictionary(Of String, Element) = BuildDictionary()  
  
    Dim theElement As Element = Nothing  
    If elements.TryGetValue(symbol, theElement) = False Then  
        Console.WriteLine(symbol & " not found")  
    Else  
        Console.WriteLine("found: " & theElement.Name)  
    End If  
End Sub  
```  
  
<a name="BKMK_LINQ"></a> 
##  <a name="using-linq-to-access-a-collection"></a>Koleksiyona erişmek için LINQ kullanma  
 LINQ (dil ile tümleşik sorgu) koleksiyonlara erişmek için kullanılabilir. LINQ sorguları filtreleme, sıralama ve Gruplama yetenekler sağlar. Daha fazla bilgi için [Visual Basic'te lınq'e Başlarken](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).  
  
 Aşağıdaki örnek, bir genel LINQ sorgusu çalıştırır `List`. LINQ sorgusu sonuçları içeren farklı bir koleksiyon döndürür.  
  
```vb  
Private Sub ShowLINQ()  
    Dim elements As List(Of Element) = BuildList()  
  
    ' LINQ Query.  
    Dim subset = From theElement In elements  
                  Where theElement.AtomicNumber < 22  
                  Order By theElement.Name  
  
    For Each theElement In subset  
        Console.WriteLine(theElement.Name & " " & theElement.AtomicNumber)  
    Next  
  
    ' Output:  
    '  Calcium 20  
    '  Potassium 19  
    '  Scandium 21  
End Sub  
  
Private Function BuildList() As List(Of Element)  
    Return New List(Of Element) From  
        {  
            {New Element With  
                {.Symbol = "K", .Name = "Potassium", .AtomicNumber = 19}},  
            {New Element With  
                {.Symbol = "Ca", .Name = "Calcium", .AtomicNumber = 20}},  
            {New Element With  
                {.Symbol = "Sc", .Name = "Scandium", .AtomicNumber = 21}},  
            {New Element With  
                {.Symbol = "Ti", .Name = "Titanium", .AtomicNumber = 22}}  
        }  
End Function  
  
Public Class Element  
    Public Property Symbol As String  
    Public Property Name As String  
    Public Property AtomicNumber As Integer  
End Class  
```  
  
 <a name="BKMK_Sorting"></a> 
## <a name="sorting-a-collection"></a>Koleksiyonda sıralama  
 Aşağıdaki örnek bir koleksiyonu sıralamak için bir yordam gösterir. Örnek örneklerini sıralar `Car` depolanan sınıfı bir <xref:System.Collections.Generic.List%601>. `Car` Sınıfının Implements <xref:System.IComparable%601> gerektiren arabirimi <xref:System.IComparable%601.CompareTo%2A> yönteminin uygulanmasını.  
  
 Her çağrı <xref:System.IComparable%601.CompareTo%2A> yöntemi sıralama için kullanılan tek bir karşılaştırma yapar. Kullanıcı tarafından yazılan kodu `CompareTo` geçerli nesnenin başka bir nesneyle her karşılaştırılışında bir değer döndürür. Döndürülen değer daha az nesne geçerli nesneye sıfırdan küçük nesnesine, geçerli nesne diğer nesneden büyükse sıfır ve sıfır büyüktür eşit olmaları durumunda. Bu, kodda büyüktür, küçüktür ölçütleri tanımlayın ve eşit sağlar.  
  
 İçinde `ListCars` yöntemi `cars.Sort()` deyimi listeyi sıralar. Bu çağrıyı <xref:System.Collections.Generic.List%601.Sort%2A> yöntemi <xref:System.Collections.Generic.List%601> neden `CompareTo` otomatik olarak çağrılmasına yöntemi `Car` nesneler `List`.  
  
```vb  
Public Sub ListCars()  
  
    ' Create some new cars.  
    Dim cars As New List(Of Car) From  
    {  
        New Car With {.Name = "car1", .Color = "blue", .Speed = 20},  
        New Car With {.Name = "car2", .Color = "red", .Speed = 50},  
        New Car With {.Name = "car3", .Color = "green", .Speed = 10},  
        New Car With {.Name = "car4", .Color = "blue", .Speed = 50},  
        New Car With {.Name = "car5", .Color = "blue", .Speed = 30},  
        New Car With {.Name = "car6", .Color = "red", .Speed = 60},  
        New Car With {.Name = "car7", .Color = "green", .Speed = 50}  
    }  
  
    ' Sort the cars by color alphabetically, and then by speed  
    ' in descending order.  
    cars.Sort()  
  
    ' View all of the cars.  
    For Each thisCar As Car In cars  
        Console.Write(thisCar.Color.PadRight(5) & " ")  
        Console.Write(thisCar.Speed.ToString & " ")  
        Console.Write(thisCar.Name)  
        Console.WriteLine()  
    Next  
  
    ' Output:  
    '  blue  50 car4  
    '  blue  30 car5  
    '  blue  20 car1  
    '  green 50 car7  
    '  green 10 car3  
    '  red   60 car6  
    '  red   50 car2  
End Sub  
  
Public Class Car  
    Implements IComparable(Of Car)  
  
    Public Property Name As String  
    Public Property Speed As Integer  
    Public Property Color As String  
  
    Public Function CompareTo(ByVal other As Car) As Integer _  
        Implements System.IComparable(Of Car).CompareTo  
        ' A call to this method makes a single comparison that is  
        ' used for sorting.  
  
        ' Determine the relative order of the objects being compared.  
        ' Sort by color alphabetically, and then by speed in  
        ' descending order.  
  
        ' Compare the colors.  
        Dim compare As Integer  
        compare = String.Compare(Me.Color, other.Color, True)  
  
        ' If the colors are the same, compare the speeds.  
        If compare = 0 Then  
            compare = Me.Speed.CompareTo(other.Speed)  
  
            ' Use descending order for speed.  
            compare = -compare  
        End If  
  
        Return compare  
    End Function  
End Class  
```  
  
<a name="BKMK_CustomCollection"></a> 
## <a name="defining-a-custom-collection"></a>Özel koleksiyonu tanımlama  
 Uygulayarak bir koleksiyon tanımlayabilirsiniz <xref:System.Collections.Generic.IEnumerable%601> veya <xref:System.Collections.IEnumerable> arabirimi. Ek bilgi için bkz: [koleksiyon numaralandırma](https://msdn.microsoft.com/library/71807ea7-9180-48a6-916f-35a5251d477f).  
  
 Bir özel koleksiyon tanımlayabilirsiniz, bunun yerine açıklanan .NET Framework içinde yer koleksiyonların kullanılması daha iyi [tür, koleksiyonları](#kinds-of-collections) bu konuda daha önce.  
  
 Aşağıdaki örnekte adlı bir özel koleksiyon tanımlar `AllColors`. Bu sınıfın uyguladığı <xref:System.Collections.IEnumerable> gerektiren arabirimi <xref:System.Collections.IEnumerable.GetEnumerator%2A> yönteminin uygulanmasını.  
  
 `GetEnumerator` Yöntemi kendinin bir örneğini döndürür `ColorEnumerator` sınıfı. `ColorEnumerator` uygulayan <xref:System.Collections.IEnumerator> gerektiren arabirimi <xref:System.Collections.IEnumerator.Current%2A> özelliği <xref:System.Collections.IEnumerator.MoveNext%2A> yöntemi ve <xref:System.Collections.IEnumerator.Reset%2A> yönteminin uygulanmasını.  
  
```vb  
Public Sub ListColors()  
    Dim colors As New AllColors()  
  
    For Each theColor As Color In colors  
        Console.Write(theColor.Name & " ")  
    Next  
    Console.WriteLine()  
    ' Output: red blue green  
End Sub  
  
' Collection class.  
Public Class AllColors  
    Implements System.Collections.IEnumerable  
  
    Private _colors() As Color =  
    {  
        New Color With {.Name = "red"},  
        New Color With {.Name = "blue"},  
        New Color With {.Name = "green"}  
    }  
  
    Public Function GetEnumerator() As System.Collections.IEnumerator _  
        Implements System.Collections.IEnumerable.GetEnumerator  
  
        Return New ColorEnumerator(_colors)  
  
        ' Instead of creating a custom enumerator, you could  
        ' use the GetEnumerator of the array.  
        'Return _colors.GetEnumerator  
    End Function  
  
    ' Custom enumerator.  
    Private Class ColorEnumerator  
        Implements System.Collections.IEnumerator  
  
        Private _colors() As Color  
        Private _position As Integer = -1  
  
        Public Sub New(ByVal colors() As Color)  
            _colors = colors  
        End Sub  
  
        Public ReadOnly Property Current() As Object _  
            Implements System.Collections.IEnumerator.Current  
            Get  
                Return _colors(_position)  
            End Get  
        End Property  
  
        Public Function MoveNext() As Boolean _  
            Implements System.Collections.IEnumerator.MoveNext  
            _position += 1  
            Return (_position < _colors.Length)  
        End Function  
  
        Public Sub Reset() Implements System.Collections.IEnumerator.Reset  
            _position = -1  
        End Sub  
    End Class  
End Class  
  
' Element class.  
Public Class Color  
    Public Property Name As String  
End Class  
```  
  
<a name="BKMK_Iterators"></a>
##  <a name="iterators"></a>Yineleyiciler  
 Bir *yineleyici* bir koleksiyon üzerinde özel yineleme yapmak için kullanılır. Bir yineleyiciyi bir yöntem olabilir veya bir `get` erişimcisi. Yineleyici bir [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) deyimini her öğesini birer birer koleksiyonunun bir döndürür.  
  
 Kullanarak bir yineleyici çağırabilirsiniz bir [her biri için... Sonraki](../../../visual-basic/language-reference/statements/for-each-next-statement.md) deyimi. Her bir yinelemesini `For Each` döngü yineleyiciyi çağırır. Olduğunda bir `Yield` yineleyicisi deyimine ulaşıldığında, bir ifade döndürülür ve kodun geçerli konumu korunur. Yürütme, yineleyicinin bir sonraki açışınızda bu konumdan başlatılır.  
  
 Daha fazla bilgi için [yineleyiciler (Visual Basic)](../../../visual-basic/programming-guide/concepts/iterators.md).  
  
 Aşağıdaki örnek yineleyici yöntemini kullanır. Yineleyici yöntem, bir `Yield` içindeki bir [için... Sonraki](../../../visual-basic/language-reference/statements/for-next-statement.md) döngü. İçinde `ListEvenNumbers` yöntemi, her bir yinelemesini `For Each` diğerine geçer yineleyici yöntem için bir çağrı oluşturur ve deyim gövdesi `Yield` deyimi.  
  
```vb  
Public Sub ListEvenNumbers()  
    For Each number As Integer In EvenSequence(5, 18)  
        Console.Write(number & " ")  
    Next  
    Console.WriteLine()  
    ' Output: 6 8 10 12 14 16 18  
End Sub  
  
Private Iterator Function EvenSequence(  
ByVal firstNumber As Integer, ByVal lastNumber As Integer) _  
As IEnumerable(Of Integer)  
  
' Yield even numbers in the range.  
    For number = firstNumber To lastNumber  
        If number Mod 2 = 0 Then  
            Yield number  
        End If  
    Next  
End Function  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Öğe Başlatıcıları](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)  
- [Programlama Kavramları (Visual Basic)](../../../visual-basic/programming-guide/concepts/index.md)  
- [Option Strict Deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
- [LINQ to Objects'in (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
- [Paralel LINQ (PLINQ)](../../../standard/parallel-programming/parallel-linq-plinq.md)  
- [Koleksiyonlar ve Veri Yapıları](../../../standard/collections/index.md)  
- [Koleksiyon oluşturma ve düzenleme](https://msdn.microsoft.com/library/2065398e-eb1a-4821-9188-75f16e42e069)  
- [Koleksiyon Sınıfı Seçme](../../../standard/collections/selecting-a-collection-class.md)  
- [Koleksiyonlardaki Karşılaştırmalar ve Sıralamalar](../../../standard/collections/comparisons-and-sorts-within-collections.md)  
- [Genel Koleksiyonlar Ne Zaman Kullanılır?](../../../standard/collections/when-to-use-generic-collections.md)
