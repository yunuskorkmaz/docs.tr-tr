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
# <a name="iterators-visual-basic"></a><span data-ttu-id="95b18-102">Yineleyiciler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="95b18-102">Iterators (Visual Basic)</span></span>
<span data-ttu-id="95b18-103">Bir *yineleyici* koleksiyonlarına listeler ve dizi gibi adım için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="95b18-103">An *iterator* can be used to step through collections such as lists and arrays.</span></span>  
  
 <span data-ttu-id="95b18-104">İterator yöntemi veya `get` erişimci gerçekleştiren özel bir yineleme içinde bir koleksiyon.</span><span class="sxs-lookup"><span data-stu-id="95b18-104">An iterator method or `get` accessor performs a custom iteration over a collection.</span></span> <span data-ttu-id="95b18-105">İterator yöntemi kullanan [verim](../../../visual-basic/language-reference/statements/yield-statement.md) her öğeye aynı anda geri dönmek için deyimi.</span><span class="sxs-lookup"><span data-stu-id="95b18-105">An iterator method uses the [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) statement to return each element one at a time.</span></span> <span data-ttu-id="95b18-106">Zaman bir `Yield` deyimi ulaşıldığında geçerli kod konumda anımsanacak.</span><span class="sxs-lookup"><span data-stu-id="95b18-106">When a `Yield` statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="95b18-107">Yürütme o konumdan yineleyici işlevi bir sonraki zamana yeniden başlatılır.</span><span class="sxs-lookup"><span data-stu-id="95b18-107">Execution is restarted from that location the next time the iterator function is called.</span></span>  
  
 <span data-ttu-id="95b18-108">İle yineleyici istemci kodundan kullanmasını bir [For Each... Sonraki](../../../visual-basic/language-reference/statements/for-each-next-statement.md) deyimi, veya bir LINQ Sorgu kullanarak.</span><span class="sxs-lookup"><span data-stu-id="95b18-108">You consume an iterator from client code by using a [For Each…Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement, or by using a LINQ query.</span></span>  
  
 <span data-ttu-id="95b18-109">Aşağıdaki örnekte, ilk yinelemesi `For Each` döngüye neden olur, devam etmek yürütme `SomeNumbers` yineleyici yöntemi ilk kadar `Yield` deyimi ulaşıldığında.</span><span class="sxs-lookup"><span data-stu-id="95b18-109">In the following example, the first iteration of the `For Each` loop causes execution to proceed  in the `SomeNumbers` iterator method until the first `Yield` statement is reached.</span></span> <span data-ttu-id="95b18-110">Bu yineleme 3 değerini döndürür ve yineleyici yöntemi geçerli konumda korunur.</span><span class="sxs-lookup"><span data-stu-id="95b18-110">This iteration returns a value of 3, and the current location in the iterator method is retained.</span></span> <span data-ttu-id="95b18-111">Döngü sonraki yinelemesinde nereden yürütülmeye yineleyici yönteminde ulaştığında yeniden durdurma kapalı, solda bir `Yield` deyimi.</span><span class="sxs-lookup"><span data-stu-id="95b18-111">On the next iteration of the loop, execution in the iterator method continues from where it left off, again stopping when it reaches a `Yield` statement.</span></span> <span data-ttu-id="95b18-112">Bu yineleme 5 değerini döndürür ve yineleyici yöntemi geçerli konuma yeniden korunur.</span><span class="sxs-lookup"><span data-stu-id="95b18-112">This iteration returns a value of 5, and the current location in the iterator method is again retained.</span></span> <span data-ttu-id="95b18-113">Yineleyici yönteminin sonuna gelindiğinde döngü tamamlar.</span><span class="sxs-lookup"><span data-stu-id="95b18-113">The loop completes when the end of the iterator method is reached.</span></span>  
  
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
  
 <span data-ttu-id="95b18-114">Yineleyici yönteminin dönüş türü veya `get` erişimci olabilir <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, veya <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="95b18-114">The return type of an iterator method or `get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
 <span data-ttu-id="95b18-115">Kullanabileceğiniz bir `Exit Function` veya `Return` yinelemeyi sonlandırmak için deyimi.</span><span class="sxs-lookup"><span data-stu-id="95b18-115">You can use an `Exit Function` or `Return` statement to end the iteration.</span></span>  
  
 <span data-ttu-id="95b18-116">Visual Basic yineleyici işlevi veya `get` erişimcisi bildirimi içeren bir [yineleyici](../../../visual-basic/language-reference/modifiers/iterator.md) değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="95b18-116">A Visual Basic iterator function or `get` accessor declaration includes an [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md) modifier.</span></span>  
  
 <span data-ttu-id="95b18-117">Yineleyiciler, Visual Studio 2012'de Visual Basic'te tanıtıldı.</span><span class="sxs-lookup"><span data-stu-id="95b18-117">Iterators were introduced in Visual Basic in Visual Studio 2012.</span></span>  
  
 <span data-ttu-id="95b18-118">**Bu konudaki**</span><span class="sxs-lookup"><span data-stu-id="95b18-118">**In this topic**</span></span>  
  
-   [<span data-ttu-id="95b18-119">Basit yineleyici</span><span class="sxs-lookup"><span data-stu-id="95b18-119">Simple Iterator</span></span>](#BKMK_SimpleIterator)  
  
-   [<span data-ttu-id="95b18-120">Koleksiyon sınıfı oluşturma</span><span class="sxs-lookup"><span data-stu-id="95b18-120">Creating a Collection Class</span></span>](#BKMK_CollectionClass)  
  
-   [<span data-ttu-id="95b18-121">Try blokları</span><span class="sxs-lookup"><span data-stu-id="95b18-121">Try Blocks</span></span>](#BKMK_TryBlocks)  
  
-   [<span data-ttu-id="95b18-122">Anonim yöntemler</span><span class="sxs-lookup"><span data-stu-id="95b18-122">Anonymous Methods</span></span>](#BKMK_AnonymousMethods)  
  
-   [<span data-ttu-id="95b18-123">Yineleyiciler genel bir listesi ile kullanma</span><span class="sxs-lookup"><span data-stu-id="95b18-123">Using Iterators with a Generic List</span></span>](#BKMK_GenericList)  
  
-   [<span data-ttu-id="95b18-124">Sözdizimi bilgileri</span><span class="sxs-lookup"><span data-stu-id="95b18-124">Syntax Information</span></span>](#BKMK_SyntaxInformation)  
  
-   [<span data-ttu-id="95b18-125">Teknik uygulama</span><span class="sxs-lookup"><span data-stu-id="95b18-125">Technical Implementation</span></span>](#BKMK_Technical)  
  
-   [<span data-ttu-id="95b18-126">Yineleyiciler kullanımı</span><span class="sxs-lookup"><span data-stu-id="95b18-126">Use of Iterators</span></span>](#BKMK_UseOfIterators)  
  
> [!NOTE]
>  <span data-ttu-id="95b18-127">Basit yineleyici örnek dışında konudaki tüm örnekleri için dahil [içeri aktarmalar](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) deyimleri için `System.Collections` ve `System.Collections.Generic` ad alanları.</span><span class="sxs-lookup"><span data-stu-id="95b18-127">For all examples in the topic except the Simple Iterator example, include [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) statements for the `System.Collections` and `System.Collections.Generic` namespaces.</span></span>  
  
##  <a name="BKMK_SimpleIterator"></a><span data-ttu-id="95b18-128">Basit yineleyici</span><span class="sxs-lookup"><span data-stu-id="95b18-128">Simple Iterator</span></span>  
 <span data-ttu-id="95b18-129">Aşağıdaki örnek bir tek sahip `Yield` içinde deyimi bir [için... Sonraki](../../../visual-basic/language-reference/statements/for-next-statement.md) döngü.</span><span class="sxs-lookup"><span data-stu-id="95b18-129">The following example has a single `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="95b18-130">İçinde `Main`, her yinelemesinden `For Each` deyimi gövde oluşturur diğerine geçer yineleyici işlevi çağrısı `Yield` deyimi.</span><span class="sxs-lookup"><span data-stu-id="95b18-130">In `Main`, each iteration of the `For Each` statement body creates a call to the iterator function, which proceeds to the next `Yield` statement.</span></span>  
  
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
  
##  <a name="BKMK_CollectionClass"></a><span data-ttu-id="95b18-131">Koleksiyon sınıfı oluşturma</span><span class="sxs-lookup"><span data-stu-id="95b18-131">Creating a Collection Class</span></span>  
 <span data-ttu-id="95b18-132">Aşağıdaki örnekte, `DaysOfTheWeek` uygulayan sınıf <xref:System.Collections.IEnumerable> gerektirir arabirimi bir <xref:System.Collections.IEnumerable.GetEnumerator%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="95b18-132">In the following example, the `DaysOfTheWeek` class implements the <xref:System.Collections.IEnumerable> interface, which requires a <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span> <span data-ttu-id="95b18-133">Derleyici örtülü olarak çağırır `GetEnumerator` döndürür yöntemi bir <xref:System.Collections.IEnumerator>.</span><span class="sxs-lookup"><span data-stu-id="95b18-133">The compiler implicitly calls the `GetEnumerator` method, which returns an <xref:System.Collections.IEnumerator>.</span></span>  
  
 <span data-ttu-id="95b18-134">`GetEnumerator` Yöntemi döndürür her dize aynı anda kullanarak `Yield` deyimi ve bir `Iterator` değiştirici işlevi bildiriminde değil.</span><span class="sxs-lookup"><span data-stu-id="95b18-134">The `GetEnumerator` method returns each string one at a time by using the `Yield` statement, and  an `Iterator` modifier is in the function declaration.</span></span>  
  
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
  
 <span data-ttu-id="95b18-135">Aşağıdaki örnekte bir `Zoo` hayvanlar koleksiyonunu içeren sınıf.</span><span class="sxs-lookup"><span data-stu-id="95b18-135">The following example creates a `Zoo` class that contains a collection of animals.</span></span>  
  
 <span data-ttu-id="95b18-136">`For Each` Sınıf örneğine başvuruda bulunan deyimi (`theZoo`) örtük olarak çağırır `GetEnumerator` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="95b18-136">The `For Each` statement that refers to the class instance (`theZoo`) implicitly calls the `GetEnumerator` method.</span></span> <span data-ttu-id="95b18-137">`For Each` Başvurmak deyimleri `Birds` ve `Mammals` özelliklerini kullanmak `AnimalsForType` yineleyici yöntemi adı.</span><span class="sxs-lookup"><span data-stu-id="95b18-137">The `For Each` statements that refer to the `Birds` and `Mammals` properties use the `AnimalsForType` named iterator method.</span></span>  
  
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
  
##  <a name="BKMK_TryBlocks"></a><span data-ttu-id="95b18-138">Try blokları</span><span class="sxs-lookup"><span data-stu-id="95b18-138">Try Blocks</span></span>  
 <span data-ttu-id="95b18-139">Visual Basic sağlayan bir `Yield` deyiminde `Try` , engelleme bir [deneyin... Catch... Finally ifadesi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="95b18-139">Visual Basic allows a `Yield` statement in the `Try` block of a [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span> <span data-ttu-id="95b18-140">A `Try` sahip blok bir `Yield` deyimi olabilir `Catch` engeller ve olabilir bir `Finally` bloğu.</span><span class="sxs-lookup"><span data-stu-id="95b18-140">A `Try` block that has a `Yield` statement can have `Catch` blocks, and can have a `Finally` block.</span></span>  
  
 <span data-ttu-id="95b18-141">Aşağıdaki örnek içerir `Try`, `Catch`, ve `Finally` bir yineleyici işlevinde engeller.</span><span class="sxs-lookup"><span data-stu-id="95b18-141">The following example includes `Try`, `Catch`, and `Finally` blocks in an iterator function.</span></span> <span data-ttu-id="95b18-142">`Finally` Yineleyici işlevi bloğunda yürütülmeden önce `For Each` yineleme biter.</span><span class="sxs-lookup"><span data-stu-id="95b18-142">The `Finally` block in the iterator function executes before the `For Each` iteration finishes.</span></span>  
  
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
  
 <span data-ttu-id="95b18-143">A `Yield` deyimi içinde olamaz bir `Catch` blok veya `Finally` bloğu.</span><span class="sxs-lookup"><span data-stu-id="95b18-143">A `Yield` statement cannot be inside a `Catch` block or a `Finally` block.</span></span>  
  
 <span data-ttu-id="95b18-144">Varsa `For Each` gövdesi (yerine yineleyici yöntemi) bir özel durum oluşturur bir `Catch` yineleyici işlevi bloğunda yürütülmez, ancak bir `Finally` yineleyici işlevi bloğunda gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="95b18-144">If the `For Each` body (instead of the iterator method) throws an exception, a `Catch` block in the iterator function is not executed, but a `Finally` block in the iterator function is executed.</span></span> <span data-ttu-id="95b18-145">A `Catch` yineleyici işlevi bloğunda yineleyici işlevinin içinde oluşan özel durumlarını yakalar.</span><span class="sxs-lookup"><span data-stu-id="95b18-145">A `Catch` block inside an iterator function catches only exceptions that occur inside the iterator function.</span></span>  
  
##  <a name="BKMK_AnonymousMethods"></a><span data-ttu-id="95b18-146">Anonim yöntemler</span><span class="sxs-lookup"><span data-stu-id="95b18-146">Anonymous Methods</span></span>  
 <span data-ttu-id="95b18-147">Visual Basic'te bir yineleyici işlevi adsız bir işlev olabilir.</span><span class="sxs-lookup"><span data-stu-id="95b18-147">In Visual Basic, an anonymous function can be an iterator function.</span></span> <span data-ttu-id="95b18-148">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="95b18-148">The following example illustrates this.</span></span>  
  
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
  
 <span data-ttu-id="95b18-149">Aşağıdaki örnek bağımsız değişkenler doğrulayan bir yineleyici olmayan yöntemi vardır.</span><span class="sxs-lookup"><span data-stu-id="95b18-149">The following example has a non-iterator method that validates the arguments.</span></span> <span data-ttu-id="95b18-150">Yöntemi, koleksiyon öğeleri açıklayan anonim yineleyici sonucunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="95b18-150">The method returns the result of an anonymous iterator that describes the collection elements.</span></span>  
  
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
  
 <span data-ttu-id="95b18-151">Doğrulama yerine yineleyici işlevinin içinde ise, ilk yinelemesi başlangıç kadar doğrulama gerçekleştirilemiyor `For Each` gövdesi.</span><span class="sxs-lookup"><span data-stu-id="95b18-151">If validation is instead inside the iterator function, the validation cannot be performed until the start of the first iteration of the `For Each` body.</span></span>  
  
##  <a name="BKMK_GenericList"></a><span data-ttu-id="95b18-152">Yineleyiciler genel bir listesi ile kullanma</span><span class="sxs-lookup"><span data-stu-id="95b18-152">Using Iterators with a Generic List</span></span>  
 <span data-ttu-id="95b18-153">Aşağıdaki örnekte, `Stack(Of T)` genel bir sınıf uygular <xref:System.Collections.Generic.IEnumerable%601> genel arabirim.</span><span class="sxs-lookup"><span data-stu-id="95b18-153">In the following example, the `Stack(Of T)` generic class implements the <xref:System.Collections.Generic.IEnumerable%601> generic interface.</span></span> <span data-ttu-id="95b18-154">`Push` Yöntemi atar değerleri türünde bir dizi `T`.</span><span class="sxs-lookup"><span data-stu-id="95b18-154">The `Push` method assigns values to an array of type `T`.</span></span> <span data-ttu-id="95b18-155"><xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> Yöntemi kullanarak dizi değerleri döndürür `Yield` deyimi.</span><span class="sxs-lookup"><span data-stu-id="95b18-155">The <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method returns the array values by using the `Yield` statement.</span></span>  
  
 <span data-ttu-id="95b18-156">Genel yanı sıra <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> yöntemi, genel olmayan <xref:System.Collections.IEnumerable.GetEnumerator%2A> gerekir ayrıca uygulanan yöntemi.</span><span class="sxs-lookup"><span data-stu-id="95b18-156">In addition to the generic <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method, the non-generic <xref:System.Collections.IEnumerable.GetEnumerator%2A> method must also be implemented.</span></span> <span data-ttu-id="95b18-157">Bunun nedeni, <xref:System.Collections.Generic.IEnumerable%601> devraldığı <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="95b18-157">This is because <xref:System.Collections.Generic.IEnumerable%601> inherits from <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="95b18-158">Genel olmayan uygulama genel uygulamasını erteler.</span><span class="sxs-lookup"><span data-stu-id="95b18-158">The non-generic implementation defers to the generic implementation.</span></span>  
  
 <span data-ttu-id="95b18-159">Örnek veri aynı koleksiyonu yineleme yapma çeşitli yollarını desteklemek için adlandırılmış yineleyiciler kullanır.</span><span class="sxs-lookup"><span data-stu-id="95b18-159">The example uses named iterators to support various ways of iterating through the same collection of data.</span></span> <span data-ttu-id="95b18-160">Bunlar yineleyiciler adlı `TopToBottom` ve `BottomToTop` özelliklerini ve `TopN` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="95b18-160">These named iterators are the `TopToBottom` and `BottomToTop` properties, and the `TopN` method.</span></span>  
  
 <span data-ttu-id="95b18-161">`BottomToTop` Özellik bildirimi içerir `Iterator` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="95b18-161">The `BottomToTop` property declaration includes the `Iterator` keyword.</span></span>  
  
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
  
##  <a name="BKMK_SyntaxInformation"></a><span data-ttu-id="95b18-162">Sözdizimi bilgileri</span><span class="sxs-lookup"><span data-stu-id="95b18-162">Syntax Information</span></span>  
 <span data-ttu-id="95b18-163">Yineleyici bir yöntem olarak oluşabilir veya `get` erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="95b18-163">An iterator can occur as a method or `get` accessor.</span></span> <span data-ttu-id="95b18-164">Yineleyici bir olay, örnek oluşturucusu, statik Oluşturucusu veya statik yıkıcı gerçekleşemez.</span><span class="sxs-lookup"><span data-stu-id="95b18-164">An iterator cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="95b18-165">Örtük bir dönüştürme ifadesi türden bulunmalıdır `Yield` yineleyici dönüş türü bildirimi.</span><span class="sxs-lookup"><span data-stu-id="95b18-165">An implicit conversion must exist from the expression type in the `Yield` statement to the return type of the iterator.</span></span>  
  
 <span data-ttu-id="95b18-166">İterator yöntemi Visual Basic'te içeremez `ByRef` parametreleri.</span><span class="sxs-lookup"><span data-stu-id="95b18-166">In Visual Basic, an iterator method cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="95b18-167">Visual Basic'te "Verim" ayrılmış bir sözcük değildir ve yalnızca içinde kullanıldığında, özel bir anlamı olan bir `Iterator` yöntemi veya `get` erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="95b18-167">In Visual Basic, "Yield" is not a reserved word and has special meaning only when it is used in an `Iterator` method or `get` accessor.</span></span>  
  
##  <a name="BKMK_Technical"></a><span data-ttu-id="95b18-168">Teknik uygulama</span><span class="sxs-lookup"><span data-stu-id="95b18-168">Technical Implementation</span></span>  
 <span data-ttu-id="95b18-169">Yineleyici bir yöntem olarak yazma rağmen derleyici, iç içe geçmiş sınıf diğer bir deyişle, etkin, Durum makinesi çevirir.</span><span class="sxs-lookup"><span data-stu-id="95b18-169">Although you write an iterator as a method, the compiler translates it into a nested class that is, in effect, a state machine.</span></span> <span data-ttu-id="95b18-170">Bu sınıf olarak uzun yineleyici konumunu izler `For Each...Next` istemci kodu döngüde devam eder.</span><span class="sxs-lookup"><span data-stu-id="95b18-170">This class keeps track of the position of the iterator as long the `For Each...Next` loop in the client code continues.</span></span>  
  
 <span data-ttu-id="95b18-171">Derleyici yaptıklarını görmek için bir yineleyici yöntemi için oluşturulan Microsoft Ara dil kodu görüntülemek için Ildasm.exe Aracı'nı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="95b18-171">To see what the compiler does, you can use the Ildasm.exe tool to view the Microsoft intermediate language code that is generated for an iterator method.</span></span>  
  
 <span data-ttu-id="95b18-172">Yineleyici için oluşturduğunuzda bir [sınıfı](../../../csharp/language-reference/keywords/class.md) veya [yapısı](../../../csharp/language-reference/keywords/struct.md), tüm uygulama gerekmez <xref:System.Collections.IEnumerator> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="95b18-172">When you create an iterator for a [class](../../../csharp/language-reference/keywords/class.md) or [struct](../../../csharp/language-reference/keywords/struct.md), you do not have to implement the whole <xref:System.Collections.IEnumerator> interface.</span></span> <span data-ttu-id="95b18-173">Derleyici yineleyici algılarsa, otomatik olarak oluşturur `Current`, `MoveNext`, ve `Dispose` yöntemlerinin <xref:System.Collections.IEnumerator> veya <xref:System.Collections.Generic.IEnumerator%601> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="95b18-173">When the compiler detects the iterator, it automatically generates the `Current`, `MoveNext`, and `Dispose` methods of the <xref:System.Collections.IEnumerator> or <xref:System.Collections.Generic.IEnumerator%601> interface.</span></span>  
  
 <span data-ttu-id="95b18-174">Art arda gelen her yinelemesinden üzerinde `For Each…Next` döngü (veya doğrudan çağrısı `IEnumerator.MoveNext`), sonraki yineleyici kod gövdesi önceki sonra sürdürür `Yield` deyimi.</span><span class="sxs-lookup"><span data-stu-id="95b18-174">On each successive iteration of the `For Each…Next` loop (or the direct call to `IEnumerator.MoveNext`), the next iterator code body resumes after the previous `Yield` statement.</span></span> <span data-ttu-id="95b18-175">Sonraki devam edip `Yield` yineleyici gövde sonuna ulaşılana kadar deyimi veya kadar bir `Exit Function` veya `Return` deyimi karşılaştı.</span><span class="sxs-lookup"><span data-stu-id="95b18-175">It then continues to the next `Yield` statement until the end of the iterator body is reached, or until an `Exit Function` or `Return` statement is encountered.</span></span>  
  
 <span data-ttu-id="95b18-176">Yineleyiciler desteklemez <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="95b18-176">Iterators do not support the <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="95b18-177">Baştan yeniden yinelemek için yeni bir yineleyici edinmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="95b18-177">To re-iterate from the start, you must obtain a new iterator.</span></span>  
  
 <span data-ttu-id="95b18-178">Ek bilgi için bkz: [Visual Basic dil belirtimi](../../../visual-basic/reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="95b18-178">For additional information, see the [Visual Basic Language Specification](../../../visual-basic/reference/language-specification/index.md).</span></span>  
  
##  <a name="BKMK_UseOfIterators"></a><span data-ttu-id="95b18-179">Yineleyiciler kullanımı</span><span class="sxs-lookup"><span data-stu-id="95b18-179">Use of Iterators</span></span>  
 <span data-ttu-id="95b18-180">Yineleyiciler basitliği korumanıza olanak tanır bir `For Each` döngü listesi sırası doldurmak için karmaşık kodlar kullanmanız gerektiğinde.</span><span class="sxs-lookup"><span data-stu-id="95b18-180">Iterators enable you to maintain the simplicity of a `For Each` loop when you need to use complex code to populate a list sequence.</span></span> <span data-ttu-id="95b18-181">Aşağıdakileri yapmak istediğinizde bu yararlı olabilir:</span><span class="sxs-lookup"><span data-stu-id="95b18-181">This can be useful when you want to do the following:</span></span>  
  
-   <span data-ttu-id="95b18-182">Sonra ilk listesi değişiklik `For Each` döngü yineleme.</span><span class="sxs-lookup"><span data-stu-id="95b18-182">Modify the list sequence after the first `For Each` loop iteration.</span></span>  
  
-   <span data-ttu-id="95b18-183">Büyük bir liste ilk yinelemesi önce tam olarak yüklenmesini önlemek bir `For Each` döngü.</span><span class="sxs-lookup"><span data-stu-id="95b18-183">Avoid fully loading a large list before the first iteration of a `For Each` loop.</span></span> <span data-ttu-id="95b18-184">Bir grup tablo satır yüklemek için disk belleğine alınan fetch örneğidir.</span><span class="sxs-lookup"><span data-stu-id="95b18-184">An example is a paged fetch to load a batch of table rows.</span></span> <span data-ttu-id="95b18-185">Başka bir örnek <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> .NET Framework içinde yineleyiciler uygulayan yöntemi.</span><span class="sxs-lookup"><span data-stu-id="95b18-185">Another example is the <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> method, which implements iterators within the .NET Framework.</span></span>  
  
-   <span data-ttu-id="95b18-186">Yineleyici listesini derlerken kapsüller.</span><span class="sxs-lookup"><span data-stu-id="95b18-186">Encapsulate building the list in the iterator.</span></span> <span data-ttu-id="95b18-187">Yineleyici yönteminde listesi oluşturun ve her bir döngü sonucu verecek.</span><span class="sxs-lookup"><span data-stu-id="95b18-187">In the iterator method, you can build the list and then yield each result in a loop.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95b18-188">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="95b18-188">See Also</span></span>  
 <xref:System.Collections.Generic>  
 <xref:System.Collections.Generic.IEnumerable%601>  
 [<span data-ttu-id="95b18-189">For Each... Sonraki deyim</span><span class="sxs-lookup"><span data-stu-id="95b18-189">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [<span data-ttu-id="95b18-190">Yield deyimi</span><span class="sxs-lookup"><span data-stu-id="95b18-190">Yield Statement</span></span>](../../../visual-basic/language-reference/statements/yield-statement.md)  
 [<span data-ttu-id="95b18-191">Yineleyici</span><span class="sxs-lookup"><span data-stu-id="95b18-191">Iterator</span></span>](../../../visual-basic/language-reference/modifiers/iterator.md)
