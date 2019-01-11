---
title: "İzlenecek yol: Verimliliği artırmak için BatchBlock ve Batchedjoinblock'u kullanma"
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, improving efficiency
ms.assetid: 5beb4983-80c2-4f60-8c51-a07f9fd94cb3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0367b4224b49377d8d17045e044976e1c511a8ed
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2019
ms.locfileid: "54222114"
---
# <a name="walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency"></a><span data-ttu-id="2d5db-102">İzlenecek yol: Verimliliği artırmak için BatchBlock ve Batchedjoinblock'u kullanma</span><span class="sxs-lookup"><span data-stu-id="2d5db-102">Walkthrough: Using BatchBlock and BatchedJoinBlock to Improve Efficiency</span></span>
<span data-ttu-id="2d5db-103">TPL veri akışı kitaplığı sağlar <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> ve böylece, bu bildirimleri alabilen ve bir veya daha fazla kaynaktan veri arabellek ve ardından o arabelleğe alınan verileri bir koleksiyon olarak yayınlar sınıfları.</span><span class="sxs-lookup"><span data-stu-id="2d5db-103">The TPL Dataflow Library provides the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> classes so that you can receive and buffer data from one or more sources and then propagate out that buffered data as one collection.</span></span> <span data-ttu-id="2d5db-104">Bu toplu işleme mekanizması bir veya daha fazla kaynaktan veri toplayın ve ardından birden fazla veri öğesi toplu olarak işleme yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="2d5db-104">This batching mechanism is useful when you collect data from one or more sources and then process multiple data elements as a batch.</span></span> <span data-ttu-id="2d5db-105">Örneğin, kayıtları bir veritabanına eklemek için veri akışı kullanan bir uygulamayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="2d5db-105">For example, consider an application that uses dataflow to insert records into a database.</span></span> <span data-ttu-id="2d5db-106">Bu işlem, birden çok öğe aynı zamanda bir kerede yerine sıralı olarak eklenirse daha verimli olabilir.</span><span class="sxs-lookup"><span data-stu-id="2d5db-106">This operation can be more efficient if multiple items are inserted at the same time instead of one at a time sequentially.</span></span> <span data-ttu-id="2d5db-107">Bu belgenin nasıl kullanılacağını açıklar <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> sınıfı gibi veritabanı verimliliğini artırmak için işlemler Ekle.</span><span class="sxs-lookup"><span data-stu-id="2d5db-107">This document describes how to use the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class to improve the efficiency of such database insert operations.</span></span> <span data-ttu-id="2d5db-108">Ayrıca nasıl kullanılacağını açıklar <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> hem sonuçları hem de program veritabanından okuduğunda oluşan özel durumları yakalamak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="2d5db-108">It also describes how to use the <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> class to capture both the results and any exceptions that occur when the program reads from a database.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="prerequisites"></a><span data-ttu-id="2d5db-109">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="2d5db-109">Prerequisites</span></span>  
  
1.  <span data-ttu-id="2d5db-110">Join Blocks bölümünü okuyun [veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) bu kılavuza başlamadan önce belgeleyin.</span><span class="sxs-lookup"><span data-stu-id="2d5db-110">Read the Join Blocks section in the [Dataflow](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) document before you start this walkthrough.</span></span>  
  
2.  <span data-ttu-id="2d5db-111">Northwind veritabanının, Northwind.sdf, bilgisayarınızda mevcut bir kopyasına sahip olduğunuzdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="2d5db-111">Ensure that you have a copy of the Northwind database, Northwind.sdf, available on your computer.</span></span> <span data-ttu-id="2d5db-112">Bu dosya, klasör % Program Files%\Microsoft SQL Server Compact Edition\v3.5\Samples genellikle bulunur\\.</span><span class="sxs-lookup"><span data-stu-id="2d5db-112">This file is typically located in the folder %Program Files%\Microsoft SQL Server Compact Edition\v3.5\Samples\\.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="2d5db-113">Bazı Windows sürümlerinde, Visual Studio'yu bir yönetici olmayan modda çalışıyorsa Northwind.sdf dosyasına bağlanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="2d5db-113">In some versions of Windows, you cannot connect to Northwind.sdf if Visual Studio is running in a non-administrator mode.</span></span> <span data-ttu-id="2d5db-114">Northwind.sdf'ye bağlamak için Visual Studio ya da bir geliştirici komut istemi için Visual Studio'da başlatma **yönetici olarak çalıştır** modu.</span><span class="sxs-lookup"><span data-stu-id="2d5db-114">To connect to Northwind.sdf, start Visual Studio or a Developer Command Prompt for Visual Studio in the **Run as administrator** mode.</span></span>  
  
 <span data-ttu-id="2d5db-115">Bu izlenecek yol aşağıdaki bölümleri içerir:</span><span class="sxs-lookup"><span data-stu-id="2d5db-115">This walkthrough contains the following sections:</span></span>  
  
-   [<span data-ttu-id="2d5db-116">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="2d5db-116">Creating the Console Application</span></span>](#creating)  
  
-   [<span data-ttu-id="2d5db-117">Çalışan sınıfı tanımlama</span><span class="sxs-lookup"><span data-stu-id="2d5db-117">Defining the Employee Class</span></span>](#employeeClass)  
  
-   [<span data-ttu-id="2d5db-118">Çalışan veritabanı işlemleri tanımlama</span><span class="sxs-lookup"><span data-stu-id="2d5db-118">Defining Employee Database Operations</span></span>](#operations)  
  
-   [<span data-ttu-id="2d5db-119">Çalışan verilerini veritabanına ara belleğe almadan ekleme</span><span class="sxs-lookup"><span data-stu-id="2d5db-119">Adding Employee Data to the Database without Using Buffering</span></span>](#nonBuffering)  
  
-   [<span data-ttu-id="2d5db-120">Veritabanına çalışan verilerini eklemek için arabelleğe almayı kullanma</span><span class="sxs-lookup"><span data-stu-id="2d5db-120">Using Buffering to Add Employee Data to the Database</span></span>](#buffering)  
  
-   [<span data-ttu-id="2d5db-121">Veritabanından çalışan verilerini okumak için arabelleğe alınmış birleşim kullanma</span><span class="sxs-lookup"><span data-stu-id="2d5db-121">Using Buffered Join to Read Employee Data from the Database</span></span>](#bufferedJoin)  
  
-   [<span data-ttu-id="2d5db-122">Tam örnek</span><span class="sxs-lookup"><span data-stu-id="2d5db-122">The Complete Example</span></span>](#complete)  
  
<a name="creating"></a>   
## <a name="creating-the-console-application"></a><span data-ttu-id="2d5db-123">Konsol Uygulaması Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2d5db-123">Creating the Console Application</span></span>  
  
<a name="consoleApp"></a>   
1.  <span data-ttu-id="2d5db-124">Bir Visual C# veya Visual Basic Visual Studio'da oluşturma **konsol uygulaması** proje.</span><span class="sxs-lookup"><span data-stu-id="2d5db-124">In Visual Studio, create a Visual C# or Visual Basic **Console Application** project.</span></span> <span data-ttu-id="2d5db-125">Bu belgede, proje adı `DataflowBatchDatabase`.</span><span class="sxs-lookup"><span data-stu-id="2d5db-125">In this document, the project is named `DataflowBatchDatabase`.</span></span>  
  
2.  <span data-ttu-id="2d5db-126">Projenizde, System.Data.SqlServerCe.dll'ye ve System.Threading.Tasks.Dataflow.dll'ye birer başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2d5db-126">In your project, add a reference to System.Data.SqlServerCe.dll and a reference to System.Threading.Tasks.Dataflow.dll.</span></span>  
  
3.  <span data-ttu-id="2d5db-127">Form1.cs (Visual Basic için Form1.vb) aşağıdaki içerdiğinden emin olun `using` (`Imports` Visual Basic'te) ifadeleri.</span><span class="sxs-lookup"><span data-stu-id="2d5db-127">Ensure that Form1.cs (Form1.vb for Visual Basic) contains the following `using` (`Imports` in Visual Basic) statements.</span></span>  
  
     [!code-csharp[TPLDataflow_BatchDatabase#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#1)]
     [!code-vb[TPLDataflow_BatchDatabase#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#1)]  
  
4.  <span data-ttu-id="2d5db-128">Aşağıdaki veri üyelerini ekleyin `Program` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="2d5db-128">Add the following data members to the `Program` class.</span></span>  
  
     [!code-csharp[TPLDataflow_BatchDatabase#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#2)]
     [!code-vb[TPLDataflow_BatchDatabase#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#2)]  
  
<a name="employeeClass"></a>   
## <a name="defining-the-employee-class"></a><span data-ttu-id="2d5db-129">Çalışan sınıfı tanımlama</span><span class="sxs-lookup"><span data-stu-id="2d5db-129">Defining the Employee Class</span></span>  
 <span data-ttu-id="2d5db-130">Ekleme `Program` sınıfı `Employee` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="2d5db-130">Add to the `Program` class the `Employee` class.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#3)]
 [!code-vb[TPLDataflow_BatchDatabase#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#3)]  
  
 <span data-ttu-id="2d5db-131">`Employee` Sınıfı üç özellik içerir `EmployeeID`, `LastName`, ve `FirstName`.</span><span class="sxs-lookup"><span data-stu-id="2d5db-131">The `Employee` class contains three properties, `EmployeeID`, `LastName`, and `FirstName`.</span></span> <span data-ttu-id="2d5db-132">Bu özelliklere karşılık `Employee ID`, `Last Name`, ve `First Name` sütunlarında `Employees` Northwind veritabanındaki tablo.</span><span class="sxs-lookup"><span data-stu-id="2d5db-132">These properties correspond to the `Employee ID`, `Last Name`, and `First Name` columns in the `Employees` table in the Northwind database.</span></span> <span data-ttu-id="2d5db-133">Bu Tanıtım için `Employee` sınıfı da tanımlar `Random` oluşturan yöntemi bir `Employee` kendi özelliklerine ilişkin rasgele değerlere sahip bir nesne.</span><span class="sxs-lookup"><span data-stu-id="2d5db-133">For this demonstration, the `Employee` class also defines the `Random` method, which creates an `Employee` object that has random values for its properties.</span></span>  
  
<a name="operations"></a>   
## <a name="defining-employee-database-operations"></a><span data-ttu-id="2d5db-134">Çalışan veritabanı işlemleri tanımlama</span><span class="sxs-lookup"><span data-stu-id="2d5db-134">Defining Employee Database Operations</span></span>  
 <span data-ttu-id="2d5db-135">Ekleme `Program` sınıfı `InsertEmployees`, `GetEmployeeCount`, ve `GetEmployeeID` yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="2d5db-135">Add to the `Program` class the `InsertEmployees`, `GetEmployeeCount`, and `GetEmployeeID` methods.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#4)]
 [!code-vb[TPLDataflow_BatchDatabase#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#4)]  
  
 <span data-ttu-id="2d5db-136">`InsertEmployees` Yöntemi veritabanına yeni çalışan kayıtlarını ekler.</span><span class="sxs-lookup"><span data-stu-id="2d5db-136">The `InsertEmployees` method adds new employee records to the database.</span></span> <span data-ttu-id="2d5db-137">`GetEmployeeCount` Yöntemi içerisindeki giriş sayısını alır `Employees` tablo.</span><span class="sxs-lookup"><span data-stu-id="2d5db-137">The `GetEmployeeCount` method retrieves the number of entries in the `Employees` table.</span></span> <span data-ttu-id="2d5db-138">`GetEmployeeID` Yöntemi sağlanan ada sahip ilk çalışanın tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="2d5db-138">The `GetEmployeeID` method retrieves the identifier of the first employee that has the provided name.</span></span> <span data-ttu-id="2d5db-139">Bu yöntemlerin her biri Northwind veritabanına bir bağlantı dizesi alır ve işlevselliği kullanır `System.Data.SqlServerCe` veritabanıyla iletişim kurmak için ad alanı.</span><span class="sxs-lookup"><span data-stu-id="2d5db-139">Each of these methods takes a connection string to the Northwind database and uses functionality in the `System.Data.SqlServerCe` namespace to communicate with the database.</span></span>  
  
<a name="nonBuffering"></a>   
## <a name="adding-employee-data-to-the-database-without-using-buffering"></a><span data-ttu-id="2d5db-140">Çalışan verilerini veritabanına ara belleğe almadan ekleme</span><span class="sxs-lookup"><span data-stu-id="2d5db-140">Adding Employee Data to the Database Without Using Buffering</span></span>  
 <span data-ttu-id="2d5db-141">Ekleme `Program` sınıfı `AddEmployees` ve `PostRandomEmployees` yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="2d5db-141">Add to the `Program` class the `AddEmployees` and `PostRandomEmployees` methods.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#5)]
 [!code-vb[TPLDataflow_BatchDatabase#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#5)]  
  
 <span data-ttu-id="2d5db-142">`AddEmployees` Yöntemi rasgele çalışan verileri ekler veritabanına veri akışı kullanarak.</span><span class="sxs-lookup"><span data-stu-id="2d5db-142">The `AddEmployees` method adds random employee data to the database by using dataflow.</span></span> <span data-ttu-id="2d5db-143">Oluşturur bir <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> çağıran nesne `InsertEmployees` veritabanına çalışan girdisi eklemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2d5db-143">It creates an <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object that calls the `InsertEmployees` method to add an employee entry to the database.</span></span> <span data-ttu-id="2d5db-144">`AddEmployees` Sonra yöntemi çağırır `PostRandomEmployees` göndermek için yöntemi `Employee` nesneleri için <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> nesne.</span><span class="sxs-lookup"><span data-stu-id="2d5db-144">The `AddEmployees` method then calls the `PostRandomEmployees` method to post multiple `Employee` objects to the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object.</span></span> <span data-ttu-id="2d5db-145">`AddEmployees` Yöntemi ardından için tüm ekleme işlemlerinin bitmesini bekler.</span><span class="sxs-lookup"><span data-stu-id="2d5db-145">The `AddEmployees` method then waits for all insert operations to finish.</span></span>  
  
<a name="buffering"></a>   
## <a name="using-buffering-to-add-employee-data-to-the-database"></a><span data-ttu-id="2d5db-146">Veritabanına çalışan verilerini eklemek için arabelleğe almayı kullanma</span><span class="sxs-lookup"><span data-stu-id="2d5db-146">Using Buffering to Add Employee Data to the Database</span></span>  
 <span data-ttu-id="2d5db-147">Ekleme `Program` sınıfı `AddEmployeesBatched` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2d5db-147">Add to the `Program` class the `AddEmployeesBatched` method.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#6)]
 [!code-vb[TPLDataflow_BatchDatabase#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#6)]  
  
 <span data-ttu-id="2d5db-148">Bu yöntem benzer `AddEmployees`, da kullanması hariç, <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> birden fazla arabellek için sınıf `Employee` bu nesnelere göndermeden önce <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> nesne.</span><span class="sxs-lookup"><span data-stu-id="2d5db-148">This method resembles `AddEmployees`, except that it also uses the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class to buffer multiple `Employee` objects before it sends those objects to the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object.</span></span> <span data-ttu-id="2d5db-149">Çünkü <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> sınıfı koleksiyon olarak birden çok öğe yayar <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> nesne dizisi olarak görev yapacak değiştirildiğinde `Employee` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="2d5db-149">Because the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class propagates out multiple elements as a collection, the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object is modified to act on an array of `Employee` objects.</span></span> <span data-ttu-id="2d5db-150">Olarak `AddEmployees` yöntemi `AddEmployeesBatched` çağrıları `PostRandomEmployees` göndermek için yöntemi `Employee` nesnelerini; ancak, `AddEmployeesBatched` bu nesnelere gönderileri <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> nesne.</span><span class="sxs-lookup"><span data-stu-id="2d5db-150">As in the `AddEmployees` method, `AddEmployeesBatched` calls the `PostRandomEmployees` method to post multiple `Employee` objects; however, `AddEmployeesBatched` posts these objects to the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> object.</span></span> <span data-ttu-id="2d5db-151">`AddEmployeesBatched` Yöntemi ayrıca tüm ekleme işlemlerinin bitmesini için bekler.</span><span class="sxs-lookup"><span data-stu-id="2d5db-151">The `AddEmployeesBatched`  method also waits for all insert operations to finish.</span></span>  
  
<a name="bufferedJoin"></a>   
## <a name="using-buffered-join-to-read-employee-data-from-the-database"></a><span data-ttu-id="2d5db-152">Veritabanından çalışan verilerini okumak için arabelleğe alınmış birleşim kullanma</span><span class="sxs-lookup"><span data-stu-id="2d5db-152">Using Buffered Join to Read Employee Data from the Database</span></span>  
 <span data-ttu-id="2d5db-153">Ekleme `Program` sınıfı `GetRandomEmployees` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2d5db-153">Add to the `Program` class the `GetRandomEmployees` method.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#7)]
 [!code-vb[TPLDataflow_BatchDatabase#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#7)]  
  
 <span data-ttu-id="2d5db-154">Bu yöntem, konsola, rasgele çalışanlar hakkında bilgileri yazdırır.</span><span class="sxs-lookup"><span data-stu-id="2d5db-154">This method prints information about random employees to the console.</span></span> <span data-ttu-id="2d5db-155">Birkaç rastgele oluşturur `Employee` nesneleri ve çağrıları `GetEmployeeID` her nesne için benzersiz tanımlayıcısını almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2d5db-155">It creates several random `Employee` objects and calls the `GetEmployeeID` method to retrieve the unique identifier for each object.</span></span> <span data-ttu-id="2d5db-156">Çünkü `GetEmployeeID` yöntemi, belirtilen ilk ve son adları eşleşen çalışan yoksa bir özel durum oluşturursa `GetRandomEmployees` yöntemi kullanan <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> depolamak için sınıf `Employee` başarılı çağrılar için nesneleri `GetEmployeeID` ve <xref:System.Exception?displayProperty=nameWithType> başarısız olan çağrılar nesneleri.</span><span class="sxs-lookup"><span data-stu-id="2d5db-156">Because the `GetEmployeeID` method throws an exception if there is no matching employee with the given first and last names, the `GetRandomEmployees` method uses the <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> class to store `Employee` objects for successful calls to `GetEmployeeID` and <xref:System.Exception?displayProperty=nameWithType> objects for calls that fail.</span></span> <span data-ttu-id="2d5db-157"><xref:System.Threading.Tasks.Dataflow.ActionBlock%601> Etkiler nesne bu örnekte bir <xref:System.Tuple%602> listesini tutan nesne `Employee` nesneleri ve listesini <xref:System.Exception> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="2d5db-157">The <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object in this example acts on a <xref:System.Tuple%602> object that holds a list of `Employee` objects and a list of <xref:System.Exception> objects.</span></span> <span data-ttu-id="2d5db-158"><xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> Nesnesi yayar, bu verileri, alınan toplam `Employee` ve <xref:System.Exception> nesnesi sayıları boyutuna eşit.</span><span class="sxs-lookup"><span data-stu-id="2d5db-158">The <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> object propagates out this data when the sum of the received `Employee` and <xref:System.Exception> object counts equals the batch size.</span></span>  
  
<a name="complete"></a>   
## <a name="the-complete-example"></a><span data-ttu-id="2d5db-159">Tam Örnek</span><span class="sxs-lookup"><span data-stu-id="2d5db-159">The Complete Example</span></span>  
 <span data-ttu-id="2d5db-160">Aşağıdaki örnekte tam kod gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2d5db-160">The following example shows the complete code.</span></span> <span data-ttu-id="2d5db-161">`Main` Yöntemi yığınlanmış veritabanı eklemeye veritabanı eklemelerini gerçekleştirmek için zaman karşı yığınlanmamış gerçekleştirmek için gerekli zamanı karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="2d5db-161">The `Main` method compares the time that is required to perform batched database insertions versus the time to perform non-batched database insertions.</span></span> <span data-ttu-id="2d5db-162">Ayrıca veritabanından çalışan verilerini okumak ve ayrıca hatalarını raporlamak için arabelleğe alınmış birleşim kullanımını da gösterir.</span><span class="sxs-lookup"><span data-stu-id="2d5db-162">It also demonstrates the use of buffered join to read employee data from the database and also report errors.</span></span>  
  
 [!code-csharp[TPLDataflow_BatchDatabase#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#100)]
 [!code-vb[TPLDataflow_BatchDatabase#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#100)]  
  
## <a name="see-also"></a><span data-ttu-id="2d5db-163">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d5db-163">See also</span></span>

- [<span data-ttu-id="2d5db-164">Veri akışı</span><span class="sxs-lookup"><span data-stu-id="2d5db-164">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
