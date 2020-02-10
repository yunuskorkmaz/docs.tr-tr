---
title: F# kullanarak Azure Blob depolama kullanmaya başlama
description: Azure Blob depolama ile yapılandırılmamış verileri bulutta depolayın.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 79f6a559ac603b0544916764126a988d3f3f43d7
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77092635"
---
# <a name="get-started-with-azure-blob-storage-using-f"></a><span data-ttu-id="a0d6d-103">F\# kullanarak Azure Blob depolama ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="a0d6d-103">Get started with Azure Blob storage using F\#</span></span>

<span data-ttu-id="a0d6d-104">Azure Blob Storage, bulutta nesne/blob olarak yapılandırılmamış veri depolayan bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-104">Azure Blob storage is a service that stores unstructured data in the cloud as objects/blobs.</span></span> <span data-ttu-id="a0d6d-105">Blob Storage belge, medya dosyası veya uygulama yükleyici gibi her tür metin veya ikili veri depolayabilir.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-105">Blob storage can store any type of text or binary data, such as a document, media file, or application installer.</span></span> <span data-ttu-id="a0d6d-106">Blob Storage aynı zamanda nesne depolama olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-106">Blob storage is also referred to as object storage.</span></span>

<span data-ttu-id="a0d6d-107">Bu makalede, blob depolamayı kullanarak genel görevlerin nasıl gerçekleştirileceği gösterilir.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-107">This article shows you how to perform common tasks using Blob storage.</span></span> <span data-ttu-id="a0d6d-108">Örnekler, .NET için Azure F# Storage istemci kitaplığı kullanılarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-108">The samples are written using F# using the Azure Storage Client Library for .NET.</span></span> <span data-ttu-id="a0d6d-109">Kapsanan görevler, Blobları karşıya yükleme, listeleme, indirme ve silme işlemleri içerir.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-109">The tasks covered include how to upload, list, download, and delete blobs.</span></span>

<span data-ttu-id="a0d6d-110">Blob depolamaya kavramsal bir genel bakış için bkz. [BLOB depolama için .net Kılavuzu](/azure/storage/blobs/storage-quickstart-blobs-dotnet).</span><span class="sxs-lookup"><span data-stu-id="a0d6d-110">For a conceptual overview of blob storage, see [the .NET guide for blob storage](/azure/storage/blobs/storage-quickstart-blobs-dotnet).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a0d6d-111">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="a0d6d-111">Prerequisites</span></span>

<span data-ttu-id="a0d6d-112">Bu kılavuzu kullanmak için önce [bir Azure depolama hesabı oluşturmanız](/azure/storage/common/storage-account-create)gerekir.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-112">To use this guide, you must first [create an Azure storage account](/azure/storage/common/storage-account-create).</span></span> <span data-ttu-id="a0d6d-113">Bu hesap için depolama erişim anahtarınıza de ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-113">You also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="a0d6d-114">F# Betik oluşturma ve etkileşimli başlatma F#</span><span class="sxs-lookup"><span data-stu-id="a0d6d-114">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="a0d6d-115">Bu makaledeki örnekler, bir F# uygulama ya da bir F# komut dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-115">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="a0d6d-116">F# Betik oluşturmak için, F# geliştirme ortamınızda `.fsx` uzantılı bir dosya oluşturun (örneğin `blobs.fsx`).</span><span class="sxs-lookup"><span data-stu-id="a0d6d-116">To create an F# script, create a file with the `.fsx` extension, for example `blobs.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="a0d6d-117">Daha sonra, `WindowsAzure.Storage` yüklemek için Paket Yöneticisi [veya](https://fsprojects.github.io/Paket/) [NuGet](https://www.nuget.org/) gibi bir [paket yöneticisi](package-management.md) kullanın ve bir `#r` yönergesi kullanarak betiğe `WindowsAzure.Storage.dll` ve `Microsoft.WindowsAzure.Configuration.dll` `Microsoft.WindowsAzure.ConfigurationManager` paketleri ve başvuruları yapın.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-117">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` and `Microsoft.WindowsAzure.ConfigurationManager` packages and reference `WindowsAzure.Storage.dll` and `Microsoft.WindowsAzure.Configuration.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="a0d6d-118">Ad alanı bildirimleri ekleme</span><span class="sxs-lookup"><span data-stu-id="a0d6d-118">Add namespace declarations</span></span>

<span data-ttu-id="a0d6d-119">Aşağıdaki `open` bildirimlerini `blobs.fsx` dosyasının üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a0d6d-119">Add the following `open` statements to the top of the `blobs.fsx` file:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a><span data-ttu-id="a0d6d-120">Bağlantı dizenizi alma</span><span class="sxs-lookup"><span data-stu-id="a0d6d-120">Get your connection string</span></span>

<span data-ttu-id="a0d6d-121">Bu öğretici için bir Azure depolama bağlantı dizesine ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-121">You need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="a0d6d-122">Bağlantı dizeleri hakkında daha fazla bilgi için bkz. [depolama bağlantı dizelerini yapılandırma](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="a0d6d-122">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="a0d6d-123">Öğreticide, Bağlantı dizenizi aşağıdaki gibi bir betiğe girersiniz:</span><span class="sxs-lookup"><span data-stu-id="a0d6d-123">For the tutorial, you enter your connection string in your script, like this:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L11-L11)]

<span data-ttu-id="a0d6d-124">Ancak, bu gerçek projeler için **önerilmez** .</span><span class="sxs-lookup"><span data-stu-id="a0d6d-124">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="a0d6d-125">Depolama hesabı anahtarınız depolama hesabınızın kök parolasına benzer.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-125">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="a0d6d-126">Depolama hesabı anahtarınızı korumak için her zaman özen gösterin.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-126">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="a0d6d-127">Diğer kullanıcılara dağıtmaktan, sabit kodlamaktan ve başkalarının erişebileceği düz metin dosyasına kaydetmekten kaçının.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-127">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="a0d6d-128">Güvenliğinin tehlikede olduğunu düşünüyorsanız, Azure portalını kullanarak anahtarınızı yeniden oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-128">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="a0d6d-129">Gerçek uygulamalar için, depolama Bağlantı dizenizi korumak için en iyi yol bir yapılandırma dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-129">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="a0d6d-130">Bağlantı dizesini bir yapılandırma dosyasından getirmek için şunu yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a0d6d-130">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L13-L15)]

<span data-ttu-id="a0d6d-131">Azure Yapılandırma Yöneticisi'ni kullanmak isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-131">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="a0d6d-132">.NET Framework `ConfigurationManager` türü gibi bir API de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-132">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="a0d6d-133">Bağlantı dizesini ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="a0d6d-133">Parse the connection string</span></span>

<span data-ttu-id="a0d6d-134">Bağlantı dizesini ayrıştırmak için şunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="a0d6d-134">To parse the connection string, use:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L21-L22)]

<span data-ttu-id="a0d6d-135">Bu, bir `CloudStorageAccount`döndürür.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-135">This returns a `CloudStorageAccount`.</span></span>

### <a name="create-some-local-dummy-data"></a><span data-ttu-id="a0d6d-136">Bazı yerel kukla veriler oluşturma</span><span class="sxs-lookup"><span data-stu-id="a0d6d-136">Create some local dummy data</span></span>

<span data-ttu-id="a0d6d-137">Başlamadan önce, betiğimizin dizininde bazı sözde yerel veriler oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-137">Before you begin, create some dummy local data in the directory of our script.</span></span> <span data-ttu-id="a0d6d-138">Daha sonra bu verileri karşıya yüklersiniz.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-138">Later you upload this data.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L28-L30)]

### <a name="create-the-blob-service-client"></a><span data-ttu-id="a0d6d-139">Blob hizmeti istemcisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="a0d6d-139">Create the Blob service client</span></span>

<span data-ttu-id="a0d6d-140">`CloudBlobClient` türü, blob depolamada depolanan kapsayıcıları ve Blobları almanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-140">The `CloudBlobClient` type enables you to retrieve containers and blobs stored in Blob storage.</span></span> <span data-ttu-id="a0d6d-141">Hizmet istemcisini oluşturma yöntemlerinden biri aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="a0d6d-141">Here's one way to create the service client:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L36-L36)]

<span data-ttu-id="a0d6d-142">Artık Blob Storage’da n veri okuyan ve bu depolamaya veri yazan kodu yazmaya hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-142">Now you are ready to write code that reads data from and writes data to Blob storage.</span></span>

## <a name="create-a-container"></a><span data-ttu-id="a0d6d-143">Bir kapsayıcı oluşturma</span><span class="sxs-lookup"><span data-stu-id="a0d6d-143">Create a container</span></span>

<span data-ttu-id="a0d6d-144">Bu örnek, zaten yoksa, nasıl bir kapsayıcı oluşturulacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="a0d6d-144">This example shows how to create a container if it does not already exist:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L42-L46)]

<span data-ttu-id="a0d6d-145">Varsayılan olarak yeni kapsayıcı özeldir, bu kapsayıcıdan blob indirmek için depolama erişim anahtarınızı belirlemeniz gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-145">By default, the new container is private, meaning that you must specify your storage access key to download blobs from this container.</span></span> <span data-ttu-id="a0d6d-146">Kapsayıcı içindeki dosyaların herkese açık olmasını istiyorsanız, aşağıdaki kodu kullanarak kapsayıcıyı herkesin erişimine açık hale getirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a0d6d-146">If you want to make the files within the container available to everyone, you can set the container to be public using the following code:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L48-L49)]

<span data-ttu-id="a0d6d-147">İnternet üzerindeki herkes, herkese açık bir kapsayıcıdaki blobları görebilir ancak uygun hesap erişim tuşu veya paylaşılan erişim imzanız olması durumunda bunları değiştirebilir veya silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-147">Anyone on the Internet can see blobs in a public container, but you can modify or delete them only if you have the appropriate account access key or a shared access signature.</span></span>

## <a name="upload-a-blob-into-a-container"></a><span data-ttu-id="a0d6d-148">Bir kapsayıcıya bir blob yükleme</span><span class="sxs-lookup"><span data-stu-id="a0d6d-148">Upload a blob into a container</span></span>

<span data-ttu-id="a0d6d-149">Azure Blob Storage blok blobları ve sayfa bloblarını destekler.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-149">Azure Blob Storage supports block blobs and page blobs.</span></span> <span data-ttu-id="a0d6d-150">Çoğu durumda, Blok Blobu kullanılacak önerilen türdür.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-150">In most cases, a block blob is the recommended type to use.</span></span>

<span data-ttu-id="a0d6d-151">Bir dosyayı bir blok blobuna yüklemek için bir kapsayıcı başvurusu alın ve blok blob başvurusu almak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-151">To upload a file to a block blob, get a container reference and use it to get a block blob reference.</span></span> <span data-ttu-id="a0d6d-152">Blob başvurunuz olduktan sonra, `UploadFromFile` yöntemini çağırarak herhangi bir veri akışını bu akışa yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-152">Once you have a blob reference, you can upload any stream of data to it by calling the `UploadFromFile` method.</span></span> <span data-ttu-id="a0d6d-153">Bu işlem, daha önce yoksa blobu oluşturur veya varsa üzerine yazar.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-153">This operation creates the blob if it didn't previously exist, or overwrite it if it does exist.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L55-L59)]

## <a name="list-the-blobs-in-a-container"></a><span data-ttu-id="a0d6d-154">Blob’ları bir kapsayıcıda listeleme</span><span class="sxs-lookup"><span data-stu-id="a0d6d-154">List the blobs in a container</span></span>

<span data-ttu-id="a0d6d-155">Blob’ları bir kapsayıcıda listelemek için ilk olarak bir kapsayıcı başvurusu edinin.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-155">To list the blobs in a container, first get a container reference.</span></span> <span data-ttu-id="a0d6d-156">Daha sonra kapsayıcının `ListBlobs` yöntemini kullanarak Blobları ve/veya dizinleri elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-156">You can then use the container's `ListBlobs` method to retrieve the blobs and/or directories within it.</span></span> <span data-ttu-id="a0d6d-157">Döndürülen bir `IListBlobItem`için zengin özellik ve yöntemlere erişmek için, bunu bir `CloudBlockBlob`, `CloudPageBlob`veya `CloudBlobDirectory` nesnesine dönüştürmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-157">To access the rich set of properties and methods for a returned `IListBlobItem`, you must cast it to a `CloudBlockBlob`, `CloudPageBlob`, or `CloudBlobDirectory` object.</span></span> <span data-ttu-id="a0d6d-158">Tür bilinmiyorsa, hangisine yayınlayacağınızı belirlemek için bir tür denetimi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-158">If the type is unknown, you can use a type check to determine which to cast it to.</span></span> <span data-ttu-id="a0d6d-159">Aşağıdaki kod, `mydata` kapsayıcıdaki her nesnenin URI’nın nasıl alınacağını ve çıkacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="a0d6d-159">The following code demonstrates how to retrieve and output the URI of each item in the `mydata` container:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L67-L80)]

<span data-ttu-id="a0d6d-160">Bloblarını adlarına yol bilgileriyle de girebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-160">You can also name blobs with path information in their names.</span></span> <span data-ttu-id="a0d6d-161">Bu, geleneksel bir dosya sisteminde olduğu gibi düzenleme ve geçiş yapabileceğiniz sanal bir dizin yapısı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-161">This creates a virtual directory structure that you can organize and traverse as you would a traditional file system.</span></span> <span data-ttu-id="a0d6d-162">Dizin yapısının yalnızca sanal olduğunu unutmayın; Blob Storage’da  kullanılabilecek kaynaklar kapsayıcılar ve bloblardır.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-162">Note that the directory structure is virtual only - the only resources available in Blob storage are containers and blobs.</span></span> <span data-ttu-id="a0d6d-163">Ancak, depolama istemci kitaplığı bir sanal dizine başvuracak bir `CloudBlobDirectory` nesnesi sunar ve bu şekilde düzenlenmiş bloblarla çalışma sürecini basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-163">However, the storage client library offers a `CloudBlobDirectory` object to refer to a virtual directory and simplify the process of working with blobs that are organized in this way.</span></span>

<span data-ttu-id="a0d6d-164">Örneğin bir kapsayıcıda yer alan ve `photos` olarak adlandırılan aşağıdaki blok blobları kümesine göz atın:</span><span class="sxs-lookup"><span data-stu-id="a0d6d-164">For example, consider the following set of block blobs in a container named `photos`:</span></span>

<span data-ttu-id="a0d6d-165">*photo1. jpg*</span><span class="sxs-lookup"><span data-stu-id="a0d6d-165">*photo1.jpg*</span></span>\
<span data-ttu-id="a0d6d-166">*2015/mimari/Description. txt*</span><span class="sxs-lookup"><span data-stu-id="a0d6d-166">*2015/architecture/description.txt*</span></span>\
<span data-ttu-id="a0d6d-167">*2015/Architecture/photo3. jpg*</span><span class="sxs-lookup"><span data-stu-id="a0d6d-167">*2015/architecture/photo3.jpg*</span></span>\
<span data-ttu-id="a0d6d-168">*2015/Architecture/photo4. jpg*</span><span class="sxs-lookup"><span data-stu-id="a0d6d-168">*2015/architecture/photo4.jpg*</span></span>\
<span data-ttu-id="a0d6d-169">*2016/Architecture/photo5. jpg*</span><span class="sxs-lookup"><span data-stu-id="a0d6d-169">*2016/architecture/photo5.jpg*</span></span>\
<span data-ttu-id="a0d6d-170">*2016/Architecture/photo6. jpg*</span><span class="sxs-lookup"><span data-stu-id="a0d6d-170">*2016/architecture/photo6.jpg*</span></span>\
<span data-ttu-id="a0d6d-171">*2016/mimari/Description. txt*</span><span class="sxs-lookup"><span data-stu-id="a0d6d-171">*2016/architecture/description.txt*</span></span>\
<span data-ttu-id="a0d6d-172">*2016/photo7. jpg*</span><span class="sxs-lookup"><span data-stu-id="a0d6d-172">*2016/photo7.jpg*</span></span>\

<span data-ttu-id="a0d6d-173">Bir kapsayıcıda `ListBlobs` çağırdığınızda (Yukarıdaki örnekte olduğu gibi), hiyerarşik bir liste döndürülür.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-173">When you call `ListBlobs` on a container (as in the above sample), a hierarchical listing is returned.</span></span> <span data-ttu-id="a0d6d-174">Hem `CloudBlobDirectory` hem de `CloudBlockBlob` nesneleri içeriyorsa, kapsayıcıda dizin ve Blobları temsil eder, sonuçta elde edilen çıktı şuna benzer:</span><span class="sxs-lookup"><span data-stu-id="a0d6d-174">If it contains both `CloudBlobDirectory` and `CloudBlockBlob` objects, representing the directories and blobs in the container, respectively, then the resulting output looks similar to this:</span></span>

```console
Directory: https://<accountname>.blob.core.windows.net/photos/2015/
Directory: https://<accountname>.blob.core.windows.net/photos/2016/
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

<span data-ttu-id="a0d6d-175">İsteğe bağlı olarak, `ListBlobs` yönteminin `UseFlatBlobListing` parametresini `true`olarak ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-175">Optionally, you can set the `UseFlatBlobListing` parameter of the `ListBlobs` method to `true`.</span></span> <span data-ttu-id="a0d6d-176">Bu durumda, kapsayıcıdaki her blob bir `CloudBlockBlob` nesne olarak döndürülür.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-176">In this case, every blob in the container is returned as a `CloudBlockBlob` object.</span></span> <span data-ttu-id="a0d6d-177">Düz bir liste döndürmek için `ListBlobs` çağrısı şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="a0d6d-177">The call to `ListBlobs` to return a flat listing looks like this:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L82-L89)]

<span data-ttu-id="a0d6d-178">kapsayıcının geçerli içeriğine bağlı olarak, sonuçlar şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="a0d6d-178">and, depending on the current contents of your container, the results look like this:</span></span>

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

## <a name="download-blobs"></a><span data-ttu-id="a0d6d-179">Blob’ları indirme</span><span class="sxs-lookup"><span data-stu-id="a0d6d-179">Download blobs</span></span>

<span data-ttu-id="a0d6d-180">Blob 'ları indirmek için önce bir blob başvurusu alın ve ardından `DownloadToStream` yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-180">To download blobs, first retrieve a blob reference and then call the `DownloadToStream` method.</span></span> <span data-ttu-id="a0d6d-181">Aşağıdaki örnek, blob içeriğini bir akış nesnesine aktarmak için `DownloadToStream` yöntemini kullanır ve böylece yerel bir dosyaya devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-181">The following example uses the `DownloadToStream` method to transfer the blob contents to a stream object that you can then persist to a local file.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L95-L101)]

<span data-ttu-id="a0d6d-182">Bir Blobun içeriğini bir metin dizesi olarak indirmek için `DownloadToStream` yöntemini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-182">You can also use the `DownloadToStream` method to download the contents of a blob as a text string.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L103-L106)]

## <a name="delete-blobs"></a><span data-ttu-id="a0d6d-183">Blob’ları silme</span><span class="sxs-lookup"><span data-stu-id="a0d6d-183">Delete blobs</span></span>

<span data-ttu-id="a0d6d-184">Bir blobu silmek için önce bir blob başvurusu alın ve ardından `Delete` yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-184">To delete a blob, first get a blob reference and then call the `Delete` method on it.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L112-L116)]

## <a name="list-blobs-in-pages-asynchronously"></a><span data-ttu-id="a0d6d-185">Blob’ları sayfalarda zaman uyumsuz olarak listeleme</span><span class="sxs-lookup"><span data-stu-id="a0d6d-185">List blobs in pages asynchronously</span></span>

<span data-ttu-id="a0d6d-186">Çok sayıda blob listeliyorsanız veya bir listeleme işlemi ile dönen sonuç sayısını denetlemek isterseniz sonuç sayfalarında blobları listeleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-186">If you are listing a large number of blobs, or you want to control the number of results you return in one listing operation, you can list blobs in pages of results.</span></span> <span data-ttu-id="a0d6d-187">Bu örnek, geniş bir sonuç kümesinin dönmesini beklerken çalıştırmanın engellenmemesi için sayfalardaki sonuçların zaman uyumsuz olarak nasıl döneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-187">This example shows how to return results in pages asynchronously, so that execution is not blocked while waiting to return a large set of results.</span></span>

<span data-ttu-id="a0d6d-188">Bu örnekte düz bir blob listesi gösterilmektedir, ancak `ListBlobsSegmentedAsync` yönteminin `useFlatBlobListing` parametresini `false`olarak ayarlayarak hiyerarşik bir liste da gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-188">This example shows a flat blob listing, but you can also perform a hierarchical listing, by setting the `useFlatBlobListing` parameter of the `ListBlobsSegmentedAsync` method to `false`.</span></span>

<span data-ttu-id="a0d6d-189">Örnek, `async` bloğu kullanarak zaman uyumsuz bir yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-189">The sample defines an asynchronous method, using an `async` block.</span></span> <span data-ttu-id="a0d6d-190">``let!`` anahtar sözcüğü, listeleme görevi tamamlanana kadar örnek yöntemi yürütmeyi askıya alır.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-190">The ``let!`` keyword suspends execution of the sample method until the listing task completes.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L122-L160)]

<span data-ttu-id="a0d6d-191">Artık bu zaman uyumsuz yordamı aşağıdaki gibi kullanabiliriz.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-191">We can now use this asynchronous routine as follows.</span></span> <span data-ttu-id="a0d6d-192">İlk olarak bazı kukla verileri karşıya yüklersiniz (Bu öğreticide daha önce oluşturulan yerel dosyayı kullanarak).</span><span class="sxs-lookup"><span data-stu-id="a0d6d-192">First you upload some dummy data (using the local file created earlier in this tutorial).</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L162-L166)]

<span data-ttu-id="a0d6d-193">Şimdi, yordamını çağırın.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-193">Now, call the routine.</span></span> <span data-ttu-id="a0d6d-194">Zaman uyumsuz işlemin yürütülmesini zorlamak için `Async.RunSynchronously` kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-194">You use `Async.RunSynchronously` to force the execution of the asynchronous operation.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L168-L168)]

## <a name="writing-to-an-append-blob"></a><span data-ttu-id="a0d6d-195">Ek blobu yazma</span><span class="sxs-lookup"><span data-stu-id="a0d6d-195">Writing to an append blob</span></span>

<span data-ttu-id="a0d6d-196">Ek blob, günlük tutma gibi ekleme işlemleri için en iyi duruma getirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-196">An append blob is optimized for append operations, such as logging.</span></span> <span data-ttu-id="a0d6d-197">Blok blobuna benzer şekilde bir ek blobu bloklardan oluşur ancak bir ek bloba yeni bir blok eklediğinizde her zaman blobun sonuna eklenir.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-197">Like a block blob, an append blob is comprised of blocks, but when you add a new block to an append blob, it is always appended to the end of the blob.</span></span> <span data-ttu-id="a0d6d-198">Bir ek blobdaki mevcut bloğu güncelleştiremezsiniz veya silemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-198">You cannot update or delete an existing block in an append blob.</span></span> <span data-ttu-id="a0d6d-199">Bir blok blobu olduğu için ek blobun blok kimliği gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-199">The block IDs for an append blob are not exposed as they are for a block blob.</span></span>

<span data-ttu-id="a0d6d-200">Her biri en fazla 4 MB olmak üzere bir ek blobundaki her blok farklı boyutlarda olabilir ve bir ek blobu en fazla 50.000 blok içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-200">Each block in an append blob can be a different size, up to a maximum of 4 MB, and an append blob can include a maximum of 50,000 blocks.</span></span> <span data-ttu-id="a0d6d-201">Bu nedenle bir ek blobunun en büyük boyutu 195 GB’den biraz fazladır (4 MB x 50.000 blok).</span><span class="sxs-lookup"><span data-stu-id="a0d6d-201">The maximum size of an append blob is therefore slightly more than 195 GB (4 MB X 50,000 blocks).</span></span>

<span data-ttu-id="a0d6d-202">Aşağıdaki örnek, yeni bir ekleme blobu oluşturur ve basit bir günlüğe kaydetme işleminin benzetimini yapar ve buna veri ekler.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-202">The following example creates a new append blob and appends some data to it, simulating a simple logging operation.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L174-L203)]

<span data-ttu-id="a0d6d-203">Üç blob türü arasındaki farklar hakkında bilgi edinmek için bkz. [Blok Blobları, Sayfa Blobları ve Ek Bloblarını anlama](https://msdn.microsoft.com/library/azure/ee691964.aspx).</span><span class="sxs-lookup"><span data-stu-id="a0d6d-203">See [Understanding Block Blobs, Page Blobs, and Append Blobs](https://msdn.microsoft.com/library/azure/ee691964.aspx) for more information about the differences between the three types of blobs.</span></span>

## <a name="concurrent-access"></a><span data-ttu-id="a0d6d-204">Eşzamanlı erişim</span><span class="sxs-lookup"><span data-stu-id="a0d6d-204">Concurrent access</span></span>

<span data-ttu-id="a0d6d-205">Birden fazla istemciden veya birden çok işlem örneğiyle bir Blobun eşzamanlı erişimini desteklemek için **ETags** veya **kiralamalar**kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-205">To support concurrent access to a blob from multiple clients or multiple process instances, you can use **ETags** or **leases**.</span></span>

- <span data-ttu-id="a0d6d-206">**ETag** -Blobun veya kapsayıcının başka bir işlem tarafından değiştirildiğini algılamaya yönelik bir yol sağlar</span><span class="sxs-lookup"><span data-stu-id="a0d6d-206">**Etag** - provides a way to detect that the blob or container has been modified by another process</span></span>

- <span data-ttu-id="a0d6d-207">**Kira** -bir zaman dilimi için bir Blobun özel, yenilenebilir, yazma veya silme erişimi elde etmek için bir yol sağlar</span><span class="sxs-lookup"><span data-stu-id="a0d6d-207">**Lease** - provides a way to obtain exclusive, renewable, write or delete access to a blob for a period of time</span></span>

<span data-ttu-id="a0d6d-208">Daha fazla bilgi için bkz. [Microsoft Azure depolama eşzamanlılık yönetimi](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).</span><span class="sxs-lookup"><span data-stu-id="a0d6d-208">For more information, see [Managing Concurrency in Microsoft Azure Storage](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).</span></span>

## <a name="naming-containers"></a><span data-ttu-id="a0d6d-209">Kapsayıcıları adlandırma</span><span class="sxs-lookup"><span data-stu-id="a0d6d-209">Naming containers</span></span>

<span data-ttu-id="a0d6d-210">Azure Storage’daki her blob bir kapsayıcıda yer almalıdır.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-210">Every blob in Azure storage must reside in a container.</span></span> <span data-ttu-id="a0d6d-211">Kapsayıcı, blob adının bir bölümünü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-211">The container forms part of the blob name.</span></span> <span data-ttu-id="a0d6d-212">Örneğin, bu örnek blob URI’lerinde `mydata` kapsayıcının adıdır:</span><span class="sxs-lookup"><span data-stu-id="a0d6d-212">For example, `mydata` is the name of the container in these sample blob URIs:</span></span>

- `https://storagesample.blob.core.windows.net/mydata/blob1.txt`
- `https://storagesample.blob.core.windows.net/mydata/photos/myphoto.jpg`

<span data-ttu-id="a0d6d-213">Kapsayıcı adı, aşağıdaki adlandırma kurallarına uygun geçerli bir DNS adı olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="a0d6d-213">A container name must be a valid DNS name, conforming to the following naming rules:</span></span>

1. <span data-ttu-id="a0d6d-214">Kapsayıcı adları bir harf veya rakamla başlamalıdır; yalnızca harf, rakam ve tire (-) karakterinden oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-214">Container names must start with a letter or number, and can contain only letters, numbers, and the dash (-) character.</span></span>
1. <span data-ttu-id="a0d6d-215">Her tire (-) karakterinin hemen önünde ve arkasında bir harf veya rakam bulunmalıdır; kapsayıcı adlarında art arda tirelere izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-215">Every dash (-) character must be immediately preceded and followed by a letter or number; consecutive dashes are not permitted in container names.</span></span>
1. <span data-ttu-id="a0d6d-216">Kapsayıcı adındaki tüm harfler küçük harf olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-216">All letters in a container name must be lowercase.</span></span>
1. <span data-ttu-id="a0d6d-217">Kapsayıcı adları 3-63 karakter arası uzunlukta olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-217">Container names must be from 3 through 63 characters long.</span></span>

<span data-ttu-id="a0d6d-218">Kapsayıcı adının her zaman küçük harfli olması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-218">Note that the name of a container must always be lowercase.</span></span> <span data-ttu-id="a0d6d-219">Kapsayıcı adına bir büyük harf katarsanız ya da başka bir deyişle kapsayıcı adlandırma kurallarını ihlal ederseniz 400 hatası alabilirsiniz (Hatalı İstek).</span><span class="sxs-lookup"><span data-stu-id="a0d6d-219">If you include an upper-case letter in a container name, or otherwise violate the container naming rules, you may receive a 400 error (Bad Request).</span></span>

## <a name="managing-security-for-blobs"></a><span data-ttu-id="a0d6d-220">Blobların güvenliğini sağlama</span><span class="sxs-lookup"><span data-stu-id="a0d6d-220">Managing security for blobs</span></span>

<span data-ttu-id="a0d6d-221">Varsayılan olarak Azure Storage, erişimi hesap erişim anahtarlarına sahip olan hesap sahibiyle sınırlandırarak verilerinizi güvende tutar.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-221">By default, Azure Storage keeps your data secure by limiting access to the account owner, who is in possession of the account access keys.</span></span> <span data-ttu-id="a0d6d-222">Depolama hesabınızda blob verileri paylaşmanız gerektiğinde bunu hesap erişim anahtarlarınızın güvenliğini tehlikeye atmadan yapmak önem taşır.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-222">When you need to share blob data in your storage account, it is important to do so without compromising the security of your account access keys.</span></span> <span data-ttu-id="a0d6d-223">Buna ek olarak kablo ve Azure Storage üzerinden güvenle geçmesini sağlamak için blob verilerini şifreleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-223">Additionally, you can encrypt blob data to ensure that it is secure going over the wire and in Azure Storage.</span></span>

### <a name="controlling-access-to-blob-data"></a><span data-ttu-id="a0d6d-224">Blob verilerine erişimi denetleme</span><span class="sxs-lookup"><span data-stu-id="a0d6d-224">Controlling access to blob data</span></span>

<span data-ttu-id="a0d6d-225">Varsayılan olarak depolama hesabındaki blob verileri yalnızca depolama hesabı sahibi tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-225">By default, the blob data in your storage account is accessible only to storage account owner.</span></span> <span data-ttu-id="a0d6d-226">Blob Depolamaya yönelik kimlik doğrulama istekleri, istek varsayılan olarak hesap erişim anahtarı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-226">Authenticating requests against Blob storage requires the account access key by default.</span></span> <span data-ttu-id="a0d6d-227">Ancak, bazı blob verilerini diğer kullanıcılar için kullanılabilir hale getirmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-227">However, you might want to make certain blob data available to other users.</span></span>

### <a name="encrypting-blob-data"></a><span data-ttu-id="a0d6d-228">Blob verilerini şifreleme</span><span class="sxs-lookup"><span data-stu-id="a0d6d-228">Encrypting blob data</span></span>

<span data-ttu-id="a0d6d-229">Azure depolama, blob verilerini hem istemcide hem de sunucuda şifrelemeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-229">Azure Storage supports encrypting blob data both at the client and on the server.</span></span>

## <a name="next-steps"></a><span data-ttu-id="a0d6d-230">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="a0d6d-230">Next steps</span></span>

<span data-ttu-id="a0d6d-231">Blob Storage’ın temellerini öğrendiğinize göre, daha fazla bilgi edinmek için bu bağlantıları izleyin.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-231">Now that you've learned the basics of Blob storage, follow these links to learn more.</span></span>

### <a name="tools"></a><span data-ttu-id="a0d6d-232">Araçlar</span><span class="sxs-lookup"><span data-stu-id="a0d6d-232">Tools</span></span>

- <span data-ttu-id="a0d6d-233">[ F# Azurestooygettypeınfo](https://fsprojects.github.io/AzureStorageTypeProvider/)</span><span class="sxs-lookup"><span data-stu-id="a0d6d-233">[F# AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/)</span></span>\
<span data-ttu-id="a0d6d-234">Blob F# , tablo ve kuyruk Azure depolama varlıklarını araştırmak ve bunlara kolayca CRUD işlemleri uygulamak için kullanılabilen bir tür sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-234">An F# Type Provider which can be used to explore Blob, Table and Queue Azure Storage assets and easily apply CRUD operations on them.</span></span>

- <span data-ttu-id="a0d6d-235">[FSharp. Azure. Storage](https://github.com/fsprojects/FSharp.Azure.Storage)</span><span class="sxs-lookup"><span data-stu-id="a0d6d-235">[FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage)</span></span>\
<span data-ttu-id="a0d6d-236">Microsoft Azure F# tablo depolama hizmeti kullanmak için bir API</span><span class="sxs-lookup"><span data-stu-id="a0d6d-236">An F# API for using Microsoft Azure Table Storage service</span></span>

- <span data-ttu-id="a0d6d-237">[Microsoft Azure Depolama Gezgini (Mao)](/azure/vs-azure-tools-storage-manage-with-storage-explorer)</span><span class="sxs-lookup"><span data-stu-id="a0d6d-237">[Microsoft Azure Storage Explorer (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer)</span></span>\
<span data-ttu-id="a0d6d-238">Microsoft 'un Windows, OS X ve Linux üzerinde Azure Depolama verileriyle görsel olarak çalışmanızı sağlayan ücretsiz ve tek başına bir uygulama.</span><span class="sxs-lookup"><span data-stu-id="a0d6d-238">A free, standalone app from Microsoft that enables you to work visually with Azure Storage data on Windows, OS X, and Linux.</span></span>

### <a name="blob-storage-reference"></a><span data-ttu-id="a0d6d-239">Blob Storage başvurusu</span><span class="sxs-lookup"><span data-stu-id="a0d6d-239">Blob storage reference</span></span>

- [<span data-ttu-id="a0d6d-240">.NET için Azure depolama API 'Leri</span><span class="sxs-lookup"><span data-stu-id="a0d6d-240">Azure Storage APIs for .NET</span></span>](/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="a0d6d-241">Azure Depolama Hizmetleri REST API Başvurusu</span><span class="sxs-lookup"><span data-stu-id="a0d6d-241">Azure Storage Services REST API Reference</span></span>](/rest/api/storageservices/)

### <a name="related-guides"></a><span data-ttu-id="a0d6d-242">İlgili kılavuzlar</span><span class="sxs-lookup"><span data-stu-id="a0d6d-242">Related guides</span></span>

- [<span data-ttu-id="a0d6d-243">.NET için Azure Blob depolama örnekleri</span><span class="sxs-lookup"><span data-stu-id="a0d6d-243">Azure Blob Storage Samples for .NET</span></span>](https://docs.microsoft.com/samples/azure-samples/storage-blob-dotnet-getting-started/storage-blob-dotnet-getting-started/)
- [<span data-ttu-id="a0d6d-244">AzCopy ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="a0d6d-244">Get started with AzCopy</span></span>](/azure/storage/common/storage-use-azcopy-v10)
- [<span data-ttu-id="a0d6d-245">Azure Depolama bağlantı dizelerini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a0d6d-245">Configure Azure Storage connection strings</span></span>](/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="a0d6d-246">Azure Depolama Ekibi Blog’u</span><span class="sxs-lookup"><span data-stu-id="a0d6d-246">Azure Storage Team Blog</span></span>](https://docs.microsoft.com/archive/blogs/windowsazurestorage/)
- [<span data-ttu-id="a0d6d-247">Hızlı başlangıç: nesne depolamada blob oluşturmak için .NET kullanın</span><span class="sxs-lookup"><span data-stu-id="a0d6d-247">Quickstart: Use .NET to create a blob in object storage</span></span>](/azure/storage/blobs/storage-quickstart-blobs-dotnet)
