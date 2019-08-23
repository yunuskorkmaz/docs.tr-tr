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
ms.openlocfilehash: 12f10f30dd767f3435044f2bbebe0eb865c29d0c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939375"
---
# <a name="basic-query-operations-visual-basic"></a><span data-ttu-id="0de2f-102">Temel Sorgu İşlemleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0de2f-102">Basic Query Operations (Visual Basic)</span></span>
<span data-ttu-id="0de2f-103">Bu konu, Visual Basic [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] ifadelerine ve bir sorguda gerçekleştirdiğiniz bazı tipik işlem türlerine kısa bir giriş sağlar.</span><span class="sxs-lookup"><span data-stu-id="0de2f-103">This topic provides a brief introduction to [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] expressions in Visual Basic, and to some of the typical kinds of operations that you perform in a query.</span></span> <span data-ttu-id="0de2f-104">Daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="0de2f-104">For more information, see the following topics:</span></span>  
  
 [<span data-ttu-id="0de2f-105">Visual Basic LINQ 'e giriş</span><span class="sxs-lookup"><span data-stu-id="0de2f-105">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
  
 [<span data-ttu-id="0de2f-106">Sorgular</span><span class="sxs-lookup"><span data-stu-id="0de2f-106">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)  
  
 [<span data-ttu-id="0de2f-107">İzlenecek yol: Visual Basic sorguları yazma</span><span class="sxs-lookup"><span data-stu-id="0de2f-107">Walkthrough: Writing Queries in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a><span data-ttu-id="0de2f-108">Veri Kaynağını (Kimden) Belirtme</span><span class="sxs-lookup"><span data-stu-id="0de2f-108">Specifying the Data Source (From)</span></span>  
 <span data-ttu-id="0de2f-109">Bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorguda, ilk adım sorgulamak istediğiniz veri kaynağını belirtmektir.</span><span class="sxs-lookup"><span data-stu-id="0de2f-109">In a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query, the first step is to specify the data source that you want to query.</span></span> <span data-ttu-id="0de2f-110">Bu nedenle, `From` bir sorgudaki yan tümce her zaman ilk olarak gelir.</span><span class="sxs-lookup"><span data-stu-id="0de2f-110">Therefore, the `From` clause in a query always comes first.</span></span> <span data-ttu-id="0de2f-111">Sorgu işleçleri, kaynağın türüne göre sonucu seçin ve şekillendirin.</span><span class="sxs-lookup"><span data-stu-id="0de2f-111">Query operators select and shape the result based on the type of the source.</span></span>  
  
 [!code-vb[VbLINQBasicOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#1)]  
  
 <span data-ttu-id="0de2f-112">Yan tümce `customers`veri kaynağını ,`cust`ve bir *Aralık değişkenini*belirtir. `From`</span><span class="sxs-lookup"><span data-stu-id="0de2f-112">The `From` clause specifies the data source, `customers`, and a *range variable*, `cust`.</span></span> <span data-ttu-id="0de2f-113">Aralık değişkeni, bir sorgu ifadesinde gerçek yineleme gerçekleşmediğinde bir döngü yineleme değişkeni gibidir.</span><span class="sxs-lookup"><span data-stu-id="0de2f-113">The range variable is like a loop iteration variable, except that in a query expression, no actual iteration occurs.</span></span> <span data-ttu-id="0de2f-114">Sorgu yürütüldüğünde, genellikle bir `For Each` döngü kullanılarak Aralık değişkeni, içinde `customers`birbirini izleyen her öğe için bir başvuru işlevi görür.</span><span class="sxs-lookup"><span data-stu-id="0de2f-114">When the query is executed, often by using a `For Each` loop, the range variable serves as a reference to each successive element in `customers`.</span></span> <span data-ttu-id="0de2f-115">Derleyici türünü `cust`çıkarsanbildiğinden, açıkça belirtmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="0de2f-115">Because the compiler can infer the type of `cust`, you do not have to specify it explicitly.</span></span> <span data-ttu-id="0de2f-116">Açık yazma olmadan ve ile yazılan sorguların örnekleri için bkz. [sorgu Işlemlerinde tür ilişkileri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="0de2f-116">For examples of queries written with and without explicit typing, see [Type Relationships in Query Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).</span></span>  
  
 <span data-ttu-id="0de2f-117">Visual Basic `From` yan tümcesini kullanma hakkında daha fazla bilgi için bkz. [from yan tümcesi](../../../../visual-basic/language-reference/queries/from-clause.md).</span><span class="sxs-lookup"><span data-stu-id="0de2f-117">For more information about how to use the `From` clause in Visual Basic, see [From Clause](../../../../visual-basic/language-reference/queries/from-clause.md).</span></span>  
  
## <a name="filtering-data-where"></a><span data-ttu-id="0de2f-118">Veri Filtreleme (Yeri)</span><span class="sxs-lookup"><span data-stu-id="0de2f-118">Filtering Data (Where)</span></span>  
 <span data-ttu-id="0de2f-119">Büyük olasılıkla en yaygın sorgu işlemi, bir filtreyi Boole ifadesi biçiminde uyguluyor.</span><span class="sxs-lookup"><span data-stu-id="0de2f-119">Probably the most common query operation is applying a filter in the form of a Boolean expression.</span></span> <span data-ttu-id="0de2f-120">Sorgu daha sonra yalnızca ifadenin true olduğu öğeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="0de2f-120">The query then returns only those elements for which the expression is true.</span></span> <span data-ttu-id="0de2f-121">Filtre `Where` uygulamak için bir yan tümce kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0de2f-121">A `Where` clause is used to perform the filtering.</span></span> <span data-ttu-id="0de2f-122">Filtre, veri kaynağındaki hangi öğelerin sonuç dizisine ekleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0de2f-122">The filter specifies which elements in the data source to include in the resulting sequence.</span></span> <span data-ttu-id="0de2f-123">Aşağıdaki örnekte, yalnızca Londra 'da bir adresi olan müşteriler dahil edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0de2f-123">In the following example, only those customers who have an address in London are included.</span></span>  
  
 [!code-vb[VbLINQBasicOps#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#2)]  
  
 <span data-ttu-id="0de2f-124">Bir `Or` `And` yantümcedekiFiltreifadelerinibirleştirmekiçinvegibimantıksalişleçlerikullanabilirsiniz.`Where`</span><span class="sxs-lookup"><span data-stu-id="0de2f-124">You can use logical operators such as `And` and `Or` to combine filter expressions in a `Where` clause.</span></span> <span data-ttu-id="0de2f-125">Örneğin, yalnızca Londra 'dan ve adı Devon olan müşterileri döndürmek için aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="0de2f-125">For example, to return only those customers who are from London and whose name is Devon, use the following code:</span></span>  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"   
```  
  
 <span data-ttu-id="0de2f-126">Londra veya Paris 'ten müşterileri döndürmek için aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="0de2f-126">To return customers from London or Paris, use the following code:</span></span>  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"   
```  
  
 <span data-ttu-id="0de2f-127">`Where` Yan tümcesinin Visual Basic ' de nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [WHERE yan tümcesi](../../../../visual-basic/language-reference/queries/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="0de2f-127">For more information about how to use the `Where` clause in Visual Basic, see [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md).</span></span>  
  
## <a name="ordering-data-order-by"></a><span data-ttu-id="0de2f-128">Veri Sıralama (Sıralama Ölçütü)</span><span class="sxs-lookup"><span data-stu-id="0de2f-128">Ordering Data (Order By)</span></span>  
 <span data-ttu-id="0de2f-129">Genellikle döndürülen verileri belirli bir sıraya göre sıralamak kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="0de2f-129">It often is convenient to sort returned data into a particular order.</span></span> <span data-ttu-id="0de2f-130">`Order By` Yan tümcesi, döndürülen dizideki öğelerin belirtilen alan veya alanlar üzerinde sıralanmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="0de2f-130">The `Order By` clause will cause the elements in the returned sequence to be sorted on a specified field or fields.</span></span> <span data-ttu-id="0de2f-131">Örneğin, aşağıdaki sorgu sonuçları `Name` özelliğine göre sıralar.</span><span class="sxs-lookup"><span data-stu-id="0de2f-131">For example, the following query sorts the results based on the `Name` property.</span></span> <span data-ttu-id="0de2f-132">Bir `Name` dize olduğu için döndürülen veriler, a 'dan Z 'ye kadar alfabetik olarak sıralanır.</span><span class="sxs-lookup"><span data-stu-id="0de2f-132">Because `Name` is a string, the returned data will be sorted alphabetically, from A to Z.</span></span>  
  
 [!code-vb[VbLINQBasicOps#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#3)]  
  
 <span data-ttu-id="0de2f-133">Sonuçları Z 'den A 'ya doğru sırada sıralamak için `Order By...Descending` yan tümcesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="0de2f-133">To order the results in reverse order, from Z to A, use the `Order By...Descending` clause.</span></span> <span data-ttu-id="0de2f-134">Varsayılan değer ne `Ascending` `Ascending` de`Descending` belirtilmemişse varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="0de2f-134">The default is `Ascending` when neither `Ascending` nor `Descending` is specified.</span></span>  
  
 <span data-ttu-id="0de2f-135">Visual Basic `Order By` yan tümcesini kullanma hakkında daha fazla bilgi için bkz. [order by yan tümcesi](../../../../visual-basic/language-reference/queries/order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="0de2f-135">For more information about how to use the `Order By` clause in Visual Basic, see [Order By Clause](../../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
## <a name="selecting-data-select"></a><span data-ttu-id="0de2f-136">Verileri Seçme (Seçim)</span><span class="sxs-lookup"><span data-stu-id="0de2f-136">Selecting Data (Select)</span></span>  
 <span data-ttu-id="0de2f-137">`Select` Yan tümce döndürülen öğelerin formunu ve içeriğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0de2f-137">The `Select` clause specifies the form and content of returned elements.</span></span> <span data-ttu-id="0de2f-138">Örneğin, sonuçlarınızın tam `Customer` nesnelerden, tek bir `Customer` özellikten, özelliklerin bir alt kümesinden, çeşitli veri kaynaklarından özelliklerin bir birleşimini veya bir hesaplamayı temel alan bir dizi yeni sonuç türüne sahip olup olmayacağını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0de2f-138">For example, you can specify whether your results will consist of complete `Customer` objects, just one `Customer` property, a subset of properties, a combination of properties from various data sources, or some new result type based on a computation.</span></span> <span data-ttu-id="0de2f-139">Yan tümce, kaynak öğenin bir kopyası dışında bir şey üretirse, işleme bir projeksiyon olarak adlandırılır. `Select`</span><span class="sxs-lookup"><span data-stu-id="0de2f-139">When the `Select` clause produces something other than a copy of the source element, the operation is called a *projection*.</span></span>  
  
 <span data-ttu-id="0de2f-140">Tüm `Customer` nesnelerden oluşan bir koleksiyonu almak için, Aralık değişkeninin kendisini seçin:</span><span class="sxs-lookup"><span data-stu-id="0de2f-140">To retrieve a collection that consists of complete `Customer` objects, select the range variable itself:</span></span>  
  
 [!code-vb[VbLINQBasicOps#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#4)]  
  
 <span data-ttu-id="0de2f-141">Bir `Customer` örnek çok fazla alan içeren büyük bir nesnedir ve almak istediğiniz tümü adı ise, aşağıdaki örnekte gösterildiği gibi öğesini seçebilirsiniz `cust.Name`.</span><span class="sxs-lookup"><span data-stu-id="0de2f-141">If a `Customer` instance is a large object that has many fields, and all that you want to retrieve is the name, you can select `cust.Name`, as shown in the following example.</span></span> <span data-ttu-id="0de2f-142">Yerel tür çıkarımı, bu, sonuç türünü `Customer` nesne koleksiyonundan bir dizeler koleksiyonuna değiştirinin algılar.</span><span class="sxs-lookup"><span data-stu-id="0de2f-142">Local type inference recognizes that this changes the result type from a collection of `Customer` objects to a collection of strings.</span></span>  
  
 [!code-vb[VbLINQBasicOps#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#5)]  
  
 <span data-ttu-id="0de2f-143">Veri kaynağından birden çok alan seçmek için iki seçeneğiniz vardır:</span><span class="sxs-lookup"><span data-stu-id="0de2f-143">To select multiple fields from the data source, you have two choices:</span></span>  
  
- <span data-ttu-id="0de2f-144">`Select` Yan tümcesinde, sonuca dahil etmek istediğiniz alanları belirtin.</span><span class="sxs-lookup"><span data-stu-id="0de2f-144">In the `Select` clause, specify the fields you want to include in the result.</span></span> <span data-ttu-id="0de2f-145">Derleyici, özellikleri olarak bu alanlara sahip anonim bir tür tanımlayacaktır.</span><span class="sxs-lookup"><span data-stu-id="0de2f-145">The compiler will define an anonymous type that has those fields as its properties.</span></span> <span data-ttu-id="0de2f-146">Daha fazla bilgi için bkz. [anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="0de2f-146">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
     <span data-ttu-id="0de2f-147">Aşağıdaki örnekteki döndürülen öğeler anonim bir türün örnekleri olduğundan, kodunuzun başka bir yerinde ada göre türe başvuramaz.</span><span class="sxs-lookup"><span data-stu-id="0de2f-147">Because the returned elements in the following example are instances of an anonymous type, you cannot refer to the type by name elsewhere in your code.</span></span> <span data-ttu-id="0de2f-148">Tür için derleyici tarafından belirlenen ad, normal Visual Basic kodunda geçerli olmayan karakterler içeriyor.</span><span class="sxs-lookup"><span data-stu-id="0de2f-148">The compiler-designated name for the type contains characters that are not valid in normal Visual Basic code.</span></span> <span data-ttu-id="0de2f-149">Aşağıdaki örnekte, içindeki `londonCusts4` sorgu tarafından döndürülen koleksiyonda bulunan öğeler, anonim bir türün örnekleridir</span><span class="sxs-lookup"><span data-stu-id="0de2f-149">In the following example, the elements in the collection that is returned by the query in `londonCusts4` are instances of an anonymous type</span></span>  
  
     [!code-vb[VbLINQBasicOps#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#6)]  
  
     <span data-ttu-id="0de2f-150">-veya-</span><span class="sxs-lookup"><span data-stu-id="0de2f-150">-or-</span></span>  
  
- <span data-ttu-id="0de2f-151">Sonuca dahil etmek istediğiniz belirli alanları içeren adlandırılmış bir tür tanımlayın ve `Select` yan tümcesindeki tür örneklerini oluşturun ve başlatın.</span><span class="sxs-lookup"><span data-stu-id="0de2f-151">Define a named type that contains the particular fields that you want to include in the result, and create and initialize instances of the type in the `Select` clause.</span></span> <span data-ttu-id="0de2f-152">Bu seçeneği yalnızca, sonuçları döndürüldüğünden koleksiyonun dışında veya yöntem çağrılarında parametre olarak geçirmeniz gerekiyorsa kullanın.</span><span class="sxs-lookup"><span data-stu-id="0de2f-152">Use this option only if you have to use individual results outside the collection in which they are returned, or if you have to pass them as parameters in method calls.</span></span> <span data-ttu-id="0de2f-153">Aşağıdaki örnekteki tür `londonCusts5` IEnumerable (namephone).</span><span class="sxs-lookup"><span data-stu-id="0de2f-153">The type of `londonCusts5` in the following example is IEnumerable(Of NamePhone).</span></span>  
  
     [!code-vb[VbLINQBasicOps#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#7)]  
  
     [!code-vb[VbLINQBasicOps#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#8)]  
  
 <span data-ttu-id="0de2f-154">Visual Basic `Select` yan tümcesini kullanma hakkında daha fazla bilgi için bkz. [Select yan tümcesi](../../../../visual-basic/language-reference/queries/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="0de2f-154">For more information about how to use the `Select` clause in Visual Basic, see [Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md).</span></span>  
  
## <a name="joining-data-join-and-group-join"></a><span data-ttu-id="0de2f-155">Veri Katma (Katma ve Grup Katma)</span><span class="sxs-lookup"><span data-stu-id="0de2f-155">Joining Data (Join and Group Join)</span></span>  
 <span data-ttu-id="0de2f-156">`From` Yan tümcelerinde birden fazla veri kaynağını çeşitli yollarla birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0de2f-156">You can combine more than one data source in the `From` clause in several ways.</span></span> <span data-ttu-id="0de2f-157">Örneğin, aşağıdaki kod iki veri kaynağını kullanır ve sonuç olarak her ikisinin de özelliklerini örtülü olarak birleştirir.</span><span class="sxs-lookup"><span data-stu-id="0de2f-157">For example, the following code uses two data sources and implicitly combines properties from both of them in the result.</span></span> <span data-ttu-id="0de2f-158">Sorgu, son adları sesli harf ile başlayan öğrencileri seçer.</span><span class="sxs-lookup"><span data-stu-id="0de2f-158">The query selects students whose last names start with a vowel.</span></span>  
  
 [!code-vb[VbLINQBasicOps#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#9)]  
  
> [!NOTE]
> <span data-ttu-id="0de2f-159">Bu kodu, [nasıl yapılır: Öğelerin](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)bir listesini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0de2f-159">You can run this code with the list of students created in [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span></span>  
  
 <span data-ttu-id="0de2f-160">Anahtar `Join` sözcüğü, SQL içindeki bir `INNER JOIN` ile eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="0de2f-160">The `Join` keyword is equivalent to an `INNER JOIN` in SQL.</span></span> <span data-ttu-id="0de2f-161">İki koleksiyonu iki koleksiyonda bulunan öğeler arasında eşleşen anahtar değerlerine dayalı olarak birleştirir.</span><span class="sxs-lookup"><span data-stu-id="0de2f-161">It combines two collections based on matching key values between elements in the two collections.</span></span> <span data-ttu-id="0de2f-162">Sorgu, eşleşen anahtar değerleri olan koleksiyon öğelerinin tümünü veya bir bölümünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="0de2f-162">The query returns all or part of the collection elements that have matching key values.</span></span> <span data-ttu-id="0de2f-163">Örneğin, aşağıdaki kod önceki örtük birleşimin eylemini yineliyor.</span><span class="sxs-lookup"><span data-stu-id="0de2f-163">For example, the following code duplicates the action of the previous implicit join.</span></span>  
  
 [!code-vb[VbLINQBasicOps#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#10)]  
  
 <span data-ttu-id="0de2f-164">`Group Join`koleksiyonları SQL gibi tek bir `LEFT JOIN` hiyerarşik koleksiyonda birleştirir.</span><span class="sxs-lookup"><span data-stu-id="0de2f-164">`Group Join` combines collections into a single hierarchical collection, just like a `LEFT JOIN` in SQL.</span></span> <span data-ttu-id="0de2f-165">Daha fazla bilgi için bkz. [JOIN yan tümcesi](../../../../visual-basic/language-reference/queries/join-clause.md) ve [Group JOIN yan tümcesi](../../../../visual-basic/language-reference/queries/group-join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="0de2f-165">For more information, see [Join Clause](../../../../visual-basic/language-reference/queries/join-clause.md) and [Group Join Clause](../../../../visual-basic/language-reference/queries/group-join-clause.md).</span></span>  
  
## <a name="grouping-data-group-by"></a><span data-ttu-id="0de2f-166">Verileri Gruplandırma (Gruplandırma Ölçütü)</span><span class="sxs-lookup"><span data-stu-id="0de2f-166">Grouping Data (Group By)</span></span>  
 <span data-ttu-id="0de2f-167">Bir sorgu sonucundaki `Group By` öğeleri, öğelerin bir veya daha fazla alanına göre gruplandırmak için bir yan tümce ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0de2f-167">You can add a `Group By` clause to group the elements in a query result according to one or more fields of the elements.</span></span> <span data-ttu-id="0de2f-168">Örneğin, aşağıdaki kod, öğrencileri sınıf yılından gruplandırır.</span><span class="sxs-lookup"><span data-stu-id="0de2f-168">For example, the following code groups students by class year.</span></span>  
  
 [!code-vb[VbLINQBasicOps#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#11)]  
  
 <span data-ttu-id="0de2f-169">Bu kodu, [nasıl yapılır: Öğelerin](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)bir listesini oluşturun, `For Each` deyimden alınan çıkış şu şekilde olur:</span><span class="sxs-lookup"><span data-stu-id="0de2f-169">If you run this code using the list of students created in [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md), the output from the `For Each` statement is:</span></span>  
  
 <span data-ttu-id="0de2f-170">Yıl Junior</span><span class="sxs-lookup"><span data-stu-id="0de2f-170">Year: Junior</span></span>  
  
 <span data-ttu-id="0de2f-171">Tucker, Michael</span><span class="sxs-lookup"><span data-stu-id="0de2f-171">Tucker, Michael</span></span>  
  
 <span data-ttu-id="0de2f-172">Garcia, Kugo</span><span class="sxs-lookup"><span data-stu-id="0de2f-172">Garcia, Hugo</span></span>  
  
 <span data-ttu-id="0de2f-173">Garcia, Deköşeli</span><span class="sxs-lookup"><span data-stu-id="0de2f-173">Garcia, Debra</span></span>  
  
 <span data-ttu-id="0de2f-174">Tucker, Izleme</span><span class="sxs-lookup"><span data-stu-id="0de2f-174">Tucker, Lance</span></span>  
  
 <span data-ttu-id="0de2f-175">Yıl Li</span><span class="sxs-lookup"><span data-stu-id="0de2f-175">Year: Senior</span></span>  
  
 <span data-ttu-id="0de2f-176">Omelchenko, Svetlana</span><span class="sxs-lookup"><span data-stu-id="0de2f-176">Omelchenko, Svetlana</span></span>  
  
 <span data-ttu-id="0de2f-177">Osada, Michiko</span><span class="sxs-lookup"><span data-stu-id="0de2f-177">Osada, Michiko</span></span>  
  
 <span data-ttu-id="0de2f-178">Fakhouri, Fadi</span><span class="sxs-lookup"><span data-stu-id="0de2f-178">Fakhouri, Fadi</span></span>  
  
 <span data-ttu-id="0de2f-179">Feng, Hanying</span><span class="sxs-lookup"><span data-stu-id="0de2f-179">Feng, Hanying</span></span>  
  
 <span data-ttu-id="0de2f-180">Adams, Terry</span><span class="sxs-lookup"><span data-stu-id="0de2f-180">Adams, Terry</span></span>  
  
 <span data-ttu-id="0de2f-181">Yıl En ye Man</span><span class="sxs-lookup"><span data-stu-id="0de2f-181">Year: Freshman</span></span>  
  
 <span data-ttu-id="0de2f-182">Mortensen, Sven</span><span class="sxs-lookup"><span data-stu-id="0de2f-182">Mortensen, Sven</span></span>  
  
 <span data-ttu-id="0de2f-183">Garcia, Cesar</span><span class="sxs-lookup"><span data-stu-id="0de2f-183">Garcia, Cesar</span></span>  
  
 <span data-ttu-id="0de2f-184">Aşağıdaki kodda gösterilen varyasyon, sınıf yıllarını sıralar ve ardından her yıl içinde öğrencileri soyadı olarak sıralar.</span><span class="sxs-lookup"><span data-stu-id="0de2f-184">The variation shown in the following code orders the class years, and then orders the students within each year by last name.</span></span>  
  
 [!code-vb[VbLINQBasicOps#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#12)]  
  
 <span data-ttu-id="0de2f-185">Hakkında `Group By`daha fazla bilgi için bkz. [Group by yan tümcesi](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="0de2f-185">For more information about `Group By`, see [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0de2f-186">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0de2f-186">See also</span></span>

- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="0de2f-187">Visual Basic LINQ ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="0de2f-187">Getting Started with LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [<span data-ttu-id="0de2f-188">Sorgular</span><span class="sxs-lookup"><span data-stu-id="0de2f-188">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="0de2f-189">Standart sorgu Işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0de2f-189">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="0de2f-190">LINQ</span><span class="sxs-lookup"><span data-stu-id="0de2f-190">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
