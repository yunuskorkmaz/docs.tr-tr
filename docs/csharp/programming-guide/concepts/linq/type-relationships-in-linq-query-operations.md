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
ms.openlocfilehash: 41853e6858fae9e8d449aeed95a6a84f343d5874
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635619"
---
# <a name="type-relationships-in-linq-query-operations-c"></a><span data-ttu-id="85785-102">LINQ Sorgu İşlemlerinde Tür İlişkileri (C#)</span><span class="sxs-lookup"><span data-stu-id="85785-102">Type Relationships in LINQ Query Operations (C#)</span></span>
<span data-ttu-id="85785-103">Sorguları etkili bir şekilde yazmak için, tam bir sorgu işlemindeki değişken türlerinin birbiriyle nasıl ilişkili olduğunu anlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="85785-103">To write queries effectively, you should understand how types of the variables in a complete query operation all relate to each other.</span></span> <span data-ttu-id="85785-104">Bu ilişkileri anlarsanız, belgelerdeki LINQ örneklerini ve kod örneklerini daha kolay kavrarsınız.</span><span class="sxs-lookup"><span data-stu-id="85785-104">If you understand these relationships you will more easily comprehend the LINQ samples and code examples in the documentation.</span></span> <span data-ttu-id="85785-105">Ayrıca, değişkenler kullanılarak örtülü olarak yazıldığında perde arkasında neler oluştuğunu `var`anlayacaksınız.</span><span class="sxs-lookup"><span data-stu-id="85785-105">Furthermore, you will understand what occurs behind the scenes when variables are implicitly typed by using `var`.</span></span>  
  
 <span data-ttu-id="85785-106">LINQ sorgu işlemleri güçlü veri kaynağı, sorgu kendisi ve sorgu yürütme olarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="85785-106">LINQ query operations are strongly typed in the data source, in the query itself, and in the query execution.</span></span> <span data-ttu-id="85785-107">Sorgudaki değişkenlerin türü, veri kaynağındaki öğelerin türüyle ve `foreach` deyimdeki yineleme değişkeninin türüyle uyumlu olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="85785-107">The type of the variables in the query must be compatible with the type of the elements in the data source and with the type of the iteration variable in the `foreach` statement.</span></span> <span data-ttu-id="85785-108">Bu güçlü yazım hatası, tür hatalarının, kullanıcılar bunlarla karşılaşmadan önce düzeltilmedikleri zaman derleme zamanında yakalandığını garanti eder.</span><span class="sxs-lookup"><span data-stu-id="85785-108">This strong typing guarantees that type errors are caught at compile time when they can be corrected before users encounter them.</span></span>  
  
 <span data-ttu-id="85785-109">Bu tür ilişkileri göstermek için, izleyen örneklerin çoğu tüm değişkenler için açık yazma kullanır.</span><span class="sxs-lookup"><span data-stu-id="85785-109">In order to demonstrate these type relationships, most of the examples that follow use explicit typing for all variables.</span></span> <span data-ttu-id="85785-110">Son örnek, [var'ı](../../../language-reference/keywords/var.md)kullanarak örtülü yazı yı kullandığınızda bile aynı ilkelerin nasıl uygulandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="85785-110">The last example shows how the same principles apply even when you use implicit typing by using [var](../../../language-reference/keywords/var.md).</span></span>  
  
## <a name="queries-that-do-not-transform-the-source-data"></a><span data-ttu-id="85785-111">Kaynak Verileri Dönüştürmeyan Sorgular</span><span class="sxs-lookup"><span data-stu-id="85785-111">Queries that do not Transform the Source Data</span></span>  
 <span data-ttu-id="85785-112">Aşağıdaki resimde, verilerde dönüşüm olmayan nesneler sorgu işlemi için bir LINQ gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="85785-112">The following illustration shows a LINQ to Objects query operation that performs no transformations on the data.</span></span> <span data-ttu-id="85785-113">Kaynak dizeleri bir dizi içerir ve sorgu çıktısı da dizeleri bir dizidir.</span><span class="sxs-lookup"><span data-stu-id="85785-113">The source contains a sequence of strings and the query output is also a sequence of strings.</span></span>  
  
 ![LINQ sorgusundaki veri türlerinin ilişkisini gösteren diyagram.](./media/type-relationships-in-linq-query-operations/linq-query-data-type-relation.png)  
  
1. <span data-ttu-id="85785-115">Veri kaynağının tür bağımsız değişkeni aralık değişkeninin türünü belirler.</span><span class="sxs-lookup"><span data-stu-id="85785-115">The type argument of the data source determines the type of the range variable.</span></span>  
  
2. <span data-ttu-id="85785-116">Seçili nesnenin türü sorgu değişkeninin türünü belirler.</span><span class="sxs-lookup"><span data-stu-id="85785-116">The type of the object that is selected determines the type of the query variable.</span></span> <span data-ttu-id="85785-117">İşte `name` bir ip.</span><span class="sxs-lookup"><span data-stu-id="85785-117">Here `name` is a string.</span></span> <span data-ttu-id="85785-118">Bu nedenle, sorgu `IEnumerable<string>`değişkeni bir .</span><span class="sxs-lookup"><span data-stu-id="85785-118">Therefore, the query variable is an `IEnumerable<string>`.</span></span>  
  
3. <span data-ttu-id="85785-119">Sorgu değişkeni `foreach` deyimde üzerinde yinelenir.</span><span class="sxs-lookup"><span data-stu-id="85785-119">The query variable is iterated over in the `foreach` statement.</span></span> <span data-ttu-id="85785-120">Sorgu değişkeni bir dize dizisi olduğundan, yineleme değişkeni de bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="85785-120">Because the query variable is a sequence of strings, the iteration variable is also a string.</span></span>  
  
## <a name="queries-that-transform-the-source-data"></a><span data-ttu-id="85785-121">Kaynak Verileri Dönüştüren Sorgular</span><span class="sxs-lookup"><span data-stu-id="85785-121">Queries that Transform the Source Data</span></span>  
 <span data-ttu-id="85785-122">Aşağıdaki resimde, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] veriler üzerinde basit bir dönüşüm gerçekleştiren bir sorgu işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="85785-122">The following illustration shows a [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] query operation that performs a simple transformation on the data.</span></span> <span data-ttu-id="85785-123">Sorgu, giriş olarak `Customer` nesnelerin bir dizi alır ve `Name` sonuç yalnızca özelliği seçer.</span><span class="sxs-lookup"><span data-stu-id="85785-123">The query takes a sequence of `Customer` objects as input, and selects only the `Name` property in the result.</span></span> <span data-ttu-id="85785-124">Bir `Name` dize olduğundan, sorgu çıktı olarak dizeleri bir dizi üretir.</span><span class="sxs-lookup"><span data-stu-id="85785-124">Because `Name` is a string, the query produces a sequence of strings as output.</span></span>  
  
 ![Veri türünü dönüştüren bir sorguyu gösteren diyagram.](./media/type-relationships-in-linq-query-operations/linq-query-transform-data-type.png)  
  
1. <span data-ttu-id="85785-126">Veri kaynağının tür bağımsız değişkeni aralık değişkeninin türünü belirler.</span><span class="sxs-lookup"><span data-stu-id="85785-126">The type argument of the data source determines the type of the range variable.</span></span>  
  
2. <span data-ttu-id="85785-127">İfade, `select` nesnenin `Name` tamamı `Customer` yerine özelliği döndürür.</span><span class="sxs-lookup"><span data-stu-id="85785-127">The `select` statement returns the `Name` property instead of the complete `Customer` object.</span></span> <span data-ttu-id="85785-128">Bir `Name` dize olduğundan, tür `custNameQuery` `string`bağımsız `Customer`değişkeni , değil.</span><span class="sxs-lookup"><span data-stu-id="85785-128">Because `Name` is a string, the type argument of `custNameQuery` is `string`, not `Customer`.</span></span>  
  
3. <span data-ttu-id="85785-129">Dizeleri bir dizi `custNameQuery` olduğundan, `foreach` döngü yineleme değişkeni de bir `string`.</span><span class="sxs-lookup"><span data-stu-id="85785-129">Because `custNameQuery` is a sequence of strings, the `foreach` loop's iteration variable must also be a `string`.</span></span>  
  
 <span data-ttu-id="85785-130">Aşağıdaki resimde biraz daha karmaşık bir dönüşüm gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="85785-130">The following illustration shows a slightly more complex transformation.</span></span> <span data-ttu-id="85785-131">İfade, `select` özgün `Customer` nesnenin yalnızca iki üyesini yakalayan anonim bir türü döndürür.</span><span class="sxs-lookup"><span data-stu-id="85785-131">The `select` statement returns an anonymous type that captures just two members of the original `Customer` object.</span></span>  
  
 ![Veri türünü dönüştüren daha karmaşık bir sorgu gösteren diyagram.](./media/type-relationships-in-linq-query-operations/linq-complex-query-transform-data-type.png)  
  
1. <span data-ttu-id="85785-133">Veri kaynağının tür bağımsız değişkeni her zaman sorgudaki aralık değişkeninin türüdür.</span><span class="sxs-lookup"><span data-stu-id="85785-133">The type argument of the data source is always the type of the range variable in the query.</span></span>  
  
2. <span data-ttu-id="85785-134">İfade `select` anonim bir tür oluşturduğundan, sorgu değişkeni örtülü `var`olarak yazılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="85785-134">Because the `select` statement produces an anonymous type, the query variable must be implicitly typed by using `var`.</span></span>  
  
3. <span data-ttu-id="85785-135">Sorgu değişkeninin türü örtülü olduğundan, döngüdeki yineleme `foreach` değişkeninin de örtülü olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="85785-135">Because the type of the query variable is implicit, the iteration variable in the `foreach` loop must also be implicit.</span></span>  
  
## <a name="letting-the-compiler-infer-type-information"></a><span data-ttu-id="85785-136">Derleyicinin tür bilgilerini çıkarmasını izin verme</span><span class="sxs-lookup"><span data-stu-id="85785-136">Letting the compiler infer type information</span></span>  
 <span data-ttu-id="85785-137">Bir sorgu işlemindeki tür ilişkilerini anlamanız gerekirken, derleyicinin tüm işi sizin için yapmasına izin verme seçeneğiniz vardır.</span><span class="sxs-lookup"><span data-stu-id="85785-137">Although you should understand the type relationships in a query operation, you have the option to let the compiler do all the work for you.</span></span> <span data-ttu-id="85785-138">[Var](../../../language-reference/keywords/var.md) anahtar sözcüğü, sorgu işlemindeki herhangi bir yerel değişken için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="85785-138">The keyword [var](../../../language-reference/keywords/var.md) can be used for any local variable in a query operation.</span></span> <span data-ttu-id="85785-139">Aşağıdaki çizim, daha önce tartışılan örnek 2'ye benzer.</span><span class="sxs-lookup"><span data-stu-id="85785-139">The following illustration is similar to example number 2 that was discussed earlier.</span></span> <span data-ttu-id="85785-140">Ancak, derleyici sorgu işleminde her değişken için güçlü türü sağlar.</span><span class="sxs-lookup"><span data-stu-id="85785-140">However, the compiler supplies the strong type for each variable in the query operation.</span></span>  
  
 ![Örtük yazı ile tür akışını gösteren diyagram.](./media/type-relationships-in-linq-query-operations/linq-type-flow-implicit-typing.png)  
  
 <span data-ttu-id="85785-142">Hakkında `var`daha fazla bilgi için bkz: [Örtülü Olarak Yazılan Yerel Değişkenler.](../../classes-and-structs/implicitly-typed-local-variables.md)</span><span class="sxs-lookup"><span data-stu-id="85785-142">For more information about `var`, see [Implicitly Typed Local Variables](../../classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
