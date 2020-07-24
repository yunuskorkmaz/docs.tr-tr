---
title: Temel LINQ Sorgu İşlemleri (C#)
description: LINQ sorgu ifadelerine ve bir sorguda gerçekleştirebileceğiniz işlemlerden bazılarını tanıtın.
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
ms.openlocfilehash: d9653be8b67ef4d971c157b8dd8d82b2ae3c2287
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105531"
---
# <a name="basic-linq-query-operations-c"></a><span data-ttu-id="00e7e-103">Temel LINQ Sorgu İşlemleri (C#)</span><span class="sxs-lookup"><span data-stu-id="00e7e-103">Basic LINQ Query Operations (C#)</span></span>
<span data-ttu-id="00e7e-104">Bu konu, LINQ sorgu ifadelerine kısa bir giriş ve bir sorguda gerçekleştirdiğiniz bazı tipik işlem türlerinden bazılarını vermektedir.</span><span class="sxs-lookup"><span data-stu-id="00e7e-104">This topic gives a brief introduction to LINQ query expressions and some of the typical kinds of operations that you perform in a query.</span></span> <span data-ttu-id="00e7e-105">Daha ayrıntılı bilgi aşağıdaki konularda yer verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="00e7e-105">More detailed information is in the following topics:</span></span>  
  
 [<span data-ttu-id="00e7e-106">LINQ sorgu Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="00e7e-106">LINQ Query Expressions</span></span>](../../../linq/index.md)  
  
 [<span data-ttu-id="00e7e-107">Standart sorgu Işleçlerine genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="00e7e-107">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)  
  
 [<span data-ttu-id="00e7e-108">İzlenecek yol: C 'de sorgu yazma #</span><span class="sxs-lookup"><span data-stu-id="00e7e-108">Walkthrough: Writing Queries in C#</span></span>](./walkthrough-writing-queries-linq.md)  
  
> [!NOTE]
> <span data-ttu-id="00e7e-109">SQL veya XQuery gibi bir sorgu dili zaten hakkında bilginiz varsa, bu konunun çoğunu atlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="00e7e-109">If you already are familiar with a query language such as SQL or XQuery, you can skip most of this topic.</span></span> <span data-ttu-id="00e7e-110">`from`LINQ sorgu ifadelerinde yan tümceler sırası hakkında bilgi edinmek için sonraki bölümde "yan tümce" konusunu okuyun.</span><span class="sxs-lookup"><span data-stu-id="00e7e-110">Read about the "`from` clause" in the next section to learn about the order of clauses in LINQ query expressions.</span></span>  
  
## <a name="obtaining-a-data-source"></a><span data-ttu-id="00e7e-111">Bir Veri Kaynağı Elde Etme</span><span class="sxs-lookup"><span data-stu-id="00e7e-111">Obtaining a Data Source</span></span>  
 <span data-ttu-id="00e7e-112">Bir LINQ sorgusunda, ilk adım veri kaynağını belirtmektir.</span><span class="sxs-lookup"><span data-stu-id="00e7e-112">In a LINQ query, the first step is to specify the data source.</span></span> <span data-ttu-id="00e7e-113">C# ' ta çoğu programlama dilinde, bir değişken kullanılmadan önce bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="00e7e-113">In C# as in most programming languages a variable must be declared before it can be used.</span></span> <span data-ttu-id="00e7e-114">LINQ sorgusunda, `from` yan tümce ilk olarak veri kaynağını ( `customers` ) ve *Aralık değişkenini* () tanıtmak için gelir `cust` .</span><span class="sxs-lookup"><span data-stu-id="00e7e-114">In a LINQ query, the `from` clause comes first in order to introduce the data source (`customers`) and the *range variable* (`cust`).</span></span>  
  
 [!code-csharp[csLINQGettingStarted#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#23)]  
  
 <span data-ttu-id="00e7e-115">Aralık değişkeni, bir `foreach` sorgu ifadesinde gerçek yineleme gerçekleşmediğinde, döngü içindeki yineleme değişkenine benzer.</span><span class="sxs-lookup"><span data-stu-id="00e7e-115">The range variable is like the iteration variable in a `foreach` loop except that no actual iteration occurs in a query expression.</span></span> <span data-ttu-id="00e7e-116">Sorgu yürütüldüğünde, Aralık değişkeni içindeki her bir ardışık öğeye başvuru olarak görev yapar `customers` .</span><span class="sxs-lookup"><span data-stu-id="00e7e-116">When the query is executed, the range variable will serve as a reference to each successive element in `customers`.</span></span> <span data-ttu-id="00e7e-117">Derleyici türünü çıkarsanbildiğinden `cust` , açıkça belirtmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="00e7e-117">Because the compiler can infer the type of `cust`, you do not have to specify it explicitly.</span></span> <span data-ttu-id="00e7e-118">Ek Aralık değişkenleri bir yan tümce tarafından bulunabilir `let` .</span><span class="sxs-lookup"><span data-stu-id="00e7e-118">Additional range variables can be introduced by a `let` clause.</span></span> <span data-ttu-id="00e7e-119">Daha fazla bilgi için bkz. [Let yan tümcesi](../../../language-reference/keywords/let-clause.md).</span><span class="sxs-lookup"><span data-stu-id="00e7e-119">For more information, see [let clause](../../../language-reference/keywords/let-clause.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="00e7e-120">Gibi genel olmayan veri kaynakları için <xref:System.Collections.ArrayList> , Aralık değişkeni açıkça yazılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="00e7e-120">For non-generic data sources such as <xref:System.Collections.ArrayList>, the range variable must be explicitly typed.</span></span> <span data-ttu-id="00e7e-121">Daha fazla bilgi için bkz. [LINQ (C#)](./how-to-query-an-arraylist-with-linq.md) ve [from yan tümcesi](../../../language-reference/keywords/from-clause.md)ile ArrayList 'i sorgulama.</span><span class="sxs-lookup"><span data-stu-id="00e7e-121">For more information, see [How to query an ArrayList with LINQ (C#)](./how-to-query-an-arraylist-with-linq.md) and [from clause](../../../language-reference/keywords/from-clause.md).</span></span>  
  
## <a name="filtering"></a><span data-ttu-id="00e7e-122">Filtreleme</span><span class="sxs-lookup"><span data-stu-id="00e7e-122">Filtering</span></span>  
 <span data-ttu-id="00e7e-123">Büyük olasılıkla en yaygın sorgu işlemi, bir filtrenin Boole ifadesi biçiminde uygulanmasından kaynaklanıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="00e7e-123">Probably the most common query operation is to apply a filter in the form of a Boolean expression.</span></span> <span data-ttu-id="00e7e-124">Filtre sorgunun yalnızca ifadenin true olduğu öğeleri döndürmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="00e7e-124">The filter causes the query to return only those elements for which the expression is true.</span></span> <span data-ttu-id="00e7e-125">Sonuç, `where` yan tümcesi kullanılarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="00e7e-125">The result is produced by using the `where` clause.</span></span> <span data-ttu-id="00e7e-126">Etkin filtre, kaynak sırasından hangi öğelerin dışlanacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="00e7e-126">The filter in effect specifies which elements to exclude from the source sequence.</span></span> <span data-ttu-id="00e7e-127">Aşağıdaki örnekte, yalnızca `customers` Londra 'da bir adresi olan kişiler döndürülür.</span><span class="sxs-lookup"><span data-stu-id="00e7e-127">In the following example, only those `customers` who have an address in London are returned.</span></span>  
  
 [!code-csharp[csLINQGettingStarted#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#24)]  
  
 <span data-ttu-id="00e7e-128">`AND` `OR` Tümce içinde gereken sayıda filtre ifadesi uygulamak Için tanıdık C# mantıksal ve işleçlerini kullanabilirsiniz `where` .</span><span class="sxs-lookup"><span data-stu-id="00e7e-128">You can use the familiar C# logical `AND` and `OR` operators to apply as many filter expressions as necessary in the `where` clause.</span></span> <span data-ttu-id="00e7e-129">Örneğin, yalnızca adı "Devon" olan "Londra" dan müşterileri döndürmek için `AND` aşağıdaki kodu yazarsınız:</span><span class="sxs-lookup"><span data-stu-id="00e7e-129">For example, to return only customers from "London" `AND` whose name is "Devon" you would write the following code:</span></span>  
  
 [!code-csharp[csLINQGettingStarted#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#25)]  
  
 <span data-ttu-id="00e7e-130">Londra veya Paris 'ten müşterileri döndürmek için aşağıdaki kodu yazarsınız:</span><span class="sxs-lookup"><span data-stu-id="00e7e-130">To return customers from London or Paris, you would write the following code:</span></span>  
  
 [!code-csharp[csLINQGettingStarted#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#26)]  
  
 <span data-ttu-id="00e7e-131">Daha fazla bilgi için bkz. [WHERE yan tümcesi](../../../language-reference/keywords/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="00e7e-131">For more information, see [where clause](../../../language-reference/keywords/where-clause.md).</span></span>  
  
## <a name="ordering"></a><span data-ttu-id="00e7e-132">Sıralama</span><span class="sxs-lookup"><span data-stu-id="00e7e-132">Ordering</span></span>  
 <span data-ttu-id="00e7e-133">Genellikle döndürülen verileri sıralamak uygundur.</span><span class="sxs-lookup"><span data-stu-id="00e7e-133">Often it is convenient to sort the returned data.</span></span> <span data-ttu-id="00e7e-134">`orderby`Yan tümcesi, döndürülen dizideki öğelerin sıralanmakta olan türün varsayılan karşılaştırmasına göre sıralanmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="00e7e-134">The `orderby` clause will cause the elements in the returned sequence to be sorted according to the default comparer for the type being sorted.</span></span> <span data-ttu-id="00e7e-135">Örneğin, aşağıdaki sorgu sonuçları özelliği temel alarak sıralamak için Genişletilebilir `Name` .</span><span class="sxs-lookup"><span data-stu-id="00e7e-135">For example, the following query can be extended to sort the results based on the `Name` property.</span></span> <span data-ttu-id="00e7e-136">`Name`Bir dize olduğundan, varsayılan karşılaştırıcı, a 'Dan Z 'ye alfabetik bir sıralama gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="00e7e-136">Because `Name` is a string, the default comparer performs an alphabetical sort from A to Z.</span></span>  
  
 [!code-csharp[csLINQGettingStarted#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#27)]  
  
 <span data-ttu-id="00e7e-137">Sonuçları Z 'den A 'ya doğru sırada sıralamak için `orderby…descending` yan tümcesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="00e7e-137">To order the results in reverse order, from Z to A, use the `orderby…descending` clause.</span></span>  
  
 <span data-ttu-id="00e7e-138">Daha fazla bilgi için bkz. [OrderBy tümcesi](../../../language-reference/keywords/orderby-clause.md).</span><span class="sxs-lookup"><span data-stu-id="00e7e-138">For more information, see [orderby clause](../../../language-reference/keywords/orderby-clause.md).</span></span>  
  
## <a name="grouping"></a><span data-ttu-id="00e7e-139">Gruplandırma</span><span class="sxs-lookup"><span data-stu-id="00e7e-139">Grouping</span></span>  
 <span data-ttu-id="00e7e-140">`group`Yan tümcesi, sonuçlarınızı belirttiğiniz bir anahtara göre gruplandırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="00e7e-140">The `group` clause enables you to group your results based on a key that you specify.</span></span> <span data-ttu-id="00e7e-141">Örneğin, `City` Londra veya Paris 'teki tüm müşterilerin ayrı gruplar halinde olması için sonuçların tarafından gruplanmasını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="00e7e-141">For example you could specify that the results should be grouped by the `City` so that all customers from London or Paris are in individual groups.</span></span> <span data-ttu-id="00e7e-142">Bu durumda, `cust.City` anahtardır.</span><span class="sxs-lookup"><span data-stu-id="00e7e-142">In this case, `cust.City` is the key.</span></span>  
  
 [!code-csharp[csLINQGettingStarted#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#28)]  
  
 <span data-ttu-id="00e7e-143">Bir yan tümcesiyle bir sorgu sonlandırdığınızda `group` , sonuçlarınız bir liste listesi alır.</span><span class="sxs-lookup"><span data-stu-id="00e7e-143">When you end a query with a `group` clause, your results take the form of a list of lists.</span></span> <span data-ttu-id="00e7e-144">Listedeki her öğe, bir `Key` üyeye ve bu anahtar altında gruplanmış bir öğe listesine sahip olan bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="00e7e-144">Each element in the list is an object that has a `Key` member and a list of elements that are grouped under that key.</span></span> <span data-ttu-id="00e7e-145">Grup dizisi üreten bir sorgu üzerinde yineleme yaparken, iç içe geçmiş bir döngü kullanmanız gerekir `foreach` .</span><span class="sxs-lookup"><span data-stu-id="00e7e-145">When you iterate over a query that produces a sequence of groups, you must use a nested `foreach` loop.</span></span> <span data-ttu-id="00e7e-146">Dış döngü her grup üzerinde yinelenir ve iç döngü her bir grubun üyesi üzerinde yinelenir.</span><span class="sxs-lookup"><span data-stu-id="00e7e-146">The outer loop iterates over each group, and the inner loop iterates over each group's members.</span></span>  
  
 <span data-ttu-id="00e7e-147">Bir grup işleminin sonuçlarına başvurmanız gerekirse, `into` daha fazla sorgulanabilecek bir tanımlayıcı oluşturmak için anahtar sözcüğünü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="00e7e-147">If you must refer to the results of a group operation, you can use the `into` keyword to create an identifier that can be queried further.</span></span> <span data-ttu-id="00e7e-148">Aşağıdaki sorgu yalnızca ikiden fazla müşteri içeren grupları döndürür:</span><span class="sxs-lookup"><span data-stu-id="00e7e-148">The following query returns only those groups that contain more than two customers:</span></span>  
  
 [!code-csharp[csLINQGettingStarted#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#29)]  
  
 <span data-ttu-id="00e7e-149">Daha fazla bilgi için bkz. [Group yan tümcesi](../../../language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="00e7e-149">For more information, see [group clause](../../../language-reference/keywords/group-clause.md).</span></span>  
  
## <a name="joining"></a><span data-ttu-id="00e7e-150">Katma</span><span class="sxs-lookup"><span data-stu-id="00e7e-150">Joining</span></span>  
 <span data-ttu-id="00e7e-151">JOIN işlemleri, veri kaynaklarında açıkça Modellenmemiş diziler arasında ilişkiler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="00e7e-151">Join operations create associations between sequences that are not explicitly modeled in the data sources.</span></span> <span data-ttu-id="00e7e-152">Örneğin, aynı konuma sahip tüm müşterileri ve dağıtımcıları bulmak için bir JOIN işlemi gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="00e7e-152">For example you can perform a join to find all the customers and distributors who have the same location.</span></span> <span data-ttu-id="00e7e-153">LINQ içinde `join` yan tümce her zaman veritabanı tabloları yerine yalnızca nesne koleksiyonlarına göre geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="00e7e-153">In LINQ the `join` clause always works against object collections instead of database tables directly.</span></span>  
  
 [!code-csharp[csLINQGettingStarted#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#36)]  
  
 <span data-ttu-id="00e7e-154">LINQ ' ta, LINQ `join` içindeki yabancı anahtarlar nesne modelinde bir öğe koleksiyonu tutan özellikler olarak temsil edildiği IÇIN SQL 'de yaptığınız kadar sık kullanmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="00e7e-154">In LINQ, you do not have to use `join` as often as you do in SQL, because foreign keys in LINQ are represented in the object model as properties that hold a collection of items.</span></span> <span data-ttu-id="00e7e-155">Örneğin, bir `Customer` nesnesi bir nesne koleksiyonu içerir `Order` .</span><span class="sxs-lookup"><span data-stu-id="00e7e-155">For example, a `Customer` object contains a collection of `Order` objects.</span></span> <span data-ttu-id="00e7e-156">Bir JOIN gerçekleştirmek yerine, siparişe nokta gösterimini kullanarak erişirsiniz:</span><span class="sxs-lookup"><span data-stu-id="00e7e-156">Rather than performing a join, you access the orders by using dot notation:</span></span>  
  
```csharp
from order in Customer.Orders...  
```  
  
 <span data-ttu-id="00e7e-157">Daha fazla bilgi için bkz. [JOIN yan tümcesi](../../../language-reference/keywords/join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="00e7e-157">For more information, see [join clause](../../../language-reference/keywords/join-clause.md).</span></span>  
  
## <a name="selecting-projections"></a><span data-ttu-id="00e7e-158">Seçme (Tahminler)</span><span class="sxs-lookup"><span data-stu-id="00e7e-158">Selecting (Projections)</span></span>  
 <span data-ttu-id="00e7e-159">`select`Yan tümcesi sorgunun sonuçlarını üretir ve döndürülen her öğenin "şeklini" veya türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="00e7e-159">The `select` clause produces the results of the query and specifies the "shape" or type of each returned element.</span></span> <span data-ttu-id="00e7e-160">Örneğin, sonuçlarınızın tam `Customer` nesneler, yalnızca bir üye, bir üye alt kümesi veya bir hesaplama ya da yeni nesne oluşturmaya göre tamamen farklı sonuç türü olacağını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="00e7e-160">For example, you can specify whether your results will consist of complete `Customer` objects, just one member, a subset of members, or some completely different result type based on a computation or new object creation.</span></span> <span data-ttu-id="00e7e-161">`select`Yan tümce, kaynak öğenin bir kopyası dışında bir şey üretirse, işleme bir *projeksiyon*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="00e7e-161">When the `select` clause produces something other than a copy of the source element, the operation is called a *projection*.</span></span> <span data-ttu-id="00e7e-162">Verileri dönüştürmek için projeksiyonun kullanımı, LINQ sorgu ifadelerinin güçlü bir özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="00e7e-162">The use of projections to transform data is a powerful capability of LINQ query expressions.</span></span> <span data-ttu-id="00e7e-163">Daha fazla bilgi için bkz. [LINQ (C#)](./data-transformations-with-linq.md) ve [Select yan tümcesi](../../../language-reference/keywords/select-clause.md)ile veri dönüştürmeleri.</span><span class="sxs-lookup"><span data-stu-id="00e7e-163">For more information, see [Data Transformations with LINQ (C#)](./data-transformations-with-linq.md) and [select clause](../../../language-reference/keywords/select-clause.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00e7e-164">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00e7e-164">See also</span></span>

- [<span data-ttu-id="00e7e-165">LINQ sorgu Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="00e7e-165">LINQ Query Expressions</span></span>](../../../linq/index.md)
- [<span data-ttu-id="00e7e-166">İzlenecek yol: C 'de sorgu yazma #</span><span class="sxs-lookup"><span data-stu-id="00e7e-166">Walkthrough: Writing Queries in C#</span></span>](./walkthrough-writing-queries-linq.md)
- [<span data-ttu-id="00e7e-167">Sorgu anahtar sözcükleri (LINQ)</span><span class="sxs-lookup"><span data-stu-id="00e7e-167">Query Keywords (LINQ)</span></span>](../../../language-reference/keywords/query-keywords.md)
- [<span data-ttu-id="00e7e-168">Anonim Türler</span><span class="sxs-lookup"><span data-stu-id="00e7e-168">Anonymous Types</span></span>](../../classes-and-structs/anonymous-types.md)
