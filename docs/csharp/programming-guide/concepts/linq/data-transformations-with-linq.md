---
title: LINQ ile Veri Dönüştürmeler (C#)
description: Verileri dönüştürmek Için C# ' de LINQ sorgularını nasıl kullanacağınızı öğrenin. Sıralama ve gruplama yaparak diziyi değiştirebilir ve select yan tümcesini kullanarak yeni türler oluşturabilirsiniz.
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
ms.openlocfilehash: af08938b6b8f169ded2180529c2b4aadebefef55
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558816"
---
# <a name="data-transformations-with-linq-c"></a><span data-ttu-id="67635-104">LINQ ile Veri Dönüştürmeler (C#)</span><span class="sxs-lookup"><span data-stu-id="67635-104">Data Transformations with LINQ (C#)</span></span>
<span data-ttu-id="67635-105">Dil ile tümleşik sorgu (LINQ) yalnızca veri alma hakkında değildir.</span><span class="sxs-lookup"><span data-stu-id="67635-105">Language-Integrated Query (LINQ) is not only about retrieving data.</span></span> <span data-ttu-id="67635-106">Ayrıca, verileri dönüştürmek için güçlü bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="67635-106">It is also a powerful tool for transforming data.</span></span> <span data-ttu-id="67635-107">Bir LINQ sorgusu kullanarak, giriş olarak bir kaynak sırası kullanabilir ve yeni bir çıkış sırası oluşturmak için bunu birçok şekilde değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="67635-107">By using a LINQ query, you can use a source sequence as input and modify it in many ways to create a new output sequence.</span></span> <span data-ttu-id="67635-108">Sıralamayı sıralama ve gruplama yoluyla öğeleri değiştirmeden değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="67635-108">You can modify the sequence itself without modifying the elements themselves by sorting and grouping.</span></span> <span data-ttu-id="67635-109">Ancak, LINQ sorgularının en güçlü özelliği de yeni türler oluşturma olanağıdır.</span><span class="sxs-lookup"><span data-stu-id="67635-109">But perhaps the most powerful feature of LINQ queries is the ability to create new types.</span></span> <span data-ttu-id="67635-110">Bu, [Select](../../../language-reference/keywords/select-clause.md) yan tümcesinde gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="67635-110">This is accomplished in the [select](../../../language-reference/keywords/select-clause.md) clause.</span></span> <span data-ttu-id="67635-111">Örneğin, aşağıdaki görevleri gerçekleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="67635-111">For example, you can perform the following tasks:</span></span>  
  
- <span data-ttu-id="67635-112">Birden çok giriş dizisini yeni bir türe sahip tek bir çıkış dizisinde birleştirin.</span><span class="sxs-lookup"><span data-stu-id="67635-112">Merge multiple input sequences into a single output sequence that has a new type.</span></span>  
  
- <span data-ttu-id="67635-113">Öğeleri, kaynak dizideki her öğenin yalnızca bir veya birkaç özelliklerinden oluşan çıkış dizileri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="67635-113">Create output sequences whose elements consist of only one or several properties of each element in the source sequence.</span></span>  
  
- <span data-ttu-id="67635-114">Öğeleri, kaynak verilerde gerçekleştirilen işlemlerin sonuçlarından oluşan çıkış dizileri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="67635-114">Create output sequences whose elements consist of the results of operations performed on the source data.</span></span>  
  
- <span data-ttu-id="67635-115">Çıkış dizilerini farklı biçimde oluşturun.</span><span class="sxs-lookup"><span data-stu-id="67635-115">Create output sequences in a different format.</span></span> <span data-ttu-id="67635-116">Örneğin, verileri SQL satırlarından veya metin dosyalarından XML 'e dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="67635-116">For example, you can transform data from SQL rows or text files into XML.</span></span>  
  
 <span data-ttu-id="67635-117">Bunlar yalnızca birkaç örnektir.</span><span class="sxs-lookup"><span data-stu-id="67635-117">These are just several examples.</span></span> <span data-ttu-id="67635-118">Tabii ki, bu dönüşümler aynı sorgudaki çeşitli şekillerde birleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="67635-118">Of course, these transformations can be combined in various ways in the same query.</span></span> <span data-ttu-id="67635-119">Ayrıca, bir sorgunun çıkış sırası yeni bir sorgu için giriş sırası olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="67635-119">Furthermore, the output sequence of one query can be used as the input sequence for a new query.</span></span>  
  
## <a name="joining-multiple-inputs-into-one-output-sequence"></a><span data-ttu-id="67635-120">Birden Çok Girdiyi Bir Çıkış Sırasına Katma</span><span class="sxs-lookup"><span data-stu-id="67635-120">Joining Multiple Inputs into One Output Sequence</span></span>  
 <span data-ttu-id="67635-121">Birden fazla giriş dizisinin öğelerini içeren bir çıkış sırası oluşturmak için bir LINQ sorgusu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="67635-121">You can use a LINQ query to create an output sequence that contains elements from more than one input sequence.</span></span> <span data-ttu-id="67635-122">Aşağıdaki örnek, iki bellek içi veri yapısının nasıl birleştirileceğini gösterir, ancak aynı ilkeler XML veya SQL veya veri kümesi kaynaklarından verileri birleştirmek için uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="67635-122">The following example shows how to combine two in-memory data structures, but the same principles can be applied to combine data from XML or SQL or DataSet sources.</span></span> <span data-ttu-id="67635-123">Aşağıdaki iki sınıf türünü varsayın:</span><span class="sxs-lookup"><span data-stu-id="67635-123">Assume the following two class types:</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#7)]  
  
 <span data-ttu-id="67635-124">Aşağıdaki örnekte sorgu gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="67635-124">The following example shows the query:</span></span>  
  
 [!code-csharp[CSLinqGettingStarted#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#8)]  
  
 <span data-ttu-id="67635-125">Daha fazla bilgi için bkz. [JOIN yan tümcesi](../../../language-reference/keywords/join-clause.md) ve [Select yan tümcesi](../../../language-reference/keywords/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="67635-125">For more information, see [join clause](../../../language-reference/keywords/join-clause.md) and [select clause](../../../language-reference/keywords/select-clause.md).</span></span>  
  
## <a name="selecting-a-subset-of-each-source-element"></a><span data-ttu-id="67635-126">Her Kaynak Öğesinin alt kümesini seçme</span><span class="sxs-lookup"><span data-stu-id="67635-126">Selecting a Subset of each Source Element</span></span>  
 <span data-ttu-id="67635-127">Kaynak dizideki her bir öğenin alt kümesini seçmek için iki temel yol vardır:</span><span class="sxs-lookup"><span data-stu-id="67635-127">There are two primary ways to select a subset of each element in the source sequence:</span></span>  
  
1. <span data-ttu-id="67635-128">Kaynak öğenin yalnızca bir üyesini seçmek için, nokta işlemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="67635-128">To select just one member of the source element, use the dot operation.</span></span> <span data-ttu-id="67635-129">Aşağıdaki örnekte, bir `Customer` nesnesinin adlı bir dize de dahil olmak üzere birkaç ortak özellik içerdiğini varsayın `City` .</span><span class="sxs-lookup"><span data-stu-id="67635-129">In the following example, assume that a `Customer` object contains several public properties including a string named `City`.</span></span> <span data-ttu-id="67635-130">Yürütüldüğünde, bu sorgu dizelerin çıkış dizisini üretir.</span><span class="sxs-lookup"><span data-stu-id="67635-130">When executed, this query will produce an output sequence of strings.</span></span>  
  
    ```csharp
    var query = from cust in Customers  
                select cust.City;  
    ```  
  
2. <span data-ttu-id="67635-131">Kaynak öğeden birden fazla özellik içeren öğeler oluşturmak için, bir nesne başlatıcısını adlandırılmış bir nesne veya anonim bir türle birlikte kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="67635-131">To create elements that contain more than one property from the source element, you can use an object initializer with either a named object or an anonymous type.</span></span> <span data-ttu-id="67635-132">Aşağıdaki örnek, her bir öğeden iki özelliği kapsüllemek için anonim bir türün kullanımını gösterir `Customer` :</span><span class="sxs-lookup"><span data-stu-id="67635-132">The following example shows the use of an anonymous type to encapsulate two properties from each `Customer` element:</span></span>  
  
    ```csharp
    var query = from cust in Customer  
                select new {Name = cust.Name, City = cust.City};  
    ```  
  
 <span data-ttu-id="67635-133">Daha fazla bilgi için bkz. [nesne ve koleksiyon başlatıcıları](../../classes-and-structs/object-and-collection-initializers.md) ve [anonim türler](../../classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="67635-133">For more information, see [Object and Collection Initializers](../../classes-and-structs/object-and-collection-initializers.md) and [Anonymous Types](../../classes-and-structs/anonymous-types.md).</span></span>  
  
## <a name="transforming-in-memory-objects-into-xml"></a><span data-ttu-id="67635-134">Bellek İçi Nesneleri XML'e dönüştürme</span><span class="sxs-lookup"><span data-stu-id="67635-134">Transforming in-Memory Objects into XML</span></span>  
 <span data-ttu-id="67635-135">LINQ sorguları, bellek içi veri yapıları, SQL veritabanları, ADO.NET veri kümeleri ve XML akışları veya belgeler arasında veri dönüştürmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="67635-135">LINQ queries make it easy to transform data between in-memory data structures, SQL databases, ADO.NET Datasets and XML streams or documents.</span></span> <span data-ttu-id="67635-136">Aşağıdaki örnek, bellek içi veri yapısındaki nesneleri XML öğelerine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="67635-136">The following example transforms objects in an in-memory data structure into XML elements.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#9)]  
  
 <span data-ttu-id="67635-137">Kod aşağıdaki XML çıktısını üretir:</span><span class="sxs-lookup"><span data-stu-id="67635-137">The code produces the following XML output:</span></span>  
  
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
  
 <span data-ttu-id="67635-138">Daha fazla bilgi için bkz. [C# ' de xml ağaçları oluşturma (LINQ to XML)](../../../../standard/linq/create-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="67635-138">For more information, see [Creating XML Trees in C# (LINQ to XML)](../../../../standard/linq/create-xml-trees.md).</span></span>  
  
## <a name="performing-operations-on-source-elements"></a><span data-ttu-id="67635-139">Kaynak Öğeler Üzerinde İşlemler Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="67635-139">Performing Operations on Source Elements</span></span>  
 <span data-ttu-id="67635-140">Çıkış sırası, kaynak dizisinden herhangi bir öğe veya öğe özelliği içermeyebilir.</span><span class="sxs-lookup"><span data-stu-id="67635-140">An output sequence might not contain any elements or element properties from the source sequence.</span></span> <span data-ttu-id="67635-141">Çıktı bunun yerine, kaynak öğeleri giriş bağımsız değişkenleri olarak kullanılarak hesaplanan bir değer dizisi olabilir.</span><span class="sxs-lookup"><span data-stu-id="67635-141">The output might instead be a sequence of values that is computed by using the source elements as input arguments.</span></span>

 <span data-ttu-id="67635-142">Aşağıdaki sorgu, dairelerin yarıçapı temsil eden bir sayı sırası alır, her yarıçap için alanı hesaplar ve Hesaplanan alanla biçimlendirilen dizeleri içeren bir çıkış sırası döndürür.</span><span class="sxs-lookup"><span data-stu-id="67635-142">The following query will take a sequence of numbers that represent radii of circles, calculate the area for each radius, and return an output sequence containing strings formatted with the calculated area.</span></span>

 <span data-ttu-id="67635-143">Çıkış sırası için her dize, [dize ilişkilendirme](../../../language-reference/tokens/interpolated.md)kullanılarak biçimlendirilir.</span><span class="sxs-lookup"><span data-stu-id="67635-143">Each string for the output sequence will be formatted using [string interpolation](../../../language-reference/tokens/interpolated.md).</span></span> <span data-ttu-id="67635-144">Bir enterpolasyonlu dize, `$` dizenin açılış tırnak işaretinin önünde olacaktır ve işlemler, enterpolasyonlu dizenin içine yerleştirilmiş küme ayraçları içinde gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="67635-144">An interpolated string will have a `$` in front of the string's opening quotation mark, and operations can be performed within curly braces placed inside the interpolated string.</span></span> <span data-ttu-id="67635-145">Bu işlemler gerçekleştirildikten sonra sonuçlar birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="67635-145">Once those operations are performed, the results will be concatenated.</span></span>
  
> [!NOTE]
> <span data-ttu-id="67635-146">Sorgu başka bir etki alanına çevrilecektir sorgu ifadelerinde çağırma yöntemi desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="67635-146">Calling methods in query expressions is not supported if the query will be translated into some other domain.</span></span> <span data-ttu-id="67635-147">Örneğin, SQL Server bir bağlamı olmadığından, içinde sıradan bir C# yöntemi çağrılamaz [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="67635-147">For example, you cannot call an ordinary C# method in [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] because SQL Server has no context for it.</span></span> <span data-ttu-id="67635-148">Ancak, saklı yordamları yöntemlere eşleyebilir ve bunları çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="67635-148">However, you can map stored procedures to methods and call those.</span></span> <span data-ttu-id="67635-149">Daha fazla bilgi için bkz. [saklı yordamlar](../../../../framework/data/adonet/sql/linq/stored-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="67635-149">For more information, see [Stored Procedures](../../../../framework/data/adonet/sql/linq/stored-procedures.md).</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#10)]  
  
## <a name="see-also"></a><span data-ttu-id="67635-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="67635-150">See also</span></span>

- [<span data-ttu-id="67635-151">Dil ile tümleşik sorgu (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="67635-151">Language-Integrated Query (LINQ) (C#)</span></span>](./index.md)
- [<span data-ttu-id="67635-152">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="67635-152">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="67635-153">LINQ - DataSet</span><span class="sxs-lookup"><span data-stu-id="67635-153">LINQ to DataSet</span></span>](../../../../framework/data/adonet/linq-to-dataset.md)
- [<span data-ttu-id="67635-154">LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="67635-154">LINQ to XML (C#)</span></span>](../../../../standard/linq/linq-xml-overview.md)
- [<span data-ttu-id="67635-155">LINQ sorgu Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="67635-155">LINQ Query Expressions</span></span>](../../../linq/index.md)
- [<span data-ttu-id="67635-156">Select yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="67635-156">select clause</span></span>](../../../language-reference/keywords/select-clause.md)
