---
title: "İç birleştirmeler gerçekleştirme"
description: "İç birleştirmeler gerçekleştirme."
keywords: .NET, .NET core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 45bceed6-f549-4114-a9b1-b44feb497742
ms.openlocfilehash: fdf75c0b7195742bdce70566ebb3880bb0565f31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="perform-inner-joins"></a><span data-ttu-id="aeaa1-104">İç birleştirmeler gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="aeaa1-104">Perform inner joins</span></span>

<span data-ttu-id="aeaa1-105">İlişkisel veritabanı bakımından, bir *INNER JOIN* her hangi ilk koleksiyon öğesinde bir sonuç kümesi ikinci koleksiyon eşleşen her öğe için bir kez görünür üretir.</span><span class="sxs-lookup"><span data-stu-id="aeaa1-105">In relational database terms, an *inner join* produces a result set in which each element of the first collection appears one time for every matching element in the second collection.</span></span> <span data-ttu-id="aeaa1-106">Bir öğenin ilk koleksiyonda eşleşen bir öğe varsa sonuç kümesinde görünmez.</span><span class="sxs-lookup"><span data-stu-id="aeaa1-106">If an element in the first collection has no matching elements, it does not appear in the result set.</span></span> <span data-ttu-id="aeaa1-107"><xref:System.Linq.Enumerable.Join%2A> Tarafından çağrılır yöntemi `join` yan tümcesinde C# ' ta, bir iç birleştirme uygular.</span><span class="sxs-lookup"><span data-stu-id="aeaa1-107">The <xref:System.Linq.Enumerable.Join%2A> method, which is called by the `join` clause in C#, implements an inner join.</span></span>  
  
 <span data-ttu-id="aeaa1-108">Bu konuda, bir iç birleştirme dört çeşidi gerçekleştirme gösterir:</span><span class="sxs-lookup"><span data-stu-id="aeaa1-108">This topic shows you how to perform four variations of an inner join:</span></span>  
  
-   <span data-ttu-id="aeaa1-109">İki veri kaynaklarından basit bir anahtarı temel öğeleri karşılık gelen basit bir iç birleştirme.</span><span class="sxs-lookup"><span data-stu-id="aeaa1-109">A simple inner join that correlates elements from two data sources based on a simple key.</span></span>  
  
-   <span data-ttu-id="aeaa1-110">İki veri kaynaklarından öğeleri karşılık gelen bir iç birleştirme temel alarak bir *bileşik* anahtarı.</span><span class="sxs-lookup"><span data-stu-id="aeaa1-110">An inner join that correlates elements from two data sources based on a *composite* key.</span></span> <span data-ttu-id="aeaa1-111">Birden fazla değerini oluşan bir anahtardır, bileşik bir anahtar, birden fazla özelliğe dayalı öğeleri ilişkilendirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="aeaa1-111">A composite key, which is a key that consists of more than one value, enables you to correlate elements based on more than one property.</span></span>  
  
-   <span data-ttu-id="aeaa1-112">A *birden fazla birleşim* hangi art arda birleştirme işlemleri birbirlerine eklenir.</span><span class="sxs-lookup"><span data-stu-id="aeaa1-112">A *multiple join* in which successive join operations are appended to each other.</span></span>  
  
-   <span data-ttu-id="aeaa1-113">Bir iç birleştirme group JOIN kullanılarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="aeaa1-113">An inner join that is implemented by using a group join.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aeaa1-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="aeaa1-114">Example</span></span>  
  
## <a name="simple-key-join-example"></a><span data-ttu-id="aeaa1-115">Basit anahtar birleşim örneği</span><span class="sxs-lookup"><span data-stu-id="aeaa1-115">Simple key join example</span></span>  
 <span data-ttu-id="aeaa1-116">Aşağıdaki örnekte, iki tür, kullanıcı tanımlı nesneler içeren iki koleksiyonları oluşturur `Person` ve `Pet`.</span><span class="sxs-lookup"><span data-stu-id="aeaa1-116">The following example creates two collections that contain objects of two user-defined types, `Person` and `Pet`.</span></span> <span data-ttu-id="aeaa1-117">Sorgu kullanan `join` yan tümcesinde eşleştirmek için C# `Person` nesnelerini `Pet` özelliği nesneleri `Owner` olan `Person`.</span><span class="sxs-lookup"><span data-stu-id="aeaa1-117">The query uses the `join` clause in C# to match `Person` objects with `Pet` objects whose `Owner` is that `Person`.</span></span> <span data-ttu-id="aeaa1-118">`select` Yan tümcesinde C# elde edilen nesnelerdeki nasıl görüneceğine tanımlar.</span><span class="sxs-lookup"><span data-stu-id="aeaa1-118">The `select` clause in C# defines how the resulting objects will look.</span></span> <span data-ttu-id="aeaa1-119">Bu örnekte, elde edilen nesnelerdeki sahibinin adı ve Evcil hayvanınızın adı oluşan anonim türleridir.</span><span class="sxs-lookup"><span data-stu-id="aeaa1-119">In this example the resulting objects are anonymous types that consist of the owner's first name and the pet's name.</span></span>  
  
 [!code-csharp[CsLINQProgJoining#1](../../../samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_1.cs)]  
  
 <span data-ttu-id="aeaa1-120">Unutmayın `Person` nesnesindeki `LastName` "Huff" sonuç olduğundan kümesine görünmez olan hiçbir `Pet` olan nesneyi `Pet.Owner` eşit `Person`.</span><span class="sxs-lookup"><span data-stu-id="aeaa1-120">Note that the `Person` object whose `LastName` is "Huff" does not appear in the result set because there is no `Pet` object that has `Pet.Owner` equal to that `Person`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aeaa1-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="aeaa1-121">Example</span></span>  
  
## <a name="composite-key-join-example"></a><span data-ttu-id="aeaa1-122">Bileşik anahtar birleşim örneği</span><span class="sxs-lookup"><span data-stu-id="aeaa1-122">Composite key join example</span></span>  
 <span data-ttu-id="aeaa1-123">Öğeleri tek bir özelliğe dayalı bağıntı yerine birden çok özelliğe göre öğeleri karşılaştırmak için bileşik bir anahtar kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aeaa1-123">Instead of correlating elements based on just one property, you can use a composite key to compare elements based on multiple properties.</span></span> <span data-ttu-id="aeaa1-124">Bunu yapmak için karşılaştırmak istediğiniz özelliklerini oluşur anonim bir tür dönmek her bir koleksiyon için anahtar Seçici işlevi belirtin.</span><span class="sxs-lookup"><span data-stu-id="aeaa1-124">To do this, specify the key selector function for each collection to return an anonymous type that consists of the properties you want to compare.</span></span> <span data-ttu-id="aeaa1-125">Özellikler etiket, bunlar aynı etiketi her anahtarın anonim türünde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="aeaa1-125">If you label the properties, they must have the same label in each key's anonymous type.</span></span> <span data-ttu-id="aeaa1-126">Özellikleri de aynı sırada yer almalıdır.</span><span class="sxs-lookup"><span data-stu-id="aeaa1-126">The properties must also appear in the same order.</span></span>  
  
 <span data-ttu-id="aeaa1-127">Aşağıdaki örnek, bir listesini kullanır `Employee` nesneleri ve listesini `Student` hangi çalışanların de Öğrenciler belirlemek için nesneleri.</span><span class="sxs-lookup"><span data-stu-id="aeaa1-127">The following example uses a list of `Employee` objects and a list of `Student` objects to determine which employees are also students.</span></span> <span data-ttu-id="aeaa1-128">Bu tür hem de bir `FirstName` ve `LastName` türündeki özelliği <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="aeaa1-128">Both of these types have a `FirstName` and a `LastName` property of type <xref:System.String>.</span></span> <span data-ttu-id="aeaa1-129">Her listenin öğelerini birleştirme anahtarları oluşturmak işlevler oluşan anonim bir tür döndürür `FirstName` ve `LastName` her öğenin özelliklerini.</span><span class="sxs-lookup"><span data-stu-id="aeaa1-129">The functions that create the join keys from each list's elements return an anonymous type that consists of the `FirstName` and `LastName` properties of each element.</span></span> <span data-ttu-id="aeaa1-130">Birleştirme işlemi bu bileşik anahtarlar eşitliği karşılaştırır ve ad ve Soyadı eşleştiği her listeden nesneleri çiftlerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="aeaa1-130">The join operation compares these composite keys for equality and returns pairs of objects from each list where both the first name and the last name match.</span></span>  
  
 [!code-csharp[CsLINQProgJoining#2](../../../samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="aeaa1-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="aeaa1-131">Example</span></span>  
  
## <a name="multiple-join-example"></a><span data-ttu-id="aeaa1-132">Birden fazla birleşim örneği</span><span class="sxs-lookup"><span data-stu-id="aeaa1-132">Multiple join example</span></span>  
 <span data-ttu-id="aeaa1-133">Birleştirme işlemleri herhangi bir sayıda birden fazla birleşim gerçekleştirmek için birbirlerine eklenmiş.</span><span class="sxs-lookup"><span data-stu-id="aeaa1-133">Any number of join operations can be appended to each other to perform a multiple join.</span></span> <span data-ttu-id="aeaa1-134">Her `join` yan tümcesinde C# karşılık gelen bir belirtilen veri kaynağı önceki birleştirme sonuçlarını.</span><span class="sxs-lookup"><span data-stu-id="aeaa1-134">Each `join` clause in C# correlates a specified data source with the results of the previous join.</span></span>  
  
 <span data-ttu-id="aeaa1-135">Aşağıdaki örnek, üç koleksiyonları oluşturur: listesini `Person` nesneleri, listesini `Cat` nesneleri ve listesini `Dog` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="aeaa1-135">The following example creates three collections: a list of `Person` objects, a list of `Cat` objects, and a list of `Dog` objects.</span></span>  
  
 <span data-ttu-id="aeaa1-136">İlk `join` kişiler ve temel kediler yan tümcesinde C# ile eşleşen bir `Person` nesne eşleşen `Cat.Owner`.</span><span class="sxs-lookup"><span data-stu-id="aeaa1-136">The first `join` clause in C# matches people and cats based on a `Person` object matching `Cat.Owner`.</span></span> <span data-ttu-id="aeaa1-137">İçeren anonim türleri dizisi döndürür `Person` nesne ve `Cat.Name`.</span><span class="sxs-lookup"><span data-stu-id="aeaa1-137">It returns a sequence of anonymous types that contain the `Person` object and `Cat.Name`.</span></span>  
  
 <span data-ttu-id="aeaa1-138">İkinci `join` yan tümcesinde C# ile ilk birleşimi tarafından döndürülen anonim türler karşılık gelen `Dog` köpekler, sağlanan listesi nesneleri temel oluşan bir bileşik anahtarı `Owner` türünde özellik `Person`ve ilk harfi hayvan kişinin adı.</span><span class="sxs-lookup"><span data-stu-id="aeaa1-138">The second `join` clause in C# correlates the anonymous types returned by the first join with `Dog` objects in the supplied list of dogs, based on a composite key that consists of the `Owner` property of type `Person`, and the first letter of the animal's name.</span></span> <span data-ttu-id="aeaa1-139">İçeren anonim türleri dizisi döndürür `Cat.Name` ve `Dog.Name` her eşleşen çifti özelliklerinden.</span><span class="sxs-lookup"><span data-stu-id="aeaa1-139">It returns a sequence of anonymous types that contain the `Cat.Name` and `Dog.Name` properties from each matching pair.</span></span> <span data-ttu-id="aeaa1-140">Bu bir iç birleştirme olduğundan, yalnızca bir eşleşme ikinci veri kaynağına sahip ilk veri kaynağı nesneden döndürülür.</span><span class="sxs-lookup"><span data-stu-id="aeaa1-140">Because this is an inner join, only those objects from the first data source that have a match in the second data source are returned.</span></span>  
  
 [!code-csharp[CsLINQProgJoining#3](../../../samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_3.cs)]  
  
## <a name="example"></a><span data-ttu-id="aeaa1-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="aeaa1-141">Example</span></span>  
  
## <a name="inner-join-by-using-grouped-join-example"></a><span data-ttu-id="aeaa1-142">Gruplandırılmış birleşim örneği kullanarak iç birleştirme</span><span class="sxs-lookup"><span data-stu-id="aeaa1-142">Inner join by using grouped join example</span></span>  
 <span data-ttu-id="aeaa1-143">Aşağıdaki örnekte bir grup birleştirme kullanarak bir iç birleştirme uygulama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="aeaa1-143">The following example shows you how to implement an inner join by using a group join.</span></span>  
  
 <span data-ttu-id="aeaa1-144">İçinde `query1`, listesini `Person` nesneleri Grup katılmış listesine `Pet` nesneleri temel alarak `Person` eşleşen `Pet.Owner` özelliği.</span><span class="sxs-lookup"><span data-stu-id="aeaa1-144">In `query1`, the list of `Person` objects is group-joined to the list of `Pet` objects based on the `Person` matching the `Pet.Owner` property.</span></span> <span data-ttu-id="aeaa1-145">Group JOIN olduğu her grubu oluşur Ara gruplarının bir koleksiyon oluşturur bir `Person` nesne ve eşleşen bir dizi `Pet` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="aeaa1-145">The group join creates a collection of intermediate groups, where each group consists of a `Person` object and a sequence of matching `Pet` objects.</span></span>  
  
 <span data-ttu-id="aeaa1-146">İkinci bir ekleyerek `from` bu sırası sıralarının sorgu yan tümcesini birleştirilmiş (ya da düzleştirilmiş) bir uzun dizi.</span><span class="sxs-lookup"><span data-stu-id="aeaa1-146">By adding a second `from` clause to the query, this sequence of sequences is combined (or flattened) into one longer sequence.</span></span> <span data-ttu-id="aeaa1-147">Son dizi öğelerin türü tarafından belirtilen `select` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="aeaa1-147">The type of the elements of the final sequence is specified by the `select` clause.</span></span> <span data-ttu-id="aeaa1-148">Bu örnekte, oluşan anonim bir tür türüdür `Person.FirstName` ve `Pet.Name` her eşleşen çifti için özellikler.</span><span class="sxs-lookup"><span data-stu-id="aeaa1-148">In this example, that type is an anonymous type that consists of the `Person.FirstName` and `Pet.Name` properties for each matching pair.</span></span>  
  
 <span data-ttu-id="aeaa1-149">Sonucu `query1` kullanarak alındıktan sonuç kümesi eşdeğerdir `join` yan tümcesi olmadan `into` bir iç birleştirme gerçekleştirmek için yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="aeaa1-149">The result of `query1` is equivalent to the result set that would have been obtained by using the `join` clause without the `into` clause to perform an inner join.</span></span> <span data-ttu-id="aeaa1-150">`query2` Değişkeni eşdeğer bu sorguyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="aeaa1-150">The `query2` variable demonstrates this equivalent query.</span></span>  
  
 [!code-csharp[CsLINQProgJoining#4](../../../samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_4.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="aeaa1-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aeaa1-151">See also</span></span>  
 <xref:System.Linq.Enumerable.Join%2A>  
 <xref:System.Linq.Enumerable.GroupJoin%2A>  
 [<span data-ttu-id="aeaa1-152">Gruplandırılmış birleştirmeler gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="aeaa1-152">Perform grouped joins</span></span>](perform-grouped-joins.md)  
 [<span data-ttu-id="aeaa1-153">Sol dış birleştirmeler gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="aeaa1-153">Perform left outer joins</span></span>](perform-left-outer-joins.md)  
 [<span data-ttu-id="aeaa1-154">Anonim türler</span><span class="sxs-lookup"><span data-stu-id="aeaa1-154">Anonymous types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)  
 
