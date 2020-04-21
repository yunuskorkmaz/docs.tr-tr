---
title: F# kullanarak Azure Dosya depolama kullanmaya başlama
description: Azure File Storage ile verileri bulutta depolayın ve Azure Virtual Machine (VM) veya Windows çalıştıran şirket içi bir uygulamadan buluta bir dosya paylaşımı bağlayın.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 1b38ee53f2f73f7b7f4ee12f712f487cb726d41e
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739596"
---
# <a name="get-started-with-azure-file-storage-using-f"></a>F kullanarak Azure Dosya depolama sına başlayın\#

Azure Dosya depolama standart [Server Message Block (SMB) Protokolü](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx)kullanarak bulutta dosya paylaşımları sunan bir hizmettir. SMB 2.1 ve SMB 3.0 desteklenir. Azure File Storage, Azure’a dosya paylaşımı kullanan eski uygulamaları maliyetli yeniden yazdırmaya ihtiyaç duymadan ve hızla taşıyabilmenizi sağlar. Azure Virtual Machines’de, Cloud Services’da veya şirket içi istemcilerde çalışan uygulamalar, bir masaüstü uygulamanın tipik SMB paylaşımı bağladığı gibi buluta bir dosya paylaşımı bağlayabilir. Ardından herhangi sayıda uygulama bileşeni eş zamanlı olarak File Storage paylaşımını bağlayıp buna erişim sağlayabilir.

Dosya depolamaya kavramsal bir genel bakış [için, dosya depolama için .NET kılavuzuna](https://docs.microsoft.com/azure/storage/storage-dotnet-how-to-use-files)bakın.

## <a name="prerequisites"></a>Ön koşullar

Bu kılavuzu kullanmak için öncelikle [bir Azure depolama hesabı oluşturmanız](https://docs.microsoft.com/azure/storage/storage-create-storage-account)gerekir.
Ayrıca bu hesap için depolama erişim anahtarına da ihtiyacınız olacak.

## <a name="create-an-f-script-and-start-f-interactive"></a>F# Komut Dosyası Oluştur ve F# İnteraktif Başlat

Bu makaledeki örnekler f# uygulamasında veya F# komut dosyasında kullanılabilir. F# komut dosyası oluşturmak için, `.fsx` örneğin `files.fsx`F# geliştirme ortamınızda uzantılı bir dosya oluşturun.

Ardından, `WindowsAzure.Storage` paketi yüklemek ve bir yönerge kullanarak komut `WindowsAzure.Storage.dll` dosyanıza başvurmak `#r` için [Paket](https://fsprojects.github.io/Paket/) veya [NuGet](https://www.nuget.org/) gibi bir [paket yöneticisi](package-management.md) kullanın.

### <a name="add-namespace-declarations"></a>Ad alanı bildirimleri ekleme

Aşağıdaki `open` bildirimlerini `files.fsx` dosyasının üstüne ekleyin:

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a>Bağlantı dizenizi alma

Bu öğretici için bir Azure Depolama bağlantı dizeniz gerekir. Bağlantı dizeleri hakkında daha fazla bilgi için [bkz.](https://docs.microsoft.com/azure/storage/storage-configure-connection-string)

Öğretici için, bağlantı dizenizi komut dosyanıza şu şekilde girersiniz:

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L11-L11)]

Ancak, bu gerçek projeler için **tavsiye edilmez.** Depolama hesabı anahtarınız depolama hesabınızın kök parolasına benzer. Depolama hesabı anahtarınızı korumak için her zaman özen gösterin. Diğer kullanıcılara dağıtmaktan, sabit kodlamaktan ve başkalarının erişebileceği düz metin dosyasına kaydetmekten kaçının. Kilitlendiğini düşünüyorsanız, anahtarınızı Azure portalını kullanarak yeniden oluşturabilirsiniz.

Gerçek uygulamalariçin depolama bağlantı dizenizi korumanın en iyi yolu yapılandırma dosyasındadır. Bağlantı dizesini yapılandırma dosyasından almak için şunları yapabilirsiniz:

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L13-L15)]

Azure Yapılandırma Yöneticisi'ni kullanmak isteğe bağlıdır. .NET Framework `ConfigurationManager` türü gibi bir API de kullanabilirsiniz.

### <a name="parse-the-connection-string"></a>Bağlantı dizesini ayrıştırma

Bağlantı dizesini ayrışdırmak için şunları kullanın:

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L21-L22)]

Bu bir `CloudStorageAccount`.

### <a name="create-the-file-service-client"></a>Dosya hizmeti istemcisini oluşturma

Tür, `CloudFileClient` Dosya depolama alanında depolanan dosyaları programlı olarak kullanmanıza olanak tanır. Hizmet istemcisini oluşturma yöntemlerinden biri aşağıda verilmiştir:

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L28-L28)]

Artık verileri okuyan ve Dosya depolamasına veri yazan kod yazmaya hazırsınız.

## <a name="create-a-file-share"></a>Dosya paylaşımı oluşturma

Bu örnek, dosya paylaşımının nasıl oluşturulabildiğini gösterir:

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L34-L35)]

## <a name="create-a-root-directory-and-a-subdirectory"></a>Kök dizini ve alt dizini oluşturma

Burada, kök dizini almak ve kök bir alt dizini olsun. Zaten yoksa ikisini de oluşturursunuz.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L41-L43)]

## <a name="upload-text-as-a-file"></a>Metin dosya olarak yükleme

Bu örnek, dosya olarak metin yüklemeyi gösterir.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L49-L50)]

### <a name="download-a-file-to-a-local-copy-of-the-file"></a>Dosyayı dosyanın yerel bir kopyasına karşı yükleme

Burada, içeriği yerel bir dosyaya ekolarak, yeni oluşturulan dosyayı indirin.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L56-L56)]

### <a name="set-the-maximum-size-for-a-file-share"></a>Dosya paylaşımı için boyut üst sınırını ayarlama

Aşağıdaki örnekte, paylaşımdaki mevcut kullanımını nasıl kontrol edileceği veya paylaşım için nasıl kota ayarlanacağı gösterilmiştir. `FetchAttributes`bir share'in 'ini `Properties`doldurmak `SetProperties` ve Azure Dosyası depolamasına yerel değişiklikleri yaymak için çağrılmalıdır.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L62-L72)]

### <a name="generate-a-shared-access-signature-for-a-file-or-file-share"></a>Dosya veya dosya paylaşımı için paylaşılan erişim imzası oluşturma

Dosya paylaşımı veya tek bir dosya için paylaşılan erişim imzası (SAS) oluşturabilirsiniz. Ayrıca, paylaşılan erişim imzalarını yönetmek için dosya paylaşımında bir paylaşılan erişim ilkesi oluşturabilirsiniz. Gizliliğinin tehlikeye girdiği durumlarda SAS’yi iptal etme aracı olarak kullanılabilmesi nedeniyle bir paylaşılan erişim ilkesi oluşturmanız önerilir.

Burada, bir paylaşım üzerinde paylaşılan bir erişim ilkesi oluşturursunuz ve ardından bu ilkeyi, paylaşımdaki bir dosyadaki bir SAS'ın kısıtlamalarını sağlamak için kullanırsınız.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L78-L94)]

Paylaşılan erişim imzaları oluşturma ve kullanma hakkında daha fazla bilgi edinmek için bkz. [Paylaşılan Erişim İmzaları (SAS) kullanma](https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-1) ve [Blob depolama ile SAS oluşturma ve kullanma](https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-2).

### <a name="copy-files"></a>Dosyaları kopyalama

Bir dosyayı başka bir dosyaya veya blob'a veya bir dosyaya kopyalayabilirsiniz. Bir blob'u bir dosyaya veya bir dosyayı blob'a kopyalıyorsanız, aynı depolama hesabı içinde kopyalıyor olsanız bile kaynak nesneyi doğrulamak için paylaşılan bir erişim imzası (SAS) kullanmanız *gerekir.*

### <a name="copy-a-file-to-another-file"></a>Dosyayı başka bir dosyaya kopyalama

Burada, bir dosyayı aynı paylaşımdaki başka bir dosyaya kopyalarsınız. Bu kopyalama işlemi aynı depolama hesabındaki dosyaları kopyaladığı için, kopyalama işlemini gerçekleştirmek üzere Paylaşılan Anahtar kimlik doğrulaması kullanabilirsiniz. 

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L100-L101)]

### <a name="copy-a-file-to-a-blob"></a>Dosyayı bir bloba kopyalama

Burada, bir dosya oluşturur ve aynı depolama hesabı içindeki bir blob'a kopyalarsınız. Kaynak dosya için, hizmetin kopyalama işlemi sırasında kaynak dosyaya erişimi doğrulamak için kullandığı bir SAS oluşturursunuz.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L107-L120)]

Aynı şekilde, bir blobu bir dosyaya kopyalayabilirsiniz. Kaynak dosya bir blob ise, kopyalama sırasında bu bloba erişimin kimlik doğrulamasını yapması için bir SAS oluşturun.

## <a name="troubleshooting-file-storage-using-metrics"></a>Ölçümleri kullanarak File Storage sorunlarını giderme

Azure Depolama Analizi, Dosya depolama ölçümleri için ölçümleri destekler. Ölçüm verilerini kullanarak istekleri ve tanılama sorunlarını izleyebilirsiniz.

[Azure portalından](https://portal.azure.com)Dosya depolama ölçümleri etkinleştirebilir veya F# 'dan şu şekilde yapabilirsiniz:

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L126-L140)]

## <a name="next-steps"></a>Sonraki adımlar

Azure Dosya depolama alanı hakkında daha fazla bilgi için bu bağlantılara bakın.

### <a name="conceptual-articles-and-videos"></a>Kavramsal makaleler ve videolar

- [Azure File Storage: Windows ve Linux için uyumlu bulut SMB dosya sistemi](https://azure.microsoft.com/resources/videos/azurecon-2015-azure-files-storage-a-frictionless-cloud-smb-file-system-for-windows-and-linux/)
- [Linux ile Azure Dosya Depolama nasıl kullanılır?](https://docs.microsoft.com/azure/storage/storage-how-to-use-files-linux)

### <a name="tooling-support-for-file-storage"></a>File Storage için araç desteği

- [Azure Storage ile Azure PowerShell’i kullanma](https://docs.microsoft.com/azure/storage/storage-powershell-guide-full)
- [Microsoft Azure Depolama ile AzCopy kullanma](https://docs.microsoft.com/azure/storage/storage-use-azcopy)
- [Azure CLI ile blob oluşturma, indirme ve listele](https://docs.microsoft.com/azure/storage/blobs/storage-quickstart-blobs-cli#create-and-manage-file-shares)

### <a name="reference"></a>Başvuru

- [.NET başvurusu için Depolama İstemci Kitaplığı](https://msdn.microsoft.com/library/azure/mt347887.aspx)
- [Dosya Hizmeti REST API başvurusu](/rest/api/storageservices/fileservices/File-Service-REST-API)

### <a name="blog-posts"></a>Blog yazıları

- [Azure Dosya Depolama genel kullanıma sunulmuştur](https://azure.microsoft.com/blog/azure-file-storage-now-generally-available/)
- [Azure Dosya Depolama İçinde](https://azure.microsoft.com/blog/inside-azure-file-storage/)
- [Microsoft Azure Dosya Hizmeti’ne Giriş](https://docs.microsoft.com/archive/blogs/windowsazurestorage/introducing-microsoft-azure-file-service)
- [Microsoft Azure Dosyaları ile kalıcı bağlantılar](https://docs.microsoft.com/archive/blogs/windowsazurestorage/persisting-connections-to-microsoft-azure-files)
