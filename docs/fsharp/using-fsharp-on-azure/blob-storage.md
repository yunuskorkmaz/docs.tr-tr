---
title: F# kullanarak Azure Blob depolama kullanmaya başlama
description: Azure Blob depolama ile yapılandırılmamış verileri bulutta depolayın.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: c8b42339ff1d76f262e956b5e34cc598e0fc855d
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630516"
---
# <a name="get-started-with-azure-blob-storage-using-f"></a><span data-ttu-id="9dffd-103">F kullanarak Azure Blob depolama ile çalışmaya başlama\#</span><span class="sxs-lookup"><span data-stu-id="9dffd-103">Get started with Azure Blob storage using F\#</span></span>

<span data-ttu-id="9dffd-104">Azure Blob depolama, bulutta nesne/blob olarak yapılandırılmamış verileri depolayan bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="9dffd-104">Azure Blob storage is a service that stores unstructured data in the cloud as objects/blobs.</span></span> <span data-ttu-id="9dffd-105">BLOB depolama, bir belge, medya dosyası veya uygulama yükleyicisi gibi herhangi bir tür metin veya ikili veri saklayabilir.</span><span class="sxs-lookup"><span data-stu-id="9dffd-105">Blob storage can store any type of text or binary data, such as a document, media file, or application installer.</span></span> <span data-ttu-id="9dffd-106">BLOB depolama alanı da nesne depolama olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="9dffd-106">Blob storage is also referred to as object storage.</span></span>

<span data-ttu-id="9dffd-107">Bu makalede, blob depolamayı kullanarak genel görevlerin nasıl gerçekleştirileceği gösterilir.</span><span class="sxs-lookup"><span data-stu-id="9dffd-107">This article shows you how to perform common tasks using Blob storage.</span></span> <span data-ttu-id="9dffd-108">Örnekler, .NET için Azure F# Storage istemci kitaplığı kullanılarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="9dffd-108">The samples are written using F# using the Azure Storage Client Library for .NET.</span></span> <span data-ttu-id="9dffd-109">Kapsanan görevler, Blobları karşıya yükleme, listeleme, indirme ve silme işlemleri içerir.</span><span class="sxs-lookup"><span data-stu-id="9dffd-109">The tasks covered include how to upload, list, download, and delete blobs.</span></span>

<span data-ttu-id="9dffd-110">Blob depolamaya kavramsal bir genel bakış için bkz. [BLOB depolama için .net Kılavuzu](/azure/storage/storage-dotnet-how-to-use-blobs).</span><span class="sxs-lookup"><span data-stu-id="9dffd-110">For a conceptual overview of blob storage, see [the .NET guide for blob storage](/azure/storage/storage-dotnet-how-to-use-blobs).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9dffd-111">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="9dffd-111">Prerequisites</span></span>

<span data-ttu-id="9dffd-112">Bu kılavuzu kullanmak için önce [bir Azure depolama hesabı oluşturmanız](/azure/storage/storage-create-storage-account)gerekir.</span><span class="sxs-lookup"><span data-stu-id="9dffd-112">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span> <span data-ttu-id="9dffd-113">Bu hesap için depolama erişim anahtarınıza de ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="9dffd-113">You also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="9dffd-114">F# Betik oluşturma ve etkileşimli başlatma F#</span><span class="sxs-lookup"><span data-stu-id="9dffd-114">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="9dffd-115">Bu makaledeki örnekler, bir F# uygulama ya da bir F# komut dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9dffd-115">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="9dffd-116">Bir F# betik oluşturmak için, örneğin `.fsx` `blobs.fsx`, F# geliştirme ortamınızda uzantılı bir dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9dffd-116">To create an F# script, create a file with the `.fsx` extension, for example `blobs.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="9dffd-117">Ardından, bir `WindowsAzure.Storage` `Microsoft.WindowsAzure.ConfigurationManager` `WindowsAzure.Storage.dll` [](https://fsprojects.github.io/Paket/) `Microsoft.WindowsAzure.Configuration.dll` [](https://www.nuget.org/) yönergesikullanarakvepaketlerinivebaşvurusunuyüklemekiçinpaketveyaNuGet`#r` gibi bir [Paket Yöneticisi](package-management.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="9dffd-117">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` and `Microsoft.WindowsAzure.ConfigurationManager` packages and reference `WindowsAzure.Storage.dll` and `Microsoft.WindowsAzure.Configuration.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="9dffd-118">Ad alanı bildirimleri ekle</span><span class="sxs-lookup"><span data-stu-id="9dffd-118">Add namespace declarations</span></span>

<span data-ttu-id="9dffd-119">Aşağıdaki `open` deyimlerini `blobs.fsx` dosyanın en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="9dffd-119">Add the following `open` statements to the top of the `blobs.fsx` file:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a><span data-ttu-id="9dffd-120">Bağlantı dizenizi alın</span><span class="sxs-lookup"><span data-stu-id="9dffd-120">Get your connection string</span></span>

<span data-ttu-id="9dffd-121">Bu öğretici için bir Azure depolama bağlantı dizesine ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="9dffd-121">You need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="9dffd-122">Bağlantı dizeleri hakkında daha fazla bilgi için bkz. [depolama bağlantı dizelerini yapılandırma](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="9dffd-122">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="9dffd-123">Öğreticide, Bağlantı dizenizi aşağıdaki gibi bir betiğe girersiniz:</span><span class="sxs-lookup"><span data-stu-id="9dffd-123">For the tutorial, you enter your connection string in your script, like this:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L11-L11)]

<span data-ttu-id="9dffd-124">Ancak, bu gerçek projeler için **önerilmez** .</span><span class="sxs-lookup"><span data-stu-id="9dffd-124">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="9dffd-125">Depolama hesabı anahtarınız, depolama hesabınızın kök parolasıyla benzerdir.</span><span class="sxs-lookup"><span data-stu-id="9dffd-125">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="9dffd-126">Depolama hesabı anahtarınızı korumak için her zaman özen gösterin.</span><span class="sxs-lookup"><span data-stu-id="9dffd-126">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="9dffd-127">Diğer kullanıcılara dağıtmaktan, sabit kodlamaktan ve başkalarının erişebileceği düz metin dosyasına kaydetmekten kaçının.</span><span class="sxs-lookup"><span data-stu-id="9dffd-127">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="9dffd-128">Güvenliğinin tehlikede olduğunu düşünüyorsanız, Azure portalını kullanarak anahtarınızı yeniden oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9dffd-128">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="9dffd-129">Gerçek uygulamalar için, depolama Bağlantı dizenizi korumak için en iyi yol bir yapılandırma dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="9dffd-129">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="9dffd-130">Bağlantı dizesini bir yapılandırma dosyasından getirmek için şunu yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9dffd-130">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L13-L15)]

<span data-ttu-id="9dffd-131">Azure Configuration Manager kullanmak isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="9dffd-131">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="9dffd-132">.NET Framework `ConfigurationManager` türü gibi bir API de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9dffd-132">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="9dffd-133">Bağlantı dizesini ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="9dffd-133">Parse the connection string</span></span>

<span data-ttu-id="9dffd-134">Bağlantı dizesini ayrıştırmak için şunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="9dffd-134">To parse the connection string, use:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L21-L22)]

<span data-ttu-id="9dffd-135">Bu, bir `CloudStorageAccount`döndürür.</span><span class="sxs-lookup"><span data-stu-id="9dffd-135">This returns a `CloudStorageAccount`.</span></span>

### <a name="create-some-local-dummy-data"></a><span data-ttu-id="9dffd-136">Bazı yerel kukla veriler oluşturma</span><span class="sxs-lookup"><span data-stu-id="9dffd-136">Create some local dummy data</span></span>

<span data-ttu-id="9dffd-137">Başlamadan önce, betiğimizin dizininde bazı sözde yerel veriler oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9dffd-137">Before you begin, create some dummy local data in the directory of our script.</span></span> <span data-ttu-id="9dffd-138">Daha sonra bu verileri karşıya yüklersiniz.</span><span class="sxs-lookup"><span data-stu-id="9dffd-138">Later you upload this data.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L28-L30)]

### <a name="create-the-blob-service-client"></a><span data-ttu-id="9dffd-139">Blob hizmeti istemcisini oluşturma</span><span class="sxs-lookup"><span data-stu-id="9dffd-139">Create the Blob service client</span></span>

<span data-ttu-id="9dffd-140">Tür `CloudBlobClient` , blob depolamada depolanan kapsayıcıları ve Blobları almanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="9dffd-140">The `CloudBlobClient` type enables you to retrieve containers and blobs stored in Blob storage.</span></span> <span data-ttu-id="9dffd-141">Hizmet istemcisini oluşturmak için bir yol aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="9dffd-141">Here's one way to create the service client:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L36-L36)]

<span data-ttu-id="9dffd-142">Artık BLOB depolama alanına veri okuyan ve veri yazan kodu yazmaya hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="9dffd-142">Now you are ready to write code that reads data from and writes data to Blob storage.</span></span>

## <a name="create-a-container"></a><span data-ttu-id="9dffd-143">Kapsayıcı oluşturma</span><span class="sxs-lookup"><span data-stu-id="9dffd-143">Create a container</span></span>

<span data-ttu-id="9dffd-144">Bu örnek, zaten yoksa kapsayıcının nasıl oluşturulacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="9dffd-144">This example shows how to create a container if it does not already exist:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L42-L46)]

<span data-ttu-id="9dffd-145">Varsayılan olarak, yeni kapsayıcı özeldir ve bu kapsayıcıdan blob 'ları indirmek için depolama erişim anahtarınızı belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9dffd-145">By default, the new container is private, meaning that you must specify your storage access key to download blobs from this container.</span></span> <span data-ttu-id="9dffd-146">Kapsayıcıdaki dosyaları herkes için kullanılabilir hale getirmek istiyorsanız, kapsayıcıyı aşağıdaki kodu kullanarak genel olacak şekilde ayarlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9dffd-146">If you want to make the files within the container available to everyone, you can set the container to be public using the following code:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L48-L49)]

<span data-ttu-id="9dffd-147">Internet 'teki herkes blob 'ları ortak bir kapsayıcıda görebilir, ancak yalnızca uygun hesap erişim anahtarı veya paylaşılan erişim imzanız varsa bunları değiştirebilir veya silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9dffd-147">Anyone on the Internet can see blobs in a public container, but you can modify or delete them only if you have the appropriate account access key or a shared access signature.</span></span>

## <a name="upload-a-blob-into-a-container"></a><span data-ttu-id="9dffd-148">Bir blobu bir kapsayıcıya yükleme</span><span class="sxs-lookup"><span data-stu-id="9dffd-148">Upload a blob into a container</span></span>

<span data-ttu-id="9dffd-149">Azure Blob depolama, blok bloblarını ve sayfa bloblarını destekler.</span><span class="sxs-lookup"><span data-stu-id="9dffd-149">Azure Blob Storage supports block blobs and page blobs.</span></span> <span data-ttu-id="9dffd-150">Çoğu durumda, Blok Blobu kullanılacak önerilen türdür.</span><span class="sxs-lookup"><span data-stu-id="9dffd-150">In most cases, a block blob is the recommended type to use.</span></span>

<span data-ttu-id="9dffd-151">Bir blok blobuna bir dosya yüklemek için bir kapsayıcı başvurusu alın ve bunu bir Blok Blobu başvurusu almak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="9dffd-151">To upload a file to a block blob, get a container reference and use it to get a block blob reference.</span></span> <span data-ttu-id="9dffd-152">Blob başvurunuz olduktan sonra, `UploadFromFile` yöntemini çağırarak herhangi bir veri akışını bu akışa yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9dffd-152">Once you have a blob reference, you can upload any stream of data to it by calling the `UploadFromFile` method.</span></span> <span data-ttu-id="9dffd-153">Bu işlem, daha önce yoksa blobu oluşturur veya varsa üzerine yazar.</span><span class="sxs-lookup"><span data-stu-id="9dffd-153">This operation creates the blob if it didn't previously exist, or overwrite it if it does exist.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L55-L59)]

## <a name="list-the-blobs-in-a-container"></a><span data-ttu-id="9dffd-154">Bir kapsayıcıdaki Blobları listeleme</span><span class="sxs-lookup"><span data-stu-id="9dffd-154">List the blobs in a container</span></span>

<span data-ttu-id="9dffd-155">Bir kapsayıcıdaki Blobları listelemek için, önce bir kapsayıcı başvurusu alın.</span><span class="sxs-lookup"><span data-stu-id="9dffd-155">To list the blobs in a container, first get a container reference.</span></span> <span data-ttu-id="9dffd-156">Daha sonra kapsayıcı ve/veya dizinlerini `ListBlobs` almak için kapsayıcının yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9dffd-156">You can then use the container's `ListBlobs` method to retrieve the blobs and/or directories within it.</span></span> <span data-ttu-id="9dffd-157">Döndürülen `IListBlobItem`zengin özellik kümesine ve yöntemlere erişmek için, bir `CloudBlockBlob`, `CloudPageBlob`veya `CloudBlobDirectory` nesnesine atamalısınız.</span><span class="sxs-lookup"><span data-stu-id="9dffd-157">To access the rich set of properties and methods for a returned `IListBlobItem`, you must cast it to a `CloudBlockBlob`, `CloudPageBlob`, or `CloudBlobDirectory` object.</span></span> <span data-ttu-id="9dffd-158">Tür bilinmiyorsa, ne tür denetimi kullanacağınızı anlamak için bir tür denetimi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9dffd-158">If the type is unknown, you can use a type check to determine which to cast it to.</span></span> <span data-ttu-id="9dffd-159">Aşağıdaki kod, `mydata` kapsayıcıdaki her bir öğenin URI 'sini alma ve çıkışın nasıl yapılacağını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="9dffd-159">The following code demonstrates how to retrieve and output the URI of each item in the `mydata` container:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L67-L80)]

<span data-ttu-id="9dffd-160">Bloblarını adlarına yol bilgileriyle de girebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9dffd-160">You can also name blobs with path information in their names.</span></span> <span data-ttu-id="9dffd-161">Bu, geleneksel bir dosya sisteminde olduğu gibi düzenleme ve geçiş yapabileceğiniz bir sanal dizin yapısı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9dffd-161">This creates a virtual directory structure that you can organize and traverse as you would a traditional file system.</span></span> <span data-ttu-id="9dffd-162">Dizin yapısının yalnızca sanal olduğunu unutmayın. blob depolamada kullanılabilen tek kaynak, kapsayıcılar ve bloblardır.</span><span class="sxs-lookup"><span data-stu-id="9dffd-162">Note that the directory structure is virtual only - the only resources available in Blob storage are containers and blobs.</span></span> <span data-ttu-id="9dffd-163">Ancak, depolama istemci kitaplığı bir sanal dizine `CloudBlobDirectory` başvuracak bir nesne sunar ve bu şekilde düzenlenmiş bloblarla çalışma sürecini basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="9dffd-163">However, the storage client library offers a `CloudBlobDirectory` object to refer to a virtual directory and simplify the process of working with blobs that are organized in this way.</span></span>

<span data-ttu-id="9dffd-164">Örneğin, aşağıdaki adlı `photos`kapsayıcıda bulunan blok Blobları kümesini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="9dffd-164">For example, consider the following set of block blobs in a container named `photos`:</span></span>

<span data-ttu-id="9dffd-165">*photo1. jpg*</span><span class="sxs-lookup"><span data-stu-id="9dffd-165">*photo1.jpg*</span></span>\
<span data-ttu-id="9dffd-166">*2015/mimari/Description. txt*</span><span class="sxs-lookup"><span data-stu-id="9dffd-166">*2015/architecture/description.txt*</span></span>\
<span data-ttu-id="9dffd-167">*2015/Architecture/photo3. jpg*</span><span class="sxs-lookup"><span data-stu-id="9dffd-167">*2015/architecture/photo3.jpg*</span></span>\
<span data-ttu-id="9dffd-168">*2015/Architecture/photo4. jpg*</span><span class="sxs-lookup"><span data-stu-id="9dffd-168">*2015/architecture/photo4.jpg*</span></span>\
<span data-ttu-id="9dffd-169">*2016/Architecture/photo5. jpg*</span><span class="sxs-lookup"><span data-stu-id="9dffd-169">*2016/architecture/photo5.jpg*</span></span>\
<span data-ttu-id="9dffd-170">*2016/Architecture/photo6. jpg*</span><span class="sxs-lookup"><span data-stu-id="9dffd-170">*2016/architecture/photo6.jpg*</span></span>\
<span data-ttu-id="9dffd-171">*2016/mimari/Description. txt*</span><span class="sxs-lookup"><span data-stu-id="9dffd-171">*2016/architecture/description.txt*</span></span>\
<span data-ttu-id="9dffd-172">*2016/photo7. jpg*</span><span class="sxs-lookup"><span data-stu-id="9dffd-172">*2016/photo7.jpg*</span></span>\

<span data-ttu-id="9dffd-173">Bir kapsayıcıda ( `ListBlobs` Yukarıdaki örnekte olduğu gibi) çağırdığınızda, hiyerarşik bir liste döndürülür.</span><span class="sxs-lookup"><span data-stu-id="9dffd-173">When you call `ListBlobs` on a container (as in the above sample), a hierarchical listing is returned.</span></span> <span data-ttu-id="9dffd-174">Hem hem de `CloudBlobDirectory` `CloudBlockBlob` nesneler içeriyorsa, kapsayıcıda dizin ve Blobları temsil eder, sonuçta elde edilen çıktı şuna benzer:</span><span class="sxs-lookup"><span data-stu-id="9dffd-174">If it contains both `CloudBlobDirectory` and `CloudBlockBlob` objects, representing the directories and blobs in the container, respectively, then the resulting output looks similar to this:</span></span>

```console
Directory: https://<accountname>.blob.core.windows.net/photos/2015/
Directory: https://<accountname>.blob.core.windows.net/photos/2016/
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

<span data-ttu-id="9dffd-175">İsteğe bağlı olarak, `UseFlatBlobListing` `ListBlobs` yönteminin parametresini olarak `true`ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9dffd-175">Optionally, you can set the `UseFlatBlobListing` parameter of the `ListBlobs` method to `true`.</span></span> <span data-ttu-id="9dffd-176">Bu durumda, kapsayıcıdaki her blob bir `CloudBlockBlob` nesne olarak döndürülür.</span><span class="sxs-lookup"><span data-stu-id="9dffd-176">In this case, every blob in the container is returned as a `CloudBlockBlob` object.</span></span> <span data-ttu-id="9dffd-177">Düz bir liste `ListBlobs` döndürmek için çağrısı şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="9dffd-177">The call to `ListBlobs` to return a flat listing looks like this:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L82-L89)]

<span data-ttu-id="9dffd-178">kapsayıcının geçerli içeriğine bağlı olarak, sonuçlar şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="9dffd-178">and, depending on the current contents of your container, the results look like this:</span></span>

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

## <a name="download-blobs"></a><span data-ttu-id="9dffd-179">Blob 'ları indir</span><span class="sxs-lookup"><span data-stu-id="9dffd-179">Download blobs</span></span>

<span data-ttu-id="9dffd-180">Blob 'ları indirmek için önce bir blob başvurusu alın ve sonra `DownloadToStream` yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="9dffd-180">To download blobs, first retrieve a blob reference and then call the `DownloadToStream` method.</span></span> <span data-ttu-id="9dffd-181">Aşağıdaki örnek, blob içeriğini `DownloadToStream` bir Stream nesnesine aktarmak için, daha sonra yerel bir dosyada kalıcı hale getirebilmeniz için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="9dffd-181">The following example uses the `DownloadToStream` method to transfer the blob contents to a stream object that you can then persist to a local file.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L95-L101)]

<span data-ttu-id="9dffd-182">Bir Blobun içeriğini bir `DownloadToStream` metin dizesi olarak indirmek için yöntemini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9dffd-182">You can also use the `DownloadToStream` method to download the contents of a blob as a text string.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L103-L106)]

## <a name="delete-blobs"></a><span data-ttu-id="9dffd-183">Blob 'ları silme</span><span class="sxs-lookup"><span data-stu-id="9dffd-183">Delete blobs</span></span>

<span data-ttu-id="9dffd-184">Bir blobu silmek için önce bir blob başvurusu alın ve ardından üzerinde `Delete` yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="9dffd-184">To delete a blob, first get a blob reference and then call the `Delete` method on it.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L112-L116)]

## <a name="list-blobs-in-pages-asynchronously"></a><span data-ttu-id="9dffd-185">Sayfalardaki Blobları zaman uyumsuz olarak Listele</span><span class="sxs-lookup"><span data-stu-id="9dffd-185">List blobs in pages asynchronously</span></span>

<span data-ttu-id="9dffd-186">Çok sayıda blob listelemeyi veya bir listeleme işleminde geri aldığınız sonuçların sayısını denetlemek istiyorsanız, blob 'ların sonuçları sayfalarında listeleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9dffd-186">If you are listing a large number of blobs, or you want to control the number of results you return in one listing operation, you can list blobs in pages of results.</span></span> <span data-ttu-id="9dffd-187">Bu örnek, büyük bir sonuç kümesi döndürmeyi beklerken yürütmenin engellenmemesi için sayfaların zaman uyumsuz olarak nasıl döndürülmeyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9dffd-187">This example shows how to return results in pages asynchronously, so that execution is not blocked while waiting to return a large set of results.</span></span>

<span data-ttu-id="9dffd-188">Bu örnek, düz bir blob listesini gösterir, ancak `useFlatBlobListing` `ListBlobsSegmentedAsync` yönteminin parametresini olarak `false`ayarlayarak hiyerarşik bir liste da gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9dffd-188">This example shows a flat blob listing, but you can also perform a hierarchical listing, by setting the `useFlatBlobListing` parameter of the `ListBlobsSegmentedAsync` method to `false`.</span></span>

<span data-ttu-id="9dffd-189">Örnek, `async` blok kullanarak bir zaman uyumsuz yöntemi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9dffd-189">The sample defines an asynchronous method, using an `async` block.</span></span> <span data-ttu-id="9dffd-190">``let!`` Anahtar sözcüğü, listeleme görevi tamamlanana kadar örnek yöntemi yürütmeyi askıya alır.</span><span class="sxs-lookup"><span data-stu-id="9dffd-190">The ``let!`` keyword suspends execution of the sample method until the listing task completes.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L122-L160)]

<span data-ttu-id="9dffd-191">Artık bu zaman uyumsuz yordamı aşağıdaki gibi kullanabiliriz.</span><span class="sxs-lookup"><span data-stu-id="9dffd-191">We can now use this asynchronous routine as follows.</span></span> <span data-ttu-id="9dffd-192">İlk olarak bazı kukla verileri karşıya yüklersiniz (Bu öğreticide daha önce oluşturulan yerel dosyayı kullanarak).</span><span class="sxs-lookup"><span data-stu-id="9dffd-192">First you upload some dummy data (using the local file created earlier in this tutorial).</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L162-L166)]

<span data-ttu-id="9dffd-193">Şimdi, yordamını çağırın.</span><span class="sxs-lookup"><span data-stu-id="9dffd-193">Now, call the routine.</span></span> <span data-ttu-id="9dffd-194">Zaman uyumsuz `Async.RunSynchronously` işlemin yürütülmesini zorlamak için kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="9dffd-194">You use `Async.RunSynchronously` to force the execution of the asynchronous operation.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L168-L168)]

## <a name="writing-to-an-append-blob"></a><span data-ttu-id="9dffd-195">Ekleme blobuna yazma</span><span class="sxs-lookup"><span data-stu-id="9dffd-195">Writing to an append blob</span></span>

<span data-ttu-id="9dffd-196">Append blobu, günlüğe kaydetme gibi ekleme işlemleri için iyileştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9dffd-196">An append blob is optimized for append operations, such as logging.</span></span> <span data-ttu-id="9dffd-197">Bir blok blobu gibi, bir ekleme blobu bloklardan oluşur, ancak ekleme blobuna yeni bir blok eklediğinizde, her zaman blob 'un sonuna eklenir.</span><span class="sxs-lookup"><span data-stu-id="9dffd-197">Like a block blob, an append blob is comprised of blocks, but when you add a new block to an append blob, it is always appended to the end of the blob.</span></span> <span data-ttu-id="9dffd-198">Ekleme blobundan var olan bir bloğu güncelleştiremez veya silemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="9dffd-198">You cannot update or delete an existing block in an append blob.</span></span> <span data-ttu-id="9dffd-199">Bir ekleme Blobun blok kimlikleri bir Blok Blobu için olduğu gibi gösterilmez.</span><span class="sxs-lookup"><span data-stu-id="9dffd-199">The block IDs for an append blob are not exposed as they are for a block blob.</span></span>

<span data-ttu-id="9dffd-200">Bir ekleme blobunun her bloğu, en fazla 4 MB olmak üzere farklı bir boyut olabilir ve bir ekleme blobu en fazla 50.000 blok içerebilir.</span><span class="sxs-lookup"><span data-stu-id="9dffd-200">Each block in an append blob can be a different size, up to a maximum of 4 MB, and an append blob can include a maximum of 50,000 blocks.</span></span> <span data-ttu-id="9dffd-201">Bu nedenle, bir ekleme Blobun en büyük boyutu 195 GB 'den (4 MB X 50.000 blok) biraz daha fazla.</span><span class="sxs-lookup"><span data-stu-id="9dffd-201">The maximum size of an append blob is therefore slightly more than 195 GB (4 MB X 50,000 blocks).</span></span>

<span data-ttu-id="9dffd-202">Aşağıdaki örnek, yeni bir ekleme blobu oluşturur ve basit bir günlüğe kaydetme işleminin benzetimini yapar ve buna veri ekler.</span><span class="sxs-lookup"><span data-stu-id="9dffd-202">The following example creates a new append blob and appends some data to it, simulating a simple logging operation.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L174-L203)]

<span data-ttu-id="9dffd-203">Üç tür blob arasındaki farklar hakkında daha fazla bilgi için bkz. [blok bloblarını, sayfa bloblarını ve ekleme Bloblarını anlama](https://msdn.microsoft.com/library/azure/ee691964.aspx) .</span><span class="sxs-lookup"><span data-stu-id="9dffd-203">See [Understanding Block Blobs, Page Blobs, and Append Blobs](https://msdn.microsoft.com/library/azure/ee691964.aspx) for more information about the differences between the three types of blobs.</span></span>

## <a name="concurrent-access"></a><span data-ttu-id="9dffd-204">Eşzamanlı erişim</span><span class="sxs-lookup"><span data-stu-id="9dffd-204">Concurrent access</span></span>

<span data-ttu-id="9dffd-205">Birden fazla istemciden veya birden çok işlem örneğiyle bir Blobun eşzamanlı erişimini desteklemek için **ETags** veya **kiralamalar**kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9dffd-205">To support concurrent access to a blob from multiple clients or multiple process instances, you can use **ETags** or **leases**.</span></span>

* <span data-ttu-id="9dffd-206">**ETag** -Blobun veya kapsayıcının başka bir işlem tarafından değiştirildiğini algılamaya yönelik bir yol sağlar</span><span class="sxs-lookup"><span data-stu-id="9dffd-206">**Etag** - provides a way to detect that the blob or container has been modified by another process</span></span>

* <span data-ttu-id="9dffd-207">**Kira** -bir zaman dilimi için bir Blobun özel, yenilenebilir, yazma veya silme erişimi elde etmek için bir yol sağlar</span><span class="sxs-lookup"><span data-stu-id="9dffd-207">**Lease** - provides a way to obtain exclusive, renewable, write or delete access to a blob for a period of time</span></span>

<span data-ttu-id="9dffd-208">Daha fazla bilgi için bkz. [Microsoft Azure depolama eşzamanlılık yönetimi](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).</span><span class="sxs-lookup"><span data-stu-id="9dffd-208">For more information, see [Managing Concurrency in Microsoft Azure Storage](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).</span></span>

## <a name="naming-containers"></a><span data-ttu-id="9dffd-209">Kapsayıcıları adlandırma</span><span class="sxs-lookup"><span data-stu-id="9dffd-209">Naming containers</span></span>

<span data-ttu-id="9dffd-210">Azure Storage 'daki her blob bir kapsayıcıda yer almalıdır.</span><span class="sxs-lookup"><span data-stu-id="9dffd-210">Every blob in Azure storage must reside in a container.</span></span> <span data-ttu-id="9dffd-211">Kapsayıcı, blob adının bir parçasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9dffd-211">The container forms part of the blob name.</span></span> <span data-ttu-id="9dffd-212">Örneğin, `mydata` Bu örnek blob URI 'lerinde kapsayıcının adıdır:</span><span class="sxs-lookup"><span data-stu-id="9dffd-212">For example, `mydata` is the name of the container in these sample blob URIs:</span></span>

- https://storagesample.blob.core.windows.net/mydata/blob1.txt
- https://storagesample.blob.core.windows.net/mydata/photos/myphoto.jpg

<span data-ttu-id="9dffd-213">Bir kapsayıcı adı, aşağıdaki adlandırma kurallarına uyan geçerli bir DNS adı olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="9dffd-213">A container name must be a valid DNS name, conforming to the following naming rules:</span></span>

1. <span data-ttu-id="9dffd-214">Kapsayıcı adları bir harf veya sayıyla başlamalıdır ve yalnızca harf, rakam ve tire (-) karakterini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="9dffd-214">Container names must start with a letter or number, and can contain only letters, numbers, and the dash (-) character.</span></span>
1. <span data-ttu-id="9dffd-215">Her Dash (-) karakteri hemen önce ve ardından bir harf veya sayı gelmelidir; kapsayıcı adlarında ardışık kesik çizgilerden izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="9dffd-215">Every dash (-) character must be immediately preceded and followed by a letter or number; consecutive dashes are not permitted in container names.</span></span>
1. <span data-ttu-id="9dffd-216">Bir kapsayıcı adındaki tüm harflerin küçük harf olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9dffd-216">All letters in a container name must be lowercase.</span></span>
1. <span data-ttu-id="9dffd-217">Kapsayıcı adları 3 ila 63 karakter uzunluğunda olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9dffd-217">Container names must be from 3 through 63 characters long.</span></span>

<span data-ttu-id="9dffd-218">Kapsayıcının adının her zaman küçük harfli olması gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9dffd-218">Note that the name of a container must always be lowercase.</span></span> <span data-ttu-id="9dffd-219">Bir kapsayıcı adına bir büyük harfli harf eklerseniz veya kapsayıcı adlandırma kurallarını ihlal ederseniz, bir 400 hatası (Hatalı Istek) alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9dffd-219">If you include an upper-case letter in a container name, or otherwise violate the container naming rules, you may receive a 400 error (Bad Request).</span></span>

## <a name="managing-security-for-blobs"></a><span data-ttu-id="9dffd-220">Blobların güvenliğini yönetme</span><span class="sxs-lookup"><span data-stu-id="9dffd-220">Managing security for blobs</span></span>

<span data-ttu-id="9dffd-221">Varsayılan olarak, Azure depolama, hesap erişim anahtarlarına sahip olan hesap sahibine erişimi sınırlandırarak verilerinizi güvende tutar.</span><span class="sxs-lookup"><span data-stu-id="9dffd-221">By default, Azure Storage keeps your data secure by limiting access to the account owner, who is in possession of the account access keys.</span></span> <span data-ttu-id="9dffd-222">Depolama hesabınızda blob verilerini paylaşmanız gerektiğinde, hesap erişim anahtarlarınızın güvenliğine ödün vermeden bunu yapmak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="9dffd-222">When you need to share blob data in your storage account, it is important to do so without compromising the security of your account access keys.</span></span> <span data-ttu-id="9dffd-223">Ayrıca, Azure depolama 'da ve Azure Storage 'da güvenli olduğundan emin olmak için blob verilerini şifreleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9dffd-223">Additionally, you can encrypt blob data to ensure that it is secure going over the wire and in Azure Storage.</span></span>

### <a name="controlling-access-to-blob-data"></a><span data-ttu-id="9dffd-224">Blob verilerine erişimi denetleme</span><span class="sxs-lookup"><span data-stu-id="9dffd-224">Controlling access to blob data</span></span>

<span data-ttu-id="9dffd-225">Varsayılan olarak, Depolama hesabınızdaki blob verilerine yalnızca depolama hesabı sahibine erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="9dffd-225">By default, the blob data in your storage account is accessible only to storage account owner.</span></span> <span data-ttu-id="9dffd-226">Blob depolamaya karşı istekleri doğrulamak, varsayılan olarak hesap erişim anahtarı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="9dffd-226">Authenticating requests against Blob storage requires the account access key by default.</span></span> <span data-ttu-id="9dffd-227">Ancak, bazı blob verilerini diğer kullanıcılar için kullanılabilir hale getirmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9dffd-227">However, you might want to make certain blob data available to other users.</span></span>

### <a name="encrypting-blob-data"></a><span data-ttu-id="9dffd-228">Blob verilerini şifreleme</span><span class="sxs-lookup"><span data-stu-id="9dffd-228">Encrypting blob data</span></span>

<span data-ttu-id="9dffd-229">Azure depolama, blob verilerini hem istemcide hem de sunucuda şifrelemeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="9dffd-229">Azure Storage supports encrypting blob data both at the client and on the server.</span></span>

## <a name="next-steps"></a><span data-ttu-id="9dffd-230">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="9dffd-230">Next steps</span></span>

<span data-ttu-id="9dffd-231">BLOB depolama hakkında temel bilgileri öğrendiğinize göre, daha fazla bilgi edinmek için bu bağlantıları izleyin.</span><span class="sxs-lookup"><span data-stu-id="9dffd-231">Now that you've learned the basics of Blob storage, follow these links to learn more.</span></span>

### <a name="tools"></a><span data-ttu-id="9dffd-232">Araçlar</span><span class="sxs-lookup"><span data-stu-id="9dffd-232">Tools</span></span>

- <span data-ttu-id="9dffd-233">[F#Azurestooygettypeınfo sağlayıcısı](https://fsprojects.github.io/AzureStorageTypeProvider/)</span><span class="sxs-lookup"><span data-stu-id="9dffd-233">[F# AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/)</span></span>\
<span data-ttu-id="9dffd-234">Blob F# , tablo ve kuyruk Azure depolama varlıklarını araştırmak ve bunlara kolayca CRUD işlemleri uygulamak için kullanılabilen bir tür sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="9dffd-234">An F# Type Provider which can be used to explore Blob, Table and Queue Azure Storage assets and easily apply CRUD operations on them.</span></span>

- <span data-ttu-id="9dffd-235">[FSharp. Azure. Storage](https://github.com/fsprojects/FSharp.Azure.Storage)</span><span class="sxs-lookup"><span data-stu-id="9dffd-235">[FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage)</span></span>\
<span data-ttu-id="9dffd-236">Microsoft Azure F# tablo depolama hizmeti kullanmak için bir API</span><span class="sxs-lookup"><span data-stu-id="9dffd-236">An F# API for using Microsoft Azure Table Storage service</span></span>

- <span data-ttu-id="9dffd-237">[Microsoft Azure Depolama Gezgini (Mao)](/azure/vs-azure-tools-storage-manage-with-storage-explorer)</span><span class="sxs-lookup"><span data-stu-id="9dffd-237">[Microsoft Azure Storage Explorer (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer)</span></span>\
<span data-ttu-id="9dffd-238">Microsoft 'un Windows, OS X ve Linux üzerinde Azure Depolama verileriyle görsel olarak çalışmanızı sağlayan ücretsiz ve tek başına bir uygulama.</span><span class="sxs-lookup"><span data-stu-id="9dffd-238">A free, standalone app from Microsoft that enables you to work visually with Azure Storage data on Windows, OS X, and Linux.</span></span>

### <a name="blob-storage-reference"></a><span data-ttu-id="9dffd-239">BLOB depolama başvurusu</span><span class="sxs-lookup"><span data-stu-id="9dffd-239">Blob storage reference</span></span>

- [<span data-ttu-id="9dffd-240">.NET için Azure depolama API 'Leri</span><span class="sxs-lookup"><span data-stu-id="9dffd-240">Azure Storage APIs for .NET</span></span>](/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="9dffd-241">Azure depolama hizmetleri REST API başvurusu</span><span class="sxs-lookup"><span data-stu-id="9dffd-241">Azure Storage Services REST API Reference</span></span>](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)

### <a name="related-guides"></a><span data-ttu-id="9dffd-242">İlgili kılavuzlar</span><span class="sxs-lookup"><span data-stu-id="9dffd-242">Related guides</span></span>

- [<span data-ttu-id="9dffd-243">Azure Blob depolama ile çalışmaya başlamaC#</span><span class="sxs-lookup"><span data-stu-id="9dffd-243">Getting Started with Azure Blob Storage in C#</span></span>](https://azure.microsoft.com/resources/samples/storage-blob-dotnet-getting-started/)
- [<span data-ttu-id="9dffd-244">Windows 'da AzCopy komut satırı yardımcı programıyla veri aktarma</span><span class="sxs-lookup"><span data-stu-id="9dffd-244">Transfer data with the AzCopy command-line utility on Windows</span></span>](/azure/storage/common/storage-use-azcopy)
- [<span data-ttu-id="9dffd-245">Linux üzerinde AzCopy komut satırı yardımcı programıyla veri aktarma</span><span class="sxs-lookup"><span data-stu-id="9dffd-245">Transfer data with the AzCopy command-line utility on Linux</span></span>](/azure/storage/common/storage-use-azcopy-linux)
- [<span data-ttu-id="9dffd-246">Azure depolama bağlantı dizelerini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="9dffd-246">Configure Azure Storage connection strings</span></span>](/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="9dffd-247">Azure depolama ekibi blogu</span><span class="sxs-lookup"><span data-stu-id="9dffd-247">Azure Storage Team Blog</span></span>](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [<span data-ttu-id="9dffd-248">Hızlı Başlangıç: .NET kullanarak nesne depolamada blob oluşturma</span><span class="sxs-lookup"><span data-stu-id="9dffd-248">Quickstart: Use .NET to create a blob in object storage</span></span>](/azure/storage/blobs/storage-quickstart-blobs-dotnet)
