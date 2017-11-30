---
title: Koleksiyonlar (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: get-started-article
ms.assetid: 5f7749f3-aaf2-4319-b63c-bfa72e1e2b7a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: aac9ed655982ff4618e0bdb7fd2af16aaa546719
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="collections-visual-basic"></a>Koleksiyonlar (Visual Basic)
Birçok uygulama için ilgili nesneleri, grupları oluşturmak ve yönetmek istediğiniz. Grup nesnelerine iki yolu vardır: nesne dizileri oluşturarak ve nesne koleksiyonları oluşturma.  
  
 Diziler oluşturmak ve sabit bir türü kesin belirlenmiş nesnelerin sayısı ile çalışmak için çok kullanışlıdır. Dizileri hakkında daha fazla bilgi için bkz: [diziler](../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
 Koleksiyonları nesneleri grupları ile çalışmak için daha esnek bir şekilde sağlar. Diziler nesneleri ile çalışma grubu büyür ve dinamik olarak uygulama değişikliği ihtiyaçları geliştikçe daraltma. Bazı koleksiyonlar için nesne anahtarı kullanarak hızlı bir şekilde alabilmeleri koleksiyona koymak nesnesine bir anahtar atayabilirsiniz.  
  
 Bu koleksiyona öğeleri ekleyebilmeniz için önce sınıfın örneğini bildirmeniz gerekir böylece bir sınıf koleksiyonudur.  
  
 Koleksiyonunuz yalnızca bir veri türündeki öğeler içeriyorsa, sınıflarda birini kullanabilirsiniz <xref:System.Collections.Generic?displayProperty=nameWithType> ad alanı. Böylece başka bir veri türü eklenebilir bir genel koleksiyon tür güvenliği zorlar. Genel bir koleksiyondaki bir öğe aldığınızda, kendi veri türü belirlenemiyor veya dönüştürmeden gerekmez.  
  
> [!NOTE]
>  Bu konudaki örnekler için dahil [içeri aktarmalar](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) deyimleri için `System.Collections.Generic` ve `System.Linq` ad alanları.  
  
 **Bu konudaki**  
  
-   [Basit bir koleksiyonun kullanma](#BKMK_SimpleCollection)  
  
-   [Koleksiyon türleri](#BKMK_KindsOfCollections)  
  
    -   [System.Collections.Generic sınıfları](#BKMK_Generic)  
  
    -   [System.Collections.Concurrent sınıfları](#BKMK_Concurrent)  
  
    -   [System.Collections sınıfları](#BKMK_Collections)  
  
    -   [Visual Basic koleksiyon sınıfı](#BKMK_VisualBasic)  
  
-   [Anahtar/değer çiftleri koleksiyonu uygulama](#BKMK_KeyValuePairs)  
  
-   [Bir koleksiyon erişmek için LINQ kullanma](#BKMK_LINQ)  
  
-   [Koleksiyonda sıralama](#BKMK_Sorting)  
  
-   [Özel bir koleksiyona tanımlama](#BKMK_CustomCollection)  
  
-   [Yineleyiciler](#BKMK_Iterators)  
  
<a name="BKMK_SimpleCollection"></a>
## <a name="using-a-simple-collection"></a>Basit bir koleksiyonun kullanma  
 Bu bölümdeki örnekleri genel kullanmak <xref:System.Collections.Generic.List%601> sınıfı, türü kesin belirlenmiş nesnelerin listesini ile çalışmanıza olanak sağlar.  
  
 Aşağıdaki örnek dizelerinin listesini oluşturur ve ardından kullanarak dizeleri tekrarlanan bir [For Each... Sonraki](../../../visual-basic/language-reference/statements/for-each-next-statement.md) deyimi.  
  
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
  
 Bir koleksiyonun içeriğini önceden biliniyorsa, kullanabileceğiniz bir *koleksiyon Başlatıcısı* koleksiyonu başlatılamadı. Daha fazla bilgi için bkz: [koleksiyon başlatıcıları](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).  
  
 Koleksiyon Başlatıcısı öğeleri koleksiyona eklemek için kullanılan dışında aşağıdaki örnek önceki örnekte aynıdır.  
  
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
  
 Kullanabileceğiniz bir [için... Sonraki](../../../visual-basic/language-reference/statements/for-next-statement.md) deyimi yerine bir `For Each` bir koleksiyonda yinelemek için deyimi. Bunun için dizin konumu tarafından koleksiyon öğeleri erişerek. Öğe dizini 0'da başlar ve öğe sayısı eksi 1'konumundaki sona erer.  
  
 Aşağıdaki örnek bir koleksiyonun öğelerini kullanarak tekrarlanan `For…Next` yerine `For Each`.  
  
```vb  
Dim salmons As New List(Of String) From  
    {"chinook", "coho", "pink", "sockeye"}  
  
For index = 0 To salmons.Count - 1  
    Console.Write(salmons(index) & " ")  
Next  
'Output: chinook coho pink sockeye  
```  
  
 Aşağıdaki örnek kaldırılacak nesne belirterek öğeyi koleksiyondan kaldırır.  
  
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
  
 Aşağıdaki örnek öğeleri genel bir listeden kaldırır. Yerine bir `For Each` deyimi, bir [için... Sonraki](../../../visual-basic/language-reference/statements/for-next-statement.md) azalan sırada tekrarlanan deyimi kullanılır. Bunun nedeni, <xref:System.Collections.Generic.List%601.RemoveAt%2A> yöntemi bir alt dizin değerine sahip olacak şekilde kaldırılan bir öğeden sonra öğeleri neden olur.  
  
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
  
 Öğe türü için <xref:System.Collections.Generic.List%601>, ayrıca kendi sınıfı tanımlayabilirsiniz. Aşağıdaki örnekte, `Galaxy` tarafından kullanılan sınıf <xref:System.Collections.Generic.List%601> kodda tanımlanır.  
  
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
 Birçok ortak koleksiyonları, .NET Framework tarafından sağlanır. Her koleksiyon türünün belirli bir amaç için tasarlanmıştır.  
  
 Genel koleksiyon sınıfları bazıları, bu bölümde açıklanmaktadır:  
  
-   <xref:System.Collections.Generic>sınıfları  
  
-   <xref:System.Collections.Concurrent>sınıfları  
  
-   <xref:System.Collections>sınıfları  
  
-   Visual Basic `Collection` sınıfı  
  
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
  
 Ek bilgi için bkz: [yaygın olarak kullanılan koleksiyon türleri](../../../standard/collections/commonly-used-collection-types.md), [koleksiyon sınıfı seçme](../../../standard/collections/selecting-a-collection-class.md), ve <xref:System.Collections.Generic?displayProperty=nameWithType>.  
  
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

<a name="BKMK_VisualBasic"></a> 
###  <a name="visual-basic-collection-class"></a>Visual Basic koleksiyon sınıfı  
 Visual Basic kullanabilirsiniz <xref:Microsoft.VisualBasic.Collection> sınıfı bir koleksiyonun öğe sayısal bir dizindir kullanarak veya bir erişmesi `String` anahtarı. Bir koleksiyon nesnesi ile veya bir anahtarı belirtmeden öğeleri ekleyebilirsiniz. Bir anahtarı olmayan bir öğe eklerseniz, erişmek için kendi sayısal dizin kullanmanız gerekir.  
  
 Visual Basic `Collection` sınıf türü olarak tüm öğeleri depolar `Object`, tüm veri türünde bir öğe ekleyebilirsiniz. Eklenmekte olan uygun olmayan veri türleri karşı hiçbir koruma yoktur.  
  
 Visual Basic kullandığınızda `Collection` sınıfı, bir koleksiyondaki ilk öğe dizini 1 vardır. Bu, başlangıç dizini 0 olduğu .NET Framework koleksiyon sınıflardan farklıdır.  
  
 Mümkün olduğunda, genel koleksiyonlarda kullanması gereken <xref:System.Collections.Generic?displayProperty=nameWithType> ad alanı veya <xref:System.Collections.Concurrent> ad alanı Visual Basic yerine `Collection` sınıfı.  
  
 Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Collection>.  
  
<a name="BKMK_KeyValuePairs"></a>
## <a name="implementing-a-collection-of-keyvalue-pairs"></a>Anahtar/değer çiftleri koleksiyonu uygulama   
 <xref:System.Collections.Generic.Dictionary%602> Genel koleksiyon her öğenin anahtarı kullanarak bir koleksiyondaki öğelerin erişmesine olanak sağlar. Her ek sözlük için bir değer ve ilişkili anahtarını oluşur. Kendi anahtarını kullanarak bir değer alma olduğundan hızlı `Dictionary` sınıfı, bir karma tablosu olarak uygulanır.  
  
 Aşağıdaki örnekte bir `Dictionary` koleksiyonu ve kullanarak sözlükte yinelenen bir `For Each` deyimi.  
  
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
  
 Bunun yerine koleksiyon Başlatıcısı oluşturmak için kullanılacak `Dictionary` değiştirebileceğiniz koleksiyonu `BuildDictionary` ve `AddToDictionary` aşağıdaki yöntemi yöntemleriyle.  
  
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
  
 Aşağıdaki örnek kullanır <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> yöntemi ve <xref:System.Collections.Generic.Dictionary%602.Item%2A> özelliği `Dictionary` öğe anahtarı tarafından hızla bulmak için. `Item` Özellik bir öğeyi erişmenize olanak tanır `elements` kullanarak koleksiyon `elements(symbol)` Visual Basic kodu.  
  
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
  
 Aşağıdaki örnek, bunun yerine kullanır <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> yöntemi anahtarının hızlı bir şekilde bir öğe bulunamıyor.  
  
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
##  <a name="using-linq-to-access-a-collection"></a>Bir koleksiyon erişmek için LINQ kullanma  
 LINQ (dil ile tümleşik sorgu) koleksiyonları erişmek için kullanılabilir. LINQ sorgularını filtreleme, sıralama ve yetenekleri gruplandırma sağlar. Daha fazla bilgi için bkz: [Visual Basic'te LINQ ile çalışmaya başlama](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).  
  
 Aşağıdaki örnek, genel karşı LINQ sorgusu çalıştırır `List`. LINQ Sorgu sonuçlarını içeren farklı bir koleksiyon döndürür.  
  
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
 Aşağıdaki örnek, bir koleksiyon sıralamak için bir yordam gösterilmektedir. Örnek örneklerini sıralar `Car` depolanmış sınıfı bir <xref:System.Collections.Generic.List%601>. `Car` Uygulayan sınıf <xref:System.IComparable%601> gerektiren arabirimi <xref:System.IComparable%601.CompareTo%2A> uygulanan yöntemi.  
  
 Her çağrı <xref:System.IComparable%601.CompareTo%2A> yöntemi sıralama için kullanılan tek bir karşılaştırma yapar. Kullanıcı tarafından yazılan kodu `CompareTo` yöntemi başka bir nesnenin geçerli nesnenin her karşılaştırma için bir değer döndürür. Döndürülen değer olan geçerli nesne ise sıfırdan az diğerinden daha az nesne, geçerli nesne bir nesneden daha büyükse, sıfır ve sıfırdan büyük eşit olup olmadıkları. Bu, kodda daha fazla değerinden ölçütleri tanımlayın ve eşit olanak sağlar.  
  
 İçinde `ListCars` yöntemi, `cars.Sort()` deyimi listesini sıralar. Bu çağrıyı <xref:System.Collections.Generic.List%601.Sort%2A> yöntemi <xref:System.Collections.Generic.List%601> neden `CompareTo` yöntemi için otomatik olarak adlandırılan `Car` nesnelerini `List`.  
  
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
## <a name="defining-a-custom-collection"></a>Özel bir koleksiyona tanımlama  
 Bir koleksiyon uygulayarak tanımlayabilirsiniz <xref:System.Collections.Generic.IEnumerable%601> veya <xref:System.Collections.IEnumerable> arabirimi. Ek bilgi için bkz: [koleksiyonu numaralandırma](http://msdn.microsoft.com/en-us/71807ea7-9180-48a6-916f-35a5251d477f).  
  
 Özel bir koleksiyona tanımlayabilirsiniz rağmen şurada açıklanan .NET Framework içinde yer alan koleksiyonlar kullanmanız daha iyi [türleri, koleksiyonları](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b) bu konuda daha önce.  
  
 Aşağıdaki örnek adlı özel koleksiyon sınıfı tanımlar `AllColors`. Bu sınıf uygulayan <xref:System.Collections.IEnumerable> gerektiren arabirimi <xref:System.Collections.IEnumerable.GetEnumerator%2A> uygulanan yöntemi.  
  
 `GetEnumerator` Yöntem örneği `ColorEnumerator` sınıfı. `ColorEnumerator`uygulayan <xref:System.Collections.IEnumerator> gerektiren arabirimi <xref:System.Collections.IEnumerator.Current%2A> özelliği, <xref:System.Collections.IEnumerator.MoveNext%2A> yöntemi ve <xref:System.Collections.IEnumerator.Reset%2A> uygulanan yöntemi.  
  
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
 Bir *yineleyici* içinde bir koleksiyon özel bir yineleme yapmak için kullanılır. Yineleyici bir yöntem olabilir veya bir `get` erişimcisi. Yineleyici kullanan bir [verim](../../../visual-basic/language-reference/statements/yield-statement.md) deyimi her birer birer koleksiyonun bir öğesi döndürür.  
  
 Yineleyici kullanarak çağırma bir [For Each... Sonraki](../../../visual-basic/language-reference/statements/for-each-next-statement.md) deyimi. Her yinelemesinden `For Each` döngü yineleyici çağırır. Zaman bir `Yield` deyimi yineleyici ulaşıldığında, bir ifade döndürülür ve kod geçerli konumda korunur. Yürütme o konumdan yineleyici adlı bir sonraki başlatılışında yeniden başlatılır.  
  
 Daha fazla bilgi için bkz: [yineleyiciler (Visual Basic)](../../../visual-basic/programming-guide/concepts/iterators.md).  
  
 Aşağıdaki örnek, bir yineleyici yöntemi kullanır. İterator yöntemi sahip bir `Yield` içinde deyimi bir [için... Sonraki](../../../visual-basic/language-reference/statements/for-next-statement.md) döngü. İçinde `ListEvenNumbers` yöntemi, her yinelemesinden `For Each` deyimi gövde oluşturur diğerine geçer yineleyici yöntemine bir çağrı `Yield` deyimi.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Koleksiyon başlatıcıları](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)  
 [Programlama Kavramları (Visual Basic)](../../../visual-basic/programming-guide/concepts/index.md)  
 [Option Strict deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [LINQ to nesneler (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
 [Paralel LINQ (PLINQ)](../../../standard/parallel-programming/parallel-linq-plinq.md)  
 [Koleksiyonlar ve veri yapıları](../../../standard/collections/index.md)  
 [Oluşturma ve koleksiyonları düzenleme](http://msdn.microsoft.com/en-us/2065398e-eb1a-4821-9188-75f16e42e069)  
 [Koleksiyon sınıfı seçme](../../../standard/collections/selecting-a-collection-class.md)  
 [Karşılaştırmalar ve sıralamalar](../../../standard/collections/comparisons-and-sorts-within-collections.md)  
 [Genel koleksiyonları ne zaman kullanılacağı](../../../standard/collections/when-to-use-generic-collections.md)
