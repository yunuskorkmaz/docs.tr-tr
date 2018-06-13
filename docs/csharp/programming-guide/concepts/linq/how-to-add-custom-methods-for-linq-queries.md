---
title: 'Nasıl yapılır: LINQ sorguları için (C#) özel yöntemler ekleme'
ms.date: 07/20/2015
ms.assetid: 1a500f60-2e10-49fb-8b2a-d8d08e4817cb
ms.openlocfilehash: cd282b4b8ee4add759070317d9dbc3f78c07abf1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33326904"
---
# <a name="how-to-add-custom-methods-for-linq-queries-c"></a><span data-ttu-id="d8bb0-102">Nasıl yapılır: LINQ sorguları için (C#) özel yöntemler ekleme</span><span class="sxs-lookup"><span data-stu-id="d8bb0-102">How to: Add Custom Methods for LINQ Queries (C#)</span></span>
<span data-ttu-id="d8bb0-103">İçin genişletme yöntemleri ekleyerek LINQ sorguları için kullanabileceğiniz yöntemler kümesi genişletebilirsiniz <xref:System.Collections.Generic.IEnumerable%601> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="d8bb0-103">You can extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="d8bb0-104">Örneğin, standart ortalama veya en fazla işlemlerinin yanı sıra, değerlerin bir sırasından tek bir değeri hesaplamak için özel bir toplama yöntemi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8bb0-104">For example, in addition to the standard average or maximum operations, you can create a custom aggregate method to compute a single value from a sequence of values.</span></span> <span data-ttu-id="d8bb0-105">Özel filtre veya değerleri dizisi için belirli veri dönüştürme olarak çalışır ve yeni sırası döndüren bir yöntem de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8bb0-105">You can also create a method that works as a custom filter or a specific data transform for a sequence of values and returns a new sequence.</span></span> <span data-ttu-id="d8bb0-106">Bu tür yöntemler örnekleridir <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, ve <xref:System.Linq.Enumerable.Reverse%2A>.</span><span class="sxs-lookup"><span data-stu-id="d8bb0-106">Examples of such methods are <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, and <xref:System.Linq.Enumerable.Reverse%2A>.</span></span>  
  
 <span data-ttu-id="d8bb0-107">Genişlettiğinizde <xref:System.Collections.Generic.IEnumerable%601> arabirimi, özel yöntemlerinizi herhangi numaralandırılabilir koleksiyonuna uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8bb0-107">When you extend the <xref:System.Collections.Generic.IEnumerable%601> interface, you can apply your custom methods to any enumerable collection.</span></span> <span data-ttu-id="d8bb0-108">Daha fazla bilgi için bkz: [genişletme yöntemleri](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="d8bb0-108">For more information, see [Extension Methods](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span>  
  
## <a name="adding-an-aggregate-method"></a><span data-ttu-id="d8bb0-109">Toplama yöntemi ekleme</span><span class="sxs-lookup"><span data-stu-id="d8bb0-109">Adding an Aggregate Method</span></span>  
 <span data-ttu-id="d8bb0-110">Birleşik bir yöntemi, bir değerler kümesinden tek bir değer hesaplar.</span><span class="sxs-lookup"><span data-stu-id="d8bb0-110">An aggregate method computes a single value from a set of values.</span></span> <span data-ttu-id="d8bb0-111">LINQ sağlar dahil olmak üzere birkaç toplama yöntemleri <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, ve <xref:System.Linq.Enumerable.Max%2A>.</span><span class="sxs-lookup"><span data-stu-id="d8bb0-111">LINQ provides several aggregate methods, including <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Max%2A>.</span></span> <span data-ttu-id="d8bb0-112">Bir genişletme yöntemi ekleyerek toplama yönteminizi oluşturabilirsiniz <xref:System.Collections.Generic.IEnumerable%601> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="d8bb0-112">You can create your own aggregate method by adding an extension method to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
 <span data-ttu-id="d8bb0-113">Aşağıdaki kod örneği olarak adlandırılan bir genişletme yöntemi oluşturulacağını gösterir `Median` ORTANCA bir dizi sayı türü için işlem için `double`.</span><span class="sxs-lookup"><span data-stu-id="d8bb0-113">The following code example shows how to create an extension method called `Median` to compute a median for a sequence of numbers of type `double`.</span></span>  
  
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
  
 <span data-ttu-id="d8bb0-114">Toplam diğer yöntemleri çağırmak aynı şekilde numaralandırılabilir herhangi bir koleksiyon için bu uzantı metodu çağırma <xref:System.Collections.Generic.IEnumerable%601> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="d8bb0-114">You call this extension method for any enumerable collection in the same way you call other aggregate methods from the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
 <span data-ttu-id="d8bb0-115">Aşağıdaki kod örneğinde nasıl kullanılacağını gösterir `Median` türünde bir dizi yöntem `double`.</span><span class="sxs-lookup"><span data-stu-id="d8bb0-115">The following code example shows how to use the `Median` method for an array of type `double`.</span></span>  
  
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
  
### <a name="overloading-an-aggregate-method-to-accept-various-types"></a><span data-ttu-id="d8bb0-116">Çeşitli türlerini kabul edecek şekilde bir toplama yöntemi aşırı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="d8bb0-116">Overloading an Aggregate Method to Accept Various Types</span></span>  
 <span data-ttu-id="d8bb0-117">Toplama yöntemi aşırı yükleme çeşitli türlerdeki dizilerini kabul.</span><span class="sxs-lookup"><span data-stu-id="d8bb0-117">You can overload your aggregate method so that it accepts sequences of various types.</span></span> <span data-ttu-id="d8bb0-118">Standart yaklaşımı, her tür için bir aşırı oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="d8bb0-118">The standard approach is to create an overload for each type.</span></span> <span data-ttu-id="d8bb0-119">Başka bir yaklaşım, genel bir tür olması ve bir temsilci kullanarak belirli bir türe dönüştürmek aşırı oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="d8bb0-119">Another approach is to create an overload that will take a generic type and convert it to a specific type by using a delegate.</span></span> <span data-ttu-id="d8bb0-120">Ayrıca, her iki yaklaşımın da birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8bb0-120">You can also combine both approaches.</span></span>  
  
#### <a name="to-create-an-overload-for-each-type"></a><span data-ttu-id="d8bb0-121">Her tür için bir aşırı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d8bb0-121">To create an overload for each type</span></span>  
 <span data-ttu-id="d8bb0-122">Desteklemek istediğiniz her bir türü için belirli bir aşırı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8bb0-122">You can create a specific overload for each type that you want to support.</span></span> <span data-ttu-id="d8bb0-123">Aşağıdaki kod örneğinde bir aşırı yüklemesini gösterir `Median` yöntemi `integer` türü.</span><span class="sxs-lookup"><span data-stu-id="d8bb0-123">The following code example shows an overload of the `Median` method for the `integer` type.</span></span>  
  
```csharp  
//int overload  
  
public static double Median(this IEnumerable<int> source)  
{  
    return (from num in source select (double)num).Median();  
}  
```   
 <span data-ttu-id="d8bb0-124">Şimdi Ara `Median` her ikisi için de aşırı `integer` ve `double` aşağıdaki kodda gösterildiği gibi türleri:</span><span class="sxs-lookup"><span data-stu-id="d8bb0-124">You can now call the `Median` overloads for both `integer` and `double` types, as shown in the following code:</span></span>  
  
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

#### <a name="to-create-a-generic-overload"></a><span data-ttu-id="d8bb0-125">Bir genel aşırı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d8bb0-125">To create a generic overload</span></span>  
 <span data-ttu-id="d8bb0-126">Genel nesneler dizisi kabul eden bir aşırı de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8bb0-126">You can also create an overload that accepts a sequence of generic objects.</span></span> <span data-ttu-id="d8bb0-127">Bu aşırı temsilci bir parametre olarak alır ve belirli bir türe genel bir tür nesnelerin bir dizi dönüştürmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="d8bb0-127">This overload takes a delegate as a parameter and uses it to convert a sequence of objects of a generic type to a specific type.</span></span>  
  
 <span data-ttu-id="d8bb0-128">Aşağıdaki kod bir aşırı yüklemesini gösterir `Median` yönteminin alan <xref:System.Func%602> temsilci parametre olarak.</span><span class="sxs-lookup"><span data-stu-id="d8bb0-128">The following code shows an overload of the `Median` method that takes the <xref:System.Func%602> delegate as a parameter.</span></span> <span data-ttu-id="d8bb0-129">Bu temsilci T genel türünde bir nesne alır ve türünde bir nesne döndürür `double`.</span><span class="sxs-lookup"><span data-stu-id="d8bb0-129">This delegate takes an object of generic type T and returns an object of type `double`.</span></span>  
  
```csharp  
// Generic overload.  
  
public static double Median<T>(this IEnumerable<T> numbers,  
                       Func<T, double> selector)  
{  
    return (from num in numbers select selector(num)).Median();  
}  
```  
  
 <span data-ttu-id="d8bb0-130">Şimdi Ara `Median` herhangi bir türde nesnelerinin bir dizisi için yöntem.</span><span class="sxs-lookup"><span data-stu-id="d8bb0-130">You can now call the `Median` method for a sequence of objects of any type.</span></span> <span data-ttu-id="d8bb0-131">Türü kendi yöntemi aşırı yüklemesini yoksa bir temsilci parametre geçirmek zorunda.</span><span class="sxs-lookup"><span data-stu-id="d8bb0-131">If the type does not have its own method overload, you have to pass a delegate parameter.</span></span> <span data-ttu-id="d8bb0-132">C# ' ta lambda ifadesi bu amaç için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8bb0-132">In C#, you can use a lambda expression for this purpose.</span></span> <span data-ttu-id="d8bb0-133">Ayrıca, Visual Basic'te yalnızca kullanırsanız `Aggregate` veya `Group By` yöntem çağrısının yerine yan tümcesi, herhangi bir değer veya bu yan tümce kapsamı içinde olan deyimi iletebilir.</span><span class="sxs-lookup"><span data-stu-id="d8bb0-133">Also, in Visual Basic only, if you use the `Aggregate` or `Group By` clause instead of the method call, you can pass any value or expression that is in the scope this clause.</span></span>  
  
 <span data-ttu-id="d8bb0-134">Aşağıdaki kod örneği nasıl çağrılacağını gösterir `Median` yöntemi dizisi ve bir dizeler dizisi.</span><span class="sxs-lookup"><span data-stu-id="d8bb0-134">The following example code shows how to call the `Median` method for an array of integers and an array of strings.</span></span> <span data-ttu-id="d8bb0-135">Dizeler için dizi dizelerde uzunlukları ORTANCA hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="d8bb0-135">For strings, the median for the lengths of strings in the array is calculated.</span></span> <span data-ttu-id="d8bb0-136">Örnek nasıl iletileceğini gösterir <xref:System.Func%602> temsilci parametresi `Median` yöntemi her örneği için.</span><span class="sxs-lookup"><span data-stu-id="d8bb0-136">The example shows how to pass the <xref:System.Func%602> delegate parameter to the `Median` method for each case.</span></span>  
  
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
## <a name="adding-a-method-that-returns-a-collection"></a><span data-ttu-id="d8bb0-137">Bir koleksiyonu döndüren bir yöntem ekleme</span><span class="sxs-lookup"><span data-stu-id="d8bb0-137">Adding a Method That Returns a Collection</span></span>  
 <span data-ttu-id="d8bb0-138">Genişletebilirsiniz <xref:System.Collections.Generic.IEnumerable%601> arabirimi bir özel sorgu yöntemiyle değerleri dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="d8bb0-138">You can extend the <xref:System.Collections.Generic.IEnumerable%601> interface with a custom query method that returns a sequence of values.</span></span> <span data-ttu-id="d8bb0-139">Bu durumda, yöntem bir koleksiyon türü döndürmelidir <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="d8bb0-139">In this case, the method must return a collection of type <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="d8bb0-140">Bu tür yöntemleri değerleri dizisi için filtre ya da veri dönüşüm uygulamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d8bb0-140">Such methods can be used to apply filters or data transforms to a sequence of values.</span></span>  
  
 <span data-ttu-id="d8bb0-141">Aşağıdaki örnek adlı bir genişletme yöntemi oluşturulacağını gösterir `AlternateElements` ilk öğesinden başlayarak, bir koleksiyondaki her bir öğe getirir.</span><span class="sxs-lookup"><span data-stu-id="d8bb0-141">The following example shows how to create an extension method named `AlternateElements` that returns every other element in a collection, starting from the first element.</span></span>  
  
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
 <span data-ttu-id="d8bb0-142">Diğer yöntemleri çağırmak gibi herhangi bir numaralandırılabilir koleksiyonu için bu genişletme yöntemi çağırabilir <xref:System.Collections.Generic.IEnumerable%601> aşağıdaki kodda gösterildiği gibi arabirim:</span><span class="sxs-lookup"><span data-stu-id="d8bb0-142">You can call this extension method for any enumerable collection just as you would call other methods from the <xref:System.Collections.Generic.IEnumerable%601> interface, as shown in the following code:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d8bb0-143">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d8bb0-143">See Also</span></span>  
 <xref:System.Collections.Generic.IEnumerable%601>  
 [<span data-ttu-id="d8bb0-144">Genişletme Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="d8bb0-144">Extension Methods</span></span>](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
