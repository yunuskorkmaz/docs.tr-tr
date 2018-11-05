---
title: F# kullanarak Azure dosya depolama ile çalışmaya başlama
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
# <a name="get-started-with-azure-file-storage-using-f"></a>F# kullanarak Azure dosya depolama ile çalışmaya başlama #

Azure dosya depolama, standart kullanarak bulutta dosya paylaşımları sağlayan bir hizmettir [sunucu ileti bloğu (SMB) Protokolü](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx). SMB 2.1 ve SMB 3.0 desteklenir. Azure dosya depolama ile hızlı ve pahalı yeniden yazmalar olmadan Azure dosya paylaşımları kullanan eski uygulamaları geçirebilirsiniz. Azure sanal makineleri veya Bulut Hizmetleri veya şirket içi istemcilerden çalışan uygulamalar, yalnızca bir masaüstü uygulamanın tipik bir SMB paylaşımına bağlandığı şekilde bulutta dosya paylaşımı bağlayabilir. Uygulama bileşenleri herhangi bir sayıda sonra bağlayın ve File storage paylaşımını bağlayıp buna erişim.

Dosya depolama kavramsal bir genel bakış için bkz. Lütfen [dosya depolama için .NET Kılavuzu](/azure/storage/storage-dotnet-how-to-use-files).

## <a name="prerequisites"></a>Önkoşullar

Bu kılavuzu kullanmak için önce [bir Azure depolama hesabı oluşturma](/azure/storage/storage-create-storage-account).
Ayrıca, bu hesap için depolama erişim anahtarınızı gerekir.

## <a name="create-an-f-script-and-start-f-interactive"></a>Bir F# komut dosyası ve başlangıç F# Etkileşimli oluşturma

Bu makaledeki örnekleri, F# uygulaması veya bir F# komut dosyası kullanılabilir. Bir F# komut dosyası oluşturmak için bir dosya oluşturun. `.fsx` uzantısı, örneğin `files.fsx`, F# geliştirme ortamınızda.

Ardından, bir [Paket Yöneticisi](package-management.md) gibi [Paket](https://fsprojects.github.io/Paket/) veya [NuGet](https://www.nuget.org/) yüklemek için `WindowsAzure.Storage` paket ve başvuru `WindowsAzure.Storage.dll` bir kullanarakbetiğinizde`#r`yönergesi.

### <a name="add-namespace-declarations"></a>Ad alanı bildirimleri ekleme

Aşağıdaki `open` üst tarafına deyimlerini `files.fsx` dosyası:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a>Bağlantı dizenizi alma

Bu öğreticide bir Azure depolama bağlantı dizesi gerekir. Bağlantı dizeleri hakkında daha fazla bilgi için bkz. [depolama bağlantı dizelerini yapılandırma](/azure/storage/storage-configure-connection-string).

Öğretici için şunun gibi komut dosyanızdaki bağlantı dizenizi girmenizi isteriz:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L11-L11)]

Ancak, bu, **önerilmez** gerçek projeleri. Depolama hesabı anahtarınız depolama hesabınızın kök parolasına benzer. Her zaman depolama hesabı anahtarınızı korumak dikkatli olun. Sabit kodlama veya başkalarının erişebileceği bir düz metin dosyasına kaydederek diğer kullanıcılara dağıtmaktan kaçının. Tehlikeye girmiş olabilecek düşünüyorsanız Azure portalını kullanarak anahtarınızı yeniden oluşturabilirsiniz.

Gerçek uygulamalar, depolama bağlantı dizenizi korumak için en iyi yolu, içinde bir yapılandırma dosyasıdır. Bir yapılandırma dosyasından bağlantı dizesini getirmek için bunu yapabilirsiniz:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L13-L15)]

Azure Yapılandırma Yöneticisi'ni kullanmak isteğe bağlıdır. .NET Framework'ün gibi bir API de kullanabilirsiniz `ConfigurationManager` türü.

### <a name="parse-the-connection-string"></a>Bağlantı dizesini ayrıştırma

Bağlantı dizesini ayrıştırmak için kullanın:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L21-L22)]

Bu döndürür bir `CloudStorageAccount`.

### <a name="create-the-file-service-client"></a>Dosya hizmeti istemcisi oluşturma

`CloudFileClient` Türü dosya depolama alanında depolanmış dosyaları programlı olarak kullanmanıza olanak sağlar. Hizmet istemcisini oluşturma yöntemlerinden biri aşağıda verilmiştir:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L28-L28)]

Artık, okuyan ve dosya depolamaya veri yazan kodu yazmaya hazırsınız.

## <a name="create-a-file-share"></a>Dosya paylaşımı oluşturma

Bu örnek, zaten yoksa, bir dosya paylaşımı oluşturma işlemini gösterir:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L34-L35)]

## <a name="create-a-root-directory-and-a-subdirectory"></a>Kök dizin ve bir alt dizin oluşturma

Kök dizin, burada size ve bir alt kök dizini alın. Henüz yoksa her ikisi de oluşturun.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L41-L43)]

## <a name="upload-text-as-a-file"></a>Metin dosyası olarak karşıya yükleme

Bu örnek metin dosyası olarak karşıya yükleme işlemini gösterir.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L49-L50)]

### <a name="download-a-file-to-a-local-copy-of-the-file"></a>Dosyanın yerel bir kopyasını dosya indirme

Burada oluşturduğunuz, dosyanın içeriğini yerel bir dosyaya ekleme indirin.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L56-L56)]

### <a name="set-the-maximum-size-for-a-file-share"></a>Bir dosya paylaşımı için boyut üst sınırı ayarlayın

Aşağıdaki örnekte bir paylaşım için geçerli kullanım denetleme ve paylaşımı için kota ayarlamak nasıl gösterir. `FetchAttributes` bir paylaşımın doldurmak için çağrılmalıdır `Properties`, ve `SetProperties` Azure dosya depolama yerel değişiklikleri yaymak için.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L62-L72)]

### <a name="generate-a-shared-access-signature-for-a-file-or-file-share"></a>Bir dosya veya dosya paylaşımı için paylaşılan erişim imzası oluşturma

Paylaşılan erişim imzası (SAS) tek bir dosyayı veya dosya paylaşımı için oluşturabilirsiniz. Ayrıca, paylaşılan erişim imzalarını yönetmek için bir dosya paylaşımında bir paylaşılan erişim ilkesi oluşturabilirsiniz. Tehlikeye girdiği durumlarda SAS'yi iptal etme yolu sağladığından bir paylaşılan erişim ilkesi oluşturmanız önerilir.

Burada, paylaşılan oluşturduğunuz erişim ilkesi paylaşımındaki ve bu ilke paylaşımdaki bir dosya çubuğunda bir SAS için sınırlamalar sağlamak için kullanın.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L78-L94)]

Paylaşılan erişim imzaları oluşturma ve kullanma hakkında daha fazla bilgi için bkz. [kullanarak paylaşılan erişim imzaları (SAS)](/azure/storage/storage-dotnet-shared-access-signature-part-1) ve [oluşturma ve kullanma Blob Depolama ile SAS](/azure/storage/storage-dotnet-shared-access-signature-part-2).

### <a name="copy-files"></a>Dosyaları Kopyala

Başka bir dosyaya veya bir bloba veya bir blobu bir dosyaya bir dosyaya kopyalayabilirsiniz. Bir blobu bir dosyaya veya bir blobu bir dosyaya kopyalıyorsanız, *gerekir* aynı depolama hesabında kopyalama yapıyor olsanız da kaynak nesnesinin kimliğini doğrulamak için bir paylaşılan erişim imzası (SAS) kullanın.

### <a name="copy-a-file-to-another-file"></a>Bir dosyayı başka bir dosyaya kopyalama

Burada, bir dosya aynı paylaşımdaki başka bir dosyaya kopyalayın. Bu kopyalama işlemi arasında aynı depolama hesabındaki dosyaları kopyaladığı için kopyalama işlemini gerçekleştirmek için paylaşılan anahtar kimlik doğrulaması'nı kullanabilirsiniz.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L100-L101)]

### <a name="copy-a-file-to-a-blob"></a>Bir dosyayı bir bloba kopyalama

Burada, bir dosya oluşturun ve aynı depolama hesabındaki bir bloba kopyalama. Hizmetin kopyalama işlemi sırasında kaynak dosyaya erişimin kimlik doğrulaması için kullandığı kaynak dosyası için bir SAS oluşturabilirsiniz.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L107-L120)]

Bir blobu bir dosyaya aynı şekilde kopyalayabilirsiniz. Kaynak nesne bir blob ise, ardından kopyalama işlemi sırasında bu bloba erişimin kimlik doğrulaması için bir SAS oluşturun.

## <a name="troubleshooting-file-storage-using-metrics"></a>Ölçümleri kullanarak File storage sorunlarını giderme

Azure depolama analizi, File storage için ölçümleri destekliyor. Ölçüm verilerini kullanarak istekleri izleyebilir ve sorunları tanılayabilir.

Dosya depolama ölçümlerini etkinleştirebilirsiniz [Azure portalı](https://portal.azure.com), ya da bunu F# şöyle:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L126-L140)]

## <a name="next-steps"></a>Sonraki adımlar

Azure dosya depolama hakkında daha fazla bilgi için şu bağlantılara göz atın.

### <a name="conceptual-articles-and-videos"></a>Kavramsal makaleler ve videolar

- [Azure dosya depolama: uyumlu bulut SMB dosya sistemi Windows ve Linux için](https://azure.microsoft.com/resources/videos/azurecon-2015-azure-files-storage-a-frictionless-cloud-smb-file-system-for-windows-and-linux/)
- [Nasıl Azure dosya depolamayı Linux ile kullanma](/azure/storage/storage-how-to-use-files-linux)

### <a name="tooling-support-for-file-storage"></a>Dosya depolama için araç desteği

- [Azure PowerShell'i Azure depolama ile kullanma](/azure/storage/storage-powershell-guide-full)
- [Microsoft Azure Storage ile AzCopy kullanma](/azure/storage/storage-use-azcopy)
- [Azure CLI ile Azure depolama kullanma](/azure/storage/storage-azure-cli#create-and-manage-file-shares)

### <a name="reference"></a>Başvuru

- [.NET başvurusu için depolama istemcisi kitaplığı](https://msdn.microsoft.com/library/azure/mt347887.aspx)
- [Dosya hizmeti REST API Başvurusu](/rest/api/storageservices/fileservices/File-Service-REST-API)

### <a name="blog-posts"></a>Blog gönderileri

- [Azure dosya depolama genel kullanıma sunulmuştur](https://azure.microsoft.com/blog/azure-file-storage-now-generally-available/)
- [Azure dosya depolama incelemesi](https://azure.microsoft.com/blog/inside-azure-file-storage/) 
- [Microsoft Azure dosya Hizmeti'ne Giriş](https://blogs.msdn.microsoft.com/windowsazurestorage/2014/05/12/introducing-microsoft-azure-file-service/)
- [Microsoft Azure dosyaları ile kalıcı bağlantılar](https://blogs.msdn.microsoft.com/windowsazurestorage/2014/05/26/persisting-connections-to-microsoft-azure-files/)
