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
ms.openlocfilehash: 8dd57a43f814d7e41ec74af3eeb6d797fef41c9c
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73418626"
---
# <a name="data-transformations-with-linq-c"></a><span data-ttu-id="caa71-102">LINQ ile Veri Dönüştürmeler (C#)</span><span class="sxs-lookup"><span data-stu-id="caa71-102">Data Transformations with LINQ (C#)</span></span>
[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] <span data-ttu-id="caa71-103">yalnızca verileri alma hakkında değildir.</span><span class="sxs-lookup"><span data-stu-id="caa71-103">is not only about retrieving data.</span></span> <span data-ttu-id="caa71-104">Ayrıca, verileri dönüştürmek için güçlü bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="caa71-104">It is also a powerful tool for transforming data.</span></span> <span data-ttu-id="caa71-105">Bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgusu kullanarak, giriş olarak bir kaynak sırası kullanabilir ve yeni bir çıkış sırası oluşturmak için bunu birçok şekilde değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="caa71-105">By using a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query, you can use a source sequence as input and modify it in many ways to create a new output sequence.</span></span> <span data-ttu-id="caa71-106">Sıralamayı sıralama ve gruplama yoluyla öğeleri değiştirmeden değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="caa71-106">You can modify the sequence itself without modifying the elements themselves by sorting and grouping.</span></span> <span data-ttu-id="caa71-107">Ancak, [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgularının en güçlü özelliği yeni türler oluşturma olanağıdır.</span><span class="sxs-lookup"><span data-stu-id="caa71-107">But perhaps the most powerful feature of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries is the ability to create new types.</span></span> <span data-ttu-id="caa71-108">Bu, [Select](../../../language-reference/keywords/select-clause.md) yan tümcesinde gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="caa71-108">This is accomplished in the [select](../../../language-reference/keywords/select-clause.md) clause.</span></span> <span data-ttu-id="caa71-109">Örneğin, aşağıdaki görevleri gerçekleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="caa71-109">For example, you can perform the following tasks:</span></span>  
  
- <span data-ttu-id="caa71-110">Birden çok giriş dizisini yeni bir türe sahip tek bir çıkış dizisinde birleştirin.</span><span class="sxs-lookup"><span data-stu-id="caa71-110">Merge multiple input sequences into a single output sequence that has a new type.</span></span>  
  
- <span data-ttu-id="caa71-111">Öğeleri, kaynak dizideki her öğenin yalnızca bir veya birkaç özelliklerinden oluşan çıkış dizileri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="caa71-111">Create output sequences whose elements consist of only one or several properties of each element in the source sequence.</span></span>  
  
- <span data-ttu-id="caa71-112">Öğeleri, kaynak verilerde gerçekleştirilen işlemlerin sonuçlarından oluşan çıkış dizileri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="caa71-112">Create output sequences whose elements consist of the results of operations performed on the source data.</span></span>  
  
- <span data-ttu-id="caa71-113">Çıkış dizilerini farklı biçimde oluşturun.</span><span class="sxs-lookup"><span data-stu-id="caa71-113">Create output sequences in a different format.</span></span> <span data-ttu-id="caa71-114">Örneğin, verileri SQL satırlarından veya metin dosyalarından XML 'e dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="caa71-114">For example, you can transform data from SQL rows or text files into XML.</span></span>  
  
 <span data-ttu-id="caa71-115">Bunlar yalnızca birkaç örnektir.</span><span class="sxs-lookup"><span data-stu-id="caa71-115">These are just several examples.</span></span> <span data-ttu-id="caa71-116">Tabii ki, bu dönüşümler aynı sorgudaki çeşitli şekillerde birleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="caa71-116">Of course, these transformations can be combined in various ways in the same query.</span></span> <span data-ttu-id="caa71-117">Ayrıca, bir sorgunun çıkış sırası yeni bir sorgu için giriş sırası olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="caa71-117">Furthermore, the output sequence of one query can be used as the input sequence for a new query.</span></span>  
  
## <a name="joining-multiple-inputs-into-one-output-sequence"></a><span data-ttu-id="caa71-118">Birden Çok Girdiyi Bir Çıkış Sırasına Katma</span><span class="sxs-lookup"><span data-stu-id="caa71-118">Joining Multiple Inputs into One Output Sequence</span></span>  
 <span data-ttu-id="caa71-119">Birden fazla giriş dizisinin öğelerini içeren bir çıkış sırası oluşturmak için [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] bir sorgu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="caa71-119">You can use a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query to create an output sequence that contains elements from more than one input sequence.</span></span> <span data-ttu-id="caa71-120">Aşağıdaki örnek, iki bellek içi veri yapısının nasıl birleştirileceğini gösterir, ancak aynı ilkeler XML veya SQL veya veri kümesi kaynaklarından verileri birleştirmek için uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="caa71-120">The following example shows how to combine two in-memory data structures, but the same principles can be applied to combine data from XML or SQL or DataSet sources.</span></span> <span data-ttu-id="caa71-121">Aşağıdaki iki sınıf türünü varsayın:</span><span class="sxs-lookup"><span data-stu-id="caa71-121">Assume the following two class types:</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#7)]  
  
 <span data-ttu-id="caa71-122">Aşağıdaki örnekte sorgu gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="caa71-122">The following example shows the query:</span></span>  
  
 [!code-csharp[CSLinqGettingStarted#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#8)]  
  
 <span data-ttu-id="caa71-123">Daha fazla bilgi için bkz. [JOIN yan tümcesi](../../../language-reference/keywords/join-clause.md) ve [Select yan tümcesi](../../../language-reference/keywords/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="caa71-123">For more information, see [join clause](../../../language-reference/keywords/join-clause.md) and [select clause](../../../language-reference/keywords/select-clause.md).</span></span>  
  
## <a name="selecting-a-subset-of-each-source-element"></a><span data-ttu-id="caa71-124">Her Kaynak Öğesinin alt kümesini seçme</span><span class="sxs-lookup"><span data-stu-id="caa71-124">Selecting a Subset of each Source Element</span></span>  
 <span data-ttu-id="caa71-125">Kaynak dizideki her bir öğenin alt kümesini seçmek için iki temel yol vardır:</span><span class="sxs-lookup"><span data-stu-id="caa71-125">There are two primary ways to select a subset of each element in the source sequence:</span></span>  
  
1. <span data-ttu-id="caa71-126">Kaynak öğenin yalnızca bir üyesini seçmek için, nokta işlemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="caa71-126">To select just one member of the source element, use the dot operation.</span></span> <span data-ttu-id="caa71-127">Aşağıdaki örnekte, bir `Customer` nesnesinin `City`adlı bir dize de dahil olmak üzere birkaç ortak özellik içerdiğini varsayın.</span><span class="sxs-lookup"><span data-stu-id="caa71-127">In the following example, assume that a `Customer` object contains several public properties including a string named `City`.</span></span> <span data-ttu-id="caa71-128">Yürütüldüğünde, bu sorgu dizelerin çıkış dizisini üretir.</span><span class="sxs-lookup"><span data-stu-id="caa71-128">When executed, this query will produce an output sequence of strings.</span></span>  
  
    ```csharp
    var query = from cust in Customers  
                select cust.City;  
    ```  
  
2. <span data-ttu-id="caa71-129">Kaynak öğeden birden fazla özellik içeren öğeler oluşturmak için, bir nesne başlatıcısını adlandırılmış bir nesne veya anonim bir türle birlikte kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="caa71-129">To create elements that contain more than one property from the source element, you can use an object initializer with either a named object or an anonymous type.</span></span> <span data-ttu-id="caa71-130">Aşağıdaki örnek, her bir `Customer` öğesinden iki özelliği kapsüllemek için anonim bir türün kullanımını gösterir:</span><span class="sxs-lookup"><span data-stu-id="caa71-130">The following example shows the use of an anonymous type to encapsulate two properties from each `Customer` element:</span></span>  
  
    ```csharp
    var query = from cust in Customer  
                select new {Name = cust.Name, City = cust.City};  
    ```  
  
 <span data-ttu-id="caa71-131">Daha fazla bilgi için bkz. [nesne ve koleksiyon başlatıcıları](../../classes-and-structs/object-and-collection-initializers.md) ve [anonim türler](../../classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="caa71-131">For more information, see [Object and Collection Initializers](../../classes-and-structs/object-and-collection-initializers.md) and [Anonymous Types](../../classes-and-structs/anonymous-types.md).</span></span>  
  
## <a name="transforming-in-memory-objects-into-xml"></a><span data-ttu-id="caa71-132">Bellek İçi Nesneleri XML'e dönüştürme</span><span class="sxs-lookup"><span data-stu-id="caa71-132">Transforming in-Memory Objects into XML</span></span>  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] <span data-ttu-id="caa71-133">sorguları, bellek içi veri yapıları, SQL veritabanları, ADO.NET veri kümeleri ve XML akışları veya belgeler arasında veri dönüştürmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="caa71-133">queries make it easy to transform data between in-memory data structures, SQL databases, ADO.NET Datasets and XML streams or documents.</span></span> <span data-ttu-id="caa71-134">Aşağıdaki örnek, bellek içi veri yapısındaki nesneleri XML öğelerine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="caa71-134">The following example transforms objects in an in-memory data structure into XML elements.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#9)]  
  
 <span data-ttu-id="caa71-135">Kod aşağıdaki XML çıktısını üretir:</span><span class="sxs-lookup"><span data-stu-id="caa71-135">The code produces the following XML output:</span></span>  
  
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
  
 <span data-ttu-id="caa71-136">Daha fazla bilgi için bkz. [XML ağaçlarını oluşturma C# (LINQ to XML)](./creating-xml-trees-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="caa71-136">For more information, see [Creating XML Trees in C# (LINQ to XML)](./creating-xml-trees-linq-to-xml-2.md).</span></span>  
  
## <a name="performing-operations-on-source-elements"></a><span data-ttu-id="caa71-137">Kaynak Öğeler Üzerinde İşlemler Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="caa71-137">Performing Operations on Source Elements</span></span>  
 <span data-ttu-id="caa71-138">Çıkış sırası, kaynak dizisinden herhangi bir öğe veya öğe özelliği içermeyebilir.</span><span class="sxs-lookup"><span data-stu-id="caa71-138">An output sequence might not contain any elements or element properties from the source sequence.</span></span> <span data-ttu-id="caa71-139">Çıktı bunun yerine, kaynak öğeleri giriş bağımsız değişkenleri olarak kullanılarak hesaplanan bir değer dizisi olabilir.</span><span class="sxs-lookup"><span data-stu-id="caa71-139">The output might instead be a sequence of values that is computed by using the source elements as input arguments.</span></span> <span data-ttu-id="caa71-140">Aşağıdaki basit sorgu yürütüldüğünde, değerleri, `double`türündeki öğelerin kaynak dizisine göre hesaplamayı temsil eden bir dize dizisi çıkarır.</span><span class="sxs-lookup"><span data-stu-id="caa71-140">The following simple query, when it is executed, outputs a sequence of strings whose values represent a calculation based on the source sequence of elements of type `double`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="caa71-141">Sorgu başka bir etki alanına çevrilecektir sorgu ifadelerinde çağırma yöntemi desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="caa71-141">Calling methods in query expressions is not supported if the query will be translated into some other domain.</span></span> <span data-ttu-id="caa71-142">Örneğin, SQL Server hiçbir bağlamı olmadığından [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] sıradan C# bir yöntem çağrılamaz.</span><span class="sxs-lookup"><span data-stu-id="caa71-142">For example, you cannot call an ordinary C# method in [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] because SQL Server has no context for it.</span></span> <span data-ttu-id="caa71-143">Ancak, saklı yordamları yöntemlere eşleyebilir ve bunları çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="caa71-143">However, you can map stored procedures to methods and call those.</span></span> <span data-ttu-id="caa71-144">Daha fazla bilgi için bkz. [saklı yordamlar](../../../../framework/data/adonet/sql/linq/stored-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="caa71-144">For more information, see [Stored Procedures](../../../../framework/data/adonet/sql/linq/stored-procedures.md).</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#10)]  
  
## <a name="see-also"></a><span data-ttu-id="caa71-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="caa71-145">See also</span></span>

- [<span data-ttu-id="caa71-146">Dil ile tümleşik sorgu (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="caa71-146">Language-Integrated Query (LINQ) (C#)</span></span>](./index.md)
- [<span data-ttu-id="caa71-147">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="caa71-147">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="caa71-148">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="caa71-148">LINQ to DataSet</span></span>](../../../../framework/data/adonet/linq-to-dataset.md)
- [<span data-ttu-id="caa71-149">LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="caa71-149">LINQ to XML (C#)</span></span>](./linq-to-xml-overview.md)
- [<span data-ttu-id="caa71-150">LINQ sorgu Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="caa71-150">LINQ Query Expressions</span></span>](../../../linq/index.md)
- [<span data-ttu-id="caa71-151">select yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="caa71-151">select clause</span></span>](../../../language-reference/keywords/select-clause.md)
