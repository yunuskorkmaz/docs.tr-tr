---
title: Standart Sorgu Operatörlerine Genel Bakış (C#)
ms.date: 07/20/2015
ms.assetid: 812fa119-5f65-4139-b4fa-55dccd8dc3ac
ms.openlocfilehash: 76c2c4684f33c3fb30748b5f08efd215548661ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167861"
---
# <a name="standard-query-operators-overview-c"></a><span data-ttu-id="32b51-102">Standart Sorgu Operatörlerine Genel Bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="32b51-102">Standard Query Operators Overview (C#)</span></span>
<span data-ttu-id="32b51-103">*Standart sorgu işleçleri* LINQ deseni oluşturan yöntemlerdir.</span><span class="sxs-lookup"><span data-stu-id="32b51-103">The *standard query operators* are the methods that form the LINQ pattern.</span></span> <span data-ttu-id="32b51-104">Bu yöntemlerin çoğu, bir dizinin <xref:System.Collections.Generic.IEnumerable%601> arabirimi veya <xref:System.Linq.IQueryable%601> arabirimi uygulayan bir nesne olduğu diziler üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="32b51-104">Most of these methods operate on sequences, where a sequence is an object whose type implements the <xref:System.Collections.Generic.IEnumerable%601> interface or the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="32b51-105">Standart sorgu işleçleri filtreleme, projeksiyon, toplama, sıralama ve daha fazlası dahil olmak üzere sorgu yetenekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="32b51-105">The standard query operators provide query capabilities including filtering, projection, aggregation, sorting and more.</span></span>  
  
 <span data-ttu-id="32b51-106">LinQ standart sorgu işleçleri, bir tür <xref:System.Collections.Generic.IEnumerable%601> nesneleri üzerinde çalışan ve diğer tür <xref:System.Linq.IQueryable%601>nesneleri üzerinde çalışan iki küme vardır.</span><span class="sxs-lookup"><span data-stu-id="32b51-106">There are two sets of LINQ standard query operators, one that operates on objects of type <xref:System.Collections.Generic.IEnumerable%601> and the other that operates on objects of type <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="32b51-107">Her kümeyi oluşturan yöntemler sırasıyla <xref:System.Linq.Enumerable> sınıfların <xref:System.Linq.Queryable> statik üyeleridir.</span><span class="sxs-lookup"><span data-stu-id="32b51-107">The methods that make up each set are static members of the <xref:System.Linq.Enumerable> and <xref:System.Linq.Queryable> classes, respectively.</span></span> <span data-ttu-id="32b51-108">Bunlar, çalıştıkları türün *uzantı yöntemleri* olarak tanımlanırlar.</span><span class="sxs-lookup"><span data-stu-id="32b51-108">They are defined as *extension methods* of the type that they operate on.</span></span> <span data-ttu-id="32b51-109">Bu, statik yöntem sözdizimi veya örnek yöntemi sözdizimi kullanılarak çağrılabileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="32b51-109">This means that they can be called by using either static method syntax or instance method syntax.</span></span>  
  
 <span data-ttu-id="32b51-110">Buna ek olarak, çeşitli standart sorgu işleci <xref:System.Collections.Generic.IEnumerable%601> yöntemleri, temel veya . <xref:System.Linq.IQueryable%601></span><span class="sxs-lookup"><span data-stu-id="32b51-110">In addition, several standard query operator methods operate on types other than those based on <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="32b51-111">Tür, <xref:System.Linq.Enumerable> her ikisi de tür <xref:System.Collections.IEnumerable>nesneleri üzerinde çalışan bu tür iki yöntem tanımlar.</span><span class="sxs-lookup"><span data-stu-id="32b51-111">The <xref:System.Linq.Enumerable> type defines two such methods that both operate on objects of type <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="32b51-112">Bu yöntemler <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>ve , linq deseninde sorgulanmak için parametreli olmayan veya genel olmayan bir koleksiyon etkinleştirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="32b51-112">These methods, <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> and <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, let you enable a non-parameterized, or non-generic, collection to be queried in the LINQ pattern.</span></span> <span data-ttu-id="32b51-113">Bunu, güçlü bir şekilde yazılan nesneler koleksiyonu oluşturarak yaparlar.</span><span class="sxs-lookup"><span data-stu-id="32b51-113">They do this by creating a strongly-typed collection of objects.</span></span> <span data-ttu-id="32b51-114">Sınıf <xref:System.Linq.Queryable> iki benzer yöntem <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> tanımlar <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>ve , türü <xref:System.Linq.Queryable>nesneleri üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="32b51-114">The <xref:System.Linq.Queryable> class defines two similar methods, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> and <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, that operate on objects of type <xref:System.Linq.Queryable>.</span></span>  
  
 <span data-ttu-id="32b51-115">Standart sorgu işleçleri, tek ton değeri veya bir değer dizisi döndürüp döndürmediklerine bağlı olarak yürütme zamanlaması açısından farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="32b51-115">The standard query operators differ in the timing of their execution, depending on whether they return a singleton value or a sequence of values.</span></span> <span data-ttu-id="32b51-116">Singleton değerini döndüren bu yöntemler <xref:System.Linq.Enumerable.Average%2A> <xref:System.Linq.Enumerable.Sum%2A>(örneğin, ve) hemen çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="32b51-116">Those methods that return a singleton value (for example, <xref:System.Linq.Enumerable.Average%2A> and <xref:System.Linq.Enumerable.Sum%2A>) execute immediately.</span></span> <span data-ttu-id="32b51-117">Sırayı döndüren yöntemler sorgu yürütmesini erteler ve sayısal bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="32b51-117">Methods that return a sequence defer the query execution and return an enumerable object.</span></span>  
  
 <span data-ttu-id="32b51-118">Bellek içi koleksiyonları nda çalışan yöntemler söz konusu olduğunda, yani uzabilen <xref:System.Collections.Generic.IEnumerable%601>bu yöntemlerde, döndürülen sayısal nesne yönteme geçirilen bağımsız değişkenleri yakalar.</span><span class="sxs-lookup"><span data-stu-id="32b51-118">In the case of the methods that operate on in-memory collections, that is, those methods that extend <xref:System.Collections.Generic.IEnumerable%601>, the returned enumerable object captures the arguments that were passed to the method.</span></span> <span data-ttu-id="32b51-119">Bu nesne numaralandırıldığında, sorgu işlecinin mantığı kullanılır ve sorgu sonuçları döndürülür.</span><span class="sxs-lookup"><span data-stu-id="32b51-119">When that object is enumerated, the logic of the query operator is employed and the query results are returned.</span></span>  
  
 <span data-ttu-id="32b51-120">Buna karşılık, genişleten <xref:System.Linq.IQueryable%601> yöntemler herhangi bir sorgu davranışı uygulamaz, ancak gerçekleştirilecek sorguyu temsil eden bir ifade ağacı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="32b51-120">In contrast, methods that extend <xref:System.Linq.IQueryable%601> do not implement any querying behavior, but build an expression tree that represents the query to be performed.</span></span> <span data-ttu-id="32b51-121">Sorgu işleme kaynak <xref:System.Linq.IQueryable%601> nesne tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="32b51-121">The query processing is handled by the source <xref:System.Linq.IQueryable%601> object.</span></span>  
  
 <span data-ttu-id="32b51-122">Sorgu yöntemlerine yapılan çağrılar, sorguların rasgele karmaşık hale gelmesine olanak tanıyan tek bir sorguda birbirine zincirlenebilir.</span><span class="sxs-lookup"><span data-stu-id="32b51-122">Calls to query methods can be chained together in one query, which enables queries to become arbitrarily complex.</span></span>  
  
 <span data-ttu-id="32b51-123">Aşağıdaki kod örneği, standart sorgu işleçlerinin bir dizi hakkında bilgi edinmek için nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="32b51-123">The following code example demonstrates how the standard query operators can be used to obtain information about a sequence.</span></span>  
  
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
  
## <a name="query-expression-syntax"></a><span data-ttu-id="32b51-124">Sorgu İfade Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="32b51-124">Query Expression Syntax</span></span>  
 <span data-ttu-id="32b51-125">Daha sık kullanılan standart sorgu işleçlerinden bazıları, *sorgu* *ifadesinin*bir parçası olarak çağrılmasını sağlayan C# ve Visual Basic dil sözdizimini adadı.</span><span class="sxs-lookup"><span data-stu-id="32b51-125">Some of the more frequently used standard query operators have dedicated C# and Visual Basic language keyword syntax that enables them to be called as part of a *query* *expression*.</span></span> <span data-ttu-id="32b51-126">Özel anahtar kelimeleri ve bunların karşılık gelen sözdizimi leri olan standart sorgu işleçleri hakkında daha fazla bilgi [için, Standart Sorgu Operatörleri (C#) için Sorgu İfadesözdizimi'ne](./query-expression-syntax-for-standard-query-operators.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="32b51-126">For more information about standard query operators that have dedicated keywords and their corresponding syntaxes, see [Query Expression Syntax for Standard Query Operators (C#)](./query-expression-syntax-for-standard-query-operators.md).</span></span>  
  
## <a name="extending-the-standard-query-operators"></a><span data-ttu-id="32b51-127">Standart Sorgu Operatörlerini Genişletme</span><span class="sxs-lookup"><span data-stu-id="32b51-127">Extending the Standard Query Operators</span></span>  
 <span data-ttu-id="32b51-128">Hedef etki alanınız veya teknolojiniz için uygun etki alanına özgü yöntemler oluşturarak standart sorgu işleçleri kümesini artırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="32b51-128">You can augment the set of standard query operators by creating domain-specific methods that are appropriate for your target domain or technology.</span></span> <span data-ttu-id="32b51-129">Ayrıca, standart sorgu işleçlerini uzaktan değerlendirme, sorgu çevirisi ve optimizasyon gibi ek hizmetler sağlayan kendi uygulamalarınızla da değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="32b51-129">You can also replace the standard query operators with your own implementations that provide additional services such as remote evaluation, query translation, and optimization.</span></span> <span data-ttu-id="32b51-130">Bir <xref:System.Linq.Enumerable.AsEnumerable%2A> örnek için bkz.</span><span class="sxs-lookup"><span data-stu-id="32b51-130">See <xref:System.Linq.Enumerable.AsEnumerable%2A> for an example.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="32b51-131">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="32b51-131">Related Sections</span></span>  
 <span data-ttu-id="32b51-132">Aşağıdaki bağlantılar, işlevsellik dayalı çeşitli standart sorgu operatörleri hakkında ek bilgi sağlayan konulara götürür.</span><span class="sxs-lookup"><span data-stu-id="32b51-132">The following links take you to topics that provide additional information about the various standard query operators based on functionality.</span></span>  
  
 [<span data-ttu-id="32b51-133">Verileri Sıralama (C#)</span><span class="sxs-lookup"><span data-stu-id="32b51-133">Sorting Data (C#)</span></span>](./sorting-data.md)  
  
 [<span data-ttu-id="32b51-134">İşlemleri Ayarla (C#)</span><span class="sxs-lookup"><span data-stu-id="32b51-134">Set Operations (C#)</span></span>](./set-operations.md)  
  
 [<span data-ttu-id="32b51-135">Veri Filtreleme (C#)</span><span class="sxs-lookup"><span data-stu-id="32b51-135">Filtering Data (C#)</span></span>](./filtering-data.md)  
  
 [<span data-ttu-id="32b51-136">Niceleyici İşlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="32b51-136">Quantifier Operations (C#)</span></span>](./quantifier-operations.md)  
  
 [<span data-ttu-id="32b51-137">Projeksiyon İşlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="32b51-137">Projection Operations (C#)</span></span>](./projection-operations.md)  
  
 [<span data-ttu-id="32b51-138">Veri Bölümleme (C#)</span><span class="sxs-lookup"><span data-stu-id="32b51-138">Partitioning Data (C#)</span></span>](./partitioning-data.md)  
  
 [<span data-ttu-id="32b51-139">İşleme Katılma (C#)</span><span class="sxs-lookup"><span data-stu-id="32b51-139">Join Operations (C#)</span></span>](./join-operations.md)  
  
 [<span data-ttu-id="32b51-140">Verileri Gruplandırma (C#)</span><span class="sxs-lookup"><span data-stu-id="32b51-140">Grouping Data (C#)</span></span>](./grouping-data.md)  
  
 [<span data-ttu-id="32b51-141">Üretim İşlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="32b51-141">Generation Operations (C#)</span></span>](./generation-operations.md)  
  
 [<span data-ttu-id="32b51-142">Eşitlik İşlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="32b51-142">Equality Operations (C#)</span></span>](./equality-operations.md)  
  
 [<span data-ttu-id="32b51-143">Eleman İşlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="32b51-143">Element Operations (C#)</span></span>](./element-operations.md)  
  
 [<span data-ttu-id="32b51-144">Veri Türlerini Dönüştürme (C#)</span><span class="sxs-lookup"><span data-stu-id="32b51-144">Converting Data Types (C#)</span></span>](./converting-data-types.md)  
  
 [<span data-ttu-id="32b51-145">Concatenation İşlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="32b51-145">Concatenation Operations (C#)</span></span>](./concatenation-operations.md)  
  
 [<span data-ttu-id="32b51-146">Toplama İşlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="32b51-146">Aggregation Operations (C#)</span></span>](./aggregation-operations.md)  
  
## <a name="see-also"></a><span data-ttu-id="32b51-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32b51-147">See also</span></span>

- <xref:System.Linq.Enumerable>
- <xref:System.Linq.Queryable>
- [<span data-ttu-id="32b51-148">LINQ Sorgularına Giriş (C#)</span><span class="sxs-lookup"><span data-stu-id="32b51-148">Introduction to LINQ Queries (C#)</span></span>](./introduction-to-linq-queries.md)
- [<span data-ttu-id="32b51-149">Standart Sorgu Operatörleri için Sorgu İfade Sözdizimi (C#)</span><span class="sxs-lookup"><span data-stu-id="32b51-149">Query Expression Syntax for Standard Query Operators (C#)</span></span>](./query-expression-syntax-for-standard-query-operators.md)
- [<span data-ttu-id="32b51-150">Standart Sorgu Operatörlerinin Yürütme Şekline Göre Sınıflandırılması (C#)</span><span class="sxs-lookup"><span data-stu-id="32b51-150">Classification of Standard Query Operators by Manner of Execution (C#)</span></span>](./classification-of-standard-query-operators-by-manner-of-execution.md)
- [<span data-ttu-id="32b51-151">Genişletme Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="32b51-151">Extension Methods</span></span>](../../classes-and-structs/extension-methods.md)
