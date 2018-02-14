---
title: "F # kullanarak Azure Table storage'ı kullanmaya başlama"
description: "Bir NoSQL veri deposu olan Azure Table storage kullanarak bulutta yapılandırılmış veri depolayın."
keywords: "Visual f #, f #, işlev, .NET, .NET Core, Azure programlama"
author: sylvanc
ms.author: phcart
ms.date: 09/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 9e5d6cea-a98c-461e-a5cc-75f1d154eafd
ms.openlocfilehash: e003f537c6f0f85b3b0ba932655ae2a54c980bc5
ms.sourcegitcommit: e2bf8e6bc365bd9a0e86fe81eeae7d14f85f48c1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/13/2018
---
# <a name="get-started-with-azure-table-storage-using-f"></a><span data-ttu-id="36573-104">F # kullanarak Azure Table storage'ı kullanmaya başlama</span><span class="sxs-lookup"><span data-stu-id="36573-104">Get started with Azure Table storage using F#</span></span> #

<span data-ttu-id="36573-105">Azure Table storage bulutta yapılandırılmış NoSQL verileri depolayan bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="36573-105">Azure Table storage is a service that stores structured NoSQL data in the cloud.</span></span> <span data-ttu-id="36573-106">Table storage, şemasız tasarım ile bir anahtar/öznitelik deposudur.</span><span class="sxs-lookup"><span data-stu-id="36573-106">Table storage is a key/attribute store with a schemaless design.</span></span> <span data-ttu-id="36573-107">Table storage şemasız olduğu için uygulamanızın ihtiyaçları geliştikçe verilerinizi uyarlamak kolaydır.</span><span class="sxs-lookup"><span data-stu-id="36573-107">Because Table storage is schemaless, it's easy to adapt your data as the needs of your application evolve.</span></span> <span data-ttu-id="36573-108">Verilere erişim hızlı ve uygun maliyetli türlü uygulama için.</span><span class="sxs-lookup"><span data-stu-id="36573-108">Access to data is fast and cost-effective for all kinds of applications.</span></span> <span data-ttu-id="36573-109">Tablo depolama genellikle maliyetini önemli ölçüde benzer hacimdeki veriler için geleneksel SQL'e daha düşüktür.</span><span class="sxs-lookup"><span data-stu-id="36573-109">Table storage is typically significantly lower in cost than traditional SQL for similar volumes of data.</span></span>

<span data-ttu-id="36573-110">Table storage, web uygulamaları, adres defterleri, cihaz bilgilerini ve başka türde bir hizmetiniz için gerekli meta veriler için kullanıcı verileri gibi esnek veri kümelerini depolamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36573-110">You can use Table storage to store flexible datasets, such as user data for web applications, address books, device information, and any other type of metadata that your service requires.</span></span> <span data-ttu-id="36573-111">Bir tablodaki herhangi bir sayıda varlık depolayabilirsiniz ve bir depolama hesabı herhangi bir sayı depolama hesabının kapasite sınırını kadar tablo içerebilir.</span><span class="sxs-lookup"><span data-stu-id="36573-111">You can store any number of entities in a table, and a storage account may contain any number of tables, up to the capacity limit of the storage account.</span></span>

### <a name="about-this-tutorial"></a><span data-ttu-id="36573-112">Bu öğretici hakkında</span><span class="sxs-lookup"><span data-stu-id="36573-112">About this tutorial</span></span>

<span data-ttu-id="36573-113">Bu öğretici oluşturma ve bir tablo silme ve ekleme, güncelleştirme, silme ve tablo verileri Sorgulama dahil olmak üzere Azure Table storage kullanarak bazı genel görevleri gerçekleştirmek için F # kodunun nasıl yazılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="36573-113">This tutorial shows how to write F# code to do some common tasks using Azure Table storage, including creating and deleting a table and inserting, updating, deleting, and querying table data.</span></span>

<span data-ttu-id="36573-114">Tablo depolama kavramsal bir genel bakış için lütfen bakın [tablo depolaması için .NET Kılavuzu](/azure/storage/storage-dotnet-how-to-use-tables)</span><span class="sxs-lookup"><span data-stu-id="36573-114">For a conceptual overview of table storage, please see [the .NET guide for table storage](/azure/storage/storage-dotnet-how-to-use-tables)</span></span>

## <a name="prerequisites"></a><span data-ttu-id="36573-115">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="36573-115">Prerequisites</span></span>

<span data-ttu-id="36573-116">Bu kılavuzu kullanmak için öncelikle [bir Azure depolama hesabı oluşturma](/azure/storage/storage-create-storage-account).</span><span class="sxs-lookup"><span data-stu-id="36573-116">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span>
<span data-ttu-id="36573-117">Bu hesap için depolama erişim anahtarınızı de gerekir.</span><span class="sxs-lookup"><span data-stu-id="36573-117">You'll also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="36573-118">Bir F # betiği ve başlangıç F # Etkileşimli oluşturma</span><span class="sxs-lookup"><span data-stu-id="36573-118">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="36573-119">Bu makaledeki örnekler, F # uygulaması veya F # betiği kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="36573-119">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="36573-120">F # betiği oluşturmak için dosya oluştur `.fsx` uzantısı, örneğin `tables.fsx`, ortamınızdaki F # geliştirme.</span><span class="sxs-lookup"><span data-stu-id="36573-120">To create an F# script, create a file with the `.fsx` extension, for example `tables.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="36573-121">Ardından, kullanın bir [Paket Yöneticisi](package-management.md) gibi [Paket](https://fsprojects.github.io/Paket/) veya [NuGet](https://www.nuget.org/) yüklemek için `WindowsAzure.Storage` paket ve başvuru `WindowsAzure.Storage.dll` bir kullanarakkomut`#r`yönergesi.</span><span class="sxs-lookup"><span data-stu-id="36573-121">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span> <span data-ttu-id="36573-122">Bunu yeniden 'Microsoft.WindowsAzure.ConfigurationManager' için Microsoft.Azure ad alanı alabilmek için.</span><span class="sxs-lookup"><span data-stu-id="36573-122">Do it again for \`Microsoft.WindowsAzure.ConfigurationManager' in order to get the Microsoft.Azure namespace.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="36573-123">Ad alanı bildirimleri ekleme</span><span class="sxs-lookup"><span data-stu-id="36573-123">Add namespace declarations</span></span>

<span data-ttu-id="36573-124">Aşağıdakileri ekleyin `open` deyimleri üstüne `tables.fsx` dosyası:</span><span class="sxs-lookup"><span data-stu-id="36573-124">Add the following `open` statements to the top of the `tables.fsx` file:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a><span data-ttu-id="36573-125">Bağlantı dizenizi Al</span><span class="sxs-lookup"><span data-stu-id="36573-125">Get your connection string</span></span>

<span data-ttu-id="36573-126">Bu öğretici için bir Azure depolama bağlantı dizesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="36573-126">You'll need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="36573-127">Bağlantı dizeleri hakkında daha fazla bilgi için bkz: [Storage bağlantı dizelerini yapılandırma](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="36573-127">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="36573-128">Öğretici için şuna benzer betiğinizin bağlantı dizenizi girin:</span><span class="sxs-lookup"><span data-stu-id="36573-128">For the tutorial, you'll enter your connection string in your script, like this:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L11-L11)]

<span data-ttu-id="36573-129">Ancak, bu olduğu **önerilmez** için gerçek projeleri.</span><span class="sxs-lookup"><span data-stu-id="36573-129">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="36573-130">Depolama hesabı anahtarınız depolama hesabınızın kök parolasına benzer.</span><span class="sxs-lookup"><span data-stu-id="36573-130">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="36573-131">Her zaman depolama hesabı anahtarınızı korumak dikkatli olun.</span><span class="sxs-lookup"><span data-stu-id="36573-131">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="36573-132">Sabit kodlama veya başkalarının erişebileceği düz metin dosyasına kaydetme diğer kullanıcılara dağıtmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="36573-132">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="36573-133">Bunu tehlikede olduğunu düşünüyorsanız, Azure Portalı'nı kullanarak anahtarınızı yeniden oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36573-133">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="36573-134">İçin gerçek uygulamalar, depolama bağlantı dizenizi korumak için en iyi yapılandırma dosyasında yoludur.</span><span class="sxs-lookup"><span data-stu-id="36573-134">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="36573-135">Yapılandırma dosyasından bağlantı dizesini almak için bunu yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="36573-135">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L13-L15)]

<span data-ttu-id="36573-136">Azure Yapılandırma Yöneticisi'ni kullanarak isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="36573-136">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="36573-137">.NET Framework'ün gibi bir API de kullanabilirsiniz `ConfigurationManager` türü.</span><span class="sxs-lookup"><span data-stu-id="36573-137">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="36573-138">Bağlantı dizesini ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="36573-138">Parse the connection string</span></span>

<span data-ttu-id="36573-139">Bağlantı dizesini ayrıştırmak için kullanın:</span><span class="sxs-lookup"><span data-stu-id="36573-139">To parse the connection string, use:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L21-L22)]

<span data-ttu-id="36573-140">Bu döndürülecek bir `CloudStorageAccount`.</span><span class="sxs-lookup"><span data-stu-id="36573-140">This will return a `CloudStorageAccount`.</span></span>

### <a name="create-the-table-service-client"></a><span data-ttu-id="36573-141">Tablo hizmeti istemcisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="36573-141">Create the Table service client</span></span>

<span data-ttu-id="36573-142">`CloudTableClient` Sınıfı tabloları ve varlıkları Table storage'da depolanan almanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="36573-142">The `CloudTableClient` class enables you to retrieve tables and entities stored in Table storage.</span></span> <span data-ttu-id="36573-143">Hizmet istemcisini oluşturma yöntemlerinden biri aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="36573-143">Here's one way to create the service client:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L28-L29)]

<span data-ttu-id="36573-144">Şimdi veri okuyan ve tablo depolamaya veri yazan kodu yazmaya hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="36573-144">Now you are ready to write code that reads data from and writes data to Table storage.</span></span>

## <a name="create-a-table"></a><span data-ttu-id="36573-145">Bir tablo oluştur</span><span class="sxs-lookup"><span data-stu-id="36573-145">Create a table</span></span>

<span data-ttu-id="36573-146">Bu örnek, zaten yoksa, bir tablo oluşturulacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="36573-146">This example shows how to create a table if it does not already exist:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L35-L39)]

## <a name="add-an-entity-to-a-table"></a><span data-ttu-id="36573-147">Tabloya bir varlık ekleme</span><span class="sxs-lookup"><span data-stu-id="36573-147">Add an entity to a table</span></span>

<span data-ttu-id="36573-148">Öğesinden devralan bir türe sahip bir varlık sahip `TableEntity`.</span><span class="sxs-lookup"><span data-stu-id="36573-148">An entity has to have a type that inherits from `TableEntity`.</span></span> <span data-ttu-id="36573-149">Genişletebilirsiniz `TableEntity` istediğiniz gibi ancak türünüz *gerekir* bir parametresiz oluşturucuya sahip.</span><span class="sxs-lookup"><span data-stu-id="36573-149">You can extend `TableEntity` in any way you like, but your type *must* have a parameter-less constructor.</span></span> <span data-ttu-id="36573-150">Yalnızca hem de özellikleri `get` ve `set` , Azure tablosunda depolanır.</span><span class="sxs-lookup"><span data-stu-id="36573-150">Only properties that have both `get` and `set` will be stored in your Azure Table.</span></span>

<span data-ttu-id="36573-151">Bir varlığın bölüm ve sıra anahtarı varlığı tabloda benzersiz şekilde tanımlar.</span><span class="sxs-lookup"><span data-stu-id="36573-151">An entity's partition and row key uniquely identify the entity in the table.</span></span> <span data-ttu-id="36573-152">Aynı bölüm anahtarına sahip varlıklar farklı bölüm anahtarlarının göre daha hızlı sorgulanabilir ancak farklı bölüm anahtarlarının kullanılması paralel işlemler daha fazla ölçeklenebilirlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="36573-152">Entities with the same partition key can be queried faster than those with different partition keys, but using diverse partition keys allows for greater scalability of parallel operations.</span></span>

<span data-ttu-id="36573-153">Bir örneği burada verilmiştir bir `Customer` kullanan `lastName` bölüm anahtarı olarak ve `firstName` satır anahtarı olarak.</span><span class="sxs-lookup"><span data-stu-id="36573-153">Here's an example of a `Customer` that uses the `lastName` as the partition key and the `firstName` as the row key.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L45-L52)]

<span data-ttu-id="36573-154">Ekleyeceğiz artık bizim `Customer` tablosu.</span><span class="sxs-lookup"><span data-stu-id="36573-154">Now we'll add our `Customer` to the table.</span></span> <span data-ttu-id="36573-155">Bunu yapmak için oluşturduğunuz bir `TableOperation` tabloda yürütülecek.</span><span class="sxs-lookup"><span data-stu-id="36573-155">To do so, you create a `TableOperation` that will execute on the table.</span></span> <span data-ttu-id="36573-156">Bu durumda, oluşturduğunuz bir `Insert` işlemi.</span><span class="sxs-lookup"><span data-stu-id="36573-156">In this case, you create an `Insert` operation.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L54-L55)]

## <a name="insert-a-batch-of-entities"></a><span data-ttu-id="36573-157">Bir toplu işlem varlık yerleştirme</span><span class="sxs-lookup"><span data-stu-id="36573-157">Insert a batch of entities</span></span>

<span data-ttu-id="36573-158">Toplu işlem varlık bir tek bir yazma işlemini kullanarak bir tabloya ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36573-158">You can insert a batch of entities into a table using a single write operation.</span></span> <span data-ttu-id="36573-159">Toplu işlemleri, tek bir yürütme işlemlere birleştirmenize izin verir, ancak bazı sınırlamalar vardır:</span><span class="sxs-lookup"><span data-stu-id="36573-159">Batch operations allow you to combine operations into a single execution, but they have some restrictions:</span></span>

- <span data-ttu-id="36573-160">Güncelleştirmeleri gerçekleştirme siler ve aynı toplu işlemde ekler.</span><span class="sxs-lookup"><span data-stu-id="36573-160">You can perform updates, deletes, and inserts in the same batch operation.</span></span>
- <span data-ttu-id="36573-161">Toplu işlem en fazla 100 varlık içerebilir.</span><span class="sxs-lookup"><span data-stu-id="36573-161">A batch operation can include up to 100 entities.</span></span>
- <span data-ttu-id="36573-162">Bir toplu işlemde tüm varlıkların aynı bölüm anahtarına sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="36573-162">All entities in a batch operation must have the same partition key.</span></span>
- <span data-ttu-id="36573-163">Bir toplu işlemde bir sorgu gerçekleştirmek mümkün olsa da, toplu işlemdeki tek işlem olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="36573-163">While it is possible to perform a query in a batch operation, it must be the only operation in the batch.</span></span>

<span data-ttu-id="36573-164">Toplu işlem iki eklemeleri birleştirir biraz kod şöyledir:</span><span class="sxs-lookup"><span data-stu-id="36573-164">Here's some code that combines two inserts into a batch operation:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L62-L71)]

## <a name="retrieve-all-entities-in-a-partition"></a><span data-ttu-id="36573-165">Tüm varlıkları bir bölüme alma</span><span class="sxs-lookup"><span data-stu-id="36573-165">Retrieve all entities in a partition</span></span>

<span data-ttu-id="36573-166">Bir bölümdeki tüm varlıklar için bir tabloyu sorgulamak için kullanın bir `TableQuery` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="36573-166">To query a table for all entities in a partition, use a `TableQuery` object.</span></span> <span data-ttu-id="36573-167">Burada, "Buster" Bölüm anahtarı olduğu varlıklar için filtreleyin.</span><span class="sxs-lookup"><span data-stu-id="36573-167">Here, you filter for entities where "Buster" is the partition key.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L77-L80)]

<span data-ttu-id="36573-168">Artık sonuçlar yazdırma:</span><span class="sxs-lookup"><span data-stu-id="36573-168">You now print the results:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L84-L85)]


## <a name="retrieve-a-range-of-entities-in-a-partition"></a><span data-ttu-id="36573-169">Bir dizi varlıkları bir bölüme alma</span><span class="sxs-lookup"><span data-stu-id="36573-169">Retrieve a range of entities in a partition</span></span>

<span data-ttu-id="36573-170">Bir bölümdeki tüm varlıkları sorgulamak istemiyorsanız bölüm anahtarı Filtresi ile bir satır anahtarı filtresini birleştirerek bir aralık belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36573-170">If you don't want to query all the entities in a partition, you can specify a range by combining the partition key filter with a row key filter.</span></span> <span data-ttu-id="36573-171">Burada, iki filtre "Buster" bölümünde tüm varlıkları almak için burada satır anahtarı (ad) alfabede "M"'den önceki bir harfle başlayan kullanın.</span><span class="sxs-lookup"><span data-stu-id="36573-171">Here, you use two filters to get all entities in the "Buster" partition where the row key (first name) starts with a letter earlier than "M" in the alphabet.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L91-L100)]

<span data-ttu-id="36573-172">Artık sonuçlar yazdırma:</span><span class="sxs-lookup"><span data-stu-id="36573-172">You now print the results:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L102-L103)]

## <a name="retrieve-a-single-entity"></a><span data-ttu-id="36573-173">Tek bir varlık alma</span><span class="sxs-lookup"><span data-stu-id="36573-173">Retrieve a single entity</span></span>

<span data-ttu-id="36573-174">Tek, belirli bir varlığı almak üzere bir sorgu yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36573-174">You can write a query to retrieve a single, specific entity.</span></span> <span data-ttu-id="36573-175">Burada, kullandığınız bir `TableOperation` "Larry Buster" Müşteri belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="36573-175">Here, you use a `TableOperation` to specify the customer "Larry Buster".</span></span> <span data-ttu-id="36573-176">Bir koleksiyon yerine ulaşırsınız bir `Customer`.</span><span class="sxs-lookup"><span data-stu-id="36573-176">Instead of a collection, you get back a `Customer`.</span></span> <span data-ttu-id="36573-177">Bir sorguda hem Bölüm anahtarı hem de satır anahtarını belirtmek tablo hizmetinden tek bir varlık almak için en hızlı yoludur.</span><span class="sxs-lookup"><span data-stu-id="36573-177">Specifying both the partition key and the row key in a query is the fastest way to retrieve a single entity from the Table service.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L109-L111)]

<span data-ttu-id="36573-178">Artık sonuçlar yazdırma:</span><span class="sxs-lookup"><span data-stu-id="36573-178">You now print the results:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L113-L115)]


## <a name="replace-an-entity"></a><span data-ttu-id="36573-179">Bir varlığı değiştirme</span><span class="sxs-lookup"><span data-stu-id="36573-179">Replace an entity</span></span>

<span data-ttu-id="36573-180">Bir varlığı güncelleştirmek için tablo hizmetinden alın, varlık nesnesini değiştirin ve sonra geri tablo hizmeti kullanmaya değişiklikleri kaydetmek bir `Replace` işlemi.</span><span class="sxs-lookup"><span data-stu-id="36573-180">To update an entity, retrieve it from the Table service, modify the entity object, and then save the changes back to the Table service using a `Replace` operation.</span></span> <span data-ttu-id="36573-181">Bu, işlem başarısız olur; bu durumda alındığından beri sunucunun varlıkta değiştirilmediği sürece bu sunucu üzerinde tamamen değiştirilmesini varlık neden olur.</span><span class="sxs-lookup"><span data-stu-id="36573-181">This causes the entity to be fully replaced on the server, unless the entity on the server has changed since it was retrieved, in which case the operation will fail.</span></span> <span data-ttu-id="36573-182">Bu hata uygulamanızı değişiklikler diğer kaynaklardan yanlışlıkla üzerine yazılmasını önlemektir.</span><span class="sxs-lookup"><span data-stu-id="36573-182">This failure is to prevent your application from inadvertently overwriting changes from other sources.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L121-L128)]

## <a name="insert-or-replace-an-entity"></a><span data-ttu-id="36573-183">Ekleme veya değiştirme bir varlık</span><span class="sxs-lookup"><span data-stu-id="36573-183">Insert-or-replace an entity</span></span>

<span data-ttu-id="36573-184">Bazı durumlarda, varlık tablosunda varsa mevcut bilinmiyor.</span><span class="sxs-lookup"><span data-stu-id="36573-184">Sometimes, you don't know if the entity exists in the table or not.</span></span> <span data-ttu-id="36573-185">Ve içinde saklı geçerli değerlerin bulursa, artık gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="36573-185">And if it does, the current values stored in it are no longer needed.</span></span> <span data-ttu-id="36573-186">Kullanabileceğiniz `InsertOrReplace` varlığı oluşturun veya, durumuna bakılmaksızın varsa değiştirin.</span><span class="sxs-lookup"><span data-stu-id="36573-186">You can use `InsertOrReplace` to create the entity, or replace it if it exists, regardless of its state.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L134-L140)]

## <a name="query-a-subset-of-entity-properties"></a><span data-ttu-id="36573-187">Varlık özelliklerinin bir alt sorgu</span><span class="sxs-lookup"><span data-stu-id="36573-187">Query a subset of entity properties</span></span>

<span data-ttu-id="36573-188">Tablo sorgusu, bunların tümü yerine bir varlıktaki birkaç özelliği alabilir.</span><span class="sxs-lookup"><span data-stu-id="36573-188">A table query can retrieve just a few properties from an entity instead of all of them.</span></span> <span data-ttu-id="36573-189">Projeksiyon, olarak adlandırılan bu teknik özellikle büyük varlıklar için sorgu performansını iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="36573-189">This technique, called projection, can improve query performance, especially for large entities.</span></span> <span data-ttu-id="36573-190">Burada, yalnızca e-posta adresleri kullanarak dönmek `DynamicTableEntity` ve `EntityResolver`.</span><span class="sxs-lookup"><span data-stu-id="36573-190">Here, you return only email addresses using `DynamicTableEntity` and `EntityResolver`.</span></span> <span data-ttu-id="36573-191">Bu kod yalnızca tablo hizmetinde bir hesap kullanırken çalıştırılır şekilde projeksiyon yerel depolama öykünücüsünde desteklenmez unutmayın.</span><span class="sxs-lookup"><span data-stu-id="36573-191">Note that projection is not supported on the local storage emulator, so this code runs only when you're using an account on the Table service.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L146-L157)]

## <a name="retrieve-entities-in-pages-asynchronously"></a><span data-ttu-id="36573-192">Varlıkları sayfalarda zaman uyumsuz olarak Al</span><span class="sxs-lookup"><span data-stu-id="36573-192">Retrieve entities in pages asynchronously</span></span>

<span data-ttu-id="36573-193">Çok sayıda varlık okuyorsanız ve bunları alındıktan gibi yerine tümünü döndürmek beklenirken işlem yapmak istediğiniz, bölümlendirilmiş bir sorgu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36573-193">If you are reading a large number of entities, and you want to process them as they are retrieved rather than waiting for them all to return, you can use a segmented query.</span></span> <span data-ttu-id="36573-194">Burada, büyük bir döndürmek için sonuç kümesi için beklerken çalıştırmanın engellenmemesi bir zaman uyumsuz iş akışı kullanarak sayfalarında sonuçları döndürür.</span><span class="sxs-lookup"><span data-stu-id="36573-194">Here, you return results in pages by using an async workflow so that execution is not blocked while you're waiting for a large set of results to return.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L163-L177)]

<span data-ttu-id="36573-195">Artık bu hesaplama zaman uyumlu olarak yürütün:</span><span class="sxs-lookup"><span data-stu-id="36573-195">You now execute this computation synchronously:</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L179-L179)]

## <a name="delete-an-entity"></a><span data-ttu-id="36573-196">Bir varlığı silme</span><span class="sxs-lookup"><span data-stu-id="36573-196">Delete an entity</span></span>

<span data-ttu-id="36573-197">Bunu aldıktan sonra bir varlık silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36573-197">You can delete an entity after you have retrieved it.</span></span> <span data-ttu-id="36573-198">Siz aldıktan sonra varlık değiştirilmiş güncelleştirmeyle bir varlık gibi bu başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="36573-198">As with updating an entity, this will fail if the entity has changed since you retrieved it.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L185-L186)]

## <a name="delete-a-table"></a><span data-ttu-id="36573-199">Tablo silme</span><span class="sxs-lookup"><span data-stu-id="36573-199">Delete a table</span></span>

<span data-ttu-id="36573-200">Bir depolama hesabından bir tablo silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36573-200">You can delete a table from a storage account.</span></span> <span data-ttu-id="36573-201">Silinmiş bir tablo silme işlemi şu süre boyunca yeniden oluşturma kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="36573-201">A table that has been deleted will be unavailable to be re-created for a period of time following the deletion.</span></span>

[!code-fsharp[TableStorage](../../../samples/snippets/fsharp/azure/table-storage.fsx#L192-L192)]

## <a name="next-steps"></a><span data-ttu-id="36573-202">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="36573-202">Next steps</span></span>

<span data-ttu-id="36573-203">Table Storage öğrendiğinize göre daha karmaşık depolama görevleri hakkında bilgi edinmek için aşağıdaki bağlantıları izleyin:</span><span class="sxs-lookup"><span data-stu-id="36573-203">Now that you've learned the basics of Table storage, follow these links to learn about more complex storage tasks:</span></span>

- [<span data-ttu-id="36573-204">.NET için Azure depolama API'leri</span><span class="sxs-lookup"><span data-stu-id="36573-204">Azure Storage APIs for .NET</span></span>](/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="36573-205">Azure depolama türü sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="36573-205">Azure Storage Type Provider</span></span>](http://fsprojects.github.io/AzureStorageTypeProvider/)
- [<span data-ttu-id="36573-206">Azure depolama ekibi blogu</span><span class="sxs-lookup"><span data-stu-id="36573-206">Azure Storage Team Blog</span></span>](http://blogs.msdn.com/b/windowsazurestorage/)
- [<span data-ttu-id="36573-207">Azure Storage bağlantı dizelerini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="36573-207">Configure Azure Storage connection strings</span></span>](/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="36573-208">.NET içinde Azure tablo depolaması ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="36573-208">Getting Started with Azure Table Storage in .NET</span></span>](https://azure.microsoft.com/documentation/samples/storage-table-dotnet-getting-started/)
