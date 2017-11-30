---
title: "Nasıl yapılır: özel yöntemler ekleme LINQ sorgularını (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 099b2e2a-83cd-45c6-aa4d-01b398b5faaf
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c94973bf9eae0feb2f7690dcc10e839b6b7c060c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-custom-methods-for-linq-queries-visual-basic"></a><span data-ttu-id="3ce50-102">Nasıl yapılır: özel yöntemler ekleme LINQ sorgularını (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3ce50-102">How to: Add Custom Methods for LINQ Queries (Visual Basic)</span></span>
<span data-ttu-id="3ce50-103">İçin genişletme yöntemleri ekleyerek LINQ sorguları için kullanabileceğiniz yöntemler kümesi genişletebilirsiniz <xref:System.Collections.Generic.IEnumerable%601> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="3ce50-103">You can extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="3ce50-104">Örneğin, standart ortalama veya en fazla işlemlerinin yanı sıra, değerlerin bir sırasından tek bir değeri hesaplamak için özel bir toplama yöntemi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3ce50-104">For example, in addition to the standard average or maximum operations, you can create a custom aggregate method to compute a single value from a sequence of values.</span></span> <span data-ttu-id="3ce50-105">Özel filtre veya değerleri dizisi için belirli veri dönüştürme olarak çalışır ve yeni sırası döndüren bir yöntem de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3ce50-105">You can also create a method that works as a custom filter or a specific data transform for a sequence of values and returns a new sequence.</span></span> <span data-ttu-id="3ce50-106">Bu tür yöntemler örnekleridir <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, ve <xref:System.Linq.Enumerable.Reverse%2A>.</span><span class="sxs-lookup"><span data-stu-id="3ce50-106">Examples of such methods are <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, and <xref:System.Linq.Enumerable.Reverse%2A>.</span></span>  
  
 <span data-ttu-id="3ce50-107">Genişlettiğinizde <xref:System.Collections.Generic.IEnumerable%601> arabirimi, özel yöntemlerinizi herhangi numaralandırılabilir koleksiyonuna uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3ce50-107">When you extend the <xref:System.Collections.Generic.IEnumerable%601> interface, you can apply your custom methods to any enumerable collection.</span></span> <span data-ttu-id="3ce50-108">Daha fazla bilgi için bkz: [genişletme yöntemleri](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="3ce50-108">For more information, see [Extension Methods](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md).</span></span>  
  
## <a name="adding-an-aggregate-method"></a><span data-ttu-id="3ce50-109">Toplama yöntemi ekleme</span><span class="sxs-lookup"><span data-stu-id="3ce50-109">Adding an Aggregate Method</span></span>  
 <span data-ttu-id="3ce50-110">Birleşik bir yöntemi, bir değerler kümesinden tek bir değer hesaplar.</span><span class="sxs-lookup"><span data-stu-id="3ce50-110">An aggregate method computes a single value from a set of values.</span></span> <span data-ttu-id="3ce50-111">LINQ sağlar dahil olmak üzere birkaç toplama yöntemleri <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, ve <xref:System.Linq.Enumerable.Max%2A>.</span><span class="sxs-lookup"><span data-stu-id="3ce50-111">LINQ provides several aggregate methods, including <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Max%2A>.</span></span> <span data-ttu-id="3ce50-112">Bir genişletme yöntemi ekleyerek toplama yönteminizi oluşturabilirsiniz <xref:System.Collections.Generic.IEnumerable%601> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="3ce50-112">You can create your own aggregate method by adding an extension method to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
 <span data-ttu-id="3ce50-113">Aşağıdaki kod örneği olarak adlandırılan bir genişletme yöntemi oluşturulacağını gösterir `Median` ORTANCA bir dizi sayı türü için işlem için `double`.</span><span class="sxs-lookup"><span data-stu-id="3ce50-113">The following code example shows how to create an extension method called `Median` to compute a median for a sequence of numbers of type `double`.</span></span>  
  
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
  
 <span data-ttu-id="3ce50-114">Toplam diğer yöntemleri çağırmak aynı şekilde numaralandırılabilir herhangi bir koleksiyon için bu uzantı metodu çağırma <xref:System.Collections.Generic.IEnumerable%601> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="3ce50-114">You call this extension method for any enumerable collection in the same way you call other aggregate methods from the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3ce50-115">Visual Basic'te ya da bir yöntem çağrısı veya standart sorgu sözdizimi için kullanabileceğiniz `Aggregate` veya `Group By` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="3ce50-115">In Visual Basic, you can either use a method call or standard query syntax for the `Aggregate` or `Group By` clause.</span></span> <span data-ttu-id="3ce50-116">Daha fazla bilgi için bkz: [Aggregate tümcesi](../../../../visual-basic/language-reference/queries/aggregate-clause.md) ve [Grup By yan tümcesi](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="3ce50-116">For more information, see [Aggregate Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md) and [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
 <span data-ttu-id="3ce50-117">Aşağıdaki kod örneğinde nasıl kullanılacağını gösterir `Median` türünde bir dizi yöntem `double`.</span><span class="sxs-lookup"><span data-stu-id="3ce50-117">The following code example shows how to use the `Median` method for an array of type `double`.</span></span>  
  
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
  

### <a name="overloading-an-aggregate-method-to-accept-various-types"></a><span data-ttu-id="3ce50-118">Çeşitli türlerini kabul edecek şekilde bir toplama yöntemi aşırı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="3ce50-118">Overloading an Aggregate Method to Accept Various Types</span></span>  
 <span data-ttu-id="3ce50-119">Toplama yöntemi aşırı yükleme çeşitli türlerdeki dizilerini kabul.</span><span class="sxs-lookup"><span data-stu-id="3ce50-119">You can overload your aggregate method so that it accepts sequences of various types.</span></span> <span data-ttu-id="3ce50-120">Standart yaklaşımı, her tür için bir aşırı oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="3ce50-120">The standard approach is to create an overload for each type.</span></span> <span data-ttu-id="3ce50-121">Başka bir yaklaşım, genel bir tür olması ve bir temsilci kullanarak belirli bir türe dönüştürmek aşırı oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="3ce50-121">Another approach is to create an overload that will take a generic type and convert it to a specific type by using a delegate.</span></span> <span data-ttu-id="3ce50-122">Ayrıca, her iki yaklaşımın da birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3ce50-122">You can also combine both approaches.</span></span>  
  
#### <a name="to-create-an-overload-for-each-type"></a><span data-ttu-id="3ce50-123">Her tür için bir aşırı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="3ce50-123">To create an overload for each type</span></span>  
 <span data-ttu-id="3ce50-124">Desteklemek istediğiniz her bir türü için belirli bir aşırı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3ce50-124">You can create a specific overload for each type that you want to support.</span></span> <span data-ttu-id="3ce50-125">Aşağıdaki kod örneğinde bir aşırı yüklemesini gösterir `Median` yöntemi `integer` türü.</span><span class="sxs-lookup"><span data-stu-id="3ce50-125">The following code example shows an overload of the `Median` method for the `integer` type.</span></span>  
  
```vb  
' Integer overload  
  
<Extension()>   
Function Median(ByVal source As IEnumerable(Of Integer)) As Double  
    Return Aggregate num In source Select CDbl(num) Into med = Median()  
End Function  
```  
 <span data-ttu-id="3ce50-126">Şimdi Ara `Median` her ikisi için de aşırı `integer` ve `double` aşağıdaki kodda gösterildiği gibi türleri:</span><span class="sxs-lookup"><span data-stu-id="3ce50-126">You can now call the `Median` overloads for both `integer` and `double` types, as shown in the following code:</span></span>  
  
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
  
 
#### <a name="to-create-a-generic-overload"></a><span data-ttu-id="3ce50-127">Bir genel aşırı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="3ce50-127">To create a generic overload</span></span>  
 <span data-ttu-id="3ce50-128">Genel nesneler dizisi kabul eden bir aşırı de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3ce50-128">You can also create an overload that accepts a sequence of generic objects.</span></span> <span data-ttu-id="3ce50-129">Bu aşırı temsilci bir parametre olarak alır ve belirli bir türe genel bir tür nesnelerin bir dizi dönüştürmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="3ce50-129">This overload takes a delegate as a parameter and uses it to convert a sequence of objects of a generic type to a specific type.</span></span>  
  
 <span data-ttu-id="3ce50-130">Aşağıdaki kod bir aşırı yüklemesini gösterir `Median` yönteminin alan <xref:System.Func%602> temsilci parametre olarak.</span><span class="sxs-lookup"><span data-stu-id="3ce50-130">The following code shows an overload of the `Median` method that takes the <xref:System.Func%602> delegate as a parameter.</span></span> <span data-ttu-id="3ce50-131">Bu temsilci T genel türünde bir nesne alır ve türünde bir nesne döndürür `double`.</span><span class="sxs-lookup"><span data-stu-id="3ce50-131">This delegate takes an object of generic type T and returns an object of type `double`.</span></span>  
  
```vb  
' Generic overload.  
  
<Extension()>   
Function Median(Of T)(ByVal source As IEnumerable(Of T),   
                      ByVal selector As Func(Of T, Double)) As Double  
    Return Aggregate num In source Select selector(num) Into med = Median()  
End Function  
```  
  
 <span data-ttu-id="3ce50-132">Şimdi Ara `Median` herhangi bir türde nesnelerinin bir dizisi için yöntem.</span><span class="sxs-lookup"><span data-stu-id="3ce50-132">You can now call the `Median` method for a sequence of objects of any type.</span></span> <span data-ttu-id="3ce50-133">Türü kendi yöntemi aşırı yüklemesini yoksa bir temsilci parametre geçirmek zorunda.</span><span class="sxs-lookup"><span data-stu-id="3ce50-133">If the type does not have its own method overload, you have to pass a delegate parameter.</span></span> <span data-ttu-id="3ce50-134">Visual Basic'te, bu amaçla bir lambda ifadesi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3ce50-134">In Visual Basic, you can use a lambda expression for this purpose.</span></span> <span data-ttu-id="3ce50-135">Ayrıca, kullanırsanız `Aggregate` veya `Group By` yöntem çağrısının yerine yan tümcesi, herhangi bir değer veya bu yan tümce kapsamı içinde olan deyimi iletebilir.</span><span class="sxs-lookup"><span data-stu-id="3ce50-135">Also, if you use the `Aggregate` or `Group By` clause instead of the method call, you can pass any value or expression that is in the scope this clause.</span></span>  
  
 <span data-ttu-id="3ce50-136">Aşağıdaki kod örneği nasıl çağrılacağını gösterir `Median` yöntemi dizisi ve bir dizeler dizisi.</span><span class="sxs-lookup"><span data-stu-id="3ce50-136">The following example code shows how to call the `Median` method for an array of integers and an array of strings.</span></span> <span data-ttu-id="3ce50-137">Dizeler için dizi dizelerde uzunlukları ORTANCA hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="3ce50-137">For strings, the median for the lengths of strings in the array is calculated.</span></span> <span data-ttu-id="3ce50-138">Örnek nasıl iletileceğini gösterir <xref:System.Func%602> temsilci parametresi `Median` yöntemi her örneği için.</span><span class="sxs-lookup"><span data-stu-id="3ce50-138">The example shows how to pass the <xref:System.Func%602> delegate parameter to the `Median` method for each case.</span></span>  
  
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
## <a name="adding-a-method-that-returns-a-collection"></a><span data-ttu-id="3ce50-139">Bir koleksiyonu döndüren bir yöntem ekleme</span><span class="sxs-lookup"><span data-stu-id="3ce50-139">Adding a Method That Returns a Collection</span></span>  
 <span data-ttu-id="3ce50-140">Genişletebilirsiniz <xref:System.Collections.Generic.IEnumerable%601> arabirimi bir özel sorgu yöntemiyle değerleri dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="3ce50-140">You can extend the <xref:System.Collections.Generic.IEnumerable%601> interface with a custom query method that returns a sequence of values.</span></span> <span data-ttu-id="3ce50-141">Bu durumda, yöntem bir koleksiyon türü döndürmelidir <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="3ce50-141">In this case, the method must return a collection of type <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="3ce50-142">Bu tür yöntemleri değerleri dizisi için filtre ya da veri dönüşüm uygulamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3ce50-142">Such methods can be used to apply filters or data transforms to a sequence of values.</span></span>  
  
 <span data-ttu-id="3ce50-143">Aşağıdaki örnek adlı bir genişletme yöntemi oluşturulacağını gösterir `AlternateElements` ilk öğesinden başlayarak, bir koleksiyondaki her bir öğe getirir.</span><span class="sxs-lookup"><span data-stu-id="3ce50-143">The following example shows how to create an extension method named `AlternateElements` that returns every other element in a collection, starting from the first element.</span></span>  
  
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
 <span data-ttu-id="3ce50-144">Diğer yöntemleri çağırmak gibi herhangi bir numaralandırılabilir koleksiyonu için bu genişletme yöntemi çağırabilir <xref:System.Collections.Generic.IEnumerable%601> aşağıdaki kodda gösterildiği gibi arabirim:</span><span class="sxs-lookup"><span data-stu-id="3ce50-144">You can call this extension method for any enumerable collection just as you would call other methods from the <xref:System.Collections.Generic.IEnumerable%601> interface, as shown in the following code:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3ce50-145">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3ce50-145">See Also</span></span>  
 <xref:System.Collections.Generic.IEnumerable%601>  
 [<span data-ttu-id="3ce50-146">Genişletme yöntemleri</span><span class="sxs-lookup"><span data-stu-id="3ce50-146">Extension Methods</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
