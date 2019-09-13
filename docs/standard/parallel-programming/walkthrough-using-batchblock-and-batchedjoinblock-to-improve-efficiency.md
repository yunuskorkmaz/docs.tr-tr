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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 32255c988397853c4b38e4ab723c7261a8999899
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929209"
---
# <a name="walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency"></a><span data-ttu-id="478b4-102">İzlenecek yol: Verimliliği Artırmak için BatchBlock ve BatchedJoinBlock'u Kullanma</span><span class="sxs-lookup"><span data-stu-id="478b4-102">Walkthrough: Using BatchBlock and BatchedJoinBlock to Improve Efficiency</span></span>

<span data-ttu-id="478b4-103">TPL veri akışı kitaplığı, ve <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> sınıflarını, bir veya daha fazla kaynaktan veri alıp arabelleğe almak ve ardından bu arabelleğe alınmış verileri tek bir koleksiyon olarak yayabilmeniz için sağlar.</span><span class="sxs-lookup"><span data-stu-id="478b4-103">The TPL Dataflow Library provides the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> classes so that you can receive and buffer data from one or more sources and then propagate out that buffered data as one collection.</span></span> <span data-ttu-id="478b4-104">Bu toplu işlem mekanizması, bir veya daha fazla kaynaktan veri topladığınızda ve sonra birden çok veri öğesini toplu iş olarak işyaparken yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="478b4-104">This batching mechanism is useful when you collect data from one or more sources and then process multiple data elements as a batch.</span></span> <span data-ttu-id="478b4-105">Örneğin, bir veritabanına kayıt eklemek için veri akışı kullanan bir uygulamayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="478b4-105">For example, consider an application that uses dataflow to insert records into a database.</span></span> <span data-ttu-id="478b4-106">Aynı anda birden çok öğe bir kez eklenirse, bu işlem daha verimli olabilir.</span><span class="sxs-lookup"><span data-stu-id="478b4-106">This operation can be more efficient if multiple items are inserted at the same time instead of one at a time sequentially.</span></span> <span data-ttu-id="478b4-107">Bu belgede, <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> bu tür veritabanı ekleme işlemlerinin verimliliğini artırmak için sınıfının nasıl kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="478b4-107">This document describes how to use the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class to improve the efficiency of such database insert operations.</span></span> <span data-ttu-id="478b4-108">Ayrıca, hem sonuçları hem de program <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> bir veritabanından okurken oluşan tüm özel durumları yakalamak için sınıfının nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="478b4-108">It also describes how to use the <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> class to capture both the results and any exceptions that occur when the program reads from a database.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="prerequisites"></a><span data-ttu-id="478b4-109">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="478b4-109">Prerequisites</span></span>

1. <span data-ttu-id="478b4-110">Bu yönergeyi başlamadan önce [veri akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) belgesindeki JOIN blokları bölümünü okuyun.</span><span class="sxs-lookup"><span data-stu-id="478b4-110">Read the Join Blocks section in the [Dataflow](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) document before you start this walkthrough.</span></span>

2. <span data-ttu-id="478b4-111">Bilgisayarınızda bulunan Northwind. sdf veritabanının bir kopyasına sahip olduğunuzdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="478b4-111">Ensure that you have a copy of the Northwind database, Northwind.sdf, available on your computer.</span></span> <span data-ttu-id="478b4-112">Bu dosya genellikle% Program Files%\Microsoft SQL Server Compact Edition \V3.5\samples\\klasöründe bulunur.</span><span class="sxs-lookup"><span data-stu-id="478b4-112">This file is typically located in the folder %Program Files%\Microsoft SQL Server Compact Edition\v3.5\Samples\\.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="478b4-113">Windows 'un bazı sürümlerinde, Visual Studio yönetici olmayan bir modda çalışıyorsa Northwind. sdf 'ye bağlanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="478b4-113">In some versions of Windows, you cannot connect to Northwind.sdf if Visual Studio is running in a non-administrator mode.</span></span> <span data-ttu-id="478b4-114">Northwind. sdf 'ye bağlanmak için Visual Studio 'yu veya Visual Studio için bir Geliştirici Komut İstemi **yönetici olarak çalıştır** modunda başlatın.</span><span class="sxs-lookup"><span data-stu-id="478b4-114">To connect to Northwind.sdf, start Visual Studio or a Developer Command Prompt for Visual Studio in the **Run as administrator** mode.</span></span>

<span data-ttu-id="478b4-115">Bu izlenecek yol aşağıdaki bölümleri içerir:</span><span class="sxs-lookup"><span data-stu-id="478b4-115">This walkthrough contains the following sections:</span></span>

- [<span data-ttu-id="478b4-116">Konsol uygulaması oluşturma</span><span class="sxs-lookup"><span data-stu-id="478b4-116">Creating the Console Application</span></span>](#creating)

- [<span data-ttu-id="478b4-117">Çalışan sınıfını tanımlama</span><span class="sxs-lookup"><span data-stu-id="478b4-117">Defining the Employee Class</span></span>](#employeeClass)

- [<span data-ttu-id="478b4-118">Çalışan veritabanı Işlemlerini tanımlama</span><span class="sxs-lookup"><span data-stu-id="478b4-118">Defining Employee Database Operations</span></span>](#operations)

- [<span data-ttu-id="478b4-119">Arabelleğe alma kullanmadan çalışan verileri veritabanına ekleme</span><span class="sxs-lookup"><span data-stu-id="478b4-119">Adding Employee Data to the Database without Using Buffering</span></span>](#nonBuffering)

- [<span data-ttu-id="478b4-120">Veritabanına çalışan verileri eklemek için arabelleğe alma kullanma</span><span class="sxs-lookup"><span data-stu-id="478b4-120">Using Buffering to Add Employee Data to the Database</span></span>](#buffering)

- [<span data-ttu-id="478b4-121">Veritabanından çalışan verilerini okumak için arabellekli katılmayı kullanma</span><span class="sxs-lookup"><span data-stu-id="478b4-121">Using Buffered Join to Read Employee Data from the Database</span></span>](#bufferedJoin)

- [<span data-ttu-id="478b4-122">Tüm örnek</span><span class="sxs-lookup"><span data-stu-id="478b4-122">The Complete Example</span></span>](#complete)

<a name="creating"></a>

## <a name="creating-the-console-application"></a><span data-ttu-id="478b4-123">Konsol Uygulaması Oluşturma</span><span class="sxs-lookup"><span data-stu-id="478b4-123">Creating the Console Application</span></span>

1. <span data-ttu-id="478b4-124">Visual Studio 'da bir görsel C# veya Visual Basic **konsol uygulaması** projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="478b4-124">In Visual Studio, create a Visual C# or Visual Basic **Console Application** project.</span></span> <span data-ttu-id="478b4-125">Bu belgede, proje adlandırılır `DataflowBatchDatabase`.</span><span class="sxs-lookup"><span data-stu-id="478b4-125">In this document, the project is named `DataflowBatchDatabase`.</span></span>

2. <span data-ttu-id="478b4-126">Projenizde, System. Data. SqlServerCe. dll ' ye bir başvuru ve System. Threading. Tasks. Dataflow. dll başvurusu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="478b4-126">In your project, add a reference to System.Data.SqlServerCe.dll and a reference to System.Threading.Tasks.Dataflow.dll.</span></span>

3. <span data-ttu-id="478b4-127">Form1.cs (Visual Basic için Form1. vb) içinde aşağıdaki `using` (`Imports` Visual Basic) deyimlerini içerdiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="478b4-127">Ensure that Form1.cs (Form1.vb for Visual Basic) contains the following `using` (`Imports` in Visual Basic) statements.</span></span>

    [!code-csharp[TPLDataflow_BatchDatabase#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#1)]
    [!code-vb[TPLDataflow_BatchDatabase#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#1)]

4. <span data-ttu-id="478b4-128">`Program` Sınıfına aşağıdaki veri üyelerini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="478b4-128">Add the following data members to the `Program` class.</span></span>

    [!code-csharp[TPLDataflow_BatchDatabase#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#2)]
    [!code-vb[TPLDataflow_BatchDatabase#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#2)]

<a name="employeeClass"></a>

## <a name="defining-the-employee-class"></a><span data-ttu-id="478b4-129">Çalışan sınıfını tanımlama</span><span class="sxs-lookup"><span data-stu-id="478b4-129">Defining the Employee Class</span></span>

<span data-ttu-id="478b4-130">`Program` Sınıfına`Employee` sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="478b4-130">Add to the `Program` class the `Employee` class.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#3)]
[!code-vb[TPLDataflow_BatchDatabase#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#3)]

<span data-ttu-id="478b4-131">Sınıfı üç `FirstName`özellik `EmployeeID` içerir`LastName`,,ve. `Employee`</span><span class="sxs-lookup"><span data-stu-id="478b4-131">The `Employee` class contains three properties, `EmployeeID`, `LastName`, and `FirstName`.</span></span> <span data-ttu-id="478b4-132">Bu özellikler, Northwind veritabanındaki `Employee ID` `Employees` tablodaki `Last Name`, ve `First Name` sütunlarına karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="478b4-132">These properties correspond to the `Employee ID`, `Last Name`, and `First Name` columns in the `Employees` table in the Northwind database.</span></span> <span data-ttu-id="478b4-133">Bu gösterim için, `Employee` sınıfı, özellikleri için rastgele değerler içeren bir `Employee` nesne oluşturan `Random` yöntemini de tanımlar.</span><span class="sxs-lookup"><span data-stu-id="478b4-133">For this demonstration, the `Employee` class also defines the `Random` method, which creates an `Employee` object that has random values for its properties.</span></span>

<a name="operations"></a>

## <a name="defining-employee-database-operations"></a><span data-ttu-id="478b4-134">Çalışan veritabanı Işlemlerini tanımlama</span><span class="sxs-lookup"><span data-stu-id="478b4-134">Defining Employee Database Operations</span></span>

<span data-ttu-id="478b4-135">`InsertEmployees` `Program` , Ve`GetEmployeeCount`yöntemlerine sınıfına ekleyin. `GetEmployeeID`</span><span class="sxs-lookup"><span data-stu-id="478b4-135">Add to the `Program` class the `InsertEmployees`, `GetEmployeeCount`, and `GetEmployeeID` methods.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#4)]
[!code-vb[TPLDataflow_BatchDatabase#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#4)]

<span data-ttu-id="478b4-136">`InsertEmployees` Yöntemi veritabanına yeni çalışan kayıtları ekler.</span><span class="sxs-lookup"><span data-stu-id="478b4-136">The `InsertEmployees` method adds new employee records to the database.</span></span> <span data-ttu-id="478b4-137">Yöntemi, `Employees` tablodaki giriş sayısını alır. `GetEmployeeCount`</span><span class="sxs-lookup"><span data-stu-id="478b4-137">The `GetEmployeeCount` method retrieves the number of entries in the `Employees` table.</span></span> <span data-ttu-id="478b4-138">`GetEmployeeID` Yöntemi, belirtilen ada sahip ilk çalışanın tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="478b4-138">The `GetEmployeeID` method retrieves the identifier of the first employee that has the provided name.</span></span> <span data-ttu-id="478b4-139">Bu yöntemlerin her biri, Northwind veritabanına bir bağlantı dizesi alır ve veritabanı ile iletişim kurmak için `System.Data.SqlServerCe` ad alanındaki işlevleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="478b4-139">Each of these methods takes a connection string to the Northwind database and uses functionality in the `System.Data.SqlServerCe` namespace to communicate with the database.</span></span>

<a name="nonBuffering"></a>

## <a name="adding-employee-data-to-the-database-without-using-buffering"></a><span data-ttu-id="478b4-140">Arabelleğe alma kullanmadan çalışan verileri veritabanına ekleme</span><span class="sxs-lookup"><span data-stu-id="478b4-140">Adding Employee Data to the Database Without Using Buffering</span></span>

<span data-ttu-id="478b4-141">`Program` Ve`PostRandomEmployees`yöntemlerini sınıfına ekleyin. `AddEmployees`</span><span class="sxs-lookup"><span data-stu-id="478b4-141">Add to the `Program` class the `AddEmployees` and `PostRandomEmployees` methods.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#5)]
[!code-vb[TPLDataflow_BatchDatabase#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#5)]

<span data-ttu-id="478b4-142">Yöntemi `AddEmployees` , veri akışı kullanarak veritabanına rastgele çalışan verileri ekler.</span><span class="sxs-lookup"><span data-stu-id="478b4-142">The `AddEmployees` method adds random employee data to the database by using dataflow.</span></span> <span data-ttu-id="478b4-143">Veritabanına bir çalışan <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> girişi eklemek için `InsertEmployees` yöntemini çağıran bir nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="478b4-143">It creates an <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object that calls the `InsertEmployees` method to add an employee entry to the database.</span></span> <span data-ttu-id="478b4-144">Yöntemi daha sonra <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> nesnesine birden `PostRandomEmployees` fazla `Employee` nesne göndermek için yöntemini çağırır. `AddEmployees`</span><span class="sxs-lookup"><span data-stu-id="478b4-144">The `AddEmployees` method then calls the `PostRandomEmployees` method to post multiple `Employee` objects to the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object.</span></span> <span data-ttu-id="478b4-145">`AddEmployees` Yöntemi daha sonra tüm ekleme işlemlerinin bitmesini bekler.</span><span class="sxs-lookup"><span data-stu-id="478b4-145">The `AddEmployees` method then waits for all insert operations to finish.</span></span>

<a name="buffering"></a>

## <a name="using-buffering-to-add-employee-data-to-the-database"></a><span data-ttu-id="478b4-146">Veritabanına çalışan verileri eklemek için arabelleğe alma kullanma</span><span class="sxs-lookup"><span data-stu-id="478b4-146">Using Buffering to Add Employee Data to the Database</span></span>

<span data-ttu-id="478b4-147">Yöntemine`AddEmployeesBatched`sınıfınaekleyin. `Program`</span><span class="sxs-lookup"><span data-stu-id="478b4-147">Add to the `Program` class the `AddEmployeesBatched` method.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#6)]
[!code-vb[TPLDataflow_BatchDatabase#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#6)]

<span data-ttu-id="478b4-148">Bu yöntem, `AddEmployees`bu nesneleri <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> nesnesine göndermeden önce birden çok <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> `Employee` nesneyi arabelleğe almak için sınıfını da kullandığından, buna benzer.</span><span class="sxs-lookup"><span data-stu-id="478b4-148">This method resembles `AddEmployees`, except that it also uses the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class to buffer multiple `Employee` objects before it sends those objects to the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object.</span></span> <span data-ttu-id="478b4-149">Sınıfı bir koleksiyon <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> olarak birden çok öğe yaydığı için nesne bir `Employee` nesne dizisi üzerinde çalışacak şekilde değiştirilir. <xref:System.Threading.Tasks.Dataflow.BatchBlock%601></span><span class="sxs-lookup"><span data-stu-id="478b4-149">Because the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class propagates out multiple elements as a collection, the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object is modified to act on an array of `Employee` objects.</span></span> <span data-ttu-id="478b4-150">`AddEmployeesBatched` `AddEmployeesBatched` `PostRandomEmployees` <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> Yönteminde olduğu gibi, birden çok`Employee` nesne göndermek için yöntemini çağırır; ancak, bu nesneleri nesnesine gönderir. `AddEmployees`</span><span class="sxs-lookup"><span data-stu-id="478b4-150">As in the `AddEmployees` method, `AddEmployeesBatched` calls the `PostRandomEmployees` method to post multiple `Employee` objects; however, `AddEmployeesBatched` posts these objects to the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> object.</span></span> <span data-ttu-id="478b4-151">`AddEmployeesBatched` Yöntemi ayrıca tüm ekleme işlemlerinin bitmesini bekler.</span><span class="sxs-lookup"><span data-stu-id="478b4-151">The `AddEmployeesBatched`  method also waits for all insert operations to finish.</span></span>

<a name="bufferedJoin"></a>

## <a name="using-buffered-join-to-read-employee-data-from-the-database"></a><span data-ttu-id="478b4-152">Veritabanından çalışan verilerini okumak için arabellekli katılmayı kullanma</span><span class="sxs-lookup"><span data-stu-id="478b4-152">Using Buffered Join to Read Employee Data from the Database</span></span>

<span data-ttu-id="478b4-153">Yöntemine`GetRandomEmployees`sınıfınaekleyin. `Program`</span><span class="sxs-lookup"><span data-stu-id="478b4-153">Add to the `Program` class the `GetRandomEmployees` method.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#7)]
[!code-vb[TPLDataflow_BatchDatabase#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#7)]

<span data-ttu-id="478b4-154">Bu yöntem, rastgele çalışanlar hakkındaki bilgileri konsola yazdırır.</span><span class="sxs-lookup"><span data-stu-id="478b4-154">This method prints information about random employees to the console.</span></span> <span data-ttu-id="478b4-155">Birkaç rastgele `Employee` nesne oluşturur ve her bir nesnenin `GetEmployeeID` benzersiz tanımlayıcısını almak için yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="478b4-155">It creates several random `Employee` objects and calls the `GetEmployeeID` method to retrieve the unique identifier for each object.</span></span> <span data-ttu-id="478b4-156"><xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> `GetRandomEmployees` `GetEmployeeID` `Employee` Verilen ilk ve son adlarla eşleşen bir çalışan yoksa Yöntem bir özel durum oluşturduğundan, yöntemi, ve ' a yapılan başarılı çağrılar için nesneleri depolamak üzere sınıfını kullanır. `GetEmployeeID` <xref:System.Exception?displayProperty=nameWithType> başarısız olan çağrıların nesneleri.</span><span class="sxs-lookup"><span data-stu-id="478b4-156">Because the `GetEmployeeID` method throws an exception if there is no matching employee with the given first and last names, the `GetRandomEmployees` method uses the <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> class to store `Employee` objects for successful calls to `GetEmployeeID` and <xref:System.Exception?displayProperty=nameWithType> objects for calls that fail.</span></span> <span data-ttu-id="478b4-157">Bu <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> örnekteki nesne, nesne listesini `Employee` ve nesne <xref:System.Tuple%602> listesini <xref:System.Exception> tutan bir nesnesi üzerinde davranır.</span><span class="sxs-lookup"><span data-stu-id="478b4-157">The <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object in this example acts on a <xref:System.Tuple%602> object that holds a list of `Employee` objects and a list of <xref:System.Exception> objects.</span></span> <span data-ttu-id="478b4-158">Alınan <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> venesne<xref:System.Exception> sayısı toplamı toplu iş boyutuna eşitse nesne bu verileri yayar. `Employee`</span><span class="sxs-lookup"><span data-stu-id="478b4-158">The <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> object propagates out this data when the sum of the received `Employee` and <xref:System.Exception> object counts equals the batch size.</span></span>

<a name="complete"></a>

## <a name="the-complete-example"></a><span data-ttu-id="478b4-159">Tam Örnek</span><span class="sxs-lookup"><span data-stu-id="478b4-159">The Complete Example</span></span>

<span data-ttu-id="478b4-160">Aşağıdaki örnek, tüm kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="478b4-160">The following example shows the complete code.</span></span> <span data-ttu-id="478b4-161">`Main` Yöntemi, toplu veritabanı eklemeleri gerçekleştirmek için gereken süreyi, toplu olmayan veritabanı ekleme işlemini gerçekleştirmek için zaman karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="478b4-161">The `Main` method compares the time that is required to perform batched database insertions versus the time to perform non-batched database insertions.</span></span> <span data-ttu-id="478b4-162">Ayrıca, veritabanından çalışan verilerini okumak ve ayrıca hataları raporlamak için, arabelleğe alınmış birleştirmenin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="478b4-162">It also demonstrates the use of buffered join to read employee data from the database and also report errors.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#100)]
[!code-vb[TPLDataflow_BatchDatabase#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#100)]

## <a name="see-also"></a><span data-ttu-id="478b4-163">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="478b4-163">See also</span></span>

- [<span data-ttu-id="478b4-164">Veri akışı</span><span class="sxs-lookup"><span data-stu-id="478b4-164">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
