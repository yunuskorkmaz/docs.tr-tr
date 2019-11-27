---
title: Sorgu İşlemlerinde Tür İlişkileri
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
ms.openlocfilehash: 8c201abef924766d52b1adb084970a24ebea2b50
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350560"
---
# <a name="type-relationships-in-query-operations-visual-basic"></a><span data-ttu-id="d4df3-102">LINQ Sorgu İşlemlerinde Tür İlişkileri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d4df3-102">Type Relationships in Query Operations (Visual Basic)</span></span>

<span data-ttu-id="d4df3-103">[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] sorgu işlemlerinde kullanılan değişkenler kesin olarak türdedir ve birbirleriyle uyumlu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d4df3-103">Variables used in [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] query operations are strongly typed and must be compatible with each other.</span></span> <span data-ttu-id="d4df3-104">Güçlü yazma, veri kaynağında, sorgunun kendisinde ve sorgu yürütmesinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d4df3-104">Strong typing is used in the data source, in the query itself, and in the query execution.</span></span> <span data-ttu-id="d4df3-105">Aşağıdaki çizimde, bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgusunu tanımlamak için kullanılan terimler tanımlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d4df3-105">The following illustration identifies terms used to describe a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query.</span></span> <span data-ttu-id="d4df3-106">Bir sorgunun kısımları hakkında daha fazla bilgi için bkz. [temel sorgu işlemleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="d4df3-106">For more information about the parts of a query, see [Basic Query Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).</span></span>

![Öğeleri vurgulanmış bir sözde kod sorgusunu gösteren ekran görüntüsü.](./media/type-relationships-in-query-operations/linq-query-description-terms.png)

<span data-ttu-id="d4df3-108">Sorgudaki aralık değişkeninin türü, veri kaynağındaki öğelerin türüyle uyumlu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d4df3-108">The type of the range variable in the query must be compatible with the type of the elements in the data source.</span></span> <span data-ttu-id="d4df3-109">Sorgu değişkeninin türü, `Select` yan tümcesinde tanımlanan dizi öğesiyle uyumlu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d4df3-109">The type of the query variable must be compatible with the sequence element defined in the `Select` clause.</span></span> <span data-ttu-id="d4df3-110">Son olarak, dizi öğelerinin türü sorguyu yürüten `For Each` bildiriminde kullanılan döngü denetimi değişkeninin türüyle uyumlu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d4df3-110">Finally, the type of the sequence elements also must be compatible with the type of the loop control variable that is used in the `For Each` statement that executes the query.</span></span> <span data-ttu-id="d4df3-111">Bu güçlü yazma, derleme zamanında tür hatalarının tanımlanmasını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="d4df3-111">This strong typing facilitates identification of type errors at compile time.</span></span>

<span data-ttu-id="d4df3-112">Visual Basic, *örtülü yazma*olarak da bilinen yerel tür çıkarımı uygulayarak güçlü yazma kullanışlı hale getirir.</span><span class="sxs-lookup"><span data-stu-id="d4df3-112">Visual Basic makes strong typing convenient by implementing local type inference, also known as *implicit typing*.</span></span> <span data-ttu-id="d4df3-113">Bu özellik önceki örnekte kullanılır ve [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] örnekleri ve belgeler boyunca bu özelliği kullanır.</span><span class="sxs-lookup"><span data-stu-id="d4df3-113">That feature is used in the previous example, and you will see it used throughout the [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] samples and documentation.</span></span> <span data-ttu-id="d4df3-114">Visual Basic, yerel tür çıkarımı yalnızca bir `As` yan tümcesi olmadan bir `Dim` deyimi kullanılarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="d4df3-114">In Visual Basic, local type inference is accomplished simply by using a `Dim` statement without an `As` clause.</span></span> <span data-ttu-id="d4df3-115">Aşağıdaki örnekte, `city` kesin bir dize olarak türdedir.</span><span class="sxs-lookup"><span data-stu-id="d4df3-115">In the following example, `city` is strongly typed as a string.</span></span>

[!code-vb[VbLINQTypeRels#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#1)]

> [!NOTE]
> <span data-ttu-id="d4df3-116">Yerel tür çıkarımı yalnızca `Option Infer` `On`olarak ayarlandığında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d4df3-116">Local type inference works only when `Option Infer` is set to `On`.</span></span> <span data-ttu-id="d4df3-117">Daha fazla bilgi için bkz. [Option Infer deyimleri](../../../../visual-basic/language-reference/statements/option-infer-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d4df3-117">For more information, see [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md).</span></span>

<span data-ttu-id="d4df3-118">Ancak, bir sorguda yerel tür çıkarımı kullanıyor olsanız bile, veri kaynağı, sorgu değişkeni ve sorgu yürütme döngüsünde değişkenler arasında aynı tür ilişkileri vardır.</span><span class="sxs-lookup"><span data-stu-id="d4df3-118">However, even if you use local type inference in a query, the same type relationships are present among the variables in the data source, the query variable, and the query execution loop.</span></span> <span data-ttu-id="d4df3-119">[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorguları yazarken veya belgelerde örnek ve kod örnekleriyle çalışırken, bu tür ilişkilerle ilgili temel bilgiye sahip olmanız yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="d4df3-119">It is useful to have a basic understanding of these type relationships when you are writing [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries, or working with the samples and code examples in the documentation.</span></span>

<span data-ttu-id="d4df3-120">Veri kaynağından döndürülen türle eşleşmeyen bir Aralık değişkeni için açık bir tür belirtmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="d4df3-120">You may need to specify an explicit type for a range variable that does not match the type returned from the data source.</span></span> <span data-ttu-id="d4df3-121">`As` yan tümcesini kullanarak Aralık değişkeninin türünü belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4df3-121">You can specify the type of the range variable by using an `As` clause.</span></span> <span data-ttu-id="d4df3-122">Ancak, dönüştürme bir [daraltma dönüştürmedir](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) ve `Option Strict` `On`olarak ayarlanırsa bu hata oluşur.</span><span class="sxs-lookup"><span data-stu-id="d4df3-122">However, this results in an error if the conversion is a [narrowing conversion](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and `Option Strict` is set to `On`.</span></span> <span data-ttu-id="d4df3-123">Bu nedenle, dönüştürmeyi veri kaynağından alınan değerlerle gerçekleştirmenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="d4df3-123">Therefore, we recommend that you perform the conversion on the values retrieved from the data source.</span></span> <span data-ttu-id="d4df3-124"><xref:System.Linq.Enumerable.Cast%2A> yöntemini kullanarak veri kaynağındaki değerleri açık Aralık değişkeni türüne dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4df3-124">You can convert the values from the data source to the explicit range variable type by using the <xref:System.Linq.Enumerable.Cast%2A> method.</span></span> <span data-ttu-id="d4df3-125">`Select` yan tümcesindeki seçili değerleri, Aralık değişkeninin türünden farklı bir açık türe de çevirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4df3-125">You can also cast the values selected in the `Select` clause to an explicit type that is different from the type of the range variable.</span></span> <span data-ttu-id="d4df3-126">Bu noktaları aşağıdaki kodda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d4df3-126">These points are illustrated in the following code.</span></span>

[!code-vb[VbLINQTypeRels#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#4)]

## <a name="queries-that-return-entire-elements-of-the-source-data"></a><span data-ttu-id="d4df3-127">Kaynak verilerin tüm öğelerini döndüren sorgular</span><span class="sxs-lookup"><span data-stu-id="d4df3-127">Queries That Return Entire Elements of the Source Data</span></span>

<span data-ttu-id="d4df3-128">Aşağıdaki örnek, kaynak verilerden seçilen bir dizi öğeyi döndüren [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] bir sorgu işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d4df3-128">The following example shows a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query operation that returns a sequence of elements selected from the source data.</span></span> <span data-ttu-id="d4df3-129">Kaynak, `names`, bir dize dizisi içerir ve sorgu çıktısı, ı harfiyle başlayan dizeleri içeren bir dizidir.</span><span class="sxs-lookup"><span data-stu-id="d4df3-129">The source, `names`, contains an array of strings, and the query output is a sequence containing strings that start with the letter M.</span></span>

[!code-vb[VbLINQTypeRels#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#2)]

<span data-ttu-id="d4df3-130">Bu, aşağıdaki koda eşdeğerdir, ancak yazılması çok daha kısadır ve kolaydır.</span><span class="sxs-lookup"><span data-stu-id="d4df3-130">This is equivalent to the following code, but is much shorter and easier to write.</span></span> <span data-ttu-id="d4df3-131">Sorgularda yerel tür çıkarımı, Visual Basic içinde tercih edilen stildir.</span><span class="sxs-lookup"><span data-stu-id="d4df3-131">Reliance on local type inference in queries is the preferred style in Visual Basic.</span></span>

[!code-vb[VbLINQTypeRels#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#3)]

<span data-ttu-id="d4df3-132">Aşağıdaki ilişkiler, türlerin örtük olarak mı yoksa açık olarak mı belirlendiği, önceki kod örneklerinde her ikisinde de mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="d4df3-132">The following relationships exist in both of the previous code examples, whether the types are determined implicitly or explicitly.</span></span>

1. <span data-ttu-id="d4df3-133">`names`veri kaynağındaki öğelerin türü, `name`Aralık değişkeninin türüdür, sorgu.</span><span class="sxs-lookup"><span data-stu-id="d4df3-133">The type of the elements in the data source, `names`, is the type of the range variable, `name`, in the query.</span></span>

2. <span data-ttu-id="d4df3-134">`name`, seçili nesnenin türü, `mNames`sorgu değişkeninin türünü belirler.</span><span class="sxs-lookup"><span data-stu-id="d4df3-134">The type of the object that is selected, `name`, determines the type of the query variable, `mNames`.</span></span> <span data-ttu-id="d4df3-135">Burada `name` bir dizedir, bu nedenle sorgu değişkeni Visual Basic IEnumerable (dize) olur.</span><span class="sxs-lookup"><span data-stu-id="d4df3-135">Here `name` is a string, so the query variable is IEnumerable(Of String) in Visual Basic.</span></span>

3. <span data-ttu-id="d4df3-136">`mNames` ' de tanımlanan sorgu `For Each` döngüsünde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="d4df3-136">The query defined in `mNames` is executed in the `For Each` loop.</span></span> <span data-ttu-id="d4df3-137">Döngü, sorguyu yürütmenin sonucunu yineler.</span><span class="sxs-lookup"><span data-stu-id="d4df3-137">The loop iterates over the result of executing the query.</span></span> <span data-ttu-id="d4df3-138">`mNames`, yürütüldüğü zaman bir dize dizisi döndürür, `nm`döngüsü yineleme değişkeni de bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="d4df3-138">Because `mNames`, when it is executed, will return a sequence of strings, the loop iteration variable, `nm`, also is a string.</span></span>

## <a name="queries-that-return-one-field-from-selected-elements"></a><span data-ttu-id="d4df3-139">Seçili öğelerden bir alan döndüren sorgular</span><span class="sxs-lookup"><span data-stu-id="d4df3-139">Queries That Return One Field from Selected Elements</span></span>

<span data-ttu-id="d4df3-140">Aşağıdaki örnek, veri kaynağından seçilen her bir öğenin yalnızca bir kısmını içeren bir dizi döndüren [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] sorgu işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d4df3-140">The following example shows a [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] query operation that returns a sequence containing only one part of each element selected from the data source.</span></span> <span data-ttu-id="d4df3-141">Sorgu, veri kaynağı olarak bir `Customer` nesneleri koleksiyonu alır ve yalnızca sonuç içindeki `Name` özelliğini projeler.</span><span class="sxs-lookup"><span data-stu-id="d4df3-141">The query takes a collection of `Customer` objects as its data source and projects only the `Name` property in the result.</span></span> <span data-ttu-id="d4df3-142">Müşteri adı bir dize olduğundan, sorgu çıktı olarak bir dizi dize üretir.</span><span class="sxs-lookup"><span data-stu-id="d4df3-142">Because the customer name is a string, the query produces a sequence of strings as output.</span></span>

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

<span data-ttu-id="d4df3-143">Değişkenler arasındaki ilişkiler, daha basit örnekteki gibi bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="d4df3-143">The relationships between variables are like those in the simpler example.</span></span>

1. <span data-ttu-id="d4df3-144">`customers`veri kaynağındaki öğelerin türü, `cust`Aralık değişkeninin türüdür, sorgu.</span><span class="sxs-lookup"><span data-stu-id="d4df3-144">The type of the elements in the data source, `customers`, is the type of the range variable, `cust`, in the query.</span></span> <span data-ttu-id="d4df3-145">Bu örnekte, bu tür `Customer`.</span><span class="sxs-lookup"><span data-stu-id="d4df3-145">In this example, that type is `Customer`.</span></span>

2. <span data-ttu-id="d4df3-146">`Select` ifade, tüm nesne yerine her bir `Customer` nesnesinin `Name` özelliğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="d4df3-146">The `Select` statement returns the `Name` property of each `Customer` object instead of the whole object.</span></span> <span data-ttu-id="d4df3-147">`Name` bir dize olduğundan, `custNames`sorgu değişkeni `Customer`değil IEnumerable (dize) olacaktır.</span><span class="sxs-lookup"><span data-stu-id="d4df3-147">Because `Name` is a string, the query variable, `custNames`, will again be IEnumerable(Of String), not of `Customer`.</span></span>

3. <span data-ttu-id="d4df3-148">`custNames` bir dizi dizeyi temsil ettiğinden, `For Each` döngüsünün yineleme değişkeni `custName`, bir dize olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d4df3-148">Because `custNames` represents a sequence of strings, the `For Each` loop's iteration variable, `custName`, must be a string.</span></span>

<span data-ttu-id="d4df3-149">Yerel tür çıkarımı olmadan, aşağıdaki örnekte gösterildiği gibi önceki örnek yazmak ve anlamak için daha fazla kullanışsız olacaktır.</span><span class="sxs-lookup"><span data-stu-id="d4df3-149">Without local type inference, the previous example would be more cumbersome to write and to understand, as the following example shows.</span></span>

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

## <a name="queries-that-require-anonymous-types"></a><span data-ttu-id="d4df3-150">Anonim türler gerektiren sorgular</span><span class="sxs-lookup"><span data-stu-id="d4df3-150">Queries That Require Anonymous Types</span></span>

<span data-ttu-id="d4df3-151">Aşağıdaki örnekte daha karmaşık bir durum gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d4df3-151">The following example shows a more complex situation.</span></span> <span data-ttu-id="d4df3-152">Önceki örnekte, tüm değişkenler için türleri açıkça belirtmek uygun değildi.</span><span class="sxs-lookup"><span data-stu-id="d4df3-152">In the previous example, it was inconvenient to specify types for all the variables explicitly.</span></span> <span data-ttu-id="d4df3-153">Bu örnekte, olanaksızdır.</span><span class="sxs-lookup"><span data-stu-id="d4df3-153">In this example, it is impossible.</span></span> <span data-ttu-id="d4df3-154">Veri kaynağından tüm `Customer` öğeleri veya her öğeden tek bir alanı seçmek yerine, bu sorgudaki `Select` yan tümce orijinal `Customer` nesnesinin iki özelliğini döndürür: `Name` ve `City`.</span><span class="sxs-lookup"><span data-stu-id="d4df3-154">Instead of selecting entire `Customer` elements from the data source, or a single field from each element, the `Select` clause in this query returns two properties of the original `Customer` object: `Name` and `City`.</span></span> <span data-ttu-id="d4df3-155">`Select` yan tümcesine yanıt olarak, derleyici bu iki özelliği içeren anonim bir tür tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d4df3-155">In response to the `Select` clause, the compiler defines an anonymous type that contains those two properties.</span></span> <span data-ttu-id="d4df3-156">`For Each` döngüsünde `nameCityQuery` yürütmenin sonucu, yeni anonim türün örneklerinin bir koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="d4df3-156">The result of executing `nameCityQuery` in the `For Each` loop is a collection of instances of the new anonymous type.</span></span> <span data-ttu-id="d4df3-157">Anonim türün kullanılabilir bir adı olmadığından, `nameCityQuery` veya `custInfo` türünü açıkça belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4df3-157">Because the anonymous type has no usable name, you cannot specify the type of `nameCityQuery` or `custInfo` explicitly.</span></span> <span data-ttu-id="d4df3-158">Yani, anonim bir tür ile `IEnumerable(Of String)``String` yerine kullanılacak tür adı yoktur.</span><span class="sxs-lookup"><span data-stu-id="d4df3-158">That is, with an anonymous type, you have no type name to use in place of `String` in `IEnumerable(Of String)`.</span></span> <span data-ttu-id="d4df3-159">Daha fazla bilgi için bkz. [anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="d4df3-159">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>

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

<span data-ttu-id="d4df3-160">Önceki örnekteki tüm değişkenlerin türlerini belirtmek mümkün olmasa da ilişkiler aynı kalır.</span><span class="sxs-lookup"><span data-stu-id="d4df3-160">Although it is not possible to specify types for all the variables in the previous example, the relationships remain the same.</span></span>

1. <span data-ttu-id="d4df3-161">Veri kaynağındaki öğelerin türü, sorgudaki aralık değişkeninin türüdür.</span><span class="sxs-lookup"><span data-stu-id="d4df3-161">The type of the elements in the data source is again the type of the range variable in the query.</span></span> <span data-ttu-id="d4df3-162">Bu örnekte, `cust` bir `Customer`örneğidir.</span><span class="sxs-lookup"><span data-stu-id="d4df3-162">In this example, `cust` is an instance of `Customer`.</span></span>

2. <span data-ttu-id="d4df3-163">`Select` deyimin anonim bir tür oluşturduğu için, `nameCityQuery`sorgu değişkeni örtük olarak anonim bir tür olarak yazılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d4df3-163">Because the `Select` statement produces an anonymous type, the query variable, `nameCityQuery`, must be implicitly typed as an anonymous type.</span></span> <span data-ttu-id="d4df3-164">Anonim bir türün kullanılabilir adı yok ve bu nedenle açıkça belirtilemez.</span><span class="sxs-lookup"><span data-stu-id="d4df3-164">An anonymous type has no usable name, and therefore cannot be specified explicitly.</span></span>

3. <span data-ttu-id="d4df3-165">`For Each` döngüsünde yineleme değişkeninin türü, adım 2 ' de oluşturulan anonim türüdür.</span><span class="sxs-lookup"><span data-stu-id="d4df3-165">The type of the iteration variable in the `For Each` loop is the anonymous type created in step 2.</span></span> <span data-ttu-id="d4df3-166">Türün kullanılabilir bir adı olmadığından, döngü yineleme değişkeninin türü örtük olarak belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="d4df3-166">Because the type has no usable name, the type of the loop iteration variable must be determined implicitly.</span></span>

## <a name="see-also"></a><span data-ttu-id="d4df3-167">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4df3-167">See also</span></span>

- [<span data-ttu-id="d4df3-168">Visual Basic LINQ ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="d4df3-168">Getting Started with LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [<span data-ttu-id="d4df3-169">Anonim Tipler</span><span class="sxs-lookup"><span data-stu-id="d4df3-169">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="d4df3-170">Yerel Çıkarım</span><span class="sxs-lookup"><span data-stu-id="d4df3-170">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="d4df3-171">Visual Basic LINQ 'e giriş</span><span class="sxs-lookup"><span data-stu-id="d4df3-171">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="d4df3-172">LINQ</span><span class="sxs-lookup"><span data-stu-id="d4df3-172">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="d4df3-173">Sorgular</span><span class="sxs-lookup"><span data-stu-id="d4df3-173">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
