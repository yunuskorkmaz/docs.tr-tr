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
# <a name="iterators-visual-basic"></a><span data-ttu-id="24536-102">Yineleyiciler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="24536-102">Iterators (Visual Basic)</span></span>

<span data-ttu-id="24536-103">Bir *Yineleyici* , listeler ve diziler gibi koleksiyonlardan dolaşmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="24536-103">An *iterator* can be used to step through collections such as lists and arrays.</span></span>

<span data-ttu-id="24536-104">Yineleyici yöntemi veya `get` erişimcisi bir koleksiyon üzerinde özel bir yineleme gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="24536-104">An iterator method or `get` accessor performs a custom iteration over a collection.</span></span> <span data-ttu-id="24536-105">Yineleyici yöntemi, her öğeyi birer birer döndürmek için [yield](../../language-reference/statements/yield-statement.md) ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="24536-105">An iterator method uses the [Yield](../../language-reference/statements/yield-statement.md) statement to return each element one at a time.</span></span> <span data-ttu-id="24536-106">Bir `Yield` ifadeye ulaşıldığında, koddaki geçerli konum hatırlanır.</span><span class="sxs-lookup"><span data-stu-id="24536-106">When a `Yield` statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="24536-107">Bu konumdan, Yineleyici işlevinin bir sonraki çağrılışında yürütme yeniden başlatılır.</span><span class="sxs-lookup"><span data-stu-id="24536-107">Execution is restarted from that location the next time the iterator function is called.</span></span>

<span data-ttu-id="24536-108">Her biri Için bir kullanarak istemci kodundan bir yineleyici kullanıyorsunuz [... Sonraki](../../language-reference/statements/for-each-next-statement.md) ifade veya BIR LINQ sorgusu kullanarak.</span><span class="sxs-lookup"><span data-stu-id="24536-108">You consume an iterator from client code by using a [For Each…Next](../../language-reference/statements/for-each-next-statement.md) statement, or by using a LINQ query.</span></span>

<span data-ttu-id="24536-109">Aşağıdaki örnekte, döngünün ilk yinelemesi `For Each` yürütmenin `SomeNumbers` ilk ifadeye ulaşılana kadar yineleyici yönteminde devam etmesine neden olur `Yield` .</span><span class="sxs-lookup"><span data-stu-id="24536-109">In the following example, the first iteration of the `For Each` loop causes execution to proceed  in the `SomeNumbers` iterator method until the first `Yield` statement is reached.</span></span> <span data-ttu-id="24536-110">Bu yineleme 3 değerini döndürür ve yineleyici yöntemindeki geçerli konum korunur.</span><span class="sxs-lookup"><span data-stu-id="24536-110">This iteration returns a value of 3, and the current location in the iterator method is retained.</span></span> <span data-ttu-id="24536-111">Döngünün bir sonraki yinelemesinde, yineleyici yönteminde yürütme kaldığınız yerden devam eder, bir ifadeye ulaştığında yeniden durdurulur `Yield` .</span><span class="sxs-lookup"><span data-stu-id="24536-111">On the next iteration of the loop, execution in the iterator method continues from where it left off, again stopping when it reaches a `Yield` statement.</span></span> <span data-ttu-id="24536-112">Bu yineleme 5 değerini döndürür ve yineleyici yöntemindeki geçerli konum yeniden korunur.</span><span class="sxs-lookup"><span data-stu-id="24536-112">This iteration returns a value of 5, and the current location in the iterator method is again retained.</span></span> <span data-ttu-id="24536-113">Yineleyici yönteminin sonuna ulaşıldığında döngü tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="24536-113">The loop completes when the end of the iterator method is reached.</span></span>

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

<span data-ttu-id="24536-114">Bir yineleyici yönteminin veya erişimcisinin dönüş türü `get` <xref:System.Collections.IEnumerable> ,, <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.IEnumerator> , veya olabilir <xref:System.Collections.Generic.IEnumerator%601> .</span><span class="sxs-lookup"><span data-stu-id="24536-114">The return type of an iterator method or `get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

<span data-ttu-id="24536-115">`Exit Function` `Return` Yinelemeyi sonlandırmak için bir veya ifadesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="24536-115">You can use an `Exit Function` or `Return` statement to end the iteration.</span></span>

<span data-ttu-id="24536-116">Visual Basic Yineleyici işlevi veya `get` erişimci bildirimi bir [Yineleyici](../../language-reference/modifiers/iterator.md) değiştiricisi içerir.</span><span class="sxs-lookup"><span data-stu-id="24536-116">A Visual Basic iterator function or `get` accessor declaration includes an [Iterator](../../language-reference/modifiers/iterator.md) modifier.</span></span>

<span data-ttu-id="24536-117">Yineleyiciler, Visual Studio 2012 ' de Visual Basic sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="24536-117">Iterators were introduced in Visual Basic in Visual Studio 2012.</span></span>

<span data-ttu-id="24536-118">**Bu konuda**</span><span class="sxs-lookup"><span data-stu-id="24536-118">**In this topic**</span></span>

- [<span data-ttu-id="24536-119">Basit Yineleyici</span><span class="sxs-lookup"><span data-stu-id="24536-119">Simple Iterator</span></span>](#BKMK_SimpleIterator)

- [<span data-ttu-id="24536-120">Koleksiyon sınıfı oluşturma</span><span class="sxs-lookup"><span data-stu-id="24536-120">Creating a Collection Class</span></span>](#BKMK_CollectionClass)

- [<span data-ttu-id="24536-121">TRY blokları</span><span class="sxs-lookup"><span data-stu-id="24536-121">Try Blocks</span></span>](#BKMK_TryBlocks)

- [<span data-ttu-id="24536-122">Anonim Yöntemler</span><span class="sxs-lookup"><span data-stu-id="24536-122">Anonymous Methods</span></span>](#BKMK_AnonymousMethods)

- [<span data-ttu-id="24536-123">Bir genel liste ile yineleyiciler kullanma</span><span class="sxs-lookup"><span data-stu-id="24536-123">Using Iterators with a Generic List</span></span>](#BKMK_GenericList)

- [<span data-ttu-id="24536-124">Sözdizimi bilgileri</span><span class="sxs-lookup"><span data-stu-id="24536-124">Syntax Information</span></span>](#BKMK_SyntaxInformation)

- [<span data-ttu-id="24536-125">Teknik Uygulama</span><span class="sxs-lookup"><span data-stu-id="24536-125">Technical Implementation</span></span>](#BKMK_Technical)

- [<span data-ttu-id="24536-126">Yineleyicilerin kullanımı</span><span class="sxs-lookup"><span data-stu-id="24536-126">Use of Iterators</span></span>](#BKMK_UseOfIterators)

> [!NOTE]
> <span data-ttu-id="24536-127">Konunun basit Yineleyici örneği hariç tüm örnekleri için, [Imports](../../language-reference/statements/imports-statement-net-namespace-and-type.md) `System.Collections` ve ad alanları için Imports deyimlerini ekleyin `System.Collections.Generic` .</span><span class="sxs-lookup"><span data-stu-id="24536-127">For all examples in the topic except the Simple Iterator example, include [Imports](../../language-reference/statements/imports-statement-net-namespace-and-type.md) statements for the `System.Collections` and `System.Collections.Generic` namespaces.</span></span>

## <a name="simple-iterator"></a><a name="BKMK_SimpleIterator"></a><span data-ttu-id="24536-128">Basit Yineleyici</span><span class="sxs-lookup"><span data-stu-id="24536-128">Simple Iterator</span></span>

<span data-ttu-id="24536-129">Aşağıdaki örnek, Için içinde olan tek bir `Yield` ifadeye sahiptir [... Sonraki](../../language-reference/statements/for-next-statement.md) döngü.</span><span class="sxs-lookup"><span data-stu-id="24536-129">The following example has a single `Yield` statement that is inside a [For…Next](../../language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="24536-130">' De `Main` , `For Each` ifade gövdesinin her yinelemesi bir sonraki ifadeye devam eden Yineleyici işlevine bir çağrı oluşturur `Yield` .</span><span class="sxs-lookup"><span data-stu-id="24536-130">In `Main`, each iteration of the `For Each` statement body creates a call to the iterator function, which proceeds to the next `Yield` statement.</span></span>

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

## <a name="creating-a-collection-class"></a><a name="BKMK_CollectionClass"></a><span data-ttu-id="24536-131">Koleksiyon sınıfı oluşturma</span><span class="sxs-lookup"><span data-stu-id="24536-131">Creating a Collection Class</span></span>

<span data-ttu-id="24536-132">Aşağıdaki örnekte, `DaysOfTheWeek` sınıfı <xref:System.Collections.IEnumerable> bir yöntemi gerektiren arabirimini uygular <xref:System.Collections.IEnumerable.GetEnumerator%2A> .</span><span class="sxs-lookup"><span data-stu-id="24536-132">In the following example, the `DaysOfTheWeek` class implements the <xref:System.Collections.IEnumerable> interface, which requires a <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span> <span data-ttu-id="24536-133">Derleyici, `GetEnumerator` bir döndüren yöntemini dolaylı olarak çağırır <xref:System.Collections.IEnumerator> .</span><span class="sxs-lookup"><span data-stu-id="24536-133">The compiler implicitly calls the `GetEnumerator` method, which returns an <xref:System.Collections.IEnumerator>.</span></span>

<span data-ttu-id="24536-134">`GetEnumerator`Yöntemi, yöntemini kullanarak her bir dizeyi birer birer döndürür `Yield` ve `Iterator` işlev bildiriminde bir değiştirici olur.</span><span class="sxs-lookup"><span data-stu-id="24536-134">The `GetEnumerator` method returns each string one at a time by using the `Yield` statement, and  an `Iterator` modifier is in the function declaration.</span></span>

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

<span data-ttu-id="24536-135">Aşağıdaki örnek, `Zoo` hayvanlar koleksiyonunu içeren bir sınıf oluşturur.</span><span class="sxs-lookup"><span data-stu-id="24536-135">The following example creates a `Zoo` class that contains a collection of animals.</span></span>

<span data-ttu-id="24536-136">`For Each`Sınıf örneğine () başvuran ifade, `theZoo` yöntemi örtük olarak çağırır `GetEnumerator` .</span><span class="sxs-lookup"><span data-stu-id="24536-136">The `For Each` statement that refers to the class instance (`theZoo`) implicitly calls the `GetEnumerator` method.</span></span> <span data-ttu-id="24536-137">`For Each` `Birds` Ve özelliklerine başvuran deyimler `Mammals` `AnimalsForType` adlandırılmış yineleyici yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="24536-137">The `For Each` statements that refer to the `Birds` and `Mammals` properties use the `AnimalsForType` named iterator method.</span></span>

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

## <a name="try-blocks"></a><a name="BKMK_TryBlocks"></a><span data-ttu-id="24536-138">TRY blokları</span><span class="sxs-lookup"><span data-stu-id="24536-138">Try Blocks</span></span>

<span data-ttu-id="24536-139">Visual Basic `Yield` try bloğundaki bir ifadeye izin verir `Try` [... Yakala... Finally ekstresi](../../language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="24536-139">Visual Basic allows a `Yield` statement in the `Try` block of a [Try...Catch...Finally Statement](../../language-reference/statements/try-catch-finally-statement.md).</span></span> <span data-ttu-id="24536-140">`Try`Bir deyime sahip bir blok `Yield` blokları olabilir `Catch` ve bir bloğuna sahip olabilir `Finally` .</span><span class="sxs-lookup"><span data-stu-id="24536-140">A `Try` block that has a `Yield` statement can have `Catch` blocks, and can have a `Finally` block.</span></span>

<span data-ttu-id="24536-141">Aşağıdaki örnek, `Try` `Catch` `Finally` bir yineleyici işlevindeki, ve bloklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="24536-141">The following example includes `Try`, `Catch`, and `Finally` blocks in an iterator function.</span></span> <span data-ttu-id="24536-142">`Finally`Yineleyici işlevindeki blok `For Each` yineleme bitmeden önce yürütülür.</span><span class="sxs-lookup"><span data-stu-id="24536-142">The `Finally` block in the iterator function executes before the `For Each` iteration finishes.</span></span>

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

<span data-ttu-id="24536-143">Bir `Yield` ifade bir `Catch` blok veya blok içinde olamaz `Finally` .</span><span class="sxs-lookup"><span data-stu-id="24536-143">A `Yield` statement cannot be inside a `Catch` block or a `Finally` block.</span></span>

<span data-ttu-id="24536-144">`For Each`Gövde (yineleyici yöntemi yerine) bir özel durum oluşturursa, `Catch` Yineleyici işlevindeki bir blok yürütülmez, ancak `Finally` Yineleyici işlevindeki bir blok yürütülür.</span><span class="sxs-lookup"><span data-stu-id="24536-144">If the `For Each` body (instead of the iterator method) throws an exception, a `Catch` block in the iterator function is not executed, but a `Finally` block in the iterator function is executed.</span></span> <span data-ttu-id="24536-145">`Catch`Yineleyici işlevi içindeki bir blok yalnızca Yineleyici işlevinin içinde oluşan özel durumları yakalar.</span><span class="sxs-lookup"><span data-stu-id="24536-145">A `Catch` block inside an iterator function catches only exceptions that occur inside the iterator function.</span></span>

## <a name="anonymous-methods"></a><a name="BKMK_AnonymousMethods"></a><span data-ttu-id="24536-146">Anonim Yöntemler</span><span class="sxs-lookup"><span data-stu-id="24536-146">Anonymous Methods</span></span>

<span data-ttu-id="24536-147">Visual Basic, anonim bir işlev bir yineleyici işlevi olabilir.</span><span class="sxs-lookup"><span data-stu-id="24536-147">In Visual Basic, an anonymous function can be an iterator function.</span></span> <span data-ttu-id="24536-148">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="24536-148">The following example illustrates this.</span></span>

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

<span data-ttu-id="24536-149">Aşağıdaki örnek, bağımsız değişkenleri doğrulayan Yineleyici olmayan bir yönteme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="24536-149">The following example has a non-iterator method that validates the arguments.</span></span> <span data-ttu-id="24536-150">Yöntemi, koleksiyon öğelerini açıklayan bir anonim yineleyicinin sonucunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="24536-150">The method returns the result of an anonymous iterator that describes the collection elements.</span></span>

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

<span data-ttu-id="24536-151">Doğrulama işlemi Yineleyici işlevi içinde ise, gövdenin ilk yinelemesinin başlangıcına kadar doğrulama gerçekleştirilemez `For Each` .</span><span class="sxs-lookup"><span data-stu-id="24536-151">If validation is instead inside the iterator function, the validation cannot be performed until the start of the first iteration of the `For Each` body.</span></span>

## <a name="using-iterators-with-a-generic-list"></a><a name="BKMK_GenericList"></a><span data-ttu-id="24536-152">Bir genel liste ile yineleyiciler kullanma</span><span class="sxs-lookup"><span data-stu-id="24536-152">Using Iterators with a Generic List</span></span>

<span data-ttu-id="24536-153">Aşağıdaki örnekte, `Stack(Of T)` Genel sınıf <xref:System.Collections.Generic.IEnumerable%601> genel arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="24536-153">In the following example, the `Stack(Of T)` generic class implements the <xref:System.Collections.Generic.IEnumerable%601> generic interface.</span></span> <span data-ttu-id="24536-154">`Push`Yöntemi, türü bir diziye değerler atar `T` .</span><span class="sxs-lookup"><span data-stu-id="24536-154">The `Push` method assigns values to an array of type `T`.</span></span> <span data-ttu-id="24536-155"><xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>Yöntemi, ifadesini kullanarak dizi değerlerini döndürür `Yield` .</span><span class="sxs-lookup"><span data-stu-id="24536-155">The <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method returns the array values by using the `Yield` statement.</span></span>

<span data-ttu-id="24536-156">Genel yöntemin yanı sıra <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> genel olmayan <xref:System.Collections.IEnumerable.GetEnumerator%2A> yöntemin de uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="24536-156">In addition to the generic <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method, the non-generic <xref:System.Collections.IEnumerable.GetEnumerator%2A> method must also be implemented.</span></span> <span data-ttu-id="24536-157">Bunun nedeni, <xref:System.Collections.Generic.IEnumerable%601> öğesinden devralmasıdır <xref:System.Collections.IEnumerable> .</span><span class="sxs-lookup"><span data-stu-id="24536-157">This is because <xref:System.Collections.Generic.IEnumerable%601> inherits from <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="24536-158">Genel olmayan uygulama genel uygulamaya erteler.</span><span class="sxs-lookup"><span data-stu-id="24536-158">The non-generic implementation defers to the generic implementation.</span></span>

<span data-ttu-id="24536-159">Örnek, aynı veri topluluğunda tekrarların çeşitli yollarını desteklemek için adlandırılmış yineleyiciler kullanır.</span><span class="sxs-lookup"><span data-stu-id="24536-159">The example uses named iterators to support various ways of iterating through the same collection of data.</span></span> <span data-ttu-id="24536-160">Bu adlandırılmış yineleyiciler, `TopToBottom` ve `BottomToTop` özellikleridir ve `TopN` yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="24536-160">These named iterators are the `TopToBottom` and `BottomToTop` properties, and the `TopN` method.</span></span>

<span data-ttu-id="24536-161">`BottomToTop`Özellik bildirimi `Iterator` anahtar sözcüğünü içerir.</span><span class="sxs-lookup"><span data-stu-id="24536-161">The `BottomToTop` property declaration includes the `Iterator` keyword.</span></span>

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

## <a name="syntax-information"></a><a name="BKMK_SyntaxInformation"></a><span data-ttu-id="24536-162">Sözdizimi bilgileri</span><span class="sxs-lookup"><span data-stu-id="24536-162">Syntax Information</span></span>

<span data-ttu-id="24536-163">Yineleyici bir yöntem veya erişimci olarak gerçekleşebilir `get` .</span><span class="sxs-lookup"><span data-stu-id="24536-163">An iterator can occur as a method or `get` accessor.</span></span> <span data-ttu-id="24536-164">Bir olay, örnek Oluşturucu, statik oluşturucu veya statik yok edicisi içinde yineleyici olamaz.</span><span class="sxs-lookup"><span data-stu-id="24536-164">An iterator cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>

<span data-ttu-id="24536-165">Deyimdeki ifade türünden, `Yield` yineleyicinin dönüş türüne örtük bir dönüştürme bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="24536-165">An implicit conversion must exist from the expression type in the `Yield` statement to the return type of the iterator.</span></span>

<span data-ttu-id="24536-166">Visual Basic, yineleyici yöntemi herhangi bir parametreye sahip olamaz `ByRef` .</span><span class="sxs-lookup"><span data-stu-id="24536-166">In Visual Basic, an iterator method cannot have any `ByRef` parameters.</span></span>

<span data-ttu-id="24536-167">Visual Basic, "yield" ayrılmış bir sözcük değildir ve yalnızca bir `Iterator` yöntemde veya erişimcisinde kullanıldığında özel anlamı vardır `get` .</span><span class="sxs-lookup"><span data-stu-id="24536-167">In Visual Basic, "Yield" is not a reserved word and has special meaning only when it is used in an `Iterator` method or `get` accessor.</span></span>

## <a name="technical-implementation"></a><a name="BKMK_Technical"></a><span data-ttu-id="24536-168">Teknik uygulama</span><span class="sxs-lookup"><span data-stu-id="24536-168">Technical Implementation</span></span>

<span data-ttu-id="24536-169">Bir yineleyici Yöntem olarak yazdığınızda, derleyici onu bir durum makinesi olan bir iç içe geçmiş sınıfa çevirir.</span><span class="sxs-lookup"><span data-stu-id="24536-169">Although you write an iterator as a method, the compiler translates it into a nested class that is, in effect, a state machine.</span></span> <span data-ttu-id="24536-170">Bu sınıf, `For Each...Next` istemci kodundaki döngü devam ettiğinde yineleyicinin konumunu izler.</span><span class="sxs-lookup"><span data-stu-id="24536-170">This class keeps track of the position of the iterator as long the `For Each...Next` loop in the client code continues.</span></span>

<span data-ttu-id="24536-171">Derleyicinin ne yaptığını görmek için, bir yineleyici yöntemi için oluşturulan Microsoft ara dil kodunu görüntülemek için ıldadsm. exe aracını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="24536-171">To see what the compiler does, you can use the Ildasm.exe tool to view the Microsoft intermediate language code that is generated for an iterator method.</span></span>

<span data-ttu-id="24536-172">Bir [sınıf](../../language-reference/statements/class-statement.md) veya [Yapı](../../language-reference/statements/structure-statement.md)için Yineleyici oluşturduğunuzda, tüm arabirimini uygulamanız gerekmez <xref:System.Collections.IEnumerator> .</span><span class="sxs-lookup"><span data-stu-id="24536-172">When you create an iterator for a [class](../../language-reference/statements/class-statement.md) or [struct](../../language-reference/statements/structure-statement.md), you do not have to implement the whole <xref:System.Collections.IEnumerator> interface.</span></span> <span data-ttu-id="24536-173">Derleyici yineleyiciyi algıladığında, `Current` `MoveNext` veya arabiriminin,, ve yöntemlerini otomatik olarak oluşturur `Dispose` <xref:System.Collections.IEnumerator> <xref:System.Collections.Generic.IEnumerator%601> .</span><span class="sxs-lookup"><span data-stu-id="24536-173">When the compiler detects the iterator, it automatically generates the `Current`, `MoveNext`, and `Dispose` methods of the <xref:System.Collections.IEnumerator> or <xref:System.Collections.Generic.IEnumerator%601> interface.</span></span>

<span data-ttu-id="24536-174">Döngünün art arda her tekrarında `For Each…Next` (veya doğrudan çağrısının `IEnumerator.MoveNext` ), sonraki Yineleyici kod gövdesi önceki deyimden sonra devam eder `Yield` .</span><span class="sxs-lookup"><span data-stu-id="24536-174">On each successive iteration of the `For Each…Next` loop (or the direct call to `IEnumerator.MoveNext`), the next iterator code body resumes after the previous `Yield` statement.</span></span> <span data-ttu-id="24536-175">Daha sonra `Yield` Yineleyici gövdesinin sonuna ulaşılana kadar veya bir `Exit Function` veya `Return` ifadesiyle karşılaşana kadar sonraki ifadeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="24536-175">It then continues to the next `Yield` statement until the end of the iterator body is reached, or until an `Exit Function` or `Return` statement is encountered.</span></span>

<span data-ttu-id="24536-176">Yineleyiciler <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> yöntemi desteklemez.</span><span class="sxs-lookup"><span data-stu-id="24536-176">Iterators do not support the <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="24536-177">Başlangıçtan yeniden yinelemek için yeni bir yineleyici edinmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="24536-177">To re-iterate from the start, you must obtain a new iterator.</span></span>

<span data-ttu-id="24536-178">Daha fazla bilgi için [Visual Basic dil belirtimine](../../reference/language-specification/index.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="24536-178">For additional information, see the [Visual Basic Language Specification](../../reference/language-specification/index.md).</span></span>

## <a name="use-of-iterators"></a><a name="BKMK_UseOfIterators"></a><span data-ttu-id="24536-179">Yineleyicilerin kullanımı</span><span class="sxs-lookup"><span data-stu-id="24536-179">Use of Iterators</span></span>

<span data-ttu-id="24536-180">Yineleyiciler, `For Each` bir liste dizisini doldurmak için karmaşık kod kullanmanız gerektiğinde bir döngünün basitliğini korumanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="24536-180">Iterators enable you to maintain the simplicity of a `For Each` loop when you need to use complex code to populate a list sequence.</span></span> <span data-ttu-id="24536-181">Bu, aşağıdakileri yapmak istediğinizde yararlı olabilir:</span><span class="sxs-lookup"><span data-stu-id="24536-181">This can be useful when you want to do the following:</span></span>

- <span data-ttu-id="24536-182">İlk döngü yinelemeden sonra liste sırasını değiştirin `For Each` .</span><span class="sxs-lookup"><span data-stu-id="24536-182">Modify the list sequence after the first `For Each` loop iteration.</span></span>

- <span data-ttu-id="24536-183">Bir döngünün ilk yinelemesinden önce büyük bir listenin tam olarak yüklenmesini önleyin `For Each` .</span><span class="sxs-lookup"><span data-stu-id="24536-183">Avoid fully loading a large list before the first iteration of a `For Each` loop.</span></span> <span data-ttu-id="24536-184">Tablo satırlarını toplu olarak yüklemek için disk belleğine alınmış bir getirme örneği.</span><span class="sxs-lookup"><span data-stu-id="24536-184">An example is a paged fetch to load a batch of table rows.</span></span> <span data-ttu-id="24536-185">Diğer bir örnek <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> , .NET Framework içinde yineleyiciler uygulayan yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="24536-185">Another example is the <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> method, which implements iterators within the .NET Framework.</span></span>

- <span data-ttu-id="24536-186">Yineleyici içinde listenin oluşturulmasını yalıt.</span><span class="sxs-lookup"><span data-stu-id="24536-186">Encapsulate building the list in the iterator.</span></span> <span data-ttu-id="24536-187">Yineleyici yönteminde, listeyi derleyip her sonucu bir döngüde sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="24536-187">In the iterator method, you can build the list and then yield each result in a loop.</span></span>

## <a name="see-also"></a><span data-ttu-id="24536-188">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="24536-188">See also</span></span>

- <xref:System.Collections.Generic>
- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="24536-189">For Each...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="24536-189">For Each...Next Statement</span></span>](../../language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="24536-190">Yield Deyimi</span><span class="sxs-lookup"><span data-stu-id="24536-190">Yield Statement</span></span>](../../language-reference/statements/yield-statement.md)
- [<span data-ttu-id="24536-191">Iterator</span><span class="sxs-lookup"><span data-stu-id="24536-191">Iterator</span></span>](../../language-reference/modifiers/iterator.md)
