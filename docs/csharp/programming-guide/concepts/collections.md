---
title: Koleksiyonlar (C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: get-started-article
ms.assetid: 317d7dc3-8587-4873-8b3e-556f86497939
caps.latest.revision: "6"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4955b3d7048b4dfee23fbcf6eeaed995ebf4f1be
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="collections-c"></a><span data-ttu-id="8e1b9-102">Koleksiyonlar (C#)</span><span class="sxs-lookup"><span data-stu-id="8e1b9-102">Collections (C#)</span></span>
<span data-ttu-id="8e1b9-103">Birçok uygulama için ilgili nesneleri, grupları oluşturmak ve yönetmek istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-103">For many applications, you want to create and manage groups of related objects.</span></span> <span data-ttu-id="8e1b9-104">Grup nesnelerine iki yolu vardır: nesne dizileri oluşturarak ve nesne koleksiyonları oluşturma.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-104">There are two ways to group objects: by creating arrays of objects, and by creating collections of objects.</span></span>  
  
 <span data-ttu-id="8e1b9-105">Diziler oluşturmak ve sabit bir türü kesin belirlenmiş nesnelerin sayısı ile çalışmak için çok kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-105">Arrays are most useful for creating and working with a fixed number of strongly-typed objects.</span></span> <span data-ttu-id="8e1b9-106">Dizileri hakkında daha fazla bilgi için bkz: [diziler](../../../csharp/programming-guide/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="8e1b9-106">For information about arrays, see [Arrays](../../../csharp/programming-guide/arrays/index.md).</span></span>  
  
 <span data-ttu-id="8e1b9-107">Koleksiyonları nesneleri grupları ile çalışmak için daha esnek bir şekilde sağlar.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-107">Collections provide a more flexible way to work with groups of objects.</span></span> <span data-ttu-id="8e1b9-108">Diziler nesneleri ile çalışma grubu büyür ve dinamik olarak uygulama değişikliği ihtiyaçları geliştikçe daraltma.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-108">Unlike arrays, the group of objects you work with can grow and shrink dynamically as the needs of the application change.</span></span> <span data-ttu-id="8e1b9-109">Bazı koleksiyonlar için nesne anahtarı kullanarak hızlı bir şekilde alabilmeleri koleksiyona koymak nesnesine bir anahtar atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-109">For some collections, you can assign a key to any object that you put into the collection so that you can quickly retrieve the object by using the key.</span></span>  
  
 <span data-ttu-id="8e1b9-110">Bu koleksiyona öğeleri ekleyebilmeniz için önce sınıfın örneğini bildirmeniz gerekir böylece bir sınıf koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-110">A collection is a class, so you must declare an instance of the class before you can add elements to that collection.</span></span>  
  
 <span data-ttu-id="8e1b9-111">Koleksiyonunuz yalnızca bir veri türündeki öğeler içeriyorsa, sınıflarda birini kullanabilirsiniz <xref:System.Collections.Generic?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-111">If your collection contains elements of only one data type, you can use one of the classes in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="8e1b9-112">Böylece başka bir veri türü eklenebilir bir genel koleksiyon tür güvenliği zorlar.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-112">A generic collection enforces type safety so that no other data type can be added to it.</span></span> <span data-ttu-id="8e1b9-113">Genel bir koleksiyondaki bir öğe aldığınızda, kendi veri türü belirlenemiyor veya dönüştürmeden gerekmez.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-113">When you retrieve an element from a generic collection, you do not have to determine its data type or convert it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8e1b9-114">Bu konudaki örnekler için dahil [kullanarak](../../../csharp/language-reference/keywords/using-directive.md) yönergeleri için `System.Collections.Generic` ve `System.Linq` ad alanları.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-114">For the examples in this topic, include [using](../../../csharp/language-reference/keywords/using-directive.md) directives for the `System.Collections.Generic` and `System.Linq` namespaces.</span></span>  
  
 <span data-ttu-id="8e1b9-115">**Bu konudaki**</span><span class="sxs-lookup"><span data-stu-id="8e1b9-115">**In this topic**</span></span>  
  
-   [<span data-ttu-id="8e1b9-116">Basit bir koleksiyonun kullanma</span><span class="sxs-lookup"><span data-stu-id="8e1b9-116">Using a Simple Collection</span></span>](#BKMK_SimpleCollection)  
  
-   [<span data-ttu-id="8e1b9-117">Koleksiyon türleri</span><span class="sxs-lookup"><span data-stu-id="8e1b9-117">Kinds of Collections</span></span>](#BKMK_KindsOfCollections)  
  
    -   [<span data-ttu-id="8e1b9-118">System.Collections.Generic sınıfları</span><span class="sxs-lookup"><span data-stu-id="8e1b9-118">System.Collections.Generic Classes</span></span>](#BKMK_Generic)  
  
    -   [<span data-ttu-id="8e1b9-119">System.Collections.Concurrent sınıfları</span><span class="sxs-lookup"><span data-stu-id="8e1b9-119">System.Collections.Concurrent Classes</span></span>](#BKMK_Concurrent)  
  
    -   [<span data-ttu-id="8e1b9-120">System.Collections sınıfları</span><span class="sxs-lookup"><span data-stu-id="8e1b9-120">System.Collections Classes</span></span>](#BKMK_Collections)  
  
-   [<span data-ttu-id="8e1b9-121">Anahtar/değer çiftleri koleksiyonu uygulama</span><span class="sxs-lookup"><span data-stu-id="8e1b9-121">Implementing a Collection of Key/Value Pairs</span></span>](#BKMK_KeyValuePairs)  
  
-   [<span data-ttu-id="8e1b9-122">Bir koleksiyon erişmek için LINQ kullanma</span><span class="sxs-lookup"><span data-stu-id="8e1b9-122">Using LINQ to Access a Collection</span></span>](#BKMK_LINQ)  
  
-   [<span data-ttu-id="8e1b9-123">Koleksiyonda sıralama</span><span class="sxs-lookup"><span data-stu-id="8e1b9-123">Sorting a Collection</span></span>](#BKMK_Sorting)  
  
-   [<span data-ttu-id="8e1b9-124">Özel bir koleksiyona tanımlama</span><span class="sxs-lookup"><span data-stu-id="8e1b9-124">Defining a Custom Collection</span></span>](#BKMK_CustomCollection)  
  
-   [<span data-ttu-id="8e1b9-125">Yineleyiciler</span><span class="sxs-lookup"><span data-stu-id="8e1b9-125">Iterators</span></span>](#BKMK_Iterators)  
  
<a name="BKMK_SimpleCollection"></a>
## <a name="using-a-simple-collection"></a><span data-ttu-id="8e1b9-126">Basit bir koleksiyonun kullanma</span><span class="sxs-lookup"><span data-stu-id="8e1b9-126">Using a Simple Collection</span></span>  
 <span data-ttu-id="8e1b9-127">Bu bölümdeki örnekleri genel kullanmak <xref:System.Collections.Generic.List%601> sınıfı, türü kesin belirlenmiş nesnelerin listesini ile çalışmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-127">The examples in this section use the generic <xref:System.Collections.Generic.List%601> class, which enables you to work with a strongly typed list of objects.</span></span>  
  
 <span data-ttu-id="8e1b9-128">Aşağıdaki örnek dizelerinin listesini oluşturur ve ardından kullanarak dizeleri tekrarlanan bir ya da [foreach](../../../csharp/language-reference/keywords/foreach-in.md) deyimi.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-128">The following example creates a list of strings and then iterates through the strings by using a or [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement.</span></span>  
  
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
  
 <span data-ttu-id="8e1b9-129">Bir koleksiyonun içeriğini önceden biliniyorsa, kullanabileceğiniz bir *koleksiyon Başlatıcısı* koleksiyonu başlatılamadı.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-129">If the contents of a collection are known in advance, you can use a *collection initializer* to initialize the collection.</span></span> <span data-ttu-id="8e1b9-130">Daha fazla bilgi için bkz: [nesne ve koleksiyon başlatıcıları](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span><span class="sxs-lookup"><span data-stu-id="8e1b9-130">For more information, see [Object and Collection Initializers](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span></span>  
  
 <span data-ttu-id="8e1b9-131">Koleksiyon Başlatıcısı öğeleri koleksiyona eklemek için kullanılan dışında aşağıdaki örnek önceki örnekte aynıdır.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-131">The following example is the same as the previous example, except a collection initializer is used to add elements to the collection.</span></span>  
  
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
  
 <span data-ttu-id="8e1b9-132">Kullanabileceğiniz bir [için](../../../csharp/language-reference/keywords/for.md) deyimi yerine bir `foreach` bir koleksiyonda yinelemek için deyimi.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-132">You can use a [for](../../../csharp/language-reference/keywords/for.md) statement instead of a `foreach` statement to iterate through a collection.</span></span> <span data-ttu-id="8e1b9-133">Bunun için dizin konumu tarafından koleksiyon öğeleri erişerek.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-133">You accomplish this by accessing the collection elements by the index position.</span></span> <span data-ttu-id="8e1b9-134">Öğe dizini 0'da başlar ve öğe sayısı eksi 1'konumundaki sona erer.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-134">The index of the elements starts at 0 and ends at the element count minus 1.</span></span>  
  
 <span data-ttu-id="8e1b9-135">Aşağıdaki örnek bir koleksiyonun öğelerini kullanarak tekrarlanan `for` yerine `foreach`.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-135">The following example iterates through the elements of a collection by using `for` instead of `foreach`.</span></span>  
  
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
  
 <span data-ttu-id="8e1b9-136">Aşağıdaki örnek kaldırılacak nesne belirterek öğeyi koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-136">The following example removes an element from the collection by specifying the object to remove.</span></span>  
  
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
  
 <span data-ttu-id="8e1b9-137">Aşağıdaki örnek öğeleri genel bir listeden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-137">The following example removes elements from a generic list.</span></span> <span data-ttu-id="8e1b9-138">Yerine bir `foreach` deyimi, bir [için](../../../csharp/language-reference/keywords/for.md) azalan sırada tekrarlanan deyimi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-138">Instead of a `foreach` statement, a [for](../../../csharp/language-reference/keywords/for.md) statement that iterates in descending order is used.</span></span> <span data-ttu-id="8e1b9-139">Bunun nedeni, <xref:System.Collections.Generic.List%601.RemoveAt%2A> yöntemi bir alt dizin değerine sahip olacak şekilde kaldırılan bir öğeden sonra öğeleri neden olur.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-139">This is because the <xref:System.Collections.Generic.List%601.RemoveAt%2A> method causes elements after a removed element to have a lower index value.</span></span>  
  
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
  
 <span data-ttu-id="8e1b9-140">Öğe türü için <xref:System.Collections.Generic.List%601>, ayrıca kendi sınıfı tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-140">For the type of elements in the <xref:System.Collections.Generic.List%601>, you can also define your own class.</span></span> <span data-ttu-id="8e1b9-141">Aşağıdaki örnekte, `Galaxy` tarafından kullanılan sınıf <xref:System.Collections.Generic.List%601> kodda tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-141">In the following example, the `Galaxy` class that is used by the <xref:System.Collections.Generic.List%601> is defined in the code.</span></span>  
  
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
## <a name="kinds-of-collections"></a><span data-ttu-id="8e1b9-142">Koleksiyon türleri</span><span class="sxs-lookup"><span data-stu-id="8e1b9-142">Kinds of Collections</span></span> 
 <span data-ttu-id="8e1b9-143">Birçok ortak koleksiyonları, .NET Framework tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-143">Many common collections are provided by the .NET Framework.</span></span> <span data-ttu-id="8e1b9-144">Her koleksiyon türünün belirli bir amaç için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-144">Each type of collection is designed for a specific purpose.</span></span>  
  
 <span data-ttu-id="8e1b9-145">Genel koleksiyon sınıfları bazıları, bu bölümde açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="8e1b9-145">Some of the common collection classes are described in this section:</span></span>  
  
-   <span data-ttu-id="8e1b9-146"><xref:System.Collections.Generic>sınıfları</span><span class="sxs-lookup"><span data-stu-id="8e1b9-146"><xref:System.Collections.Generic> classes</span></span>  
  
-   <span data-ttu-id="8e1b9-147"><xref:System.Collections.Concurrent>sınıfları</span><span class="sxs-lookup"><span data-stu-id="8e1b9-147"><xref:System.Collections.Concurrent> classes</span></span>  
  
-   <span data-ttu-id="8e1b9-148"><xref:System.Collections>sınıfları</span><span class="sxs-lookup"><span data-stu-id="8e1b9-148"><xref:System.Collections> classes</span></span>  
  
<a name="BKMK_Generic"></a>
### <a name="systemcollectionsgeneric-classes"></a><span data-ttu-id="8e1b9-149">System.Collections.Generic sınıfları</span><span class="sxs-lookup"><span data-stu-id="8e1b9-149">System.Collections.Generic Classes</span></span>  
 <span data-ttu-id="8e1b9-150">Sınıflarda birini kullanarak genel bir koleksiyon oluşturabilirsiniz <xref:System.Collections.Generic> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-150">You can create a generic collection by using one of the classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="8e1b9-151">Koleksiyondaki her öğe aynı veri türüne sahip bir genel koleksiyon faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-151">A generic collection is useful when every item in the collection has the same data type.</span></span> <span data-ttu-id="8e1b9-152">Bir genel koleksiyon yalnızca istenen verilerin vererek güçlü yazmaya zorlar eklenecek türü.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-152">A generic collection enforces strong typing by allowing only the desired data type to be added.</span></span>  
  
 <span data-ttu-id="8e1b9-153">Aşağıdaki tabloda bazı sık kullanılan sınıfları listeler <xref:System.Collections.Generic?displayProperty=nameWithType> ad alanı:</span><span class="sxs-lookup"><span data-stu-id="8e1b9-153">The following table lists some of the frequently used classes of the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace:</span></span>  

|<span data-ttu-id="8e1b9-154">örneği</span><span class="sxs-lookup"><span data-stu-id="8e1b9-154">Class</span></span>|<span data-ttu-id="8e1b9-155">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8e1b9-155">Description</span></span>| 
|---|---|  
|<xref:System.Collections.Generic.Dictionary%602>|<span data-ttu-id="8e1b9-156">Anahtarına göre düzenlenir anahtar/değer çiftlerinin koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-156">Represents a collection of key/value pairs that are organized based on the key.</span></span>|  
|<xref:System.Collections.Generic.List%601>|<span data-ttu-id="8e1b9-157">Dizini tarafından erişilebilecek nesnelerin bir listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-157">Represents a list of objects that can be accessed by index.</span></span> <span data-ttu-id="8e1b9-158">Arama, sıralama ve listelerini değiştirmek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-158">Provides methods to search, sort, and modify lists.</span></span>|  
|<xref:System.Collections.Generic.Queue%601>|<span data-ttu-id="8e1b9-159">İlk gelen, nesnelerin giren ilk çıkar (FIFO) koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-159">Represents a first in, first out (FIFO) collection of objects.</span></span>|  
|<xref:System.Collections.Generic.SortedList%602>|<span data-ttu-id="8e1b9-160">Anahtarıyla ilişkili üzerinde temel sıralı anahtar/değer çiftlerinin koleksiyonunu temsil eder <xref:System.Collections.Generic.IComparer%601> uygulaması.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-160">Represents a collection of key/value pairs that are sorted by key based on the associated <xref:System.Collections.Generic.IComparer%601> implementation.</span></span>|  
|<xref:System.Collections.Generic.Stack%601>|<span data-ttu-id="8e1b9-161">Son olarak, nesnelerin ilk çıkar (LIFO) koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-161">Represents a last in, first out (LIFO) collection of objects.</span></span>|  
  
 <span data-ttu-id="8e1b9-162">Ek bilgi için bkz: [yaygın olarak kullanılan koleksiyon türleri](../../../standard/collections/commonly-used-collection-types.md), [koleksiyon sınıfı seçme](../../../standard/collections/selecting-a-collection-class.md), ve <xref:System.Collections.Generic>.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-162">For additional information, see [Commonly Used Collection Types](../../../standard/collections/commonly-used-collection-types.md), [Selecting a Collection Class](../../../standard/collections/selecting-a-collection-class.md), and <xref:System.Collections.Generic>.</span></span>  
  
<a name="BKMK_Concurrent"></a>
### <a name="systemcollectionsconcurrent-classes"></a><span data-ttu-id="8e1b9-163">System.Collections.Concurrent sınıfları</span><span class="sxs-lookup"><span data-stu-id="8e1b9-163">System.Collections.Concurrent Classes</span></span>  
 <span data-ttu-id="8e1b9-164">.NET Framework 4 veya daha yeni koleksiyonlardaki <xref:System.Collections.Concurrent> ad alanı koleksiyon öğeleri birden çok iş parçacığından erişmek için etkin iş parçacığı açısından güvenli işlemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-164">In the .NET Framework 4 or newer, the collections in the <xref:System.Collections.Concurrent> namespace provide efficient thread-safe operations for accessing collection items from multiple threads.</span></span>  
  
 <span data-ttu-id="8e1b9-165">Sınıflarda <xref:System.Collections.Concurrent> ad alanı, ilgili türler yerine kullanılmalıdır <xref:System.Collections.Generic?displayProperty=nameWithType> ve <xref:System.Collections?displayProperty=nameWithType> birden çok iş parçacığı aynı anda koleksiyonuna erişme her ad alanları.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-165">The classes in the <xref:System.Collections.Concurrent> namespace should be used instead of the corresponding types in the <xref:System.Collections.Generic?displayProperty=nameWithType> and <xref:System.Collections?displayProperty=nameWithType> namespaces whenever multiple threads are accessing the collection concurrently.</span></span> <span data-ttu-id="8e1b9-166">Daha fazla bilgi için bkz: [iş parçacığı koleksiyonları](../../../standard/collections/thread-safe/index.md) ve <xref:System.Collections.Concurrent>.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-166">For more information, see [Thread-Safe Collections](../../../standard/collections/thread-safe/index.md) and <xref:System.Collections.Concurrent>.</span></span>  
  
 <span data-ttu-id="8e1b9-167">Dahil bazı sınıfları <xref:System.Collections.Concurrent> ad <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, ve <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-167">Some classes included in the <xref:System.Collections.Concurrent> namespace are <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>  
  
<a name="BKMK_Collections"></a>
### <a name="systemcollections-classes"></a><span data-ttu-id="8e1b9-168">System.Collections sınıfları</span><span class="sxs-lookup"><span data-stu-id="8e1b9-168">System.Collections Classes</span></span>  
 <span data-ttu-id="8e1b9-169">Sınıflarda <xref:System.Collections?displayProperty=nameWithType> özellikle yazılan nesnelerin, ancak nesne türü ad alanı öğeleri saklamayın `Object`.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-169">The classes in the <xref:System.Collections?displayProperty=nameWithType> namespace do not store elements as specifically typed objects, but as objects of type `Object`.</span></span>  
  
 <span data-ttu-id="8e1b9-170">Mümkün olduğunda, genel koleksiyonlarda kullanması gereken <xref:System.Collections.Generic?displayProperty=nameWithType> ad alanı veya <xref:System.Collections.Concurrent> eski türler yerine ad `System.Collections` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-170">Whenever possible, you should use the generic collections in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace or the <xref:System.Collections.Concurrent> namespace instead of the legacy types in the `System.Collections` namespace.</span></span>  
  
 <span data-ttu-id="8e1b9-171">Aşağıdaki tabloda bazı sık kullanılan sınıfları listeler `System.Collections` ad alanı:</span><span class="sxs-lookup"><span data-stu-id="8e1b9-171">The following table lists some of the frequently used classes in the `System.Collections` namespace:</span></span>  
  
|<span data-ttu-id="8e1b9-172">örneği</span><span class="sxs-lookup"><span data-stu-id="8e1b9-172">Class</span></span>|<span data-ttu-id="8e1b9-173">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8e1b9-173">Description</span></span>|  
|---|---|  
|<xref:System.Collections.ArrayList>|<span data-ttu-id="8e1b9-174">Temsil nesneleri büyüklüğü dinamik olarak artan bir dizi gerekli.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-174">Represents an array of objects whose size is dynamically increased as required.</span></span>|  
|<xref:System.Collections.Hashtable>|<span data-ttu-id="8e1b9-175">Anahtar karma koduna göre düzenlenir anahtar/değer çiftlerinin koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-175">Represents a collection of key/value pairs that are organized based on the hash code of the key.</span></span>|  
|<xref:System.Collections.Queue>|<span data-ttu-id="8e1b9-176">İlk gelen, nesnelerin giren ilk çıkar (FIFO) koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-176">Represents a first in, first out (FIFO) collection of objects.</span></span>|  
|<xref:System.Collections.Stack>|<span data-ttu-id="8e1b9-177">Son olarak, nesnelerin ilk çıkar (LIFO) koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-177">Represents a last in, first out (LIFO) collection of objects.</span></span>|  
  
 <span data-ttu-id="8e1b9-178"><xref:System.Collections.Specialized> Ad alanı, yalnızca dize koleksiyonlar ve bağlı listesi ve karma sözlükler gibi özelleştirilmiş ve kesin türü belirtilmiş koleksiyon sınıfları sağlar.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-178">The <xref:System.Collections.Specialized> namespace provides specialized and strongly typed collection classes, such as string-only collections and linked-list and hybrid dictionaries.</span></span>  

<a name="BKMK_KeyValuePairs"></a>
## <a name="implementing-a-collection-of-keyvalue-pairs"></a><span data-ttu-id="8e1b9-179">Anahtar/değer çiftleri koleksiyonu uygulama</span><span class="sxs-lookup"><span data-stu-id="8e1b9-179">Implementing a Collection of Key/Value Pairs</span></span>  
 <span data-ttu-id="8e1b9-180"><xref:System.Collections.Generic.Dictionary%602> Genel koleksiyon her öğenin anahtarı kullanarak bir koleksiyondaki öğelerin erişmesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-180">The <xref:System.Collections.Generic.Dictionary%602> generic collection enables you to access to elements in a collection by using the key of each element.</span></span> <span data-ttu-id="8e1b9-181">Her ek sözlük için bir değer ve ilişkili anahtarını oluşur.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-181">Each addition to the dictionary consists of a value and its associated key.</span></span> <span data-ttu-id="8e1b9-182">Kendi anahtarını kullanarak bir değer alma olduğundan hızlı `Dictionary` sınıfı, bir karma tablosu olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-182">Retrieving a value by using its key is fast because the `Dictionary` class is implemented as a hash table.</span></span>  
  
 <span data-ttu-id="8e1b9-183">Aşağıdaki örnekte bir `Dictionary` koleksiyonu ve kullanarak sözlükte yinelenen bir `foreach` deyimi.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-183">The following example creates a `Dictionary` collection and iterates through the dictionary by using a `foreach` statement.</span></span>  
  
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
  
 <span data-ttu-id="8e1b9-184">Bunun yerine koleksiyon Başlatıcısı oluşturmak için kullanılacak `Dictionary` değiştirebileceğiniz koleksiyonu `BuildDictionary` ve `AddToDictionary` aşağıdaki yöntemi yöntemleriyle.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-184">To instead use a collection initializer to build the `Dictionary` collection, you can replace the `BuildDictionary` and `AddToDictionary` methods with the following method.</span></span>  
  
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
  
 <span data-ttu-id="8e1b9-185">Aşağıdaki örnek kullanır <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> yöntemi ve <xref:System.Collections.Generic.Dictionary%602.Item%2A> özelliği `Dictionary` öğe anahtarı tarafından hızla bulmak için.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-185">The following example uses the <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> method and the <xref:System.Collections.Generic.Dictionary%602.Item%2A> property of `Dictionary` to quickly find an item by key.</span></span> <span data-ttu-id="8e1b9-186">`Item` Özellik bir öğeyi erişmenize olanak tanır `elements` kullanarak koleksiyon `elements[symbol]` C#.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-186">The `Item` property enables you to access an item in the `elements` collection by using the `elements[symbol]` in C#.</span></span>  
  
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
  
 <span data-ttu-id="8e1b9-187">Aşağıdaki örnek, bunun yerine kullanır <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> yöntemi anahtarının hızlı bir şekilde bir öğe bulunamıyor.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-187">The following example instead uses the <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> method quickly find an item by key.</span></span>  
  
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
## <a name="using-linq-to-access-a-collection"></a><span data-ttu-id="8e1b9-188">Bir koleksiyon erişmek için LINQ kullanma</span><span class="sxs-lookup"><span data-stu-id="8e1b9-188">Using LINQ to Access a Collection</span></span>  
 <span data-ttu-id="8e1b9-189">LINQ (dil ile tümleşik sorgu) koleksiyonları erişmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-189">LINQ (Language-Integrated Query) can be used to access collections.</span></span> <span data-ttu-id="8e1b9-190">LINQ sorgularını filtreleme, sıralama ve yetenekleri gruplandırma sağlar.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-190">LINQ queries provide filtering, ordering, and grouping capabilities.</span></span> <span data-ttu-id="8e1b9-191">Daha fazla bilgi için bkz: [C# üzerinde LINQ ile çalışmaya başlama](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="8e1b9-191">For more information, see  [Getting Started with LINQ in C#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md).</span></span>  
  
 <span data-ttu-id="8e1b9-192">Aşağıdaki örnek, genel karşı LINQ sorgusu çalıştırır `List`.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-192">The following example runs a LINQ query against a generic `List`.</span></span> <span data-ttu-id="8e1b9-193">LINQ Sorgu sonuçlarını içeren farklı bir koleksiyon döndürür.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-193">The LINQ query returns a different collection that contains the results.</span></span>  
  
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
## <a name="sorting-a-collection"></a><span data-ttu-id="8e1b9-194">Koleksiyonda sıralama</span><span class="sxs-lookup"><span data-stu-id="8e1b9-194">Sorting a Collection</span></span>  
 <span data-ttu-id="8e1b9-195">Aşağıdaki örnek, bir koleksiyon sıralamak için bir yordam gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-195">The following example illustrates a procedure for sorting a collection.</span></span> <span data-ttu-id="8e1b9-196">Örnek örneklerini sıralar `Car` depolanmış sınıfı bir <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-196">The example sorts instances of the `Car` class that are stored in a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="8e1b9-197">`Car` Uygulayan sınıf <xref:System.IComparable%601> gerektiren arabirimi <xref:System.IComparable%601.CompareTo%2A> uygulanan yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-197">The `Car` class implements the <xref:System.IComparable%601> interface, which requires that the <xref:System.IComparable%601.CompareTo%2A> method be implemented.</span></span>  
  
 <span data-ttu-id="8e1b9-198">Her çağrı <xref:System.IComparable%601.CompareTo%2A> yöntemi sıralama için kullanılan tek bir karşılaştırma yapar.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-198">Each call to the <xref:System.IComparable%601.CompareTo%2A> method makes a single comparison that is used for sorting.</span></span> <span data-ttu-id="8e1b9-199">Kullanıcı tarafından yazılan kodu `CompareTo` yöntemi başka bir nesnenin geçerli nesnenin her karşılaştırma için bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-199">User-written code in the `CompareTo` method returns a value for each comparison of the current object with another object.</span></span> <span data-ttu-id="8e1b9-200">Döndürülen değer olan geçerli nesne ise sıfırdan az diğerinden daha az nesne, geçerli nesne bir nesneden daha büyükse, sıfır ve sıfırdan büyük eşit olup olmadıkları.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-200">The value returned is less than zero if the current object is less than the other object, greater than zero if the current object is greater than the other object, and zero if they are equal.</span></span> <span data-ttu-id="8e1b9-201">Bu, kodda daha fazla değerinden ölçütleri tanımlayın ve eşit olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-201">This enables you to define in code the criteria for greater than, less than, and equal.</span></span>  
  
 <span data-ttu-id="8e1b9-202">İçinde `ListCars` yöntemi, `cars.Sort()` deyimi listesini sıralar.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-202">In the `ListCars` method, the `cars.Sort()` statement sorts the list.</span></span> <span data-ttu-id="8e1b9-203">Bu çağrıyı <xref:System.Collections.Generic.List%601.Sort%2A> yöntemi <xref:System.Collections.Generic.List%601> neden `CompareTo` yöntemi için otomatik olarak adlandırılan `Car` nesnelerini `List`.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-203">This call to the <xref:System.Collections.Generic.List%601.Sort%2A> method of the <xref:System.Collections.Generic.List%601> causes the `CompareTo` method to be called automatically for the `Car` objects in the `List`.</span></span>  
  
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
## <a name="defining-a-custom-collection"></a><span data-ttu-id="8e1b9-204">Özel bir koleksiyona tanımlama</span><span class="sxs-lookup"><span data-stu-id="8e1b9-204">Defining a Custom Collection</span></span>  
 <span data-ttu-id="8e1b9-205">Bir koleksiyon uygulayarak tanımlayabilirsiniz <xref:System.Collections.Generic.IEnumerable%601> veya <xref:System.Collections.IEnumerable> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-205">You can define a collection by implementing the <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="8e1b9-206">Ek bilgi için bkz: [nasıl yapılır: foreach ile koleksiyon sınıfına erişme](../../../csharp/programming-guide/classes-and-structs/how-to-access-a-collection-class-with-foreach.md).</span><span class="sxs-lookup"><span data-stu-id="8e1b9-206">For additional information, see [How to: Access a Collection Class with foreach](../../../csharp/programming-guide/classes-and-structs/how-to-access-a-collection-class-with-foreach.md).</span></span>  
  
 <span data-ttu-id="8e1b9-207">Özel bir koleksiyona tanımlayabilirsiniz rağmen şurada açıklanan .NET Framework içinde yer alan koleksiyonlar kullanmanız daha iyi [türleri, koleksiyonları](#BKMK_KindsOfCollections) bu konuda daha önce.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-207">Although you can define a custom collection, it is usually better to instead use the collections that are included in the .NET Framework, which are described in [Kinds of Collections](#BKMK_KindsOfCollections) earlier in this topic.</span></span>  
  
 <span data-ttu-id="8e1b9-208">Aşağıdaki örnek adlı özel koleksiyon sınıfı tanımlar `AllColors`.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-208">The following example defines a custom collection class named `AllColors`.</span></span> <span data-ttu-id="8e1b9-209">Bu sınıf uygulayan <xref:System.Collections.IEnumerable> gerektiren arabirimi <xref:System.Collections.IEnumerable.GetEnumerator%2A> uygulanan yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-209">This class implements the <xref:System.Collections.IEnumerable> interface, which requires that the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method be implemented.</span></span>  
  
 <span data-ttu-id="8e1b9-210">`GetEnumerator` Yöntem örneği `ColorEnumerator` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-210">The `GetEnumerator` method returns an instance of the `ColorEnumerator` class.</span></span> <span data-ttu-id="8e1b9-211">`ColorEnumerator`uygulayan <xref:System.Collections.IEnumerator> gerektiren arabirimi <xref:System.Collections.IEnumerator.Current%2A> özelliği, <xref:System.Collections.IEnumerator.MoveNext%2A> yöntemi ve <xref:System.Collections.IEnumerator.Reset%2A> uygulanan yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-211">`ColorEnumerator` implements the <xref:System.Collections.IEnumerator> interface, which requires that the <xref:System.Collections.IEnumerator.Current%2A> property, <xref:System.Collections.IEnumerator.MoveNext%2A> method, and <xref:System.Collections.IEnumerator.Reset%2A> method be implemented.</span></span>  
  
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
##  <a name="iterators"></a><span data-ttu-id="8e1b9-212">Yineleyiciler</span><span class="sxs-lookup"><span data-stu-id="8e1b9-212">Iterators</span></span>  
 <span data-ttu-id="8e1b9-213">Bir *yineleyici* içinde bir koleksiyon özel bir yineleme yapmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-213">An *iterator* is used to perform a custom iteration over a collection.</span></span> <span data-ttu-id="8e1b9-214">Yineleyici bir yöntem olabilir veya bir `get` erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-214">An iterator can be a method or a `get` accessor.</span></span> <span data-ttu-id="8e1b9-215">Yineleyici kullanan bir [verim return](../../../csharp/language-reference/keywords/yield.md) deyimi her birer birer koleksiyonun bir öğesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-215">An iterator uses a [yield return](../../../csharp/language-reference/keywords/yield.md) statement to return each element of the collection one at a time.</span></span>  
  
 <span data-ttu-id="8e1b9-216">Yineleyici kullanarak çağırma bir [foreach](../../../csharp/language-reference/keywords/foreach-in.md) deyimi.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-216">You call an iterator by using a [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement.</span></span> <span data-ttu-id="8e1b9-217">Her yinelemesinden `foreach` döngü yineleyici çağırır.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-217">Each iteration of the `foreach` loop calls the iterator.</span></span> <span data-ttu-id="8e1b9-218">Zaman bir `yield return` deyimi yineleyici ulaşıldığında, bir ifade döndürülür ve kod geçerli konumda korunur.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-218">When a `yield return` statement is reached in the iterator, an expression is returned, and the current location in code is retained.</span></span> <span data-ttu-id="8e1b9-219">Yürütme o konumdan yineleyici adlı bir sonraki başlatılışında yeniden başlatılır.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-219">Execution is restarted from that location the next time that the iterator is called.</span></span>  
  
 <span data-ttu-id="8e1b9-220">Daha fazla bilgi için bkz: [yineleyiciler (C#)](../../../csharp/programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="8e1b9-220">For more information, see [Iterators (C#)](../../../csharp/programming-guide/concepts/iterators.md).</span></span>  
  
 <span data-ttu-id="8e1b9-221">Aşağıdaki örnek, bir yineleyici yöntemi kullanır.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-221">The following example uses an iterator method.</span></span> <span data-ttu-id="8e1b9-222">İterator yöntemi sahip bir `yield return` içinde deyimi bir [için](../../../csharp/language-reference/keywords/for.md) döngü.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-222">The iterator method has a `yield return` statement that is inside a [for](../../../csharp/language-reference/keywords/for.md) loop.</span></span> <span data-ttu-id="8e1b9-223">İçinde `ListEvenNumbers` yöntemi, her yinelemesinden `foreach` deyimi gövde oluşturur diğerine geçer yineleyici yöntemine bir çağrı `yield return` deyimi.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-223">In the `ListEvenNumbers` method, each iteration of the `foreach` statement body creates a call to the iterator method, which proceeds to the next `yield return` statement.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8e1b9-224">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8e1b9-224">See Also</span></span>  
 [<span data-ttu-id="8e1b9-225">Nesne ve koleksiyon başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="8e1b9-225">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
 [<span data-ttu-id="8e1b9-226">Programlama Kavramları (C#)</span><span class="sxs-lookup"><span data-stu-id="8e1b9-226">Programming Concepts (C#)</span></span>](../../../csharp/programming-guide/concepts/index.md)  
 [<span data-ttu-id="8e1b9-227">Option Strict deyimi</span><span class="sxs-lookup"><span data-stu-id="8e1b9-227">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="8e1b9-228">LINQ to nesneler (C#)</span><span class="sxs-lookup"><span data-stu-id="8e1b9-228">LINQ to Objects (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)  
 [<span data-ttu-id="8e1b9-229">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="8e1b9-229">Parallel LINQ (PLINQ)</span></span>](../../../standard/parallel-programming/parallel-linq-plinq.md)  
 [<span data-ttu-id="8e1b9-230">Koleksiyonlar ve veri yapıları</span><span class="sxs-lookup"><span data-stu-id="8e1b9-230">Collections and Data Structures</span></span>](../../../standard/collections/index.md)  
 [<span data-ttu-id="8e1b9-231">Oluşturma ve koleksiyonları düzenleme</span><span class="sxs-lookup"><span data-stu-id="8e1b9-231">Creating and Manipulating Collections</span></span>](http://msdn.microsoft.com/en-us/2065398e-eb1a-4821-9188-75f16e42e069)  
 [<span data-ttu-id="8e1b9-232">Koleksiyon sınıfı seçme</span><span class="sxs-lookup"><span data-stu-id="8e1b9-232">Selecting a Collection Class</span></span>](../../../standard/collections/selecting-a-collection-class.md)  
 [<span data-ttu-id="8e1b9-233">Karşılaştırmalar ve sıralamalar</span><span class="sxs-lookup"><span data-stu-id="8e1b9-233">Comparisons and Sorts Within Collections</span></span>](../../../standard/collections/comparisons-and-sorts-within-collections.md)  
 [<span data-ttu-id="8e1b9-234">Genel koleksiyonları ne zaman kullanılacağı</span><span class="sxs-lookup"><span data-stu-id="8e1b9-234">When to Use Generic Collections</span></span>](../../../standard/collections/when-to-use-generic-collections.md)  
 [<span data-ttu-id="8e1b9-235">Nasıl yapılır: foreach ile koleksiyon sınıfına erişme</span><span class="sxs-lookup"><span data-stu-id="8e1b9-235">How to: Access a Collection Class with foreach</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-access-a-collection-class-with-foreach.md)
