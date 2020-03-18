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
ms.openlocfilehash: 393e3bd24c4bc8b89064e01e1048b24254f5f83b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635957"
---
# <a name="data-transformations-with-linq-c"></a><span data-ttu-id="e1b4f-102">LINQ ile Veri Dönüştürmeler (C#)</span><span class="sxs-lookup"><span data-stu-id="e1b4f-102">Data Transformations with LINQ (C#)</span></span>
<span data-ttu-id="e1b4f-103">Dil-Tümleşik Sorgu (LINQ) sadece veri almakla ilgili değildir.</span><span class="sxs-lookup"><span data-stu-id="e1b4f-103">Language-Integrated Query (LINQ) is not only about retrieving data.</span></span> <span data-ttu-id="e1b4f-104">Aynı zamanda verileri dönüştürmek için güçlü bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="e1b4f-104">It is also a powerful tool for transforming data.</span></span> <span data-ttu-id="e1b4f-105">BIR LINQ sorgusu kullanarak, giriş olarak bir kaynak dizisi kullanabilir ve yeni bir çıktı dizisi oluşturmak için birçok şekilde değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1b4f-105">By using a LINQ query, you can use a source sequence as input and modify it in many ways to create a new output sequence.</span></span> <span data-ttu-id="e1b4f-106">Sıralama ve gruplandırma ile öğelerin kendilerini değiştirmeden sıranın kendisini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1b4f-106">You can modify the sequence itself without modifying the elements themselves by sorting and grouping.</span></span> <span data-ttu-id="e1b4f-107">Ama belki de LINQ sorgularının en güçlü özelliği yeni türler oluşturma yeteneğidir.</span><span class="sxs-lookup"><span data-stu-id="e1b4f-107">But perhaps the most powerful feature of LINQ queries is the ability to create new types.</span></span> <span data-ttu-id="e1b4f-108">Bu, [seçme](../../../language-reference/keywords/select-clause.md) yan tümcesinde gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e1b4f-108">This is accomplished in the [select](../../../language-reference/keywords/select-clause.md) clause.</span></span> <span data-ttu-id="e1b4f-109">Örneğin, aşağıdaki görevleri gerçekleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e1b4f-109">For example, you can perform the following tasks:</span></span>  
  
- <span data-ttu-id="e1b4f-110">Birden çok giriş dizisini yeni bir türü olan tek bir çıkış dizisinde birleştirin.</span><span class="sxs-lookup"><span data-stu-id="e1b4f-110">Merge multiple input sequences into a single output sequence that has a new type.</span></span>  
  
- <span data-ttu-id="e1b4f-111">Öğeleri kaynak dizisinde her öğenin yalnızca bir veya birkaç özelliğinden oluşan çıktı dizileri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e1b4f-111">Create output sequences whose elements consist of only one or several properties of each element in the source sequence.</span></span>  
  
- <span data-ttu-id="e1b4f-112">Öğeleri kaynak veriler üzerinde gerçekleştirilen işlemlerin sonuçlarından oluşan çıktı dizileri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e1b4f-112">Create output sequences whose elements consist of the results of operations performed on the source data.</span></span>  
  
- <span data-ttu-id="e1b4f-113">Farklı bir biçimde çıkış dizileri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e1b4f-113">Create output sequences in a different format.</span></span> <span data-ttu-id="e1b4f-114">Örneğin, SQL satırlarından veya metin dosyalarından gelen verileri XML'e dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1b4f-114">For example, you can transform data from SQL rows or text files into XML.</span></span>  
  
 <span data-ttu-id="e1b4f-115">Bunlar sadece birkaç örnektir.</span><span class="sxs-lookup"><span data-stu-id="e1b4f-115">These are just several examples.</span></span> <span data-ttu-id="e1b4f-116">Tabii ki, bu dönüşümler aynı sorguda çeşitli şekillerde birleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="e1b4f-116">Of course, these transformations can be combined in various ways in the same query.</span></span> <span data-ttu-id="e1b4f-117">Ayrıca, bir sorgunun çıkış sırası yeni bir sorgu için giriş sırası olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e1b4f-117">Furthermore, the output sequence of one query can be used as the input sequence for a new query.</span></span>  
  
## <a name="joining-multiple-inputs-into-one-output-sequence"></a><span data-ttu-id="e1b4f-118">Birden Çok Girdiyi Bir Çıkış Sırasına Katma</span><span class="sxs-lookup"><span data-stu-id="e1b4f-118">Joining Multiple Inputs into One Output Sequence</span></span>  
 <span data-ttu-id="e1b4f-119">Birden fazla giriş dizisinden öğeler içeren bir çıktı dizisi oluşturmak için linq sorgusu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1b4f-119">You can use a LINQ query to create an output sequence that contains elements from more than one input sequence.</span></span> <span data-ttu-id="e1b4f-120">Aşağıdaki örnek, iki bellek içi veri yapısının nasıl birleştirilebildiğini gösterir, ancak XML veya SQL veya DataSet kaynaklarından gelen verileri birleştirmek için aynı ilkeler uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="e1b4f-120">The following example shows how to combine two in-memory data structures, but the same principles can be applied to combine data from XML or SQL or DataSet sources.</span></span> <span data-ttu-id="e1b4f-121">Aşağıdaki iki sınıf türünü varsayalım:</span><span class="sxs-lookup"><span data-stu-id="e1b4f-121">Assume the following two class types:</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#7)]  
  
 <span data-ttu-id="e1b4f-122">Aşağıdaki örnekte sorgu gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="e1b4f-122">The following example shows the query:</span></span>  
  
 [!code-csharp[CSLinqGettingStarted#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#8)]  
  
 <span data-ttu-id="e1b4f-123">Daha fazla bilgi için [join yan tümcesi](../../../language-reference/keywords/join-clause.md) ve [seçme yan tümcesi'ne](../../../language-reference/keywords/select-clause.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="e1b4f-123">For more information, see [join clause](../../../language-reference/keywords/join-clause.md) and [select clause](../../../language-reference/keywords/select-clause.md).</span></span>  
  
## <a name="selecting-a-subset-of-each-source-element"></a><span data-ttu-id="e1b4f-124">Her Kaynak Öğesinin alt kümesini seçme</span><span class="sxs-lookup"><span data-stu-id="e1b4f-124">Selecting a Subset of each Source Element</span></span>  
 <span data-ttu-id="e1b4f-125">Kaynak dizideki her öğenin bir alt kümesini seçmenin iki birincil yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="e1b4f-125">There are two primary ways to select a subset of each element in the source sequence:</span></span>  
  
1. <span data-ttu-id="e1b4f-126">Kaynak öğenin yalnızca bir üyesini seçmek için nokta işlemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e1b4f-126">To select just one member of the source element, use the dot operation.</span></span> <span data-ttu-id="e1b4f-127">Aşağıdaki örnekte, bir `Customer` nesnenin adlı `City`dize de dahil olmak üzere birkaç ortak özellik içerdiğini varsayalım.</span><span class="sxs-lookup"><span data-stu-id="e1b4f-127">In the following example, assume that a `Customer` object contains several public properties including a string named `City`.</span></span> <span data-ttu-id="e1b4f-128">Yürütüldüğünde, bu sorgu dizeleri bir çıkış dizisi üretecek.</span><span class="sxs-lookup"><span data-stu-id="e1b4f-128">When executed, this query will produce an output sequence of strings.</span></span>  
  
    ```csharp
    var query = from cust in Customers  
                select cust.City;  
    ```  
  
2. <span data-ttu-id="e1b4f-129">Kaynak öğeden birden fazla özellik içeren öğeler oluşturmak için, adlandırılmış bir nesne veya anonim türiçeren bir nesne başlatılması nı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1b4f-129">To create elements that contain more than one property from the source element, you can use an object initializer with either a named object or an anonymous type.</span></span> <span data-ttu-id="e1b4f-130">Aşağıdaki örnek, her `Customer` öğeden iki özelliği kapsüllemek için anonim bir türün kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="e1b4f-130">The following example shows the use of an anonymous type to encapsulate two properties from each `Customer` element:</span></span>  
  
    ```csharp
    var query = from cust in Customer  
                select new {Name = cust.Name, City = cust.City};  
    ```  
  
 <span data-ttu-id="e1b4f-131">Daha fazla bilgi için [Nesne ve Koleksiyon Başlangıç Layıcıları](../../classes-and-structs/object-and-collection-initializers.md) ve Anonim [Türleri'ne](../../classes-and-structs/anonymous-types.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="e1b4f-131">For more information, see [Object and Collection Initializers](../../classes-and-structs/object-and-collection-initializers.md) and [Anonymous Types](../../classes-and-structs/anonymous-types.md).</span></span>  
  
## <a name="transforming-in-memory-objects-into-xml"></a><span data-ttu-id="e1b4f-132">Bellek İçi Nesneleri XML'e dönüştürme</span><span class="sxs-lookup"><span data-stu-id="e1b4f-132">Transforming in-Memory Objects into XML</span></span>  
 <span data-ttu-id="e1b4f-133">LINQ sorguları, bellek içi veri yapıları, SQL veritabanları, ADO.NET Datasets ve XML akışları veya belgeler arasındaki verileri dönüştürmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="e1b4f-133">LINQ queries make it easy to transform data between in-memory data structures, SQL databases, ADO.NET Datasets and XML streams or documents.</span></span> <span data-ttu-id="e1b4f-134">Aşağıdaki örnek, bellek içi veri yapısındaki nesneleri XML öğelerine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="e1b4f-134">The following example transforms objects in an in-memory data structure into XML elements.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#9)]  
  
 <span data-ttu-id="e1b4f-135">Kod aşağıdaki XML çıktısını üretir:</span><span class="sxs-lookup"><span data-stu-id="e1b4f-135">The code produces the following XML output:</span></span>  
  
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
  
 <span data-ttu-id="e1b4f-136">Daha fazla bilgi için [C# (LINQ-XML) xml ağaçları oluşturma'ya](./creating-xml-trees-linq-to-xml-2.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="e1b4f-136">For more information, see [Creating XML Trees in C# (LINQ to XML)](./creating-xml-trees-linq-to-xml-2.md).</span></span>  
  
## <a name="performing-operations-on-source-elements"></a><span data-ttu-id="e1b4f-137">Kaynak Öğeler Üzerinde İşlemler Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="e1b4f-137">Performing Operations on Source Elements</span></span>  
 <span data-ttu-id="e1b4f-138">Bir çıktı dizisi kaynak diziden herhangi bir öğe veya öğe özelliği içermeyebilir.</span><span class="sxs-lookup"><span data-stu-id="e1b4f-138">An output sequence might not contain any elements or element properties from the source sequence.</span></span> <span data-ttu-id="e1b4f-139">Çıktı bunun yerine, kaynak öğeleri girdi bağımsız değişkenleri olarak kullanılarak hesaplanan bir değer dizisi olabilir.</span><span class="sxs-lookup"><span data-stu-id="e1b4f-139">The output might instead be a sequence of values that is computed by using the source elements as input arguments.</span></span> <span data-ttu-id="e1b4f-140">Aşağıdaki basit sorgu, yürütüldüğünde, değerleri tür `double`elemanlarının kaynak sırasını temel alan bir hesaplamayı temsil eden bir dize dizisi verir.</span><span class="sxs-lookup"><span data-stu-id="e1b4f-140">The following simple query, when it is executed, outputs a sequence of strings whose values represent a calculation based on the source sequence of elements of type `double`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e1b4f-141">Sorgu başka bir etki alanına çevrilecekse, sorgu ifadelerindeki arama yöntemleri desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="e1b4f-141">Calling methods in query expressions is not supported if the query will be translated into some other domain.</span></span> <span data-ttu-id="e1b4f-142">Örneğin, SQL Server'ın bağlamı [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] olmadığı için sıradan bir C# yöntemini çağıramazsınız.</span><span class="sxs-lookup"><span data-stu-id="e1b4f-142">For example, you cannot call an ordinary C# method in [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] because SQL Server has no context for it.</span></span> <span data-ttu-id="e1b4f-143">Ancak, depolanan yordamları yöntemlerle eşleyebilir ve bunları çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1b4f-143">However, you can map stored procedures to methods and call those.</span></span> <span data-ttu-id="e1b4f-144">Daha fazla bilgi [için, Depolanan Yordamlar'a](../../../../framework/data/adonet/sql/linq/stored-procedures.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="e1b4f-144">For more information, see [Stored Procedures](../../../../framework/data/adonet/sql/linq/stored-procedures.md).</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#10)]  
  
## <a name="see-also"></a><span data-ttu-id="e1b4f-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e1b4f-145">See also</span></span>

- [<span data-ttu-id="e1b4f-146">Dil-Tümleşik Sorgu (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="e1b4f-146">Language-Integrated Query (LINQ) (C#)</span></span>](./index.md)
- [<span data-ttu-id="e1b4f-147">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="e1b4f-147">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="e1b4f-148">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="e1b4f-148">LINQ to DataSet</span></span>](../../../../framework/data/adonet/linq-to-dataset.md)
- [<span data-ttu-id="e1b4f-149">LinQ xml (C#) için</span><span class="sxs-lookup"><span data-stu-id="e1b4f-149">LINQ to XML (C#)</span></span>](./linq-to-xml-overview.md)
- [<span data-ttu-id="e1b4f-150">LINQ Sorgu İfadeleri</span><span class="sxs-lookup"><span data-stu-id="e1b4f-150">LINQ Query Expressions</span></span>](../../../linq/index.md)
- [<span data-ttu-id="e1b4f-151">yan tümceyi seçin</span><span class="sxs-lookup"><span data-stu-id="e1b4f-151">select clause</span></span>](../../../language-reference/keywords/select-clause.md)
