---
title: "Nasıl yapılır: özel veritabanı işlevleri çağırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 4354e5eb-dd45-469d-97fb-1c495705ee59
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 3d3f2e0235c5e141673d0b3f51c85e5e51e86694
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-call-custom-database-functions"></a><span data-ttu-id="48f5b-102">Nasıl yapılır: özel veritabanı işlevleri çağırma</span><span class="sxs-lookup"><span data-stu-id="48f5b-102">How to: Call Custom Database Functions</span></span>
<span data-ttu-id="48f5b-103">Bu konu, veritabanından LINQ Entities sorguları için tanımlanan özel işlevlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="48f5b-103">This topic describes how to call custom functions that are defined in the database from within LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="48f5b-104">LINQ Entities sorgularında adlı veritabanı işlevleri veritabanı içinde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="48f5b-104">Database functions that are called from LINQ to Entities queries are executed in the database.</span></span> <span data-ttu-id="48f5b-105">İşlevler veritabanında yürütmek, uygulama performansını iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="48f5b-105">Executing functions in the database can improve application performance.</span></span>  
  
 <span data-ttu-id="48f5b-106">Aşağıdaki yordamda, bir özel veritabanı işlevi çağırmak için İleri düzey bir özeti sağlar.</span><span class="sxs-lookup"><span data-stu-id="48f5b-106">The procedure below provides a high-level outline for calling a custom database function.</span></span> <span data-ttu-id="48f5b-107">Aşağıdaki örnek yordamdaki adımları hakkında daha fazla ayrıntı sağlar.</span><span class="sxs-lookup"><span data-stu-id="48f5b-107">The example that follows provides more detail about the steps in the procedure.</span></span>  
  
### <a name="to-call-custom-functions-that-are-defined-in-the-database"></a><span data-ttu-id="48f5b-108">Veritabanında tanımlanan özel işlevleri çağırmak için</span><span class="sxs-lookup"><span data-stu-id="48f5b-108">To call custom functions that are defined in the database</span></span>  
  
1.  <span data-ttu-id="48f5b-109">Veritabanınızda özel bir işlev oluşturun.</span><span class="sxs-lookup"><span data-stu-id="48f5b-109">Create a custom function in your database.</span></span>  
  
     <span data-ttu-id="48f5b-110">SQL Server özel işlevler oluşturma hakkında daha fazla bilgi için bkz: [CREATE FUNCTION (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkID=139871).</span><span class="sxs-lookup"><span data-stu-id="48f5b-110">For more information about creating custom functions in SQL Server, see [CREATE FUNCTION (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkID=139871).</span></span>  
  
2.  <span data-ttu-id="48f5b-111">.Edmx dosyasının depo şeması tanım dili (SSDL) işlevinde bildirin.</span><span class="sxs-lookup"><span data-stu-id="48f5b-111">Declare a function in the store schema definition language (SSDL) of your .edmx file.</span></span> <span data-ttu-id="48f5b-112">İşlevin adı veritabanında bildirilen işlevin adı ile aynı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="48f5b-112">The name of the function must be the same as the name of the function declared in the database.</span></span>  
  
     <span data-ttu-id="48f5b-113">Daha fazla bilgi için bkz: [işlevi öğesi (SSDL)](http://msdn.microsoft.com/en-us/b60cfc3d-8b93-423e-8c99-b867256640a4).</span><span class="sxs-lookup"><span data-stu-id="48f5b-113">For more information, see [Function Element (SSDL)](http://msdn.microsoft.com/en-us/b60cfc3d-8b93-423e-8c99-b867256640a4).</span></span>  
  
3.  <span data-ttu-id="48f5b-114">Karşılık gelen bir yöntemi, uygulama kodunuzda bir sınıf ekleyin ve geçerli bir <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> yönteme unutmayın <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> ve <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> özniteliğinin parametreleridir kavramsal model ad alanı adını ve kavramsal işlev adı Sırasıyla model.</span><span class="sxs-lookup"><span data-stu-id="48f5b-114">Add a corresponding method to a class in your application code and apply a <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to the method Note that the <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> and <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parameters of the attribute are the namespace name of the conceptual model and the function name in the conceptual model respectively.</span></span> <span data-ttu-id="48f5b-115">İşlevi ad çözümlemesi LINQ için büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="48f5b-115">Function name resolution for LINQ is case sensitive.</span></span>  
  
4.  <span data-ttu-id="48f5b-116">Bir LINQ to Entities sorgusunda yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="48f5b-116">Call the method in a LINQ to Entities query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="48f5b-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="48f5b-117">Example</span></span>  
 <span data-ttu-id="48f5b-118">Aşağıdaki örnek, bir özel veritabanı işlevinden bir LINQ to Entities sorgusunda çağrı gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="48f5b-118">The following example demonstrates how to call a custom database function from within a LINQ to Entities query.</span></span> <span data-ttu-id="48f5b-119">Örneğin Okul modelini kullanır.</span><span class="sxs-lookup"><span data-stu-id="48f5b-119">The example uses the School model.</span></span> <span data-ttu-id="48f5b-120">Okul modeli hakkında daha fazla bilgi için bkz: [Okul örnek veritabanı oluşturma](http://msdn.microsoft.com/en-us/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0) ve [Okul .edmx dosyasının oluşturma](http://msdn.microsoft.com/en-us/c48b3907-a8be-4fe6-884c-e95af1852758).</span><span class="sxs-lookup"><span data-stu-id="48f5b-120">For information about the School model, see [Creating the School Sample Database](http://msdn.microsoft.com/en-us/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0) and [Generating the School .edmx File](http://msdn.microsoft.com/en-us/c48b3907-a8be-4fe6-884c-e95af1852758).</span></span>  
  
 <span data-ttu-id="48f5b-121">Aşağıdaki kod ekler `AvgStudentGrade` Okul örnek veritabanına işlevi.</span><span class="sxs-lookup"><span data-stu-id="48f5b-121">The following code adds the `AvgStudentGrade` function to the School sample database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="48f5b-122">Özel veritabanı işlevi çağırmak için veritabanı sunucusu bakılmaksızın aynı adımlardır.</span><span class="sxs-lookup"><span data-stu-id="48f5b-122">The steps for calling a custom database function are the same regardless of the database server.</span></span> <span data-ttu-id="48f5b-123">Ancak, aşağıdaki kod, bir SQL Server veritabanında bir işlev oluşturma için özeldir.</span><span class="sxs-lookup"><span data-stu-id="48f5b-123">However, the code below is specific to creating a function in a SQL Server database.</span></span> <span data-ttu-id="48f5b-124">Diğer veritabanı sunucuları özel bir işlev oluşturma kodunu farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="48f5b-124">The code for creating a custom function in other database servers might differ.</span></span>  
  
 [!code-sql[DP L2E MapToDBFunction#1](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp l2e maptodbfunction/tsql/create_avgstudentgrade.sql#1)]  
  
## <a name="example"></a><span data-ttu-id="48f5b-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="48f5b-125">Example</span></span>  
 <span data-ttu-id="48f5b-126">Ardından, .edmx dosyasının depo şeması tanım dili (SSDL) işlevinde bildirin.</span><span class="sxs-lookup"><span data-stu-id="48f5b-126">Next, declare a function in the store schema definition language (SSDL) of your .edmx file.</span></span> <span data-ttu-id="48f5b-127">Aşağıdaki kod bildirir `AvgStudentGrade` SSDL işlevinde:</span><span class="sxs-lookup"><span data-stu-id="48f5b-127">the following code declares the `AvgStudentGrade` function in SSDL:</span></span>  
  
 [!code-xml[DP L2E MapToDBFunction#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/school.edmx#2)]  
  
## <a name="example"></a><span data-ttu-id="48f5b-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="48f5b-128">Example</span></span>  
 <span data-ttu-id="48f5b-129">Şimdi bir yöntem oluşturma ve SSDL bildirilen işlevi eşleyin.</span><span class="sxs-lookup"><span data-stu-id="48f5b-129">Now create a method and map it to the function declared in the SSDL.</span></span> <span data-ttu-id="48f5b-130">Aşağıdaki sınıf yönteminde SSDL (yukarıda) kullanılarak tanımlanmış işlevi eşlenmiş bir <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="48f5b-130">The method in the following class is mapped to the function defined in the SSDL (above) by using an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span></span> <span data-ttu-id="48f5b-131">Bu yöntem çağrıldığında, veritabanında karşılık gelen işlevi yürütülür.</span><span class="sxs-lookup"><span data-stu-id="48f5b-131">When this method is called, the corresponding function in the database is executed.</span></span>  
  
 [!code-csharp[DP L2E MapToDBFunction#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#3)]
 [!code-vb[DP L2E MapToDBFunction#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="48f5b-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="48f5b-132">Example</span></span>  
 <span data-ttu-id="48f5b-133">Son olarak, bir LINQ to Entities sorgusunda yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="48f5b-133">Finally, call the method in a LINQ to Entities query.</span></span> <span data-ttu-id="48f5b-134">Aşağıdaki kod, konsola Öğrenciler adların ve ortalama dereceleri görüntüler:</span><span class="sxs-lookup"><span data-stu-id="48f5b-134">The following code displays students' last names and average grades to the console:</span></span>  
  
 [!code-csharp[DP L2E MapToDBFunction#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#4)]
 [!code-vb[DP L2E MapToDBFunction#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="48f5b-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="48f5b-135">See Also</span></span>  
 [<span data-ttu-id="48f5b-136">.edmx dosyasının genel bakış</span><span class="sxs-lookup"><span data-stu-id="48f5b-136">.edmx File Overview</span></span>](http://msdn.microsoft.com/en-us/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [<span data-ttu-id="48f5b-137">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="48f5b-137">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
