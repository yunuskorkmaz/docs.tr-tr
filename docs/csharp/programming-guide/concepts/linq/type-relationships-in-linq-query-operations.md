---
title: "LINQ Sorgu İşlemlerinde Tür İlişkileri (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- inferring type information [LINQ in C#]
- data sources [LINQ in C#], type relationships
- queries [LINQ in C#], type relationships
- relationships [LINQ in C#]
- type relationships [LINQ in C#]
- variable relationships [LINQ in C#]
- type information inferred [LINQ in C#]
- data transformations [LINQ in C#]
- LINQ [C#], type relationships
ms.assetid: 99118938-d47c-4d7e-bb22-2657a9f95268
caps.latest.revision: "25"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a088a7f673a9f6aea7a0f50e18746259171bb7e2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="type-relationships-in-linq-query-operations-c"></a><span data-ttu-id="28615-102">LINQ Sorgu İşlemlerinde Tür İlişkileri (C#)</span><span class="sxs-lookup"><span data-stu-id="28615-102">Type Relationships in LINQ Query Operations (C#)</span></span>
<span data-ttu-id="28615-103">Sorguları etkili bir şekilde yazmak için tam bir sorgu işlemi tüm değişken türleri, birbirleriyle nasıl ilişkili olduğunu anlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="28615-103">To write queries effectively, you should understand how types of the variables in a complete query operation all relate to each other.</span></span> <span data-ttu-id="28615-104">Bu ilişkileri anlarsanız, daha kolay kavrama [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] belgelerinde örnekleri ve kod.</span><span class="sxs-lookup"><span data-stu-id="28615-104">If you understand these relationships you will more easily comprehend the [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] samples and code examples in the documentation.</span></span> <span data-ttu-id="28615-105">Ayrıca, değişkenleri kullanarak örtük olarak yazılan ne olacağı arka planda anlayabileceği `var`.</span><span class="sxs-lookup"><span data-stu-id="28615-105">Furthermore, you will understand what occurs behind the scenes when variables are implicitly typed by using `var`.</span></span>  
  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]<span data-ttu-id="28615-106">sorgu işlemleri, veri kaynağı, sorgu ve sorgu yürütmesi kesin türü belirtilmiş.</span><span class="sxs-lookup"><span data-stu-id="28615-106"> query operations are strongly typed in the data source, in the query itself, and in the query execution.</span></span> <span data-ttu-id="28615-107">Sorgu değişkenleri türünde veri kaynağındaki öğelerin türü ve yineleme değişkenin türü ile uyumlu olmalıdır `foreach` deyimi.</span><span class="sxs-lookup"><span data-stu-id="28615-107">The type of the variables in the query must be compatible with the type of the elements in the data source and with the type of the iteration variable in the `foreach` statement.</span></span> <span data-ttu-id="28615-108">Bu güçlü yazarak türü hataları kullanıcılar bunları karşılaşmadan önce zaman bunlar düzeltilebilir derleme zamanında yakalanır güvence altına alır.</span><span class="sxs-lookup"><span data-stu-id="28615-108">This strong typing guarantees that type errors are caught at compile time when they can be corrected before users encounter them.</span></span>  
  
 <span data-ttu-id="28615-109">Bu tür ilişkileri göstermek için açık tüm değişkenleri yazarak izleyin örnekler çoğunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="28615-109">In order to demonstrate these type relationships, most of the examples that follow use explicit typing for all variables.</span></span> <span data-ttu-id="28615-110">Son örnek bile kullanarak örtük yazarak kullandığınızda, aynı ilkeleri nasıl uygulandığını gösterir [var](../../../../csharp/language-reference/keywords/var.md).</span><span class="sxs-lookup"><span data-stu-id="28615-110">The last example shows how the same principles apply even when you use implicit typing by using [var](../../../../csharp/language-reference/keywords/var.md).</span></span>  
  
## <a name="queries-that-do-not-transform-the-source-data"></a><span data-ttu-id="28615-111">Veri kaynağını dönüştürülmez sorguları</span><span class="sxs-lookup"><span data-stu-id="28615-111">Queries that do not Transform the Source Data</span></span>  
 <span data-ttu-id="28615-112">Aşağıdaki çizimde gösterildiği bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] nesnelere sorgu verileri hiçbir dönüşümleri gerçekleştirir işlemi.</span><span class="sxs-lookup"><span data-stu-id="28615-112">The following illustration shows a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] to Objects query operation that performs no transformations on the data.</span></span> <span data-ttu-id="28615-113">Kaynak dizeleri dizisi içerir ve sorgu çıktısı da dizeleri dizisidir.</span><span class="sxs-lookup"><span data-stu-id="28615-113">The source contains a sequence of strings and the query output is also a sequence of strings.</span></span>  
  
 <span data-ttu-id="28615-114">![İlişki veri türleri bir LINQ Sorgu](../../../../csharp/programming-guide/concepts/linq/media/linq_flow1.png "LINQ_flow1")</span><span class="sxs-lookup"><span data-stu-id="28615-114">![Relation of data types in a LINQ query](../../../../csharp/programming-guide/concepts/linq/media/linq_flow1.png "LINQ_flow1")</span></span>  
  
1.  <span data-ttu-id="28615-115">Veri kaynağının tür bağımsız değişkeni aralık değişkeninin türünü belirler.</span><span class="sxs-lookup"><span data-stu-id="28615-115">The type argument of the data source determines the type of the range variable.</span></span>  
  
2.  <span data-ttu-id="28615-116">Seçili nesne türünü sorgu değişken türünü belirler.</span><span class="sxs-lookup"><span data-stu-id="28615-116">The type of the object that is selected determines the type of the query variable.</span></span> <span data-ttu-id="28615-117">Burada `name` bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="28615-117">Here `name` is a string.</span></span> <span data-ttu-id="28615-118">Bu nedenle, sorgu değişkeni, bir `IEnumerable` \<dize >.</span><span class="sxs-lookup"><span data-stu-id="28615-118">Therefore, the query variable is an `IEnumerable`\<string>.</span></span>  
  
3.  <span data-ttu-id="28615-119">İçinde üzerinden sorgu değişkeni yinelendiğinde `foreach` deyimi.</span><span class="sxs-lookup"><span data-stu-id="28615-119">The query variable is iterated over in the `foreach` statement.</span></span> <span data-ttu-id="28615-120">Sorgu değişkeni bir dizi dize olduğundan, yineleme değişkeni de bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="28615-120">Because the query variable is a sequence of strings, the iteration variable is also a string.</span></span>  
  
## <a name="queries-that-transform-the-source-data"></a><span data-ttu-id="28615-121">Kaynak veri dönüştürme sorguları</span><span class="sxs-lookup"><span data-stu-id="28615-121">Queries that Transform the Source Data</span></span>  
 <span data-ttu-id="28615-122">Aşağıdaki çizimde gösterildiği bir [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] sorgu basit bir dönüşüm verileri üzerindeki işlevini işlemi.</span><span class="sxs-lookup"><span data-stu-id="28615-122">The following illustration shows a [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] query operation that performs a simple transformation on the data.</span></span> <span data-ttu-id="28615-123">Sorgu bir dizisini alır `Customer` nesneleri giriş olarak ve yalnızca seçer `Name` sonucun bir özellik.</span><span class="sxs-lookup"><span data-stu-id="28615-123">The query takes a sequence of `Customer` objects as input, and selects only the `Name` property in the result.</span></span> <span data-ttu-id="28615-124">Çünkü `Name` bir dize, dize dizisi çıktı olarak bir sorgu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="28615-124">Because `Name` is a string, the query produces a sequence of strings as output.</span></span>  
  
 <span data-ttu-id="28615-125">![Veri türü dönüşümleri bir sorgu](../../../../csharp/programming-guide/concepts/linq/media/linq_flow2.png "LINQ_flow2")</span><span class="sxs-lookup"><span data-stu-id="28615-125">![A query that transforms the data type](../../../../csharp/programming-guide/concepts/linq/media/linq_flow2.png "LINQ_flow2")</span></span>  
  
1.  <span data-ttu-id="28615-126">Veri kaynağının tür bağımsız değişkeni aralık değişkeninin türünü belirler.</span><span class="sxs-lookup"><span data-stu-id="28615-126">The type argument of the data source determines the type of the range variable.</span></span>  
  
2.  <span data-ttu-id="28615-127">`select` Deyiminin döndüreceği `Name` özelliği tam yerine `Customer` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="28615-127">The `select` statement returns the `Name` property instead of the complete `Customer` object.</span></span> <span data-ttu-id="28615-128">Çünkü `Name` tür bağımsız değişkeni bir dize `custNameQuery` olan `string`değil `Customer`.</span><span class="sxs-lookup"><span data-stu-id="28615-128">Because `Name` is a string, the type argument of `custNameQuery` is `string`, not `Customer`.</span></span>  
  
3.  <span data-ttu-id="28615-129">Çünkü `custNameQuery` dizeleri dizisidir `foreach` döngünün yineleme değişkeni de olmalıdır bir `string`.</span><span class="sxs-lookup"><span data-stu-id="28615-129">Because `custNameQuery` is a sequence of strings, the `foreach` loop's iteration variable must also be a `string`.</span></span>  
  
 <span data-ttu-id="28615-130">Aşağıdaki çizimde biraz daha karmaşık bir dönüşüm gösterir.</span><span class="sxs-lookup"><span data-stu-id="28615-130">The following illustration shows a slightly more complex transformation.</span></span> <span data-ttu-id="28615-131">`select` Deyimi yalnızca iki üyeleri özgün yakalar anonim bir tür döndürür `Customer` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="28615-131">The `select` statement returns an anonymous type that captures just two members of the original `Customer` object.</span></span>  
  
 <span data-ttu-id="28615-132">![Veri türü dönüşümleri bir sorgu](../../../../csharp/programming-guide/concepts/linq/media/linq_flow3.png "LINQ_flow3")</span><span class="sxs-lookup"><span data-stu-id="28615-132">![A query that transforms the data type](../../../../csharp/programming-guide/concepts/linq/media/linq_flow3.png "LINQ_flow3")</span></span>  
  
1.  <span data-ttu-id="28615-133">Tür bağımsız değişkeni veri kaynağının her zaman sorgu aralık değişkeni türüdür.</span><span class="sxs-lookup"><span data-stu-id="28615-133">The type argument of the data source is always the type of the range variable in the query.</span></span>  
  
2.  <span data-ttu-id="28615-134">Çünkü `select` bildirimi üreten anonim bir tür, sorgu değişkeni kullanarak örtük olarak yazılmalıdır `var`.</span><span class="sxs-lookup"><span data-stu-id="28615-134">Because the `select` statement produces an anonymous type, the query variable must be implicitly typed by using `var`.</span></span>  
  
3.  <span data-ttu-id="28615-135">Sorgu değişkeninin türü örtük, olduğundan yineleme değişkeni `foreach` döngü de örtük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="28615-135">Because the type of the query variable is implicit, the iteration variable in the `foreach` loop must also be implicit.</span></span>  
  
## <a name="letting-the-compiler-infer-type-information"></a><span data-ttu-id="28615-136">Tür bilgileri Infer derleyici izin vererek</span><span class="sxs-lookup"><span data-stu-id="28615-136">Letting the compiler infer type information</span></span>  
 <span data-ttu-id="28615-137">Bir sorgu işlemi türü ilişkilerde anlamalısınız olmamakla birlikte, tüm iş bunu derleyici izin verme seçeneğini vardır.</span><span class="sxs-lookup"><span data-stu-id="28615-137">Although you should understand the type relationships in a query operation, you have the option to let the compiler do all the work for you.</span></span> <span data-ttu-id="28615-138">Anahtar sözcüğü [var](../../../../csharp/language-reference/keywords/var.md) herhangi bir yerel değişken bir sorgu işlemi olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="28615-138">The keyword [var](../../../../csharp/language-reference/keywords/var.md) can be used for any local variable in a query operation.</span></span> <span data-ttu-id="28615-139">Aşağıdaki çizimde, yukarıda açıklanan örnek sayısı için 2 benzer.</span><span class="sxs-lookup"><span data-stu-id="28615-139">The following illustration is similar to example number 2 that was discussed earlier.</span></span> <span data-ttu-id="28615-140">Ancak, sorgu işlemi her bir değişken için güçlü tür derleyici sağlar.</span><span class="sxs-lookup"><span data-stu-id="28615-140">However, the compiler supplies the strong type for each variable in the query operation.</span></span>  
  
 <span data-ttu-id="28615-141">![Örtülü yazma ile akış türü](../../../../csharp/programming-guide/concepts/linq/media/linq_flow4.png "LINQ_flow4")</span><span class="sxs-lookup"><span data-stu-id="28615-141">![Type flow with implicit typing](../../../../csharp/programming-guide/concepts/linq/media/linq_flow4.png "LINQ_flow4")</span></span>  
  
 <span data-ttu-id="28615-142">Hakkında daha fazla bilgi için `var`, bkz: [örtük olarak yazılan yerel değişkenler](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="28615-142">For more information about `var`, see [Implicitly Typed Local Variables](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28615-143">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="28615-143">See Also</span></span>  
 [<span data-ttu-id="28615-144">C# üzerinde LINQ ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="28615-144">Getting Started with LINQ in C#</span></span>](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
