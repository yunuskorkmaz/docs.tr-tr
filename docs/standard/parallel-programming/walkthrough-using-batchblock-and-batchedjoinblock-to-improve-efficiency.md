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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73091354"
---
# <a name="walkthrough-using-batchblock-and-batchedjoinblock-to-improve-efficiency"></a><span data-ttu-id="b592b-102">İzlenecek yol: Verimliliği Artırmak için BatchBlock ve BatchedJoinBlock'u Kullanma</span><span class="sxs-lookup"><span data-stu-id="b592b-102">Walkthrough: Using BatchBlock and BatchedJoinBlock to Improve Efficiency</span></span>

<span data-ttu-id="b592b-103">TPL Veri Akışı Kitaplığı, bir veya daha fazla kaynaktan veri alıp arabelleğe almanız ve sonra arabelleğe alınan verileri tek bir koleksiyon olarak yayabileceğiniz ve <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> sınıfları sağlar.</span><span class="sxs-lookup"><span data-stu-id="b592b-103">The TPL Dataflow Library provides the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602?displayProperty=nameWithType> classes so that you can receive and buffer data from one or more sources and then propagate out that buffered data as one collection.</span></span> <span data-ttu-id="b592b-104">Bu toplu işlem mekanizması, bir veya daha fazla kaynaktan veri toplayıp birden çok veri öğesini toplu olarak işlediğinde yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="b592b-104">This batching mechanism is useful when you collect data from one or more sources and then process multiple data elements as a batch.</span></span> <span data-ttu-id="b592b-105">Örneğin, kayıtları veritabanına eklemek için veri akışını kullanan bir uygulama düşünün.</span><span class="sxs-lookup"><span data-stu-id="b592b-105">For example, consider an application that uses dataflow to insert records into a database.</span></span> <span data-ttu-id="b592b-106">Bu işlem, birer birer sırayla yerine aynı anda birden çok öğe eklenirse daha verimli olabilir.</span><span class="sxs-lookup"><span data-stu-id="b592b-106">This operation can be more efficient if multiple items are inserted at the same time instead of one at a time sequentially.</span></span> <span data-ttu-id="b592b-107">Bu belge, bu <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> tür veritabanı ekleme işlemlerinin verimliliğini artırmak için sınıfın nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="b592b-107">This document describes how to use the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class to improve the efficiency of such database insert operations.</span></span> <span data-ttu-id="b592b-108">Ayrıca, hem sonuçları <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> hem de program veritabanından okuduğunda oluşan özel durumları yakalamak için sınıfın nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="b592b-108">It also describes how to use the <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> class to capture both the results and any exceptions that occur when the program reads from a database.</span></span>

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="prerequisites"></a><span data-ttu-id="b592b-109">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="b592b-109">Prerequisites</span></span>

1. <span data-ttu-id="b592b-110">Bu gözden geçirmeyi başlatmadan önce [Veri Akışı](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) belgesindeki Blokları Birleştir bölümünü okuyun.</span><span class="sxs-lookup"><span data-stu-id="b592b-110">Read the Join Blocks section in the [Dataflow](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) document before you start this walkthrough.</span></span>

2. <span data-ttu-id="b592b-111">Northwind veritabanınorthwind.sdf, bilgisayarınızda bulunan bir kopyasını olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="b592b-111">Ensure that you have a copy of the Northwind database, Northwind.sdf, available on your computer.</span></span> <span data-ttu-id="b592b-112">Bu dosya genellikle %Program Dosyaları%\Microsoft SQL Server Compact Edition\v3.5\Samples\\klasöründe bulunur.</span><span class="sxs-lookup"><span data-stu-id="b592b-112">This file is typically located in the folder %Program Files%\Microsoft SQL Server Compact Edition\v3.5\Samples\\.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="b592b-113">Windows'un bazı sürümlerinde, Visual Studio yönetici olmayan bir modda çalışıyorsa Northwind.sdf'ye bağlanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="b592b-113">In some versions of Windows, you cannot connect to Northwind.sdf if Visual Studio is running in a non-administrator mode.</span></span> <span data-ttu-id="b592b-114">Northwind.sdf'ye bağlanmak için Visual Studio'yu veya Yönetici modunda **Visual** Studio için Geliştirici Komut Komut Ustem'i başlatın.</span><span class="sxs-lookup"><span data-stu-id="b592b-114">To connect to Northwind.sdf, start Visual Studio or a Developer Command Prompt for Visual Studio in the **Run as administrator** mode.</span></span>

<span data-ttu-id="b592b-115">Bu izksiyon aşağıdaki bölümleri içerir:</span><span class="sxs-lookup"><span data-stu-id="b592b-115">This walkthrough contains the following sections:</span></span>

- [<span data-ttu-id="b592b-116">Konsol Uygulaması Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b592b-116">Creating the Console Application</span></span>](#creating)

- [<span data-ttu-id="b592b-117">Çalışan Sınıfının Tanımlanması</span><span class="sxs-lookup"><span data-stu-id="b592b-117">Defining the Employee Class</span></span>](#employeeClass)

- [<span data-ttu-id="b592b-118">Çalışan Veritabanı İşlemlerinin Tanımlanması</span><span class="sxs-lookup"><span data-stu-id="b592b-118">Defining Employee Database Operations</span></span>](#operations)

- [<span data-ttu-id="b592b-119">Arabelleğe Alma Kullanmadan Veritabanına Çalışan Verilerini Ekleme</span><span class="sxs-lookup"><span data-stu-id="b592b-119">Adding Employee Data to the Database without Using Buffering</span></span>](#nonBuffering)

- [<span data-ttu-id="b592b-120">Çalışan Verilerini Veritabanına Eklemek Için Arabelleğe Alma Kullanma</span><span class="sxs-lookup"><span data-stu-id="b592b-120">Using Buffering to Add Employee Data to the Database</span></span>](#buffering)

- [<span data-ttu-id="b592b-121">Veritabanından Çalışan Verilerini Okumak için Arabelleğe Alma Birleştirme'yi Kullanma</span><span class="sxs-lookup"><span data-stu-id="b592b-121">Using Buffered Join to Read Employee Data from the Database</span></span>](#bufferedJoin)

- [<span data-ttu-id="b592b-122">Tam Örnek</span><span class="sxs-lookup"><span data-stu-id="b592b-122">The Complete Example</span></span>](#complete)

<a name="creating"></a>

## <a name="creating-the-console-application"></a><span data-ttu-id="b592b-123">Konsol Uygulaması Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b592b-123">Creating the Console Application</span></span>

1. <span data-ttu-id="b592b-124">Visual Studio'da Visual C# veya Visual Basic **Console Application** projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b592b-124">In Visual Studio, create a Visual C# or Visual Basic **Console Application** project.</span></span> <span data-ttu-id="b592b-125">Bu belgede, proje adı `DataflowBatchDatabase`.</span><span class="sxs-lookup"><span data-stu-id="b592b-125">In this document, the project is named `DataflowBatchDatabase`.</span></span>

2. <span data-ttu-id="b592b-126">Projenizde System.Data.SqlServerCe.dll'ye bir referans ve System.Threading.Tasks.Dataflow.dll adresine bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b592b-126">In your project, add a reference to System.Data.SqlServerCe.dll and a reference to System.Threading.Tasks.Dataflow.dll.</span></span>

3. <span data-ttu-id="b592b-127">Form1.cs (Visual Basic için Form1.vb) `using` aşağıdaki`Imports` ifadeleri içerdiğinden emin olun ( Visual Basic'te).</span><span class="sxs-lookup"><span data-stu-id="b592b-127">Ensure that Form1.cs (Form1.vb for Visual Basic) contains the following `using` (`Imports` in Visual Basic) statements.</span></span>

    [!code-csharp[TPLDataflow_BatchDatabase#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#1)]
    [!code-vb[TPLDataflow_BatchDatabase#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#1)]

4. <span data-ttu-id="b592b-128">Aşağıdaki veri üyelerini sınıfa `Program` ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b592b-128">Add the following data members to the `Program` class.</span></span>

    [!code-csharp[TPLDataflow_BatchDatabase#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#2)]
    [!code-vb[TPLDataflow_BatchDatabase#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#2)]

<a name="employeeClass"></a>

## <a name="defining-the-employee-class"></a><span data-ttu-id="b592b-129">Çalışan Sınıfının Tanımlanması</span><span class="sxs-lookup"><span data-stu-id="b592b-129">Defining the Employee Class</span></span>

<span data-ttu-id="b592b-130">Sınıfa `Program` sınıfı `Employee` ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b592b-130">Add to the `Program` class the `Employee` class.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#3)]
[!code-vb[TPLDataflow_BatchDatabase#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#3)]

<span data-ttu-id="b592b-131">Sınıf `Employee` üç özellik `EmployeeID`içerir, `LastName` `FirstName`, , ve .</span><span class="sxs-lookup"><span data-stu-id="b592b-131">The `Employee` class contains three properties, `EmployeeID`, `LastName`, and `FirstName`.</span></span> <span data-ttu-id="b592b-132">Bu özellikler Northwind `Last Name`veritabanındaki `First Name` `Employees` tablodaki `Employee ID`, ve sütunlara karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="b592b-132">These properties correspond to the `Employee ID`, `Last Name`, and `First Name` columns in the `Employees` table in the Northwind database.</span></span> <span data-ttu-id="b592b-133">Bu gösteri için `Employee` sınıf, özellikleri `Random` için rasgele değerlere sahip bir `Employee` nesne oluşturan yöntemi de tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b592b-133">For this demonstration, the `Employee` class also defines the `Random` method, which creates an `Employee` object that has random values for its properties.</span></span>

<a name="operations"></a>

## <a name="defining-employee-database-operations"></a><span data-ttu-id="b592b-134">Çalışan Veritabanı İşlemlerinin Tanımlanması</span><span class="sxs-lookup"><span data-stu-id="b592b-134">Defining Employee Database Operations</span></span>

<span data-ttu-id="b592b-135">Sınıfa `Program` `InsertEmployees`, ve `GetEmployeeCount` `GetEmployeeID` yöntemleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b592b-135">Add to the `Program` class the `InsertEmployees`, `GetEmployeeCount`, and `GetEmployeeID` methods.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#4)]
[!code-vb[TPLDataflow_BatchDatabase#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#4)]

<span data-ttu-id="b592b-136">Yöntem `InsertEmployees` veritabanına yeni çalışan kayıtları ekler.</span><span class="sxs-lookup"><span data-stu-id="b592b-136">The `InsertEmployees` method adds new employee records to the database.</span></span> <span data-ttu-id="b592b-137">Yöntem, `GetEmployeeCount` `Employees` tablodaki giriş sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="b592b-137">The `GetEmployeeCount` method retrieves the number of entries in the `Employees` table.</span></span> <span data-ttu-id="b592b-138">Yöntem, `GetEmployeeID` sağlanan adı taşıyan ilk çalışanın tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="b592b-138">The `GetEmployeeID` method retrieves the identifier of the first employee that has the provided name.</span></span> <span data-ttu-id="b592b-139">Bu yöntemlerin her biri Northwind veritabanına bir bağlantı `System.Data.SqlServerCe` dizesi alır ve veritabanı ile iletişim kurmak için ad alanında işlevselliği kullanır.</span><span class="sxs-lookup"><span data-stu-id="b592b-139">Each of these methods takes a connection string to the Northwind database and uses functionality in the `System.Data.SqlServerCe` namespace to communicate with the database.</span></span>

<a name="nonBuffering"></a>

## <a name="adding-employee-data-to-the-database-without-using-buffering"></a><span data-ttu-id="b592b-140">Arabelleğe Alma Kullanmadan Veritabanına Çalışan Verilerini Ekleme</span><span class="sxs-lookup"><span data-stu-id="b592b-140">Adding Employee Data to the Database Without Using Buffering</span></span>

<span data-ttu-id="b592b-141">Sınıfa `Program` yöntemleri `AddEmployees` ve `PostRandomEmployees` yöntemleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b592b-141">Add to the `Program` class the `AddEmployees` and `PostRandomEmployees` methods.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#5)]
[!code-vb[TPLDataflow_BatchDatabase#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#5)]

<span data-ttu-id="b592b-142">Yöntem, `AddEmployees` veri akışını kullanarak veritabanına rasgele çalışan verileri ekler.</span><span class="sxs-lookup"><span data-stu-id="b592b-142">The `AddEmployees` method adds random employee data to the database by using dataflow.</span></span> <span data-ttu-id="b592b-143">Veritabanına `InsertEmployees` çalışan <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> girişi eklemek için yöntemi çağıran bir nesne oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b592b-143">It creates an <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object that calls the `InsertEmployees` method to add an employee entry to the database.</span></span> <span data-ttu-id="b592b-144">Yöntem `AddEmployees` daha sonra `PostRandomEmployees` <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> nesneye `Employee` birden çok nesne göndermek için yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="b592b-144">The `AddEmployees` method then calls the `PostRandomEmployees` method to post multiple `Employee` objects to the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object.</span></span> <span data-ttu-id="b592b-145">Yöntem `AddEmployees` daha sonra tüm ekleme işlemlerinin tamamlanmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="b592b-145">The `AddEmployees` method then waits for all insert operations to finish.</span></span>

<a name="buffering"></a>

## <a name="using-buffering-to-add-employee-data-to-the-database"></a><span data-ttu-id="b592b-146">Çalışan Verilerini Veritabanına Eklemek Için Arabelleğe Alma Kullanma</span><span class="sxs-lookup"><span data-stu-id="b592b-146">Using Buffering to Add Employee Data to the Database</span></span>

<span data-ttu-id="b592b-147">Sınıfa `Program` yöntemi `AddEmployeesBatched` ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b592b-147">Add to the `Program` class the `AddEmployeesBatched` method.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#6)]
[!code-vb[TPLDataflow_BatchDatabase#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#6)]

<span data-ttu-id="b592b-148">Bu yöntem, `AddEmployees`bu nesneleri <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> `Employee` <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> nesneye göndermeden önce birden çok nesneyi arabelleğe almak için sınıfı kullanması dışında benzer.</span><span class="sxs-lookup"><span data-stu-id="b592b-148">This method resembles `AddEmployees`, except that it also uses the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class to buffer multiple `Employee` objects before it sends those objects to the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object.</span></span> <span data-ttu-id="b592b-149">Sınıf <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> koleksiyon olarak birden çok öğe yaydığından, <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> nesne bir dizi `Employee` nesne üzerinde hareket etmek üzere değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="b592b-149">Because the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> class propagates out multiple elements as a collection, the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object is modified to act on an array of `Employee` objects.</span></span> <span data-ttu-id="b592b-150">`AddEmployees` Yöntemde olduğu `AddEmployeesBatched` gibi, `PostRandomEmployees` yöntemi birden `Employee` çok nesneyi göndermek için çağırır; ancak, `AddEmployeesBatched` bu nesneleri <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> nesneye gönderir.</span><span class="sxs-lookup"><span data-stu-id="b592b-150">As in the `AddEmployees` method, `AddEmployeesBatched` calls the `PostRandomEmployees` method to post multiple `Employee` objects; however, `AddEmployeesBatched` posts these objects to the <xref:System.Threading.Tasks.Dataflow.BatchBlock%601> object.</span></span> <span data-ttu-id="b592b-151">Yöntem `AddEmployeesBatched` ayrıca tüm ekleme işlemlerinin tamamlanmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="b592b-151">The `AddEmployeesBatched`  method also waits for all insert operations to finish.</span></span>

<a name="bufferedJoin"></a>

## <a name="using-buffered-join-to-read-employee-data-from-the-database"></a><span data-ttu-id="b592b-152">Veritabanından Çalışan Verilerini Okumak için Arabelleğe Alma Birleştirme'yi Kullanma</span><span class="sxs-lookup"><span data-stu-id="b592b-152">Using Buffered Join to Read Employee Data from the Database</span></span>

<span data-ttu-id="b592b-153">Sınıfa `Program` yöntemi `GetRandomEmployees` ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b592b-153">Add to the `Program` class the `GetRandomEmployees` method.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#7)]
[!code-vb[TPLDataflow_BatchDatabase#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#7)]

<span data-ttu-id="b592b-154">Bu yöntem, rasgele çalışanlar hakkındaki bilgileri konsola yazdırır.</span><span class="sxs-lookup"><span data-stu-id="b592b-154">This method prints information about random employees to the console.</span></span> <span data-ttu-id="b592b-155">Birkaç rasgele `Employee` nesne oluşturur ve `GetEmployeeID` her nesne için benzersiz tanımlayıcıyı almak için yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="b592b-155">It creates several random `Employee` objects and calls the `GetEmployeeID` method to retrieve the unique identifier for each object.</span></span> <span data-ttu-id="b592b-156">`GetEmployeeID` Yöntem, verilen ad ve soyadlarla eşleşen bir çalışan yoksa bir `GetRandomEmployees` özel durum <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> attığından, yöntem sınıfı başarılı çağrılar için nesneleri depolamak `Employee` `GetEmployeeID` için kullanır ve <xref:System.Exception?displayProperty=nameWithType> başarısız olan çağrılar için nesneler.</span><span class="sxs-lookup"><span data-stu-id="b592b-156">Because the `GetEmployeeID` method throws an exception if there is no matching employee with the given first and last names, the `GetRandomEmployees` method uses the <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> class to store `Employee` objects for successful calls to `GetEmployeeID` and <xref:System.Exception?displayProperty=nameWithType> objects for calls that fail.</span></span> <span data-ttu-id="b592b-157">Bu <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> örnekteki nesne, <xref:System.Tuple%602> `Employee` nesnelerin ve <xref:System.Exception> nesnelerin listesini tutan bir nesne üzerinde hareket eder.</span><span class="sxs-lookup"><span data-stu-id="b592b-157">The <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object in this example acts on a <xref:System.Tuple%602> object that holds a list of `Employee` objects and a list of <xref:System.Exception> objects.</span></span> <span data-ttu-id="b592b-158">Alınan <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> `Employee` ve <xref:System.Exception> nesne sayısı toplu iş boyutuna eşit olduğunda nesne bu verileri yaşar.</span><span class="sxs-lookup"><span data-stu-id="b592b-158">The <xref:System.Threading.Tasks.Dataflow.BatchedJoinBlock%602> object propagates out this data when the sum of the received `Employee` and <xref:System.Exception> object counts equals the batch size.</span></span>

<a name="complete"></a>

## <a name="the-complete-example"></a><span data-ttu-id="b592b-159">Tam Örnek</span><span class="sxs-lookup"><span data-stu-id="b592b-159">The Complete Example</span></span>

<span data-ttu-id="b592b-160">Aşağıdaki örnek, kodun tamamını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b592b-160">The following example shows the complete code.</span></span> <span data-ttu-id="b592b-161">Yöntem, `Main` toplu veritabanı eklemelerini gerçekleştirmek için gereken süreyle toplu olmayan veritabanı eklemelerini gerçekleştirme süresini karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="b592b-161">The `Main` method compares the time that is required to perform batched database insertions versus the time to perform non-batched database insertions.</span></span> <span data-ttu-id="b592b-162">Ayrıca, veritabanından çalışan verilerini okumak ve hataları bildirmek için arabelleğe alınan birleştirme kullanımını da gösterir.</span><span class="sxs-lookup"><span data-stu-id="b592b-162">It also demonstrates the use of buffered join to read employee data from the database and also report errors.</span></span>

[!code-csharp[TPLDataflow_BatchDatabase#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_batchdatabase/cs/dataflowbatchdatabase.cs#100)]
[!code-vb[TPLDataflow_BatchDatabase#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_batchdatabase/vb/dataflowbatchdatabase.vb#100)]

## <a name="see-also"></a><span data-ttu-id="b592b-163">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b592b-163">See also</span></span>

- [<span data-ttu-id="b592b-164">Veri akışı</span><span class="sxs-lookup"><span data-stu-id="b592b-164">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
