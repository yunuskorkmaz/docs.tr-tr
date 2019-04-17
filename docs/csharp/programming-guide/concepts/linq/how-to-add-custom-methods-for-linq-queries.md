---
title: 'Nasıl yapılır: LINQ sorguları için özel yöntemler ekleme (C#)'
ms.date: 07/20/2015
ms.assetid: 1a500f60-2e10-49fb-8b2a-d8d08e4817cb
ms.openlocfilehash: 5aca346c182d63967f02a7f5444c5fd6d86ae3d1
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2019
ms.locfileid: "59610905"
---
# <a name="how-to-add-custom-methods-for-linq-queries-c"></a><span data-ttu-id="4ffb5-102">Nasıl yapılır: LINQ sorguları için özel yöntemler ekleme (C#)</span><span class="sxs-lookup"><span data-stu-id="4ffb5-102">How to: Add Custom Methods for LINQ Queries (C#)</span></span>

<span data-ttu-id="4ffb5-103">İçin genişletme yöntemleri ekleyerek LINQ sorguları için kullanabileceğiniz yöntemleri kümesini genişletebilirsiniz <xref:System.Collections.Generic.IEnumerable%601> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="4ffb5-103">You can extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="4ffb5-104">Örneğin, standart ortalama veya en fazla işlem ek olarak, değerler dizisinin tek bir değeri hesaplamak için özel bir toplama yöntemi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ffb5-104">For example, in addition to the standard average or maximum operations, you can create a custom aggregate method to compute a single value from a sequence of values.</span></span> <span data-ttu-id="4ffb5-105">Özel bir filtre veya belirli veri dönüştürme için değerler olarak çalışır ve yeni bir dizisini döndüren bir yöntemi de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ffb5-105">You can also create a method that works as a custom filter or a specific data transform for a sequence of values and returns a new sequence.</span></span> <span data-ttu-id="4ffb5-106">Bu tür yöntemler örnekler <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, ve <xref:System.Linq.Enumerable.Reverse%2A>.</span><span class="sxs-lookup"><span data-stu-id="4ffb5-106">Examples of such methods are <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, and <xref:System.Linq.Enumerable.Reverse%2A>.</span></span>

<span data-ttu-id="4ffb5-107">Genişlettiğinizde <xref:System.Collections.Generic.IEnumerable%601> arabirimi, herhangi bir sıralanabilir koleksiyonun özel yöntemlerinizi uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ffb5-107">When you extend the <xref:System.Collections.Generic.IEnumerable%601> interface, you can apply your custom methods to any enumerable collection.</span></span> <span data-ttu-id="4ffb5-108">Daha fazla bilgi için [genişletme yöntemleri](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="4ffb5-108">For more information, see [Extension Methods](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span>

## <a name="adding-an-aggregate-method"></a><span data-ttu-id="4ffb5-109">Bir toplama yöntemi ekleme</span><span class="sxs-lookup"><span data-stu-id="4ffb5-109">Adding an Aggregate Method</span></span>

<span data-ttu-id="4ffb5-110">Bir toplama yöntemi, bir değerler kümesinden tek bir değer hesaplar.</span><span class="sxs-lookup"><span data-stu-id="4ffb5-110">An aggregate method computes a single value from a set of values.</span></span> <span data-ttu-id="4ffb5-111">LINQ dahil olmak üzere çeşitli toplama yöntemleri sağlar <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, ve <xref:System.Linq.Enumerable.Max%2A>.</span><span class="sxs-lookup"><span data-stu-id="4ffb5-111">LINQ provides several aggregate methods, including <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Max%2A>.</span></span> <span data-ttu-id="4ffb5-112">Bir uzantı yöntemine ekleyerek kendi toplama yöntemi oluşturabilirsiniz <xref:System.Collections.Generic.IEnumerable%601> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="4ffb5-112">You can create your own aggregate method by adding an extension method to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>

<span data-ttu-id="4ffb5-113">Aşağıdaki kod örneği, adında bir genişletme yöntemi oluşturma işlemi gösterilmektedir `Median` sayı türünde bir dizi için bir ORTANCA işlem `double`.</span><span class="sxs-lookup"><span data-stu-id="4ffb5-113">The following code example shows how to create an extension method called `Median` to compute a median for a sequence of numbers of type `double`.</span></span>

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

<span data-ttu-id="4ffb5-114">Aynı şekilde diğer toplama yöntemleri çağırmak için herhangi bir sıralanabilir koleksiyonun bu uzantı metodu çağırma <xref:System.Collections.Generic.IEnumerable%601> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="4ffb5-114">You call this extension method for any enumerable collection in the same way you call other aggregate methods from the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>

<span data-ttu-id="4ffb5-115">Aşağıdaki kod örneği kullanma işlemini gösterir `Median` türünde bir dizi yöntemi `double`.</span><span class="sxs-lookup"><span data-stu-id="4ffb5-115">The following code example shows how to use the `Median` method for an array of type `double`.</span></span>

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

### <a name="overloading-an-aggregate-method-to-accept-various-types"></a><span data-ttu-id="4ffb5-116">Çeşitli türleri kabul etmek için bir toplama yöntemi aşırı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="4ffb5-116">Overloading an Aggregate Method to Accept Various Types</span></span>

<span data-ttu-id="4ffb5-117">Böylece dizileri çeşitli türlerde kabul ettiğiniz toplama yöntemi aşırı yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="4ffb5-117">You can overload your aggregate method so that it accepts sequences of various types.</span></span> <span data-ttu-id="4ffb5-118">Standart bir yaklaşım, her tür için bir aşırı oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="4ffb5-118">The standard approach is to create an overload for each type.</span></span> <span data-ttu-id="4ffb5-119">Başka bir yaklaşım genel bir tür olması ve temsilci kullanarak belirli bir türe dönüştürme aşırı oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="4ffb5-119">Another approach is to create an overload that will take a generic type and convert it to a specific type by using a delegate.</span></span> <span data-ttu-id="4ffb5-120">Ayrıca, iki yaklaşımı birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ffb5-120">You can also combine both approaches.</span></span>

#### <a name="to-create-an-overload-for-each-type"></a><span data-ttu-id="4ffb5-121">Her tür için bir aşırı yükleme oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="4ffb5-121">To create an overload for each type</span></span>

<span data-ttu-id="4ffb5-122">Desteklemek istediğiniz her bir türü için belirli bir aşırı yükleme oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ffb5-122">You can create a specific overload for each type that you want to support.</span></span> <span data-ttu-id="4ffb5-123">Aşağıdaki kod örneği bir aşırı yüklemesini gösterir `Median` yöntemi `integer` türü.</span><span class="sxs-lookup"><span data-stu-id="4ffb5-123">The following code example shows an overload of the `Median` method for the `integer` type.</span></span>

```csharp
//int overload

public static double Median(this IEnumerable<int> source)
{
    return (from num in source select (double)num).Median();
}
```

<span data-ttu-id="4ffb5-124">Artık çağırabilirsiniz `Median` hem de aşırı `integer` ve `double` türleri, aşağıdaki kodda gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="4ffb5-124">You can now call the `Median` overloads for both `integer` and `double` types, as shown in the following code:</span></span>

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

#### <a name="to-create-a-generic-overload"></a><span data-ttu-id="4ffb5-125">Genel bir aşırı yükleme oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="4ffb5-125">To create a generic overload</span></span>

<span data-ttu-id="4ffb5-126">Genel nesneler dizisi kabul eden bir aşırı yüklemeyi de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ffb5-126">You can also create an overload that accepts a sequence of generic objects.</span></span> <span data-ttu-id="4ffb5-127">Bu aşırı yükleme, bir temsilci bir parametre olarak alır ve genel bir türün nesnelerinin bir dizisi belirli bir türe dönüştürmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="4ffb5-127">This overload takes a delegate as a parameter and uses it to convert a sequence of objects of a generic type to a specific type.</span></span>

<span data-ttu-id="4ffb5-128">Aşağıdaki kod, bir aşırı yüklemesini göstermektedir `Median` gereken yöntemini <xref:System.Func%602> temsilci bir parametre olarak.</span><span class="sxs-lookup"><span data-stu-id="4ffb5-128">The following code shows an overload of the `Median` method that takes the <xref:System.Func%602> delegate as a parameter.</span></span> <span data-ttu-id="4ffb5-129">Bu temsilci T genel türünün bir nesnesini alır ve türünde bir nesne döndürür `double`.</span><span class="sxs-lookup"><span data-stu-id="4ffb5-129">This delegate takes an object of generic type T and returns an object of type `double`.</span></span>

```csharp
// Generic overload.

public static double Median<T>(this IEnumerable<T> numbers,
                       Func<T, double> selector)
{
    return (from num in numbers select selector(num)).Median();
}
```

<span data-ttu-id="4ffb5-130">Artık çağırabilirsiniz `Median` herhangi bir türde nesneler dizisi için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4ffb5-130">You can now call the `Median` method for a sequence of objects of any type.</span></span> <span data-ttu-id="4ffb5-131">Türü kendi yöntemi aşırı yüklemesini yoksa bir temsilci parametresi geçirmek zorunda.</span><span class="sxs-lookup"><span data-stu-id="4ffb5-131">If the type does not have its own method overload, you have to pass a delegate parameter.</span></span> <span data-ttu-id="4ffb5-132">C# içinde bir lambda ifadesi bu amaç için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ffb5-132">In C#, you can use a lambda expression for this purpose.</span></span> <span data-ttu-id="4ffb5-133">Ayrıca, yalnızca Visual Basic'te, kullanırsanız `Aggregate` veya `Group By` yan tümcesi yerine bir yöntem çağrısı, herhangi bir değer veya kapsamda bu yan tümce ifadesi iletebilir.</span><span class="sxs-lookup"><span data-stu-id="4ffb5-133">Also, in Visual Basic only, if you use the `Aggregate` or `Group By` clause instead of the method call, you can pass any value or expression that is in the scope this clause.</span></span>

<span data-ttu-id="4ffb5-134">Aşağıdaki kod örneği nasıl çağrılacağını gösterir `Median` yöntemi için tamsayı dizisi ve dize dizisi.</span><span class="sxs-lookup"><span data-stu-id="4ffb5-134">The following example code shows how to call the `Median` method for an array of integers and an array of strings.</span></span> <span data-ttu-id="4ffb5-135">Dizeler için dize dizisinde uzunluklarının için ORTANCA hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="4ffb5-135">For strings, the median for the lengths of strings in the array is calculated.</span></span> <span data-ttu-id="4ffb5-136">Bu örnek nasıl geçirileceğini gösterir <xref:System.Func%602> temsilci parametresi `Median` her örneği için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="4ffb5-136">The example shows how to pass the <xref:System.Func%602> delegate parameter to the `Median` method for each case.</span></span>

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

## <a name="adding-a-method-that-returns-a-collection"></a><span data-ttu-id="4ffb5-137">Bir koleksiyonu döndüren bir yöntem ekleme</span><span class="sxs-lookup"><span data-stu-id="4ffb5-137">Adding a Method That Returns a Collection</span></span>

<span data-ttu-id="4ffb5-138">Genişletebileceğiniz <xref:System.Collections.Generic.IEnumerable%601> değerlerini bir dizi döndürür bir özel sorgu yöntemi ile arabirim.</span><span class="sxs-lookup"><span data-stu-id="4ffb5-138">You can extend the <xref:System.Collections.Generic.IEnumerable%601> interface with a custom query method that returns a sequence of values.</span></span> <span data-ttu-id="4ffb5-139">Bu durumda, yöntem türü bir koleksiyon döndürmelidir <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="4ffb5-139">In this case, the method must return a collection of type <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="4ffb5-140">Bu tür yöntemler, değerler dizisi için filtre veya veri dönüşüm uygulamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4ffb5-140">Such methods can be used to apply filters or data transforms to a sequence of values.</span></span>

<span data-ttu-id="4ffb5-141">Aşağıdaki örnekte adlı bir genişletme yöntemi oluşturma işlemi gösterilmektedir `AlternateElements` ilk öğesinden başlayarak, bir koleksiyondaki her bir öğe döndürür.</span><span class="sxs-lookup"><span data-stu-id="4ffb5-141">The following example shows how to create an extension method named `AlternateElements` that returns every other element in a collection, starting from the first element.</span></span>

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

<span data-ttu-id="4ffb5-142">Gibi diğer yöntemleri çağırmak bu genişletme yöntemi için herhangi bir sıralanabilir koleksiyonun çağırabilirsiniz <xref:System.Collections.Generic.IEnumerable%601> aşağıdaki kodda gösterildiği gibi arabirim:</span><span class="sxs-lookup"><span data-stu-id="4ffb5-142">You can call this extension method for any enumerable collection just as you would call other methods from the <xref:System.Collections.Generic.IEnumerable%601> interface, as shown in the following code:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4ffb5-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4ffb5-143">See also</span></span>

- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="4ffb5-144">Genişletme Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="4ffb5-144">Extension Methods</span></span>](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
