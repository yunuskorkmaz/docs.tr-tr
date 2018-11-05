---
title: 'F # kullanarak Azure dosya depolama ile çalışmaya başlama'
description: Azure dosya depolama ile bulutta dosya data Store bir Azure sanal makineden (VM), bulut dosya paylaşımını bağlama ve bir şirket içi uygulamasından Windows çalıştıran.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: e772da5f81d2e6827295d0dfe150934a415eb3bb
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "33569349"
---
# <a name="get-started-with-azure-file-storage-using-f"></a><span data-ttu-id="003a0-103">F # kullanarak Azure dosya depolama ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="003a0-103">Get started with Azure File storage using F#</span></span> #

<span data-ttu-id="003a0-104">Azure dosya depolama, standart kullanarak bulutta dosya paylaşımları sağlayan bir hizmettir [sunucu ileti bloğu (SMB) Protokolü](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx).</span><span class="sxs-lookup"><span data-stu-id="003a0-104">Azure File storage is a service that offers file shares in the cloud using the standard [Server Message Block (SMB) Protocol](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx).</span></span> <span data-ttu-id="003a0-105">SMB 2.1 ve SMB 3.0 desteklenir.</span><span class="sxs-lookup"><span data-stu-id="003a0-105">Both SMB 2.1 and SMB 3.0 are supported.</span></span> <span data-ttu-id="003a0-106">Azure dosya depolama ile hızlı ve pahalı yeniden yazmalar olmadan Azure dosya paylaşımları kullanan eski uygulamaları geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="003a0-106">With Azure File storage, you can migrate legacy applications that rely on file shares to Azure quickly and without costly rewrites.</span></span> <span data-ttu-id="003a0-107">Azure sanal makineleri veya Bulut Hizmetleri veya şirket içi istemcilerden çalışan uygulamalar, yalnızca bir masaüstü uygulamanın tipik bir SMB paylaşımına bağlandığı şekilde bulutta dosya paylaşımı bağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="003a0-107">Applications running in Azure virtual machines or cloud services or from on-premises clients can mount a file share in the cloud, just as a desktop application mounts a typical SMB share.</span></span> <span data-ttu-id="003a0-108">Uygulama bileşenleri herhangi bir sayıda sonra bağlayın ve File storage paylaşımını bağlayıp buna erişim.</span><span class="sxs-lookup"><span data-stu-id="003a0-108">Any number of application components can then mount and access the File storage share simultaneously.</span></span>

<span data-ttu-id="003a0-109">Dosya depolama kavramsal bir genel bakış için bkz. Lütfen [dosya depolama için .NET Kılavuzu](/azure/storage/storage-dotnet-how-to-use-files).</span><span class="sxs-lookup"><span data-stu-id="003a0-109">For a conceptual overview of file storage, please see [the .NET guide for file storage](/azure/storage/storage-dotnet-how-to-use-files).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="003a0-110">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="003a0-110">Prerequisites</span></span>

<span data-ttu-id="003a0-111">Bu kılavuzu kullanmak için önce [bir Azure depolama hesabı oluşturma](/azure/storage/storage-create-storage-account).</span><span class="sxs-lookup"><span data-stu-id="003a0-111">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span>
<span data-ttu-id="003a0-112">Ayrıca, bu hesap için depolama erişim anahtarınızı gerekir.</span><span class="sxs-lookup"><span data-stu-id="003a0-112">You'll also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="003a0-113">Bir F # komut dosyası ve başlangıç F # Etkileşimli oluşturma</span><span class="sxs-lookup"><span data-stu-id="003a0-113">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="003a0-114">Bu makaledeki örnekleri, F # uygulaması veya bir F # komut dosyası kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="003a0-114">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="003a0-115">Bir F # komut dosyası oluşturmak için bir dosya oluşturun. `.fsx` uzantısı, örneğin `files.fsx`, F # geliştirme ortamınızda.</span><span class="sxs-lookup"><span data-stu-id="003a0-115">To create an F# script, create a file with the `.fsx` extension, for example `files.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="003a0-116">Ardından, bir [Paket Yöneticisi](package-management.md) gibi [Paket](https://fsprojects.github.io/Paket/) veya [NuGet](https://www.nuget.org/) yüklemek için `WindowsAzure.Storage` paket ve başvuru `WindowsAzure.Storage.dll` bir kullanarakbetiğinizde`#r`yönergesi.</span><span class="sxs-lookup"><span data-stu-id="003a0-116">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="003a0-117">Ad alanı bildirimleri ekleme</span><span class="sxs-lookup"><span data-stu-id="003a0-117">Add namespace declarations</span></span>

<span data-ttu-id="003a0-118">Aşağıdaki `open` üst tarafına deyimlerini `files.fsx` dosyası:</span><span class="sxs-lookup"><span data-stu-id="003a0-118">Add the following `open` statements to the top of the `files.fsx` file:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a><span data-ttu-id="003a0-119">Bağlantı dizenizi alma</span><span class="sxs-lookup"><span data-stu-id="003a0-119">Get your connection string</span></span>

<span data-ttu-id="003a0-120">Bu öğreticide bir Azure depolama bağlantı dizesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="003a0-120">You'll need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="003a0-121">Bağlantı dizeleri hakkında daha fazla bilgi için bkz. [depolama bağlantı dizelerini yapılandırma](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="003a0-121">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="003a0-122">Öğretici için şunun gibi komut dosyanızdaki bağlantı dizenizi girmenizi isteriz:</span><span class="sxs-lookup"><span data-stu-id="003a0-122">For the tutorial, you'll enter your connection string in your script, like this:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L11-L11)]

<span data-ttu-id="003a0-123">Ancak, bu, **önerilmez** gerçek projeleri.</span><span class="sxs-lookup"><span data-stu-id="003a0-123">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="003a0-124">Depolama hesabı anahtarınız depolama hesabınızın kök parolasına benzer.</span><span class="sxs-lookup"><span data-stu-id="003a0-124">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="003a0-125">Her zaman depolama hesabı anahtarınızı korumak dikkatli olun.</span><span class="sxs-lookup"><span data-stu-id="003a0-125">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="003a0-126">Sabit kodlama veya başkalarının erişebileceği bir düz metin dosyasına kaydederek diğer kullanıcılara dağıtmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="003a0-126">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="003a0-127">Tehlikeye girmiş olabilecek düşünüyorsanız Azure portalını kullanarak anahtarınızı yeniden oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="003a0-127">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="003a0-128">Gerçek uygulamalar, depolama bağlantı dizenizi korumak için en iyi yolu, içinde bir yapılandırma dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="003a0-128">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="003a0-129">Bir yapılandırma dosyasından bağlantı dizesini getirmek için bunu yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="003a0-129">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L13-L15)]

<span data-ttu-id="003a0-130">Azure Yapılandırma Yöneticisi'ni kullanmak isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="003a0-130">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="003a0-131">.NET Framework'ün gibi bir API de kullanabilirsiniz `ConfigurationManager` türü.</span><span class="sxs-lookup"><span data-stu-id="003a0-131">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="003a0-132">Bağlantı dizesini ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="003a0-132">Parse the connection string</span></span>

<span data-ttu-id="003a0-133">Bağlantı dizesini ayrıştırmak için kullanın:</span><span class="sxs-lookup"><span data-stu-id="003a0-133">To parse the connection string, use:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L21-L22)]

<span data-ttu-id="003a0-134">Bu döndürür bir `CloudStorageAccount`.</span><span class="sxs-lookup"><span data-stu-id="003a0-134">This will return a `CloudStorageAccount`.</span></span>

### <a name="create-the-file-service-client"></a><span data-ttu-id="003a0-135">Dosya hizmeti istemcisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="003a0-135">Create the File service client</span></span>

<span data-ttu-id="003a0-136">`CloudFileClient` Türü dosya depolama alanında depolanmış dosyaları programlı olarak kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="003a0-136">The `CloudFileClient` type enables you to programmatically use files stored in File storage.</span></span> <span data-ttu-id="003a0-137">Hizmet istemcisini oluşturma yöntemlerinden biri aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="003a0-137">Here's one way to create the service client:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L28-L28)]

<span data-ttu-id="003a0-138">Artık, okuyan ve dosya depolamaya veri yazan kodu yazmaya hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="003a0-138">Now you are ready to write code that reads data from and writes data to File storage.</span></span>

## <a name="create-a-file-share"></a><span data-ttu-id="003a0-139">Dosya paylaşımı oluşturma</span><span class="sxs-lookup"><span data-stu-id="003a0-139">Create a file share</span></span>

<span data-ttu-id="003a0-140">Bu örnek, zaten yoksa, bir dosya paylaşımı oluşturma işlemini gösterir:</span><span class="sxs-lookup"><span data-stu-id="003a0-140">This example shows how to create a file share if it does not already exist:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L34-L35)]

## <a name="create-a-root-directory-and-a-subdirectory"></a><span data-ttu-id="003a0-141">Kök dizin ve bir alt dizin oluşturma</span><span class="sxs-lookup"><span data-stu-id="003a0-141">Create a root directory and a subdirectory</span></span>

<span data-ttu-id="003a0-142">Kök dizin, burada size ve bir alt kök dizini alın.</span><span class="sxs-lookup"><span data-stu-id="003a0-142">Here, you get the root directory and get a sub-directory of the root.</span></span> <span data-ttu-id="003a0-143">Henüz yoksa her ikisi de oluşturun.</span><span class="sxs-lookup"><span data-stu-id="003a0-143">You create both if they don't already exist.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L41-L43)]

## <a name="upload-text-as-a-file"></a><span data-ttu-id="003a0-144">Metin dosyası olarak karşıya yükleme</span><span class="sxs-lookup"><span data-stu-id="003a0-144">Upload text as a file</span></span>

<span data-ttu-id="003a0-145">Bu örnek metin dosyası olarak karşıya yükleme işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="003a0-145">This example shows how to upload text as a file.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L49-L50)]

### <a name="download-a-file-to-a-local-copy-of-the-file"></a><span data-ttu-id="003a0-146">Dosyanın yerel bir kopyasını dosya indirme</span><span class="sxs-lookup"><span data-stu-id="003a0-146">Download a file to a local copy of the file</span></span>

<span data-ttu-id="003a0-147">Burada oluşturduğunuz, dosyanın içeriğini yerel bir dosyaya ekleme indirin.</span><span class="sxs-lookup"><span data-stu-id="003a0-147">Here you download the file just created, appending the contents to a local file.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L56-L56)]

### <a name="set-the-maximum-size-for-a-file-share"></a><span data-ttu-id="003a0-148">Bir dosya paylaşımı için boyut üst sınırı ayarlayın</span><span class="sxs-lookup"><span data-stu-id="003a0-148">Set the maximum size for a file share</span></span>

<span data-ttu-id="003a0-149">Aşağıdaki örnekte bir paylaşım için geçerli kullanım denetleme ve paylaşımı için kota ayarlamak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="003a0-149">The example below shows how to check the current usage for a share and how to set the quota for the share.</span></span> <span data-ttu-id="003a0-150">`FetchAttributes` bir paylaşımın doldurmak için çağrılmalıdır `Properties`, ve `SetProperties` Azure dosya depolama yerel değişiklikleri yaymak için.</span><span class="sxs-lookup"><span data-stu-id="003a0-150">`FetchAttributes` must be called to populate a share's `Properties`, and `SetProperties` to propagate local changes to Azure File storage.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L62-L72)]

### <a name="generate-a-shared-access-signature-for-a-file-or-file-share"></a><span data-ttu-id="003a0-151">Bir dosya veya dosya paylaşımı için paylaşılan erişim imzası oluşturma</span><span class="sxs-lookup"><span data-stu-id="003a0-151">Generate a shared access signature for a file or file share</span></span>

<span data-ttu-id="003a0-152">Paylaşılan erişim imzası (SAS) tek bir dosyayı veya dosya paylaşımı için oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="003a0-152">You can generate a shared access signature (SAS) for a file share or for an individual file.</span></span> <span data-ttu-id="003a0-153">Ayrıca, paylaşılan erişim imzalarını yönetmek için bir dosya paylaşımında bir paylaşılan erişim ilkesi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="003a0-153">You can also create a shared access policy on a file share to manage shared access signatures.</span></span> <span data-ttu-id="003a0-154">Tehlikeye girdiği durumlarda SAS'yi iptal etme yolu sağladığından bir paylaşılan erişim ilkesi oluşturmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="003a0-154">Creating a shared access policy is recommended, as it provides a means of revoking the SAS if it should be compromised.</span></span>

<span data-ttu-id="003a0-155">Burada, paylaşılan oluşturduğunuz erişim ilkesi paylaşımındaki ve bu ilke paylaşımdaki bir dosya çubuğunda bir SAS için sınırlamalar sağlamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="003a0-155">Here, you create a shared access policy on a share, and then use that policy to provide the constraints for a SAS on a file in the share.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L78-L94)]

<span data-ttu-id="003a0-156">Paylaşılan erişim imzaları oluşturma ve kullanma hakkında daha fazla bilgi için bkz. [kullanarak paylaşılan erişim imzaları (SAS)](/azure/storage/storage-dotnet-shared-access-signature-part-1) ve [oluşturma ve kullanma Blob Depolama ile SAS](/azure/storage/storage-dotnet-shared-access-signature-part-2).</span><span class="sxs-lookup"><span data-stu-id="003a0-156">For more information about creating and using shared access signatures, see [Using Shared Access Signatures (SAS)](/azure/storage/storage-dotnet-shared-access-signature-part-1) and [Create and use a SAS with Blob storage](/azure/storage/storage-dotnet-shared-access-signature-part-2).</span></span>

### <a name="copy-files"></a><span data-ttu-id="003a0-157">Dosyaları Kopyala</span><span class="sxs-lookup"><span data-stu-id="003a0-157">Copy files</span></span>

<span data-ttu-id="003a0-158">Başka bir dosyaya veya bir bloba veya bir blobu bir dosyaya bir dosyaya kopyalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="003a0-158">You can copy a file to another file or to a blob, or a blob to a file.</span></span> <span data-ttu-id="003a0-159">Bir blobu bir dosyaya veya bir blobu bir dosyaya kopyalıyorsanız, *gerekir* aynı depolama hesabında kopyalama yapıyor olsanız da kaynak nesnesinin kimliğini doğrulamak için bir paylaşılan erişim imzası (SAS) kullanın.</span><span class="sxs-lookup"><span data-stu-id="003a0-159">If you are copying a blob to a file, or a file to a blob, you *must* use a shared access signature (SAS) to authenticate the source object, even if you are copying within the same storage account.</span></span>

### <a name="copy-a-file-to-another-file"></a><span data-ttu-id="003a0-160">Bir dosyayı başka bir dosyaya kopyalama</span><span class="sxs-lookup"><span data-stu-id="003a0-160">Copy a file to another file</span></span>

<span data-ttu-id="003a0-161">Burada, bir dosya aynı paylaşımdaki başka bir dosyaya kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="003a0-161">Here, you copy a file to another file in the same share.</span></span> <span data-ttu-id="003a0-162">Bu kopyalama işlemi arasında aynı depolama hesabındaki dosyaları kopyaladığı için kopyalama işlemini gerçekleştirmek için paylaşılan anahtar kimlik doğrulaması'nı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="003a0-162">Because this copy operation copies between files in the same storage account, you can use Shared Key authentication to perform the copy.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L100-L101)]

### <a name="copy-a-file-to-a-blob"></a><span data-ttu-id="003a0-163">Bir dosyayı bir bloba kopyalama</span><span class="sxs-lookup"><span data-stu-id="003a0-163">Copy a file to a blob</span></span>

<span data-ttu-id="003a0-164">Burada, bir dosya oluşturun ve aynı depolama hesabındaki bir bloba kopyalama.</span><span class="sxs-lookup"><span data-stu-id="003a0-164">Here, you create a file and copy it to a blob within the same storage account.</span></span> <span data-ttu-id="003a0-165">Hizmetin kopyalama işlemi sırasında kaynak dosyaya erişimin kimlik doğrulaması için kullandığı kaynak dosyası için bir SAS oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="003a0-165">You create a SAS for the source file, which the service uses to authenticate access to the source file during the copy operation.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L107-L120)]

<span data-ttu-id="003a0-166">Bir blobu bir dosyaya aynı şekilde kopyalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="003a0-166">You can copy a blob to a file in the same way.</span></span> <span data-ttu-id="003a0-167">Kaynak nesne bir blob ise, ardından kopyalama işlemi sırasında bu bloba erişimin kimlik doğrulaması için bir SAS oluşturun.</span><span class="sxs-lookup"><span data-stu-id="003a0-167">If the source object is a blob, then create a SAS to authenticate access to that blob during the copy operation.</span></span>

## <a name="troubleshooting-file-storage-using-metrics"></a><span data-ttu-id="003a0-168">Ölçümleri kullanarak File storage sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="003a0-168">Troubleshooting File storage using metrics</span></span>

<span data-ttu-id="003a0-169">Azure depolama analizi, File storage için ölçümleri destekliyor.</span><span class="sxs-lookup"><span data-stu-id="003a0-169">Azure Storage Analytics supports metrics for File storage.</span></span> <span data-ttu-id="003a0-170">Ölçüm verilerini kullanarak istekleri izleyebilir ve sorunları tanılayabilir.</span><span class="sxs-lookup"><span data-stu-id="003a0-170">With metrics data, you can trace requests and diagnose issues.</span></span>

<span data-ttu-id="003a0-171">Dosya depolama ölçümlerini etkinleştirebilirsiniz [Azure portalı](https://portal.azure.com), ya da bunu F# şöyle:</span><span class="sxs-lookup"><span data-stu-id="003a0-171">You can enable metrics for File storage from the [Azure Portal](https://portal.azure.com), or you can do it from F# like this:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L126-L140)]

## <a name="next-steps"></a><span data-ttu-id="003a0-172">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="003a0-172">Next steps</span></span>

<span data-ttu-id="003a0-173">Azure dosya depolama hakkında daha fazla bilgi için şu bağlantılara göz atın.</span><span class="sxs-lookup"><span data-stu-id="003a0-173">See these links for more information about Azure File storage.</span></span>

### <a name="conceptual-articles-and-videos"></a><span data-ttu-id="003a0-174">Kavramsal makaleler ve videolar</span><span class="sxs-lookup"><span data-stu-id="003a0-174">Conceptual articles and videos</span></span>

- [<span data-ttu-id="003a0-175">Azure dosya depolama: uyumlu bulut SMB dosya sistemi Windows ve Linux için</span><span class="sxs-lookup"><span data-stu-id="003a0-175">Azure Files Storage: a frictionless cloud SMB file system for Windows and Linux</span></span>](https://azure.microsoft.com/resources/videos/azurecon-2015-azure-files-storage-a-frictionless-cloud-smb-file-system-for-windows-and-linux/)
- [<span data-ttu-id="003a0-176">Nasıl Azure dosya depolamayı Linux ile kullanma</span><span class="sxs-lookup"><span data-stu-id="003a0-176">How to use Azure File Storage with Linux</span></span>](/azure/storage/storage-how-to-use-files-linux)

### <a name="tooling-support-for-file-storage"></a><span data-ttu-id="003a0-177">Dosya depolama için araç desteği</span><span class="sxs-lookup"><span data-stu-id="003a0-177">Tooling support for File storage</span></span>

- [<span data-ttu-id="003a0-178">Azure PowerShell'i Azure depolama ile kullanma</span><span class="sxs-lookup"><span data-stu-id="003a0-178">Using Azure PowerShell with Azure Storage</span></span>](/azure/storage/storage-powershell-guide-full)
- [<span data-ttu-id="003a0-179">Microsoft Azure Storage ile AzCopy kullanma</span><span class="sxs-lookup"><span data-stu-id="003a0-179">How to use AzCopy with Microsoft Azure Storage</span></span>](/azure/storage/storage-use-azcopy)
- [<span data-ttu-id="003a0-180">Azure CLI ile Azure depolama kullanma</span><span class="sxs-lookup"><span data-stu-id="003a0-180">Using the Azure CLI with Azure Storage</span></span>](/azure/storage/storage-azure-cli#create-and-manage-file-shares)

### <a name="reference"></a><span data-ttu-id="003a0-181">Başvuru</span><span class="sxs-lookup"><span data-stu-id="003a0-181">Reference</span></span>

- [<span data-ttu-id="003a0-182">.NET başvurusu için depolama istemcisi kitaplığı</span><span class="sxs-lookup"><span data-stu-id="003a0-182">Storage Client Library for .NET reference</span></span>](https://msdn.microsoft.com/library/azure/mt347887.aspx)
- [<span data-ttu-id="003a0-183">Dosya hizmeti REST API Başvurusu</span><span class="sxs-lookup"><span data-stu-id="003a0-183">File Service REST API reference</span></span>](/rest/api/storageservices/fileservices/File-Service-REST-API)

### <a name="blog-posts"></a><span data-ttu-id="003a0-184">Blog gönderileri</span><span class="sxs-lookup"><span data-stu-id="003a0-184">Blog posts</span></span>

- [<span data-ttu-id="003a0-185">Azure dosya depolama genel kullanıma sunulmuştur</span><span class="sxs-lookup"><span data-stu-id="003a0-185">Azure File storage is now generally available</span></span>](https://azure.microsoft.com/blog/azure-file-storage-now-generally-available/)
- [<span data-ttu-id="003a0-186">Azure dosya depolama incelemesi</span><span class="sxs-lookup"><span data-stu-id="003a0-186">Inside Azure File Storage</span></span>](https://azure.microsoft.com/blog/inside-azure-file-storage/) 
- [<span data-ttu-id="003a0-187">Microsoft Azure dosya Hizmeti'ne Giriş</span><span class="sxs-lookup"><span data-stu-id="003a0-187">Introducing Microsoft Azure File Service</span></span>](https://blogs.msdn.microsoft.com/windowsazurestorage/2014/05/12/introducing-microsoft-azure-file-service/)
- [<span data-ttu-id="003a0-188">Microsoft Azure dosyaları ile kalıcı bağlantılar</span><span class="sxs-lookup"><span data-stu-id="003a0-188">Persisting connections to Microsoft Azure Files</span></span>](https://blogs.msdn.microsoft.com/windowsazurestorage/2014/05/26/persisting-connections-to-microsoft-azure-files/)
