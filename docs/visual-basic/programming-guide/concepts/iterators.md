---
title: Yineleyiciler (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: f26b5c1e-fe9d-4004-b287-da7919d717ae
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f02249f7f30d2cd6b43aa75530ace099286c7d7f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iterators-visual-basic"></a>Yineleyiciler (Visual Basic)
Bir *yineleyici* koleksiyonlarına listeler ve dizi gibi adım için kullanılabilir.  
  
 İterator yöntemi veya `get` erişimci gerçekleştiren özel bir yineleme içinde bir koleksiyon. İterator yöntemi kullanan [verim](../../../visual-basic/language-reference/statements/yield-statement.md) her öğeye aynı anda geri dönmek için deyimi. Zaman bir `Yield` deyimi ulaşıldığında geçerli kod konumda anımsanacak. Yürütme o konumdan yineleyici işlevi bir sonraki zamana yeniden başlatılır.  
  
 İle yineleyici istemci kodundan kullanmasını bir [For Each... Sonraki](../../../visual-basic/language-reference/statements/for-each-next-statement.md) deyimi, veya bir LINQ Sorgu kullanarak.  
  
 Aşağıdaki örnekte, ilk yinelemesi `For Each` döngüye neden olur, devam etmek yürütme `SomeNumbers` yineleyici yöntemi ilk kadar `Yield` deyimi ulaşıldığında. Bu yineleme 3 değerini döndürür ve yineleyici yöntemi geçerli konumda korunur. Döngü sonraki yinelemesinde nereden yürütülmeye yineleyici yönteminde ulaştığında yeniden durdurma kapalı, solda bir `Yield` deyimi. Bu yineleme 5 değerini döndürür ve yineleyici yöntemi geçerli konuma yeniden korunur. Yineleyici yönteminin sonuna gelindiğinde döngü tamamlar.  
  
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
  
 Yineleyici yönteminin dönüş türü veya `get` erişimci olabilir <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, veya <xref:System.Collections.Generic.IEnumerator%601>.  
  
 Kullanabileceğiniz bir `Exit Function` veya `Return` yinelemeyi sonlandırmak için deyimi.  
  
 Visual Basic yineleyici işlevi veya `get` erişimcisi bildirimi içeren bir [yineleyici](../../../visual-basic/language-reference/modifiers/iterator.md) değiştiricisi.  
  
 Yineleyiciler, Visual Studio 2012'de Visual Basic'te tanıtıldı.  
  
 **Bu konudaki**  
  
-   [Basit yineleyici](#BKMK_SimpleIterator)  
  
-   [Koleksiyon sınıfı oluşturma](#BKMK_CollectionClass)  
  
-   [Try blokları](#BKMK_TryBlocks)  
  
-   [Anonim yöntemler](#BKMK_AnonymousMethods)  
  
-   [Yineleyiciler genel bir listesi ile kullanma](#BKMK_GenericList)  
  
-   [Sözdizimi bilgileri](#BKMK_SyntaxInformation)  
  
-   [Teknik uygulama](#BKMK_Technical)  
  
-   [Yineleyiciler kullanımı](#BKMK_UseOfIterators)  
  
> [!NOTE]
>  Basit yineleyici örnek dışında konudaki tüm örnekleri için dahil [içeri aktarmalar](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) deyimleri için `System.Collections` ve `System.Collections.Generic` ad alanları.  
  
##  <a name="BKMK_SimpleIterator"></a>Basit yineleyici  
 Aşağıdaki örnek bir tek sahip `Yield` içinde deyimi bir [için... Sonraki](../../../visual-basic/language-reference/statements/for-next-statement.md) döngü. İçinde `Main`, her yinelemesinden `For Each` deyimi gövde oluşturur diğerine geçer yineleyici işlevi çağrısı `Yield` deyimi.  
  
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
  
##  <a name="BKMK_CollectionClass"></a>Koleksiyon sınıfı oluşturma  
 Aşağıdaki örnekte, `DaysOfTheWeek` uygulayan sınıf <xref:System.Collections.IEnumerable> gerektirir arabirimi bir <xref:System.Collections.IEnumerable.GetEnumerator%2A> yöntemi. Derleyici örtülü olarak çağırır `GetEnumerator` döndürür yöntemi bir <xref:System.Collections.IEnumerator>.  
  
 `GetEnumerator` Yöntemi döndürür her dize aynı anda kullanarak `Yield` deyimi ve bir `Iterator` değiştirici işlevi bildiriminde değil.  
  
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
  
 Aşağıdaki örnekte bir `Zoo` hayvanlar koleksiyonunu içeren sınıf.  
  
 `For Each` Sınıf örneğine başvuruda bulunan deyimi (`theZoo`) örtük olarak çağırır `GetEnumerator` yöntemi. `For Each` Başvurmak deyimleri `Birds` ve `Mammals` özelliklerini kullanmak `AnimalsForType` yineleyici yöntemi adı.  
  
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
  
##  <a name="BKMK_TryBlocks"></a>Try blokları  
 Visual Basic sağlayan bir `Yield` deyiminde `Try` , engelleme bir [deneyin... Catch... Finally ifadesi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md). A `Try` sahip blok bir `Yield` deyimi olabilir `Catch` engeller ve olabilir bir `Finally` bloğu.  
  
 Aşağıdaki örnek içerir `Try`, `Catch`, ve `Finally` bir yineleyici işlevinde engeller. `Finally` Yineleyici işlevi bloğunda yürütülmeden önce `For Each` yineleme biter.  
  
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
  
 A `Yield` deyimi içinde olamaz bir `Catch` blok veya `Finally` bloğu.  
  
 Varsa `For Each` gövdesi (yerine yineleyici yöntemi) bir özel durum oluşturur bir `Catch` yineleyici işlevi bloğunda yürütülmez, ancak bir `Finally` yineleyici işlevi bloğunda gerçekleştirilir. A `Catch` yineleyici işlevi bloğunda yineleyici işlevinin içinde oluşan özel durumlarını yakalar.  
  
##  <a name="BKMK_AnonymousMethods"></a>Anonim yöntemler  
 Visual Basic'te bir yineleyici işlevi adsız bir işlev olabilir. Aşağıdaki örnek bunu göstermektedir.  
  
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
  
 Aşağıdaki örnek bağımsız değişkenler doğrulayan bir yineleyici olmayan yöntemi vardır. Yöntemi, koleksiyon öğeleri açıklayan anonim yineleyici sonucunu döndürür.  
  
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
  
 Doğrulama yerine yineleyici işlevinin içinde ise, ilk yinelemesi başlangıç kadar doğrulama gerçekleştirilemiyor `For Each` gövdesi.  
  
##  <a name="BKMK_GenericList"></a>Yineleyiciler genel bir listesi ile kullanma  
 Aşağıdaki örnekte, `Stack(Of T)` genel bir sınıf uygular <xref:System.Collections.Generic.IEnumerable%601> genel arabirim. `Push` Yöntemi atar değerleri türünde bir dizi `T`. <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> Yöntemi kullanarak dizi değerleri döndürür `Yield` deyimi.  
  
 Genel yanı sıra <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> yöntemi, genel olmayan <xref:System.Collections.IEnumerable.GetEnumerator%2A> gerekir ayrıca uygulanan yöntemi. Bunun nedeni, <xref:System.Collections.Generic.IEnumerable%601> devraldığı <xref:System.Collections.IEnumerable>. Genel olmayan uygulama genel uygulamasını erteler.  
  
 Örnek veri aynı koleksiyonu yineleme yapma çeşitli yollarını desteklemek için adlandırılmış yineleyiciler kullanır. Bunlar yineleyiciler adlı `TopToBottom` ve `BottomToTop` özelliklerini ve `TopN` yöntemi.  
  
 `BottomToTop` Özellik bildirimi içerir `Iterator` anahtar sözcüğü.  
  
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
  
##  <a name="BKMK_SyntaxInformation"></a>Sözdizimi bilgileri  
 Yineleyici bir yöntem olarak oluşabilir veya `get` erişimcisi. Yineleyici bir olay, örnek oluşturucusu, statik Oluşturucusu veya statik yıkıcı gerçekleşemez.  
  
 Örtük bir dönüştürme ifadesi türden bulunmalıdır `Yield` yineleyici dönüş türü bildirimi.  
  
 İterator yöntemi Visual Basic'te içeremez `ByRef` parametreleri.  
  
 Visual Basic'te "Verim" ayrılmış bir sözcük değildir ve yalnızca içinde kullanıldığında, özel bir anlamı olan bir `Iterator` yöntemi veya `get` erişimcisi.  
  
##  <a name="BKMK_Technical"></a>Teknik uygulama  
 Yineleyici bir yöntem olarak yazma rağmen derleyici, iç içe geçmiş sınıf diğer bir deyişle, etkin, Durum makinesi çevirir. Bu sınıf olarak uzun yineleyici konumunu izler `For Each...Next` istemci kodu döngüde devam eder.  
  
 Derleyici yaptıklarını görmek için bir yineleyici yöntemi için oluşturulan Microsoft Ara dil kodu görüntülemek için Ildasm.exe Aracı'nı kullanabilirsiniz.  
  
 Yineleyici için oluşturduğunuzda bir [sınıfı](../../../csharp/language-reference/keywords/class.md) veya [yapısı](../../../csharp/language-reference/keywords/struct.md), tüm uygulama gerekmez <xref:System.Collections.IEnumerator> arabirimi. Derleyici yineleyici algılarsa, otomatik olarak oluşturur `Current`, `MoveNext`, ve `Dispose` yöntemlerinin <xref:System.Collections.IEnumerator> veya <xref:System.Collections.Generic.IEnumerator%601> arabirimi.  
  
 Art arda gelen her yinelemesinden üzerinde `For Each…Next` döngü (veya doğrudan çağrısı `IEnumerator.MoveNext`), sonraki yineleyici kod gövdesi önceki sonra sürdürür `Yield` deyimi. Sonraki devam edip `Yield` yineleyici gövde sonuna ulaşılana kadar deyimi veya kadar bir `Exit Function` veya `Return` deyimi karşılaştı.  
  
 Yineleyiciler desteklemez <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> yöntemi. Baştan yeniden yinelemek için yeni bir yineleyici edinmeniz gerekir.  
  
 Ek bilgi için bkz: [Visual Basic dil belirtimi](../../../visual-basic/reference/language-specification/index.md).  
  
##  <a name="BKMK_UseOfIterators"></a>Yineleyiciler kullanımı  
 Yineleyiciler basitliği korumanıza olanak tanır bir `For Each` döngü listesi sırası doldurmak için karmaşık kodlar kullanmanız gerektiğinde. Aşağıdakileri yapmak istediğinizde bu yararlı olabilir:  
  
-   Sonra ilk listesi değişiklik `For Each` döngü yineleme.  
  
-   Büyük bir liste ilk yinelemesi önce tam olarak yüklenmesini önlemek bir `For Each` döngü. Bir grup tablo satır yüklemek için disk belleğine alınan fetch örneğidir. Başka bir örnek <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> .NET Framework içinde yineleyiciler uygulayan yöntemi.  
  
-   Yineleyici listesini derlerken kapsüller. Yineleyici yönteminde listesi oluşturun ve her bir döngü sonucu verecek.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Collections.Generic>  
 <xref:System.Collections.Generic.IEnumerable%601>  
 [For Each... Sonraki deyim](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [Yield deyimi](../../../visual-basic/language-reference/statements/yield-statement.md)  
 [Yineleyici](../../../visual-basic/language-reference/modifiers/iterator.md)
