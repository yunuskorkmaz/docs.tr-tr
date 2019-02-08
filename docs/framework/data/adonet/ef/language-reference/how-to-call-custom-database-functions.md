---
title: 'Nasıl yapılır: Özel veritabanı işlevleri çağırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4354e5eb-dd45-469d-97fb-1c495705ee59
ms.openlocfilehash: cdb7b5c90e98f299f37cd09fc83ddfdcca31effd
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55826635"
---
# <a name="how-to-call-custom-database-functions"></a><span data-ttu-id="b66d8-102">Nasıl yapılır: Özel veritabanı işlevleri çağırma</span><span class="sxs-lookup"><span data-stu-id="b66d8-102">How to: Call Custom Database Functions</span></span>
<span data-ttu-id="b66d8-103">Bu konu, veritabanı içinde LINQ to Entities sorgularında tanımlanan özel işlevleri çağırmak açıklar.</span><span class="sxs-lookup"><span data-stu-id="b66d8-103">This topic describes how to call custom functions that are defined in the database from within LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="b66d8-104">Entities sorgularında LINQ çağrılan veritabanı işlevleri veritabanında yürütülür.</span><span class="sxs-lookup"><span data-stu-id="b66d8-104">Database functions that are called from LINQ to Entities queries are executed in the database.</span></span> <span data-ttu-id="b66d8-105">İşlevler veritabanında yürütmek, uygulama performansını iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="b66d8-105">Executing functions in the database can improve application performance.</span></span>  
  
 <span data-ttu-id="b66d8-106">Aşağıdaki yordam, bir özel veritabanı işlevi çağırmak için İleri düzey bir özeti sağlar.</span><span class="sxs-lookup"><span data-stu-id="b66d8-106">The procedure below provides a high-level outline for calling a custom database function.</span></span> <span data-ttu-id="b66d8-107">Aşağıdaki örnek, bu yordamdaki adımları hakkında daha fazla ayrıntı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b66d8-107">The example that follows provides more detail about the steps in the procedure.</span></span>  
  
### <a name="to-call-custom-functions-that-are-defined-in-the-database"></a><span data-ttu-id="b66d8-108">Veritabanında tanımlanan özel işlevleri çağırmak için</span><span class="sxs-lookup"><span data-stu-id="b66d8-108">To call custom functions that are defined in the database</span></span>  
  
1.  <span data-ttu-id="b66d8-109">Özel bir işlev veritabanınızı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b66d8-109">Create a custom function in your database.</span></span>  
  
     <span data-ttu-id="b66d8-110">SQL Server özel işlevler oluşturma hakkında daha fazla bilgi için bkz. [CREATE FUNCTION (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkID=139871).</span><span class="sxs-lookup"><span data-stu-id="b66d8-110">For more information about creating custom functions in SQL Server, see [CREATE FUNCTION (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkID=139871).</span></span>  
  
2.  <span data-ttu-id="b66d8-111">.Edmx dosyanızın depo şeması tanım dili (SSDL) bir işlevde bildirin.</span><span class="sxs-lookup"><span data-stu-id="b66d8-111">Declare a function in the store schema definition language (SSDL) of your .edmx file.</span></span> <span data-ttu-id="b66d8-112">İşlev adı veritabanında bildirilen işlev adı ile aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b66d8-112">The name of the function must be the same as the name of the function declared in the database.</span></span>  
  
     <span data-ttu-id="b66d8-113">Daha fazla bilgi için [işlevi öğesi (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#function-element-ssdl).</span><span class="sxs-lookup"><span data-stu-id="b66d8-113">For more information, see [Function Element (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#function-element-ssdl).</span></span>  
  
3.  <span data-ttu-id="b66d8-114">Karşılık gelen bir yöntem uygulama kodunuzda bir sınıf ekleyin ve geçerli bir <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> yönteme unutmayın <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> ve <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> öznitelik parametreleri: kavramsal modelin ad alanı adı ve kavramsal işlev adı Sırasıyla model.</span><span class="sxs-lookup"><span data-stu-id="b66d8-114">Add a corresponding method to a class in your application code and apply a <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to the method Note that the <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> and <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parameters of the attribute are the namespace name of the conceptual model and the function name in the conceptual model respectively.</span></span> <span data-ttu-id="b66d8-115">LINQ için ad çözümlemesi işlevi büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="b66d8-115">Function name resolution for LINQ is case sensitive.</span></span>  
  
4.  <span data-ttu-id="b66d8-116">Bir LINQ to Entities sorgusunda yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="b66d8-116">Call the method in a LINQ to Entities query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b66d8-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="b66d8-117">Example</span></span>  
 <span data-ttu-id="b66d8-118">Aşağıdaki örnek bir özel veritabanı işlevden içinde bir LINQ to Entities sorgusunda çağırmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="b66d8-118">The following example demonstrates how to call a custom database function from within a LINQ to Entities query.</span></span> <span data-ttu-id="b66d8-119">Örneğin, okul modeli kullanır.</span><span class="sxs-lookup"><span data-stu-id="b66d8-119">The example uses the School model.</span></span> <span data-ttu-id="b66d8-120">Okul modeli hakkında daha fazla bilgi için bkz: [School örnek veritabanını oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)) ve [Okul .edmx dosyası oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="b66d8-120">For information about the School model, see [Creating the School Sample Database](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)) and [Generating the School .edmx File](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100)).</span></span>  
  
 <span data-ttu-id="b66d8-121">Aşağıdaki kodu ekler `AvgStudentGrade` School örnek veritabanını işlevi.</span><span class="sxs-lookup"><span data-stu-id="b66d8-121">The following code adds the `AvgStudentGrade` function to the School sample database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b66d8-122">Özel veritabanını işlevi çağırmak için adımları veritabanı sunucusu bağımsız olarak aynıdır.</span><span class="sxs-lookup"><span data-stu-id="b66d8-122">The steps for calling a custom database function are the same regardless of the database server.</span></span> <span data-ttu-id="b66d8-123">Ancak, aşağıdaki kod, bir SQL Server veritabanında bir işlev oluşturmak için özeldir.</span><span class="sxs-lookup"><span data-stu-id="b66d8-123">However, the code below is specific to creating a function in a SQL Server database.</span></span> <span data-ttu-id="b66d8-124">Diğer veritabanı sunucuları özel bir işlev oluşturma kodunu farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="b66d8-124">The code for creating a custom function in other database servers might differ.</span></span>  
  
 [!code-sql[DP L2E MapToDBFunction#1](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp l2e maptodbfunction/tsql/create_avgstudentgrade.sql#1)]  
  
## <a name="example"></a><span data-ttu-id="b66d8-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="b66d8-125">Example</span></span>  
 <span data-ttu-id="b66d8-126">Ardından, .edmx dosyanızın depo şeması tanım dili (SSDL) bir işlevde bildirin.</span><span class="sxs-lookup"><span data-stu-id="b66d8-126">Next, declare a function in the store schema definition language (SSDL) of your .edmx file.</span></span> <span data-ttu-id="b66d8-127">Aşağıdaki kod bildirir `AvgStudentGrade` SSDL işlevinde:</span><span class="sxs-lookup"><span data-stu-id="b66d8-127">the following code declares the `AvgStudentGrade` function in SSDL:</span></span>  
  
 [!code-xml[DP L2E MapToDBFunction#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/school.edmx#2)]  
  
## <a name="example"></a><span data-ttu-id="b66d8-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="b66d8-128">Example</span></span>  
 <span data-ttu-id="b66d8-129">Artık bir yöntem oluşturma ve SSDL içinde bildirilen işlev eşleyin.</span><span class="sxs-lookup"><span data-stu-id="b66d8-129">Now create a method and map it to the function declared in the SSDL.</span></span> <span data-ttu-id="b66d8-130">Aşağıdaki sınıf yöntemi (yukarıda) SSDL kullanılarak tanımlanmış işlevi eşlenmiş bir <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b66d8-130">The method in the following class is mapped to the function defined in the SSDL (above) by using an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span></span> <span data-ttu-id="b66d8-131">Bu yöntem çağrıldığında, veritabanında ilgili işlev yürütülür.</span><span class="sxs-lookup"><span data-stu-id="b66d8-131">When this method is called, the corresponding function in the database is executed.</span></span>  
  
 [!code-csharp[DP L2E MapToDBFunction#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#3)]
 [!code-vb[DP L2E MapToDBFunction#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="b66d8-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="b66d8-132">Example</span></span>  
 <span data-ttu-id="b66d8-133">Son olarak, bir LINQ to Entities sorgusunda yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="b66d8-133">Finally, call the method in a LINQ to Entities query.</span></span> <span data-ttu-id="b66d8-134">Aşağıdaki kod, konsola öğrencilerinin adların ve ortalama derece görüntüler:</span><span class="sxs-lookup"><span data-stu-id="b66d8-134">The following code displays students' last names and average grades to the console:</span></span>  
  
 [!code-csharp[DP L2E MapToDBFunction#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#4)]
 [!code-vb[DP L2E MapToDBFunction#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="b66d8-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b66d8-135">See also</span></span>
- <span data-ttu-id="b66d8-136">[.edmx dosyasını genel bakış](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b66d8-136">[.edmx File Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span></span>
- [<span data-ttu-id="b66d8-137">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="b66d8-137">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
