---
title: LINQ Sorgu İşlemlerinde Tür İlişkileri (C#)
ms.date: 07/20/2015
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
ms.openlocfilehash: 42519a74be1bd6934bc7a3304d154321697d128c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591014"
---
# <a name="type-relationships-in-linq-query-operations-c"></a><span data-ttu-id="db957-102">LINQ Sorgu İşlemlerinde Tür İlişkileri (C#)</span><span class="sxs-lookup"><span data-stu-id="db957-102">Type Relationships in LINQ Query Operations (C#)</span></span>
<span data-ttu-id="db957-103">Sorguları etkili bir şekilde yazmak için, bir bütün sorgu işlemindeki değişkenlerin türlerinin birbirleriyle ilişkisini anlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="db957-103">To write queries effectively, you should understand how types of the variables in a complete query operation all relate to each other.</span></span> <span data-ttu-id="db957-104">Bu ilişkileri anladıysanız, belgelerde [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] örnekleri ve kod örneklerini daha kolay anlarsınız.</span><span class="sxs-lookup"><span data-stu-id="db957-104">If you understand these relationships you will more easily comprehend the [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] samples and code examples in the documentation.</span></span> <span data-ttu-id="db957-105">Ayrıca, değişkenler, kullanılarak `var`örtük olarak yazıldığında ne olduğunu anlamış olursunuz.</span><span class="sxs-lookup"><span data-stu-id="db957-105">Furthermore, you will understand what occurs behind the scenes when variables are implicitly typed by using `var`.</span></span>  
  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]<span data-ttu-id="db957-106">sorgu işlemleri veri kaynağında, sorgunun kendisinde ve sorgu yürütmesinde kesin olarak türdedir.</span><span class="sxs-lookup"><span data-stu-id="db957-106">query operations are strongly typed in the data source, in the query itself, and in the query execution.</span></span> <span data-ttu-id="db957-107">Sorgudaki değişkenlerin türü, veri kaynağındaki öğelerin türüyle ve `foreach` deyimdeki yineleme değişkeni türüyle uyumlu olmalıdır).</span><span class="sxs-lookup"><span data-stu-id="db957-107">The type of the variables in the query must be compatible with the type of the elements in the data source and with the type of the iteration variable in the `foreach` statement.</span></span> <span data-ttu-id="db957-108">Bu güçlü yazma, tür hatalarının Kullanıcı tarafından karşılaşmadan önce düzeltilebilecekleri derleme zamanında yakalanmasını güvence altına alır.</span><span class="sxs-lookup"><span data-stu-id="db957-108">This strong typing guarantees that type errors are caught at compile time when they can be corrected before users encounter them.</span></span>  
  
 <span data-ttu-id="db957-109">Bu tür ilişkilerini göstermek için, aşağıdaki örneklerin çoğu tüm değişkenler için açık yazma kullanır.</span><span class="sxs-lookup"><span data-stu-id="db957-109">In order to demonstrate these type relationships, most of the examples that follow use explicit typing for all variables.</span></span> <span data-ttu-id="db957-110">Son örnek, [var](../../../language-reference/keywords/var.md)kullanarak örtük yazma kullandığınızda bile aynı ilkelerin nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="db957-110">The last example shows how the same principles apply even when you use implicit typing by using [var](../../../language-reference/keywords/var.md).</span></span>  
  
## <a name="queries-that-do-not-transform-the-source-data"></a><span data-ttu-id="db957-111">Kaynak verileri dönüştürmeksizin sorgular</span><span class="sxs-lookup"><span data-stu-id="db957-111">Queries that do not Transform the Source Data</span></span>  
 <span data-ttu-id="db957-112">Aşağıdaki çizimde, verilerde dönüştürme [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] gerçekleştirmeyen bir nesneler sorgu işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="db957-112">The following illustration shows a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] to Objects query operation that performs no transformations on the data.</span></span> <span data-ttu-id="db957-113">Kaynak bir dize dizisi içerir ve sorgu çıktısı da dizeler dizisidir.</span><span class="sxs-lookup"><span data-stu-id="db957-113">The source contains a sequence of strings and the query output is also a sequence of strings.</span></span>  
  
 ![LINQ sorgusundaki veri türlerinin ilişkisini gösteren diyagram.](./media/type-relationships-in-linq-query-operations/linq-query-data-type-relation.png)  
  
1. <span data-ttu-id="db957-115">Veri kaynağının tür bağımsız değişkeni, Aralık değişkeninin türünü belirler.</span><span class="sxs-lookup"><span data-stu-id="db957-115">The type argument of the data source determines the type of the range variable.</span></span>  
  
2. <span data-ttu-id="db957-116">Seçilen nesnenin türü, sorgu değişkeninin türünü belirler.</span><span class="sxs-lookup"><span data-stu-id="db957-116">The type of the object that is selected determines the type of the query variable.</span></span> <span data-ttu-id="db957-117">İşte `name` bir dize.</span><span class="sxs-lookup"><span data-stu-id="db957-117">Here `name` is a string.</span></span> <span data-ttu-id="db957-118">Bu nedenle, sorgu değişkeni bir `IEnumerable<string>`.</span><span class="sxs-lookup"><span data-stu-id="db957-118">Therefore, the query variable is an `IEnumerable<string>`.</span></span>  
  
3. <span data-ttu-id="db957-119">Sorgu değişkeni, `foreach` ifadesinde tekrarlanıyor.</span><span class="sxs-lookup"><span data-stu-id="db957-119">The query variable is iterated over in the `foreach` statement.</span></span> <span data-ttu-id="db957-120">Sorgu değişkeni bir dizeler dizisi olduğundan, yineleme değişkeni de bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="db957-120">Because the query variable is a sequence of strings, the iteration variable is also a string.</span></span>  
  
## <a name="queries-that-transform-the-source-data"></a><span data-ttu-id="db957-121">Kaynak verileri dönüştüren sorgular</span><span class="sxs-lookup"><span data-stu-id="db957-121">Queries that Transform the Source Data</span></span>  
 <span data-ttu-id="db957-122">Aşağıdaki çizimde, verilerde basit [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] bir dönüşüm gerçekleştiren bir sorgu işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="db957-122">The following illustration shows a [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] query operation that performs a simple transformation on the data.</span></span> <span data-ttu-id="db957-123">Sorgu, giriş olarak bir dizi `Customer` nesne alır ve `Name` yalnızca sonuç içindeki özelliği seçer.</span><span class="sxs-lookup"><span data-stu-id="db957-123">The query takes a sequence of `Customer` objects as input, and selects only the `Name` property in the result.</span></span> <span data-ttu-id="db957-124">`Name` Bir dize olduğundan, sorgu çıktı olarak bir dize dizisi üretir.</span><span class="sxs-lookup"><span data-stu-id="db957-124">Because `Name` is a string, the query produces a sequence of strings as output.</span></span>  
  
 ![Veri türünü dönüştüren bir sorgu gösteren diyagram.](./media/type-relationships-in-linq-query-operations/linq-query-transform-data-type.png)  
  
1. <span data-ttu-id="db957-126">Veri kaynağının tür bağımsız değişkeni, Aralık değişkeninin türünü belirler.</span><span class="sxs-lookup"><span data-stu-id="db957-126">The type argument of the data source determines the type of the range variable.</span></span>  
  
2. <span data-ttu-id="db957-127">İfade, `Name` tüm`Customer` nesne yerine özelliği döndürür. `select`</span><span class="sxs-lookup"><span data-stu-id="db957-127">The `select` statement returns the `Name` property instead of the complete `Customer` object.</span></span> <span data-ttu-id="db957-128">Bir dize olduğundan, `custNameQuery` `Customer`öğesinin tür bağımsız değişkeni değildir. `string` `Name`</span><span class="sxs-lookup"><span data-stu-id="db957-128">Because `Name` is a string, the type argument of `custNameQuery` is `string`, not `Customer`.</span></span>  
  
3. <span data-ttu-id="db957-129">Bir dize dizisi olduğundan `foreach` , döngünün yineleme değişkeni de bir `string`olmalıdır. `custNameQuery`</span><span class="sxs-lookup"><span data-stu-id="db957-129">Because `custNameQuery` is a sequence of strings, the `foreach` loop's iteration variable must also be a `string`.</span></span>  
  
 <span data-ttu-id="db957-130">Aşağıdaki çizimde biraz daha karmaşık bir dönüştürme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="db957-130">The following illustration shows a slightly more complex transformation.</span></span> <span data-ttu-id="db957-131">İfade, özgün `Customer` nesnenin yalnızca iki üyesini yakalayan bir anonim tür döndürür. `select`</span><span class="sxs-lookup"><span data-stu-id="db957-131">The `select` statement returns an anonymous type that captures just two members of the original `Customer` object.</span></span>  
  
 ![Veri türünü dönüştüren daha karmaşık bir sorgu gösteren diyagram.](./media/type-relationships-in-linq-query-operations/linq-complex-query-transform-data-type.png)  
  
1. <span data-ttu-id="db957-133">Veri kaynağının tür bağımsız değişkeni her zaman sorgudaki aralık değişkeninin türüdür.</span><span class="sxs-lookup"><span data-stu-id="db957-133">The type argument of the data source is always the type of the range variable in the query.</span></span>  
  
2. <span data-ttu-id="db957-134">İfade anonim bir tür oluşturduğundan, sorgu değişkeninin kullanılarak `var`örtük olarak yazılması gerekir. `select`</span><span class="sxs-lookup"><span data-stu-id="db957-134">Because the `select` statement produces an anonymous type, the query variable must be implicitly typed by using `var`.</span></span>  
  
3. <span data-ttu-id="db957-135">Sorgu değişkeninin türü örtük olduğundan, `foreach` döngüdeki yineleme değişkeni de örtük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="db957-135">Because the type of the query variable is implicit, the iteration variable in the `foreach` loop must also be implicit.</span></span>  
  
## <a name="letting-the-compiler-infer-type-information"></a><span data-ttu-id="db957-136">Derleyicinin tür bilgilerini çıkarmalarına izin verme</span><span class="sxs-lookup"><span data-stu-id="db957-136">Letting the compiler infer type information</span></span>  
 <span data-ttu-id="db957-137">Bir sorgu işlemindeki tür ilişkilerini anlamanız gerekse de, derleyicinin tüm işleri gerçekleştirmesini sağlamak için seçeneğiniz vardır.</span><span class="sxs-lookup"><span data-stu-id="db957-137">Although you should understand the type relationships in a query operation, you have the option to let the compiler do all the work for you.</span></span> <span data-ttu-id="db957-138">[Var](../../../language-reference/keywords/var.md) anahtar sözcüğü, bir sorgu işlemindeki herhangi bir yerel değişken için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="db957-138">The keyword [var](../../../language-reference/keywords/var.md) can be used for any local variable in a query operation.</span></span> <span data-ttu-id="db957-139">Aşağıdaki çizim, daha önce açıklanan örnek numarası 2 ' ye benzer.</span><span class="sxs-lookup"><span data-stu-id="db957-139">The following illustration is similar to example number 2 that was discussed earlier.</span></span> <span data-ttu-id="db957-140">Ancak, derleyici sorgu işlemindeki her değişken için güçlü tür sağlar.</span><span class="sxs-lookup"><span data-stu-id="db957-140">However, the compiler supplies the strong type for each variable in the query operation.</span></span>  
  
 ![Türü örtük olarak yazılan tür akışını gösteren diyagram.](./media/type-relationships-in-linq-query-operations/linq-type-flow-implicit-typing.png)  
  
 <span data-ttu-id="db957-142">Hakkında `var`daha fazla bilgi için bkz. [örtülü olarak yazılan yerel değişkenler](../../classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="db957-142">For more information about `var`, see [Implicitly Typed Local Variables](../../classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
