---
title: "İzlenecek yol: Verimliliği Artırmak için BatchBlock ve BatchedJoinBlock'u Kullanma"
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, improving efficiency
ms.assetid: 5beb4983-80c2-4f60-8c51-a07f9fd94cb3
ms.openlocfilehash: 4b2b6a6124bf8cc0fb3b379607135283678e3268
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73091354"
---
# <a name="walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency"></a><span data-ttu-id="3a664-102">İzlenecek yol: Verimliliği Artırmak için BatchBlock ve BatchedJoinBlock'u Kullanma</span><span class="sxs-lookup"><span data-stu-id="3a664-102">Walkthrough: Using BatchBlock and BatchedJoinBlock to Improve Efficiency</span></span>

<span data-ttu-id="3a664-103">TPL veri akışı kitaplığı, bir veya daha fazla kaynaktan veri alıp, daha sonra bu arabellekli verileri tek bir koleksiyon olarak yayabilmeniz için <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> sınıfları sağlar.</span><span class="sxs-lookup"><span data-stu-id="3a664-103">The TPL Dataflow Library provides the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> classes so that you can receive and buffer data from one or more sources and then propagate out that buffered data as one collection.</span></span> <span data-ttu-id="3a664-104">Bu toplu işlem mekanizması, bir veya daha fazla kaynaktan veri topladığınızda ve sonra birden çok veri öğesini toplu iş olarak işyaparken yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="3a664-104">This batching mechanism is useful when you collect data from one or more sources and then process multiple data elements as a batch.</span></span> <span data-ttu-id="3a664-105">Örneğin, bir veritabanına kayıt eklemek için veri akışı kullanan bir uygulamayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="3a664-105">For example, consider an application that uses dataflow to insert records into a database.</span></span> <span data-ttu-id="3a664-106">Aynı anda birden çok öğe bir kez eklenirse, bu işlem daha verimli olabilir.</span><span class="sxs-lookup"><span data-stu-id="3a664-106">This operation can be more efficient if multiple items are inserted at the same time instead of one at a time sequentially.</span></span> <span data-ttu-id="3a664-107">Bu belgede, bu tür veritabanı ekleme işlemlerinin verimliliğini artırmak için <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> sınıfının nasıl kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3a664-107">This document describes how to use the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class to improve the efficiency of such database insert operations.</span></span> <span data-ttu-id="3a664-108">Ayrıca, hem sonuçları hem de program bir veritabanından okurken oluşan tüm özel durumları yakalamak için <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> sınıfının nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="3a664-108">It also describes how to use the <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> class to capture both the results and any exceptions that occur when the program reads from a database.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="prerequisites"></a><span data-ttu-id="3a664-109">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="3a664-109">Prerequisites</span></span>

1. <span data-ttu-id="3a664-110">Bu yönergeyi başlamadan önce [veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) belgesindeki JOIN blokları bölümünü okuyun.</span><span class="sxs-lookup"><span data-stu-id="3a664-110">Read the Join Blocks section in the [Dataflow](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) document before you start this walkthrough.</span></span>

2. <span data-ttu-id="3a664-111">Bilgisayarınızda bulunan Northwind. sdf veritabanının bir kopyasına sahip olduğunuzdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="3a664-111">Ensure that you have a copy of the Northwind database, Northwind.sdf, available on your computer.</span></span> <span data-ttu-id="3a664-112">Bu dosya genellikle% Program Files%\Microsoft SQL Server Compact Edition \V3.5\samples\\klasöründe bulunur.</span><span class="sxs-lookup"><span data-stu-id="3a664-112">This file is typically located in the folder %Program Files%\Microsoft SQL Server Compact Edition\v3.5\Samples\\.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="3a664-113">Windows 'un bazı sürümlerinde, Visual Studio yönetici olmayan bir modda çalışıyorsa Northwind. sdf 'ye bağlanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="3a664-113">In some versions of Windows, you cannot connect to Northwind.sdf if Visual Studio is running in a non-administrator mode.</span></span> <span data-ttu-id="3a664-114">Northwind. sdf 'ye bağlanmak için Visual Studio 'yu veya Visual Studio için bir Geliştirici Komut İstemi **yönetici olarak çalıştır** modunda başlatın.</span><span class="sxs-lookup"><span data-stu-id="3a664-114">To connect to Northwind.sdf, start Visual Studio or a Developer Command Prompt for Visual Studio in the **Run as administrator** mode.</span></span>

<span data-ttu-id="3a664-115">Bu izlenecek yol aşağıdaki bölümleri içerir:</span><span class="sxs-lookup"><span data-stu-id="3a664-115">This walkthrough contains the following sections:</span></span>

- [<span data-ttu-id="3a664-116">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="3a664-116">Creating the Console Application</span></span>](#creating)

- [<span data-ttu-id="3a664-117">Çalışan sınıfını tanımlama</span><span class="sxs-lookup"><span data-stu-id="3a664-117">Defining the Employee Class</span></span>](#employeeClass)

- [<span data-ttu-id="3a664-118">Çalışan veritabanı Işlemlerini tanımlama</span><span class="sxs-lookup"><span data-stu-id="3a664-118">Defining Employee Database Operations</span></span>](#operations)

- [<span data-ttu-id="3a664-119">Arabelleğe alma kullanmadan çalışan verileri veritabanına ekleme</span><span class="sxs-lookup"><span data-stu-id="3a664-119">Adding Employee Data to the Database without Using Buffering</span></span>](#nonBuffering)

- [<span data-ttu-id="3a664-120">Veritabanına çalışan verileri eklemek için arabelleğe alma kullanma</span><span class="sxs-lookup"><span data-stu-id="3a664-120">Using Buffering to Add Employee Data to the Database</span></span>](#buffering)

- [<span data-ttu-id="3a664-121">Veritabanından çalışan verilerini okumak için arabellekli katılmayı kullanma</span><span class="sxs-lookup"><span data-stu-id="3a664-121">Using Buffered Join to Read Employee Data from the Database</span></span>](#bufferedJoin)

- [<span data-ttu-id="3a664-122">Tüm örnek</span><span class="sxs-lookup"><span data-stu-id="3a664-122">The Complete Example</span></span>](#complete)

<a name="creating"></a>

## <a name="creating-the-console-application"></a><span data-ttu-id="3a664-123">Konsol Uygulaması Oluşturma</span><span class="sxs-lookup"><span data-stu-id="3a664-123">Creating the Console Application</span></span>

1. <span data-ttu-id="3a664-124">Visual Studio 'da bir görsel C# veya Visual Basic **konsol uygulaması** projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3a664-124">In Visual Studio, create a Visual C# or Visual Basic **Console Application** project.</span></span> <span data-ttu-id="3a664-125">Bu belgede, proje `DataflowBatchDatabase`olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="3a664-125">In this document, the project is named `DataflowBatchDatabase`.</span></span>

2. <span data-ttu-id="3a664-126">Projenizde, System. Data. SqlServerCe. dll ' ye bir başvuru ve System. Threading. Tasks. Dataflow. dll başvurusu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3a664-126">In your project, add a reference to System.Data.SqlServerCe.dll and a reference to System.Threading.Tasks.Dataflow.dll.</span></span>

3. <span data-ttu-id="3a664-127">Form1.cs (Visual Basic için Form1. vb) 'in aşağıdaki `using` (`Imports` Visual Basic) deyimlerine sahip olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="3a664-127">Ensure that Form1.cs (Form1.vb for Visual Basic) contains the following `using` (`Imports` in Visual Basic) statements.</span></span>

    [!code-csharp[TPLDataflow_BatchDatabase#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#1)]
    [!code-vb[TPLDataflow_BatchDatabase#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#1)]

4. <span data-ttu-id="3a664-128">Aşağıdaki veri üyelerini `Program` sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3a664-128">Add the following data members to the `Program` class.</span></span>

    [!code-csharp[TPLDataflow_BatchDatabase#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#2)]
    [!code-vb[TPLDataflow_BatchDatabase#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#2)]

<a name="employeeClass"></a>

## <a name="defining-the-employee-class"></a><span data-ttu-id="3a664-129">Çalışan sınıfını tanımlama</span><span class="sxs-lookup"><span data-stu-id="3a664-129">Defining the Employee Class</span></span>

<span data-ttu-id="3a664-130">`Employee` sınıfına `Program` sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3a664-130">Add to the `Program` class the `Employee` class.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#3)]
[!code-vb[TPLDataflow_BatchDatabase#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#3)]

<span data-ttu-id="3a664-131">`Employee` sınıfı üç özellik içerir, `EmployeeID`, `LastName`ve `FirstName`.</span><span class="sxs-lookup"><span data-stu-id="3a664-131">The `Employee` class contains three properties, `EmployeeID`, `LastName`, and `FirstName`.</span></span> <span data-ttu-id="3a664-132">Bu özellikler, Northwind veritabanındaki `Employees` tablosundaki `Employee ID`, `Last Name`ve `First Name` sütunlarına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="3a664-132">These properties correspond to the `Employee ID`, `Last Name`, and `First Name` columns in the `Employees` table in the Northwind database.</span></span> <span data-ttu-id="3a664-133">Bu gösterim için `Employee` sınıfı, özellikleri için rastgele değerler içeren bir `Employee` nesnesi oluşturan `Random` yöntemini de tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3a664-133">For this demonstration, the `Employee` class also defines the `Random` method, which creates an `Employee` object that has random values for its properties.</span></span>

<a name="operations"></a>

## <a name="defining-employee-database-operations"></a><span data-ttu-id="3a664-134">Çalışan veritabanı Işlemlerini tanımlama</span><span class="sxs-lookup"><span data-stu-id="3a664-134">Defining Employee Database Operations</span></span>

<span data-ttu-id="3a664-135">`InsertEmployees`, `GetEmployeeCount`ve `GetEmployeeID` yöntemlerine `Program` sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3a664-135">Add to the `Program` class the `InsertEmployees`, `GetEmployeeCount`, and `GetEmployeeID` methods.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#4)]
[!code-vb[TPLDataflow_BatchDatabase#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#4)]

<span data-ttu-id="3a664-136">`InsertEmployees` yöntemi veritabanına yeni çalışan kayıtları ekler.</span><span class="sxs-lookup"><span data-stu-id="3a664-136">The `InsertEmployees` method adds new employee records to the database.</span></span> <span data-ttu-id="3a664-137">`GetEmployeeCount` yöntemi, `Employees` tablosundaki giriş sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="3a664-137">The `GetEmployeeCount` method retrieves the number of entries in the `Employees` table.</span></span> <span data-ttu-id="3a664-138">`GetEmployeeID` yöntemi, belirtilen ada sahip ilk çalışanın tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="3a664-138">The `GetEmployeeID` method retrieves the identifier of the first employee that has the provided name.</span></span> <span data-ttu-id="3a664-139">Bu yöntemlerin her biri, Northwind veritabanına bir bağlantı dizesi alır ve veritabanı ile iletişim kurmak için `System.Data.SqlServerCe` ad alanındaki işlevleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="3a664-139">Each of these methods takes a connection string to the Northwind database and uses functionality in the `System.Data.SqlServerCe` namespace to communicate with the database.</span></span>

<a name="nonBuffering"></a>

## <a name="adding-employee-data-to-the-database-without-using-buffering"></a><span data-ttu-id="3a664-140">Arabelleğe alma kullanmadan çalışan verileri veritabanına ekleme</span><span class="sxs-lookup"><span data-stu-id="3a664-140">Adding Employee Data to the Database Without Using Buffering</span></span>

<span data-ttu-id="3a664-141">`AddEmployees` ve `PostRandomEmployees` yöntemlerine `Program` sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3a664-141">Add to the `Program` class the `AddEmployees` and `PostRandomEmployees` methods.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#5)]
[!code-vb[TPLDataflow_BatchDatabase#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#5)]

<span data-ttu-id="3a664-142">`AddEmployees` yöntemi, veri akışı kullanarak veritabanına rastgele çalışan verileri ekler.</span><span class="sxs-lookup"><span data-stu-id="3a664-142">The `AddEmployees` method adds random employee data to the database by using dataflow.</span></span> <span data-ttu-id="3a664-143">Veritabanına bir çalışan girişi eklemek için `InsertEmployees` yöntemini çağıran bir <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3a664-143">It creates an <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object that calls the `InsertEmployees` method to add an employee entry to the database.</span></span> <span data-ttu-id="3a664-144">`AddEmployees` yöntemi daha sonra birden çok `Employee` nesnesini <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> nesnesine göndermek için `PostRandomEmployees` yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="3a664-144">The `AddEmployees` method then calls the `PostRandomEmployees` method to post multiple `Employee` objects to the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object.</span></span> <span data-ttu-id="3a664-145">`AddEmployees` yöntemi daha sonra tüm ekleme işlemlerinin bitmesini bekler.</span><span class="sxs-lookup"><span data-stu-id="3a664-145">The `AddEmployees` method then waits for all insert operations to finish.</span></span>

<a name="buffering"></a>

## <a name="using-buffering-to-add-employee-data-to-the-database"></a><span data-ttu-id="3a664-146">Veritabanına çalışan verileri eklemek için arabelleğe alma kullanma</span><span class="sxs-lookup"><span data-stu-id="3a664-146">Using Buffering to Add Employee Data to the Database</span></span>

<span data-ttu-id="3a664-147">`AddEmployeesBatched` yöntemine `Program` sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3a664-147">Add to the `Program` class the `AddEmployeesBatched` method.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#6)]
[!code-vb[TPLDataflow_BatchDatabase#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#6)]

<span data-ttu-id="3a664-148">Bu yöntem, bu nesneleri <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> nesnesine göndermeden önce birden çok `Employee` nesnesini arabelleğe almak için <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> sınıfını da kullandığından `AddEmployees`benzer.</span><span class="sxs-lookup"><span data-stu-id="3a664-148">This method resembles `AddEmployees`, except that it also uses the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class to buffer multiple `Employee` objects before it sends those objects to the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object.</span></span> <span data-ttu-id="3a664-149"><xref:System.Threading.Tasks.Dataflow.BatchBlock%601> sınıfı birden çok öğeyi bir koleksiyon olarak yaydığı için, <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> nesnesi `Employee` nesne dizisinde çalışacak şekilde değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="3a664-149">Because the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class propagates out multiple elements as a collection, the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object is modified to act on an array of `Employee` objects.</span></span> <span data-ttu-id="3a664-150">`AddEmployees` yönteminde olduğu gibi, `AddEmployeesBatched` birden çok `Employee` nesnesi göndermek için `PostRandomEmployees` yöntemini çağırır; Ancak, bu nesneleri <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> nesnesine `AddEmployeesBatched` nakleder.</span><span class="sxs-lookup"><span data-stu-id="3a664-150">As in the `AddEmployees` method, `AddEmployeesBatched` calls the `PostRandomEmployees` method to post multiple `Employee` objects; however, `AddEmployeesBatched` posts these objects to the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> object.</span></span> <span data-ttu-id="3a664-151">`AddEmployeesBatched` Yöntemi ayrıca tüm ekleme işlemlerinin bitmesini bekler.</span><span class="sxs-lookup"><span data-stu-id="3a664-151">The `AddEmployeesBatched`  method also waits for all insert operations to finish.</span></span>

<a name="bufferedJoin"></a>

## <a name="using-buffered-join-to-read-employee-data-from-the-database"></a><span data-ttu-id="3a664-152">Veritabanından çalışan verilerini okumak için arabellekli katılmayı kullanma</span><span class="sxs-lookup"><span data-stu-id="3a664-152">Using Buffered Join to Read Employee Data from the Database</span></span>

<span data-ttu-id="3a664-153">`GetRandomEmployees` yöntemine `Program` sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3a664-153">Add to the `Program` class the `GetRandomEmployees` method.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#7)]
[!code-vb[TPLDataflow_BatchDatabase#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#7)]

<span data-ttu-id="3a664-154">Bu yöntem, rastgele çalışanlar hakkındaki bilgileri konsola yazdırır.</span><span class="sxs-lookup"><span data-stu-id="3a664-154">This method prints information about random employees to the console.</span></span> <span data-ttu-id="3a664-155">Birkaç rastgele `Employee` nesnesi oluşturur ve her bir nesnenin benzersiz tanımlayıcısını almak için `GetEmployeeID` yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="3a664-155">It creates several random `Employee` objects and calls the `GetEmployeeID` method to retrieve the unique identifier for each object.</span></span> <span data-ttu-id="3a664-156">`GetEmployeeID` Yöntemi verilen ilk ve son adlarla eşleşen bir çalışan yoksa bir özel durum oluşturduğundan, `GetRandomEmployees` yöntemi, başarısız olan çağrılar için `GetEmployeeID` ve <xref:System.Exception?displayProperty=nameWithType> nesnelerine başarılı çağrılar için `Employee` nesneleri depolamak üzere <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> sınıfını kullanır .</span><span class="sxs-lookup"><span data-stu-id="3a664-156">Because the `GetEmployeeID` method throws an exception if there is no matching employee with the given first and last names, the `GetRandomEmployees` method uses the <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> class to store `Employee` objects for successful calls to `GetEmployeeID` and <xref:System.Exception?displayProperty=nameWithType> objects for calls that fail.</span></span> <span data-ttu-id="3a664-157">Bu örnekteki <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> nesnesi, `Employee` nesne listesini ve <xref:System.Exception> nesnelerinin bir listesini tutan bir <xref:System.Tuple%602> nesnesi üzerinde davranır.</span><span class="sxs-lookup"><span data-stu-id="3a664-157">The <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object in this example acts on a <xref:System.Tuple%602> object that holds a list of `Employee` objects and a list of <xref:System.Exception> objects.</span></span> <span data-ttu-id="3a664-158"><xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> nesnesi, alınan `Employee` toplamı ve <xref:System.Exception> nesne sayısı toplu iş boyutuna eşitse bu verileri yayar.</span><span class="sxs-lookup"><span data-stu-id="3a664-158">The <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> object propagates out this data when the sum of the received `Employee` and <xref:System.Exception> object counts equals the batch size.</span></span>

<a name="complete"></a>

## <a name="the-complete-example"></a><span data-ttu-id="3a664-159">Tam Örnek</span><span class="sxs-lookup"><span data-stu-id="3a664-159">The Complete Example</span></span>

<span data-ttu-id="3a664-160">Aşağıdaki örnek, tüm kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="3a664-160">The following example shows the complete code.</span></span> <span data-ttu-id="3a664-161">`Main` yöntemi, toplu veritabanı eklemeleri gerçekleştirmek için gereken süreyi, toplu olmayan veritabanı eklemeleri gerçekleştirme zamanına göre karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="3a664-161">The `Main` method compares the time that is required to perform batched database insertions versus the time to perform non-batched database insertions.</span></span> <span data-ttu-id="3a664-162">Ayrıca, veritabanından çalışan verilerini okumak ve ayrıca hataları raporlamak için, arabelleğe alınmış birleştirmenin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3a664-162">It also demonstrates the use of buffered join to read employee data from the database and also report errors.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#100)]
[!code-vb[TPLDataflow_BatchDatabase#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#100)]

## <a name="see-also"></a><span data-ttu-id="3a664-163">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3a664-163">See also</span></span>

- [<span data-ttu-id="3a664-164">Veri akışı</span><span class="sxs-lookup"><span data-stu-id="3a664-164">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
