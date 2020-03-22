---
title: Temel Sorgu İşlemleri
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
ms.openlocfilehash: efae72c65ad67b4a1b157b67dcc4d4d65f31f77b
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266384"
---
# <a name="basic-query-operations-visual-basic"></a><span data-ttu-id="31691-102">Temel Sorgu İşlemleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31691-102">Basic Query Operations (Visual Basic)</span></span>
<span data-ttu-id="31691-103">Bu konu, Visual Basic'teki Dil Tümleşik Sorgu (LINQ) ifadelerine ve bir sorguda gerçekleştirdiğiniz tipik işlem türlerinden bazılarına kısa bir giriş sağlar.</span><span class="sxs-lookup"><span data-stu-id="31691-103">This topic provides a brief introduction to Language-Integrated Query (LINQ) expressions in Visual Basic, and to some of the typical kinds of operations that you perform in a query.</span></span> <span data-ttu-id="31691-104">Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:</span><span class="sxs-lookup"><span data-stu-id="31691-104">For more information, see the following topics:</span></span>  
  
 [<span data-ttu-id="31691-105">Visual Basic'de LINQ'e Giriş</span><span class="sxs-lookup"><span data-stu-id="31691-105">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
  
 [<span data-ttu-id="31691-106">Sorgular</span><span class="sxs-lookup"><span data-stu-id="31691-106">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)  
  
 [<span data-ttu-id="31691-107">İzlenecek Yol: Visual Basic'de Sorgu Yazma</span><span class="sxs-lookup"><span data-stu-id="31691-107">Walkthrough: Writing Queries in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a><span data-ttu-id="31691-108">Veri Kaynağını (Kimden) Belirtme</span><span class="sxs-lookup"><span data-stu-id="31691-108">Specifying the Data Source (From)</span></span>  
 <span data-ttu-id="31691-109">LINQ sorgusunda ilk adım, sorgulamak istediğiniz veri kaynağını belirtmektir.</span><span class="sxs-lookup"><span data-stu-id="31691-109">In a LINQ query, the first step is to specify the data source that you want to query.</span></span> <span data-ttu-id="31691-110">Bu nedenle, bir sorguda `From` yan tümce her zaman önce gelir.</span><span class="sxs-lookup"><span data-stu-id="31691-110">Therefore, the `From` clause in a query always comes first.</span></span> <span data-ttu-id="31691-111">Sorgu işleçleri kaynağın türüne göre sonucu seçer ve şekillendirin.</span><span class="sxs-lookup"><span data-stu-id="31691-111">Query operators select and shape the result based on the type of the source.</span></span>  
  
 [!code-vb[VbLINQBasicOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#1)]  
  
 <span data-ttu-id="31691-112">Yan `From` tümce, veri kaynağını `customers`ve *bir aralık değişkenini* `cust`belirtir.</span><span class="sxs-lookup"><span data-stu-id="31691-112">The `From` clause specifies the data source, `customers`, and a *range variable*, `cust`.</span></span> <span data-ttu-id="31691-113">Aralık değişkeni bir döngü yineleme değişkeni gibidir, ancak sorgu ifadesinde gerçek yineleme gerçekleşmez.</span><span class="sxs-lookup"><span data-stu-id="31691-113">The range variable is like a loop iteration variable, except that in a query expression, no actual iteration occurs.</span></span> <span data-ttu-id="31691-114">Sorgu yürütüldüğünde, genellikle bir `For Each` döngü kullanılarak, aralık değişkeni `customers`.</span><span class="sxs-lookup"><span data-stu-id="31691-114">When the query is executed, often by using a `For Each` loop, the range variable serves as a reference to each successive element in `customers`.</span></span> <span data-ttu-id="31691-115">Derleyici türünü `cust`çıkarabileceğinden, bunu açıkça belirtmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="31691-115">Because the compiler can infer the type of `cust`, you do not have to specify it explicitly.</span></span> <span data-ttu-id="31691-116">Açık yazıyla ve açık yazmadan yazılan sorgu örnekleri için sorgu [işlemlerinde (Visual Basic) Tür İlişkileri](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="31691-116">For examples of queries written with and without explicit typing, see [Type Relationships in Query Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md).</span></span>  
  
 <span data-ttu-id="31691-117">Visual Basic'teki yan `From` tümcenin nasıl kullanılacağı hakkında daha fazla bilgi için [Bkz.](../../../../visual-basic/language-reference/queries/from-clause.md)</span><span class="sxs-lookup"><span data-stu-id="31691-117">For more information about how to use the `From` clause in Visual Basic, see [From Clause](../../../../visual-basic/language-reference/queries/from-clause.md).</span></span>  
  
## <a name="filtering-data-where"></a><span data-ttu-id="31691-118">Veri Filtreleme (Yeri)</span><span class="sxs-lookup"><span data-stu-id="31691-118">Filtering Data (Where)</span></span>  
 <span data-ttu-id="31691-119">Büyük olasılıkla en yaygın sorgu işlemi Boolean ifadesi şeklinde bir filtre uygulamaktır.</span><span class="sxs-lookup"><span data-stu-id="31691-119">Probably the most common query operation is applying a filter in the form of a Boolean expression.</span></span> <span data-ttu-id="31691-120">Sorgu daha sonra yalnızca ifadenin doğru olduğu öğeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="31691-120">The query then returns only those elements for which the expression is true.</span></span> <span data-ttu-id="31691-121">Filtreleme gerçekleştirmek için bir `Where` yan tümce kullanılır.</span><span class="sxs-lookup"><span data-stu-id="31691-121">A `Where` clause is used to perform the filtering.</span></span> <span data-ttu-id="31691-122">Filtre, veri kaynağındaki hangi öğelerin elde edilen sıraya dahil olacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="31691-122">The filter specifies which elements in the data source to include in the resulting sequence.</span></span> <span data-ttu-id="31691-123">Aşağıdaki örnekte, yalnızca Londra'da adresi olan müşteriler dahildir.</span><span class="sxs-lookup"><span data-stu-id="31691-123">In the following example, only those customers who have an address in London are included.</span></span>  
  
 [!code-vb[VbLINQBasicOps#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#2)]  
  
 <span data-ttu-id="31691-124">Bir `Where` yan tümcedeki `And` `Or` filtre ifadeleri gibi mantıksal işleçleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31691-124">You can use logical operators such as `And` and `Or` to combine filter expressions in a `Where` clause.</span></span> <span data-ttu-id="31691-125">Örneğin, yalnızca Londra'dan gelen ve adı Devon olan müşterileri döndürmek için aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="31691-125">For example, to return only those customers who are from London and whose name is Devon, use the following code:</span></span>  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"
```  
  
 <span data-ttu-id="31691-126">Londra veya Paris'ten müşterileri iade etmek için aşağıdaki kodu kullanın:</span><span class="sxs-lookup"><span data-stu-id="31691-126">To return customers from London or Paris, use the following code:</span></span>  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"
```  
  
 <span data-ttu-id="31691-127">Visual Basic'teki yan `Where` tümcenin nasıl kullanılacağı hakkında daha fazla bilgi için [bkz.](../../../../visual-basic/language-reference/queries/where-clause.md)</span><span class="sxs-lookup"><span data-stu-id="31691-127">For more information about how to use the `Where` clause in Visual Basic, see [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md).</span></span>  
  
## <a name="ordering-data-order-by"></a><span data-ttu-id="31691-128">Veri Sıralama (Sıralama Ölçütü)</span><span class="sxs-lookup"><span data-stu-id="31691-128">Ordering Data (Order By)</span></span>  
 <span data-ttu-id="31691-129">Döndürülen verileri belirli bir sırada sıralamak genellikle uygundur.</span><span class="sxs-lookup"><span data-stu-id="31691-129">It often is convenient to sort returned data into a particular order.</span></span> <span data-ttu-id="31691-130">Yan `Order By` tümce, döndürülen sırada yer alan öğelerin belirli bir alanda veya alanda sıralansın.</span><span class="sxs-lookup"><span data-stu-id="31691-130">The `Order By` clause will cause the elements in the returned sequence to be sorted on a specified field or fields.</span></span> <span data-ttu-id="31691-131">Örneğin, aşağıdaki sorgu sonuçları `Name` özelliğe göre sıralar.</span><span class="sxs-lookup"><span data-stu-id="31691-131">For example, the following query sorts the results based on the `Name` property.</span></span> <span data-ttu-id="31691-132">`Name` Bir dize olduğundan, döndürülen veriler a'dan Z'ye alfabetik olarak sıralanır.</span><span class="sxs-lookup"><span data-stu-id="31691-132">Because `Name` is a string, the returned data will be sorted alphabetically, from A to Z.</span></span>  
  
 [!code-vb[VbLINQBasicOps#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#3)]  
  
 <span data-ttu-id="31691-133">Sonuçları z'den A'ya ters sırayla `Order By...Descending` sıralamak için yan tümceyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="31691-133">To order the results in reverse order, from Z to A, use the `Order By...Descending` clause.</span></span> <span data-ttu-id="31691-134">Varsayılan değer, `Ascending` `Ascending` ne `Descending` belirtilmiş ne de belirtilir.</span><span class="sxs-lookup"><span data-stu-id="31691-134">The default is `Ascending` when neither `Ascending` nor `Descending` is specified.</span></span>  
  
 <span data-ttu-id="31691-135">Visual Basic'teki yan `Order By` tümcenin nasıl kullanılacağı hakkında daha fazla bilgi için [bkz.](../../../../visual-basic/language-reference/queries/order-by-clause.md)</span><span class="sxs-lookup"><span data-stu-id="31691-135">For more information about how to use the `Order By` clause in Visual Basic, see [Order By Clause](../../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
## <a name="selecting-data-select"></a><span data-ttu-id="31691-136">Verileri Seçme (Seçim)</span><span class="sxs-lookup"><span data-stu-id="31691-136">Selecting Data (Select)</span></span>  
 <span data-ttu-id="31691-137">Yan `Select` tümce, döndürülen öğelerin biçimini ve içeriğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="31691-137">The `Select` clause specifies the form and content of returned elements.</span></span> <span data-ttu-id="31691-138">Örneğin, sonuçlarınızın tam `Customer` nesnelerden mi, yalnızca bir `Customer` özellikten, bir özellik alt kümesinden, çeşitli veri kaynaklarından özelliklerin birleşiminden mi yoksa bir hesaplamaya dayalı yeni bir sonuç türünden mi oluşacağını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31691-138">For example, you can specify whether your results will consist of complete `Customer` objects, just one `Customer` property, a subset of properties, a combination of properties from various data sources, or some new result type based on a computation.</span></span> <span data-ttu-id="31691-139">`Select` Yan tümce kaynak öğenin bir kopyası ndan başka bir şey ürettiğinde, işlem *projeksiyon*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="31691-139">When the `Select` clause produces something other than a copy of the source element, the operation is called a *projection*.</span></span>  
  
 <span data-ttu-id="31691-140">Tam `Customer` nesnelerden oluşan bir koleksiyon almak için aralık değişkeninin kendisini seçin:</span><span class="sxs-lookup"><span data-stu-id="31691-140">To retrieve a collection that consists of complete `Customer` objects, select the range variable itself:</span></span>  
  
 [!code-vb[VbLINQBasicOps#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#4)]  
  
 <span data-ttu-id="31691-141">Bir `Customer` örnek çok alanı olan büyük bir nesneyse ve almak istediğiniz tek şey `cust.Name`adsa, aşağıdaki örnekte gösterildiği gibi, bunu seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31691-141">If a `Customer` instance is a large object that has many fields, and all that you want to retrieve is the name, you can select `cust.Name`, as shown in the following example.</span></span> <span data-ttu-id="31691-142">Yerel tür çıkarım, bu nesnelerin bir koleksiyondan `Customer` dizeleri bir koleksiyon için sonuç türünü değiştirir tanır.</span><span class="sxs-lookup"><span data-stu-id="31691-142">Local type inference recognizes that this changes the result type from a collection of `Customer` objects to a collection of strings.</span></span>  
  
 [!code-vb[VbLINQBasicOps#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#5)]  
  
 <span data-ttu-id="31691-143">Veri kaynağından birden çok alan seçmek için iki seçeneğiniz vardır:</span><span class="sxs-lookup"><span data-stu-id="31691-143">To select multiple fields from the data source, you have two choices:</span></span>  
  
- <span data-ttu-id="31691-144">Yan `Select` tümcede, sonuca eklemek istediğiniz alanları belirtin.</span><span class="sxs-lookup"><span data-stu-id="31691-144">In the `Select` clause, specify the fields you want to include in the result.</span></span> <span data-ttu-id="31691-145">Derleyici, özellikleri bu alanları içeren anonim bir tür tanımlar.</span><span class="sxs-lookup"><span data-stu-id="31691-145">The compiler will define an anonymous type that has those fields as its properties.</span></span> <span data-ttu-id="31691-146">Daha fazla bilgi için [Bkz. Anonim Türler.](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)</span><span class="sxs-lookup"><span data-stu-id="31691-146">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
     <span data-ttu-id="31691-147">Aşağıdaki örnekte döndürülen öğeler anonim tür örnekleri olduğundan, kodunuzun başka bir yerinde ada göre türüne başvuramazsınız.</span><span class="sxs-lookup"><span data-stu-id="31691-147">Because the returned elements in the following example are instances of an anonymous type, you cannot refer to the type by name elsewhere in your code.</span></span> <span data-ttu-id="31691-148">Tür için derleyici tarafından atanan ad, normal Visual Basic kodunda geçerli olmayan karakterler içerir.</span><span class="sxs-lookup"><span data-stu-id="31691-148">The compiler-designated name for the type contains characters that are not valid in normal Visual Basic code.</span></span> <span data-ttu-id="31691-149">Aşağıdaki örnekte, koleksiyondaki sorgu tarafından döndürülen öğeler `londonCusts4` anonim türörnekleridir</span><span class="sxs-lookup"><span data-stu-id="31691-149">In the following example, the elements in the collection that is returned by the query in `londonCusts4` are instances of an anonymous type</span></span>  
  
     [!code-vb[VbLINQBasicOps#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#6)]  
  
     <span data-ttu-id="31691-150">-veya-</span><span class="sxs-lookup"><span data-stu-id="31691-150">-or-</span></span>  
  
- <span data-ttu-id="31691-151">Sonuca eklemek istediğiniz belirli alanları içeren adlandırılmış bir tür tanımlayın ve yan tümcedeki `Select` tür örnekleri oluşturun ve başharfe alın.</span><span class="sxs-lookup"><span data-stu-id="31691-151">Define a named type that contains the particular fields that you want to include in the result, and create and initialize instances of the type in the `Select` clause.</span></span> <span data-ttu-id="31691-152">Bu seçeneği yalnızca iade edildikleri koleksiyon dışında tek tek sonuçlar kullanmanız gerekiyorsa veya bunları yöntem çağrılarında parametre olarak geçirmeniz gerekiyorsa kullanın.</span><span class="sxs-lookup"><span data-stu-id="31691-152">Use this option only if you have to use individual results outside the collection in which they are returned, or if you have to pass them as parameters in method calls.</span></span> <span data-ttu-id="31691-153">Aşağıdaki `londonCusts5` örnekte türü IEnumerable (NamePhone of) olduğunu.</span><span class="sxs-lookup"><span data-stu-id="31691-153">The type of `londonCusts5` in the following example is IEnumerable(Of NamePhone).</span></span>  
  
     [!code-vb[VbLINQBasicOps#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#7)]  
  
     [!code-vb[VbLINQBasicOps#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#8)]  
  
 <span data-ttu-id="31691-154">Visual Basic'te yan `Select` tümcenin nasıl kullanılacağı hakkında daha fazla bilgi için [bkz.](../../../../visual-basic/language-reference/queries/select-clause.md)</span><span class="sxs-lookup"><span data-stu-id="31691-154">For more information about how to use the `Select` clause in Visual Basic, see [Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md).</span></span>  
  
## <a name="joining-data-join-and-group-join"></a><span data-ttu-id="31691-155">Veri Katma (Katma ve Grup Katma)</span><span class="sxs-lookup"><span data-stu-id="31691-155">Joining Data (Join and Group Join)</span></span>  
 <span data-ttu-id="31691-156">`From` Yan tümcede birden fazla veri kaynağını çeşitli şekillerde birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31691-156">You can combine more than one data source in the `From` clause in several ways.</span></span> <span data-ttu-id="31691-157">Örneğin, aşağıdaki kod iki veri kaynağı kullanır ve dolaylı olarak sonuç her ikisinin özellikleri birleştirir.</span><span class="sxs-lookup"><span data-stu-id="31691-157">For example, the following code uses two data sources and implicitly combines properties from both of them in the result.</span></span> <span data-ttu-id="31691-158">Sorgu, soyadı sesli harfle başlayan öğrencileri seçer.</span><span class="sxs-lookup"><span data-stu-id="31691-158">The query selects students whose last names start with a vowel.</span></span>  
  
 [!code-vb[VbLINQBasicOps#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#9)]  
  
> [!NOTE]
> <span data-ttu-id="31691-159">Bu [kodu, Nasıl Oluşturulur: Öğeler Listesi Oluşturma'da](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)oluşturulan öğrencilerin listesiyle çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31691-159">You can run this code with the list of students created in [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md).</span></span>  
  
 <span data-ttu-id="31691-160">Anahtar `Join` kelime SQL'deki `INNER JOIN` bir kelimeye eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="31691-160">The `Join` keyword is equivalent to an `INNER JOIN` in SQL.</span></span> <span data-ttu-id="31691-161">İki koleksiyondaki öğeler arasında eşleşen anahtar değerleri temel alan iki koleksiyonu birleştirir.</span><span class="sxs-lookup"><span data-stu-id="31691-161">It combines two collections based on matching key values between elements in the two collections.</span></span> <span data-ttu-id="31691-162">Sorgu, anahtar değerleri eşleşen toplama öğelerinin tümününveya bir kısmını döndürür.</span><span class="sxs-lookup"><span data-stu-id="31691-162">The query returns all or part of the collection elements that have matching key values.</span></span> <span data-ttu-id="31691-163">Örneğin, aşağıdaki kod önceki örtük birleştirme eylemini yineler.</span><span class="sxs-lookup"><span data-stu-id="31691-163">For example, the following code duplicates the action of the previous implicit join.</span></span>  
  
 [!code-vb[VbLINQBasicOps#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#10)]  
  
 <span data-ttu-id="31691-164">`Group Join`koleksiyonları SQL'deki gibi `LEFT JOIN` tek bir hiyerarşik koleksiyonda birleştirir.</span><span class="sxs-lookup"><span data-stu-id="31691-164">`Group Join` combines collections into a single hierarchical collection, just like a `LEFT JOIN` in SQL.</span></span> <span data-ttu-id="31691-165">Daha fazla bilgi için [Group Join Clause](../../../../visual-basic/language-reference/queries/group-join-clause.md) [bkz.](../../../../visual-basic/language-reference/queries/join-clause.md)</span><span class="sxs-lookup"><span data-stu-id="31691-165">For more information, see [Join Clause](../../../../visual-basic/language-reference/queries/join-clause.md) and [Group Join Clause](../../../../visual-basic/language-reference/queries/group-join-clause.md).</span></span>  
  
## <a name="grouping-data-group-by"></a><span data-ttu-id="31691-166">Verileri Gruplandırma (Gruplandırma Ölçütü)</span><span class="sxs-lookup"><span data-stu-id="31691-166">Grouping Data (Group By)</span></span>  
 <span data-ttu-id="31691-167">Sorgu sonucundaki `Group By` öğeleri öğelerin bir veya daha fazla alanına göre gruplandırmak için bir yan tümce ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31691-167">You can add a `Group By` clause to group the elements in a query result according to one or more fields of the elements.</span></span> <span data-ttu-id="31691-168">Örneğin, aşağıdaki kod öğrencileri sınıf yılına göre gruplanır.</span><span class="sxs-lookup"><span data-stu-id="31691-168">For example, the following code groups students by class year.</span></span>  
  
 [!code-vb[VbLINQBasicOps#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#11)]  
  
 <span data-ttu-id="31691-169">Bu kodu [nasıl oluşturulur: Öğeler Listesi oluşturma'](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)da oluşturulan öğrencilerin listesini kullanarak `For Each` çalıştırın, deyimden çıktı:</span><span class="sxs-lookup"><span data-stu-id="31691-169">If you run this code using the list of students created in [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md), the output from the `For Each` statement is:</span></span>  
  
 <span data-ttu-id="31691-170">Yıl: Junior</span><span class="sxs-lookup"><span data-stu-id="31691-170">Year: Junior</span></span>  
  
 <span data-ttu-id="31691-171">Tucker, Michael</span><span class="sxs-lookup"><span data-stu-id="31691-171">Tucker, Michael</span></span>  
  
 <span data-ttu-id="31691-172">Garcia, Hugo</span><span class="sxs-lookup"><span data-stu-id="31691-172">Garcia, Hugo</span></span>  
  
 <span data-ttu-id="31691-173">Garcia, Debra</span><span class="sxs-lookup"><span data-stu-id="31691-173">Garcia, Debra</span></span>  
  
 <span data-ttu-id="31691-174">Tucker, Lance</span><span class="sxs-lookup"><span data-stu-id="31691-174">Tucker, Lance</span></span>  
  
 <span data-ttu-id="31691-175">Yıl: Kıdemli</span><span class="sxs-lookup"><span data-stu-id="31691-175">Year: Senior</span></span>  
  
 <span data-ttu-id="31691-176">Omelchenko, Svetlana</span><span class="sxs-lookup"><span data-stu-id="31691-176">Omelchenko, Svetlana</span></span>  
  
 <span data-ttu-id="31691-177">Osada, Michiko</span><span class="sxs-lookup"><span data-stu-id="31691-177">Osada, Michiko</span></span>  
  
 <span data-ttu-id="31691-178">Fakhouri, Fadi</span><span class="sxs-lookup"><span data-stu-id="31691-178">Fakhouri, Fadi</span></span>  
  
 <span data-ttu-id="31691-179">Feng, Hanying</span><span class="sxs-lookup"><span data-stu-id="31691-179">Feng, Hanying</span></span>  
  
 <span data-ttu-id="31691-180">Adams, Terry</span><span class="sxs-lookup"><span data-stu-id="31691-180">Adams, Terry</span></span>  
  
 <span data-ttu-id="31691-181">Yıl: Birinci Sınıf</span><span class="sxs-lookup"><span data-stu-id="31691-181">Year: Freshman</span></span>  
  
 <span data-ttu-id="31691-182">Mortensen, Sven</span><span class="sxs-lookup"><span data-stu-id="31691-182">Mortensen, Sven</span></span>  
  
 <span data-ttu-id="31691-183">Garcia, Cesar</span><span class="sxs-lookup"><span data-stu-id="31691-183">Garcia, Cesar</span></span>  
  
 <span data-ttu-id="31691-184">Aşağıdaki kodda gösterilen varyasyon sınıf yıllarını emreder ve her yıl içinde öğrencilere soyadını verir.</span><span class="sxs-lookup"><span data-stu-id="31691-184">The variation shown in the following code orders the class years, and then orders the students within each year by last name.</span></span>  
  
 [!code-vb[VbLINQBasicOps#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#12)]  
  
 <span data-ttu-id="31691-185">Hakkında `Group By`daha fazla bilgi için bkz: [Grup Yan Tümcesi.](../../../../visual-basic/language-reference/queries/group-by-clause.md)</span><span class="sxs-lookup"><span data-stu-id="31691-185">For more information about `Group By`, see [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31691-186">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="31691-186">See also</span></span>

- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="31691-187">Visual Basic'te LINQ'e Başlarken</span><span class="sxs-lookup"><span data-stu-id="31691-187">Getting Started with LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [<span data-ttu-id="31691-188">Sorgular</span><span class="sxs-lookup"><span data-stu-id="31691-188">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="31691-189">Standart Sorgu Operatörlerine Genel Bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31691-189">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="31691-190">LINQ</span><span class="sxs-lookup"><span data-stu-id="31691-190">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
