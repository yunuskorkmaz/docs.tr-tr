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
ms.openlocfilehash: 5928478518b0bc1eb498381567d52d5ddba4d8b7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61702444"
---
# <a name="data-transformations-with-linq-c"></a><span data-ttu-id="d3071-102">LINQ ile Veri Dönüştürmeler (C#)</span><span class="sxs-lookup"><span data-stu-id="d3071-102">Data Transformations with LINQ (C#)</span></span>
[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] <span data-ttu-id="d3071-103">yalnızca veri alma hakkında değil.</span><span class="sxs-lookup"><span data-stu-id="d3071-103">is not only about retrieving data.</span></span> <span data-ttu-id="d3071-104">Veri dönüştürme için de güçlü bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="d3071-104">It is also a powerful tool for transforming data.</span></span> <span data-ttu-id="d3071-105">Kullanarak bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu, giriş ve yeni bir çıkış dizisi oluşturmak için birçok şekilde değiştirme gibi bir kaynak sırası kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d3071-105">By using a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query, you can use a source sequence as input and modify it in many ways to create a new output sequence.</span></span> <span data-ttu-id="d3071-106">Öğeleri sıralama ve gruplandırma değiştirmeden dizisi kendisini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d3071-106">You can modify the sequence itself without modifying the elements themselves by sorting and grouping.</span></span> <span data-ttu-id="d3071-107">Ancak belki de en güçlü özelliğidir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgulardır yeni türleri oluşturma olanağı.</span><span class="sxs-lookup"><span data-stu-id="d3071-107">But perhaps the most powerful feature of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries is the ability to create new types.</span></span> <span data-ttu-id="d3071-108">Bu, gerçekleştirilir [seçin](../../../../csharp/language-reference/keywords/select-clause.md) yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="d3071-108">This is accomplished in the [select](../../../../csharp/language-reference/keywords/select-clause.md) clause.</span></span> <span data-ttu-id="d3071-109">Örneğin, aşağıdaki görevleri gerçekleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d3071-109">For example, you can perform the following tasks:</span></span>  
  
- <span data-ttu-id="d3071-110">Birden çok giriş dizilerini yeni bir türü olan bir tek bir çıkış sırasına birleştirin.</span><span class="sxs-lookup"><span data-stu-id="d3071-110">Merge multiple input sequences into a single output sequence that has a new type.</span></span>  
  
- <span data-ttu-id="d3071-111">Öğeleri kaynak sırasındaki her öğenin yalnızca bir veya birkaç özellikleri oluşur çıkış sıraları oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d3071-111">Create output sequences whose elements consist of only one or several properties of each element in the source sequence.</span></span>  
  
- <span data-ttu-id="d3071-112">Kaynak veriler üzerinde gerçekleştirilen işlemlerin sonuçlarını öğeleri oluşur çıkış sıraları oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d3071-112">Create output sequences whose elements consist of the results of operations performed on the source data.</span></span>  
  
- <span data-ttu-id="d3071-113">Çıkış sıraları farklı bir biçimde oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d3071-113">Create output sequences in a different format.</span></span> <span data-ttu-id="d3071-114">Örneğin, verileri SQL satırları veya metin dosyalarından XML'e dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d3071-114">For example, you can transform data from SQL rows or text files into XML.</span></span>  
  
 <span data-ttu-id="d3071-115">Bunlar yalnızca birkaç örnektir.</span><span class="sxs-lookup"><span data-stu-id="d3071-115">These are just several examples.</span></span> <span data-ttu-id="d3071-116">Elbette, bu dönüştürmeleri, çeşitli yollarla aynı sorguda birleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="d3071-116">Of course, these transformations can be combined in various ways in the same query.</span></span> <span data-ttu-id="d3071-117">Ayrıca, bir sorgu çıkış dizisi, yeni bir sorgu için giriş dizisi kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d3071-117">Furthermore, the output sequence of one query can be used as the input sequence for a new query.</span></span>  
  
## <a name="joining-multiple-inputs-into-one-output-sequence"></a><span data-ttu-id="d3071-118">Birden Çok Girdiyi Bir Çıkış Sırasına Katma</span><span class="sxs-lookup"><span data-stu-id="d3071-118">Joining Multiple Inputs into One Output Sequence</span></span>  
 <span data-ttu-id="d3071-119">Kullanabileceğiniz bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] birden fazla giriş dizisinin öğeleri içeren bir çıkış dizisi oluşturmak için sorgu.</span><span class="sxs-lookup"><span data-stu-id="d3071-119">You can use a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query to create an output sequence that contains elements from more than one input sequence.</span></span> <span data-ttu-id="d3071-120">Aşağıdaki örnek, iki bellek içi veri yapılarını birleştirilecek gösterilmektedir, ancak aynı ilkeler, XML veya SQL veya veri kaynaklarından alınan verileri birleştirmek için uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="d3071-120">The following example shows how to combine two in-memory data structures, but the same principles can be applied to combine data from XML or SQL or DataSet sources.</span></span> <span data-ttu-id="d3071-121">Aşağıdaki iki sınıf türleri varsayın:</span><span class="sxs-lookup"><span data-stu-id="d3071-121">Assume the following two class types:</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#7)]  
  
 <span data-ttu-id="d3071-122">Aşağıdaki örnek sorgu gösterir:</span><span class="sxs-lookup"><span data-stu-id="d3071-122">The following example shows the query:</span></span>  
  
 [!code-csharp[CSLinqGettingStarted#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#8)]  
  
 <span data-ttu-id="d3071-123">Daha fazla bilgi için [JOIN yan tümcesi](../../../../csharp/language-reference/keywords/join-clause.md) ve [select yan tümcesi](../../../../csharp/language-reference/keywords/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="d3071-123">For more information, see [join clause](../../../../csharp/language-reference/keywords/join-clause.md) and [select clause](../../../../csharp/language-reference/keywords/select-clause.md).</span></span>  
  
## <a name="selecting-a-subset-of-each-source-element"></a><span data-ttu-id="d3071-124">Her Kaynak Öğesinin alt kümesini seçme</span><span class="sxs-lookup"><span data-stu-id="d3071-124">Selecting a Subset of each Source Element</span></span>  
 <span data-ttu-id="d3071-125">Kaynak dizideki her öğe kümesini seçmek için iki temel yol vardır:</span><span class="sxs-lookup"><span data-stu-id="d3071-125">There are two primary ways to select a subset of each element in the source sequence:</span></span>  
  
1. <span data-ttu-id="d3071-126">Kaynak öğesi yalnızca bir üye seçmek için nokta işlemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="d3071-126">To select just one member of the source element, use the dot operation.</span></span> <span data-ttu-id="d3071-127">Aşağıdaki örnekte, varsayımında bir `Customer` nesnesini içeren bir dize adlı de dahil olmak üzere birkaç ortak özellikler `City`.</span><span class="sxs-lookup"><span data-stu-id="d3071-127">In the following example, assume that a `Customer` object contains several public properties including a string named `City`.</span></span> <span data-ttu-id="d3071-128">Bu sorgu yürütüldüğünde, dize bir çıkış sırası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d3071-128">When executed, this query will produce an output sequence of strings.</span></span>  
  
    ```csharp
    var query = from cust in Customers  
                select cust.City;  
    ```  
  
2. <span data-ttu-id="d3071-129">Kaynak öğesi birden fazla özelliği içeren öğeler oluşturmak için bir nesne Başlatıcı adlandırılmış bir nesneye veya anonim bir tür ile kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d3071-129">To create elements that contain more than one property from the source element, you can use an object initializer with either a named object or an anonymous type.</span></span> <span data-ttu-id="d3071-130">Aşağıdaki örnek her iki özellik yalıtılacak anonim bir türün kullanımı gösterilmektedir `Customer` öğesi:</span><span class="sxs-lookup"><span data-stu-id="d3071-130">The following example shows the use of an anonymous type to encapsulate two properties from each `Customer` element:</span></span>  
  
    ```csharp
    var query = from cust in Customer  
                select new {Name = cust.Name, City = cust.City};  
    ```  
  
 <span data-ttu-id="d3071-131">Daha fazla bilgi için [nesne ve koleksiyon başlatıcıları](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md) ve [anonim türler](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="d3071-131">For more information, see [Object and Collection Initializers](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md) and [Anonymous Types](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span>  
  
## <a name="transforming-in-memory-objects-into-xml"></a><span data-ttu-id="d3071-132">Bellek İçi Nesneleri XML'e dönüştürme</span><span class="sxs-lookup"><span data-stu-id="d3071-132">Transforming in-Memory Objects into XML</span></span>  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] <span data-ttu-id="d3071-133">sorguları bellek içi veri yapıları, SQL veritabanları arasında verileri dönüştürmek kolaylaştırır [!INCLUDE[vstecado](~/includes/vstecado-md.md)] veri kümeleri ve XML akışlarını veya belgeler.</span><span class="sxs-lookup"><span data-stu-id="d3071-133">queries make it easy to transform data between in-memory data structures, SQL databases, [!INCLUDE[vstecado](~/includes/vstecado-md.md)] Datasets and XML streams or documents.</span></span> <span data-ttu-id="d3071-134">Aşağıdaki örnek, nesneleri bir bellek içi veri yapısı XML öğeleri dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="d3071-134">The following example transforms objects in an in-memory data structure into XML elements.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#9)]  
  
 <span data-ttu-id="d3071-135">Kod aşağıdaki XML çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="d3071-135">The code produces the following XML output:</span></span>  
  
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
  
 <span data-ttu-id="d3071-136">Daha fazla bilgi için [C# (LINQ to XML) XML ağaçları oluşturma](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="d3071-136">For more information, see [Creating XML Trees in C# (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees-linq-to-xml-2.md).</span></span>  
  
## <a name="performing-operations-on-source-elements"></a><span data-ttu-id="d3071-137">Kaynak Öğeler Üzerinde İşlemler Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="d3071-137">Performing Operations on Source Elements</span></span>  
 <span data-ttu-id="d3071-138">Bir çıkış dizisi, herhangi bir öğe veya öğe özellikleri için kaynak sırasından içermeyebilir.</span><span class="sxs-lookup"><span data-stu-id="d3071-138">An output sequence might not contain any elements or element properties from the source sequence.</span></span> <span data-ttu-id="d3071-139">Çıkışı, bunun yerine kaynak öğeleri giriş bağımsız değişkeni kullanarak hesaplanan değerler bir dizi olabilir.</span><span class="sxs-lookup"><span data-stu-id="d3071-139">The output might instead be a sequence of values that is computed by using the source elements as input arguments.</span></span> <span data-ttu-id="d3071-140">Yürütüldüğünde, aşağıdaki basit sorgu, bir dizi dize değerleri temsil eden türünde öğeler kaynak dizi temel hesaplama çıkarır `double`.</span><span class="sxs-lookup"><span data-stu-id="d3071-140">The following simple query, when it is executed, outputs a sequence of strings whose values represent a calculation based on the source sequence of elements of type `double`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d3071-141">Sorgu başka bir etki alanına çevrilir, sorgu ifadelerinde yöntem çağırma desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="d3071-141">Calling methods in query expressions is not supported if the query will be translated into some other domain.</span></span> <span data-ttu-id="d3071-142">Örneğin, bir normal C# tuto metodu nelze vyvolat [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] SQL Server için hiçbir bağlam olduğundan.</span><span class="sxs-lookup"><span data-stu-id="d3071-142">For example, you cannot call an ordinary C# method in [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] because SQL Server has no context for it.</span></span> <span data-ttu-id="d3071-143">Ancak, eşleştirme yöntemleri için saklı yordamlar ve bu çağırın.</span><span class="sxs-lookup"><span data-stu-id="d3071-143">However, you can map stored procedures to methods and call those.</span></span> <span data-ttu-id="d3071-144">Daha fazla bilgi için [saklı yordamlar](../../../../framework/data/adonet/sql/linq/stored-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="d3071-144">For more information, see [Stored Procedures](../../../../framework/data/adonet/sql/linq/stored-procedures.md).</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#10)]  
  
## <a name="see-also"></a><span data-ttu-id="d3071-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3071-145">See also</span></span>

- [<span data-ttu-id="d3071-146">Dil ile tümleşik sorgu (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d3071-146">Language-Integrated Query (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="d3071-147">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="d3071-147">LINQ to SQL</span></span>](../../../../../docs/framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="d3071-148">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="d3071-148">LINQ to DataSet</span></span>](../../../../framework/data/adonet/linq-to-dataset.md)
- [<span data-ttu-id="d3071-149">LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="d3071-149">LINQ to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)
- [<span data-ttu-id="d3071-150">LINQ Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="d3071-150">LINQ Query Expressions</span></span>](../../../../csharp/programming-guide/linq-query-expressions/index.md)
- [<span data-ttu-id="d3071-151">select yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="d3071-151">select clause</span></span>](../../../../csharp/language-reference/keywords/select-clause.md)
