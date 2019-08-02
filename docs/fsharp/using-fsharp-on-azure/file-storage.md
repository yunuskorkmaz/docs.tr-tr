---
title: F# kullanarak Azure Dosya depolama kullanmaya başlama
description: Dosya verilerini bulutta Azure dosya depolama ile depolayın ve bulut dosya paylaşımınızı bir Azure sanal makinesinden (VM) veya Windows çalıştıran şirket içi bir uygulamadan bağlayın.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: a0e3cab56ba0f3db27335822616b4976a5d9de62
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630501"
---
# <a name="get-started-with-azure-file-storage-using-f"></a><span data-ttu-id="68a30-103">F kullanarak Azure dosya depolama ile çalışmaya başlama\#</span><span class="sxs-lookup"><span data-stu-id="68a30-103">Get started with Azure File storage using F\#</span></span>

<span data-ttu-id="68a30-104">Azure dosya depolama, standart [sunucu Ileti bloğu (SMB) protokolünü](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx)kullanarak bulutta dosya paylaşımları sunan bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="68a30-104">Azure File storage is a service that offers file shares in the cloud using the standard [Server Message Block (SMB) Protocol](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx).</span></span> <span data-ttu-id="68a30-105">SMB 2.1 ve SMB 3.0 desteklenir.</span><span class="sxs-lookup"><span data-stu-id="68a30-105">Both SMB 2.1 and SMB 3.0 are supported.</span></span> <span data-ttu-id="68a30-106">Azure File Storage, Azure’a dosya paylaşımı kullanan eski uygulamaları maliyetli yeniden yazdırmaya ihtiyaç duymadan ve hızla taşıyabilmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="68a30-106">With Azure File storage, you can migrate legacy applications that rely on file shares to Azure quickly and without costly rewrites.</span></span> <span data-ttu-id="68a30-107">Azure Virtual Machines’de, Cloud Services’da veya şirket içi istemcilerde çalışan uygulamalar, bir masaüstü uygulamanın tipik SMB paylaşımı bağladığı gibi buluta bir dosya paylaşımı bağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="68a30-107">Applications running in Azure virtual machines or cloud services or from on-premises clients can mount a file share in the cloud, just as a desktop application mounts a typical SMB share.</span></span> <span data-ttu-id="68a30-108">Ardından herhangi sayıda uygulama bileşeni eş zamanlı olarak File Storage paylaşımını bağlayıp buna erişim sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="68a30-108">Any number of application components can then mount and access the File storage share simultaneously.</span></span>

<span data-ttu-id="68a30-109">Dosya depolamaya kavramsal bir genel bakış için lütfen bkz. [dosya depolaması için .net Kılavuzu](/azure/storage/storage-dotnet-how-to-use-files).</span><span class="sxs-lookup"><span data-stu-id="68a30-109">For a conceptual overview of file storage, please see [the .NET guide for file storage](/azure/storage/storage-dotnet-how-to-use-files).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="68a30-110">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="68a30-110">Prerequisites</span></span>

<span data-ttu-id="68a30-111">Bu kılavuzu kullanmak için önce [bir Azure depolama hesabı oluşturmanız](/azure/storage/storage-create-storage-account)gerekir.</span><span class="sxs-lookup"><span data-stu-id="68a30-111">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span>
<span data-ttu-id="68a30-112">Ayrıca, bu hesap için depolama erişim anahtarınız gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="68a30-112">You'll also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="68a30-113">F# Betik oluşturma ve etkileşimli başlatma F#</span><span class="sxs-lookup"><span data-stu-id="68a30-113">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="68a30-114">Bu makaledeki örnekler, bir F# uygulama ya da bir F# komut dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="68a30-114">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="68a30-115">Bir F# betik oluşturmak için, örneğin `.fsx` `files.fsx`, F# geliştirme ortamınızda uzantılı bir dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="68a30-115">To create an F# script, create a file with the `.fsx` extension, for example `files.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="68a30-116">Daha sonra, `WindowsAzure.Storage` paketi ve bir `WindowsAzure.Storage.dll` [](https://fsprojects.github.io/Paket/) yönergekullanarakbetiğepaketvebaşvuruyüklemekiçin,paketveyaNuGetgibibirpaketyöneticisi`#r` kullanın. [](package-management.md) [](https://www.nuget.org/)</span><span class="sxs-lookup"><span data-stu-id="68a30-116">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="68a30-117">Ad alanı bildirimleri ekle</span><span class="sxs-lookup"><span data-stu-id="68a30-117">Add namespace declarations</span></span>

<span data-ttu-id="68a30-118">Aşağıdaki `open` deyimlerini `files.fsx` dosyanın en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="68a30-118">Add the following `open` statements to the top of the `files.fsx` file:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a><span data-ttu-id="68a30-119">Bağlantı dizenizi alın</span><span class="sxs-lookup"><span data-stu-id="68a30-119">Get your connection string</span></span>

<span data-ttu-id="68a30-120">Bu öğretici için bir Azure depolama bağlantı dizesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="68a30-120">You'll need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="68a30-121">Bağlantı dizeleri hakkında daha fazla bilgi için bkz. [depolama bağlantı dizelerini yapılandırma](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="68a30-121">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="68a30-122">Öğreticide, aşağıdaki gibi, komut dosyası için Bağlantı dizenizi girersiniz:</span><span class="sxs-lookup"><span data-stu-id="68a30-122">For the tutorial, you'll enter your connection string in your script, like this:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L11-L11)]

<span data-ttu-id="68a30-123">Ancak, bu gerçek projeler için **önerilmez** .</span><span class="sxs-lookup"><span data-stu-id="68a30-123">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="68a30-124">Depolama hesabı anahtarınız, depolama hesabınızın kök parolasıyla benzerdir.</span><span class="sxs-lookup"><span data-stu-id="68a30-124">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="68a30-125">Depolama hesabı anahtarınızı korumak için her zaman özen gösterin.</span><span class="sxs-lookup"><span data-stu-id="68a30-125">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="68a30-126">Diğer kullanıcılara dağıtmaktan, sabit kodlamaktan ve başkalarının erişebileceği düz metin dosyasına kaydetmekten kaçının.</span><span class="sxs-lookup"><span data-stu-id="68a30-126">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="68a30-127">Güvenliğinin tehlikede olduğunu düşünüyorsanız, Azure portalını kullanarak anahtarınızı yeniden oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68a30-127">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="68a30-128">Gerçek uygulamalar için, depolama Bağlantı dizenizi korumak için en iyi yol bir yapılandırma dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="68a30-128">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="68a30-129">Bağlantı dizesini bir yapılandırma dosyasından getirmek için şunu yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="68a30-129">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L13-L15)]

<span data-ttu-id="68a30-130">Azure Configuration Manager kullanmak isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="68a30-130">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="68a30-131">.NET Framework `ConfigurationManager` türü gibi bir API de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68a30-131">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="68a30-132">Bağlantı dizesini ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="68a30-132">Parse the connection string</span></span>

<span data-ttu-id="68a30-133">Bağlantı dizesini ayrıştırmak için şunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="68a30-133">To parse the connection string, use:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L21-L22)]

<span data-ttu-id="68a30-134">Bu, döndürür `CloudStorageAccount`.</span><span class="sxs-lookup"><span data-stu-id="68a30-134">This will return a `CloudStorageAccount`.</span></span>

### <a name="create-the-file-service-client"></a><span data-ttu-id="68a30-135">Dosya hizmeti istemcisini oluşturma</span><span class="sxs-lookup"><span data-stu-id="68a30-135">Create the File service client</span></span>

<span data-ttu-id="68a30-136">Türü `CloudFileClient` , dosya depolama alanında depolanan dosyaları programlı olarak kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="68a30-136">The `CloudFileClient` type enables you to programmatically use files stored in File storage.</span></span> <span data-ttu-id="68a30-137">Hizmet istemcisini oluşturmak için bir yol aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="68a30-137">Here's one way to create the service client:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L28-L28)]

<span data-ttu-id="68a30-138">Artık, verileri okuyan ve dosya depolama alanına veri yazan kodu yazmaya hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="68a30-138">Now you are ready to write code that reads data from and writes data to File storage.</span></span>

## <a name="create-a-file-share"></a><span data-ttu-id="68a30-139">Dosya paylaşma oluşturma</span><span class="sxs-lookup"><span data-stu-id="68a30-139">Create a file share</span></span>

<span data-ttu-id="68a30-140">Bu örnek, zaten yoksa bir dosya paylaşımının nasıl oluşturulacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="68a30-140">This example shows how to create a file share if it does not already exist:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L34-L35)]

## <a name="create-a-root-directory-and-a-subdirectory"></a><span data-ttu-id="68a30-141">Kök dizin ve alt dizin oluşturma</span><span class="sxs-lookup"><span data-stu-id="68a30-141">Create a root directory and a subdirectory</span></span>

<span data-ttu-id="68a30-142">Burada kök dizini alır ve kökün bir alt dizinini alırsınız.</span><span class="sxs-lookup"><span data-stu-id="68a30-142">Here, you get the root directory and get a sub-directory of the root.</span></span> <span data-ttu-id="68a30-143">Zaten mevcut değilse oluşturun.</span><span class="sxs-lookup"><span data-stu-id="68a30-143">You create both if they don't already exist.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L41-L43)]

## <a name="upload-text-as-a-file"></a><span data-ttu-id="68a30-144">Metni dosya olarak karşıya yükle</span><span class="sxs-lookup"><span data-stu-id="68a30-144">Upload text as a file</span></span>

<span data-ttu-id="68a30-145">Bu örnekte, metnin dosya olarak nasıl yükleneceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="68a30-145">This example shows how to upload text as a file.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L49-L50)]

### <a name="download-a-file-to-a-local-copy-of-the-file"></a><span data-ttu-id="68a30-146">Dosyanın yerel kopyasına bir dosya indir</span><span class="sxs-lookup"><span data-stu-id="68a30-146">Download a file to a local copy of the file</span></span>

<span data-ttu-id="68a30-147">Burada, yeni oluşturulan dosyayı indirerek içeriği yerel bir dosyaya ekleyin.</span><span class="sxs-lookup"><span data-stu-id="68a30-147">Here you download the file just created, appending the contents to a local file.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L56-L56)]

### <a name="set-the-maximum-size-for-a-file-share"></a><span data-ttu-id="68a30-148">Dosya paylaşımının en büyük boyutunu ayarlama</span><span class="sxs-lookup"><span data-stu-id="68a30-148">Set the maximum size for a file share</span></span>

<span data-ttu-id="68a30-149">Aşağıdaki örnekte, bir paylaşımın geçerli kullanımının nasıl denetlenecek ve paylaşımın kotasının nasıl ayarlanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="68a30-149">The example below shows how to check the current usage for a share and how to set the quota for the share.</span></span> <span data-ttu-id="68a30-150">`FetchAttributes`bir paylaşımın `Properties`doldurulmasında ve `SetProperties` yerel değişiklikleri Azure dosya depolama alanına yaymaya yönelik olarak çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="68a30-150">`FetchAttributes` must be called to populate a share's `Properties`, and `SetProperties` to propagate local changes to Azure File storage.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L62-L72)]

### <a name="generate-a-shared-access-signature-for-a-file-or-file-share"></a><span data-ttu-id="68a30-151">Dosya veya dosya paylaşımının paylaşılan erişim imzasını oluşturma</span><span class="sxs-lookup"><span data-stu-id="68a30-151">Generate a shared access signature for a file or file share</span></span>

<span data-ttu-id="68a30-152">Bir dosya paylaşımında veya tek bir dosya için paylaşılan erişim imzası (SAS) oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68a30-152">You can generate a shared access signature (SAS) for a file share or for an individual file.</span></span> <span data-ttu-id="68a30-153">Paylaşılan erişim imzalarını yönetmek için, bir dosya paylaşımında paylaşılan erişim ilkesi de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68a30-153">You can also create a shared access policy on a file share to manage shared access signatures.</span></span> <span data-ttu-id="68a30-154">Bir paylaşılan erişim ilkesinin oluşturulması önerilir, çünkü tehlikeye atılması gerekiyorsa SAS 'yi iptal etmek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="68a30-154">Creating a shared access policy is recommended, as it provides a means of revoking the SAS if it should be compromised.</span></span>

<span data-ttu-id="68a30-155">Burada, bir paylaşımda paylaşılan erişim ilkesi oluşturun ve ardından bu ilkeyi kullanarak paylaşımdaki bir dosya üzerindeki bir SAS için kısıtlamalar sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68a30-155">Here, you create a shared access policy on a share, and then use that policy to provide the constraints for a SAS on a file in the share.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L78-L94)]

<span data-ttu-id="68a30-156">Paylaşılan erişim imzaları oluşturma ve kullanma hakkında daha fazla bilgi için bkz. [paylaşılan erişim imzaları (SAS) kullanma](/azure/storage/storage-dotnet-shared-access-signature-part-1) ve [BLOB depolama ile SAS oluşturma ve kullanma](/azure/storage/storage-dotnet-shared-access-signature-part-2).</span><span class="sxs-lookup"><span data-stu-id="68a30-156">For more information about creating and using shared access signatures, see [Using Shared Access Signatures (SAS)](/azure/storage/storage-dotnet-shared-access-signature-part-1) and [Create and use a SAS with Blob storage](/azure/storage/storage-dotnet-shared-access-signature-part-2).</span></span>

### <a name="copy-files"></a><span data-ttu-id="68a30-157">Dosyaları Kopyala</span><span class="sxs-lookup"><span data-stu-id="68a30-157">Copy files</span></span>

<span data-ttu-id="68a30-158">Bir dosyayı başka bir dosyaya veya blob 'a ya da bir bloba bir dosyaya kopyalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68a30-158">You can copy a file to another file or to a blob, or a blob to a file.</span></span> <span data-ttu-id="68a30-159">Bir blobu bir dosyaya veya bir dosyayı bir bloba kopyalıyorsanız, aynı depolama hesabı içinde kopyalama olsanız bile, kaynak nesnenin kimliğini doğrulamak için bir paylaşılan erişim imzası (SAS) kullanmanız *gerekir* .</span><span class="sxs-lookup"><span data-stu-id="68a30-159">If you are copying a blob to a file, or a file to a blob, you *must* use a shared access signature (SAS) to authenticate the source object, even if you are copying within the same storage account.</span></span>

### <a name="copy-a-file-to-another-file"></a><span data-ttu-id="68a30-160">Dosyayı başka bir dosyaya kopyalama</span><span class="sxs-lookup"><span data-stu-id="68a30-160">Copy a file to another file</span></span>

<span data-ttu-id="68a30-161">Burada, bir dosyayı aynı paylaşımdaki başka bir dosyaya kopyalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68a30-161">Here, you copy a file to another file in the same share.</span></span> <span data-ttu-id="68a30-162">Bu kopyalama işlemi aynı depolama hesabındaki dosyalar arasında kopya yaptığından, kopyayı gerçekleştirmek için paylaşılan anahtar kimlik doğrulaması kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68a30-162">Because this copy operation copies between files in the same storage account, you can use Shared Key authentication to perform the copy.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L100-L101)]

### <a name="copy-a-file-to-a-blob"></a><span data-ttu-id="68a30-163">Blob 'a dosya kopyalama</span><span class="sxs-lookup"><span data-stu-id="68a30-163">Copy a file to a blob</span></span>

<span data-ttu-id="68a30-164">Burada, bir dosya oluşturup aynı depolama hesabı içindeki bir bloba kopyalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68a30-164">Here, you create a file and copy it to a blob within the same storage account.</span></span> <span data-ttu-id="68a30-165">Kaynak dosya için, hizmetin kopyalama işlemi sırasında kaynak dosyaya erişimin kimliğini doğrulamak için kullandığı bir SAS oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="68a30-165">You create a SAS for the source file, which the service uses to authenticate access to the source file during the copy operation.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L107-L120)]

<span data-ttu-id="68a30-166">Bir blobu bir dosyaya aynı şekilde kopyalayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68a30-166">You can copy a blob to a file in the same way.</span></span> <span data-ttu-id="68a30-167">Kaynak nesne bir blob ise, kopyalama işlemi sırasında o bloba erişim kimliğini doğrulamak için bir SAS oluşturun.</span><span class="sxs-lookup"><span data-stu-id="68a30-167">If the source object is a blob, then create a SAS to authenticate access to that blob during the copy operation.</span></span>

## <a name="troubleshooting-file-storage-using-metrics"></a><span data-ttu-id="68a30-168">Ölçümleri kullanarak dosya depolama sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="68a30-168">Troubleshooting File storage using metrics</span></span>

<span data-ttu-id="68a30-169">Azure Depolama Analizi dosya depolama için ölçümleri destekler.</span><span class="sxs-lookup"><span data-stu-id="68a30-169">Azure Storage Analytics supports metrics for File storage.</span></span> <span data-ttu-id="68a30-170">Ölçüm verileriyle, istekleri izleyebilir ve sorunları tanılayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="68a30-170">With metrics data, you can trace requests and diagnose issues.</span></span>

<span data-ttu-id="68a30-171">[Azure portalından](https://portal.azure.com)dosya depolama ölçümlerini etkinleştirebilir veya bunu şu F# şekilde yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="68a30-171">You can enable metrics for File storage from the [Azure Portal](https://portal.azure.com), or you can do it from F# like this:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L126-L140)]

## <a name="next-steps"></a><span data-ttu-id="68a30-172">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="68a30-172">Next steps</span></span>

<span data-ttu-id="68a30-173">Azure dosya depolama hakkında daha fazla bilgi için bu bağlantılara bakın.</span><span class="sxs-lookup"><span data-stu-id="68a30-173">See these links for more information about Azure File storage.</span></span>

### <a name="conceptual-articles-and-videos"></a><span data-ttu-id="68a30-174">Kavramsal makaleler ve videolar</span><span class="sxs-lookup"><span data-stu-id="68a30-174">Conceptual articles and videos</span></span>

- [<span data-ttu-id="68a30-175">Azure dosya depolama: Windows ve Linux için sorunsuz bulut SMB dosya sistemi</span><span class="sxs-lookup"><span data-stu-id="68a30-175">Azure Files Storage: a frictionless cloud SMB file system for Windows and Linux</span></span>](https://azure.microsoft.com/resources/videos/azurecon-2015-azure-files-storage-a-frictionless-cloud-smb-file-system-for-windows-and-linux/)
- [<span data-ttu-id="68a30-176">Linux ile Azure dosya depolama kullanma</span><span class="sxs-lookup"><span data-stu-id="68a30-176">How to use Azure File Storage with Linux</span></span>](/azure/storage/storage-how-to-use-files-linux)

### <a name="tooling-support-for-file-storage"></a><span data-ttu-id="68a30-177">Dosya depolama için araç desteği</span><span class="sxs-lookup"><span data-stu-id="68a30-177">Tooling support for File storage</span></span>

- [<span data-ttu-id="68a30-178">Azure depolama ile Azure PowerShell kullanma</span><span class="sxs-lookup"><span data-stu-id="68a30-178">Using Azure PowerShell with Azure Storage</span></span>](/azure/storage/storage-powershell-guide-full)
- [<span data-ttu-id="68a30-179">Microsoft Azure Depolama ile AzCopy kullanma</span><span class="sxs-lookup"><span data-stu-id="68a30-179">How to use AzCopy with Microsoft Azure Storage</span></span>](/azure/storage/storage-use-azcopy)
- [<span data-ttu-id="68a30-180">Azure depolama ile Azure CLı kullanma</span><span class="sxs-lookup"><span data-stu-id="68a30-180">Using the Azure CLI with Azure Storage</span></span>](/azure/storage/storage-azure-cli#create-and-manage-file-shares)

### <a name="reference"></a><span data-ttu-id="68a30-181">Başvuru</span><span class="sxs-lookup"><span data-stu-id="68a30-181">Reference</span></span>

- [<span data-ttu-id="68a30-182">.NET başvurusu için Depolama İstemci Kitaplığı</span><span class="sxs-lookup"><span data-stu-id="68a30-182">Storage Client Library for .NET reference</span></span>](https://msdn.microsoft.com/library/azure/mt347887.aspx)
- [<span data-ttu-id="68a30-183">Dosya hizmeti REST API başvurusu</span><span class="sxs-lookup"><span data-stu-id="68a30-183">File Service REST API reference</span></span>](/rest/api/storageservices/fileservices/File-Service-REST-API)

### <a name="blog-posts"></a><span data-ttu-id="68a30-184">Blog gönderileri</span><span class="sxs-lookup"><span data-stu-id="68a30-184">Blog posts</span></span>

- [<span data-ttu-id="68a30-185">Azure dosya depolama genel kullanıma sunuldu</span><span class="sxs-lookup"><span data-stu-id="68a30-185">Azure File storage is now generally available</span></span>](https://azure.microsoft.com/blog/azure-file-storage-now-generally-available/)
- [<span data-ttu-id="68a30-186">Azure dosya depolama alanı içinde</span><span class="sxs-lookup"><span data-stu-id="68a30-186">Inside Azure File Storage</span></span>](https://azure.microsoft.com/blog/inside-azure-file-storage/) 
- [<span data-ttu-id="68a30-187">Microsoft Azure dosya hizmetine giriş</span><span class="sxs-lookup"><span data-stu-id="68a30-187">Introducing Microsoft Azure File Service</span></span>](https://blogs.msdn.microsoft.com/windowsazurestorage/2014/05/12/introducing-microsoft-azure-file-service/)
- [<span data-ttu-id="68a30-188">Microsoft Azure dosyalara yönelik kalıcı bağlantılar</span><span class="sxs-lookup"><span data-stu-id="68a30-188">Persisting connections to Microsoft Azure Files</span></span>](https://blogs.msdn.microsoft.com/windowsazurestorage/2014/05/26/persisting-connections-to-microsoft-azure-files/)
