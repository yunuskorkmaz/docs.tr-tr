---
title: Standart sorgu işleçlerine genel bakış (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 302bd39e-2ec1-495b-94bf-37d370d6f05f
ms.openlocfilehash: 9bfdf2163be52d9016a800d65006bbc4fbf560a3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58841478"
---
# <a name="standard-query-operators-overview-visual-basic"></a><span data-ttu-id="128b0-102">Standart sorgu işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="128b0-102">Standard Query Operators Overview (Visual Basic)</span></span>
<span data-ttu-id="128b0-103">*Standart sorgu işleçleri* LINQ desen form yöntemlerdir.</span><span class="sxs-lookup"><span data-stu-id="128b0-103">The *standard query operators* are the methods that form the LINQ pattern.</span></span> <span data-ttu-id="128b0-104">Bu yöntemlerin çoğu bir dizi türü uygulayan bir nesne olduğu dizileri üzerinde çalışması <xref:System.Collections.Generic.IEnumerable%601> arabirimi veya <xref:System.Linq.IQueryable%601> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="128b0-104">Most of these methods operate on sequences, where a sequence is an object whose type implements the <xref:System.Collections.Generic.IEnumerable%601> interface or the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="128b0-105">Standart sorgu işleçleri, filtreleme, projeksiyon, toplama, sıralama ve daha fazlası dahil olmak üzere sorgu işlevleri sağlayın.</span><span class="sxs-lookup"><span data-stu-id="128b0-105">The standard query operators provide query capabilities including filtering, projection, aggregation, sorting and more.</span></span>  
  
 <span data-ttu-id="128b0-106">LINQ standart sorgu işleçlerinin, türündeki nesneler üzerinde çalışan bir iki kümesi <xref:System.Collections.Generic.IEnumerable%601> ve türündeki nesneler üzerinde çalışan diğer <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="128b0-106">There are two sets of LINQ standard query operators, one that operates on objects of type <xref:System.Collections.Generic.IEnumerable%601> and the other that operates on objects of type <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="128b0-107">Her bir kümesini oluşturan yöntemleri statik üyeleridir <xref:System.Linq.Enumerable> ve <xref:System.Linq.Queryable> sınıfları, sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="128b0-107">The methods that make up each set are static members of the <xref:System.Linq.Enumerable> and <xref:System.Linq.Queryable> classes, respectively.</span></span> <span data-ttu-id="128b0-108">Olarak tanımlanan *genişletme yöntemleri* türündeki bunlar üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="128b0-108">They are defined as *extension methods* of the type that they operate on.</span></span> <span data-ttu-id="128b0-109">Başka bir deyişle, bunlar statik yöntem sözdizimi veya örnek yöntem sözdizimi kullanılarak çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="128b0-109">This means that they can be called by using either static method syntax or instance method syntax.</span></span>  
  
 <span data-ttu-id="128b0-110">Ayrıca, birçok standart sorgu işleci yöntemleri türlerine göre dışındaki çalışan <xref:System.Collections.Generic.IEnumerable%601> veya <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="128b0-110">In addition, several standard query operator methods operate on types other than those based on <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="128b0-111"><xref:System.Linq.Enumerable> Türünü tanımlayan iki yöntem her ikisi de türündeki nesneler üzerinde çalışan <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="128b0-111">The <xref:System.Linq.Enumerable> type defines two such methods that both operate on objects of type <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="128b0-112">Bu yöntemler <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> ve <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, let LINQ desen Sorgulanacak forceseek veya genel olmayan, bir koleksiyon etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="128b0-112">These methods, <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> and <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, let you enable a non-parameterized, or non-generic, collection to be queried in the LINQ pattern.</span></span> <span data-ttu-id="128b0-113">Bunlar nesneleri türü kesin belirlenmiş koleksiyonu oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="128b0-113">They do this by creating a strongly-typed collection of objects.</span></span> <span data-ttu-id="128b0-114"><xref:System.Linq.Queryable> Sınıfı tanımlayan iki benzer yöntem <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> ve <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, türündeki nesneler üzerinde çalışan <xref:System.Linq.Queryable>.</span><span class="sxs-lookup"><span data-stu-id="128b0-114">The <xref:System.Linq.Queryable> class defines two similar methods, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> and <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, that operate on objects of type <xref:System.Linq.Queryable>.</span></span>  
  
 <span data-ttu-id="128b0-115">Standart sorgu işleçleri, bunlar bir tekil değer veya değerlerini bir dizi döndürür bağlı olarak, yürütme, zamanlama içinde farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="128b0-115">The standard query operators differ in the timing of their execution, depending on whether they return a singleton value or a sequence of values.</span></span> <span data-ttu-id="128b0-116">Tekil değer döndüren bu yöntemler (örneğin, <xref:System.Linq.Enumerable.Average%2A> ve <xref:System.Linq.Enumerable.Sum%2A>) hemen yürütün.</span><span class="sxs-lookup"><span data-stu-id="128b0-116">Those methods that return a singleton value (for example, <xref:System.Linq.Enumerable.Average%2A> and <xref:System.Linq.Enumerable.Sum%2A>) execute immediately.</span></span> <span data-ttu-id="128b0-117">Bir dizi döndüren yöntemler, sorgu yürütme ertele ve bir numaralandırma nesnesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="128b0-117">Methods that return a sequence defer the query execution and return an enumerable object.</span></span>  
  
 <span data-ttu-id="128b0-118">Bellek içi koleksiyonlarda genişleten bu yöntemler diğer bir deyişle, çalışan yöntemleri söz konusu olduğunda <xref:System.Collections.Generic.IEnumerable%601>, yönteme geçirilen bağımsız değişkenler döndürülen numaralandırılabilir nesne yakalar.</span><span class="sxs-lookup"><span data-stu-id="128b0-118">In the case of the methods that operate on in-memory collections, that is, those methods that extend <xref:System.Collections.Generic.IEnumerable%601>, the returned enumerable object captures the arguments that were passed to the method.</span></span> <span data-ttu-id="128b0-119">Bu nesne numaralandırılana sorgu işleci mantığını işe ve sorgu sonuçları döndürülür.</span><span class="sxs-lookup"><span data-stu-id="128b0-119">When that object is enumerated, the logic of the query operator is employed and the query results are returned.</span></span>  
  
 <span data-ttu-id="128b0-120">Buna karşılık, yöntemleri, genişleten <xref:System.Linq.IQueryable%601> herhangi bir davranış sorgulanırken kullanılmaz, ancak gerçekleştirilmesi için sorguyu temsil eden ifade ağacında oluşturun.</span><span class="sxs-lookup"><span data-stu-id="128b0-120">In contrast, methods that extend <xref:System.Linq.IQueryable%601> do not implement any querying behavior, but build an expression tree that represents the query to be performed.</span></span> <span data-ttu-id="128b0-121">Sorgu işleme kaynak tarafından işlendiğini <xref:System.Linq.IQueryable%601> nesne.</span><span class="sxs-lookup"><span data-stu-id="128b0-121">The query processing is handled by the source <xref:System.Linq.IQueryable%601> object.</span></span>  
  
 <span data-ttu-id="128b0-122">Sorgu yöntemlere yapılan çağrılar, sorguları rasgele karmaşık olmasını sağlayan bir sorguda birbirine zincirlenebilir.</span><span class="sxs-lookup"><span data-stu-id="128b0-122">Calls to query methods can be chained together in one query, which enables queries to become arbitrarily complex.</span></span>  
  
 <span data-ttu-id="128b0-123">Aşağıdaki kod örneği, bir dizi hakkında bilgi edinmek için standart sorgu işleçleri'nın nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="128b0-123">The following code example demonstrates how the standard query operators can be used to obtain information about a sequence.</span></span>  
  
```vb  
Dim sentence = "the quick brown fox jumps over the lazy dog"  
' Split the string into individual words to create a collection.  
Dim words = sentence.Split(" "c)  
  
Dim query = From word In words   
            Group word.ToUpper() By word.Length Into gr = Group   
            Order By Length _  
            Select Length, GroupedWords = gr  
  
Dim output As New System.Text.StringBuilder  
For Each obj In query  
    output.AppendLine(String.Format("Words of length {0}:", obj.Length))  
    For Each word As String In obj.GroupedWords  
        output.AppendLine(word)  
    Next  
Next  
  
'Display the output  
MsgBox(output.ToString())  
  
' This code example produces the following output:  
'  
' Words of length 3:  
' THE  
' FOX  
' THE  
' DOG  
' Words of length 4:  
' OVER  
' LAZY  
' Words of length 5:  
' QUICK  
' BROWN  
' JUMPS   
```  
  
## <a name="query-expression-syntax"></a><span data-ttu-id="128b0-124">Sorgu ifadesi söz dizimi</span><span class="sxs-lookup"><span data-stu-id="128b0-124">Query Expression Syntax</span></span>  
 <span data-ttu-id="128b0-125">Bazı daha sık kullanılan standart sorgu işleçlerinin bir parçası olarak çağrılacak tanıyan C# ve Visual Basic dili anahtar sözcüğü sözdizimini adanmış bir *sorgu* *ifade*.</span><span class="sxs-lookup"><span data-stu-id="128b0-125">Some of the more frequently used standard query operators have dedicated C# and Visual Basic language keyword syntax that enables them to be called as part of a *query* *expression*.</span></span> <span data-ttu-id="128b0-126">Anahtar sözcükleri ve bunların karşılık gelen sözdizimleri adanmış standart sorgu işleçleri hakkında daha fazla bilgi için bkz. [standart sorgu işleçleri (Visual Basic) için sorgu ifade sözdizimi](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md).</span><span class="sxs-lookup"><span data-stu-id="128b0-126">For more information about standard query operators that have dedicated keywords and their corresponding syntaxes, see [Query Expression Syntax for Standard Query Operators (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md).</span></span>  
  
## <a name="extending-the-standard-query-operators"></a><span data-ttu-id="128b0-127">Standart sorgu işleçlerini genişletme</span><span class="sxs-lookup"><span data-stu-id="128b0-127">Extending the Standard Query Operators</span></span>  
 <span data-ttu-id="128b0-128">Hedef etki alanına veya teknoloji için uygun olan oluşturma etki alanına özgü yöntemlerle standart sorgu işleçleri kümesini genişletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="128b0-128">You can augment the set of standard query operators by creating domain-specific methods that are appropriate for your target domain or technology.</span></span> <span data-ttu-id="128b0-129">Uzak değerlendirme, sorgu çevirisi ve en iyi duruma getirme gibi ek hizmetler sağlayan kendi uygulamaları ile standart sorgu işleçleri de değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="128b0-129">You can also replace the standard query operators with your own implementations that provide additional services such as remote evaluation, query translation, and optimization.</span></span> <span data-ttu-id="128b0-130">Bkz: <xref:System.Linq.Enumerable.AsEnumerable%2A> örneği.</span><span class="sxs-lookup"><span data-stu-id="128b0-130">See <xref:System.Linq.Enumerable.AsEnumerable%2A> for an example.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="128b0-131">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="128b0-131">Related Sections</span></span>  
 <span data-ttu-id="128b0-132">Aşağıdaki bağlantılar işlevselliğine bağlı olarak çeşitli standart sorgu işleçleri hakkında ek bilgiler sağlayan konulara yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="128b0-132">The following links take you to topics that provide additional information about the various standard query operators based on functionality.</span></span>  
  
 [<span data-ttu-id="128b0-133">Verileri Sıralama</span><span class="sxs-lookup"><span data-stu-id="128b0-133">Sorting Data</span></span>](../../../../visual-basic/programming-guide/concepts/linq/sorting-data.md)  
  
 [<span data-ttu-id="128b0-134">Ayarlama işlemleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="128b0-134">Set Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/set-operations.md)  
  
 [<span data-ttu-id="128b0-135">Filtre verileri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="128b0-135">Filtering Data (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/filtering-data.md)  
  
 [<span data-ttu-id="128b0-136">Niceleyici işlemleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="128b0-136">Quantifier Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)  
  
 [<span data-ttu-id="128b0-137">Projeksiyon işlemleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="128b0-137">Projection Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)  
  
 [<span data-ttu-id="128b0-138">Bölümleme veri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="128b0-138">Partitioning Data (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/partitioning-data.md)  
  
 [<span data-ttu-id="128b0-139">Birleştirme işlemleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="128b0-139">Join Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/join-operations.md)  
  
 [<span data-ttu-id="128b0-140">Gruplandırma veri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="128b0-140">Grouping Data (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/grouping-data.md)  
  
 [<span data-ttu-id="128b0-141">Oluşturma işlemleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="128b0-141">Generation Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/generation-operations.md)  
  
 [<span data-ttu-id="128b0-142">Eşitlik işlemleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="128b0-142">Equality Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/equality-operations.md)  
  
 [<span data-ttu-id="128b0-143">Öğe işlemleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="128b0-143">Element Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/element-operations.md)  
  
 [<span data-ttu-id="128b0-144">Dönüştürme veri türleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="128b0-144">Converting Data Types (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md)  
  
 [<span data-ttu-id="128b0-145">Birleştirme işlemleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="128b0-145">Concatenation Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/concatenation-operations.md)  
  
 [<span data-ttu-id="128b0-146">Toplama işlemleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="128b0-146">Aggregation Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md)  
  
## <a name="see-also"></a><span data-ttu-id="128b0-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="128b0-147">See also</span></span>

- <xref:System.Linq.Enumerable>
- <xref:System.Linq.Queryable>
- [<span data-ttu-id="128b0-148">Lınq'ye giriş (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="128b0-148">Introduction to LINQ (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)
- [<span data-ttu-id="128b0-149">Standart sorgu işleçleri (Visual Basic) için sorgu ifade sözdizimi</span><span class="sxs-lookup"><span data-stu-id="128b0-149">Query Expression Syntax for Standard Query Operators (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)
- [<span data-ttu-id="128b0-150">Standart sorgu işleçlerinin yöntemine göre sınıflandırılması yürütme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="128b0-150">Classification of Standard Query Operators by Manner of Execution (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)
- [<span data-ttu-id="128b0-151">Genişletme Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="128b0-151">Extension Methods</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
