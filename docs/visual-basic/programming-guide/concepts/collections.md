---
title: Koleksiyonlar
ms.date: 07/20/2015
ms.assetid: 5f7749f3-aaf2-4319-b63c-bfa72e1e2b7a
ms.openlocfilehash: ba16d04e781bcf69356b1f603d92e104816a0860
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347089"
---
# <a name="collections-visual-basic"></a><span data-ttu-id="b42dd-102">Koleksiyonlar (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b42dd-102">Collections (Visual Basic)</span></span>

<span data-ttu-id="b42dd-103">Birçok uygulama için ilgili nesne grupları oluşturmak ve yönetmek istersiniz.</span><span class="sxs-lookup"><span data-stu-id="b42dd-103">For many applications, you want to create and manage groups of related objects.</span></span> <span data-ttu-id="b42dd-104">Nesneleri gruplandırmanın iki yolu vardır: nesne dizileri oluşturarak ve nesne koleksiyonları oluşturarak.</span><span class="sxs-lookup"><span data-stu-id="b42dd-104">There are two ways to group objects: by creating arrays of objects, and by creating collections of objects.</span></span>

<span data-ttu-id="b42dd-105">Diziler, kesin olarak belirlenmiş sabit sayıda nesne oluşturmak ve bunlarla çalışmak için en yararlı seçenektir.</span><span class="sxs-lookup"><span data-stu-id="b42dd-105">Arrays are most useful for creating and working with a fixed number of strongly-typed objects.</span></span> <span data-ttu-id="b42dd-106">Diziler hakkında daha fazla bilgi için bkz. [diziler](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="b42dd-106">For information about arrays, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>

<span data-ttu-id="b42dd-107">Koleksiyonlar, nesne gruplarıyla çalışmak için daha esnek bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="b42dd-107">Collections provide a more flexible way to work with groups of objects.</span></span> <span data-ttu-id="b42dd-108">Dizilerden farklı olarak, çalıştığınız nesne grubu, uygulama değişikliğinin ihtiyaçlarına göre dinamik olarak büyüyebilir ve küçülebilir.</span><span class="sxs-lookup"><span data-stu-id="b42dd-108">Unlike arrays, the group of objects you work with can grow and shrink dynamically as the needs of the application change.</span></span> <span data-ttu-id="b42dd-109">Bazı koleksiyonlar için, anahtarı kullanarak nesneyi hızlı bir şekilde alabilmeniz için koleksiyona yerleştirdiğiniz herhangi bir nesneye bir anahtar atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b42dd-109">For some collections, you can assign a key to any object that you put into the collection so that you can quickly retrieve the object by using the key.</span></span>

<span data-ttu-id="b42dd-110">Koleksiyon bir sınıftır, bu nedenle bu koleksiyona öğe ekleyebilmeniz için önce sınıfın bir örneğini bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b42dd-110">A collection is a class, so you must declare an instance of the class before you can add elements to that collection.</span></span>

<span data-ttu-id="b42dd-111">Koleksiyonunuz yalnızca bir veri türünün öğelerini içeriyorsa, <xref:System.Collections.Generic?displayProperty=nameWithType> ad alanındaki sınıflardan birini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b42dd-111">If your collection contains elements of only one data type, you can use one of the classes in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="b42dd-112">Genel bir koleksiyon, tür güvenliğini, başka bir veri türü eklenememesi için uygular.</span><span class="sxs-lookup"><span data-stu-id="b42dd-112">A generic collection enforces type safety so that no other data type can be added to it.</span></span> <span data-ttu-id="b42dd-113">Genel koleksiyondan bir öğe aldığınızda, veri türünü belirlememek veya dönüştürmek zorunda değilsiniz.</span><span class="sxs-lookup"><span data-stu-id="b42dd-113">When you retrieve an element from a generic collection, you do not have to determine its data type or convert it.</span></span>

> [!NOTE]
> <span data-ttu-id="b42dd-114">Bu konudaki örnekler için, `System.Collections.Generic` ve `System.Linq` ad alanları için [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) deyimlerini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b42dd-114">For the examples in this topic, include [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) statements for the `System.Collections.Generic` and `System.Linq` namespaces.</span></span>

<a name="BKMK_SimpleCollection"></a>

## <a name="using-a-simple-collection"></a><span data-ttu-id="b42dd-115">Basit bir koleksiyon kullanma</span><span class="sxs-lookup"><span data-stu-id="b42dd-115">Using a Simple Collection</span></span>

<span data-ttu-id="b42dd-116">Bu bölümdeki örneklerde, türü kesin belirlenmiş bir nesne listesiyle çalışmanıza olanak sağlayan genel <xref:System.Collections.Generic.List%601> sınıfını kullanın.</span><span class="sxs-lookup"><span data-stu-id="b42dd-116">The examples in this section use the generic <xref:System.Collections.Generic.List%601> class, which enables you to work with a strongly typed list of objects.</span></span>

<span data-ttu-id="b42dd-117">Aşağıdaki örnek, dizelerin bir listesini oluşturur ve sonra her biri Için bir kullanarak dizeler arasında yinelenir [... Sonraki](../../../visual-basic/language-reference/statements/for-each-next-statement.md) ifade.</span><span class="sxs-lookup"><span data-stu-id="b42dd-117">The following example creates a list of strings and then iterates through the strings by using a [For Each…Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement.</span></span>

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

<span data-ttu-id="b42dd-118">Bir koleksiyonun içeriği önceden biliniyorsa, koleksiyonu başlatmak için bir *koleksiyon başlatıcısı* kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b42dd-118">If the contents of a collection are known in advance, you can use a *collection initializer* to initialize the collection.</span></span> <span data-ttu-id="b42dd-119">Daha fazla bilgi için bkz. [koleksiyon başlatıcıları](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).</span><span class="sxs-lookup"><span data-stu-id="b42dd-119">For more information, see [Collection Initializers](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).</span></span>

<span data-ttu-id="b42dd-120">Aşağıdaki örnek, koleksiyona öğe eklemek için bir koleksiyon başlatıcısı kullanılması dışında, önceki örnekle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="b42dd-120">The following example is the same as the previous example, except a collection initializer is used to add elements to the collection.</span></span>

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

<span data-ttu-id="b42dd-121">Için bir kullanabilirsiniz... [ ](../../../visual-basic/language-reference/statements/for-next-statement.md)Bir koleksiyon üzerinden yinelemek için bir `For Each` deyimin yerine Next ifadesinin.</span><span class="sxs-lookup"><span data-stu-id="b42dd-121">You can use a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) statement instead of a `For Each` statement to iterate through a collection.</span></span> <span data-ttu-id="b42dd-122">Bunu, koleksiyon öğelerine dizin konumuna erişerek gerçekleştirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b42dd-122">You accomplish this by accessing the collection elements by the index position.</span></span> <span data-ttu-id="b42dd-123">Öğelerin dizini 0 ' dan başlar ve öğe sayısı eksi 1 ' den sona erer.</span><span class="sxs-lookup"><span data-stu-id="b42dd-123">The index of the elements starts at 0 and ends at the element count minus 1.</span></span>

<span data-ttu-id="b42dd-124">Aşağıdaki örnek, `For Each`yerine `For…Next` kullanarak bir koleksiyonun öğeleri boyunca yinelenir.</span><span class="sxs-lookup"><span data-stu-id="b42dd-124">The following example iterates through the elements of a collection by using `For…Next` instead of `For Each`.</span></span>

```vb
Dim salmons As New List(Of String) From
    {"chinook", "coho", "pink", "sockeye"}

For index = 0 To salmons.Count - 1
    Console.Write(salmons(index) & " ")
Next
'Output: chinook coho pink sockeye
```

<span data-ttu-id="b42dd-125">Aşağıdaki örnek, kaldırılacak nesneyi belirterek koleksiyondan bir öğeyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="b42dd-125">The following example removes an element from the collection by specifying the object to remove.</span></span>

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

<span data-ttu-id="b42dd-126">Aşağıdaki örnek, genel bir listeden öğeleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="b42dd-126">The following example removes elements from a generic list.</span></span> <span data-ttu-id="b42dd-127">`For Each`, Için a... [ ](../../../visual-basic/language-reference/statements/for-next-statement.md)Azalan sırada yinelenen bir sonraki ifade kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b42dd-127">Instead of a `For Each` statement, a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) statement that iterates in descending order is used.</span></span> <span data-ttu-id="b42dd-128">Bunun nedeni <xref:System.Collections.Generic.List%601.RemoveAt%2A> yöntemi kaldırılan bir öğeden sonra öğelerin daha düşük bir dizin değerine sahip olmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="b42dd-128">This is because the <xref:System.Collections.Generic.List%601.RemoveAt%2A> method causes elements after a removed element to have a lower index value.</span></span>

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

<span data-ttu-id="b42dd-129"><xref:System.Collections.Generic.List%601>öğe türü için kendi sınıfınızı de tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b42dd-129">For the type of elements in the <xref:System.Collections.Generic.List%601>, you can also define your own class.</span></span> <span data-ttu-id="b42dd-130">Aşağıdaki örnekte, <xref:System.Collections.Generic.List%601> tarafından kullanılan `Galaxy` sınıfı kodda tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="b42dd-130">In the following example, the `Galaxy` class that is used by the <xref:System.Collections.Generic.List%601> is defined in the code.</span></span>

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

## <a name="kinds-of-collections"></a><span data-ttu-id="b42dd-131">Koleksiyon türleri</span><span class="sxs-lookup"><span data-stu-id="b42dd-131">Kinds of Collections</span></span>

<span data-ttu-id="b42dd-132">Birçok ortak koleksiyon .NET Framework tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="b42dd-132">Many common collections are provided by the .NET Framework.</span></span> <span data-ttu-id="b42dd-133">Her koleksiyon türü belirli bir amaç için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="b42dd-133">Each type of collection is designed for a specific purpose.</span></span>

<span data-ttu-id="b42dd-134">Ortak koleksiyon sınıflarından bazıları bu bölümde açıklanmıştır:</span><span class="sxs-lookup"><span data-stu-id="b42dd-134">Some of the common collection classes are described in this section:</span></span>

- <span data-ttu-id="b42dd-135"><xref:System.Collections.Generic> sınıflar</span><span class="sxs-lookup"><span data-stu-id="b42dd-135"><xref:System.Collections.Generic> classes</span></span>

- <span data-ttu-id="b42dd-136"><xref:System.Collections.Concurrent> sınıflar</span><span class="sxs-lookup"><span data-stu-id="b42dd-136"><xref:System.Collections.Concurrent> classes</span></span>

- <span data-ttu-id="b42dd-137"><xref:System.Collections> sınıflar</span><span class="sxs-lookup"><span data-stu-id="b42dd-137"><xref:System.Collections> classes</span></span>

- <span data-ttu-id="b42dd-138">Visual Basic `Collection` sınıfı</span><span class="sxs-lookup"><span data-stu-id="b42dd-138">Visual Basic `Collection` class</span></span>

<a name="BKMK_Generic"></a>

### <a name="systemcollectionsgeneric-classes"></a><span data-ttu-id="b42dd-139">System. Collections. Generic sınıfları</span><span class="sxs-lookup"><span data-stu-id="b42dd-139">System.Collections.Generic Classes</span></span>

<span data-ttu-id="b42dd-140"><xref:System.Collections.Generic> ad alanındaki sınıflardan birini kullanarak genel bir koleksiyon oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b42dd-140">You can create a generic collection by using one of the classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="b42dd-141">Genel bir koleksiyon, koleksiyondaki her öğe aynı veri türüne sahip olduğunda faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="b42dd-141">A generic collection is useful when every item in the collection has the same data type.</span></span> <span data-ttu-id="b42dd-142">Genel bir koleksiyon, yalnızca istenen veri türünün eklenmesine izin vererek güçlü yazma uygular.</span><span class="sxs-lookup"><span data-stu-id="b42dd-142">A generic collection enforces strong typing by allowing only the desired data type to be added.</span></span>

<span data-ttu-id="b42dd-143">Aşağıdaki tabloda <xref:System.Collections.Generic?displayProperty=nameWithType> ad alanının sık kullanılan sınıflarının bazıları listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="b42dd-143">The following table lists some of the frequently used classes of the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace:</span></span>

|<span data-ttu-id="b42dd-144">Sınıf</span><span class="sxs-lookup"><span data-stu-id="b42dd-144">Class</span></span>|<span data-ttu-id="b42dd-145">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b42dd-145">Description</span></span>|
|---|---|
|<xref:System.Collections.Generic.Dictionary%602>|<span data-ttu-id="b42dd-146">Anahtara göre düzenlenen anahtar/değer çiftleri koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b42dd-146">Represents a collection of key/value pairs that are organized based on the key.</span></span>|
|<xref:System.Collections.Generic.List%601>|<span data-ttu-id="b42dd-147">Dizin tarafından erişilebilen nesnelerin listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b42dd-147">Represents a list of objects that can be accessed by index.</span></span> <span data-ttu-id="b42dd-148">Listeleri aramak, sıralamak ve değiştirmek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b42dd-148">Provides methods to search, sort, and modify lists.</span></span>|
|<xref:System.Collections.Generic.Queue%601>|<span data-ttu-id="b42dd-149">Nesnelerin ilk, ilk çıkar (FıFO) koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b42dd-149">Represents a first in, first out (FIFO) collection of objects.</span></span>|
|<xref:System.Collections.Generic.SortedList%602>|<span data-ttu-id="b42dd-150">İlişkili <xref:System.Collections.Generic.IComparer%601> uygulamasına göre anahtara göre sıralanan anahtar/değer çiftleri koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b42dd-150">Represents a collection of key/value pairs that are sorted by key based on the associated <xref:System.Collections.Generic.IComparer%601> implementation.</span></span>|
|<xref:System.Collections.Generic.Stack%601>|<span data-ttu-id="b42dd-151">Nesnelerin son, ilk çıkar (LıFO) koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b42dd-151">Represents a last in, first out (LIFO) collection of objects.</span></span>|

<span data-ttu-id="b42dd-152">Daha fazla bilgi için bkz. [yaygın olarak kullanılan koleksiyon türleri](../../../standard/collections/commonly-used-collection-types.md), [bir koleksiyon sınıfı seçme](../../../standard/collections/selecting-a-collection-class.md)ve <xref:System.Collections.Generic?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b42dd-152">For additional information, see [Commonly Used Collection Types](../../../standard/collections/commonly-used-collection-types.md), [Selecting a Collection Class](../../../standard/collections/selecting-a-collection-class.md), and <xref:System.Collections.Generic?displayProperty=nameWithType>.</span></span>

<a name="BKMK_Concurrent"></a>

### <a name="systemcollectionsconcurrent-classes"></a><span data-ttu-id="b42dd-153">System. Collections. eşzamanlı sınıflar</span><span class="sxs-lookup"><span data-stu-id="b42dd-153">System.Collections.Concurrent Classes</span></span>

<span data-ttu-id="b42dd-154">.NET Framework 4 veya daha yeni bir sürümde, <xref:System.Collections.Concurrent> ad alanındaki koleksiyonlar, koleksiyon öğelerine birden çok iş parçacığından erişmek için verimli iş parçacığı güvenli işlemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="b42dd-154">In the .NET Framework 4 or newer, the collections in the <xref:System.Collections.Concurrent> namespace provide efficient thread-safe operations for accessing collection items from multiple threads.</span></span>

<span data-ttu-id="b42dd-155"><xref:System.Collections.Concurrent> ad alanındaki sınıflar, koleksiyona aynı anda birden çok iş parçacığı eriştiği zaman, <xref:System.Collections.Generic?displayProperty=nameWithType> ve <xref:System.Collections?displayProperty=nameWithType> ad alanlarında karşılık gelen türler yerine kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b42dd-155">The classes in the <xref:System.Collections.Concurrent> namespace should be used instead of the corresponding types in the <xref:System.Collections.Generic?displayProperty=nameWithType> and <xref:System.Collections?displayProperty=nameWithType> namespaces whenever multiple threads are accessing the collection concurrently.</span></span> <span data-ttu-id="b42dd-156">Daha fazla bilgi için bkz. [Iş parçacığı güvenli koleksiyonlar](../../../standard/collections/thread-safe/index.md) ve <xref:System.Collections.Concurrent>.</span><span class="sxs-lookup"><span data-stu-id="b42dd-156">For more information, see [Thread-Safe Collections](../../../standard/collections/thread-safe/index.md) and <xref:System.Collections.Concurrent>.</span></span>

<span data-ttu-id="b42dd-157"><xref:System.Collections.Concurrent> ad alanına eklenen bazı sınıflar <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>ve <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span><span class="sxs-lookup"><span data-stu-id="b42dd-157">Some classes included in the <xref:System.Collections.Concurrent> namespace are <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>

<a name="BKMK_Collections"></a>

### <a name="systemcollections-classes"></a><span data-ttu-id="b42dd-158">System. Collections sınıfları</span><span class="sxs-lookup"><span data-stu-id="b42dd-158">System.Collections Classes</span></span>

<span data-ttu-id="b42dd-159"><xref:System.Collections?displayProperty=nameWithType> ad alanındaki sınıflar öğeleri özel olarak yazılmış nesneler olarak depolamaz, ancak `Object`türündeki nesneler.</span><span class="sxs-lookup"><span data-stu-id="b42dd-159">The classes in the <xref:System.Collections?displayProperty=nameWithType> namespace do not store elements as specifically typed objects, but as objects of type `Object`.</span></span>

<span data-ttu-id="b42dd-160">Mümkün olduğunda, <xref:System.Collections.Generic?displayProperty=nameWithType> ad alanındaki genel koleksiyonları veya `System.Collections` ad alanındaki eski türler yerine <xref:System.Collections.Concurrent> ad alanını kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b42dd-160">Whenever possible, you should use the generic collections in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace or the <xref:System.Collections.Concurrent> namespace instead of the legacy types in the `System.Collections` namespace.</span></span>

<span data-ttu-id="b42dd-161">Aşağıdaki tabloda `System.Collections` ad alanında sık kullanılan sınıfların bazıları listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="b42dd-161">The following table lists some of the frequently used classes in the `System.Collections` namespace:</span></span>

|<span data-ttu-id="b42dd-162">Sınıf</span><span class="sxs-lookup"><span data-stu-id="b42dd-162">Class</span></span>|<span data-ttu-id="b42dd-163">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b42dd-163">Description</span></span>|
|---|---|
|<xref:System.Collections.ArrayList>|<span data-ttu-id="b42dd-164">Boyutu dinamik olarak gerektiği şekilde arttığı bir nesne dizisini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b42dd-164">Represents an array of objects whose size is dynamically increased as required.</span></span>|
|<xref:System.Collections.Hashtable>|<span data-ttu-id="b42dd-165">Anahtarın karma koduna göre düzenlenmiş anahtar/değer çiftleri koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b42dd-165">Represents a collection of key/value pairs that are organized based on the hash code of the key.</span></span>|
|<xref:System.Collections.Queue>|<span data-ttu-id="b42dd-166">Nesnelerin ilk, ilk çıkar (FıFO) koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b42dd-166">Represents a first in, first out (FIFO) collection of objects.</span></span>|
|<xref:System.Collections.Stack>|<span data-ttu-id="b42dd-167">Nesnelerin son, ilk çıkar (LıFO) koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b42dd-167">Represents a last in, first out (LIFO) collection of objects.</span></span>|

<span data-ttu-id="b42dd-168"><xref:System.Collections.Specialized> ad alanı, yalnızca dize toplamaları ve bağlantılı liste ve karma sözlük gibi özelleştirilmiş ve kesin tür belirtilmiş koleksiyon sınıfları sağlar.</span><span class="sxs-lookup"><span data-stu-id="b42dd-168">The <xref:System.Collections.Specialized> namespace provides specialized and strongly typed collection classes, such as string-only collections and linked-list and hybrid dictionaries.</span></span>

<a name="BKMK_VisualBasic"></a>

### <a name="visual-basic-collection-class"></a><span data-ttu-id="b42dd-169">Visual Basic Collection sınıfı</span><span class="sxs-lookup"><span data-stu-id="b42dd-169">Visual Basic Collection Class</span></span>

<span data-ttu-id="b42dd-170">Sayısal bir dizin veya `String` anahtarı kullanarak bir koleksiyon öğesine erişmek için Visual Basic <xref:Microsoft.VisualBasic.Collection> sınıfını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b42dd-170">You can use the Visual Basic <xref:Microsoft.VisualBasic.Collection> class to access a collection item by using either a numeric index or a `String` key.</span></span> <span data-ttu-id="b42dd-171">Bir koleksiyon nesnesine, anahtar belirtmeden ya da belirtmeden öğe ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b42dd-171">You can add items to a collection object either with or without specifying a key.</span></span> <span data-ttu-id="b42dd-172">Anahtar içermeyen bir öğe eklerseniz, ona erişmek için sayısal dizinini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b42dd-172">If you add an item without a key, you must use its numeric index to access it.</span></span>

<span data-ttu-id="b42dd-173">Visual Basic `Collection` sınıfı tüm öğelerini tür `Object`olarak depolar, böylece herhangi bir veri türü için bir öğe ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b42dd-173">The Visual Basic `Collection` class stores all its elements as type `Object`, so you can add an item of any data type.</span></span> <span data-ttu-id="b42dd-174">Eklenmekte olan uygunsuz veri türlerine karşı bir koruma yoktur.</span><span class="sxs-lookup"><span data-stu-id="b42dd-174">There is no safeguard against inappropriate data types being added.</span></span>

<span data-ttu-id="b42dd-175">Visual Basic `Collection` sınıfını kullandığınızda, bir koleksiyondaki ilk öğenin dizini 1 ' dir.</span><span class="sxs-lookup"><span data-stu-id="b42dd-175">When you use the Visual Basic `Collection` class, the first item in a collection has an index of 1.</span></span> <span data-ttu-id="b42dd-176">Bu, Başlangıç dizininin 0 olduğu .NET Framework koleksiyon sınıflarından farklıdır.</span><span class="sxs-lookup"><span data-stu-id="b42dd-176">This differs from the .NET Framework collection classes, for which the starting index is 0.</span></span>

<span data-ttu-id="b42dd-177">Mümkün olduğunda, <xref:System.Collections.Generic?displayProperty=nameWithType> ad alanındaki genel koleksiyonları veya Visual Basic `Collection` sınıfı yerine <xref:System.Collections.Concurrent> ad alanını kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b42dd-177">Whenever possible, you should use the generic collections in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace or the <xref:System.Collections.Concurrent> namespace instead of the Visual Basic `Collection` class.</span></span>

<span data-ttu-id="b42dd-178">Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Collection>.</span><span class="sxs-lookup"><span data-stu-id="b42dd-178">For more information, see <xref:Microsoft.VisualBasic.Collection>.</span></span>

<a name="BKMK_KeyValuePairs"></a>

## <a name="implementing-a-collection-of-keyvalue-pairs"></a><span data-ttu-id="b42dd-179">Anahtar/değer çiftleri koleksiyonu uygulama</span><span class="sxs-lookup"><span data-stu-id="b42dd-179">Implementing a Collection of Key/Value Pairs</span></span>

<span data-ttu-id="b42dd-180"><xref:System.Collections.Generic.Dictionary%602> genel koleksiyonu, her bir öğenin anahtarını kullanarak bir koleksiyondaki öğelere erişmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b42dd-180">The <xref:System.Collections.Generic.Dictionary%602> generic collection enables you to access to elements in a collection by using the key of each element.</span></span> <span data-ttu-id="b42dd-181">Sözlüğe eklenen her ekleme bir değerden ve ilişkili anahtarından oluşur.</span><span class="sxs-lookup"><span data-stu-id="b42dd-181">Each addition to the dictionary consists of a value and its associated key.</span></span> <span data-ttu-id="b42dd-182">`Dictionary` sınıfı bir karma tablo olarak uygulandığından, anahtarını kullanarak bir değerin alınması hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="b42dd-182">Retrieving a value by using its key is fast because the `Dictionary` class is implemented as a hash table.</span></span>

<span data-ttu-id="b42dd-183">Aşağıdaki örnek bir `Dictionary` koleksiyonu oluşturur ve bir `For Each` ifadesini kullanarak sözlükten yinelenir.</span><span class="sxs-lookup"><span data-stu-id="b42dd-183">The following example creates a `Dictionary` collection and iterates through the dictionary by using a `For Each` statement.</span></span>

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

<span data-ttu-id="b42dd-184">Bunun yerine, `Dictionary` koleksiyonunu oluşturmak için bir koleksiyon başlatıcısı kullanmak için, `BuildDictionary` ve `AddToDictionary` yöntemlerini aşağıdaki yöntemle değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b42dd-184">To instead use a collection initializer to build the `Dictionary` collection, you can replace the `BuildDictionary` and `AddToDictionary` methods with the following method.</span></span>

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

<span data-ttu-id="b42dd-185">Aşağıdaki örnek, bir öğeyi anahtara göre hızlı bir şekilde bulmak için `Dictionary` <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> yöntemini ve <xref:System.Collections.Generic.Dictionary%602.Item%2A> özelliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="b42dd-185">The following example uses the <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> method and the <xref:System.Collections.Generic.Dictionary%602.Item%2A> property of `Dictionary` to quickly find an item by key.</span></span> <span data-ttu-id="b42dd-186">`Item` özelliği, Visual Basic `elements(symbol)` kodu kullanarak `elements` koleksiyonundaki bir öğeye erişmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b42dd-186">The `Item` property enables you to access an item in the `elements` collection by using the `elements(symbol)` code in Visual Basic.</span></span>

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

<span data-ttu-id="b42dd-187">Aşağıdaki örnek bunun yerine, bir öğeyi anahtara göre hızlı bir şekilde bulmak <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="b42dd-187">The following example instead uses the <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> method quickly find an item by key.</span></span>

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

## <a name="using-linq-to-access-a-collection"></a><span data-ttu-id="b42dd-188">Koleksiyona erişmek için LINQ kullanma</span><span class="sxs-lookup"><span data-stu-id="b42dd-188">Using LINQ to Access a Collection</span></span>

<span data-ttu-id="b42dd-189">LINQ (dil ile tümleşik sorgu), koleksiyonlara erişmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b42dd-189">LINQ (Language-Integrated Query) can be used to access collections.</span></span> <span data-ttu-id="b42dd-190">LINQ sorguları filtreleme, sıralama ve gruplama özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="b42dd-190">LINQ queries provide filtering, ordering, and grouping capabilities.</span></span> <span data-ttu-id="b42dd-191">Daha fazla bilgi için bkz. [VISUAL BASIC LINQ Ile çalışmaya](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)başlama.</span><span class="sxs-lookup"><span data-stu-id="b42dd-191">For more information, see [Getting Started with LINQ in Visual Basic](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).</span></span>

<span data-ttu-id="b42dd-192">Aşağıdaki örnek, bir genel `List`karşı bir LINQ sorgusu çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="b42dd-192">The following example runs a LINQ query against a generic `List`.</span></span> <span data-ttu-id="b42dd-193">LINQ sorgusu, sonuçları içeren farklı bir koleksiyon döndürür.</span><span class="sxs-lookup"><span data-stu-id="b42dd-193">The LINQ query returns a different collection that contains the results.</span></span>

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

## <a name="sorting-a-collection"></a><span data-ttu-id="b42dd-194">Bir koleksiyonu sıralama</span><span class="sxs-lookup"><span data-stu-id="b42dd-194">Sorting a Collection</span></span>

<span data-ttu-id="b42dd-195">Aşağıdaki örnek bir koleksiyonu sıralamak için bir yordam gösterir.</span><span class="sxs-lookup"><span data-stu-id="b42dd-195">The following example illustrates a procedure for sorting a collection.</span></span> <span data-ttu-id="b42dd-196">Örnek, bir <xref:System.Collections.Generic.List%601>depolanan `Car` sınıfının örneklerini sıralar.</span><span class="sxs-lookup"><span data-stu-id="b42dd-196">The example sorts instances of the `Car` class that are stored in a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="b42dd-197">`Car` sınıfı, <xref:System.IComparable%601.CompareTo%2A> yönteminin uygulanması için <xref:System.IComparable%601> arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="b42dd-197">The `Car` class implements the <xref:System.IComparable%601> interface, which requires that the <xref:System.IComparable%601.CompareTo%2A> method be implemented.</span></span>

<span data-ttu-id="b42dd-198"><xref:System.IComparable%601.CompareTo%2A> yöntemine yapılan her çağrı, sıralama için kullanılan tek bir karşılaştırma yapar.</span><span class="sxs-lookup"><span data-stu-id="b42dd-198">Each call to the <xref:System.IComparable%601.CompareTo%2A> method makes a single comparison that is used for sorting.</span></span> <span data-ttu-id="b42dd-199">`CompareTo` yönteminde Kullanıcı tarafından yazılan kod, geçerli nesnenin her karşılaştırması için başka bir nesneyle ilgili bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="b42dd-199">User-written code in the `CompareTo` method returns a value for each comparison of the current object with another object.</span></span> <span data-ttu-id="b42dd-200">Geçerli nesne diğer nesneden daha küçükse döndürülen değer sıfırdan küçük, geçerli nesne diğer nesneden büyükse sıfırdan büyük ve eşitse sıfır.</span><span class="sxs-lookup"><span data-stu-id="b42dd-200">The value returned is less than zero if the current object is less than the other object, greater than zero if the current object is greater than the other object, and zero if they are equal.</span></span> <span data-ttu-id="b42dd-201">Bu, büyük, küçüktür ve eşittir ölçütlerine göre kod içinde tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b42dd-201">This enables you to define in code the criteria for greater than, less than, and equal.</span></span>

<span data-ttu-id="b42dd-202">`ListCars` yönteminde, `cars.Sort()` ifade listeyi sıralar.</span><span class="sxs-lookup"><span data-stu-id="b42dd-202">In the `ListCars` method, the `cars.Sort()` statement sorts the list.</span></span> <span data-ttu-id="b42dd-203"><xref:System.Collections.Generic.List%601> <xref:System.Collections.Generic.List%601.Sort%2A> yöntemine yapılan bu çağrı, `CompareTo` yönteminin `List``Car` nesneler için otomatik olarak çağrılmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="b42dd-203">This call to the <xref:System.Collections.Generic.List%601.Sort%2A> method of the <xref:System.Collections.Generic.List%601> causes the `CompareTo` method to be called automatically for the `Car` objects in the `List`.</span></span>

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

## <a name="defining-a-custom-collection"></a><span data-ttu-id="b42dd-204">Özel bir koleksiyon tanımlama</span><span class="sxs-lookup"><span data-stu-id="b42dd-204">Defining a Custom Collection</span></span>

<span data-ttu-id="b42dd-205"><xref:System.Collections.Generic.IEnumerable%601> veya <xref:System.Collections.IEnumerable> arabirimini uygulayarak bir koleksiyon tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b42dd-205">You can define a collection by implementing the <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="b42dd-206">Daha fazla bilgi için bkz. [bir koleksiyonu numaralandırma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hwyysy67(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="b42dd-206">For additional information, see [Enumerating a Collection](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hwyysy67(v=vs.100)).</span></span>

<span data-ttu-id="b42dd-207">Özel bir koleksiyon tanımlamanızı mümkün olsa da, bu konunun önceki kısımlarında yer alan [koleksiyonlar türlerinde](#kinds-of-collections) açıklanan .NET Framework dahil edilen koleksiyonları kullanmak genellikle daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="b42dd-207">Although you can define a custom collection, it is usually better to instead use the collections that are included in the .NET Framework, which are described in [Kinds of Collections](#kinds-of-collections) earlier in this topic.</span></span>

<span data-ttu-id="b42dd-208">Aşağıdaki örnek, `AllColors`adlı bir özel koleksiyon sınıfını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b42dd-208">The following example defines a custom collection class named `AllColors`.</span></span> <span data-ttu-id="b42dd-209">Bu sınıf, <xref:System.Collections.IEnumerable.GetEnumerator%2A> yönteminin uygulanması için <xref:System.Collections.IEnumerable> arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="b42dd-209">This class implements the <xref:System.Collections.IEnumerable> interface, which requires that the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method be implemented.</span></span>

<span data-ttu-id="b42dd-210">`GetEnumerator` yöntemi `ColorEnumerator` sınıfının bir örneğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="b42dd-210">The `GetEnumerator` method returns an instance of the `ColorEnumerator` class.</span></span> <span data-ttu-id="b42dd-211">`ColorEnumerator`, <xref:System.Collections.IEnumerator.Current%2A> özelliğinin, <xref:System.Collections.IEnumerator.MoveNext%2A> yönteminin ve <xref:System.Collections.IEnumerator.Reset%2A> yönteminin uygulanması için <xref:System.Collections.IEnumerator> arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="b42dd-211">`ColorEnumerator` implements the <xref:System.Collections.IEnumerator> interface, which requires that the <xref:System.Collections.IEnumerator.Current%2A> property, <xref:System.Collections.IEnumerator.MoveNext%2A> method, and <xref:System.Collections.IEnumerator.Reset%2A> method be implemented.</span></span>

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

## <a name="iterators"></a><span data-ttu-id="b42dd-212">Yineleyiciler</span><span class="sxs-lookup"><span data-stu-id="b42dd-212">Iterators</span></span>

<span data-ttu-id="b42dd-213">Bir *Yineleyici* , bir koleksiyon üzerinde özel bir yineleme gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b42dd-213">An *iterator* is used to perform a custom iteration over a collection.</span></span> <span data-ttu-id="b42dd-214">Yineleyici bir yöntem veya `get` erişimcisi olabilir.</span><span class="sxs-lookup"><span data-stu-id="b42dd-214">An iterator can be a method or a `get` accessor.</span></span> <span data-ttu-id="b42dd-215">Bir yineleyici, tek seferde koleksiyonun her bir öğesini döndürmek için bir [yield](../../../visual-basic/language-reference/statements/yield-statement.md) ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="b42dd-215">An iterator uses a [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) statement to return each element of the collection one at a time.</span></span>

<span data-ttu-id="b42dd-216">Her biri Için bir yineleyiciyi kullanarak bir yineleyici çağırın [... Sonraki](../../../visual-basic/language-reference/statements/for-each-next-statement.md) ifade.</span><span class="sxs-lookup"><span data-stu-id="b42dd-216">You call an iterator by using a [For Each…Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement.</span></span> <span data-ttu-id="b42dd-217">`For Each` döngüsünün her yinelemesi yineleyiciyi çağırır.</span><span class="sxs-lookup"><span data-stu-id="b42dd-217">Each iteration of the `For Each` loop calls the iterator.</span></span> <span data-ttu-id="b42dd-218">Yineleyiciden bir `Yield` deyimine ulaşıldığında, bir ifade döndürülür ve koddaki geçerli konum korunur.</span><span class="sxs-lookup"><span data-stu-id="b42dd-218">When a `Yield` statement is reached in the iterator, an expression is returned, and the current location in code is retained.</span></span> <span data-ttu-id="b42dd-219">Bu konumdan, yineleyici bir sonraki sefer çağrıldığında yürütme yeniden başlatılır.</span><span class="sxs-lookup"><span data-stu-id="b42dd-219">Execution is restarted from that location the next time that the iterator is called.</span></span>

<span data-ttu-id="b42dd-220">Daha fazla bilgi için bkz. [yineleyiciler (Visual Basic)](../../../visual-basic/programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="b42dd-220">For more information, see [Iterators (Visual Basic)](../../../visual-basic/programming-guide/concepts/iterators.md).</span></span>

<span data-ttu-id="b42dd-221">Aşağıdaki örnek bir yineleyici yöntemi kullanır.</span><span class="sxs-lookup"><span data-stu-id="b42dd-221">The following example uses an iterator method.</span></span> <span data-ttu-id="b42dd-222">Yineleyici yöntemi bir for... içinde olan bir `Yield` ifadeye sahiptir [... Sonraki](../../../visual-basic/language-reference/statements/for-next-statement.md) döngü.</span><span class="sxs-lookup"><span data-stu-id="b42dd-222">The iterator method has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="b42dd-223">`ListEvenNumbers` yönteminde, `For Each` deyimin gövdesinin her yinelemesi, bir sonraki `Yield` ifadesine devam eden Yineleyici yöntemine bir çağrı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b42dd-223">In the `ListEvenNumbers` method, each iteration of the `For Each` statement body creates a call to the iterator method, which proceeds to the next `Yield` statement.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b42dd-224">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b42dd-224">See also</span></span>

- [<span data-ttu-id="b42dd-225">Öğe Başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="b42dd-225">Collection Initializers</span></span>](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [<span data-ttu-id="b42dd-226">Programlama kavramları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b42dd-226">Programming Concepts (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="b42dd-227">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="b42dd-227">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="b42dd-228">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b42dd-228">LINQ to Objects (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [<span data-ttu-id="b42dd-229">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="b42dd-229">Parallel LINQ (PLINQ)</span></span>](../../../standard/parallel-programming/parallel-linq-plinq.md)
- [<span data-ttu-id="b42dd-230">Koleksiyonlar ve Veri Yapıları</span><span class="sxs-lookup"><span data-stu-id="b42dd-230">Collections and Data Structures</span></span>](../../../standard/collections/index.md)
- [<span data-ttu-id="b42dd-231">Koleksiyon Sınıfı Seçme</span><span class="sxs-lookup"><span data-stu-id="b42dd-231">Selecting a Collection Class</span></span>](../../../standard/collections/selecting-a-collection-class.md)
- [<span data-ttu-id="b42dd-232">Koleksiyonlardaki Karşılaştırmalar ve Sıralamalar</span><span class="sxs-lookup"><span data-stu-id="b42dd-232">Comparisons and Sorts Within Collections</span></span>](../../../standard/collections/comparisons-and-sorts-within-collections.md)
- [<span data-ttu-id="b42dd-233">Genel Koleksiyonlar Ne Zaman Kullanılır?</span><span class="sxs-lookup"><span data-stu-id="b42dd-233">When to Use Generic Collections</span></span>](../../../standard/collections/when-to-use-generic-collections.md)
