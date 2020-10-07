---
title: F# kullanarak Azure Blob depolama kullanmaya başlama
description: Azure Blob depolama ile yapılandırılmamış verileri bulutta depolayın.
author: sylvanc
ms.date: 09/20/2016
ms.custom: devx-track-fsharp
ms.openlocfilehash: 91aec8fc2b57c71ce4ba47d62619912af6c71e59
ms.sourcegitcommit: a8a205034eeffc7c3e1bdd6f506a75b0f7099ebf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2020
ms.locfileid: "91756253"
---
# <a name="get-started-with-azure-blob-storage-using-f"></a><span data-ttu-id="ffc35-103">F kullanarak Azure Blob depolama ile çalışmaya başlama\#</span><span class="sxs-lookup"><span data-stu-id="ffc35-103">Get started with Azure Blob storage using F\#</span></span>

<span data-ttu-id="ffc35-104">Azure Blob Storage, bulutta nesne/blob olarak yapılandırılmamış veri depolayan bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="ffc35-104">Azure Blob storage is a service that stores unstructured data in the cloud as objects/blobs.</span></span> <span data-ttu-id="ffc35-105">Blob Storage belge, medya dosyası veya uygulama yükleyici gibi her tür metin veya ikili veri depolayabilir.</span><span class="sxs-lookup"><span data-stu-id="ffc35-105">Blob storage can store any type of text or binary data, such as a document, media file, or application installer.</span></span> <span data-ttu-id="ffc35-106">Blob Storage aynı zamanda nesne depolama olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="ffc35-106">Blob storage is also referred to as object storage.</span></span>

<span data-ttu-id="ffc35-107">Bu makalede, blob depolamayı kullanarak genel görevlerin nasıl gerçekleştirileceği gösterilir.</span><span class="sxs-lookup"><span data-stu-id="ffc35-107">This article shows you how to perform common tasks using Blob storage.</span></span> <span data-ttu-id="ffc35-108">Örnekler, .NET için Azure Storage Istemci kitaplığı kullanılarak F # kullanılarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="ffc35-108">The samples are written using F# using the Azure Storage Client Library for .NET.</span></span> <span data-ttu-id="ffc35-109">Kapsanan görevler, Blobları karşıya yükleme, listeleme, indirme ve silme işlemleri içerir.</span><span class="sxs-lookup"><span data-stu-id="ffc35-109">The tasks covered include how to upload, list, download, and delete blobs.</span></span>

<span data-ttu-id="ffc35-110">Blob depolamaya kavramsal bir genel bakış için bkz. [BLOB depolama için .net Kılavuzu](/azure/storage/blobs/storage-quickstart-blobs-dotnet).</span><span class="sxs-lookup"><span data-stu-id="ffc35-110">For a conceptual overview of blob storage, see [the .NET guide for blob storage](/azure/storage/blobs/storage-quickstart-blobs-dotnet).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ffc35-111">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="ffc35-111">Prerequisites</span></span>

<span data-ttu-id="ffc35-112">Bu kılavuzu kullanmak için önce [bir Azure depolama hesabı oluşturmanız](/azure/storage/common/storage-account-create)gerekir.</span><span class="sxs-lookup"><span data-stu-id="ffc35-112">To use this guide, you must first [create an Azure storage account](/azure/storage/common/storage-account-create).</span></span> <span data-ttu-id="ffc35-113">Bu hesap için depolama erişim anahtarınıza de ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="ffc35-113">You also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="ffc35-114">F # betiği oluşturun ve F# Etkileşimli başlatın</span><span class="sxs-lookup"><span data-stu-id="ffc35-114">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="ffc35-115">Bu makaledeki örnekler bir F # uygulamasında veya F # betiğinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ffc35-115">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="ffc35-116">F # betiği oluşturmak için, `.fsx` Örneğin `blobs.fsx` f # geliştirme ortamınızda uzantılı bir dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ffc35-116">To create an F# script, create a file with the `.fsx` extension, for example `blobs.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="ffc35-117">Ardından, [NuGet](https://www.nuget.org/) [Paket](https://fsprojects.github.io/Paket/) [package manager](package-management.md) `WindowsAzure.Storage` `Microsoft.WindowsAzure.ConfigurationManager` `WindowsAzure.Storage.dll` `Microsoft.WindowsAzure.Configuration.dll` bir yönergesi kullanarak ve paketlerini ve başvurusunu `#r` yüklemek için paket veya NuGet gibi bir paket Yöneticisi kullanın.</span><span class="sxs-lookup"><span data-stu-id="ffc35-117">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` and `Microsoft.WindowsAzure.ConfigurationManager` packages and reference `WindowsAzure.Storage.dll` and `Microsoft.WindowsAzure.Configuration.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="ffc35-118">Ad alanı bildirimleri ekleme</span><span class="sxs-lookup"><span data-stu-id="ffc35-118">Add namespace declarations</span></span>

<span data-ttu-id="ffc35-119">Aşağıdaki `open` bildirimlerini `blobs.fsx` dosyasının üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="ffc35-119">Add the following `open` statements to the top of the `blobs.fsx` file:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a><span data-ttu-id="ffc35-120">Bağlantı dizenizi alma</span><span class="sxs-lookup"><span data-stu-id="ffc35-120">Get your connection string</span></span>

<span data-ttu-id="ffc35-121">Bu öğretici için bir Azure depolama bağlantı dizesine ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="ffc35-121">You need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="ffc35-122">Bağlantı dizeleri hakkında daha fazla bilgi için bkz. [depolama bağlantı dizelerini yapılandırma](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="ffc35-122">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="ffc35-123">Öğreticide, Bağlantı dizenizi aşağıdaki gibi bir betiğe girersiniz:</span><span class="sxs-lookup"><span data-stu-id="ffc35-123">For the tutorial, you enter your connection string in your script, like this:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L11-L11)]

<span data-ttu-id="ffc35-124">Ancak, bu gerçek projeler için **önerilmez** .</span><span class="sxs-lookup"><span data-stu-id="ffc35-124">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="ffc35-125">Depolama hesabı anahtarınız depolama hesabınızın kök parolasına benzer.</span><span class="sxs-lookup"><span data-stu-id="ffc35-125">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="ffc35-126">Depolama hesabı anahtarınızı korumak için her zaman özen gösterin.</span><span class="sxs-lookup"><span data-stu-id="ffc35-126">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="ffc35-127">Diğer kullanıcılara dağıtmaktan, sabit kodlamaktan ve başkalarının erişebileceği düz metin dosyasına kaydetmekten kaçının.</span><span class="sxs-lookup"><span data-stu-id="ffc35-127">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="ffc35-128">Azure portal tehlikede olduğunu düşünüyorsanız, anahtarınızı yeniden oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ffc35-128">You can regenerate your key using the Azure portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="ffc35-129">Gerçek uygulamalar için, depolama Bağlantı dizenizi korumak için en iyi yol bir yapılandırma dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="ffc35-129">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="ffc35-130">Bağlantı dizesini bir yapılandırma dosyasından getirmek için şunu yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ffc35-130">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L13-L15)]

<span data-ttu-id="ffc35-131">Azure Yapılandırma Yöneticisi'ni kullanmak isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="ffc35-131">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="ffc35-132">.NET Framework türü gibi bir API de kullanabilirsiniz `ConfigurationManager` .</span><span class="sxs-lookup"><span data-stu-id="ffc35-132">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="ffc35-133">Bağlantı dizesini ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="ffc35-133">Parse the connection string</span></span>

<span data-ttu-id="ffc35-134">Bağlantı dizesini ayrıştırmak için şunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="ffc35-134">To parse the connection string, use:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L21-L22)]

<span data-ttu-id="ffc35-135">Bu, bir döndürür `CloudStorageAccount` .</span><span class="sxs-lookup"><span data-stu-id="ffc35-135">This returns a `CloudStorageAccount`.</span></span>

### <a name="create-some-local-dummy-data"></a><span data-ttu-id="ffc35-136">Bazı yerel kukla veriler oluşturma</span><span class="sxs-lookup"><span data-stu-id="ffc35-136">Create some local dummy data</span></span>

<span data-ttu-id="ffc35-137">Başlamadan önce, betiğimizin dizininde bazı sözde yerel veriler oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ffc35-137">Before you begin, create some dummy local data in the directory of our script.</span></span> <span data-ttu-id="ffc35-138">Daha sonra bu verileri karşıya yüklersiniz.</span><span class="sxs-lookup"><span data-stu-id="ffc35-138">Later you upload this data.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L28-L30)]

### <a name="create-the-blob-service-client"></a><span data-ttu-id="ffc35-139">Blob hizmeti istemcisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="ffc35-139">Create the Blob service client</span></span>

<span data-ttu-id="ffc35-140">`CloudBlobClient`Tür, blob depolamada depolanan kapsayıcıları ve Blobları almanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="ffc35-140">The `CloudBlobClient` type enables you to retrieve containers and blobs stored in Blob storage.</span></span> <span data-ttu-id="ffc35-141">Hizmet istemcisini oluşturma yöntemlerinden biri aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="ffc35-141">Here's one way to create the service client:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L36-L36)]

<span data-ttu-id="ffc35-142">Artık Blob Storage’da n veri okuyan ve bu depolamaya veri yazan kodu yazmaya hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="ffc35-142">Now you are ready to write code that reads data from and writes data to Blob storage.</span></span>

## <a name="create-a-container"></a><span data-ttu-id="ffc35-143">Bir kapsayıcı oluşturma</span><span class="sxs-lookup"><span data-stu-id="ffc35-143">Create a container</span></span>

<span data-ttu-id="ffc35-144">Bu örnek, zaten yoksa, nasıl bir kapsayıcı oluşturulacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="ffc35-144">This example shows how to create a container if it does not already exist:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L42-L46)]

<span data-ttu-id="ffc35-145">Varsayılan olarak yeni kapsayıcı özeldir, bu kapsayıcıdan blob indirmek için depolama erişim anahtarınızı belirlemeniz gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="ffc35-145">By default, the new container is private, meaning that you must specify your storage access key to download blobs from this container.</span></span> <span data-ttu-id="ffc35-146">Kapsayıcı içindeki dosyaların herkese açık olmasını istiyorsanız, aşağıdaki kodu kullanarak kapsayıcıyı herkesin erişimine açık hale getirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ffc35-146">If you want to make the files within the container available to everyone, you can set the container to be public using the following code:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L48-L49)]

<span data-ttu-id="ffc35-147">İnternet üzerindeki herkes, herkese açık bir kapsayıcıdaki blobları görebilir ancak uygun hesap erişim tuşu veya paylaşılan erişim imzanız olması durumunda bunları değiştirebilir veya silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ffc35-147">Anyone on the Internet can see blobs in a public container, but you can modify or delete them only if you have the appropriate account access key or a shared access signature.</span></span>

## <a name="upload-a-blob-into-a-container"></a><span data-ttu-id="ffc35-148">Bir kapsayıcıya bir blob yükleme</span><span class="sxs-lookup"><span data-stu-id="ffc35-148">Upload a blob into a container</span></span>

<span data-ttu-id="ffc35-149">Azure Blob Storage blok blobları ve sayfa bloblarını destekler.</span><span class="sxs-lookup"><span data-stu-id="ffc35-149">Azure Blob Storage supports block blobs and page blobs.</span></span> <span data-ttu-id="ffc35-150">Çoğu durumda, Blok Blobu kullanılacak önerilen türdür.</span><span class="sxs-lookup"><span data-stu-id="ffc35-150">In most cases, a block blob is the recommended type to use.</span></span>

<span data-ttu-id="ffc35-151">Bir dosyayı bir blok blobuna yüklemek için bir kapsayıcı başvurusu alın ve blok blob başvurusu almak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="ffc35-151">To upload a file to a block blob, get a container reference and use it to get a block blob reference.</span></span> <span data-ttu-id="ffc35-152">Blob başvurunuz olduktan sonra, yöntemini çağırarak herhangi bir veri akışını bu akışa yükleyebilirsiniz `UploadFromFile` .</span><span class="sxs-lookup"><span data-stu-id="ffc35-152">Once you have a blob reference, you can upload any stream of data to it by calling the `UploadFromFile` method.</span></span> <span data-ttu-id="ffc35-153">Bu işlem, daha önce yoksa blobu oluşturur veya varsa üzerine yazar.</span><span class="sxs-lookup"><span data-stu-id="ffc35-153">This operation creates the blob if it didn't previously exist, or overwrite it if it does exist.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L55-L59)]

## <a name="list-the-blobs-in-a-container"></a><span data-ttu-id="ffc35-154">Kapsayıcıdaki blobları listeleme</span><span class="sxs-lookup"><span data-stu-id="ffc35-154">List the blobs in a container</span></span>

<span data-ttu-id="ffc35-155">Blob’ları bir kapsayıcıda listelemek için ilk olarak bir kapsayıcı başvurusu edinin.</span><span class="sxs-lookup"><span data-stu-id="ffc35-155">To list the blobs in a container, first get a container reference.</span></span> <span data-ttu-id="ffc35-156">Daha sonra kapsayıcı `ListBlobs` ve/veya dizinlerini almak için kapsayıcının yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ffc35-156">You can then use the container's `ListBlobs` method to retrieve the blobs and/or directories within it.</span></span> <span data-ttu-id="ffc35-157">Döndürülen zengin özellik kümesine ve yöntemlere erişmek için, `IListBlobItem` bir `CloudBlockBlob` , `CloudPageBlob` veya `CloudBlobDirectory` nesnesine atamalısınız.</span><span class="sxs-lookup"><span data-stu-id="ffc35-157">To access the rich set of properties and methods for a returned `IListBlobItem`, you must cast it to a `CloudBlockBlob`, `CloudPageBlob`, or `CloudBlobDirectory` object.</span></span> <span data-ttu-id="ffc35-158">Tür bilinmiyorsa, hangisine yayınlayacağınızı belirlemek için bir tür denetimi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ffc35-158">If the type is unknown, you can use a type check to determine which to cast it to.</span></span> <span data-ttu-id="ffc35-159">Aşağıdaki kod, `mydata` kapsayıcıdaki her nesnenin URI’nın nasıl alınacağını ve çıkacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="ffc35-159">The following code demonstrates how to retrieve and output the URI of each item in the `mydata` container:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L67-L80)]

<span data-ttu-id="ffc35-160">Bloblarını adlarına yol bilgileriyle de girebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ffc35-160">You can also name blobs with path information in their names.</span></span> <span data-ttu-id="ffc35-161">Bu, geleneksel bir dosya sisteminde olduğu gibi düzenleme ve geçiş yapabileceğiniz sanal bir dizin yapısı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ffc35-161">This creates a virtual directory structure that you can organize and traverse as you would a traditional file system.</span></span> <span data-ttu-id="ffc35-162">Dizin yapısı yalnızca sanal, blob depolamada kullanılabilen tek kaynak kapsayıcılar ve bloblardır.</span><span class="sxs-lookup"><span data-stu-id="ffc35-162">The directory structure is virtual only - the only resources available in Blob storage are containers and blobs.</span></span> <span data-ttu-id="ffc35-163">Ancak, depolama istemci kitaplığı bir `CloudBlobDirectory` sanal dizine başvuracak bir nesne sunar ve bu şekilde düzenlenmiş bloblarla çalışma sürecini basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="ffc35-163">However, the storage client library offers a `CloudBlobDirectory` object to refer to a virtual directory and simplify the process of working with blobs that are organized in this way.</span></span>

<span data-ttu-id="ffc35-164">Örneğin bir kapsayıcıda yer alan ve `photos` olarak adlandırılan aşağıdaki blok blobları kümesine göz atın:</span><span class="sxs-lookup"><span data-stu-id="ffc35-164">For example, consider the following set of block blobs in a container named `photos`:</span></span>

<span data-ttu-id="ffc35-165">*photo1.jpg*</span><span class="sxs-lookup"><span data-stu-id="ffc35-165">*photo1.jpg*</span></span>\
<span data-ttu-id="ffc35-166">*2015/mimari/description.txt*</span><span class="sxs-lookup"><span data-stu-id="ffc35-166">*2015/architecture/description.txt*</span></span>\
<span data-ttu-id="ffc35-167">*2015/mimari/photo3.jpg*</span><span class="sxs-lookup"><span data-stu-id="ffc35-167">*2015/architecture/photo3.jpg*</span></span>\
<span data-ttu-id="ffc35-168">*2015/mimari/photo4.jpg*</span><span class="sxs-lookup"><span data-stu-id="ffc35-168">*2015/architecture/photo4.jpg*</span></span>\
<span data-ttu-id="ffc35-169">*2016/mimari/photo5.jpg*</span><span class="sxs-lookup"><span data-stu-id="ffc35-169">*2016/architecture/photo5.jpg*</span></span>\
<span data-ttu-id="ffc35-170">*2016/mimari/photo6.jpg*</span><span class="sxs-lookup"><span data-stu-id="ffc35-170">*2016/architecture/photo6.jpg*</span></span>\
<span data-ttu-id="ffc35-171">*2016/mimari/description.txt*</span><span class="sxs-lookup"><span data-stu-id="ffc35-171">*2016/architecture/description.txt*</span></span>\
<span data-ttu-id="ffc35-172">*2016/photo7.jpg*</span><span class="sxs-lookup"><span data-stu-id="ffc35-172">*2016/photo7.jpg*</span></span>\

<span data-ttu-id="ffc35-173">`ListBlobs`Bir kapsayıcıda (Yukarıdaki örnekte olduğu gibi) çağırdığınızda, hiyerarşik bir liste döndürülür.</span><span class="sxs-lookup"><span data-stu-id="ffc35-173">When you call `ListBlobs` on a container (as in the above sample), a hierarchical listing is returned.</span></span> <span data-ttu-id="ffc35-174">Hem hem de nesneler içeriyorsa, `CloudBlobDirectory` `CloudBlockBlob` kapsayıcıda dizin ve Blobları temsil eder, sonuçta elde edilen çıktı şuna benzer:</span><span class="sxs-lookup"><span data-stu-id="ffc35-174">If it contains both `CloudBlobDirectory` and `CloudBlockBlob` objects, representing the directories and blobs in the container, respectively, then the resulting output looks similar to this:</span></span>

```console
Directory: https://<accountname>.blob.core.windows.net/photos/2015/
Directory: https://<accountname>.blob.core.windows.net/photos/2016/
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

<span data-ttu-id="ffc35-175">İsteğe bağlı olarak, `UseFlatBlobListing` `ListBlobs` yönteminin parametresini olarak ayarlayabilirsiniz `true` .</span><span class="sxs-lookup"><span data-stu-id="ffc35-175">Optionally, you can set the `UseFlatBlobListing` parameter of the `ListBlobs` method to `true`.</span></span> <span data-ttu-id="ffc35-176">Bu durumda, kapsayıcıdaki her blob bir nesne olarak döndürülür `CloudBlockBlob` .</span><span class="sxs-lookup"><span data-stu-id="ffc35-176">In this case, every blob in the container is returned as a `CloudBlockBlob` object.</span></span> <span data-ttu-id="ffc35-177">`ListBlobs`Düz bir liste döndürmek için çağrısı şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="ffc35-177">The call to `ListBlobs` to return a flat listing looks like this:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L82-L89)]

<span data-ttu-id="ffc35-178">kapsayıcının geçerli içeriğine bağlı olarak, sonuçlar şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="ffc35-178">and, depending on the current contents of your container, the results look like this:</span></span>

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

## <a name="download-blobs"></a><span data-ttu-id="ffc35-179">Blob’ları indirme</span><span class="sxs-lookup"><span data-stu-id="ffc35-179">Download blobs</span></span>

<span data-ttu-id="ffc35-180">Blob 'ları indirmek için önce bir blob başvurusu alın ve sonra yöntemi çağırın `DownloadToStream` .</span><span class="sxs-lookup"><span data-stu-id="ffc35-180">To download blobs, first retrieve a blob reference and then call the `DownloadToStream` method.</span></span> <span data-ttu-id="ffc35-181">Aşağıdaki örnek, `DownloadToStream` BLOB içeriğini bir Stream nesnesine aktarmak için, daha sonra yerel bir dosyada kalıcı hale getirebilmeniz için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ffc35-181">The following example uses the `DownloadToStream` method to transfer the blob contents to a stream object that you can then persist to a local file.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L95-L101)]

<span data-ttu-id="ffc35-182">`DownloadToStream`Bir Blobun içeriğini bir metin dizesi olarak indirmek için yöntemini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ffc35-182">You can also use the `DownloadToStream` method to download the contents of a blob as a text string.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L103-L106)]

## <a name="delete-blobs"></a><span data-ttu-id="ffc35-183">Blob’ları silme</span><span class="sxs-lookup"><span data-stu-id="ffc35-183">Delete blobs</span></span>

<span data-ttu-id="ffc35-184">Bir blobu silmek için önce bir blob başvurusu alın ve ardından `Delete` üzerinde yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="ffc35-184">To delete a blob, first get a blob reference and then call the `Delete` method on it.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L112-L116)]

## <a name="list-blobs-in-pages-asynchronously"></a><span data-ttu-id="ffc35-185">Blob’ları sayfalarda zaman uyumsuz olarak listeleme</span><span class="sxs-lookup"><span data-stu-id="ffc35-185">List blobs in pages asynchronously</span></span>

<span data-ttu-id="ffc35-186">Çok sayıda blob listeliyorsanız veya bir listeleme işlemi ile dönen sonuç sayısını denetlemek isterseniz sonuç sayfalarında blobları listeleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ffc35-186">If you are listing a large number of blobs, or you want to control the number of results you return in one listing operation, you can list blobs in pages of results.</span></span> <span data-ttu-id="ffc35-187">Bu örnek, geniş bir sonuç kümesinin dönmesini beklerken çalıştırmanın engellenmemesi için sayfalardaki sonuçların zaman uyumsuz olarak nasıl döneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ffc35-187">This example shows how to return results in pages asynchronously, so that execution is not blocked while waiting to return a large set of results.</span></span>

<span data-ttu-id="ffc35-188">Bu örnek, düz bir blob listesini gösterir, ancak `useFlatBlobListing` yönteminin parametresini olarak ayarlayarak hiyerarşik bir liste da gerçekleştirebilirsiniz `ListBlobsSegmentedAsync` `false` .</span><span class="sxs-lookup"><span data-stu-id="ffc35-188">This example shows a flat blob listing, but you can also perform a hierarchical listing, by setting the `useFlatBlobListing` parameter of the `ListBlobsSegmentedAsync` method to `false`.</span></span>

<span data-ttu-id="ffc35-189">Örnek, blok kullanarak bir zaman uyumsuz yöntemi tanımlar `async` .</span><span class="sxs-lookup"><span data-stu-id="ffc35-189">The sample defines an asynchronous method, using an `async` block.</span></span> <span data-ttu-id="ffc35-190">``let!``Anahtar sözcüğü, listeleme görevi tamamlanana kadar örnek yöntemi yürütmeyi askıya alır.</span><span class="sxs-lookup"><span data-stu-id="ffc35-190">The ``let!`` keyword suspends execution of the sample method until the listing task completes.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L122-L160)]

<span data-ttu-id="ffc35-191">Artık bu zaman uyumsuz yordamı aşağıdaki gibi kullanabiliriz.</span><span class="sxs-lookup"><span data-stu-id="ffc35-191">We can now use this asynchronous routine as follows.</span></span> <span data-ttu-id="ffc35-192">İlk olarak bazı kukla verileri karşıya yüklersiniz (Bu öğreticide daha önce oluşturulan yerel dosyayı kullanarak).</span><span class="sxs-lookup"><span data-stu-id="ffc35-192">First you upload some dummy data (using the local file created earlier in this tutorial).</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L162-L166)]

<span data-ttu-id="ffc35-193">Şimdi, yordamını çağırın.</span><span class="sxs-lookup"><span data-stu-id="ffc35-193">Now, call the routine.</span></span> <span data-ttu-id="ffc35-194">`Async.RunSynchronously`Zaman uyumsuz işlemin yürütülmesini zorlamak için kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="ffc35-194">You use `Async.RunSynchronously` to force the execution of the asynchronous operation.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L168-L168)]

## <a name="writing-to-an-append-blob"></a><span data-ttu-id="ffc35-195">Ek blobu yazma</span><span class="sxs-lookup"><span data-stu-id="ffc35-195">Writing to an append blob</span></span>

<span data-ttu-id="ffc35-196">Ek blob, günlük tutma gibi ekleme işlemleri için en iyi duruma getirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ffc35-196">An append blob is optimized for append operations, such as logging.</span></span> <span data-ttu-id="ffc35-197">Bir blok blobu gibi, bir ekleme blobu bloklardan oluşur, ancak ekleme blobuna yeni bir blok eklediğinizde, her zaman blob 'un sonuna eklenir.</span><span class="sxs-lookup"><span data-stu-id="ffc35-197">Like a block blob, an append blob is composed of blocks, but when you add a new block to an append blob, it is always appended to the end of the blob.</span></span> <span data-ttu-id="ffc35-198">Bir ek blobdaki mevcut bloğu güncelleştiremezsiniz veya silemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="ffc35-198">You cannot update or delete an existing block in an append blob.</span></span> <span data-ttu-id="ffc35-199">Bir blok blobu olduğu için ek blobun blok kimliği gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="ffc35-199">The block IDs for an append blob are not exposed as they are for a block blob.</span></span>

<span data-ttu-id="ffc35-200">Her biri en fazla 4 MB olmak üzere bir ek blobundaki her blok farklı boyutlarda olabilir ve bir ek blobu en fazla 50.000 blok içerebilir.</span><span class="sxs-lookup"><span data-stu-id="ffc35-200">Each block in an append blob can be a different size, up to a maximum of 4 MB, and an append blob can include a maximum of 50,000 blocks.</span></span> <span data-ttu-id="ffc35-201">Bu nedenle bir ek blobunun en büyük boyutu 195 GB’den biraz fazladır (4 MB x 50.000 blok).</span><span class="sxs-lookup"><span data-stu-id="ffc35-201">The maximum size of an append blob is therefore slightly more than 195 GB (4 MB X 50,000 blocks).</span></span>

<span data-ttu-id="ffc35-202">Aşağıdaki örnek, yeni bir ekleme blobu oluşturur ve basit bir günlüğe kaydetme işleminin benzetimini yapar ve buna veri ekler.</span><span class="sxs-lookup"><span data-stu-id="ffc35-202">The following example creates a new append blob and appends some data to it, simulating a simple logging operation.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L174-L203)]

<span data-ttu-id="ffc35-203">Üç blob türü arasındaki farklar hakkında bilgi edinmek için bkz. [Blok Blobları, Sayfa Blobları ve Ek Bloblarını anlama](/rest/api/storageservices/Understanding-Block-Blobs--Append-Blobs--and-Page-Blobs).</span><span class="sxs-lookup"><span data-stu-id="ffc35-203">See [Understanding Block Blobs, Page Blobs, and Append Blobs](/rest/api/storageservices/Understanding-Block-Blobs--Append-Blobs--and-Page-Blobs) for more information about the differences between the three types of blobs.</span></span>

## <a name="concurrent-access"></a><span data-ttu-id="ffc35-204">Eşzamanlı erişim</span><span class="sxs-lookup"><span data-stu-id="ffc35-204">Concurrent access</span></span>

<span data-ttu-id="ffc35-205">Birden fazla istemciden veya birden çok işlem örneğiyle bir Blobun eşzamanlı erişimini desteklemek için **ETags** veya **kiralamalar**kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ffc35-205">To support concurrent access to a blob from multiple clients or multiple process instances, you can use **ETags** or **leases**.</span></span>

- <span data-ttu-id="ffc35-206">**ETag** -Blobun veya kapsayıcının başka bir işlem tarafından değiştirildiğini algılamaya yönelik bir yol sağlar</span><span class="sxs-lookup"><span data-stu-id="ffc35-206">**Etag** - provides a way to detect that the blob or container has been modified by another process</span></span>

- <span data-ttu-id="ffc35-207">**Kira** -bir zaman dilimi için bir Blobun özel, yenilenebilir, yazma veya silme erişimi almanın bir yolunu sağlar</span><span class="sxs-lookup"><span data-stu-id="ffc35-207">**Lease** - provides a way to obtain exclusive, renewable, write, or delete access to a blob for a period of time</span></span>

<span data-ttu-id="ffc35-208">Daha fazla bilgi için bkz. [Microsoft Azure depolama eşzamanlılık yönetimi](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).</span><span class="sxs-lookup"><span data-stu-id="ffc35-208">For more information, see [Managing Concurrency in Microsoft Azure Storage](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).</span></span>

## <a name="naming-containers"></a><span data-ttu-id="ffc35-209">Kapsayıcıları adlandırma</span><span class="sxs-lookup"><span data-stu-id="ffc35-209">Naming containers</span></span>

<span data-ttu-id="ffc35-210">Azure Storage’daki her blob bir kapsayıcıda yer almalıdır.</span><span class="sxs-lookup"><span data-stu-id="ffc35-210">Every blob in Azure storage must reside in a container.</span></span> <span data-ttu-id="ffc35-211">Kapsayıcı, blob adının bir bölümünü oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ffc35-211">The container forms part of the blob name.</span></span> <span data-ttu-id="ffc35-212">Örneğin, bu örnek blob URI’lerinde `mydata` kapsayıcının adıdır:</span><span class="sxs-lookup"><span data-stu-id="ffc35-212">For example, `mydata` is the name of the container in these sample blob URIs:</span></span>

- `https://storagesample.blob.core.windows.net/mydata/blob1.txt`
- `https://storagesample.blob.core.windows.net/mydata/photos/myphoto.jpg`

<span data-ttu-id="ffc35-213">Kapsayıcı adı, aşağıdaki adlandırma kurallarına uygun geçerli bir DNS adı olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="ffc35-213">A container name must be a valid DNS name, conforming to the following naming rules:</span></span>

1. <span data-ttu-id="ffc35-214">Kapsayıcı adları bir harf veya rakamla başlamalıdır; yalnızca harf, rakam ve tire (-) karakterinden oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="ffc35-214">Container names must start with a letter or number, and can contain only letters, numbers, and the dash (-) character.</span></span>
1. <span data-ttu-id="ffc35-215">Her tire (-) karakterinin hemen önünde ve arkasında bir harf veya rakam bulunmalıdır; kapsayıcı adlarında art arda tirelere izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="ffc35-215">Every dash (-) character must be immediately preceded and followed by a letter or number; consecutive dashes are not permitted in container names.</span></span>
1. <span data-ttu-id="ffc35-216">Kapsayıcı adındaki tüm harfler küçük harf olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ffc35-216">All letters in a container name must be lowercase.</span></span>
1. <span data-ttu-id="ffc35-217">Kapsayıcı adları 3-63 karakter arası uzunlukta olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ffc35-217">Container names must be from 3 through 63 characters long.</span></span>

<span data-ttu-id="ffc35-218">Kapsayıcının adı her zaman küçük harfle yazılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ffc35-218">The name of a container must always be lowercase.</span></span> <span data-ttu-id="ffc35-219">Kapsayıcı adına bir büyük harf katarsanız ya da başka bir deyişle kapsayıcı adlandırma kurallarını ihlal ederseniz 400 hatası alabilirsiniz (Hatalı İstek).</span><span class="sxs-lookup"><span data-stu-id="ffc35-219">If you include an upper-case letter in a container name, or otherwise violate the container naming rules, you may receive a 400 error (Bad Request).</span></span>

## <a name="managing-security-for-blobs"></a><span data-ttu-id="ffc35-220">Blobların güvenliğini sağlama</span><span class="sxs-lookup"><span data-stu-id="ffc35-220">Managing security for blobs</span></span>

<span data-ttu-id="ffc35-221">Varsayılan olarak Azure Storage, erişimi hesap erişim anahtarlarına sahip olan hesap sahibiyle sınırlandırarak verilerinizi güvende tutar.</span><span class="sxs-lookup"><span data-stu-id="ffc35-221">By default, Azure Storage keeps your data secure by limiting access to the account owner, who is in possession of the account access keys.</span></span> <span data-ttu-id="ffc35-222">Depolama hesabınızda blob verileri paylaşmanız gerektiğinde bunu hesap erişim anahtarlarınızın güvenliğini tehlikeye atmadan yapmak önem taşır.</span><span class="sxs-lookup"><span data-stu-id="ffc35-222">When you need to share blob data in your storage account, it is important to do so without compromising the security of your account access keys.</span></span> <span data-ttu-id="ffc35-223">Buna ek olarak kablo ve Azure Storage üzerinden güvenle geçmesini sağlamak için blob verilerini şifreleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ffc35-223">Additionally, you can encrypt blob data to ensure that it is secure going over the wire and in Azure Storage.</span></span>

### <a name="controlling-access-to-blob-data"></a><span data-ttu-id="ffc35-224">Blob verilerine erişimi denetleme</span><span class="sxs-lookup"><span data-stu-id="ffc35-224">Controlling access to blob data</span></span>

<span data-ttu-id="ffc35-225">Varsayılan olarak depolama hesabındaki blob verileri yalnızca depolama hesabı sahibi tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="ffc35-225">By default, the blob data in your storage account is accessible only to storage account owner.</span></span> <span data-ttu-id="ffc35-226">Blob Depolamaya yönelik kimlik doğrulama istekleri, istek varsayılan olarak hesap erişim anahtarı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ffc35-226">Authenticating requests against Blob storage requires the account access key by default.</span></span> <span data-ttu-id="ffc35-227">Ancak, bazı blob verilerini diğer kullanıcılar için kullanılabilir hale getirmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ffc35-227">However, you might want to make certain blob data available to other users.</span></span>

### <a name="encrypting-blob-data"></a><span data-ttu-id="ffc35-228">Blob verilerini şifreleme</span><span class="sxs-lookup"><span data-stu-id="ffc35-228">Encrypting blob data</span></span>

<span data-ttu-id="ffc35-229">Azure depolama, blob verilerini hem istemcide hem de sunucuda şifrelemeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="ffc35-229">Azure Storage supports encrypting blob data both at the client and on the server.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ffc35-230">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="ffc35-230">Next steps</span></span>

<span data-ttu-id="ffc35-231">Blob Storage’ın temellerini öğrendiğinize göre, daha fazla bilgi edinmek için bu bağlantıları izleyin.</span><span class="sxs-lookup"><span data-stu-id="ffc35-231">Now that you've learned the basics of Blob storage, follow these links to learn more.</span></span>

### <a name="tools"></a><span data-ttu-id="ffc35-232">Araçlar</span><span class="sxs-lookup"><span data-stu-id="ffc35-232">Tools</span></span>

- <span data-ttu-id="ffc35-233">[F # Azurestooygettypeınfo sağlayıcı](https://fsprojects.github.io/AzureStorageTypeProvider/)</span><span class="sxs-lookup"><span data-stu-id="ffc35-233">[F# AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/)</span></span>\
<span data-ttu-id="ffc35-234">Blob, tablo ve kuyruk Azure depolama varlıklarını araştırmak ve bunlara kolayca CRUD işlemleri uygulamak için kullanılabilen bir F # tür sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="ffc35-234">An F# Type Provider that can be used to explore Blob, Table, and Queue Azure Storage assets and easily apply CRUD operations on them.</span></span>

- <span data-ttu-id="ffc35-235">[FSharp. Azure. Storage](https://github.com/fsprojects/FSharp.Azure.Storage)</span><span class="sxs-lookup"><span data-stu-id="ffc35-235">[FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage)</span></span>\
<span data-ttu-id="ffc35-236">Microsoft Azure Table Storage hizmetini kullanmak için bir F # API 'SI</span><span class="sxs-lookup"><span data-stu-id="ffc35-236">An F# API for using Microsoft Azure Table Storage service</span></span>

- <span data-ttu-id="ffc35-237">[Microsoft Azure Depolama Gezgini (Mao)](/azure/vs-azure-tools-storage-manage-with-storage-explorer)</span><span class="sxs-lookup"><span data-stu-id="ffc35-237">[Microsoft Azure Storage Explorer (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer)</span></span>\
<span data-ttu-id="ffc35-238">Microsoft 'un Windows, OS X ve Linux üzerinde Azure Depolama verileriyle görsel olarak çalışmanızı sağlayan ücretsiz ve tek başına bir uygulama.</span><span class="sxs-lookup"><span data-stu-id="ffc35-238">A free, standalone app from Microsoft that enables you to work visually with Azure Storage data on Windows, OS X, and Linux.</span></span>

### <a name="blob-storage-reference"></a><span data-ttu-id="ffc35-239">Blob Storage başvurusu</span><span class="sxs-lookup"><span data-stu-id="ffc35-239">Blob storage reference</span></span>

- [<span data-ttu-id="ffc35-240">.NET için Azure Depolama API'leri</span><span class="sxs-lookup"><span data-stu-id="ffc35-240">Azure Storage APIs for .NET</span></span>](/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="ffc35-241">Azure Depolama Hizmeti REST API Başvurusu</span><span class="sxs-lookup"><span data-stu-id="ffc35-241">Azure Storage Services REST API Reference</span></span>](/rest/api/storageservices/)

### <a name="related-guides"></a><span data-ttu-id="ffc35-242">İlgili kılavuzlar</span><span class="sxs-lookup"><span data-stu-id="ffc35-242">Related guides</span></span>

- [<span data-ttu-id="ffc35-243">.NET için Azure Blob depolama örnekleri</span><span class="sxs-lookup"><span data-stu-id="ffc35-243">Azure Blob Storage Samples for .NET</span></span>](/samples/azure-samples/storage-blob-dotnet-getting-started/storage-blob-dotnet-getting-started/)
- [<span data-ttu-id="ffc35-244">AzCopy’yi kullanmaya başlama</span><span class="sxs-lookup"><span data-stu-id="ffc35-244">Get started with AzCopy</span></span>](/azure/storage/common/storage-use-azcopy-v10)
- [<span data-ttu-id="ffc35-245">Azure depolama bağlantı dizelerini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ffc35-245">Configure Azure Storage connection strings</span></span>](/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="ffc35-246">Azure Depolama Ekibi Blogu</span><span class="sxs-lookup"><span data-stu-id="ffc35-246">Azure Storage Team Blog</span></span>](/archive/blogs/windowsazurestorage/)
- [<span data-ttu-id="ffc35-247">Hızlı Başlangıç: Nesne depolamada blob oluşturmak için .NET kullanma</span><span class="sxs-lookup"><span data-stu-id="ffc35-247">Quickstart: Use .NET to create a blob in object storage</span></span>](/azure/storage/blobs/storage-quickstart-blobs-dotnet)
