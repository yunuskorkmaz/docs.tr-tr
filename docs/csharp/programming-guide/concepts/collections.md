---
title: Koleksiyonlar (C#)
ms.date: 07/20/2015
ms.assetid: 317d7dc3-8587-4873-8b3e-556f86497939
ms.openlocfilehash: a560155b936aef7a4a346d39eaed75e0a85c1a73
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169889"
---
# <a name="collections-c"></a><span data-ttu-id="e293c-102">Koleksiyonlar (C#)</span><span class="sxs-lookup"><span data-stu-id="e293c-102">Collections (C#)</span></span>

<span data-ttu-id="e293c-103">Birçok uygulama için, ilgili nesnelerin grupları oluşturmak ve yönetmek istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="e293c-103">For many applications, you want to create and manage groups of related objects.</span></span> <span data-ttu-id="e293c-104">Nesneleri gruplandırmanın iki yolu vardır: nesne dizileri oluşturarak ve nesnelerin koleksiyonlarını oluşturarak.</span><span class="sxs-lookup"><span data-stu-id="e293c-104">There are two ways to group objects: by creating arrays of objects, and by creating collections of objects.</span></span>

<span data-ttu-id="e293c-105">Diziler, güçlü bir şekilde yazılan sabit sayıda nesne oluşturmak ve bunlarla çalışmak için en kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="e293c-105">Arrays are most useful for creating and working with a fixed number of strongly-typed objects.</span></span> <span data-ttu-id="e293c-106">Diziler hakkında daha fazla bilgi için [Diziler'e](../arrays/index.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="e293c-106">For information about arrays, see [Arrays](../arrays/index.md).</span></span>

<span data-ttu-id="e293c-107">Koleksiyonlar, nesne gruplarıyla çalışmak için daha esnek bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="e293c-107">Collections provide a more flexible way to work with groups of objects.</span></span> <span data-ttu-id="e293c-108">Dizilerin aksine, birlikte çalıştığınız nesne grubu, uygulamanın gereksinimleri değiştikçe dinamik olarak büyüyebilir ve küçülebilir.</span><span class="sxs-lookup"><span data-stu-id="e293c-108">Unlike arrays, the group of objects you work with can grow and shrink dynamically as the needs of the application change.</span></span> <span data-ttu-id="e293c-109">Bazı koleksiyonlar için, anahtarı kullanarak nesneyi hızla alabilmeniz için koleksiyona koyduğunuz herhangi bir nesneye bir anahtar atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e293c-109">For some collections, you can assign a key to any object that you put into the collection so that you can quickly retrieve the object by using the key.</span></span>

<span data-ttu-id="e293c-110">Koleksiyon bir sınıftır, bu nedenle bu koleksiyona öğe eklemeden önce sınıfın bir örneğini bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e293c-110">A collection is a class, so you must declare an instance of the class before you can add elements to that collection.</span></span>

<span data-ttu-id="e293c-111">Koleksiyonunuz yalnızca bir veri türüöğeleri içeriyorsa, <xref:System.Collections.Generic?displayProperty=nameWithType> ad alanındaki sınıflardan birini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e293c-111">If your collection contains elements of only one data type, you can use one of the classes in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="e293c-112">Genel bir koleksiyon, türü başka bir veri türünün eklenmeyecek şekilde tür güvenliğini zorlar.</span><span class="sxs-lookup"><span data-stu-id="e293c-112">A generic collection enforces type safety so that no other data type can be added to it.</span></span> <span data-ttu-id="e293c-113">Genel bir koleksiyondan bir öğe aldığınızda, öğe türünü belirlemeniz veya dönüştürmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="e293c-113">When you retrieve an element from a generic collection, you do not have to determine its data type or convert it.</span></span>

> [!NOTE]
> <span data-ttu-id="e293c-114">Bu konudaki örnekler için, ve `System.Linq` ad `System.Collections.Generic` alanları için yönergeleri [niçin kullanma](../../language-reference/keywords/using-directive.md) içerir.</span><span class="sxs-lookup"><span data-stu-id="e293c-114">For the examples in this topic, include [using](../../language-reference/keywords/using-directive.md) directives for the `System.Collections.Generic` and `System.Linq` namespaces.</span></span>

 <span data-ttu-id="e293c-115">**Bu konuda**</span><span class="sxs-lookup"><span data-stu-id="e293c-115">**In this topic**</span></span>

- [<span data-ttu-id="e293c-116">Basit Bir Koleksiyon Kullanma</span><span class="sxs-lookup"><span data-stu-id="e293c-116">Using a Simple Collection</span></span>](#BKMK_SimpleCollection)

- [<span data-ttu-id="e293c-117">Koleksiyon Çeşitleri</span><span class="sxs-lookup"><span data-stu-id="e293c-117">Kinds of Collections</span></span>](#BKMK_KindsOfCollections)

  - [<span data-ttu-id="e293c-118">System.Collections.Generic Sınıflar</span><span class="sxs-lookup"><span data-stu-id="e293c-118">System.Collections.Generic Classes</span></span>](#BKMK_Generic)

  - [<span data-ttu-id="e293c-119">System.Collections.Eşzamanlı Sınıflar</span><span class="sxs-lookup"><span data-stu-id="e293c-119">System.Collections.Concurrent Classes</span></span>](#BKMK_Concurrent)

  - [<span data-ttu-id="e293c-120">System.Collections Sınıfları</span><span class="sxs-lookup"><span data-stu-id="e293c-120">System.Collections Classes</span></span>](#BKMK_Collections)

- [<span data-ttu-id="e293c-121">Anahtar/Değer Çiftleri Koleksiyonunu Uygulama</span><span class="sxs-lookup"><span data-stu-id="e293c-121">Implementing a Collection of Key/Value Pairs</span></span>](#BKMK_KeyValuePairs)

- [<span data-ttu-id="e293c-122">Koleksiyona Erişmek için LINQ kullanma</span><span class="sxs-lookup"><span data-stu-id="e293c-122">Using LINQ to Access a Collection</span></span>](#BKMK_LINQ)

- [<span data-ttu-id="e293c-123">Koleksiyonu Sıralama</span><span class="sxs-lookup"><span data-stu-id="e293c-123">Sorting a Collection</span></span>](#BKMK_Sorting)

- [<span data-ttu-id="e293c-124">Özel Koleksiyon Tanımlama</span><span class="sxs-lookup"><span data-stu-id="e293c-124">Defining a Custom Collection</span></span>](#BKMK_CustomCollection)

- [<span data-ttu-id="e293c-125">Yineleyiciler</span><span class="sxs-lookup"><span data-stu-id="e293c-125">Iterators</span></span>](#BKMK_Iterators)

<a name="BKMK_SimpleCollection"></a>

## <a name="using-a-simple-collection"></a><span data-ttu-id="e293c-126">Basit Bir Koleksiyon Kullanma</span><span class="sxs-lookup"><span data-stu-id="e293c-126">Using a Simple Collection</span></span>

<span data-ttu-id="e293c-127">Bu bölümdeki örnekler, <xref:System.Collections.Generic.List%601> güçlü bir şekilde yazılan nesneler listesiyle çalışmanızı sağlayan genel sınıfı kullanır.</span><span class="sxs-lookup"><span data-stu-id="e293c-127">The examples in this section use the generic <xref:System.Collections.Generic.List%601> class, which enables you to work with a strongly typed list of objects.</span></span>

<span data-ttu-id="e293c-128">Aşağıdaki örnek, dizeleri bir listesini oluşturur ve sonra [foreach](../../language-reference/keywords/foreach-in.md) deyimi kullanarak dizeleri ile yineler.</span><span class="sxs-lookup"><span data-stu-id="e293c-128">The following example creates a list of strings and then iterates through the strings by using a [foreach](../../language-reference/keywords/foreach-in.md) statement.</span></span>

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

<span data-ttu-id="e293c-129">Bir koleksiyonun içeriği önceden biliniyorsa, koleksiyonun başlatılması için bir *koleksiyon başlatılması* nı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e293c-129">If the contents of a collection are known in advance, you can use a *collection initializer* to initialize the collection.</span></span> <span data-ttu-id="e293c-130">Daha fazla bilgi için [Object ve Collection Initializers'a](../classes-and-structs/object-and-collection-initializers.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="e293c-130">For more information, see [Object and Collection Initializers](../classes-and-structs/object-and-collection-initializers.md).</span></span>

<span data-ttu-id="e293c-131">Aşağıdaki örnek, koleksiyona öğe eklemek için bir koleksiyon başlatılması nın kullanılması dışında, önceki örnekle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="e293c-131">The following example is the same as the previous example, except a collection initializer is used to add elements to the collection.</span></span>

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

<span data-ttu-id="e293c-132">[Bir](../../language-reference/keywords/for.md) koleksiyon aracılığıyla yinelemek `foreach` için deyim yerine for deyimi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e293c-132">You can use a [for](../../language-reference/keywords/for.md) statement instead of a `foreach` statement to iterate through a collection.</span></span> <span data-ttu-id="e293c-133">Bunu dizin konumuna göre koleksiyon öğelerine erişerek gerçekleştirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e293c-133">You accomplish this by accessing the collection elements by the index position.</span></span> <span data-ttu-id="e293c-134">Elementlerin dizini 0 ile başlar ve eksi 1 öğe sayısıyla biter.</span><span class="sxs-lookup"><span data-stu-id="e293c-134">The index of the elements starts at 0 and ends at the element count minus 1.</span></span>

<span data-ttu-id="e293c-135">Aşağıdaki örnek, bir koleksiyonun öğelerini yerine `for` kullanarak `foreach`yineler.</span><span class="sxs-lookup"><span data-stu-id="e293c-135">The following example iterates through the elements of a collection by using `for` instead of `foreach`.</span></span>

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

<span data-ttu-id="e293c-136">Aşağıdaki örnek, kaldırılacak nesneyi belirterek bir öğeyi koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="e293c-136">The following example removes an element from the collection by specifying the object to remove.</span></span>

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

<span data-ttu-id="e293c-137">Aşağıdaki örnek, öğeleri genel bir listeden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="e293c-137">The following example removes elements from a generic list.</span></span> <span data-ttu-id="e293c-138">Bir `foreach` deyim yerine, azalan sırada yineleyen [bir](../../language-reference/keywords/for.md) ifade kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e293c-138">Instead of a `foreach` statement, a [for](../../language-reference/keywords/for.md) statement that iterates in descending order is used.</span></span> <span data-ttu-id="e293c-139">Bunun nedeni, <xref:System.Collections.Generic.List%601.RemoveAt%2A> yöntemin kaldırılan öğeden sonraki öğelerin daha düşük bir dizin değerine sahip olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="e293c-139">This is because the <xref:System.Collections.Generic.List%601.RemoveAt%2A> method causes elements after a removed element to have a lower index value.</span></span>

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

<span data-ttu-id="e293c-140">Öğelerin türü <xref:System.Collections.Generic.List%601>için, kendi sınıf tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e293c-140">For the type of elements in the <xref:System.Collections.Generic.List%601>, you can also define your own class.</span></span> <span data-ttu-id="e293c-141">Aşağıdaki örnekte, `Galaxy` kodda <xref:System.Collections.Generic.List%601> kullanılan sınıf tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="e293c-141">In the following example, the `Galaxy` class that is used by the <xref:System.Collections.Generic.List%601> is defined in the code.</span></span>

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

## <a name="kinds-of-collections"></a><span data-ttu-id="e293c-142">Koleksiyon Çeşitleri</span><span class="sxs-lookup"><span data-stu-id="e293c-142">Kinds of Collections</span></span>

<span data-ttu-id="e293c-143">Birçok ortak koleksiyon .NET Framework tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="e293c-143">Many common collections are provided by the .NET Framework.</span></span> <span data-ttu-id="e293c-144">Her koleksiyon türü belirli bir amaç için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e293c-144">Each type of collection is designed for a specific purpose.</span></span>

<span data-ttu-id="e293c-145">Ortak toplama sınıflarından bazıları bu bölümde açıklanmıştır:</span><span class="sxs-lookup"><span data-stu-id="e293c-145">Some of the common collection classes are described in this section:</span></span>

- <span data-ttu-id="e293c-146"><xref:System.Collections.Generic> sınıflar</span><span class="sxs-lookup"><span data-stu-id="e293c-146"><xref:System.Collections.Generic> classes</span></span>

- <span data-ttu-id="e293c-147"><xref:System.Collections.Concurrent> sınıflar</span><span class="sxs-lookup"><span data-stu-id="e293c-147"><xref:System.Collections.Concurrent> classes</span></span>

- <span data-ttu-id="e293c-148"><xref:System.Collections> sınıflar</span><span class="sxs-lookup"><span data-stu-id="e293c-148"><xref:System.Collections> classes</span></span>

<a name="BKMK_Generic"></a>

### <a name="systemcollectionsgeneric-classes"></a><span data-ttu-id="e293c-149">System.Collections.Generic Sınıflar</span><span class="sxs-lookup"><span data-stu-id="e293c-149">System.Collections.Generic Classes</span></span>

<span data-ttu-id="e293c-150"><xref:System.Collections.Generic> Ad alanındaki sınıflardan birini kullanarak genel bir koleksiyon oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e293c-150">You can create a generic collection by using one of the classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="e293c-151">Genel bir koleksiyon, koleksiyondaki her öğe aynı veri türüne sahipse yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="e293c-151">A generic collection is useful when every item in the collection has the same data type.</span></span> <span data-ttu-id="e293c-152">Genel bir koleksiyon, yalnızca istenen veri türünün eklenmesine izin vererek güçlü yazmayı zorlar.</span><span class="sxs-lookup"><span data-stu-id="e293c-152">A generic collection enforces strong typing by allowing only the desired data type to be added.</span></span>

<span data-ttu-id="e293c-153">Aşağıdaki tabloda ad alanının sık kullanılan <xref:System.Collections.Generic?displayProperty=nameWithType> sınıflarından bazıları listelenebvardır:</span><span class="sxs-lookup"><span data-stu-id="e293c-153">The following table lists some of the frequently used classes of the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace:</span></span>

|<span data-ttu-id="e293c-154">Sınıf</span><span class="sxs-lookup"><span data-stu-id="e293c-154">Class</span></span>|<span data-ttu-id="e293c-155">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e293c-155">Description</span></span>|
|---|---|
|<xref:System.Collections.Generic.Dictionary%602>|<span data-ttu-id="e293c-156">Anahtara göre düzenlenmiş anahtar/değer çiftleri koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e293c-156">Represents a collection of key/value pairs that are organized based on the key.</span></span>|
|<xref:System.Collections.Generic.List%601>|<span data-ttu-id="e293c-157">Dizin tarafından erişilebilen nesnelerin listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e293c-157">Represents a list of objects that can be accessed by index.</span></span> <span data-ttu-id="e293c-158">Listeleri aramak, sıralamak ve değiştirmek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e293c-158">Provides methods to search, sort, and modify lists.</span></span>|
|<xref:System.Collections.Generic.Queue%601>|<span data-ttu-id="e293c-159">Nesnelerin ilk, ilk çıkan (FIFO) koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e293c-159">Represents a first in, first out (FIFO) collection of objects.</span></span>|
|<xref:System.Collections.Generic.SortedList%602>|<span data-ttu-id="e293c-160">İlişkili <xref:System.Collections.Generic.IComparer%601> uygulamaya göre anahtara göre sıralanmış anahtar/değer çiftleri koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e293c-160">Represents a collection of key/value pairs that are sorted by key based on the associated <xref:System.Collections.Generic.IComparer%601> implementation.</span></span>|
|<xref:System.Collections.Generic.Stack%601>|<span data-ttu-id="e293c-161">Nesnelerin son, ilk çıkan (LIFO) koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e293c-161">Represents a last in, first out (LIFO) collection of objects.</span></span>|

<span data-ttu-id="e293c-162">Ek bilgi için, [Sık Kullanılan Koleksiyon Türleri](../../../standard/collections/commonly-used-collection-types.md), Toplama Sınıfı [Seçme](../../../standard/collections/selecting-a-collection-class.md)ve <xref:System.Collections.Generic>.</span><span class="sxs-lookup"><span data-stu-id="e293c-162">For additional information, see [Commonly Used Collection Types](../../../standard/collections/commonly-used-collection-types.md), [Selecting a Collection Class](../../../standard/collections/selecting-a-collection-class.md), and <xref:System.Collections.Generic>.</span></span>

<a name="BKMK_Concurrent"></a>

### <a name="systemcollectionsconcurrent-classes"></a><span data-ttu-id="e293c-163">System.Collections.Eşzamanlı Sınıflar</span><span class="sxs-lookup"><span data-stu-id="e293c-163">System.Collections.Concurrent Classes</span></span>

<span data-ttu-id="e293c-164">.NET Framework 4 veya daha yeni, <xref:System.Collections.Concurrent> ad alanındaki koleksiyonlar, birden çok iş parçacığından koleksiyon öğelerine erişmek için verimli iş parçacığı güvenli işlemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e293c-164">In the .NET Framework 4 or newer, the collections in the <xref:System.Collections.Concurrent> namespace provide efficient thread-safe operations for accessing collection items from multiple threads.</span></span>

<span data-ttu-id="e293c-165"><xref:System.Collections.Concurrent> Birden çok iş parçacığı aynı anda koleksiyona <xref:System.Collections.Generic?displayProperty=nameWithType> erişirken ad alanında ve <xref:System.Collections?displayProperty=nameWithType> ad alanlarındaki karşılık gelen türler yerine ad alanındaki sınıflar kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e293c-165">The classes in the <xref:System.Collections.Concurrent> namespace should be used instead of the corresponding types in the <xref:System.Collections.Generic?displayProperty=nameWithType> and <xref:System.Collections?displayProperty=nameWithType> namespaces whenever multiple threads are accessing the collection concurrently.</span></span> <span data-ttu-id="e293c-166">Daha fazla bilgi için İş Parçacığı <xref:System.Collections.Concurrent>Güvenli [Koleksiyonları](../../../standard/collections/thread-safe/index.md) ve .</span><span class="sxs-lookup"><span data-stu-id="e293c-166">For more information, see [Thread-Safe Collections](../../../standard/collections/thread-safe/index.md) and <xref:System.Collections.Concurrent>.</span></span>

<span data-ttu-id="e293c-167"><xref:System.Collections.Concurrent> Ad alanına dahil edilen bazı <xref:System.Collections.Concurrent.BlockingCollection%601> <xref:System.Collections.Concurrent.ConcurrentDictionary%602>sınıflar <xref:System.Collections.Concurrent.ConcurrentQueue%601>, <xref:System.Collections.Concurrent.ConcurrentStack%601>, , ve .</span><span class="sxs-lookup"><span data-stu-id="e293c-167">Some classes included in the <xref:System.Collections.Concurrent> namespace are <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>

<a name="BKMK_Collections"></a>

### <a name="systemcollections-classes"></a><span data-ttu-id="e293c-168">System.Collections Sınıfları</span><span class="sxs-lookup"><span data-stu-id="e293c-168">System.Collections Classes</span></span>

<span data-ttu-id="e293c-169"><xref:System.Collections?displayProperty=nameWithType> Ad alanındaki sınıflar öğeleri özel olarak yazılan nesneler olarak değil, tür `Object`nesneleri olarak depolar.</span><span class="sxs-lookup"><span data-stu-id="e293c-169">The classes in the <xref:System.Collections?displayProperty=nameWithType> namespace do not store elements as specifically typed objects, but as objects of type `Object`.</span></span>

<span data-ttu-id="e293c-170">Mümkün olduğunda, <xref:System.Collections.Generic?displayProperty=nameWithType> <xref:System.Collections.Concurrent> `System.Collections` ad alanındaki eski türler yerine ad alanında veya ad alanında genel koleksiyonları kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e293c-170">Whenever possible, you should use the generic collections in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace or the <xref:System.Collections.Concurrent> namespace instead of the legacy types in the `System.Collections` namespace.</span></span>

<span data-ttu-id="e293c-171">Aşağıdaki tabloda ad alanında sık kullanılan `System.Collections` sınıflardan bazıları listelenemektedir:</span><span class="sxs-lookup"><span data-stu-id="e293c-171">The following table lists some of the frequently used classes in the `System.Collections` namespace:</span></span>

|<span data-ttu-id="e293c-172">Sınıf</span><span class="sxs-lookup"><span data-stu-id="e293c-172">Class</span></span>|<span data-ttu-id="e293c-173">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e293c-173">Description</span></span>|
|---|---|
|<xref:System.Collections.ArrayList>|<span data-ttu-id="e293c-174">Boyutu gerektiği gibi dinamik olarak artırılmış bir nesne dizisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e293c-174">Represents an array of objects whose size is dynamically increased as required.</span></span>|
|<xref:System.Collections.Hashtable>|<span data-ttu-id="e293c-175">Anahtarın karma koduna göre düzenlenen anahtar/değer çiftleri koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e293c-175">Represents a collection of key/value pairs that are organized based on the hash code of the key.</span></span>|
|<xref:System.Collections.Queue>|<span data-ttu-id="e293c-176">Nesnelerin ilk, ilk çıkan (FIFO) koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e293c-176">Represents a first in, first out (FIFO) collection of objects.</span></span>|
|<xref:System.Collections.Stack>|<span data-ttu-id="e293c-177">Nesnelerin son, ilk çıkan (LIFO) koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e293c-177">Represents a last in, first out (LIFO) collection of objects.</span></span>|

<span data-ttu-id="e293c-178">Ad <xref:System.Collections.Specialized> alanı, yalnızca dize koleksiyonları ve bağlantılı liste ve karma sözlükler gibi özel ve güçlü bir şekilde yazılan koleksiyon sınıfları sağlar.</span><span class="sxs-lookup"><span data-stu-id="e293c-178">The <xref:System.Collections.Specialized> namespace provides specialized and strongly typed collection classes, such as string-only collections and linked-list and hybrid dictionaries.</span></span>

<a name="BKMK_KeyValuePairs"></a>

## <a name="implementing-a-collection-of-keyvalue-pairs"></a><span data-ttu-id="e293c-179">Anahtar/Değer Çiftleri Koleksiyonunu Uygulama</span><span class="sxs-lookup"><span data-stu-id="e293c-179">Implementing a Collection of Key/Value Pairs</span></span>

<span data-ttu-id="e293c-180">Genel <xref:System.Collections.Generic.Dictionary%602> koleksiyon, her öğenin anahtarını kullanarak koleksiyondaki öğelere erişmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e293c-180">The <xref:System.Collections.Generic.Dictionary%602> generic collection enables you to access to elements in a collection by using the key of each element.</span></span> <span data-ttu-id="e293c-181">Sözlükteki her ek bir değer ve ilişkili anahtardan oluşur.</span><span class="sxs-lookup"><span data-stu-id="e293c-181">Each addition to the dictionary consists of a value and its associated key.</span></span> <span data-ttu-id="e293c-182">`Dictionary` Sınıf karma tablo olarak uygulandığından, anahtarını kullanarak bir değer almak hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="e293c-182">Retrieving a value by using its key is fast because the `Dictionary` class is implemented as a hash table.</span></span>

<span data-ttu-id="e293c-183">Aşağıdaki örnek bir `Dictionary` koleksiyon oluşturur ve bir `foreach` deyim kullanarak sözlük teyidi.</span><span class="sxs-lookup"><span data-stu-id="e293c-183">The following example creates a `Dictionary` collection and iterates through the dictionary by using a `foreach` statement.</span></span>

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

<span data-ttu-id="e293c-184">Bunun `Dictionary` yerine, koleksiyonu oluşturmak için bir koleksiyon baş `BuildDictionary` harflerini kullanmak için, aşağıdaki yöntemle ve `AddToDictionary` yöntemleri değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e293c-184">To instead use a collection initializer to build the `Dictionary` collection, you can replace the `BuildDictionary` and `AddToDictionary` methods with the following method.</span></span>

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

<span data-ttu-id="e293c-185">Aşağıdaki örnekte, <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> bir <xref:System.Collections.Generic.Dictionary%602.Item%2A> öğeyi `Dictionary` anahtarla hızlı bir şekilde bulmak için yöntem ve özellik kullanır.</span><span class="sxs-lookup"><span data-stu-id="e293c-185">The following example uses the <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> method and the <xref:System.Collections.Generic.Dictionary%602.Item%2A> property of `Dictionary` to quickly find an item by key.</span></span> <span data-ttu-id="e293c-186">Özellik, `Item` `elements` `elements[symbol]` c#'daki öğeyi kullanarak koleksiyondaki bir öğeye erişmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e293c-186">The `Item` property enables you to access an item in the `elements` collection by using the `elements[symbol]` in C#.</span></span>

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

<span data-ttu-id="e293c-187">Aşağıdaki örnek yerine <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> yöntemi hızlı bir şekilde anahtara göre bir öğe bulmak kullanır.</span><span class="sxs-lookup"><span data-stu-id="e293c-187">The following example instead uses the <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> method quickly find an item by key.</span></span>

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

## <a name="using-linq-to-access-a-collection"></a><span data-ttu-id="e293c-188">Koleksiyona Erişmek için LINQ kullanma</span><span class="sxs-lookup"><span data-stu-id="e293c-188">Using LINQ to Access a Collection</span></span>

<span data-ttu-id="e293c-189">LINQ (Dil-Tümleşik Sorgu) koleksiyonlara erişmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e293c-189">LINQ (Language-Integrated Query) can be used to access collections.</span></span> <span data-ttu-id="e293c-190">LINQ sorguları filtreleme, sıralama ve gruplandırma özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="e293c-190">LINQ queries provide filtering, ordering, and grouping capabilities.</span></span> <span data-ttu-id="e293c-191">Daha fazla bilgi için [C# içinde LINQ ile Başlarken'e](linq/index.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="e293c-191">For more information, see [Getting Started with LINQ in C#](linq/index.md).</span></span>

<span data-ttu-id="e293c-192">Aşağıdaki örnek, genel `List`bir karşı bir LINQ sorgusu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e293c-192">The following example runs a LINQ query against a generic `List`.</span></span> <span data-ttu-id="e293c-193">LINQ sorgusu sonuçları içeren farklı bir koleksiyon döndürür.</span><span class="sxs-lookup"><span data-stu-id="e293c-193">The LINQ query returns a different collection that contains the results.</span></span>

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

## <a name="sorting-a-collection"></a><span data-ttu-id="e293c-194">Koleksiyonu Sıralama</span><span class="sxs-lookup"><span data-stu-id="e293c-194">Sorting a Collection</span></span>

<span data-ttu-id="e293c-195">Aşağıdaki örnek, bir koleksiyonu sıralama yordamını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="e293c-195">The following example illustrates a procedure for sorting a collection.</span></span> <span data-ttu-id="e293c-196">Örnek, bir <xref:System.Collections.Generic.List%601>' `Car` de depolanan sınıfın örneklerini sıralar</span><span class="sxs-lookup"><span data-stu-id="e293c-196">The example sorts instances of the `Car` class that are stored in a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="e293c-197">Sınıf, `Car` yöntemin <xref:System.IComparable%601> <xref:System.IComparable%601.CompareTo%2A> uygulanmasını gerektiren arabirimi uygular.</span><span class="sxs-lookup"><span data-stu-id="e293c-197">The `Car` class implements the <xref:System.IComparable%601> interface, which requires that the <xref:System.IComparable%601.CompareTo%2A> method be implemented.</span></span>

<span data-ttu-id="e293c-198">Yönteme <xref:System.IComparable%601.CompareTo%2A> yapılan her çağrı, sıralama için kullanılan tek bir karşılaştırma yapar.</span><span class="sxs-lookup"><span data-stu-id="e293c-198">Each call to the <xref:System.IComparable%601.CompareTo%2A> method makes a single comparison that is used for sorting.</span></span> <span data-ttu-id="e293c-199">`CompareTo` Yöntemdeki kullanıcı tarafından yazılan kod, geçerli nesnenin başka bir nesneyle her karşılaştırılması için bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="e293c-199">User-written code in the `CompareTo` method returns a value for each comparison of the current object with another object.</span></span> <span data-ttu-id="e293c-200">Dönen değer, geçerli nesne diğer nesneden küçükse, geçerli nesne diğer nesneden büyükse sıfırdan büyük, eşitse sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="e293c-200">The value returned is less than zero if the current object is less than the other object, greater than zero if the current object is greater than the other object, and zero if they are equal.</span></span> <span data-ttu-id="e293c-201">Bu, kodda daha büyük, daha az ve eşit ölçütleri tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="e293c-201">This enables you to define in code the criteria for greater than, less than, and equal.</span></span>

<span data-ttu-id="e293c-202">`ListCars` Yöntemde, `cars.Sort()` deyim listeyi sıralar.</span><span class="sxs-lookup"><span data-stu-id="e293c-202">In the `ListCars` method, the `cars.Sort()` statement sorts the list.</span></span> <span data-ttu-id="e293c-203">Bu çağrı <xref:System.Collections.Generic.List%601.Sort%2A> yöntemine <xref:System.Collections.Generic.List%601> neden `CompareTo` olan `Car` yöntemin `List`nesneler için otomatik olarak çağrılması.</span><span class="sxs-lookup"><span data-stu-id="e293c-203">This call to the <xref:System.Collections.Generic.List%601.Sort%2A> method of the <xref:System.Collections.Generic.List%601> causes the `CompareTo` method to be called automatically for the `Car` objects in the `List`.</span></span>

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

## <a name="defining-a-custom-collection"></a><span data-ttu-id="e293c-204">Özel Koleksiyon Tanımlama</span><span class="sxs-lookup"><span data-stu-id="e293c-204">Defining a Custom Collection</span></span>

<span data-ttu-id="e293c-205">Bir koleksiyonu <xref:System.Collections.Generic.IEnumerable%601> veya <xref:System.Collections.IEnumerable> arabirimi uygulayarak tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e293c-205">You can define a collection by implementing the <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.IEnumerable> interface.</span></span>

<span data-ttu-id="e293c-206">Özel bir koleksiyon tanımlayabiliyor olsanız da, bu konunun başlarında [Koleksiyon Türleri'nde](#BKMK_KindsOfCollections) açıklanan .NET Framework'de yer alan koleksiyonları kullanmak genellikle daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="e293c-206">Although you can define a custom collection, it is usually better to instead use the collections that are included in the .NET Framework, which are described in [Kinds of Collections](#BKMK_KindsOfCollections) earlier in this topic.</span></span>

<span data-ttu-id="e293c-207">Aşağıdaki örnek, adlı `AllColors`özel bir koleksiyon sınıfı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e293c-207">The following example defines a custom collection class named `AllColors`.</span></span> <span data-ttu-id="e293c-208">Bu sınıf, <xref:System.Collections.IEnumerable> yöntemin <xref:System.Collections.IEnumerable.GetEnumerator%2A> uygulanmasını gerektiren arabirimi uygular.</span><span class="sxs-lookup"><span data-stu-id="e293c-208">This class implements the <xref:System.Collections.IEnumerable> interface, which requires that the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method be implemented.</span></span>

<span data-ttu-id="e293c-209">Yöntem `GetEnumerator` sınıfın bir örneğini `ColorEnumerator` döndürür.</span><span class="sxs-lookup"><span data-stu-id="e293c-209">The `GetEnumerator` method returns an instance of the `ColorEnumerator` class.</span></span> <span data-ttu-id="e293c-210">`ColorEnumerator`özelliğin, <xref:System.Collections.IEnumerator> <xref:System.Collections.IEnumerator.MoveNext%2A> yöntemin ve <xref:System.Collections.IEnumerator.Reset%2A> <xref:System.Collections.IEnumerator.Current%2A> yöntemin uygulanmasını gerektiren arabirimi uygular.</span><span class="sxs-lookup"><span data-stu-id="e293c-210">`ColorEnumerator` implements the <xref:System.Collections.IEnumerator> interface, which requires that the <xref:System.Collections.IEnumerator.Current%2A> property, <xref:System.Collections.IEnumerator.MoveNext%2A> method, and <xref:System.Collections.IEnumerator.Reset%2A> method be implemented.</span></span>

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

## <a name="iterators"></a><span data-ttu-id="e293c-211">Yineleyiciler</span><span class="sxs-lookup"><span data-stu-id="e293c-211">Iterators</span></span>

<span data-ttu-id="e293c-212">Bir *yineleme,* bir koleksiyon üzerinde özel yineleme gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e293c-212">An *iterator* is used to perform a custom iteration over a collection.</span></span> <span data-ttu-id="e293c-213">Bir yineleyici bir yöntem veya `get` erişimci olabilir.</span><span class="sxs-lookup"><span data-stu-id="e293c-213">An iterator can be a method or a `get` accessor.</span></span> <span data-ttu-id="e293c-214">Bir yineleyici, koleksiyonun her öğesini birer birer döndürmek için [bir verim iade](../../language-reference/keywords/yield.md) deyimi kullanır.</span><span class="sxs-lookup"><span data-stu-id="e293c-214">An iterator uses a [yield return](../../language-reference/keywords/yield.md) statement to return each element of the collection one at a time.</span></span>

<span data-ttu-id="e293c-215">[Her](../../language-reference/keywords/foreach-in.md) bir ifade yi kullanarak bir yineleyici çağırırsınız.</span><span class="sxs-lookup"><span data-stu-id="e293c-215">You call an iterator by using a [foreach](../../language-reference/keywords/foreach-in.md) statement.</span></span> <span data-ttu-id="e293c-216">Döngünün `foreach` her yinelemesi yineleyiciyi çağırır.</span><span class="sxs-lookup"><span data-stu-id="e293c-216">Each iteration of the `foreach` loop calls the iterator.</span></span> <span data-ttu-id="e293c-217">Bir `yield return` deyim yineleyicide ulaşıldığında, bir ifade döndürülür ve koddaki geçerli konum korunur.</span><span class="sxs-lookup"><span data-stu-id="e293c-217">When a `yield return` statement is reached in the iterator, an expression is returned, and the current location in code is retained.</span></span> <span data-ttu-id="e293c-218">Yürütme, yineleyici çağrıldığında bu konumdan yeniden başlatılır.</span><span class="sxs-lookup"><span data-stu-id="e293c-218">Execution is restarted from that location the next time that the iterator is called.</span></span>

<span data-ttu-id="e293c-219">Daha fazla bilgi için [Bkz. Yineleyiciler (C#)](./iterators.md).</span><span class="sxs-lookup"><span data-stu-id="e293c-219">For more information, see [Iterators (C#)](./iterators.md).</span></span>

<span data-ttu-id="e293c-220">Aşağıdaki örnekte bir yineleyici yöntemi kullanır.</span><span class="sxs-lookup"><span data-stu-id="e293c-220">The following example uses an iterator method.</span></span> <span data-ttu-id="e293c-221">Yineleyici yöntemi, [for](../../language-reference/keywords/for.md) `yield return` döngüsü içinde bir deyim vardır.</span><span class="sxs-lookup"><span data-stu-id="e293c-221">The iterator method has a `yield return` statement that is inside a [for](../../language-reference/keywords/for.md) loop.</span></span> <span data-ttu-id="e293c-222">`ListEvenNumbers` Yöntemde, deyim gövdesinin `foreach` her yinelemesi, bir sonraki `yield return` deyime devam eden yineleyici yöntemine bir çağrı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e293c-222">In the `ListEvenNumbers` method, each iteration of the `foreach` statement body creates a call to the iterator method, which proceeds to the next `yield return` statement.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="e293c-223">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e293c-223">See also</span></span>

- [<span data-ttu-id="e293c-224">Nesne ve Koleksiyon Başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="e293c-224">Object and Collection Initializers</span></span>](../classes-and-structs/object-and-collection-initializers.md)
- [<span data-ttu-id="e293c-225">Programlama Kavramları (C#)</span><span class="sxs-lookup"><span data-stu-id="e293c-225">Programming Concepts (C#)</span></span>](./index.md)
- [<span data-ttu-id="e293c-226">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="e293c-226">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="e293c-227">Nesnelere LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="e293c-227">LINQ to Objects (C#)</span></span>](./linq/linq-to-objects.md)
- [<span data-ttu-id="e293c-228">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="e293c-228">Parallel LINQ (PLINQ)</span></span>](../../../standard/parallel-programming/parallel-linq-plinq.md)
- [<span data-ttu-id="e293c-229">Koleksiyonlar ve Veri Yapıları</span><span class="sxs-lookup"><span data-stu-id="e293c-229">Collections and Data Structures</span></span>](../../../standard/collections/index.md)
- [<span data-ttu-id="e293c-230">Koleksiyon Sınıfı Seçme</span><span class="sxs-lookup"><span data-stu-id="e293c-230">Selecting a Collection Class</span></span>](../../../standard/collections/selecting-a-collection-class.md)
- [<span data-ttu-id="e293c-231">Koleksiyonlardaki Karşılaştırmalar ve Sıralamalar</span><span class="sxs-lookup"><span data-stu-id="e293c-231">Comparisons and Sorts Within Collections</span></span>](../../../standard/collections/comparisons-and-sorts-within-collections.md)
- [<span data-ttu-id="e293c-232">Genel Koleksiyonlar Ne Zaman Kullanılır?</span><span class="sxs-lookup"><span data-stu-id="e293c-232">When to Use Generic Collections</span></span>](../../../standard/collections/when-to-use-generic-collections.md)
