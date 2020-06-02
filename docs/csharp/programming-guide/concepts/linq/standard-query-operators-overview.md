---
title: Standart sorgu Işleçlerine genel bakış (C#)
ms.date: 07/20/2015
ms.assetid: 812fa119-5f65-4139-b4fa-55dccd8dc3ac
ms.openlocfilehash: 2327ed84734e4f4ad826e02ed4e30b8784a59716
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287432"
---
# <a name="standard-query-operators-overview-c"></a><span data-ttu-id="18204-102">Standart sorgu Işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="18204-102">Standard Query Operators Overview (C#)</span></span>
<span data-ttu-id="18204-103">*Standart sorgu IŞLEÇLERI* LINQ deseninin bulunduğu yöntemlerdir.</span><span class="sxs-lookup"><span data-stu-id="18204-103">The *standard query operators* are the methods that form the LINQ pattern.</span></span> <span data-ttu-id="18204-104">Bu yöntemlerin çoğu diziler üzerinde çalışır, burada bir sıra, türü arabirimini veya arabirimi uygulayan bir nesnedir <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Linq.IQueryable%601> .</span><span class="sxs-lookup"><span data-stu-id="18204-104">Most of these methods operate on sequences, where a sequence is an object whose type implements the <xref:System.Collections.Generic.IEnumerable%601> interface or the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="18204-105">Standart sorgu işleçleri filtreleme, yansıtma, toplama, sıralama ve daha fazlasını içeren sorgu özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="18204-105">The standard query operators provide query capabilities including filtering, projection, aggregation, sorting and more.</span></span>  
  
 <span data-ttu-id="18204-106">Türü nesneler üzerinde çalışan diğeri türü nesneler üzerinde çalışan iki LINQ standart sorgu işleci kümesi vardır <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Linq.IQueryable%601> .</span><span class="sxs-lookup"><span data-stu-id="18204-106">There are two sets of LINQ standard query operators, one that operates on objects of type <xref:System.Collections.Generic.IEnumerable%601> and the other that operates on objects of type <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="18204-107">Her kümeyi oluşturan Yöntemler <xref:System.Linq.Enumerable> sırasıyla ve sınıflarının statik üyeleridir <xref:System.Linq.Queryable> .</span><span class="sxs-lookup"><span data-stu-id="18204-107">The methods that make up each set are static members of the <xref:System.Linq.Enumerable> and <xref:System.Linq.Queryable> classes, respectively.</span></span> <span data-ttu-id="18204-108">Bunlar üzerinde çalıştıkları türün *Uzantı yöntemleri* olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="18204-108">They are defined as *extension methods* of the type that they operate on.</span></span> <span data-ttu-id="18204-109">Uzantı yöntemleri, statik yöntem sözdizimi veya örnek yöntemi sözdizimi kullanılarak çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="18204-109">Extension methods can be called by using either static method syntax or instance method syntax.</span></span>  
  
 <span data-ttu-id="18204-110">Ayrıca, birkaç standart sorgu işleci yöntemi, veya tabanlı olanlar dışındaki türler üzerinde çalışır <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Linq.IQueryable%601> .</span><span class="sxs-lookup"><span data-stu-id="18204-110">In addition, several standard query operator methods operate on types other than those based on <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="18204-111"><xref:System.Linq.Enumerable>Türü, her ikisi de türündeki nesneler üzerinde çalışan iki yöntemi tanımlar <xref:System.Collections.IEnumerable> .</span><span class="sxs-lookup"><span data-stu-id="18204-111">The <xref:System.Linq.Enumerable> type defines two such methods that both operate on objects of type <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="18204-112">Bu yöntemler <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> ve <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29> , parametreli olmayan veya genel olmayan BIR koleksiyonun LINQ düzeninde sorgulanmasını etkinleştirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="18204-112">These methods, <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> and <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, let you enable a non-parameterized, or non-generic, collection to be queried in the LINQ pattern.</span></span> <span data-ttu-id="18204-113">Bunu, türü kesin belirlenmiş bir nesne koleksiyonu oluşturarak yapabilirler.</span><span class="sxs-lookup"><span data-stu-id="18204-113">They do this by creating a strongly typed collection of objects.</span></span> <span data-ttu-id="18204-114"><xref:System.Linq.Queryable>Sınıfı, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> ve <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29> türündeki nesneler üzerinde çalışan iki benzer yöntemi tanımlar <xref:System.Linq.Queryable> .</span><span class="sxs-lookup"><span data-stu-id="18204-114">The <xref:System.Linq.Queryable> class defines two similar methods, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> and <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, that operate on objects of type <xref:System.Linq.Queryable>.</span></span>  
  
 <span data-ttu-id="18204-115">Standart sorgu işleçleri, tek bir değer veya bir dizi değer döndürmediğine bağlı olarak yürütmesinin zamanlamalarına göre farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="18204-115">The standard query operators differ in the timing of their execution, depending on whether they return a singleton value or a sequence of values.</span></span> <span data-ttu-id="18204-116">Tek bir değer döndüren Yöntemler (örneğin, <xref:System.Linq.Enumerable.Average%2A> ve <xref:System.Linq.Enumerable.Sum%2A> ) hemen yürütülür.</span><span class="sxs-lookup"><span data-stu-id="18204-116">Those methods that return a singleton value (for example, <xref:System.Linq.Enumerable.Average%2A> and <xref:System.Linq.Enumerable.Sum%2A>) execute immediately.</span></span> <span data-ttu-id="18204-117">Bir dizi döndüren yöntemler sorgu yürütmesini erteler ve Numaralandırılabilir bir nesne döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="18204-117">Methods that return a sequence defer the query execution and return an enumerable object.</span></span>  
  
 <span data-ttu-id="18204-118">Bellek içi koleksiyonlar üzerinde çalışan yöntemler için, diğer bir deyişle, <xref:System.Collections.Generic.IEnumerable%601> döndürülen sıralanabilir nesne, metoduna geçirilen bağımsız değişkenleri yakalar.</span><span class="sxs-lookup"><span data-stu-id="18204-118">For methods that operate on in-memory collections, that is, those methods that extend <xref:System.Collections.Generic.IEnumerable%601>, the returned enumerable object captures the arguments that were passed to the method.</span></span> <span data-ttu-id="18204-119">Bu nesne numaralandırıldıktan sonra, sorgu işlecinin mantığı işe alınır ve sorgu sonuçları döndürülür.</span><span class="sxs-lookup"><span data-stu-id="18204-119">When that object is enumerated, the logic of the query operator is employed and the query results are returned.</span></span>  
  
 <span data-ttu-id="18204-120">Buna karşılık, genişleyen Yöntemler <xref:System.Linq.IQueryable%601> herhangi bir sorgulama davranışı uygulamaz, ancak gerçekleştirilecek sorguyu temsil eden bir ifade ağacı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="18204-120">In contrast, methods that extend <xref:System.Linq.IQueryable%601> do not implement any querying behavior, but build an expression tree that represents the query to be performed.</span></span> <span data-ttu-id="18204-121">Sorgu işleme, kaynak nesne tarafından işlenir <xref:System.Linq.IQueryable%601> .</span><span class="sxs-lookup"><span data-stu-id="18204-121">The query processing is handled by the source <xref:System.Linq.IQueryable%601> object.</span></span>  
  
 <span data-ttu-id="18204-122">Sorgu yöntemlerine yapılan çağrılar tek bir sorgu içinde birbirine zincirlenebilir ve bu da sorguların rastgele karmaşık olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="18204-122">Calls to query methods can be chained together in one query, which enables queries to become arbitrarily complex.</span></span>  
  
 <span data-ttu-id="18204-123">Aşağıdaki kod örneği, bir dizi hakkında bilgi edinmek için standart sorgu işleçlerinin nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="18204-123">The following code example demonstrates how the standard query operators can be used to obtain information about a sequence.</span></span>  
  
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
  
## <a name="query-expression-syntax"></a><span data-ttu-id="18204-124">Sorgu Ifadesi söz dizimi</span><span class="sxs-lookup"><span data-stu-id="18204-124">Query Expression Syntax</span></span>  
 <span data-ttu-id="18204-125">Daha sık kullanılan standart sorgu işleçlerinden bazılarının, bir *sorgu* *ifadesinin*parçası olarak çağrılmasına olanak sağlayan adanmış C# ve Visual Basic Language anahtar sözcüğü vardır.</span><span class="sxs-lookup"><span data-stu-id="18204-125">Some of the more frequently used standard query operators have dedicated C# and Visual Basic language keyword syntax that enables them to be called as part of a *query* *expression*.</span></span> <span data-ttu-id="18204-126">Adanmış anahtar sözcüklere ve bunlara karşılık gelen sözdizimleri içeren standart sorgu işleçleri hakkında daha fazla bilgi için bkz. [Standart sorgu işleçleri Için sorgu Ifadesi sözdizimi (C#)](./query-expression-syntax-for-standard-query-operators.md).</span><span class="sxs-lookup"><span data-stu-id="18204-126">For more information about standard query operators that have dedicated keywords and their corresponding syntaxes, see [Query Expression Syntax for Standard Query Operators (C#)](./query-expression-syntax-for-standard-query-operators.md).</span></span>  
  
## <a name="extending-the-standard-query-operators"></a><span data-ttu-id="18204-127">Standart sorgu Işleçlerini genişletme</span><span class="sxs-lookup"><span data-stu-id="18204-127">Extending the Standard Query Operators</span></span>  
 <span data-ttu-id="18204-128">Hedef etki alanınız veya teknolojiniz için uygun olan alana özgü Yöntemler oluşturarak standart sorgu işleçleri kümesini daha da getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="18204-128">You can augment the set of standard query operators by creating domain-specific methods that are appropriate for your target domain or technology.</span></span> <span data-ttu-id="18204-129">Standart sorgu işleçlerini, uzaktan değerlendirme, sorgu çevirisi ve iyileştirme gibi ek hizmetler sağlayan kendi uygulamalarınız ile de değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="18204-129">You can also replace the standard query operators with your own implementations that provide additional services such as remote evaluation, query translation, and optimization.</span></span> <span data-ttu-id="18204-130"><xref:System.Linq.Enumerable.AsEnumerable%2A>Bir örnek için bkz..</span><span class="sxs-lookup"><span data-stu-id="18204-130">See <xref:System.Linq.Enumerable.AsEnumerable%2A> for an example.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="18204-131">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="18204-131">Related Sections</span></span>  
 <span data-ttu-id="18204-132">Aşağıdaki bağlantılar, işlevleri temel alan çeşitli standart sorgu işleçleri hakkında ek bilgiler sağlayan konulara götürür.</span><span class="sxs-lookup"><span data-stu-id="18204-132">The following links take you to topics that provide additional information about the various standard query operators based on functionality.</span></span>  
  
 [<span data-ttu-id="18204-133">Verileri sıralama (C#)</span><span class="sxs-lookup"><span data-stu-id="18204-133">Sorting Data (C#)</span></span>](./sorting-data.md)  
  
 [<span data-ttu-id="18204-134">Ayarlama Işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="18204-134">Set Operations (C#)</span></span>](./set-operations.md)  
  
 [<span data-ttu-id="18204-135">Verileri filtreleme (C#)</span><span class="sxs-lookup"><span data-stu-id="18204-135">Filtering Data (C#)</span></span>](./filtering-data.md)  
  
 [<span data-ttu-id="18204-136">Nicelik belirteci Işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="18204-136">Quantifier Operations (C#)</span></span>](./quantifier-operations.md)  
  
 [<span data-ttu-id="18204-137">Projeksiyon Işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="18204-137">Projection Operations (C#)</span></span>](./projection-operations.md)  
  
 [<span data-ttu-id="18204-138">Verileri bölümleme (C#)</span><span class="sxs-lookup"><span data-stu-id="18204-138">Partitioning Data (C#)</span></span>](./partitioning-data.md)  
  
 [<span data-ttu-id="18204-139">JOIN Işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="18204-139">Join Operations (C#)</span></span>](./join-operations.md)  
  
 [<span data-ttu-id="18204-140">Verileri gruplandırma (C#)</span><span class="sxs-lookup"><span data-stu-id="18204-140">Grouping Data (C#)</span></span>](./grouping-data.md)  
  
 [<span data-ttu-id="18204-141">Oluşturma Işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="18204-141">Generation Operations (C#)</span></span>](./generation-operations.md)  
  
 [<span data-ttu-id="18204-142">Eşitlik Işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="18204-142">Equality Operations (C#)</span></span>](./equality-operations.md)  
  
 [<span data-ttu-id="18204-143">Öğe Işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="18204-143">Element Operations (C#)</span></span>](./element-operations.md)  
  
 [<span data-ttu-id="18204-144">Veri türlerini dönüştürme (C#)</span><span class="sxs-lookup"><span data-stu-id="18204-144">Converting Data Types (C#)</span></span>](./converting-data-types.md)  
  
 [<span data-ttu-id="18204-145">Birleştirme Işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="18204-145">Concatenation Operations (C#)</span></span>](./concatenation-operations.md)  
  
 [<span data-ttu-id="18204-146">Toplama Işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="18204-146">Aggregation Operations (C#)</span></span>](./aggregation-operations.md)  
  
## <a name="see-also"></a><span data-ttu-id="18204-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="18204-147">See also</span></span>

- <xref:System.Linq.Enumerable>
- <xref:System.Linq.Queryable>
- [<span data-ttu-id="18204-148">LINQ Sorgularına Giriş (C#)</span><span class="sxs-lookup"><span data-stu-id="18204-148">Introduction to LINQ Queries (C#)</span></span>](./introduction-to-linq-queries.md)
- [<span data-ttu-id="18204-149">Standart sorgu Işleçleri için sorgu Ifadesi sözdizimi (C#)</span><span class="sxs-lookup"><span data-stu-id="18204-149">Query Expression Syntax for Standard Query Operators (C#)</span></span>](./query-expression-syntax-for-standard-query-operators.md)
- [<span data-ttu-id="18204-150">Standart sorgu Işleçlerinin yürütme yöntemine göre sınıflandırılması (C#)</span><span class="sxs-lookup"><span data-stu-id="18204-150">Classification of Standard Query Operators by Manner of Execution (C#)</span></span>](./classification-of-standard-query-operators-by-manner-of-execution.md)
- [<span data-ttu-id="18204-151">Uzantı Metotları</span><span class="sxs-lookup"><span data-stu-id="18204-151">Extension Methods</span></span>](../../classes-and-structs/extension-methods.md)
