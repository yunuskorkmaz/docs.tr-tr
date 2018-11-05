---
title: F# kullanarak Azure Blob depolamayı kullanmaya başlama
description: Azure Blob Depolama ile bulutta yapılandırılmamış veri Store.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: ea9dc334ec9c2bcd4a80cc501d4b6634da5f64e4
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "44037288"
---
# <a name="get-started-with-azure-blob-storage-using-f"></a><span data-ttu-id="8adfb-103">F# kullanarak Azure Blob depolamayı kullanmaya başlama</span><span class="sxs-lookup"><span data-stu-id="8adfb-103">Get started with Azure Blob storage using F#</span></span> #

<span data-ttu-id="8adfb-104">Azure Blob Depolama, yapılandırılmamış verileri nesne/BLOB olarak bulutta depolayan bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="8adfb-104">Azure Blob storage is a service that stores unstructured data in the cloud as objects/blobs.</span></span> <span data-ttu-id="8adfb-105">BLOB Depolama, herhangi bir türde metin veya belge, medya dosyası veya uygulama Yükleyici gibi ikili veri depolayabilir.</span><span class="sxs-lookup"><span data-stu-id="8adfb-105">Blob storage can store any type of text or binary data, such as a document, media file, or application installer.</span></span> <span data-ttu-id="8adfb-106">BLOB storage ayrıca nesne depolama olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="8adfb-106">Blob storage is also referred to as object storage.</span></span>

<span data-ttu-id="8adfb-107">Bu makalede, Blob depolamayı kullanarak ortak görevleri nasıl gerçekleştireceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="8adfb-107">This article shows you how to perform common tasks using Blob storage.</span></span> <span data-ttu-id="8adfb-108">Örnekler, F# .NET için Azure depolama istemci kitaplığı kullanarak kullanarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="8adfb-108">The samples are written using F# using the Azure Storage Client Library for .NET.</span></span> <span data-ttu-id="8adfb-109">Kapsanan görevleri yüklemek, listelemek, indirmek ve blobları silme işlemini içerir.</span><span class="sxs-lookup"><span data-stu-id="8adfb-109">The tasks covered include how to upload, list, download, and delete blobs.</span></span>

<span data-ttu-id="8adfb-110">Blob depolama kavramsal bir genel bakış için bkz: [blob depolama için .NET Kılavuzu](/azure/storage/storage-dotnet-how-to-use-blobs).</span><span class="sxs-lookup"><span data-stu-id="8adfb-110">For a conceptual overview of blob storage, see [the .NET guide for blob storage](/azure/storage/storage-dotnet-how-to-use-blobs).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8adfb-111">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="8adfb-111">Prerequisites</span></span>

<span data-ttu-id="8adfb-112">Bu kılavuzu kullanmak için önce [bir Azure depolama hesabı oluşturma](/azure/storage/storage-create-storage-account).</span><span class="sxs-lookup"><span data-stu-id="8adfb-112">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span> <span data-ttu-id="8adfb-113">Ayrıca bu hesap için depolama erişim anahtarınızı gerekir.</span><span class="sxs-lookup"><span data-stu-id="8adfb-113">You also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="8adfb-114">Bir F# komut dosyası ve başlangıç F# Etkileşimli oluşturma</span><span class="sxs-lookup"><span data-stu-id="8adfb-114">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="8adfb-115">Bu makaledeki örnekleri, F# uygulaması veya bir F# komut dosyası kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8adfb-115">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="8adfb-116">Bir F# komut dosyası oluşturmak için bir dosya oluşturun. `.fsx` uzantısı, örneğin `blobs.fsx`, F# geliştirme ortamınızda.</span><span class="sxs-lookup"><span data-stu-id="8adfb-116">To create an F# script, create a file with the `.fsx` extension, for example `blobs.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="8adfb-117">Ardından, bir [Paket Yöneticisi](package-management.md) gibi [Paket](https://fsprojects.github.io/Paket/) veya [NuGet](https://www.nuget.org/) yüklemek için `WindowsAzure.Storage` ve `Microsoft.WindowsAzure.ConfigurationManager` paketler ve başvuru `WindowsAzure.Storage.dll` ve `Microsoft.WindowsAzure.Configuration.dll` komut dosyası kullanarak bir `#r` yönergesi.</span><span class="sxs-lookup"><span data-stu-id="8adfb-117">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` and `Microsoft.WindowsAzure.ConfigurationManager` packages and reference `WindowsAzure.Storage.dll` and `Microsoft.WindowsAzure.Configuration.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="8adfb-118">Ad alanı bildirimleri ekleme</span><span class="sxs-lookup"><span data-stu-id="8adfb-118">Add namespace declarations</span></span>

<span data-ttu-id="8adfb-119">Aşağıdaki `open` üst tarafına deyimlerini `blobs.fsx` dosyası:</span><span class="sxs-lookup"><span data-stu-id="8adfb-119">Add the following `open` statements to the top of the `blobs.fsx` file:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a><span data-ttu-id="8adfb-120">Bağlantı dizenizi alma</span><span class="sxs-lookup"><span data-stu-id="8adfb-120">Get your connection string</span></span>

<span data-ttu-id="8adfb-121">Bu öğreticide bir Azure depolama bağlantı dizesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="8adfb-121">You need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="8adfb-122">Bağlantı dizeleri hakkında daha fazla bilgi için bkz. [depolama bağlantı dizelerini yapılandırma](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="8adfb-122">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="8adfb-123">Öğretici için şunun gibi komut dosyanızdaki bağlantı dizenizi girin:</span><span class="sxs-lookup"><span data-stu-id="8adfb-123">For the tutorial, you enter your connection string in your script, like this:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L11-L11)]

<span data-ttu-id="8adfb-124">Ancak, bu, **önerilmez** gerçek projeleri.</span><span class="sxs-lookup"><span data-stu-id="8adfb-124">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="8adfb-125">Depolama hesabı anahtarınız depolama hesabınızın kök parolasına benzer.</span><span class="sxs-lookup"><span data-stu-id="8adfb-125">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="8adfb-126">Her zaman depolama hesabı anahtarınızı korumak dikkatli olun.</span><span class="sxs-lookup"><span data-stu-id="8adfb-126">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="8adfb-127">Sabit kodlama veya başkalarının erişebileceği bir düz metin dosyasına kaydederek diğer kullanıcılara dağıtmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="8adfb-127">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="8adfb-128">Tehlikeye girmiş olabilecek düşünüyorsanız Azure portalını kullanarak anahtarınızı yeniden oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8adfb-128">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="8adfb-129">Gerçek uygulamalar, depolama bağlantı dizenizi korumak için en iyi yolu, içinde bir yapılandırma dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="8adfb-129">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="8adfb-130">Bir yapılandırma dosyasından bağlantı dizesini getirmek için bunu yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8adfb-130">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L13-L15)]

<span data-ttu-id="8adfb-131">Azure Yapılandırma Yöneticisi'ni kullanmak isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="8adfb-131">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="8adfb-132">.NET Framework'ün gibi bir API de kullanabilirsiniz `ConfigurationManager` türü.</span><span class="sxs-lookup"><span data-stu-id="8adfb-132">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="8adfb-133">Bağlantı dizesini ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="8adfb-133">Parse the connection string</span></span>

<span data-ttu-id="8adfb-134">Bağlantı dizesini ayrıştırmak için kullanın:</span><span class="sxs-lookup"><span data-stu-id="8adfb-134">To parse the connection string, use:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L21-L22)]

<span data-ttu-id="8adfb-135">Bu döndürür bir `CloudStorageAccount`.</span><span class="sxs-lookup"><span data-stu-id="8adfb-135">This returns a `CloudStorageAccount`.</span></span>

### <a name="create-some-local-dummy-data"></a><span data-ttu-id="8adfb-136">Yerel bazı örnek veri oluşturma</span><span class="sxs-lookup"><span data-stu-id="8adfb-136">Create some local dummy data</span></span>

<span data-ttu-id="8adfb-137">Başlamadan önce bazı işlevsiz bir yerel veri betiğimizi dizininde oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8adfb-137">Before you begin, create some dummy local data in the directory of our script.</span></span> <span data-ttu-id="8adfb-138">Daha sonra bu verileri karşıya yükleyin.</span><span class="sxs-lookup"><span data-stu-id="8adfb-138">Later you upload this data.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L28-L30)]

### <a name="create-the-blob-service-client"></a><span data-ttu-id="8adfb-139">Blob hizmeti istemcisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="8adfb-139">Create the Blob service client</span></span>

<span data-ttu-id="8adfb-140">`CloudBlobClient` Türü kapsayıcıları ve Blob Depolama alanında depolanan blobları almanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="8adfb-140">The `CloudBlobClient` type enables you to retrieve containers and blobs stored in Blob storage.</span></span> <span data-ttu-id="8adfb-141">Hizmet istemcisini oluşturma yöntemlerinden biri aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="8adfb-141">Here's one way to create the service client:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L36-L36)]

<span data-ttu-id="8adfb-142">Şimdi, okuyan ve Blob depolamaya veri yazan kodu yazmaya hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="8adfb-142">Now you are ready to write code that reads data from and writes data to Blob storage.</span></span>

## <a name="create-a-container"></a><span data-ttu-id="8adfb-143">Bir kapsayıcı oluşturma</span><span class="sxs-lookup"><span data-stu-id="8adfb-143">Create a container</span></span>

<span data-ttu-id="8adfb-144">Bu örnek, zaten yoksa, bir kapsayıcı oluşturma işlemi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="8adfb-144">This example shows how to create a container if it does not already exist:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L42-L46)]

<span data-ttu-id="8adfb-145">Varsayılan olarak, yeni özel Bu kapsayıcıdan BLOB indirmek için depolama erişim anahtarınızı belirlemeniz gerektiği anlamına kapsayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="8adfb-145">By default, the new container is private, meaning that you must specify your storage access key to download blobs from this container.</span></span> <span data-ttu-id="8adfb-146">Kapsayıcı içindeki dosyaların herkese kullanılabilmesini istiyorsanız, kapsayıcı aşağıdaki kodu kullanarak genel olarak ayarlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8adfb-146">If you want to make the files within the container available to everyone, you can set the container to be public using the following code:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L48-L49)]

<span data-ttu-id="8adfb-147">Internet'teki herkes ortak bir kapsayıcıdaki blobları görebilir ancak değiştirdiğinizde ya da yalnızca uygun hesap erişim anahtarı veya paylaşılan erişim imzası varsa bunları silin.</span><span class="sxs-lookup"><span data-stu-id="8adfb-147">Anyone on the Internet can see blobs in a public container, but you can modify or delete them only if you have the appropriate account access key or a shared access signature.</span></span>

## <a name="upload-a-blob-into-a-container"></a><span data-ttu-id="8adfb-148">Bir kapsayıcıya bir blob yükleme</span><span class="sxs-lookup"><span data-stu-id="8adfb-148">Upload a blob into a container</span></span>

<span data-ttu-id="8adfb-149">Azure Blob Depolama blok blobları ve sayfa bloblarını destekler.</span><span class="sxs-lookup"><span data-stu-id="8adfb-149">Azure Blob Storage supports block blobs and page blobs.</span></span> <span data-ttu-id="8adfb-150">Çoğu durumda, bir blok blobu kullanmak için önerilen türdür.</span><span class="sxs-lookup"><span data-stu-id="8adfb-150">In most cases, a block blob is the recommended type to use.</span></span>

<span data-ttu-id="8adfb-151">Bir dosyayı bir blok blobuna yüklemek için bir kapsayıcı başvurusu alın ve blok blob başvurusu almak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="8adfb-151">To upload a file to a block blob, get a container reference and use it to get a block blob reference.</span></span> <span data-ttu-id="8adfb-152">Bir blob başvurusunu aldıktan sonra herhangi bir veri akışı için çağırarak yükleyebilirsiniz `UploadFromFile` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8adfb-152">Once you have a blob reference, you can upload any stream of data to it by calling the `UploadFromFile` method.</span></span> <span data-ttu-id="8adfb-153">Bu işlem, daha önce mevcut fırsatınız veya mevcut değilse üzerine blob oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8adfb-153">This operation creates the blob if it didn't previously exist, or overwrite it if it does exist.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L55-L59)]

## <a name="list-the-blobs-in-a-container"></a><span data-ttu-id="8adfb-154">Bir kapsayıcıdaki blobları Listele</span><span class="sxs-lookup"><span data-stu-id="8adfb-154">List the blobs in a container</span></span>

<span data-ttu-id="8adfb-155">Bir kapsayıcıdaki blobları listelemek için ilk olarak bir kapsayıcı başvurusu alın.</span><span class="sxs-lookup"><span data-stu-id="8adfb-155">To list the blobs in a container, first get a container reference.</span></span> <span data-ttu-id="8adfb-156">Daha sonra kapsayıcının kullanabilirsiniz `ListBlobs` blobları ve/veya dizinleri içine almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8adfb-156">You can then use the container's `ListBlobs` method to retrieve the blobs and/or directories within it.</span></span> <span data-ttu-id="8adfb-157">Zengin özellik ve yöntem dönen erişmeye `IListBlobItem`, kendisine dönüştürmelisiniz bir `CloudBlockBlob`, `CloudPageBlob`, veya `CloudBlobDirectory` nesne.</span><span class="sxs-lookup"><span data-stu-id="8adfb-157">To access the rich set of properties and methods for a returned `IListBlobItem`, you must cast it to a `CloudBlockBlob`, `CloudPageBlob`, or `CloudBlobDirectory` object.</span></span> <span data-ttu-id="8adfb-158">Tür bilinmiyorsa, yayınlayacağınızı belirlemek için bir tür denetimi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8adfb-158">If the type is unknown, you can use a type check to determine which to cast it to.</span></span> <span data-ttu-id="8adfb-159">Aşağıdaki kod, almak ve her nesnenin URI çıkış gösterilmiştir `mydata` kapsayıcı:</span><span class="sxs-lookup"><span data-stu-id="8adfb-159">The following code demonstrates how to retrieve and output the URI of each item in the `mydata` container:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L67-L80)]

<span data-ttu-id="8adfb-160">Adı blobları adlarında yol bilgileriyle de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8adfb-160">You can also name blobs with path information in their names.</span></span> <span data-ttu-id="8adfb-161">Bu, geleneksel bir dosya sisteminde olduğu gibi çapraz geçiş düzenleyebilir ve bir sanal dizin yapısı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8adfb-161">This creates a virtual directory structure that you can organize and traverse as you would a traditional file system.</span></span> <span data-ttu-id="8adfb-162">Dizin yapısı yalnızca sanaldır - kaynak yalnızca Blob Depolama alanında kullanılabilir kapsayıcılar ve bloblar kullanılabilir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8adfb-162">Note that the directory structure is virtual only - the only resources available in Blob storage are containers and blobs.</span></span> <span data-ttu-id="8adfb-163">Ancak, depolama istemcisi kitaplığı sunan bir `CloudBlobDirectory` sanal dizine ait ve bu şekilde düzenlenen bloblarla çalışma sürecini basitleştirmek için nesne.</span><span class="sxs-lookup"><span data-stu-id="8adfb-163">However, the storage client library offers a `CloudBlobDirectory` object to refer to a virtual directory and simplify the process of working with blobs that are organized in this way.</span></span>

<span data-ttu-id="8adfb-164">Örneğin, aşağıdaki adlı bir kapsayıcı içinde blok blobları kümesine göz önünde bulundurun `photos`:</span><span class="sxs-lookup"><span data-stu-id="8adfb-164">For example, consider the following set of block blobs in a container named `photos`:</span></span>

<span data-ttu-id="8adfb-165">*photo1.jpg*
*2015/architecture/description.txt*
*2015/architecture/photo3.jpg*
*2015 / Mimari/photo4.jpg*
*2016/architecture/photo5.jpg*
*2016/architecture/photo6.jpg* 
 *2016/architecture/description.txt*
*2016/photo7.jpg*</span><span class="sxs-lookup"><span data-stu-id="8adfb-165">*photo1.jpg*
*2015/architecture/description.txt*
*2015/architecture/photo3.jpg*
*2015/architecture/photo4.jpg*
*2016/architecture/photo5.jpg*
*2016/architecture/photo6.jpg*
*2016/architecture/description.txt*
*2016/photo7.jpg*</span></span>

<span data-ttu-id="8adfb-166">Çağırdığınızda `ListBlobs` (Yukarıdaki örnek) olduğu gibi bir kapsayıcı, hiyerarşik bir listeleme döndürülür.</span><span class="sxs-lookup"><span data-stu-id="8adfb-166">When you call `ListBlobs` on a container (as in the above sample), a hierarchical listing is returned.</span></span> <span data-ttu-id="8adfb-167">Her ikisi de içeriyorsa `CloudBlobDirectory` ve `CloudBlockBlob` sonuçta çıktı şuna benzer sonra dizinleri ve blobları kapsayıcıda sırasıyla temsil eden nesneler:</span><span class="sxs-lookup"><span data-stu-id="8adfb-167">If it contains both `CloudBlobDirectory` and `CloudBlockBlob` objects, representing the directories and blobs in the container, respectively, then the resulting output looks similar to this:</span></span>

```console
Directory: https://<accountname>.blob.core.windows.net/photos/2015/
Directory: https://<accountname>.blob.core.windows.net/photos/2016/
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

<span data-ttu-id="8adfb-168">İsteğe bağlı olarak ayarlayabileceğiniz `UseFlatBlobListing` parametresinin `ListBlobs` yönteme `true`.</span><span class="sxs-lookup"><span data-stu-id="8adfb-168">Optionally, you can set the `UseFlatBlobListing` parameter of the `ListBlobs` method to `true`.</span></span> <span data-ttu-id="8adfb-169">Bu durumda kapsayıcıdaki her blob olarak döndürülen bir `CloudBlockBlob` nesne.</span><span class="sxs-lookup"><span data-stu-id="8adfb-169">In this case, every blob in the container is returned as a `CloudBlockBlob` object.</span></span> <span data-ttu-id="8adfb-170">Çağrı `ListBlobs` döndürülecek bir düz liste aşağıdaki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="8adfb-170">The call to `ListBlobs` to return a flat listing looks like this:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L82-L89)]

<span data-ttu-id="8adfb-171">ve kapsayıcınızı geçerli içeriğini bağlı olarak, sonuçlar şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="8adfb-171">and, depending on the current contents of your container, the results look like this:</span></span>

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

## <a name="download-blobs"></a><span data-ttu-id="8adfb-172">Blobları indirin</span><span class="sxs-lookup"><span data-stu-id="8adfb-172">Download blobs</span></span>

<span data-ttu-id="8adfb-173">Blobları indirmek için önce bir blob başvurusu alın ve sonra çağrı `DownloadToStream` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8adfb-173">To download blobs, first retrieve a blob reference and then call the `DownloadToStream` method.</span></span> <span data-ttu-id="8adfb-174">Aşağıdaki örnekte `DownloadToStream` blob içeriklerini, ardından yerel bir dosyaya kalıcı bir akış nesnesine aktarmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8adfb-174">The following example uses the `DownloadToStream` method to transfer the blob contents to a stream object that you can then persist to a local file.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L95-L101)]

<span data-ttu-id="8adfb-175">Ayrıca `DownloadToStream` bir metin dizesi olarak bir blobun içeriklerini indirmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8adfb-175">You can also use the `DownloadToStream` method to download the contents of a blob as a text string.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L103-L106)]

## <a name="delete-blobs"></a><span data-ttu-id="8adfb-176">Blobları Sil</span><span class="sxs-lookup"><span data-stu-id="8adfb-176">Delete blobs</span></span>

<span data-ttu-id="8adfb-177">Bir blobu silmek için önce bir blob başvurusu alın ve sonra çağrı `Delete` yöntemini.</span><span class="sxs-lookup"><span data-stu-id="8adfb-177">To delete a blob, first get a blob reference and then call the `Delete` method on it.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L112-L116)]

## <a name="list-blobs-in-pages-asynchronously"></a><span data-ttu-id="8adfb-178">BLOB'ları sayfalarda zaman uyumsuz olarak listeleme</span><span class="sxs-lookup"><span data-stu-id="8adfb-178">List blobs in pages asynchronously</span></span>

<span data-ttu-id="8adfb-179">Çok sayıda BLOB listeliyorsanız veya bir listeleme işlemi ile dönen sonuç sayısını denetlemek isterseniz sonuç sayfalarında blobları listeleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8adfb-179">If you are listing a large number of blobs, or you want to control the number of results you return in one listing operation, you can list blobs in pages of results.</span></span> <span data-ttu-id="8adfb-180">Bu örnek, böylece geniş bir sonuç kümesinin dönmesini beklerken yürütme engellenip engellenmediğini sayfalarda zaman uyumsuz olarak sonuçları döndürmek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="8adfb-180">This example shows how to return results in pages asynchronously, so that execution is not blocked while waiting to return a large set of results.</span></span>

<span data-ttu-id="8adfb-181">Bu örnek düz bir blob listesi gösterir, ancak ayarlayarak hiyerarşik bir listeleme gerçekleştirebilirsiniz `useFlatBlobListing` parametresinin `ListBlobsSegmentedAsync` yönteme `false`.</span><span class="sxs-lookup"><span data-stu-id="8adfb-181">This example shows a flat blob listing, but you can also perform a hierarchical listing, by setting the `useFlatBlobListing` parameter of the `ListBlobsSegmentedAsync` method to `false`.</span></span>

<span data-ttu-id="8adfb-182">Örnek zaman uyumsuz bir yöntem tanımlar kullanarak bir `async` blok.</span><span class="sxs-lookup"><span data-stu-id="8adfb-182">The sample defines an asynchronous method, using an `async` block.</span></span> <span data-ttu-id="8adfb-183">``let!`` Anahtar sözcüğü listeleme görevi tamamlanana kadar örnek yöntemin yürütülmesini askıya alır.</span><span class="sxs-lookup"><span data-stu-id="8adfb-183">The ``let!`` keyword suspends execution of the sample method until the listing task completes.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L122-L160)]

<span data-ttu-id="8adfb-184">Artık bu zaman uyumsuz bir yordam gibi kullanabiliriz.</span><span class="sxs-lookup"><span data-stu-id="8adfb-184">We can now use this asynchronous routine as follows.</span></span> <span data-ttu-id="8adfb-185">İlk (Bu öğreticide daha önce oluşturulan yerel dosya kullanarak) işlevsiz bazı veriler yükleyin.</span><span class="sxs-lookup"><span data-stu-id="8adfb-185">First you upload some dummy data (using the local file created earlier in this tutorial).</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L162-L166)]

<span data-ttu-id="8adfb-186">Şimdi, rutinin çağırın.</span><span class="sxs-lookup"><span data-stu-id="8adfb-186">Now, call the routine.</span></span> <span data-ttu-id="8adfb-187">Kullandığınız `Async.RunSynchronously` zaman uyumsuz işlem yürütülmesini zorlamak için.</span><span class="sxs-lookup"><span data-stu-id="8adfb-187">You use `Async.RunSynchronously` to force the execution of the asynchronous operation.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L168-L168)]

## <a name="writing-to-an-append-blob"></a><span data-ttu-id="8adfb-188">Bir ek blobu yazma</span><span class="sxs-lookup"><span data-stu-id="8adfb-188">Writing to an append blob</span></span>

<span data-ttu-id="8adfb-189">Bir ekleme blobu, günlüğe kaydetme gibi ekleme işlemleri için iyileştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8adfb-189">An append blob is optimized for append operations, such as logging.</span></span> <span data-ttu-id="8adfb-190">Blok blobuna benzer bir ek blobu bloklardan oluşur ancak bir ek bloba yeni bir blok eklediğinizde her zaman blobun sonuna eklenir.</span><span class="sxs-lookup"><span data-stu-id="8adfb-190">Like a block blob, an append blob is comprised of blocks, but when you add a new block to an append blob, it is always appended to the end of the blob.</span></span> <span data-ttu-id="8adfb-191">Güncelleştiremezsiniz veya ek blobdaki mevcut bloğu silin.</span><span class="sxs-lookup"><span data-stu-id="8adfb-191">You cannot update or delete an existing block in an append blob.</span></span> <span data-ttu-id="8adfb-192">Bir blok blobu için olduğu gibi ek blobun blok kimliği gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="8adfb-192">The block IDs for an append blob are not exposed as they are for a block blob.</span></span>

<span data-ttu-id="8adfb-193">Her bir ek blobu bloğunda en çok 4 MB, farklı boyutlarda olabilir ve bir ek blobu en fazla 50.000 blok içerebilir.</span><span class="sxs-lookup"><span data-stu-id="8adfb-193">Each block in an append blob can be a different size, up to a maximum of 4 MB, and an append blob can include a maximum of 50,000 blocks.</span></span> <span data-ttu-id="8adfb-194">Bu nedenle bir ek blobunun en büyük boyutu 195 GB'tan biraz daha fazladır (4 MB X 50.000 blok) ' dir.</span><span class="sxs-lookup"><span data-stu-id="8adfb-194">The maximum size of an append blob is therefore slightly more than 195 GB (4 MB X 50,000 blocks).</span></span>

<span data-ttu-id="8adfb-195">Aşağıdaki örnek, yeni bir ek blob oluşturur ve bazı veriler, bir basit günlüğe kaydetme işlemini benzeterek buna.</span><span class="sxs-lookup"><span data-stu-id="8adfb-195">The following example creates a new append blob and appends some data to it, simulating a simple logging operation.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L174-L203)]

<span data-ttu-id="8adfb-196">Bkz: [anlama blok Blobları, sayfa Blobları ve ekleme Blobları](https://msdn.microsoft.com/library/azure/ee691964.aspx) üç tür BLOB arasındaki farklar hakkında daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="8adfb-196">See [Understanding Block Blobs, Page Blobs, and Append Blobs](https://msdn.microsoft.com/library/azure/ee691964.aspx) for more information about the differences between the three types of blobs.</span></span>

## <a name="concurrent-access"></a><span data-ttu-id="8adfb-197">Eş zamanlı erişim</span><span class="sxs-lookup"><span data-stu-id="8adfb-197">Concurrent access</span></span>

<span data-ttu-id="8adfb-198">Birden çok istemciden veya birden çok işlem örnekleri eş zamanlı erişim bir blob olarak desteklemek için kullanabileceğiniz **Etag'ler** veya **kiraları**.</span><span class="sxs-lookup"><span data-stu-id="8adfb-198">To support concurrent access to a blob from multiple clients or multiple process instances, you can use **ETags** or **leases**.</span></span>

* <span data-ttu-id="8adfb-199">**ETag** -blob veya kapsayıcı başka bir işlem tarafından değiştirilmiş algılamak için bir yol sağlar</span><span class="sxs-lookup"><span data-stu-id="8adfb-199">**Etag** - provides a way to detect that the blob or container has been modified by another process</span></span>

* <span data-ttu-id="8adfb-200">**Kira** -özel ve yenilenebilir elde etmek, yazma veya silme bir süre için bir bloba erişimi için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="8adfb-200">**Lease** - provides a way to obtain exclusive, renewable, write or delete access to a blob for a period of time</span></span>

<span data-ttu-id="8adfb-201">Daha fazla bilgi için [Microsoft Azure Depolama'da eşzamanlılığı yönetme](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).</span><span class="sxs-lookup"><span data-stu-id="8adfb-201">For more information, see [Managing Concurrency in Microsoft Azure Storage](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).</span></span>

## <a name="naming-containers"></a><span data-ttu-id="8adfb-202">Kapsayıcı adlandırma</span><span class="sxs-lookup"><span data-stu-id="8adfb-202">Naming containers</span></span>

<span data-ttu-id="8adfb-203">Her blob Azure depolamadaki bir kapsayıcıda yer almalıdır.</span><span class="sxs-lookup"><span data-stu-id="8adfb-203">Every blob in Azure storage must reside in a container.</span></span> <span data-ttu-id="8adfb-204">Kapsayıcı, blob adının bir kısmını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8adfb-204">The container forms part of the blob name.</span></span> <span data-ttu-id="8adfb-205">Örneğin, `mydata` Bu örnek blob Urı'lerinde kapsayıcısında adıdır:</span><span class="sxs-lookup"><span data-stu-id="8adfb-205">For example, `mydata` is the name of the container in these sample blob URIs:</span></span>

    https://storagesample.blob.core.windows.net/mydata/blob1.txt
    https://storagesample.blob.core.windows.net/mydata/photos/myphoto.jpg

<span data-ttu-id="8adfb-206">Bir kapsayıcı adı, geçerli bir DNS adı, aşağıdaki adlandırma kurallarına uygun olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="8adfb-206">A container name must be a valid DNS name, conforming to the following naming rules:</span></span>

1. <span data-ttu-id="8adfb-207">Kapsayıcı adları bir harf veya sayı ile başlamalıdır ve yalnızca harf, rakam ve tire (-) karakteri içermelidir.</span><span class="sxs-lookup"><span data-stu-id="8adfb-207">Container names must start with a letter or number, and can contain only letters, numbers, and the dash (-) character.</span></span>
1. <span data-ttu-id="8adfb-208">Her tire (-) karakterinin hemen önünde ve bir harf veya rakam olmalıdır; kapsayıcı adlarında art arda tirelere izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="8adfb-208">Every dash (-) character must be immediately preceded and followed by a letter or number; consecutive dashes are not permitted in container names.</span></span>
1. <span data-ttu-id="8adfb-209">Kapsayıcı adındaki tüm harfler küçük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8adfb-209">All letters in a container name must be lowercase.</span></span>
1. <span data-ttu-id="8adfb-210">Kapsayıcı adları 3 ila 63 karakter uzunluğunda olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8adfb-210">Container names must be from 3 through 63 characters long.</span></span>

<span data-ttu-id="8adfb-211">Kapsayıcı adının her zaman küçük harfli olması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8adfb-211">Note that the name of a container must always be lowercase.</span></span> <span data-ttu-id="8adfb-212">Kapsayıcı adına bir büyük harf içerir ya da aksi takdirde kapsayıcı adlandırma kurallarını ihlal (Hatalı istek) 400 hatası alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8adfb-212">If you include an upper-case letter in a container name, or otherwise violate the container naming rules, you may receive a 400 error (Bad Request).</span></span>

## <a name="managing-security-for-blobs"></a><span data-ttu-id="8adfb-213">Blobların güvenliğini sağlama</span><span class="sxs-lookup"><span data-stu-id="8adfb-213">Managing security for blobs</span></span>

<span data-ttu-id="8adfb-214">Varsayılan olarak, Azure depolama, veri erişimi hesap erişim anahtarlarını elinde olan bir hesap sahibi sınırlayarak güvende tutar.</span><span class="sxs-lookup"><span data-stu-id="8adfb-214">By default, Azure Storage keeps your data secure by limiting access to the account owner, who is in possession of the account access keys.</span></span> <span data-ttu-id="8adfb-215">Depolama hesabınızda blob verileri paylaşmanız gerektiğinde bunu hesap erişim tuşlarınızı güvenliğini tehlikeye atmadan yapmak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="8adfb-215">When you need to share blob data in your storage account, it is important to do so without compromising the security of your account access keys.</span></span> <span data-ttu-id="8adfb-216">Ayrıca, aktarımda ve Azure Depolama'da güvenli olduğundan emin olmak için blob verilerini şifreleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8adfb-216">Additionally, you can encrypt blob data to ensure that it is secure going over the wire and in Azure Storage.</span></span>

### <a name="controlling-access-to-blob-data"></a><span data-ttu-id="8adfb-217">Blob verilerine erişimi denetleme</span><span class="sxs-lookup"><span data-stu-id="8adfb-217">Controlling access to blob data</span></span>

<span data-ttu-id="8adfb-218">Varsayılan olarak, depolama hesabınızdaki blob verileri yalnızca depolama hesabı sahibi erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="8adfb-218">By default, the blob data in your storage account is accessible only to storage account owner.</span></span> <span data-ttu-id="8adfb-219">Blob depolamaya yönelik isteklerine kimlik doğrulaması varsayılan olarak hesap erişim anahtarı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="8adfb-219">Authenticating requests against Blob storage requires the account access key by default.</span></span> <span data-ttu-id="8adfb-220">Ancak, belirli blob verilerinin diğer kullanıcılar tarafından kullanılabilmesini sağlamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8adfb-220">However, you might want to make certain blob data available to other users.</span></span>

<span data-ttu-id="8adfb-221">BLOB depolamaya erişimi denetleme hakkında daha fazla bilgi için bkz: [erişim denetimi için blob depolama bölümünde .NET Kılavuzu](/azure/storage/storage-dotnet-how-to-use-blobs#controlling-access-to-blob-data).</span><span class="sxs-lookup"><span data-stu-id="8adfb-221">For details on how to control access to blob storage, see [the .NET guide for blob storage section on access control](/azure/storage/storage-dotnet-how-to-use-blobs#controlling-access-to-blob-data).</span></span>


### <a name="encrypting-blob-data"></a><span data-ttu-id="8adfb-222">BLOB verilerini şifreleme</span><span class="sxs-lookup"><span data-stu-id="8adfb-222">Encrypting blob data</span></span>

<span data-ttu-id="8adfb-223">Azure Storage hem istemci hem de sunucuda blob verilerin şifrelenmesini destekler.</span><span class="sxs-lookup"><span data-stu-id="8adfb-223">Azure Storage supports encrypting blob data both at the client and on the server.</span></span>

<span data-ttu-id="8adfb-224">Blob verilerini şifreleme hakkında daha fazla bilgi için bkz [blob depolama bölümünde şifreleme için .NET Kılavuzu](/azure/storage/storage-dotnet-how-to-use-blobs#encrypting-blob-data).</span><span class="sxs-lookup"><span data-stu-id="8adfb-224">For details on encrypting blob data, see [the .NET guide for blob storage section on encryption](/azure/storage/storage-dotnet-how-to-use-blobs#encrypting-blob-data).</span></span>

## <a name="next-steps"></a><span data-ttu-id="8adfb-225">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="8adfb-225">Next steps</span></span>

<span data-ttu-id="8adfb-226">Blob storage'nın temellerini öğrendiğinize göre daha fazla bilgi için bu bağlantıları izleyin.</span><span class="sxs-lookup"><span data-stu-id="8adfb-226">Now that you've learned the basics of Blob storage, follow these links to learn more.</span></span>

### <a name="tools"></a><span data-ttu-id="8adfb-227">Araçlar</span><span class="sxs-lookup"><span data-stu-id="8adfb-227">Tools</span></span>
- <span data-ttu-id="8adfb-228">[F# AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/) bir F# tür Blob, tablo ve kuyruk Azure depolama varlıkları keşfedin ve bunları CRUD işlemleri kolayca uygulamak için kullanılan sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="8adfb-228">[F# AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/) An F# Type Provider which can be used to explore Blob, Table and Queue Azure Storage assets and easily apply CRUD operations on them.</span></span>
- <span data-ttu-id="8adfb-229">[FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage) bir F# Microsoft Azure tablo depolama hizmeti kullanım API'si</span><span class="sxs-lookup"><span data-stu-id="8adfb-229">[FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage) An F# API for using Microsoft Azure Table Storage service</span></span>
- <span data-ttu-id="8adfb-230">[Microsoft Azure Depolama Gezgini (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer) Microsoft'un Windows, OS X ve Linux'ta Azure depolama verileriyle görsel olarak çalışmanızı sağlayan ücretsiz, tek başına uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="8adfb-230">[Microsoft Azure Storage Explorer (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer) is a free, standalone app from Microsoft that enables you to work visually with Azure Storage data on Windows, OS X, and Linux.</span></span>

### <a name="blob-storage-reference"></a><span data-ttu-id="8adfb-231">BLOB storage başvurusu</span><span class="sxs-lookup"><span data-stu-id="8adfb-231">Blob storage reference</span></span>

- [<span data-ttu-id="8adfb-232">.NET için Azure depolama API'leri</span><span class="sxs-lookup"><span data-stu-id="8adfb-232">Azure Storage APIs for .NET</span></span>](/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="8adfb-233">Azure depolama hizmetleri REST API Başvurusu</span><span class="sxs-lookup"><span data-stu-id="8adfb-233">Azure Storage Services REST API Reference</span></span>](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)

### <a name="related-guides"></a><span data-ttu-id="8adfb-234">İlgili kılavuzları</span><span class="sxs-lookup"><span data-stu-id="8adfb-234">Related guides</span></span>

- [<span data-ttu-id="8adfb-235">C# ' de Azure Blob Depolama kullanmaya başlama</span><span class="sxs-lookup"><span data-stu-id="8adfb-235">Getting Started with Azure Blob Storage in C#</span></span>](https://azure.microsoft.com/resources/samples/storage-blob-dotnet-getting-started/)
- [<span data-ttu-id="8adfb-236">Windows üzerinde AzCopy komut satırı yardımcı programı ile veri aktarma</span><span class="sxs-lookup"><span data-stu-id="8adfb-236">Transfer data with the AzCopy command-line utility on Windows</span></span>](/azure/storage/common/storage-use-azcopy)
- [<span data-ttu-id="8adfb-237">Linux üzerinde AzCopy komut satırı yardımcı programı ile veri aktarma</span><span class="sxs-lookup"><span data-stu-id="8adfb-237">Transfer data with the AzCopy command-line utility on Linux</span></span>](/azure/storage/common/storage-use-azcopy-linux)
- [<span data-ttu-id="8adfb-238">Azure Storage bağlantı dizelerini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="8adfb-238">Configure Azure Storage connection strings</span></span>](/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="8adfb-239">Azure depolama ekibi blogu</span><span class="sxs-lookup"><span data-stu-id="8adfb-239">Azure Storage Team Blog</span></span>](https://blogs.msdn.microsoft.com/windowsazurestorage/)
