---
title: "F # kullanarak Azure Table storage'ı kullanmaya başlama"
description: Azure Table storage veya Azure Cosmos DB kullanarak bulutta yapılandırılmış veri depolayın.
keywords: 'Visual f #, f #, işlev, .NET, .NET Core, Azure programlama'
author: sylvanc
ms.author: phcart
ms.date: 03/26/2018
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 9e5d6cea-a98c-461e-a5cc-75f1d154eafd
ms.openlocfilehash: 6d40211e13e8d213aa5a40d585dd384abf49ddfa
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/28/2018
---
# <a name="get-started-with-azure-table-storage-and-the-azure-cosmos-db-table-api-using-f"></a><span data-ttu-id="1343d-104">Azure tablo depolaması ve F # kullanarak Azure Cosmos DB tablo API'sini kullanmaya başlama</span><span class="sxs-lookup"><span data-stu-id="1343d-104">Get started with Azure Table storage and the Azure Cosmos DB Table API using F#</span></span> # 

<span data-ttu-id="1343d-105">Azure Table storage bulutta yapılandırılmış NoSQL verileri depolayan bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="1343d-105">Azure Table storage is a service that stores structured NoSQL data in the cloud.</span></span> <span data-ttu-id="1343d-106">Table storage, şemasız tasarım ile bir anahtar/öznitelik deposudur.</span><span class="sxs-lookup"><span data-stu-id="1343d-106">Table storage is a key/attribute store with a schemaless design.</span></span> <span data-ttu-id="1343d-107">Table storage şemasız olduğu için uygulamanızın ihtiyaçları geliştikçe verilerinizi uyarlamak kolaydır.</span><span class="sxs-lookup"><span data-stu-id="1343d-107">Because Table storage is schemaless, it's easy to adapt your data as the needs of your application evolve.</span></span> <span data-ttu-id="1343d-108">Verilere erişim hızlı ve uygun maliyetli türlü uygulama için.</span><span class="sxs-lookup"><span data-stu-id="1343d-108">Access to data is fast and cost-effective for all kinds of applications.</span></span> <span data-ttu-id="1343d-109">Tablo depolama genellikle maliyetini önemli ölçüde benzer hacimdeki veriler için geleneksel SQL'e daha düşüktür.</span><span class="sxs-lookup"><span data-stu-id="1343d-109">Table storage is typically significantly lower in cost than traditional SQL for similar volumes of data.</span></span>

<span data-ttu-id="1343d-110">Table storage, web uygulamaları, adres defterleri, cihaz bilgilerini ve başka türde bir hizmetiniz için gerekli meta veriler için kullanıcı verileri gibi esnek veri kümelerini depolamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1343d-110">You can use Table storage to store flexible datasets, such as user data for web applications, address books, device information, and any other type of metadata that your service requires.</span></span> <span data-ttu-id="1343d-111">Bir tablodaki herhangi bir sayıda varlık depolayabilirsiniz ve bir depolama hesabı herhangi bir sayı depolama hesabının kapasite sınırını kadar tablo içerebilir.</span><span class="sxs-lookup"><span data-stu-id="1343d-111">You can store any number of entities in a table, and a storage account may contain any number of tables, up to the capacity limit of the storage account.</span></span>

<span data-ttu-id="1343d-112">Azure Cosmos DB Azure tablo depolaması için yazılmıştır ve premium özellikleri gibi gerektiren uygulamalar için tablo API sağlar:</span><span class="sxs-lookup"><span data-stu-id="1343d-112">Azure Cosmos DB provides the Table API for applications that are written for Azure Table storage and that require premium capabilities such as:</span></span>

- <span data-ttu-id="1343d-113">Anahtar teslimi genel dağıtım.</span><span class="sxs-lookup"><span data-stu-id="1343d-113">Turnkey global distribution.</span></span>
- <span data-ttu-id="1343d-114">Dünya çapında ayrılmış işleme.</span><span class="sxs-lookup"><span data-stu-id="1343d-114">Dedicated throughput worldwide.</span></span>
- <span data-ttu-id="1343d-115">Tek basamaklı milisaniyelik gecikme 99 adresindeki.</span><span class="sxs-lookup"><span data-stu-id="1343d-115">Single-digit millisecond latencies at the 99th percentile.</span></span>
- <span data-ttu-id="1343d-116">Yüksek oranda kullanılabilirlik garanti.</span><span class="sxs-lookup"><span data-stu-id="1343d-116">Guaranteed high availability.</span></span>
- <span data-ttu-id="1343d-117">Otomatik ikincil dizin.</span><span class="sxs-lookup"><span data-stu-id="1343d-117">Automatic secondary indexing.</span></span>

<span data-ttu-id="1343d-118">Azure tablo depolaması için yazılmış uygulamalar için hiçbir kod değişikliklerle tablo API kullanarak Azure Cosmos DB geçirmek ve premium özelliklerinden.</span><span class="sxs-lookup"><span data-stu-id="1343d-118">Applications written for Azure Table storage can migrate to Azure Cosmos DB by using the Table API with no code changes and take advantage of premium capabilities.</span></span> <span data-ttu-id="1343d-119">Tablo API, .NET, Java, Python ve Node.js için İstemci SDK kullanılabilir sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1343d-119">The Table API has client SDKs available for .NET, Java, Python, and Node.js.</span></span>

<span data-ttu-id="1343d-120">Daha fazla bilgi için bkz: [Azure Cosmos DB tablo API giriş](https://docs.microsoft.com/azure/cosmos-db/table-introduction).</span><span class="sxs-lookup"><span data-stu-id="1343d-120">For more information, see [Introduction to Azure Cosmos DB Table API](https://docs.microsoft.com/azure/cosmos-db/table-introduction).</span></span>

## <a name="about-this-tutorial"></a><span data-ttu-id="1343d-121">Bu öğretici hakkında</span><span class="sxs-lookup"><span data-stu-id="1343d-121">About this tutorial</span></span>

<span data-ttu-id="1343d-122">Bu öğretici, Azure Table storage veya Azure Cosmos DB tablo oluşturma ve bir tablo silme ve ekleme, güncelleştirme, silme ve tablo verileri Sorgulama dahil olmak üzere API'sini kullanarak bazı genel görevleri gerçekleştirmek için F # kodunun nasıl yazılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1343d-122">This tutorial shows how to write F# code to do some common tasks using Azure Table storage or the Azure Cosmos DB Table API, including creating and deleting a table and inserting, updating, deleting, and querying table data.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1343d-123">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="1343d-123">Prerequisites</span></span>

<span data-ttu-id="1343d-124">Bu kılavuzu kullanmak için öncelikle [bir Azure depolama hesabı oluşturma](/azure/storage/storage-create-storage-account) veya [Azure Cosmos DB hesap](https://azure.microsoft.com/try/cosmosdb/).</span><span class="sxs-lookup"><span data-stu-id="1343d-124">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account) or [Azure Cosmos DB account](https://azure.microsoft.com/try/cosmosdb/).</span></span>


## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="1343d-125">Bir F # betiği ve başlangıç F # Etkileşimli oluşturma</span><span class="sxs-lookup"><span data-stu-id="1343d-125">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="1343d-126">Bu makaledeki örnekler, F # uygulaması veya F # betiği kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1343d-126">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="1343d-127">F # betiği oluşturmak için dosya oluştur `.fsx` uzantısı, örneğin `tables.fsx`, ortamınızdaki F # geliştirme.</span><span class="sxs-lookup"><span data-stu-id="1343d-127">To create an F# script, create a file with the `.fsx` extension, for example `tables.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="1343d-128">Ardından, kullanın bir [Paket Yöneticisi](package-management.md) gibi [Paket](https://fsprojects.github.io/Paket/) veya [NuGet](https://www.nuget.org/) yüklemek için `WindowsAzure.Storage` paket ve başvuru `WindowsAzure.Storage.dll` bir kullanarakkomut`#r`yönergesi.</span><span class="sxs-lookup"><span data-stu-id="1343d-128">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span> <span data-ttu-id="1343d-129">Bunu yeniden `Microsoft.WindowsAzure.ConfigurationManager` Microsoft.Azure ad alanı alabilmek için.</span><span class="sxs-lookup"><span data-stu-id="1343d-129">Do it again for `Microsoft.WindowsAzure.ConfigurationManager` in order to get the Microsoft.Azure namespace.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="1343d-130">Ad alanı bildirimleri ekleme</span><span class="sxs-lookup"><span data-stu-id="1343d-130">Add namespace declarations</span></span>

<span data-ttu-id="1343d-131">Aşağıdakileri ekleyin `open` deyimleri üstüne `tables.fsx` dosyası:</span><span class="sxs-lookup"><span data-stu-id="1343d-131">Add the following `open` statements to the top of the `tables.fsx` file:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L1-L5)]

### <a name="get-your-azure-storage-connection-string"></a><span data-ttu-id="1343d-132">Azure depolama bağlantı dizenizi Al</span><span class="sxs-lookup"><span data-stu-id="1343d-132">Get your Azure Storage connection string</span></span>

<span data-ttu-id="1343d-133">Azure depolama tablo hizmetine bağlanıyorsanız, bağlantı dizenizi Bu öğretici için gerekir.</span><span class="sxs-lookup"><span data-stu-id="1343d-133">If you're connecting to Azure Storage Table service, you'll need your connection string for this tutorial.</span></span> <span data-ttu-id="1343d-134">Bağlantı dizenizi Azure portalından kopyalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1343d-134">You can copy your connection string from the Azure portal.</span></span> <span data-ttu-id="1343d-135">Bağlantı dizeleri hakkında daha fazla bilgi için bkz: [Storage bağlantı dizelerini yapılandırma](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="1343d-135">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

### <a name="get-your-azure-cosmos-db-connection-string"></a><span data-ttu-id="1343d-136">Azure Cosmos veritabanı bağlantı dizenizi Al</span><span class="sxs-lookup"><span data-stu-id="1343d-136">Get your Azure Cosmos DB connection string</span></span>

<span data-ttu-id="1343d-137">Azure Cosmos Veritabanına bağlanıyorsanız, bağlantı dizenizi Bu öğretici için gerekir.</span><span class="sxs-lookup"><span data-stu-id="1343d-137">If you're connecting to Azure Cosmos DB, you'll need your connection string for this tutorial.</span></span> <span data-ttu-id="1343d-138">Bağlantı dizenizi Azure portalından kopyalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1343d-138">You can copy your connection string from the Azure portal.</span></span> <span data-ttu-id="1343d-139">Azure portalında Cosmos DB hesabınıza gidin **ayarları** > **bağlantı dizesi**, tıklatıp **kopyalama** birincil bağlantınızı kopyalamak için düğmesi Dize.</span><span class="sxs-lookup"><span data-stu-id="1343d-139">In the Azure portal, in your Cosmos DB account, go to **Settings** > **Connection String**, and click the **Copy** button to copy your Primary Connection String.</span></span> 

<span data-ttu-id="1343d-140">Öğretici için aşağıdaki örneğe benzer betiğinizin bağlantı dizenizi girin:</span><span class="sxs-lookup"><span data-stu-id="1343d-140">For the tutorial, enter your connection string in your script, like the following example:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L11-L11)]

<span data-ttu-id="1343d-141">Ancak, bu olduğu **önerilmez** için gerçek projeleri.</span><span class="sxs-lookup"><span data-stu-id="1343d-141">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="1343d-142">Depolama hesabı anahtarınız depolama hesabınızın kök parolasına benzer.</span><span class="sxs-lookup"><span data-stu-id="1343d-142">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="1343d-143">Her zaman depolama hesabı anahtarınızı korumak dikkatli olun.</span><span class="sxs-lookup"><span data-stu-id="1343d-143">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="1343d-144">Sabit kodlama veya başkalarının erişebileceği düz metin dosyasına kaydetme diğer kullanıcılara dağıtmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="1343d-144">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="1343d-145">Bunu tehlikede olduğunu düşünüyorsanız, Azure Portalı'nı kullanarak anahtarınızı yeniden oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1343d-145">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="1343d-146">İçin gerçek uygulamalar, depolama bağlantı dizenizi korumak için en iyi yapılandırma dosyasında yoludur.</span><span class="sxs-lookup"><span data-stu-id="1343d-146">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="1343d-147">Yapılandırma dosyasından bağlantı dizesini almak için bunu yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1343d-147">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L13-L15)]

<span data-ttu-id="1343d-148">Azure Yapılandırma Yöneticisi'ni kullanarak isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="1343d-148">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="1343d-149">.NET Framework'ün gibi bir API de kullanabilirsiniz `ConfigurationManager` türü.</span><span class="sxs-lookup"><span data-stu-id="1343d-149">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="1343d-150">Bağlantı dizesini ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="1343d-150">Parse the connection string</span></span>

<span data-ttu-id="1343d-151">Bağlantı dizesini ayrıştırmak için kullanın:</span><span class="sxs-lookup"><span data-stu-id="1343d-151">To parse the connection string, use:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L21-L22)]

<span data-ttu-id="1343d-152">Bu döndürür bir `CloudStorageAccount`.</span><span class="sxs-lookup"><span data-stu-id="1343d-152">This returns a `CloudStorageAccount`.</span></span>

### <a name="create-the-table-service-client"></a><span data-ttu-id="1343d-153">Tablo hizmeti istemcisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="1343d-153">Create the Table service client</span></span>

<span data-ttu-id="1343d-154">`CloudTableClient` Sınıfı tabloları ve varlıkları tablo depolama almanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="1343d-154">The `CloudTableClient` class enables you to retrieve tables and entities in Table storage.</span></span> <span data-ttu-id="1343d-155">Hizmet istemcisini oluşturma yöntemlerinden biri aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="1343d-155">Here's one way to create the service client:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L28-L29)]

<span data-ttu-id="1343d-156">Şimdi veri okuyan ve tablo depolamaya veri yazan kodu yazmaya hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="1343d-156">Now you are ready to write code that reads data from and writes data to Table storage.</span></span>

### <a name="create-a-table"></a><span data-ttu-id="1343d-157">Bir tablo oluştur</span><span class="sxs-lookup"><span data-stu-id="1343d-157">Create a table</span></span>

<span data-ttu-id="1343d-158">Bu örnek, zaten yoksa, bir tablo oluşturulacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="1343d-158">This example shows how to create a table if it does not already exist:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L35-L39)]

### <a name="add-an-entity-to-a-table"></a><span data-ttu-id="1343d-159">Tabloya bir varlık ekleme</span><span class="sxs-lookup"><span data-stu-id="1343d-159">Add an entity to a table</span></span>

<span data-ttu-id="1343d-160">Öğesinden devralan bir türe sahip bir varlık sahip `TableEntity`.</span><span class="sxs-lookup"><span data-stu-id="1343d-160">An entity has to have a type that inherits from `TableEntity`.</span></span> <span data-ttu-id="1343d-161">Genişletebilirsiniz `TableEntity` istediğiniz gibi ancak türünüz *gerekir* bir parametresiz oluşturucuya sahip.</span><span class="sxs-lookup"><span data-stu-id="1343d-161">You can extend `TableEntity` in any way you like, but your type *must* have a parameter-less constructor.</span></span> <span data-ttu-id="1343d-162">Yalnızca hem de özellikleri `get` ve `set` Azure tablosunda depolanır.</span><span class="sxs-lookup"><span data-stu-id="1343d-162">Only properties that have both `get` and `set` are stored in your Azure Table.</span></span>

<span data-ttu-id="1343d-163">Bir varlığın bölüm ve sıra anahtarı varlığı tabloda benzersiz şekilde tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1343d-163">An entity's partition and row key uniquely identify the entity in the table.</span></span> <span data-ttu-id="1343d-164">Aynı bölüm anahtarına sahip varlıklar farklı bölüm anahtarlarının göre daha hızlı sorgulanabilir ancak farklı bölüm anahtarlarının kullanılması paralel işlemler daha fazla ölçeklenebilirlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="1343d-164">Entities with the same partition key can be queried faster than those with different partition keys, but using diverse partition keys allows for greater scalability of parallel operations.</span></span>

<span data-ttu-id="1343d-165">Bir örneği burada verilmiştir bir `Customer` kullanan `lastName` bölüm anahtarı olarak ve `firstName` satır anahtarı olarak.</span><span class="sxs-lookup"><span data-stu-id="1343d-165">Here's an example of a `Customer` that uses the `lastName` as the partition key and the `firstName` as the row key.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L45-L52)]

<span data-ttu-id="1343d-166">Şimdi ekleyin `Customer` tablosu.</span><span class="sxs-lookup"><span data-stu-id="1343d-166">Now add `Customer` to the table.</span></span> <span data-ttu-id="1343d-167">Bunu yapmak için oluşturun bir `TableOperation` tabloda yürütür.</span><span class="sxs-lookup"><span data-stu-id="1343d-167">To do so, create a `TableOperation` that executes on the table.</span></span> <span data-ttu-id="1343d-168">Bu durumda, oluşturduğunuz bir `Insert` işlemi.</span><span class="sxs-lookup"><span data-stu-id="1343d-168">In this case, you create an `Insert` operation.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L54-L55)]

### <a name="insert-a-batch-of-entities"></a><span data-ttu-id="1343d-169">Bir toplu işlem varlık yerleştirme</span><span class="sxs-lookup"><span data-stu-id="1343d-169">Insert a batch of entities</span></span>

<span data-ttu-id="1343d-170">Toplu işlem varlık bir tek bir yazma işlemini kullanarak bir tabloya ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1343d-170">You can insert a batch of entities into a table using a single write operation.</span></span> <span data-ttu-id="1343d-171">Toplu işlemleri, tek bir yürütme işlemlere birleştirmenize izin verir, ancak bazı sınırlamalar vardır:</span><span class="sxs-lookup"><span data-stu-id="1343d-171">Batch operations allow you to combine operations into a single execution, but they have some restrictions:</span></span>

- <span data-ttu-id="1343d-172">Güncelleştirmeleri gerçekleştirme siler ve aynı toplu işlemde ekler.</span><span class="sxs-lookup"><span data-stu-id="1343d-172">You can perform updates, deletes, and inserts in the same batch operation.</span></span>
- <span data-ttu-id="1343d-173">Toplu işlem en fazla 100 varlık içerebilir.</span><span class="sxs-lookup"><span data-stu-id="1343d-173">A batch operation can include up to 100 entities.</span></span>
- <span data-ttu-id="1343d-174">Bir toplu işlemde tüm varlıkların aynı bölüm anahtarına sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1343d-174">All entities in a batch operation must have the same partition key.</span></span>
- <span data-ttu-id="1343d-175">Bir toplu işlemde bir sorgu gerçekleştirmek mümkün olsa da, toplu işlemdeki tek işlem olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1343d-175">While it is possible to perform a query in a batch operation, it must be the only operation in the batch.</span></span>

<span data-ttu-id="1343d-176">Toplu işlem iki eklemeleri birleştirir biraz kod şöyledir:</span><span class="sxs-lookup"><span data-stu-id="1343d-176">Here's some code that combines two inserts into a batch operation:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L62-L71)]

### <a name="retrieve-all-entities-in-a-partition"></a><span data-ttu-id="1343d-177">Tüm varlıkları bir bölüme alma</span><span class="sxs-lookup"><span data-stu-id="1343d-177">Retrieve all entities in a partition</span></span>

<span data-ttu-id="1343d-178">Bir bölümdeki tüm varlıklar için bir tabloyu sorgulamak için kullanın bir `TableQuery` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="1343d-178">To query a table for all entities in a partition, use a `TableQuery` object.</span></span> <span data-ttu-id="1343d-179">Burada, "Smith" Bölüm anahtarı olduğu varlıklar için filtreleyin.</span><span class="sxs-lookup"><span data-stu-id="1343d-179">Here, you filter for entities where "Smith" is the partition key.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L77-L82)]

<span data-ttu-id="1343d-180">Artık sonuçlar yazdırma:</span><span class="sxs-lookup"><span data-stu-id="1343d-180">You now print the results:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L84-L85)]


### <a name="retrieve-a-range-of-entities-in-a-partition"></a><span data-ttu-id="1343d-181">Bir dizi varlıkları bir bölüme alma</span><span class="sxs-lookup"><span data-stu-id="1343d-181">Retrieve a range of entities in a partition</span></span>

<span data-ttu-id="1343d-182">Bir bölümdeki tüm varlıkları sorgulamak istemiyorsanız bölüm anahtarı Filtresi ile bir satır anahtarı filtresini birleştirerek bir aralık belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1343d-182">If you don't want to query all the entities in a partition, you can specify a range by combining the partition key filter with a row key filter.</span></span> <span data-ttu-id="1343d-183">Burada, iki filtre "Smith" bölümünde tüm varlıkları almak için burada satır anahtarı (ad) alfabede "M"'den önceki bir harfle başlayan kullanın.</span><span class="sxs-lookup"><span data-stu-id="1343d-183">Here, you use two filters to get all entities in the "Smith" partition where the row key (first name) starts with a letter earlier than "M" in the alphabet.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L91-L100)]

<span data-ttu-id="1343d-184">Artık sonuçlar yazdırma:</span><span class="sxs-lookup"><span data-stu-id="1343d-184">You now print the results:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L102-L103)]

### <a name="retrieve-a-single-entity"></a><span data-ttu-id="1343d-185">Tek bir varlık alma</span><span class="sxs-lookup"><span data-stu-id="1343d-185">Retrieve a single entity</span></span>

<span data-ttu-id="1343d-186">Tek, belirli bir varlığı almak üzere bir sorgu yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1343d-186">You can write a query to retrieve a single, specific entity.</span></span> <span data-ttu-id="1343d-187">Burada, kullandığınız bir `TableOperation` "Ben Smith" Müşteri belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="1343d-187">Here, you use a `TableOperation` to specify the customer "Ben Smith".</span></span> <span data-ttu-id="1343d-188">Bir koleksiyon yerine ulaşırsınız bir `Customer`.</span><span class="sxs-lookup"><span data-stu-id="1343d-188">Instead of a collection, you get back a `Customer`.</span></span> <span data-ttu-id="1343d-189">Bir sorguda hem Bölüm anahtarı hem de satır anahtarını belirtmek tablo hizmetinden tek bir varlık almak için en hızlı yoludur.</span><span class="sxs-lookup"><span data-stu-id="1343d-189">Specifying both the partition key and the row key in a query is the fastest way to retrieve a single entity from the Table service.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L109-L111)]

<span data-ttu-id="1343d-190">Artık sonuçlar yazdırma:</span><span class="sxs-lookup"><span data-stu-id="1343d-190">You now print the results:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L113-L115)]


### <a name="replace-an-entity"></a><span data-ttu-id="1343d-191">Bir varlığı değiştirme</span><span class="sxs-lookup"><span data-stu-id="1343d-191">Replace an entity</span></span>

<span data-ttu-id="1343d-192">Bir varlığı güncelleştirmek için tablo hizmetinden alın, varlık nesnesini değiştirin ve sonra geri tablo hizmeti kullanmaya değişiklikleri kaydetmek bir `Replace` işlemi.</span><span class="sxs-lookup"><span data-stu-id="1343d-192">To update an entity, retrieve it from the Table service, modify the entity object, and then save the changes back to the Table service using a `Replace` operation.</span></span> <span data-ttu-id="1343d-193">Bu, bu durumda işlem başarısız alındığından beri sunucunun varlıkta değiştirilmediği sürece bu sunucu üzerinde tamamen değiştirilmesini varlık neden olur.</span><span class="sxs-lookup"><span data-stu-id="1343d-193">This causes the entity to be fully replaced on the server, unless the entity on the server has changed since it was retrieved, in which case the operation fails.</span></span> <span data-ttu-id="1343d-194">Bu hata uygulamanızı değişiklikler diğer kaynaklardan yanlışlıkla üzerine yazılmasını önlemektir.</span><span class="sxs-lookup"><span data-stu-id="1343d-194">This failure is to prevent your application from inadvertently overwriting changes from other sources.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L121-L128)]

### <a name="insert-or-replace-an-entity"></a><span data-ttu-id="1343d-195">Ekleme veya değiştirme bir varlık</span><span class="sxs-lookup"><span data-stu-id="1343d-195">Insert-or-replace an entity</span></span>

<span data-ttu-id="1343d-196">Bazı durumlarda, bir varlık tablosunda var olup olmadığını bilemeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1343d-196">Sometimes, you don't know whether an entity exists in the table.</span></span> <span data-ttu-id="1343d-197">Ve içinde saklı geçerli değerlerin bulursa, artık gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="1343d-197">And if it does, the current values stored in it are no longer needed.</span></span> <span data-ttu-id="1343d-198">Kullanabileceğiniz `InsertOrReplace` varlığı oluşturun veya, durumuna bakılmaksızın varsa değiştirin.</span><span class="sxs-lookup"><span data-stu-id="1343d-198">You can use `InsertOrReplace` to create the entity, or replace it if it exists, regardless of its state.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L134-L141)]

### <a name="query-a-subset-of-entity-properties"></a><span data-ttu-id="1343d-199">Varlık özelliklerinin bir alt sorgu</span><span class="sxs-lookup"><span data-stu-id="1343d-199">Query a subset of entity properties</span></span>

<span data-ttu-id="1343d-200">Tablo sorgusu, bunların tümü yerine bir varlıktaki birkaç özelliği alabilir.</span><span class="sxs-lookup"><span data-stu-id="1343d-200">A table query can retrieve just a few properties from an entity instead of all of them.</span></span> <span data-ttu-id="1343d-201">Projeksiyon, olarak adlandırılan bu teknik özellikle büyük varlıklar için sorgu performansını iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="1343d-201">This technique, called projection, can improve query performance, especially for large entities.</span></span> <span data-ttu-id="1343d-202">Burada, yalnızca e-posta adresleri kullanarak dönmek `DynamicTableEntity` ve `EntityResolver`.</span><span class="sxs-lookup"><span data-stu-id="1343d-202">Here, you return only email addresses using `DynamicTableEntity` and `EntityResolver`.</span></span> <span data-ttu-id="1343d-203">Bu kod yalnızca tablo hizmetinde bir hesap kullanırken çalıştırılır şekilde projeksiyon yerel depolama öykünücüsünde desteklenmez unutmayın.</span><span class="sxs-lookup"><span data-stu-id="1343d-203">Note that projection is not supported on the local storage emulator, so this code runs only when you're using an account on the Table service.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L147-L158)]

### <a name="retrieve-entities-in-pages-asynchronously"></a><span data-ttu-id="1343d-204">Varlıkları sayfalarda zaman uyumsuz olarak Al</span><span class="sxs-lookup"><span data-stu-id="1343d-204">Retrieve entities in pages asynchronously</span></span>

<span data-ttu-id="1343d-205">Çok sayıda varlık okuyorsanız ve bunları alındıktan gibi yerine tümünü döndürmek beklenirken işlem yapmak istediğiniz, bölümlendirilmiş bir sorgu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1343d-205">If you are reading a large number of entities, and you want to process them as they are retrieved rather than waiting for them all to return, you can use a segmented query.</span></span> <span data-ttu-id="1343d-206">Burada, büyük bir döndürmek için sonuç kümesi için beklerken çalıştırmanın engellenmemesi bir zaman uyumsuz iş akışı kullanarak sayfalarında sonuçları döndürür.</span><span class="sxs-lookup"><span data-stu-id="1343d-206">Here, you return results in pages by using an async workflow so that execution is not blocked while you're waiting for a large set of results to return.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L163-L178)]

<span data-ttu-id="1343d-207">Artık bu hesaplama zaman uyumlu olarak yürütün:</span><span class="sxs-lookup"><span data-stu-id="1343d-207">You now execute this computation synchronously:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L180-L180)]

### <a name="delete-an-entity"></a><span data-ttu-id="1343d-208">Bir varlığı silme</span><span class="sxs-lookup"><span data-stu-id="1343d-208">Delete an entity</span></span>

<span data-ttu-id="1343d-209">Bunu aldıktan sonra bir varlık silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1343d-209">You can delete an entity after you have retrieved it.</span></span> <span data-ttu-id="1343d-210">Siz aldıktan sonra varlık değiştirilmiş güncelleştirmeyle bir varlık gibi bu başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="1343d-210">As with updating an entity, this fails if the entity has changed since you retrieved it.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L186-L187)]

### <a name="delete-a-table"></a><span data-ttu-id="1343d-211">Tablo silme</span><span class="sxs-lookup"><span data-stu-id="1343d-211">Delete a table</span></span>

<span data-ttu-id="1343d-212">Bir depolama hesabından bir tablo silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1343d-212">You can delete a table from a storage account.</span></span> <span data-ttu-id="1343d-213">Silinmiş bir tablo silme işlemi şu süre boyunca yeniden oluşturma kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="1343d-213">A table that has been deleted will be unavailable to be re-created for a period of time following the deletion.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L193-L193)]

## <a name="next-steps"></a><span data-ttu-id="1343d-214">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="1343d-214">Next steps</span></span>

<span data-ttu-id="1343d-215">Table Storage öğrendiğinize göre daha karmaşık depolama görevleri ve Azure Cosmos DB tablo API hakkında bilgi edinmek için aşağıdaki bağlantıları izleyin.</span><span class="sxs-lookup"><span data-stu-id="1343d-215">Now that you've learned the basics of Table storage, follow these links to learn about more complex storage tasks and the Azure Cosmos DB Table API.</span></span>

- [<span data-ttu-id="1343d-216">Azure Cosmos DB tablo API giriş</span><span class="sxs-lookup"><span data-stu-id="1343d-216">Introduction to Azure Cosmos DB Table API</span></span>](https://docs.microsoft.com/azure/cosmos-db/table-introduction)
- [<span data-ttu-id="1343d-217">.NET başvurusu için depolama istemci kitaplığı</span><span class="sxs-lookup"><span data-stu-id="1343d-217">Storage Client Library for .NET reference</span></span>](https://docs.microsoft.com/dotnet/api/overview/azure/storage?view=azure-dotnet)
- [<span data-ttu-id="1343d-218">Azure depolama türü sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="1343d-218">Azure Storage Type Provider</span></span>](http://fsprojects.github.io/AzureStorageTypeProvider/)
- [<span data-ttu-id="1343d-219">Azure depolama ekibi blogu</span><span class="sxs-lookup"><span data-stu-id="1343d-219">Azure Storage Team Blog</span></span>](http://blogs.msdn.com/b/windowsazurestorage/)
- [<span data-ttu-id="1343d-220">Bağlantı dizeleri yapılandırma</span><span class="sxs-lookup"><span data-stu-id="1343d-220">Configuring Connection Strings</span></span>](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="1343d-221">.NET içinde Azure tablo depolaması ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="1343d-221">Getting Started with Azure Table Storage in .NET</span></span>](https://azure.microsoft.com/resources/samples/storage-table-dotnet-getting-started/)
