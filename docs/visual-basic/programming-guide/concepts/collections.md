---
title: Koleksiyonlar
ms.date: 07/20/2015
ms.assetid: 5f7749f3-aaf2-4319-b63c-bfa72e1e2b7a
ms.openlocfilehash: ba16d04e781bcf69356b1f603d92e104816a0860
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347089"
---
# <a name="collections-visual-basic"></a>Koleksiyonlar (Visual Basic)

Birçok uygulama için ilgili nesne grupları oluşturmak ve yönetmek istersiniz. Nesneleri gruplandırmanın iki yolu vardır: nesne dizileri oluşturarak ve nesne koleksiyonları oluşturarak.

Diziler, kesin olarak belirlenmiş sabit sayıda nesne oluşturmak ve bunlarla çalışmak için en yararlı seçenektir. Diziler hakkında daha fazla bilgi için bkz. [diziler](../../../visual-basic/programming-guide/language-features/arrays/index.md).

Koleksiyonlar, nesne gruplarıyla çalışmak için daha esnek bir yol sağlar. Dizilerden farklı olarak, çalıştığınız nesne grubu, uygulama değişikliğinin ihtiyaçlarına göre dinamik olarak büyüyebilir ve küçülebilir. Bazı koleksiyonlar için, anahtarı kullanarak nesneyi hızlı bir şekilde alabilmeniz için koleksiyona yerleştirdiğiniz herhangi bir nesneye bir anahtar atayabilirsiniz.

Koleksiyon bir sınıftır, bu nedenle bu koleksiyona öğe ekleyebilmeniz için önce sınıfın bir örneğini bildirmeniz gerekir.

Koleksiyonunuz yalnızca bir veri türünün öğelerini içeriyorsa, <xref:System.Collections.Generic?displayProperty=nameWithType> ad alanındaki sınıflardan birini kullanabilirsiniz. Genel bir koleksiyon, tür güvenliğini, başka bir veri türü eklenememesi için uygular. Genel koleksiyondan bir öğe aldığınızda, veri türünü belirlememek veya dönüştürmek zorunda değilsiniz.

> [!NOTE]
> Bu konudaki örnekler için, `System.Collections.Generic` ve `System.Linq` ad alanları için [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) deyimlerini ekleyin.

<a name="BKMK_SimpleCollection"></a>

## <a name="using-a-simple-collection"></a>Basit bir koleksiyon kullanma

Bu bölümdeki örneklerde, türü kesin belirlenmiş bir nesne listesiyle çalışmanıza olanak sağlayan genel <xref:System.Collections.Generic.List%601> sınıfını kullanın.

Aşağıdaki örnek, dizelerin bir listesini oluşturur ve sonra her biri Için bir kullanarak dizeler arasında yinelenir [... Sonraki](../../../visual-basic/language-reference/statements/for-each-next-statement.md) ifade.

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

Bir koleksiyonun içeriği önceden biliniyorsa, koleksiyonu başlatmak için bir *koleksiyon başlatıcısı* kullanabilirsiniz. Daha fazla bilgi için bkz. [koleksiyon başlatıcıları](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).

Aşağıdaki örnek, koleksiyona öğe eklemek için bir koleksiyon başlatıcısı kullanılması dışında, önceki örnekle aynıdır.

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

Için bir kullanabilirsiniz... [ ](../../../visual-basic/language-reference/statements/for-next-statement.md)Bir koleksiyon üzerinden yinelemek için bir `For Each` deyimin yerine Next ifadesinin. Bunu, koleksiyon öğelerine dizin konumuna erişerek gerçekleştirirsiniz. Öğelerin dizini 0 ' dan başlar ve öğe sayısı eksi 1 ' den sona erer.

Aşağıdaki örnek, `For Each`yerine `For…Next` kullanarak bir koleksiyonun öğeleri boyunca yinelenir.

```vb
Dim salmons As New List(Of String) From
    {"chinook", "coho", "pink", "sockeye"}

For index = 0 To salmons.Count - 1
    Console.Write(salmons(index) & " ")
Next
'Output: chinook coho pink sockeye
```

Aşağıdaki örnek, kaldırılacak nesneyi belirterek koleksiyondan bir öğeyi kaldırır.

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

Aşağıdaki örnek, genel bir listeden öğeleri kaldırır. `For Each`, Için a... [ ](../../../visual-basic/language-reference/statements/for-next-statement.md)Azalan sırada yinelenen bir sonraki ifade kullanılır. Bunun nedeni <xref:System.Collections.Generic.List%601.RemoveAt%2A> yöntemi kaldırılan bir öğeden sonra öğelerin daha düşük bir dizin değerine sahip olmasına neden olur.

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

<xref:System.Collections.Generic.List%601>öğe türü için kendi sınıfınızı de tanımlayabilirsiniz. Aşağıdaki örnekte, <xref:System.Collections.Generic.List%601> tarafından kullanılan `Galaxy` sınıfı kodda tanımlanmıştır.

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

Birçok ortak koleksiyon .NET Framework tarafından sağlanır. Her koleksiyon türü belirli bir amaç için tasarlanmıştır.

Ortak koleksiyon sınıflarından bazıları bu bölümde açıklanmıştır:

- <xref:System.Collections.Generic> sınıflar

- <xref:System.Collections.Concurrent> sınıflar

- <xref:System.Collections> sınıflar

- Visual Basic `Collection` sınıfı

<a name="BKMK_Generic"></a>

### <a name="systemcollectionsgeneric-classes"></a>System. Collections. Generic sınıfları

<xref:System.Collections.Generic> ad alanındaki sınıflardan birini kullanarak genel bir koleksiyon oluşturabilirsiniz. Genel bir koleksiyon, koleksiyondaki her öğe aynı veri türüne sahip olduğunda faydalıdır. Genel bir koleksiyon, yalnızca istenen veri türünün eklenmesine izin vererek güçlü yazma uygular.

Aşağıdaki tabloda <xref:System.Collections.Generic?displayProperty=nameWithType> ad alanının sık kullanılan sınıflarının bazıları listelenmektedir:

|Sınıf|Açıklama|
|---|---|
|<xref:System.Collections.Generic.Dictionary%602>|Anahtara göre düzenlenen anahtar/değer çiftleri koleksiyonunu temsil eder.|
|<xref:System.Collections.Generic.List%601>|Dizin tarafından erişilebilen nesnelerin listesini temsil eder. Listeleri aramak, sıralamak ve değiştirmek için yöntemler sağlar.|
|<xref:System.Collections.Generic.Queue%601>|Nesnelerin ilk, ilk çıkar (FıFO) koleksiyonunu temsil eder.|
|<xref:System.Collections.Generic.SortedList%602>|İlişkili <xref:System.Collections.Generic.IComparer%601> uygulamasına göre anahtara göre sıralanan anahtar/değer çiftleri koleksiyonunu temsil eder.|
|<xref:System.Collections.Generic.Stack%601>|Nesnelerin son, ilk çıkar (LıFO) koleksiyonunu temsil eder.|

Daha fazla bilgi için bkz. [yaygın olarak kullanılan koleksiyon türleri](../../../standard/collections/commonly-used-collection-types.md), [bir koleksiyon sınıfı seçme](../../../standard/collections/selecting-a-collection-class.md)ve <xref:System.Collections.Generic?displayProperty=nameWithType>.

<a name="BKMK_Concurrent"></a>

### <a name="systemcollectionsconcurrent-classes"></a>System. Collections. eşzamanlı sınıflar

.NET Framework 4 veya daha yeni bir sürümde, <xref:System.Collections.Concurrent> ad alanındaki koleksiyonlar, koleksiyon öğelerine birden çok iş parçacığından erişmek için verimli iş parçacığı güvenli işlemleri sağlar.

<xref:System.Collections.Concurrent> ad alanındaki sınıflar, koleksiyona aynı anda birden çok iş parçacığı eriştiği zaman, <xref:System.Collections.Generic?displayProperty=nameWithType> ve <xref:System.Collections?displayProperty=nameWithType> ad alanlarında karşılık gelen türler yerine kullanılmalıdır. Daha fazla bilgi için bkz. [Iş parçacığı güvenli koleksiyonlar](../../../standard/collections/thread-safe/index.md) ve <xref:System.Collections.Concurrent>.

<xref:System.Collections.Concurrent> ad alanına eklenen bazı sınıflar <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>ve <xref:System.Collections.Concurrent.ConcurrentStack%601>.

<a name="BKMK_Collections"></a>

### <a name="systemcollections-classes"></a>System. Collections sınıfları

<xref:System.Collections?displayProperty=nameWithType> ad alanındaki sınıflar öğeleri özel olarak yazılmış nesneler olarak depolamaz, ancak `Object`türündeki nesneler.

Mümkün olduğunda, <xref:System.Collections.Generic?displayProperty=nameWithType> ad alanındaki genel koleksiyonları veya `System.Collections` ad alanındaki eski türler yerine <xref:System.Collections.Concurrent> ad alanını kullanmanız gerekir.

Aşağıdaki tabloda `System.Collections` ad alanında sık kullanılan sınıfların bazıları listelenmektedir:

|Sınıf|Açıklama|
|---|---|
|<xref:System.Collections.ArrayList>|Boyutu dinamik olarak gerektiği şekilde arttığı bir nesne dizisini temsil eder.|
|<xref:System.Collections.Hashtable>|Anahtarın karma koduna göre düzenlenmiş anahtar/değer çiftleri koleksiyonunu temsil eder.|
|<xref:System.Collections.Queue>|Nesnelerin ilk, ilk çıkar (FıFO) koleksiyonunu temsil eder.|
|<xref:System.Collections.Stack>|Nesnelerin son, ilk çıkar (LıFO) koleksiyonunu temsil eder.|

<xref:System.Collections.Specialized> ad alanı, yalnızca dize toplamaları ve bağlantılı liste ve karma sözlük gibi özelleştirilmiş ve kesin tür belirtilmiş koleksiyon sınıfları sağlar.

<a name="BKMK_VisualBasic"></a>

### <a name="visual-basic-collection-class"></a>Visual Basic Collection sınıfı

Sayısal bir dizin veya `String` anahtarı kullanarak bir koleksiyon öğesine erişmek için Visual Basic <xref:Microsoft.VisualBasic.Collection> sınıfını kullanabilirsiniz. Bir koleksiyon nesnesine, anahtar belirtmeden ya da belirtmeden öğe ekleyebilirsiniz. Anahtar içermeyen bir öğe eklerseniz, ona erişmek için sayısal dizinini kullanmanız gerekir.

Visual Basic `Collection` sınıfı tüm öğelerini tür `Object`olarak depolar, böylece herhangi bir veri türü için bir öğe ekleyebilirsiniz. Eklenmekte olan uygunsuz veri türlerine karşı bir koruma yoktur.

Visual Basic `Collection` sınıfını kullandığınızda, bir koleksiyondaki ilk öğenin dizini 1 ' dir. Bu, Başlangıç dizininin 0 olduğu .NET Framework koleksiyon sınıflarından farklıdır.

Mümkün olduğunda, <xref:System.Collections.Generic?displayProperty=nameWithType> ad alanındaki genel koleksiyonları veya Visual Basic `Collection` sınıfı yerine <xref:System.Collections.Concurrent> ad alanını kullanmanız gerekir.

Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Collection>.

<a name="BKMK_KeyValuePairs"></a>

## <a name="implementing-a-collection-of-keyvalue-pairs"></a>Anahtar/değer çiftleri koleksiyonu uygulama

<xref:System.Collections.Generic.Dictionary%602> genel koleksiyonu, her bir öğenin anahtarını kullanarak bir koleksiyondaki öğelere erişmenizi sağlar. Sözlüğe eklenen her ekleme bir değerden ve ilişkili anahtarından oluşur. `Dictionary` sınıfı bir karma tablo olarak uygulandığından, anahtarını kullanarak bir değerin alınması hızlıdır.

Aşağıdaki örnek bir `Dictionary` koleksiyonu oluşturur ve bir `For Each` ifadesini kullanarak sözlükten yinelenir.

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

Bunun yerine, `Dictionary` koleksiyonunu oluşturmak için bir koleksiyon başlatıcısı kullanmak için, `BuildDictionary` ve `AddToDictionary` yöntemlerini aşağıdaki yöntemle değiştirebilirsiniz.

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

Aşağıdaki örnek, bir öğeyi anahtara göre hızlı bir şekilde bulmak için `Dictionary` <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> yöntemini ve <xref:System.Collections.Generic.Dictionary%602.Item%2A> özelliğini kullanır. `Item` özelliği, Visual Basic `elements(symbol)` kodu kullanarak `elements` koleksiyonundaki bir öğeye erişmenizi sağlar.

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

Aşağıdaki örnek bunun yerine, bir öğeyi anahtara göre hızlı bir şekilde bulmak <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> yöntemini kullanır.

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

## <a name="using-linq-to-access-a-collection"></a>Koleksiyona erişmek için LINQ kullanma

LINQ (dil ile tümleşik sorgu), koleksiyonlara erişmek için kullanılabilir. LINQ sorguları filtreleme, sıralama ve gruplama özellikleri sağlar. Daha fazla bilgi için bkz. [VISUAL BASIC LINQ Ile çalışmaya](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)başlama.

Aşağıdaki örnek, bir genel `List`karşı bir LINQ sorgusu çalıştırır. LINQ sorgusu, sonuçları içeren farklı bir koleksiyon döndürür.

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

## <a name="sorting-a-collection"></a>Bir koleksiyonu sıralama

Aşağıdaki örnek bir koleksiyonu sıralamak için bir yordam gösterir. Örnek, bir <xref:System.Collections.Generic.List%601>depolanan `Car` sınıfının örneklerini sıralar. `Car` sınıfı, <xref:System.IComparable%601.CompareTo%2A> yönteminin uygulanması için <xref:System.IComparable%601> arabirimini uygular.

<xref:System.IComparable%601.CompareTo%2A> yöntemine yapılan her çağrı, sıralama için kullanılan tek bir karşılaştırma yapar. `CompareTo` yönteminde Kullanıcı tarafından yazılan kod, geçerli nesnenin her karşılaştırması için başka bir nesneyle ilgili bir değer döndürür. Geçerli nesne diğer nesneden daha küçükse döndürülen değer sıfırdan küçük, geçerli nesne diğer nesneden büyükse sıfırdan büyük ve eşitse sıfır. Bu, büyük, küçüktür ve eşittir ölçütlerine göre kod içinde tanımlamanızı sağlar.

`ListCars` yönteminde, `cars.Sort()` ifade listeyi sıralar. <xref:System.Collections.Generic.List%601> <xref:System.Collections.Generic.List%601.Sort%2A> yöntemine yapılan bu çağrı, `CompareTo` yönteminin `List``Car` nesneler için otomatik olarak çağrılmasına neden olur.

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

## <a name="defining-a-custom-collection"></a>Özel bir koleksiyon tanımlama

<xref:System.Collections.Generic.IEnumerable%601> veya <xref:System.Collections.IEnumerable> arabirimini uygulayarak bir koleksiyon tanımlayabilirsiniz. Daha fazla bilgi için bkz. [bir koleksiyonu numaralandırma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hwyysy67(v=vs.100)).

Özel bir koleksiyon tanımlamanızı mümkün olsa da, bu konunun önceki kısımlarında yer alan [koleksiyonlar türlerinde](#kinds-of-collections) açıklanan .NET Framework dahil edilen koleksiyonları kullanmak genellikle daha iyidir.

Aşağıdaki örnek, `AllColors`adlı bir özel koleksiyon sınıfını tanımlar. Bu sınıf, <xref:System.Collections.IEnumerable.GetEnumerator%2A> yönteminin uygulanması için <xref:System.Collections.IEnumerable> arabirimini uygular.

`GetEnumerator` yöntemi `ColorEnumerator` sınıfının bir örneğini döndürür. `ColorEnumerator`, <xref:System.Collections.IEnumerator.Current%2A> özelliğinin, <xref:System.Collections.IEnumerator.MoveNext%2A> yönteminin ve <xref:System.Collections.IEnumerator.Reset%2A> yönteminin uygulanması için <xref:System.Collections.IEnumerator> arabirimini uygular.

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

## <a name="iterators"></a>Yineleyiciler

Bir *Yineleyici* , bir koleksiyon üzerinde özel bir yineleme gerçekleştirmek için kullanılır. Yineleyici bir yöntem veya `get` erişimcisi olabilir. Bir yineleyici, tek seferde koleksiyonun her bir öğesini döndürmek için bir [yield](../../../visual-basic/language-reference/statements/yield-statement.md) ifadesini kullanır.

Her biri Için bir yineleyiciyi kullanarak bir yineleyici çağırın [... Sonraki](../../../visual-basic/language-reference/statements/for-each-next-statement.md) ifade. `For Each` döngüsünün her yinelemesi yineleyiciyi çağırır. Yineleyiciden bir `Yield` deyimine ulaşıldığında, bir ifade döndürülür ve koddaki geçerli konum korunur. Bu konumdan, yineleyici bir sonraki sefer çağrıldığında yürütme yeniden başlatılır.

Daha fazla bilgi için bkz. [yineleyiciler (Visual Basic)](../../../visual-basic/programming-guide/concepts/iterators.md).

Aşağıdaki örnek bir yineleyici yöntemi kullanır. Yineleyici yöntemi bir for... içinde olan bir `Yield` ifadeye sahiptir [... Sonraki](../../../visual-basic/language-reference/statements/for-next-statement.md) döngü. `ListEvenNumbers` yönteminde, `For Each` deyimin gövdesinin her yinelemesi, bir sonraki `Yield` ifadesine devam eden Yineleyici yöntemine bir çağrı oluşturur.

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
- [Programlama kavramları (Visual Basic)](../../../visual-basic/programming-guide/concepts/index.md)
- [Option Strict Deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [LINQ to Objects (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [Paralel LINQ (PLINQ)](../../../standard/parallel-programming/parallel-linq-plinq.md)
- [Koleksiyonlar ve Veri Yapıları](../../../standard/collections/index.md)
- [Koleksiyon Sınıfı Seçme](../../../standard/collections/selecting-a-collection-class.md)
- [Koleksiyonlardaki Karşılaştırmalar ve Sıralamalar](../../../standard/collections/comparisons-and-sorts-within-collections.md)
- [Genel Koleksiyonlar Ne Zaman Kullanılır?](../../../standard/collections/when-to-use-generic-collections.md)
