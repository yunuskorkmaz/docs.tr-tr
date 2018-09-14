---
title: Koleksiyonlar (C#)
ms.date: 07/20/2015
ms.assetid: 317d7dc3-8587-4873-8b3e-556f86497939
ms.openlocfilehash: 24b2155c07b6b66820d373d6310ff6b1c6ab224f
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45527453"
---
# <a name="collections-c"></a><span data-ttu-id="4c032-102">Koleksiyonlar (C#)</span><span class="sxs-lookup"><span data-stu-id="4c032-102">Collections (C#)</span></span>
<span data-ttu-id="4c032-103">Birçok uygulama için ilgili nesnelerin gruplarını oluşturmak ve yönetmek istersiniz.</span><span class="sxs-lookup"><span data-stu-id="4c032-103">For many applications, you want to create and manage groups of related objects.</span></span> <span data-ttu-id="4c032-104">Grup nesnelerini iki yolu vardır: nesne dizileri oluşturarak ve veya nesne koleksiyonu oluşturarak.</span><span class="sxs-lookup"><span data-stu-id="4c032-104">There are two ways to group objects: by creating arrays of objects, and by creating collections of objects.</span></span>  
  
 <span data-ttu-id="4c032-105">Dizileri oluşturmak ve nesneleri türü kesin olarak belirtilmiş sabit sayıdaki ile çalışmak için ekseriyetle faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="4c032-105">Arrays are most useful for creating and working with a fixed number of strongly-typed objects.</span></span> <span data-ttu-id="4c032-106">Diziler hakkında daha fazla bilgi için bkz: [diziler](../../../csharp/programming-guide/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="4c032-106">For information about arrays, see [Arrays](../../../csharp/programming-guide/arrays/index.md).</span></span>  
  
 <span data-ttu-id="4c032-107">Koleksiyonlar nesne grupları ile çalışmak için daha esnek bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="4c032-107">Collections provide a more flexible way to work with groups of objects.</span></span> <span data-ttu-id="4c032-108">Dizilerden farklı olarak çalıştığınız nesne büyütme ve uygulamanın ihtiyacına göre dinamik olarak Daralt.</span><span class="sxs-lookup"><span data-stu-id="4c032-108">Unlike arrays, the group of objects you work with can grow and shrink dynamically as the needs of the application change.</span></span> <span data-ttu-id="4c032-109">Bazı koleksiyonlar için koleksiyona eklediğiniz ve böylece anahtarını kullanarak hızlı bir şekilde nesnesi alabilirsiniz herhangi bir nesneye bir anahtar atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4c032-109">For some collections, you can assign a key to any object that you put into the collection so that you can quickly retrieve the object by using the key.</span></span>  
  
 <span data-ttu-id="4c032-110">Bir koleksiyon bir sınıfı olduğundan bu koleksiyona öğeleri eklemeden önce sınıfının bir örneğini bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4c032-110">A collection is a class, so you must declare an instance of the class before you can add elements to that collection.</span></span>  
  
 <span data-ttu-id="4c032-111">Koleksiyonunuz tek bir veri türünde öğeler içeriyorsa, sınıflarda birini kullanabilirsiniz <xref:System.Collections.Generic?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="4c032-111">If your collection contains elements of only one data type, you can use one of the classes in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="4c032-112">Genel koleksiyon tür güvenliği sağlar, böylece başka bir veri türü eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="4c032-112">A generic collection enforces type safety so that no other data type can be added to it.</span></span> <span data-ttu-id="4c032-113">Bir genel koleksiyondan öğe aldığınızda veri türünü belirlemeniz veya dönüştürmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="4c032-113">When you retrieve an element from a generic collection, you do not have to determine its data type or convert it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4c032-114">Bu konudaki örnekler için dahil [kullanarak](../../../csharp/language-reference/keywords/using-directive.md) yönergeleri `System.Collections.Generic` ve `System.Linq` ad alanları.</span><span class="sxs-lookup"><span data-stu-id="4c032-114">For the examples in this topic, include [using](../../../csharp/language-reference/keywords/using-directive.md) directives for the `System.Collections.Generic` and `System.Linq` namespaces.</span></span>  
  
 <span data-ttu-id="4c032-115">**Bu konudaki**</span><span class="sxs-lookup"><span data-stu-id="4c032-115">**In this topic**</span></span>  
  
-   [<span data-ttu-id="4c032-116">Basit bir koleksiyon kullanma</span><span class="sxs-lookup"><span data-stu-id="4c032-116">Using a Simple Collection</span></span>](#BKMK_SimpleCollection)  
  
-   [<span data-ttu-id="4c032-117">Koleksiyon türleri</span><span class="sxs-lookup"><span data-stu-id="4c032-117">Kinds of Collections</span></span>](#BKMK_KindsOfCollections)  
  
    -   [<span data-ttu-id="4c032-118">System.Collections.Generic sınıfları</span><span class="sxs-lookup"><span data-stu-id="4c032-118">System.Collections.Generic Classes</span></span>](#BKMK_Generic)  
  
    -   [<span data-ttu-id="4c032-119">System.Collections.Concurrent sınıfları</span><span class="sxs-lookup"><span data-stu-id="4c032-119">System.Collections.Concurrent Classes</span></span>](#BKMK_Concurrent)  
  
    -   [<span data-ttu-id="4c032-120">System.Collections sınıfları</span><span class="sxs-lookup"><span data-stu-id="4c032-120">System.Collections Classes</span></span>](#BKMK_Collections)  
  
-   [<span data-ttu-id="4c032-121">Anahtar/değer çiftleri topluluğu uygulama</span><span class="sxs-lookup"><span data-stu-id="4c032-121">Implementing a Collection of Key/Value Pairs</span></span>](#BKMK_KeyValuePairs)  
  
-   [<span data-ttu-id="4c032-122">Koleksiyona erişmek için LINQ kullanma</span><span class="sxs-lookup"><span data-stu-id="4c032-122">Using LINQ to Access a Collection</span></span>](#BKMK_LINQ)  
  
-   [<span data-ttu-id="4c032-123">Koleksiyonda sıralama</span><span class="sxs-lookup"><span data-stu-id="4c032-123">Sorting a Collection</span></span>](#BKMK_Sorting)  
  
-   [<span data-ttu-id="4c032-124">Özel koleksiyonu tanımlama</span><span class="sxs-lookup"><span data-stu-id="4c032-124">Defining a Custom Collection</span></span>](#BKMK_CustomCollection)  
  
-   [<span data-ttu-id="4c032-125">Yineleyiciler</span><span class="sxs-lookup"><span data-stu-id="4c032-125">Iterators</span></span>](#BKMK_Iterators)  
  
<a name="BKMK_SimpleCollection"></a>
## <a name="using-a-simple-collection"></a><span data-ttu-id="4c032-126">Basit bir koleksiyon kullanma</span><span class="sxs-lookup"><span data-stu-id="4c032-126">Using a Simple Collection</span></span>  
 <span data-ttu-id="4c032-127">Bu bölümdeki örneklerde genel kullanın <xref:System.Collections.Generic.List%601> sınıfını, bir türü kesin belirlenmiş nesneler listesiyle çalışmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="4c032-127">The examples in this section use the generic <xref:System.Collections.Generic.List%601> class, which enables you to work with a strongly typed list of objects.</span></span>  
  
 <span data-ttu-id="4c032-128">Aşağıdaki örnek bir dize listesi oluşturur ve ardından kullanarak dizeler arasında yinelenir. bir ya da [foreach](../../../csharp/language-reference/keywords/foreach-in.md) deyimi.</span><span class="sxs-lookup"><span data-stu-id="4c032-128">The following example creates a list of strings and then iterates through the strings by using a or [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement.</span></span>  
  
```csharp  
// Create a list of strings.  
var salmons = new List<string>();  
salmons.Add("chinook");  
salmons.Add("coho");  
salmons.Add("pink");  
salmons.Add("sockeye");  
  
// Iterate through the list.  
foreach (var salmon in salmons)  
{  
    Console.Write(salmon + " ");  
}  
// Output: chinook coho pink sockeye  
```  
  
 <span data-ttu-id="4c032-129">Bir koleksiyonun içeriği önceden biliniyorsa, kullanabileceğiniz bir *koleksiyon Başlatıcısı* koleksiyonu başlatmak için.</span><span class="sxs-lookup"><span data-stu-id="4c032-129">If the contents of a collection are known in advance, you can use a *collection initializer* to initialize the collection.</span></span> <span data-ttu-id="4c032-130">Daha fazla bilgi için [nesne ve koleksiyon başlatıcıları](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span><span class="sxs-lookup"><span data-stu-id="4c032-130">For more information, see [Object and Collection Initializers](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span></span>  
  
 <span data-ttu-id="4c032-131">Koleksiyona öğeleri eklemek için bir koleksiyon Başlatıcısı kullanılması dışında aşağıdaki örnek önceki örnekle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="4c032-131">The following example is the same as the previous example, except a collection initializer is used to add elements to the collection.</span></span>  
  
```csharp  
// Create a list of strings by using a  
// collection initializer.  
var salmons = new List<string> { "chinook", "coho", "pink", "sockeye" };  
  
// Iterate through the list.  
foreach (var salmon in salmons)  
{  
    Console.Write(salmon + " ");  
}  
// Output: chinook coho pink sockeye  
```  
  
 <span data-ttu-id="4c032-132">Kullanabileceğiniz bir [için](../../../csharp/language-reference/keywords/for.md) deyimi yerine bir `foreach` deyimi bir koleksiyon içinde yineleme için.</span><span class="sxs-lookup"><span data-stu-id="4c032-132">You can use a [for](../../../csharp/language-reference/keywords/for.md) statement instead of a `foreach` statement to iterate through a collection.</span></span> <span data-ttu-id="4c032-133">Bu, bir koleksiyon öğelerine dizin konumundan erişerek gerçekleştirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4c032-133">You accomplish this by accessing the collection elements by the index position.</span></span> <span data-ttu-id="4c032-134">Öğelerin dizini 0'da başlar ve öğe sayısı eksi 1'de sona erer.</span><span class="sxs-lookup"><span data-stu-id="4c032-134">The index of the elements starts at 0 and ends at the element count minus 1.</span></span>  
  
 <span data-ttu-id="4c032-135">Aşağıdaki örneği kullanarak bir koleksiyonun öğeleri yinelenir `for` yerine `foreach`.</span><span class="sxs-lookup"><span data-stu-id="4c032-135">The following example iterates through the elements of a collection by using `for` instead of `foreach`.</span></span>  
  
```csharp  
// Create a list of strings by using a  
// collection initializer.  
var salmons = new List<string> { "chinook", "coho", "pink", "sockeye" };  
  
for (var index = 0; index < salmons.Count; index++)  
{  
    Console.Write(salmons[index] + " ");  
}  
// Output: chinook coho pink sockeye  
```  
  
 <span data-ttu-id="4c032-136">Aşağıdaki örnek, bir öğe kaldırmak için nesneyi belirterek koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="4c032-136">The following example removes an element from the collection by specifying the object to remove.</span></span>  
  
```csharp  
// Create a list of strings by using a  
// collection initializer.  
var salmons = new List<string> { "chinook", "coho", "pink", "sockeye" };  
  
// Remove an element from the list by specifying  
// the object.  
salmons.Remove("coho");  
  
// Iterate through the list.  
foreach (var salmon in salmons)  
{  
    Console.Write(salmon + " ");  
}  
// Output: chinook pink sockeye  
```  
  
 <span data-ttu-id="4c032-137">Aşağıdaki örnek bir genel listeden öğeleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="4c032-137">The following example removes elements from a generic list.</span></span> <span data-ttu-id="4c032-138">Yerine bir `foreach` deyimi, bir [için](../../../csharp/language-reference/keywords/for.md) azalan sırada yenileyen deyimi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4c032-138">Instead of a `foreach` statement, a [for](../../../csharp/language-reference/keywords/for.md) statement that iterates in descending order is used.</span></span> <span data-ttu-id="4c032-139">Bunun nedeni, <xref:System.Collections.Generic.List%601.RemoveAt%2A> yöntemi bir alt dizin değerine sahip olacak şekilde kaldırılmış bir öğeden sonra öğe neden olur.</span><span class="sxs-lookup"><span data-stu-id="4c032-139">This is because the <xref:System.Collections.Generic.List%601.RemoveAt%2A> method causes elements after a removed element to have a lower index value.</span></span>  
  
```csharp  
var numbers = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
  
// Remove odd numbers.  
for (var index = numbers.Count - 1; index >= 0; index--)  
{  
    if (numbers[index] % 2 == 1)  
    {  
        // Remove the element by specifying  
        // the zero-based index in the list.  
        numbers.RemoveAt(index);  
    }  
}  
  
// Iterate through the list.  
// A lambda expression is placed in the ForEach method  
// of the List(T) object.  
numbers.ForEach(  
    number => Console.Write(number + " "));  
// Output: 0 2 4 6 8  
```  
  
 <span data-ttu-id="4c032-140">İçindeki öğe türleri için <xref:System.Collections.Generic.List%601>, ayrıca kendi sınıfınızı tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4c032-140">For the type of elements in the <xref:System.Collections.Generic.List%601>, you can also define your own class.</span></span> <span data-ttu-id="4c032-141">Aşağıdaki örnekte, `Galaxy` tarafından kullanılan sınıfı <xref:System.Collections.Generic.List%601> kodda tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="4c032-141">In the following example, the `Galaxy` class that is used by the <xref:System.Collections.Generic.List%601> is defined in the code.</span></span>  
  
```csharp  
private static void IterateThroughList()  
{  
    var theGalaxies = new List<Galaxy>  
        {  
            new Galaxy() { Name="Tadpole", MegaLightYears=400},  
            new Galaxy() { Name="Pinwheel", MegaLightYears=25},  
            new Galaxy() { Name="Milky Way", MegaLightYears=0},  
            new Galaxy() { Name="Andromeda", MegaLightYears=3}  
        };  
  
    foreach (Galaxy theGalaxy in theGalaxies)  
    {  
        Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears);  
    }  
  
    // Output:  
    //  Tadpole  400  
    //  Pinwheel  25  
    //  Milky Way  0  
    //  Andromeda  3  
}  
  
public class Galaxy  
{  
    public string Name { get; set; }  
    public int MegaLightYears { get; set; }  
}  
```  

<a name="BKMK_KindsOfCollections"></a>
## <a name="kinds-of-collections"></a><span data-ttu-id="4c032-142">Koleksiyon türleri</span><span class="sxs-lookup"><span data-stu-id="4c032-142">Kinds of Collections</span></span> 
 <span data-ttu-id="4c032-143">Ortak koleksiyonların çoğu .NET Framework tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="4c032-143">Many common collections are provided by the .NET Framework.</span></span> <span data-ttu-id="4c032-144">Her koleksiyon türü belirli bir amaç için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="4c032-144">Each type of collection is designed for a specific purpose.</span></span>  
  
 <span data-ttu-id="4c032-145">Bazı ortak koleksiyon sınıfları, bu bölümde açıklanan:</span><span class="sxs-lookup"><span data-stu-id="4c032-145">Some of the common collection classes are described in this section:</span></span>  
  
-   <span data-ttu-id="4c032-146"><xref:System.Collections.Generic> Sınıfları</span><span class="sxs-lookup"><span data-stu-id="4c032-146"><xref:System.Collections.Generic> classes</span></span>  
  
-   <span data-ttu-id="4c032-147"><xref:System.Collections.Concurrent> Sınıfları</span><span class="sxs-lookup"><span data-stu-id="4c032-147"><xref:System.Collections.Concurrent> classes</span></span>  
  
-   <span data-ttu-id="4c032-148"><xref:System.Collections> Sınıfları</span><span class="sxs-lookup"><span data-stu-id="4c032-148"><xref:System.Collections> classes</span></span>  
  
<a name="BKMK_Generic"></a>
### <a name="systemcollectionsgeneric-classes"></a><span data-ttu-id="4c032-149">System.Collections.Generic sınıfları</span><span class="sxs-lookup"><span data-stu-id="4c032-149">System.Collections.Generic Classes</span></span>  
 <span data-ttu-id="4c032-150">Genel koleksiyon sınıfları birini kullanarak oluşturabileceğiniz <xref:System.Collections.Generic> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="4c032-150">You can create a generic collection by using one of the classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="4c032-151">Genel koleksiyon, koleksiyondaki her öğe aynı veri türüne sahip olduğunda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="4c032-151">A generic collection is useful when every item in the collection has the same data type.</span></span> <span data-ttu-id="4c032-152">Yalnızca istenen veri sağlayarak güçlü yazmayı genel koleksiyon sağlar eklenecek türü.</span><span class="sxs-lookup"><span data-stu-id="4c032-152">A generic collection enforces strong typing by allowing only the desired data type to be added.</span></span>  
  
 <span data-ttu-id="4c032-153">Aşağıdaki tabloda sık kullanılan sınıflarından bazılarını listeler <xref:System.Collections.Generic?displayProperty=nameWithType> ad alanı:</span><span class="sxs-lookup"><span data-stu-id="4c032-153">The following table lists some of the frequently used classes of the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace:</span></span>  

|<span data-ttu-id="4c032-154">örneği</span><span class="sxs-lookup"><span data-stu-id="4c032-154">Class</span></span>|<span data-ttu-id="4c032-155">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4c032-155">Description</span></span>| 
|---|---|  
|<xref:System.Collections.Generic.Dictionary%602>|<span data-ttu-id="4c032-156">Anahtara göre düzenlenen anahtar/değer çifti koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4c032-156">Represents a collection of key/value pairs that are organized based on the key.</span></span>|  
|<xref:System.Collections.Generic.List%601>|<span data-ttu-id="4c032-157">Dizin tarafından erişilebilecek nesnelerin bir listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4c032-157">Represents a list of objects that can be accessed by index.</span></span> <span data-ttu-id="4c032-158">Arama, sıralama ve listelerini değiştirmek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="4c032-158">Provides methods to search, sort, and modify lists.</span></span>|  
|<xref:System.Collections.Generic.Queue%601>|<span data-ttu-id="4c032-159">İlk giren ilk çıkar (FIFO) nesne koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4c032-159">Represents a first in, first out (FIFO) collection of objects.</span></span>|  
|<xref:System.Collections.Generic.SortedList%602>|<span data-ttu-id="4c032-160">Anahtarıyla ilişkili göre sıralanan anahtar/değer çiftlerinin koleksiyonunu temsil eder <xref:System.Collections.Generic.IComparer%601> uygulaması.</span><span class="sxs-lookup"><span data-stu-id="4c032-160">Represents a collection of key/value pairs that are sorted by key based on the associated <xref:System.Collections.Generic.IComparer%601> implementation.</span></span>|  
|<xref:System.Collections.Generic.Stack%601>|<span data-ttu-id="4c032-161">Son giren ilk çıkar (LIFO) nesne koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4c032-161">Represents a last in, first out (LIFO) collection of objects.</span></span>|  
  
 <span data-ttu-id="4c032-162">Ek bilgi için bkz: [yaygın olarak kullanılan koleksiyon türleri](../../../standard/collections/commonly-used-collection-types.md), [koleksiyon sınıfı seçme](../../../standard/collections/selecting-a-collection-class.md), ve <xref:System.Collections.Generic>.</span><span class="sxs-lookup"><span data-stu-id="4c032-162">For additional information, see [Commonly Used Collection Types](../../../standard/collections/commonly-used-collection-types.md), [Selecting a Collection Class](../../../standard/collections/selecting-a-collection-class.md), and <xref:System.Collections.Generic>.</span></span>  
  
<a name="BKMK_Concurrent"></a>
### <a name="systemcollectionsconcurrent-classes"></a><span data-ttu-id="4c032-163">System.Collections.Concurrent sınıfları</span><span class="sxs-lookup"><span data-stu-id="4c032-163">System.Collections.Concurrent Classes</span></span>  
 <span data-ttu-id="4c032-164">.NET Framework 4 veya daha yeni sürümü, koleksiyonlar <xref:System.Collections.Concurrent> ad alanı, koleksiyon öğelerine birden fazla iş parçacığından erişmek için verimli bir iş parçacığı açısından güvenli işlemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="4c032-164">In the .NET Framework 4 or newer, the collections in the <xref:System.Collections.Concurrent> namespace provide efficient thread-safe operations for accessing collection items from multiple threads.</span></span>  
  
 <span data-ttu-id="4c032-165">Sınıflarda <xref:System.Collections.Concurrent> ad alanı, karşılık gelen türler yerine kullanılmalıdır <xref:System.Collections.Generic?displayProperty=nameWithType> ve <xref:System.Collections?displayProperty=nameWithType> birden çok iş parçacığı koleksiyon eriştiği her seferde ad alanları.</span><span class="sxs-lookup"><span data-stu-id="4c032-165">The classes in the <xref:System.Collections.Concurrent> namespace should be used instead of the corresponding types in the <xref:System.Collections.Generic?displayProperty=nameWithType> and <xref:System.Collections?displayProperty=nameWithType> namespaces whenever multiple threads are accessing the collection concurrently.</span></span> <span data-ttu-id="4c032-166">Daha fazla bilgi için [iş parçacığı güvenli koleksiyonları](../../../standard/collections/thread-safe/index.md) ve <xref:System.Collections.Concurrent>.</span><span class="sxs-lookup"><span data-stu-id="4c032-166">For more information, see [Thread-Safe Collections](../../../standard/collections/thread-safe/index.md) and <xref:System.Collections.Concurrent>.</span></span>  
  
 <span data-ttu-id="4c032-167">Eklenen bazı sınıflar <xref:System.Collections.Concurrent> ad <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, ve <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span><span class="sxs-lookup"><span data-stu-id="4c032-167">Some classes included in the <xref:System.Collections.Concurrent> namespace are <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>  
  
<a name="BKMK_Collections"></a>
### <a name="systemcollections-classes"></a><span data-ttu-id="4c032-168">System.Collections sınıfları</span><span class="sxs-lookup"><span data-stu-id="4c032-168">System.Collections Classes</span></span>  
 <span data-ttu-id="4c032-169">Sınıflarda <xref:System.Collections?displayProperty=nameWithType> özellikle yazılmış nesneler, ancak nesne türü ad alanı öğeleri saklamayın `Object`.</span><span class="sxs-lookup"><span data-stu-id="4c032-169">The classes in the <xref:System.Collections?displayProperty=nameWithType> namespace do not store elements as specifically typed objects, but as objects of type `Object`.</span></span>  
  
 <span data-ttu-id="4c032-170">Mümkün olduğunda genel koleksiyonları kullanması gereken <xref:System.Collections.Generic?displayProperty=nameWithType> ad alanı veya <xref:System.Collections.Concurrent> ad alanındaki eski türlerde yerine `System.Collections` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="4c032-170">Whenever possible, you should use the generic collections in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace or the <xref:System.Collections.Concurrent> namespace instead of the legacy types in the `System.Collections` namespace.</span></span>  
  
 <span data-ttu-id="4c032-171">Aşağıdaki tabloda sık kullanılan sınıflarından bazılarını listeler `System.Collections` ad alanı:</span><span class="sxs-lookup"><span data-stu-id="4c032-171">The following table lists some of the frequently used classes in the `System.Collections` namespace:</span></span>  
  
|<span data-ttu-id="4c032-172">örneği</span><span class="sxs-lookup"><span data-stu-id="4c032-172">Class</span></span>|<span data-ttu-id="4c032-173">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4c032-173">Description</span></span>|  
|---|---|  
|<xref:System.Collections.ArrayList>|<span data-ttu-id="4c032-174">Bir dizi boyutu olarak dinamik olarak artırılan nesne dizilerini temsil gereklidir.</span><span class="sxs-lookup"><span data-stu-id="4c032-174">Represents an array of objects whose size is dynamically increased as required.</span></span>|  
|<xref:System.Collections.Hashtable>|<span data-ttu-id="4c032-175">Anahtarın karma koduna göre düzenlenen anahtar/değer çifti koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4c032-175">Represents a collection of key/value pairs that are organized based on the hash code of the key.</span></span>|  
|<xref:System.Collections.Queue>|<span data-ttu-id="4c032-176">İlk giren ilk çıkar (FIFO) nesne koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4c032-176">Represents a first in, first out (FIFO) collection of objects.</span></span>|  
|<xref:System.Collections.Stack>|<span data-ttu-id="4c032-177">Son giren ilk çıkar (LIFO) nesne koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4c032-177">Represents a last in, first out (LIFO) collection of objects.</span></span>|  
  
 <span data-ttu-id="4c032-178"><xref:System.Collections.Specialized> Ad alanı yalnızca dize koleksiyonları ve bağlantılı liste ve melez sözlükler gibi özelleştirilmiş ve türü kesin belirlenmiş koleksiyon sınıfları sağlar.</span><span class="sxs-lookup"><span data-stu-id="4c032-178">The <xref:System.Collections.Specialized> namespace provides specialized and strongly typed collection classes, such as string-only collections and linked-list and hybrid dictionaries.</span></span>  

<a name="BKMK_KeyValuePairs"></a>
## <a name="implementing-a-collection-of-keyvalue-pairs"></a><span data-ttu-id="4c032-179">Anahtar/değer çiftleri topluluğu uygulama</span><span class="sxs-lookup"><span data-stu-id="4c032-179">Implementing a Collection of Key/Value Pairs</span></span>  
 <span data-ttu-id="4c032-180"><xref:System.Collections.Generic.Dictionary%602> Genel koleksiyonu her öğenin anahtarını kullanarak bir koleksiyondaki öğelere erişmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="4c032-180">The <xref:System.Collections.Generic.Dictionary%602> generic collection enables you to access to elements in a collection by using the key of each element.</span></span> <span data-ttu-id="4c032-181">Her ek sözlük için bir değer ve ilişkili anahtarını oluşur.</span><span class="sxs-lookup"><span data-stu-id="4c032-181">Each addition to the dictionary consists of a value and its associated key.</span></span> <span data-ttu-id="4c032-182">Bir değeri anahtarını kullanarak almak oldukça hızlıdır `Dictionary` sınıfı bir karma tablo olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="4c032-182">Retrieving a value by using its key is fast because the `Dictionary` class is implemented as a hash table.</span></span>  
  
 <span data-ttu-id="4c032-183">Aşağıdaki örnek, oluşturur bir `Dictionary` koleksiyonu ve kullanarak sözlük yinelenir. bir `foreach` deyimi.</span><span class="sxs-lookup"><span data-stu-id="4c032-183">The following example creates a `Dictionary` collection and iterates through the dictionary by using a `foreach` statement.</span></span>  
  
```csharp  
private static void IterateThruDictionary()  
{  
    Dictionary<string, Element> elements = BuildDictionary();  
  
    foreach (KeyValuePair<string, Element> kvp in elements)  
    {  
        Element theElement = kvp.Value;  
  
        Console.WriteLine("key: " + kvp.Key);  
        Console.WriteLine("values: " + theElement.Symbol + " " +  
            theElement.Name + " " + theElement.AtomicNumber);  
    }  
}  
  
private static Dictionary<string, Element> BuildDictionary()  
{  
    var elements = new Dictionary<string, Element>();  
  
    AddToDictionary(elements, "K", "Potassium", 19);  
    AddToDictionary(elements, "Ca", "Calcium", 20);  
    AddToDictionary(elements, "Sc", "Scandium", 21);  
    AddToDictionary(elements, "Ti", "Titanium", 22);  
  
    return elements;  
}  
  
private static void AddToDictionary(Dictionary<string, Element> elements,  
    string symbol, string name, int atomicNumber)  
{  
    Element theElement = new Element();  
  
    theElement.Symbol = symbol;  
    theElement.Name = name;  
    theElement.AtomicNumber = atomicNumber;  
  
    elements.Add(key: theElement.Symbol, value: theElement);  
}  
  
public class Element  
{  
    public string Symbol { get; set; }  
    public string Name { get; set; }  
    public int AtomicNumber { get; set; }  
}  
```  
  
 <span data-ttu-id="4c032-184">Bunun yerine bir koleksiyon Başlatıcısı oluşturmak için kullanılacak `Dictionary` koleksiyonu değiştirebilirsiniz `BuildDictionary` ve `AddToDictionary` yöntemlerini aşağıdaki yöntemle.</span><span class="sxs-lookup"><span data-stu-id="4c032-184">To instead use a collection initializer to build the `Dictionary` collection, you can replace the `BuildDictionary` and `AddToDictionary` methods with the following method.</span></span>  
  
```csharp  
private static Dictionary<string, Element> BuildDictionary2()  
{  
    return new Dictionary<string, Element>  
    {  
        {"K",  
            new Element() { Symbol="K", Name="Potassium", AtomicNumber=19}},  
        {"Ca",  
            new Element() { Symbol="Ca", Name="Calcium", AtomicNumber=20}},  
        {"Sc",  
            new Element() { Symbol="Sc", Name="Scandium", AtomicNumber=21}},  
        {"Ti",  
            new Element() { Symbol="Ti", Name="Titanium", AtomicNumber=22}}  
    };  
}  
```  
  
 <span data-ttu-id="4c032-185">Aşağıdaki örnekte <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> yöntemi ve <xref:System.Collections.Generic.Dictionary%602.Item%2A> özelliği `Dictionary` öğeyi anahtara göre hızlı bir şekilde bulmak için.</span><span class="sxs-lookup"><span data-stu-id="4c032-185">The following example uses the <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> method and the <xref:System.Collections.Generic.Dictionary%602.Item%2A> property of `Dictionary` to quickly find an item by key.</span></span> <span data-ttu-id="4c032-186">`Item` Özelliği bir öğeye erişmenize olanak tanır `elements` kullanarak koleksiyon `elements[symbol]` C#.</span><span class="sxs-lookup"><span data-stu-id="4c032-186">The `Item` property enables you to access an item in the `elements` collection by using the `elements[symbol]` in C#.</span></span>  
  
```csharp  
private static void FindInDictionary(string symbol)  
{  
    Dictionary<string, Element> elements = BuildDictionary();  
  
    if (elements.ContainsKey(symbol) == false)  
    {  
        Console.WriteLine(symbol + " not found");  
    }  
    else  
    {  
        Element theElement = elements[symbol];  
        Console.WriteLine("found: " + theElement.Name);  
    }  
}  
```  
  
 <span data-ttu-id="4c032-187">Aşağıdaki örnek, bunun yerine kullanır <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> yöntemi anahtara göre hızlı bir şekilde öğeyi bulun.</span><span class="sxs-lookup"><span data-stu-id="4c032-187">The following example instead uses the <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> method quickly find an item by key.</span></span>  
  
```csharp  
private static void FindInDictionary2(string symbol)  
{  
    Dictionary<string, Element> elements = BuildDictionary();  
  
    Element theElement = null;  
    if (elements.TryGetValue(symbol, out theElement) == false)  
        Console.WriteLine(symbol + " not found");  
    else  
        Console.WriteLine("found: " + theElement.Name);  
}  
```  

<a name="BKMK_LINQ"></a>
## <a name="using-linq-to-access-a-collection"></a><span data-ttu-id="4c032-188">Koleksiyona erişmek için LINQ kullanma</span><span class="sxs-lookup"><span data-stu-id="4c032-188">Using LINQ to Access a Collection</span></span>  
 <span data-ttu-id="4c032-189">LINQ (dil ile tümleşik sorgu) koleksiyonlara erişmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4c032-189">LINQ (Language-Integrated Query) can be used to access collections.</span></span> <span data-ttu-id="4c032-190">LINQ sorguları filtreleme, sıralama ve Gruplama yetenekler sağlar.</span><span class="sxs-lookup"><span data-stu-id="4c032-190">LINQ queries provide filtering, ordering, and grouping capabilities.</span></span> <span data-ttu-id="4c032-191">Daha fazla bilgi için [C# üzerinde LINQ ile çalışmaya başlama](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="4c032-191">For more information, see  [Getting Started with LINQ in C#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md).</span></span>  
  
 <span data-ttu-id="4c032-192">Aşağıdaki örnek, bir genel LINQ sorgusu çalıştırır `List`.</span><span class="sxs-lookup"><span data-stu-id="4c032-192">The following example runs a LINQ query against a generic `List`.</span></span> <span data-ttu-id="4c032-193">LINQ sorgusu sonuçları içeren farklı bir koleksiyon döndürür.</span><span class="sxs-lookup"><span data-stu-id="4c032-193">The LINQ query returns a different collection that contains the results.</span></span>  
  
```csharp  
private static void ShowLINQ()  
{  
    List<Element> elements = BuildList();  
  
    // LINQ Query.  
    var subset = from theElement in elements  
                 where theElement.AtomicNumber < 22  
                 orderby theElement.Name  
                 select theElement;  
  
    foreach (Element theElement in subset)  
    {  
        Console.WriteLine(theElement.Name + " " + theElement.AtomicNumber);  
    }  
  
    // Output:  
    //  Calcium 20  
    //  Potassium 19  
    //  Scandium 21  
}  
  
private static List<Element> BuildList()  
{  
    return new List<Element>  
    {  
        { new Element() { Symbol="K", Name="Potassium", AtomicNumber=19}},  
        { new Element() { Symbol="Ca", Name="Calcium", AtomicNumber=20}},  
        { new Element() { Symbol="Sc", Name="Scandium", AtomicNumber=21}},  
        { new Element() { Symbol="Ti", Name="Titanium", AtomicNumber=22}}  
    };  
}  
  
public class Element  
{  
    public string Symbol { get; set; }  
    public string Name { get; set; }  
    public int AtomicNumber { get; set; }  
}  
```  

<a name="BKMK_Sorting"></a>
## <a name="sorting-a-collection"></a><span data-ttu-id="4c032-194">Koleksiyonda sıralama</span><span class="sxs-lookup"><span data-stu-id="4c032-194">Sorting a Collection</span></span>  
 <span data-ttu-id="4c032-195">Aşağıdaki örnek bir koleksiyonu sıralamak için bir yordam gösterir.</span><span class="sxs-lookup"><span data-stu-id="4c032-195">The following example illustrates a procedure for sorting a collection.</span></span> <span data-ttu-id="4c032-196">Örnek örneklerini sıralar `Car` depolanan sınıfı bir <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="4c032-196">The example sorts instances of the `Car` class that are stored in a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="4c032-197">`Car` Sınıfının Implements <xref:System.IComparable%601> gerektiren arabirimi <xref:System.IComparable%601.CompareTo%2A> yönteminin uygulanmasını.</span><span class="sxs-lookup"><span data-stu-id="4c032-197">The `Car` class implements the <xref:System.IComparable%601> interface, which requires that the <xref:System.IComparable%601.CompareTo%2A> method be implemented.</span></span>  
  
 <span data-ttu-id="4c032-198">Her çağrı <xref:System.IComparable%601.CompareTo%2A> yöntemi sıralama için kullanılan tek bir karşılaştırma yapar.</span><span class="sxs-lookup"><span data-stu-id="4c032-198">Each call to the <xref:System.IComparable%601.CompareTo%2A> method makes a single comparison that is used for sorting.</span></span> <span data-ttu-id="4c032-199">Kullanıcı tarafından yazılan kodu `CompareTo` geçerli nesnenin başka bir nesneyle her karşılaştırılışında bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="4c032-199">User-written code in the `CompareTo` method returns a value for each comparison of the current object with another object.</span></span> <span data-ttu-id="4c032-200">Döndürülen değer daha az nesne geçerli nesneye sıfırdan küçük nesnesine, geçerli nesne diğer nesneden büyükse sıfır ve sıfır büyüktür eşit olmaları durumunda.</span><span class="sxs-lookup"><span data-stu-id="4c032-200">The value returned is less than zero if the current object is less than the other object, greater than zero if the current object is greater than the other object, and zero if they are equal.</span></span> <span data-ttu-id="4c032-201">Bu, kodda büyüktür, küçüktür ölçütleri tanımlayın ve eşit sağlar.</span><span class="sxs-lookup"><span data-stu-id="4c032-201">This enables you to define in code the criteria for greater than, less than, and equal.</span></span>  
  
 <span data-ttu-id="4c032-202">İçinde `ListCars` yöntemi `cars.Sort()` deyimi listeyi sıralar.</span><span class="sxs-lookup"><span data-stu-id="4c032-202">In the `ListCars` method, the `cars.Sort()` statement sorts the list.</span></span> <span data-ttu-id="4c032-203">Bu çağrıyı <xref:System.Collections.Generic.List%601.Sort%2A> yöntemi <xref:System.Collections.Generic.List%601> neden `CompareTo` otomatik olarak çağrılmasına yöntemi `Car` nesneler `List`.</span><span class="sxs-lookup"><span data-stu-id="4c032-203">This call to the <xref:System.Collections.Generic.List%601.Sort%2A> method of the <xref:System.Collections.Generic.List%601> causes the `CompareTo` method to be called automatically for the `Car` objects in the `List`.</span></span>  
  
```csharp  
private static void ListCars()  
{  
    var cars = new List<Car>  
    {  
        { new Car() { Name = "car1", Color = "blue", Speed = 20}},  
        { new Car() { Name = "car2", Color = "red", Speed = 50}},  
        { new Car() { Name = "car3", Color = "green", Speed = 10}},  
        { new Car() { Name = "car4", Color = "blue", Speed = 50}},  
        { new Car() { Name = "car5", Color = "blue", Speed = 30}},  
        { new Car() { Name = "car6", Color = "red", Speed = 60}},  
        { new Car() { Name = "car7", Color = "green", Speed = 50}}  
    };  
  
    // Sort the cars by color alphabetically, and then by speed  
    // in descending order.  
    cars.Sort();  
  
    // View all of the cars.  
    foreach (Car thisCar in cars)  
    {  
        Console.Write(thisCar.Color.PadRight(5) + " ");  
        Console.Write(thisCar.Speed.ToString() + " ");  
        Console.Write(thisCar.Name);  
        Console.WriteLine();  
    }  
  
    // Output:  
    //  blue  50 car4  
    //  blue  30 car5  
    //  blue  20 car1  
    //  green 50 car7  
    //  green 10 car3  
    //  red   60 car6  
    //  red   50 car2  
}  
  
public class Car : IComparable<Car>  
{  
    public string Name { get; set; }  
    public int Speed { get; set; }  
    public string Color { get; set; }  
  
    public int CompareTo(Car other)  
    {  
        // A call to this method makes a single comparison that is  
        // used for sorting.  
  
        // Determine the relative order of the objects being compared.  
        // Sort by color alphabetically, and then by speed in  
        // descending order.  
  
        // Compare the colors.  
        int compare;  
        compare = String.Compare(this.Color, other.Color, true);  
  
        // If the colors are the same, compare the speeds.  
        if (compare == 0)  
        {  
            compare = this.Speed.CompareTo(other.Speed);  
  
            // Use descending order for speed.  
            compare = -compare;  
        }  
  
        return compare;  
    }  
}  
```  
  
<a name="BKMK_CustomCollection"></a>
## <a name="defining-a-custom-collection"></a><span data-ttu-id="4c032-204">Özel koleksiyonu tanımlama</span><span class="sxs-lookup"><span data-stu-id="4c032-204">Defining a Custom Collection</span></span>  
 <span data-ttu-id="4c032-205">Uygulayarak bir koleksiyon tanımlayabilirsiniz <xref:System.Collections.Generic.IEnumerable%601> veya <xref:System.Collections.IEnumerable> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="4c032-205">You can define a collection by implementing the <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.IEnumerable> interface.</span></span>  
  
 <span data-ttu-id="4c032-206">Bir özel koleksiyon tanımlayabilirsiniz, bunun yerine açıklanan .NET Framework içinde yer koleksiyonların kullanılması daha iyi [tür, koleksiyonları](#BKMK_KindsOfCollections) bu konuda daha önce.</span><span class="sxs-lookup"><span data-stu-id="4c032-206">Although you can define a custom collection, it is usually better to instead use the collections that are included in the .NET Framework, which are described in [Kinds of Collections](#BKMK_KindsOfCollections) earlier in this topic.</span></span>  
  
 <span data-ttu-id="4c032-207">Aşağıdaki örnekte adlı bir özel koleksiyon tanımlar `AllColors`.</span><span class="sxs-lookup"><span data-stu-id="4c032-207">The following example defines a custom collection class named `AllColors`.</span></span> <span data-ttu-id="4c032-208">Bu sınıfın uyguladığı <xref:System.Collections.IEnumerable> gerektiren arabirimi <xref:System.Collections.IEnumerable.GetEnumerator%2A> yönteminin uygulanmasını.</span><span class="sxs-lookup"><span data-stu-id="4c032-208">This class implements the <xref:System.Collections.IEnumerable> interface, which requires that the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method be implemented.</span></span>  
  
 <span data-ttu-id="4c032-209">`GetEnumerator` Yöntemi kendinin bir örneğini döndürür `ColorEnumerator` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="4c032-209">The `GetEnumerator` method returns an instance of the `ColorEnumerator` class.</span></span> <span data-ttu-id="4c032-210">`ColorEnumerator` uygulayan <xref:System.Collections.IEnumerator> gerektiren arabirimi <xref:System.Collections.IEnumerator.Current%2A> özelliği <xref:System.Collections.IEnumerator.MoveNext%2A> yöntemi ve <xref:System.Collections.IEnumerator.Reset%2A> yönteminin uygulanmasını.</span><span class="sxs-lookup"><span data-stu-id="4c032-210">`ColorEnumerator` implements the <xref:System.Collections.IEnumerator> interface, which requires that the <xref:System.Collections.IEnumerator.Current%2A> property, <xref:System.Collections.IEnumerator.MoveNext%2A> method, and <xref:System.Collections.IEnumerator.Reset%2A> method be implemented.</span></span>  
  
```csharp  
private static void ListColors()  
{  
    var colors = new AllColors();  
  
    foreach (Color theColor in colors)  
    {  
        Console.Write(theColor.Name + " ");  
    }  
    Console.WriteLine();  
    // Output: red blue green  
}  
  
// Collection class.  
public class AllColors : System.Collections.IEnumerable  
{  
    Color[] _colors =  
    {  
        new Color() { Name = "red" },  
        new Color() { Name = "blue" },  
        new Color() { Name = "green" }  
    };  
  
    public System.Collections.IEnumerator GetEnumerator()  
    {  
        return new ColorEnumerator(_colors);  
  
        // Instead of creating a custom enumerator, you could  
        // use the GetEnumerator of the array.  
        //return _colors.GetEnumerator();  
    }  
  
    // Custom enumerator.  
    private class ColorEnumerator : System.Collections.IEnumerator  
    {  
        private Color[] _colors;  
        private int _position = -1;  
  
        public ColorEnumerator(Color[] colors)  
        {  
            _colors = colors;  
        }  
  
        object System.Collections.IEnumerator.Current  
        {  
            get  
            {  
                return _colors[_position];  
            }  
        }  
  
        bool System.Collections.IEnumerator.MoveNext()  
        {  
            _position++;  
            return (_position < _colors.Length);  
        }  
  
        void System.Collections.IEnumerator.Reset()  
        {  
            _position = -1;  
        }  
    }  
}  
  
// Element class.  
public class Color  
{  
    public string Name { get; set; }  
}  
```  

<a name="BKMK_Iterators"></a> 
##  <a name="iterators"></a><span data-ttu-id="4c032-211">Yineleyiciler</span><span class="sxs-lookup"><span data-stu-id="4c032-211">Iterators</span></span>  
 <span data-ttu-id="4c032-212">Bir *yineleyici* bir koleksiyon üzerinde özel yineleme yapmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4c032-212">An *iterator* is used to perform a custom iteration over a collection.</span></span> <span data-ttu-id="4c032-213">Bir yineleyiciyi bir yöntem olabilir veya bir `get` erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="4c032-213">An iterator can be a method or a `get` accessor.</span></span> <span data-ttu-id="4c032-214">Yineleyici bir [yield return](../../../csharp/language-reference/keywords/yield.md) deyimini her öğesini birer birer koleksiyonunun bir döndürür.</span><span class="sxs-lookup"><span data-stu-id="4c032-214">An iterator uses a [yield return](../../../csharp/language-reference/keywords/yield.md) statement to return each element of the collection one at a time.</span></span>  
  
 <span data-ttu-id="4c032-215">Kullanarak bir yineleyici çağırabilirsiniz bir [foreach](../../../csharp/language-reference/keywords/foreach-in.md) deyimi.</span><span class="sxs-lookup"><span data-stu-id="4c032-215">You call an iterator by using a [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement.</span></span> <span data-ttu-id="4c032-216">Her bir yinelemesini `foreach` döngü yineleyiciyi çağırır.</span><span class="sxs-lookup"><span data-stu-id="4c032-216">Each iteration of the `foreach` loop calls the iterator.</span></span> <span data-ttu-id="4c032-217">Olduğunda bir `yield return` yineleyicisi deyimine ulaşıldığında, bir ifade döndürülür ve kodun geçerli konumu korunur.</span><span class="sxs-lookup"><span data-stu-id="4c032-217">When a `yield return` statement is reached in the iterator, an expression is returned, and the current location in code is retained.</span></span> <span data-ttu-id="4c032-218">Yürütme, yineleyicinin bir sonraki açışınızda bu konumdan başlatılır.</span><span class="sxs-lookup"><span data-stu-id="4c032-218">Execution is restarted from that location the next time that the iterator is called.</span></span>  
  
 <span data-ttu-id="4c032-219">Daha fazla bilgi için [yineleyiciler (C#)](../../../csharp/programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="4c032-219">For more information, see [Iterators (C#)](../../../csharp/programming-guide/concepts/iterators.md).</span></span>  
  
 <span data-ttu-id="4c032-220">Aşağıdaki örnek yineleyici yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="4c032-220">The following example uses an iterator method.</span></span> <span data-ttu-id="4c032-221">Yineleyici yöntem, bir `yield return` içindeki bir [için](../../../csharp/language-reference/keywords/for.md) döngü.</span><span class="sxs-lookup"><span data-stu-id="4c032-221">The iterator method has a `yield return` statement that is inside a [for](../../../csharp/language-reference/keywords/for.md) loop.</span></span> <span data-ttu-id="4c032-222">İçinde `ListEvenNumbers` yöntemi, her bir yinelemesini `foreach` diğerine geçer yineleyici yöntem için bir çağrı oluşturur ve deyim gövdesi `yield return` deyimi.</span><span class="sxs-lookup"><span data-stu-id="4c032-222">In the `ListEvenNumbers` method, each iteration of the `foreach` statement body creates a call to the iterator method, which proceeds to the next `yield return` statement.</span></span>  
  
```csharp  
private static void ListEvenNumbers()  
{  
    foreach (int number in EvenSequence(5, 18))  
    {  
        Console.Write(number.ToString() + " ");  
    }  
    Console.WriteLine();  
    // Output: 6 8 10 12 14 16 18  
}  
  
private static IEnumerable<int> EvenSequence(  
    int firstNumber, int lastNumber)  
{  
    // Yield even numbers in the range.  
    for (var number = firstNumber; number <= lastNumber; number++)  
    {  
        if (number % 2 == 0)  
        {  
            yield return number;  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="4c032-223">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4c032-223">See Also</span></span>

- [<span data-ttu-id="4c032-224">Nesne ve Koleksiyon Başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="4c032-224">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
- [<span data-ttu-id="4c032-225">Programlama Kavramları (C#)</span><span class="sxs-lookup"><span data-stu-id="4c032-225">Programming Concepts (C#)</span></span>](../../../csharp/programming-guide/concepts/index.md)  
- [<span data-ttu-id="4c032-226">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="4c032-226">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
- [<span data-ttu-id="4c032-227">LINQ to Objects'in (C#)</span><span class="sxs-lookup"><span data-stu-id="4c032-227">LINQ to Objects (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
- [<span data-ttu-id="4c032-228">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="4c032-228">Parallel LINQ (PLINQ)</span></span>](../../../standard/parallel-programming/parallel-linq-plinq.md)  
- [<span data-ttu-id="4c032-229">Koleksiyonlar ve Veri Yapıları</span><span class="sxs-lookup"><span data-stu-id="4c032-229">Collections and Data Structures</span></span>](../../../standard/collections/index.md)  
- [<span data-ttu-id="4c032-230">Koleksiyon oluşturma ve düzenleme</span><span class="sxs-lookup"><span data-stu-id="4c032-230">Creating and Manipulating Collections</span></span>](https://msdn.microsoft.com/library/2065398e-eb1a-4821-9188-75f16e42e069)  
- [<span data-ttu-id="4c032-231">Koleksiyon Sınıfı Seçme</span><span class="sxs-lookup"><span data-stu-id="4c032-231">Selecting a Collection Class</span></span>](../../../standard/collections/selecting-a-collection-class.md)  
- [<span data-ttu-id="4c032-232">Koleksiyonlardaki Karşılaştırmalar ve Sıralamalar</span><span class="sxs-lookup"><span data-stu-id="4c032-232">Comparisons and Sorts Within Collections</span></span>](../../../standard/collections/comparisons-and-sorts-within-collections.md)  
- [<span data-ttu-id="4c032-233">Genel Koleksiyonlar Ne Zaman Kullanılır?</span><span class="sxs-lookup"><span data-stu-id="4c032-233">When to Use Generic Collections</span></span>](../../../standard/collections/when-to-use-generic-collections.md)  
