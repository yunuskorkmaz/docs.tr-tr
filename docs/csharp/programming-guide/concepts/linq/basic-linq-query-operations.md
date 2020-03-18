---
title: Temel LINQ Sorgu İşlemleri (C#)
ms.date: 07/20/2015
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
ms.openlocfilehash: 91c038303c1ad7c2530964d3102aae49090c4c2a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635945"
---
# <a name="basic-linq-query-operations-c"></a><span data-ttu-id="f8e42-102">Temel LINQ Sorgu İşlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="f8e42-102">Basic LINQ Query Operations (C#)</span></span>
<span data-ttu-id="f8e42-103">Bu konu, LINQ sorgu ifadelerine ve bir sorguda gerçekleştirdiğiniz tipik işlem türlerinden bazılarına kısa bir giriş sağlar.</span><span class="sxs-lookup"><span data-stu-id="f8e42-103">This topic gives a brief introduction to LINQ query expressions and some of the typical kinds of operations that you perform in a query.</span></span> <span data-ttu-id="f8e42-104">Daha ayrıntılı bilgi aşağıdaki konularda:</span><span class="sxs-lookup"><span data-stu-id="f8e42-104">More detailed information is in the following topics:</span></span>  
  
 [<span data-ttu-id="f8e42-105">LINQ Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="f8e42-105">LINQ Query Expressions</span></span>](../../../linq/index.md)  
  
 [<span data-ttu-id="f8e42-106">Standart Sorgu Operatörlerine Genel Bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="f8e42-106">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)  
  
 [<span data-ttu-id="f8e42-107">Walkthrough: C'de Sorgu Yazma #</span><span class="sxs-lookup"><span data-stu-id="f8e42-107">Walkthrough: Writing Queries in C#</span></span>](./walkthrough-writing-queries-linq.md)  
  
> [!NOTE]
> <span data-ttu-id="f8e42-108">SQL veya XQuery gibi bir sorgu dilini zaten biliyorsanız, bu konunun çoğunu atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8e42-108">If you already are familiar with a query language such as SQL or XQuery, you can skip most of this topic.</span></span> <span data-ttu-id="f8e42-109">LINQ sorgu`from` ifadelerindeki yan tümcelerin sırası hakkında bilgi edinmek için bir sonraki bölümdeki "yan tümce" hakkında bilgi edinin.</span><span class="sxs-lookup"><span data-stu-id="f8e42-109">Read about the "`from` clause" in the next section to learn about the order of clauses in LINQ query expressions.</span></span>  
  
## <a name="obtaining-a-data-source"></a><span data-ttu-id="f8e42-110">Bir Veri Kaynağı Elde Etme</span><span class="sxs-lookup"><span data-stu-id="f8e42-110">Obtaining a Data Source</span></span>  
 <span data-ttu-id="f8e42-111">LINQ sorgusunda ilk adım veri kaynağını belirtmektir.</span><span class="sxs-lookup"><span data-stu-id="f8e42-111">In a LINQ query, the first step is to specify the data source.</span></span> <span data-ttu-id="f8e42-112">Çoğu programlama dilinde olduğu gibi C#'da da kullanılmadan önce bir değişken in bildirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="f8e42-112">In C# as in most programming languages a variable must be declared before it can be used.</span></span> <span data-ttu-id="f8e42-113">BIR LINQ `from` sorgusunda, yan tümce önce veri`customers`kaynağını ( )`cust`ve aralık *değişkenini* ( ) tanıtmak için gelir.</span><span class="sxs-lookup"><span data-stu-id="f8e42-113">In a LINQ query, the `from` clause comes first in order to introduce the data source (`customers`) and the *range variable* (`cust`).</span></span>  
  
 [!code-csharp[csLINQGettingStarted#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#23)]  
  
 <span data-ttu-id="f8e42-114">Aralık değişkeni, sorgu ifadesinde gerçek `foreach` yineleme olmaması dışında bir döngüdeki yineleme değişkeni gibidir.</span><span class="sxs-lookup"><span data-stu-id="f8e42-114">The range variable is like the iteration variable in a `foreach` loop except that no actual iteration occurs in a query expression.</span></span> <span data-ttu-id="f8e42-115">Sorgu yürütüldüğünde, aralık değişkeni `customers`' deki her ardışık öğeye başvuru görevi göreceksiniz.</span><span class="sxs-lookup"><span data-stu-id="f8e42-115">When the query is executed, the range variable will serve as a reference to each successive element in `customers`.</span></span> <span data-ttu-id="f8e42-116">Derleyici türünü `cust`çıkarabileceğinden, bunu açıkça belirtmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="f8e42-116">Because the compiler can infer the type of `cust`, you do not have to specify it explicitly.</span></span> <span data-ttu-id="f8e42-117">Ek aralık değişkenleri bir `let` yan tümce ile tanıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="f8e42-117">Additional range variables can be introduced by a `let` clause.</span></span> <span data-ttu-id="f8e42-118">Daha fazla bilgi için [bkz.](../../../language-reference/keywords/let-clause.md)</span><span class="sxs-lookup"><span data-stu-id="f8e42-118">For more information, see [let clause](../../../language-reference/keywords/let-clause.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f8e42-119">Gibi genel olmayan veri <xref:System.Collections.ArrayList>kaynakları için, aralık değişkeni açıkça yazılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f8e42-119">For non-generic data sources such as <xref:System.Collections.ArrayList>, the range variable must be explicitly typed.</span></span> <span data-ttu-id="f8e42-120">Daha fazla bilgi için LINQ (C#) ile ve [yan tümcesinden](../../../language-reference/keywords/from-clause.md) [bir ArrayList'i nasıl sorgularız](./how-to-query-an-arraylist-with-linq.md) bilgi sini görün.</span><span class="sxs-lookup"><span data-stu-id="f8e42-120">For more information, see [How to query an ArrayList with LINQ (C#)](./how-to-query-an-arraylist-with-linq.md) and [from clause](../../../language-reference/keywords/from-clause.md).</span></span>  
  
## <a name="filtering"></a><span data-ttu-id="f8e42-121">Filtreleme</span><span class="sxs-lookup"><span data-stu-id="f8e42-121">Filtering</span></span>  
 <span data-ttu-id="f8e42-122">Muhtemelen en yaygın sorgu işlemi Boolean ifadesi şeklinde bir filtre uygulamaktır.</span><span class="sxs-lookup"><span data-stu-id="f8e42-122">Probably the most common query operation is to apply a filter in the form of a Boolean expression.</span></span> <span data-ttu-id="f8e42-123">Filtre, sorgunun yalnızca ifadenin doğru olduğu öğeleri döndürmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="f8e42-123">The filter causes the query to return only those elements for which the expression is true.</span></span> <span data-ttu-id="f8e42-124">`where` Sonuç, yan tümce kullanılarak elde edilir.</span><span class="sxs-lookup"><span data-stu-id="f8e42-124">The result is produced by using the `where` clause.</span></span> <span data-ttu-id="f8e42-125">Etkin filtre, kaynak dizisinden hangi öğelerin dışlanacağı belirtilir.</span><span class="sxs-lookup"><span data-stu-id="f8e42-125">The filter in effect specifies which elements to exclude from the source sequence.</span></span> <span data-ttu-id="f8e42-126">Aşağıdaki örnekte, yalnızca `customers` Londra'da adresi olanlar iade edilir.</span><span class="sxs-lookup"><span data-stu-id="f8e42-126">In the following example, only those `customers` who have an address in London are returned.</span></span>  
  
 [!code-csharp[csLINQGettingStarted#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#24)]  
  
 <span data-ttu-id="f8e42-127">Yan tümcede gerektiği `AND` kadar `OR` filtre ifadesi uygulamak için tanıdık C# mantıksal ve işleçleri kullanabilirsiniz. `where`</span><span class="sxs-lookup"><span data-stu-id="f8e42-127">You can use the familiar C# logical `AND` and `OR` operators to apply as many filter expressions as necessary in the `where` clause.</span></span> <span data-ttu-id="f8e42-128">Örneğin, yalnızca "Londra"dan adı `AND` "Devon" olan müşterileri iade etmek için aşağıdaki kodu yazarsınız:</span><span class="sxs-lookup"><span data-stu-id="f8e42-128">For example, to return only customers from "London" `AND` whose name is "Devon" you would write the following code:</span></span>  
  
 [!code-csharp[csLINQGettingStarted#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#25)]  
  
 <span data-ttu-id="f8e42-129">Londra veya Paris'ten gelen müşterileri iade etmek için aşağıdaki kodu yazarsınız:</span><span class="sxs-lookup"><span data-stu-id="f8e42-129">To return customers from London or Paris, you would write the following code:</span></span>  
  
 [!code-csharp[csLINQGettingStarted#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#26)]  
  
 <span data-ttu-id="f8e42-130">Daha fazla bilgi için [bkz.](../../../language-reference/keywords/where-clause.md)</span><span class="sxs-lookup"><span data-stu-id="f8e42-130">For more information, see [where clause](../../../language-reference/keywords/where-clause.md).</span></span>  
  
## <a name="ordering"></a><span data-ttu-id="f8e42-131">Sıralama</span><span class="sxs-lookup"><span data-stu-id="f8e42-131">Ordering</span></span>  
 <span data-ttu-id="f8e42-132">Genellikle döndürülen verileri sıralamak için uygundur.</span><span class="sxs-lookup"><span data-stu-id="f8e42-132">Often it is convenient to sort the returned data.</span></span> <span data-ttu-id="f8e42-133">Yan `orderby` tümce, döndürülen sırada yer alan öğelerin sıralanan tür için varsayılan karşılayıcıya göre sıralansın.</span><span class="sxs-lookup"><span data-stu-id="f8e42-133">The `orderby` clause will cause the elements in the returned sequence to be sorted according to the default comparer for the type being sorted.</span></span> <span data-ttu-id="f8e42-134">Örneğin, aşağıdaki sorgu `Name` özelliğine göre sonuçları sıralamak için genişletilebilir.</span><span class="sxs-lookup"><span data-stu-id="f8e42-134">For example, the following query can be extended to sort the results based on the `Name` property.</span></span> <span data-ttu-id="f8e42-135">Bir `Name` dize olduğundan, varsayılan karşılayıcı A'dan Z'ye alfabetik bir sıralama gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="f8e42-135">Because `Name` is a string, the default comparer performs an alphabetical sort from A to Z.</span></span>  
  
 [!code-csharp[csLINQGettingStarted#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#27)]  
  
 <span data-ttu-id="f8e42-136">Sonuçları z'den A'ya ters sırayla `orderby…descending` sıralamak için yan tümceyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="f8e42-136">To order the results in reverse order, from Z to A, use the `orderby…descending` clause.</span></span>  
  
 <span data-ttu-id="f8e42-137">Daha fazla bilgi için [orderby yan tümcesi'ne](../../../language-reference/keywords/orderby-clause.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="f8e42-137">For more information, see [orderby clause](../../../language-reference/keywords/orderby-clause.md).</span></span>  
  
## <a name="grouping"></a><span data-ttu-id="f8e42-138">Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="f8e42-138">Grouping</span></span>  
 <span data-ttu-id="f8e42-139">Yan `group` tümce, sonuçlarınızı belirttiğiniz bir anahtara göre gruplandırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="f8e42-139">The `group` clause enables you to group your results based on a key that you specify.</span></span> <span data-ttu-id="f8e42-140">Örneğin, Londra veya Paris'ten gelen tüm `City` müşterilerin ayrı gruplar halinde olması için sonuçların bunlara göre gruplandırılması gerektiğini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8e42-140">For example you could specify that the results should be grouped by the `City` so that all customers from London or Paris are in individual groups.</span></span> <span data-ttu-id="f8e42-141">Bu durumda, `cust.City` anahtardır.</span><span class="sxs-lookup"><span data-stu-id="f8e42-141">In this case, `cust.City` is the key.</span></span>  
  
 [!code-csharp[csLINQGettingStarted#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#28)]  
  
 <span data-ttu-id="f8e42-142">Bir sorguyu bir `group` yan tümceyle sonladiğinizde, sonuçlarınız liste listesi biçiminde dir.</span><span class="sxs-lookup"><span data-stu-id="f8e42-142">When you end a query with a `group` clause, your results take the form of a list of lists.</span></span> <span data-ttu-id="f8e42-143">Listedeki her öğe, bir `Key` üyesi ve bu anahtar altında gruplanmış öğelerin listesi olan bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="f8e42-143">Each element in the list is an object that has a `Key` member and a list of elements that are grouped under that key.</span></span> <span data-ttu-id="f8e42-144">Bir grup dizisi oluşturan bir sorgu üzerinde yinelediğinizde, iç `foreach` içe bir döngü kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f8e42-144">When you iterate over a query that produces a sequence of groups, you must use a nested `foreach` loop.</span></span> <span data-ttu-id="f8e42-145">Dış döngü her grubun üzerinde yineler ve iç döngü her grubun üyeleri üzerinde yineler.</span><span class="sxs-lookup"><span data-stu-id="f8e42-145">The outer loop iterates over each group, and the inner loop iterates over each group's members.</span></span>  
  
 <span data-ttu-id="f8e42-146">Bir grup işleminin sonuçlarına başvurmanız gerekiyorsa, `into` daha fazla sorgulanabilecek bir tanımlayıcı oluşturmak için anahtar sözcüğü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8e42-146">If you must refer to the results of a group operation, you can use the `into` keyword to create an identifier that can be queried further.</span></span> <span data-ttu-id="f8e42-147">Aşağıdaki sorgu yalnızca ikiden fazla müşteri içeren grupları döndürür:</span><span class="sxs-lookup"><span data-stu-id="f8e42-147">The following query returns only those groups that contain more than two customers:</span></span>  
  
 [!code-csharp[csLINQGettingStarted#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#29)]  
  
 <span data-ttu-id="f8e42-148">Daha fazla bilgi için [grup yan tümcesi'ne](../../../language-reference/keywords/group-clause.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="f8e42-148">For more information, see [group clause](../../../language-reference/keywords/group-clause.md).</span></span>  
  
## <a name="joining"></a><span data-ttu-id="f8e42-149">Katma</span><span class="sxs-lookup"><span data-stu-id="f8e42-149">Joining</span></span>  
 <span data-ttu-id="f8e42-150">Birleştirme işlemleri, veri kaynaklarında açıkça modellenmemiş diziler arasında ilişki oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f8e42-150">Join operations create associations between sequences that are not explicitly modeled in the data sources.</span></span> <span data-ttu-id="f8e42-151">Örneğin, aynı konuma sahip tüm müşterileri ve distribütörleri bulmak için bir birleştirme gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8e42-151">For example you can perform a join to find all the customers and distributors who have the same location.</span></span> <span data-ttu-id="f8e42-152">LINQ'da `join` yan tümce her zaman veritabanı tabloları yerine nesne koleksiyonlarına karşı çalışır.</span><span class="sxs-lookup"><span data-stu-id="f8e42-152">In LINQ the `join` clause always works against object collections instead of database tables directly.</span></span>  
  
 [!code-csharp[csLINQGettingStarted#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#36)]  
  
 <span data-ttu-id="f8e42-153">LINQ'da, SQL'de `join` kullandığınız sıklıkta kullanmanız gerekmez, çünkü LINQ'daki yabancı anahtarlar nesne modelinde bir öğe koleksiyonu tutan özellikler olarak temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="f8e42-153">In LINQ, you do not have to use `join` as often as you do in SQL, because foreign keys in LINQ are represented in the object model as properties that hold a collection of items.</span></span> <span data-ttu-id="f8e42-154">Örneğin, bir `Customer` nesne nesnelerin `Order` bir koleksiyon içerir.</span><span class="sxs-lookup"><span data-stu-id="f8e42-154">For example, a `Customer` object contains a collection of `Order` objects.</span></span> <span data-ttu-id="f8e42-155">Birleştirme gerçekleştirmek yerine, nokta gösterimi kullanarak siparişlere erişebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f8e42-155">Rather than performing a join, you access the orders by using dot notation:</span></span>  
  
```csharp
from order in Customer.Orders...  
```  
  
 <span data-ttu-id="f8e42-156">Daha fazla bilgi için [ara yan tümcesi'ne](../../../language-reference/keywords/join-clause.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="f8e42-156">For more information, see [join clause](../../../language-reference/keywords/join-clause.md).</span></span>  
  
## <a name="selecting-projections"></a><span data-ttu-id="f8e42-157">Seçme (Tahminler)</span><span class="sxs-lookup"><span data-stu-id="f8e42-157">Selecting (Projections)</span></span>  
 <span data-ttu-id="f8e42-158">Yan `select` tümce sorgunun sonuçlarını üretir ve döndürülen her öğenin "şeklini" veya türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="f8e42-158">The `select` clause produces the results of the query and specifies the "shape" or type of each returned element.</span></span> <span data-ttu-id="f8e42-159">Örneğin, sonuçlarınızın tam `Customer` nesnelerden mi, yalnızca bir üyeden, bir üye alt kümesinden mi yoksa bir hesaplamaya veya yeni nesne oluşturmaya dayalı tamamen farklı bir sonuç türünden mi oluşacağını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8e42-159">For example, you can specify whether your results will consist of complete `Customer` objects, just one member, a subset of members, or some completely different result type based on a computation or new object creation.</span></span> <span data-ttu-id="f8e42-160">`select` Yan tümce kaynak öğenin bir kopyası ndan başka bir şey ürettiğinde, işlem *projeksiyon*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="f8e42-160">When the `select` clause produces something other than a copy of the source element, the operation is called a *projection*.</span></span> <span data-ttu-id="f8e42-161">Verileri dönüştürmek için projeksiyonların kullanılması LINQ sorgu ifadelerinin güçlü bir yeteneğidir.</span><span class="sxs-lookup"><span data-stu-id="f8e42-161">The use of projections to transform data is a powerful capability of LINQ query expressions.</span></span> <span data-ttu-id="f8e42-162">Daha fazla bilgi için [LINQ (C#) ile Veri Dönüşümleri](./data-transformations-with-linq.md) ve [select yan tümcesi](../../../language-reference/keywords/select-clause.md)'ne bakın.</span><span class="sxs-lookup"><span data-stu-id="f8e42-162">For more information, see [Data Transformations with LINQ (C#)](./data-transformations-with-linq.md) and [select clause](../../../language-reference/keywords/select-clause.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8e42-163">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f8e42-163">See also</span></span>

- [<span data-ttu-id="f8e42-164">LINQ Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="f8e42-164">LINQ Query Expressions</span></span>](../../../linq/index.md)
- [<span data-ttu-id="f8e42-165">Walkthrough: C'de Sorgu Yazma #</span><span class="sxs-lookup"><span data-stu-id="f8e42-165">Walkthrough: Writing Queries in C#</span></span>](./walkthrough-writing-queries-linq.md)
- [<span data-ttu-id="f8e42-166">Sorgu Anahtar Kelimeleri (LINQ)</span><span class="sxs-lookup"><span data-stu-id="f8e42-166">Query Keywords (LINQ)</span></span>](../../../language-reference/keywords/query-keywords.md)
- [<span data-ttu-id="f8e42-167">Anonim Türler</span><span class="sxs-lookup"><span data-stu-id="f8e42-167">Anonymous Types</span></span>](../../classes-and-structs/anonymous-types.md)
