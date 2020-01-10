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
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635619"
---
# <a name="type-relationships-in-linq-query-operations-c"></a><span data-ttu-id="73479-102">LINQ Sorgu İşlemlerinde Tür İlişkileri (C#)</span><span class="sxs-lookup"><span data-stu-id="73479-102">Type Relationships in LINQ Query Operations (C#)</span></span>
<span data-ttu-id="73479-103">Sorguları etkili bir şekilde yazmak için, bir bütün sorgu işlemindeki değişkenlerin türlerinin birbirleriyle ilişkisini anlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="73479-103">To write queries effectively, you should understand how types of the variables in a complete query operation all relate to each other.</span></span> <span data-ttu-id="73479-104">Bu ilişkileri anladıysanız, belgede LINQ örneklerini ve kod örneklerini daha kolay anlarsınız.</span><span class="sxs-lookup"><span data-stu-id="73479-104">If you understand these relationships you will more easily comprehend the LINQ samples and code examples in the documentation.</span></span> <span data-ttu-id="73479-105">Ayrıca, değişkenler `var`kullanılarak örtük olarak yazıldığında, arka planda neler olduğunu anlamış olursunuz.</span><span class="sxs-lookup"><span data-stu-id="73479-105">Furthermore, you will understand what occurs behind the scenes when variables are implicitly typed by using `var`.</span></span>  
  
 <span data-ttu-id="73479-106">LINQ sorgu işlemleri veri kaynağında, sorgunun kendisinde ve sorgu yürütmesinde kesin olarak türdedir.</span><span class="sxs-lookup"><span data-stu-id="73479-106">LINQ query operations are strongly typed in the data source, in the query itself, and in the query execution.</span></span> <span data-ttu-id="73479-107">Sorgudaki değişkenlerin türü, veri kaynağındaki öğelerin türü ile ve `foreach` deyimindeki yineleme değişkeni türüyle uyumlu olmalıdır).</span><span class="sxs-lookup"><span data-stu-id="73479-107">The type of the variables in the query must be compatible with the type of the elements in the data source and with the type of the iteration variable in the `foreach` statement.</span></span> <span data-ttu-id="73479-108">Bu güçlü yazma, tür hatalarının Kullanıcı tarafından karşılaşmadan önce düzeltilebilecekleri derleme zamanında yakalanmasını güvence altına alır.</span><span class="sxs-lookup"><span data-stu-id="73479-108">This strong typing guarantees that type errors are caught at compile time when they can be corrected before users encounter them.</span></span>  
  
 <span data-ttu-id="73479-109">Bu tür ilişkilerini göstermek için, aşağıdaki örneklerin çoğu tüm değişkenler için açık yazma kullanır.</span><span class="sxs-lookup"><span data-stu-id="73479-109">In order to demonstrate these type relationships, most of the examples that follow use explicit typing for all variables.</span></span> <span data-ttu-id="73479-110">Son örnek, [var](../../../language-reference/keywords/var.md)kullanarak örtük yazma kullandığınızda bile aynı ilkelerin nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="73479-110">The last example shows how the same principles apply even when you use implicit typing by using [var](../../../language-reference/keywords/var.md).</span></span>  
  
## <a name="queries-that-do-not-transform-the-source-data"></a><span data-ttu-id="73479-111">Kaynak verileri dönüştürmeksizin sorgular</span><span class="sxs-lookup"><span data-stu-id="73479-111">Queries that do not Transform the Source Data</span></span>  
 <span data-ttu-id="73479-112">Aşağıdaki çizimde, verilerde dönüştürme gerçekleştirmeyen bir LINQ to Objects sorgu işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="73479-112">The following illustration shows a LINQ to Objects query operation that performs no transformations on the data.</span></span> <span data-ttu-id="73479-113">Kaynak bir dize dizisi içerir ve sorgu çıktısı da dizeler dizisidir.</span><span class="sxs-lookup"><span data-stu-id="73479-113">The source contains a sequence of strings and the query output is also a sequence of strings.</span></span>  
  
 ![LINQ sorgusundaki veri türlerinin ilişkisini gösteren diyagram.](./media/type-relationships-in-linq-query-operations/linq-query-data-type-relation.png)  
  
1. <span data-ttu-id="73479-115">Veri kaynağının tür bağımsız değişkeni, Aralık değişkeninin türünü belirler.</span><span class="sxs-lookup"><span data-stu-id="73479-115">The type argument of the data source determines the type of the range variable.</span></span>  
  
2. <span data-ttu-id="73479-116">Seçilen nesnenin türü, sorgu değişkeninin türünü belirler.</span><span class="sxs-lookup"><span data-stu-id="73479-116">The type of the object that is selected determines the type of the query variable.</span></span> <span data-ttu-id="73479-117">Burada `name` bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="73479-117">Here `name` is a string.</span></span> <span data-ttu-id="73479-118">Bu nedenle, sorgu değişkeni bir `IEnumerable<string>`.</span><span class="sxs-lookup"><span data-stu-id="73479-118">Therefore, the query variable is an `IEnumerable<string>`.</span></span>  
  
3. <span data-ttu-id="73479-119">Sorgu değişkeni `foreach` bildiriminde tekrarlanıyor.</span><span class="sxs-lookup"><span data-stu-id="73479-119">The query variable is iterated over in the `foreach` statement.</span></span> <span data-ttu-id="73479-120">Sorgu değişkeni bir dizeler dizisi olduğundan, yineleme değişkeni de bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="73479-120">Because the query variable is a sequence of strings, the iteration variable is also a string.</span></span>  
  
## <a name="queries-that-transform-the-source-data"></a><span data-ttu-id="73479-121">Kaynak verileri dönüştüren sorgular</span><span class="sxs-lookup"><span data-stu-id="73479-121">Queries that Transform the Source Data</span></span>  
 <span data-ttu-id="73479-122">Aşağıdaki çizimde, verilerde basit bir dönüşüm gerçekleştiren [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] bir sorgu işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="73479-122">The following illustration shows a [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] query operation that performs a simple transformation on the data.</span></span> <span data-ttu-id="73479-123">Sorgu, girdi olarak `Customer` nesnelerden oluşan bir dizi alır ve yalnızca sonuç içinde `Name` özelliğini seçer.</span><span class="sxs-lookup"><span data-stu-id="73479-123">The query takes a sequence of `Customer` objects as input, and selects only the `Name` property in the result.</span></span> <span data-ttu-id="73479-124">`Name` bir dize olduğundan, sorgu çıktı olarak bir dizi dize üretir.</span><span class="sxs-lookup"><span data-stu-id="73479-124">Because `Name` is a string, the query produces a sequence of strings as output.</span></span>  
  
 ![Veri türünü dönüştüren bir sorgu gösteren diyagram.](./media/type-relationships-in-linq-query-operations/linq-query-transform-data-type.png)  
  
1. <span data-ttu-id="73479-126">Veri kaynağının tür bağımsız değişkeni, Aralık değişkeninin türünü belirler.</span><span class="sxs-lookup"><span data-stu-id="73479-126">The type argument of the data source determines the type of the range variable.</span></span>  
  
2. <span data-ttu-id="73479-127">`select` ifade, tüm `Customer` nesnesi yerine `Name` özelliğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="73479-127">The `select` statement returns the `Name` property instead of the complete `Customer` object.</span></span> <span data-ttu-id="73479-128">`Name` bir dize olduğundan, `custNameQuery` tür bağımsız değişkeni `Customer`değil `string`.</span><span class="sxs-lookup"><span data-stu-id="73479-128">Because `Name` is a string, the type argument of `custNameQuery` is `string`, not `Customer`.</span></span>  
  
3. <span data-ttu-id="73479-129">`custNameQuery` bir dizeler dizisi olduğundan, `foreach` döngüsünün yineleme değişkeni de bir `string`olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="73479-129">Because `custNameQuery` is a sequence of strings, the `foreach` loop's iteration variable must also be a `string`.</span></span>  
  
 <span data-ttu-id="73479-130">Aşağıdaki çizimde biraz daha karmaşık bir dönüştürme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="73479-130">The following illustration shows a slightly more complex transformation.</span></span> <span data-ttu-id="73479-131">`select` ifade, özgün `Customer` nesnesinin yalnızca iki üyesini yakalayan bir anonim tür döndürür.</span><span class="sxs-lookup"><span data-stu-id="73479-131">The `select` statement returns an anonymous type that captures just two members of the original `Customer` object.</span></span>  
  
 ![Veri türünü dönüştüren daha karmaşık bir sorgu gösteren diyagram.](./media/type-relationships-in-linq-query-operations/linq-complex-query-transform-data-type.png)  
  
1. <span data-ttu-id="73479-133">Veri kaynağının tür bağımsız değişkeni her zaman sorgudaki aralık değişkeninin türüdür.</span><span class="sxs-lookup"><span data-stu-id="73479-133">The type argument of the data source is always the type of the range variable in the query.</span></span>  
  
2. <span data-ttu-id="73479-134">`select` deyimleri anonim bir tür oluşturduğundan, sorgu değişkeni `var`kullanılarak örtük olarak yazılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="73479-134">Because the `select` statement produces an anonymous type, the query variable must be implicitly typed by using `var`.</span></span>  
  
3. <span data-ttu-id="73479-135">Sorgu değişkeninin türü örtük olduğundan, `foreach` döngüsünde yineleme değişkeni de örtük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="73479-135">Because the type of the query variable is implicit, the iteration variable in the `foreach` loop must also be implicit.</span></span>  
  
## <a name="letting-the-compiler-infer-type-information"></a><span data-ttu-id="73479-136">Derleyicinin tür bilgilerini çıkarmalarına izin verme</span><span class="sxs-lookup"><span data-stu-id="73479-136">Letting the compiler infer type information</span></span>  
 <span data-ttu-id="73479-137">Bir sorgu işlemindeki tür ilişkilerini anlamanız gerekse de, derleyicinin tüm işleri gerçekleştirmesini sağlamak için seçeneğiniz vardır.</span><span class="sxs-lookup"><span data-stu-id="73479-137">Although you should understand the type relationships in a query operation, you have the option to let the compiler do all the work for you.</span></span> <span data-ttu-id="73479-138">[Var](../../../language-reference/keywords/var.md) anahtar sözcüğü, bir sorgu işlemindeki herhangi bir yerel değişken için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="73479-138">The keyword [var](../../../language-reference/keywords/var.md) can be used for any local variable in a query operation.</span></span> <span data-ttu-id="73479-139">Aşağıdaki çizim, daha önce açıklanan örnek numarası 2 ' ye benzer.</span><span class="sxs-lookup"><span data-stu-id="73479-139">The following illustration is similar to example number 2 that was discussed earlier.</span></span> <span data-ttu-id="73479-140">Ancak, derleyici sorgu işlemindeki her değişken için güçlü tür sağlar.</span><span class="sxs-lookup"><span data-stu-id="73479-140">However, the compiler supplies the strong type for each variable in the query operation.</span></span>  
  
 ![Türü örtük olarak yazılan tür akışını gösteren diyagram.](./media/type-relationships-in-linq-query-operations/linq-type-flow-implicit-typing.png)  
  
 <span data-ttu-id="73479-142">`var`hakkında daha fazla bilgi için bkz. [örtülü olarak yazılan yerel değişkenler](../../classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="73479-142">For more information about `var`, see [Implicitly Typed Local Variables](../../classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
