---
title: "LINQ Sorgu İşlemlerinde Tür İlişkileri (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "34"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1b93188475dd2bb00aea044ff178028eb87e00d4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="type-relationships-in-query-operations-visual-basic"></a><span data-ttu-id="ce99c-102">LINQ Sorgu İşlemlerinde Tür İlişkileri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ce99c-102">Type Relationships in Query Operations (Visual Basic)</span></span>
<span data-ttu-id="ce99c-103">Kullanılan değişkenleri [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] sorgu işlemleri kesin türü belirtilmiş ve birbiriyle uyumlu olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ce99c-103">Variables used in [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] query operations are strongly typed and must be compatible with each other.</span></span> <span data-ttu-id="ce99c-104">Güçlü yazarak, veri kaynağı, sorgu ve sorgu yürütmesi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ce99c-104">Strong typing is used in the data source, in the query itself, and in the query execution.</span></span> <span data-ttu-id="ce99c-105">Aşağıdaki çizimde açıklamak için kullanılan terimler tanımlayan bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu.</span><span class="sxs-lookup"><span data-stu-id="ce99c-105">The following illustration identifies terms used to describe a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query.</span></span> <span data-ttu-id="ce99c-106">Bir sorgunun bölümlerini hakkında daha fazla bilgi için bkz: [temel sorgu işlemleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="ce99c-106">For more information about the parts of a query, see [Basic Query Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).</span></span>  
  
 <span data-ttu-id="ce99c-107">![Öğeleri vurgulanmış sahte kod sorgu. ] (../../../../visual-basic/programming-guide/concepts/linq/media/sjltyperels.png "SJLtypeRels")</span><span class="sxs-lookup"><span data-stu-id="ce99c-107">![Pseudocode query with elements highlighted.](../../../../visual-basic/programming-guide/concepts/linq/media/sjltyperels.png "SJLtypeRels")</span></span>  
<span data-ttu-id="ce99c-108">LINQ Sorgu bölümleri</span><span class="sxs-lookup"><span data-stu-id="ce99c-108">Parts of a LINQ query</span></span>  
  
 <span data-ttu-id="ce99c-109">Sorgudaki Aralık değişkeninin türü veri kaynağındaki öğelerin türü ile uyumlu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ce99c-109">The type of the range variable in the query must be compatible with the type of the elements in the data source.</span></span> <span data-ttu-id="ce99c-110">Sorgu değişkeninin türü tanımlanan dizisi öğesi ile uyumlu olmalıdır `Select` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="ce99c-110">The type of the query variable must be compatible with the sequence element defined in the `Select` clause.</span></span> <span data-ttu-id="ce99c-111">Son olarak, sıra öğelerin türü ayrıca kullanılan for döngüsü denetim değişkeni türü ile uyumlu olmalıdır `For Each` Sorguyu yürüten deyimi.</span><span class="sxs-lookup"><span data-stu-id="ce99c-111">Finally, the type of the sequence elements also must be compatible with the type of the loop control variable that is used in the `For Each` statement that executes the query.</span></span> <span data-ttu-id="ce99c-112">Bu güçlü yazarak türü hataları tanımlaması derleme zamanında kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="ce99c-112">This strong typing facilitates identification of type errors at compile time.</span></span>  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="ce99c-113">güçlü yazarak yerel türü çıkarımı olarak da bilinen uygulayarak kullanışlı hale getirir *örtülü yazma*.</span><span class="sxs-lookup"><span data-stu-id="ce99c-113"> makes strong typing convenient by implementing local type inference, also known as *implicit typing*.</span></span> <span data-ttu-id="ce99c-114">Özellik, önceki örnekte kullanılır ve bunu genelinde kullanılan görür [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] örnekler ve belgeler.</span><span class="sxs-lookup"><span data-stu-id="ce99c-114">That feature is used in the previous example, and you will see it used throughout the [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] samples and documentation.</span></span> <span data-ttu-id="ce99c-115">Visual Basic'te yerel türü çıkarımı yalnızca kullanılarak gerçekleştirilen bir `Dim` deyimi olmadan bir `As` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="ce99c-115">In Visual Basic, local type inference is accomplished simply by using a `Dim` statement without an `As` clause.</span></span> <span data-ttu-id="ce99c-116">Aşağıdaki örnekte, `city` bir dize olarak kesin türü belirtilmiş.</span><span class="sxs-lookup"><span data-stu-id="ce99c-116">In the following example, `city` is strongly typed as a string.</span></span>  
  
 [!code-vb[VbLINQTypeRels#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_1.vb)]  
  
> [!NOTE]
>  <span data-ttu-id="ce99c-117">Yerel türü çıkarımı çalışır yalnızca `Option Infer` ayarlanır `On`.</span><span class="sxs-lookup"><span data-stu-id="ce99c-117">Local type inference works only when `Option Infer` is set to `On`.</span></span> <span data-ttu-id="ce99c-118">Daha fazla bilgi için bkz: [Option Infer deyimi](../../../../visual-basic/language-reference/statements/option-infer-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ce99c-118">For more information, see [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md).</span></span>  
  
 <span data-ttu-id="ce99c-119">Ancak, bir sorguda yerel türü çıkarımı kullansanız bile aynı tür ilişkileri veri kaynağındaki değişkenleri sorgu değişkeni ve sorgu yürütme döngüsü arasında mevcut.</span><span class="sxs-lookup"><span data-stu-id="ce99c-119">However, even if you use local type inference in a query, the same type relationships are present among the variables in the data source, the query variable, and the query execution loop.</span></span> <span data-ttu-id="ce99c-120">Yazarken bu tür ilişkileri ilgili temel bilgilere sahip yararlıdır [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgular veya belgelerinde örnekleri ve kodu ile çalışma.</span><span class="sxs-lookup"><span data-stu-id="ce99c-120">It is useful to have a basic understanding of these type relationships when you are writing [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries, or working with the samples and code examples in the documentation.</span></span>  
  
 <span data-ttu-id="ce99c-121">Veri kaynağından döndürülen türü eşleşmiyor bir aralık değişkeni için bir açık tür belirtmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="ce99c-121">You may need to specify an explicit type for a range variable that does not match the type returned from the data source.</span></span> <span data-ttu-id="ce99c-122">Aralık değişkeninin türünü kullanarak belirtebilirsiniz bir `As` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="ce99c-122">You can specify the type of the range variable by using an `As` clause.</span></span> <span data-ttu-id="ce99c-123">Ancak, bu hatayla sonuçlanır dönüştürme ise bir [dönüştürme daraltma](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) ve `Option Strict` ayarlanır `On`.</span><span class="sxs-lookup"><span data-stu-id="ce99c-123">However, this results in an error if the conversion is a [narrowing conversion](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and `Option Strict` is set to `On`.</span></span> <span data-ttu-id="ce99c-124">Bu nedenle, veri kaynağından alınan değerleri dönüştürme gerçekleştirmenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="ce99c-124">Therefore, we recommend that you perform the conversion on the values retrieved from the data source.</span></span> <span data-ttu-id="ce99c-125">Kullanarak açık aralık değişkeni türü veri kaynağından değerleri dönüştürebilirsiniz <xref:System.Linq.Enumerable.Cast%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ce99c-125">You can convert the values from the data source to the explicit range variable type by using the <xref:System.Linq.Enumerable.Cast%2A> method.</span></span> <span data-ttu-id="ce99c-126">Seçilen değerleri de çevirebilirsiniz `Select` yan tümcesinin aralık değişkeni türünden farklı bir açık tür.</span><span class="sxs-lookup"><span data-stu-id="ce99c-126">You can also cast the values selected in the `Select` clause to an explicit type that is different from the type of the range variable.</span></span> <span data-ttu-id="ce99c-127">Bu noktalar aşağıdaki kodda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ce99c-127">These points are illustrated in the following code.</span></span>  
  
 [!code-vb[VbLINQTypeRels#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_2.vb)]  
  
## <a name="queries-that-return-entire-elements-of-the-source-data"></a><span data-ttu-id="ce99c-128">Kaynak verilerin tüm öğeleri döndüren sorgular</span><span class="sxs-lookup"><span data-stu-id="ce99c-128">Queries That Return Entire Elements of the Source Data</span></span>  
 <span data-ttu-id="ce99c-129">Aşağıdaki örnekte gösterildiği bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu işleminin veri kaynağından seçilen öğeleri bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="ce99c-129">The following example shows a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query operation that returns a sequence of elements selected from the source data.</span></span> <span data-ttu-id="ce99c-130">Kaynak `names`, bir dizisini içerir ve sorgu çıktısı M harfle başlayan dizelerini içeren bir dizidir.</span><span class="sxs-lookup"><span data-stu-id="ce99c-130">The source, `names`, contains an array of strings, and the query output is a sequence containing strings that start with the letter M.</span></span>  
  
 [!code-vb[VbLINQTypeRels#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_3.vb)]  
  
 <span data-ttu-id="ce99c-131">Bu, aşağıdaki kodu eşdeğerdir, ancak daha kısa ve yazma daha kolay.</span><span class="sxs-lookup"><span data-stu-id="ce99c-131">This is equivalent to the following code, but is much shorter and easier to write.</span></span> <span data-ttu-id="ce99c-132">Yerel türü çıkarımı sorgularda bağımlılık Visual Basic'te tercih edilen stili ' dir.</span><span class="sxs-lookup"><span data-stu-id="ce99c-132">Reliance on local type inference in queries is the preferred style in Visual Basic.</span></span>  
  
 [!code-vb[VbLINQTypeRels#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/type-relationships-in-query-operations_4.vb)]  
  
 <span data-ttu-id="ce99c-133">Türü örtük veya açık olarak belirlenir olup olmadığını aşağıdaki ilişkileri önceki kod örnekleri, ikisi de yok.</span><span class="sxs-lookup"><span data-stu-id="ce99c-133">The following relationships exist in both of the previous code examples, whether the types are determined implicitly or explicitly.</span></span>  
  
1.  <span data-ttu-id="ce99c-134">Veri kaynağındaki öğelerin türü `names`, Aralık değişkeninin tür `name`, sorgu.</span><span class="sxs-lookup"><span data-stu-id="ce99c-134">The type of the elements in the data source, `names`, is the type of the range variable, `name`, in the query.</span></span>  
  
2.  <span data-ttu-id="ce99c-135">Seçili nesne türünü `name`, sorgu değişken türünü belirler `mNames`.</span><span class="sxs-lookup"><span data-stu-id="ce99c-135">The type of the object that is selected, `name`, determines the type of the query variable, `mNames`.</span></span> <span data-ttu-id="ce99c-136">Burada `name` sorgu değişkeni Visual Basic'de IEnumerable (Of dize) olacak şekilde bir dize değil.</span><span class="sxs-lookup"><span data-stu-id="ce99c-136">Here `name` is a string, so the query variable is IEnumerable(Of String) in Visual Basic.</span></span>  
  
3.  <span data-ttu-id="ce99c-137">Tanımlanan sorgu `mNames` yürütülür `For Each` döngü.</span><span class="sxs-lookup"><span data-stu-id="ce99c-137">The query defined in `mNames` is executed in the `For Each` loop.</span></span> <span data-ttu-id="ce99c-138">Döngü sorgu yürütmenin sonucu yineler.</span><span class="sxs-lookup"><span data-stu-id="ce99c-138">The loop iterates over the result of executing the query.</span></span> <span data-ttu-id="ce99c-139">Çünkü `mNames`, yürütüldüğünde, bir dizi dize, döngü yineleme değişkeni döndürür `nm`, ayrıca bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="ce99c-139">Because `mNames`, when it is executed, will return a sequence of strings, the loop iteration variable, `nm`, also is a string.</span></span>  
  
## <a name="queries-that-return-one-field-from-selected-elements"></a><span data-ttu-id="ce99c-140">Seçilen öğeleri bir alan döndüren sorgular</span><span class="sxs-lookup"><span data-stu-id="ce99c-140">Queries That Return One Field from Selected Elements</span></span>  
 <span data-ttu-id="ce99c-141">Aşağıdaki örnekte gösterildiği bir [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] sorgu işleminin veri kaynağından seçilen her öğe yalnızca bir bölümünü içeren bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="ce99c-141">The following example shows a [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] query operation that returns a sequence containing only one part of each element selected from the data source.</span></span> <span data-ttu-id="ce99c-142">Sorgu bir koleksiyonunu alır `Customer` nesneleri, veri kaynağı olarak ve yalnızca projeleri `Name` sonucun bir özellik.</span><span class="sxs-lookup"><span data-stu-id="ce99c-142">The query takes a collection of `Customer` objects as its data source and projects only the `Name` property in the result.</span></span> <span data-ttu-id="ce99c-143">Müşteri adı bir dize olduğundan, sorgu dizeleri dizisi çıktı olarak üretir.</span><span class="sxs-lookup"><span data-stu-id="ce99c-143">Because the customer name is a string, the query produces a sequence of strings as output.</span></span>  
  
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
  
 <span data-ttu-id="ce99c-144">Bu basit örnekte değişkenleri arasındaki ilişkileri gibidir.</span><span class="sxs-lookup"><span data-stu-id="ce99c-144">The relationships between variables are like those in the simpler example.</span></span>  
  
1.  <span data-ttu-id="ce99c-145">Veri kaynağındaki öğelerin türü `customers`, Aralık değişkeninin tür `cust`, sorgu.</span><span class="sxs-lookup"><span data-stu-id="ce99c-145">The type of the elements in the data source, `customers`, is the type of the range variable, `cust`, in the query.</span></span> <span data-ttu-id="ce99c-146">Türü bu örnekte, `Customer`.</span><span class="sxs-lookup"><span data-stu-id="ce99c-146">In this example, that type is `Customer`.</span></span>  
  
2.  <span data-ttu-id="ce99c-147">`Select` Deyiminin döndüreceği `Name` her özellik `Customer` nesnenin tamamı yerine nesne.</span><span class="sxs-lookup"><span data-stu-id="ce99c-147">The `Select` statement returns the `Name` property of each `Customer` object instead of the whole object.</span></span> <span data-ttu-id="ce99c-148">Çünkü `Name` sorgu değişken bir dize `custNames`, yeniden (dize), IEnumerable, olmaz `Customer`.</span><span class="sxs-lookup"><span data-stu-id="ce99c-148">Because `Name` is a string, the query variable, `custNames`, will again be IEnumerable(Of String), not of `Customer`.</span></span>  
  
3.  <span data-ttu-id="ce99c-149">Çünkü `custNames` dizeler, bir dizi temsil eden `For Each` döngünün yineleme değişkeni `custName`, bir dize olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ce99c-149">Because `custNames` represents a sequence of strings, the `For Each` loop's iteration variable, `custName`, must be a string.</span></span>  
  
 <span data-ttu-id="ce99c-150">Yerel türü çıkarımı önceki örnek yazmak için ve anlaşılması aşağıdaki örnekte gösterildiği gibi daha kullanışsız olabilir.</span><span class="sxs-lookup"><span data-stu-id="ce99c-150">Without local type inference, the previous example would be more cumbersome to write and to understand, as the following example shows.</span></span>  
  
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
  
## <a name="queries-that-require-anonymous-types"></a><span data-ttu-id="ce99c-151">Anonim türler gerektiren sorguları</span><span class="sxs-lookup"><span data-stu-id="ce99c-151">Queries That Require Anonymous Types</span></span>  
 <span data-ttu-id="ce99c-152">Aşağıdaki örnek, daha karmaşık bir durumu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ce99c-152">The following example shows a more complex situation.</span></span> <span data-ttu-id="ce99c-153">Önceki örnekte, tüm değişkenleri türlerinde açıkça belirtmek kullanışsız.</span><span class="sxs-lookup"><span data-stu-id="ce99c-153">In the previous example, it was inconvenient to specify types for all the variables explicitly.</span></span> <span data-ttu-id="ce99c-154">Bu örnekte, mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="ce99c-154">In this example, it is impossible.</span></span> <span data-ttu-id="ce99c-155">Tüm seçmek yerine `Customer` veri kaynağı veya tek bir alan her öğeden öğelerinden `Select` bu sorgu yan tümcesinde iki özgün özelliklerini döndürür `Customer` nesne: `Name` ve `City`.</span><span class="sxs-lookup"><span data-stu-id="ce99c-155">Instead of selecting entire `Customer` elements from the data source, or a single field from each element, the `Select` clause in this query returns two properties of the original `Customer` object: `Name` and `City`.</span></span> <span data-ttu-id="ce99c-156">Yanıt olarak `Select` yan tümcesi, derleyici, bu iki özellik içeren bir anonim türü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ce99c-156">In response to the `Select` clause, the compiler defines an anonymous type that contains those two properties.</span></span> <span data-ttu-id="ce99c-157">Yürütmenin sonucu `nameCityQuery` içinde `For Each` döngü yeni anonim türdeki örneklerin koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="ce99c-157">The result of executing `nameCityQuery` in the `For Each` loop is a collection of instances of the new anonymous type.</span></span> <span data-ttu-id="ce99c-158">Anonim tür kullanılabilir ad olduğundan türünü belirtemezsiniz `nameCityQuery` veya `custInfo` açıkça.</span><span class="sxs-lookup"><span data-stu-id="ce99c-158">Because the anonymous type has no usable name, you cannot specify the type of `nameCityQuery` or `custInfo` explicitly.</span></span> <span data-ttu-id="ce99c-159">Diğer bir deyişle, sahip anonim bir tür, hiçbir tür adı yerine kullanılacak elinizde `String` içinde `IEnumerable(Of String)`.</span><span class="sxs-lookup"><span data-stu-id="ce99c-159">That is, with an anonymous type, you have no type name to use in place of `String` in `IEnumerable(Of String)`.</span></span> <span data-ttu-id="ce99c-160">Daha fazla bilgi için bkz: [anonim türler](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="ce99c-160">For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
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
  
 <span data-ttu-id="ce99c-161">Önceki örnekte tüm değişkenleri türlerinde belirlemek mümkün olmasa da ilişkileri aynı kalır.</span><span class="sxs-lookup"><span data-stu-id="ce99c-161">Although it is not possible to specify types for all the variables in the previous example, the relationships remain the same.</span></span>  
  
1.  <span data-ttu-id="ce99c-162">Veri kaynağındaki öğelerin türü yeniden sorgusunda aralık değişkeni türüdür.</span><span class="sxs-lookup"><span data-stu-id="ce99c-162">The type of the elements in the data source is again the type of the range variable in the query.</span></span> <span data-ttu-id="ce99c-163">Bu örnekte, `cust` örneği `Customer`.</span><span class="sxs-lookup"><span data-stu-id="ce99c-163">In this example, `cust` is an instance of `Customer`.</span></span>  
  
2.  <span data-ttu-id="ce99c-164">Çünkü `Select` bildirimi üreten anonim bir tür, sorgu değişkeni `nameCityQuery`, anonim bir tür olarak örtülü olarak yazılan gerekir.</span><span class="sxs-lookup"><span data-stu-id="ce99c-164">Because the `Select` statement produces an anonymous type, the query variable, `nameCityQuery`, must be implicitly typed as an anonymous type.</span></span> <span data-ttu-id="ce99c-165">Anonim bir tür kullanılabilir adı yok ve bu nedenle açıkça belirtilemez.</span><span class="sxs-lookup"><span data-stu-id="ce99c-165">An anonymous type has no usable name, and therefore cannot be specified explicitly.</span></span>  
  
3.  <span data-ttu-id="ce99c-166">Yineleme değişkeni türü `For Each` döngü 2. adımda oluşturduğunuz anonim türüdür.</span><span class="sxs-lookup"><span data-stu-id="ce99c-166">The type of the iteration variable in the `For Each` loop is the anonymous type created in step 2.</span></span> <span data-ttu-id="ce99c-167">Kullanılabilir ad türüne sahip olduğundan, döngü yineleme değişkeni türü örtük olarak belirlenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="ce99c-167">Because the type has no usable name, the type of the loop iteration variable must be determined implicitly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce99c-168">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ce99c-168">See Also</span></span>  
 [<span data-ttu-id="ce99c-169">Visual Basic'te Lınq'e Başlarken</span><span class="sxs-lookup"><span data-stu-id="ce99c-169">Getting Started with LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [<span data-ttu-id="ce99c-170">Anonim türler</span><span class="sxs-lookup"><span data-stu-id="ce99c-170">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [<span data-ttu-id="ce99c-171">Yerel tür çıkarımı</span><span class="sxs-lookup"><span data-stu-id="ce99c-171">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="ce99c-172">Visual Basic'de LINQ'e giriş</span><span class="sxs-lookup"><span data-stu-id="ce99c-172">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="ce99c-173">LINQ</span><span class="sxs-lookup"><span data-stu-id="ce99c-173">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="ce99c-174">Sorguları</span><span class="sxs-lookup"><span data-stu-id="ce99c-174">Queries</span></span>](../../../../visual-basic/language-reference/queries/queries.md)
