---
title: Standart sorgu işleçlerine genel bakış (C#)
ms.date: 07/20/2015
ms.assetid: 812fa119-5f65-4139-b4fa-55dccd8dc3ac
ms.openlocfilehash: 7ce3a13c98bf08eae79906f1806427741568155e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61680512"
---
# <a name="standard-query-operators-overview-c"></a><span data-ttu-id="3e656-102">Standart sorgu işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="3e656-102">Standard Query Operators Overview (C#)</span></span>
<span data-ttu-id="3e656-103">*Standart sorgu işleçleri* LINQ desen form yöntemlerdir.</span><span class="sxs-lookup"><span data-stu-id="3e656-103">The *standard query operators* are the methods that form the LINQ pattern.</span></span> <span data-ttu-id="3e656-104">Bu yöntemlerin çoğu bir dizi türü uygulayan bir nesne olduğu dizileri üzerinde çalışması <xref:System.Collections.Generic.IEnumerable%601> arabirimi veya <xref:System.Linq.IQueryable%601> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="3e656-104">Most of these methods operate on sequences, where a sequence is an object whose type implements the <xref:System.Collections.Generic.IEnumerable%601> interface or the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="3e656-105">Standart sorgu işleçleri, filtreleme, projeksiyon, toplama, sıralama ve daha fazlası dahil olmak üzere sorgu işlevleri sağlayın.</span><span class="sxs-lookup"><span data-stu-id="3e656-105">The standard query operators provide query capabilities including filtering, projection, aggregation, sorting and more.</span></span>  
  
 <span data-ttu-id="3e656-106">LINQ standart sorgu işleçlerinin, türündeki nesneler üzerinde çalışan bir iki kümesi <xref:System.Collections.Generic.IEnumerable%601> ve türündeki nesneler üzerinde çalışan diğer <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="3e656-106">There are two sets of LINQ standard query operators, one that operates on objects of type <xref:System.Collections.Generic.IEnumerable%601> and the other that operates on objects of type <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="3e656-107">Her bir kümesini oluşturan yöntemleri statik üyeleridir <xref:System.Linq.Enumerable> ve <xref:System.Linq.Queryable> sınıfları, sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="3e656-107">The methods that make up each set are static members of the <xref:System.Linq.Enumerable> and <xref:System.Linq.Queryable> classes, respectively.</span></span> <span data-ttu-id="3e656-108">Olarak tanımlanan *genişletme yöntemleri* türündeki bunlar üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="3e656-108">They are defined as *extension methods* of the type that they operate on.</span></span> <span data-ttu-id="3e656-109">Başka bir deyişle, bunlar statik yöntem sözdizimi veya örnek yöntem sözdizimi kullanılarak çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="3e656-109">This means that they can be called by using either static method syntax or instance method syntax.</span></span>  
  
 <span data-ttu-id="3e656-110">Ayrıca, birçok standart sorgu işleci yöntemleri türlerine göre dışındaki çalışan <xref:System.Collections.Generic.IEnumerable%601> veya <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="3e656-110">In addition, several standard query operator methods operate on types other than those based on <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="3e656-111"><xref:System.Linq.Enumerable> Türünü tanımlayan iki yöntem her ikisi de türündeki nesneler üzerinde çalışan <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="3e656-111">The <xref:System.Linq.Enumerable> type defines two such methods that both operate on objects of type <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="3e656-112">Bu yöntemler <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> ve <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, let LINQ desen Sorgulanacak forceseek veya genel olmayan, bir koleksiyon etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="3e656-112">These methods, <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> and <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, let you enable a non-parameterized, or non-generic, collection to be queried in the LINQ pattern.</span></span> <span data-ttu-id="3e656-113">Bunlar nesneleri türü kesin belirlenmiş koleksiyonu oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3e656-113">They do this by creating a strongly-typed collection of objects.</span></span> <span data-ttu-id="3e656-114"><xref:System.Linq.Queryable> Sınıfı tanımlayan iki benzer yöntem <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> ve <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, türündeki nesneler üzerinde çalışan <xref:System.Linq.Queryable>.</span><span class="sxs-lookup"><span data-stu-id="3e656-114">The <xref:System.Linq.Queryable> class defines two similar methods, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> and <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, that operate on objects of type <xref:System.Linq.Queryable>.</span></span>  
  
 <span data-ttu-id="3e656-115">Standart sorgu işleçleri, bunlar bir tekil değer veya değerlerini bir dizi döndürür bağlı olarak, yürütme, zamanlama içinde farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="3e656-115">The standard query operators differ in the timing of their execution, depending on whether they return a singleton value or a sequence of values.</span></span> <span data-ttu-id="3e656-116">Tekil değer döndüren bu yöntemler (örneğin, <xref:System.Linq.Enumerable.Average%2A> ve <xref:System.Linq.Enumerable.Sum%2A>) hemen yürütün.</span><span class="sxs-lookup"><span data-stu-id="3e656-116">Those methods that return a singleton value (for example, <xref:System.Linq.Enumerable.Average%2A> and <xref:System.Linq.Enumerable.Sum%2A>) execute immediately.</span></span> <span data-ttu-id="3e656-117">Bir dizi döndüren yöntemler, sorgu yürütme ertele ve bir numaralandırma nesnesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="3e656-117">Methods that return a sequence defer the query execution and return an enumerable object.</span></span>  
  
 <span data-ttu-id="3e656-118">Bellek içi koleksiyonlarda genişleten bu yöntemler diğer bir deyişle, çalışan yöntemleri söz konusu olduğunda <xref:System.Collections.Generic.IEnumerable%601>, yönteme geçirilen bağımsız değişkenler döndürülen numaralandırılabilir nesne yakalar.</span><span class="sxs-lookup"><span data-stu-id="3e656-118">In the case of the methods that operate on in-memory collections, that is, those methods that extend <xref:System.Collections.Generic.IEnumerable%601>, the returned enumerable object captures the arguments that were passed to the method.</span></span> <span data-ttu-id="3e656-119">Bu nesne numaralandırılana sorgu işleci mantığını işe ve sorgu sonuçları döndürülür.</span><span class="sxs-lookup"><span data-stu-id="3e656-119">When that object is enumerated, the logic of the query operator is employed and the query results are returned.</span></span>  
  
 <span data-ttu-id="3e656-120">Buna karşılık, yöntemleri, genişleten <xref:System.Linq.IQueryable%601> herhangi bir davranış sorgulanırken kullanılmaz, ancak gerçekleştirilmesi için sorguyu temsil eden ifade ağacında oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3e656-120">In contrast, methods that extend <xref:System.Linq.IQueryable%601> do not implement any querying behavior, but build an expression tree that represents the query to be performed.</span></span> <span data-ttu-id="3e656-121">Sorgu işleme kaynak tarafından işlendiğini <xref:System.Linq.IQueryable%601> nesne.</span><span class="sxs-lookup"><span data-stu-id="3e656-121">The query processing is handled by the source <xref:System.Linq.IQueryable%601> object.</span></span>  
  
 <span data-ttu-id="3e656-122">Sorgu yöntemlere yapılan çağrılar, sorguları rasgele karmaşık olmasını sağlayan bir sorguda birbirine zincirlenebilir.</span><span class="sxs-lookup"><span data-stu-id="3e656-122">Calls to query methods can be chained together in one query, which enables queries to become arbitrarily complex.</span></span>  
  
 <span data-ttu-id="3e656-123">Aşağıdaki kod örneği, bir dizi hakkında bilgi edinmek için standart sorgu işleçleri'nın nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3e656-123">The following code example demonstrates how the standard query operators can be used to obtain information about a sequence.</span></span>  
  
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
  
## <a name="query-expression-syntax"></a><span data-ttu-id="3e656-124">Sorgu ifadesi söz dizimi</span><span class="sxs-lookup"><span data-stu-id="3e656-124">Query Expression Syntax</span></span>  
 <span data-ttu-id="3e656-125">Bazı daha sık kullanılan standart sorgu işleçlerinin bir parçası olarak çağrılacak tanıyan C# ve Visual Basic dili anahtar sözcüğü sözdizimini adanmış bir *sorgu* *ifade*.</span><span class="sxs-lookup"><span data-stu-id="3e656-125">Some of the more frequently used standard query operators have dedicated C# and Visual Basic language keyword syntax that enables them to be called as part of a *query* *expression*.</span></span> <span data-ttu-id="3e656-126">Anahtar sözcükleri ve bunların karşılık gelen sözdizimleri adanmış standart sorgu işleçleri hakkında daha fazla bilgi için bkz. [standart sorgu işleçleri (C#) için sorgu ifade sözdizimi](../../../../csharp/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md).</span><span class="sxs-lookup"><span data-stu-id="3e656-126">For more information about standard query operators that have dedicated keywords and their corresponding syntaxes, see [Query Expression Syntax for Standard Query Operators (C#)](../../../../csharp/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md).</span></span>  
  
## <a name="extending-the-standard-query-operators"></a><span data-ttu-id="3e656-127">Standart sorgu işleçlerini genişletme</span><span class="sxs-lookup"><span data-stu-id="3e656-127">Extending the Standard Query Operators</span></span>  
 <span data-ttu-id="3e656-128">Hedef etki alanına veya teknoloji için uygun olan oluşturma etki alanına özgü yöntemlerle standart sorgu işleçleri kümesini genişletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e656-128">You can augment the set of standard query operators by creating domain-specific methods that are appropriate for your target domain or technology.</span></span> <span data-ttu-id="3e656-129">Uzak değerlendirme, sorgu çevirisi ve en iyi duruma getirme gibi ek hizmetler sağlayan kendi uygulamaları ile standart sorgu işleçleri de değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3e656-129">You can also replace the standard query operators with your own implementations that provide additional services such as remote evaluation, query translation, and optimization.</span></span> <span data-ttu-id="3e656-130">Bkz: <xref:System.Linq.Enumerable.AsEnumerable%2A> örneği.</span><span class="sxs-lookup"><span data-stu-id="3e656-130">See <xref:System.Linq.Enumerable.AsEnumerable%2A> for an example.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3e656-131">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="3e656-131">Related Sections</span></span>  
 <span data-ttu-id="3e656-132">Aşağıdaki bağlantılar işlevselliğine bağlı olarak çeşitli standart sorgu işleçleri hakkında ek bilgiler sağlayan konulara yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="3e656-132">The following links take you to topics that provide additional information about the various standard query operators based on functionality.</span></span>  
  
 [<span data-ttu-id="3e656-133">Verileri sıralama (C#)</span><span class="sxs-lookup"><span data-stu-id="3e656-133">Sorting Data (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/sorting-data.md)  
  
 [<span data-ttu-id="3e656-134">Ayarlama işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="3e656-134">Set Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/set-operations.md)  
  
 [<span data-ttu-id="3e656-135">Verileri filtreleme (C#)</span><span class="sxs-lookup"><span data-stu-id="3e656-135">Filtering Data (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/filtering-data.md)  
  
 [<span data-ttu-id="3e656-136">Niceleyici işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="3e656-136">Quantifier Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/quantifier-operations.md)  
  
 [<span data-ttu-id="3e656-137">Projeksiyon işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="3e656-137">Projection Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projection-operations.md)  
  
 [<span data-ttu-id="3e656-138">Veri bölümleme (C#)</span><span class="sxs-lookup"><span data-stu-id="3e656-138">Partitioning Data (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/partitioning-data.md)  
  
 [<span data-ttu-id="3e656-139">Birleştirme işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="3e656-139">Join Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/join-operations.md)  
  
 [<span data-ttu-id="3e656-140">Verileri gruplandırma (C#)</span><span class="sxs-lookup"><span data-stu-id="3e656-140">Grouping Data (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/grouping-data.md)  
  
 [<span data-ttu-id="3e656-141">Oluşturma işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="3e656-141">Generation Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/generation-operations.md)  
  
 [<span data-ttu-id="3e656-142">Eşitlik işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="3e656-142">Equality Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/equality-operations.md)  
  
 [<span data-ttu-id="3e656-143">Öğe işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="3e656-143">Element Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/element-operations.md)  
  
 [<span data-ttu-id="3e656-144">Veri türlerini dönüştürme (C#)</span><span class="sxs-lookup"><span data-stu-id="3e656-144">Converting Data Types (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/converting-data-types.md)  
  
 [<span data-ttu-id="3e656-145">Birleştirme işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="3e656-145">Concatenation Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/concatenation-operations.md)  
  
 [<span data-ttu-id="3e656-146">Toplama işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="3e656-146">Aggregation Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/aggregation-operations.md)  
  
## <a name="see-also"></a><span data-ttu-id="3e656-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3e656-147">See also</span></span>

- <xref:System.Linq.Enumerable>
- <xref:System.Linq.Queryable>
- [<span data-ttu-id="3e656-148">LINQ sorguları (C#) giriş</span><span class="sxs-lookup"><span data-stu-id="3e656-148">Introduction to LINQ Queries (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)
- [<span data-ttu-id="3e656-149">Standart sorgu işleçleri (C#) için sorgu ifade sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3e656-149">Query Expression Syntax for Standard Query Operators (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)
- [<span data-ttu-id="3e656-150">Standart sorgu işleçlerinin yöntemine göre sınıflandırılması yürütme (C#)</span><span class="sxs-lookup"><span data-stu-id="3e656-150">Classification of Standard Query Operators by Manner of Execution (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)
- [<span data-ttu-id="3e656-151">Genişletme Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="3e656-151">Extension Methods</span></span>](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
