---
title: 'Nasıl yapılır: LINQ sorguları (Visual Basic) için özel yöntemler'
ms.date: 07/20/2015
ms.assetid: 099b2e2a-83cd-45c6-aa4d-01b398b5faaf
ms.openlocfilehash: 59d08f7b7799964063514ad294567aadd11b0579
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2019
ms.locfileid: "59614015"
---
# <a name="how-to-add-custom-methods-for-linq-queries-visual-basic"></a><span data-ttu-id="a23e0-102">Nasıl yapılır: LINQ sorguları (Visual Basic) için özel yöntemler</span><span class="sxs-lookup"><span data-stu-id="a23e0-102">How to: Add Custom Methods for LINQ Queries (Visual Basic)</span></span>

<span data-ttu-id="a23e0-103">İçin genişletme yöntemleri ekleyerek LINQ sorguları için kullanabileceğiniz yöntemleri kümesini genişletebilirsiniz <xref:System.Collections.Generic.IEnumerable%601> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="a23e0-103">You can extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="a23e0-104">Örneğin, standart ortalama veya en fazla işlem ek olarak, değerler dizisinin tek bir değeri hesaplamak için özel bir toplama yöntemi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a23e0-104">For example, in addition to the standard average or maximum operations, you can create a custom aggregate method to compute a single value from a sequence of values.</span></span> <span data-ttu-id="a23e0-105">Özel bir filtre veya belirli veri dönüştürme için değerler olarak çalışır ve yeni bir dizisini döndüren bir yöntemi de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a23e0-105">You can also create a method that works as a custom filter or a specific data transform for a sequence of values and returns a new sequence.</span></span> <span data-ttu-id="a23e0-106">Bu tür yöntemler örnekler <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, ve <xref:System.Linq.Enumerable.Reverse%2A>.</span><span class="sxs-lookup"><span data-stu-id="a23e0-106">Examples of such methods are <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, and <xref:System.Linq.Enumerable.Reverse%2A>.</span></span>

<span data-ttu-id="a23e0-107">Genişlettiğinizde <xref:System.Collections.Generic.IEnumerable%601> arabirimi, herhangi bir sıralanabilir koleksiyonun özel yöntemlerinizi uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a23e0-107">When you extend the <xref:System.Collections.Generic.IEnumerable%601> interface, you can apply your custom methods to any enumerable collection.</span></span> <span data-ttu-id="a23e0-108">Daha fazla bilgi için [genişletme yöntemleri](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="a23e0-108">For more information, see [Extension Methods](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).</span></span>

## <a name="adding-an-aggregate-method"></a><span data-ttu-id="a23e0-109">Bir toplama yöntemi ekleme</span><span class="sxs-lookup"><span data-stu-id="a23e0-109">Adding an Aggregate Method</span></span>

<span data-ttu-id="a23e0-110">Bir toplama yöntemi, bir değerler kümesinden tek bir değer hesaplar.</span><span class="sxs-lookup"><span data-stu-id="a23e0-110">An aggregate method computes a single value from a set of values.</span></span> <span data-ttu-id="a23e0-111">LINQ dahil olmak üzere çeşitli toplama yöntemleri sağlar <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, ve <xref:System.Linq.Enumerable.Max%2A>.</span><span class="sxs-lookup"><span data-stu-id="a23e0-111">LINQ provides several aggregate methods, including <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Max%2A>.</span></span> <span data-ttu-id="a23e0-112">Bir uzantı yöntemine ekleyerek kendi toplama yöntemi oluşturabilirsiniz <xref:System.Collections.Generic.IEnumerable%601> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="a23e0-112">You can create your own aggregate method by adding an extension method to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>

<span data-ttu-id="a23e0-113">Aşağıdaki kod örneği, adında bir genişletme yöntemi oluşturma işlemi gösterilmektedir `Median` sayı türünde bir dizi için bir ORTANCA işlem `double`.</span><span class="sxs-lookup"><span data-stu-id="a23e0-113">The following code example shows how to create an extension method called `Median` to compute a median for a sequence of numbers of type `double`.</span></span>

```vb
Imports System.Runtime.CompilerServices

Module LINQExtension

    ' Extension method for the IEnumerable(of T) interface.
    ' The method accepts only values of the Double type.
    <Extension()>
    Function Median(ByVal source As IEnumerable(Of Double)) As Double
        If source.Count = 0 Then
            Throw New InvalidOperationException("Cannot compute median for an empty set.")
        End If

        Dim sortedSource = From number In source
                           Order By number

        Dim itemIndex = sortedSource.Count \ 2

        If sortedSource.Count Mod 2 = 0 Then
            ' Even number of items in list.
            Return (sortedSource(itemIndex) + sortedSource(itemIndex - 1)) / 2
        Else
            ' Odd number of items in list.
            Return sortedSource(itemIndex)
        End If
    End Function
End Module
```

<span data-ttu-id="a23e0-114">Aynı şekilde diğer toplama yöntemleri çağırmak için herhangi bir sıralanabilir koleksiyonun bu uzantı metodu çağırma <xref:System.Collections.Generic.IEnumerable%601> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="a23e0-114">You call this extension method for any enumerable collection in the same way you call other aggregate methods from the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>

> [!NOTE]
> <span data-ttu-id="a23e0-115">Visual Basic'te ya da bir yöntem çağrısı veya standart sorgu söz dizimi için kullanabileceğiniz `Aggregate` veya `Group By` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="a23e0-115">In Visual Basic, you can either use a method call or standard query syntax for the `Aggregate` or `Group By` clause.</span></span> <span data-ttu-id="a23e0-116">Daha fazla bilgi için [Aggregate tümcesi](../../../../visual-basic/language-reference/queries/aggregate-clause.md) ve [Group yan tümcesi tarafından](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="a23e0-116">For more information, see [Aggregate Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md) and [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>

<span data-ttu-id="a23e0-117">Aşağıdaki kod örneği kullanma işlemini gösterir `Median` türünde bir dizi yöntemi `double`.</span><span class="sxs-lookup"><span data-stu-id="a23e0-117">The following code example shows how to use the `Median` method for an array of type `double`.</span></span>

```vb
Dim numbers1() As Double = {1.9, 2, 8, 4, 5.7, 6, 7.2, 0}

Dim query1 = Aggregate num In numbers1 Into Median()

Console.WriteLine("Double: Median = " & query1)
```

```vb
' This code produces the following output:
'
' Double: Median = 4.85
```

### <a name="overloading-an-aggregate-method-to-accept-various-types"></a><span data-ttu-id="a23e0-118">Çeşitli türleri kabul etmek için bir toplama yöntemi aşırı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="a23e0-118">Overloading an Aggregate Method to Accept Various Types</span></span>

<span data-ttu-id="a23e0-119">Böylece dizileri çeşitli türlerde kabul ettiğiniz toplama yöntemi aşırı yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="a23e0-119">You can overload your aggregate method so that it accepts sequences of various types.</span></span> <span data-ttu-id="a23e0-120">Standart bir yaklaşım, her tür için bir aşırı oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="a23e0-120">The standard approach is to create an overload for each type.</span></span> <span data-ttu-id="a23e0-121">Başka bir yaklaşım genel bir tür olması ve temsilci kullanarak belirli bir türe dönüştürme aşırı oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="a23e0-121">Another approach is to create an overload that will take a generic type and convert it to a specific type by using a delegate.</span></span> <span data-ttu-id="a23e0-122">Ayrıca, iki yaklaşımı birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a23e0-122">You can also combine both approaches.</span></span>

#### <a name="to-create-an-overload-for-each-type"></a><span data-ttu-id="a23e0-123">Her tür için bir aşırı yükleme oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="a23e0-123">To create an overload for each type</span></span>

<span data-ttu-id="a23e0-124">Desteklemek istediğiniz her bir türü için belirli bir aşırı yükleme oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a23e0-124">You can create a specific overload for each type that you want to support.</span></span> <span data-ttu-id="a23e0-125">Aşağıdaki kod örneği bir aşırı yüklemesini gösterir `Median` yöntemi `integer` türü.</span><span class="sxs-lookup"><span data-stu-id="a23e0-125">The following code example shows an overload of the `Median` method for the `integer` type.</span></span>

```vb
' Integer overload

<Extension()>
Function Median(ByVal source As IEnumerable(Of Integer)) As Double
    Return Aggregate num In source Select CDbl(num) Into med = Median()
End Function
```

<span data-ttu-id="a23e0-126">Artık çağırabilirsiniz `Median` hem de aşırı `integer` ve `double` türleri, aşağıdaki kodda gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="a23e0-126">You can now call the `Median` overloads for both `integer` and `double` types, as shown in the following code:</span></span>

```vb
Dim numbers1() As Double = {1.9, 2, 8, 4, 5.7, 6, 7.2, 0}

Dim query1 = Aggregate num In numbers1 Into Median()

Console.WriteLine("Double: Median = " & query1)
```

```vb
Dim numbers2() As Integer = {1, 2, 3, 4, 5}

Dim query2 = Aggregate num In numbers2 Into Median()

Console.WriteLine("Integer: Median = " & query2)
```

```vb
' This code produces the following output:
'
' Double: Median = 4.85
' Integer: Median = 3
```

#### <a name="to-create-a-generic-overload"></a><span data-ttu-id="a23e0-127">Genel bir aşırı yükleme oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="a23e0-127">To create a generic overload</span></span>

<span data-ttu-id="a23e0-128">Genel nesneler dizisi kabul eden bir aşırı yüklemeyi de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a23e0-128">You can also create an overload that accepts a sequence of generic objects.</span></span> <span data-ttu-id="a23e0-129">Bu aşırı yükleme, bir temsilci bir parametre olarak alır ve genel bir türün nesnelerinin bir dizisi belirli bir türe dönüştürmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="a23e0-129">This overload takes a delegate as a parameter and uses it to convert a sequence of objects of a generic type to a specific type.</span></span>

<span data-ttu-id="a23e0-130">Aşağıdaki kod, bir aşırı yüklemesini göstermektedir `Median` gereken yöntemini <xref:System.Func%602> temsilci bir parametre olarak.</span><span class="sxs-lookup"><span data-stu-id="a23e0-130">The following code shows an overload of the `Median` method that takes the <xref:System.Func%602> delegate as a parameter.</span></span> <span data-ttu-id="a23e0-131">Bu temsilci T genel türünün bir nesnesini alır ve türünde bir nesne döndürür `double`.</span><span class="sxs-lookup"><span data-stu-id="a23e0-131">This delegate takes an object of generic type T and returns an object of type `double`.</span></span>

```vb
' Generic overload.

<Extension()>
Function Median(Of T)(ByVal source As IEnumerable(Of T),
                      ByVal selector As Func(Of T, Double)) As Double
    Return Aggregate num In source Select selector(num) Into med = Median()
End Function
```

<span data-ttu-id="a23e0-132">Artık çağırabilirsiniz `Median` herhangi bir türde nesneler dizisi için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a23e0-132">You can now call the `Median` method for a sequence of objects of any type.</span></span> <span data-ttu-id="a23e0-133">Türü kendi yöntemi aşırı yüklemesini yoksa bir temsilci parametresi geçirmek zorunda.</span><span class="sxs-lookup"><span data-stu-id="a23e0-133">If the type does not have its own method overload, you have to pass a delegate parameter.</span></span> <span data-ttu-id="a23e0-134">Visual Basic'te, bir lambda ifadesi bu amaç için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a23e0-134">In Visual Basic, you can use a lambda expression for this purpose.</span></span> <span data-ttu-id="a23e0-135">Ayrıca, kullanırsanız `Aggregate` veya `Group By` yan tümcesi yerine bir yöntem çağrısı, herhangi bir değer veya kapsamda bu yan tümce ifadesi iletebilir.</span><span class="sxs-lookup"><span data-stu-id="a23e0-135">Also, if you use the `Aggregate` or `Group By` clause instead of the method call, you can pass any value or expression that is in the scope this clause.</span></span>

<span data-ttu-id="a23e0-136">Aşağıdaki kod örneği nasıl çağrılacağını gösterir `Median` yöntemi için tamsayı dizisi ve dize dizisi.</span><span class="sxs-lookup"><span data-stu-id="a23e0-136">The following example code shows how to call the `Median` method for an array of integers and an array of strings.</span></span> <span data-ttu-id="a23e0-137">Dizeler için dize dizisinde uzunluklarının için ORTANCA hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="a23e0-137">For strings, the median for the lengths of strings in the array is calculated.</span></span> <span data-ttu-id="a23e0-138">Bu örnek nasıl geçirileceğini gösterir <xref:System.Func%602> temsilci parametresi `Median` her örneği için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a23e0-138">The example shows how to pass the <xref:System.Func%602> delegate parameter to the `Median` method for each case.</span></span>

```vb
Dim numbers3() As Integer = {1, 2, 3, 4, 5}

' You can use num as a parameter for the Median method
' so that the compiler will implicitly convert its value to double.
' If there is no implicit conversion, the compiler will
' display an error message.

Dim query3 = Aggregate num In numbers3 Into Median(num)

Console.WriteLine("Integer: Median = " & query3)

Dim numbers4() As String = {"one", "two", "three", "four", "five"}

' With the generic overload, you can also use numeric properties of objects.

Dim query4 = Aggregate str In numbers4 Into Median(str.Length)

Console.WriteLine("String: Median = " & query4)

' This code produces the following output:
'
' Integer: Median = 3
' String: Median = 4
```

## <a name="adding-a-method-that-returns-a-collection"></a><span data-ttu-id="a23e0-139">Bir koleksiyonu döndüren bir yöntem ekleme</span><span class="sxs-lookup"><span data-stu-id="a23e0-139">Adding a Method That Returns a Collection</span></span>

<span data-ttu-id="a23e0-140">Genişletebileceğiniz <xref:System.Collections.Generic.IEnumerable%601> değerlerini bir dizi döndürür bir özel sorgu yöntemi ile arabirim.</span><span class="sxs-lookup"><span data-stu-id="a23e0-140">You can extend the <xref:System.Collections.Generic.IEnumerable%601> interface with a custom query method that returns a sequence of values.</span></span> <span data-ttu-id="a23e0-141">Bu durumda, yöntem türü bir koleksiyon döndürmelidir <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="a23e0-141">In this case, the method must return a collection of type <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="a23e0-142">Bu tür yöntemler, değerler dizisi için filtre veya veri dönüşüm uygulamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a23e0-142">Such methods can be used to apply filters or data transforms to a sequence of values.</span></span>

<span data-ttu-id="a23e0-143">Aşağıdaki örnekte adlı bir genişletme yöntemi oluşturma işlemi gösterilmektedir `AlternateElements` ilk öğesinden başlayarak, bir koleksiyondaki her bir öğe döndürür.</span><span class="sxs-lookup"><span data-stu-id="a23e0-143">The following example shows how to create an extension method named `AlternateElements` that returns every other element in a collection, starting from the first element.</span></span>

```vb
' Extension method for the IEnumerable(of T) interface.
' The method returns every other element of a sequence.

<Extension()>
Function AlternateElements(Of T)(
    ByVal source As IEnumerable(Of T)
    ) As IEnumerable(Of T)

    Dim list As New List(Of T)
    Dim i = 0
    For Each element In source
        If (i Mod 2 = 0) Then
            list.Add(element)
        End If
        i = i + 1
    Next
    Return list
End Function
```

<span data-ttu-id="a23e0-144">Gibi diğer yöntemleri çağırmak bu genişletme yöntemi için herhangi bir sıralanabilir koleksiyonun çağırabilirsiniz <xref:System.Collections.Generic.IEnumerable%601> aşağıdaki kodda gösterildiği gibi arabirim:</span><span class="sxs-lookup"><span data-stu-id="a23e0-144">You can call this extension method for any enumerable collection just as you would call other methods from the <xref:System.Collections.Generic.IEnumerable%601> interface, as shown in the following code:</span></span>

```vb
Dim strings() As String = {"a", "b", "c", "d", "e"}

Dim query = strings.AlternateElements()

For Each element In query
    Console.WriteLine(element)
Next

' This code produces the following output:
'
' a
' c
' e
```

## <a name="see-also"></a><span data-ttu-id="a23e0-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a23e0-145">See also</span></span>

- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="a23e0-146">Genişletme Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="a23e0-146">Extension Methods</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
