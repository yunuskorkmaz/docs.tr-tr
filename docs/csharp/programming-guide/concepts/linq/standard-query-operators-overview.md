---
title: Standart sorgu Işleçlerine genelC#bakış ()
ms.date: 07/20/2015
ms.assetid: 812fa119-5f65-4139-b4fa-55dccd8dc3ac
ms.openlocfilehash: e6419fef5c211995aa4d2bd0796a0d0336dc47a9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590981"
---
# <a name="standard-query-operators-overview-c"></a><span data-ttu-id="51163-102">Standart sorgu Işleçlerine genelC#bakış ()</span><span class="sxs-lookup"><span data-stu-id="51163-102">Standard Query Operators Overview (C#)</span></span>
<span data-ttu-id="51163-103">*Standart sorgu IŞLEÇLERI* LINQ deseninin bulunduğu yöntemlerdir.</span><span class="sxs-lookup"><span data-stu-id="51163-103">The *standard query operators* are the methods that form the LINQ pattern.</span></span> <span data-ttu-id="51163-104">Bu yöntemlerin çoğu diziler üzerinde çalışır, burada bir sıra, türü <xref:System.Collections.Generic.IEnumerable%601> arabirimini <xref:System.Linq.IQueryable%601> veya arabirimi uygulayan bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="51163-104">Most of these methods operate on sequences, where a sequence is an object whose type implements the <xref:System.Collections.Generic.IEnumerable%601> interface or the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="51163-105">Standart sorgu işleçleri filtreleme, yansıtma, toplama, sıralama ve daha fazlasını içeren sorgu özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="51163-105">The standard query operators provide query capabilities including filtering, projection, aggregation, sorting and more.</span></span>  
  
 <span data-ttu-id="51163-106">Türü <xref:System.Collections.Generic.IEnumerable%601> nesneler üzerinde çalışan diğeri türü <xref:System.Linq.IQueryable%601>nesneler üzerinde çalışan iki LINQ standart sorgu işleci kümesi vardır.</span><span class="sxs-lookup"><span data-stu-id="51163-106">There are two sets of LINQ standard query operators, one that operates on objects of type <xref:System.Collections.Generic.IEnumerable%601> and the other that operates on objects of type <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="51163-107">Her kümeyi oluşturan Yöntemler sırasıyla <xref:System.Linq.Enumerable> ve <xref:System.Linq.Queryable> sınıflarının statik üyeleridir.</span><span class="sxs-lookup"><span data-stu-id="51163-107">The methods that make up each set are static members of the <xref:System.Linq.Enumerable> and <xref:System.Linq.Queryable> classes, respectively.</span></span> <span data-ttu-id="51163-108">Bunlar üzerinde çalıştıkları türün *Uzantı yöntemleri* olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="51163-108">They are defined as *extension methods* of the type that they operate on.</span></span> <span data-ttu-id="51163-109">Bu, statik yöntem sözdizimi veya örnek yöntemi sözdizimi kullanılarak çağrılabilecek anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="51163-109">This means that they can be called by using either static method syntax or instance method syntax.</span></span>  
  
 <span data-ttu-id="51163-110">Ayrıca, birkaç standart sorgu işleci yöntemi, <xref:System.Collections.Generic.IEnumerable%601> veya <xref:System.Linq.IQueryable%601>tabanlı olanlar dışındaki türler üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="51163-110">In addition, several standard query operator methods operate on types other than those based on <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="51163-111">Türü <xref:System.Linq.Enumerable> , her ikisi de türündeki <xref:System.Collections.IEnumerable>nesneler üzerinde çalışan iki yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="51163-111">The <xref:System.Linq.Enumerable> type defines two such methods that both operate on objects of type <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="51163-112">Bu yöntemler <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> ve <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, parametreli olmayan veya genel olmayan bir koleksiyonun LINQ düzeninde sorgulanmasını etkinleştirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="51163-112">These methods, <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> and <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, let you enable a non-parameterized, or non-generic, collection to be queried in the LINQ pattern.</span></span> <span data-ttu-id="51163-113">Bu, nesne türü kesin belirlenmiş bir koleksiyon oluşturarak bunu yapabilirler.</span><span class="sxs-lookup"><span data-stu-id="51163-113">They do this by creating a strongly-typed collection of objects.</span></span> <span data-ttu-id="51163-114">Sınıfı, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> ve<xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>türündeki nesneler<xref:System.Linq.Queryable>üzerinde çalışan iki benzer yöntemi tanımlar. <xref:System.Linq.Queryable></span><span class="sxs-lookup"><span data-stu-id="51163-114">The <xref:System.Linq.Queryable> class defines two similar methods, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> and <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, that operate on objects of type <xref:System.Linq.Queryable>.</span></span>  
  
 <span data-ttu-id="51163-115">Standart sorgu işleçleri, tek bir değer veya bir dizi değer döndürmediğine bağlı olarak yürütmesinin zamanlamalarına göre farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="51163-115">The standard query operators differ in the timing of their execution, depending on whether they return a singleton value or a sequence of values.</span></span> <span data-ttu-id="51163-116">Tek bir değer döndüren Yöntemler (örneğin, <xref:System.Linq.Enumerable.Average%2A> ve <xref:System.Linq.Enumerable.Sum%2A>) hemen yürütülür.</span><span class="sxs-lookup"><span data-stu-id="51163-116">Those methods that return a singleton value (for example, <xref:System.Linq.Enumerable.Average%2A> and <xref:System.Linq.Enumerable.Sum%2A>) execute immediately.</span></span> <span data-ttu-id="51163-117">Bir dizi döndüren yöntemler sorgu yürütmesini erteler ve Numaralandırılabilir bir nesne döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="51163-117">Methods that return a sequence defer the query execution and return an enumerable object.</span></span>  
  
 <span data-ttu-id="51163-118">Bellek içi koleksiyonlar üzerinde çalışan yöntemler söz konusu olduğunda, diğer bir deyişle <xref:System.Collections.Generic.IEnumerable%601>, döndürülen sıralanabilir nesne, metoduna geçirilen bağımsız değişkenleri yakalar.</span><span class="sxs-lookup"><span data-stu-id="51163-118">In the case of the methods that operate on in-memory collections, that is, those methods that extend <xref:System.Collections.Generic.IEnumerable%601>, the returned enumerable object captures the arguments that were passed to the method.</span></span> <span data-ttu-id="51163-119">Bu nesne numaralandırıldıktan sonra, sorgu işlecinin mantığı işe alınır ve sorgu sonuçları döndürülür.</span><span class="sxs-lookup"><span data-stu-id="51163-119">When that object is enumerated, the logic of the query operator is employed and the query results are returned.</span></span>  
  
 <span data-ttu-id="51163-120">Buna karşılık, genişleyen <xref:System.Linq.IQueryable%601> Yöntemler herhangi bir sorgulama davranışı uygulamaz, ancak gerçekleştirilecek sorguyu temsil eden bir ifade ağacı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="51163-120">In contrast, methods that extend <xref:System.Linq.IQueryable%601> do not implement any querying behavior, but build an expression tree that represents the query to be performed.</span></span> <span data-ttu-id="51163-121">Sorgu işleme, kaynak <xref:System.Linq.IQueryable%601> nesne tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="51163-121">The query processing is handled by the source <xref:System.Linq.IQueryable%601> object.</span></span>  
  
 <span data-ttu-id="51163-122">Sorgu yöntemlerine yapılan çağrılar tek bir sorgu içinde birbirine zincirlenebilir ve bu da sorguların rastgele karmaşık olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="51163-122">Calls to query methods can be chained together in one query, which enables queries to become arbitrarily complex.</span></span>  
  
 <span data-ttu-id="51163-123">Aşağıdaki kod örneği, bir dizi hakkında bilgi edinmek için standart sorgu işleçlerinin nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="51163-123">The following code example demonstrates how the standard query operators can be used to obtain information about a sequence.</span></span>  
  
```csharp  
string sentence = "the quick brown fox jumps over the lazy dog";  
// Split the string into individual words to create a collection.  
string[] words = sentence.Split(' ');  
  
// Using query expression syntax.  
var query = from word in words  
            group word.ToUpper() by word.Length into gr  
            orderby gr.Key  
            select new { Length = gr.Key, Words = gr };  
  
// Using method-based query syntax.  
var query2 = words.  
    GroupBy(w => w.Length, w => w.ToUpper()).  
    Select(g => new { Length = g.Key, Words = g }).  
    OrderBy(o => o.Length);  
  
foreach (var obj in query)  
{  
    Console.WriteLine("Words of length {0}:", obj.Length);  
    foreach (string word in obj.Words)  
        Console.WriteLine(word);  
}  
  
// This code example produces the following output:  
//  
// Words of length 3:  
// THE  
// FOX  
// THE  
// DOG  
// Words of length 4:  
// OVER  
// LAZY  
// Words of length 5:  
// QUICK  
// BROWN  
// JUMPS   
```  
  
## <a name="query-expression-syntax"></a><span data-ttu-id="51163-124">Sorgu Ifadesi söz dizimi</span><span class="sxs-lookup"><span data-stu-id="51163-124">Query Expression Syntax</span></span>  
 <span data-ttu-id="51163-125">Daha sık kullanılan standart sorgu işleçlerinden bazılarının, bir C# *sorgu* *ifadesinin*parçası olarak çağrılmasına olanak tanıyan adanmış ve Visual Basic Language anahtar sözcüğü sözdizimi vardır.</span><span class="sxs-lookup"><span data-stu-id="51163-125">Some of the more frequently used standard query operators have dedicated C# and Visual Basic language keyword syntax that enables them to be called as part of a *query* *expression*.</span></span> <span data-ttu-id="51163-126">Adanmış anahtar sözcüklere ve bunlara karşılık gelen sözdizimleri içeren standart sorgu işleçleri hakkında daha fazla bilgi için bkz. [Standart sorgu işleçleri Için sorgu IfadesiC#sözdizimi ()](./query-expression-syntax-for-standard-query-operators.md).</span><span class="sxs-lookup"><span data-stu-id="51163-126">For more information about standard query operators that have dedicated keywords and their corresponding syntaxes, see [Query Expression Syntax for Standard Query Operators (C#)](./query-expression-syntax-for-standard-query-operators.md).</span></span>  
  
## <a name="extending-the-standard-query-operators"></a><span data-ttu-id="51163-127">Standart sorgu Işleçlerini genişletme</span><span class="sxs-lookup"><span data-stu-id="51163-127">Extending the Standard Query Operators</span></span>  
 <span data-ttu-id="51163-128">Hedef etki alanınız veya teknolojiniz için uygun olan alana özgü Yöntemler oluşturarak standart sorgu işleçleri kümesini daha da getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51163-128">You can augment the set of standard query operators by creating domain-specific methods that are appropriate for your target domain or technology.</span></span> <span data-ttu-id="51163-129">Standart sorgu işleçlerini, uzaktan değerlendirme, sorgu çevirisi ve iyileştirme gibi ek hizmetler sağlayan kendi uygulamalarınız ile de değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51163-129">You can also replace the standard query operators with your own implementations that provide additional services such as remote evaluation, query translation, and optimization.</span></span> <span data-ttu-id="51163-130">Bir <xref:System.Linq.Enumerable.AsEnumerable%2A> örnek için bkz.</span><span class="sxs-lookup"><span data-stu-id="51163-130">See <xref:System.Linq.Enumerable.AsEnumerable%2A> for an example.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="51163-131">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="51163-131">Related Sections</span></span>  
 <span data-ttu-id="51163-132">Aşağıdaki bağlantılar, işlevleri temel alan çeşitli standart sorgu işleçleri hakkında ek bilgiler sağlayan konulara götürür.</span><span class="sxs-lookup"><span data-stu-id="51163-132">The following links take you to topics that provide additional information about the various standard query operators based on functionality.</span></span>  
  
 [<span data-ttu-id="51163-133">Verileri sıralama (C#)</span><span class="sxs-lookup"><span data-stu-id="51163-133">Sorting Data (C#)</span></span>](./sorting-data.md)  
  
 [<span data-ttu-id="51163-134">Işlemleri ayarla (C#)</span><span class="sxs-lookup"><span data-stu-id="51163-134">Set Operations (C#)</span></span>](./set-operations.md)  
  
 [<span data-ttu-id="51163-135">Verileri filtreleme (C#)</span><span class="sxs-lookup"><span data-stu-id="51163-135">Filtering Data (C#)</span></span>](./filtering-data.md)  
  
 [<span data-ttu-id="51163-136">Nicelik belirteci IşlemleriC#()</span><span class="sxs-lookup"><span data-stu-id="51163-136">Quantifier Operations (C#)</span></span>](./quantifier-operations.md)  
  
 [<span data-ttu-id="51163-137">Projeksiyon Işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="51163-137">Projection Operations (C#)</span></span>](./projection-operations.md)  
  
 [<span data-ttu-id="51163-138">Verileri bölümleme (C#)</span><span class="sxs-lookup"><span data-stu-id="51163-138">Partitioning Data (C#)</span></span>](./partitioning-data.md)  
  
 [<span data-ttu-id="51163-139">JOIN Işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="51163-139">Join Operations (C#)</span></span>](./join-operations.md)  
  
 [<span data-ttu-id="51163-140">Verileri gruplandırma (C#)</span><span class="sxs-lookup"><span data-stu-id="51163-140">Grouping Data (C#)</span></span>](./grouping-data.md)  
  
 [<span data-ttu-id="51163-141">Oluşturma Işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="51163-141">Generation Operations (C#)</span></span>](./generation-operations.md)  
  
 [<span data-ttu-id="51163-142">Eşitlik Işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="51163-142">Equality Operations (C#)</span></span>](./equality-operations.md)  
  
 [<span data-ttu-id="51163-143">Öğe Işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="51163-143">Element Operations (C#)</span></span>](./element-operations.md)  
  
 [<span data-ttu-id="51163-144">Veri türlerini dönüştürme (C#)</span><span class="sxs-lookup"><span data-stu-id="51163-144">Converting Data Types (C#)</span></span>](./converting-data-types.md)  
  
 [<span data-ttu-id="51163-145">Birleştirme Işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="51163-145">Concatenation Operations (C#)</span></span>](./concatenation-operations.md)  
  
 [<span data-ttu-id="51163-146">Toplama Işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="51163-146">Aggregation Operations (C#)</span></span>](./aggregation-operations.md)  
  
## <a name="see-also"></a><span data-ttu-id="51163-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="51163-147">See also</span></span>

- <xref:System.Linq.Enumerable>
- <xref:System.Linq.Queryable>
- [<span data-ttu-id="51163-148">LINQ Sorgularına Giriş (C#)</span><span class="sxs-lookup"><span data-stu-id="51163-148">Introduction to LINQ Queries (C#)</span></span>](./introduction-to-linq-queries.md)
- [<span data-ttu-id="51163-149">Standart sorgu Işleçleri için sorgu Ifadesi sözdizimi (C#)</span><span class="sxs-lookup"><span data-stu-id="51163-149">Query Expression Syntax for Standard Query Operators (C#)</span></span>](./query-expression-syntax-for-standard-query-operators.md)
- [<span data-ttu-id="51163-150">Standart sorgu Işleçleri yürütme (C#) yöntemine göre sınıflandırması</span><span class="sxs-lookup"><span data-stu-id="51163-150">Classification of Standard Query Operators by Manner of Execution (C#)</span></span>](./classification-of-standard-query-operators-by-manner-of-execution.md)
- [<span data-ttu-id="51163-151">Genişletme Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="51163-151">Extension Methods</span></span>](../../classes-and-structs/extension-methods.md)
