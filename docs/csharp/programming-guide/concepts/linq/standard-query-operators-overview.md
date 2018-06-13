---
title: Standart sorgu işleçlerine genel bakış (C#)
ms.date: 07/20/2015
ms.assetid: 812fa119-5f65-4139-b4fa-55dccd8dc3ac
ms.openlocfilehash: 36bd5927e64ffacb97beac28b8e7790204e08c5c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33337330"
---
# <a name="standard-query-operators-overview-c"></a><span data-ttu-id="b2138-102">Standart sorgu işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="b2138-102">Standard Query Operators Overview (C#)</span></span>
<span data-ttu-id="b2138-103">*Standart sorgu işleçleri* LINQ düzeni form yöntemleridir.</span><span class="sxs-lookup"><span data-stu-id="b2138-103">The *standard query operators* are the methods that form the LINQ pattern.</span></span> <span data-ttu-id="b2138-104">Bu yöntemlerin çoğu bir dizi türü uygulayan bir nesne olduğu sıraları üzerinde çalışması <xref:System.Collections.Generic.IEnumerable%601> arabirimi veya <xref:System.Linq.IQueryable%601> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="b2138-104">Most of these methods operate on sequences, where a sequence is an object whose type implements the <xref:System.Collections.Generic.IEnumerable%601> interface or the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="b2138-105">Standart sorgu işleçleri filtreleme, yansıtma, toplama, sıralama ve daha fazlası dahil olmak üzere sorgu özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="b2138-105">The standard query operators provide query capabilities including filtering, projection, aggregation, sorting and more.</span></span>  
  
 <span data-ttu-id="b2138-106">LINQ standart sorgu işleçleri, bir tür nesneler üzerinde çalışan iki kümesi vardır <xref:System.Collections.Generic.IEnumerable%601> ve tür nesneler üzerinde çalışan diğer <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="b2138-106">There are two sets of LINQ standard query operators, one that operates on objects of type <xref:System.Collections.Generic.IEnumerable%601> and the other that operates on objects of type <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="b2138-107">Her ayarlama yapmak yöntemleri statik üyeleri olan <xref:System.Linq.Enumerable> ve <xref:System.Linq.Queryable> sınıfları, sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="b2138-107">The methods that make up each set are static members of the <xref:System.Linq.Enumerable> and <xref:System.Linq.Queryable> classes, respectively.</span></span> <span data-ttu-id="b2138-108">Olarak tanımlanan *genişletme yöntemleri* üzerinde çalışacağı türü.</span><span class="sxs-lookup"><span data-stu-id="b2138-108">They are defined as *extension methods* of the type that they operate on.</span></span> <span data-ttu-id="b2138-109">Başka bir deyişle, bunlar statik yöntem sözdizimi veya örnek yöntemi sözdizimini kullanarak çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="b2138-109">This means that they can be called by using either static method syntax or instance method syntax.</span></span>  
  
 <span data-ttu-id="b2138-110">Ayrıca, çeşitli standart sorgu işleci yöntemler türleri üzerinde tabanlı olanlar dışındaki çalışmayabilir <xref:System.Collections.Generic.IEnumerable%601> veya <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="b2138-110">In addition, several standard query operator methods operate on types other than those based on <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="b2138-111"><xref:System.Linq.Enumerable> Türünü tanımlayan iki tür yöntem her ikisi de türündeki nesneler üzerinde çalışan <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="b2138-111">The <xref:System.Linq.Enumerable> type defines two such methods that both operate on objects of type <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="b2138-112">Bu yöntemler <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> ve <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, let LINQ desende Sorgulanacak parametreli olmayan veya genel olmayan, bir toplama etkinleştir.</span><span class="sxs-lookup"><span data-stu-id="b2138-112">These methods, <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> and <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, let you enable a non-parameterized, or non-generic, collection to be queried in the LINQ pattern.</span></span> <span data-ttu-id="b2138-113">Kesin türü belirtilmiş bir nesneler koleksiyonunu oluşturarak bunu.</span><span class="sxs-lookup"><span data-stu-id="b2138-113">They do this by creating a strongly-typed collection of objects.</span></span> <span data-ttu-id="b2138-114"><xref:System.Linq.Queryable> Sınıfı tanımlayan iki benzer yöntemler <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> ve <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, türündeki nesneler üzerinde çalışan <xref:System.Linq.Queryable>.</span><span class="sxs-lookup"><span data-stu-id="b2138-114">The <xref:System.Linq.Queryable> class defines two similar methods, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> and <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, that operate on objects of type <xref:System.Linq.Queryable>.</span></span>  
  
 <span data-ttu-id="b2138-115">Standart sorgu işleçleri, bunlar bir singleton değeri veya değerler dizisini döndürür bağlı olarak, yürütme, zamanlama içinde farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="b2138-115">The standard query operators differ in the timing of their execution, depending on whether they return a singleton value or a sequence of values.</span></span> <span data-ttu-id="b2138-116">Tek değer döndürme bu yöntemleri (örneğin, <xref:System.Linq.Enumerable.Average%2A> ve <xref:System.Linq.Enumerable.Sum%2A>) hemen yürütün.</span><span class="sxs-lookup"><span data-stu-id="b2138-116">Those methods that return a singleton value (for example, <xref:System.Linq.Enumerable.Average%2A> and <xref:System.Linq.Enumerable.Sum%2A>) execute immediately.</span></span> <span data-ttu-id="b2138-117">Bir dizi döndüren yöntemler sorgu yürütme erteleneceği ve bir numaralandırma nesnesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="b2138-117">Methods that return a sequence defer the query execution and return an enumerable object.</span></span>  
  
 <span data-ttu-id="b2138-118">Bellek içi koleksiyonlarında, diğer bir deyişle, genişletme bu yöntemleri çalışması yöntemleri durumunda <xref:System.Collections.Generic.IEnumerable%601>, yönteme geçirilen bağımsız değişken döndürülen numaralandırılabilir nesne yakalar.</span><span class="sxs-lookup"><span data-stu-id="b2138-118">In the case of the methods that operate on in-memory collections, that is, those methods that extend <xref:System.Collections.Generic.IEnumerable%601>, the returned enumerable object captures the arguments that were passed to the method.</span></span> <span data-ttu-id="b2138-119">Bu nesne numaralandırılan sorgu işleci mantığı işe ve sorgusu sonuç döndürmedi.</span><span class="sxs-lookup"><span data-stu-id="b2138-119">When that object is enumerated, the logic of the query operator is employed and the query results are returned.</span></span>  
  
 <span data-ttu-id="b2138-120">Buna karşılık, yöntemleri, genişletme <xref:System.Linq.IQueryable%601> herhangi sorgulanırken davranışı kullanılmaz, ancak gerçekleştirilmesi için sorguyu temsil eden bir ifade ağacına derleme.</span><span class="sxs-lookup"><span data-stu-id="b2138-120">In contrast, methods that extend <xref:System.Linq.IQueryable%601> do not implement any querying behavior, but build an expression tree that represents the query to be performed.</span></span> <span data-ttu-id="b2138-121">Sorgu işleme kaynak tarafından işlenen <xref:System.Linq.IQueryable%601> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="b2138-121">The query processing is handled by the source <xref:System.Linq.IQueryable%601> object.</span></span>  
  
 <span data-ttu-id="b2138-122">Sorgu yöntemleri çağrıları rasgele karmaşık hale gelmesine sorgularını sağlayan, tek bir sorguda birbirine zincirlenebilir.</span><span class="sxs-lookup"><span data-stu-id="b2138-122">Calls to query methods can be chained together in one query, which enables queries to become arbitrarily complex.</span></span>  
  
 <span data-ttu-id="b2138-123">Aşağıdaki kod örneği, bir dizi hakkında bilgi edinmek için standart sorgu işleçleri'nın nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b2138-123">The following code example demonstrates how the standard query operators can be used to obtain information about a sequence.</span></span>  
  
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
  
## <a name="query-expression-syntax"></a><span data-ttu-id="b2138-124">Sorgu ifade sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b2138-124">Query Expression Syntax</span></span>  
 <span data-ttu-id="b2138-125">Bazı daha sık kullanılan standart sorgu işleçleri bunları parçası olarak çağrılacak etkinleştiren C# ve Visual Basic dil anahtar sözcüğü sözdizimini adanmış bir *sorgu* *ifade*.</span><span class="sxs-lookup"><span data-stu-id="b2138-125">Some of the more frequently used standard query operators have dedicated C# and Visual Basic language keyword syntax that enables them to be called as part of a *query* *expression*.</span></span> <span data-ttu-id="b2138-126">Anahtar sözcükler ve bunların karşılık gelen sözdizimleri ayrılmış standart sorgu işleçleri hakkında daha fazla bilgi için bkz: [standart sorgu işleçleri (C#) için sorgu ifade sözdizimi](../../../../csharp/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md).</span><span class="sxs-lookup"><span data-stu-id="b2138-126">For more information about standard query operators that have dedicated keywords and their corresponding syntaxes, see [Query Expression Syntax for Standard Query Operators (C#)](../../../../csharp/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md).</span></span>  
  
## <a name="extending-the-standard-query-operators"></a><span data-ttu-id="b2138-127">Standart sorgu işleçleri genişletme</span><span class="sxs-lookup"><span data-stu-id="b2138-127">Extending the Standard Query Operators</span></span>  
 <span data-ttu-id="b2138-128">Standart sorgu işleçleri kümesi hedef etki alanına veya teknoloji için uygun olan oluşturma etki alanına özgü yöntemlerle genişletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2138-128">You can augment the set of standard query operators by creating domain-specific methods that are appropriate for your target domain or technology.</span></span> <span data-ttu-id="b2138-129">Standart sorgu işleçleri, uzak değerlendirme, sorgu çeviri ve en iyi duruma getirme gibi ek hizmetleri sağlayan kendi uygulamaları ile de değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2138-129">You can also replace the standard query operators with your own implementations that provide additional services such as remote evaluation, query translation, and optimization.</span></span> <span data-ttu-id="b2138-130">Bkz: <xref:System.Linq.Enumerable.AsEnumerable%2A> bir örnek.</span><span class="sxs-lookup"><span data-stu-id="b2138-130">See <xref:System.Linq.Enumerable.AsEnumerable%2A> for an example.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b2138-131">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="b2138-131">Related Sections</span></span>  
 <span data-ttu-id="b2138-132">Aşağıdaki bağlantılar işlevselliğine bağlı çeşitli standart sorgu işleçleri hakkında ek bilgiler sağlayan konulara götürür.</span><span class="sxs-lookup"><span data-stu-id="b2138-132">The following links take you to topics that provide additional information about the various standard query operators based on functionality.</span></span>  
  
 [<span data-ttu-id="b2138-133">Veri sıralama (C#)</span><span class="sxs-lookup"><span data-stu-id="b2138-133">Sorting Data (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/sorting-data.md)  
  
 [<span data-ttu-id="b2138-134">Ayarlama işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="b2138-134">Set Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/set-operations.md)  
  
 [<span data-ttu-id="b2138-135">Filtre verileri (C#)</span><span class="sxs-lookup"><span data-stu-id="b2138-135">Filtering Data (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/filtering-data.md)  
  
 [<span data-ttu-id="b2138-136">Niceleyici işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="b2138-136">Quantifier Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/quantifier-operations.md)  
  
 [<span data-ttu-id="b2138-137">Projeksiyon işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="b2138-137">Projection Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projection-operations.md)  
  
 [<span data-ttu-id="b2138-138">Bölümleme verileri (C#)</span><span class="sxs-lookup"><span data-stu-id="b2138-138">Partitioning Data (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/partitioning-data.md)  
  
 [<span data-ttu-id="b2138-139">Birleştirme işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="b2138-139">Join Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/join-operations.md)  
  
 [<span data-ttu-id="b2138-140">Verileri gruplandırma (C#)</span><span class="sxs-lookup"><span data-stu-id="b2138-140">Grouping Data (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/grouping-data.md)  
  
 [<span data-ttu-id="b2138-141">Oluşturma işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="b2138-141">Generation Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/generation-operations.md)  
  
 [<span data-ttu-id="b2138-142">Eşitlik işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="b2138-142">Equality Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/equality-operations.md)  
  
 [<span data-ttu-id="b2138-143">Öğe işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="b2138-143">Element Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/element-operations.md)  
  
 [<span data-ttu-id="b2138-144">Dönüştürme veri türleri (C#)</span><span class="sxs-lookup"><span data-stu-id="b2138-144">Converting Data Types (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/converting-data-types.md)  
  
 [<span data-ttu-id="b2138-145">Birleştirme işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="b2138-145">Concatenation Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/concatenation-operations.md)  
  
 [<span data-ttu-id="b2138-146">Toplama işlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="b2138-146">Aggregation Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/aggregation-operations.md)  
  
## <a name="see-also"></a><span data-ttu-id="b2138-147">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b2138-147">See Also</span></span>  
 <xref:System.Linq.Enumerable>  
 <xref:System.Linq.Queryable>  
 [<span data-ttu-id="b2138-148">Giriş LINQ sorgularını (C#)</span><span class="sxs-lookup"><span data-stu-id="b2138-148">Introduction to LINQ Queries (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)  
 [<span data-ttu-id="b2138-149">Standart sorgu işleçleri (C#) için sorgu ifade sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b2138-149">Query Expression Syntax for Standard Query Operators (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)  
 [<span data-ttu-id="b2138-150">Standart sorgu işleçleri yürütme (C#) yöntemine göre sınıflandırılması</span><span class="sxs-lookup"><span data-stu-id="b2138-150">Classification of Standard Query Operators by Manner of Execution (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)  
 [<span data-ttu-id="b2138-151">Genişletme Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="b2138-151">Extension Methods</span></span>](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
