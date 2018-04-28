---
title: "İzlenecek yol: Verimliliği Artırmak için BatchBlock ve BatchedJoinBlock'u Kullanma"
ms.date: 03/30/2017
ms.prod: .net
ms.technology: dotnet-standard
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, improving efficiency
ms.assetid: 5beb4983-80c2-4f60-8c51-a07f9fd94cb3
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e9305fd2a0e61a71f6875d6061f835e9cdae5dd1
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency"></a><span data-ttu-id="2fc36-102">İzlenecek yol: Verimliliği Artırmak için BatchBlock ve BatchedJoinBlock'u Kullanma</span><span class="sxs-lookup"><span data-stu-id="2fc36-102">Walkthrough: Using BatchBlock and BatchedJoinBlock to Improve Efficiency</span></span>
<span data-ttu-id="2fc36-103">TPL veri akışı kitaplığı sağlar <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> , alabilir ve arabellek bir veya daha fazla kaynaklardan veri ve o arabelleğe alınan verileri bir koleksiyon olarak kullanıma yayılması böylece sınıfları.</span><span class="sxs-lookup"><span data-stu-id="2fc36-103">The TPL Dataflow Library provides the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> classes so that you can receive and buffer data from one or more sources and then propagate out that buffered data as one collection.</span></span> <span data-ttu-id="2fc36-104">Bu toplu mekanizması, bir veya daha çok kaynaktan veri toplamak ve ardından birden çok veri öğesi toplu iş olarak işlem durumlarda faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="2fc36-104">This batching mechanism is useful when you collect data from one or more sources and then process multiple data elements as a batch.</span></span> <span data-ttu-id="2fc36-105">Örneğin, bir veritabanına kayıtları eklemek için veri akışı kullanan bir uygulamayı göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="2fc36-105">For example, consider an application that uses dataflow to insert records into a database.</span></span> <span data-ttu-id="2fc36-106">Bu işlem, birden çok öğe aynı zamanda bir kerede yerine sırayla eklenirse daha etkili olabilir.</span><span class="sxs-lookup"><span data-stu-id="2fc36-106">This operation can be more efficient if multiple items are inserted at the same time instead of one at a time sequentially.</span></span> <span data-ttu-id="2fc36-107">Bu belge nasıl kullanılacağını açıklar <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> böyle bir veritabanını verimliliğini artırmak için sınıf ekleme işlemleri.</span><span class="sxs-lookup"><span data-stu-id="2fc36-107">This document describes how to use the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class to improve the efficiency of such database insert operations.</span></span> <span data-ttu-id="2fc36-108">Ayrıca nasıl kullanılacağını açıklar <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> sonuçları ve programı bir veritabanından okuduğunda oluşan özel durumları yakalamak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="2fc36-108">It also describes how to use the <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> class to capture both the results and any exceptions that occur when the program reads from a database.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="prerequisites"></a><span data-ttu-id="2fc36-109">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="2fc36-109">Prerequisites</span></span>  
  
1.  <span data-ttu-id="2fc36-110">Birleştirme blokları bölümünde okuma [veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) bu kılavuza başlamadan önce belge.</span><span class="sxs-lookup"><span data-stu-id="2fc36-110">Read the Join Blocks section in the [Dataflow](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) document before you start this walkthrough.</span></span>  
  
2.  <span data-ttu-id="2fc36-111">Northwind veritabanı Northwind.sdf, bilgisayarınızda bulunan bir kopya olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="2fc36-111">Ensure that you have a copy of the Northwind database, Northwind.sdf, available on your computer.</span></span> <span data-ttu-id="2fc36-112">Bu dosya, klasör % Program Files%\Microsoft SQL Server Compact Edition\v3.5\Samples genellikle bulunur\\.</span><span class="sxs-lookup"><span data-stu-id="2fc36-112">This file is typically located in the folder %Program Files%\Microsoft SQL Server Compact Edition\v3.5\Samples\\.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="2fc36-113">Bazı Windows sürümlerinde, Visual Studio yönetici olmayan modda çalışıyorsa, Northwind.sdf için bağlantı kuramıyor.</span><span class="sxs-lookup"><span data-stu-id="2fc36-113">In some versions of Windows, you cannot connect to Northwind.sdf if Visual Studio is running in a non-administrator mode.</span></span> <span data-ttu-id="2fc36-114">Visual Studio veya Visual Studio komut istemi başlatmak için Northwind.sdf bağlanmak için **yönetici olarak çalıştır** modu.</span><span class="sxs-lookup"><span data-stu-id="2fc36-114">To connect to Northwind.sdf, start Visual Studio or a Visual Studio command prompt in the **Run as administrator** mode.</span></span>  
  
 <span data-ttu-id="2fc36-115">Bu kılavuz aşağıdaki bölümleri içerir:</span><span class="sxs-lookup"><span data-stu-id="2fc36-115">This walkthrough contains the following sections:</span></span>  
  
-   [<span data-ttu-id="2fc36-116">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="2fc36-116">Creating the Console Application</span></span>](#creating)  
  
-   [<span data-ttu-id="2fc36-117">Çalışan sınıf tanımlama</span><span class="sxs-lookup"><span data-stu-id="2fc36-117">Defining the Employee Class</span></span>](#employeeClass)  
  
-   [<span data-ttu-id="2fc36-118">Çalışan veritabanı işlemleri tanımlama</span><span class="sxs-lookup"><span data-stu-id="2fc36-118">Defining Employee Database Operations</span></span>](#operations)  
  
-   [<span data-ttu-id="2fc36-119">Veritabanına arabelleğe alma kullanmadan çalışan verilerini ekleme</span><span class="sxs-lookup"><span data-stu-id="2fc36-119">Adding Employee Data to the Database without Using Buffering</span></span>](#nonBuffering)  
  
-   [<span data-ttu-id="2fc36-120">Çalışan veri eklemek için arabelleğe almayı kullanma</span><span class="sxs-lookup"><span data-stu-id="2fc36-120">Using Buffering to Add Employee Data to the Database</span></span>](#buffering)  
  
-   [<span data-ttu-id="2fc36-121">Çalışan verilerini veritabanından okumak için arabelleğe alınan birleştirme kullanma</span><span class="sxs-lookup"><span data-stu-id="2fc36-121">Using Buffered Join to Read Employee Data from the Database</span></span>](#bufferedJoin)  
  
-   [<span data-ttu-id="2fc36-122">Tam bir örnek</span><span class="sxs-lookup"><span data-stu-id="2fc36-122">The Complete Example</span></span>](#complete)  
  
<a name="creating"></a>   
## <a name="creating-the-console-application"></a><span data-ttu-id="2fc36-123">Konsol Uygulaması Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2fc36-123">Creating the Console Application</span></span>  
  
<a name="consoleApp"></a>   
1.  <span data-ttu-id="2fc36-124">Visual Studio'da bir Visual C# veya Visual Basic oluşturma **konsol uygulaması** projesi.</span><span class="sxs-lookup"><span data-stu-id="2fc36-124">In Visual Studio, create a Visual C# or Visual Basic **Console Application** project.</span></span> <span data-ttu-id="2fc36-125">Bu belgede, proje adı `DataflowBatchDatabase`.</span><span class="sxs-lookup"><span data-stu-id="2fc36-125">In this document, the project is named `DataflowBatchDatabase`.</span></span>  
  
2.  <span data-ttu-id="2fc36-126">Projenizde, System.Data.SqlServerCe.dll başvuru ve System.Threading.Tasks.Dataflow.dll bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2fc36-126">In your project, add a reference to System.Data.SqlServerCe.dll and a reference to System.Threading.Tasks.Dataflow.dll.</span></span>  
  
3.  <span data-ttu-id="2fc36-127">Form1.cs (Visual Basic Form1.vb) aşağıdaki içerdiğinden emin olun `using` (`Imports` Visual Basic'te) deyimleri.</span><span class="sxs-lookup"><span data-stu-id="2fc36-127">Ensure that Form1.cs (Form1.vb for Visual Basic) contains the following `using` (`Imports` in Visual Basic) statements.</span></span>  
  
     [!code-csharp[TPLDataflow_BatchDatabase#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#1)]
     [!code-vb[TPLDataflow_BatchDatabase#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#1)]  
  
4.  <span data-ttu-id="2fc36-128">Aşağıdaki veri üye ekleme `Program` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="2fc36-128">Add the following data members to the `Program` class.</span></span>  
  
     [!code-csharp[TPLDataflow_BatchDatabase#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#2)]
     [!code-vb[TPLDataflow_BatchDatabase#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#2)]  
  
<a name="employeeClass"></a>   
## <a name="defining-the-employee-class"></a><span data-ttu-id="2fc36-129">Çalışan sınıf tanımlama</span><span class="sxs-lookup"><span data-stu-id="2fc36-129">Defining the Employee Class</span></span>  
 <span data-ttu-id="2fc36-130">Ekleme `Program` sınıfı `Employee` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="2fc36-130">Add to the `Program` class the `Employee` class.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#3)]
 [!code-vb[TPLDataflow_BatchDatabase#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#3)]  
  
 <span data-ttu-id="2fc36-131">`Employee` Sınıfı üç özellik içerir `EmployeeID`, `LastName`, ve `FirstName`.</span><span class="sxs-lookup"><span data-stu-id="2fc36-131">The `Employee` class contains three properties, `EmployeeID`, `LastName`, and `FirstName`.</span></span> <span data-ttu-id="2fc36-132">Bu özellikleri karşılık `Employee ID`, `Last Name`, ve `First Name` sütunlarında `Employees` Northwind veritabanı tablosunda.</span><span class="sxs-lookup"><span data-stu-id="2fc36-132">These properties correspond to the `Employee ID`, `Last Name`, and `First Name` columns in the `Employees` table in the Northwind database.</span></span> <span data-ttu-id="2fc36-133">Bu Tanıtım için `Employee` sınıfı ayrıca tanımlayan `Random` oluşturur yöntemi bir `Employee` özelliklerini için rastgele değerlerine sahip bir nesne.</span><span class="sxs-lookup"><span data-stu-id="2fc36-133">For this demonstration, the `Employee` class also defines the `Random` method, which creates an `Employee` object that has random values for its properties.</span></span>  
  
<a name="operations"></a>   
## <a name="defining-employee-database-operations"></a><span data-ttu-id="2fc36-134">Çalışan veritabanı işlemleri tanımlama</span><span class="sxs-lookup"><span data-stu-id="2fc36-134">Defining Employee Database Operations</span></span>  
 <span data-ttu-id="2fc36-135">Ekleme `Program` sınıfı `InsertEmployees`, `GetEmployeeCount`, ve `GetEmployeeID` yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="2fc36-135">Add to the `Program` class the `InsertEmployees`, `GetEmployeeCount`, and `GetEmployeeID` methods.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#4)]
 [!code-vb[TPLDataflow_BatchDatabase#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#4)]  
  
 <span data-ttu-id="2fc36-136">`InsertEmployees` Yöntemi yeni çalışan kayıtları veritabanına ekler.</span><span class="sxs-lookup"><span data-stu-id="2fc36-136">The `InsertEmployees` method adds new employee records to the database.</span></span> <span data-ttu-id="2fc36-137">`GetEmployeeCount` Yöntemi alır giriş sayısı `Employees` tablo.</span><span class="sxs-lookup"><span data-stu-id="2fc36-137">The `GetEmployeeCount` method retrieves the number of entries in the `Employees` table.</span></span> <span data-ttu-id="2fc36-138">`GetEmployeeID` Yöntemi sağlanan adına sahip ilk çalışan tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="2fc36-138">The `GetEmployeeID` method retrieves the identifier of the first employee that has the provided name.</span></span> <span data-ttu-id="2fc36-139">Bu yöntemlerin her biri Northwind veritabanına bir bağlantı dizesi alır ve işlevleri kullanır `System.Data.SqlServerCe` veritabanıyla iletişim kurmak için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="2fc36-139">Each of these methods takes a connection string to the Northwind database and uses functionality in the `System.Data.SqlServerCe` namespace to communicate with the database.</span></span>  
  
<a name="nonBuffering"></a>   
## <a name="adding-employee-data-to-the-database-without-using-buffering"></a><span data-ttu-id="2fc36-140">Veritabanına arabelleğe alma kullanmadan çalışan verilerini ekleme</span><span class="sxs-lookup"><span data-stu-id="2fc36-140">Adding Employee Data to the Database Without Using Buffering</span></span>  
 <span data-ttu-id="2fc36-141">Ekleme `Program` sınıfı `AddEmployees` ve `PostRandomEmployees` yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="2fc36-141">Add to the `Program` class the `AddEmployees` and `PostRandomEmployees` methods.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#5)]
 [!code-vb[TPLDataflow_BatchDatabase#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#5)]  
  
 <span data-ttu-id="2fc36-142">`AddEmployees` Yöntemi ekler rastgele çalışan verilerini veritabanına veri akışı kullanarak.</span><span class="sxs-lookup"><span data-stu-id="2fc36-142">The `AddEmployees` method adds random employee data to the database by using dataflow.</span></span> <span data-ttu-id="2fc36-143">Oluşturduğu bir <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> çağıran nesne `InsertEmployees` veritabanına bir çalışan giriş eklemek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="2fc36-143">It creates an <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object that calls the `InsertEmployees` method to add an employee entry to the database.</span></span> <span data-ttu-id="2fc36-144">`AddEmployees` Sonra yöntemi çağırır `PostRandomEmployees` birden çok gönderme yöntemi `Employee` nesneleri <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="2fc36-144">The `AddEmployees` method then calls the `PostRandomEmployees` method to post multiple `Employee` objects to the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object.</span></span> <span data-ttu-id="2fc36-145">`AddEmployees` Yöntemi sonra tüm işlemleri tamamlamak için INSERT bekler.</span><span class="sxs-lookup"><span data-stu-id="2fc36-145">The `AddEmployees` method then waits for all insert operations to finish.</span></span>  
  
<a name="buffering"></a>   
## <a name="using-buffering-to-add-employee-data-to-the-database"></a><span data-ttu-id="2fc36-146">Çalışan veri eklemek için arabelleğe almayı kullanma</span><span class="sxs-lookup"><span data-stu-id="2fc36-146">Using Buffering to Add Employee Data to the Database</span></span>  
 <span data-ttu-id="2fc36-147">Ekleme `Program` sınıfı `AddEmployeesBatched` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2fc36-147">Add to the `Program` class the `AddEmployeesBatched` method.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#6)]
 [!code-vb[TPLDataflow_BatchDatabase#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#6)]  
  
 <span data-ttu-id="2fc36-148">Bu yöntem benzer `AddEmployees`, ayrıca kullanır ancak bu <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> birden çok arabellek için sınıf `Employee` bu nesnelerle göndermeden önce nesneleri <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="2fc36-148">This method resembles `AddEmployees`, except that it also uses the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class to buffer multiple `Employee` objects before it sends those objects to the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object.</span></span> <span data-ttu-id="2fc36-149">Çünkü <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> sınıfı, bir koleksiyon olarak birden çok öğeleri yayar <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> dizisi olarak davranacak şekilde nesne değiştiren `Employee` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="2fc36-149">Because the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class propagates out multiple elements as a collection, the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object is modified to act on an array of `Employee` objects.</span></span> <span data-ttu-id="2fc36-150">Olarak `AddEmployees` yöntemi, `AddEmployeesBatched` çağrıları `PostRandomEmployees` birden çok gönderme yöntemi `Employee` nesneleri; ancak, `AddEmployeesBatched` bu nesnelere yazılarını <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="2fc36-150">As in the `AddEmployees` method, `AddEmployeesBatched` calls the `PostRandomEmployees` method to post multiple `Employee` objects; however, `AddEmployeesBatched` posts these objects to the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> object.</span></span> <span data-ttu-id="2fc36-151">`AddEmployeesBatched` Yöntemi de tüm tamamlanması için işlemleri eklemek için bekler.</span><span class="sxs-lookup"><span data-stu-id="2fc36-151">The `AddEmployeesBatched`  method also waits for all insert operations to finish.</span></span>  
  
<a name="bufferedJoin"></a>   
## <a name="using-buffered-join-to-read-employee-data-from-the-database"></a><span data-ttu-id="2fc36-152">Çalışan verilerini veritabanından okumak için arabelleğe alınan birleştirme kullanma</span><span class="sxs-lookup"><span data-stu-id="2fc36-152">Using Buffered Join to Read Employee Data from the Database</span></span>  
 <span data-ttu-id="2fc36-153">Ekleme `Program` sınıfı `GetRandomEmployees` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2fc36-153">Add to the `Program` class the `GetRandomEmployees` method.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#7)]
 [!code-vb[TPLDataflow_BatchDatabase#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#7)]  
  
 <span data-ttu-id="2fc36-154">Bu yöntem konsoluna rastgele çalışanlar hakkında bilgi yazdırır.</span><span class="sxs-lookup"><span data-stu-id="2fc36-154">This method prints information about random employees to the console.</span></span> <span data-ttu-id="2fc36-155">Birkaç rastgele oluşturduğu `Employee` nesneleri ve çağrıları `GetEmployeeID` her nesne için benzersiz tanımlayıcı alma yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2fc36-155">It creates several random `Employee` objects and calls the `GetEmployeeID` method to retrieve the unique identifier for each object.</span></span> <span data-ttu-id="2fc36-156">Çünkü `GetEmployeeID` yöntemi aykırı verilen ilk ve son adları ile eşleşen hiçbir çalışan ise `GetRandomEmployees` yöntemi kullanır <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> depolamak için sınıf `Employee` başarılı çağrılar için nesneleri `GetEmployeeID` ve <xref:System.Exception?displayProperty=nameWithType> başarısız çağrılar nesneleri.</span><span class="sxs-lookup"><span data-stu-id="2fc36-156">Because the `GetEmployeeID` method throws an exception if there is no matching employee with the given first and last names, the `GetRandomEmployees` method uses the <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> class to store `Employee` objects for successful calls to `GetEmployeeID` and <xref:System.Exception?displayProperty=nameWithType> objects for calls that fail.</span></span> <span data-ttu-id="2fc36-157"><xref:System.Threading.Tasks.Dataflow.ActionBlock%601> Nesne bu örnekte davranan bir <xref:System.Tuple%602> listesini tutar nesne `Employee` nesneleri ve listesini <xref:System.Exception> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="2fc36-157">The <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object in this example acts on a <xref:System.Tuple%602> object that holds a list of `Employee` objects and a list of <xref:System.Exception> objects.</span></span> <span data-ttu-id="2fc36-158"><xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> Nesne yayar bu verileri, alınan toplam `Employee` ve <xref:System.Exception> nesne sayısına eşittir toplu iş boyutu.</span><span class="sxs-lookup"><span data-stu-id="2fc36-158">The <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> object propagates out this data when the sum of the received `Employee` and <xref:System.Exception> object counts equals the batch size.</span></span>  
  
<a name="complete"></a>   
## <a name="the-complete-example"></a><span data-ttu-id="2fc36-159">Tam Örnek</span><span class="sxs-lookup"><span data-stu-id="2fc36-159">The Complete Example</span></span>  
 <span data-ttu-id="2fc36-160">Aşağıdaki örnek eksiksiz kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="2fc36-160">The following example shows the complete code.</span></span> <span data-ttu-id="2fc36-161">`Main` Yöntemi toplu veritabanı eklenenleri toplu olmayan veritabanı eklemeleri gerçekleştirmek için gereken süre karşı gerçekleştirmek için gereken zamanı karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="2fc36-161">The `Main` method compares the time that is required to perform batched database insertions versus the time to perform non-batched database insertions.</span></span> <span data-ttu-id="2fc36-162">Ayrıca, çalışan verilerini veritabanından okunur ve ayrıca hatalarını raporlamak için arabelleğe alınan birleşim kullanımını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="2fc36-162">It also demonstrates the use of buffered join to read employee data from the database and also report errors.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#100)]
 [!code-vb[TPLDataflow_BatchDatabase#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#100)]  
  
## <a name="see-also"></a><span data-ttu-id="2fc36-163">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2fc36-163">See Also</span></span>  
 [<span data-ttu-id="2fc36-164">Veri akışı</span><span class="sxs-lookup"><span data-stu-id="2fc36-164">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
