---
title: "F # kullanarak Azure File storage'ı kullanmaya başlama"
description: Azure File storage ile bulutta dosya verileri depolamak ve bir Azure sanal makineden (VM), bulut dosya paylaşımını bağlama veya bir şirket içi uygulamasından Windows çalıştırıyor.
author: sylvanc
ms.author: phcart
ms.date: 09/20/2016
ms.topic: conceptual
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: f4eb02bc3e4aca0653a4fa991c1593f988f1d1af
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="get-started-with-azure-file-storage-using-f"></a><span data-ttu-id="0e7e6-103">F # kullanarak Azure File storage'ı kullanmaya başlama</span><span class="sxs-lookup"><span data-stu-id="0e7e6-103">Get started with Azure File storage using F#</span></span> #

<span data-ttu-id="0e7e6-104">Azure File storage bu dosya paylaşımları standardını kullanarak bulutta sunan hizmet [sunucu ileti bloğu (SMB) Protokolü](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx).</span><span class="sxs-lookup"><span data-stu-id="0e7e6-104">Azure File storage is a service that offers file shares in the cloud using the standard [Server Message Block (SMB) Protocol](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx).</span></span> <span data-ttu-id="0e7e6-105">SMB 2.1 ve SMB 3.0 desteklenir.</span><span class="sxs-lookup"><span data-stu-id="0e7e6-105">Both SMB 2.1 and SMB 3.0 are supported.</span></span> <span data-ttu-id="0e7e6-106">Azure File storage ile maliyetli yeniden yazdırmaya gerek duymadan ve hızla Azure'a dosya paylaşımı kullanan eski uygulamalar geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e7e6-106">With Azure File storage, you can migrate legacy applications that rely on file shares to Azure quickly and without costly rewrites.</span></span> <span data-ttu-id="0e7e6-107">Azure virtual machines veya cloud services veya şirket içi istemcilerde çalışan uygulamalar, yalnızca bir masaüstü uygulamasının tipik bir SMB paylaşımına bağlandığı şekilde buluta bir dosya paylaşımı bağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="0e7e6-107">Applications running in Azure virtual machines or cloud services or from on-premises clients can mount a file share in the cloud, just as a desktop application mounts a typical SMB share.</span></span> <span data-ttu-id="0e7e6-108">Uygulama bileşenleri herhangi bir sayıda sonra bağlayabilir ve File storage paylaşımını bağlayıp buna erişim.</span><span class="sxs-lookup"><span data-stu-id="0e7e6-108">Any number of application components can then mount and access the File storage share simultaneously.</span></span>

<span data-ttu-id="0e7e6-109">Dosya depolama kavramsal bir genel bakış için lütfen bkz [file storage için .NET Kılavuzu](/azure/storage/storage-dotnet-how-to-use-files).</span><span class="sxs-lookup"><span data-stu-id="0e7e6-109">For a conceptual overview of file storage, please see [the .NET guide for file storage](/azure/storage/storage-dotnet-how-to-use-files).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0e7e6-110">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="0e7e6-110">Prerequisites</span></span>

<span data-ttu-id="0e7e6-111">Bu kılavuzu kullanmak için öncelikle [bir Azure depolama hesabı oluşturma](/azure/storage/storage-create-storage-account).</span><span class="sxs-lookup"><span data-stu-id="0e7e6-111">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span>
<span data-ttu-id="0e7e6-112">Bu hesap için depolama erişim anahtarınızı de gerekir.</span><span class="sxs-lookup"><span data-stu-id="0e7e6-112">You'll also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="0e7e6-113">Bir F # betiği ve başlangıç F # Etkileşimli oluşturma</span><span class="sxs-lookup"><span data-stu-id="0e7e6-113">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="0e7e6-114">Bu makaledeki örnekler, F # uygulaması veya F # betiği kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0e7e6-114">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="0e7e6-115">F # betiği oluşturmak için dosya oluştur `.fsx` uzantısı, örneğin `files.fsx`, ortamınızdaki F # geliştirme.</span><span class="sxs-lookup"><span data-stu-id="0e7e6-115">To create an F# script, create a file with the `.fsx` extension, for example `files.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="0e7e6-116">Ardından, kullanın bir [Paket Yöneticisi](package-management.md) gibi [Paket](https://fsprojects.github.io/Paket/) veya [NuGet](https://www.nuget.org/) yüklemek için `WindowsAzure.Storage` paket ve başvuru `WindowsAzure.Storage.dll` bir kullanarakkomut`#r`yönergesi.</span><span class="sxs-lookup"><span data-stu-id="0e7e6-116">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="0e7e6-117">Ad alanı bildirimleri ekleme</span><span class="sxs-lookup"><span data-stu-id="0e7e6-117">Add namespace declarations</span></span>

<span data-ttu-id="0e7e6-118">Aşağıdakileri ekleyin `open` deyimleri üstüne `files.fsx` dosyası:</span><span class="sxs-lookup"><span data-stu-id="0e7e6-118">Add the following `open` statements to the top of the `files.fsx` file:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a><span data-ttu-id="0e7e6-119">Bağlantı dizenizi Al</span><span class="sxs-lookup"><span data-stu-id="0e7e6-119">Get your connection string</span></span>

<span data-ttu-id="0e7e6-120">Bu öğretici için bir Azure depolama bağlantı dizesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="0e7e6-120">You'll need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="0e7e6-121">Bağlantı dizeleri hakkında daha fazla bilgi için bkz: [Storage bağlantı dizelerini yapılandırma](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="0e7e6-121">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="0e7e6-122">Öğretici için şuna benzer betiğinizin bağlantı dizenizi girin:</span><span class="sxs-lookup"><span data-stu-id="0e7e6-122">For the tutorial, you'll enter your connection string in your script, like this:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L11-L11)]

<span data-ttu-id="0e7e6-123">Ancak, bu olduğu **önerilmez** için gerçek projeleri.</span><span class="sxs-lookup"><span data-stu-id="0e7e6-123">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="0e7e6-124">Depolama hesabı anahtarınız depolama hesabınızın kök parolasına benzer.</span><span class="sxs-lookup"><span data-stu-id="0e7e6-124">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="0e7e6-125">Her zaman depolama hesabı anahtarınızı korumak dikkatli olun.</span><span class="sxs-lookup"><span data-stu-id="0e7e6-125">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="0e7e6-126">Sabit kodlama veya başkalarının erişebileceği düz metin dosyasına kaydetme diğer kullanıcılara dağıtmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="0e7e6-126">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="0e7e6-127">Bunu tehlikede olduğunu düşünüyorsanız, Azure Portalı'nı kullanarak anahtarınızı yeniden oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e7e6-127">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="0e7e6-128">İçin gerçek uygulamalar, depolama bağlantı dizenizi korumak için en iyi yapılandırma dosyasında yoludur.</span><span class="sxs-lookup"><span data-stu-id="0e7e6-128">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="0e7e6-129">Yapılandırma dosyasından bağlantı dizesini almak için bunu yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0e7e6-129">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L13-L15)]

<span data-ttu-id="0e7e6-130">Azure Yapılandırma Yöneticisi'ni kullanarak isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="0e7e6-130">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="0e7e6-131">.NET Framework'ün gibi bir API de kullanabilirsiniz `ConfigurationManager` türü.</span><span class="sxs-lookup"><span data-stu-id="0e7e6-131">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="0e7e6-132">Bağlantı dizesini ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="0e7e6-132">Parse the connection string</span></span>

<span data-ttu-id="0e7e6-133">Bağlantı dizesini ayrıştırmak için kullanın:</span><span class="sxs-lookup"><span data-stu-id="0e7e6-133">To parse the connection string, use:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L21-L22)]

<span data-ttu-id="0e7e6-134">Bu döndürülecek bir `CloudStorageAccount`.</span><span class="sxs-lookup"><span data-stu-id="0e7e6-134">This will return a `CloudStorageAccount`.</span></span>

### <a name="create-the-file-service-client"></a><span data-ttu-id="0e7e6-135">Dosya hizmeti istemcisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="0e7e6-135">Create the File service client</span></span>

<span data-ttu-id="0e7e6-136">`CloudFileClient` Türü File storage'da depolanan dosyaları programlı olarak kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="0e7e6-136">The `CloudFileClient` type enables you to programmatically use files stored in File storage.</span></span> <span data-ttu-id="0e7e6-137">Hizmet istemcisini oluşturma yöntemlerinden biri aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="0e7e6-137">Here's one way to create the service client:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L28-L28)]

<span data-ttu-id="0e7e6-138">Şimdi veri okuyan ve dosya depolama alanına veri yazan kodu yazmaya hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="0e7e6-138">Now you are ready to write code that reads data from and writes data to File storage.</span></span>

## <a name="create-a-file-share"></a><span data-ttu-id="0e7e6-139">Dosya paylaşımı oluşturma</span><span class="sxs-lookup"><span data-stu-id="0e7e6-139">Create a file share</span></span>

<span data-ttu-id="0e7e6-140">Bu örnek, zaten yoksa, bir dosya paylaşımı oluşturmak gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="0e7e6-140">This example shows how to create a file share if it does not already exist:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L34-L35)]

## <a name="create-a-root-directory-and-a-subdirectory"></a><span data-ttu-id="0e7e6-141">Bir kök dizin ve bir alt dizin oluşturma</span><span class="sxs-lookup"><span data-stu-id="0e7e6-141">Create a root directory and a subdirectory</span></span>

<span data-ttu-id="0e7e6-142">Burada, kök dizini almak ve bir alt dizinin kök alın.</span><span class="sxs-lookup"><span data-stu-id="0e7e6-142">Here, you get the root directory and get a sub-directory of the root.</span></span> <span data-ttu-id="0e7e6-143">Henüz yoksa her ikisini de oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0e7e6-143">You create both if they don't already exist.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L41-L43)]

## <a name="upload-text-as-a-file"></a><span data-ttu-id="0e7e6-144">Metin dosyası olarak karşıya yükleme</span><span class="sxs-lookup"><span data-stu-id="0e7e6-144">Upload text as a file</span></span>

<span data-ttu-id="0e7e6-145">Bu örnek metin dosyası olarak karşıya nasıl yükleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0e7e6-145">This example shows how to upload text as a file.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L49-L50)]

### <a name="download-a-file-to-a-local-copy-of-the-file"></a><span data-ttu-id="0e7e6-146">Dosyanın yerel bir kopyasını dosya indirme</span><span class="sxs-lookup"><span data-stu-id="0e7e6-146">Download a file to a local copy of the file</span></span>

<span data-ttu-id="0e7e6-147">Burada oluşturduğunuz, dosya yerel bir dosyaya içeriği ekleme indirin.</span><span class="sxs-lookup"><span data-stu-id="0e7e6-147">Here you download the file just created, appending the contents to a local file.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L56-L56)]

### <a name="set-the-maximum-size-for-a-file-share"></a><span data-ttu-id="0e7e6-148">Bir dosya paylaşımı için en büyük boyutunu ayarlama</span><span class="sxs-lookup"><span data-stu-id="0e7e6-148">Set the maximum size for a file share</span></span>

<span data-ttu-id="0e7e6-149">Aşağıdaki örnek, bir paylaşım için geçerli kullanım kontrol etme ve paylaşımı için kota ayarlanamıyor gösterir.</span><span class="sxs-lookup"><span data-stu-id="0e7e6-149">The example below shows how to check the current usage for a share and how to set the quota for the share.</span></span> <span data-ttu-id="0e7e6-150">`FetchAttributes` bir paylaşımın doldurmak için çağrılmalıdır `Properties`, ve `SetProperties` Azure File storage yerel değişiklikleri yaymak için.</span><span class="sxs-lookup"><span data-stu-id="0e7e6-150">`FetchAttributes` must be called to populate a share's `Properties`, and `SetProperties` to propagate local changes to Azure File storage.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L62-L72)]

### <a name="generate-a-shared-access-signature-for-a-file-or-file-share"></a><span data-ttu-id="0e7e6-151">Bir dosya veya dosya paylaşımı için bir paylaşılan erişim imzası oluşturma</span><span class="sxs-lookup"><span data-stu-id="0e7e6-151">Generate a shared access signature for a file or file share</span></span>

<span data-ttu-id="0e7e6-152">Paylaşılan erişim imzası (SAS) tek bir dosyayı veya dosya paylaşımı için oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e7e6-152">You can generate a shared access signature (SAS) for a file share or for an individual file.</span></span> <span data-ttu-id="0e7e6-153">Ayrıca, paylaşılan erişim imzalarını yönetmek için bir dosya paylaşımında bir paylaşılan erişim ilkesi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e7e6-153">You can also create a shared access policy on a file share to manage shared access signatures.</span></span> <span data-ttu-id="0e7e6-154">Tehlikeye girdiği durumlarda SAS iptal etme yolu sağladığı gibi bir paylaşılan erişim ilkesi oluşturmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="0e7e6-154">Creating a shared access policy is recommended, as it provides a means of revoking the SAS if it should be compromised.</span></span>

<span data-ttu-id="0e7e6-155">Burada, paylaşılan oluşturduğunuz erişim ilkesi paylaşımındaki ve bir dosya paylaşımında SAS için sınırlamalar sağlamak için bu ilkeyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="0e7e6-155">Here, you create a shared access policy on a share, and then use that policy to provide the constraints for a SAS on a file in the share.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L78-L94)]

<span data-ttu-id="0e7e6-156">Oluşturma ve paylaşılan erişim imzaları kullanma hakkında daha fazla bilgi için bkz: [kullanarak paylaşılan erişim imzaları (SAS)](/azure/storage/storage-dotnet-shared-access-signature-part-1) ve [oluşturma ve kullanma Blob storage ile SAS](/azure/storage/storage-dotnet-shared-access-signature-part-2).</span><span class="sxs-lookup"><span data-stu-id="0e7e6-156">For more information about creating and using shared access signatures, see [Using Shared Access Signatures (SAS)](/azure/storage/storage-dotnet-shared-access-signature-part-1) and [Create and use a SAS with Blob storage](/azure/storage/storage-dotnet-shared-access-signature-part-2).</span></span>

### <a name="copy-files"></a><span data-ttu-id="0e7e6-157">Dosyaları kopyalama</span><span class="sxs-lookup"><span data-stu-id="0e7e6-157">Copy files</span></span>

<span data-ttu-id="0e7e6-158">Bir dosyayı başka bir dosyaya veya bir blob veya bir blobu bir dosyaya kopyalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e7e6-158">You can copy a file to another file or to a blob, or a blob to a file.</span></span> <span data-ttu-id="0e7e6-159">Bir blobu bir dosyaya veya bir blobu bir dosyaya kopyalama yapıyorsanız, *gerekir* aynı depolama hesabında kopyalama yapıyor olsanız kaynak nesne kimlik doğrulaması için paylaşılan erişim imzası (SAS) kullanın.</span><span class="sxs-lookup"><span data-stu-id="0e7e6-159">If you are copying a blob to a file, or a file to a blob, you *must* use a shared access signature (SAS) to authenticate the source object, even if you are copying within the same storage account.</span></span>

### <a name="copy-a-file-to-another-file"></a><span data-ttu-id="0e7e6-160">Bir dosyayı başka bir dosyaya kopyalama</span><span class="sxs-lookup"><span data-stu-id="0e7e6-160">Copy a file to another file</span></span>

<span data-ttu-id="0e7e6-161">Burada, bir dosya aynı paylaşımdaki başka bir dosyaya kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="0e7e6-161">Here, you copy a file to another file in the same share.</span></span> <span data-ttu-id="0e7e6-162">Bu kopyalama işlemi aynı depolama hesabındaki dosyaları kopyaladığı için kopyalama işlemini gerçekleştirmek için paylaşılan anahtar kimlik doğrulaması kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e7e6-162">Because this copy operation copies between files in the same storage account, you can use Shared Key authentication to perform the copy.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L100-L101)]

### <a name="copy-a-file-to-a-blob"></a><span data-ttu-id="0e7e6-163">Bir dosyayı bir bloba kopyalama</span><span class="sxs-lookup"><span data-stu-id="0e7e6-163">Copy a file to a blob</span></span>

<span data-ttu-id="0e7e6-164">Burada, bir dosya oluşturun ve aynı depolama hesabındaki bir bloba kopyalama.</span><span class="sxs-lookup"><span data-stu-id="0e7e6-164">Here, you create a file and copy it to a blob within the same storage account.</span></span> <span data-ttu-id="0e7e6-165">Hizmetin kopyalama işlemi sırasında kaynak dosyaya erişimin kimlik doğrulaması yapmak için kullandığı kaynak dosya için bir SAS oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0e7e6-165">You create a SAS for the source file, which the service uses to authenticate access to the source file during the copy operation.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L107-L120)]

<span data-ttu-id="0e7e6-166">Aynı şekilde bir blobu bir dosyaya kopyalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e7e6-166">You can copy a blob to a file in the same way.</span></span> <span data-ttu-id="0e7e6-167">Kaynak nesne bir blob ise, bu erişim kopyalama işlemi sırasında kimlik doğrulaması için bir SAS oluşturun.</span><span class="sxs-lookup"><span data-stu-id="0e7e6-167">If the source object is a blob, then create a SAS to authenticate access to that blob during the copy operation.</span></span>

## <a name="troubleshooting-file-storage-using-metrics"></a><span data-ttu-id="0e7e6-168">Ölçümleri kullanarak File storage sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="0e7e6-168">Troubleshooting File storage using metrics</span></span>

<span data-ttu-id="0e7e6-169">Azure Storage Analytics ölçümleri File storage için destekler.</span><span class="sxs-lookup"><span data-stu-id="0e7e6-169">Azure Storage Analytics supports metrics for File storage.</span></span> <span data-ttu-id="0e7e6-170">Ölçüm verilerini kullanarak istekleri izleme ve sorunlarını tanılamak.</span><span class="sxs-lookup"><span data-stu-id="0e7e6-170">With metrics data, you can trace requests and diagnose issues.</span></span>

<span data-ttu-id="0e7e6-171">Dan File storage için ölçümleri etkinleştirebilirsiniz [Azure Portal](https://portal.azure.com), veya bunu F # şu şekilde yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0e7e6-171">You can enable metrics for File storage from the [Azure Portal](https://portal.azure.com), or you can do it from F# like this:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L126-L140)]

## <a name="next-steps"></a><span data-ttu-id="0e7e6-172">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="0e7e6-172">Next steps</span></span>

<span data-ttu-id="0e7e6-173">Azure File storage hakkında daha fazla bilgi için şu bağlantılara bakın.</span><span class="sxs-lookup"><span data-stu-id="0e7e6-173">See these links for more information about Azure File storage.</span></span>

### <a name="conceptual-articles-and-videos"></a><span data-ttu-id="0e7e6-174">Kavramsal makaleler ve videolar</span><span class="sxs-lookup"><span data-stu-id="0e7e6-174">Conceptual articles and videos</span></span>

- [<span data-ttu-id="0e7e6-175">Azure File Storage: uyumlu bulut SMB dosya sistemi Windows ve Linux için</span><span class="sxs-lookup"><span data-stu-id="0e7e6-175">Azure Files Storage: a frictionless cloud SMB file system for Windows and Linux</span></span>](https://azure.microsoft.com/resources/videos/azurecon-2015-azure-files-storage-a-frictionless-cloud-smb-file-system-for-windows-and-linux/)
- [<span data-ttu-id="0e7e6-176">Azure File Storage Linux ile kullanma</span><span class="sxs-lookup"><span data-stu-id="0e7e6-176">How to use Azure File Storage with Linux</span></span>](/azure/storage/storage-how-to-use-files-linux)

### <a name="tooling-support-for-file-storage"></a><span data-ttu-id="0e7e6-177">File storage için araç desteği</span><span class="sxs-lookup"><span data-stu-id="0e7e6-177">Tooling support for File storage</span></span>

- [<span data-ttu-id="0e7e6-178">Azure Storage ile Azure PowerShell'i kullanma</span><span class="sxs-lookup"><span data-stu-id="0e7e6-178">Using Azure PowerShell with Azure Storage</span></span>](/azure/storage/storage-powershell-guide-full)
- [<span data-ttu-id="0e7e6-179">Microsoft Azure Storage ile AzCopy kullanma</span><span class="sxs-lookup"><span data-stu-id="0e7e6-179">How to use AzCopy with Microsoft Azure Storage</span></span>](/azure/storage/storage-use-azcopy)
- [<span data-ttu-id="0e7e6-180">Azure Storage ile Azure CLI kullanma</span><span class="sxs-lookup"><span data-stu-id="0e7e6-180">Using the Azure CLI with Azure Storage</span></span>](/azure/storage/storage-azure-cli#create-and-manage-file-shares)

### <a name="reference"></a><span data-ttu-id="0e7e6-181">Başvuru</span><span class="sxs-lookup"><span data-stu-id="0e7e6-181">Reference</span></span>

- [<span data-ttu-id="0e7e6-182">.NET başvurusu için depolama istemci kitaplığı</span><span class="sxs-lookup"><span data-stu-id="0e7e6-182">Storage Client Library for .NET reference</span></span>](https://msdn.microsoft.com/library/azure/mt347887.aspx)
- [<span data-ttu-id="0e7e6-183">Dosya hizmeti REST API'si başvurusu</span><span class="sxs-lookup"><span data-stu-id="0e7e6-183">File Service REST API reference</span></span>](/rest/api/storageservices/fileservices/File-Service-REST-API)

### <a name="blog-posts"></a><span data-ttu-id="0e7e6-184">Blog gönderileri</span><span class="sxs-lookup"><span data-stu-id="0e7e6-184">Blog posts</span></span>

- [<span data-ttu-id="0e7e6-185">Azure File storage genel kullanıma sunulmuştur</span><span class="sxs-lookup"><span data-stu-id="0e7e6-185">Azure File storage is now generally available</span></span>](https://azure.microsoft.com/blog/azure-file-storage-now-generally-available/)
- [<span data-ttu-id="0e7e6-186">Azure File Storage incelemesi</span><span class="sxs-lookup"><span data-stu-id="0e7e6-186">Inside Azure File Storage</span></span>](https://azure.microsoft.com/blog/inside-azure-file-storage/) 
- [<span data-ttu-id="0e7e6-187">Microsoft Azure dosya Hizmeti'ne Giriş</span><span class="sxs-lookup"><span data-stu-id="0e7e6-187">Introducing Microsoft Azure File Service</span></span>](https://blogs.msdn.microsoft.com/windowsazurestorage/2014/05/12/introducing-microsoft-azure-file-service/)
- [<span data-ttu-id="0e7e6-188">Microsoft Azure dosyaları ile kalıcı bağlantılar</span><span class="sxs-lookup"><span data-stu-id="0e7e6-188">Persisting connections to Microsoft Azure Files</span></span>](https://blogs.msdn.microsoft.com/windowsazurestorage/2014/05/26/persisting-connections-to-microsoft-azure-files/)
