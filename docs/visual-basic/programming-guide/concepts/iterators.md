---
title: Yineleyiciler (Visual Basic)
ms.date: 07/20/2015
ms.assetid: f26b5c1e-fe9d-4004-b287-da7919d717ae
ms.openlocfilehash: f9d5a976badc80c5ce00258f46e1d347f20be2f3
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583356"
---
# <a name="iterators-visual-basic"></a><span data-ttu-id="d18bd-102">Yineleyiciler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d18bd-102">Iterators (Visual Basic)</span></span>

<span data-ttu-id="d18bd-103">Bir *Yineleyici* , listeler ve diziler gibi koleksiyonlardan dolaşmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d18bd-103">An *iterator* can be used to step through collections such as lists and arrays.</span></span>

<span data-ttu-id="d18bd-104">Yineleyici yöntemi veya `get` erişimcisi bir koleksiyon üzerinde özel bir yineleme gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="d18bd-104">An iterator method or `get` accessor performs a custom iteration over a collection.</span></span> <span data-ttu-id="d18bd-105">Yineleyici yöntemi, her öğeyi birer birer döndürmek için [yield](../../../visual-basic/language-reference/statements/yield-statement.md) ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d18bd-105">An iterator method uses the [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) statement to return each element one at a time.</span></span> <span data-ttu-id="d18bd-106">@No__t_0 ifadeye ulaşıldığında, koddaki geçerli konum hatırlanır.</span><span class="sxs-lookup"><span data-stu-id="d18bd-106">When a `Yield` statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="d18bd-107">Bu konumdan, Yineleyici işlevinin bir sonraki çağrılışında yürütme yeniden başlatılır.</span><span class="sxs-lookup"><span data-stu-id="d18bd-107">Execution is restarted from that location the next time the iterator function is called.</span></span>

<span data-ttu-id="d18bd-108">Her biri Için bir kullanarak istemci kodundan bir yineleyici kullanıyorsunuz [... Sonraki](../../../visual-basic/language-reference/statements/for-each-next-statement.md) ifade veya BIR LINQ sorgusu kullanarak.</span><span class="sxs-lookup"><span data-stu-id="d18bd-108">You consume an iterator from client code by using a [For Each…Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement, or by using a LINQ query.</span></span>

<span data-ttu-id="d18bd-109">Aşağıdaki örnekte, ilk `Yield` ifadeye ulaşılana kadar `For Each` döngüsünün ilk yinelemesi yürütmenin `SomeNumbers` yineleyici yönteminde devam etmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="d18bd-109">In the following example, the first iteration of the `For Each` loop causes execution to proceed  in the `SomeNumbers` iterator method until the first `Yield` statement is reached.</span></span> <span data-ttu-id="d18bd-110">Bu yineleme 3 değerini döndürür ve yineleyici yöntemindeki geçerli konum korunur.</span><span class="sxs-lookup"><span data-stu-id="d18bd-110">This iteration returns a value of 3, and the current location in the iterator method is retained.</span></span> <span data-ttu-id="d18bd-111">Döngünün bir sonraki yinelemesinde, yineleyici yönteminde yürütme kaldığınız yerden devam eder, bir `Yield` bildirimine ulaştığında yeniden durdurulur.</span><span class="sxs-lookup"><span data-stu-id="d18bd-111">On the next iteration of the loop, execution in the iterator method continues from where it left off, again stopping when it reaches a `Yield` statement.</span></span> <span data-ttu-id="d18bd-112">Bu yineleme 5 değerini döndürür ve yineleyici yöntemindeki geçerli konum yeniden korunur.</span><span class="sxs-lookup"><span data-stu-id="d18bd-112">This iteration returns a value of 5, and the current location in the iterator method is again retained.</span></span> <span data-ttu-id="d18bd-113">Yineleyici yönteminin sonuna ulaşıldığında döngü tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="d18bd-113">The loop completes when the end of the iterator method is reached.</span></span>

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

<span data-ttu-id="d18bd-114">Yineleyici yöntemi veya `get` erişimcisinin dönüş türü <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator> veya <xref:System.Collections.Generic.IEnumerator%601> olabilir.</span><span class="sxs-lookup"><span data-stu-id="d18bd-114">The return type of an iterator method or `get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

<span data-ttu-id="d18bd-115">Yinelemeyi sonlandırmak için bir `Exit Function` veya `Return` ifadesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d18bd-115">You can use an `Exit Function` or `Return` statement to end the iteration.</span></span>

<span data-ttu-id="d18bd-116">Visual Basic Yineleyici işlevi veya `get` erişimci bildirimi bir [Yineleyici](../../../visual-basic/language-reference/modifiers/iterator.md) değiştiricisi içerir.</span><span class="sxs-lookup"><span data-stu-id="d18bd-116">A Visual Basic iterator function or `get` accessor declaration includes an [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md) modifier.</span></span>

<span data-ttu-id="d18bd-117">Yineleyiciler, Visual Studio 2012 ' de Visual Basic sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="d18bd-117">Iterators were introduced in Visual Basic in Visual Studio 2012.</span></span>

<span data-ttu-id="d18bd-118">**Bu konuda**</span><span class="sxs-lookup"><span data-stu-id="d18bd-118">**In this topic**</span></span>

- [<span data-ttu-id="d18bd-119">Basit Yineleyici</span><span class="sxs-lookup"><span data-stu-id="d18bd-119">Simple Iterator</span></span>](#BKMK_SimpleIterator)

- [<span data-ttu-id="d18bd-120">Koleksiyon sınıfı oluşturma</span><span class="sxs-lookup"><span data-stu-id="d18bd-120">Creating a Collection Class</span></span>](#BKMK_CollectionClass)

- [<span data-ttu-id="d18bd-121">TRY blokları</span><span class="sxs-lookup"><span data-stu-id="d18bd-121">Try Blocks</span></span>](#BKMK_TryBlocks)

- [<span data-ttu-id="d18bd-122">Anonim Metotlar</span><span class="sxs-lookup"><span data-stu-id="d18bd-122">Anonymous Methods</span></span>](#BKMK_AnonymousMethods)

- [<span data-ttu-id="d18bd-123">Bir genel liste ile yineleyiciler kullanma</span><span class="sxs-lookup"><span data-stu-id="d18bd-123">Using Iterators with a Generic List</span></span>](#BKMK_GenericList)

- [<span data-ttu-id="d18bd-124">Sözdizimi bilgileri</span><span class="sxs-lookup"><span data-stu-id="d18bd-124">Syntax Information</span></span>](#BKMK_SyntaxInformation)

- [<span data-ttu-id="d18bd-125">Teknik uygulama</span><span class="sxs-lookup"><span data-stu-id="d18bd-125">Technical Implementation</span></span>](#BKMK_Technical)

- [<span data-ttu-id="d18bd-126">Yineleyicilerin kullanımı</span><span class="sxs-lookup"><span data-stu-id="d18bd-126">Use of Iterators</span></span>](#BKMK_UseOfIterators)

> [!NOTE]
> <span data-ttu-id="d18bd-127">Konunun basit Yineleyici örneği hariç tüm örnekleri için, `System.Collections` ve `System.Collections.Generic` ad alanları için [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) deyimlerini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d18bd-127">For all examples in the topic except the Simple Iterator example, include [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) statements for the `System.Collections` and `System.Collections.Generic` namespaces.</span></span>

## <a name="BKMK_SimpleIterator"></a><span data-ttu-id="d18bd-128">Basit Yineleyici</span><span class="sxs-lookup"><span data-stu-id="d18bd-128">Simple Iterator</span></span>

<span data-ttu-id="d18bd-129">Aşağıdaki örnek, Için içinde olan tek bir `Yield` bildirimine sahiptir [... Sonraki](../../../visual-basic/language-reference/statements/for-next-statement.md) döngü.</span><span class="sxs-lookup"><span data-stu-id="d18bd-129">The following example has a single `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="d18bd-130">@No__t_0, `For Each` deyimin gövdesinin her yinelemesi, bir sonraki `Yield` ifadesine devam eden Yineleyici işlevine bir çağrı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d18bd-130">In `Main`, each iteration of the `For Each` statement body creates a call to the iterator function, which proceeds to the next `Yield` statement.</span></span>

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

## <a name="BKMK_CollectionClass"></a><span data-ttu-id="d18bd-131">Koleksiyon sınıfı oluşturma</span><span class="sxs-lookup"><span data-stu-id="d18bd-131">Creating a Collection Class</span></span>

<span data-ttu-id="d18bd-132">Aşağıdaki örnekte, `DaysOfTheWeek` sınıfı bir <xref:System.Collections.IEnumerable.GetEnumerator%2A> yöntemi gerektiren <xref:System.Collections.IEnumerable> arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="d18bd-132">In the following example, the `DaysOfTheWeek` class implements the <xref:System.Collections.IEnumerable> interface, which requires a <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span> <span data-ttu-id="d18bd-133">Derleyici, bir <xref:System.Collections.IEnumerator> döndüren `GetEnumerator` yöntemini örtülü olarak çağırır.</span><span class="sxs-lookup"><span data-stu-id="d18bd-133">The compiler implicitly calls the `GetEnumerator` method, which returns an <xref:System.Collections.IEnumerator>.</span></span>

<span data-ttu-id="d18bd-134">@No__t_0 yöntemi her bir dizeyi her bir kez `Yield` ifadesini kullanarak döndürür ve bir `Iterator` değiştiricisi işlev bildiriminde bulunur.</span><span class="sxs-lookup"><span data-stu-id="d18bd-134">The `GetEnumerator` method returns each string one at a time by using the `Yield` statement, and  an `Iterator` modifier is in the function declaration.</span></span>

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

<span data-ttu-id="d18bd-135">Aşağıdaki örnek, hayvanlar koleksiyonu içeren bir `Zoo` sınıfı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d18bd-135">The following example creates a `Zoo` class that contains a collection of animals.</span></span>

<span data-ttu-id="d18bd-136">Sınıf örneğine (`theZoo`) başvuran `For Each` ifade `GetEnumerator` yöntemini örtülü olarak çağırır.</span><span class="sxs-lookup"><span data-stu-id="d18bd-136">The `For Each` statement that refers to the class instance (`theZoo`) implicitly calls the `GetEnumerator` method.</span></span> <span data-ttu-id="d18bd-137">@No__t_1 ve `Mammals` özelliklerine başvuran `For Each` deyimleri, `AnimalsForType` adlı yineleyici yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d18bd-137">The `For Each` statements that refer to the `Birds` and `Mammals` properties use the `AnimalsForType` named iterator method.</span></span>

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

## <a name="BKMK_TryBlocks"></a><span data-ttu-id="d18bd-138">TRY blokları</span><span class="sxs-lookup"><span data-stu-id="d18bd-138">Try Blocks</span></span>

<span data-ttu-id="d18bd-139">Visual Basic TRY `Try` bloğunda `Yield` bildirimine izin verir [... Yakala... Finally ekstresi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d18bd-139">Visual Basic allows a `Yield` statement in the `Try` block of a [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span> <span data-ttu-id="d18bd-140">@No__t_1 bildirimine sahip bir `Try` bloğunda `Catch` blokları olabilir ve bir `Finally` bloğuna sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="d18bd-140">A `Try` block that has a `Yield` statement can have `Catch` blocks, and can have a `Finally` block.</span></span>

<span data-ttu-id="d18bd-141">Aşağıdaki örnek bir yineleyici işlevinde `Try`, `Catch` ve `Finally` bloklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="d18bd-141">The following example includes `Try`, `Catch`, and `Finally` blocks in an iterator function.</span></span> <span data-ttu-id="d18bd-142">Yineleyici işlevindeki `Finally` bloğu, `For Each` yineleme tamamlanmadan önce yürütülür.</span><span class="sxs-lookup"><span data-stu-id="d18bd-142">The `Finally` block in the iterator function executes before the `For Each` iteration finishes.</span></span>

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

<span data-ttu-id="d18bd-143">@No__t_0 bir ifade `Catch` bloğunun veya `Finally` bloğunun içinde olamaz.</span><span class="sxs-lookup"><span data-stu-id="d18bd-143">A `Yield` statement cannot be inside a `Catch` block or a `Finally` block.</span></span>

<span data-ttu-id="d18bd-144">@No__t_0 gövdesi (yineleyici yöntemi yerine) bir özel durum oluşturursa, yineleyici işlevindeki bir `Catch` bloğu yürütülmez, ancak Yineleyici işlevindeki bir `Finally` bloğu yürütülür.</span><span class="sxs-lookup"><span data-stu-id="d18bd-144">If the `For Each` body (instead of the iterator method) throws an exception, a `Catch` block in the iterator function is not executed, but a `Finally` block in the iterator function is executed.</span></span> <span data-ttu-id="d18bd-145">Yineleyici işlevi içindeki bir `Catch` bloğu yalnızca Yineleyici işlevinin içinde oluşan özel durumları yakalar.</span><span class="sxs-lookup"><span data-stu-id="d18bd-145">A `Catch` block inside an iterator function catches only exceptions that occur inside the iterator function.</span></span>

## <a name="BKMK_AnonymousMethods"></a><span data-ttu-id="d18bd-146">Anonim Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d18bd-146">Anonymous Methods</span></span>

<span data-ttu-id="d18bd-147">Visual Basic, anonim bir işlev bir yineleyici işlevi olabilir.</span><span class="sxs-lookup"><span data-stu-id="d18bd-147">In Visual Basic, an anonymous function can be an iterator function.</span></span> <span data-ttu-id="d18bd-148">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="d18bd-148">The following example illustrates this.</span></span>

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

<span data-ttu-id="d18bd-149">Aşağıdaki örnek, bağımsız değişkenleri doğrulayan Yineleyici olmayan bir yönteme sahiptir.</span><span class="sxs-lookup"><span data-stu-id="d18bd-149">The following example has a non-iterator method that validates the arguments.</span></span> <span data-ttu-id="d18bd-150">Yöntemi, koleksiyon öğelerini açıklayan bir anonim yineleyicinin sonucunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="d18bd-150">The method returns the result of an anonymous iterator that describes the collection elements.</span></span>

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

<span data-ttu-id="d18bd-151">Doğrulama işlemi Yineleyici işlevinin içindeyse, `For Each` gövdesinin ilk yinelemesinin başlangıcına kadar doğrulama gerçekleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="d18bd-151">If validation is instead inside the iterator function, the validation cannot be performed until the start of the first iteration of the `For Each` body.</span></span>

## <a name="BKMK_GenericList"></a><span data-ttu-id="d18bd-152">Bir genel liste ile yineleyiciler kullanma</span><span class="sxs-lookup"><span data-stu-id="d18bd-152">Using Iterators with a Generic List</span></span>

<span data-ttu-id="d18bd-153">Aşağıdaki örnekte, `Stack(Of T)` genel sınıfı <xref:System.Collections.Generic.IEnumerable%601> genel arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="d18bd-153">In the following example, the `Stack(Of T)` generic class implements the <xref:System.Collections.Generic.IEnumerable%601> generic interface.</span></span> <span data-ttu-id="d18bd-154">@No__t_0 yöntemi `T` türünde bir diziye değerler atar.</span><span class="sxs-lookup"><span data-stu-id="d18bd-154">The `Push` method assigns values to an array of type `T`.</span></span> <span data-ttu-id="d18bd-155">@No__t_0 yöntemi `Yield` ifadesini kullanarak dizi değerlerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="d18bd-155">The <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method returns the array values by using the `Yield` statement.</span></span>

<span data-ttu-id="d18bd-156">Genel <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> metoduna ek olarak, genel olmayan <xref:System.Collections.IEnumerable.GetEnumerator%2A> yönteminin da uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d18bd-156">In addition to the generic <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method, the non-generic <xref:System.Collections.IEnumerable.GetEnumerator%2A> method must also be implemented.</span></span> <span data-ttu-id="d18bd-157">Bunun nedeni <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.IEnumerable> devralmasıdır.</span><span class="sxs-lookup"><span data-stu-id="d18bd-157">This is because <xref:System.Collections.Generic.IEnumerable%601> inherits from <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="d18bd-158">Genel olmayan uygulama genel uygulamaya erteler.</span><span class="sxs-lookup"><span data-stu-id="d18bd-158">The non-generic implementation defers to the generic implementation.</span></span>

<span data-ttu-id="d18bd-159">Örnek, aynı veri topluluğunda tekrarların çeşitli yollarını desteklemek için adlandırılmış yineleyiciler kullanır.</span><span class="sxs-lookup"><span data-stu-id="d18bd-159">The example uses named iterators to support various ways of iterating through the same collection of data.</span></span> <span data-ttu-id="d18bd-160">Bu adlandırılmış yineleyiciler `TopToBottom` ve `BottomToTop` özelliklerdir ve `TopN` yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="d18bd-160">These named iterators are the `TopToBottom` and `BottomToTop` properties, and the `TopN` method.</span></span>

<span data-ttu-id="d18bd-161">@No__t_0 özelliği bildirimi `Iterator` anahtar sözcüğünü içerir.</span><span class="sxs-lookup"><span data-stu-id="d18bd-161">The `BottomToTop` property declaration includes the `Iterator` keyword.</span></span>

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

## <a name="BKMK_SyntaxInformation"></a><span data-ttu-id="d18bd-162">Sözdizimi bilgileri</span><span class="sxs-lookup"><span data-stu-id="d18bd-162">Syntax Information</span></span>

<span data-ttu-id="d18bd-163">Yineleyici, bir yöntem veya `get` erişimcisi olarak gerçekleşebilir.</span><span class="sxs-lookup"><span data-stu-id="d18bd-163">An iterator can occur as a method or `get` accessor.</span></span> <span data-ttu-id="d18bd-164">Bir olay, örnek Oluşturucu, statik oluşturucu veya statik yok edicisi içinde yineleyici olamaz.</span><span class="sxs-lookup"><span data-stu-id="d18bd-164">An iterator cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>

<span data-ttu-id="d18bd-165">@No__t_0 deyimindeki ifade türünden örtük bir dönüştürme, yineleyicinin dönüş türüne sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d18bd-165">An implicit conversion must exist from the expression type in the `Yield` statement to the return type of the iterator.</span></span>

<span data-ttu-id="d18bd-166">Visual Basic, yineleyici yöntemi `ByRef` parametreye sahip olamaz.</span><span class="sxs-lookup"><span data-stu-id="d18bd-166">In Visual Basic, an iterator method cannot have any `ByRef` parameters.</span></span>

<span data-ttu-id="d18bd-167">Visual Basic, "yield" ayrılmış bir sözcük değildir ve yalnızca bir `Iterator` yönteminde veya `get` erişimcisinde kullanıldığında özel anlamı vardır.</span><span class="sxs-lookup"><span data-stu-id="d18bd-167">In Visual Basic, "Yield" is not a reserved word and has special meaning only when it is used in an `Iterator` method or `get` accessor.</span></span>

## <a name="BKMK_Technical"></a><span data-ttu-id="d18bd-168">Teknik uygulama</span><span class="sxs-lookup"><span data-stu-id="d18bd-168">Technical Implementation</span></span>

<span data-ttu-id="d18bd-169">Bir yineleyici Yöntem olarak yazdığınızda, derleyici onu bir durum makinesi olan bir iç içe geçmiş sınıfa çevirir.</span><span class="sxs-lookup"><span data-stu-id="d18bd-169">Although you write an iterator as a method, the compiler translates it into a nested class that is, in effect, a state machine.</span></span> <span data-ttu-id="d18bd-170">Bu sınıf, istemci kodundaki `For Each...Next` döngüsünün devam ettiği sürece yineleyicinin konumunu izler.</span><span class="sxs-lookup"><span data-stu-id="d18bd-170">This class keeps track of the position of the iterator as long the `For Each...Next` loop in the client code continues.</span></span>

<span data-ttu-id="d18bd-171">Derleyicinin ne yaptığını görmek için, bir yineleyici yöntemi için oluşturulan Microsoft ara dil kodunu görüntülemek için ıldadsm. exe aracını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d18bd-171">To see what the compiler does, you can use the Ildasm.exe tool to view the Microsoft intermediate language code that is generated for an iterator method.</span></span>

<span data-ttu-id="d18bd-172">Bir [sınıf](../../../csharp/language-reference/keywords/class.md) veya [Yapı](../../../csharp/language-reference/keywords/struct.md)için yineleyici oluşturduğunuzda, tüm <xref:System.Collections.IEnumerator> arabirimini uygulamanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="d18bd-172">When you create an iterator for a [class](../../../csharp/language-reference/keywords/class.md) or [struct](../../../csharp/language-reference/keywords/struct.md), you do not have to implement the whole <xref:System.Collections.IEnumerator> interface.</span></span> <span data-ttu-id="d18bd-173">Derleyici yineleyiciyi algıladığında, <xref:System.Collections.IEnumerator> veya <xref:System.Collections.Generic.IEnumerator%601> arabiriminin `Current`, `MoveNext` ve `Dispose` yöntemlerini otomatik olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d18bd-173">When the compiler detects the iterator, it automatically generates the `Current`, `MoveNext`, and `Dispose` methods of the <xref:System.Collections.IEnumerator> or <xref:System.Collections.Generic.IEnumerator%601> interface.</span></span>

<span data-ttu-id="d18bd-174">@No__t_0 döngüsünün art arda her tekrarında (veya doğrudan `IEnumerator.MoveNext` çağrısı), sonraki Yineleyici kod gövdesi önceki `Yield` deyimden sonra devam eder.</span><span class="sxs-lookup"><span data-stu-id="d18bd-174">On each successive iteration of the `For Each…Next` loop (or the direct call to `IEnumerator.MoveNext`), the next iterator code body resumes after the previous `Yield` statement.</span></span> <span data-ttu-id="d18bd-175">Daha sonra Yineleyici gövdesinin sonuna ulaşılana kadar veya bir `Exit Function` ya da `Return` ifadesiyle karşılaşana kadar sonraki `Yield` bildirimine devam eder.</span><span class="sxs-lookup"><span data-stu-id="d18bd-175">It then continues to the next `Yield` statement until the end of the iterator body is reached, or until an `Exit Function` or `Return` statement is encountered.</span></span>

<span data-ttu-id="d18bd-176">Yineleyiciler <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> metodunu desteklemez.</span><span class="sxs-lookup"><span data-stu-id="d18bd-176">Iterators do not support the <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="d18bd-177">Başlangıçtan yeniden yinelemek için yeni bir yineleyici edinmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d18bd-177">To re-iterate from the start, you must obtain a new iterator.</span></span>

<span data-ttu-id="d18bd-178">Daha fazla bilgi için [Visual Basic dil belirtimine](../../../visual-basic/reference/language-specification/index.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="d18bd-178">For additional information, see the [Visual Basic Language Specification](../../../visual-basic/reference/language-specification/index.md).</span></span>

## <a name="BKMK_UseOfIterators"></a><span data-ttu-id="d18bd-179">Yineleyicilerin kullanımı</span><span class="sxs-lookup"><span data-stu-id="d18bd-179">Use of Iterators</span></span>

<span data-ttu-id="d18bd-180">Yineleyiciler, bir liste dizisini doldurmak için karmaşık kod kullanmanız gerektiğinde `For Each` döngüsünün basitliğini korumanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="d18bd-180">Iterators enable you to maintain the simplicity of a `For Each` loop when you need to use complex code to populate a list sequence.</span></span> <span data-ttu-id="d18bd-181">Bu, aşağıdakileri yapmak istediğinizde yararlı olabilir:</span><span class="sxs-lookup"><span data-stu-id="d18bd-181">This can be useful when you want to do the following:</span></span>

- <span data-ttu-id="d18bd-182">İlk `For Each` döngüsü yinelemeden sonra liste sırasını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d18bd-182">Modify the list sequence after the first `For Each` loop iteration.</span></span>

- <span data-ttu-id="d18bd-183">@No__t_0 döngüsünün ilk yinelemesinden önce büyük bir listenin tam olarak yüklenmesini önleyin.</span><span class="sxs-lookup"><span data-stu-id="d18bd-183">Avoid fully loading a large list before the first iteration of a `For Each` loop.</span></span> <span data-ttu-id="d18bd-184">Tablo satırlarını toplu olarak yüklemek için disk belleğine alınmış bir getirme örneği.</span><span class="sxs-lookup"><span data-stu-id="d18bd-184">An example is a paged fetch to load a batch of table rows.</span></span> <span data-ttu-id="d18bd-185">Başka bir örnek, .NET Framework içinde yineleyiciler uygulayan <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="d18bd-185">Another example is the <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> method, which implements iterators within the .NET Framework.</span></span>

- <span data-ttu-id="d18bd-186">Yineleyici içinde listenin oluşturulmasını yalıt.</span><span class="sxs-lookup"><span data-stu-id="d18bd-186">Encapsulate building the list in the iterator.</span></span> <span data-ttu-id="d18bd-187">Yineleyici yönteminde, listeyi derleyip her sonucu bir döngüde sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d18bd-187">In the iterator method, you can build the list and then yield each result in a loop.</span></span>

## <a name="see-also"></a><span data-ttu-id="d18bd-188">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d18bd-188">See also</span></span>

- <xref:System.Collections.Generic>
- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="d18bd-189">For Each...Next Deyimi</span><span class="sxs-lookup"><span data-stu-id="d18bd-189">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="d18bd-190">Yield Deyimi</span><span class="sxs-lookup"><span data-stu-id="d18bd-190">Yield Statement</span></span>](../../../visual-basic/language-reference/statements/yield-statement.md)
- [<span data-ttu-id="d18bd-191">Iterator</span><span class="sxs-lookup"><span data-stu-id="d18bd-191">Iterator</span></span>](../../../visual-basic/language-reference/modifiers/iterator.md)
