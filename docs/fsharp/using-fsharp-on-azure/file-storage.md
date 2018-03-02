---
title: "F # kullanarak Azure File storage'ı kullanmaya başlama"
description: "Azure File storage ile bulutta dosya verileri depolamak ve bir Azure sanal makineden (VM), bulut dosya paylaşımını bağlama veya bir şirket içi uygulamasından Windows çalıştırıyor."
keywords: "Visual f #, f #, işlev, .NET, .NET Core, Azure programlama"
author: sylvanc
ms.author: phcart
ms.date: 09/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 5c26a0aa-186e-476c-9f87-e0191754579e
ms.openlocfilehash: 5e1f6914acad5ae8c7148a7238e2d1d6a8ca5867
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2018
---
# <a name="get-started-with-azure-file-storage-using-f"></a>F # kullanarak Azure File storage'ı kullanmaya başlama #

Azure File storage bu dosya paylaşımları standardını kullanarak bulutta sunan hizmet [sunucu ileti bloğu (SMB) Protokolü](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx). SMB 2.1 ve SMB 3.0 desteklenir. Azure File storage ile maliyetli yeniden yazdırmaya gerek duymadan ve hızla Azure'a dosya paylaşımı kullanan eski uygulamalar geçirebilirsiniz. Azure virtual machines veya cloud services veya şirket içi istemcilerde çalışan uygulamalar, yalnızca bir masaüstü uygulamasının tipik bir SMB paylaşımına bağlandığı şekilde buluta bir dosya paylaşımı bağlayabilir. Uygulama bileşenleri herhangi bir sayıda sonra bağlayabilir ve File storage paylaşımını bağlayıp buna erişim.

Dosya depolama kavramsal bir genel bakış için lütfen bkz [file storage için .NET Kılavuzu](/azure/storage/storage-dotnet-how-to-use-files).

## <a name="prerequisites"></a>Önkoşullar

Bu kılavuzu kullanmak için öncelikle [bir Azure depolama hesabı oluşturma](/azure/storage/storage-create-storage-account).
Bu hesap için depolama erişim anahtarınızı de gerekir.

## <a name="create-an-f-script-and-start-f-interactive"></a>Bir F # betiği ve başlangıç F # Etkileşimli oluşturma

Bu makaledeki örnekler, F # uygulaması veya F # betiği kullanılabilir. F # betiği oluşturmak için dosya oluştur `.fsx` uzantısı, örneğin `files.fsx`, ortamınızdaki F # geliştirme.

Ardından, kullanın bir [Paket Yöneticisi](package-management.md) gibi [Paket](https://fsprojects.github.io/Paket/) veya [NuGet](https://www.nuget.org/) yüklemek için `WindowsAzure.Storage` paket ve başvuru `WindowsAzure.Storage.dll` bir kullanarakkomut`#r`yönergesi.

### <a name="add-namespace-declarations"></a>Ad alanı bildirimleri ekleme

Aşağıdakileri ekleyin `open` deyimleri üstüne `files.fsx` dosyası:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a>Bağlantı dizenizi Al

Bu öğretici için bir Azure depolama bağlantı dizesi gerekir. Bağlantı dizeleri hakkında daha fazla bilgi için bkz: [Storage bağlantı dizelerini yapılandırma](/azure/storage/storage-configure-connection-string).

Öğretici için şuna benzer betiğinizin bağlantı dizenizi girin:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L11-L11)]

Ancak, bu olduğu **önerilmez** için gerçek projeleri. Depolama hesabı anahtarınız depolama hesabınızın kök parolasına benzer. Her zaman depolama hesabı anahtarınızı korumak dikkatli olun. Sabit kodlama veya başkalarının erişebileceği düz metin dosyasına kaydetme diğer kullanıcılara dağıtmaktan kaçının. Bunu tehlikede olduğunu düşünüyorsanız, Azure Portalı'nı kullanarak anahtarınızı yeniden oluşturabilirsiniz.

İçin gerçek uygulamalar, depolama bağlantı dizenizi korumak için en iyi yapılandırma dosyasında yoludur. Yapılandırma dosyasından bağlantı dizesini almak için bunu yapabilirsiniz:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L13-L15)]

Azure Yapılandırma Yöneticisi'ni kullanarak isteğe bağlıdır. .NET Framework'ün gibi bir API de kullanabilirsiniz `ConfigurationManager` türü.

### <a name="parse-the-connection-string"></a>Bağlantı dizesini ayrıştırma

Bağlantı dizesini ayrıştırmak için kullanın:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L21-L22)]

Bu döndürülecek bir `CloudStorageAccount`.

### <a name="create-the-file-service-client"></a>Dosya hizmeti istemcisi oluşturma

`CloudFileClient` Türü File storage'da depolanan dosyaları programlı olarak kullanmanıza olanak sağlar. Hizmet istemcisini oluşturma yöntemlerinden biri aşağıda verilmiştir:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L28-L28)]

Şimdi veri okuyan ve dosya depolama alanına veri yazan kodu yazmaya hazırsınız.

## <a name="create-a-file-share"></a>Dosya paylaşımı oluşturma

Bu örnek, zaten yoksa, bir dosya paylaşımı oluşturmak gösterilmektedir:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L34-L35)]

## <a name="create-a-root-directory-and-a-subdirectory"></a>Bir kök dizin ve bir alt dizin oluşturma

Burada, kök dizini almak ve bir alt dizinin kök alın. Henüz yoksa her ikisini de oluşturun.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L41-L43)]

## <a name="upload-text-as-a-file"></a>Metin dosyası olarak karşıya yükleme

Bu örnek metin dosyası olarak karşıya nasıl yükleneceğini gösterir.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L49-L50)]

### <a name="download-a-file-to-a-local-copy-of-the-file"></a>Dosyanın yerel bir kopyasını dosya indirme

Burada oluşturduğunuz, dosya yerel bir dosyaya içeriği ekleme indirin.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L56-L56)]

### <a name="set-the-maximum-size-for-a-file-share"></a>Bir dosya paylaşımı için en büyük boyutunu ayarlama

Aşağıdaki örnek, bir paylaşım için geçerli kullanım kontrol etme ve paylaşımı için kota ayarlanamıyor gösterir. `FetchAttributes` bir paylaşımın doldurmak için çağrılmalıdır `Properties`, ve `SetProperties` Azure File storage yerel değişiklikleri yaymak için.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L62-L72)]

### <a name="generate-a-shared-access-signature-for-a-file-or-file-share"></a>Bir dosya veya dosya paylaşımı için bir paylaşılan erişim imzası oluşturma

Paylaşılan erişim imzası (SAS) tek bir dosyayı veya dosya paylaşımı için oluşturabilirsiniz. Ayrıca, paylaşılan erişim imzalarını yönetmek için bir dosya paylaşımında bir paylaşılan erişim ilkesi oluşturabilirsiniz. Tehlikeye girdiği durumlarda SAS iptal etme yolu sağladığı gibi bir paylaşılan erişim ilkesi oluşturmanız önerilir.

Burada, paylaşılan oluşturduğunuz erişim ilkesi paylaşımındaki ve bir dosya paylaşımında SAS için sınırlamalar sağlamak için bu ilkeyi kullanın.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L78-L94)]

Oluşturma ve paylaşılan erişim imzaları kullanma hakkında daha fazla bilgi için bkz: [kullanarak paylaşılan erişim imzaları (SAS)](/azure/storage/storage-dotnet-shared-access-signature-part-1) ve [oluşturma ve kullanma Blob storage ile SAS](/azure/storage/storage-dotnet-shared-access-signature-part-2).

### <a name="copy-files"></a>Dosyaları kopyalama

Bir dosyayı başka bir dosyaya veya bir blob veya bir blobu bir dosyaya kopyalayabilirsiniz. Bir blobu bir dosyaya veya bir blobu bir dosyaya kopyalama yapıyorsanız, *gerekir* aynı depolama hesabında kopyalama yapıyor olsanız kaynak nesne kimlik doğrulaması için paylaşılan erişim imzası (SAS) kullanın.

### <a name="copy-a-file-to-another-file"></a>Bir dosyayı başka bir dosyaya kopyalama

Burada, bir dosya aynı paylaşımdaki başka bir dosyaya kopyalayın. Bu kopyalama işlemi aynı depolama hesabındaki dosyaları kopyaladığı için kopyalama işlemini gerçekleştirmek için paylaşılan anahtar kimlik doğrulaması kullanabilirsiniz.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L100-L101)]

### <a name="copy-a-file-to-a-blob"></a>Bir dosyayı bir bloba kopyalama

Burada, bir dosya oluşturun ve aynı depolama hesabındaki bir bloba kopyalama. Hizmetin kopyalama işlemi sırasında kaynak dosyaya erişimin kimlik doğrulaması yapmak için kullandığı kaynak dosya için bir SAS oluşturun.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L107-L120)]

Aynı şekilde bir blobu bir dosyaya kopyalayabilirsiniz. Kaynak nesne bir blob ise, bu erişim kopyalama işlemi sırasında kimlik doğrulaması için bir SAS oluşturun.

## <a name="troubleshooting-file-storage-using-metrics"></a>Ölçümleri kullanarak File storage sorunlarını giderme

Azure Storage Analytics ölçümleri File storage için destekler. Ölçüm verilerini kullanarak istekleri izleme ve sorunlarını tanılamak.

Dan File storage için ölçümleri etkinleştirebilirsiniz [Azure Portal](https://portal.azure.com), veya bunu F # şu şekilde yapabilirsiniz:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L126-L140)]

## <a name="next-steps"></a>Sonraki adımlar

Azure File storage hakkında daha fazla bilgi için şu bağlantılara bakın.

### <a name="conceptual-articles-and-videos"></a>Kavramsal makaleler ve videolar

- [Azure File Storage: uyumlu bulut SMB dosya sistemi Windows ve Linux için](https://azure.microsoft.com/resources/videos/azurecon-2015-azure-files-storage-a-frictionless-cloud-smb-file-system-for-windows-and-linux/)
- [Azure File Storage Linux ile kullanma](/azure/storage/storage-how-to-use-files-linux)

### <a name="tooling-support-for-file-storage"></a>File storage için araç desteği

- [Azure Storage ile Azure PowerShell'i kullanma](/azure/storage/storage-powershell-guide-full)
- [Microsoft Azure Storage ile AzCopy kullanma](/azure/storage/storage-use-azcopy)
- [Azure Storage ile Azure CLI kullanma](/azure/storage/storage-azure-cli#create-and-manage-file-shares)

### <a name="reference"></a>Başvuru

- [.NET başvurusu için depolama istemci kitaplığı](https://msdn.microsoft.com/library/azure/mt347887.aspx)
- [Dosya hizmeti REST API'si başvurusu](/rest/api/storageservices/fileservices/File-Service-REST-API)

### <a name="blog-posts"></a>Blog gönderileri

- [Azure File storage genel kullanıma sunulmuştur](https://azure.microsoft.com/blog/azure-file-storage-now-generally-available/)
- [Azure File Storage incelemesi](https://azure.microsoft.com/blog/inside-azure-file-storage/) 
- [Microsoft Azure dosya Hizmeti'ne Giriş](https://blogs.msdn.microsoft.com/windowsazurestorage/2014/05/12/introducing-microsoft-azure-file-service/)
- [Microsoft Azure dosyaları ile kalıcı bağlantılar](https://blogs.msdn.microsoft.com/windowsazurestorage/2014/05/26/persisting-connections-to-microsoft-azure-files/)
