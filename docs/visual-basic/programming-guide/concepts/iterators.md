---
description: 'Daha fazla bilgi edinin: yineleyiciler (Visual Basic)'
title: Yineleyiciler
ms.date: 07/20/2015
ms.assetid: f26b5c1e-fe9d-4004-b287-da7919d717ae
ms.openlocfilehash: 9d12bd436a976e3f84dbd063ca746fc7e3b17bfb
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100462158"
---
# <a name="iterators-visual-basic"></a><span data-ttu-id="7580a-103">Yineleyiciler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7580a-103">Iterators (Visual Basic)</span></span>

<span data-ttu-id="7580a-104">Bir *Yineleyici* , listeler ve diziler gibi koleksiyonlardan dolaşmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7580a-104">An *iterator* can be used to step through collections such as lists and arrays.</span></span>

<span data-ttu-id="7580a-105">Yineleyici yöntemi veya `get` erişimcisi bir koleksiyon üzerinde özel bir yineleme gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="7580a-105">An iterator method or `get` accessor performs a custom iteration over a collection.</span></span> <span data-ttu-id="7580a-106">Yineleyici yöntemi, her öğeyi birer birer döndürmek için [yield](../../language-reference/statements/yield-statement.md) ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="7580a-106">An iterator method uses the [Yield](../../language-reference/statements/yield-statement.md) statement to return each element one at a time.</span></span> <span data-ttu-id="7580a-107">Bir `Yield` ifadeye ulaşıldığında, koddaki geçerli konum hatırlanır.</span><span class="sxs-lookup"><span data-stu-id="7580a-107">When a `Yield` statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="7580a-108">Bu konumdan, Yineleyici işlevinin bir sonraki çağrılışında yürütme yeniden başlatılır.</span><span class="sxs-lookup"><span data-stu-id="7580a-108">Execution is restarted from that location the next time the iterator function is called.</span></span>

<span data-ttu-id="7580a-109">Her biri Için bir kullanarak istemci kodundan bir yineleyici kullanıyorsunuz [... Sonraki](../../language-reference/statements/for-each-next-statement.md) ifade veya BIR LINQ sorgusu kullanarak.</span><span class="sxs-lookup"><span data-stu-id="7580a-109">You consume an iterator from client code by using a [For Each…Next](../../language-reference/statements/for-each-next-statement.md) statement, or by using a LINQ query.</span></span>

<span data-ttu-id="7580a-110">Aşağıdaki örnekte, döngünün ilk yinelemesi `For Each` yürütmenin `SomeNumbers` ilk ifadeye ulaşılana kadar yineleyici yönteminde devam etmesine neden olur `Yield` .</span><span class="sxs-lookup"><span data-stu-id="7580a-110">In the following example, the first iteration of the `For Each` loop causes execution to proceed  in the `SomeNumbers` iterator method until the first `Yield` statement is reached.</span></span> <span data-ttu-id="7580a-111">Bu yineleme 3 değerini döndürür ve yineleyici yöntemindeki geçerli konum korunur.</span><span class="sxs-lookup"><span data-stu-id="7580a-111">This iteration returns a value of 3, and the current location in the iterator method is retained.</span></span> <span data-ttu-id="7580a-112">Döngünün bir sonraki yinelemesinde, yineleyici yönteminde yürütme kaldığınız yerden devam eder, bir ifadeye ulaştığında yeniden durdurulur `Yield` .</span><span class="sxs-lookup"><span data-stu-id="7580a-112">On the next iteration of the loop, execution in the iterator method continues from where it left off, again stopping when it reaches a `Yield` statement.</span></span> <span data-ttu-id="7580a-113">Bu yineleme 5 değerini döndürür ve yineleyici yöntemindeki geçerli konum yeniden korunur.</span><span class="sxs-lookup"><span data-stu-id="7580a-113">This iteration returns a value of 5, and the current location in the iterator method is again retained.</span></span> <span data-ttu-id="7580a-114">Yineleyici yönteminin sonuna ulaşıldığında döngü tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="7580a-114">The loop completes when the end of the iterator method is reached.</span></span>

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

<span data-ttu-id="7580a-115">Bir yineleyici yönteminin veya erişimcisinin dönüş türü `get` <xref:System.Collections.IEnumerable> ,, <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.IEnumerator> , veya olabilir <xref:System.Collections.Generic.IEnumerator%601> .</span><span class="sxs-lookup"><span data-stu-id="7580a-115">The return type of an iterator method or `get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

<span data-ttu-id="7580a-116">`Exit Function` `Return` Yinelemeyi sonlandırmak için bir veya ifadesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7580a-116">You can use an `Exit Function` or `Return` statement to end the iteration.</span></span>

<span data-ttu-id="7580a-117">Visual Basic Yineleyici işlevi veya `get` erişimci bildirimi bir [Yineleyici](../../language-reference/modifiers/iterator.md) değiştiricisi içerir.</span><span class="sxs-lookup"><span data-stu-id="7580a-117">A Visual Basic iterator function or `get` accessor declaration includes an [Iterator](../../language-reference/modifiers/iterator.md) modifier.</span></span>

<span data-ttu-id="7580a-118">Yineleyiciler, Visual Studio 2012 ' de Visual Basic sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="7580a-118">Iterators were introduced in Visual Basic in Visual Studio 2012.</span></span>

<span data-ttu-id="7580a-119">**Bu konuda**</span><span class="sxs-lookup"><span data-stu-id="7580a-119">**In this topic**</span></span>

- [<span data-ttu-id="7580a-120">Basit Yineleyici</span><span class="sxs-lookup"><span data-stu-id="7580a-120">Simple Iterator</span></span>](#BKMK_SimpleIterator)

- [<span data-ttu-id="7580a-121">Koleksiyon sınıfı oluşturma</span><span class="sxs-lookup"><span data-stu-id="7580a-121">Creating a Collection Class</span></span>](#BKMK_CollectionClass)

- [<span data-ttu-id="7580a-122">TRY blokları</span><span class="sxs-lookup"><span data-stu-id="7580a-122">Try Blocks</span></span>](#BKMK_TryBlocks)

- [<span data-ttu-id="7580a-123">Anonim Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7580a-123">Anonymous Methods</span></span>](#BKMK_AnonymousMethods)

- [<span data-ttu-id="7580a-124">Bir genel liste ile yineleyiciler kullanma</span><span class="sxs-lookup"><span data-stu-id="7580a-124">Using Iterators with a Generic List</span></span>](#BKMK_GenericList)

- [<span data-ttu-id="7580a-125">Sözdizimi bilgileri</span><span class="sxs-lookup"><span data-stu-id="7580a-125">Syntax Information</span></span>](#BKMK_SyntaxInformation)

- [<span data-ttu-id="7580a-126">Teknik Uygulama</span><span class="sxs-lookup"><span data-stu-id="7580a-126">Technical Implementation</span></span>](#BKMK_Technical)

- [<span data-ttu-id="7580a-127">Yineleyicilerin kullanımı</span><span class="sxs-lookup"><span data-stu-id="7580a-127">Use of Iterators</span></span>](#BKMK_UseOfIterators)

> [!NOTE]
> <span data-ttu-id="7580a-128">Konunun basit Yineleyici örneği hariç tüm örnekleri için, [](../../language-reference/statements/imports-statement-net-namespace-and-type.md) `System.Collections` ve ad alanları için Imports deyimlerini ekleyin `System.Collections.Generic` .</span><span class="sxs-lookup"><span data-stu-id="7580a-128">For all examples in the topic except the Simple Iterator example, include [Imports](../../language-reference/statements/imports-statement-net-namespace-and-type.md) statements for the `System.Collections` and `System.Collections.Generic` namespaces.</span></span>

## <a name="simple-iterator"></a><a name="BKMK_SimpleIterator"></a> <span data-ttu-id="7580a-129">Basit Yineleyici</span><span class="sxs-lookup"><span data-stu-id="7580a-129">Simple Iterator</span></span>

<span data-ttu-id="7580a-130">Aşağıdaki örnek, Için içinde olan tek bir `Yield` ifadeye sahiptir [... Sonraki](../../language-reference/statements/for-next-statement.md) döngü.</span><span class="sxs-lookup"><span data-stu-id="7580a-130">The following example has a single `Yield` statement that is inside a [For…Next](../../language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="7580a-131">' De `Main` , `For Each` ifade gövdesinin her yinelemesi bir sonraki ifadeye devam eden Yineleyici işlevine bir çağrı oluşturur `Yield` .</span><span class="sxs-lookup"><span data-stu-id="7580a-131">In `Main`, each iteration of the `For Each` statement body creates a call to the iterator function, which proceeds to the next `Yield` statement.</span></span>

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

## <a name="creating-a-collection-class"></a><a name="BKMK_CollectionClass"></a> <span data-ttu-id="7580a-132">Koleksiyon sınıfı oluşturma</span><span class="sxs-lookup"><span data-stu-id="7580a-132">Creating a Collection Class</span></span>

<span data-ttu-id="7580a-133">Aşağıdaki örnekte, `DaysOfTheWeek` sınıfı <xref:System.Collections.IEnumerable> bir yöntemi gerektiren arabirimini uygular <xref:System.Collections.IEnumerable.GetEnumerator%2A> .</span><span class="sxs-lookup"><span data-stu-id="7580a-133">In the following example, the `DaysOfTheWeek` class implements the <xref:System.Collections.IEnumerable> interface, which requires a <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span> <span data-ttu-id="7580a-134">Derleyici, `GetEnumerator` bir döndüren yöntemini dolaylı olarak çağırır <xref:System.Collections.IEnumerator> .</span><span class="sxs-lookup"><span data-stu-id="7580a-134">The compiler implicitly calls the `GetEnumerator` method, which returns an <xref:System.Collections.IEnumerator>.</span></span>

<span data-ttu-id="7580a-135">`GetEnumerator`Yöntemi, yöntemini kullanarak her bir dizeyi birer birer döndürür `Yield` ve `Iterator` işlev bildiriminde bir değiştirici olur.</span><span class="sxs-lookup"><span data-stu-id="7580a-135">The `GetEnumerator` method returns each string one at a time by using the `Yield` statement, and  an `Iterator` modifier is in the function declaration.</span></span>

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

<span data-ttu-id="7580a-136">Aşağıdaki örnek, `Zoo` hayvanlar koleksiyonunu içeren bir sınıf oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7580a-136">The following example creates a `Zoo` class that contains a collection of animals.</span></span>

<span data-ttu-id="7580a-137">`For Each`Sınıf örneğine () başvuran ifade, `theZoo` yöntemi örtük olarak çağırır `GetEnumerator` .</span><span class="sxs-lookup"><span data-stu-id="7580a-137">The `For Each` statement that refers to the class instance (`theZoo`) implicitly calls the `GetEnumerator` method.</span></span> <span data-ttu-id="7580a-138">`For Each` `Birds` Ve özelliklerine başvuran deyimler `Mammals` `AnimalsForType` adlandırılmış yineleyici yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="7580a-138">The `For Each` statements that refer to the `Birds` and `Mammals` properties use the `AnimalsForType` named iterator method.</span></span>

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

## <a name="try-blocks"></a><a name="BKMK_TryBlocks"></a> <span data-ttu-id="7580a-139">TRY blokları</span><span class="sxs-lookup"><span data-stu-id="7580a-139">Try Blocks</span></span>

<span data-ttu-id="7580a-140">Visual Basic `Yield` try bloğundaki bir ifadeye izin verir `Try` [... Yakala... Finally ekstresi](../../language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="7580a-140">Visual Basic allows a `Yield` statement in the `Try` block of a [Try...Catch...Finally Statement](../../language-reference/statements/try-catch-finally-statement.md).</span></span> <span data-ttu-id="7580a-141">`Try`Bir deyime sahip bir blok `Yield` blokları olabilir `Catch` ve bir bloğuna sahip olabilir `Finally` .</span><span class="sxs-lookup"><span data-stu-id="7580a-141">A `Try` block that has a `Yield` statement can have `Catch` blocks, and can have a `Finally` block.</span></span>

<span data-ttu-id="7580a-142">Aşağıdaki örnek, `Try` `Catch` `Finally` bir yineleyici işlevindeki, ve bloklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="7580a-142">The following example includes `Try`, `Catch`, and `Finally` blocks in an iterator function.</span></span> <span data-ttu-id="7580a-143">`Finally`Yineleyici işlevindeki blok `For Each` yineleme bitmeden önce yürütülür.</span><span class="sxs-lookup"><span data-stu-id="7580a-143">The `Finally` block in the iterator function executes before the `For Each` iteration finishes.</span></span>

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

<span data-ttu-id="7580a-144">Bir `Yield` ifade bir `Catch` blok veya blok içinde olamaz `Finally` .</span><span class="sxs-lookup"><span data-stu-id="7580a-144">A `Yield` statement cannot be inside a `Catch` block or a `Finally` block.</span></span>

<span data-ttu-id="7580a-145">`For Each`Gövde (yineleyici yöntemi yerine) bir özel durum oluşturursa, `Catch` Yineleyici işlevindeki bir blok yürütülmez, ancak `Finally` Yineleyici işlevindeki bir blok yürütülür.</span><span class="sxs-lookup"><span data-stu-id="7580a-145">If the `For Each` body (instead of the iterator method) throws an exception, a `Catch` block in the iterator function is not executed, but a `Finally` block in the iterator function is executed.</span></span> <span data-ttu-id="7580a-146">`Catch`Yineleyici işlevi içindeki bir blok yalnızca Yineleyici işlevinin içinde oluşan özel durumları yakalar.</span><span class="sxs-lookup"><span data-stu-id="7580a-146">A `Catch` block inside an iterator function catches only exceptions that occur inside the iterator function.</span></span>

## <a name="anonymous-methods"></a><a name="BKMK_AnonymousMethods"></a> <span data-ttu-id="7580a-147">Anonim Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7580a-147">Anonymous Methods</span></span>

<span data-ttu-id="7580a-148">Visual Basic, anonim bir işlev bir yineleyici işlevi olabilir.</span><span class="sxs-lookup"><span data-stu-id="7580a-148">In Visual Basic, an anonymous function can be an iterator function.</span></span> <span data-ttu-id="7580a-149">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="7580a-149">The following example illustrates this.</span></span>

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

<span data-ttu-id="7580a-150">Aşağıdaki örnek, bağımsız değişkenleri doğrulayan Yineleyici olmayan bir yönteme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="7580a-150">The following example has a non-iterator method that validates the arguments.</span></span> <span data-ttu-id="7580a-151">Yöntemi, koleksiyon öğelerini açıklayan bir anonim yineleyicinin sonucunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="7580a-151">The method returns the result of an anonymous iterator that describes the collection elements.</span></span>

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

<span data-ttu-id="7580a-152">Doğrulama işlemi Yineleyici işlevi içinde ise, gövdenin ilk yinelemesinin başlangıcına kadar doğrulama gerçekleştirilemez `For Each` .</span><span class="sxs-lookup"><span data-stu-id="7580a-152">If validation is instead inside the iterator function, the validation cannot be performed until the start of the first iteration of the `For Each` body.</span></span>

## <a name="using-iterators-with-a-generic-list"></a><a name="BKMK_GenericList"></a> <span data-ttu-id="7580a-153">Bir genel liste ile yineleyiciler kullanma</span><span class="sxs-lookup"><span data-stu-id="7580a-153">Using Iterators with a Generic List</span></span>

<span data-ttu-id="7580a-154">Aşağıdaki örnekte, `Stack(Of T)` Genel sınıf <xref:System.Collections.Generic.IEnumerable%601> genel arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="7580a-154">In the following example, the `Stack(Of T)` generic class implements the <xref:System.Collections.Generic.IEnumerable%601> generic interface.</span></span> <span data-ttu-id="7580a-155">`Push`Yöntemi, türü bir diziye değerler atar `T` .</span><span class="sxs-lookup"><span data-stu-id="7580a-155">The `Push` method assigns values to an array of type `T`.</span></span> <span data-ttu-id="7580a-156"><xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>Yöntemi, ifadesini kullanarak dizi değerlerini döndürür `Yield` .</span><span class="sxs-lookup"><span data-stu-id="7580a-156">The <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method returns the array values by using the `Yield` statement.</span></span>

<span data-ttu-id="7580a-157">Genel yöntemin yanı sıra <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> genel olmayan <xref:System.Collections.IEnumerable.GetEnumerator%2A> yöntemin de uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7580a-157">In addition to the generic <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method, the non-generic <xref:System.Collections.IEnumerable.GetEnumerator%2A> method must also be implemented.</span></span> <span data-ttu-id="7580a-158">Bunun nedeni, <xref:System.Collections.Generic.IEnumerable%601> öğesinden devralmasıdır <xref:System.Collections.IEnumerable> .</span><span class="sxs-lookup"><span data-stu-id="7580a-158">This is because <xref:System.Collections.Generic.IEnumerable%601> inherits from <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="7580a-159">Genel olmayan uygulama genel uygulamaya erteler.</span><span class="sxs-lookup"><span data-stu-id="7580a-159">The non-generic implementation defers to the generic implementation.</span></span>

<span data-ttu-id="7580a-160">Örnek, aynı veri topluluğunda tekrarların çeşitli yollarını desteklemek için adlandırılmış yineleyiciler kullanır.</span><span class="sxs-lookup"><span data-stu-id="7580a-160">The example uses named iterators to support various ways of iterating through the same collection of data.</span></span> <span data-ttu-id="7580a-161">Bu adlandırılmış yineleyiciler, `TopToBottom` ve `BottomToTop` özellikleridir ve `TopN` yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="7580a-161">These named iterators are the `TopToBottom` and `BottomToTop` properties, and the `TopN` method.</span></span>

<span data-ttu-id="7580a-162">`BottomToTop`Özellik bildirimi `Iterator` anahtar sözcüğünü içerir.</span><span class="sxs-lookup"><span data-stu-id="7580a-162">The `BottomToTop` property declaration includes the `Iterator` keyword.</span></span>

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

## <a name="syntax-information"></a><a name="BKMK_SyntaxInformation"></a> <span data-ttu-id="7580a-163">Sözdizimi bilgileri</span><span class="sxs-lookup"><span data-stu-id="7580a-163">Syntax Information</span></span>

<span data-ttu-id="7580a-164">Yineleyici bir yöntem veya erişimci olarak gerçekleşebilir `get` .</span><span class="sxs-lookup"><span data-stu-id="7580a-164">An iterator can occur as a method or `get` accessor.</span></span> <span data-ttu-id="7580a-165">Bir olay, örnek Oluşturucu, statik oluşturucu veya statik yok edicisi içinde yineleyici olamaz.</span><span class="sxs-lookup"><span data-stu-id="7580a-165">An iterator cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>

<span data-ttu-id="7580a-166">Deyimdeki ifade türünden, `Yield` yineleyicinin dönüş türüne örtük bir dönüştürme bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7580a-166">An implicit conversion must exist from the expression type in the `Yield` statement to the return type of the iterator.</span></span>

<span data-ttu-id="7580a-167">Visual Basic, yineleyici yöntemi herhangi bir parametreye sahip olamaz `ByRef` .</span><span class="sxs-lookup"><span data-stu-id="7580a-167">In Visual Basic, an iterator method cannot have any `ByRef` parameters.</span></span>

<span data-ttu-id="7580a-168">Visual Basic, "yield" ayrılmış bir sözcük değildir ve yalnızca bir `Iterator` yöntemde veya erişimcisinde kullanıldığında özel anlamı vardır `get` .</span><span class="sxs-lookup"><span data-stu-id="7580a-168">In Visual Basic, "Yield" is not a reserved word and has special meaning only when it is used in an `Iterator` method or `get` accessor.</span></span>

## <a name="technical-implementation"></a><a name="BKMK_Technical"></a> <span data-ttu-id="7580a-169">Teknik uygulama</span><span class="sxs-lookup"><span data-stu-id="7580a-169">Technical Implementation</span></span>

<span data-ttu-id="7580a-170">Bir yineleyici Yöntem olarak yazdığınızda, derleyici onu bir durum makinesi olan bir iç içe geçmiş sınıfa çevirir.</span><span class="sxs-lookup"><span data-stu-id="7580a-170">Although you write an iterator as a method, the compiler translates it into a nested class that is, in effect, a state machine.</span></span> <span data-ttu-id="7580a-171">Bu sınıf, `For Each...Next` istemci kodundaki döngü devam ettiğinde yineleyicinin konumunu izler.</span><span class="sxs-lookup"><span data-stu-id="7580a-171">This class keeps track of the position of the iterator as long the `For Each...Next` loop in the client code continues.</span></span>

<span data-ttu-id="7580a-172">Derleyicinin ne yaptığını görmek için Ildasm.exe aracını kullanarak bir yineleyici yöntemi için oluşturulan Microsoft ara dil kodunu görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7580a-172">To see what the compiler does, you can use the Ildasm.exe tool to view the Microsoft intermediate language code that is generated for an iterator method.</span></span>

<span data-ttu-id="7580a-173">Bir [sınıf](../../language-reference/statements/class-statement.md) veya [Yapı](../../language-reference/statements/structure-statement.md)için Yineleyici oluşturduğunuzda, tüm arabirimini uygulamanız gerekmez <xref:System.Collections.IEnumerator> .</span><span class="sxs-lookup"><span data-stu-id="7580a-173">When you create an iterator for a [class](../../language-reference/statements/class-statement.md) or [struct](../../language-reference/statements/structure-statement.md), you do not have to implement the whole <xref:System.Collections.IEnumerator> interface.</span></span> <span data-ttu-id="7580a-174">Derleyici yineleyiciyi algıladığında, `Current` `MoveNext` veya arabiriminin,, ve yöntemlerini otomatik olarak oluşturur `Dispose` <xref:System.Collections.IEnumerator> <xref:System.Collections.Generic.IEnumerator%601> .</span><span class="sxs-lookup"><span data-stu-id="7580a-174">When the compiler detects the iterator, it automatically generates the `Current`, `MoveNext`, and `Dispose` methods of the <xref:System.Collections.IEnumerator> or <xref:System.Collections.Generic.IEnumerator%601> interface.</span></span>

<span data-ttu-id="7580a-175">Döngünün art arda her tekrarında `For Each…Next` (veya doğrudan çağrısının `IEnumerator.MoveNext` ), sonraki Yineleyici kod gövdesi önceki deyimden sonra devam eder `Yield` .</span><span class="sxs-lookup"><span data-stu-id="7580a-175">On each successive iteration of the `For Each…Next` loop (or the direct call to `IEnumerator.MoveNext`), the next iterator code body resumes after the previous `Yield` statement.</span></span> <span data-ttu-id="7580a-176">Daha sonra `Yield` Yineleyici gövdesinin sonuna ulaşılana kadar veya bir `Exit Function` veya `Return` ifadesiyle karşılaşana kadar sonraki ifadeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="7580a-176">It then continues to the next `Yield` statement until the end of the iterator body is reached, or until an `Exit Function` or `Return` statement is encountered.</span></span>

<span data-ttu-id="7580a-177">Yineleyiciler <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> yöntemi desteklemez.</span><span class="sxs-lookup"><span data-stu-id="7580a-177">Iterators do not support the <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="7580a-178">Başlangıçtan yeniden yinelemek için yeni bir yineleyici edinmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7580a-178">To re-iterate from the start, you must obtain a new iterator.</span></span>

<span data-ttu-id="7580a-179">Daha fazla bilgi için [Visual Basic dil belirtimine](../../reference/language-specification/index.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="7580a-179">For additional information, see the [Visual Basic Language Specification](../../reference/language-specification/index.md).</span></span>

## <a name="use-of-iterators"></a><a name="BKMK_UseOfIterators"></a> <span data-ttu-id="7580a-180">Yineleyicilerin kullanımı</span><span class="sxs-lookup"><span data-stu-id="7580a-180">Use of Iterators</span></span>

<span data-ttu-id="7580a-181">Yineleyiciler, `For Each` bir liste dizisini doldurmak için karmaşık kod kullanmanız gerektiğinde bir döngünün basitliğini korumanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="7580a-181">Iterators enable you to maintain the simplicity of a `For Each` loop when you need to use complex code to populate a list sequence.</span></span> <span data-ttu-id="7580a-182">Bu, aşağıdakileri yapmak istediğinizde yararlı olabilir:</span><span class="sxs-lookup"><span data-stu-id="7580a-182">This can be useful when you want to do the following:</span></span>

- <span data-ttu-id="7580a-183">İlk döngü yinelemeden sonra liste sırasını değiştirin `For Each` .</span><span class="sxs-lookup"><span data-stu-id="7580a-183">Modify the list sequence after the first `For Each` loop iteration.</span></span>

- <span data-ttu-id="7580a-184">Bir döngünün ilk yinelemesinden önce büyük bir listenin tam olarak yüklenmesini önleyin `For Each` .</span><span class="sxs-lookup"><span data-stu-id="7580a-184">Avoid fully loading a large list before the first iteration of a `For Each` loop.</span></span> <span data-ttu-id="7580a-185">Tablo satırlarını toplu olarak yüklemek için disk belleğine alınmış bir getirme örneği.</span><span class="sxs-lookup"><span data-stu-id="7580a-185">An example is a paged fetch to load a batch of table rows.</span></span> <span data-ttu-id="7580a-186">Diğer bir örnek <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> , .NET Framework içinde yineleyiciler uygulayan yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="7580a-186">Another example is the <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> method, which implements iterators within the .NET Framework.</span></span>

- <span data-ttu-id="7580a-187">Yineleyici içinde listenin oluşturulmasını yalıt.</span><span class="sxs-lookup"><span data-stu-id="7580a-187">Encapsulate building the list in the iterator.</span></span> <span data-ttu-id="7580a-188">Yineleyici yönteminde, listeyi derleyip her sonucu bir döngüde sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7580a-188">In the iterator method, you can build the list and then yield each result in a loop.</span></span>

## <a name="see-also"></a><span data-ttu-id="7580a-189">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7580a-189">See also</span></span>

- <xref:System.Collections.Generic>
- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="7580a-190">For Each...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="7580a-190">For Each...Next Statement</span></span>](../../language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="7580a-191">Yield Deyimi</span><span class="sxs-lookup"><span data-stu-id="7580a-191">Yield Statement</span></span>](../../language-reference/statements/yield-statement.md)
- [<span data-ttu-id="7580a-192">Iterator</span><span class="sxs-lookup"><span data-stu-id="7580a-192">Iterator</span></span>](../../language-reference/modifiers/iterator.md)
