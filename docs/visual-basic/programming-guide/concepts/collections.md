---
title: Koleksiyonlar
ms.date: 07/20/2015
ms.assetid: 5f7749f3-aaf2-4319-b63c-bfa72e1e2b7a
ms.openlocfilehash: 232b9ec7b5975092e73daf0a7384fa816f55f72f
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646340"
---
# <a name="collections-visual-basic"></a><span data-ttu-id="f2ad0-102">Koleksiyonlar (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2ad0-102">Collections (Visual Basic)</span></span>

<span data-ttu-id="f2ad0-103">Birçok uygulama için, ilgili nesnelerin grupları oluşturmak ve yönetmek istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-103">For many applications, you want to create and manage groups of related objects.</span></span> <span data-ttu-id="f2ad0-104">Nesneleri gruplandırmanın iki yolu vardır: nesne dizileri oluşturarak ve nesnelerin koleksiyonlarını oluşturarak.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-104">There are two ways to group objects: by creating arrays of objects, and by creating collections of objects.</span></span>

<span data-ttu-id="f2ad0-105">Diziler, güçlü bir şekilde yazılan sabit sayıda nesne oluşturmak ve bunlarla çalışmak için en kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-105">Arrays are most useful for creating and working with a fixed number of strongly-typed objects.</span></span> <span data-ttu-id="f2ad0-106">Diziler hakkında daha fazla bilgi için [Diziler'e](../../../visual-basic/programming-guide/language-features/arrays/index.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-106">For information about arrays, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>

<span data-ttu-id="f2ad0-107">Koleksiyonlar, nesne gruplarıyla çalışmak için daha esnek bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-107">Collections provide a more flexible way to work with groups of objects.</span></span> <span data-ttu-id="f2ad0-108">Dizilerin aksine, birlikte çalıştığınız nesne grubu, uygulamanın gereksinimleri değiştikçe dinamik olarak büyüyebilir ve küçülebilir.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-108">Unlike arrays, the group of objects you work with can grow and shrink dynamically as the needs of the application change.</span></span> <span data-ttu-id="f2ad0-109">Bazı koleksiyonlar için, anahtarı kullanarak nesneyi hızla alabilmeniz için koleksiyona koyduğunuz herhangi bir nesneye bir anahtar atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-109">For some collections, you can assign a key to any object that you put into the collection so that you can quickly retrieve the object by using the key.</span></span>

<span data-ttu-id="f2ad0-110">Koleksiyon bir sınıftır, bu nedenle bu koleksiyona öğe eklemeden önce sınıfın bir örneğini bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-110">A collection is a class, so you must declare an instance of the class before you can add elements to that collection.</span></span>

<span data-ttu-id="f2ad0-111">Koleksiyonunuz yalnızca bir veri türüöğeleri içeriyorsa, <xref:System.Collections.Generic?displayProperty=nameWithType> ad alanındaki sınıflardan birini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-111">If your collection contains elements of only one data type, you can use one of the classes in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="f2ad0-112">Genel bir koleksiyon, türü başka bir veri türünün eklenmeyecek şekilde tür güvenliğini zorlar.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-112">A generic collection enforces type safety so that no other data type can be added to it.</span></span> <span data-ttu-id="f2ad0-113">Genel bir koleksiyondan bir öğe aldığınızda, öğe türünü belirlemeniz veya dönüştürmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-113">When you retrieve an element from a generic collection, you do not have to determine its data type or convert it.</span></span>

> [!NOTE]
> <span data-ttu-id="f2ad0-114">Bu konuyla ilgili örnekler için, dış `System.Collections.Generic` `System.Linq` mekan için [Aktarım](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) deyimleri ve ad alanları içerir.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-114">For the examples in this topic, include [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) statements for the `System.Collections.Generic` and `System.Linq` namespaces.</span></span>

<a name="BKMK_SimpleCollection"></a>

## <a name="using-a-simple-collection"></a><span data-ttu-id="f2ad0-115">Basit Bir Koleksiyon Kullanma</span><span class="sxs-lookup"><span data-stu-id="f2ad0-115">Using a Simple Collection</span></span>

<span data-ttu-id="f2ad0-116">Bu bölümdeki örnekler, <xref:System.Collections.Generic.List%601> güçlü bir şekilde yazılan nesneler listesiyle çalışmanızı sağlayan genel sınıfı kullanır.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-116">The examples in this section use the generic <xref:System.Collections.Generic.List%601> class, which enables you to work with a strongly typed list of objects.</span></span>

<span data-ttu-id="f2ad0-117">Aşağıdaki örnek, dizeleri bir listesini oluşturur ve sonra her biri için kullanarak dizeleri ile yineler [... Sıradaki](../../../visual-basic/language-reference/statements/for-each-next-statement.md) ifade.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-117">The following example creates a list of strings and then iterates through the strings by using a [For Each…Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement.</span></span>

```vb
' Create a list of strings.
Dim salmons As New List(Of String)
salmons.Add("chinook")
salmons.Add("coho")
salmons.Add("pink")
salmons.Add("sockeye")

' Iterate through the list.
For Each salmon As String In salmons
    Console.Write(salmon & " ")
Next
'Output: chinook coho pink sockeye
```

<span data-ttu-id="f2ad0-118">Bir koleksiyonun içeriği önceden biliniyorsa, koleksiyonun başlatılması için bir *koleksiyon başlatılması* nı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-118">If the contents of a collection are known in advance, you can use a *collection initializer* to initialize the collection.</span></span> <span data-ttu-id="f2ad0-119">Daha fazla bilgi için [Bkz. Collection Initializers](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).</span><span class="sxs-lookup"><span data-stu-id="f2ad0-119">For more information, see [Collection Initializers](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).</span></span>

<span data-ttu-id="f2ad0-120">Aşağıdaki örnek, koleksiyona öğe eklemek için bir koleksiyon başlatılması nın kullanılması dışında, önceki örnekle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-120">The following example is the same as the previous example, except a collection initializer is used to add elements to the collection.</span></span>

```vb
' Create a list of strings by using a
' collection initializer.
Dim salmons As New List(Of String) From
    {"chinook", "coho", "pink", "sockeye"}

For Each salmon As String In salmons
    Console.Write(salmon & " ")
Next
'Output: chinook coho pink sockeye
```

<span data-ttu-id="f2ad0-121">Bir For kullanabilirsiniz [... Bir sonraki](../../../visual-basic/language-reference/statements/for-next-statement.md) deyim `For Each` yerine bir koleksiyon aracılığıyla yinelemek için bir deyim.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-121">You can use a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) statement instead of a `For Each` statement to iterate through a collection.</span></span> <span data-ttu-id="f2ad0-122">Bunu dizin konumuna göre koleksiyon öğelerine erişerek gerçekleştirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-122">You accomplish this by accessing the collection elements by the index position.</span></span> <span data-ttu-id="f2ad0-123">Elementlerin dizini 0 ile başlar ve eksi 1 öğe sayısıyla biter.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-123">The index of the elements starts at 0 and ends at the element count minus 1.</span></span>

<span data-ttu-id="f2ad0-124">Aşağıdaki örnek, bir koleksiyonun öğelerini yerine `For…Next` kullanarak `For Each`yineler.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-124">The following example iterates through the elements of a collection by using `For…Next` instead of `For Each`.</span></span>

```vb
Dim salmons As New List(Of String) From
    {"chinook", "coho", "pink", "sockeye"}

For index = 0 To salmons.Count - 1
    Console.Write(salmons(index) & " ")
Next
'Output: chinook coho pink sockeye
```

<span data-ttu-id="f2ad0-125">Aşağıdaki örnek, kaldırılacak nesneyi belirterek bir öğeyi koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-125">The following example removes an element from the collection by specifying the object to remove.</span></span>

```vb
' Create a list of strings by using a
' collection initializer.
Dim salmons As New List(Of String) From
    {"chinook", "coho", "pink", "sockeye"}

' Remove an element in the list by specifying
' the object.
salmons.Remove("coho")

For Each salmon As String In salmons
    Console.Write(salmon & " ")
Next
'Output: chinook pink sockeye
```

<span data-ttu-id="f2ad0-126">Aşağıdaki örnek, öğeleri genel bir listeden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-126">The following example removes elements from a generic list.</span></span> <span data-ttu-id="f2ad0-127">Bir `For Each` deyim yerine, bir [For... Sonraki](../../../visual-basic/language-reference/statements/for-next-statement.md) deyim inen sırada yineler kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-127">Instead of a `For Each` statement, a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) statement that iterates in descending order is used.</span></span> <span data-ttu-id="f2ad0-128">Bunun nedeni, <xref:System.Collections.Generic.List%601.RemoveAt%2A> yöntemin kaldırılan öğeden sonraki öğelerin daha düşük bir dizin değerine sahip olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-128">This is because the <xref:System.Collections.Generic.List%601.RemoveAt%2A> method causes elements after a removed element to have a lower index value.</span></span>

```vb
Dim numbers As New List(Of Integer) From
    {0, 1, 2, 3, 4, 5, 6, 7, 8, 9}

' Remove odd numbers.
For index As Integer = numbers.Count - 1 To 0 Step -1
    If numbers(index) Mod 2 = 1 Then
        ' Remove the element by specifying
        ' the zero-based index in the list.
        numbers.RemoveAt(index)
    End If
Next

' Iterate through the list.
' A lambda expression is placed in the ForEach method
' of the List(T) object.
numbers.ForEach(
    Sub(number) Console.Write(number & " "))
' Output: 0 2 4 6 8
```

<span data-ttu-id="f2ad0-129">Öğelerin türü <xref:System.Collections.Generic.List%601>için, kendi sınıf tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-129">For the type of elements in the <xref:System.Collections.Generic.List%601>, you can also define your own class.</span></span> <span data-ttu-id="f2ad0-130">Aşağıdaki örnekte, `Galaxy` kodda <xref:System.Collections.Generic.List%601> kullanılan sınıf tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-130">In the following example, the `Galaxy` class that is used by the <xref:System.Collections.Generic.List%601> is defined in the code.</span></span>

```vb
Private Sub IterateThroughList()
    Dim theGalaxies As New List(Of Galaxy) From
        {
            New Galaxy With {.Name = "Tadpole", .MegaLightYears = 400},
            New Galaxy With {.Name = "Pinwheel", .MegaLightYears = 25},
            New Galaxy With {.Name = "Milky Way", .MegaLightYears = 0},
            New Galaxy With {.Name = "Andromeda", .MegaLightYears = 3}
        }

    For Each theGalaxy In theGalaxies
        With theGalaxy
            Console.WriteLine(.Name & "  " & .MegaLightYears)
        End With
    Next

    ' Output:
    '  Tadpole  400
    '  Pinwheel  25
    '  Milky Way  0
    '  Andromeda  3
End Sub

Public Class Galaxy
    Public Property Name As String
    Public Property MegaLightYears As Integer
End Class
```

<a name="BKMK_KindsOfCollections"></a>

## <a name="kinds-of-collections"></a><span data-ttu-id="f2ad0-131">Koleksiyon Çeşitleri</span><span class="sxs-lookup"><span data-stu-id="f2ad0-131">Kinds of Collections</span></span>

<span data-ttu-id="f2ad0-132">Birçok ortak koleksiyon .NET Framework tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-132">Many common collections are provided by the .NET Framework.</span></span> <span data-ttu-id="f2ad0-133">Her koleksiyon türü belirli bir amaç için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-133">Each type of collection is designed for a specific purpose.</span></span>

<span data-ttu-id="f2ad0-134">Ortak toplama sınıflarından bazıları bu bölümde açıklanmıştır:</span><span class="sxs-lookup"><span data-stu-id="f2ad0-134">Some of the common collection classes are described in this section:</span></span>

- <span data-ttu-id="f2ad0-135"><xref:System.Collections.Generic> sınıflar</span><span class="sxs-lookup"><span data-stu-id="f2ad0-135"><xref:System.Collections.Generic> classes</span></span>

- <span data-ttu-id="f2ad0-136"><xref:System.Collections.Concurrent> sınıflar</span><span class="sxs-lookup"><span data-stu-id="f2ad0-136"><xref:System.Collections.Concurrent> classes</span></span>

- <span data-ttu-id="f2ad0-137"><xref:System.Collections> sınıflar</span><span class="sxs-lookup"><span data-stu-id="f2ad0-137"><xref:System.Collections> classes</span></span>

- <span data-ttu-id="f2ad0-138">Visual `Collection` Basic sınıfı</span><span class="sxs-lookup"><span data-stu-id="f2ad0-138">Visual Basic `Collection` class</span></span>

<a name="BKMK_Generic"></a>

### <a name="systemcollectionsgeneric-classes"></a><span data-ttu-id="f2ad0-139">System.Collections.Generic Sınıflar</span><span class="sxs-lookup"><span data-stu-id="f2ad0-139">System.Collections.Generic Classes</span></span>

<span data-ttu-id="f2ad0-140"><xref:System.Collections.Generic> Ad alanındaki sınıflardan birini kullanarak genel bir koleksiyon oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-140">You can create a generic collection by using one of the classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="f2ad0-141">Genel bir koleksiyon, koleksiyondaki her öğe aynı veri türüne sahipse yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-141">A generic collection is useful when every item in the collection has the same data type.</span></span> <span data-ttu-id="f2ad0-142">Genel bir koleksiyon, yalnızca istenen veri türünün eklenmesine izin vererek güçlü yazmayı zorlar.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-142">A generic collection enforces strong typing by allowing only the desired data type to be added.</span></span>

<span data-ttu-id="f2ad0-143">Aşağıdaki tabloda ad alanının sık kullanılan <xref:System.Collections.Generic?displayProperty=nameWithType> sınıflarından bazıları listelenebvardır:</span><span class="sxs-lookup"><span data-stu-id="f2ad0-143">The following table lists some of the frequently used classes of the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace:</span></span>

|<span data-ttu-id="f2ad0-144">Sınıf</span><span class="sxs-lookup"><span data-stu-id="f2ad0-144">Class</span></span>|<span data-ttu-id="f2ad0-145">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f2ad0-145">Description</span></span>|
|---|---|
|<xref:System.Collections.Generic.Dictionary%602>|<span data-ttu-id="f2ad0-146">Anahtara göre düzenlenmiş anahtar/değer çiftleri koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-146">Represents a collection of key/value pairs that are organized based on the key.</span></span>|
|<xref:System.Collections.Generic.List%601>|<span data-ttu-id="f2ad0-147">Dizin tarafından erişilebilen nesnelerin listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-147">Represents a list of objects that can be accessed by index.</span></span> <span data-ttu-id="f2ad0-148">Listeleri aramak, sıralamak ve değiştirmek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-148">Provides methods to search, sort, and modify lists.</span></span>|
|<xref:System.Collections.Generic.Queue%601>|<span data-ttu-id="f2ad0-149">Nesnelerin ilk, ilk çıkan (FIFO) koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-149">Represents a first in, first out (FIFO) collection of objects.</span></span>|
|<xref:System.Collections.Generic.SortedList%602>|<span data-ttu-id="f2ad0-150">İlişkili <xref:System.Collections.Generic.IComparer%601> uygulamaya göre anahtara göre sıralanmış anahtar/değer çiftleri koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-150">Represents a collection of key/value pairs that are sorted by key based on the associated <xref:System.Collections.Generic.IComparer%601> implementation.</span></span>|
|<xref:System.Collections.Generic.Stack%601>|<span data-ttu-id="f2ad0-151">Nesnelerin son, ilk çıkan (LIFO) koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-151">Represents a last in, first out (LIFO) collection of objects.</span></span>|

<span data-ttu-id="f2ad0-152">Ek bilgi için, [Sık Kullanılan Koleksiyon Türleri](../../../standard/collections/commonly-used-collection-types.md), Toplama Sınıfı [Seçme](../../../standard/collections/selecting-a-collection-class.md)ve <xref:System.Collections.Generic?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-152">For additional information, see [Commonly Used Collection Types](../../../standard/collections/commonly-used-collection-types.md), [Selecting a Collection Class](../../../standard/collections/selecting-a-collection-class.md), and <xref:System.Collections.Generic?displayProperty=nameWithType>.</span></span>

<a name="BKMK_Concurrent"></a>

### <a name="systemcollectionsconcurrent-classes"></a><span data-ttu-id="f2ad0-153">System.Collections.Eşzamanlı Sınıflar</span><span class="sxs-lookup"><span data-stu-id="f2ad0-153">System.Collections.Concurrent Classes</span></span>

<span data-ttu-id="f2ad0-154">.NET Framework 4 veya daha yeni, <xref:System.Collections.Concurrent> ad alanındaki koleksiyonlar, birden çok iş parçacığından koleksiyon öğelerine erişmek için verimli iş parçacığı güvenli işlemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-154">In the .NET Framework 4 or newer, the collections in the <xref:System.Collections.Concurrent> namespace provide efficient thread-safe operations for accessing collection items from multiple threads.</span></span>

<span data-ttu-id="f2ad0-155"><xref:System.Collections.Concurrent> Birden çok iş parçacığı aynı anda koleksiyona <xref:System.Collections.Generic?displayProperty=nameWithType> erişirken ad alanında ve <xref:System.Collections?displayProperty=nameWithType> ad alanlarındaki karşılık gelen türler yerine ad alanındaki sınıflar kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-155">The classes in the <xref:System.Collections.Concurrent> namespace should be used instead of the corresponding types in the <xref:System.Collections.Generic?displayProperty=nameWithType> and <xref:System.Collections?displayProperty=nameWithType> namespaces whenever multiple threads are accessing the collection concurrently.</span></span> <span data-ttu-id="f2ad0-156">Daha fazla bilgi için İş Parçacığı <xref:System.Collections.Concurrent>Güvenli [Koleksiyonları](../../../standard/collections/thread-safe/index.md) ve .</span><span class="sxs-lookup"><span data-stu-id="f2ad0-156">For more information, see [Thread-Safe Collections](../../../standard/collections/thread-safe/index.md) and <xref:System.Collections.Concurrent>.</span></span>

<span data-ttu-id="f2ad0-157"><xref:System.Collections.Concurrent> Ad alanına dahil edilen bazı <xref:System.Collections.Concurrent.BlockingCollection%601> <xref:System.Collections.Concurrent.ConcurrentDictionary%602>sınıflar <xref:System.Collections.Concurrent.ConcurrentQueue%601>, <xref:System.Collections.Concurrent.ConcurrentStack%601>, , ve .</span><span class="sxs-lookup"><span data-stu-id="f2ad0-157">Some classes included in the <xref:System.Collections.Concurrent> namespace are <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>

<a name="BKMK_Collections"></a>

### <a name="systemcollections-classes"></a><span data-ttu-id="f2ad0-158">System.Collections Sınıfları</span><span class="sxs-lookup"><span data-stu-id="f2ad0-158">System.Collections Classes</span></span>

<span data-ttu-id="f2ad0-159"><xref:System.Collections?displayProperty=nameWithType> Ad alanındaki sınıflar öğeleri özel olarak yazılan nesneler olarak değil, tür `Object`nesneleri olarak depolar.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-159">The classes in the <xref:System.Collections?displayProperty=nameWithType> namespace do not store elements as specifically typed objects, but as objects of type `Object`.</span></span>

<span data-ttu-id="f2ad0-160">Mümkün olduğunda, <xref:System.Collections.Generic?displayProperty=nameWithType> <xref:System.Collections.Concurrent> `System.Collections` ad alanındaki eski türler yerine ad alanında veya ad alanında genel koleksiyonları kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-160">Whenever possible, you should use the generic collections in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace or the <xref:System.Collections.Concurrent> namespace instead of the legacy types in the `System.Collections` namespace.</span></span>

<span data-ttu-id="f2ad0-161">Aşağıdaki tabloda ad alanında sık kullanılan `System.Collections` sınıflardan bazıları listelenemektedir:</span><span class="sxs-lookup"><span data-stu-id="f2ad0-161">The following table lists some of the frequently used classes in the `System.Collections` namespace:</span></span>

|<span data-ttu-id="f2ad0-162">Sınıf</span><span class="sxs-lookup"><span data-stu-id="f2ad0-162">Class</span></span>|<span data-ttu-id="f2ad0-163">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f2ad0-163">Description</span></span>|
|---|---|
|<xref:System.Collections.ArrayList>|<span data-ttu-id="f2ad0-164">Boyutu gerektiği gibi dinamik olarak artırılmış bir nesne dizisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-164">Represents an array of objects whose size is dynamically increased as required.</span></span>|
|<xref:System.Collections.Hashtable>|<span data-ttu-id="f2ad0-165">Anahtarın karma koduna göre düzenlenen anahtar/değer çiftleri koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-165">Represents a collection of key/value pairs that are organized based on the hash code of the key.</span></span>|
|<xref:System.Collections.Queue>|<span data-ttu-id="f2ad0-166">Nesnelerin ilk, ilk çıkan (FIFO) koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-166">Represents a first in, first out (FIFO) collection of objects.</span></span>|
|<xref:System.Collections.Stack>|<span data-ttu-id="f2ad0-167">Nesnelerin son, ilk çıkan (LIFO) koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-167">Represents a last in, first out (LIFO) collection of objects.</span></span>|

<span data-ttu-id="f2ad0-168">Ad <xref:System.Collections.Specialized> alanı, yalnızca dize koleksiyonları ve bağlantılı liste ve karma sözlükler gibi özel ve güçlü bir şekilde yazılan koleksiyon sınıfları sağlar.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-168">The <xref:System.Collections.Specialized> namespace provides specialized and strongly typed collection classes, such as string-only collections and linked-list and hybrid dictionaries.</span></span>

<a name="BKMK_VisualBasic"></a>

### <a name="visual-basic-collection-class"></a><span data-ttu-id="f2ad0-169">Visual Basic Toplama Sınıfı</span><span class="sxs-lookup"><span data-stu-id="f2ad0-169">Visual Basic Collection Class</span></span>

<span data-ttu-id="f2ad0-170">Sayısal dizin veya <xref:Microsoft.VisualBasic.Collection> `String` anahtar kullanarak bir koleksiyon öğesine erişmek için Visual Basic sınıfını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-170">You can use the Visual Basic <xref:Microsoft.VisualBasic.Collection> class to access a collection item by using either a numeric index or a `String` key.</span></span> <span data-ttu-id="f2ad0-171">Bir anahtar belirterek veya belirtmeden bir koleksiyon nesnesine öğe ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-171">You can add items to a collection object either with or without specifying a key.</span></span> <span data-ttu-id="f2ad0-172">Bir öğeyi anahtarı olmadan eklerseniz, öğeye erişmek için sayısal dizinini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-172">If you add an item without a key, you must use its numeric index to access it.</span></span>

<span data-ttu-id="f2ad0-173">Visual Basic `Collection` sınıfı tüm öğelerini `Object`tür olarak depolar, böylece herhangi bir veri türünden bir öğe ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-173">The Visual Basic `Collection` class stores all its elements as type `Object`, so you can add an item of any data type.</span></span> <span data-ttu-id="f2ad0-174">Uygunsuz veri türlerinin eklenmesine karşı koruma yoktur.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-174">There is no safeguard against inappropriate data types being added.</span></span>

<span data-ttu-id="f2ad0-175">Visual Basic `Collection` sınıfını kullandığınızda, koleksiyondaki ilk öğenin dizin1'dir.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-175">When you use the Visual Basic `Collection` class, the first item in a collection has an index of 1.</span></span> <span data-ttu-id="f2ad0-176">Bu, başlangıç dizininin 0 olduğu .NET Framework toplama sınıflarından farklıdır.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-176">This differs from the .NET Framework collection classes, for which the starting index is 0.</span></span>

<span data-ttu-id="f2ad0-177">Mümkün olduğunda, Visual Basic <xref:System.Collections.Generic?displayProperty=nameWithType> <xref:System.Collections.Concurrent> `Collection` sınıfı yerine ad alanında veya ad alanında genel koleksiyonları kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-177">Whenever possible, you should use the generic collections in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace or the <xref:System.Collections.Concurrent> namespace instead of the Visual Basic `Collection` class.</span></span>

<span data-ttu-id="f2ad0-178">Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Collection>.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-178">For more information, see <xref:Microsoft.VisualBasic.Collection>.</span></span>

<a name="BKMK_KeyValuePairs"></a>

## <a name="implementing-a-collection-of-keyvalue-pairs"></a><span data-ttu-id="f2ad0-179">Anahtar/Değer Çiftleri Koleksiyonunu Uygulama</span><span class="sxs-lookup"><span data-stu-id="f2ad0-179">Implementing a Collection of Key/Value Pairs</span></span>

<span data-ttu-id="f2ad0-180">Genel <xref:System.Collections.Generic.Dictionary%602> koleksiyon, her öğenin anahtarını kullanarak koleksiyondaki öğelere erişmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-180">The <xref:System.Collections.Generic.Dictionary%602> generic collection enables you to access to elements in a collection by using the key of each element.</span></span> <span data-ttu-id="f2ad0-181">Sözlükteki her ek bir değer ve ilişkili anahtardan oluşur.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-181">Each addition to the dictionary consists of a value and its associated key.</span></span> <span data-ttu-id="f2ad0-182">`Dictionary` Sınıf karma tablo olarak uygulandığından, anahtarını kullanarak bir değer almak hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-182">Retrieving a value by using its key is fast because the `Dictionary` class is implemented as a hash table.</span></span>

<span data-ttu-id="f2ad0-183">Aşağıdaki örnek bir `Dictionary` koleksiyon oluşturur ve bir `For Each` deyim kullanarak sözlük teyidi.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-183">The following example creates a `Dictionary` collection and iterates through the dictionary by using a `For Each` statement.</span></span>

```vb
Private Sub IterateThroughDictionary()
    Dim elements As Dictionary(Of String, Element) = BuildDictionary()

    For Each kvp As KeyValuePair(Of String, Element) In elements
        Dim theElement As Element = kvp.Value

        Console.WriteLine("key: " & kvp.Key)
        With theElement
            Console.WriteLine("values: " & .Symbol & " " &
                .Name & " " & .AtomicNumber)
        End With
    Next
End Sub

Private Function BuildDictionary() As Dictionary(Of String, Element)
    Dim elements As New Dictionary(Of String, Element)

    AddToDictionary(elements, "K", "Potassium", 19)
    AddToDictionary(elements, "Ca", "Calcium", 20)
    AddToDictionary(elements, "Sc", "Scandium", 21)
    AddToDictionary(elements, "Ti", "Titanium", 22)

    Return elements
End Function

Private Sub AddToDictionary(ByVal elements As Dictionary(Of String, Element),
ByVal symbol As String, ByVal name As String, ByVal atomicNumber As Integer)
    Dim theElement As New Element

    theElement.Symbol = symbol
    theElement.Name = name
    theElement.AtomicNumber = atomicNumber

    elements.Add(Key:=theElement.Symbol, value:=theElement)
End Sub

Public Class Element
    Public Property Symbol As String
    Public Property Name As String
    Public Property AtomicNumber As Integer
End Class
```

<span data-ttu-id="f2ad0-184">Bunun `Dictionary` yerine, koleksiyonu oluşturmak için bir koleksiyon baş `BuildDictionary` harflerini kullanmak için, aşağıdaki yöntemle ve `AddToDictionary` yöntemleri değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-184">To instead use a collection initializer to build the `Dictionary` collection, you can replace the `BuildDictionary` and `AddToDictionary` methods with the following method.</span></span>

```vb
Private Function BuildDictionary2() As Dictionary(Of String, Element)
    Return New Dictionary(Of String, Element) From
        {
            {"K", New Element With
                {.Symbol = "K", .Name = "Potassium", .AtomicNumber = 19}},
            {"Ca", New Element With
                {.Symbol = "Ca", .Name = "Calcium", .AtomicNumber = 20}},
            {"Sc", New Element With
                {.Symbol = "Sc", .Name = "Scandium", .AtomicNumber = 21}},
            {"Ti", New Element With
                {.Symbol = "Ti", .Name = "Titanium", .AtomicNumber = 22}}
        }
End Function
```

<span data-ttu-id="f2ad0-185">Aşağıdaki örnekte, <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> bir <xref:System.Collections.Generic.Dictionary%602.Item%2A> öğeyi `Dictionary` anahtarla hızlı bir şekilde bulmak için yöntem ve özellik kullanır.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-185">The following example uses the <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> method and the <xref:System.Collections.Generic.Dictionary%602.Item%2A> property of `Dictionary` to quickly find an item by key.</span></span> <span data-ttu-id="f2ad0-186">Özellik, `Item` Visual Basic'teki `elements` `elements(symbol)` kodu kullanarak koleksiyondaki bir öğeye erişmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-186">The `Item` property enables you to access an item in the `elements` collection by using the `elements(symbol)` code in Visual Basic.</span></span>

```vb
Private Sub FindInDictionary(ByVal symbol As String)
    Dim elements As Dictionary(Of String, Element) = BuildDictionary()

    If elements.ContainsKey(symbol) = False Then
        Console.WriteLine(symbol & " not found")
    Else
        Dim theElement = elements(symbol)
        Console.WriteLine("found: " & theElement.Name)
    End If
End Sub
```

<span data-ttu-id="f2ad0-187">Aşağıdaki örnek yerine <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> yöntemi hızlı bir şekilde anahtara göre bir öğe bulmak kullanır.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-187">The following example instead uses the <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> method quickly find an item by key.</span></span>

```vb
Private Sub FindInDictionary2(ByVal symbol As String)
    Dim elements As Dictionary(Of String, Element) = BuildDictionary()

    Dim theElement As Element = Nothing
    If elements.TryGetValue(symbol, theElement) = False Then
        Console.WriteLine(symbol & " not found")
    Else
        Console.WriteLine("found: " & theElement.Name)
    End If
End Sub
```

<a name="BKMK_LINQ"></a>

## <a name="using-linq-to-access-a-collection"></a><span data-ttu-id="f2ad0-188">Koleksiyona Erişmek için LINQ kullanma</span><span class="sxs-lookup"><span data-stu-id="f2ad0-188">Using LINQ to Access a Collection</span></span>

<span data-ttu-id="f2ad0-189">LINQ (Dil-Tümleşik Sorgu) koleksiyonlara erişmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-189">LINQ (Language-Integrated Query) can be used to access collections.</span></span> <span data-ttu-id="f2ad0-190">LINQ sorguları filtreleme, sıralama ve gruplandırma özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-190">LINQ queries provide filtering, ordering, and grouping capabilities.</span></span> <span data-ttu-id="f2ad0-191">Daha fazla bilgi için [Visual Basic'te LINQ ile başlarken](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-191">For more information, see [Getting Started with LINQ in Visual Basic](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).</span></span>

<span data-ttu-id="f2ad0-192">Aşağıdaki örnek, genel `List`bir karşı bir LINQ sorgusu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-192">The following example runs a LINQ query against a generic `List`.</span></span> <span data-ttu-id="f2ad0-193">LINQ sorgusu sonuçları içeren farklı bir koleksiyon döndürür.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-193">The LINQ query returns a different collection that contains the results.</span></span>

```vb
Private Sub ShowLINQ()
    Dim elements As List(Of Element) = BuildList()

    ' LINQ Query.
    Dim subset = From theElement In elements
                  Where theElement.AtomicNumber < 22
                  Order By theElement.Name

    For Each theElement In subset
        Console.WriteLine(theElement.Name & " " & theElement.AtomicNumber)
    Next

    ' Output:
    '  Calcium 20
    '  Potassium 19
    '  Scandium 21
End Sub

Private Function BuildList() As List(Of Element)
    Return New List(Of Element) From
        {
            {New Element With
                {.Symbol = "K", .Name = "Potassium", .AtomicNumber = 19}},
            {New Element With
                {.Symbol = "Ca", .Name = "Calcium", .AtomicNumber = 20}},
            {New Element With
                {.Symbol = "Sc", .Name = "Scandium", .AtomicNumber = 21}},
            {New Element With
                {.Symbol = "Ti", .Name = "Titanium", .AtomicNumber = 22}}
        }
End Function

Public Class Element
    Public Property Symbol As String
    Public Property Name As String
    Public Property AtomicNumber As Integer
End Class
```

<a name="BKMK_Sorting"></a>

## <a name="sorting-a-collection"></a><span data-ttu-id="f2ad0-194">Koleksiyonu Sıralama</span><span class="sxs-lookup"><span data-stu-id="f2ad0-194">Sorting a Collection</span></span>

<span data-ttu-id="f2ad0-195">Aşağıdaki örnek, bir koleksiyonu sıralama yordamını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-195">The following example illustrates a procedure for sorting a collection.</span></span> <span data-ttu-id="f2ad0-196">Örnek, bir <xref:System.Collections.Generic.List%601>' `Car` de depolanan sınıfın örneklerini sıralar</span><span class="sxs-lookup"><span data-stu-id="f2ad0-196">The example sorts instances of the `Car` class that are stored in a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="f2ad0-197">Sınıf, `Car` yöntemin <xref:System.IComparable%601> <xref:System.IComparable%601.CompareTo%2A> uygulanmasını gerektiren arabirimi uygular.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-197">The `Car` class implements the <xref:System.IComparable%601> interface, which requires that the <xref:System.IComparable%601.CompareTo%2A> method be implemented.</span></span>

<span data-ttu-id="f2ad0-198">Yönteme <xref:System.IComparable%601.CompareTo%2A> yapılan her çağrı, sıralama için kullanılan tek bir karşılaştırma yapar.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-198">Each call to the <xref:System.IComparable%601.CompareTo%2A> method makes a single comparison that is used for sorting.</span></span> <span data-ttu-id="f2ad0-199">`CompareTo` Yöntemdeki kullanıcı tarafından yazılan kod, geçerli nesnenin başka bir nesneyle her karşılaştırılması için bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-199">User-written code in the `CompareTo` method returns a value for each comparison of the current object with another object.</span></span> <span data-ttu-id="f2ad0-200">Dönen değer, geçerli nesne diğer nesneden küçükse, geçerli nesne diğer nesneden büyükse sıfırdan büyük, eşitse sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-200">The value returned is less than zero if the current object is less than the other object, greater than zero if the current object is greater than the other object, and zero if they are equal.</span></span> <span data-ttu-id="f2ad0-201">Bu, kodda daha büyük, daha az ve eşit ölçütleri tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-201">This enables you to define in code the criteria for greater than, less than, and equal.</span></span>

<span data-ttu-id="f2ad0-202">`ListCars` Yöntemde, `cars.Sort()` deyim listeyi sıralar.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-202">In the `ListCars` method, the `cars.Sort()` statement sorts the list.</span></span> <span data-ttu-id="f2ad0-203">Bu çağrı <xref:System.Collections.Generic.List%601.Sort%2A> yöntemine <xref:System.Collections.Generic.List%601> neden `CompareTo` olan `Car` yöntemin `List`nesneler için otomatik olarak çağrılması.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-203">This call to the <xref:System.Collections.Generic.List%601.Sort%2A> method of the <xref:System.Collections.Generic.List%601> causes the `CompareTo` method to be called automatically for the `Car` objects in the `List`.</span></span>

```vb
Public Sub ListCars()

    ' Create some new cars.
    Dim cars As New List(Of Car) From
    {
        New Car With {.Name = "car1", .Color = "blue", .Speed = 20},
        New Car With {.Name = "car2", .Color = "red", .Speed = 50},
        New Car With {.Name = "car3", .Color = "green", .Speed = 10},
        New Car With {.Name = "car4", .Color = "blue", .Speed = 50},
        New Car With {.Name = "car5", .Color = "blue", .Speed = 30},
        New Car With {.Name = "car6", .Color = "red", .Speed = 60},
        New Car With {.Name = "car7", .Color = "green", .Speed = 50}
    }

    ' Sort the cars by color alphabetically, and then by speed
    ' in descending order.
    cars.Sort()

    ' View all of the cars.
    For Each thisCar As Car In cars
        Console.Write(thisCar.Color.PadRight(5) & " ")
        Console.Write(thisCar.Speed.ToString & " ")
        Console.Write(thisCar.Name)
        Console.WriteLine()
    Next

    ' Output:
    '  blue  50 car4
    '  blue  30 car5
    '  blue  20 car1
    '  green 50 car7
    '  green 10 car3
    '  red   60 car6
    '  red   50 car2
End Sub

Public Class Car
    Implements IComparable(Of Car)

    Public Property Name As String
    Public Property Speed As Integer
    Public Property Color As String

    Public Function CompareTo(ByVal other As Car) As Integer _
        Implements System.IComparable(Of Car).CompareTo
        ' A call to this method makes a single comparison that is
        ' used for sorting.

        ' Determine the relative order of the objects being compared.
        ' Sort by color alphabetically, and then by speed in
        ' descending order.

        ' Compare the colors.
        Dim compare As Integer
        compare = String.Compare(Me.Color, other.Color, True)

        ' If the colors are the same, compare the speeds.
        If compare = 0 Then
            compare = Me.Speed.CompareTo(other.Speed)

            ' Use descending order for speed.
            compare = -compare
        End If

        Return compare
    End Function
End Class
```

<a name="BKMK_CustomCollection"></a>

## <a name="defining-a-custom-collection"></a><span data-ttu-id="f2ad0-204">Özel Koleksiyon Tanımlama</span><span class="sxs-lookup"><span data-stu-id="f2ad0-204">Defining a Custom Collection</span></span>

<span data-ttu-id="f2ad0-205">Bir koleksiyonu <xref:System.Collections.Generic.IEnumerable%601> veya <xref:System.Collections.IEnumerable> arabirimi uygulayarak tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-205">You can define a collection by implementing the <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="f2ad0-206">Daha fazla bilgi için [bkz.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hwyysy67(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f2ad0-206">For additional information, see [Enumerating a Collection](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hwyysy67(v=vs.100)).</span></span>

<span data-ttu-id="f2ad0-207">Özel bir koleksiyon tanımlayabiliyor olsanız da, bu konunun başlarında [Koleksiyon Türleri'nde](#kinds-of-collections) açıklanan .NET Framework'de yer alan koleksiyonları kullanmak genellikle daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-207">Although you can define a custom collection, it is usually better to instead use the collections that are included in the .NET Framework, which are described in [Kinds of Collections](#kinds-of-collections) earlier in this topic.</span></span>

<span data-ttu-id="f2ad0-208">Aşağıdaki örnek, adlı `AllColors`özel bir koleksiyon sınıfı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-208">The following example defines a custom collection class named `AllColors`.</span></span> <span data-ttu-id="f2ad0-209">Bu sınıf, <xref:System.Collections.IEnumerable> yöntemin <xref:System.Collections.IEnumerable.GetEnumerator%2A> uygulanmasını gerektiren arabirimi uygular.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-209">This class implements the <xref:System.Collections.IEnumerable> interface, which requires that the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method be implemented.</span></span>

<span data-ttu-id="f2ad0-210">Yöntem `GetEnumerator` sınıfın bir örneğini `ColorEnumerator` döndürür.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-210">The `GetEnumerator` method returns an instance of the `ColorEnumerator` class.</span></span> <span data-ttu-id="f2ad0-211">`ColorEnumerator`özelliğin, <xref:System.Collections.IEnumerator> <xref:System.Collections.IEnumerator.MoveNext%2A> yöntemin ve <xref:System.Collections.IEnumerator.Reset%2A> <xref:System.Collections.IEnumerator.Current%2A> yöntemin uygulanmasını gerektiren arabirimi uygular.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-211">`ColorEnumerator` implements the <xref:System.Collections.IEnumerator> interface, which requires that the <xref:System.Collections.IEnumerator.Current%2A> property, <xref:System.Collections.IEnumerator.MoveNext%2A> method, and <xref:System.Collections.IEnumerator.Reset%2A> method be implemented.</span></span>

```vb
Public Sub ListColors()
    Dim colors As New AllColors()

    For Each theColor As Color In colors
        Console.Write(theColor.Name & " ")
    Next
    Console.WriteLine()
    ' Output: red blue green
End Sub

' Collection class.
Public Class AllColors
    Implements System.Collections.IEnumerable

    Private _colors() As Color =
    {
        New Color With {.Name = "red"},
        New Color With {.Name = "blue"},
        New Color With {.Name = "green"}
    }

    Public Function GetEnumerator() As System.Collections.IEnumerator _
        Implements System.Collections.IEnumerable.GetEnumerator

        Return New ColorEnumerator(_colors)

        ' Instead of creating a custom enumerator, you could
        ' use the GetEnumerator of the array.
        'Return _colors.GetEnumerator
    End Function

    ' Custom enumerator.
    Private Class ColorEnumerator
        Implements System.Collections.IEnumerator

        Private _colors() As Color
        Private _position As Integer = -1

        Public Sub New(ByVal colors() As Color)
            _colors = colors
        End Sub

        Public ReadOnly Property Current() As Object _
            Implements System.Collections.IEnumerator.Current
            Get
                Return _colors(_position)
            End Get
        End Property

        Public Function MoveNext() As Boolean _
            Implements System.Collections.IEnumerator.MoveNext
            _position += 1
            Return (_position < _colors.Length)
        End Function

        Public Sub Reset() Implements System.Collections.IEnumerator.Reset
            _position = -1
        End Sub
    End Class
End Class

' Element class.
Public Class Color
    Public Property Name As String
End Class
```

<a name="BKMK_Iterators"></a>

## <a name="iterators"></a><span data-ttu-id="f2ad0-212">Yineleyiciler</span><span class="sxs-lookup"><span data-stu-id="f2ad0-212">Iterators</span></span>

<span data-ttu-id="f2ad0-213">Bir *yineleme,* bir koleksiyon üzerinde özel yineleme gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-213">An *iterator* is used to perform a custom iteration over a collection.</span></span> <span data-ttu-id="f2ad0-214">Bir yineleyici bir yöntem veya `get` erişimci olabilir.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-214">An iterator can be a method or a `get` accessor.</span></span> <span data-ttu-id="f2ad0-215">Bir yineleyici, koleksiyonun her öğesini birer birer döndürmek için [bir Verim](../../../visual-basic/language-reference/statements/yield-statement.md) deyimi kullanır.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-215">An iterator uses a [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) statement to return each element of the collection one at a time.</span></span>

<span data-ttu-id="f2ad0-216">Her biri için bir kullanarak bir yineleyici arama [... Sıradaki](../../../visual-basic/language-reference/statements/for-each-next-statement.md) ifade.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-216">You call an iterator by using a [For Each…Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement.</span></span> <span data-ttu-id="f2ad0-217">Döngünün `For Each` her yinelemesi yineleyiciyi çağırır.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-217">Each iteration of the `For Each` loop calls the iterator.</span></span> <span data-ttu-id="f2ad0-218">Bir `Yield` deyim yineleyicide ulaşıldığında, bir ifade döndürülür ve koddaki geçerli konum korunur.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-218">When a `Yield` statement is reached in the iterator, an expression is returned, and the current location in code is retained.</span></span> <span data-ttu-id="f2ad0-219">Yürütme, yineleyici çağrıldığında bu konumdan yeniden başlatılır.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-219">Execution is restarted from that location the next time that the iterator is called.</span></span>

<span data-ttu-id="f2ad0-220">Daha fazla bilgi için [Bkz. Yineleyiciler (Visual Basic)](../../../visual-basic/programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="f2ad0-220">For more information, see [Iterators (Visual Basic)](../../../visual-basic/programming-guide/concepts/iterators.md).</span></span>

<span data-ttu-id="f2ad0-221">Aşağıdaki örnekte bir yineleyici yöntemi kullanır.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-221">The following example uses an iterator method.</span></span> <span data-ttu-id="f2ad0-222">Yineleyici yöntemi bir For `Yield` içinde bir deyimi vardır [... Bir sonraki](../../../visual-basic/language-reference/statements/for-next-statement.md) döngü.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-222">The iterator method has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="f2ad0-223">`ListEvenNumbers` Yöntemde, deyim gövdesinin `For Each` her yinelemesi, bir sonraki `Yield` deyime devam eden yineleyici yöntemine bir çağrı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-223">In the `ListEvenNumbers` method, each iteration of the `For Each` statement body creates a call to the iterator method, which proceeds to the next `Yield` statement.</span></span>

```vb
Public Sub ListEvenNumbers()
    For Each number As Integer In EvenSequence(5, 18)
        Console.Write(number & " ")
    Next
    Console.WriteLine()
    ' Output: 6 8 10 12 14 16 18
End Sub

Private Iterator Function EvenSequence(
ByVal firstNumber As Integer, ByVal lastNumber As Integer) _
As IEnumerable(Of Integer)

' Yield even numbers in the range.
    For number = firstNumber To lastNumber
        If number Mod 2 = 0 Then
            Yield number
        End If
    Next
End Function
```

## <a name="see-also"></a><span data-ttu-id="f2ad0-224">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2ad0-224">See also</span></span>

- [<span data-ttu-id="f2ad0-225">Koleksiyon Baş harfleri</span><span class="sxs-lookup"><span data-stu-id="f2ad0-225">Collection Initializers</span></span>](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [<span data-ttu-id="f2ad0-226">Programlama Kavramları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2ad0-226">Programming Concepts (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="f2ad0-227">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="f2ad0-227">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="f2ad0-228">Nesnelere LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2ad0-228">LINQ to Objects (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [<span data-ttu-id="f2ad0-229">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="f2ad0-229">Parallel LINQ (PLINQ)</span></span>](../../../standard/parallel-programming/introduction-to-plinq.md)
- [<span data-ttu-id="f2ad0-230">Koleksiyonlar ve Veri Yapıları</span><span class="sxs-lookup"><span data-stu-id="f2ad0-230">Collections and Data Structures</span></span>](../../../standard/collections/index.md)
- [<span data-ttu-id="f2ad0-231">Koleksiyon Sınıfı Seçme</span><span class="sxs-lookup"><span data-stu-id="f2ad0-231">Selecting a Collection Class</span></span>](../../../standard/collections/selecting-a-collection-class.md)
- [<span data-ttu-id="f2ad0-232">Koleksiyonlar İçindeKi Karşılaştırmalar ve Sıralamalar</span><span class="sxs-lookup"><span data-stu-id="f2ad0-232">Comparisons and Sorts Within Collections</span></span>](../../../standard/collections/comparisons-and-sorts-within-collections.md)
- [<span data-ttu-id="f2ad0-233">Genel Koleksiyonlar Ne Zaman Kullanılır?</span><span class="sxs-lookup"><span data-stu-id="f2ad0-233">When to Use Generic Collections</span></span>](../../../standard/collections/when-to-use-generic-collections.md)
