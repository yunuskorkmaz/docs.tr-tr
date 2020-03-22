---
title: Koleksiyonlar
ms.date: 07/20/2015
ms.assetid: 5f7749f3-aaf2-4319-b63c-bfa72e1e2b7a
ms.openlocfilehash: ba16d04e781bcf69356b1f603d92e104816a0860
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400829"
---
# <a name="collections-visual-basic"></a>Koleksiyonlar (Visual Basic)

Birçok uygulama için, ilgili nesnelerin grupları oluşturmak ve yönetmek istiyorsunuz. Nesneleri gruplandırmanın iki yolu vardır: nesne dizileri oluşturarak ve nesnelerin koleksiyonlarını oluşturarak.

Diziler, güçlü bir şekilde yazılan sabit sayıda nesne oluşturmak ve bunlarla çalışmak için en kullanışlıdır. Diziler hakkında daha fazla bilgi için [Diziler'e](../../../visual-basic/programming-guide/language-features/arrays/index.md)bakın.

Koleksiyonlar, nesne gruplarıyla çalışmak için daha esnek bir yol sağlar. Dizilerin aksine, birlikte çalıştığınız nesne grubu, uygulamanın gereksinimleri değiştikçe dinamik olarak büyüyebilir ve küçülebilir. Bazı koleksiyonlar için, anahtarı kullanarak nesneyi hızla alabilmeniz için koleksiyona koyduğunuz herhangi bir nesneye bir anahtar atayabilirsiniz.

Koleksiyon bir sınıftır, bu nedenle bu koleksiyona öğe eklemeden önce sınıfın bir örneğini bildirmeniz gerekir.

Koleksiyonunuz yalnızca bir veri türüöğeleri içeriyorsa, <xref:System.Collections.Generic?displayProperty=nameWithType> ad alanındaki sınıflardan birini kullanabilirsiniz. Genel bir koleksiyon, türü başka bir veri türünün eklenmeyecek şekilde tür güvenliğini zorlar. Genel bir koleksiyondan bir öğe aldığınızda, öğe türünü belirlemeniz veya dönüştürmeniz gerekmez.

> [!NOTE]
> Bu konuyla ilgili örnekler için, dış `System.Collections.Generic` `System.Linq` mekan için [Aktarım](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) deyimleri ve ad alanları içerir.

<a name="BKMK_SimpleCollection"></a>

## <a name="using-a-simple-collection"></a>Basit Bir Koleksiyon Kullanma

Bu bölümdeki örnekler, <xref:System.Collections.Generic.List%601> güçlü bir şekilde yazılan nesneler listesiyle çalışmanızı sağlayan genel sınıfı kullanır.

Aşağıdaki örnek, dizeleri bir listesini oluşturur ve sonra her biri için kullanarak dizeleri ile yineler [... Sıradaki](../../../visual-basic/language-reference/statements/for-each-next-statement.md) ifade.

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

Bir koleksiyonun içeriği önceden biliniyorsa, koleksiyonun başlatılması için bir *koleksiyon başlatılması* nı kullanabilirsiniz. Daha fazla bilgi için [Bkz. Collection Initializers](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).

Aşağıdaki örnek, koleksiyona öğe eklemek için bir koleksiyon başlatılması nın kullanılması dışında, önceki örnekle aynıdır.

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

Bir For kullanabilirsiniz [... Bir sonraki](../../../visual-basic/language-reference/statements/for-next-statement.md) deyim `For Each` yerine bir koleksiyon aracılığıyla yinelemek için bir deyim. Bunu dizin konumuna göre koleksiyon öğelerine erişerek gerçekleştirirsiniz. Elementlerin dizini 0 ile başlar ve eksi 1 öğe sayısıyla biter.

Aşağıdaki örnek, bir koleksiyonun öğelerini yerine `For…Next` kullanarak `For Each`yineler.

```vb
Dim salmons As New List(Of String) From
    {"chinook", "coho", "pink", "sockeye"}

For index = 0 To salmons.Count - 1
    Console.Write(salmons(index) & " ")
Next
'Output: chinook coho pink sockeye
```

Aşağıdaki örnek, kaldırılacak nesneyi belirterek bir öğeyi koleksiyondan kaldırır.

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

Aşağıdaki örnek, öğeleri genel bir listeden kaldırır. Bir `For Each` deyim yerine, bir [For... Sonraki](../../../visual-basic/language-reference/statements/for-next-statement.md) deyim inen sırada yineler kullanılır. Bunun nedeni, <xref:System.Collections.Generic.List%601.RemoveAt%2A> yöntemin kaldırılan öğeden sonraki öğelerin daha düşük bir dizin değerine sahip olmasıdır.

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

Öğelerin türü <xref:System.Collections.Generic.List%601>için, kendi sınıf tanımlayabilirsiniz. Aşağıdaki örnekte, `Galaxy` kodda <xref:System.Collections.Generic.List%601> kullanılan sınıf tanımlanır.

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

## <a name="kinds-of-collections"></a>Koleksiyon Çeşitleri

Birçok ortak koleksiyon .NET Framework tarafından sağlanır. Her koleksiyon türü belirli bir amaç için tasarlanmıştır.

Ortak toplama sınıflarından bazıları bu bölümde açıklanmıştır:

- <xref:System.Collections.Generic> sınıflar

- <xref:System.Collections.Concurrent> sınıflar

- <xref:System.Collections> sınıflar

- Visual `Collection` Basic sınıfı

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

Ek bilgi için, [Sık Kullanılan Koleksiyon Türleri](../../../standard/collections/commonly-used-collection-types.md), Toplama Sınıfı [Seçme](../../../standard/collections/selecting-a-collection-class.md)ve <xref:System.Collections.Generic?displayProperty=nameWithType>.

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

<a name="BKMK_VisualBasic"></a>

### <a name="visual-basic-collection-class"></a>Visual Basic Toplama Sınıfı

Sayısal dizin veya <xref:Microsoft.VisualBasic.Collection> `String` anahtar kullanarak bir koleksiyon öğesine erişmek için Visual Basic sınıfını kullanabilirsiniz. Bir anahtar belirterek veya belirtmeden bir koleksiyon nesnesine öğe ekleyebilirsiniz. Bir öğeyi anahtarı olmadan eklerseniz, öğeye erişmek için sayısal dizinini kullanmanız gerekir.

Visual Basic `Collection` sınıfı tüm öğelerini `Object`tür olarak depolar, böylece herhangi bir veri türünden bir öğe ekleyebilirsiniz. Uygunsuz veri türlerinin eklenmesine karşı koruma yoktur.

Visual Basic `Collection` sınıfını kullandığınızda, koleksiyondaki ilk öğenin dizin1'dir. Bu, başlangıç dizininin 0 olduğu .NET Framework toplama sınıflarından farklıdır.

Mümkün olduğunda, Visual Basic <xref:System.Collections.Generic?displayProperty=nameWithType> <xref:System.Collections.Concurrent> `Collection` sınıfı yerine ad alanında veya ad alanında genel koleksiyonları kullanmanız gerekir.

Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Collection>.

<a name="BKMK_KeyValuePairs"></a>

## <a name="implementing-a-collection-of-keyvalue-pairs"></a>Anahtar/Değer Çiftleri Koleksiyonunu Uygulama

Genel <xref:System.Collections.Generic.Dictionary%602> koleksiyon, her öğenin anahtarını kullanarak koleksiyondaki öğelere erişmenizi sağlar. Sözlükteki her ek bir değer ve ilişkili anahtardan oluşur. `Dictionary` Sınıf karma tablo olarak uygulandığından, anahtarını kullanarak bir değer almak hızlıdır.

Aşağıdaki örnek bir `Dictionary` koleksiyon oluşturur ve bir `For Each` deyim kullanarak sözlük teyidi.

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

Bunun `Dictionary` yerine, koleksiyonu oluşturmak için bir koleksiyon baş `BuildDictionary` harflerini kullanmak için, aşağıdaki yöntemle ve `AddToDictionary` yöntemleri değiştirebilirsiniz.

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

Aşağıdaki örnekte, <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> bir <xref:System.Collections.Generic.Dictionary%602.Item%2A> öğeyi `Dictionary` anahtarla hızlı bir şekilde bulmak için yöntem ve özellik kullanır. Özellik, `Item` Visual Basic'teki `elements` `elements(symbol)` kodu kullanarak koleksiyondaki bir öğeye erişmenizi sağlar.

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

Aşağıdaki örnek yerine <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> yöntemi hızlı bir şekilde anahtara göre bir öğe bulmak kullanır.

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

## <a name="using-linq-to-access-a-collection"></a>Koleksiyona Erişmek için LINQ kullanma

LINQ (Dil-Tümleşik Sorgu) koleksiyonlara erişmek için kullanılabilir. LINQ sorguları filtreleme, sıralama ve gruplandırma özellikleri sağlar. Daha fazla bilgi için [Visual Basic'te LINQ ile başlarken](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)bakın.

Aşağıdaki örnek, genel `List`bir karşı bir LINQ sorgusu çalıştırın. LINQ sorgusu sonuçları içeren farklı bir koleksiyon döndürür.

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

## <a name="sorting-a-collection"></a>Koleksiyonu Sıralama

Aşağıdaki örnek, bir koleksiyonu sıralama yordamını göstermektedir. Örnek, bir <xref:System.Collections.Generic.List%601>' `Car` de depolanan sınıfın örneklerini sıralar Sınıf, `Car` yöntemin <xref:System.IComparable%601> <xref:System.IComparable%601.CompareTo%2A> uygulanmasını gerektiren arabirimi uygular.

Yönteme <xref:System.IComparable%601.CompareTo%2A> yapılan her çağrı, sıralama için kullanılan tek bir karşılaştırma yapar. `CompareTo` Yöntemdeki kullanıcı tarafından yazılan kod, geçerli nesnenin başka bir nesneyle her karşılaştırılması için bir değer döndürür. Dönen değer, geçerli nesne diğer nesneden küçükse, geçerli nesne diğer nesneden büyükse sıfırdan büyük, eşitse sıfırdır. Bu, kodda daha büyük, daha az ve eşit ölçütleri tanımlamanızı sağlar.

`ListCars` Yöntemde, `cars.Sort()` deyim listeyi sıralar. Bu çağrı <xref:System.Collections.Generic.List%601.Sort%2A> yöntemine <xref:System.Collections.Generic.List%601> neden `CompareTo` olan `Car` yöntemin `List`nesneler için otomatik olarak çağrılması.

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

## <a name="defining-a-custom-collection"></a>Özel Koleksiyon Tanımlama

Bir koleksiyonu <xref:System.Collections.Generic.IEnumerable%601> veya <xref:System.Collections.IEnumerable> arabirimi uygulayarak tanımlayabilirsiniz. Daha fazla bilgi için [bkz.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hwyysy67(v=vs.100))

Özel bir koleksiyon tanımlayabiliyor olsanız da, bu konunun başlarında [Koleksiyon Türleri'nde](#kinds-of-collections) açıklanan .NET Framework'de yer alan koleksiyonları kullanmak genellikle daha iyidir.

Aşağıdaki örnek, adlı `AllColors`özel bir koleksiyon sınıfı tanımlar. Bu sınıf, <xref:System.Collections.IEnumerable> yöntemin <xref:System.Collections.IEnumerable.GetEnumerator%2A> uygulanmasını gerektiren arabirimi uygular.

Yöntem `GetEnumerator` sınıfın bir örneğini `ColorEnumerator` döndürür. `ColorEnumerator`özelliğin, <xref:System.Collections.IEnumerator> <xref:System.Collections.IEnumerator.MoveNext%2A> yöntemin ve <xref:System.Collections.IEnumerator.Reset%2A> <xref:System.Collections.IEnumerator.Current%2A> yöntemin uygulanmasını gerektiren arabirimi uygular.

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

Bir *yineleme,* bir koleksiyon üzerinde özel yineleme gerçekleştirmek için kullanılır. Bir yineleyici bir yöntem veya `get` erişimci olabilir. Bir yineleyici, koleksiyonun her öğesini birer birer döndürmek için [bir Verim](../../../visual-basic/language-reference/statements/yield-statement.md) deyimi kullanır.

Her biri için bir kullanarak bir yineleyici arama [... Sıradaki](../../../visual-basic/language-reference/statements/for-each-next-statement.md) ifade. Döngünün `For Each` her yinelemesi yineleyiciyi çağırır. Bir `Yield` deyim yineleyicide ulaşıldığında, bir ifade döndürülür ve koddaki geçerli konum korunur. Yürütme, yineleyici çağrıldığında bu konumdan yeniden başlatılır.

Daha fazla bilgi için [Bkz. Yineleyiciler (Visual Basic)](../../../visual-basic/programming-guide/concepts/iterators.md).

Aşağıdaki örnekte bir yineleyici yöntemi kullanır. Yineleyici yöntemi bir For `Yield` içinde bir deyimi vardır [... Bir sonraki](../../../visual-basic/language-reference/statements/for-next-statement.md) döngü. `ListEvenNumbers` Yöntemde, deyim gövdesinin `For Each` her yinelemesi, bir sonraki `Yield` deyime devam eden yineleyici yöntemine bir çağrı oluşturur.

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
- [Nesnelere LINQ (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [Paralel LINQ (PLINQ)](../../../standard/parallel-programming/parallel-linq-plinq.md)
- [Koleksiyonlar ve Veri Yapıları](../../../standard/collections/index.md)
- [Koleksiyon Sınıfı Seçme](../../../standard/collections/selecting-a-collection-class.md)
- [Koleksiyonlardaki Karşılaştırmalar ve Sıralamalar](../../../standard/collections/comparisons-and-sorts-within-collections.md)
- [Genel Koleksiyonlar Ne Zaman Kullanılır?](../../../standard/collections/when-to-use-generic-collections.md)
