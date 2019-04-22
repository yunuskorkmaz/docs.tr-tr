---
title: Yineleyiciler (Visual Basic)
ms.date: 07/20/2015
ms.assetid: f26b5c1e-fe9d-4004-b287-da7919d717ae
ms.openlocfilehash: 313ce0c79a71af1b602ecd4ccc9bd0ebceb5696e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58820855"
---
# <a name="iterators-visual-basic"></a>Yineleyiciler (Visual Basic)
Bir *yineleyici* koleksiyonlarına listeler ve diziler gibi adım için kullanılabilir.  
  
 Yineleyici yöntemini veya `get` erişimci bir koleksiyon üzerinde özel yineleme gerçekleştirir. Yineleyici yöntemini kullanır [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) her öğeyi bir defada döndürmek için deyimi. Olduğunda bir `Yield` deyimine ulaşıldığında, kodun geçerli konumu anımsanacak. Yürütme, yineleyici işlevinin bir sonraki zamana o konumdan başlatılır.  
  
 Kullanarak bir yineleyici istemci kodundan kullanmak bir [her biri için... Sonraki](../../../visual-basic/language-reference/statements/for-each-next-statement.md) deyimini veya LINQ sorgusu kullanarak.  
  
 Aşağıdaki örnekte, ilk yinelemeyi `For Each` döngüye neden oluyor, devam etmek yürütme `SomeNumbers` yineleyici yöntemin ilk kadar `Yield` deyimine ulaşıldığında. Bu yineleme 3 değerini döndürür ve yineleyici yöntem geçerli konumu korunur. Döngüsünün sonraki yinelemesinde, yineleyici yöntemin yürütülmesine kadar devam eder, ulaştığında yeniden kaldığı bir `Yield` deyimi. Bu yineleme 5 değerini döndürür ve yineleyici yöntem geçerli konumu tekrar korunur. Yineleyici yöntemin sonuna ulaşıldığında döngüsünü tamamlar.  
  
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
  
 Bir yineleyici yöntemin dönüş türü veya `get` erişimcisi olabilir <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, veya <xref:System.Collections.Generic.IEnumerator%601>.  
  
 Kullanabileceğiniz bir `Exit Function` veya `Return` yinelemeyi sonlandırmak için deyimi.  
  
 Visual Basic yineleyici işlevi veya `get` erişimci bildirimi içeren bir [yineleyici](../../../visual-basic/language-reference/modifiers/iterator.md) değiştiricisi.  
  
 Visual Studio 2012'de Visual Basic'te yineleyiciler sunulur.  
  
 **Bu konudaki**  
  
-   [Basit bir yineleyici](#BKMK_SimpleIterator)  
  
-   [Koleksiyon sınıfı oluşturma](#BKMK_CollectionClass)  
  
-   [Try blokları](#BKMK_TryBlocks)  
  
-   [Anonim Metotlar](#BKMK_AnonymousMethods)  
  
-   [Yineleyiciler genel listeyle kullanma](#BKMK_GenericList)  
  
-   [Söz dizimi bilgileri](#BKMK_SyntaxInformation)  
  
-   [Teknik uygulama](#BKMK_Technical)  
  
-   [Yineleyicilerin kullanın](#BKMK_UseOfIterators)  
  
> [!NOTE]
>  Konusunda basit bir yineleyici örnek hariç tüm örnekler için dahil [içeri aktarmalar](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) deyimleri için `System.Collections` ve `System.Collections.Generic` ad alanları.  
  
## <a name="BKMK_SimpleIterator"></a> Basit bir yineleyici  
 Aşağıdaki örnek, tek bir sahip `Yield` içindeki bir [için... Sonraki](../../../visual-basic/language-reference/statements/for-next-statement.md) döngü. İçinde `Main`, her bir yinelemesini `For Each` diğerine geçer yineleyici işlevine bir çağrı oluşturur ve deyim gövdesi `Yield` deyimi.  
  
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
  
## <a name="BKMK_CollectionClass"></a> Koleksiyon sınıfı oluşturma  
 Aşağıdaki örnekte, `DaysOfTheWeek` sınıfının Implements <xref:System.Collections.IEnumerable> gerektiren arabirimi bir <xref:System.Collections.IEnumerable.GetEnumerator%2A> yöntemi. Derleyici örtük olarak çağırır `GetEnumerator` döndüren yöntemi bir <xref:System.Collections.IEnumerator>.  
  
 `GetEnumerator` Yöntemi döndürür her dize bir kerede kullanarak `Yield` deyimi ve bir `Iterator` işlev bildiriminde bir değiştiricidir.  
  
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
  
 Aşağıdaki örnek, oluşturur bir `Zoo` hayvanlar koleksiyonunu içeren sınıf.  
  
 `For Each` Sınıfı örneğini ifade deyimi (`theZoo`) örtük olarak çağırır `GetEnumerator` yöntemi. `For Each` Başvurmak ifadeleri `Birds` ve `Mammals` özellikleri kullanım `AnimalsForType` yineleyici yöntemin adı.  
  
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
  
## <a name="BKMK_TryBlocks"></a> Try blokları  
 Visual Basic sağlayan bir `Yield` deyiminde `Try` bloğu bir [deneyin... Catch... Finally deyimini](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md). A `Try` sahip blok bir `Yield` deyimi olabilir `Catch` engeller ve olabilir bir `Finally` blok.  
  
 Aşağıdaki örnek içerir `Try`, `Catch`, ve `Finally` bir yineleyici işlevinde engeller. `Finally` Yineleyici işlevindeki bloğun önce `For Each` yineleme biter.  
  
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
  
 A `Yield` deyimi içinde olamaz bir `Catch` blok veya `Finally` blok.  
  
 Varsa `For Each` gövdesi (yineleyici yöntemi) yerine bir özel durum oluşturursa bir `Catch` yineleyici işleve bloğunda yürütülmedi, ancak bir `Finally` yineleyici işleve bloğunda yürütülür. A `Catch` blok içinde bir yineleyici işlevi yineleyici işlevde oluşan özel durumları yakalar.  
  
## <a name="BKMK_AnonymousMethods"></a> Anonim yöntemler  
 Visual Basic'te bir anonim işlev bir yineleyici işlevi olabilir. Aşağıdaki örnek bunu göstermektedir.  
  
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
  
 Aşağıdaki örnek, bağımsız değişkenler doğrulayan bir yineleyici olmayan yöntemi vardır. Yöntemi, koleksiyon öğeleri açıklayan anonim bir yineleyici sonucunu döndürür.  
  
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
  
 Doğrulama bunun yerine, yineleyici işlevinin içinde ise, ilk yinelemeyi başlangıcını kadar doğrulama gerçekleştirilemiyor `For Each` gövdesi.  
  
## <a name="BKMK_GenericList"></a> Yineleyiciler genel listeyle kullanma  
 Aşağıdaki örnekte, `Stack(Of T)` genel bir sınıf uygulayan <xref:System.Collections.Generic.IEnumerable%601> genel arabirim. `Push` Yöntemi, bir dizi türüne değerleri atar `T`. <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> Yöntemi kullanarak dizi değerlerini döndürür `Yield` deyimi.  
  
 Genel yanı sıra <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> yöntem, genel olmayan <xref:System.Collections.IEnumerable.GetEnumerator%2A> yöntemi de uygulanmalı. Bunun nedeni, <xref:System.Collections.Generic.IEnumerable%601> devraldığı <xref:System.Collections.IEnumerable>. Genel olmayan uygulama için genel uygulamasını erteler.  
  
 Örneğin, verilerin aynı koleksiyon aracılığıyla yineleme çeşitli yöntemler desteklemek için adlandırılmış yineleyiciler kullanır. Bunlar yineleyiciler adlı `TopToBottom` ve `BottomToTop` özellikleri ve `TopN` yöntemi.  
  
 `BottomToTop` Özellik bildiriminde içerir `Iterator` anahtar sözcüğü.  
  
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
  
## <a name="BKMK_SyntaxInformation"></a> Söz dizimi bilgileri  
 Yineleyici yöntem olarak oluşabilir veya `get` erişimcisi. Bir yineleyiciyi bir olay, örnek oluşturucusu, statik oluşturucu veya statik yok Edicisi olamaz.  
  
 Örtük bir dönüştürme ifadesi türden bulunmalıdır `Yield` deyimi için dönüş türü yineleyici.  
  
 Yineleyici yöntem Visual Basic'te içeremez `ByRef` parametreleri.  
  
 Visual Basic'te "Yield" ayrılmış bir sözcük değildir ve yalnızca içinde kullanıldığında özel anlamı bir `Iterator` yöntemi veya `get` erişimcisi.  
  
## <a name="BKMK_Technical"></a> Teknik uygulama  
 Bir yöntem olarak bir yineleyici yazma olsa da, derleyici, iç içe geçmiş bir sınıf içinde başka bir deyişle, aslında bir Durum makinesi çevirir. Bu sınıf olarak uzun yineleyici konumunu izler `For Each...Next` istemci kodu döngüde devam eder.  
  
 Derleyicinin ne yaptığını görmek için bir yineleyici yöntem için oluşturulan Microsoft Ara dil kodunu görüntülemek için Ildasm.exe Aracı'nı kullanabilirsiniz.  
  
 İçin bir yineleyici oluşturduğunuzda bir [sınıfı](../../../csharp/language-reference/keywords/class.md) veya [yapı](../../../csharp/language-reference/keywords/struct.md), bütün uygulamak zorunda değilsiniz <xref:System.Collections.IEnumerator> arabirimi. Derleyici yineleyici algıladığında otomatik olarak oluşturduğu `Current`, `MoveNext`, ve `Dispose` yöntemlerinin <xref:System.Collections.IEnumerator> veya <xref:System.Collections.Generic.IEnumerator%601> arabirimi.  
  
 Her yinelemede üzerinde `For Each…Next` döngü (veya doğrudan arama `IEnumerator.MoveNext`), İleri yineleyici kod gövdesi önceki sonra sürdürür `Yield` deyimi. Daha sonra bir sonraki sürdürür `Yield` yineleyici gövdenin sonuna ulaşılana kadar bir deyimi veya kadar bir `Exit Function` veya `Return` deyimi karşılaştı.  
  
 Yineleyicileri desteklemez <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> yöntemi. Baştan yeniden yinelemek için yeni bir yineleyici edinmeniz gerekir.  
  
 Ek bilgi için bkz: [Visual Basic dil belirtimi](../../../visual-basic/reference/language-specification/index.md).  
  
## <a name="BKMK_UseOfIterators"></a> Yineleyicilerin kullanın  
 Yineleyiciler basitliğinin korumak etkinleştirme bir `For Each` döngü listesi sırası doldurmak için karmaşık kodlar kullanmanız gerektiğinde. Aşağıdakileri yapmak istediğinizde bu yararlı olabilir:  
  
-   Liste sonra ilk dağıtmayın `For Each` döngü yinelemesi.  
  
-   Büyük bir liste ilk yinelemeyi önce tam olarak yüklenmesini önlemek bir `For Each` döngü. Tablo satırları toplu yükleme için disk belleğine alınan fetch buna bir örnektir. Başka bir örnek <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> yineleyiciler .NET Framework içindeki uygulayan yöntemi.  
  
-   Yineleyici listesinde oluşturmaya kapsüller. Yineleyici yöntem içinde listesi oluşturmak ve ardından her bir döngü sonucu verecek.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic>
- <xref:System.Collections.Generic.IEnumerable%601>
- [For Each...Next Deyimi](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [Yield Deyimi](../../../visual-basic/language-reference/statements/yield-statement.md)
- [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md)
