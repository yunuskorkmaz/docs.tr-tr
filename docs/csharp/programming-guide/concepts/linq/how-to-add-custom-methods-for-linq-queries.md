---
title: LINQ sorguları için özel yöntemler ekleme (C#)
ms.date: 07/20/2015
ms.assetid: 1a500f60-2e10-49fb-8b2a-d8d08e4817cb
ms.openlocfilehash: e16175d3332b6ce36458eaa78af093e4f8772723
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141476"
---
# <a name="how-to-add-custom-methods-for-linq-queries-c"></a><span data-ttu-id="0e703-102">LINQ sorguları için özel yöntemler ekleme (C#)</span><span class="sxs-lookup"><span data-stu-id="0e703-102">How to add custom methods for LINQ queries (C#)</span></span>

<span data-ttu-id="0e703-103">Arabirime uzantı yöntemleri ekleyerek LINQ sorguları için kullanabileceğiniz <xref:System.Collections.Generic.IEnumerable%601> yöntem kümesini genişletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e703-103">You can extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="0e703-104">Örneğin, standart ortalama veya maksimum işlemlere ek olarak, bir değer dizisinden tek bir değer hesaplamak için özel bir toplama yöntemi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e703-104">For example, in addition to the standard average or maximum operations, you can create a custom aggregate method to compute a single value from a sequence of values.</span></span> <span data-ttu-id="0e703-105">Ayrıca, bir değer dizisi için özel bir filtre veya belirli bir veri dönüşümü olarak çalışan ve yeni bir sıra döndüren bir yöntem de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e703-105">You can also create a method that works as a custom filter or a specific data transform for a sequence of values and returns a new sequence.</span></span> <span data-ttu-id="0e703-106">Bu tür yöntemlere <xref:System.Linq.Enumerable.Skip%2A>örnek <xref:System.Linq.Enumerable.Reverse%2A>olarak <xref:System.Linq.Enumerable.Distinct%2A>, , ve .</span><span class="sxs-lookup"><span data-stu-id="0e703-106">Examples of such methods are <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, and <xref:System.Linq.Enumerable.Reverse%2A>.</span></span>

<span data-ttu-id="0e703-107"><xref:System.Collections.Generic.IEnumerable%601> Arabirimi genişletdiğinizde, özel yöntemlerinizi herhangi bir sayısal koleksiyona uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e703-107">When you extend the <xref:System.Collections.Generic.IEnumerable%601> interface, you can apply your custom methods to any enumerable collection.</span></span> <span data-ttu-id="0e703-108">Daha fazla bilgi için [Uzantı Yöntemleri'ne](../../classes-and-structs/extension-methods.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="0e703-108">For more information, see [Extension Methods](../../classes-and-structs/extension-methods.md).</span></span>

## <a name="adding-an-aggregate-method"></a><span data-ttu-id="0e703-109">Toplama Yöntemi Ekleme</span><span class="sxs-lookup"><span data-stu-id="0e703-109">Adding an Aggregate Method</span></span>

<span data-ttu-id="0e703-110">Toplu yöntem, bir değer kümesinden tek bir değer hesaplar.</span><span class="sxs-lookup"><span data-stu-id="0e703-110">An aggregate method computes a single value from a set of values.</span></span> <span data-ttu-id="0e703-111">LINQ, <xref:System.Linq.Enumerable.Average%2A>, , <xref:System.Linq.Enumerable.Min%2A>ve <xref:System.Linq.Enumerable.Max%2A>.</span><span class="sxs-lookup"><span data-stu-id="0e703-111">LINQ provides several aggregate methods, including <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Max%2A>.</span></span> <span data-ttu-id="0e703-112">Arabirime bir uzantı yöntemi ekleyerek kendi <xref:System.Collections.Generic.IEnumerable%601> toplama yönteminizi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e703-112">You can create your own aggregate method by adding an extension method to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>

<span data-ttu-id="0e703-113">Aşağıdaki kod örneği, bir tür `Median` `double`sayısı dizisi için ortanca yı hesaplamak için çağrılan bir uzantı yönteminin nasıl oluşturulurunun gösteriş olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="0e703-113">The following code example shows how to create an extension method called `Median` to compute a median for a sequence of numbers of type `double`.</span></span>

```csharp
public static class LINQExtension
{
    public static double Median(this IEnumerable<double> source)
    {
        if (source.Count() == 0)
        {
            throw new InvalidOperationException("Cannot compute median for an empty set.");
        }

        var sortedList = from number in source
                         orderby number
                         select number;

        int itemIndex = (int)sortedList.Count() / 2;

        if (sortedList.Count() % 2 == 0)
        {
            // Even number of items.
            return (sortedList.ElementAt(itemIndex) + sortedList.ElementAt(itemIndex - 1)) / 2;
        }
        else
        {
            // Odd number of items.
            return sortedList.ElementAt(itemIndex);
        }
    }
}
```

<span data-ttu-id="0e703-114">Bu uzantı yöntemini, <xref:System.Collections.Generic.IEnumerable%601> arabirimden diğer toplu yöntemleri çağırdığınız şekilde numaralandırma yöntemiolarak çağırırsınız.</span><span class="sxs-lookup"><span data-stu-id="0e703-114">You call this extension method for any enumerable collection in the same way you call other aggregate methods from the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>

<span data-ttu-id="0e703-115">Aşağıdaki kod örneği, yöntemin `Median` bir tür `double`dizisi için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0e703-115">The following code example shows how to use the `Median` method for an array of type `double`.</span></span>

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

### <a name="overloading-an-aggregate-method-to-accept-various-types"></a><span data-ttu-id="0e703-116">Çeşitli Türleri Kabul Etmek Için Bir Agrega Yöntemini Aşırı Yükleme</span><span class="sxs-lookup"><span data-stu-id="0e703-116">Overloading an Aggregate Method to Accept Various Types</span></span>

<span data-ttu-id="0e703-117">Çeşitli türdeki dizileri kabul etmek için toplu yönteminizi aşırı yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e703-117">You can overload your aggregate method so that it accepts sequences of various types.</span></span> <span data-ttu-id="0e703-118">Standart yaklaşım, her tür için aşırı yük oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="0e703-118">The standard approach is to create an overload for each type.</span></span> <span data-ttu-id="0e703-119">Başka bir yaklaşım, genel bir tür alacak ve bir temsilci kullanarak belirli bir türe dönüştürmek bir aşırı yük oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="0e703-119">Another approach is to create an overload that will take a generic type and convert it to a specific type by using a delegate.</span></span> <span data-ttu-id="0e703-120">Ayrıca her iki yaklaşımı da birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e703-120">You can also combine both approaches.</span></span>

#### <a name="to-create-an-overload-for-each-type"></a><span data-ttu-id="0e703-121">Her tür için aşırı yük oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="0e703-121">To create an overload for each type</span></span>

<span data-ttu-id="0e703-122">Desteklemek istediğiniz her tür için belirli bir aşırı yükleme oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e703-122">You can create a specific overload for each type that you want to support.</span></span> <span data-ttu-id="0e703-123">Aşağıdaki kod `Median` `integer` örneği, tür için yöntemin aşırı yüklenmesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0e703-123">The following code example shows an overload of the `Median` method for the `integer` type.</span></span>

```csharp
//int overload

public static double Median(this IEnumerable<int> source)
{
    return (from num in source select (double)num).Median();
}
```

<span data-ttu-id="0e703-124">Artık aşağıdaki kodda gösterildiği `integer` gibi, hem de `double` türler için `Median` aşırı yüklemeleri arayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0e703-124">You can now call the `Median` overloads for both `integer` and `double` types, as shown in the following code:</span></span>

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

#### <a name="to-create-a-generic-overload"></a><span data-ttu-id="0e703-125">Genel bir aşırı yük oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="0e703-125">To create a generic overload</span></span>

<span data-ttu-id="0e703-126">Ayrıca, genel nesnelerin bir dizi kabul eden bir aşırı yük oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e703-126">You can also create an overload that accepts a sequence of generic objects.</span></span> <span data-ttu-id="0e703-127">Bu aşırı yük bir temsilciyi parametre olarak alır ve genel bir türdeki nesnelerin dizisini belirli bir türe dönüştürmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="0e703-127">This overload takes a delegate as a parameter and uses it to convert a sequence of objects of a generic type to a specific type.</span></span>

<span data-ttu-id="0e703-128">Aşağıdaki kod, `Median` <xref:System.Func%602> temsilciyi parametre olarak alan yöntemin aşırı yüklenmesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0e703-128">The following code shows an overload of the `Median` method that takes the <xref:System.Func%602> delegate as a parameter.</span></span> <span data-ttu-id="0e703-129">Bu temsilci genel t türünde bir nesne `double`alır ve türünde bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="0e703-129">This delegate takes an object of generic type T and returns an object of type `double`.</span></span>

```csharp
// Generic overload.

public static double Median<T>(this IEnumerable<T> numbers,
                       Func<T, double> selector)
{
    return (from num in numbers select selector(num)).Median();
}
```

<span data-ttu-id="0e703-130">Artık herhangi bir `Median` türdeki nesnelerin bir dizi için yöntemi arayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e703-130">You can now call the `Median` method for a sequence of objects of any type.</span></span> <span data-ttu-id="0e703-131">Türün kendi yöntemi aşırı yüklemesi yoksa, bir temsilci parametresini geçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0e703-131">If the type does not have its own method overload, you have to pass a delegate parameter.</span></span> <span data-ttu-id="0e703-132">C#'da, bu amaçla lambda ifadesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e703-132">In C#, you can use a lambda expression for this purpose.</span></span> <span data-ttu-id="0e703-133">Ayrıca, yalnızca Visual Basic'te, `Aggregate` `Group By` yöntem çağrısı yerine veya yan tümcesini kullanırsanız, bu yan tümce kapsamında ki herhangi bir değeri veya ifadeyi geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e703-133">Also, in Visual Basic only, if you use the `Aggregate` or `Group By` clause instead of the method call, you can pass any value or expression that is in the scope this clause.</span></span>

<span data-ttu-id="0e703-134">Aşağıdaki örnek kod, bir `Median` dizi bir karşıcı ve dize dizisi için yöntemin nasıl çağrılmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0e703-134">The following example code shows how to call the `Median` method for an array of integers and an array of strings.</span></span> <span data-ttu-id="0e703-135">Dizeleri için, dizideki dizelerin uzunluklarının ortancası hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="0e703-135">For strings, the median for the lengths of strings in the array is calculated.</span></span> <span data-ttu-id="0e703-136">Örnek, <xref:System.Func%602> her servis talebi için `Median` yönteme temsilci parametresinin nasıl geçirilen gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0e703-136">The example shows how to pass the <xref:System.Func%602> delegate parameter to the `Median` method for each case.</span></span>

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

## <a name="adding-a-method-that-returns-a-collection"></a><span data-ttu-id="0e703-137">Koleksiyon Döndüren Yöntem Ekleme</span><span class="sxs-lookup"><span data-stu-id="0e703-137">Adding a Method That Returns a Collection</span></span>

<span data-ttu-id="0e703-138"><xref:System.Collections.Generic.IEnumerable%601> Bir değer dizisi döndüren özel bir sorgu yöntemiyle arabirimi genişletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e703-138">You can extend the <xref:System.Collections.Generic.IEnumerable%601> interface with a custom query method that returns a sequence of values.</span></span> <span data-ttu-id="0e703-139">Bu durumda, yöntem türünden <xref:System.Collections.Generic.IEnumerable%601>bir koleksiyon döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="0e703-139">In this case, the method must return a collection of type <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="0e703-140">Bu tür yöntemler, filtreleri veya veri dönüşümlerini bir değer dizisine uygulamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0e703-140">Such methods can be used to apply filters or data transforms to a sequence of values.</span></span>

<span data-ttu-id="0e703-141">Aşağıdaki örnek, ilk öğeden başlayarak bir koleksiyondaki diğer tüm öğeyi döndüren adlandırılmış `AlternateElements` bir uzantı yönteminin nasıl oluşturulurdu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0e703-141">The following example shows how to create an extension method named `AlternateElements` that returns every other element in a collection, starting from the first element.</span></span>

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

<span data-ttu-id="0e703-142">Aşağıdaki kodda gösterildiği gibi, <xref:System.Collections.Generic.IEnumerable%601> arabirimden diğer yöntemleri çağıracağınız gibi, herhangi bir numaralandırma için bu uzantılı yöntemi arayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0e703-142">You can call this extension method for any enumerable collection just as you would call other methods from the <xref:System.Collections.Generic.IEnumerable%601> interface, as shown in the following code:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="0e703-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0e703-143">See also</span></span>

- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="0e703-144">Genişletme Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="0e703-144">Extension Methods</span></span>](../../classes-and-structs/extension-methods.md)
