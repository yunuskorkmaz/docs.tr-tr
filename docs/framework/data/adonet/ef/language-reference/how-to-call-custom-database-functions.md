---
title: 'Nasıl yapılır: Özel Veritabanı İşlevleri Çağırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4354e5eb-dd45-469d-97fb-1c495705ee59
ms.openlocfilehash: 6ddd6ebc6215ec17fa416fb0de8f81cf631365db
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936038"
---
# <a name="how-to-call-custom-database-functions"></a><span data-ttu-id="b1e88-102">Nasıl yapılır: Özel Veritabanı İşlevleri Çağırma</span><span class="sxs-lookup"><span data-stu-id="b1e88-102">How to: Call Custom Database Functions</span></span>
<span data-ttu-id="b1e88-103">Bu konu, LINQ to Entities sorguları içinden veritabanında tanımlanan özel işlevlerin nasıl çağrılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="b1e88-103">This topic describes how to call custom functions that are defined in the database from within LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="b1e88-104">LINQ to Entities sorgulardan çağrılan veritabanı işlevleri veritabanında yürütülür.</span><span class="sxs-lookup"><span data-stu-id="b1e88-104">Database functions that are called from LINQ to Entities queries are executed in the database.</span></span> <span data-ttu-id="b1e88-105">Veritabanındaki işlevlerin yürütülmesi, uygulama performansını iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="b1e88-105">Executing functions in the database can improve application performance.</span></span>  
  
 <span data-ttu-id="b1e88-106">Aşağıdaki yordam, özel bir veritabanı işlevini çağırmak için üst düzey bir ana hat sağlar.</span><span class="sxs-lookup"><span data-stu-id="b1e88-106">The procedure below provides a high-level outline for calling a custom database function.</span></span> <span data-ttu-id="b1e88-107">Aşağıdaki örnek, yordamdaki adımlar hakkında daha fazla ayrıntı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b1e88-107">The example that follows provides more detail about the steps in the procedure.</span></span>  
  
### <a name="to-call-custom-functions-that-are-defined-in-the-database"></a><span data-ttu-id="b1e88-108">Veritabanında tanımlanan özel işlevleri çağırmak için</span><span class="sxs-lookup"><span data-stu-id="b1e88-108">To call custom functions that are defined in the database</span></span>  
  
1. <span data-ttu-id="b1e88-109">Veritabanınızda özel bir işlev oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b1e88-109">Create a custom function in your database.</span></span>  
  
     <span data-ttu-id="b1e88-110">SQL Server özel işlevler oluşturma hakkında daha fazla bilgi için bkz. [create FUNCTION (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkID=139871).</span><span class="sxs-lookup"><span data-stu-id="b1e88-110">For more information about creating custom functions in SQL Server, see [CREATE FUNCTION (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkID=139871).</span></span>  
  
2. <span data-ttu-id="b1e88-111">. Edmx dosyanızın mağaza şeması tanım dili (SSDL) içinde bir işlev bildirin.</span><span class="sxs-lookup"><span data-stu-id="b1e88-111">Declare a function in the store schema definition language (SSDL) of your .edmx file.</span></span> <span data-ttu-id="b1e88-112">İşlevin adı, veritabanında belirtilen işlevin adı ile aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b1e88-112">The name of the function must be the same as the name of the function declared in the database.</span></span>  
  
     <span data-ttu-id="b1e88-113">Daha fazla bilgi için bkz. [Işlev öğesi (ssdl)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#function-element-ssdl).</span><span class="sxs-lookup"><span data-stu-id="b1e88-113">For more information, see [Function Element (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#function-element-ssdl).</span></span>  
  
3. <span data-ttu-id="b1e88-114">Uygulama kodunuzda bir sınıfa karşılık gelen bir yöntemi ekleyin ve yöntemine bir <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> uygulayın; <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> bu özniteliğin ve <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parametrelerinin kavramsal modelin ad alanı adı ve kavram içindeki işlev adı olduğunu unutmayın. sırasıyla model.</span><span class="sxs-lookup"><span data-stu-id="b1e88-114">Add a corresponding method to a class in your application code and apply a <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to the method Note that the <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> and <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parameters of the attribute are the namespace name of the conceptual model and the function name in the conceptual model respectively.</span></span> <span data-ttu-id="b1e88-115">LINQ için işlev adı çözümlemesi büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="b1e88-115">Function name resolution for LINQ is case sensitive.</span></span>  
  
4. <span data-ttu-id="b1e88-116">Yöntemi bir LINQ to Entities sorgusunda çağırın.</span><span class="sxs-lookup"><span data-stu-id="b1e88-116">Call the method in a LINQ to Entities query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1e88-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="b1e88-117">Example</span></span>  
 <span data-ttu-id="b1e88-118">Aşağıdaki örnek, bir LINQ to Entities sorgusunun içinden özel bir veritabanı işlevinin nasıl çağrılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b1e88-118">The following example demonstrates how to call a custom database function from within a LINQ to Entities query.</span></span> <span data-ttu-id="b1e88-119">Örnek, okul modelini kullanır.</span><span class="sxs-lookup"><span data-stu-id="b1e88-119">The example uses the School model.</span></span> <span data-ttu-id="b1e88-120">Okul modeli hakkında daha fazla bilgi için bkz. [okul örnek veritabanı oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)) ve [okul. edmx dosyası](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100))oluşturma.</span><span class="sxs-lookup"><span data-stu-id="b1e88-120">For information about the School model, see [Creating the School Sample Database](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)) and [Generating the School .edmx File](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100)).</span></span>  
  
 <span data-ttu-id="b1e88-121">Aşağıdaki kod, okul örnek `AvgStudentGrade` veritabanına işlevi ekler.</span><span class="sxs-lookup"><span data-stu-id="b1e88-121">The following code adds the `AvgStudentGrade` function to the School sample database.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b1e88-122">Özel bir veritabanı işlevini çağırma adımları veritabanı sunucusundan bağımsız olarak aynıdır.</span><span class="sxs-lookup"><span data-stu-id="b1e88-122">The steps for calling a custom database function are the same regardless of the database server.</span></span> <span data-ttu-id="b1e88-123">Ancak, aşağıdaki kod SQL Server veritabanında bir işlev oluşturmak için özeldir.</span><span class="sxs-lookup"><span data-stu-id="b1e88-123">However, the code below is specific to creating a function in a SQL Server database.</span></span> <span data-ttu-id="b1e88-124">Diğer veritabanı sunucularında özel bir işlev oluşturma kodu farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="b1e88-124">The code for creating a custom function in other database servers might differ.</span></span>  
  
 [!code-sql[DP L2E MapToDBFunction#1](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp l2e maptodbfunction/tsql/create_avgstudentgrade.sql#1)]  
  
## <a name="example"></a><span data-ttu-id="b1e88-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="b1e88-125">Example</span></span>  
 <span data-ttu-id="b1e88-126">Sonra,. edmx dosyanızın mağaza şeması tanım dili (SSDL) içinde bir işlev bildirin.</span><span class="sxs-lookup"><span data-stu-id="b1e88-126">Next, declare a function in the store schema definition language (SSDL) of your .edmx file.</span></span> <span data-ttu-id="b1e88-127">Aşağıdaki kod, SSDL içindeki `AvgStudentGrade` işlevi bildirir:</span><span class="sxs-lookup"><span data-stu-id="b1e88-127">the following code declares the `AvgStudentGrade` function in SSDL:</span></span>  
  
 [!code-xml[DP L2E MapToDBFunction#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/school.edmx#2)]  
  
## <a name="example"></a><span data-ttu-id="b1e88-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="b1e88-128">Example</span></span>  
 <span data-ttu-id="b1e88-129">Şimdi bir yöntem oluşturun ve bu yöntemi SSDL öğesinde belirtilen işlevle eşleyin.</span><span class="sxs-lookup"><span data-stu-id="b1e88-129">Now create a method and map it to the function declared in the SSDL.</span></span> <span data-ttu-id="b1e88-130">Aşağıdaki sınıftaki yöntemi, kullanarak <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>SSDL (yukarıda) içinde tanımlanan işlevle eşlenir.</span><span class="sxs-lookup"><span data-stu-id="b1e88-130">The method in the following class is mapped to the function defined in the SSDL (above) by using an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span></span> <span data-ttu-id="b1e88-131">Bu yöntem çağrıldığında, veritabanındaki karşılık gelen işlev yürütülür.</span><span class="sxs-lookup"><span data-stu-id="b1e88-131">When this method is called, the corresponding function in the database is executed.</span></span>  
  
 [!code-csharp[DP L2E MapToDBFunction#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#3)]
 [!code-vb[DP L2E MapToDBFunction#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="b1e88-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="b1e88-132">Example</span></span>  
 <span data-ttu-id="b1e88-133">Son olarak, yöntemi bir LINQ to Entities sorgusunda çağırın.</span><span class="sxs-lookup"><span data-stu-id="b1e88-133">Finally, call the method in a LINQ to Entities query.</span></span> <span data-ttu-id="b1e88-134">Aşağıdaki kod, öğrenciler için en son adları ve ortalama bir not konsolunu görüntüler:</span><span class="sxs-lookup"><span data-stu-id="b1e88-134">The following code displays students' last names and average grades to the console:</span></span>  
  
 [!code-csharp[DP L2E MapToDBFunction#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#4)]
 [!code-vb[DP L2E MapToDBFunction#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="b1e88-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b1e88-135">See also</span></span>

- <span data-ttu-id="b1e88-136">[. edmx dosyasına genel bakış](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b1e88-136">[.edmx File Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span></span>
- [<span data-ttu-id="b1e88-137">LINQ to Entities Sorguları</span><span class="sxs-lookup"><span data-stu-id="b1e88-137">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
