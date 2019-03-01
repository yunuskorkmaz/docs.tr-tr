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
ms.openlocfilehash: d72a55cadce287979fad25396327680e1f0e0aaf
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56979105"
---
# <a name="type-relationships-in-query-operations-visual-basic"></a><span data-ttu-id="f04fd-102">LINQ Sorgu İşlemlerinde Tür İlişkileri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f04fd-102">Type Relationships in Query Operations (Visual Basic)</span></span>
<span data-ttu-id="f04fd-103">Kullanılan değişkenleri [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] sorgu işlemleri kesin olarak belirlenmiştir ve birbiriyle uyumlu olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f04fd-103">Variables used in [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] query operations are strongly typed and must be compatible with each other.</span></span> <span data-ttu-id="f04fd-104">Güçlü veri kaynağının, sorgu ve sorgu yürütme kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f04fd-104">Strong typing is used in the data source, in the query itself, and in the query execution.</span></span> <span data-ttu-id="f04fd-105">Aşağıdaki çizimde açıklamak için kullanılan terimler tanımlayan bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu.</span><span class="sxs-lookup"><span data-stu-id="f04fd-105">The following illustration identifies terms used to describe a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query.</span></span> <span data-ttu-id="f04fd-106">Bir sorgunun bölümlerini hakkında daha fazla bilgi için bkz: [temel sorgu işlemleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="f04fd-106">For more information about the parts of a query, see [Basic Query Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).</span></span>  
  
 <span data-ttu-id="f04fd-107">![Öğeleri vurgulanmış sözde kod sorgu. ](../../../../visual-basic/programming-guide/concepts/linq/media/sjltyperels.png "SJLtypeRels")</span><span class="sxs-lookup"><span data-stu-id="f04fd-107">![Pseudocode query with elements highlighted.](../../../../visual-basic/programming-guide/concepts/linq/media/sjltyperels.png "SJLtypeRels")</span></span>  
<span data-ttu-id="f04fd-108">LINQ sorgusu bölümleri</span><span class="sxs-lookup"><span data-stu-id="f04fd-108">Parts of a LINQ query</span></span>  
  
 <span data-ttu-id="f04fd-109">Sorgudaki Aralık değişkeninin türü, veri kaynağındaki öğelerin türü ile uyumlu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f04fd-109">The type of the range variable in the query must be compatible with the type of the elements in the data source.</span></span> <span data-ttu-id="f04fd-110">Sorgu değişkeninin türü tanımlanan dizisi öğe ile uyumlu olmalıdır `Select` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="f04fd-110">The type of the query variable must be compatible with the sequence element defined in the `Select` clause.</span></span> <span data-ttu-id="f04fd-111">Son olarak, dizisinin öğelerinin türü de kullanılan döngü denetim değişkeni türü ile uyumlu olmalıdır `For Each` Sorguyu yürüten deyimi.</span><span class="sxs-lookup"><span data-stu-id="f04fd-111">Finally, the type of the sequence elements also must be compatible with the type of the loop control variable that is used in the `For Each` statement that executes the query.</span></span> <span data-ttu-id="f04fd-112">Bu güçlü yazım, Yazım hatalarının derleme zamanında kimliği kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="f04fd-112">This strong typing facilitates identification of type errors at compile time.</span></span>  
  
 <span data-ttu-id="f04fd-113">Visual Basic yapar güçlü yazarak uygun olarak da bilinen bir yerel tür çıkarımı uygulayarak *örtülü yazma*.</span><span class="sxs-lookup"><span data-stu-id="f04fd-113">Visual Basic makes strong typing convenient by implementing local type inference, also known as *implicit typing*.</span></span> <span data-ttu-id="f04fd-114">Özellik, önceki örnekte kullanılır ve genelinde kullanılan görürsünüz [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] örnekler ve belgeler.</span><span class="sxs-lookup"><span data-stu-id="f04fd-114">That feature is used in the previous example, and you will see it used throughout the [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] samples and documentation.</span></span> <span data-ttu-id="f04fd-115">Visual Basic'te yerel tür çıkarımı yalnızca'i kullanılarak başarılır bir `Dim` deyimi olmadan bir `As` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="f04fd-115">In Visual Basic, local type inference is accomplished simply by using a `Dim` statement without an `As` clause.</span></span> <span data-ttu-id="f04fd-116">Aşağıdaki örnekte, `city` bir dize olarak kesin.</span><span class="sxs-lookup"><span data-stu-id="f04fd-116">In the following example, `city` is strongly typed as a string.</span></span>  
  
 [!code-vb[VbLINQTypeRels#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#1)]  
  
> [!NOTE]
>  <span data-ttu-id="f04fd-117">Yerel tür çıkarımı yalnızca çalışır `Option Infer` ayarlanır `On`.</span><span class="sxs-lookup"><span data-stu-id="f04fd-117">Local type inference works only when `Option Infer` is set to `On`.</span></span> <span data-ttu-id="f04fd-118">Daha fazla bilgi için [Option Infer deyimi](../../../../visual-basic/language-reference/statements/option-infer-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f04fd-118">For more information, see [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md).</span></span>  
  
 <span data-ttu-id="f04fd-119">Bir sorguda yerel tür çıkarımı kullanıyor olsanız bile, ancak aynı tür ilişkilerini veri kaynağındaki değişkenleri, sorgu değişkeni ve sorgu yürütme döngüsü arasında yok.</span><span class="sxs-lookup"><span data-stu-id="f04fd-119">However, even if you use local type inference in a query, the same type relationships are present among the variables in the data source, the query variable, and the query execution loop.</span></span> <span data-ttu-id="f04fd-120">Siz yazarken bu tür ilişkilerini temel bir anlayışa sahip olmak yararlı [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorguları veya kod örneklerinde belgeleri ve örnekleri ile çalışma.</span><span class="sxs-lookup"><span data-stu-id="f04fd-120">It is useful to have a basic understanding of these type relationships when you are writing [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries, or working with the samples and code examples in the documentation.</span></span>  
  
 <span data-ttu-id="f04fd-121">Veri kaynağından döndürülen tür eşleşmeyen bir aralık değişkeni için açık bir tür belirtmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="f04fd-121">You may need to specify an explicit type for a range variable that does not match the type returned from the data source.</span></span> <span data-ttu-id="f04fd-122">Aralık değişkeninin türünü kullanarak belirtebileceğiniz bir `As` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="f04fd-122">You can specify the type of the range variable by using an `As` clause.</span></span> <span data-ttu-id="f04fd-123">Ancak, bu hatayla sonuçlanır bir dönüştürme ise bir [daraltma dönüştürmesi](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) ve `Option Strict` ayarlanır `On`.</span><span class="sxs-lookup"><span data-stu-id="f04fd-123">However, this results in an error if the conversion is a [narrowing conversion](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and `Option Strict` is set to `On`.</span></span> <span data-ttu-id="f04fd-124">Bu nedenle, veri kaynağından alınan değerleri dönüştürme almanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="f04fd-124">Therefore, we recommend that you perform the conversion on the values retrieved from the data source.</span></span> <span data-ttu-id="f04fd-125">Kullanarak açık aralığı değişken türü için veri kaynağından değerleri dönüştürebilirsiniz <xref:System.Linq.Enumerable.Cast%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f04fd-125">You can convert the values from the data source to the explicit range variable type by using the <xref:System.Linq.Enumerable.Cast%2A> method.</span></span> <span data-ttu-id="f04fd-126">Seçilen değerleri de çevirebilirsiniz `Select` yan tümcesinin aralık değişkeni türünden farklı olan açık bir tür.</span><span class="sxs-lookup"><span data-stu-id="f04fd-126">You can also cast the values selected in the `Select` clause to an explicit type that is different from the type of the range variable.</span></span> <span data-ttu-id="f04fd-127">Bu noktaları, aşağıdaki kodda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f04fd-127">These points are illustrated in the following code.</span></span>  
  
 [!code-vb[VbLINQTypeRels#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#4)]  
  
## <a name="queries-that-return-entire-elements-of-the-source-data"></a><span data-ttu-id="f04fd-128">Tüm öğeleri kaynak verilerin döndüren sorgular</span><span class="sxs-lookup"><span data-stu-id="f04fd-128">Queries That Return Entire Elements of the Source Data</span></span>  
 <span data-ttu-id="f04fd-129">Aşağıdaki örnekte gösterildiği bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgulama işlemi, veri kaynağından seçilen öğelerin bir dizisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="f04fd-129">The following example shows a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query operation that returns a sequence of elements selected from the source data.</span></span> <span data-ttu-id="f04fd-130">Kaynak `names`, dizelerden oluşan bir dizi içeriyor ve sorgu çıktısı M harfi ile başlayan dizeleri içeren bir dizidir.</span><span class="sxs-lookup"><span data-stu-id="f04fd-130">The source, `names`, contains an array of strings, and the query output is a sequence containing strings that start with the letter M.</span></span>  
  
 [!code-vb[VbLINQTypeRels#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#2)]  
  
 <span data-ttu-id="f04fd-131">Bu, aşağıdaki koda eşdeğerdir, ancak çok daha kısa ve yazmak daha kolay.</span><span class="sxs-lookup"><span data-stu-id="f04fd-131">This is equivalent to the following code, but is much shorter and easier to write.</span></span> <span data-ttu-id="f04fd-132">Yerel tür çıkarımı sorgularda güvenme Visual Basic'te tercih edilen stilidir.</span><span class="sxs-lookup"><span data-stu-id="f04fd-132">Reliance on local type inference in queries is the preferred style in Visual Basic.</span></span>  
  
 [!code-vb[VbLINQTypeRels#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#3)]  
  
 <span data-ttu-id="f04fd-133">Türleri açık veya örtük olarak belirlenmiş olup olmadığını aşağıdaki ilişkileri hem de önceki kod örnekleri, mevcut.</span><span class="sxs-lookup"><span data-stu-id="f04fd-133">The following relationships exist in both of the previous code examples, whether the types are determined implicitly or explicitly.</span></span>  
  
1.  <span data-ttu-id="f04fd-134">Veri kaynağındaki öğelerin türü `names`, Aralık değişkeninin türü `name`, sorgu.</span><span class="sxs-lookup"><span data-stu-id="f04fd-134">The type of the elements in the data source, `names`, is the type of the range variable, `name`, in the query.</span></span>  
  
2.  <span data-ttu-id="f04fd-135">Seçili olan nesnenin türü `name`, sorgu değişkeni türünü belirler `mNames`.</span><span class="sxs-lookup"><span data-stu-id="f04fd-135">The type of the object that is selected, `name`, determines the type of the query variable, `mNames`.</span></span> <span data-ttu-id="f04fd-136">Burada `name` sorgu değişkeni Visual Basic'de IEnumerable (Of String), bu nedenle, bir dize ise.</span><span class="sxs-lookup"><span data-stu-id="f04fd-136">Here `name` is a string, so the query variable is IEnumerable(Of String) in Visual Basic.</span></span>  
  
3.  <span data-ttu-id="f04fd-137">Nde tanımlanan sorgu `mNames` yürütüldü `For Each` döngü.</span><span class="sxs-lookup"><span data-stu-id="f04fd-137">The query defined in `mNames` is executed in the `For Each` loop.</span></span> <span data-ttu-id="f04fd-138">Döngü sorgu yürütmenin sonucu üzerinde yinelenir.</span><span class="sxs-lookup"><span data-stu-id="f04fd-138">The loop iterates over the result of executing the query.</span></span> <span data-ttu-id="f04fd-139">Çünkü `mNames`, yürütüldüğünde, dizeler, döngü yineleme değişkeni, bir dizi döndürür `nm`, ayrıca bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="f04fd-139">Because `mNames`, when it is executed, will return a sequence of strings, the loop iteration variable, `nm`, also is a string.</span></span>  
  
## <a name="queries-that-return-one-field-from-selected-elements"></a><span data-ttu-id="f04fd-140">Seçilen öğelerden bir alan döndüren sorgular</span><span class="sxs-lookup"><span data-stu-id="f04fd-140">Queries That Return One Field from Selected Elements</span></span>  
 <span data-ttu-id="f04fd-141">Aşağıdaki örnekte gösterildiği bir [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] sorgulama veri kaynağından seçilen her öğe yalnızca bir bölümünü içeren bir dizi döndüren işlemi.</span><span class="sxs-lookup"><span data-stu-id="f04fd-141">The following example shows a [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] query operation that returns a sequence containing only one part of each element selected from the data source.</span></span> <span data-ttu-id="f04fd-142">Sorgu koleksiyonunu alır `Customer` nesneleri, veri kaynağı olarak ve yalnızca projeleri `Name` sonucun bir özellik.</span><span class="sxs-lookup"><span data-stu-id="f04fd-142">The query takes a collection of `Customer` objects as its data source and projects only the `Name` property in the result.</span></span> <span data-ttu-id="f04fd-143">Müşteri adı bir dize olduğundan, sorgu çıktı olarak bir dize sırası üretir.</span><span class="sxs-lookup"><span data-stu-id="f04fd-143">Because the customer name is a string, the query produces a sequence of strings as output.</span></span>  
  
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
  
 <span data-ttu-id="f04fd-144">Bu basit örnekte değişkenleri arasındaki ilişkileri gibidir.</span><span class="sxs-lookup"><span data-stu-id="f04fd-144">The relationships between variables are like those in the simpler example.</span></span>  
  
1.  <span data-ttu-id="f04fd-145">Veri kaynağındaki öğelerin türü `customers`, Aralık değişkeninin türü `cust`, sorgu.</span><span class="sxs-lookup"><span data-stu-id="f04fd-145">The type of the elements in the data source, `customers`, is the type of the range variable, `cust`, in the query.</span></span> <span data-ttu-id="f04fd-146">Türü bu örnekte, `Customer`.</span><span class="sxs-lookup"><span data-stu-id="f04fd-146">In this example, that type is `Customer`.</span></span>  
  
2.  <span data-ttu-id="f04fd-147">`Select` Deyimi döndürür `Name` her özellik `Customer` nesnenin tamamı yerine nesne.</span><span class="sxs-lookup"><span data-stu-id="f04fd-147">The `Select` statement returns the `Name` property of each `Customer` object instead of the whole object.</span></span> <span data-ttu-id="f04fd-148">Çünkü `Name` sorgu değişkeni bir dize ise `custNames`, yeniden IEnumerable (Of String), olmayacaktır `Customer`.</span><span class="sxs-lookup"><span data-stu-id="f04fd-148">Because `Name` is a string, the query variable, `custNames`, will again be IEnumerable(Of String), not of `Customer`.</span></span>  
  
3.  <span data-ttu-id="f04fd-149">Çünkü `custNames` dizeleri temsil `For Each` döngüsünün yineleme değişkeni `custName`, bir dize olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f04fd-149">Because `custNames` represents a sequence of strings, the `For Each` loop's iteration variable, `custName`, must be a string.</span></span>  
  
 <span data-ttu-id="f04fd-150">Önceki örnekte yerel tür çıkarımı, yazma ve anlama, aşağıdaki örnekte gösterildiği gibi daha kullanışsız olur.</span><span class="sxs-lookup"><span data-stu-id="f04fd-150">Without local type inference, the previous example would be more cumbersome to write and to understand, as the following example shows.</span></span>  
  
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
  
## <a name="queries-that-require-anonymous-types"></a><span data-ttu-id="f04fd-151">Anonim türler gerektiren sorguları</span><span class="sxs-lookup"><span data-stu-id="f04fd-151">Queries That Require Anonymous Types</span></span>  
 <span data-ttu-id="f04fd-152">Aşağıdaki örnek, daha karmaşık bir durum gösterir.</span><span class="sxs-lookup"><span data-stu-id="f04fd-152">The following example shows a more complex situation.</span></span> <span data-ttu-id="f04fd-153">Önceki örnekte, tüm değişkenlerin türleri açıkça belirtmek uygun.</span><span class="sxs-lookup"><span data-stu-id="f04fd-153">In the previous example, it was inconvenient to specify types for all the variables explicitly.</span></span> <span data-ttu-id="f04fd-154">Bu örnekte, mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="f04fd-154">In this example, it is impossible.</span></span> <span data-ttu-id="f04fd-155">Tümünü seçmek yerine `Customer` öğeleri veri kaynağından veya tek bir alan her öğeden `Select` bu sorgu yan tümcesi, iki özellik özgün döndürür `Customer` nesne: `Name` ve `City`.</span><span class="sxs-lookup"><span data-stu-id="f04fd-155">Instead of selecting entire `Customer` elements from the data source, or a single field from each element, the `Select` clause in this query returns two properties of the original `Customer` object: `Name` and `City`.</span></span> <span data-ttu-id="f04fd-156">Yanıt olarak `Select` yan tümcesi, derleyici, bu iki özellik içeren bir anonim tür tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f04fd-156">In response to the `Select` clause, the compiler defines an anonymous type that contains those two properties.</span></span> <span data-ttu-id="f04fd-157">Yürütmenin sonucu `nameCityQuery` içinde `For Each` döngü, yeni anonim türdeki örneklerin koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="f04fd-157">The result of executing `nameCityQuery` in the `For Each` loop is a collection of instances of the new anonymous type.</span></span> <span data-ttu-id="f04fd-158">Anonim tür kullanılabilir adı olduğundan, türünü belirtemezsiniz `nameCityQuery` veya `custInfo` açıkça.</span><span class="sxs-lookup"><span data-stu-id="f04fd-158">Because the anonymous type has no usable name, you cannot specify the type of `nameCityQuery` or `custInfo` explicitly.</span></span> <span data-ttu-id="f04fd-159">Diğer bir deyişle, anonim bir tür ile hiçbir tür adı yerine kullanılacak elinizde `String` içinde `IEnumerable(Of String)`.</span><span class="sxs-lookup"><span data-stu-id="f04fd-159">That is, with an anonymous type, you have no type name to use in place of `String` in `IEnumerable(Of String)`.</span></span> <span data-ttu-id="f04fd-160">Daha fazla bilgi için [anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="f04fd-160">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
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
  
 <span data-ttu-id="f04fd-161">Önceki örnekte tüm değişkenlerin türleri belirlemek mümkün olmasa da, ilişkileri aynı kalır.</span><span class="sxs-lookup"><span data-stu-id="f04fd-161">Although it is not possible to specify types for all the variables in the previous example, the relationships remain the same.</span></span>  
  
1.  <span data-ttu-id="f04fd-162">Veri kaynağındaki öğelerin türü yeniden sorgudaki Aralık değişkeninin türüdür.</span><span class="sxs-lookup"><span data-stu-id="f04fd-162">The type of the elements in the data source is again the type of the range variable in the query.</span></span> <span data-ttu-id="f04fd-163">Bu örnekte, `cust` örneğidir `Customer`.</span><span class="sxs-lookup"><span data-stu-id="f04fd-163">In this example, `cust` is an instance of `Customer`.</span></span>  
  
2.  <span data-ttu-id="f04fd-164">Çünkü `Select` deyimi, sorgu değişkeni anonim bir tür ürettiğinden `nameCityQuery`, anonim bir tür dolaylı olarak yazılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f04fd-164">Because the `Select` statement produces an anonymous type, the query variable, `nameCityQuery`, must be implicitly typed as an anonymous type.</span></span> <span data-ttu-id="f04fd-165">Anonim bir tür kullanılabilir adı yok ve bu nedenle açıkça belirtilemez.</span><span class="sxs-lookup"><span data-stu-id="f04fd-165">An anonymous type has no usable name, and therefore cannot be specified explicitly.</span></span>  
  
3.  <span data-ttu-id="f04fd-166">Yineleme değişkeni türünü `For Each` döngü 2. adımda oluşturduğunuz anonim türdür.</span><span class="sxs-lookup"><span data-stu-id="f04fd-166">The type of the iteration variable in the `For Each` loop is the anonymous type created in step 2.</span></span> <span data-ttu-id="f04fd-167">Tür kullanılabilir adı olduğundan, döngü yineleme değişkeninin türü örtülü olarak belirlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="f04fd-167">Because the type has no usable name, the type of the loop iteration variable must be determined implicitly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f04fd-168">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f04fd-168">See also</span></span>
- [<span data-ttu-id="f04fd-169">Visual Basic'te lınq'e Başlarken</span><span class="sxs-lookup"><span data-stu-id="f04fd-169">Getting Started with LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [<span data-ttu-id="f04fd-170">Anonim Tipler</span><span class="sxs-lookup"><span data-stu-id="f04fd-170">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="f04fd-171">Yerel Çıkarım</span><span class="sxs-lookup"><span data-stu-id="f04fd-171">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="f04fd-172">Visual Basic'de LINQ'e giriş</span><span class="sxs-lookup"><span data-stu-id="f04fd-172">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="f04fd-173">LINQ</span><span class="sxs-lookup"><span data-stu-id="f04fd-173">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="f04fd-174">Sorgular</span><span class="sxs-lookup"><span data-stu-id="f04fd-174">Queries</span></span>](../../../../visual-basic/language-reference/queries/index.md)
