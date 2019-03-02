---
title: Temel Sorgu İşlemleri (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- data sources [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- ordering data [LINQ in Visual Basic]
- projections [LINQ in Visual Basic]
- LINQ [Visual Basic], query operations
- Order By clause [LINQ in Visual Basic]
- joining data [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], basic operations
- selecting data [LINQ in Visual Basic]
- Group By clause [LINQ in Visual Basic]
- grouping data [LINQ in Visual Basic]
- Select clause [LINQ in Visual Basic]
ms.assetid: 1146f6d0-fcb8-4f4d-8223-c9db52620d21
ms.openlocfilehash: 141040a715487b3cbcfff1c3b9969a0869c8a3d8
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57201721"
---
# <a name="basic-query-operations-visual-basic"></a><span data-ttu-id="62aba-102">Temel Sorgu İşlemleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="62aba-102">Basic Query Operations (Visual Basic)</span></span>
<span data-ttu-id="62aba-103">Bu konu, kısa bir giriş sağlar. [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] ifadeleri Visual Basic'te ve bazı sorguda gerçekleştirdiğiniz işlemleri tipik türleri.</span><span class="sxs-lookup"><span data-stu-id="62aba-103">This topic provides a brief introduction to [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] expressions in Visual Basic, and to some of the typical kinds of operations that you perform in a query.</span></span> <span data-ttu-id="62aba-104">Daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="62aba-104">For more information, see the following topics:</span></span>  
  
 [<span data-ttu-id="62aba-105">Visual Basic'de LINQ'e giriş</span><span class="sxs-lookup"><span data-stu-id="62aba-105">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
  
 [<span data-ttu-id="62aba-106">Sorgular</span><span class="sxs-lookup"><span data-stu-id="62aba-106">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)  
  
 [<span data-ttu-id="62aba-107">İzlenecek yol: Visual Basic'de sorgu yazma</span><span class="sxs-lookup"><span data-stu-id="62aba-107">Walkthrough: Writing Queries in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a><span data-ttu-id="62aba-108">Veri Kaynağını (Kimden) Belirtme</span><span class="sxs-lookup"><span data-stu-id="62aba-108">Specifying the Data Source (From)</span></span>  
 <span data-ttu-id="62aba-109">İçinde bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu, ilk adımıdır sorgulamak istediğiniz veri kaynağını belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="62aba-109">In a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query, the first step is to specify the data source that you want to query.</span></span> <span data-ttu-id="62aba-110">Bu nedenle, `From` yan tümcesinin sorgudaki her zaman gelen ilk.</span><span class="sxs-lookup"><span data-stu-id="62aba-110">Therefore, the `From` clause in a query always comes first.</span></span> <span data-ttu-id="62aba-111">Sorgu işleçleri seçin ve kaynak türüne göre sonuç şekli.</span><span class="sxs-lookup"><span data-stu-id="62aba-111">Query operators select and shape the result based on the type of the source.</span></span>  
  
 [!code-vb[VbLINQBasicOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#1)]  
  
 <span data-ttu-id="62aba-112">`From` Yan tümcesi veri kaynağını belirtir `customers`ve *aralık değişkeni*, `cust`.</span><span class="sxs-lookup"><span data-stu-id="62aba-112">The `From` clause specifies the data source, `customers`, and a *range variable*, `cust`.</span></span> <span data-ttu-id="62aba-113">Aralık değişkeni bir döngü yineleme değişkeni gibi bir sorgu ifadesinde gerçek yineleme gerçekleşir dışında aynıdır.</span><span class="sxs-lookup"><span data-stu-id="62aba-113">The range variable is like a loop iteration variable, except that in a query expression, no actual iteration occurs.</span></span> <span data-ttu-id="62aba-114">Ne zaman sorgu yürütüldüğünde, genellikle kullanarak bir `For Each` aralık değişkeni döngü, hizmet art arda gelen her öğe için başvuru olarak `customers`.</span><span class="sxs-lookup"><span data-stu-id="62aba-114">When the query is executed, often by using a `For Each` loop, the range variable serves as a reference to each successive element in `customers`.</span></span> <span data-ttu-id="62aba-115">Derleyicinin türü çıkarsayabilir `cust`, açıkça belirtmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="62aba-115">Because the compiler can infer the type of `cust`, you do not have to specify it explicitly.</span></span> <span data-ttu-id="62aba-116">Olmadan açık yazım ve yazılan sorgularının örnekleri için bkz: [(Visual Basic) sorgu işlemlerinde tür ilişkileri](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="62aba-116">For examples of queries written with and without explicit typing, see [Type Relationships in Query Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).</span></span>  
  
 <span data-ttu-id="62aba-117">Nasıl kullanılacağı hakkında daha fazla bilgi için `From` yan tümcesine Visual Basic'te bakın [From yan tümcesi](../../../../visual-basic/language-reference/queries/from-clause.md).</span><span class="sxs-lookup"><span data-stu-id="62aba-117">For more information about how to use the `From` clause in Visual Basic, see [From Clause](../../../../visual-basic/language-reference/queries/from-clause.md).</span></span>  
  
## <a name="filtering-data-where"></a><span data-ttu-id="62aba-118">Veri Filtreleme (Yeri)</span><span class="sxs-lookup"><span data-stu-id="62aba-118">Filtering Data (Where)</span></span>  
 <span data-ttu-id="62aba-119">Muhtemelen en sık kullanılan sorgu işlemi formunda bir Boolean ifadesinin filtre uygulanıyor.</span><span class="sxs-lookup"><span data-stu-id="62aba-119">Probably the most common query operation is applying a filter in the form of a Boolean expression.</span></span> <span data-ttu-id="62aba-120">Sorgu, ardından ifade true olduğu öğeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="62aba-120">The query then returns only those elements for which the expression is true.</span></span> <span data-ttu-id="62aba-121">A `Where` yan tümcesi filtreleme işlemleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="62aba-121">A `Where` clause is used to perform the filtering.</span></span> <span data-ttu-id="62aba-122">Filtre hangi öğelerin elde edilen sırayla eklemek için veri kaynağı belirtir.</span><span class="sxs-lookup"><span data-stu-id="62aba-122">The filter specifies which elements in the data source to include in the resulting sequence.</span></span> <span data-ttu-id="62aba-123">Aşağıdaki örnekte, Londra'daki bir adresi olan müşterilerin dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="62aba-123">In the following example, only those customers who have an address in London are included.</span></span>  
  
 [!code-vb[VbLINQBasicOps#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#2)]  
  
 <span data-ttu-id="62aba-124">Mantıksal işleçler gibi kullanabileceğiniz `And` ve `Or` filtre ifadelerinde birleştirmek için bir `Where` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="62aba-124">You can use logical operators such as `And` and `Or` to combine filter expressions in a `Where` clause.</span></span> <span data-ttu-id="62aba-125">Örneğin, yalnızca Londra'dan olan ve Devon adı olan müşteriler döndürmek için aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="62aba-125">For example, to return only those customers who are from London and whose name is Devon, use the following code:</span></span>  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"   
```  
  
 <span data-ttu-id="62aba-126">Müşteriler Londra veya Paris döndürmek için aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="62aba-126">To return customers from London or Paris, use the following code:</span></span>  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"   
```  
  
 <span data-ttu-id="62aba-127">Nasıl kullanılacağı hakkında daha fazla bilgi için `Where` yan tümcesine Visual Basic'te bakın [Where yan tümcesi](../../../../visual-basic/language-reference/queries/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="62aba-127">For more information about how to use the `Where` clause in Visual Basic, see [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md).</span></span>  
  
## <a name="ordering-data-order-by"></a><span data-ttu-id="62aba-128">Veri Sıralama (Sıralama Ölçütü)</span><span class="sxs-lookup"><span data-stu-id="62aba-128">Ordering Data (Order By)</span></span>  
 <span data-ttu-id="62aba-129">Genellikle, döndürülen veriler belirli bir sıralamaya sıralamak uygundur.</span><span class="sxs-lookup"><span data-stu-id="62aba-129">It often is convenient to sort returned data into a particular order.</span></span> <span data-ttu-id="62aba-130">`Order By` Yan tümcesi neden öğeleri belirtilen bir alan veya alanlar üzerinde sıralanacak döndürülen dizideki.</span><span class="sxs-lookup"><span data-stu-id="62aba-130">The `Order By` clause will cause the elements in the returned sequence to be sorted on a specified field or fields.</span></span> <span data-ttu-id="62aba-131">Örneğin, aşağıdaki sorguyu göre sonuçları sıralayan `Name` özelliği.</span><span class="sxs-lookup"><span data-stu-id="62aba-131">For example, the following query sorts the results based on the `Name` property.</span></span> <span data-ttu-id="62aba-132">Çünkü `Name` bir dizedir, döndürülen veriler, a-z alfabetik olarak sıralanır.</span><span class="sxs-lookup"><span data-stu-id="62aba-132">Because `Name` is a string, the returned data will be sorted alphabetically, from A to Z.</span></span>  
  
 [!code-vb[VbLINQBasicOps#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#3)]  
  
 <span data-ttu-id="62aba-133">Sonuçları Z'den A'ya, ters sırada sıralamak için kullanmak `Order By...Descending` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="62aba-133">To order the results in reverse order, from Z to A, use the `Order By...Descending` clause.</span></span> <span data-ttu-id="62aba-134">Varsayılan değer `Ascending` ne zaman `Ascending` ya da `Descending` belirtilir.</span><span class="sxs-lookup"><span data-stu-id="62aba-134">The default is `Ascending` when neither `Ascending` nor `Descending` is specified.</span></span>  
  
 <span data-ttu-id="62aba-135">Nasıl kullanılacağı hakkında daha fazla bilgi için `Order By` yan tümcesine Visual Basic'te bakın [Order By yan tümcesi](../../../../visual-basic/language-reference/queries/order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="62aba-135">For more information about how to use the `Order By` clause in Visual Basic, see [Order By Clause](../../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
## <a name="selecting-data-select"></a><span data-ttu-id="62aba-136">Verileri Seçme (Seçim)</span><span class="sxs-lookup"><span data-stu-id="62aba-136">Selecting Data (Select)</span></span>  
 <span data-ttu-id="62aba-137">`Select` Yan tümcesi, form ve döndürülen öğelerin içeriğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="62aba-137">The `Select` clause specifies the form and content of returned elements.</span></span> <span data-ttu-id="62aba-138">Örneğin, sizin sonuçlarınız, tam oluşacağını belirtebilirsiniz `Customer` nesneler, yalnızca bir tane `Customer` özelliği, bir özellik alt kümesi, çeşitli veri kaynaklarından veya bazı yeni sonuç türü özelliklerinin alan üzerinde bir hesaplama.</span><span class="sxs-lookup"><span data-stu-id="62aba-138">For example, you can specify whether your results will consist of complete `Customer` objects, just one `Customer` property, a subset of properties, a combination of properties from various data sources, or some new result type based on a computation.</span></span> <span data-ttu-id="62aba-139">Zaman `Select` yan tümcesi bir kopyasını bir kaynak öğesi dışında bir şey üretir, işlem çağrılır bir *projeksiyon*.</span><span class="sxs-lookup"><span data-stu-id="62aba-139">When the `Select` clause produces something other than a copy of the source element, the operation is called a *projection*.</span></span>  
  
 <span data-ttu-id="62aba-140">Tam oluşan bir koleksiyonu almak için `Customer` nesneleri, aralık değişkeni seçin:</span><span class="sxs-lookup"><span data-stu-id="62aba-140">To retrieve a collection that consists of complete `Customer` objects, select the range variable itself:</span></span>  
  
 [!code-vb[VbLINQBasicOps#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#4)]  
  
 <span data-ttu-id="62aba-141">Varsa bir `Customer` örneği birçok alan, bir büyük nesnesi olan ve almak istediğiniz tüm adı, seçebileceğiniz `cust.Name`, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="62aba-141">If a `Customer` instance is a large object that has many fields, and all that you want to retrieve is the name, you can select `cust.Name`, as shown in the following example.</span></span> <span data-ttu-id="62aba-142">Yerel tür çıkarımı tanır bu sonuç türü koleksiyonundan değiştirir `Customer` dizelerden oluşan bir koleksiyon nesneleri.</span><span class="sxs-lookup"><span data-stu-id="62aba-142">Local type inference recognizes that this changes the result type from a collection of `Customer` objects to a collection of strings.</span></span>  
  
 [!code-vb[VbLINQBasicOps#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#5)]  
  
 <span data-ttu-id="62aba-143">Veri kaynağından birden çok alan seçmek için iki seçeneğiniz vardır:</span><span class="sxs-lookup"><span data-stu-id="62aba-143">To select multiple fields from the data source, you have two choices:</span></span>  
  
-   <span data-ttu-id="62aba-144">İçinde `Select` yan tümcesi, sonuç dahil etmek istediğiniz alanları belirtin.</span><span class="sxs-lookup"><span data-stu-id="62aba-144">In the `Select` clause, specify the fields you want to include in the result.</span></span> <span data-ttu-id="62aba-145">Derleyici bu alanları olarak kendi özellikleri olan anonim bir tür tanımlar.</span><span class="sxs-lookup"><span data-stu-id="62aba-145">The compiler will define an anonymous type that has those fields as its properties.</span></span> <span data-ttu-id="62aba-146">Daha fazla bilgi için [anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="62aba-146">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
     <span data-ttu-id="62aba-147">Aşağıdaki örnekte döndürülen öğeler anonim bir türün örneklerinin olduğundan, türüne adıyla başka bir yerde kodunuzda başvuruda bulunamaz.</span><span class="sxs-lookup"><span data-stu-id="62aba-147">Because the returned elements in the following example are instances of an anonymous type, you cannot refer to the type by name elsewhere in your code.</span></span> <span data-ttu-id="62aba-148">Derleyici tarafından atanan adı türü için normal Visual Basic kodu içinde geçerli olmayan karakterler içeriyor.</span><span class="sxs-lookup"><span data-stu-id="62aba-148">The compiler-designated name for the type contains characters that are not valid in normal Visual Basic code.</span></span> <span data-ttu-id="62aba-149">Aşağıdaki örnekte, sorgu tarafından döndürülen koleksiyondaki öğelerin `londonCusts4` anonim bir türün örnekleri</span><span class="sxs-lookup"><span data-stu-id="62aba-149">In the following example, the elements in the collection that is returned by the query in `londonCusts4` are instances of an anonymous type</span></span>  
  
     [!code-vb[VbLINQBasicOps#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#6)]  
  
     <span data-ttu-id="62aba-150">-veya-</span><span class="sxs-lookup"><span data-stu-id="62aba-150">-or-</span></span>  
  
-   <span data-ttu-id="62aba-151">Adlandırılmış tür sonucuna dahil, oluşturma ve başlatma türün örneklerinin istediğiniz belirli alanları içeren tanımlama `Select` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="62aba-151">Define a named type that contains the particular fields that you want to include in the result, and create and initialize instances of the type in the `Select` clause.</span></span> <span data-ttu-id="62aba-152">Yalnızca bireysel sonuçları döndürülen koleksiyon dışında kullanmanız gerekiyorsa veya yöntem çağrılarını parametreler olarak geçirileceğini gerekiyorsa bu seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="62aba-152">Use this option only if you have to use individual results outside the collection in which they are returned, or if you have to pass them as parameters in method calls.</span></span> <span data-ttu-id="62aba-153">Türünü `londonCusts5` IEnumerable (Of NamePhone) aşağıdaki örnekte olduğu.</span><span class="sxs-lookup"><span data-stu-id="62aba-153">The type of `londonCusts5` in the following example is IEnumerable(Of NamePhone).</span></span>  
  
     [!code-vb[VbLINQBasicOps#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#7)]  
  
     [!code-vb[VbLINQBasicOps#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#8)]  
  
 <span data-ttu-id="62aba-154">Nasıl kullanılacağı hakkında daha fazla bilgi için `Select` yan tümcesine Visual Basic'te bakın [Select tümcesi](../../../../visual-basic/language-reference/queries/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="62aba-154">For more information about how to use the `Select` clause in Visual Basic, see [Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md).</span></span>  
  
## <a name="joining-data-join-and-group-join"></a><span data-ttu-id="62aba-155">Veri Katma (Katma ve Grup Katma)</span><span class="sxs-lookup"><span data-stu-id="62aba-155">Joining Data (Join and Group Join)</span></span>  
 <span data-ttu-id="62aba-156">Birden fazla veri kaynağında birleştirebilirsiniz `From` çeşitli şekillerde yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="62aba-156">You can combine more than one data source in the `From` clause in several ways.</span></span> <span data-ttu-id="62aba-157">Örneğin, aşağıdaki kod, iki veri kaynağı kullanır ve sonuçta ikisinin özelliklerinden örtük olarak birleştirir.</span><span class="sxs-lookup"><span data-stu-id="62aba-157">For example, the following code uses two data sources and implicitly combines properties from both of them in the result.</span></span> <span data-ttu-id="62aba-158">Sorgu son adları bir harfle başlayan Öğrenciler seçer.</span><span class="sxs-lookup"><span data-stu-id="62aba-158">The query selects students whose last names start with a vowel.</span></span>  
  
 [!code-vb[VbLINQBasicOps#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#9)]  
  
> [!NOTE]
>  <span data-ttu-id="62aba-159">Oluşturulan Öğrenciler listesiyle birlikte bu kodu çalıştırmak [nasıl yapılır: Öğe listesi oluşturma](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span><span class="sxs-lookup"><span data-stu-id="62aba-159">You can run this code with the list of students created in [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span></span>  
  
 <span data-ttu-id="62aba-160">`Join` Anahtar sözcüğü, eşdeğer bir `INNER JOIN` SQL.</span><span class="sxs-lookup"><span data-stu-id="62aba-160">The `Join` keyword is equivalent to an `INNER JOIN` in SQL.</span></span> <span data-ttu-id="62aba-161">Bu, iki koleksiyon öğeleri arasında eşleşen anahtar değerlere göre iki koleksiyon birleştirir.</span><span class="sxs-lookup"><span data-stu-id="62aba-161">It combines two collections based on matching key values between elements in the two collections.</span></span> <span data-ttu-id="62aba-162">Sorgu anahtar değerlerini eşleşen koleksiyon öğelerinin bir kısmını veya tamamını döndürür.</span><span class="sxs-lookup"><span data-stu-id="62aba-162">The query returns all or part of the collection elements that have matching key values.</span></span> <span data-ttu-id="62aba-163">Örneğin, aşağıdaki kod önceki örtük birleştirme eylemini çoğaltır.</span><span class="sxs-lookup"><span data-stu-id="62aba-163">For example, the following code duplicates the action of the previous implicit join.</span></span>  
  
 [!code-vb[VbLINQBasicOps#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#10)]  
  
 <span data-ttu-id="62aba-164">`Group Join` Tıpkı koleksiyonları tek bir hiyerarşik koleksiyon halinde birleştirir bir `LEFT JOIN` SQL.</span><span class="sxs-lookup"><span data-stu-id="62aba-164">`Group Join` combines collections into a single hierarchical collection, just like a `LEFT JOIN` in SQL.</span></span> <span data-ttu-id="62aba-165">Daha fazla bilgi için [JOIN yan tümcesi](../../../../visual-basic/language-reference/queries/join-clause.md) ve [Group JOIN yan tümcesi](../../../../visual-basic/language-reference/queries/group-join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="62aba-165">For more information, see [Join Clause](../../../../visual-basic/language-reference/queries/join-clause.md) and [Group Join Clause](../../../../visual-basic/language-reference/queries/group-join-clause.md).</span></span>  
  
## <a name="grouping-data-group-by"></a><span data-ttu-id="62aba-166">Verileri Gruplandırma (Gruplandırma Ölçütü)</span><span class="sxs-lookup"><span data-stu-id="62aba-166">Grouping Data (Group By)</span></span>  
 <span data-ttu-id="62aba-167">Ekleyebileceğiniz bir `Group By` yan tümcesi bir sorgu sonucunu öğelerin bir veya daha fazla alanlara göre öğeleri gruplandırmak için.</span><span class="sxs-lookup"><span data-stu-id="62aba-167">You can add a `Group By` clause to group the elements in a query result according to one or more fields of the elements.</span></span> <span data-ttu-id="62aba-168">Örneğin, aşağıdaki kod Öğrenciler sınıfı yıla göre gruplandırır.</span><span class="sxs-lookup"><span data-stu-id="62aba-168">For example, the following code groups students by class year.</span></span>  
  
 [!code-vb[VbLINQBasicOps#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#11)]  
  
 <span data-ttu-id="62aba-169">Oluşturulan Öğrenciler listesini kullanarak bu kodu çalıştırırsanız [nasıl yapılır: Bir öğe listesi oluşturma](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md), çıkışı `For Each` deyimidir:</span><span class="sxs-lookup"><span data-stu-id="62aba-169">If you run this code using the list of students created in [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md), the output from the `For Each` statement is:</span></span>  
  
 <span data-ttu-id="62aba-170">Yıl: Alt düzey</span><span class="sxs-lookup"><span data-stu-id="62aba-170">Year: Junior</span></span>  
  
 <span data-ttu-id="62aba-171">Tucker, Michael</span><span class="sxs-lookup"><span data-stu-id="62aba-171">Tucker, Michael</span></span>  
  
 <span data-ttu-id="62aba-172">Garcia, Hugo</span><span class="sxs-lookup"><span data-stu-id="62aba-172">Garcia, Hugo</span></span>  
  
 <span data-ttu-id="62aba-173">Garcia, Debra</span><span class="sxs-lookup"><span data-stu-id="62aba-173">Garcia, Debra</span></span>  
  
 <span data-ttu-id="62aba-174">Tucker, Lance</span><span class="sxs-lookup"><span data-stu-id="62aba-174">Tucker, Lance</span></span>  
  
 <span data-ttu-id="62aba-175">Yıl: Üst düzey</span><span class="sxs-lookup"><span data-stu-id="62aba-175">Year: Senior</span></span>  
  
 <span data-ttu-id="62aba-176">Omelchenko, Svetlana</span><span class="sxs-lookup"><span data-stu-id="62aba-176">Omelchenko, Svetlana</span></span>  
  
 <span data-ttu-id="62aba-177">Osada, Michiko</span><span class="sxs-lookup"><span data-stu-id="62aba-177">Osada, Michiko</span></span>  
  
 <span data-ttu-id="62aba-178">Fakhouri, Fadi</span><span class="sxs-lookup"><span data-stu-id="62aba-178">Fakhouri, Fadi</span></span>  
  
 <span data-ttu-id="62aba-179">Feng, Hanying</span><span class="sxs-lookup"><span data-stu-id="62aba-179">Feng, Hanying</span></span>  
  
 <span data-ttu-id="62aba-180">Adams, Terry</span><span class="sxs-lookup"><span data-stu-id="62aba-180">Adams, Terry</span></span>  
  
 <span data-ttu-id="62aba-181">Yıl: Freshman</span><span class="sxs-lookup"><span data-stu-id="62aba-181">Year: Freshman</span></span>  
  
 <span data-ttu-id="62aba-182">Mortensen, Sven</span><span class="sxs-lookup"><span data-stu-id="62aba-182">Mortensen, Sven</span></span>  
  
 <span data-ttu-id="62aba-183">Garcia, Cesar</span><span class="sxs-lookup"><span data-stu-id="62aba-183">Garcia, Cesar</span></span>  
  
 <span data-ttu-id="62aba-184">Aşağıdaki kodda gösterilen değişim sınıfı yıllar sıralar ve ardından Öğrenciler her yıl içinde soyadına göre sıralar.</span><span class="sxs-lookup"><span data-stu-id="62aba-184">The variation shown in the following code orders the class years, and then orders the students within each year by last name.</span></span>  
  
 [!code-vb[VbLINQBasicOps#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#12)]  
  
 <span data-ttu-id="62aba-185">Hakkında daha fazla bilgi için `Group By`, bkz: [Group yan tümcesi tarafından](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="62aba-185">For more information about `Group By`, see [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62aba-186">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="62aba-186">See also</span></span>
- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="62aba-187">Visual Basic'te lınq'e Başlarken</span><span class="sxs-lookup"><span data-stu-id="62aba-187">Getting Started with LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [<span data-ttu-id="62aba-188">Sorgular</span><span class="sxs-lookup"><span data-stu-id="62aba-188">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="62aba-189">Standart sorgu işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="62aba-189">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="62aba-190">LINQ</span><span class="sxs-lookup"><span data-stu-id="62aba-190">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
