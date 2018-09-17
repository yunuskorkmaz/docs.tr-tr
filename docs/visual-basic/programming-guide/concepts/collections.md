---
title: Koleksiyonlar (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 5f7749f3-aaf2-4319-b63c-bfa72e1e2b7a
ms.openlocfilehash: 60519de1f580bf1cfa4aa067d4a999b20ea8d54d
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45685796"
---
# <a name="collections-visual-basic"></a><span data-ttu-id="de325-102">Koleksiyonlar (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="de325-102">Collections (Visual Basic)</span></span>
<span data-ttu-id="de325-103">Birçok uygulama için ilgili nesnelerin gruplarını oluşturmak ve yönetmek istersiniz.</span><span class="sxs-lookup"><span data-stu-id="de325-103">For many applications, you want to create and manage groups of related objects.</span></span> <span data-ttu-id="de325-104">Grup nesnelerini iki yolu vardır: nesne dizileri oluşturarak ve veya nesne koleksiyonu oluşturarak.</span><span class="sxs-lookup"><span data-stu-id="de325-104">There are two ways to group objects: by creating arrays of objects, and by creating collections of objects.</span></span>  
  
 <span data-ttu-id="de325-105">Dizileri oluşturmak ve nesneleri türü kesin olarak belirtilmiş sabit sayıdaki ile çalışmak için ekseriyetle faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="de325-105">Arrays are most useful for creating and working with a fixed number of strongly-typed objects.</span></span> <span data-ttu-id="de325-106">Diziler hakkında daha fazla bilgi için bkz: [diziler](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="de325-106">For information about arrays, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
 <span data-ttu-id="de325-107">Koleksiyonlar nesne grupları ile çalışmak için daha esnek bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="de325-107">Collections provide a more flexible way to work with groups of objects.</span></span> <span data-ttu-id="de325-108">Dizilerden farklı olarak çalıştığınız nesne büyütme ve uygulamanın ihtiyacına göre dinamik olarak Daralt.</span><span class="sxs-lookup"><span data-stu-id="de325-108">Unlike arrays, the group of objects you work with can grow and shrink dynamically as the needs of the application change.</span></span> <span data-ttu-id="de325-109">Bazı koleksiyonlar için koleksiyona eklediğiniz ve böylece anahtarını kullanarak hızlı bir şekilde nesnesi alabilirsiniz herhangi bir nesneye bir anahtar atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="de325-109">For some collections, you can assign a key to any object that you put into the collection so that you can quickly retrieve the object by using the key.</span></span>  
  
 <span data-ttu-id="de325-110">Bir koleksiyon bir sınıfı olduğundan bu koleksiyona öğeleri eklemeden önce sınıfının bir örneğini bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="de325-110">A collection is a class, so you must declare an instance of the class before you can add elements to that collection.</span></span>  
  
 <span data-ttu-id="de325-111">Koleksiyonunuz tek bir veri türünde öğeler içeriyorsa, sınıflarda birini kullanabilirsiniz <xref:System.Collections.Generic?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="de325-111">If your collection contains elements of only one data type, you can use one of the classes in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="de325-112">Genel koleksiyon tür güvenliği sağlar, böylece başka bir veri türü eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="de325-112">A generic collection enforces type safety so that no other data type can be added to it.</span></span> <span data-ttu-id="de325-113">Bir genel koleksiyondan öğe aldığınızda veri türünü belirlemeniz veya dönüştürmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="de325-113">When you retrieve an element from a generic collection, you do not have to determine its data type or convert it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="de325-114">Bu konudaki örnekler için dahil [içeri aktarmalar](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) deyimleri için `System.Collections.Generic` ve `System.Linq` ad alanları.</span><span class="sxs-lookup"><span data-stu-id="de325-114">For the examples in this topic, include [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) statements for the `System.Collections.Generic` and `System.Linq` namespaces.</span></span>  
  
 <span data-ttu-id="de325-115">**Bu konudaki**</span><span class="sxs-lookup"><span data-stu-id="de325-115">**In this topic**</span></span>  
  
-   [<span data-ttu-id="de325-116">Basit bir koleksiyon kullanma</span><span class="sxs-lookup"><span data-stu-id="de325-116">Using a Simple Collection</span></span>](#BKMK_SimpleCollection)  
  
-   [<span data-ttu-id="de325-117">Koleksiyon türleri</span><span class="sxs-lookup"><span data-stu-id="de325-117">Kinds of Collections</span></span>](#BKMK_KindsOfCollections)  
  
    -   [<span data-ttu-id="de325-118">System.Collections.Generic sınıfları</span><span class="sxs-lookup"><span data-stu-id="de325-118">System.Collections.Generic Classes</span></span>](#BKMK_Generic)  
  
    -   [<span data-ttu-id="de325-119">System.Collections.Concurrent sınıfları</span><span class="sxs-lookup"><span data-stu-id="de325-119">System.Collections.Concurrent Classes</span></span>](#BKMK_Concurrent)  
  
    -   [<span data-ttu-id="de325-120">System.Collections sınıfları</span><span class="sxs-lookup"><span data-stu-id="de325-120">System.Collections Classes</span></span>](#BKMK_Collections)  
  
    -   [<span data-ttu-id="de325-121">Visual Basic Collection sınıfı</span><span class="sxs-lookup"><span data-stu-id="de325-121">Visual Basic Collection Class</span></span>](#BKMK_VisualBasic)  
  
-   [<span data-ttu-id="de325-122">Anahtar/değer çiftleri topluluğu uygulama</span><span class="sxs-lookup"><span data-stu-id="de325-122">Implementing a Collection of Key/Value Pairs</span></span>](#BKMK_KeyValuePairs)  
  
-   [<span data-ttu-id="de325-123">Koleksiyona erişmek için LINQ kullanma</span><span class="sxs-lookup"><span data-stu-id="de325-123">Using LINQ to Access a Collection</span></span>](#BKMK_LINQ)  
  
-   [<span data-ttu-id="de325-124">Koleksiyonda sıralama</span><span class="sxs-lookup"><span data-stu-id="de325-124">Sorting a Collection</span></span>](#BKMK_Sorting)  
  
-   [<span data-ttu-id="de325-125">Özel koleksiyonu tanımlama</span><span class="sxs-lookup"><span data-stu-id="de325-125">Defining a Custom Collection</span></span>](#BKMK_CustomCollection)  
  
-   [<span data-ttu-id="de325-126">Yineleyiciler</span><span class="sxs-lookup"><span data-stu-id="de325-126">Iterators</span></span>](#BKMK_Iterators)  
  
<a name="BKMK_SimpleCollection"></a>
## <a name="using-a-simple-collection"></a><span data-ttu-id="de325-127">Basit bir koleksiyon kullanma</span><span class="sxs-lookup"><span data-stu-id="de325-127">Using a Simple Collection</span></span>  
 <span data-ttu-id="de325-128">Bu bölümdeki örneklerde genel kullanın <xref:System.Collections.Generic.List%601> sınıfını, bir türü kesin belirlenmiş nesneler listesiyle çalışmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="de325-128">The examples in this section use the generic <xref:System.Collections.Generic.List%601> class, which enables you to work with a strongly typed list of objects.</span></span>  
  
 <span data-ttu-id="de325-129">Aşağıdaki örnek bir dize listesi oluşturur ve ardından kullanarak dizeler arasında dolaşır bir [her biri için... Sonraki](../../../visual-basic/language-reference/statements/for-each-next-statement.md) deyimi.</span><span class="sxs-lookup"><span data-stu-id="de325-129">The following example creates a list of strings and then iterates through the strings by using a [For Each…Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement.</span></span>  
  
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
  
 <span data-ttu-id="de325-130">Bir koleksiyonun içeriği önceden biliniyorsa, kullanabileceğiniz bir *koleksiyon Başlatıcısı* koleksiyonu başlatmak için.</span><span class="sxs-lookup"><span data-stu-id="de325-130">If the contents of a collection are known in advance, you can use a *collection initializer* to initialize the collection.</span></span> <span data-ttu-id="de325-131">Daha fazla bilgi için [koleksiyon başlatıcıları](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).</span><span class="sxs-lookup"><span data-stu-id="de325-131">For more information, see [Collection Initializers](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).</span></span>  
  
 <span data-ttu-id="de325-132">Koleksiyona öğeleri eklemek için bir koleksiyon Başlatıcısı kullanılması dışında aşağıdaki örnek önceki örnekle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="de325-132">The following example is the same as the previous example, except a collection initializer is used to add elements to the collection.</span></span>  
  
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
  
 <span data-ttu-id="de325-133">Kullanabileceğiniz bir [için... Sonraki](../../../visual-basic/language-reference/statements/for-next-statement.md) deyimi yerine bir `For Each` deyimi bir koleksiyon içinde yineleme için.</span><span class="sxs-lookup"><span data-stu-id="de325-133">You can use a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) statement instead of a `For Each` statement to iterate through a collection.</span></span> <span data-ttu-id="de325-134">Bu, bir koleksiyon öğelerine dizin konumundan erişerek gerçekleştirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="de325-134">You accomplish this by accessing the collection elements by the index position.</span></span> <span data-ttu-id="de325-135">Öğelerin dizini 0'da başlar ve öğe sayısı eksi 1'de sona erer.</span><span class="sxs-lookup"><span data-stu-id="de325-135">The index of the elements starts at 0 and ends at the element count minus 1.</span></span>  
  
 <span data-ttu-id="de325-136">Aşağıdaki örneği kullanarak bir koleksiyonun öğeleri yinelenir `For…Next` yerine `For Each`.</span><span class="sxs-lookup"><span data-stu-id="de325-136">The following example iterates through the elements of a collection by using `For…Next` instead of `For Each`.</span></span>  
  
```vb  
Dim salmons As New List(Of String) From  
    {"chinook", "coho", "pink", "sockeye"}  
  
For index = 0 To salmons.Count - 1  
    Console.Write(salmons(index) & " ")  
Next  
'Output: chinook coho pink sockeye  
```  
  
 <span data-ttu-id="de325-137">Aşağıdaki örnek, bir öğe kaldırmak için nesneyi belirterek koleksiyondan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="de325-137">The following example removes an element from the collection by specifying the object to remove.</span></span>  
  
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
  
 <span data-ttu-id="de325-138">Aşağıdaki örnek bir genel listeden öğeleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="de325-138">The following example removes elements from a generic list.</span></span> <span data-ttu-id="de325-139">Yerine bir `For Each` deyimi, bir [için... Sonraki](../../../visual-basic/language-reference/statements/for-next-statement.md) azalan sırada yenileyen deyimi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="de325-139">Instead of a `For Each` statement, a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) statement that iterates in descending order is used.</span></span> <span data-ttu-id="de325-140">Bunun nedeni, <xref:System.Collections.Generic.List%601.RemoveAt%2A> yöntemi bir alt dizin değerine sahip olacak şekilde kaldırılmış bir öğeden sonra öğe neden olur.</span><span class="sxs-lookup"><span data-stu-id="de325-140">This is because the <xref:System.Collections.Generic.List%601.RemoveAt%2A> method causes elements after a removed element to have a lower index value.</span></span>  
  
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
  
 <span data-ttu-id="de325-141">İçindeki öğe türleri için <xref:System.Collections.Generic.List%601>, ayrıca kendi sınıfınızı tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="de325-141">For the type of elements in the <xref:System.Collections.Generic.List%601>, you can also define your own class.</span></span> <span data-ttu-id="de325-142">Aşağıdaki örnekte, `Galaxy` tarafından kullanılan sınıfı <xref:System.Collections.Generic.List%601> kodda tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="de325-142">In the following example, the `Galaxy` class that is used by the <xref:System.Collections.Generic.List%601> is defined in the code.</span></span>  
  
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
## <a name="kinds-of-collections"></a><span data-ttu-id="de325-143">Koleksiyon türleri</span><span class="sxs-lookup"><span data-stu-id="de325-143">Kinds of Collections</span></span>   
 <span data-ttu-id="de325-144">Ortak koleksiyonların çoğu .NET Framework tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="de325-144">Many common collections are provided by the .NET Framework.</span></span> <span data-ttu-id="de325-145">Her koleksiyon türü belirli bir amaç için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="de325-145">Each type of collection is designed for a specific purpose.</span></span>  
  
 <span data-ttu-id="de325-146">Bazı ortak koleksiyon sınıfları, bu bölümde açıklanan:</span><span class="sxs-lookup"><span data-stu-id="de325-146">Some of the common collection classes are described in this section:</span></span>  
  
-   <span data-ttu-id="de325-147"><xref:System.Collections.Generic> Sınıfları</span><span class="sxs-lookup"><span data-stu-id="de325-147"><xref:System.Collections.Generic> classes</span></span>  
  
-   <span data-ttu-id="de325-148"><xref:System.Collections.Concurrent> Sınıfları</span><span class="sxs-lookup"><span data-stu-id="de325-148"><xref:System.Collections.Concurrent> classes</span></span>  
  
-   <span data-ttu-id="de325-149"><xref:System.Collections> Sınıfları</span><span class="sxs-lookup"><span data-stu-id="de325-149"><xref:System.Collections> classes</span></span>  
  
-   <span data-ttu-id="de325-150">Visual Basic `Collection` sınıfı</span><span class="sxs-lookup"><span data-stu-id="de325-150">Visual Basic `Collection` class</span></span>  
  
<a name="BKMK_Generic"></a>
### <a name="systemcollectionsgeneric-classes"></a><span data-ttu-id="de325-151">System.Collections.Generic sınıfları</span><span class="sxs-lookup"><span data-stu-id="de325-151">System.Collections.Generic Classes</span></span>  

 <span data-ttu-id="de325-152">Genel koleksiyon sınıfları birini kullanarak oluşturabileceğiniz <xref:System.Collections.Generic> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="de325-152">You can create a generic collection by using one of the classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="de325-153">Genel koleksiyon, koleksiyondaki her öğe aynı veri türüne sahip olduğunda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="de325-153">A generic collection is useful when every item in the collection has the same data type.</span></span> <span data-ttu-id="de325-154">Yalnızca istenen veri sağlayarak güçlü yazmayı genel koleksiyon sağlar eklenecek türü.</span><span class="sxs-lookup"><span data-stu-id="de325-154">A generic collection enforces strong typing by allowing only the desired data type to be added.</span></span>  
  
 <span data-ttu-id="de325-155">Aşağıdaki tabloda sık kullanılan sınıflarından bazılarını listeler <xref:System.Collections.Generic?displayProperty=nameWithType> ad alanı:</span><span class="sxs-lookup"><span data-stu-id="de325-155">The following table lists some of the frequently used classes of the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace:</span></span>  
  
|<span data-ttu-id="de325-156">örneği</span><span class="sxs-lookup"><span data-stu-id="de325-156">Class</span></span>|<span data-ttu-id="de325-157">Açıklama</span><span class="sxs-lookup"><span data-stu-id="de325-157">Description</span></span>|  
|---|---|  
|<xref:System.Collections.Generic.Dictionary%602>|<span data-ttu-id="de325-158">Anahtara göre düzenlenen anahtar/değer çifti koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="de325-158">Represents a collection of key/value pairs that are organized based on the key.</span></span>|  
|<xref:System.Collections.Generic.List%601>|<span data-ttu-id="de325-159">Dizin tarafından erişilebilecek nesnelerin bir listesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="de325-159">Represents a list of objects that can be accessed by index.</span></span> <span data-ttu-id="de325-160">Arama, sıralama ve listelerini değiştirmek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="de325-160">Provides methods to search, sort, and modify lists.</span></span>|  
|<xref:System.Collections.Generic.Queue%601>|<span data-ttu-id="de325-161">İlk giren ilk çıkar (FIFO) nesne koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="de325-161">Represents a first in, first out (FIFO) collection of objects.</span></span>|  
|<xref:System.Collections.Generic.SortedList%602>|<span data-ttu-id="de325-162">Anahtarıyla ilişkili göre sıralanan anahtar/değer çiftlerinin koleksiyonunu temsil eder <xref:System.Collections.Generic.IComparer%601> uygulaması.</span><span class="sxs-lookup"><span data-stu-id="de325-162">Represents a collection of key/value pairs that are sorted by key based on the associated <xref:System.Collections.Generic.IComparer%601> implementation.</span></span>|  
|<xref:System.Collections.Generic.Stack%601>|<span data-ttu-id="de325-163">Son giren ilk çıkar (LIFO) nesne koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="de325-163">Represents a last in, first out (LIFO) collection of objects.</span></span>|  
  
 <span data-ttu-id="de325-164">Ek bilgi için bkz: [yaygın olarak kullanılan koleksiyon türleri](../../../standard/collections/commonly-used-collection-types.md), [koleksiyon sınıfı seçme](../../../standard/collections/selecting-a-collection-class.md), ve <xref:System.Collections.Generic?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="de325-164">For additional information, see [Commonly Used Collection Types](../../../standard/collections/commonly-used-collection-types.md), [Selecting a Collection Class](../../../standard/collections/selecting-a-collection-class.md), and <xref:System.Collections.Generic?displayProperty=nameWithType>.</span></span>  
  
<a name="BKMK_Concurrent"></a>
### <a name="systemcollectionsconcurrent-classes"></a><span data-ttu-id="de325-165">System.Collections.Concurrent sınıfları</span><span class="sxs-lookup"><span data-stu-id="de325-165">System.Collections.Concurrent Classes</span></span>   
 <span data-ttu-id="de325-166">.NET Framework 4 veya daha yeni sürümü, koleksiyonlar <xref:System.Collections.Concurrent> ad alanı, koleksiyon öğelerine birden fazla iş parçacığından erişmek için verimli bir iş parçacığı açısından güvenli işlemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="de325-166">In the .NET Framework 4 or newer, the collections in the <xref:System.Collections.Concurrent> namespace provide efficient thread-safe operations for accessing collection items from multiple threads.</span></span>  
  
 <span data-ttu-id="de325-167">Sınıflarda <xref:System.Collections.Concurrent> ad alanı, karşılık gelen türler yerine kullanılmalıdır <xref:System.Collections.Generic?displayProperty=nameWithType> ve <xref:System.Collections?displayProperty=nameWithType> birden çok iş parçacığı koleksiyon eriştiği her seferde ad alanları.</span><span class="sxs-lookup"><span data-stu-id="de325-167">The classes in the <xref:System.Collections.Concurrent> namespace should be used instead of the corresponding types in the <xref:System.Collections.Generic?displayProperty=nameWithType> and <xref:System.Collections?displayProperty=nameWithType> namespaces whenever multiple threads are accessing the collection concurrently.</span></span> <span data-ttu-id="de325-168">Daha fazla bilgi için [iş parçacığı güvenli koleksiyonları](../../../standard/collections/thread-safe/index.md) ve <xref:System.Collections.Concurrent>.</span><span class="sxs-lookup"><span data-stu-id="de325-168">For more information, see [Thread-Safe Collections](../../../standard/collections/thread-safe/index.md) and <xref:System.Collections.Concurrent>.</span></span>  
  
 <span data-ttu-id="de325-169">Eklenen bazı sınıflar <xref:System.Collections.Concurrent> ad <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, ve <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span><span class="sxs-lookup"><span data-stu-id="de325-169">Some classes included in the <xref:System.Collections.Concurrent> namespace are <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, and <xref:System.Collections.Concurrent.ConcurrentStack%601>.</span></span>  
  
<a name="BKMK_Collections"></a>
### <a name="systemcollections-classes"></a><span data-ttu-id="de325-170">System.Collections sınıfları</span><span class="sxs-lookup"><span data-stu-id="de325-170">System.Collections Classes</span></span>    
 <span data-ttu-id="de325-171">Sınıflarda <xref:System.Collections?displayProperty=nameWithType> özellikle yazılmış nesneler, ancak nesne türü ad alanı öğeleri saklamayın `Object`.</span><span class="sxs-lookup"><span data-stu-id="de325-171">The classes in the <xref:System.Collections?displayProperty=nameWithType> namespace do not store elements as specifically typed objects, but as objects of type `Object`.</span></span>  
  
 <span data-ttu-id="de325-172">Mümkün olduğunda genel koleksiyonları kullanması gereken <xref:System.Collections.Generic?displayProperty=nameWithType> ad alanı veya <xref:System.Collections.Concurrent> ad alanındaki eski türlerde yerine `System.Collections` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="de325-172">Whenever possible, you should use the generic collections in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace or the <xref:System.Collections.Concurrent> namespace instead of the legacy types in the `System.Collections` namespace.</span></span>  
  
 <span data-ttu-id="de325-173">Aşağıdaki tabloda sık kullanılan sınıflarından bazılarını listeler `System.Collections` ad alanı:</span><span class="sxs-lookup"><span data-stu-id="de325-173">The following table lists some of the frequently used classes in the `System.Collections` namespace:</span></span>  
  
|<span data-ttu-id="de325-174">örneği</span><span class="sxs-lookup"><span data-stu-id="de325-174">Class</span></span>|<span data-ttu-id="de325-175">Açıklama</span><span class="sxs-lookup"><span data-stu-id="de325-175">Description</span></span>|  
|---|---|  
|<xref:System.Collections.ArrayList>|<span data-ttu-id="de325-176">Bir dizi boyutu olarak dinamik olarak artırılan nesne dizilerini temsil gereklidir.</span><span class="sxs-lookup"><span data-stu-id="de325-176">Represents an array of objects whose size is dynamically increased as required.</span></span>|  
|<xref:System.Collections.Hashtable>|<span data-ttu-id="de325-177">Anahtarın karma koduna göre düzenlenen anahtar/değer çifti koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="de325-177">Represents a collection of key/value pairs that are organized based on the hash code of the key.</span></span>|  
|<xref:System.Collections.Queue>|<span data-ttu-id="de325-178">İlk giren ilk çıkar (FIFO) nesne koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="de325-178">Represents a first in, first out (FIFO) collection of objects.</span></span>|  
|<xref:System.Collections.Stack>|<span data-ttu-id="de325-179">Son giren ilk çıkar (LIFO) nesne koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="de325-179">Represents a last in, first out (LIFO) collection of objects.</span></span>|  
  
 <span data-ttu-id="de325-180"><xref:System.Collections.Specialized> Ad alanı yalnızca dize koleksiyonları ve bağlantılı liste ve melez sözlükler gibi özelleştirilmiş ve türü kesin belirlenmiş koleksiyon sınıfları sağlar.</span><span class="sxs-lookup"><span data-stu-id="de325-180">The <xref:System.Collections.Specialized> namespace provides specialized and strongly typed collection classes, such as string-only collections and linked-list and hybrid dictionaries.</span></span>  

<a name="BKMK_VisualBasic"></a> 
###  <a name="visual-basic-collection-class"></a><span data-ttu-id="de325-181">Visual Basic Collection sınıfı</span><span class="sxs-lookup"><span data-stu-id="de325-181">Visual Basic Collection Class</span></span>  
 <span data-ttu-id="de325-182">Visual Basic kullanabileceğiniz <xref:Microsoft.VisualBasic.Collection> erişimi öğesi sayısal dizin kullanarak koleksiyon veya bir sınıf `String` anahtarı.</span><span class="sxs-lookup"><span data-stu-id="de325-182">You can use the Visual Basic <xref:Microsoft.VisualBasic.Collection> class to access a collection item by using either a numeric index or a `String` key.</span></span> <span data-ttu-id="de325-183">Bir koleksiyon nesnesi ile veya bir anahtar belirtmeden öğe ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="de325-183">You can add items to a collection object either with or without specifying a key.</span></span> <span data-ttu-id="de325-184">Bir anahtar olmadan bir öğe eklerseniz, erişmek için sayısal dizinini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="de325-184">If you add an item without a key, you must use its numeric index to access it.</span></span>  
  
 <span data-ttu-id="de325-185">Visual Basic `Collection` sınıf türü olarak tüm öğelerini depolar `Object`, herhangi bir veri türünde bir öğe ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="de325-185">The Visual Basic `Collection` class stores all its elements as type `Object`, so you can add an item of any data type.</span></span> <span data-ttu-id="de325-186">Eklenen uygunsuz veri türleriyle yoktur.</span><span class="sxs-lookup"><span data-stu-id="de325-186">There is no safeguard against inappropriate data types being added.</span></span>  
  
 <span data-ttu-id="de325-187">Visual Basic kullandığınızda `Collection` sınıfı, bir koleksiyondaki ilk öğe dizini 1 vardır.</span><span class="sxs-lookup"><span data-stu-id="de325-187">When you use the Visual Basic `Collection` class, the first item in a collection has an index of 1.</span></span> <span data-ttu-id="de325-188">Bu, başlangıç dizini 0 olduğu .NET Framework koleksiyon sınıflarından farklıdır.</span><span class="sxs-lookup"><span data-stu-id="de325-188">This differs from the .NET Framework collection classes, for which the starting index is 0.</span></span>  
  
 <span data-ttu-id="de325-189">Mümkün olduğunda genel koleksiyonları kullanması gereken <xref:System.Collections.Generic?displayProperty=nameWithType> ad alanı veya <xref:System.Collections.Concurrent> ad alanı Visual Basic yerine `Collection` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="de325-189">Whenever possible, you should use the generic collections in the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace or the <xref:System.Collections.Concurrent> namespace instead of the Visual Basic `Collection` class.</span></span>  
  
 <span data-ttu-id="de325-190">Daha fazla bilgi için bkz. <xref:Microsoft.VisualBasic.Collection>.</span><span class="sxs-lookup"><span data-stu-id="de325-190">For more information, see <xref:Microsoft.VisualBasic.Collection>.</span></span>  
  
<a name="BKMK_KeyValuePairs"></a>
## <a name="implementing-a-collection-of-keyvalue-pairs"></a><span data-ttu-id="de325-191">Anahtar/değer çiftleri topluluğu uygulama</span><span class="sxs-lookup"><span data-stu-id="de325-191">Implementing a Collection of Key/Value Pairs</span></span>   
 <span data-ttu-id="de325-192"><xref:System.Collections.Generic.Dictionary%602> Genel koleksiyonu her öğenin anahtarını kullanarak bir koleksiyondaki öğelere erişmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="de325-192">The <xref:System.Collections.Generic.Dictionary%602> generic collection enables you to access to elements in a collection by using the key of each element.</span></span> <span data-ttu-id="de325-193">Her ek sözlük için bir değer ve ilişkili anahtarını oluşur.</span><span class="sxs-lookup"><span data-stu-id="de325-193">Each addition to the dictionary consists of a value and its associated key.</span></span> <span data-ttu-id="de325-194">Bir değeri anahtarını kullanarak almak oldukça hızlıdır `Dictionary` sınıfı bir karma tablo olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="de325-194">Retrieving a value by using its key is fast because the `Dictionary` class is implemented as a hash table.</span></span>  
  
 <span data-ttu-id="de325-195">Aşağıdaki örnek, oluşturur bir `Dictionary` koleksiyonu ve kullanarak sözlük yinelenir. bir `For Each` deyimi.</span><span class="sxs-lookup"><span data-stu-id="de325-195">The following example creates a `Dictionary` collection and iterates through the dictionary by using a `For Each` statement.</span></span>  
  
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
  
 <span data-ttu-id="de325-196">Bunun yerine bir koleksiyon Başlatıcısı oluşturmak için kullanılacak `Dictionary` koleksiyonu değiştirebilirsiniz `BuildDictionary` ve `AddToDictionary` yöntemlerini aşağıdaki yöntemle.</span><span class="sxs-lookup"><span data-stu-id="de325-196">To instead use a collection initializer to build the `Dictionary` collection, you can replace the `BuildDictionary` and `AddToDictionary` methods with the following method.</span></span>  
  
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
  
 <span data-ttu-id="de325-197">Aşağıdaki örnekte <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> yöntemi ve <xref:System.Collections.Generic.Dictionary%602.Item%2A> özelliği `Dictionary` öğeyi anahtara göre hızlı bir şekilde bulmak için.</span><span class="sxs-lookup"><span data-stu-id="de325-197">The following example uses the <xref:System.Collections.Generic.Dictionary%602.ContainsKey%2A> method and the <xref:System.Collections.Generic.Dictionary%602.Item%2A> property of `Dictionary` to quickly find an item by key.</span></span> <span data-ttu-id="de325-198">`Item` Özelliği bir öğeye erişmenize olanak tanır `elements` kullanarak koleksiyon `elements(symbol)` Visual Basic kod.</span><span class="sxs-lookup"><span data-stu-id="de325-198">The `Item` property enables you to access an item in the `elements` collection by using the `elements(symbol)` code in Visual Basic.</span></span>  
  
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
  
 <span data-ttu-id="de325-199">Aşağıdaki örnek, bunun yerine kullanır <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> yöntemi anahtara göre hızlı bir şekilde öğeyi bulun.</span><span class="sxs-lookup"><span data-stu-id="de325-199">The following example instead uses the <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> method quickly find an item by key.</span></span>  
  
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
##  <a name="using-linq-to-access-a-collection"></a><span data-ttu-id="de325-200">Koleksiyona erişmek için LINQ kullanma</span><span class="sxs-lookup"><span data-stu-id="de325-200">Using LINQ to Access a Collection</span></span>  
 <span data-ttu-id="de325-201">LINQ (dil ile tümleşik sorgu) koleksiyonlara erişmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="de325-201">LINQ (Language-Integrated Query) can be used to access collections.</span></span> <span data-ttu-id="de325-202">LINQ sorguları filtreleme, sıralama ve Gruplama yetenekler sağlar.</span><span class="sxs-lookup"><span data-stu-id="de325-202">LINQ queries provide filtering, ordering, and grouping capabilities.</span></span> <span data-ttu-id="de325-203">Daha fazla bilgi için [Visual Basic'te lınq'e Başlarken](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="de325-203">For more information, see [Getting Started with LINQ in Visual Basic](../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md).</span></span>  
  
 <span data-ttu-id="de325-204">Aşağıdaki örnek, bir genel LINQ sorgusu çalıştırır `List`.</span><span class="sxs-lookup"><span data-stu-id="de325-204">The following example runs a LINQ query against a generic `List`.</span></span> <span data-ttu-id="de325-205">LINQ sorgusu sonuçları içeren farklı bir koleksiyon döndürür.</span><span class="sxs-lookup"><span data-stu-id="de325-205">The LINQ query returns a different collection that contains the results.</span></span>  
  
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
## <a name="sorting-a-collection"></a><span data-ttu-id="de325-206">Koleksiyonda sıralama</span><span class="sxs-lookup"><span data-stu-id="de325-206">Sorting a Collection</span></span>  
 <span data-ttu-id="de325-207">Aşağıdaki örnek bir koleksiyonu sıralamak için bir yordam gösterir.</span><span class="sxs-lookup"><span data-stu-id="de325-207">The following example illustrates a procedure for sorting a collection.</span></span> <span data-ttu-id="de325-208">Örnek örneklerini sıralar `Car` depolanan sınıfı bir <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="de325-208">The example sorts instances of the `Car` class that are stored in a <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="de325-209">`Car` Sınıfının Implements <xref:System.IComparable%601> gerektiren arabirimi <xref:System.IComparable%601.CompareTo%2A> yönteminin uygulanmasını.</span><span class="sxs-lookup"><span data-stu-id="de325-209">The `Car` class implements the <xref:System.IComparable%601> interface, which requires that the <xref:System.IComparable%601.CompareTo%2A> method be implemented.</span></span>  
  
 <span data-ttu-id="de325-210">Her çağrı <xref:System.IComparable%601.CompareTo%2A> yöntemi sıralama için kullanılan tek bir karşılaştırma yapar.</span><span class="sxs-lookup"><span data-stu-id="de325-210">Each call to the <xref:System.IComparable%601.CompareTo%2A> method makes a single comparison that is used for sorting.</span></span> <span data-ttu-id="de325-211">Kullanıcı tarafından yazılan kodu `CompareTo` geçerli nesnenin başka bir nesneyle her karşılaştırılışında bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="de325-211">User-written code in the `CompareTo` method returns a value for each comparison of the current object with another object.</span></span> <span data-ttu-id="de325-212">Döndürülen değer daha az nesne geçerli nesneye sıfırdan küçük nesnesine, geçerli nesne diğer nesneden büyükse sıfır ve sıfır büyüktür eşit olmaları durumunda.</span><span class="sxs-lookup"><span data-stu-id="de325-212">The value returned is less than zero if the current object is less than the other object, greater than zero if the current object is greater than the other object, and zero if they are equal.</span></span> <span data-ttu-id="de325-213">Bu, kodda büyüktür, küçüktür ölçütleri tanımlayın ve eşit sağlar.</span><span class="sxs-lookup"><span data-stu-id="de325-213">This enables you to define in code the criteria for greater than, less than, and equal.</span></span>  
  
 <span data-ttu-id="de325-214">İçinde `ListCars` yöntemi `cars.Sort()` deyimi listeyi sıralar.</span><span class="sxs-lookup"><span data-stu-id="de325-214">In the `ListCars` method, the `cars.Sort()` statement sorts the list.</span></span> <span data-ttu-id="de325-215">Bu çağrıyı <xref:System.Collections.Generic.List%601.Sort%2A> yöntemi <xref:System.Collections.Generic.List%601> neden `CompareTo` otomatik olarak çağrılmasına yöntemi `Car` nesneler `List`.</span><span class="sxs-lookup"><span data-stu-id="de325-215">This call to the <xref:System.Collections.Generic.List%601.Sort%2A> method of the <xref:System.Collections.Generic.List%601> causes the `CompareTo` method to be called automatically for the `Car` objects in the `List`.</span></span>  
  
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
## <a name="defining-a-custom-collection"></a><span data-ttu-id="de325-216">Özel koleksiyonu tanımlama</span><span class="sxs-lookup"><span data-stu-id="de325-216">Defining a Custom Collection</span></span>  
 <span data-ttu-id="de325-217">Uygulayarak bir koleksiyon tanımlayabilirsiniz <xref:System.Collections.Generic.IEnumerable%601> veya <xref:System.Collections.IEnumerable> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="de325-217">You can define a collection by implementing the <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="de325-218">Ek bilgi için bkz: [koleksiyon numaralandırma](https://msdn.microsoft.com/library/71807ea7-9180-48a6-916f-35a5251d477f).</span><span class="sxs-lookup"><span data-stu-id="de325-218">For additional information, see [Enumerating a Collection](https://msdn.microsoft.com/library/71807ea7-9180-48a6-916f-35a5251d477f).</span></span>  
  
 <span data-ttu-id="de325-219">Bir özel koleksiyon tanımlayabilirsiniz, bunun yerine açıklanan .NET Framework içinde yer koleksiyonların kullanılması daha iyi [tür, koleksiyonları](#kinds-of-collections) bu konuda daha önce.</span><span class="sxs-lookup"><span data-stu-id="de325-219">Although you can define a custom collection, it is usually better to instead use the collections that are included in the .NET Framework, which are described in [Kinds of Collections](#kinds-of-collections) earlier in this topic.</span></span>  
  
 <span data-ttu-id="de325-220">Aşağıdaki örnekte adlı bir özel koleksiyon tanımlar `AllColors`.</span><span class="sxs-lookup"><span data-stu-id="de325-220">The following example defines a custom collection class named `AllColors`.</span></span> <span data-ttu-id="de325-221">Bu sınıfın uyguladığı <xref:System.Collections.IEnumerable> gerektiren arabirimi <xref:System.Collections.IEnumerable.GetEnumerator%2A> yönteminin uygulanmasını.</span><span class="sxs-lookup"><span data-stu-id="de325-221">This class implements the <xref:System.Collections.IEnumerable> interface, which requires that the <xref:System.Collections.IEnumerable.GetEnumerator%2A> method be implemented.</span></span>  
  
 <span data-ttu-id="de325-222">`GetEnumerator` Yöntemi kendinin bir örneğini döndürür `ColorEnumerator` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="de325-222">The `GetEnumerator` method returns an instance of the `ColorEnumerator` class.</span></span> <span data-ttu-id="de325-223">`ColorEnumerator` uygulayan <xref:System.Collections.IEnumerator> gerektiren arabirimi <xref:System.Collections.IEnumerator.Current%2A> özelliği <xref:System.Collections.IEnumerator.MoveNext%2A> yöntemi ve <xref:System.Collections.IEnumerator.Reset%2A> yönteminin uygulanmasını.</span><span class="sxs-lookup"><span data-stu-id="de325-223">`ColorEnumerator` implements the <xref:System.Collections.IEnumerator> interface, which requires that the <xref:System.Collections.IEnumerator.Current%2A> property, <xref:System.Collections.IEnumerator.MoveNext%2A> method, and <xref:System.Collections.IEnumerator.Reset%2A> method be implemented.</span></span>  
  
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
##  <a name="iterators"></a><span data-ttu-id="de325-224">Yineleyiciler</span><span class="sxs-lookup"><span data-stu-id="de325-224">Iterators</span></span>  
 <span data-ttu-id="de325-225">Bir *yineleyici* bir koleksiyon üzerinde özel yineleme yapmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="de325-225">An *iterator* is used to perform a custom iteration over a collection.</span></span> <span data-ttu-id="de325-226">Bir yineleyiciyi bir yöntem olabilir veya bir `get` erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="de325-226">An iterator can be a method or a `get` accessor.</span></span> <span data-ttu-id="de325-227">Yineleyici bir [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) deyimini her öğesini birer birer koleksiyonunun bir döndürür.</span><span class="sxs-lookup"><span data-stu-id="de325-227">An iterator uses a [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) statement to return each element of the collection one at a time.</span></span>  
  
 <span data-ttu-id="de325-228">Kullanarak bir yineleyici çağırabilirsiniz bir [her biri için... Sonraki](../../../visual-basic/language-reference/statements/for-each-next-statement.md) deyimi.</span><span class="sxs-lookup"><span data-stu-id="de325-228">You call an iterator by using a [For Each…Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement.</span></span> <span data-ttu-id="de325-229">Her bir yinelemesini `For Each` döngü yineleyiciyi çağırır.</span><span class="sxs-lookup"><span data-stu-id="de325-229">Each iteration of the `For Each` loop calls the iterator.</span></span> <span data-ttu-id="de325-230">Olduğunda bir `Yield` yineleyicisi deyimine ulaşıldığında, bir ifade döndürülür ve kodun geçerli konumu korunur.</span><span class="sxs-lookup"><span data-stu-id="de325-230">When a `Yield` statement is reached in the iterator, an expression is returned, and the current location in code is retained.</span></span> <span data-ttu-id="de325-231">Yürütme, yineleyicinin bir sonraki açışınızda bu konumdan başlatılır.</span><span class="sxs-lookup"><span data-stu-id="de325-231">Execution is restarted from that location the next time that the iterator is called.</span></span>  
  
 <span data-ttu-id="de325-232">Daha fazla bilgi için [yineleyiciler (Visual Basic)](../../../visual-basic/programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="de325-232">For more information, see [Iterators (Visual Basic)](../../../visual-basic/programming-guide/concepts/iterators.md).</span></span>  
  
 <span data-ttu-id="de325-233">Aşağıdaki örnek yineleyici yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="de325-233">The following example uses an iterator method.</span></span> <span data-ttu-id="de325-234">Yineleyici yöntem, bir `Yield` içindeki bir [için... Sonraki](../../../visual-basic/language-reference/statements/for-next-statement.md) döngü.</span><span class="sxs-lookup"><span data-stu-id="de325-234">The iterator method has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="de325-235">İçinde `ListEvenNumbers` yöntemi, her bir yinelemesini `For Each` diğerine geçer yineleyici yöntem için bir çağrı oluşturur ve deyim gövdesi `Yield` deyimi.</span><span class="sxs-lookup"><span data-stu-id="de325-235">In the `ListEvenNumbers` method, each iteration of the `For Each` statement body creates a call to the iterator method, which proceeds to the next `Yield` statement.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="de325-236">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="de325-236">See also</span></span>

- [<span data-ttu-id="de325-237">Öğe Başlatıcıları</span><span class="sxs-lookup"><span data-stu-id="de325-237">Collection Initializers</span></span>](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)  
- [<span data-ttu-id="de325-238">Programlama Kavramları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="de325-238">Programming Concepts (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/index.md)  
- [<span data-ttu-id="de325-239">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="de325-239">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
- [<span data-ttu-id="de325-240">LINQ to Objects'in (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="de325-240">LINQ to Objects (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
- [<span data-ttu-id="de325-241">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="de325-241">Parallel LINQ (PLINQ)</span></span>](../../../standard/parallel-programming/parallel-linq-plinq.md)  
- [<span data-ttu-id="de325-242">Koleksiyonlar ve Veri Yapıları</span><span class="sxs-lookup"><span data-stu-id="de325-242">Collections and Data Structures</span></span>](../../../standard/collections/index.md)  
- [<span data-ttu-id="de325-243">Koleksiyon oluşturma ve düzenleme</span><span class="sxs-lookup"><span data-stu-id="de325-243">Creating and Manipulating Collections</span></span>](https://msdn.microsoft.com/library/2065398e-eb1a-4821-9188-75f16e42e069)  
- [<span data-ttu-id="de325-244">Koleksiyon Sınıfı Seçme</span><span class="sxs-lookup"><span data-stu-id="de325-244">Selecting a Collection Class</span></span>](../../../standard/collections/selecting-a-collection-class.md)  
- [<span data-ttu-id="de325-245">Koleksiyonlardaki Karşılaştırmalar ve Sıralamalar</span><span class="sxs-lookup"><span data-stu-id="de325-245">Comparisons and Sorts Within Collections</span></span>](../../../standard/collections/comparisons-and-sorts-within-collections.md)  
- [<span data-ttu-id="de325-246">Genel Koleksiyonlar Ne Zaman Kullanılır?</span><span class="sxs-lookup"><span data-stu-id="de325-246">When to Use Generic Collections</span></span>](../../../standard/collections/when-to-use-generic-collections.md)
