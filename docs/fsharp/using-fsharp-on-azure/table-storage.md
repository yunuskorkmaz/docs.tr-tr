---
title: "F # kullanarak Azure Table storage'ı kullanmaya başlama"
description: Azure Table storage veya Azure Cosmos DB kullanarak bulutta yapılandırılmış veri depolayın.
author: sylvanc
ms.date: 03/26/2018
ms.openlocfilehash: ac81bc88db1436aa4d5f576da61a90839df04b99
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33575407"
---
# <a name="get-started-with-azure-table-storage-and-the-azure-cosmos-db-table-api-using-f"></a><span data-ttu-id="f8f72-103">Azure tablo depolaması ve F # kullanarak Azure Cosmos DB tablo API'sini kullanmaya başlama</span><span class="sxs-lookup"><span data-stu-id="f8f72-103">Get started with Azure Table storage and the Azure Cosmos DB Table API using F#</span></span> # 

<span data-ttu-id="f8f72-104">Azure Table storage bulutta yapılandırılmış NoSQL verileri depolayan bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="f8f72-104">Azure Table storage is a service that stores structured NoSQL data in the cloud.</span></span> <span data-ttu-id="f8f72-105">Table storage, şemasız tasarım ile bir anahtar/öznitelik deposudur.</span><span class="sxs-lookup"><span data-stu-id="f8f72-105">Table storage is a key/attribute store with a schemaless design.</span></span> <span data-ttu-id="f8f72-106">Table storage şemasız olduğu için uygulamanızın ihtiyaçları geliştikçe verilerinizi uyarlamak kolaydır.</span><span class="sxs-lookup"><span data-stu-id="f8f72-106">Because Table storage is schemaless, it's easy to adapt your data as the needs of your application evolve.</span></span> <span data-ttu-id="f8f72-107">Verilere erişim hızlı ve uygun maliyetli türlü uygulama için.</span><span class="sxs-lookup"><span data-stu-id="f8f72-107">Access to data is fast and cost-effective for all kinds of applications.</span></span> <span data-ttu-id="f8f72-108">Tablo depolama genellikle maliyetini önemli ölçüde benzer hacimdeki veriler için geleneksel SQL'e daha düşüktür.</span><span class="sxs-lookup"><span data-stu-id="f8f72-108">Table storage is typically significantly lower in cost than traditional SQL for similar volumes of data.</span></span>

<span data-ttu-id="f8f72-109">Table storage, web uygulamaları, adres defterleri, cihaz bilgilerini ve başka türde bir hizmetiniz için gerekli meta veriler için kullanıcı verileri gibi esnek veri kümelerini depolamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8f72-109">You can use Table storage to store flexible datasets, such as user data for web applications, address books, device information, and any other type of metadata that your service requires.</span></span> <span data-ttu-id="f8f72-110">Bir tablodaki herhangi bir sayıda varlık depolayabilirsiniz ve bir depolama hesabı herhangi bir sayı depolama hesabının kapasite sınırını kadar tablo içerebilir.</span><span class="sxs-lookup"><span data-stu-id="f8f72-110">You can store any number of entities in a table, and a storage account may contain any number of tables, up to the capacity limit of the storage account.</span></span>

<span data-ttu-id="f8f72-111">Azure Cosmos DB Azure tablo depolaması için yazılmıştır ve premium özellikleri gibi gerektiren uygulamalar için tablo API sağlar:</span><span class="sxs-lookup"><span data-stu-id="f8f72-111">Azure Cosmos DB provides the Table API for applications that are written for Azure Table storage and that require premium capabilities such as:</span></span>

- <span data-ttu-id="f8f72-112">Anahtar teslimi genel dağıtım.</span><span class="sxs-lookup"><span data-stu-id="f8f72-112">Turnkey global distribution.</span></span>
- <span data-ttu-id="f8f72-113">Dünya çapında ayrılmış işleme.</span><span class="sxs-lookup"><span data-stu-id="f8f72-113">Dedicated throughput worldwide.</span></span>
- <span data-ttu-id="f8f72-114">Tek basamaklı milisaniyelik gecikme 99 adresindeki.</span><span class="sxs-lookup"><span data-stu-id="f8f72-114">Single-digit millisecond latencies at the 99th percentile.</span></span>
- <span data-ttu-id="f8f72-115">Yüksek oranda kullanılabilirlik garanti.</span><span class="sxs-lookup"><span data-stu-id="f8f72-115">Guaranteed high availability.</span></span>
- <span data-ttu-id="f8f72-116">Otomatik ikincil dizin.</span><span class="sxs-lookup"><span data-stu-id="f8f72-116">Automatic secondary indexing.</span></span>

<span data-ttu-id="f8f72-117">Azure tablo depolaması için yazılmış uygulamalar için hiçbir kod değişikliklerle tablo API kullanarak Azure Cosmos DB geçirmek ve premium özelliklerinden.</span><span class="sxs-lookup"><span data-stu-id="f8f72-117">Applications written for Azure Table storage can migrate to Azure Cosmos DB by using the Table API with no code changes and take advantage of premium capabilities.</span></span> <span data-ttu-id="f8f72-118">Tablo API, .NET, Java, Python ve Node.js için İstemci SDK kullanılabilir sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f8f72-118">The Table API has client SDKs available for .NET, Java, Python, and Node.js.</span></span>

<span data-ttu-id="f8f72-119">Daha fazla bilgi için bkz: [Azure Cosmos DB tablo API giriş](https://docs.microsoft.com/azure/cosmos-db/table-introduction).</span><span class="sxs-lookup"><span data-stu-id="f8f72-119">For more information, see [Introduction to Azure Cosmos DB Table API](https://docs.microsoft.com/azure/cosmos-db/table-introduction).</span></span>

## <a name="about-this-tutorial"></a><span data-ttu-id="f8f72-120">Bu öğretici hakkında</span><span class="sxs-lookup"><span data-stu-id="f8f72-120">About this tutorial</span></span>

<span data-ttu-id="f8f72-121">Bu öğretici, Azure Table storage veya Azure Cosmos DB tablo oluşturma ve bir tablo silme ve ekleme, güncelleştirme, silme ve tablo verileri Sorgulama dahil olmak üzere API'sini kullanarak bazı genel görevleri gerçekleştirmek için F # kodunun nasıl yazılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f8f72-121">This tutorial shows how to write F# code to do some common tasks using Azure Table storage or the Azure Cosmos DB Table API, including creating and deleting a table and inserting, updating, deleting, and querying table data.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f8f72-122">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="f8f72-122">Prerequisites</span></span>

<span data-ttu-id="f8f72-123">Bu kılavuzu kullanmak için öncelikle [bir Azure depolama hesabı oluşturma](/azure/storage/storage-create-storage-account) veya [Azure Cosmos DB hesap](https://azure.microsoft.com/try/cosmosdb/).</span><span class="sxs-lookup"><span data-stu-id="f8f72-123">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account) or [Azure Cosmos DB account](https://azure.microsoft.com/try/cosmosdb/).</span></span>


## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="f8f72-124">Bir F # betiği ve başlangıç F # Etkileşimli oluşturma</span><span class="sxs-lookup"><span data-stu-id="f8f72-124">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="f8f72-125">Bu makaledeki örnekler, F # uygulaması veya F # betiği kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f8f72-125">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="f8f72-126">F # betiği oluşturmak için dosya oluştur `.fsx` uzantısı, örneğin `tables.fsx`, ortamınızdaki F # geliştirme.</span><span class="sxs-lookup"><span data-stu-id="f8f72-126">To create an F# script, create a file with the `.fsx` extension, for example `tables.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="f8f72-127">Ardından, kullanın bir [Paket Yöneticisi](package-management.md) gibi [Paket](https://fsprojects.github.io/Paket/) veya [NuGet](https://www.nuget.org/) yüklemek için `WindowsAzure.Storage` paket ve başvuru `WindowsAzure.Storage.dll` bir kullanarakkomut`#r`yönergesi.</span><span class="sxs-lookup"><span data-stu-id="f8f72-127">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span> <span data-ttu-id="f8f72-128">Bunu yeniden `Microsoft.WindowsAzure.ConfigurationManager` Microsoft.Azure ad alanı alabilmek için.</span><span class="sxs-lookup"><span data-stu-id="f8f72-128">Do it again for `Microsoft.WindowsAzure.ConfigurationManager` in order to get the Microsoft.Azure namespace.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="f8f72-129">Ad alanı bildirimleri ekleme</span><span class="sxs-lookup"><span data-stu-id="f8f72-129">Add namespace declarations</span></span>

<span data-ttu-id="f8f72-130">Aşağıdakileri ekleyin `open` deyimleri üstüne `tables.fsx` dosyası:</span><span class="sxs-lookup"><span data-stu-id="f8f72-130">Add the following `open` statements to the top of the `tables.fsx` file:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L1-L5)]

### <a name="get-your-azure-storage-connection-string"></a><span data-ttu-id="f8f72-131">Azure depolama bağlantı dizenizi Al</span><span class="sxs-lookup"><span data-stu-id="f8f72-131">Get your Azure Storage connection string</span></span>

<span data-ttu-id="f8f72-132">Azure depolama tablo hizmetine bağlanıyorsanız, bağlantı dizenizi Bu öğretici için gerekir.</span><span class="sxs-lookup"><span data-stu-id="f8f72-132">If you're connecting to Azure Storage Table service, you'll need your connection string for this tutorial.</span></span> <span data-ttu-id="f8f72-133">Bağlantı dizenizi Azure portalından kopyalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8f72-133">You can copy your connection string from the Azure portal.</span></span> <span data-ttu-id="f8f72-134">Bağlantı dizeleri hakkında daha fazla bilgi için bkz: [Storage bağlantı dizelerini yapılandırma](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="f8f72-134">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

### <a name="get-your-azure-cosmos-db-connection-string"></a><span data-ttu-id="f8f72-135">Azure Cosmos veritabanı bağlantı dizenizi Al</span><span class="sxs-lookup"><span data-stu-id="f8f72-135">Get your Azure Cosmos DB connection string</span></span>

<span data-ttu-id="f8f72-136">Azure Cosmos Veritabanına bağlanıyorsanız, bağlantı dizenizi Bu öğretici için gerekir.</span><span class="sxs-lookup"><span data-stu-id="f8f72-136">If you're connecting to Azure Cosmos DB, you'll need your connection string for this tutorial.</span></span> <span data-ttu-id="f8f72-137">Bağlantı dizenizi Azure portalından kopyalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8f72-137">You can copy your connection string from the Azure portal.</span></span> <span data-ttu-id="f8f72-138">Azure portalında Cosmos DB hesabınıza gidin **ayarları** > **bağlantı dizesi**, tıklatıp **kopyalama** birincil bağlantınızı kopyalamak için düğmesi Dize.</span><span class="sxs-lookup"><span data-stu-id="f8f72-138">In the Azure portal, in your Cosmos DB account, go to **Settings** > **Connection String**, and click the **Copy** button to copy your Primary Connection String.</span></span> 

<span data-ttu-id="f8f72-139">Öğretici için aşağıdaki örneğe benzer betiğinizin bağlantı dizenizi girin:</span><span class="sxs-lookup"><span data-stu-id="f8f72-139">For the tutorial, enter your connection string in your script, like the following example:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L11-L11)]

<span data-ttu-id="f8f72-140">Ancak, bu olduğu **önerilmez** için gerçek projeleri.</span><span class="sxs-lookup"><span data-stu-id="f8f72-140">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="f8f72-141">Depolama hesabı anahtarınız depolama hesabınızın kök parolasına benzer.</span><span class="sxs-lookup"><span data-stu-id="f8f72-141">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="f8f72-142">Her zaman depolama hesabı anahtarınızı korumak dikkatli olun.</span><span class="sxs-lookup"><span data-stu-id="f8f72-142">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="f8f72-143">Sabit kodlama veya başkalarının erişebileceği düz metin dosyasına kaydetme diğer kullanıcılara dağıtmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="f8f72-143">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="f8f72-144">Bunu tehlikede olduğunu düşünüyorsanız, Azure Portalı'nı kullanarak anahtarınızı yeniden oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8f72-144">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="f8f72-145">İçin gerçek uygulamalar, depolama bağlantı dizenizi korumak için en iyi yapılandırma dosyasında yoludur.</span><span class="sxs-lookup"><span data-stu-id="f8f72-145">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="f8f72-146">Yapılandırma dosyasından bağlantı dizesini almak için bunu yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f8f72-146">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L13-L15)]

<span data-ttu-id="f8f72-147">Azure Yapılandırma Yöneticisi'ni kullanarak isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="f8f72-147">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="f8f72-148">.NET Framework'ün gibi bir API de kullanabilirsiniz `ConfigurationManager` türü.</span><span class="sxs-lookup"><span data-stu-id="f8f72-148">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="f8f72-149">Bağlantı dizesini ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="f8f72-149">Parse the connection string</span></span>

<span data-ttu-id="f8f72-150">Bağlantı dizesini ayrıştırmak için kullanın:</span><span class="sxs-lookup"><span data-stu-id="f8f72-150">To parse the connection string, use:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L21-L22)]

<span data-ttu-id="f8f72-151">Bu döndürür bir `CloudStorageAccount`.</span><span class="sxs-lookup"><span data-stu-id="f8f72-151">This returns a `CloudStorageAccount`.</span></span>

### <a name="create-the-table-service-client"></a><span data-ttu-id="f8f72-152">Tablo hizmeti istemcisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="f8f72-152">Create the Table service client</span></span>

<span data-ttu-id="f8f72-153">`CloudTableClient` Sınıfı tabloları ve varlıkları tablo depolama almanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="f8f72-153">The `CloudTableClient` class enables you to retrieve tables and entities in Table storage.</span></span> <span data-ttu-id="f8f72-154">Hizmet istemcisini oluşturma yöntemlerinden biri aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="f8f72-154">Here's one way to create the service client:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L28-L29)]

<span data-ttu-id="f8f72-155">Şimdi veri okuyan ve tablo depolamaya veri yazan kodu yazmaya hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="f8f72-155">Now you are ready to write code that reads data from and writes data to Table storage.</span></span>

### <a name="create-a-table"></a><span data-ttu-id="f8f72-156">Bir tablo oluştur</span><span class="sxs-lookup"><span data-stu-id="f8f72-156">Create a table</span></span>

<span data-ttu-id="f8f72-157">Bu örnek, zaten yoksa, bir tablo oluşturulacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="f8f72-157">This example shows how to create a table if it does not already exist:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L35-L39)]

### <a name="add-an-entity-to-a-table"></a><span data-ttu-id="f8f72-158">Tabloya bir varlık ekleme</span><span class="sxs-lookup"><span data-stu-id="f8f72-158">Add an entity to a table</span></span>

<span data-ttu-id="f8f72-159">Öğesinden devralan bir türe sahip bir varlık sahip `TableEntity`.</span><span class="sxs-lookup"><span data-stu-id="f8f72-159">An entity has to have a type that inherits from `TableEntity`.</span></span> <span data-ttu-id="f8f72-160">Genişletebilirsiniz `TableEntity` istediğiniz gibi ancak türünüz *gerekir* bir parametresiz oluşturucuya sahip.</span><span class="sxs-lookup"><span data-stu-id="f8f72-160">You can extend `TableEntity` in any way you like, but your type *must* have a parameter-less constructor.</span></span> <span data-ttu-id="f8f72-161">Yalnızca hem de özellikleri `get` ve `set` Azure tablosunda depolanır.</span><span class="sxs-lookup"><span data-stu-id="f8f72-161">Only properties that have both `get` and `set` are stored in your Azure Table.</span></span>

<span data-ttu-id="f8f72-162">Bir varlığın bölüm ve sıra anahtarı varlığı tabloda benzersiz şekilde tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f8f72-162">An entity's partition and row key uniquely identify the entity in the table.</span></span> <span data-ttu-id="f8f72-163">Aynı bölüm anahtarına sahip varlıklar farklı bölüm anahtarlarının göre daha hızlı sorgulanabilir ancak farklı bölüm anahtarlarının kullanılması paralel işlemler daha fazla ölçeklenebilirlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="f8f72-163">Entities with the same partition key can be queried faster than those with different partition keys, but using diverse partition keys allows for greater scalability of parallel operations.</span></span>

<span data-ttu-id="f8f72-164">Bir örneği burada verilmiştir bir `Customer` kullanan `lastName` bölüm anahtarı olarak ve `firstName` satır anahtarı olarak.</span><span class="sxs-lookup"><span data-stu-id="f8f72-164">Here's an example of a `Customer` that uses the `lastName` as the partition key and the `firstName` as the row key.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L45-L52)]

<span data-ttu-id="f8f72-165">Şimdi ekleyin `Customer` tablosu.</span><span class="sxs-lookup"><span data-stu-id="f8f72-165">Now add `Customer` to the table.</span></span> <span data-ttu-id="f8f72-166">Bunu yapmak için oluşturun bir `TableOperation` tabloda yürütür.</span><span class="sxs-lookup"><span data-stu-id="f8f72-166">To do so, create a `TableOperation` that executes on the table.</span></span> <span data-ttu-id="f8f72-167">Bu durumda, oluşturduğunuz bir `Insert` işlemi.</span><span class="sxs-lookup"><span data-stu-id="f8f72-167">In this case, you create an `Insert` operation.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L54-L55)]

### <a name="insert-a-batch-of-entities"></a><span data-ttu-id="f8f72-168">Bir toplu işlem varlık yerleştirme</span><span class="sxs-lookup"><span data-stu-id="f8f72-168">Insert a batch of entities</span></span>

<span data-ttu-id="f8f72-169">Toplu işlem varlık bir tek bir yazma işlemini kullanarak bir tabloya ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8f72-169">You can insert a batch of entities into a table using a single write operation.</span></span> <span data-ttu-id="f8f72-170">Toplu işlemleri, tek bir yürütme işlemlere birleştirmenize izin verir, ancak bazı sınırlamalar vardır:</span><span class="sxs-lookup"><span data-stu-id="f8f72-170">Batch operations allow you to combine operations into a single execution, but they have some restrictions:</span></span>

- <span data-ttu-id="f8f72-171">Güncelleştirmeleri gerçekleştirme siler ve aynı toplu işlemde ekler.</span><span class="sxs-lookup"><span data-stu-id="f8f72-171">You can perform updates, deletes, and inserts in the same batch operation.</span></span>
- <span data-ttu-id="f8f72-172">Toplu işlem en fazla 100 varlık içerebilir.</span><span class="sxs-lookup"><span data-stu-id="f8f72-172">A batch operation can include up to 100 entities.</span></span>
- <span data-ttu-id="f8f72-173">Bir toplu işlemde tüm varlıkların aynı bölüm anahtarına sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f8f72-173">All entities in a batch operation must have the same partition key.</span></span>
- <span data-ttu-id="f8f72-174">Bir toplu işlemde bir sorgu gerçekleştirmek mümkün olsa da, toplu işlemdeki tek işlem olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f8f72-174">While it is possible to perform a query in a batch operation, it must be the only operation in the batch.</span></span>

<span data-ttu-id="f8f72-175">Toplu işlem iki eklemeleri birleştirir biraz kod şöyledir:</span><span class="sxs-lookup"><span data-stu-id="f8f72-175">Here's some code that combines two inserts into a batch operation:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L62-L71)]

### <a name="retrieve-all-entities-in-a-partition"></a><span data-ttu-id="f8f72-176">Tüm varlıkları bir bölüme alma</span><span class="sxs-lookup"><span data-stu-id="f8f72-176">Retrieve all entities in a partition</span></span>

<span data-ttu-id="f8f72-177">Bir bölümdeki tüm varlıklar için bir tabloyu sorgulamak için kullanın bir `TableQuery` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="f8f72-177">To query a table for all entities in a partition, use a `TableQuery` object.</span></span> <span data-ttu-id="f8f72-178">Burada, "Smith" Bölüm anahtarı olduğu varlıklar için filtreleyin.</span><span class="sxs-lookup"><span data-stu-id="f8f72-178">Here, you filter for entities where "Smith" is the partition key.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L77-L82)]

<span data-ttu-id="f8f72-179">Artık sonuçlar yazdırma:</span><span class="sxs-lookup"><span data-stu-id="f8f72-179">You now print the results:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L84-L85)]


### <a name="retrieve-a-range-of-entities-in-a-partition"></a><span data-ttu-id="f8f72-180">Bir dizi varlıkları bir bölüme alma</span><span class="sxs-lookup"><span data-stu-id="f8f72-180">Retrieve a range of entities in a partition</span></span>

<span data-ttu-id="f8f72-181">Bir bölümdeki tüm varlıkları sorgulamak istemiyorsanız bölüm anahtarı Filtresi ile bir satır anahtarı filtresini birleştirerek bir aralık belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8f72-181">If you don't want to query all the entities in a partition, you can specify a range by combining the partition key filter with a row key filter.</span></span> <span data-ttu-id="f8f72-182">Burada, iki filtre "Smith" bölümünde tüm varlıkları almak için burada satır anahtarı (ad) alfabede "M"'den önceki bir harfle başlayan kullanın.</span><span class="sxs-lookup"><span data-stu-id="f8f72-182">Here, you use two filters to get all entities in the "Smith" partition where the row key (first name) starts with a letter earlier than "M" in the alphabet.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L91-L100)]

<span data-ttu-id="f8f72-183">Artık sonuçlar yazdırma:</span><span class="sxs-lookup"><span data-stu-id="f8f72-183">You now print the results:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L102-L103)]

### <a name="retrieve-a-single-entity"></a><span data-ttu-id="f8f72-184">Tek bir varlık alma</span><span class="sxs-lookup"><span data-stu-id="f8f72-184">Retrieve a single entity</span></span>

<span data-ttu-id="f8f72-185">Tek, belirli bir varlığı almak üzere bir sorgu yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8f72-185">You can write a query to retrieve a single, specific entity.</span></span> <span data-ttu-id="f8f72-186">Burada, kullandığınız bir `TableOperation` "Ben Smith" Müşteri belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="f8f72-186">Here, you use a `TableOperation` to specify the customer "Ben Smith".</span></span> <span data-ttu-id="f8f72-187">Bir koleksiyon yerine ulaşırsınız bir `Customer`.</span><span class="sxs-lookup"><span data-stu-id="f8f72-187">Instead of a collection, you get back a `Customer`.</span></span> <span data-ttu-id="f8f72-188">Bir sorguda hem Bölüm anahtarı hem de satır anahtarını belirtmek tablo hizmetinden tek bir varlık almak için en hızlı yoludur.</span><span class="sxs-lookup"><span data-stu-id="f8f72-188">Specifying both the partition key and the row key in a query is the fastest way to retrieve a single entity from the Table service.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L109-L111)]

<span data-ttu-id="f8f72-189">Artık sonuçlar yazdırma:</span><span class="sxs-lookup"><span data-stu-id="f8f72-189">You now print the results:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L113-L115)]


### <a name="replace-an-entity"></a><span data-ttu-id="f8f72-190">Bir varlığı değiştirme</span><span class="sxs-lookup"><span data-stu-id="f8f72-190">Replace an entity</span></span>

<span data-ttu-id="f8f72-191">Bir varlığı güncelleştirmek için tablo hizmetinden alın, varlık nesnesini değiştirin ve sonra geri tablo hizmeti kullanmaya değişiklikleri kaydetmek bir `Replace` işlemi.</span><span class="sxs-lookup"><span data-stu-id="f8f72-191">To update an entity, retrieve it from the Table service, modify the entity object, and then save the changes back to the Table service using a `Replace` operation.</span></span> <span data-ttu-id="f8f72-192">Bu, bu durumda işlem başarısız alındığından beri sunucunun varlıkta değiştirilmediği sürece bu sunucu üzerinde tamamen değiştirilmesini varlık neden olur.</span><span class="sxs-lookup"><span data-stu-id="f8f72-192">This causes the entity to be fully replaced on the server, unless the entity on the server has changed since it was retrieved, in which case the operation fails.</span></span> <span data-ttu-id="f8f72-193">Bu hata uygulamanızı değişiklikler diğer kaynaklardan yanlışlıkla üzerine yazılmasını önlemektir.</span><span class="sxs-lookup"><span data-stu-id="f8f72-193">This failure is to prevent your application from inadvertently overwriting changes from other sources.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L121-L128)]

### <a name="insert-or-replace-an-entity"></a><span data-ttu-id="f8f72-194">Ekleme veya değiştirme bir varlık</span><span class="sxs-lookup"><span data-stu-id="f8f72-194">Insert-or-replace an entity</span></span>

<span data-ttu-id="f8f72-195">Bazı durumlarda, bir varlık tablosunda var olup olmadığını bilemeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8f72-195">Sometimes, you don't know whether an entity exists in the table.</span></span> <span data-ttu-id="f8f72-196">Ve içinde saklı geçerli değerlerin bulursa, artık gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="f8f72-196">And if it does, the current values stored in it are no longer needed.</span></span> <span data-ttu-id="f8f72-197">Kullanabileceğiniz `InsertOrReplace` varlığı oluşturun veya, durumuna bakılmaksızın varsa değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f8f72-197">You can use `InsertOrReplace` to create the entity, or replace it if it exists, regardless of its state.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L134-L141)]

### <a name="query-a-subset-of-entity-properties"></a><span data-ttu-id="f8f72-198">Varlık özelliklerinin bir alt sorgu</span><span class="sxs-lookup"><span data-stu-id="f8f72-198">Query a subset of entity properties</span></span>

<span data-ttu-id="f8f72-199">Tablo sorgusu, bunların tümü yerine bir varlıktaki birkaç özelliği alabilir.</span><span class="sxs-lookup"><span data-stu-id="f8f72-199">A table query can retrieve just a few properties from an entity instead of all of them.</span></span> <span data-ttu-id="f8f72-200">Projeksiyon, olarak adlandırılan bu teknik özellikle büyük varlıklar için sorgu performansını iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="f8f72-200">This technique, called projection, can improve query performance, especially for large entities.</span></span> <span data-ttu-id="f8f72-201">Burada, yalnızca e-posta adresleri kullanarak dönmek `DynamicTableEntity` ve `EntityResolver`.</span><span class="sxs-lookup"><span data-stu-id="f8f72-201">Here, you return only email addresses using `DynamicTableEntity` and `EntityResolver`.</span></span> <span data-ttu-id="f8f72-202">Bu kod yalnızca tablo hizmetinde bir hesap kullanırken çalıştırılır şekilde projeksiyon yerel depolama öykünücüsünde desteklenmez unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f8f72-202">Note that projection is not supported on the local storage emulator, so this code runs only when you're using an account on the Table service.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L147-L158)]

### <a name="retrieve-entities-in-pages-asynchronously"></a><span data-ttu-id="f8f72-203">Varlıkları sayfalarda zaman uyumsuz olarak Al</span><span class="sxs-lookup"><span data-stu-id="f8f72-203">Retrieve entities in pages asynchronously</span></span>

<span data-ttu-id="f8f72-204">Çok sayıda varlık okuyorsanız ve bunları alındıktan gibi yerine tümünü döndürmek beklenirken işlem yapmak istediğiniz, bölümlendirilmiş bir sorgu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8f72-204">If you are reading a large number of entities, and you want to process them as they are retrieved rather than waiting for them all to return, you can use a segmented query.</span></span> <span data-ttu-id="f8f72-205">Burada, büyük bir döndürmek için sonuç kümesi için beklerken çalıştırmanın engellenmemesi bir zaman uyumsuz iş akışı kullanarak sayfalarında sonuçları döndürür.</span><span class="sxs-lookup"><span data-stu-id="f8f72-205">Here, you return results in pages by using an async workflow so that execution is not blocked while you're waiting for a large set of results to return.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L163-L178)]

<span data-ttu-id="f8f72-206">Artık bu hesaplama zaman uyumlu olarak yürütün:</span><span class="sxs-lookup"><span data-stu-id="f8f72-206">You now execute this computation synchronously:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L180-L180)]

### <a name="delete-an-entity"></a><span data-ttu-id="f8f72-207">Bir varlığı silme</span><span class="sxs-lookup"><span data-stu-id="f8f72-207">Delete an entity</span></span>

<span data-ttu-id="f8f72-208">Bunu aldıktan sonra bir varlık silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8f72-208">You can delete an entity after you have retrieved it.</span></span> <span data-ttu-id="f8f72-209">Siz aldıktan sonra varlık değiştirilmiş güncelleştirmeyle bir varlık gibi bu başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="f8f72-209">As with updating an entity, this fails if the entity has changed since you retrieved it.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L186-L187)]

### <a name="delete-a-table"></a><span data-ttu-id="f8f72-210">Tablo silme</span><span class="sxs-lookup"><span data-stu-id="f8f72-210">Delete a table</span></span>

<span data-ttu-id="f8f72-211">Bir depolama hesabından bir tablo silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8f72-211">You can delete a table from a storage account.</span></span> <span data-ttu-id="f8f72-212">Silinmiş bir tablo silme işlemi şu süre boyunca yeniden oluşturma kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="f8f72-212">A table that has been deleted will be unavailable to be re-created for a period of time following the deletion.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L193-L193)]

## <a name="next-steps"></a><span data-ttu-id="f8f72-213">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="f8f72-213">Next steps</span></span>

<span data-ttu-id="f8f72-214">Table Storage öğrendiğinize göre daha karmaşık depolama görevleri ve Azure Cosmos DB tablo API hakkında bilgi edinmek için aşağıdaki bağlantıları izleyin.</span><span class="sxs-lookup"><span data-stu-id="f8f72-214">Now that you've learned the basics of Table storage, follow these links to learn about more complex storage tasks and the Azure Cosmos DB Table API.</span></span>

- [<span data-ttu-id="f8f72-215">Azure Cosmos DB tablo API giriş</span><span class="sxs-lookup"><span data-stu-id="f8f72-215">Introduction to Azure Cosmos DB Table API</span></span>](https://docs.microsoft.com/azure/cosmos-db/table-introduction)
- [<span data-ttu-id="f8f72-216">.NET başvurusu için depolama istemci kitaplığı</span><span class="sxs-lookup"><span data-stu-id="f8f72-216">Storage Client Library for .NET reference</span></span>](https://docs.microsoft.com/dotnet/api/overview/azure/storage?view=azure-dotnet)
- [<span data-ttu-id="f8f72-217">Azure depolama türü sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="f8f72-217">Azure Storage Type Provider</span></span>](http://fsprojects.github.io/AzureStorageTypeProvider/)
- [<span data-ttu-id="f8f72-218">Azure depolama ekibi blogu</span><span class="sxs-lookup"><span data-stu-id="f8f72-218">Azure Storage Team Blog</span></span>](http://blogs.msdn.com/b/windowsazurestorage/)
- [<span data-ttu-id="f8f72-219">Bağlantı dizeleri yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f8f72-219">Configuring Connection Strings</span></span>](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="f8f72-220">.NET içinde Azure tablo depolaması ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="f8f72-220">Getting Started with Azure Table Storage in .NET</span></span>](https://azure.microsoft.com/resources/samples/storage-table-dotnet-getting-started/)
