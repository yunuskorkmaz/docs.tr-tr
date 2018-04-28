---
title: "F # kullanarak Azure Blob storage'ı kullanmaya başlama"
description: Azure Blob storage ile bulutta yapılandırılmamış veri depolayın.
author: sylvanc
ms.author: phcart
ms.date: 09/20/2016
ms.topic: conceptual
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 0414f0ca4aa2c2b75e80b3fd6531be74924fb60f
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="get-started-with-azure-blob-storage-using-f"></a><span data-ttu-id="ba712-103">F # kullanarak Azure Blob storage'ı kullanmaya başlama</span><span class="sxs-lookup"><span data-stu-id="ba712-103">Get started with Azure Blob storage using F#</span></span> #

<span data-ttu-id="ba712-104">Azure Blob storage bulutta nesne/BLOB olarak yapılandırılmamış veri depolayan bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="ba712-104">Azure Blob storage is a service that stores unstructured data in the cloud as objects/blobs.</span></span> <span data-ttu-id="ba712-105">BLOB Depolama metin veya ikili veriler, belge, ortam dosyası veya uygulama Yükleyici gibi herhangi bir türde depolayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba712-105">Blob storage can store any type of text or binary data, such as a document, media file, or application installer.</span></span> <span data-ttu-id="ba712-106">BLOB storage ayrıca nesne depolama olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="ba712-106">Blob storage is also referred to as object storage.</span></span>

<span data-ttu-id="ba712-107">Bu makalede, Blob storage kullanarak ortak görevlerin nasıl gerçekleştirileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ba712-107">This article shows you how to perform common tasks using Blob storage.</span></span> <span data-ttu-id="ba712-108">Örnekler, F # .NET için Azure Storage istemci kitaplığı kullanılarak kullanılarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="ba712-108">The samples are written using F# using the Azure Storage Client Library for .NET.</span></span> <span data-ttu-id="ba712-109">Karşıya yükleme listesinde, indirin ve BLOB'ları silme nasıl ele görevleri içerir.</span><span class="sxs-lookup"><span data-stu-id="ba712-109">The tasks covered include how to upload, list, download, and delete blobs.</span></span>

<span data-ttu-id="ba712-110">Blob depolama kavramsal bir genel bakış için bkz: [blob storage için .NET Kılavuzu](/azure/storage/storage-dotnet-how-to-use-blobs).</span><span class="sxs-lookup"><span data-stu-id="ba712-110">For a conceptual overview of blob storage, see [the .NET guide for blob storage](/azure/storage/storage-dotnet-how-to-use-blobs).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ba712-111">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="ba712-111">Prerequisites</span></span>

<span data-ttu-id="ba712-112">Bu kılavuzu kullanmak için öncelikle [bir Azure depolama hesabı oluşturma](/azure/storage/storage-create-storage-account).</span><span class="sxs-lookup"><span data-stu-id="ba712-112">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span> <span data-ttu-id="ba712-113">Ayrıca bu hesap için depolama erişim anahtarınızı gerekir.</span><span class="sxs-lookup"><span data-stu-id="ba712-113">You also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="ba712-114">Bir F # betiği ve başlangıç F # Etkileşimli oluşturma</span><span class="sxs-lookup"><span data-stu-id="ba712-114">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="ba712-115">Bu makaledeki örnekler, F # uygulaması veya F # betiği kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ba712-115">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="ba712-116">F # betiği oluşturmak için dosya oluştur `.fsx` uzantısı, örneğin `blobs.fsx`, ortamınızdaki F # geliştirme.</span><span class="sxs-lookup"><span data-stu-id="ba712-116">To create an F# script, create a file with the `.fsx` extension, for example `blobs.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="ba712-117">Ardından, kullanın bir [Paket Yöneticisi](package-management.md) gibi [Paket](https://fsprojects.github.io/Paket/) veya [NuGet](https://www.nuget.org/) yüklemek için `WindowsAzure.Storage` ve `Microsoft.WindowsAzure.ConfigurationManager` paketler ve başvuru `WindowsAzure.Storage.dll` ve `Microsoft.WindowsAzure.Configuration.dll` komut dosyası kullanarak bir `#r` yönergesi.</span><span class="sxs-lookup"><span data-stu-id="ba712-117">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` and `Microsoft.WindowsAzure.ConfigurationManager` packages and reference `WindowsAzure.Storage.dll` and `Microsoft.WindowsAzure.Configuration.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="ba712-118">Ad alanı bildirimleri ekleme</span><span class="sxs-lookup"><span data-stu-id="ba712-118">Add namespace declarations</span></span>

<span data-ttu-id="ba712-119">Aşağıdakileri ekleyin `open` deyimleri üstüne `blobs.fsx` dosyası:</span><span class="sxs-lookup"><span data-stu-id="ba712-119">Add the following `open` statements to the top of the `blobs.fsx` file:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a><span data-ttu-id="ba712-120">Bağlantı dizenizi Al</span><span class="sxs-lookup"><span data-stu-id="ba712-120">Get your connection string</span></span>

<span data-ttu-id="ba712-121">Bu öğretici için bir Azure depolama bağlantı dizesi gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="ba712-121">You need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="ba712-122">Bağlantı dizeleri hakkında daha fazla bilgi için bkz: [Storage bağlantı dizelerini yapılandırma](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="ba712-122">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="ba712-123">Öğretici için bağlantı dizenizi şuna benzer betiğinizin girin:</span><span class="sxs-lookup"><span data-stu-id="ba712-123">For the tutorial, you enter your connection string in your script, like this:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L11-L11)]

<span data-ttu-id="ba712-124">Ancak, bu olduğu **önerilmez** için gerçek projeleri.</span><span class="sxs-lookup"><span data-stu-id="ba712-124">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="ba712-125">Depolama hesabı anahtarınız depolama hesabınızın kök parolasına benzer.</span><span class="sxs-lookup"><span data-stu-id="ba712-125">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="ba712-126">Her zaman depolama hesabı anahtarınızı korumak dikkatli olun.</span><span class="sxs-lookup"><span data-stu-id="ba712-126">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="ba712-127">Sabit kodlama veya başkalarının erişebileceği düz metin dosyasına kaydetme diğer kullanıcılara dağıtmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="ba712-127">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="ba712-128">Bunu tehlikede olduğunu düşünüyorsanız, Azure Portalı'nı kullanarak anahtarınızı yeniden oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba712-128">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="ba712-129">İçin gerçek uygulamalar, depolama bağlantı dizenizi korumak için en iyi yapılandırma dosyasında yoludur.</span><span class="sxs-lookup"><span data-stu-id="ba712-129">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="ba712-130">Yapılandırma dosyasından bağlantı dizesini almak için bunu yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ba712-130">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L13-L15)]

<span data-ttu-id="ba712-131">Azure Yapılandırma Yöneticisi'ni kullanarak isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="ba712-131">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="ba712-132">.NET Framework'ün gibi bir API de kullanabilirsiniz `ConfigurationManager` türü.</span><span class="sxs-lookup"><span data-stu-id="ba712-132">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="ba712-133">Bağlantı dizesini ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="ba712-133">Parse the connection string</span></span>

<span data-ttu-id="ba712-134">Bağlantı dizesini ayrıştırmak için kullanın:</span><span class="sxs-lookup"><span data-stu-id="ba712-134">To parse the connection string, use:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L21-L22)]

<span data-ttu-id="ba712-135">Bu döndürür bir `CloudStorageAccount`.</span><span class="sxs-lookup"><span data-stu-id="ba712-135">This returns a `CloudStorageAccount`.</span></span>

### <a name="create-some-local-dummy-data"></a><span data-ttu-id="ba712-136">Bazı yerel sahte veriler oluşturun</span><span class="sxs-lookup"><span data-stu-id="ba712-136">Create some local dummy data</span></span>

<span data-ttu-id="ba712-137">Başlamadan önce bazı kukla yerel veri bizim betik dizininde oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ba712-137">Before you begin, create some dummy local data in the directory of our script.</span></span> <span data-ttu-id="ba712-138">Daha sonra bu verileri karşıya yükleyin.</span><span class="sxs-lookup"><span data-stu-id="ba712-138">Later you upload this data.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L28-L30)]

### <a name="create-the-blob-service-client"></a><span data-ttu-id="ba712-139">Blob hizmeti istemcisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="ba712-139">Create the Blob service client</span></span>

<span data-ttu-id="ba712-140">`CloudBlobClient` Türü kapsayıcılar ve bloblar Blob storage'da depolanan almanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="ba712-140">The `CloudBlobClient` type enables you to retrieve containers and blobs stored in Blob storage.</span></span> <span data-ttu-id="ba712-141">Hizmet istemcisini oluşturma yöntemlerinden biri aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="ba712-141">Here's one way to create the service client:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L36-L36)]

<span data-ttu-id="ba712-142">Şimdi veri okuyan ve Blob depolamaya veri yazan kodu yazmaya hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="ba712-142">Now you are ready to write code that reads data from and writes data to Blob storage.</span></span>

## <a name="create-a-container"></a><span data-ttu-id="ba712-143">Bir kapsayıcı oluşturma</span><span class="sxs-lookup"><span data-stu-id="ba712-143">Create a container</span></span>

<span data-ttu-id="ba712-144">Bu örnek, zaten yoksa, bir kapsayıcı oluşturulacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="ba712-144">This example shows how to create a container if it does not already exist:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L42-L46)]

<span data-ttu-id="ba712-145">Varsayılan olarak, yeni kapsayıcı Bu kapsayıcıdan BLOB indirmek için depolama erişim tuşunuzı belirlemeniz gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="ba712-145">By default, the new container is private, meaning that you must specify your storage access key to download blobs from this container.</span></span> <span data-ttu-id="ba712-146">Kapsayıcı içindeki dosyaların herkese kullanılabilmesini istiyorsanız, aşağıdaki kodu kullanarak genel kapsayıcıya ayarlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ba712-146">If you want to make the files within the container available to everyone, you can set the container to be public using the following code:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L48-L49)]

<span data-ttu-id="ba712-147">Internet üzerinden herkes ortak bir kapsayıcıdaki blobları görebilir ancak değiştirmek veya yalnızca uygun hesap erişim tuşu veya paylaşılan erişim imzası varsa silin.</span><span class="sxs-lookup"><span data-stu-id="ba712-147">Anyone on the Internet can see blobs in a public container, but you can modify or delete them only if you have the appropriate account access key or a shared access signature.</span></span>

## <a name="upload-a-blob-into-a-container"></a><span data-ttu-id="ba712-148">Bir kapsayıcıya bir blob karşıya yükleme</span><span class="sxs-lookup"><span data-stu-id="ba712-148">Upload a blob into a container</span></span>

<span data-ttu-id="ba712-149">Azure Blob Storage blok blobları ve sayfa bloblarını destekler.</span><span class="sxs-lookup"><span data-stu-id="ba712-149">Azure Blob Storage supports block blobs and page blobs.</span></span> <span data-ttu-id="ba712-150">Çoğu durumda, bir blok blobu kullanmak için önerilen türüdür.</span><span class="sxs-lookup"><span data-stu-id="ba712-150">In most cases, a block blob is the recommended type to use.</span></span>

<span data-ttu-id="ba712-151">Bir dosyayı bir blok blobuna yüklemek için bir kapsayıcı başvurusu alın ve blok blob başvurusu almak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="ba712-151">To upload a file to a block blob, get a container reference and use it to get a block blob reference.</span></span> <span data-ttu-id="ba712-152">Bir blob başvurusu edindiğinizde veri kendisine çağırarak yükleyebilirsiniz `UploadFromFile` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ba712-152">Once you have a blob reference, you can upload any stream of data to it by calling the `UploadFromFile` method.</span></span> <span data-ttu-id="ba712-153">Bu işlem, daha önce mevcut alamadık veya mevcut değilse üzerine blob oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ba712-153">This operation creates the blob if it didn't previously exist, or overwrite it if it does exist.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L55-L59)]

## <a name="list-the-blobs-in-a-container"></a><span data-ttu-id="ba712-154">BLOB'ları bir kapsayıcıda listelemek</span><span class="sxs-lookup"><span data-stu-id="ba712-154">List the blobs in a container</span></span>

<span data-ttu-id="ba712-155">BLOB'ları bir kapsayıcıda listelemek için önce bir kapsayıcı başvurusu edinin.</span><span class="sxs-lookup"><span data-stu-id="ba712-155">To list the blobs in a container, first get a container reference.</span></span> <span data-ttu-id="ba712-156">Kapsayıcının sonra kullanabileceğiniz `ListBlobs` blobları ve/veya dizinleri içindeki alma yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ba712-156">You can then use the container's `ListBlobs` method to retrieve the blobs and/or directories within it.</span></span> <span data-ttu-id="ba712-157">Zengin özellik ve yöntem erişmek için `IListBlobItem`, kendisine atamalısınız bir `CloudBlockBlob`, `CloudPageBlob`, veya `CloudBlobDirectory` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="ba712-157">To access the rich set of properties and methods for a returned `IListBlobItem`, you must cast it to a `CloudBlockBlob`, `CloudPageBlob`, or `CloudBlobDirectory` object.</span></span> <span data-ttu-id="ba712-158">Tür bilinmiyorsa, hangisine yayınlayacağınızı belirlemek için bir tür denetimi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba712-158">If the type is unknown, you can use a type check to determine which to cast it to.</span></span> <span data-ttu-id="ba712-159">Aşağıdaki kodda almak ve her öğe URI'sini çıkış gösterilmiştir `mydata` kapsayıcı:</span><span class="sxs-lookup"><span data-stu-id="ba712-159">The following code demonstrates how to retrieve and output the URI of each item in the `mydata` container:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L67-L80)]

<span data-ttu-id="ba712-160">Ayrıca, ad blobları adlarında yol bilgileriyle de erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba712-160">You can also name blobs with path information in their names.</span></span> <span data-ttu-id="ba712-161">Bu, düzenlemek ve geleneksel bir dosya sisteminde olduğu gibi çapraz bir sanal dizin yapısı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ba712-161">This creates a virtual directory structure that you can organize and traverse as you would a traditional file system.</span></span> <span data-ttu-id="ba712-162">Dizin yapısı yalnızca sanal - yalnızca Blob depolama alanına kullanılabilir kapsayıcılar ve bloblar kaynaklardır unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ba712-162">Note that the directory structure is virtual only - the only resources available in Blob storage are containers and blobs.</span></span> <span data-ttu-id="ba712-163">Ancak, depolama istemci kitaplığı sunan bir `CloudBlobDirectory` bir sanal dizine ait ve bu şekilde düzenlenen BLOB'ları ile çalışma sürecini basitleştirmek için nesne.</span><span class="sxs-lookup"><span data-stu-id="ba712-163">However, the storage client library offers a `CloudBlobDirectory` object to refer to a virtual directory and simplify the process of working with blobs that are organized in this way.</span></span>

<span data-ttu-id="ba712-164">Örneğin, aşağıdaki blok blobları adlı bir kapsayıcı kümesini göz önünde bulundurun `photos`:</span><span class="sxs-lookup"><span data-stu-id="ba712-164">For example, consider the following set of block blobs in a container named `photos`:</span></span>

<span data-ttu-id="ba712-165">*photo1.jpg*
*2015/architecture/description.txt*
*2015/architecture/photo3.jpg*
*2015 / Mimari/photo4.jpg*
*2016/architecture/photo5.jpg*
*2016/architecture/photo6.jpg* 
 *2016/architecture/description.txt*
*2016/photo7.jpg*</span><span class="sxs-lookup"><span data-stu-id="ba712-165">*photo1.jpg*
*2015/architecture/description.txt*
*2015/architecture/photo3.jpg*
*2015/architecture/photo4.jpg*
*2016/architecture/photo5.jpg*
*2016/architecture/photo6.jpg*
*2016/architecture/description.txt*
*2016/photo7.jpg*</span></span>

<span data-ttu-id="ba712-166">Çağırdığınızda `ListBlobs` (yukarıdaki örnekte) olduğu bir kapsayıcıda, hiyerarşik bir listeleme döner.</span><span class="sxs-lookup"><span data-stu-id="ba712-166">When you call `ListBlobs` on a container (as in the above sample), a hierarchical listing is returned.</span></span> <span data-ttu-id="ba712-167">Her ikisi de içeriyorsa, `CloudBlobDirectory` ve `CloudBlockBlob` sonuçta çıktı şuna benzer sonra dizinleri ve blobları kapsayıcıda sırasıyla temsil eden nesneler:</span><span class="sxs-lookup"><span data-stu-id="ba712-167">If it contains both `CloudBlobDirectory` and `CloudBlockBlob` objects, representing the directories and blobs in the container, respectively, then the resulting output looks similar to this:</span></span>

```console
Directory: https://<accountname>.blob.core.windows.net/photos/2015/
Directory: https://<accountname>.blob.core.windows.net/photos/2016/
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

<span data-ttu-id="ba712-168">İsteğe bağlı olarak, ayarlayabileceğiniz `UseFlatBlobListing` parametresinin `ListBlobs` yöntemine `true`.</span><span class="sxs-lookup"><span data-stu-id="ba712-168">Optionally, you can set the `UseFlatBlobListing` parameter of the `ListBlobs` method to `true`.</span></span> <span data-ttu-id="ba712-169">Bu durumda kapsayıcıdaki her blob olarak döndürülür bir `CloudBlockBlob` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="ba712-169">In this case, every blob in the container is returned as a `CloudBlockBlob` object.</span></span> <span data-ttu-id="ba712-170">Çağrı `ListBlobs` düz listeleme şu şekilde görünür döndürmek için:</span><span class="sxs-lookup"><span data-stu-id="ba712-170">The call to `ListBlobs` to return a flat listing looks like this:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L82-L89)]

<span data-ttu-id="ba712-171">Ayrıca, kapsayıcı geçerli içeriğini bağlı olarak, sonuçlar şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="ba712-171">and, depending on the current contents of your container, the results look like this:</span></span>

```console
Block blob of length 4: https://<accountname>.blob.core.windows.net/photos/2015/architecture/description.txt
Block blob of length 314618: https://<accountname>.blob.core.windows.net/photos/2015/architecture/photo3.jpg
Block blob of length 522713: https://<accountname>.blob.core.windows.net/photos/2015/architecture/photo4.jpg
Block blob of length 4: https://<accountname>.blob.core.windows.net/photos/2016/architecture/description.txt
Block blob of length 419048: https://<accountname>.blob.core.windows.net/photos/2016/architecture/photo5.jpg
Block blob of length 506388: https://<accountname>.blob.core.windows.net/photos/2016/architecture/photo6.jpg
Block blob of length 399751: https://<accountname>.blob.core.windows.net/photos/2016/photo7.jpg
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

## <a name="download-blobs"></a><span data-ttu-id="ba712-172">BLOB'ları indirme</span><span class="sxs-lookup"><span data-stu-id="ba712-172">Download blobs</span></span>

<span data-ttu-id="ba712-173">BLOB'ları indirmek için önce bir blob başvurusu alın ve ardından çağırın `DownloadToStream` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ba712-173">To download blobs, first retrieve a blob reference and then call the `DownloadToStream` method.</span></span> <span data-ttu-id="ba712-174">Aşağıdaki örnek kullanır `DownloadToStream` blob içeriklerini sonra yerel bir dosyaya kalıcı bir akış nesnesine aktarmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="ba712-174">The following example uses the `DownloadToStream` method to transfer the blob contents to a stream object that you can then persist to a local file.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L95-L101)]

<span data-ttu-id="ba712-175">Aynı zamanda `DownloadToStream` yöntemi bir blob'u bir metin dizesi olarak içeriğini indirmek için.</span><span class="sxs-lookup"><span data-stu-id="ba712-175">You can also use the `DownloadToStream` method to download the contents of a blob as a text string.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L103-L106)]

## <a name="delete-blobs"></a><span data-ttu-id="ba712-176">BLOB'ları silme</span><span class="sxs-lookup"><span data-stu-id="ba712-176">Delete blobs</span></span>

<span data-ttu-id="ba712-177">Bir blobu silmek için önce bir blob başvurusu alın ve ardından çağıran `Delete` yöntemini.</span><span class="sxs-lookup"><span data-stu-id="ba712-177">To delete a blob, first get a blob reference and then call the `Delete` method on it.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L112-L116)]

## <a name="list-blobs-in-pages-asynchronously"></a><span data-ttu-id="ba712-178">BLOB'ları sayfalarda zaman uyumsuz olarak listeleme</span><span class="sxs-lookup"><span data-stu-id="ba712-178">List blobs in pages asynchronously</span></span>

<span data-ttu-id="ba712-179">Çok sayıda BLOB listeliyorsanız veya bir listeleme işlemi ile dönen sonuç sayısını denetlemek istiyorsanız, sonuç sayfalarında blobları listeleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba712-179">If you are listing a large number of blobs, or you want to control the number of results you return in one listing operation, you can list blobs in pages of results.</span></span> <span data-ttu-id="ba712-180">Böylece yürütme büyük bir sonuç kümesi dönmesini beklerken engellenmeyen Bu örnek sonuç sayfalarında zaman uyumsuz olarak döndürmek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ba712-180">This example shows how to return results in pages asynchronously, so that execution is not blocked while waiting to return a large set of results.</span></span>

<span data-ttu-id="ba712-181">Bu örnek düz bir blob listesi gösterir, ancak ayarlayarak hiyerarşik bir listeleme gerçekleştirebilirsiniz `useFlatBlobListing` parametresinin `ListBlobsSegmentedAsync` yöntemine `false`.</span><span class="sxs-lookup"><span data-stu-id="ba712-181">This example shows a flat blob listing, but you can also perform a hierarchical listing, by setting the `useFlatBlobListing` parameter of the `ListBlobsSegmentedAsync` method to `false`.</span></span>

<span data-ttu-id="ba712-182">Örnek zaman uyumsuz bir yöntem tanımlar kullanarak bir `async` bloğu.</span><span class="sxs-lookup"><span data-stu-id="ba712-182">The sample defines an asynchronous method, using an `async` block.</span></span> <span data-ttu-id="ba712-183">``let!`` Anahtar sözcük listeleme görevi tamamlanana kadar örnek yöntemin yürütme askıya alır.</span><span class="sxs-lookup"><span data-stu-id="ba712-183">The ``let!`` keyword suspends execution of the sample method until the listing task completes.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L122-L160)]

<span data-ttu-id="ba712-184">Biz artık bu zaman uyumsuz yordam aşağıdaki gibi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba712-184">We can now use this asynchronous routine as follows.</span></span> <span data-ttu-id="ba712-185">İlk (Bu öğreticide daha önce oluşturulan yerel dosya kullanarak) bazı sahte veriler karşıya yükleyin.</span><span class="sxs-lookup"><span data-stu-id="ba712-185">First you upload some dummy data (using the local file created earlier in this tutorial).</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L162-L166)]

<span data-ttu-id="ba712-186">Şimdi, yordamını çağırın.</span><span class="sxs-lookup"><span data-stu-id="ba712-186">Now, call the routine.</span></span> <span data-ttu-id="ba712-187">Kullandığınız ``Async.RunSynchronously`` zaman uyumsuz işlemin yürütülmesini zorlamak için.</span><span class="sxs-lookup"><span data-stu-id="ba712-187">You use ``Async.RunSynchronously`` to force the execution of the asynchronous operation.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L168-L168)]

## <a name="writing-to-an-append-blob"></a><span data-ttu-id="ba712-188">Bir ek blobu yazma</span><span class="sxs-lookup"><span data-stu-id="ba712-188">Writing to an append blob</span></span>

<span data-ttu-id="ba712-189">Ek blob, günlük tutma gibi ekleme işlemleri için optimize edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ba712-189">An append blob is optimized for append operations, such as logging.</span></span> <span data-ttu-id="ba712-190">Bir blok blobu gibi bir ek blobu bloklardan oluşur ancak bir ek bloba yeni bir blok eklediğinizde her zaman blobun sonuna eklenir.</span><span class="sxs-lookup"><span data-stu-id="ba712-190">Like a block blob, an append blob is comprised of blocks, but when you add a new block to an append blob, it is always appended to the end of the blob.</span></span> <span data-ttu-id="ba712-191">Güncelleştirilemiyor veya blobdaki mevcut bloğu silinemiyor.</span><span class="sxs-lookup"><span data-stu-id="ba712-191">You cannot update or delete an existing block in an append blob.</span></span> <span data-ttu-id="ba712-192">Bir blok blobu olduğu gibi ek blobun blok kimliği gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="ba712-192">The block IDs for an append blob are not exposed as they are for a block blob.</span></span>

<span data-ttu-id="ba712-193">Her bir ek blobu bloğunda en fazla 4 MB, farklı bir boyutta olabilir ve bir ek blobu en fazla 50.000 blok içerebilir.</span><span class="sxs-lookup"><span data-stu-id="ba712-193">Each block in an append blob can be a different size, up to a maximum of 4 MB, and an append blob can include a maximum of 50,000 blocks.</span></span> <span data-ttu-id="ba712-194">Bu nedenle bir ek blobu en büyük boyutu 195 GB'den biraz fazladır (4 MB X 50.000 blok) ' dir.</span><span class="sxs-lookup"><span data-stu-id="ba712-194">The maximum size of an append blob is therefore slightly more than 195 GB (4 MB X 50,000 blocks).</span></span>

<span data-ttu-id="ba712-195">Aşağıdaki örnek yeni bir ek blob oluşturur ve bazı verileri, bir basit günlük yazma işlemini benzeterek ekler.</span><span class="sxs-lookup"><span data-stu-id="ba712-195">The following example creates a new append blob and appends some data to it, simulating a simple logging operation.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L174-L203)]

<span data-ttu-id="ba712-196">Bkz: [anlama blok Blobları, sayfa Blobları ve ek Bloblarını](https://msdn.microsoft.com/library/azure/ee691964.aspx) üç BLOB türü arasındaki farklar hakkında daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="ba712-196">See [Understanding Block Blobs, Page Blobs, and Append Blobs](https://msdn.microsoft.com/library/azure/ee691964.aspx) for more information about the differences between the three types of blobs.</span></span>

## <a name="concurrent-access"></a><span data-ttu-id="ba712-197">Eş zamanlı erişim</span><span class="sxs-lookup"><span data-stu-id="ba712-197">Concurrent access</span></span>

<span data-ttu-id="ba712-198">Eş zamanlı erişim bir blob'a birden çok istemciden veya birden çok örneği desteklemek için kullanabileceğiniz **Etag'ler** veya **kiraları**.</span><span class="sxs-lookup"><span data-stu-id="ba712-198">To support concurrent access to a blob from multiple clients or multiple process instances, you can use **ETags** or **leases**.</span></span>

* <span data-ttu-id="ba712-199">**ETag** -blob veya kapsayıcı başka bir işlem tarafından değiştirilmiş algılamak için bir yol sağlar</span><span class="sxs-lookup"><span data-stu-id="ba712-199">**Etag** - provides a way to detect that the blob or container has been modified by another process</span></span>

* <span data-ttu-id="ba712-200">**Kira** -elde özel ve yenilenebilir, yazma erişimi veya bir blob için bir süre silmek için bir yol sağlar</span><span class="sxs-lookup"><span data-stu-id="ba712-200">**Lease** - provides a way to obtain exclusive, renewable, write or delete access to a blob for a period of time</span></span>

<span data-ttu-id="ba712-201">Daha fazla bilgi için bkz: [yönetme eşzamanlılık Microsoft Azure depolama alanında](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).</span><span class="sxs-lookup"><span data-stu-id="ba712-201">For more information, see [Managing Concurrency in Microsoft Azure Storage](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).</span></span>

## <a name="naming-containers"></a><span data-ttu-id="ba712-202">Kapsayıcı adlandırma</span><span class="sxs-lookup"><span data-stu-id="ba712-202">Naming containers</span></span>

<span data-ttu-id="ba712-203">Azure depolama her blob bir kapsayıcıda yer almalıdır.</span><span class="sxs-lookup"><span data-stu-id="ba712-203">Every blob in Azure storage must reside in a container.</span></span> <span data-ttu-id="ba712-204">Kapsayıcı, blob adı bölümü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ba712-204">The container forms part of the blob name.</span></span> <span data-ttu-id="ba712-205">Örneğin, `mydata` Bu örnek blob Urı'lerinde kapsayıcısında adıdır:</span><span class="sxs-lookup"><span data-stu-id="ba712-205">For example, `mydata` is the name of the container in these sample blob URIs:</span></span>

    https://storagesample.blob.core.windows.net/mydata/blob1.txt
    https://storagesample.blob.core.windows.net/mydata/photos/myphoto.jpg

<span data-ttu-id="ba712-206">Bir kapsayıcı adı aşağıdaki adlandırma kurallarına uygun geçerli bir DNS adı olması gerekir:</span><span class="sxs-lookup"><span data-stu-id="ba712-206">A container name must be a valid DNS name, conforming to the following naming rules:</span></span>

1. <span data-ttu-id="ba712-207">Kapsayıcı adları bir harf veya sayı ile başlamalı ve yalnızca harf, rakam ve tire (-) karakterini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="ba712-207">Container names must start with a letter or number, and can contain only letters, numbers, and the dash (-) character.</span></span>
1. <span data-ttu-id="ba712-208">Her tire (-) karakterinden hemen önce ve bir harf veya sayı gelmelidir gerekir; kapsayıcı adlarında art arda tirelere izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="ba712-208">Every dash (-) character must be immediately preceded and followed by a letter or number; consecutive dashes are not permitted in container names.</span></span>
1. <span data-ttu-id="ba712-209">Kapsayıcı adındaki tüm harfler küçük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ba712-209">All letters in a container name must be lowercase.</span></span>
1. <span data-ttu-id="ba712-210">Kapsayıcı adları 3-63 karakter uzunluğunda olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ba712-210">Container names must be from 3 through 63 characters long.</span></span>

<span data-ttu-id="ba712-211">Kapsayıcı adının her zaman küçük harfli olması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ba712-211">Note that the name of a container must always be lowercase.</span></span> <span data-ttu-id="ba712-212">Kapsayıcı adına bir büyük harf eklemek ya da aksi takdirde kapsayıcı adlandırma kurallarını ihlal 400 hatası (Hatalı istek) alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba712-212">If you include an upper-case letter in a container name, or otherwise violate the container naming rules, you may receive a 400 error (Bad Request).</span></span>

## <a name="managing-security-for-blobs"></a><span data-ttu-id="ba712-213">Blobların güvenliğini sağlama</span><span class="sxs-lookup"><span data-stu-id="ba712-213">Managing security for blobs</span></span>

<span data-ttu-id="ba712-214">Varsayılan olarak, Azure depolama, verilerinizi hesabı erişim anahtarlarını elinde olan hesap sahibi erişimi kısıtlayarak güvende tutar.</span><span class="sxs-lookup"><span data-stu-id="ba712-214">By default, Azure Storage keeps your data secure by limiting access to the account owner, who is in possession of the account access keys.</span></span> <span data-ttu-id="ba712-215">Depolama hesabınızda blob verileri paylaşmanız gerektiğinde bunu hesap erişim tuşlarınızı güvenliği tehlikeye atmadan yapmak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="ba712-215">When you need to share blob data in your storage account, it is important to do so without compromising the security of your account access keys.</span></span> <span data-ttu-id="ba712-216">Ayrıca, Azure storage'da ve kablo üzerinden giderek güvenli olduğundan emin olmak için blob verilerini şifreleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba712-216">Additionally, you can encrypt blob data to ensure that it is secure going over the wire and in Azure Storage.</span></span>

### <a name="controlling-access-to-blob-data"></a><span data-ttu-id="ba712-217">Blob verilerine erişimi denetleme</span><span class="sxs-lookup"><span data-stu-id="ba712-217">Controlling access to blob data</span></span>

<span data-ttu-id="ba712-218">Varsayılan olarak, depolama hesabınızda blob verileri yalnızca depolama hesabı sahibi erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="ba712-218">By default, the blob data in your storage account is accessible only to storage account owner.</span></span> <span data-ttu-id="ba712-219">Blob Storage'a karşı istek kimlik doğrulaması varsayılan olarak hesap erişim tuşu gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ba712-219">Authenticating requests against Blob storage requires the account access key by default.</span></span> <span data-ttu-id="ba712-220">Ancak, çeşitli blob verilerinin diğer kullanıcılar tarafından kullanılabilmesini sağlamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba712-220">However, you might want to make certain blob data available to other users.</span></span>

<span data-ttu-id="ba712-221">Blob depolama erişimi denetleme hakkında daha fazla bilgi için bkz: [blob depolama bölümü için .NET Kılavuzu erişim denetimi hakkında](/azure/storage/storage-dotnet-how-to-use-blobs#controlling-access-to-blob-data).</span><span class="sxs-lookup"><span data-stu-id="ba712-221">For details on how to control access to blob storage, see [the .NET guide for blob storage section on access control](/azure/storage/storage-dotnet-how-to-use-blobs#controlling-access-to-blob-data).</span></span>


### <a name="encrypting-blob-data"></a><span data-ttu-id="ba712-222">BLOB verilerini şifreleme</span><span class="sxs-lookup"><span data-stu-id="ba712-222">Encrypting blob data</span></span>

<span data-ttu-id="ba712-223">Azure Storage hem istemci hem de sunucuda blob verisi şifreleme destekler.</span><span class="sxs-lookup"><span data-stu-id="ba712-223">Azure Storage supports encrypting blob data both at the client and on the server.</span></span>

<span data-ttu-id="ba712-224">Blob verilerini şifreleme hakkında daha fazla bilgi için bkz: [blob depolama bölümü şifrelemesi için .NET Kılavuzu](/azure/storage/storage-dotnet-how-to-use-blobs#encrypting-blob-data).</span><span class="sxs-lookup"><span data-stu-id="ba712-224">For details on encrypting blob data, see [the .NET guide for blob storage section on encryption](/azure/storage/storage-dotnet-how-to-use-blobs#encrypting-blob-data).</span></span>

## <a name="next-steps"></a><span data-ttu-id="ba712-225">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="ba712-225">Next steps</span></span>

<span data-ttu-id="ba712-226">Blob storage'nın öğrendiğinize göre daha fazla bilgi için aşağıdaki bağlantıları izleyin.</span><span class="sxs-lookup"><span data-stu-id="ba712-226">Now that you've learned the basics of Blob storage, follow these links to learn more.</span></span>

### <a name="tools"></a><span data-ttu-id="ba712-227">Araçlar</span><span class="sxs-lookup"><span data-stu-id="ba712-227">Tools</span></span>
- <span data-ttu-id="ba712-228">[F # AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/) bir F # tür Blob, tablo ve kuyruk Azure depolama varlıklar keşfetmek ve bunları CRUD işlemleri kolayca uygulamak için kullanılan sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="ba712-228">[F# AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/) An F# Type Provider which can be used to explore Blob, Table and Queue Azure Storage assets and easily apply CRUD operations on them.</span></span>
- <span data-ttu-id="ba712-229">[FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage) bir F # Microsoft Azure Table Storage hizmeti kullandığınız için API</span><span class="sxs-lookup"><span data-stu-id="ba712-229">[FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage) An F# API for using Microsoft Azure Table Storage service</span></span>
- <span data-ttu-id="ba712-230">[Microsoft Azure Depolama Gezgini (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer) görsel olarak Azure Storage ile Windows, OS X ve Linux üzerinde çalışmanıza olanak tanır Microsoft'tan ücretsiz, bir tek başına uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="ba712-230">[Microsoft Azure Storage Explorer (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer) is a free, standalone app from Microsoft that enables you to work visually with Azure Storage data on Windows, OS X, and Linux.</span></span>

### <a name="blob-storage-reference"></a><span data-ttu-id="ba712-231">BLOB Depolama başvurusu</span><span class="sxs-lookup"><span data-stu-id="ba712-231">Blob storage reference</span></span>

- [<span data-ttu-id="ba712-232">.NET için Azure depolama API'leri</span><span class="sxs-lookup"><span data-stu-id="ba712-232">Azure Storage APIs for .NET</span></span>](/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="ba712-233">Azure Storage Hizmetleri REST API Başvurusu</span><span class="sxs-lookup"><span data-stu-id="ba712-233">Azure Storage Services REST API Reference</span></span>](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)

### <a name="related-guides"></a><span data-ttu-id="ba712-234">İlgili kılavuzları</span><span class="sxs-lookup"><span data-stu-id="ba712-234">Related guides</span></span>

- [<span data-ttu-id="ba712-235">Azure Blob Depolama C# kullanmaya Başlarken</span><span class="sxs-lookup"><span data-stu-id="ba712-235">Getting Started with Azure Blob Storage in C#</span></span>](https://azure.microsoft.com/resources/samples/storage-blob-dotnet-getting-started/)
- [<span data-ttu-id="ba712-236">Windows üzerinde AzCopy komut satırı yardımcı programı ile veri aktarımı</span><span class="sxs-lookup"><span data-stu-id="ba712-236">Transfer data with the AzCopy command-line utility on Windows</span></span>](/azure/storage/common/storage-use-azcopy)
- [<span data-ttu-id="ba712-237">Linux'ta AzCopy komut satırı yardımcı programı ile veri aktarımı</span><span class="sxs-lookup"><span data-stu-id="ba712-237">Transfer data with the AzCopy command-line utility on Linux</span></span>](/azure/storage/common/storage-use-azcopy-linux)
- [<span data-ttu-id="ba712-238">Azure Storage bağlantı dizelerini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ba712-238">Configure Azure Storage connection strings</span></span>](/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="ba712-239">Azure depolama ekibi blogu</span><span class="sxs-lookup"><span data-stu-id="ba712-239">Azure Storage Team Blog</span></span>](https://blogs.msdn.microsoft.com/windowsazurestorage/)
