---
title: 'Nasıl yapılır: Özel Veritabanı İşlevleri Çağırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4354e5eb-dd45-469d-97fb-1c495705ee59
ms.openlocfilehash: f3177ab98382506770c4655c62573da5c1d96c69
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78848762"
---
# <a name="how-to-call-custom-database-functions"></a><span data-ttu-id="43cca-102">Nasıl yapılır: Özel Veritabanı İşlevleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="43cca-102">How to: Call Custom Database Functions</span></span>

<span data-ttu-id="43cca-103">Bu konu, LINQ içinden Varlıklar sorgularına veritabanında tanımlanan özel işlevlerin nasıl çağrılmasını açıklar.</span><span class="sxs-lookup"><span data-stu-id="43cca-103">This topic describes how to call custom functions that are defined in the database from within LINQ to Entities queries.</span></span>

<span data-ttu-id="43cca-104">LINQ'dan Varlıklara sorguolarak çağrılan veritabanı işlevleri veritabanında yürütülür.</span><span class="sxs-lookup"><span data-stu-id="43cca-104">Database functions that are called from LINQ to Entities queries are executed in the database.</span></span> <span data-ttu-id="43cca-105">Veritabanındaki işlevleri yürütme uygulama performansını artırabilir.</span><span class="sxs-lookup"><span data-stu-id="43cca-105">Executing functions in the database can improve application performance.</span></span>

<span data-ttu-id="43cca-106">Aşağıdaki yordam, özel bir veritabanı işlevini çağırmak için üst düzey bir anahat sağlar.</span><span class="sxs-lookup"><span data-stu-id="43cca-106">The procedure below provides a high-level outline for calling a custom database function.</span></span> <span data-ttu-id="43cca-107">Aşağıdaki örnek, yordamdaki adımlar hakkında daha fazla ayrıntı sağlar.</span><span class="sxs-lookup"><span data-stu-id="43cca-107">The example that follows provides more detail about the steps in the procedure.</span></span>

## <a name="to-call-custom-functions-that-are-defined-in-the-database"></a><span data-ttu-id="43cca-108">Veritabanında tanımlanan özel işlevleri çağırmak için</span><span class="sxs-lookup"><span data-stu-id="43cca-108">To call custom functions that are defined in the database</span></span>

1. <span data-ttu-id="43cca-109">Veritabanınızda özel bir işlev oluşturun.</span><span class="sxs-lookup"><span data-stu-id="43cca-109">Create a custom function in your database.</span></span>

     <span data-ttu-id="43cca-110">SQL Server'da özel işlevler oluşturma hakkında daha fazla bilgi için [CREATE FUNCTION (Transact-SQL)](/sql/t-sql/statements/create-function-transact-sql)adresine bakın.</span><span class="sxs-lookup"><span data-stu-id="43cca-110">For more information about creating custom functions in SQL Server, see [CREATE FUNCTION (Transact-SQL)](/sql/t-sql/statements/create-function-transact-sql).</span></span>

2. <span data-ttu-id="43cca-111">.edmx dosyanızın mağaza şema tanım dilinde (SSDL) bir işlev bildirin.</span><span class="sxs-lookup"><span data-stu-id="43cca-111">Declare a function in the store schema definition language (SSDL) of your .edmx file.</span></span> <span data-ttu-id="43cca-112">İşlevin adı veritabanında bildirilen işlevin adı ile aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="43cca-112">The name of the function must be the same as the name of the function declared in the database.</span></span>

     <span data-ttu-id="43cca-113">Daha fazla bilgi için [Bkz. İşlev Öğesi (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#function-element-ssdl).</span><span class="sxs-lookup"><span data-stu-id="43cca-113">For more information, see [Function Element (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#function-element-ssdl).</span></span>

3. <span data-ttu-id="43cca-114">Uygulama kodunuzdaki bir sınıfa karşılık gelen <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> bir yöntem ekleyin <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> ve yönteme bir uygulama Özniteliğin parametrelerinin kavramsal modelin ad alanı adı ve kavramsal modeldeki işlev adı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="43cca-114">Add a corresponding method to a class in your application code and apply a <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to the method Note that the <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> and <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parameters of the attribute are the namespace name of the conceptual model and the function name in the conceptual model respectively.</span></span> <span data-ttu-id="43cca-115">LINQ için işlev adı çözünürlüğü büyük/küçük harf duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="43cca-115">Function name resolution for LINQ is case sensitive.</span></span>

4. <span data-ttu-id="43cca-116">LinQ'daki yöntemi Varlıklar sorgusuna çağırın.</span><span class="sxs-lookup"><span data-stu-id="43cca-116">Call the method in a LINQ to Entities query.</span></span>  

## <a name="example"></a><span data-ttu-id="43cca-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="43cca-117">Example</span></span>

<span data-ttu-id="43cca-118">Aşağıdaki örnek, linq'den Varlıklar sorgusuna özel bir veritabanı işlevinin nasıl çağrılmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="43cca-118">The following example demonstrates how to call a custom database function from within a LINQ to Entities query.</span></span> <span data-ttu-id="43cca-119">Örnek, Okul modelini kullanır.</span><span class="sxs-lookup"><span data-stu-id="43cca-119">The example uses the School model.</span></span> <span data-ttu-id="43cca-120">Okul modeli hakkında daha fazla bilgi için [Generating the School .edmx File](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100)) [bkz.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="43cca-120">For information about the School model, see [Creating the School Sample Database](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)) and [Generating the School .edmx File](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100)).</span></span>

<span data-ttu-id="43cca-121">Aşağıdaki kod, `AvgStudentGrade` İşlevin Okul örnek veritabanına ekleniyor.</span><span class="sxs-lookup"><span data-stu-id="43cca-121">The following code adds the `AvgStudentGrade` function to the School sample database.</span></span>

> [!NOTE]
> <span data-ttu-id="43cca-122">Özel bir veritabanı işlevini çağırma adımları, veritabanı sunucusundan bağımsız olarak aynıdır.</span><span class="sxs-lookup"><span data-stu-id="43cca-122">The steps for calling a custom database function are the same regardless of the database server.</span></span> <span data-ttu-id="43cca-123">Ancak, aşağıdaki kod bir SQL Server veritabanında bir işlev oluşturmak için özeldir.</span><span class="sxs-lookup"><span data-stu-id="43cca-123">However, the code below is specific to creating a function in a SQL Server database.</span></span> <span data-ttu-id="43cca-124">Diğer veritabanı sunucularında özel bir işlev oluşturma kodu farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="43cca-124">The code for creating a custom function in other database servers might differ.</span></span>

[!code-sql[DP L2E MapToDBFunction#1](~/samples/snippets/tsql/VS_Snippets_Data/dp l2e maptodbfunction/tsql/create_avgstudentgrade.sql#1)]

## <a name="example"></a><span data-ttu-id="43cca-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="43cca-125">Example</span></span>

<span data-ttu-id="43cca-126">Ardından, *.edmx* dosyanızın mağaza şema tanım dilinde (SSDL) bir işlev bildirin.</span><span class="sxs-lookup"><span data-stu-id="43cca-126">Next, declare a function in the store schema definition language (SSDL) of your *.edmx* file.</span></span> <span data-ttu-id="43cca-127">Aşağıdaki kod SSDL `AvgStudentGrade` işlevi bildirir:</span><span class="sxs-lookup"><span data-stu-id="43cca-127">The following code declares the `AvgStudentGrade` function in SSDL:</span></span>

[!code-xml[DP L2E MapToDBFunction#2](~/samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/school.edmx#2)]

## <a name="example"></a><span data-ttu-id="43cca-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="43cca-128">Example</span></span>

<span data-ttu-id="43cca-129">Şimdi, bir yöntem oluşturun ve ssdl'de bildirilen işleve göre eşle.</span><span class="sxs-lookup"><span data-stu-id="43cca-129">Now, create a method and map it to the function declared in the SSDL.</span></span> <span data-ttu-id="43cca-130">Aşağıdaki sınıftaki yöntem, SSDL'de tanımlanan işleve (üstte) bir <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="43cca-130">The method in the following class is mapped to the function defined in the SSDL (above) by using an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span></span> <span data-ttu-id="43cca-131">Bu yöntem çağrıldığında, veritabanındaki karşılık gelen işlev yürütülür.</span><span class="sxs-lookup"><span data-stu-id="43cca-131">When this method is called, the corresponding function in the database is executed.</span></span>

[!code-csharp[DP L2E MapToDBFunction#3](~/samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#3)]
[!code-vb[DP L2E MapToDBFunction#3](~/samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#3)]

## <a name="example"></a><span data-ttu-id="43cca-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="43cca-132">Example</span></span>

<span data-ttu-id="43cca-133">Son olarak, LinQ'dan Varlıklar sorgusuna yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="43cca-133">Finally, call the method in a LINQ to Entities query.</span></span> <span data-ttu-id="43cca-134">Aşağıdaki kod, öğrencilerin soyadlarını ve ortalama notlarını konsolda görüntüler:</span><span class="sxs-lookup"><span data-stu-id="43cca-134">The following code displays students' last names and average grades to the console:</span></span>

[!code-csharp[DP L2E MapToDBFunction#4](~/samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#4)]
[!code-vb[DP L2E MapToDBFunction#4](~/samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#4)]

## <a name="see-also"></a><span data-ttu-id="43cca-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43cca-135">See also</span></span>

- <span data-ttu-id="43cca-136">[.edmx Dosyaya Genel Bakış](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="43cca-136">[.edmx File Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span></span>
- [<span data-ttu-id="43cca-137">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="43cca-137">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
