---
title: F# kullanarak Azure Dosya depolama kullanmaya başlama
description: Azure File Storage ile verileri bulutta depolayın ve Azure Virtual Machine (VM) veya Windows çalıştıran şirket içi bir uygulamadan buluta bir dosya paylaşımı bağlayın.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 04bee82fd9d3c652cd99b9c951880f6ba89610ee
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90548468"
---
# <a name="get-started-with-azure-file-storage-using-f"></a>F kullanarak Azure dosya depolama ile çalışmaya başlama\#

Azure dosya depolama, standart [sunucu Ileti bloğu (SMB) protokolünü](/windows/win32/fileio/microsoft-smb-protocol-and-cifs-protocol-overview)kullanarak bulutta dosya paylaşımları sunan bir hizmettir. SMB 2.1 ve SMB 3.0 desteklenir. Azure File Storage, Azure’a dosya paylaşımı kullanan eski uygulamaları maliyetli yeniden yazdırmaya ihtiyaç duymadan ve hızla taşıyabilmenizi sağlar. Azure Virtual Machines’de, Cloud Services’da veya şirket içi istemcilerde çalışan uygulamalar, bir masaüstü uygulamanın tipik SMB paylaşımı bağladığı gibi buluta bir dosya paylaşımı bağlayabilir. Ardından herhangi sayıda uygulama bileşeni eş zamanlı olarak File Storage paylaşımını bağlayıp buna erişim sağlayabilir.

Dosya depolamaya kavramsal bir genel bakış için bkz. [dosya depolama için .net Kılavuzu](/azure/storage/storage-dotnet-how-to-use-files).

## <a name="prerequisites"></a>Önkoşullar

Bu kılavuzu kullanmak için önce [bir Azure depolama hesabı oluşturmanız](/azure/storage/storage-create-storage-account)gerekir.
Ayrıca, bu hesap için depolama erişim anahtarınız gerekecektir.

## <a name="create-an-f-script-and-start-f-interactive"></a>F # betiği oluşturun ve F# Etkileşimli başlatın

Bu makaledeki örnekler bir F # uygulamasında veya F # betiğinde kullanılabilir. F # betiği oluşturmak için, `.fsx` Örneğin `files.fsx` f # geliştirme ortamınızda uzantılı bir dosya oluşturun.

Daha sonra, [NuGet](https://www.nuget.org/) [Paket](https://fsprojects.github.io/Paket/) paketi [package manager](package-management.md) `WindowsAzure.Storage` ve `WindowsAzure.Storage.dll` bir yönerge kullanarak betiğe paket ve başvuru yüklemek için, paket veya NuGet gibi bir paket Yöneticisi kullanın `#r` .

### <a name="add-namespace-declarations"></a>Ad alanı bildirimleri ekleme

Aşağıdaki `open` bildirimlerini `files.fsx` dosyasının üstüne ekleyin:

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a>Bağlantı dizenizi alma

Bu öğretici için bir Azure depolama bağlantı dizesi gerekir. Bağlantı dizeleri hakkında daha fazla bilgi için bkz. [depolama bağlantı dizelerini yapılandırma](/azure/storage/storage-configure-connection-string).

Öğreticide, aşağıdaki gibi, komut dosyası için Bağlantı dizenizi girersiniz:

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L11-L11)]

Ancak, bu gerçek projeler için **önerilmez** . Depolama hesabı anahtarınız depolama hesabınızın kök parolasına benzer. Depolama hesabı anahtarınızı korumak için her zaman özen gösterin. Diğer kullanıcılara dağıtmaktan, sabit kodlamaktan ve başkalarının erişebileceği düz metin dosyasına kaydetmekten kaçının. Azure portal tehlikede olduğunu düşünüyorsanız, anahtarınızı yeniden oluşturabilirsiniz.

Gerçek uygulamalar için, depolama Bağlantı dizenizi korumak için en iyi yol bir yapılandırma dosyasıdır. Bağlantı dizesini bir yapılandırma dosyasından getirmek için şunu yapabilirsiniz:

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L13-L15)]

Azure Yapılandırma Yöneticisi'ni kullanmak isteğe bağlıdır. .NET Framework türü gibi bir API de kullanabilirsiniz `ConfigurationManager` .

### <a name="parse-the-connection-string"></a>Bağlantı dizesini ayrıştırma

Bağlantı dizesini ayrıştırmak için şunu kullanın:

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L21-L22)]

Bu, döndürür `CloudStorageAccount` .

### <a name="create-the-file-service-client"></a>Dosya hizmeti istemcisini oluşturma

`CloudFileClient`Türü, dosya depolama alanında depolanan dosyaları programlı olarak kullanmanıza olanak sağlar. Hizmet istemcisini oluşturma yöntemlerinden biri aşağıda verilmiştir:

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L28-L28)]

Artık, verileri okuyan ve dosya depolama alanına veri yazan kodu yazmaya hazırsınız.

## <a name="create-a-file-share"></a>Dosya paylaşımı oluşturma

Bu örnek, zaten yoksa bir dosya paylaşımının nasıl oluşturulacağını gösterir:

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L34-L35)]

## <a name="create-a-root-directory-and-a-subdirectory"></a>Kök dizin ve alt dizin oluşturma

Burada kök dizini alır ve kökün bir alt dizinini alırsınız. Zaten mevcut değilse oluşturun.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L41-L43)]

## <a name="upload-text-as-a-file"></a>Metni dosya olarak karşıya yükle

Bu örnekte, metnin dosya olarak nasıl yükleneceği gösterilmektedir.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L49-L50)]

### <a name="download-a-file-to-a-local-copy-of-the-file"></a>Dosyanın yerel kopyasına bir dosya indir

Burada, yeni oluşturulan dosyayı indirerek içeriği yerel bir dosyaya ekleyin.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L56-L56)]

### <a name="set-the-maximum-size-for-a-file-share"></a>Dosya paylaşımı için boyut üst sınırını ayarlama

Aşağıdaki örnekte, paylaşımdaki mevcut kullanımını nasıl kontrol edileceği veya paylaşım için nasıl kota ayarlanacağı gösterilmiştir. `FetchAttributes` bir paylaşımın doldurulmasında `Properties` ve `SetProperties` Yerel değişiklikleri Azure dosya depolama alanına yaymaya yönelik olarak çağrılmalıdır.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L62-L72)]

### <a name="generate-a-shared-access-signature-for-a-file-or-file-share"></a>Dosya veya dosya paylaşımı için paylaşılan erişim imzası oluşturma

Bir dosya paylaşımında veya tek bir dosya için paylaşılan erişim imzası (SAS) oluşturabilirsiniz. Ayrıca, paylaşılan erişim imzalarını yönetmek için dosya paylaşımında bir paylaşılan erişim ilkesi oluşturabilirsiniz. Gizliliğinin tehlikeye girdiği durumlarda SAS’yi iptal etme aracı olarak kullanılabilmesi nedeniyle bir paylaşılan erişim ilkesi oluşturmanız önerilir.

Burada, bir paylaşımda paylaşılan erişim ilkesi oluşturun ve ardından bu ilkeyi kullanarak paylaşımdaki bir dosya üzerindeki bir SAS için kısıtlamalar sağlayabilirsiniz.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L78-L94)]

Paylaşılan erişim imzaları oluşturma ve kullanma hakkında daha fazla bilgi edinmek için bkz. [Paylaşılan Erişim İmzaları (SAS) kullanma](/azure/storage/storage-dotnet-shared-access-signature-part-1) ve [Blob depolama ile SAS oluşturma ve kullanma](/azure/storage/storage-dotnet-shared-access-signature-part-2).

### <a name="copy-files"></a>Dosyaları kopyalama

Bir dosyayı başka bir dosyaya veya blob 'a ya da bir bloba bir dosyaya kopyalayabilirsiniz. Bir blobu bir dosyaya veya bir dosyayı bir bloba kopyalıyorsanız, aynı depolama hesabı içinde kopyalama olsanız bile, kaynak nesnenin kimliğini doğrulamak için bir paylaşılan erişim imzası (SAS) kullanmanız *gerekir* .

### <a name="copy-a-file-to-another-file"></a>Dosyayı başka bir dosyaya kopyalama

Burada, bir dosyayı aynı paylaşımdaki başka bir dosyaya kopyalayabilirsiniz. Bu kopyalama işlemi aynı depolama hesabındaki dosyaları kopyaladığı için, kopyalama işlemini gerçekleştirmek üzere Paylaşılan Anahtar kimlik doğrulaması kullanabilirsiniz. 

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L100-L101)]

### <a name="copy-a-file-to-a-blob"></a>Dosyayı bir bloba kopyalama

Burada, bir dosya oluşturup aynı depolama hesabı içindeki bir bloba kopyalayabilirsiniz. Kaynak dosya için, hizmetin kopyalama işlemi sırasında kaynak dosyaya erişimin kimliğini doğrulamak için kullandığı bir SAS oluşturursunuz.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L107-L120)]

Aynı şekilde, bir blobu bir dosyaya kopyalayabilirsiniz. Kaynak dosya bir blob ise, kopyalama sırasında bu bloba erişimin kimlik doğrulamasını yapması için bir SAS oluşturun.

## <a name="troubleshooting-file-storage-using-metrics"></a>Ölçümleri kullanarak File Storage sorunlarını giderme

Azure Depolama Analizi dosya depolama için ölçümleri destekler. Ölçüm verilerini kullanarak istekleri ve tanılama sorunlarını izleyebilirsiniz.

[Azure Portal](https://portal.azure.com)dosya depolama için ölçümleri etkinleştirebilir veya bunun gibi F # ' dan yapabilirsiniz:

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L126-L140)]

## <a name="next-steps"></a>Sonraki adımlar

Azure dosya depolama hakkında daha fazla bilgi için bu bağlantılara bakın.

### <a name="conceptual-articles-and-videos"></a>Kavramsal makaleler ve videolar

- [Azure File Storage: Windows ve Linux için uyumlu bulut SMB dosya sistemi](https://azure.microsoft.com/resources/videos/azurecon-2015-azure-files-storage-a-frictionless-cloud-smb-file-system-for-windows-and-linux/)
- [Linux ile Azure dosya depolama kullanma](/azure/storage/storage-how-to-use-files-linux)

### <a name="tooling-support-for-file-storage"></a>File Storage için araç desteği

- [Azure Storage ile Azure PowerShell’i kullanma](/azure/storage/storage-powershell-guide-full)
- [Microsoft Azure Depolama ile AzCopy kullanma](/azure/storage/storage-use-azcopy)
- [Azure CLı ile Bloblar oluşturun, indirin ve listeleyin](/azure/storage/blobs/storage-quickstart-blobs-cli#create-and-manage-file-shares)

### <a name="reference"></a>Başvuru

- [.NET için depolama Istemci kitaplığı başvurusu](/dotnet/api/overview/azure/storage)
- [Dosya Hizmeti REST API başvurusu](/rest/api/storageservices/fileservices/File-Service-REST-API)

### <a name="blog-posts"></a>Blog yazıları

- [Azure Dosya Depolama genel kullanıma sunulmuştur](https://azure.microsoft.com/blog/azure-file-storage-now-generally-available/)
- [Azure dosya depolama alanı içinde](https://azure.microsoft.com/blog/inside-azure-file-storage/)
- [Microsoft Azure Dosya Hizmeti’ne Giriş](/archive/blogs/windowsazurestorage/introducing-microsoft-azure-file-service)
- [Microsoft Azure Dosyaları ile kalıcı bağlantılar](/archive/blogs/windowsazurestorage/persisting-connections-to-microsoft-azure-files)
