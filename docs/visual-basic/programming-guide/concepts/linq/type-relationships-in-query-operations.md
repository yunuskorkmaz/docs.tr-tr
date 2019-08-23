---
title: LINQ Sorgu İşlemlerinde Tür İlişkileri (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- variable relationships [LINQ in Visual Basic]
- type information inferred [LINQ in Visual Basic]
- type relationships [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], type relationships
- data sources [LINQ in Visual Basic], type relationships
- LINQ [Visual Basic], type relationships
- inferring type information [LINQ in Visual Basic]
- relationships [LINQ in Visual Basic]
ms.assetid: b5ff4da5-f3fd-4a8e-aaac-1cbf52fa16f6
ms.openlocfilehash: 4851d0a74de38f0fb6b6deee34cf7b3e66eb11b4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937487"
---
# <a name="type-relationships-in-query-operations-visual-basic"></a><span data-ttu-id="0cd9c-102">LINQ Sorgu İşlemlerinde Tür İlişkileri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0cd9c-102">Type Relationships in Query Operations (Visual Basic)</span></span>
<span data-ttu-id="0cd9c-103">[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] Sorgu işlemlerinde kullanılan değişkenler kesin olarak türdedir ve birbirleriyle uyumlu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0cd9c-103">Variables used in [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] query operations are strongly typed and must be compatible with each other.</span></span> <span data-ttu-id="0cd9c-104">Güçlü yazma, veri kaynağında, sorgunun kendisinde ve sorgu yürütmesinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0cd9c-104">Strong typing is used in the data source, in the query itself, and in the query execution.</span></span> <span data-ttu-id="0cd9c-105">Aşağıdaki çizimde bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorguyu tanımlamak için kullanılan terimler tanımlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0cd9c-105">The following illustration identifies terms used to describe a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query.</span></span> <span data-ttu-id="0cd9c-106">Bir sorgunun kısımları hakkında daha fazla bilgi için bkz. [temel sorgu işlemleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="0cd9c-106">For more information about the parts of a query, see [Basic Query Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).</span></span>  
  
 ![Öğeleri vurgulanmış bir sözde kod sorgusunu gösteren ekran görüntüsü.](./media/type-relationships-in-query-operations/linq-query-description-terms.png)  
  
 <span data-ttu-id="0cd9c-108">Sorgudaki aralık değişkeninin türü, veri kaynağındaki öğelerin türüyle uyumlu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0cd9c-108">The type of the range variable in the query must be compatible with the type of the elements in the data source.</span></span> <span data-ttu-id="0cd9c-109">Sorgu değişkeninin türü, `Select` yan tümcesinde tanımlanan dizi öğesiyle uyumlu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0cd9c-109">The type of the query variable must be compatible with the sequence element defined in the `Select` clause.</span></span> <span data-ttu-id="0cd9c-110">Son olarak, dizi öğelerinin türü sorguyu yürüten `For Each` ifadede kullanılan döngü denetimi değişkeninin türüyle uyumlu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0cd9c-110">Finally, the type of the sequence elements also must be compatible with the type of the loop control variable that is used in the `For Each` statement that executes the query.</span></span> <span data-ttu-id="0cd9c-111">Bu güçlü yazma, derleme zamanında tür hatalarının tanımlanmasını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="0cd9c-111">This strong typing facilitates identification of type errors at compile time.</span></span>  
  
 <span data-ttu-id="0cd9c-112">Visual Basic, *örtülü yazma*olarak da bilinen yerel tür çıkarımı uygulayarak güçlü yazma kullanışlı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="0cd9c-112">Visual Basic makes strong typing convenient by implementing local type inference, also known as *implicit typing*.</span></span> <span data-ttu-id="0cd9c-113">Bu özellik, önceki örnekte kullanılır ve bu özellik, [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] örnek ve belgeler genelinde kullanıldığını görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="0cd9c-113">That feature is used in the previous example, and you will see it used throughout the [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] samples and documentation.</span></span> <span data-ttu-id="0cd9c-114">Visual Basic, yerel tür çıkarımı yalnızca `Dim` `As` yan tümce olmadan bir deyimi kullanılarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="0cd9c-114">In Visual Basic, local type inference is accomplished simply by using a `Dim` statement without an `As` clause.</span></span> <span data-ttu-id="0cd9c-115">Aşağıdaki örnekte, `city` kesin bir dize olarak türdedir.</span><span class="sxs-lookup"><span data-stu-id="0cd9c-115">In the following example, `city` is strongly typed as a string.</span></span>  
  
 [!code-vb[VbLINQTypeRels#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#1)]  
  
> [!NOTE]
> <span data-ttu-id="0cd9c-116">Yerel tür çıkarımı yalnızca `Option Infer` olarak `On`ayarlandığında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0cd9c-116">Local type inference works only when `Option Infer` is set to `On`.</span></span> <span data-ttu-id="0cd9c-117">Daha fazla bilgi için bkz. [Option Infer deyimleri](../../../../visual-basic/language-reference/statements/option-infer-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0cd9c-117">For more information, see [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md).</span></span>  
  
 <span data-ttu-id="0cd9c-118">Ancak, bir sorguda yerel tür çıkarımı kullanıyor olsanız bile, veri kaynağı, sorgu değişkeni ve sorgu yürütme döngüsünde değişkenler arasında aynı tür ilişkileri vardır.</span><span class="sxs-lookup"><span data-stu-id="0cd9c-118">However, even if you use local type inference in a query, the same type relationships are present among the variables in the data source, the query variable, and the query execution loop.</span></span> <span data-ttu-id="0cd9c-119">Sorgu yazarken [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] veya belgelerde örnek ve kod örnekleriyle çalışırken, bu tür ilişkilerden temel olarak anlaşılmak yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="0cd9c-119">It is useful to have a basic understanding of these type relationships when you are writing [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries, or working with the samples and code examples in the documentation.</span></span>  
  
 <span data-ttu-id="0cd9c-120">Veri kaynağından döndürülen türle eşleşmeyen bir Aralık değişkeni için açık bir tür belirtmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="0cd9c-120">You may need to specify an explicit type for a range variable that does not match the type returned from the data source.</span></span> <span data-ttu-id="0cd9c-121">Bir `As` yan tümce kullanarak Aralık değişkeninin türünü belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0cd9c-121">You can specify the type of the range variable by using an `As` clause.</span></span> <span data-ttu-id="0cd9c-122">Ancak, dönüştürme bir [daraltma dönüştürmesi](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) ise ve `Option Strict` olarak `On`ayarlanmışsa bu hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="0cd9c-122">However, this results in an error if the conversion is a [narrowing conversion](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and `Option Strict` is set to `On`.</span></span> <span data-ttu-id="0cd9c-123">Bu nedenle, dönüştürmeyi veri kaynağından alınan değerlerle gerçekleştirmenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="0cd9c-123">Therefore, we recommend that you perform the conversion on the values retrieved from the data source.</span></span> <span data-ttu-id="0cd9c-124"><xref:System.Linq.Enumerable.Cast%2A> Yöntemini kullanarak veri kaynağındaki değerleri açık Aralık değişkeni türüne dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0cd9c-124">You can convert the values from the data source to the explicit range variable type by using the <xref:System.Linq.Enumerable.Cast%2A> method.</span></span> <span data-ttu-id="0cd9c-125">`Select` Yan tümcesindeki seçili değerleri, Aralık değişkeninin türünden farklı bir açık türe de çevirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0cd9c-125">You can also cast the values selected in the `Select` clause to an explicit type that is different from the type of the range variable.</span></span> <span data-ttu-id="0cd9c-126">Bu noktaları aşağıdaki kodda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0cd9c-126">These points are illustrated in the following code.</span></span>  
  
 [!code-vb[VbLINQTypeRels#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#4)]  
  
## <a name="queries-that-return-entire-elements-of-the-source-data"></a><span data-ttu-id="0cd9c-127">Kaynak verilerin tüm öğelerini döndüren sorgular</span><span class="sxs-lookup"><span data-stu-id="0cd9c-127">Queries That Return Entire Elements of the Source Data</span></span>  
 <span data-ttu-id="0cd9c-128">Aşağıdaki örnek, kaynak verilerden [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] seçilen öğelerin dizisini döndüren bir sorgu işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0cd9c-128">The following example shows a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query operation that returns a sequence of elements selected from the source data.</span></span> <span data-ttu-id="0cd9c-129">Kaynak, `names`bir dize dizisi içerir ve sorgu çıktısı, ı harfiyle başlayan dizeleri içeren bir dizidir.</span><span class="sxs-lookup"><span data-stu-id="0cd9c-129">The source, `names`, contains an array of strings, and the query output is a sequence containing strings that start with the letter M.</span></span>  
  
 [!code-vb[VbLINQTypeRels#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#2)]  
  
 <span data-ttu-id="0cd9c-130">Bu, aşağıdaki koda eşdeğerdir, ancak yazılması çok daha kısadır ve kolaydır.</span><span class="sxs-lookup"><span data-stu-id="0cd9c-130">This is equivalent to the following code, but is much shorter and easier to write.</span></span> <span data-ttu-id="0cd9c-131">Sorgularda yerel tür çıkarımı, Visual Basic içinde tercih edilen stildir.</span><span class="sxs-lookup"><span data-stu-id="0cd9c-131">Reliance on local type inference in queries is the preferred style in Visual Basic.</span></span>  
  
 [!code-vb[VbLINQTypeRels#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#3)]  
  
 <span data-ttu-id="0cd9c-132">Aşağıdaki ilişkiler, türlerin örtük olarak mı yoksa açık olarak mı belirlendiği, önceki kod örneklerinde her ikisinde de mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="0cd9c-132">The following relationships exist in both of the previous code examples, whether the types are determined implicitly or explicitly.</span></span>  
  
1. <span data-ttu-id="0cd9c-133">Veri kaynağındaki `names`öğelerin türü, sorgusunda,,,, Aralık `name`değişkeninin türüdür.</span><span class="sxs-lookup"><span data-stu-id="0cd9c-133">The type of the elements in the data source, `names`, is the type of the range variable, `name`, in the query.</span></span>  
  
2. <span data-ttu-id="0cd9c-134">Seçilen `name`nesnenin türü, sorgu `mNames`değişkeninin türünü belirler.</span><span class="sxs-lookup"><span data-stu-id="0cd9c-134">The type of the object that is selected, `name`, determines the type of the query variable, `mNames`.</span></span> <span data-ttu-id="0cd9c-135">Burada `name` bir dize olduğundan sorgu değişkeni Visual Basic IEnumerable (dize) olur.</span><span class="sxs-lookup"><span data-stu-id="0cd9c-135">Here `name` is a string, so the query variable is IEnumerable(Of String) in Visual Basic.</span></span>  
  
3. <span data-ttu-id="0cd9c-136">İçinde `mNames` tanımlanan sorgu, `For Each` döngüsünde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="0cd9c-136">The query defined in `mNames` is executed in the `For Each` loop.</span></span> <span data-ttu-id="0cd9c-137">Döngü, sorguyu yürütmenin sonucunu yineler.</span><span class="sxs-lookup"><span data-stu-id="0cd9c-137">The loop iterates over the result of executing the query.</span></span> <span data-ttu-id="0cd9c-138">Yürütüldüğünde, bir dize dizisi döndürür, Loop yineleme `nm`değişkeni de bir dizedir. `mNames`</span><span class="sxs-lookup"><span data-stu-id="0cd9c-138">Because `mNames`, when it is executed, will return a sequence of strings, the loop iteration variable, `nm`, also is a string.</span></span>  
  
## <a name="queries-that-return-one-field-from-selected-elements"></a><span data-ttu-id="0cd9c-139">Seçili öğelerden bir alan döndüren sorgular</span><span class="sxs-lookup"><span data-stu-id="0cd9c-139">Queries That Return One Field from Selected Elements</span></span>  
 <span data-ttu-id="0cd9c-140">Aşağıdaki örnek, veri kaynağından [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] seçilen her bir öğenin yalnızca bir kısmını içeren bir dizi döndüren bir sorgu işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0cd9c-140">The following example shows a [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] query operation that returns a sequence containing only one part of each element selected from the data source.</span></span> <span data-ttu-id="0cd9c-141">Sorgu, veri kaynağı olarak `Customer` nesneler koleksiyonunu ve `Name` yalnızca sonuç içindeki özelliği kullanır.</span><span class="sxs-lookup"><span data-stu-id="0cd9c-141">The query takes a collection of `Customer` objects as its data source and projects only the `Name` property in the result.</span></span> <span data-ttu-id="0cd9c-142">Müşteri adı bir dize olduğundan, sorgu çıktı olarak bir dizi dize üretir.</span><span class="sxs-lookup"><span data-stu-id="0cd9c-142">Because the customer name is a string, the query produces a sequence of strings as output.</span></span>  
  
```vb  
' Method GetTable returns a table of Customer objects.  
Dim customers = db.GetTable(Of Customer)()  
Dim custNames = From cust In customers   
                Where cust.City = "London"   
                Select cust.Name  
  
For Each custName In custNames  
    Console.WriteLine(custName)  
Next  
```  
  
 <span data-ttu-id="0cd9c-143">Değişkenler arasındaki ilişkiler, daha basit örnekteki gibi bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="0cd9c-143">The relationships between variables are like those in the simpler example.</span></span>  
  
1. <span data-ttu-id="0cd9c-144">Veri kaynağındaki `customers`öğelerin türü, sorgusunda,,,, Aralık `cust`değişkeninin türüdür.</span><span class="sxs-lookup"><span data-stu-id="0cd9c-144">The type of the elements in the data source, `customers`, is the type of the range variable, `cust`, in the query.</span></span> <span data-ttu-id="0cd9c-145">Bu örnekte, bu tür olur `Customer`.</span><span class="sxs-lookup"><span data-stu-id="0cd9c-145">In this example, that type is `Customer`.</span></span>  
  
2. <span data-ttu-id="0cd9c-146">İfade, tüm nesne `Name` yerine her `Customer` nesnenin özelliğini döndürür. `Select`</span><span class="sxs-lookup"><span data-stu-id="0cd9c-146">The `Select` statement returns the `Name` property of each `Customer` object instead of the whole object.</span></span> <span data-ttu-id="0cd9c-147">Bir dize olduğundan, sorgu `custNames`değişkeni yeniden IEnumerable ( `Customer`dize) olacaktır, değil. `Name`</span><span class="sxs-lookup"><span data-stu-id="0cd9c-147">Because `Name` is a string, the query variable, `custNames`, will again be IEnumerable(Of String), not of `Customer`.</span></span>  
  
3. <span data-ttu-id="0cd9c-148">, Bir dizi dizeyi `custName` `For Each` `custNames` temsil ettiğinden, döngünün yineleme değişkeni, bir dize olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0cd9c-148">Because `custNames` represents a sequence of strings, the `For Each` loop's iteration variable, `custName`, must be a string.</span></span>  
  
 <span data-ttu-id="0cd9c-149">Yerel tür çıkarımı olmadan, aşağıdaki örnekte gösterildiği gibi önceki örnek yazmak ve anlamak için daha fazla kullanışsız olacaktır.</span><span class="sxs-lookup"><span data-stu-id="0cd9c-149">Without local type inference, the previous example would be more cumbersome to write and to understand, as the following example shows.</span></span>  
  
```vb  
' Method GetTable returns a table of Customer objects.  
 Dim customers As Table(Of Customer) = db.GetTable(Of Customer)()  
 Dim custNames As IEnumerable(Of String) =  
     From cust As Customer In customers   
     Where cust.City = "London"   
     Select cust.Name  
  
 For Each custName As String In custNames  
     Console.WriteLine(custName)  
 Next  
```  
  
## <a name="queries-that-require-anonymous-types"></a><span data-ttu-id="0cd9c-150">Anonim türler gerektiren sorgular</span><span class="sxs-lookup"><span data-stu-id="0cd9c-150">Queries That Require Anonymous Types</span></span>  
 <span data-ttu-id="0cd9c-151">Aşağıdaki örnekte daha karmaşık bir durum gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0cd9c-151">The following example shows a more complex situation.</span></span> <span data-ttu-id="0cd9c-152">Önceki örnekte, tüm değişkenler için türleri açıkça belirtmek uygun değildi.</span><span class="sxs-lookup"><span data-stu-id="0cd9c-152">In the previous example, it was inconvenient to specify types for all the variables explicitly.</span></span> <span data-ttu-id="0cd9c-153">Bu örnekte, olanaksızdır.</span><span class="sxs-lookup"><span data-stu-id="0cd9c-153">In this example, it is impossible.</span></span> <span data-ttu-id="0cd9c-154">Tüm `Customer` öğeleri veri kaynağından veya her öğeden tek bir alandan seçmek yerine `Select` , bu sorgudaki yan tümce özgün `Customer` nesnenin iki özelliğini döndürür: `Name` ve `City`.</span><span class="sxs-lookup"><span data-stu-id="0cd9c-154">Instead of selecting entire `Customer` elements from the data source, or a single field from each element, the `Select` clause in this query returns two properties of the original `Customer` object: `Name` and `City`.</span></span> <span data-ttu-id="0cd9c-155">`Select` Yan tümcesine yanıt olarak, derleyici bu iki özelliği içeren anonim bir tür tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0cd9c-155">In response to the `Select` clause, the compiler defines an anonymous type that contains those two properties.</span></span> <span data-ttu-id="0cd9c-156">Döngüde`For Each` yürütmenin `nameCityQuery` sonucu, yeni anonim türün örneklerinin bir koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="0cd9c-156">The result of executing `nameCityQuery` in the `For Each` loop is a collection of instances of the new anonymous type.</span></span> <span data-ttu-id="0cd9c-157">Anonim türün kullanılabilir bir `nameCityQuery` adı olmadığından, türü veya `custInfo` açıkça belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="0cd9c-157">Because the anonymous type has no usable name, you cannot specify the type of `nameCityQuery` or `custInfo` explicitly.</span></span> <span data-ttu-id="0cd9c-158">Diğer bir deyişle, bir anonim tür ile, ' `String` de `IEnumerable(Of String)`' ın yerine kullanılacak tür adı yoktur.</span><span class="sxs-lookup"><span data-stu-id="0cd9c-158">That is, with an anonymous type, you have no type name to use in place of `String` in `IEnumerable(Of String)`.</span></span> <span data-ttu-id="0cd9c-159">Daha fazla bilgi için bkz. [anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="0cd9c-159">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
```vb  
' Method GetTable returns a table of Customer objects.  
Dim customers = db.GetTable(Of Customer)()  
Dim nameCityQuery = From cust In customers   
                    Where cust.City = "London"   
                    Select cust.Name, cust.City  
  
For Each custInfo In nameCityQuery  
    Console.WriteLine(custInfo.Name)  
Next  
```  
  
 <span data-ttu-id="0cd9c-160">Önceki örnekteki tüm değişkenlerin türlerini belirtmek mümkün olmasa da ilişkiler aynı kalır.</span><span class="sxs-lookup"><span data-stu-id="0cd9c-160">Although it is not possible to specify types for all the variables in the previous example, the relationships remain the same.</span></span>  
  
1. <span data-ttu-id="0cd9c-161">Veri kaynağındaki öğelerin türü, sorgudaki aralık değişkeninin türüdür.</span><span class="sxs-lookup"><span data-stu-id="0cd9c-161">The type of the elements in the data source is again the type of the range variable in the query.</span></span> <span data-ttu-id="0cd9c-162">Bu örnekte, `cust` bir `Customer`örneğidir.</span><span class="sxs-lookup"><span data-stu-id="0cd9c-162">In this example, `cust` is an instance of `Customer`.</span></span>  
  
2. <span data-ttu-id="0cd9c-163">İfade anonim bir tür oluşturduğundan, sorgu `nameCityQuery`değişkeni örtülü olarak anonim bir tür olarak yazılmalıdır. `Select`</span><span class="sxs-lookup"><span data-stu-id="0cd9c-163">Because the `Select` statement produces an anonymous type, the query variable, `nameCityQuery`, must be implicitly typed as an anonymous type.</span></span> <span data-ttu-id="0cd9c-164">Anonim bir türün kullanılabilir adı yok ve bu nedenle açıkça belirtilemez.</span><span class="sxs-lookup"><span data-stu-id="0cd9c-164">An anonymous type has no usable name, and therefore cannot be specified explicitly.</span></span>  
  
3. <span data-ttu-id="0cd9c-165">`For Each` Döngüdeki yineleme değişkeninin türü 2. adımda oluşturulan anonim türüdür.</span><span class="sxs-lookup"><span data-stu-id="0cd9c-165">The type of the iteration variable in the `For Each` loop is the anonymous type created in step 2.</span></span> <span data-ttu-id="0cd9c-166">Türün kullanılabilir bir adı olmadığından, döngü yineleme değişkeninin türü örtük olarak belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="0cd9c-166">Because the type has no usable name, the type of the loop iteration variable must be determined implicitly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cd9c-167">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0cd9c-167">See also</span></span>

- [<span data-ttu-id="0cd9c-168">Visual Basic LINQ ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="0cd9c-168">Getting Started with LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [<span data-ttu-id="0cd9c-169">Anonim Tipler</span><span class="sxs-lookup"><span data-stu-id="0cd9c-169">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="0cd9c-170">Yerel Çıkarım</span><span class="sxs-lookup"><span data-stu-id="0cd9c-170">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="0cd9c-171">Visual Basic LINQ 'e giriş</span><span class="sxs-lookup"><span data-stu-id="0cd9c-171">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="0cd9c-172">LINQ</span><span class="sxs-lookup"><span data-stu-id="0cd9c-172">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="0cd9c-173">Sorgular</span><span class="sxs-lookup"><span data-stu-id="0cd9c-173">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
