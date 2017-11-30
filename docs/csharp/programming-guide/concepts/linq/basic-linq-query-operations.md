---
title: "Temel LINQ Sorgu İşlemleri (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- orderby clause [LINQ in C#]
- ordering data [LINQ in C#]
- selecting data [LINQ in C#]
- queries [LINQ in C#], basic operations
- grouping data [LINQ in C#]
- data sources [LINQ in C#]
- sorting data [LINQ in C#]
- projections [LINQ in C#]
- filtering data [LINQ in C#]
- joining data [LINQ in C#]
- select clause [LINQ in C#]
- LINQ [C#], basic query operations
- join clause [LINQ in C#]
- group clause [LINQ in C#]
ms.assetid: a7ea3421-1cf4-4df7-832a-aa22fe6379e9
caps.latest.revision: "39"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c7a258ae8d85425abb6d1474d2cb01b02f6deb2e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="basic-linq-query-operations-c"></a><span data-ttu-id="66dd7-102">Temel LINQ Sorgu İşlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="66dd7-102">Basic LINQ Query Operations (C#)</span></span>
<span data-ttu-id="66dd7-103">Bu konuda kısa bir giriş sağlar [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu ifadeleri ve bazı tipik türleri sorguda gerçekleştirdiğiniz işlem.</span><span class="sxs-lookup"><span data-stu-id="66dd7-103">This topic gives a brief introduction to [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions and some of the typical kinds of operations that you perform in a query.</span></span> <span data-ttu-id="66dd7-104">Daha ayrıntılı bilgi aşağıdaki konularda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="66dd7-104">More detailed information is in the following topics:</span></span>  
  
 [<span data-ttu-id="66dd7-105">LINQ Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="66dd7-105">LINQ Query Expressions</span></span>](../../../../csharp/programming-guide/linq-query-expressions/index.md)  
  
 [<span data-ttu-id="66dd7-106">Standart sorgu işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="66dd7-106">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
  
 [<span data-ttu-id="66dd7-107">İzlenecek yol: Sorguları C# ile yazma</span><span class="sxs-lookup"><span data-stu-id="66dd7-107">Walkthrough: Writing Queries in C#</span></span>](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)  
  
> [!NOTE]
>  <span data-ttu-id="66dd7-108">SQL veya XQuery gibi bir sorgu dili ile bilginiz varsa, bu konunun en atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66dd7-108">If you already are familiar with a query language such as SQL or XQuery, you can skip most of this topic.</span></span> <span data-ttu-id="66dd7-109">Hakkında bilgi edinin "`from` yan tümcesi" yan tümcelerinde sırasını hakkında bilgi almak için sonraki bölümde [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu ifadeleri.</span><span class="sxs-lookup"><span data-stu-id="66dd7-109">Read about the "`from` clause" in the next section to learn about the order of clauses in [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span>  
  
## <a name="obtaining-a-data-source"></a><span data-ttu-id="66dd7-110">Bir Veri Kaynağı Elde Etme</span><span class="sxs-lookup"><span data-stu-id="66dd7-110">Obtaining a Data Source</span></span>  
 <span data-ttu-id="66dd7-111">İçinde bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu, ilk adımdır veri kaynağını belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="66dd7-111">In a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query, the first step is to specify the data source.</span></span> <span data-ttu-id="66dd7-112">Kullanılabilmesi için C# çoğu programlama dilinde olduğu gibi bir değişkeni bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="66dd7-112">In C# as in most programming languages a variable must be declared before it can be used.</span></span> <span data-ttu-id="66dd7-113">İçinde bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu `from` yan tümcesi gelen ilk veri kaynağı sunmak için (`customers`) ve *aralık değişkeni* (`cust`).</span><span class="sxs-lookup"><span data-stu-id="66dd7-113">In a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query, the `from` clause comes first in order to introduce the data source (`customers`) and the *range variable* (`cust`).</span></span>  
  
 [!code-csharp[csLINQGettingStarted#23](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_1.cs)]  
  
 <span data-ttu-id="66dd7-114">Yineleme değişkeni aralık değişkeni benzer bir `foreach` sorgu ifadesinde gerçek bir yineleme gerçekleşir ancak bu döngü.</span><span class="sxs-lookup"><span data-stu-id="66dd7-114">The range variable is like the iteration variable in a `foreach` loop except that no actual iteration occurs in a query expression.</span></span> <span data-ttu-id="66dd7-115">Sorgu çalıştırıldığında, aralık değişkeni art arda gelen her öğe için bir başvuru olarak hizmet verecektir `customers`.</span><span class="sxs-lookup"><span data-stu-id="66dd7-115">When the query is executed, the range variable will serve as a reference to each successive element in `customers`.</span></span> <span data-ttu-id="66dd7-116">Derleyici türünü çıkarımını çünkü `cust`, açıkça belirtmek zorunda değilsiniz.</span><span class="sxs-lookup"><span data-stu-id="66dd7-116">Because the compiler can infer the type of `cust`, you do not have to specify it explicitly.</span></span> <span data-ttu-id="66dd7-117">Ek aralık değişkeni sunulan tarafından bir `let` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="66dd7-117">Additional range variables can be introduced by a `let` clause.</span></span> <span data-ttu-id="66dd7-118">Daha fazla bilgi için bkz: [let tümcesi](../../../../csharp/language-reference/keywords/let-clause.md).</span><span class="sxs-lookup"><span data-stu-id="66dd7-118">For more information, see [let clause](../../../../csharp/language-reference/keywords/let-clause.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="66dd7-119">İçin genel olmayan veri kaynakları gibi <xref:System.Collections.ArrayList>, aralık değişkeni açıkça yazılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="66dd7-119">For non-generic data sources such as <xref:System.Collections.ArrayList>, the range variable must be explicitly typed.</span></span> <span data-ttu-id="66dd7-120">Daha fazla bilgi için bkz: [nasıl yapılır: LINQ (C#) ile ArrayList sorgulama](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md) ve [from yan tümcesi](../../../../csharp/language-reference/keywords/from-clause.md).</span><span class="sxs-lookup"><span data-stu-id="66dd7-120">For more information, see [How to: Query an ArrayList with LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md) and [from clause](../../../../csharp/language-reference/keywords/from-clause.md).</span></span>  
  
## <a name="filtering"></a><span data-ttu-id="66dd7-121">Filtreleme</span><span class="sxs-lookup"><span data-stu-id="66dd7-121">Filtering</span></span>  
 <span data-ttu-id="66dd7-122">Boole ifadesi şeklinde bir filtre uygulamak için en yaygın sorgu işlemi olabilir.</span><span class="sxs-lookup"><span data-stu-id="66dd7-122">Probably the most common query operation is to apply a filter in the form of a Boolean expression.</span></span> <span data-ttu-id="66dd7-123">Filtre yalnızca ifade doğru ise öğeleri döndürecek şekilde sorguyu neden olur.</span><span class="sxs-lookup"><span data-stu-id="66dd7-123">The filter causes the query to return only those elements for which the expression is true.</span></span> <span data-ttu-id="66dd7-124">Sonuç kullanılarak üretilen `where` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="66dd7-124">The result is produced by using the `where` clause.</span></span> <span data-ttu-id="66dd7-125">Filtre etkin kaynak dizisinden dışlamak için hangi öğelerin belirtir.</span><span class="sxs-lookup"><span data-stu-id="66dd7-125">The filter in effect specifies which elements to exclude from the source sequence.</span></span> <span data-ttu-id="66dd7-126">Aşağıdaki örnekte, yalnızca `customers` bir adresi Londra'da sahip döndürülür.</span><span class="sxs-lookup"><span data-stu-id="66dd7-126">In the following example, only those `customers` who have an address in London are returned.</span></span>  
  
 [!code-csharp[csLINQGettingStarted#24](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_2.cs)]  
  
 <span data-ttu-id="66dd7-127">Kullanabileceğiniz tanıdık C# mantıksal `AND` ve `OR` birçok ifadeleri gerekli olarak filtre olarak uygulamak için işleçleri `where` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="66dd7-127">You can use the familiar C# logical `AND` and `OR` operators to apply as many filter expressions as necessary in the `where` clause.</span></span> <span data-ttu-id="66dd7-128">Örneğin, "Londra'dan" yalnızca Müşteriler döndürülecek `AND` adı olan "yazma aşağıdaki kodu Devon":</span><span class="sxs-lookup"><span data-stu-id="66dd7-128">For example, to return only customers from "London" `AND` whose name is "Devon" you would write the following code:</span></span>  
  
 [!code-csharp[csLINQGettingStarted#25](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_3.cs)]  
  
 <span data-ttu-id="66dd7-129">Londra veya Paris müşteriler döndürmek için aşağıdaki kodu yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="66dd7-129">To return customers from London or Paris, you would write the following code:</span></span>  
  
 [!code-csharp[csLINQGettingStarted#26](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_4.cs)]  
  
 <span data-ttu-id="66dd7-130">Daha fazla bilgi için bkz: [burada yan tümcesi](../../../../csharp/language-reference/keywords/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="66dd7-130">For more information, see [where clause](../../../../csharp/language-reference/keywords/where-clause.md).</span></span>  
  
## <a name="ordering"></a><span data-ttu-id="66dd7-131">Sıralama</span><span class="sxs-lookup"><span data-stu-id="66dd7-131">Ordering</span></span>  
 <span data-ttu-id="66dd7-132">Genellikle döndürülen verileri sıralamak uygundur.</span><span class="sxs-lookup"><span data-stu-id="66dd7-132">Often it is convenient to sort the returned data.</span></span> <span data-ttu-id="66dd7-133">`orderby` Yan tümcesi neden olacak öğeleri göre sıralanan türü için varsayılan karşılaştırıcı sıralanacak döndürülen dizideki.</span><span class="sxs-lookup"><span data-stu-id="66dd7-133">The `orderby` clause will cause the elements in the returned sequence to be sorted according to the default comparer for the type being sorted.</span></span> <span data-ttu-id="66dd7-134">Örneğin, aşağıdaki sorguyu temel sonuçları sıralamak için Genişletilebilir `Name` özelliği.</span><span class="sxs-lookup"><span data-stu-id="66dd7-134">For example, the following query can be extended to sort the results based on the `Name` property.</span></span> <span data-ttu-id="66dd7-135">Çünkü `Name` bir dizedir varsayılan karşılaştırıcı alfabetik sıralama A'dan Z'ye gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="66dd7-135">Because `Name` is a string, the default comparer performs an alphabetical sort from A to Z.</span></span>  
  
 [!code-csharp[csLINQGettingStarted#27](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_5.cs)]  
  
 <span data-ttu-id="66dd7-136">Sonuçları Z'den A'ya, ters sırada sıralamak için kullanmak `orderby…descending` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="66dd7-136">To order the results in reverse order, from Z to A, use the `orderby…descending` clause.</span></span>  
  
 <span data-ttu-id="66dd7-137">Daha fazla bilgi için bkz: [orderby yan tümcesinin](../../../../csharp/language-reference/keywords/orderby-clause.md).</span><span class="sxs-lookup"><span data-stu-id="66dd7-137">For more information, see [orderby clause](../../../../csharp/language-reference/keywords/orderby-clause.md).</span></span>  
  
## <a name="grouping"></a><span data-ttu-id="66dd7-138">Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="66dd7-138">Grouping</span></span>  
 <span data-ttu-id="66dd7-139">`group` Yan tümcesi, belirttiğiniz bir anahtarı temel sonuçlarınızı gruplamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="66dd7-139">The `group` clause enables you to group your results based on a key that you specify.</span></span> <span data-ttu-id="66dd7-140">Örneğin sonuçları tarafından gruplandırılmalıdır belirtebilirsiniz `City` tek tek gruplarında Londra veya Paris tüm müşterilerden; böylece.</span><span class="sxs-lookup"><span data-stu-id="66dd7-140">For example you could specify that the results should be grouped by the `City` so that all customers from London or Paris are in individual groups.</span></span> <span data-ttu-id="66dd7-141">Bu durumda, `cust.City` anahtardır.</span><span class="sxs-lookup"><span data-stu-id="66dd7-141">In this case, `cust.City` is the key.</span></span>  
  
 [!code-csharp[csLINQGettingStarted#28](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_6.cs)]  
  
 <span data-ttu-id="66dd7-142">Son zaman bir sorgu ile bir `group` yan tümcesi, sonuçlarınızı formun listeleri listesini alın.</span><span class="sxs-lookup"><span data-stu-id="66dd7-142">When you end a query with a `group` clause, your results take the form of a list of lists.</span></span> <span data-ttu-id="66dd7-143">Her bir öğe listesi olan bir nesnedir bir `Key` üye ve bu anahtarın altında gruplanmış öğeleri listesi.</span><span class="sxs-lookup"><span data-stu-id="66dd7-143">Each element in the list is an object that has a `Key` member and a list of elements that are grouped under that key.</span></span> <span data-ttu-id="66dd7-144">Grup bir dizi üreten bir sorgu yineleme yaparken, iç içe bir kullanmalısınız `foreach` döngü.</span><span class="sxs-lookup"><span data-stu-id="66dd7-144">When you iterate over a query that produces a sequence of groups, you must use a nested `foreach` loop.</span></span> <span data-ttu-id="66dd7-145">Her grup üzerinden dış döngüsü yineler ve iç döngüsü her grubun üyeleri üzerinde yineler.</span><span class="sxs-lookup"><span data-stu-id="66dd7-145">The outer loop iterates over each group, and the inner loop iterates over each group's members.</span></span>  
  
 <span data-ttu-id="66dd7-146">Bir grup İşlem sonuçlarını başvurmalıdır, kullanabileceğiniz `into` daha fazla sorgulanabilir bir tanımlayıcı oluşturmak üzere anahtar sözcük.</span><span class="sxs-lookup"><span data-stu-id="66dd7-146">If you must refer to the results of a group operation, you can use the `into` keyword to create an identifier that can be queried further.</span></span> <span data-ttu-id="66dd7-147">Aşağıdaki sorguda ikiden fazla müşteriler içeren gruplar döndürür:</span><span class="sxs-lookup"><span data-stu-id="66dd7-147">The following query returns only those groups that contain more than two customers:</span></span>  
  
 [!code-csharp[csLINQGettingStarted#29](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_7.cs)]  
  
 <span data-ttu-id="66dd7-148">Daha fazla bilgi için bkz: [group yan tümcesi](../../../../csharp/language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="66dd7-148">For more information, see [group clause](../../../../csharp/language-reference/keywords/group-clause.md).</span></span>  
  
## <a name="joining"></a><span data-ttu-id="66dd7-149">Katılma</span><span class="sxs-lookup"><span data-stu-id="66dd7-149">Joining</span></span>  
 <span data-ttu-id="66dd7-150">Birleştirme işlemleri oluşturmak dizileri arasındaki ilişkileri, veri kaynaklarında açıkça Modellenen değil.</span><span class="sxs-lookup"><span data-stu-id="66dd7-150">Join operations create associations between sequences that are not explicitly modeled in the data sources.</span></span> <span data-ttu-id="66dd7-151">Örneğin müşteriler ve aynı konuma sahip dağıtıcıları bulmak için bir birleştirme gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66dd7-151">For example you can perform a join to find all the customers and distributors who have the same location.</span></span> <span data-ttu-id="66dd7-152">İçinde [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] `join` yan tümcesi her zaman çalışır veritabanı tablolarını yerine nesne koleksiyonları karşı doğrudan.</span><span class="sxs-lookup"><span data-stu-id="66dd7-152">In [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] the `join` clause always works against object collections instead of database tables directly.</span></span>  
  
 [!code-csharp[csLINQGettingStarted#36](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_8.cs)]  
  
 <span data-ttu-id="66dd7-153">İçinde [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] kullanmak zorunda değil `join` SQL'de çünkü bunu sıklıkta yabancı anahtarları [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] nesne modelinde öğeleri koleksiyonu tutun özellikleri olarak temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="66dd7-153">In [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] you do not have to use `join` as often as you do in SQL because foreign keys in [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] are represented in the object model as properties that hold a collection of items.</span></span> <span data-ttu-id="66dd7-154">Örneğin, bir `Customer` nesnesini içeren koleksiyonu `Order` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="66dd7-154">For example, a `Customer` object contains a collection of `Order` objects.</span></span> <span data-ttu-id="66dd7-155">Bir birleştirme gerçekleştirmek yerine, noktalı gösterim kullanılarak siparişleri erişebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="66dd7-155">Rather than performing a join, you access the orders by using dot notation:</span></span>  
  
```  
from order in Customer.Orders...  
```  
  
 <span data-ttu-id="66dd7-156">Daha fazla bilgi için bkz: [JOIN yan tümcesi](../../../../csharp/language-reference/keywords/join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="66dd7-156">For more information, see [join clause](../../../../csharp/language-reference/keywords/join-clause.md).</span></span>  
  
## <a name="selecting-projections"></a><span data-ttu-id="66dd7-157">Seçme (Tahminler)</span><span class="sxs-lookup"><span data-stu-id="66dd7-157">Selecting (Projections)</span></span>  
 <span data-ttu-id="66dd7-158">`select` Yan tümcesi sorgu sonuçlarını üretir ve "Şekil" ya da her döndürülen öğe türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="66dd7-158">The `select` clause produces the results of the query and specifies the "shape" or type of each returned element.</span></span> <span data-ttu-id="66dd7-159">Örneğin, sonuçlarınızı, tam oluşacağını belirtebilirsiniz `Customer` nesneleri, yalnızca bir üye, üyelerin bir alt kümesini veya bazı tamamen farklı bir sonuç türü göre bir hesaplama veya yeni nesne oluşturma.</span><span class="sxs-lookup"><span data-stu-id="66dd7-159">For example, you can specify whether your results will consist of complete `Customer` objects, just one member, a subset of members, or some completely different result type based on a computation or new object creation.</span></span> <span data-ttu-id="66dd7-160">Zaman `select` yan tümcesi üreten bir kopyasını kaynak öğenin dışında işlemi adlı bir *projeksiyon*.</span><span class="sxs-lookup"><span data-stu-id="66dd7-160">When the `select` clause produces something other than a copy of the source element, the operation is called a *projection*.</span></span> <span data-ttu-id="66dd7-161">Verileri dönüştürmek için tahminleri güçlü kullanımıdır [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu ifadeleri.</span><span class="sxs-lookup"><span data-stu-id="66dd7-161">The use of projections to transform data is a powerful capability of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span> <span data-ttu-id="66dd7-162">Daha fazla bilgi için bkz: [LINQ (C#) ile veri dönüştürmeler](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md) ve [select yan tümcesi](../../../../csharp/language-reference/keywords/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="66dd7-162">For more information, see [Data Transformations with LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md) and [select clause](../../../../csharp/language-reference/keywords/select-clause.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66dd7-163">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="66dd7-163">See Also</span></span>  
 [<span data-ttu-id="66dd7-164">C# üzerinde LINQ ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="66dd7-164">Getting Started with LINQ in C#</span></span>](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [<span data-ttu-id="66dd7-165">LINQ Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="66dd7-165">LINQ Query Expressions</span></span>](../../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [<span data-ttu-id="66dd7-166">İzlenecek yol: Sorguları C# ile yazma</span><span class="sxs-lookup"><span data-stu-id="66dd7-166">Walkthrough: Writing Queries in C#</span></span>](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)  
 [<span data-ttu-id="66dd7-167">Sorgu anahtar sözcükleri (LINQ)</span><span class="sxs-lookup"><span data-stu-id="66dd7-167">Query Keywords (LINQ)</span></span>](../../../../csharp/language-reference/keywords/query-keywords.md)  
 [<span data-ttu-id="66dd7-168">Anonim türler</span><span class="sxs-lookup"><span data-stu-id="66dd7-168">Anonymous Types</span></span>](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
