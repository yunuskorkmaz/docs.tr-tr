---
title: F# kullanarak Azure Tablo depolama kullanmaya başlama
description: Yapılandırılmış verileri Azure Tablo depolama veya Azure Cosmos DB kullanarak bulutta depolayın.
author: sylvanc
ms.date: 03/26/2018
ms.openlocfilehash: 30ffd5f099dbb8efbf57104a2ade6c26304b7cee
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395201"
---
# <a name="get-started-with-azure-table-storage-and-the-azure-cosmos-db-table-api-using-f"></a><span data-ttu-id="520a1-103">F @ no__t-0 kullanarak Azure Tablo depolama ve Azure Cosmos DB Tablo API'si kullanmaya başlama</span><span class="sxs-lookup"><span data-stu-id="520a1-103">Get started with Azure Table storage and the Azure Cosmos DB Table API using F\#</span></span>

<span data-ttu-id="520a1-104">Azure Tablo depolama, bulutta yapılandırılmış NoSQL verilerini depolayan bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="520a1-104">Azure Table storage is a service that stores structured NoSQL data in the cloud.</span></span> <span data-ttu-id="520a1-105">Tablo depolama, şesız bir tasarıma sahip bir anahtar/öznitelik deposudur.</span><span class="sxs-lookup"><span data-stu-id="520a1-105">Table storage is a key/attribute store with a schemaless design.</span></span> <span data-ttu-id="520a1-106">Tablo Depolaması şesız olduğundan, uygulamanızın ihtiyaçları geliştikçe verilerinizi kolayca uyarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="520a1-106">Because Table storage is schemaless, it's easy to adapt your data as the needs of your application evolve.</span></span> <span data-ttu-id="520a1-107">Verilere erişim, tüm uygulama türleri için hızlı ve uygun maliyetli bir hesaplıdır.</span><span class="sxs-lookup"><span data-stu-id="520a1-107">Access to data is fast and cost-effective for all kinds of applications.</span></span> <span data-ttu-id="520a1-108">Tablo depolaması, benzer veri birimleri için geleneksel SQL 'den büyük ölçüde düşük maliyetlidir.</span><span class="sxs-lookup"><span data-stu-id="520a1-108">Table storage is typically significantly lower in cost than traditional SQL for similar volumes of data.</span></span>

<span data-ttu-id="520a1-109">Web uygulamaları için Kullanıcı verileri, adres defterleri, cihaz bilgileri ve hizmetinizin gerektirdiği diğer meta veri türleri gibi esnek veri kümelerini depolamak için tablo depolama alanını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="520a1-109">You can use Table storage to store flexible datasets, such as user data for web applications, address books, device information, and any other type of metadata that your service requires.</span></span> <span data-ttu-id="520a1-110">Bir tabloda herhangi bir sayıda varlığı saklayabilirsiniz ve depolama hesabı, depolama hesabının kapasite sınırına kadar herhangi bir sayıda tablo içerebilir.</span><span class="sxs-lookup"><span data-stu-id="520a1-110">You can store any number of entities in a table, and a storage account may contain any number of tables, up to the capacity limit of the storage account.</span></span>

<span data-ttu-id="520a1-111">Azure Cosmos DB, Azure Tablo depolaması için yazılmış ve şu gibi Premium yetenekler gerektiren uygulamalar için Tablo API'si sağlar:</span><span class="sxs-lookup"><span data-stu-id="520a1-111">Azure Cosmos DB provides the Table API for applications that are written for Azure Table storage and that require premium capabilities such as:</span></span>

- <span data-ttu-id="520a1-112">Anahtar genel dağıtımı.</span><span class="sxs-lookup"><span data-stu-id="520a1-112">Turnkey global distribution.</span></span>
- <span data-ttu-id="520a1-113">Dünya çapındaki adanmış aktarım hızı.</span><span class="sxs-lookup"><span data-stu-id="520a1-113">Dedicated throughput worldwide.</span></span>
- <span data-ttu-id="520a1-114">99. yüzdede tek basamaklı milisaniyelik gecikme süresi.</span><span class="sxs-lookup"><span data-stu-id="520a1-114">Single-digit millisecond latencies at the 99th percentile.</span></span>
- <span data-ttu-id="520a1-115">Garantili yüksek kullanılabilirlik.</span><span class="sxs-lookup"><span data-stu-id="520a1-115">Guaranteed high availability.</span></span>
- <span data-ttu-id="520a1-116">Otomatik ikincil dizin oluşturma.</span><span class="sxs-lookup"><span data-stu-id="520a1-116">Automatic secondary indexing.</span></span>

<span data-ttu-id="520a1-117">Azure Tablo depolaması için yazılmış uygulamalar, kod değişikliği olmadan Tablo API'si kullanarak Azure Cosmos DB ve Premium özelliklerden yararlanabilir.</span><span class="sxs-lookup"><span data-stu-id="520a1-117">Applications written for Azure Table storage can migrate to Azure Cosmos DB by using the Table API with no code changes and take advantage of premium capabilities.</span></span> <span data-ttu-id="520a1-118">Tablo API'si .NET, Java, Python ve Node. js için kullanılabilir istemci SDK 'larına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="520a1-118">The Table API has client SDKs available for .NET, Java, Python, and Node.js.</span></span>

<span data-ttu-id="520a1-119">Daha fazla bilgi için bkz. [Azure Cosmos DB tablo API'si giriş](https://docs.microsoft.com/azure/cosmos-db/table-introduction).</span><span class="sxs-lookup"><span data-stu-id="520a1-119">For more information, see [Introduction to Azure Cosmos DB Table API](https://docs.microsoft.com/azure/cosmos-db/table-introduction).</span></span>

## <a name="about-this-tutorial"></a><span data-ttu-id="520a1-120">Bu öğretici hakkında</span><span class="sxs-lookup"><span data-stu-id="520a1-120">About this tutorial</span></span>

<span data-ttu-id="520a1-121">Bu öğreticide, tablo oluşturma F# ve silme ve tablo verileri ekleme, güncelleştirme, silme ve sorgulama dahil olmak üzere Azure Tablo depolamayı veya Azure Cosmos db tablo API'si kullanarak bazı yaygın görevleri yapmak için nasıl kod yazacağınız gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="520a1-121">This tutorial shows how to write F# code to do some common tasks using Azure Table storage or the Azure Cosmos DB Table API, including creating and deleting a table and inserting, updating, deleting, and querying table data.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="520a1-122">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="520a1-122">Prerequisites</span></span>

<span data-ttu-id="520a1-123">Bu kılavuzu kullanmak için, önce [bir Azure depolama hesabı](/azure/storage/storage-create-storage-account) veya [Azure Cosmos DB hesabı](https://azure.microsoft.com/try/cosmosdb/)oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="520a1-123">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account) or [Azure Cosmos DB account](https://azure.microsoft.com/try/cosmosdb/).</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="520a1-124">F# Betik oluşturma ve etkileşimli başlatma F#</span><span class="sxs-lookup"><span data-stu-id="520a1-124">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="520a1-125">Bu makaledeki örnekler, bir F# uygulama ya da bir F# komut dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="520a1-125">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="520a1-126">F# Betik oluşturmak için, F# geliştirme ortamınızda `.fsx` uzantılı bir dosya oluşturun (örneğin, `tables.fsx`).</span><span class="sxs-lookup"><span data-stu-id="520a1-126">To create an F# script, create a file with the `.fsx` extension, for example `tables.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="520a1-127">Ardından, bir `#r` yönergesini kullanarak `WindowsAzure.Storage` paketini ve betiğe `WindowsAzure.Storage.dll` ' ü yüklemek için, paket veya [NuGet](https://www.nuget.org/) [gibi bir](https://fsprojects.github.io/Paket/) [Paket Yöneticisi](package-management.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="520a1-127">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span> <span data-ttu-id="520a1-128">Microsoft. Azure ad alanını almak için `Microsoft.WindowsAzure.ConfigurationManager` için yeniden yapın.</span><span class="sxs-lookup"><span data-stu-id="520a1-128">Do it again for `Microsoft.WindowsAzure.ConfigurationManager` in order to get the Microsoft.Azure namespace.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="520a1-129">Ad alanı bildirimleri ekle</span><span class="sxs-lookup"><span data-stu-id="520a1-129">Add namespace declarations</span></span>

<span data-ttu-id="520a1-130">Aşağıdaki `open` deyimlerini `tables.fsx` dosyasının en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="520a1-130">Add the following `open` statements to the top of the `tables.fsx` file:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L1-L5)]

### <a name="get-your-azure-storage-connection-string"></a><span data-ttu-id="520a1-131">Azure depolama Bağlantı dizenizi alın</span><span class="sxs-lookup"><span data-stu-id="520a1-131">Get your Azure Storage connection string</span></span>

<span data-ttu-id="520a1-132">Azure Storage Table Service 'e bağlanıyorsanız, bu öğretici için bağlantı dizeniz olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="520a1-132">If you're connecting to Azure Storage Table service, you'll need your connection string for this tutorial.</span></span> <span data-ttu-id="520a1-133">Bağlantı dizenizi Azure portal kopyalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="520a1-133">You can copy your connection string from the Azure portal.</span></span> <span data-ttu-id="520a1-134">Bağlantı dizeleri hakkında daha fazla bilgi için bkz. [depolama bağlantı dizelerini yapılandırma](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="520a1-134">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

### <a name="get-your-azure-cosmos-db-connection-string"></a><span data-ttu-id="520a1-135">Azure Cosmos DB Bağlantı dizenizi alın</span><span class="sxs-lookup"><span data-stu-id="520a1-135">Get your Azure Cosmos DB connection string</span></span>

<span data-ttu-id="520a1-136">Azure Cosmos DB 'e bağlanıyorsanız, bu öğretici için bağlantı dizeniz olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="520a1-136">If you're connecting to Azure Cosmos DB, you'll need your connection string for this tutorial.</span></span> <span data-ttu-id="520a1-137">Bağlantı dizenizi Azure portal kopyalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="520a1-137">You can copy your connection string from the Azure portal.</span></span> <span data-ttu-id="520a1-138">Azure portal, Cosmos DB hesabınızda **ayarlar** > **bağlantı dizesi**' ne gidin ve **Kopyala** düğmesine tıklayarak birincil Bağlantı dizenizi kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="520a1-138">In the Azure portal, in your Cosmos DB account, go to **Settings** > **Connection String**, and click the **Copy** button to copy your Primary Connection String.</span></span> 

<span data-ttu-id="520a1-139">Öğreticide, aşağıdaki örnekte olduğu gibi betiğe Bağlantı dizenizi girin:</span><span class="sxs-lookup"><span data-stu-id="520a1-139">For the tutorial, enter your connection string in your script, like the following example:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L11-L11)]

<span data-ttu-id="520a1-140">Ancak, bu gerçek projeler için **önerilmez** .</span><span class="sxs-lookup"><span data-stu-id="520a1-140">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="520a1-141">Depolama hesabı anahtarınız, depolama hesabınızın kök parolasıyla benzerdir.</span><span class="sxs-lookup"><span data-stu-id="520a1-141">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="520a1-142">Depolama hesabı anahtarınızı korumak için her zaman dikkatli olun.</span><span class="sxs-lookup"><span data-stu-id="520a1-142">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="520a1-143">Diğer kullanıcılara dağıtmaktan, sabit kodlamasına veya başkalarının erişebileceği bir düz metin dosyasına kaydetmekten kaçının.</span><span class="sxs-lookup"><span data-stu-id="520a1-143">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="520a1-144">Güvenliğinin tehlikede olduğunu düşünüyorsanız, Azure portalını kullanarak anahtarınızı yeniden oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="520a1-144">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="520a1-145">Gerçek uygulamalar için, depolama Bağlantı dizenizi korumak için en iyi yol bir yapılandırma dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="520a1-145">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="520a1-146">Bağlantı dizesini bir yapılandırma dosyasından getirmek için şunu yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="520a1-146">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L13-L15)]

<span data-ttu-id="520a1-147">Azure Configuration Manager kullanmak isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="520a1-147">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="520a1-148">.NET Framework `ConfigurationManager` türü gibi bir API de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="520a1-148">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="520a1-149">Bağlantı dizesini Ayrıştır</span><span class="sxs-lookup"><span data-stu-id="520a1-149">Parse the connection string</span></span>

<span data-ttu-id="520a1-150">Bağlantı dizesini ayrıştırmak için şunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="520a1-150">To parse the connection string, use:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L21-L22)]

<span data-ttu-id="520a1-151">Bu `CloudStorageAccount` döndürür.</span><span class="sxs-lookup"><span data-stu-id="520a1-151">This returns a `CloudStorageAccount`.</span></span>

### <a name="create-the-table-service-client"></a><span data-ttu-id="520a1-152">Tablo hizmeti istemcisini oluşturma</span><span class="sxs-lookup"><span data-stu-id="520a1-152">Create the Table service client</span></span>

<span data-ttu-id="520a1-153">@No__t-0 sınıfı tablo depolamadaki tabloları ve varlıkları almanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="520a1-153">The `CloudTableClient` class enables you to retrieve tables and entities in Table storage.</span></span> <span data-ttu-id="520a1-154">Hizmet istemcisini oluşturmak için bir yol aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="520a1-154">Here's one way to create the service client:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L28-L29)]

<span data-ttu-id="520a1-155">Artık, verileri okuyan ve tablo depolamaya veri yazan kodu yazmaya hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="520a1-155">Now you are ready to write code that reads data from and writes data to Table storage.</span></span>

### <a name="create-a-table"></a><span data-ttu-id="520a1-156">Tablo oluşturma</span><span class="sxs-lookup"><span data-stu-id="520a1-156">Create a table</span></span>

<span data-ttu-id="520a1-157">Bu örnek, zaten yoksa tablo oluşturmayı gösterir:</span><span class="sxs-lookup"><span data-stu-id="520a1-157">This example shows how to create a table if it does not already exist:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L35-L39)]

### <a name="add-an-entity-to-a-table"></a><span data-ttu-id="520a1-158">Tabloya varlık ekleme</span><span class="sxs-lookup"><span data-stu-id="520a1-158">Add an entity to a table</span></span>

<span data-ttu-id="520a1-159">Bir varlık `TableEntity` ' dan devralan bir türe sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="520a1-159">An entity has to have a type that inherits from `TableEntity`.</span></span> <span data-ttu-id="520a1-160">@No__t-0 ' ı dilediğiniz şekilde genişletebilirsiniz, ancak türü parametre-daha az bir oluşturucuya sahip *olmalıdır* .</span><span class="sxs-lookup"><span data-stu-id="520a1-160">You can extend `TableEntity` in any way you like, but your type *must* have a parameter-less constructor.</span></span> <span data-ttu-id="520a1-161">Yalnızca `get` ve `set` olan özellikler Azure tablonuzda depolanır.</span><span class="sxs-lookup"><span data-stu-id="520a1-161">Only properties that have both `get` and `set` are stored in your Azure Table.</span></span>

<span data-ttu-id="520a1-162">Bir varlığın bölüm ve satır anahtarı, varlığı tabloda benzersiz şekilde tanımlar.</span><span class="sxs-lookup"><span data-stu-id="520a1-162">An entity's partition and row key uniquely identify the entity in the table.</span></span> <span data-ttu-id="520a1-163">Aynı bölüm anahtarına sahip varlıklar farklı bölüm anahtarlarıyla daha hızlı sorgulanabilir ancak farklı bölüm anahtarlarının kullanılması paralel işlemler için daha fazla ölçeklenebilirlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="520a1-163">Entities with the same partition key can be queried faster than those with different partition keys, but using diverse partition keys allows for greater scalability of parallel operations.</span></span>

<span data-ttu-id="520a1-164">Bölüm anahtarı olarak `lastName` ' i ve satır anahtarı olarak `firstName` ' i kullanan `Customer` ' a bir örnek aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="520a1-164">Here's an example of a `Customer` that uses the `lastName` as the partition key and the `firstName` as the row key.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L45-L52)]

<span data-ttu-id="520a1-165">Şimdi tabloya `Customer` ekleyin.</span><span class="sxs-lookup"><span data-stu-id="520a1-165">Now add `Customer` to the table.</span></span> <span data-ttu-id="520a1-166">Bunu yapmak için tabloda yürütülen bir `TableOperation` oluşturun.</span><span class="sxs-lookup"><span data-stu-id="520a1-166">To do so, create a `TableOperation` that executes on the table.</span></span> <span data-ttu-id="520a1-167">Bu durumda, `Insert` işlemi oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="520a1-167">In this case, you create an `Insert` operation.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L54-L55)]

### <a name="insert-a-batch-of-entities"></a><span data-ttu-id="520a1-168">Varlık toplu işi ekleme</span><span class="sxs-lookup"><span data-stu-id="520a1-168">Insert a batch of entities</span></span>

<span data-ttu-id="520a1-169">Tek bir yazma işlemi kullanarak bir tabloya bir varlık toplu işi ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="520a1-169">You can insert a batch of entities into a table using a single write operation.</span></span> <span data-ttu-id="520a1-170">Batch işlemleri, işlemleri tek bir yürütmeye birleştirmenizi sağlar, ancak bazı kısıtlamalar vardır:</span><span class="sxs-lookup"><span data-stu-id="520a1-170">Batch operations allow you to combine operations into a single execution, but they have some restrictions:</span></span>

- <span data-ttu-id="520a1-171">Aynı toplu işlemde güncelleştirme, silme ve ekleme işlemleri gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="520a1-171">You can perform updates, deletes, and inserts in the same batch operation.</span></span>
- <span data-ttu-id="520a1-172">Toplu işlem, en fazla 100 varlık içerebilir.</span><span class="sxs-lookup"><span data-stu-id="520a1-172">A batch operation can include up to 100 entities.</span></span>
- <span data-ttu-id="520a1-173">Bir toplu işlemdeki tüm varlıkların aynı bölüm anahtarı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="520a1-173">All entities in a batch operation must have the same partition key.</span></span>
- <span data-ttu-id="520a1-174">Toplu işlemde bir sorgu gerçekleştirmek mümkün olsa da, toplu işlemdeki tek işlem olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="520a1-174">While it is possible to perform a query in a batch operation, it must be the only operation in the batch.</span></span>

<span data-ttu-id="520a1-175">İşte bir toplu işlemin iki ekleme işlemini birleştiren kod:</span><span class="sxs-lookup"><span data-stu-id="520a1-175">Here's some code that combines two inserts into a batch operation:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L62-L71)]

### <a name="retrieve-all-entities-in-a-partition"></a><span data-ttu-id="520a1-176">Bir bölümdeki tüm varlıkları alma</span><span class="sxs-lookup"><span data-stu-id="520a1-176">Retrieve all entities in a partition</span></span>

<span data-ttu-id="520a1-177">Bir bölümdeki tüm varlıklar için bir tabloyu sorgulamak üzere `TableQuery` nesnesi kullanın.</span><span class="sxs-lookup"><span data-stu-id="520a1-177">To query a table for all entities in a partition, use a `TableQuery` object.</span></span> <span data-ttu-id="520a1-178">Burada, "Smith" bölümünün bölüm anahtarı olduğu varlıklar için filtre uygulayın.</span><span class="sxs-lookup"><span data-stu-id="520a1-178">Here, you filter for entities where "Smith" is the partition key.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L77-L82)]

<span data-ttu-id="520a1-179">Şimdi sonuçları yazdırmıyorsunuz:</span><span class="sxs-lookup"><span data-stu-id="520a1-179">You now print the results:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L84-L85)]

### <a name="retrieve-a-range-of-entities-in-a-partition"></a><span data-ttu-id="520a1-180">Bir bölümdeki varlık aralığını alma</span><span class="sxs-lookup"><span data-stu-id="520a1-180">Retrieve a range of entities in a partition</span></span>

<span data-ttu-id="520a1-181">Bir bölümdeki tüm varlıkları sorgulamak istemiyorsanız, bölüm anahtarı filtresini bir satır anahtar filtresiyle birleştirerek bir Aralık belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="520a1-181">If you don't want to query all the entities in a partition, you can specify a range by combining the partition key filter with a row key filter.</span></span> <span data-ttu-id="520a1-182">Burada, "Smith" bölümünde bulunan ve satır anahtarı (ad) alfabedeki "M" den önceki bir harfle başlayan tüm varlıkları almak için iki filtre kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="520a1-182">Here, you use two filters to get all entities in the "Smith" partition where the row key (first name) starts with a letter earlier than "M" in the alphabet.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L91-L100)]

<span data-ttu-id="520a1-183">Şimdi sonuçları yazdırmıyorsunuz:</span><span class="sxs-lookup"><span data-stu-id="520a1-183">You now print the results:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L102-L103)]

### <a name="retrieve-a-single-entity"></a><span data-ttu-id="520a1-184">Tek bir varlık alma</span><span class="sxs-lookup"><span data-stu-id="520a1-184">Retrieve a single entity</span></span>

<span data-ttu-id="520a1-185">Tek, belirli bir varlığı almak için bir sorgu yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="520a1-185">You can write a query to retrieve a single, specific entity.</span></span> <span data-ttu-id="520a1-186">Burada, "Ben Smith" müşterisini belirtmek için bir @no__t (0) kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="520a1-186">Here, you use a `TableOperation` to specify the customer "Ben Smith".</span></span> <span data-ttu-id="520a1-187">Bir koleksiyon yerine bir @no__t geri alırsınız.</span><span class="sxs-lookup"><span data-stu-id="520a1-187">Instead of a collection, you get back a `Customer`.</span></span> <span data-ttu-id="520a1-188">Bir sorgudaki bölüm anahtarını ve satır anahtarını belirtme, tablo hizmetinden tek bir varlık almanın en hızlı yoludur.</span><span class="sxs-lookup"><span data-stu-id="520a1-188">Specifying both the partition key and the row key in a query is the fastest way to retrieve a single entity from the Table service.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L109-L111)]

<span data-ttu-id="520a1-189">Şimdi sonuçları yazdırmıyorsunuz:</span><span class="sxs-lookup"><span data-stu-id="520a1-189">You now print the results:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L113-L115)]

### <a name="replace-an-entity"></a><span data-ttu-id="520a1-190">Bir varlığı değiştirme</span><span class="sxs-lookup"><span data-stu-id="520a1-190">Replace an entity</span></span>

<span data-ttu-id="520a1-191">Bir varlığı güncelleştirmek için tablo hizmetinden alın, varlık nesnesini değiştirin ve ardından `Replace` işlemi kullanarak değişiklikleri tablo hizmetine geri kaydedin.</span><span class="sxs-lookup"><span data-stu-id="520a1-191">To update an entity, retrieve it from the Table service, modify the entity object, and then save the changes back to the Table service using a `Replace` operation.</span></span> <span data-ttu-id="520a1-192">Bu, sunucudaki varlık alındıktan sonra değiştirilmemişse varlığın sunucu üzerinde tamamen değiştirilmesini sağlar, bu durumda işlem başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="520a1-192">This causes the entity to be fully replaced on the server, unless the entity on the server has changed since it was retrieved, in which case the operation fails.</span></span> <span data-ttu-id="520a1-193">Bu hata, uygulamanızın diğer kaynaklardaki değişikliklerin yanlışlıkla üzerine yazılmasını önlemektir.</span><span class="sxs-lookup"><span data-stu-id="520a1-193">This failure is to prevent your application from inadvertently overwriting changes from other sources.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L121-L128)]

### <a name="insert-or-replace-an-entity"></a><span data-ttu-id="520a1-194">Varlığı ekleme veya değiştirme</span><span class="sxs-lookup"><span data-stu-id="520a1-194">Insert-or-replace an entity</span></span>

<span data-ttu-id="520a1-195">Bazen, tabloda bir varlık olup olmadığını bilemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="520a1-195">Sometimes, you don't know whether an entity exists in the table.</span></span> <span data-ttu-id="520a1-196">Varsa, içinde depolanan geçerli değerlere artık gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="520a1-196">And if it does, the current values stored in it are no longer needed.</span></span> <span data-ttu-id="520a1-197">Varlığı oluşturmak için `InsertOrReplace` ' ı kullanabilir veya varsa, durumu ne olursa olsun değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="520a1-197">You can use `InsertOrReplace` to create the entity, or replace it if it exists, regardless of its state.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L134-L141)]

### <a name="query-a-subset-of-entity-properties"></a><span data-ttu-id="520a1-198">Varlık özelliklerinin bir alt kümesini sorgulama</span><span class="sxs-lookup"><span data-stu-id="520a1-198">Query a subset of entity properties</span></span>

<span data-ttu-id="520a1-199">Tablo sorgusu, her biri yerine bir varlıktan yalnızca birkaç özelliği alabilir.</span><span class="sxs-lookup"><span data-stu-id="520a1-199">A table query can retrieve just a few properties from an entity instead of all of them.</span></span> <span data-ttu-id="520a1-200">Projeksiyon olarak adlandırılan bu teknik, özellikle büyük varlıklar için sorgu performansını iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="520a1-200">This technique, called projection, can improve query performance, especially for large entities.</span></span> <span data-ttu-id="520a1-201">Burada yalnızca `DynamicTableEntity` ve `EntityResolver` ' i kullanarak e-posta adresleri döndürürler.</span><span class="sxs-lookup"><span data-stu-id="520a1-201">Here, you return only email addresses using `DynamicTableEntity` and `EntityResolver`.</span></span> <span data-ttu-id="520a1-202">Projeksiyon yerel depolama öykünücüsünde desteklenmediğini unutmayın, bu nedenle bu kod yalnızca tablo hizmetinde bir hesap kullandığınızda çalışır.</span><span class="sxs-lookup"><span data-stu-id="520a1-202">Note that projection is not supported on the local storage emulator, so this code runs only when you're using an account on the Table service.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L147-L158)]

### <a name="retrieve-entities-in-pages-asynchronously"></a><span data-ttu-id="520a1-203">Sayfalardaki varlıkları zaman uyumsuz olarak alma</span><span class="sxs-lookup"><span data-stu-id="520a1-203">Retrieve entities in pages asynchronously</span></span>

<span data-ttu-id="520a1-204">Çok sayıda varlığı okuyorsanız ve bunların tümünün dönmesini beklemek yerine alındığı gibi işlemek istiyorsanız, bölümlenmiş bir sorgu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="520a1-204">If you are reading a large number of entities, and you want to process them as they are retrieved rather than waiting for them all to return, you can use a segmented query.</span></span> <span data-ttu-id="520a1-205">Burada, büyük bir sonuç kümesinin döndürülmesini beklerken yürütmenin engellenmemesi için zaman uyumsuz iş akışı kullanarak sayfalardaki sonuçları döndürüyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="520a1-205">Here, you return results in pages by using an async workflow so that execution is not blocked while you're waiting for a large set of results to return.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L163-L178)]

<span data-ttu-id="520a1-206">Artık bu hesaplamayı zaman uyumlu olarak yürütütemezsiniz:</span><span class="sxs-lookup"><span data-stu-id="520a1-206">You now execute this computation synchronously:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L180-L180)]

### <a name="delete-an-entity"></a><span data-ttu-id="520a1-207">Bir varlığı silme</span><span class="sxs-lookup"><span data-stu-id="520a1-207">Delete an entity</span></span>

<span data-ttu-id="520a1-208">Bir varlığı aldıktan sonra silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="520a1-208">You can delete an entity after you have retrieved it.</span></span> <span data-ttu-id="520a1-209">Bir varlığı güncelleştirmede olduğu gibi, varlık onu aldıktan sonra değiştiyse bu başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="520a1-209">As with updating an entity, this fails if the entity has changed since you retrieved it.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L186-L187)]

### <a name="delete-a-table"></a><span data-ttu-id="520a1-210">Tablo silme</span><span class="sxs-lookup"><span data-stu-id="520a1-210">Delete a table</span></span>

<span data-ttu-id="520a1-211">Bir depolama hesabındaki bir tabloyu silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="520a1-211">You can delete a table from a storage account.</span></span> <span data-ttu-id="520a1-212">Silinen bir tablonun silinme sonrasında bir süre için yeniden oluşturulması kullanılamayacak.</span><span class="sxs-lookup"><span data-stu-id="520a1-212">A table that has been deleted will be unavailable to be re-created for a period of time following the deletion.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L193-L193)]

## <a name="next-steps"></a><span data-ttu-id="520a1-213">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="520a1-213">Next steps</span></span>

<span data-ttu-id="520a1-214">Artık tablo depolamanın temellerini öğrendiğinize göre, daha karmaşık depolama görevleri ve Azure Cosmos DB Tablo API'si hakkında bilgi edinmek için bu bağlantıları izleyin.</span><span class="sxs-lookup"><span data-stu-id="520a1-214">Now that you've learned the basics of Table storage, follow these links to learn about more complex storage tasks and the Azure Cosmos DB Table API.</span></span>

- [<span data-ttu-id="520a1-215">Azure Cosmos DB Tablo API'si giriş</span><span class="sxs-lookup"><span data-stu-id="520a1-215">Introduction to Azure Cosmos DB Table API</span></span>](https://docs.microsoft.com/azure/cosmos-db/table-introduction)
- [<span data-ttu-id="520a1-216">.NET için depolama Istemci kitaplığı başvurusu</span><span class="sxs-lookup"><span data-stu-id="520a1-216">Storage Client Library for .NET reference</span></span>](https://docs.microsoft.com/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="520a1-217">Azure depolama türü sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="520a1-217">Azure Storage Type Provider</span></span>](https://fsprojects.github.io/AzureStorageTypeProvider/)
- [<span data-ttu-id="520a1-218">Azure depolama ekibi blogu</span><span class="sxs-lookup"><span data-stu-id="520a1-218">Azure Storage Team Blog</span></span>](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [<span data-ttu-id="520a1-219">Bağlantı dizelerini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="520a1-219">Configuring Connection Strings</span></span>](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string)
