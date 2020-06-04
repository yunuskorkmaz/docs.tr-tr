---
title: 'Nasıl yapılır: LINQ Sorguları için Özel Yöntemler'
ms.date: 07/20/2015
ms.assetid: 099b2e2a-83cd-45c6-aa4d-01b398b5faaf
ms.openlocfilehash: 55004441d2d1d74556da6841f28d113b876d1048
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400610"
---
# <a name="how-to-add-custom-methods-for-linq-queries-visual-basic"></a><span data-ttu-id="f6215-102">Nasıl yapılır: LINQ sorguları için özel yöntemler ekleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6215-102">How to: Add Custom Methods for LINQ Queries (Visual Basic)</span></span>

<span data-ttu-id="f6215-103">Arabirime uzantı yöntemleri ekleyerek, LINQ sorguları için kullanabileceğiniz yöntemlerin kümesini genişletebilirsiniz <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="f6215-103">You can extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="f6215-104">Örneğin, standart ortalama veya en yüksek işlemlere ek olarak, bir dizi değerden tek bir değeri hesaplamak için özel bir toplama yöntemi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f6215-104">For example, in addition to the standard average or maximum operations, you can create a custom aggregate method to compute a single value from a sequence of values.</span></span> <span data-ttu-id="f6215-105">Ayrıca, bir dizi değer için özel bir filtre veya belirli bir veri dönüştürmesi olarak çalışacak bir yöntem oluşturabilirsiniz ve yeni bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="f6215-105">You can also create a method that works as a custom filter or a specific data transform for a sequence of values and returns a new sequence.</span></span> <span data-ttu-id="f6215-106">Bu tür yöntemlere örnekler, <xref:System.Linq.Enumerable.Distinct%2A> <xref:System.Linq.Enumerable.Skip%2A> ve ' dir <xref:System.Linq.Enumerable.Reverse%2A> .</span><span class="sxs-lookup"><span data-stu-id="f6215-106">Examples of such methods are <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, and <xref:System.Linq.Enumerable.Reverse%2A>.</span></span>

<span data-ttu-id="f6215-107"><xref:System.Collections.Generic.IEnumerable%601>Arabirimi genişlettiğinizde, özel yöntemlerinizi herhangi bir sıralanabilir koleksiyona uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f6215-107">When you extend the <xref:System.Collections.Generic.IEnumerable%601> interface, you can apply your custom methods to any enumerable collection.</span></span> <span data-ttu-id="f6215-108">Daha fazla bilgi için bkz. [Uzantı yöntemleri](../../language-features/procedures/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="f6215-108">For more information, see [Extension Methods](../../language-features/procedures/extension-methods.md).</span></span>

## <a name="adding-an-aggregate-method"></a><span data-ttu-id="f6215-109">Toplama yöntemi ekleme</span><span class="sxs-lookup"><span data-stu-id="f6215-109">Adding an Aggregate Method</span></span>

<span data-ttu-id="f6215-110">Toplama yöntemi bir değer kümesinden tek bir değeri hesaplar.</span><span class="sxs-lookup"><span data-stu-id="f6215-110">An aggregate method computes a single value from a set of values.</span></span> <span data-ttu-id="f6215-111">LINQ, ve dahil olmak üzere birkaç toplama yöntemi sağlar <xref:System.Linq.Enumerable.Average%2A> <xref:System.Linq.Enumerable.Min%2A> <xref:System.Linq.Enumerable.Max%2A> .</span><span class="sxs-lookup"><span data-stu-id="f6215-111">LINQ provides several aggregate methods, including <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Max%2A>.</span></span> <span data-ttu-id="f6215-112">Arayüze bir genişletme yöntemi ekleyerek kendi toplama yönteminizi oluşturabilirsiniz <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="f6215-112">You can create your own aggregate method by adding an extension method to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>

<span data-ttu-id="f6215-113">Aşağıdaki kod örneği, `Median` bir tür sayı dizisi için ortanca hesaplamak üzere çağrılan bir genişletme yönteminin nasıl oluşturulacağını göstermektedir `double` .</span><span class="sxs-lookup"><span data-stu-id="f6215-113">The following code example shows how to create an extension method called `Median` to compute a median for a sequence of numbers of type `double`.</span></span>

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

<span data-ttu-id="f6215-114">Bu genişletme yöntemini, herhangi bir sıralanabilir koleksiyon için, arabirimden diğer toplama yöntemlerini çağırdığınız şekilde çağırabilirsiniz <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="f6215-114">You call this extension method for any enumerable collection in the same way you call other aggregate methods from the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>

> [!NOTE]
> <span data-ttu-id="f6215-115">Visual Basic, `Aggregate` veya yan tümcesi için bir yöntem çağrısı veya standart sorgu söz dizimini kullanabilirsiniz `Group By` .</span><span class="sxs-lookup"><span data-stu-id="f6215-115">In Visual Basic, you can either use a method call or standard query syntax for the `Aggregate` or `Group By` clause.</span></span> <span data-ttu-id="f6215-116">Daha fazla bilgi için bkz. [toplama yan tümcesi](../../../language-reference/queries/aggregate-clause.md) ve [Group by yan tümcesi](../../../language-reference/queries/group-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="f6215-116">For more information, see [Aggregate Clause](../../../language-reference/queries/aggregate-clause.md) and [Group By Clause](../../../language-reference/queries/group-by-clause.md).</span></span>

<span data-ttu-id="f6215-117">Aşağıdaki kod örneği, `Median` bir dizi türü için yönteminin nasıl kullanılacağını gösterir `double` .</span><span class="sxs-lookup"><span data-stu-id="f6215-117">The following code example shows how to use the `Median` method for an array of type `double`.</span></span>

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

### <a name="overloading-an-aggregate-method-to-accept-various-types"></a><span data-ttu-id="f6215-118">Çeşitli türleri kabul etmek için bir toplama yöntemini aşırı yükleme</span><span class="sxs-lookup"><span data-stu-id="f6215-118">Overloading an Aggregate Method to Accept Various Types</span></span>

<span data-ttu-id="f6215-119">Toplama yönteminizi çeşitli türlerde dizileri kabul edecek şekilde aşırı yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f6215-119">You can overload your aggregate method so that it accepts sequences of various types.</span></span> <span data-ttu-id="f6215-120">Standart yaklaşım, her tür için bir aşırı yükleme oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="f6215-120">The standard approach is to create an overload for each type.</span></span> <span data-ttu-id="f6215-121">Başka bir yaklaşım ise genel bir tür alacak ve bir temsilciyi kullanarak belirli bir türe dönüştürecek bir aşırı yükleme oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="f6215-121">Another approach is to create an overload that will take a generic type and convert it to a specific type by using a delegate.</span></span> <span data-ttu-id="f6215-122">Her iki yaklaşımı de birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f6215-122">You can also combine both approaches.</span></span>

#### <a name="to-create-an-overload-for-each-type"></a><span data-ttu-id="f6215-123">Her tür için bir aşırı yükleme oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="f6215-123">To create an overload for each type</span></span>

<span data-ttu-id="f6215-124">Desteklemek istediğiniz her tür için belirli bir aşırı yükleme oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f6215-124">You can create a specific overload for each type that you want to support.</span></span> <span data-ttu-id="f6215-125">Aşağıdaki kod örneği, türü için yönteminin bir aşırı yüklemesini gösterir `Median` `integer` .</span><span class="sxs-lookup"><span data-stu-id="f6215-125">The following code example shows an overload of the `Median` method for the `integer` type.</span></span>

```vb
' Integer overload

<Extension()>
Function Median(ByVal source As IEnumerable(Of Integer)) As Double
    Return Aggregate num In source Select CDbl(num) Into med = Median()
End Function
```

<span data-ttu-id="f6215-126">Artık `Median` `integer` `double` , aşağıdaki kodda gösterildiği gibi, hem hem de türleri için aşırı yüklemeleri çağırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f6215-126">You can now call the `Median` overloads for both `integer` and `double` types, as shown in the following code:</span></span>

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

#### <a name="to-create-a-generic-overload"></a><span data-ttu-id="f6215-127">Genel aşırı yükleme oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="f6215-127">To create a generic overload</span></span>

<span data-ttu-id="f6215-128">Ayrıca, genel nesne dizisini kabul eden bir aşırı yükleme de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f6215-128">You can also create an overload that accepts a sequence of generic objects.</span></span> <span data-ttu-id="f6215-129">Bu aşırı yükleme bir temsilciyi parametre olarak alır ve bir genel türdeki nesne dizisini belirli bir türe dönüştürmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="f6215-129">This overload takes a delegate as a parameter and uses it to convert a sequence of objects of a generic type to a specific type.</span></span>

<span data-ttu-id="f6215-130">Aşağıdaki kod, `Median` <xref:System.Func%602> bir parametresi olarak temsilciyi alan yönteminin bir aşırı yüklemesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f6215-130">The following code shows an overload of the `Median` method that takes the <xref:System.Func%602> delegate as a parameter.</span></span> <span data-ttu-id="f6215-131">Bu temsilci, T genel türünde bir nesne alır ve türünde bir nesne döndürür `double` .</span><span class="sxs-lookup"><span data-stu-id="f6215-131">This delegate takes an object of generic type T and returns an object of type `double`.</span></span>

```vb
' Generic overload.

<Extension()>
Function Median(Of T)(ByVal source As IEnumerable(Of T),
                      ByVal selector As Func(Of T, Double)) As Double
    Return Aggregate num In source Select selector(num) Into med = Median()
End Function
```

<span data-ttu-id="f6215-132">Artık `Median` herhangi bir türdeki nesne dizisi için yöntemini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f6215-132">You can now call the `Median` method for a sequence of objects of any type.</span></span> <span data-ttu-id="f6215-133">Türün kendi yöntem aşırı yüklemesi yoksa, bir temsilci parametresi geçirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f6215-133">If the type does not have its own method overload, you have to pass a delegate parameter.</span></span> <span data-ttu-id="f6215-134">Visual Basic, bu amaçla bir lambda ifadesi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f6215-134">In Visual Basic, you can use a lambda expression for this purpose.</span></span> <span data-ttu-id="f6215-135">Ayrıca, `Aggregate` `Group By` Yöntem çağrısı yerine OR yan tümcesini kullanırsanız, bu yan tümce kapsamındaki herhangi bir değer veya ifade geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f6215-135">Also, if you use the `Aggregate` or `Group By` clause instead of the method call, you can pass any value or expression that is in the scope this clause.</span></span>

<span data-ttu-id="f6215-136">Aşağıdaki örnek kod, `Median` bir tamsayılar dizisi ve dizeler dizisi için yönteminin nasıl çağrılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f6215-136">The following example code shows how to call the `Median` method for an array of integers and an array of strings.</span></span> <span data-ttu-id="f6215-137">Dizeler için, dizideki dizelerin uzunluklarının ortancası hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="f6215-137">For strings, the median for the lengths of strings in the array is calculated.</span></span> <span data-ttu-id="f6215-138">Örnek, <xref:System.Func%602> her durumda temsilci parametresinin yönteme nasıl geçirileceğini gösterir `Median` .</span><span class="sxs-lookup"><span data-stu-id="f6215-138">The example shows how to pass the <xref:System.Func%602> delegate parameter to the `Median` method for each case.</span></span>

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

## <a name="adding-a-method-that-returns-a-collection"></a><span data-ttu-id="f6215-139">Koleksiyon döndüren bir yöntem ekleme</span><span class="sxs-lookup"><span data-stu-id="f6215-139">Adding a Method That Returns a Collection</span></span>

<span data-ttu-id="f6215-140"><xref:System.Collections.Generic.IEnumerable%601>Arabirimi bir değer dizisi döndüren özel bir sorgu yöntemiyle genişletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f6215-140">You can extend the <xref:System.Collections.Generic.IEnumerable%601> interface with a custom query method that returns a sequence of values.</span></span> <span data-ttu-id="f6215-141">Bu durumda, yöntemin türünde bir koleksiyon döndürmesi gerekir <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="f6215-141">In this case, the method must return a collection of type <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="f6215-142">Bu tür yöntemler, bir değerler dizisine filtre veya veri dönüştürmeleri uygulamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f6215-142">Such methods can be used to apply filters or data transforms to a sequence of values.</span></span>

<span data-ttu-id="f6215-143">Aşağıdaki örnek, `AlternateElements` ilk öğeden başlayarak bir koleksiyondaki her öğeyi döndüren adlı bir genişletme yönteminin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f6215-143">The following example shows how to create an extension method named `AlternateElements` that returns every other element in a collection, starting from the first element.</span></span>

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

<span data-ttu-id="f6215-144">Aşağıdaki kodda gösterildiği gibi, herhangi bir sayılabilir koleksiyon için bu genişletme yöntemini, arabirimden diğer yöntemleri çağırdığınız gibi çağırabilirsiniz <xref:System.Collections.Generic.IEnumerable%601> :</span><span class="sxs-lookup"><span data-stu-id="f6215-144">You can call this extension method for any enumerable collection just as you would call other methods from the <xref:System.Collections.Generic.IEnumerable%601> interface, as shown in the following code:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f6215-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f6215-145">See also</span></span>

- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="f6215-146">Uzantı yöntemleri</span><span class="sxs-lookup"><span data-stu-id="f6215-146">Extension Methods</span></span>](../../language-features/procedures/extension-methods.md)
