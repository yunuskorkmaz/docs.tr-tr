---
title: LINQ ile Veri Dönüştürmeler (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], data transformations
- source elements [LINQ in C#]
- joining multiple inputs [LINQ in C#]
- multiple outputs for one output sequence [LINQ in C#]
- subset of source elements [LINQ in C#]
- data sources [LINQ in C#], data transformations
- data transformations [LINQ in C#]
ms.assetid: 674eae9e-bc72-4a88-aed3-802b45b25811
ms.openlocfilehash: c165f78c53cec0417d39320580b812ff01fef68b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33333264"
---
# <a name="data-transformations-with-linq-c"></a><span data-ttu-id="ceea7-102">LINQ ile Veri Dönüştürmeler (C#)</span><span class="sxs-lookup"><span data-stu-id="ceea7-102">Data Transformations with LINQ (C#)</span></span>
[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]<span data-ttu-id="ceea7-103"> yalnızca veri alma hakkında değil.</span><span class="sxs-lookup"><span data-stu-id="ceea7-103"> is not only about retrieving data.</span></span> <span data-ttu-id="ceea7-104">Veri dönüştürme için de güçlü bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="ceea7-104">It is also a powerful tool for transforming data.</span></span> <span data-ttu-id="ceea7-105">Kullanarak bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu olarak giriş ve yeni bir çıkış sırası oluşturmak için birçok yolla değiştirme kaynağı sırası kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ceea7-105">By using a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query, you can use a source sequence as input and modify it in many ways to create a new output sequence.</span></span> <span data-ttu-id="ceea7-106">Öğeleri sıralama ve Gruplama değiştirmeden dizisi kendisini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ceea7-106">You can modify the sequence itself without modifying the elements themselves by sorting and grouping.</span></span> <span data-ttu-id="ceea7-107">Ancak, belki de en güçlü özelliği [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgudur yeni türleri oluşturma yeteneği.</span><span class="sxs-lookup"><span data-stu-id="ceea7-107">But perhaps the most powerful feature of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries is the ability to create new types.</span></span> <span data-ttu-id="ceea7-108">Bu, gerçekleştirilir [seçin](../../../../csharp/language-reference/keywords/select-clause.md) yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="ceea7-108">This is accomplished in the [select](../../../../csharp/language-reference/keywords/select-clause.md) clause.</span></span> <span data-ttu-id="ceea7-109">Örneğin, aşağıdaki görevleri gerçekleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ceea7-109">For example, you can perform the following tasks:</span></span>  
  
-   <span data-ttu-id="ceea7-110">Birden çok giriş dizilerini yeni bir türe sahip bir tek bir çıkış sırası birleştirin.</span><span class="sxs-lookup"><span data-stu-id="ceea7-110">Merge multiple input sequences into a single output sequence that has a new type.</span></span>  
  
-   <span data-ttu-id="ceea7-111">Kaynak sıradaki her bir öğe yalnızca bir veya birkaç özelliklerini öğeleri oluşur çıkış sıraları oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ceea7-111">Create output sequences whose elements consist of only one or several properties of each element in the source sequence.</span></span>  
  
-   <span data-ttu-id="ceea7-112">Kaynak veriler üzerinde gerçekleştirilen işlemler sonuçlarını öğeleri oluşur çıkış sıraları oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ceea7-112">Create output sequences whose elements consist of the results of operations performed on the source data.</span></span>  
  
-   <span data-ttu-id="ceea7-113">Çıkış sıraları farklı bir biçimde oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ceea7-113">Create output sequences in a different format.</span></span> <span data-ttu-id="ceea7-114">Örneğin, XML verileri SQL satırları veya metin dosyalarından dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ceea7-114">For example, you can transform data from SQL rows or text files into XML.</span></span>  
  
 <span data-ttu-id="ceea7-115">Bu, yalnızca birkaç örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ceea7-115">These are just several examples.</span></span> <span data-ttu-id="ceea7-116">Elbette, bu dönüşümleri aynı sorguda çeşitli şekillerde birleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="ceea7-116">Of course, these transformations can be combined in various ways in the same query.</span></span> <span data-ttu-id="ceea7-117">Ayrıca, bir sorgu çıkış dizisi giriş dizisi yeni bir sorgu için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ceea7-117">Furthermore, the output sequence of one query can be used as the input sequence for a new query.</span></span>  
  
## <a name="joining-multiple-inputs-into-one-output-sequence"></a><span data-ttu-id="ceea7-118">Birden Çok Girdiyi Bir Çıkış Sırasına Katma</span><span class="sxs-lookup"><span data-stu-id="ceea7-118">Joining Multiple Inputs into One Output Sequence</span></span>  
 <span data-ttu-id="ceea7-119">Kullanabileceğiniz bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] birden fazla giriş sırası öğeleri içeren bir çıkış sırası oluşturmak için sorgu.</span><span class="sxs-lookup"><span data-stu-id="ceea7-119">You can use a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query to create an output sequence that contains elements from more than one input sequence.</span></span> <span data-ttu-id="ceea7-120">Aşağıdaki örnekte, iki bellek içi veri yapılarını birleştirmek gösterilmektedir, ancak aynı ilkeler XML veya SQL veya veri kümesi kaynaklardan veri birleştirmek için uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="ceea7-120">The following example shows how to combine two in-memory data structures, but the same principles can be applied to combine data from XML or SQL or DataSet sources.</span></span> <span data-ttu-id="ceea7-121">Aşağıdaki iki sınıf türleri varsayın:</span><span class="sxs-lookup"><span data-stu-id="ceea7-121">Assume the following two class types:</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#7](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/data-transformations-with-linq_1.cs)]  
  
 <span data-ttu-id="ceea7-122">Aşağıdaki örnek sorgu gösterir:</span><span class="sxs-lookup"><span data-stu-id="ceea7-122">The following example shows the query:</span></span>  
  
 [!code-csharp[CSLinqGettingStarted#8](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/data-transformations-with-linq_2.cs)]  
  
 <span data-ttu-id="ceea7-123">Daha fazla bilgi için bkz: [JOIN yan tümcesi](../../../../csharp/language-reference/keywords/join-clause.md) ve [select yan tümcesi](../../../../csharp/language-reference/keywords/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="ceea7-123">For more information, see [join clause](../../../../csharp/language-reference/keywords/join-clause.md) and [select clause](../../../../csharp/language-reference/keywords/select-clause.md).</span></span>  
  
## <a name="selecting-a-subset-of-each-source-element"></a><span data-ttu-id="ceea7-124">Her Kaynak Öğesinin alt kümesini seçme</span><span class="sxs-lookup"><span data-stu-id="ceea7-124">Selecting a Subset of each Source Element</span></span>  
 <span data-ttu-id="ceea7-125">Her öğe kümesini kaynak sırasını seçmek için birincil iki yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="ceea7-125">There are two primary ways to select a subset of each element in the source sequence:</span></span>  
  
1.  <span data-ttu-id="ceea7-126">Source öğesi yalnızca bir üye seçmek için nokta işlemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="ceea7-126">To select just one member of the source element, use the dot operation.</span></span> <span data-ttu-id="ceea7-127">Aşağıdaki örnekte, varsayımında bir `Customer` nesnesini içeren adlı bir dize dahil olmak üzere birkaç ortak özellikler `City`.</span><span class="sxs-lookup"><span data-stu-id="ceea7-127">In the following example, assume that a `Customer` object contains several public properties including a string named `City`.</span></span> <span data-ttu-id="ceea7-128">Çalıştırıldığında, bu sorgu dizeleri çıkış dizisi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ceea7-128">When executed, this query will produce an output sequence of strings.</span></span>  
  
    ```  
    var query = from cust in Customers  
                select cust.City;  
    ```  
  
2.  <span data-ttu-id="ceea7-129">Source öğesi birden fazla özelliğinden içeren öğeleri oluşturmak için nesne Başlatıcı adlandırılmış bir nesne veya anonim bir tür ile kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ceea7-129">To create elements that contain more than one property from the source element, you can use an object initializer with either a named object or an anonymous type.</span></span> <span data-ttu-id="ceea7-130">Aşağıdaki örnek, her iki özellik kapsülleyen anonim bir tür kullanımını gösterir `Customer` öğe:</span><span class="sxs-lookup"><span data-stu-id="ceea7-130">The following example shows the use of an anonymous type to encapsulate two properties from each `Customer` element:</span></span>  
  
    ```  
    var query = from cust in Customer  
                select new {Name = cust.Name, City = cust.City};  
    ```  
  
 <span data-ttu-id="ceea7-131">Daha fazla bilgi için bkz: [nesne ve koleksiyon başlatıcıları](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md) ve [anonim türler](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="ceea7-131">For more information, see [Object and Collection Initializers](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md) and [Anonymous Types](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span>  
  
## <a name="transforming-in-memory-objects-into-xml"></a><span data-ttu-id="ceea7-132">Bellek İçi Nesneleri XML'e dönüştürme</span><span class="sxs-lookup"><span data-stu-id="ceea7-132">Transforming in-Memory Objects into XML</span></span>  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]<span data-ttu-id="ceea7-133"> sorguları bellek içi veri yapılarını, SQL veritabanları arasında verileri dönüştürmek kolaylaştırır [!INCLUDE[vstecado](~/includes/vstecado-md.md)] veri kümelerini ve XML akışları ya da belgeler.</span><span class="sxs-lookup"><span data-stu-id="ceea7-133"> queries make it easy to transform data between in-memory data structures, SQL databases, [!INCLUDE[vstecado](~/includes/vstecado-md.md)] Datasets and XML streams or documents.</span></span> <span data-ttu-id="ceea7-134">Aşağıdaki örnekte bir bellek içi veri yapısı nesneleri XML elemanlara dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="ceea7-134">The following example transforms objects in an in-memory data structure into XML elements.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#9](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/data-transformations-with-linq_3.cs)]  
  
 <span data-ttu-id="ceea7-135">Kod şu XML çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="ceea7-135">The code produces the following XML output:</span></span>  
  
```xml  
<Root>  
  <student>  
    <First>Svetlana</First>  
    <Last>Omelchenko</Last>  
    <Scores>97,92,81,60</Scores>  
  </student>  
  <student>  
    <First>Claire</First>  
    <Last>O'Donnell</Last>  
    <Scores>75,84,91,39</Scores>  
  </student>  
  <student>  
    <First>Sven</First>  
    <Last>Mortensen</Last>  
    <Scores>88,94,65,91</Scores>  
  </student>  
</Root>  
```  
  
 <span data-ttu-id="ceea7-136">Daha fazla bilgi için bkz: [oluşturma XML ağaçları C# (LINQ-XML)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="ceea7-136">For more information, see [Creating XML Trees in C# (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees-linq-to-xml-2.md).</span></span>  
  
## <a name="performing-operations-on-source-elements"></a><span data-ttu-id="ceea7-137">Kaynak Öğeler Üzerinde İşlemler Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="ceea7-137">Performing Operations on Source Elements</span></span>  
 <span data-ttu-id="ceea7-138">Çıkış dizisi, herhangi bir öğe veya kaynak sıradaki öğenin özelliklerinden içermeyebilir.</span><span class="sxs-lookup"><span data-stu-id="ceea7-138">An output sequence might not contain any elements or element properties from the source sequence.</span></span> <span data-ttu-id="ceea7-139">Çıkışı, bunun yerine kaynak öğelerin giriş bağımsız değişken olarak kullanarak hesaplanan bir değerleri dizisi olabilir.</span><span class="sxs-lookup"><span data-stu-id="ceea7-139">The output might instead be a sequence of values that is computed by using the source elements as input arguments.</span></span> <span data-ttu-id="ceea7-140">Yürütüldüğünde, aşağıdaki basit sorgu, bir dizi dize değerleri temsil eden türündeki öğeler kaynak sıralamasına dayalı bir hesaplama çıkarır `double`.</span><span class="sxs-lookup"><span data-stu-id="ceea7-140">The following simple query, when it is executed, outputs a sequence of strings whose values represent a calculation based on the source sequence of elements of type `double`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ceea7-141">Sorgu başka bir etki alanına çevrilir, sorgu ifadelerinde yöntemleri çağırma desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="ceea7-141">Calling methods in query expressions is not supported if the query will be translated into some other domain.</span></span> <span data-ttu-id="ceea7-142">Örneğin, bir sıradan C# yöntemi çağrılamıyor [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] SQL Server bağlam için içerdiğinden.</span><span class="sxs-lookup"><span data-stu-id="ceea7-142">For example, you cannot call an ordinary C# method in [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] because SQL Server has no context for it.</span></span> <span data-ttu-id="ceea7-143">Ancak, saklı yordamlar eşleştirme için yöntemleri ve bu çağırın.</span><span class="sxs-lookup"><span data-stu-id="ceea7-143">However, you can map stored procedures to methods and call those.</span></span> <span data-ttu-id="ceea7-144">Daha fazla bilgi için bkz: [saklı yordamlar](../../../../framework/data/adonet/sql/linq/stored-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="ceea7-144">For more information, see [Stored Procedures](../../../../framework/data/adonet/sql/linq/stored-procedures.md).</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#10](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/data-transformations-with-linq_4.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="ceea7-145">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ceea7-145">See Also</span></span>  
 [<span data-ttu-id="ceea7-146">Dil ile tümleşik sorgu (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="ceea7-146">Language-Integrated Query (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/index.md)  
 [<span data-ttu-id="ceea7-147">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="ceea7-147">LINQ to SQL</span></span>](../../../../../docs/framework/data/adonet/sql/linq/index.md)  
 [<span data-ttu-id="ceea7-148">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="ceea7-148">LINQ to DataSet</span></span>](../../../../framework/data/adonet/linq-to-dataset.md)  
 [<span data-ttu-id="ceea7-149">LINQ-XML (C#)</span><span class="sxs-lookup"><span data-stu-id="ceea7-149">LINQ to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)  
 [<span data-ttu-id="ceea7-150">LINQ Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="ceea7-150">LINQ Query Expressions</span></span>](../../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [<span data-ttu-id="ceea7-151">select yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="ceea7-151">select clause</span></span>](../../../../csharp/language-reference/keywords/select-clause.md)
