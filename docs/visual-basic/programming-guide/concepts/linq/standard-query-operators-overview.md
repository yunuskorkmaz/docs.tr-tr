---
title: Standart sorgu Işleçlerine genel bakış (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 302bd39e-2ec1-495b-94bf-37d370d6f05f
ms.openlocfilehash: 22ae1f89379deff0436177d792382c434348b2d4
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524016"
---
# <a name="standard-query-operators-overview-visual-basic"></a><span data-ttu-id="c9048-102">Standart sorgu Işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9048-102">Standard Query Operators Overview (Visual Basic)</span></span>

<span data-ttu-id="c9048-103">*Standart sorgu IŞLEÇLERI* LINQ deseninin bulunduğu yöntemlerdir.</span><span class="sxs-lookup"><span data-stu-id="c9048-103">The *standard query operators* are the methods that form the LINQ pattern.</span></span> <span data-ttu-id="c9048-104">Bu yöntemlerin çoğu diziler üzerinde çalışır, burada bir sıra, türü <xref:System.Collections.Generic.IEnumerable%601> arabirimini veya <xref:System.Linq.IQueryable%601> arabirimini uygulayan bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="c9048-104">Most of these methods operate on sequences, where a sequence is an object whose type implements the <xref:System.Collections.Generic.IEnumerable%601> interface or the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="c9048-105">Standart sorgu işleçleri filtreleme, yansıtma, toplama, sıralama ve daha fazlasını içeren sorgu özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="c9048-105">The standard query operators provide query capabilities including filtering, projection, aggregation, sorting and more.</span></span>

<span data-ttu-id="c9048-106">@No__t_0 türünde nesneler üzerinde çalışan diğeri, <xref:System.Linq.IQueryable%601> türündeki nesneler üzerinde çalışan iki LINQ standart sorgu işleci kümesi vardır.</span><span class="sxs-lookup"><span data-stu-id="c9048-106">There are two sets of LINQ standard query operators, one that operates on objects of type <xref:System.Collections.Generic.IEnumerable%601> and the other that operates on objects of type <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="c9048-107">Her kümeyi oluşturan Yöntemler sırasıyla <xref:System.Linq.Enumerable> ve <xref:System.Linq.Queryable> sınıflarının statik üyeleridir.</span><span class="sxs-lookup"><span data-stu-id="c9048-107">The methods that make up each set are static members of the <xref:System.Linq.Enumerable> and <xref:System.Linq.Queryable> classes, respectively.</span></span> <span data-ttu-id="c9048-108">Bunlar üzerinde çalıştıkları türün *Uzantı yöntemleri* olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c9048-108">They are defined as *extension methods* of the type that they operate on.</span></span> <span data-ttu-id="c9048-109">Bu, statik yöntem sözdizimi veya örnek yöntemi sözdizimi kullanılarak çağrılabilecek anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c9048-109">This means that they can be called by using either static method syntax or instance method syntax.</span></span>

<span data-ttu-id="c9048-110">Ayrıca, bazı standart sorgu işleci yöntemleri <xref:System.Collections.Generic.IEnumerable%601> veya <xref:System.Linq.IQueryable%601> temel alan türler üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="c9048-110">In addition, several standard query operator methods operate on types other than those based on <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="c9048-111">@No__t_0 türü, her ikisi de <xref:System.Collections.IEnumerable> türündeki nesneler üzerinde çalışan iki yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c9048-111">The <xref:System.Linq.Enumerable> type defines two such methods that both operate on objects of type <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="c9048-112">Bu yöntemler, <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> ve <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, parametreli olmayan veya genel olmayan bir koleksiyonun LINQ düzeninde sorgulanmasını etkinleştirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c9048-112">These methods, <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> and <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, let you enable a non-parameterized, or non-generic, collection to be queried in the LINQ pattern.</span></span> <span data-ttu-id="c9048-113">Bu, nesne türü kesin belirlenmiş bir koleksiyon oluşturarak bunu yapabilirler.</span><span class="sxs-lookup"><span data-stu-id="c9048-113">They do this by creating a strongly-typed collection of objects.</span></span> <span data-ttu-id="c9048-114">@No__t_0 sınıfı, <xref:System.Linq.Queryable> türünde nesneler üzerinde çalışan <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> ve <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29> benzer iki yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c9048-114">The <xref:System.Linq.Queryable> class defines two similar methods, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> and <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, that operate on objects of type <xref:System.Linq.Queryable>.</span></span>

<span data-ttu-id="c9048-115">Standart sorgu işleçleri, tek bir değer veya bir dizi değer döndürmediğine bağlı olarak yürütmesinin zamanlamalarına göre farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="c9048-115">The standard query operators differ in the timing of their execution, depending on whether they return a singleton value or a sequence of values.</span></span> <span data-ttu-id="c9048-116">Tek bir değer döndüren Yöntemler (örneğin, <xref:System.Linq.Enumerable.Average%2A> ve <xref:System.Linq.Enumerable.Sum%2A>) hemen yürütülür.</span><span class="sxs-lookup"><span data-stu-id="c9048-116">Those methods that return a singleton value (for example, <xref:System.Linq.Enumerable.Average%2A> and <xref:System.Linq.Enumerable.Sum%2A>) execute immediately.</span></span> <span data-ttu-id="c9048-117">Bir dizi döndüren yöntemler sorgu yürütmesini erteler ve Numaralandırılabilir bir nesne döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="c9048-117">Methods that return a sequence defer the query execution and return an enumerable object.</span></span>

<span data-ttu-id="c9048-118">Bellek içi koleksiyonlar üzerinde çalışan yöntemler söz konusu olduğunda, diğer bir deyişle, <xref:System.Collections.Generic.IEnumerable%601> genişleten Yöntemler, döndürülen sıralanabilir nesne yöntemine geçirilen bağımsız değişkenleri yakalar.</span><span class="sxs-lookup"><span data-stu-id="c9048-118">In the case of the methods that operate on in-memory collections, that is, those methods that extend <xref:System.Collections.Generic.IEnumerable%601>, the returned enumerable object captures the arguments that were passed to the method.</span></span> <span data-ttu-id="c9048-119">Bu nesne numaralandırıldıktan sonra, sorgu işlecinin mantığı işe alınır ve sorgu sonuçları döndürülür.</span><span class="sxs-lookup"><span data-stu-id="c9048-119">When that object is enumerated, the logic of the query operator is employed and the query results are returned.</span></span>

<span data-ttu-id="c9048-120">Buna karşılık, <xref:System.Linq.IQueryable%601> genişleyen Yöntemler herhangi bir sorgulama davranışı uygulamaz, ancak gerçekleştirilecek sorguyu temsil eden bir ifade ağacı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c9048-120">In contrast, methods that extend <xref:System.Linq.IQueryable%601> do not implement any querying behavior, but build an expression tree that represents the query to be performed.</span></span> <span data-ttu-id="c9048-121">Sorgu işleme, kaynak <xref:System.Linq.IQueryable%601> nesnesi tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="c9048-121">The query processing is handled by the source <xref:System.Linq.IQueryable%601> object.</span></span>

<span data-ttu-id="c9048-122">Sorgu yöntemlerine yapılan çağrılar tek bir sorgu içinde birbirine zincirlenebilir ve bu da sorguların rastgele karmaşık olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="c9048-122">Calls to query methods can be chained together in one query, which enables queries to become arbitrarily complex.</span></span>

<span data-ttu-id="c9048-123">Aşağıdaki kod örneği, bir dizi hakkında bilgi edinmek için standart sorgu işleçlerinin nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c9048-123">The following code example demonstrates how the standard query operators can be used to obtain information about a sequence.</span></span>

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

## <a name="query-expression-syntax"></a><span data-ttu-id="c9048-124">Sorgu Ifadesi söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c9048-124">Query Expression Syntax</span></span>

<span data-ttu-id="c9048-125">Daha sık kullanılan standart sorgu işleçlerinden bazılarının, bir C# *sorgu* *ifadesinin*parçası olarak çağrılmasına olanak tanıyan adanmış ve Visual Basic Language anahtar sözcüğü sözdizimi vardır.</span><span class="sxs-lookup"><span data-stu-id="c9048-125">Some of the more frequently used standard query operators have dedicated C# and Visual Basic language keyword syntax that enables them to be called as part of a *query* *expression*.</span></span> <span data-ttu-id="c9048-126">Adanmış anahtar sözcüklere ve bunlara karşılık gelen sözdizimleri içeren standart sorgu işleçleri hakkında daha fazla bilgi için bkz. [Standart sorgu işleçleri Için sorgu Ifadesi sözdizimi (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md).</span><span class="sxs-lookup"><span data-stu-id="c9048-126">For more information about standard query operators that have dedicated keywords and their corresponding syntaxes, see [Query Expression Syntax for Standard Query Operators (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md).</span></span>

## <a name="extending-the-standard-query-operators"></a><span data-ttu-id="c9048-127">Standart sorgu Işleçlerini genişletme</span><span class="sxs-lookup"><span data-stu-id="c9048-127">Extending the Standard Query Operators</span></span>

<span data-ttu-id="c9048-128">Hedef etki alanınız veya teknolojiniz için uygun olan alana özgü Yöntemler oluşturarak standart sorgu işleçleri kümesini daha da getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9048-128">You can augment the set of standard query operators by creating domain-specific methods that are appropriate for your target domain or technology.</span></span> <span data-ttu-id="c9048-129">Standart sorgu işleçlerini, uzaktan değerlendirme, sorgu çevirisi ve iyileştirme gibi ek hizmetler sağlayan kendi uygulamalarınız ile de değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9048-129">You can also replace the standard query operators with your own implementations that provide additional services such as remote evaluation, query translation, and optimization.</span></span> <span data-ttu-id="c9048-130">Bir örnek için bkz. <xref:System.Linq.Enumerable.AsEnumerable%2A>.</span><span class="sxs-lookup"><span data-stu-id="c9048-130">See <xref:System.Linq.Enumerable.AsEnumerable%2A> for an example.</span></span>

## <a name="related-sections"></a><span data-ttu-id="c9048-131">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="c9048-131">Related Sections</span></span>

<span data-ttu-id="c9048-132">Aşağıdaki bağlantılar, işlevleri temel alan çeşitli standart sorgu işleçleri hakkında ek bilgiler sağlayan konulara götürür.</span><span class="sxs-lookup"><span data-stu-id="c9048-132">The following links take you to topics that provide additional information about the various standard query operators based on functionality.</span></span>

- [<span data-ttu-id="c9048-133">Verileri Sıralama</span><span class="sxs-lookup"><span data-stu-id="c9048-133">Sorting Data</span></span>](../../../../visual-basic/programming-guide/concepts/linq/sorting-data.md)

- [<span data-ttu-id="c9048-134">Işlemleri ayarlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9048-134">Set Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/set-operations.md)

- [<span data-ttu-id="c9048-135">Verileri filtreleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9048-135">Filtering Data (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/filtering-data.md)

- [<span data-ttu-id="c9048-136">Nicelik belirteci Işlemleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9048-136">Quantifier Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)

- [<span data-ttu-id="c9048-137">Projeksiyon Işlemleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9048-137">Projection Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)

- [<span data-ttu-id="c9048-138">Verileri bölümlendirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9048-138">Partitioning Data (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/partitioning-data.md)

- [<span data-ttu-id="c9048-139">JOIN Işlemleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9048-139">Join Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/join-operations.md)

- [<span data-ttu-id="c9048-140">Verileri gruplandırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9048-140">Grouping Data (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/grouping-data.md)

- [<span data-ttu-id="c9048-141">Oluşturma Işlemleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9048-141">Generation Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/generation-operations.md)

- [<span data-ttu-id="c9048-142">Eşitlik Işlemleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9048-142">Equality Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/equality-operations.md)

- [<span data-ttu-id="c9048-143">Öğe Işlemleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9048-143">Element Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/element-operations.md)

- [<span data-ttu-id="c9048-144">Veri türlerini dönüştürme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9048-144">Converting Data Types (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md)

- [<span data-ttu-id="c9048-145">Birleştirme Işlemleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9048-145">Concatenation Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/concatenation-operations.md)

- [<span data-ttu-id="c9048-146">Toplama Işlemleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9048-146">Aggregation Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md)

## <a name="see-also"></a><span data-ttu-id="c9048-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c9048-147">See also</span></span>

- <xref:System.Linq.Enumerable>
- <xref:System.Linq.Queryable>
- [<span data-ttu-id="c9048-148">LINQ 'e giriş (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9048-148">Introduction to LINQ (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)
- [<span data-ttu-id="c9048-149">Standart sorgu Işleçleri için sorgu Ifadesi sözdizimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9048-149">Query Expression Syntax for Standard Query Operators (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)
- [<span data-ttu-id="c9048-150">Standart sorgu Işleçleri yürütme yöntemine göre sınıflandırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9048-150">Classification of Standard Query Operators by Manner of Execution (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)
- [<span data-ttu-id="c9048-151">Genişletme Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="c9048-151">Extension Methods</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
