---
title: Yineleyiciler
ms.date: 07/20/2015
ms.assetid: f26b5c1e-fe9d-4004-b287-da7919d717ae
ms.openlocfilehash: e638d35aeb86837d91fb14681d300772e3c2375a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410935"
---
# <a name="iterators-visual-basic"></a>Yineleyiciler (Visual Basic)

Bir *Yineleyici* , listeler ve diziler gibi koleksiyonlardan dolaşmak için kullanılabilir.

Yineleyici yöntemi veya `get` erişimcisi bir koleksiyon üzerinde özel bir yineleme gerçekleştirir. Yineleyici yöntemi, her öğeyi birer birer döndürmek için [yield](../../language-reference/statements/yield-statement.md) ifadesini kullanır. Bir `Yield` ifadeye ulaşıldığında, koddaki geçerli konum hatırlanır. Bu konumdan, Yineleyici işlevinin bir sonraki çağrılışında yürütme yeniden başlatılır.

Her biri Için bir kullanarak istemci kodundan bir yineleyici kullanıyorsunuz [... Sonraki](../../language-reference/statements/for-each-next-statement.md) ifade veya BIR LINQ sorgusu kullanarak.

Aşağıdaki örnekte, döngünün ilk yinelemesi `For Each` yürütmenin `SomeNumbers` ilk ifadeye ulaşılana kadar yineleyici yönteminde devam etmesine neden olur `Yield` . Bu yineleme 3 değerini döndürür ve yineleyici yöntemindeki geçerli konum korunur. Döngünün bir sonraki yinelemesinde, yineleyici yönteminde yürütme kaldığınız yerden devam eder, bir ifadeye ulaştığında yeniden durdurulur `Yield` . Bu yineleme 5 değerini döndürür ve yineleyici yöntemindeki geçerli konum yeniden korunur. Yineleyici yönteminin sonuna ulaşıldığında döngü tamamlanır.

```vb
Sub Main()
    For Each number As Integer In SomeNumbers()
        Console.Write(number & " ")
    Next
    ' Output: 3 5 8
    Console.ReadKey()
End Sub

Private Iterator Function SomeNumbers() As System.Collections.IEnumerable
    Yield 3
    Yield 5
    Yield 8
End Function
```

Bir yineleyici yönteminin veya erişimcisinin dönüş türü `get` <xref:System.Collections.IEnumerable> ,, <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.IEnumerator> , veya olabilir <xref:System.Collections.Generic.IEnumerator%601> .

`Exit Function` `Return` Yinelemeyi sonlandırmak için bir veya ifadesini kullanabilirsiniz.

Visual Basic Yineleyici işlevi veya `get` erişimci bildirimi bir [Yineleyici](../../language-reference/modifiers/iterator.md) değiştiricisi içerir.

Yineleyiciler, Visual Studio 2012 ' de Visual Basic sunulmuştur.

**Bu konuda**

- [Basit Yineleyici](#BKMK_SimpleIterator)

- [Koleksiyon sınıfı oluşturma](#BKMK_CollectionClass)

- [TRY blokları](#BKMK_TryBlocks)

- [Anonim Yöntemler](#BKMK_AnonymousMethods)

- [Bir genel liste ile yineleyiciler kullanma](#BKMK_GenericList)

- [Sözdizimi bilgileri](#BKMK_SyntaxInformation)

- [Teknik Uygulama](#BKMK_Technical)

- [Yineleyicilerin kullanımı](#BKMK_UseOfIterators)

> [!NOTE]
> Konunun basit Yineleyici örneği hariç tüm örnekleri için, [Imports](../../language-reference/statements/imports-statement-net-namespace-and-type.md) `System.Collections` ve ad alanları için Imports deyimlerini ekleyin `System.Collections.Generic` .

## <a name="simple-iterator"></a><a name="BKMK_SimpleIterator"></a>Basit Yineleyici

Aşağıdaki örnek, Için içinde olan tek bir `Yield` ifadeye sahiptir [... Sonraki](../../language-reference/statements/for-next-statement.md) döngü. ' De `Main` , `For Each` ifade gövdesinin her yinelemesi bir sonraki ifadeye devam eden Yineleyici işlevine bir çağrı oluşturur `Yield` .

```vb
Sub Main()
    For Each number As Integer In EvenSequence(5, 18)
        Console.Write(number & " ")
    Next
    ' Output: 6 8 10 12 14 16 18
    Console.ReadKey()
End Sub

Private Iterator Function EvenSequence(
ByVal firstNumber As Integer, ByVal lastNumber As Integer) _
As System.Collections.Generic.IEnumerable(Of Integer)

    ' Yield even numbers in the range.
    For number As Integer = firstNumber To lastNumber
        If number Mod 2 = 0 Then
            Yield number
        End If
    Next
End Function
```

## <a name="creating-a-collection-class"></a><a name="BKMK_CollectionClass"></a>Koleksiyon sınıfı oluşturma

Aşağıdaki örnekte, `DaysOfTheWeek` sınıfı <xref:System.Collections.IEnumerable> bir yöntemi gerektiren arabirimini uygular <xref:System.Collections.IEnumerable.GetEnumerator%2A> . Derleyici, `GetEnumerator` bir döndüren yöntemini dolaylı olarak çağırır <xref:System.Collections.IEnumerator> .

`GetEnumerator`Yöntemi, yöntemini kullanarak her bir dizeyi birer birer döndürür `Yield` ve `Iterator` işlev bildiriminde bir değiştirici olur.

```vb
Sub Main()
    Dim days As New DaysOfTheWeek()
    For Each day As String In days
        Console.Write(day & " ")
    Next
    ' Output: Sun Mon Tue Wed Thu Fri Sat
    Console.ReadKey()
End Sub

Private Class DaysOfTheWeek
    Implements IEnumerable

    Public days =
        New String() {"Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat"}

    Public Iterator Function GetEnumerator() As IEnumerator _
        Implements IEnumerable.GetEnumerator

        ' Yield each day of the week.
        For i As Integer = 0 To days.Length - 1
            Yield days(i)
        Next
    End Function
End Class
```

Aşağıdaki örnek, `Zoo` hayvanlar koleksiyonunu içeren bir sınıf oluşturur.

`For Each`Sınıf örneğine () başvuran ifade, `theZoo` yöntemi örtük olarak çağırır `GetEnumerator` . `For Each` `Birds` Ve özelliklerine başvuran deyimler `Mammals` `AnimalsForType` adlandırılmış yineleyici yöntemini kullanır.

```vb
Sub Main()
    Dim theZoo As New Zoo()

    theZoo.AddMammal("Whale")
    theZoo.AddMammal("Rhinoceros")
    theZoo.AddBird("Penguin")
    theZoo.AddBird("Warbler")

    For Each name As String In theZoo
        Console.Write(name & " ")
    Next
    Console.WriteLine()
    ' Output: Whale Rhinoceros Penguin Warbler

    For Each name As String In theZoo.Birds
        Console.Write(name & " ")
    Next
    Console.WriteLine()
    ' Output: Penguin Warbler

    For Each name As String In theZoo.Mammals
        Console.Write(name & " ")
    Next
    Console.WriteLine()
    ' Output: Whale Rhinoceros

    Console.ReadKey()
End Sub

Public Class Zoo
    Implements IEnumerable

    ' Private members.
    Private animals As New List(Of Animal)

    ' Public methods.
    Public Sub AddMammal(ByVal name As String)
        animals.Add(New Animal With {.Name = name, .Type = Animal.TypeEnum.Mammal})
    End Sub

    Public Sub AddBird(ByVal name As String)
        animals.Add(New Animal With {.Name = name, .Type = Animal.TypeEnum.Bird})
    End Sub

    Public Iterator Function GetEnumerator() As IEnumerator _
        Implements IEnumerable.GetEnumerator

        For Each theAnimal As Animal In animals
            Yield theAnimal.Name
        Next
    End Function

    ' Public members.
    Public ReadOnly Property Mammals As IEnumerable
        Get
            Return AnimalsForType(Animal.TypeEnum.Mammal)
        End Get
    End Property

    Public ReadOnly Property Birds As IEnumerable
        Get
            Return AnimalsForType(Animal.TypeEnum.Bird)
        End Get
    End Property

    ' Private methods.
    Private Iterator Function AnimalsForType( _
    ByVal type As Animal.TypeEnum) As IEnumerable
        For Each theAnimal As Animal In animals
            If (theAnimal.Type = type) Then
                Yield theAnimal.Name
            End If
        Next
    End Function

    ' Private class.
    Private Class Animal
        Public Enum TypeEnum
            Bird
            Mammal
        End Enum

        Public Property Name As String
        Public Property Type As TypeEnum
    End Class
End Class
```

## <a name="try-blocks"></a><a name="BKMK_TryBlocks"></a>TRY blokları

Visual Basic `Yield` try bloğundaki bir ifadeye izin verir `Try` [... Yakala... Finally ekstresi](../../language-reference/statements/try-catch-finally-statement.md). `Try`Bir deyime sahip bir blok `Yield` blokları olabilir `Catch` ve bir bloğuna sahip olabilir `Finally` .

Aşağıdaki örnek, `Try` `Catch` `Finally` bir yineleyici işlevindeki, ve bloklarını içerir. `Finally`Yineleyici işlevindeki blok `For Each` yineleme bitmeden önce yürütülür.

```vb
Sub Main()
    For Each number As Integer In Test()
        Console.WriteLine(number)
    Next
    Console.WriteLine("For Each is done.")

    ' Output:
    '  3
    '  4
    '  Something happened. Yields are done.
    '  Finally is called.
    '  For Each is done.
    Console.ReadKey()
End Sub

Private Iterator Function Test() As IEnumerable(Of Integer)
    Try
        Yield 3
        Yield 4
        Throw New Exception("Something happened. Yields are done.")
        Yield 5
        Yield 6
    Catch ex As Exception
        Console.WriteLine(ex.Message)
    Finally
        Console.WriteLine("Finally is called.")
    End Try
End Function
```

Bir `Yield` ifade bir `Catch` blok veya blok içinde olamaz `Finally` .

`For Each`Gövde (yineleyici yöntemi yerine) bir özel durum oluşturursa, `Catch` Yineleyici işlevindeki bir blok yürütülmez, ancak `Finally` Yineleyici işlevindeki bir blok yürütülür. `Catch`Yineleyici işlevi içindeki bir blok yalnızca Yineleyici işlevinin içinde oluşan özel durumları yakalar.

## <a name="anonymous-methods"></a><a name="BKMK_AnonymousMethods"></a>Anonim Yöntemler

Visual Basic, anonim bir işlev bir yineleyici işlevi olabilir. Aşağıdaki örnek bunu göstermektedir.

```vb
Dim iterateSequence = Iterator Function() _
                      As IEnumerable(Of Integer)
                          Yield 1
                          Yield 2
                      End Function

For Each number As Integer In iterateSequence()
    Console.Write(number & " ")
Next
' Output: 1 2
Console.ReadKey()
```

Aşağıdaki örnek, bağımsız değişkenleri doğrulayan Yineleyici olmayan bir yönteme sahiptir. Yöntemi, koleksiyon öğelerini açıklayan bir anonim yineleyicinin sonucunu döndürür.

```vb
Sub Main()
    For Each number As Integer In GetSequence(5, 10)
        Console.Write(number & " ")
    Next
    ' Output: 5 6 7 8 9 10
    Console.ReadKey()
End Sub

Public Function GetSequence(ByVal low As Integer, ByVal high As Integer) _
As IEnumerable
    ' Validate the arguments.
    If low < 1 Then
        Throw New ArgumentException("low is too low")
    End If
    If high > 140 Then
        Throw New ArgumentException("high is too high")
    End If

    ' Return an anonymous iterator function.
    Dim iterateSequence = Iterator Function() As IEnumerable
                              For index = low To high
                                  Yield index
                              Next
                          End Function
    Return iterateSequence()
End Function
```

Doğrulama işlemi Yineleyici işlevi içinde ise, gövdenin ilk yinelemesinin başlangıcına kadar doğrulama gerçekleştirilemez `For Each` .

## <a name="using-iterators-with-a-generic-list"></a><a name="BKMK_GenericList"></a>Bir genel liste ile yineleyiciler kullanma

Aşağıdaki örnekte, `Stack(Of T)` Genel sınıf <xref:System.Collections.Generic.IEnumerable%601> genel arabirimini uygular. `Push`Yöntemi, türü bir diziye değerler atar `T` . <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>Yöntemi, ifadesini kullanarak dizi değerlerini döndürür `Yield` .

Genel yöntemin yanı sıra <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> genel olmayan <xref:System.Collections.IEnumerable.GetEnumerator%2A> yöntemin de uygulanması gerekir. Bunun nedeni, <xref:System.Collections.Generic.IEnumerable%601> öğesinden devralmasıdır <xref:System.Collections.IEnumerable> . Genel olmayan uygulama genel uygulamaya erteler.

Örnek, aynı veri topluluğunda tekrarların çeşitli yollarını desteklemek için adlandırılmış yineleyiciler kullanır. Bu adlandırılmış yineleyiciler, `TopToBottom` ve `BottomToTop` özellikleridir ve `TopN` yöntemidir.

`BottomToTop`Özellik bildirimi `Iterator` anahtar sözcüğünü içerir.

```vb
Sub Main()
    Dim theStack As New Stack(Of Integer)

    ' Add items to the stack.
    For number As Integer = 0 To 9
        theStack.Push(number)
    Next

    ' Retrieve items from the stack.
    ' For Each is allowed because theStack implements
    ' IEnumerable(Of Integer).
    For Each number As Integer In theStack
        Console.Write("{0} ", number)
    Next
    Console.WriteLine()
    ' Output: 9 8 7 6 5 4 3 2 1 0

    ' For Each is allowed, because theStack.TopToBottom
    ' returns IEnumerable(Of Integer).
    For Each number As Integer In theStack.TopToBottom
        Console.Write("{0} ", number)
    Next
    Console.WriteLine()
    ' Output: 9 8 7 6 5 4 3 2 1 0

    For Each number As Integer In theStack.BottomToTop
        Console.Write("{0} ", number)
    Next
    Console.WriteLine()
    ' Output: 0 1 2 3 4 5 6 7 8 9

    For Each number As Integer In theStack.TopN(7)
        Console.Write("{0} ", number)
    Next
    Console.WriteLine()
    ' Output: 9 8 7 6 5 4 3

    Console.ReadKey()
End Sub

Public Class Stack(Of T)
    Implements IEnumerable(Of T)

    Private values As T() = New T(99) {}
    Private top As Integer = 0

    Public Sub Push(ByVal t As T)
        values(top) = t
        top = top + 1
    End Sub

    Public Function Pop() As T
        top = top - 1
        Return values(top)
    End Function

    ' This function implements the GetEnumerator method. It allows
    ' an instance of the class to be used in a For Each statement.
    Public Iterator Function GetEnumerator() As IEnumerator(Of T) _
        Implements IEnumerable(Of T).GetEnumerator

        For index As Integer = top - 1 To 0 Step -1
            Yield values(index)
        Next
    End Function

    Public Iterator Function GetEnumerator1() As IEnumerator _
        Implements IEnumerable.GetEnumerator

        Yield GetEnumerator()
    End Function

    Public ReadOnly Property TopToBottom() As IEnumerable(Of T)
        Get
            Return Me
        End Get
    End Property

    Public ReadOnly Iterator Property BottomToTop As IEnumerable(Of T)
        Get
            For index As Integer = 0 To top - 1
                Yield values(index)
            Next
        End Get
    End Property

    Public Iterator Function TopN(ByVal itemsFromTop As Integer) _
        As IEnumerable(Of T)

        ' Return less than itemsFromTop if necessary.
        Dim startIndex As Integer =
            If(itemsFromTop >= top, 0, top - itemsFromTop)

        For index As Integer = top - 1 To startIndex Step -1
            Yield values(index)
        Next
    End Function
End Class
```

## <a name="syntax-information"></a><a name="BKMK_SyntaxInformation"></a>Sözdizimi bilgileri

Yineleyici bir yöntem veya erişimci olarak gerçekleşebilir `get` . Bir olay, örnek Oluşturucu, statik oluşturucu veya statik yok edicisi içinde yineleyici olamaz.

Deyimdeki ifade türünden, `Yield` yineleyicinin dönüş türüne örtük bir dönüştürme bulunmalıdır.

Visual Basic, yineleyici yöntemi herhangi bir parametreye sahip olamaz `ByRef` .

Visual Basic, "yield" ayrılmış bir sözcük değildir ve yalnızca bir `Iterator` yöntemde veya erişimcisinde kullanıldığında özel anlamı vardır `get` .

## <a name="technical-implementation"></a><a name="BKMK_Technical"></a>Teknik uygulama

Bir yineleyici Yöntem olarak yazdığınızda, derleyici onu bir durum makinesi olan bir iç içe geçmiş sınıfa çevirir. Bu sınıf, `For Each...Next` istemci kodundaki döngü devam ettiğinde yineleyicinin konumunu izler.

Derleyicinin ne yaptığını görmek için, bir yineleyici yöntemi için oluşturulan Microsoft ara dil kodunu görüntülemek için ıldadsm. exe aracını kullanabilirsiniz.

Bir [sınıf](../../language-reference/statements/class-statement.md) veya [Yapı](../../language-reference/statements/structure-statement.md)için Yineleyici oluşturduğunuzda, tüm arabirimini uygulamanız gerekmez <xref:System.Collections.IEnumerator> . Derleyici yineleyiciyi algıladığında, `Current` `MoveNext` veya arabiriminin,, ve yöntemlerini otomatik olarak oluşturur `Dispose` <xref:System.Collections.IEnumerator> <xref:System.Collections.Generic.IEnumerator%601> .

Döngünün art arda her tekrarında `For Each…Next` (veya doğrudan çağrısının `IEnumerator.MoveNext` ), sonraki Yineleyici kod gövdesi önceki deyimden sonra devam eder `Yield` . Daha sonra `Yield` Yineleyici gövdesinin sonuna ulaşılana kadar veya bir `Exit Function` veya `Return` ifadesiyle karşılaşana kadar sonraki ifadeye devam eder.

Yineleyiciler <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> yöntemi desteklemez. Başlangıçtan yeniden yinelemek için yeni bir yineleyici edinmeniz gerekir.

Daha fazla bilgi için [Visual Basic dil belirtimine](../../reference/language-specification/index.md)bakın.

## <a name="use-of-iterators"></a><a name="BKMK_UseOfIterators"></a>Yineleyicilerin kullanımı

Yineleyiciler, `For Each` bir liste dizisini doldurmak için karmaşık kod kullanmanız gerektiğinde bir döngünün basitliğini korumanıza olanak sağlar. Bu, aşağıdakileri yapmak istediğinizde yararlı olabilir:

- İlk döngü yinelemeden sonra liste sırasını değiştirin `For Each` .

- Bir döngünün ilk yinelemesinden önce büyük bir listenin tam olarak yüklenmesini önleyin `For Each` . Tablo satırlarını toplu olarak yüklemek için disk belleğine alınmış bir getirme örneği. Diğer bir örnek <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> , .NET Framework içinde yineleyiciler uygulayan yöntemidir.

- Yineleyici içinde listenin oluşturulmasını yalıt. Yineleyici yönteminde, listeyi derleyip her sonucu bir döngüde sağlayabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic>
- <xref:System.Collections.Generic.IEnumerable%601>
- [For Each...Next Deyimi](../../language-reference/statements/for-each-next-statement.md)
- [Yield Deyimi](../../language-reference/statements/yield-statement.md)
- [Iterator](../../language-reference/modifiers/iterator.md)
