---
title: Standart sorgu Işleçlerine genel bakış (C#)
description: LINQ standart sorgu işleçleri, C# ' de filtreleme, projeksiyon, toplama ve sıralama dahil olmak üzere sorgu özellikleri sağlar.
ms.date: 07/20/2015
ms.assetid: 812fa119-5f65-4139-b4fa-55dccd8dc3ac
ms.openlocfilehash: 1ff98e47641dbe7a884b7d6c7758c1fe61b95091
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178781"
---
# <a name="standard-query-operators-overview-c"></a><span data-ttu-id="218cf-103">Standart sorgu Işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="218cf-103">Standard Query Operators Overview (C#)</span></span>

<span data-ttu-id="218cf-104">*Standart sorgu IŞLEÇLERI* LINQ deseninin bulunduğu yöntemlerdir.</span><span class="sxs-lookup"><span data-stu-id="218cf-104">The *standard query operators* are the methods that form the LINQ pattern.</span></span> <span data-ttu-id="218cf-105">Bu yöntemlerin çoğu diziler üzerinde çalışır, burada bir sıra, türü arabirimini veya arabirimi uygulayan bir nesnedir <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Linq.IQueryable%601> .</span><span class="sxs-lookup"><span data-stu-id="218cf-105">Most of these methods operate on sequences, where a sequence is an object whose type implements the <xref:System.Collections.Generic.IEnumerable%601> interface or the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="218cf-106">Standart sorgu işleçleri filtreleme, yansıtma, toplama, sıralama ve daha fazlasını içeren sorgu özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="218cf-106">The standard query operators provide query capabilities including filtering, projection, aggregation, sorting and more.</span></span>  
  
 <span data-ttu-id="218cf-107">LINQ standart sorgu işleçlerinin iki kümesi vardır: türü nesneler üzerinde çalışan diğeri <xref:System.Collections.Generic.IEnumerable%601> , türündeki nesneler üzerinde çalışır <xref:System.Linq.IQueryable%601> .</span><span class="sxs-lookup"><span data-stu-id="218cf-107">There are two sets of LINQ standard query operators: one that operates on objects of type <xref:System.Collections.Generic.IEnumerable%601>, another that operates on objects of type <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="218cf-108">Her kümeyi oluşturan Yöntemler <xref:System.Linq.Enumerable> sırasıyla ve sınıflarının statik üyeleridir <xref:System.Linq.Queryable> .</span><span class="sxs-lookup"><span data-stu-id="218cf-108">The methods that make up each set are static members of the <xref:System.Linq.Enumerable> and <xref:System.Linq.Queryable> classes, respectively.</span></span> <span data-ttu-id="218cf-109">Bunlar üzerinde çalıştıkları türün *Uzantı yöntemleri* olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="218cf-109">They are defined as *extension methods* of the type that they operate on.</span></span> <span data-ttu-id="218cf-110">Uzantı yöntemleri, statik yöntem sözdizimi veya örnek yöntemi sözdizimi kullanılarak çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="218cf-110">Extension methods can be called by using either static method syntax or instance method syntax.</span></span>  
  
 <span data-ttu-id="218cf-111">Ayrıca, birkaç standart sorgu işleci yöntemi, veya tabanlı olanlar dışındaki türler üzerinde çalışır <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Linq.IQueryable%601> .</span><span class="sxs-lookup"><span data-stu-id="218cf-111">In addition, several standard query operator methods operate on types other than those based on <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="218cf-112"><xref:System.Linq.Enumerable>Türü, her ikisi de türündeki nesneler üzerinde çalışan iki yöntemi tanımlar <xref:System.Collections.IEnumerable> .</span><span class="sxs-lookup"><span data-stu-id="218cf-112">The <xref:System.Linq.Enumerable> type defines two such methods that both operate on objects of type <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="218cf-113">Bu yöntemler <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> ve <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29> , parametreli olmayan veya genel olmayan BIR koleksiyonun LINQ düzeninde sorgulanmasını etkinleştirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="218cf-113">These methods, <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> and <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, let you enable a non-parameterized, or non-generic, collection to be queried in the LINQ pattern.</span></span> <span data-ttu-id="218cf-114">Bunu, türü kesin belirlenmiş bir nesne koleksiyonu oluşturarak yapabilirler.</span><span class="sxs-lookup"><span data-stu-id="218cf-114">They do this by creating a strongly typed collection of objects.</span></span> <span data-ttu-id="218cf-115"><xref:System.Linq.Queryable>Sınıfı, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> ve <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29> türündeki nesneler üzerinde çalışan iki benzer yöntemi tanımlar <xref:System.Linq.Queryable> .</span><span class="sxs-lookup"><span data-stu-id="218cf-115">The <xref:System.Linq.Queryable> class defines two similar methods, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> and <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, that operate on objects of type <xref:System.Linq.Queryable>.</span></span>  
  
 <span data-ttu-id="218cf-116">Standart sorgu işleçleri, tek bir değer veya bir dizi değer döndürmediğine bağlı olarak yürütmesinin zamanlamalarına göre farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="218cf-116">The standard query operators differ in the timing of their execution, depending on whether they return a singleton value or a sequence of values.</span></span> <span data-ttu-id="218cf-117">Tek bir değer döndüren Yöntemler (örneğin, <xref:System.Linq.Enumerable.Average%2A> ve <xref:System.Linq.Enumerable.Sum%2A> ) hemen yürütülür.</span><span class="sxs-lookup"><span data-stu-id="218cf-117">Those methods that return a singleton value (for example, <xref:System.Linq.Enumerable.Average%2A> and <xref:System.Linq.Enumerable.Sum%2A>) execute immediately.</span></span> <span data-ttu-id="218cf-118">Bir dizi döndüren yöntemler sorgu yürütmesini erteler ve Numaralandırılabilir bir nesne döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="218cf-118">Methods that return a sequence defer the query execution and return an enumerable object.</span></span>  
  
 <span data-ttu-id="218cf-119">Bellek içi koleksiyonlar üzerinde çalışan yöntemler için, diğer bir deyişle, <xref:System.Collections.Generic.IEnumerable%601> döndürülen sıralanabilir nesne, metoduna geçirilen bağımsız değişkenleri yakalar.</span><span class="sxs-lookup"><span data-stu-id="218cf-119">For methods that operate on in-memory collections, that is, those methods that extend <xref:System.Collections.Generic.IEnumerable%601>, the returned enumerable object captures the arguments that were passed to the method.</span></span> <span data-ttu-id="218cf-120">Bu nesne numaralandırıldıktan sonra, sorgu işlecinin mantığı işe alınır ve sorgu sonuçları döndürülür.</span><span class="sxs-lookup"><span data-stu-id="218cf-120">When that object is enumerated, the logic of the query operator is employed and the query results are returned.</span></span>  
  
 <span data-ttu-id="218cf-121">Buna karşılık, genişleyen Yöntemler <xref:System.Linq.IQueryable%601> herhangi bir sorgulama davranışı uygulamaz.</span><span class="sxs-lookup"><span data-stu-id="218cf-121">In contrast, methods that extend <xref:System.Linq.IQueryable%601> don't implement any querying behavior.</span></span> <span data-ttu-id="218cf-122">Bunlar gerçekleştirilecek sorguyu temsil eden bir ifade ağacı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="218cf-122">They build an expression tree that represents the query to be performed.</span></span> <span data-ttu-id="218cf-123">Sorgu işleme, kaynak nesne tarafından işlenir <xref:System.Linq.IQueryable%601> .</span><span class="sxs-lookup"><span data-stu-id="218cf-123">The query processing is handled by the source <xref:System.Linq.IQueryable%601> object.</span></span>  
  
 <span data-ttu-id="218cf-124">Sorgu yöntemlerine yapılan çağrılar tek bir sorgu içinde birbirine zincirlenebilir ve bu da sorguların rastgele karmaşık olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="218cf-124">Calls to query methods can be chained together in one query, which enables queries to become arbitrarily complex.</span></span>  
  
 <span data-ttu-id="218cf-125">Aşağıdaki kod örneği, bir dizi hakkında bilgi edinmek için standart sorgu işleçlerinin nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="218cf-125">The following code example demonstrates how the standard query operators can be used to obtain information about a sequence.</span></span>  
  
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
  
## <a name="query-expression-syntax"></a><span data-ttu-id="218cf-126">Sorgu Ifadesi söz dizimi</span><span class="sxs-lookup"><span data-stu-id="218cf-126">Query Expression Syntax</span></span>  

 <span data-ttu-id="218cf-127">Daha sık kullanılan standart sorgu işleçlerinden bazılarının, bir *sorgu* *ifadesinin*parçası olarak çağrılmasına olanak sağlayan adanmış C# ve Visual Basic Language anahtar sözcüğü vardır.</span><span class="sxs-lookup"><span data-stu-id="218cf-127">Some of the more frequently used standard query operators have dedicated C# and Visual Basic language keyword syntax that enables them to be called as part of a *query* *expression*.</span></span> <span data-ttu-id="218cf-128">Adanmış anahtar sözcüklere ve bunlara karşılık gelen sözdizimleri içeren standart sorgu işleçleri hakkında daha fazla bilgi için bkz. [Standart sorgu işleçleri Için sorgu Ifadesi sözdizimi (C#)](./query-expression-syntax-for-standard-query-operators.md).</span><span class="sxs-lookup"><span data-stu-id="218cf-128">For more information about standard query operators that have dedicated keywords and their corresponding syntaxes, see [Query Expression Syntax for Standard Query Operators (C#)](./query-expression-syntax-for-standard-query-operators.md).</span></span>  
  
## <a name="extending-the-standard-query-operators"></a><span data-ttu-id="218cf-129">Standart sorgu Işleçlerini genişletme</span><span class="sxs-lookup"><span data-stu-id="218cf-129">Extending the Standard Query Operators</span></span>  

 <span data-ttu-id="218cf-130">Hedef etki alanınız veya teknolojiniz için uygun olan alana özgü Yöntemler oluşturarak standart sorgu işleçleri kümesini daha da getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="218cf-130">You can augment the set of standard query operators by creating domain-specific methods that are appropriate for your target domain or technology.</span></span> <span data-ttu-id="218cf-131">Standart sorgu işleçlerini, uzaktan değerlendirme, sorgu çevirisi ve iyileştirme gibi ek hizmetler sağlayan kendi uygulamalarınız ile de değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="218cf-131">You can also replace the standard query operators with your own implementations that provide additional services such as remote evaluation, query translation, and optimization.</span></span> <span data-ttu-id="218cf-132"><xref:System.Linq.Enumerable.AsEnumerable%2A>Bir örnek için bkz..</span><span class="sxs-lookup"><span data-stu-id="218cf-132">See <xref:System.Linq.Enumerable.AsEnumerable%2A> for an example.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="218cf-133">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="218cf-133">Related Sections</span></span>  

 <span data-ttu-id="218cf-134">Aşağıdaki bağlantılar, işlevleri temel alan çeşitli standart sorgu işleçleri hakkında ek bilgiler sağlayan makalelere götürür.</span><span class="sxs-lookup"><span data-stu-id="218cf-134">The following links take you to articles that provide additional information about the various standard query operators based on functionality.</span></span>  
  
 [<span data-ttu-id="218cf-135">Verileri sıralama (C#)</span><span class="sxs-lookup"><span data-stu-id="218cf-135">Sorting Data (C#)</span></span>](./sorting-data.md)  
  
 [<span data-ttu-id="218cf-136">Ayarlama Işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="218cf-136">Set Operations (C#)</span></span>](./set-operations.md)  
  
 [<span data-ttu-id="218cf-137">Verileri filtreleme (C#)</span><span class="sxs-lookup"><span data-stu-id="218cf-137">Filtering Data (C#)</span></span>](./filtering-data.md)  
  
 [<span data-ttu-id="218cf-138">Nicelik belirteci Işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="218cf-138">Quantifier Operations (C#)</span></span>](./quantifier-operations.md)  
  
 [<span data-ttu-id="218cf-139">Projeksiyon Işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="218cf-139">Projection Operations (C#)</span></span>](./projection-operations.md)  
  
 [<span data-ttu-id="218cf-140">Verileri bölümleme (C#)</span><span class="sxs-lookup"><span data-stu-id="218cf-140">Partitioning Data (C#)</span></span>](./partitioning-data.md)  
  
 [<span data-ttu-id="218cf-141">JOIN Işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="218cf-141">Join Operations (C#)</span></span>](./join-operations.md)  
  
 [<span data-ttu-id="218cf-142">Verileri gruplandırma (C#)</span><span class="sxs-lookup"><span data-stu-id="218cf-142">Grouping Data (C#)</span></span>](./grouping-data.md)  
  
 [<span data-ttu-id="218cf-143">Oluşturma Işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="218cf-143">Generation Operations (C#)</span></span>](./generation-operations.md)  
  
 [<span data-ttu-id="218cf-144">Eşitlik Işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="218cf-144">Equality Operations (C#)</span></span>](./equality-operations.md)  
  
 [<span data-ttu-id="218cf-145">Öğe Işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="218cf-145">Element Operations (C#)</span></span>](./element-operations.md)  
  
 [<span data-ttu-id="218cf-146">Veri türlerini dönüştürme (C#)</span><span class="sxs-lookup"><span data-stu-id="218cf-146">Converting Data Types (C#)</span></span>](./converting-data-types.md)  
  
 [<span data-ttu-id="218cf-147">Birleştirme Işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="218cf-147">Concatenation Operations (C#)</span></span>](./concatenation-operations.md)  
  
 [<span data-ttu-id="218cf-148">Toplama Işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="218cf-148">Aggregation Operations (C#)</span></span>](./aggregation-operations.md)  
  
## <a name="see-also"></a><span data-ttu-id="218cf-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="218cf-149">See also</span></span>

- <xref:System.Linq.Enumerable>
- <xref:System.Linq.Queryable>
- [<span data-ttu-id="218cf-150">LINQ Sorgularına Giriş (C#)</span><span class="sxs-lookup"><span data-stu-id="218cf-150">Introduction to LINQ Queries (C#)</span></span>](./introduction-to-linq-queries.md)
- [<span data-ttu-id="218cf-151">Standart sorgu Işleçleri için sorgu Ifadesi sözdizimi (C#)</span><span class="sxs-lookup"><span data-stu-id="218cf-151">Query Expression Syntax for Standard Query Operators (C#)</span></span>](./query-expression-syntax-for-standard-query-operators.md)
- [<span data-ttu-id="218cf-152">Standart sorgu Işleçlerinin yürütme yöntemine göre sınıflandırılması (C#)</span><span class="sxs-lookup"><span data-stu-id="218cf-152">Classification of Standard Query Operators by Manner of Execution (C#)</span></span>](./classification-of-standard-query-operators-by-manner-of-execution.md)
- [<span data-ttu-id="218cf-153">Uzantı yöntemleri</span><span class="sxs-lookup"><span data-stu-id="218cf-153">Extension Methods</span></span>](../../classes-and-structs/extension-methods.md)
