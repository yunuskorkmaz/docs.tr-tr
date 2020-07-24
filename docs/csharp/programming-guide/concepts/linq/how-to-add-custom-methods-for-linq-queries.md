---
title: LINQ sorguları için özel yöntemler ekleme (C#)
description: C# ' de IEnumerable arabirimine uzantı yöntemleri ekleyerek, LINQ sorguları için kullanabileceğiniz yöntemlerin kümesini genişletmeyi öğrenin <T> .
ms.date: 07/20/2015
ms.assetid: 1a500f60-2e10-49fb-8b2a-d8d08e4817cb
ms.openlocfilehash: fac0eb4e14eb3bb36313232a7d7fa3060c0ac171
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103604"
---
# <a name="how-to-add-custom-methods-for-linq-queries-c"></a><span data-ttu-id="245f7-103">LINQ sorguları için özel yöntemler ekleme (C#)</span><span class="sxs-lookup"><span data-stu-id="245f7-103">How to add custom methods for LINQ queries (C#)</span></span>

<span data-ttu-id="245f7-104">Arabirime uzantı yöntemleri ekleyerek, LINQ sorguları için kullanabileceğiniz yöntemlerin kümesini genişletebilirsiniz <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="245f7-104">You can extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="245f7-105">Örneğin, standart ortalama veya en yüksek işlemlere ek olarak, bir dizi değerden tek bir değeri hesaplamak için özel bir toplama yöntemi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="245f7-105">For example, in addition to the standard average or maximum operations, you can create a custom aggregate method to compute a single value from a sequence of values.</span></span> <span data-ttu-id="245f7-106">Ayrıca, bir dizi değer için özel bir filtre veya belirli bir veri dönüştürmesi olarak çalışacak bir yöntem oluşturabilirsiniz ve yeni bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="245f7-106">You can also create a method that works as a custom filter or a specific data transform for a sequence of values and returns a new sequence.</span></span> <span data-ttu-id="245f7-107">Bu tür yöntemlere örnekler, <xref:System.Linq.Enumerable.Distinct%2A> <xref:System.Linq.Enumerable.Skip%2A> ve ' dir <xref:System.Linq.Enumerable.Reverse%2A> .</span><span class="sxs-lookup"><span data-stu-id="245f7-107">Examples of such methods are <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, and <xref:System.Linq.Enumerable.Reverse%2A>.</span></span>

<span data-ttu-id="245f7-108"><xref:System.Collections.Generic.IEnumerable%601>Arabirimi genişlettiğinizde, özel yöntemlerinizi herhangi bir sıralanabilir koleksiyona uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="245f7-108">When you extend the <xref:System.Collections.Generic.IEnumerable%601> interface, you can apply your custom methods to any enumerable collection.</span></span> <span data-ttu-id="245f7-109">Daha fazla bilgi için bkz. [Uzantı yöntemleri](../../classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="245f7-109">For more information, see [Extension Methods](../../classes-and-structs/extension-methods.md).</span></span>

## <a name="adding-an-aggregate-method"></a><span data-ttu-id="245f7-110">Toplama yöntemi ekleme</span><span class="sxs-lookup"><span data-stu-id="245f7-110">Adding an Aggregate Method</span></span>

<span data-ttu-id="245f7-111">Toplama yöntemi bir değer kümesinden tek bir değeri hesaplar.</span><span class="sxs-lookup"><span data-stu-id="245f7-111">An aggregate method computes a single value from a set of values.</span></span> <span data-ttu-id="245f7-112">LINQ, ve dahil olmak üzere birkaç toplama yöntemi sağlar <xref:System.Linq.Enumerable.Average%2A> <xref:System.Linq.Enumerable.Min%2A> <xref:System.Linq.Enumerable.Max%2A> .</span><span class="sxs-lookup"><span data-stu-id="245f7-112">LINQ provides several aggregate methods, including <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Max%2A>.</span></span> <span data-ttu-id="245f7-113">Arayüze bir genişletme yöntemi ekleyerek kendi toplama yönteminizi oluşturabilirsiniz <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="245f7-113">You can create your own aggregate method by adding an extension method to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>

<span data-ttu-id="245f7-114">Aşağıdaki kod örneği, `Median` bir tür sayı dizisi için ortanca hesaplamak üzere çağrılan bir genişletme yönteminin nasıl oluşturulacağını göstermektedir `double` .</span><span class="sxs-lookup"><span data-stu-id="245f7-114">The following code example shows how to create an extension method called `Median` to compute a median for a sequence of numbers of type `double`.</span></span>

```csharp
public static class LINQExtension
{
    public static double Median(this IEnumerable<double> source)
    {
        var countOfElementsInTheSet = source?.Count() ?? 0;

        if (countOfElementsInTheSet == 0)
        {
            throw new InvalidOperationException("Cannot compute median for a null or empty set.");
        }

        var sortedList = (from number in source
                         orderby number
                         select number).ToList();

        int itemIndex = countOfElementsInTheSet / 2;

        if (countOfElementsInTheSet % 2 == 0)
        {
            // Even number of items.
            return (sortedList[itemIndex] + sortedList[itemIndex - 1]) / 2;
        }
        else
        {
            // Odd number of items.
            return sortedList[itemIndex];
        }
    }
}
```

<span data-ttu-id="245f7-115">Bu genişletme yöntemini, herhangi bir sıralanabilir koleksiyon için, arabirimden diğer toplama yöntemlerini çağırdığınız şekilde çağırabilirsiniz <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="245f7-115">You call this extension method for any enumerable collection in the same way you call other aggregate methods from the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>

<span data-ttu-id="245f7-116">Aşağıdaki kod örneği, `Median` bir dizi türü için yönteminin nasıl kullanılacağını gösterir `double` .</span><span class="sxs-lookup"><span data-stu-id="245f7-116">The following code example shows how to use the `Median` method for an array of type `double`.</span></span>

```csharp
double[] numbers1 = { 1.9, 2, 8, 4, 5.7, 6, 7.2, 0 };

var query1 = numbers1.Median();

Console.WriteLine("double: Median = " + query1);
```

```csharp
/*
 This code produces the following output:

 Double: Median = 4.85
*/
```

### <a name="overloading-an-aggregate-method-to-accept-various-types"></a><span data-ttu-id="245f7-117">Çeşitli türleri kabul etmek için bir toplama yöntemini aşırı yükleme</span><span class="sxs-lookup"><span data-stu-id="245f7-117">Overloading an Aggregate Method to Accept Various Types</span></span>

<span data-ttu-id="245f7-118">Toplama yönteminizi çeşitli türlerde dizileri kabul edecek şekilde aşırı yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="245f7-118">You can overload your aggregate method so that it accepts sequences of various types.</span></span> <span data-ttu-id="245f7-119">Standart yaklaşım, her tür için bir aşırı yükleme oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="245f7-119">The standard approach is to create an overload for each type.</span></span> <span data-ttu-id="245f7-120">Başka bir yaklaşım ise genel bir tür alacak ve bir temsilciyi kullanarak belirli bir türe dönüştürecek bir aşırı yükleme oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="245f7-120">Another approach is to create an overload that will take a generic type and convert it to a specific type by using a delegate.</span></span> <span data-ttu-id="245f7-121">Her iki yaklaşımı de birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="245f7-121">You can also combine both approaches.</span></span>

#### <a name="to-create-an-overload-for-each-type"></a><span data-ttu-id="245f7-122">Her tür için bir aşırı yükleme oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="245f7-122">To create an overload for each type</span></span>

<span data-ttu-id="245f7-123">Desteklemek istediğiniz her tür için belirli bir aşırı yükleme oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="245f7-123">You can create a specific overload for each type that you want to support.</span></span> <span data-ttu-id="245f7-124">Aşağıdaki kod örneği, türü için yönteminin bir aşırı yüklemesini gösterir `Median` `integer` .</span><span class="sxs-lookup"><span data-stu-id="245f7-124">The following code example shows an overload of the `Median` method for the `integer` type.</span></span>

```csharp
//int overload

public static double Median(this IEnumerable<int> source)
{
    return (from num in source select (double)num).Median();
}
```

<span data-ttu-id="245f7-125">Artık `Median` `integer` `double` , aşağıdaki kodda gösterildiği gibi, hem hem de türleri için aşırı yüklemeleri çağırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="245f7-125">You can now call the `Median` overloads for both `integer` and `double` types, as shown in the following code:</span></span>

```csharp
double[] numbers1 = { 1.9, 2, 8, 4, 5.7, 6, 7.2, 0 };

var query1 = numbers1.Median();

Console.WriteLine("double: Median = " + query1);
```

```csharp
int[] numbers2 = { 1, 2, 3, 4, 5 };

var query2 = numbers2.Median();

Console.WriteLine("int: Median = " + query2);
```

```csharp
/*
 This code produces the following output:

 Double: Median = 4.85
 Integer: Median = 3
*/
```

#### <a name="to-create-a-generic-overload"></a><span data-ttu-id="245f7-126">Genel aşırı yükleme oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="245f7-126">To create a generic overload</span></span>

<span data-ttu-id="245f7-127">Ayrıca, genel nesne dizisini kabul eden bir aşırı yükleme de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="245f7-127">You can also create an overload that accepts a sequence of generic objects.</span></span> <span data-ttu-id="245f7-128">Bu aşırı yükleme bir temsilciyi parametre olarak alır ve bir genel türdeki nesne dizisini belirli bir türe dönüştürmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="245f7-128">This overload takes a delegate as a parameter and uses it to convert a sequence of objects of a generic type to a specific type.</span></span>

<span data-ttu-id="245f7-129">Aşağıdaki kod, `Median` <xref:System.Func%602> bir parametresi olarak temsilciyi alan yönteminin bir aşırı yüklemesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="245f7-129">The following code shows an overload of the `Median` method that takes the <xref:System.Func%602> delegate as a parameter.</span></span> <span data-ttu-id="245f7-130">Bu temsilci, T genel türünde bir nesne alır ve türünde bir nesne döndürür `double` .</span><span class="sxs-lookup"><span data-stu-id="245f7-130">This delegate takes an object of generic type T and returns an object of type `double`.</span></span>

```csharp
// Generic overload.

public static double Median<T>(this IEnumerable<T> numbers,
                       Func<T, double> selector)
{
    return (from num in numbers select selector(num)).Median();
}
```

<span data-ttu-id="245f7-131">Artık `Median` herhangi bir türdeki nesne dizisi için yöntemini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="245f7-131">You can now call the `Median` method for a sequence of objects of any type.</span></span> <span data-ttu-id="245f7-132">Türün kendi yöntem aşırı yüklemesi yoksa, bir temsilci parametresi geçirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="245f7-132">If the type does not have its own method overload, you have to pass a delegate parameter.</span></span> <span data-ttu-id="245f7-133">C# dilinde, bu amaçla bir lambda ifadesi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="245f7-133">In C#, you can use a lambda expression for this purpose.</span></span> <span data-ttu-id="245f7-134">Ayrıca, yalnızca Visual Basic ' de, `Aggregate` `Group By` Yöntem çağrısı yerine OR yan tümcesini kullanırsanız, bu yan tümce kapsamındaki herhangi bir değer veya ifade geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="245f7-134">Also, in Visual Basic only, if you use the `Aggregate` or `Group By` clause instead of the method call, you can pass any value or expression that is in the scope this clause.</span></span>

<span data-ttu-id="245f7-135">Aşağıdaki örnek kod, `Median` bir tamsayılar dizisi ve dizeler dizisi için yönteminin nasıl çağrılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="245f7-135">The following example code shows how to call the `Median` method for an array of integers and an array of strings.</span></span> <span data-ttu-id="245f7-136">Dizeler için, dizideki dizelerin uzunluklarının ortancası hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="245f7-136">For strings, the median for the lengths of strings in the array is calculated.</span></span> <span data-ttu-id="245f7-137">Örnek, <xref:System.Func%602> her durumda temsilci parametresinin yönteme nasıl geçirileceğini gösterir `Median` .</span><span class="sxs-lookup"><span data-stu-id="245f7-137">The example shows how to pass the <xref:System.Func%602> delegate parameter to the `Median` method for each case.</span></span>

```csharp
int[] numbers3 = { 1, 2, 3, 4, 5 };

/*
  You can use the num=>num lambda expression as a parameter for the Median method
  so that the compiler will implicitly convert its value to double.
  If there is no implicit conversion, the compiler will display an error message.
*/

var query3 = numbers3.Median(num => num);

Console.WriteLine("int: Median = " + query3);

string[] numbers4 = { "one", "two", "three", "four", "five" };

// With the generic overload, you can also use numeric properties of objects.

var query4 = numbers4.Median(str => str.Length);

Console.WriteLine("String: Median = " + query4);

/*
 This code produces the following output:

 Integer: Median = 3
 String: Median = 4
*/
```

## <a name="adding-a-method-that-returns-a-collection"></a><span data-ttu-id="245f7-138">Koleksiyon döndüren bir yöntem ekleme</span><span class="sxs-lookup"><span data-stu-id="245f7-138">Adding a Method That Returns a Collection</span></span>

<span data-ttu-id="245f7-139"><xref:System.Collections.Generic.IEnumerable%601>Arabirimi bir değer dizisi döndüren özel bir sorgu yöntemiyle genişletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="245f7-139">You can extend the <xref:System.Collections.Generic.IEnumerable%601> interface with a custom query method that returns a sequence of values.</span></span> <span data-ttu-id="245f7-140">Bu durumda, yöntemin türünde bir koleksiyon döndürmesi gerekir <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="245f7-140">In this case, the method must return a collection of type <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="245f7-141">Bu tür yöntemler, bir değerler dizisine filtre veya veri dönüştürmeleri uygulamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="245f7-141">Such methods can be used to apply filters or data transforms to a sequence of values.</span></span>

<span data-ttu-id="245f7-142">Aşağıdaki örnek, `AlternateElements` ilk öğeden başlayarak bir koleksiyondaki her öğeyi döndüren adlı bir genişletme yönteminin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="245f7-142">The following example shows how to create an extension method named `AlternateElements` that returns every other element in a collection, starting from the first element.</span></span>

```csharp
// Extension method for the IEnumerable<T> interface.
// The method returns every other element of a sequence.

public static IEnumerable<T> AlternateElements<T>(this IEnumerable<T> source)
{
    List<T> list = new List<T>();

    int i = 0;

    foreach (var element in source)
    {
        if (i % 2 == 0)
        {
            list.Add(element);
        }

        i++;
    }

    return list;
}
```

<span data-ttu-id="245f7-143">Aşağıdaki kodda gösterildiği gibi, herhangi bir sayılabilir koleksiyon için bu genişletme yöntemini, arabirimden diğer yöntemleri çağırdığınız gibi çağırabilirsiniz <xref:System.Collections.Generic.IEnumerable%601> :</span><span class="sxs-lookup"><span data-stu-id="245f7-143">You can call this extension method for any enumerable collection just as you would call other methods from the <xref:System.Collections.Generic.IEnumerable%601> interface, as shown in the following code:</span></span>

```csharp
string[] strings = { "a", "b", "c", "d", "e" };

var query = strings.AlternateElements();

foreach (var element in query)
{
    Console.WriteLine(element);
}
/*
 This code produces the following output:

 a
 c
 e
*/
```

## <a name="see-also"></a><span data-ttu-id="245f7-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="245f7-144">See also</span></span>

- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="245f7-145">Uzantı Metotları</span><span class="sxs-lookup"><span data-stu-id="245f7-145">Extension Methods</span></span>](../../classes-and-structs/extension-methods.md)
