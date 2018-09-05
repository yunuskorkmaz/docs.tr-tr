---
title: 'Nasıl yapılır: özel veritabanı işlevleri çağırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4354e5eb-dd45-469d-97fb-1c495705ee59
ms.openlocfilehash: 4e7c94dce5b50fe93f00aaaa72206be3394faf62
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43542212"
---
# <a name="how-to-call-custom-database-functions"></a><span data-ttu-id="07380-102">Nasıl yapılır: özel veritabanı işlevleri çağırma</span><span class="sxs-lookup"><span data-stu-id="07380-102">How to: Call Custom Database Functions</span></span>
<span data-ttu-id="07380-103">Bu konu, veritabanı içinde LINQ to Entities sorgularında tanımlanan özel işlevleri çağırmak açıklar.</span><span class="sxs-lookup"><span data-stu-id="07380-103">This topic describes how to call custom functions that are defined in the database from within LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="07380-104">Entities sorgularında LINQ çağrılan veritabanı işlevleri veritabanında yürütülür.</span><span class="sxs-lookup"><span data-stu-id="07380-104">Database functions that are called from LINQ to Entities queries are executed in the database.</span></span> <span data-ttu-id="07380-105">İşlevler veritabanında yürütmek, uygulama performansını iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="07380-105">Executing functions in the database can improve application performance.</span></span>  
  
 <span data-ttu-id="07380-106">Aşağıdaki yordam, bir özel veritabanı işlevi çağırmak için İleri düzey bir özeti sağlar.</span><span class="sxs-lookup"><span data-stu-id="07380-106">The procedure below provides a high-level outline for calling a custom database function.</span></span> <span data-ttu-id="07380-107">Aşağıdaki örnek, bu yordamdaki adımları hakkında daha fazla ayrıntı sağlar.</span><span class="sxs-lookup"><span data-stu-id="07380-107">The example that follows provides more detail about the steps in the procedure.</span></span>  
  
### <a name="to-call-custom-functions-that-are-defined-in-the-database"></a><span data-ttu-id="07380-108">Veritabanında tanımlanan özel işlevleri çağırmak için</span><span class="sxs-lookup"><span data-stu-id="07380-108">To call custom functions that are defined in the database</span></span>  
  
1.  <span data-ttu-id="07380-109">Özel bir işlev veritabanınızı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="07380-109">Create a custom function in your database.</span></span>  
  
     <span data-ttu-id="07380-110">SQL Server özel işlevler oluşturma hakkında daha fazla bilgi için bkz. [CREATE FUNCTION (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkID=139871).</span><span class="sxs-lookup"><span data-stu-id="07380-110">For more information about creating custom functions in SQL Server, see [CREATE FUNCTION (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkID=139871).</span></span>  
  
2.  <span data-ttu-id="07380-111">.Edmx dosyanızın depo şeması tanım dili (SSDL) bir işlevde bildirin.</span><span class="sxs-lookup"><span data-stu-id="07380-111">Declare a function in the store schema definition language (SSDL) of your .edmx file.</span></span> <span data-ttu-id="07380-112">İşlev adı veritabanında bildirilen işlev adı ile aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="07380-112">The name of the function must be the same as the name of the function declared in the database.</span></span>  
  
     <span data-ttu-id="07380-113">Daha fazla bilgi için [işlevi öğesi (SSDL)](https://msdn.microsoft.com/library/b60cfc3d-8b93-423e-8c99-b867256640a4).</span><span class="sxs-lookup"><span data-stu-id="07380-113">For more information, see [Function Element (SSDL)](https://msdn.microsoft.com/library/b60cfc3d-8b93-423e-8c99-b867256640a4).</span></span>  
  
3.  <span data-ttu-id="07380-114">Karşılık gelen bir yöntem uygulama kodunuzda bir sınıf ekleyin ve geçerli bir <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> yönteme unutmayın <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> ve <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> öznitelik parametreleri: kavramsal modelin ad alanı adı ve kavramsal işlev adı Sırasıyla model.</span><span class="sxs-lookup"><span data-stu-id="07380-114">Add a corresponding method to a class in your application code and apply a <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to the method Note that the <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> and <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parameters of the attribute are the namespace name of the conceptual model and the function name in the conceptual model respectively.</span></span> <span data-ttu-id="07380-115">LINQ için ad çözümlemesi işlevi büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="07380-115">Function name resolution for LINQ is case sensitive.</span></span>  
  
4.  <span data-ttu-id="07380-116">Bir LINQ to Entities sorgusunda yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="07380-116">Call the method in a LINQ to Entities query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07380-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="07380-117">Example</span></span>  
 <span data-ttu-id="07380-118">Aşağıdaki örnek bir özel veritabanı işlevden içinde bir LINQ to Entities sorgusunda çağırmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="07380-118">The following example demonstrates how to call a custom database function from within a LINQ to Entities query.</span></span> <span data-ttu-id="07380-119">Örneğin, okul modeli kullanır.</span><span class="sxs-lookup"><span data-stu-id="07380-119">The example uses the School model.</span></span> <span data-ttu-id="07380-120">Okul modeli hakkında daha fazla bilgi için bkz: [School örnek veritabanını oluşturma](https://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0) ve [Okul .edmx dosyası oluşturma](https://msdn.microsoft.com/library/c48b3907-a8be-4fe6-884c-e95af1852758).</span><span class="sxs-lookup"><span data-stu-id="07380-120">For information about the School model, see [Creating the School Sample Database](https://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0) and [Generating the School .edmx File](https://msdn.microsoft.com/library/c48b3907-a8be-4fe6-884c-e95af1852758).</span></span>  
  
 <span data-ttu-id="07380-121">Aşağıdaki kodu ekler `AvgStudentGrade` School örnek veritabanını işlevi.</span><span class="sxs-lookup"><span data-stu-id="07380-121">The following code adds the `AvgStudentGrade` function to the School sample database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="07380-122">Özel veritabanını işlevi çağırmak için adımları veritabanı sunucusu bağımsız olarak aynıdır.</span><span class="sxs-lookup"><span data-stu-id="07380-122">The steps for calling a custom database function are the same regardless of the database server.</span></span> <span data-ttu-id="07380-123">Ancak, aşağıdaki kod, bir SQL Server veritabanında bir işlev oluşturmak için özeldir.</span><span class="sxs-lookup"><span data-stu-id="07380-123">However, the code below is specific to creating a function in a SQL Server database.</span></span> <span data-ttu-id="07380-124">Diğer veritabanı sunucuları özel bir işlev oluşturma kodunu farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="07380-124">The code for creating a custom function in other database servers might differ.</span></span>  
  
 [!code-sql[DP L2E MapToDBFunction#1](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp l2e maptodbfunction/tsql/create_avgstudentgrade.sql#1)]  
  
## <a name="example"></a><span data-ttu-id="07380-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="07380-125">Example</span></span>  
 <span data-ttu-id="07380-126">Ardından, .edmx dosyanızın depo şeması tanım dili (SSDL) bir işlevde bildirin.</span><span class="sxs-lookup"><span data-stu-id="07380-126">Next, declare a function in the store schema definition language (SSDL) of your .edmx file.</span></span> <span data-ttu-id="07380-127">Aşağıdaki kod bildirir `AvgStudentGrade` SSDL işlevinde:</span><span class="sxs-lookup"><span data-stu-id="07380-127">the following code declares the `AvgStudentGrade` function in SSDL:</span></span>  
  
 [!code-xml[DP L2E MapToDBFunction#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/school.edmx#2)]  
  
## <a name="example"></a><span data-ttu-id="07380-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="07380-128">Example</span></span>  
 <span data-ttu-id="07380-129">Artık bir yöntem oluşturma ve SSDL içinde bildirilen işlev eşleyin.</span><span class="sxs-lookup"><span data-stu-id="07380-129">Now create a method and map it to the function declared in the SSDL.</span></span> <span data-ttu-id="07380-130">Aşağıdaki sınıf yöntemi (yukarıda) SSDL kullanılarak tanımlanmış işlevi eşlenmiş bir <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="07380-130">The method in the following class is mapped to the function defined in the SSDL (above) by using an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span></span> <span data-ttu-id="07380-131">Bu yöntem çağrıldığında, veritabanında ilgili işlev yürütülür.</span><span class="sxs-lookup"><span data-stu-id="07380-131">When this method is called, the corresponding function in the database is executed.</span></span>  
  
 [!code-csharp[DP L2E MapToDBFunction#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#3)]
 [!code-vb[DP L2E MapToDBFunction#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="07380-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="07380-132">Example</span></span>  
 <span data-ttu-id="07380-133">Son olarak, bir LINQ to Entities sorgusunda yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="07380-133">Finally, call the method in a LINQ to Entities query.</span></span> <span data-ttu-id="07380-134">Aşağıdaki kod, konsola öğrencilerinin adların ve ortalama derece görüntüler:</span><span class="sxs-lookup"><span data-stu-id="07380-134">The following code displays students' last names and average grades to the console:</span></span>  
  
 [!code-csharp[DP L2E MapToDBFunction#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#4)]
 [!code-vb[DP L2E MapToDBFunction#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="07380-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="07380-135">See Also</span></span>  
 [<span data-ttu-id="07380-136">.edmx dosyasını genel bakış</span><span class="sxs-lookup"><span data-stu-id="07380-136">.edmx File Overview</span></span>](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [<span data-ttu-id="07380-137">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="07380-137">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
