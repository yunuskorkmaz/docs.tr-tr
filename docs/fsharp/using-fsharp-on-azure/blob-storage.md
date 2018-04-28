---
title: "F # kullanarak Azure Blob storage'ı kullanmaya başlama"
description: Azure Blob storage ile bulutta yapılandırılmamış veri depolayın.
author: sylvanc
ms.author: phcart
ms.date: 09/20/2016
ms.topic: conceptual
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 0414f0ca4aa2c2b75e80b3fd6531be74924fb60f
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="get-started-with-azure-blob-storage-using-f"></a>F # kullanarak Azure Blob storage'ı kullanmaya başlama #

Azure Blob storage bulutta nesne/BLOB olarak yapılandırılmamış veri depolayan bir hizmettir. BLOB Depolama metin veya ikili veriler, belge, ortam dosyası veya uygulama Yükleyici gibi herhangi bir türde depolayabilirsiniz. BLOB storage ayrıca nesne depolama olarak adlandırılır.

Bu makalede, Blob storage kullanarak ortak görevlerin nasıl gerçekleştirileceği gösterilmektedir. Örnekler, F # .NET için Azure Storage istemci kitaplığı kullanılarak kullanılarak yazılır. Karşıya yükleme listesinde, indirin ve BLOB'ları silme nasıl ele görevleri içerir.

Blob depolama kavramsal bir genel bakış için bkz: [blob storage için .NET Kılavuzu](/azure/storage/storage-dotnet-how-to-use-blobs).

## <a name="prerequisites"></a>Önkoşullar

Bu kılavuzu kullanmak için öncelikle [bir Azure depolama hesabı oluşturma](/azure/storage/storage-create-storage-account). Ayrıca bu hesap için depolama erişim anahtarınızı gerekir.

## <a name="create-an-f-script-and-start-f-interactive"></a>Bir F # betiği ve başlangıç F # Etkileşimli oluşturma

Bu makaledeki örnekler, F # uygulaması veya F # betiği kullanılabilir. F # betiği oluşturmak için dosya oluştur `.fsx` uzantısı, örneğin `blobs.fsx`, ortamınızdaki F # geliştirme.

Ardından, kullanın bir [Paket Yöneticisi](package-management.md) gibi [Paket](https://fsprojects.github.io/Paket/) veya [NuGet](https://www.nuget.org/) yüklemek için `WindowsAzure.Storage` ve `Microsoft.WindowsAzure.ConfigurationManager` paketler ve başvuru `WindowsAzure.Storage.dll` ve `Microsoft.WindowsAzure.Configuration.dll` komut dosyası kullanarak bir `#r` yönergesi.

### <a name="add-namespace-declarations"></a>Ad alanı bildirimleri ekleme

Aşağıdakileri ekleyin `open` deyimleri üstüne `blobs.fsx` dosyası:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a>Bağlantı dizenizi Al

Bu öğretici için bir Azure depolama bağlantı dizesi gerekiyor. Bağlantı dizeleri hakkında daha fazla bilgi için bkz: [Storage bağlantı dizelerini yapılandırma](/azure/storage/storage-configure-connection-string).

Öğretici için bağlantı dizenizi şuna benzer betiğinizin girin:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L11-L11)]

Ancak, bu olduğu **önerilmez** için gerçek projeleri. Depolama hesabı anahtarınız depolama hesabınızın kök parolasına benzer. Her zaman depolama hesabı anahtarınızı korumak dikkatli olun. Sabit kodlama veya başkalarının erişebileceği düz metin dosyasına kaydetme diğer kullanıcılara dağıtmaktan kaçının. Bunu tehlikede olduğunu düşünüyorsanız, Azure Portalı'nı kullanarak anahtarınızı yeniden oluşturabilirsiniz.

İçin gerçek uygulamalar, depolama bağlantı dizenizi korumak için en iyi yapılandırma dosyasında yoludur. Yapılandırma dosyasından bağlantı dizesini almak için bunu yapabilirsiniz:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L13-L15)]

Azure Yapılandırma Yöneticisi'ni kullanarak isteğe bağlıdır. .NET Framework'ün gibi bir API de kullanabilirsiniz `ConfigurationManager` türü.

### <a name="parse-the-connection-string"></a>Bağlantı dizesini ayrıştırma

Bağlantı dizesini ayrıştırmak için kullanın:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L21-L22)]

Bu döndürür bir `CloudStorageAccount`.

### <a name="create-some-local-dummy-data"></a>Bazı yerel sahte veriler oluşturun

Başlamadan önce bazı kukla yerel veri bizim betik dizininde oluşturun. Daha sonra bu verileri karşıya yükleyin.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L28-L30)]

### <a name="create-the-blob-service-client"></a>Blob hizmeti istemcisi oluşturma

`CloudBlobClient` Türü kapsayıcılar ve bloblar Blob storage'da depolanan almanıza olanak sağlar. Hizmet istemcisini oluşturma yöntemlerinden biri aşağıda verilmiştir:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L36-L36)]

Şimdi veri okuyan ve Blob depolamaya veri yazan kodu yazmaya hazırsınız.

## <a name="create-a-container"></a>Bir kapsayıcı oluşturma

Bu örnek, zaten yoksa, bir kapsayıcı oluşturulacağını gösterir:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L42-L46)]

Varsayılan olarak, yeni kapsayıcı Bu kapsayıcıdan BLOB indirmek için depolama erişim tuşunuzı belirlemeniz gerektiği anlamına gelir. Kapsayıcı içindeki dosyaların herkese kullanılabilmesini istiyorsanız, aşağıdaki kodu kullanarak genel kapsayıcıya ayarlayabilirsiniz:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L48-L49)]

Internet üzerinden herkes ortak bir kapsayıcıdaki blobları görebilir ancak değiştirmek veya yalnızca uygun hesap erişim tuşu veya paylaşılan erişim imzası varsa silin.

## <a name="upload-a-blob-into-a-container"></a>Bir kapsayıcıya bir blob karşıya yükleme

Azure Blob Storage blok blobları ve sayfa bloblarını destekler. Çoğu durumda, bir blok blobu kullanmak için önerilen türüdür.

Bir dosyayı bir blok blobuna yüklemek için bir kapsayıcı başvurusu alın ve blok blob başvurusu almak için kullanın. Bir blob başvurusu edindiğinizde veri kendisine çağırarak yükleyebilirsiniz `UploadFromFile` yöntemi. Bu işlem, daha önce mevcut alamadık veya mevcut değilse üzerine blob oluşturur.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L55-L59)]

## <a name="list-the-blobs-in-a-container"></a>BLOB'ları bir kapsayıcıda listelemek

BLOB'ları bir kapsayıcıda listelemek için önce bir kapsayıcı başvurusu edinin. Kapsayıcının sonra kullanabileceğiniz `ListBlobs` blobları ve/veya dizinleri içindeki alma yöntemi. Zengin özellik ve yöntem erişmek için `IListBlobItem`, kendisine atamalısınız bir `CloudBlockBlob`, `CloudPageBlob`, veya `CloudBlobDirectory` nesnesi. Tür bilinmiyorsa, hangisine yayınlayacağınızı belirlemek için bir tür denetimi kullanabilirsiniz. Aşağıdaki kodda almak ve her öğe URI'sini çıkış gösterilmiştir `mydata` kapsayıcı:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L67-L80)]

Ayrıca, ad blobları adlarında yol bilgileriyle de erişebilirsiniz. Bu, düzenlemek ve geleneksel bir dosya sisteminde olduğu gibi çapraz bir sanal dizin yapısı oluşturur. Dizin yapısı yalnızca sanal - yalnızca Blob depolama alanına kullanılabilir kapsayıcılar ve bloblar kaynaklardır unutmayın. Ancak, depolama istemci kitaplığı sunan bir `CloudBlobDirectory` bir sanal dizine ait ve bu şekilde düzenlenen BLOB'ları ile çalışma sürecini basitleştirmek için nesne.

Örneğin, aşağıdaki blok blobları adlı bir kapsayıcı kümesini göz önünde bulundurun `photos`:

*photo1.jpg*
*2015/architecture/description.txt*
*2015/architecture/photo3.jpg*
*2015 / Mimari/photo4.jpg*
*2016/architecture/photo5.jpg*
*2016/architecture/photo6.jpg* 
 *2016/architecture/description.txt*
*2016/photo7.jpg*

Çağırdığınızda `ListBlobs` (yukarıdaki örnekte) olduğu bir kapsayıcıda, hiyerarşik bir listeleme döner. Her ikisi de içeriyorsa, `CloudBlobDirectory` ve `CloudBlockBlob` sonuçta çıktı şuna benzer sonra dizinleri ve blobları kapsayıcıda sırasıyla temsil eden nesneler:

```console
Directory: https://<accountname>.blob.core.windows.net/photos/2015/
Directory: https://<accountname>.blob.core.windows.net/photos/2016/
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

İsteğe bağlı olarak, ayarlayabileceğiniz `UseFlatBlobListing` parametresinin `ListBlobs` yöntemine `true`. Bu durumda kapsayıcıdaki her blob olarak döndürülür bir `CloudBlockBlob` nesnesi. Çağrı `ListBlobs` düz listeleme şu şekilde görünür döndürmek için:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L82-L89)]

Ayrıca, kapsayıcı geçerli içeriğini bağlı olarak, sonuçlar şöyle görünür:

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

## <a name="download-blobs"></a>BLOB'ları indirme

BLOB'ları indirmek için önce bir blob başvurusu alın ve ardından çağırın `DownloadToStream` yöntemi. Aşağıdaki örnek kullanır `DownloadToStream` blob içeriklerini sonra yerel bir dosyaya kalıcı bir akış nesnesine aktarmak için yöntem.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L95-L101)]

Aynı zamanda `DownloadToStream` yöntemi bir blob'u bir metin dizesi olarak içeriğini indirmek için.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L103-L106)]

## <a name="delete-blobs"></a>BLOB'ları silme

Bir blobu silmek için önce bir blob başvurusu alın ve ardından çağıran `Delete` yöntemini.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L112-L116)]

## <a name="list-blobs-in-pages-asynchronously"></a>BLOB'ları sayfalarda zaman uyumsuz olarak listeleme

Çok sayıda BLOB listeliyorsanız veya bir listeleme işlemi ile dönen sonuç sayısını denetlemek istiyorsanız, sonuç sayfalarında blobları listeleyebilirsiniz. Böylece yürütme büyük bir sonuç kümesi dönmesini beklerken engellenmeyen Bu örnek sonuç sayfalarında zaman uyumsuz olarak döndürmek gösterilmiştir.

Bu örnek düz bir blob listesi gösterir, ancak ayarlayarak hiyerarşik bir listeleme gerçekleştirebilirsiniz `useFlatBlobListing` parametresinin `ListBlobsSegmentedAsync` yöntemine `false`.

Örnek zaman uyumsuz bir yöntem tanımlar kullanarak bir `async` bloğu. ``let!`` Anahtar sözcük listeleme görevi tamamlanana kadar örnek yöntemin yürütme askıya alır.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L122-L160)]

Biz artık bu zaman uyumsuz yordam aşağıdaki gibi kullanabilirsiniz. İlk (Bu öğreticide daha önce oluşturulan yerel dosya kullanarak) bazı sahte veriler karşıya yükleyin.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L162-L166)]

Şimdi, yordamını çağırın. Kullandığınız ``Async.RunSynchronously`` zaman uyumsuz işlemin yürütülmesini zorlamak için.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L168-L168)]

## <a name="writing-to-an-append-blob"></a>Bir ek blobu yazma

Ek blob, günlük tutma gibi ekleme işlemleri için optimize edilmiştir. Bir blok blobu gibi bir ek blobu bloklardan oluşur ancak bir ek bloba yeni bir blok eklediğinizde her zaman blobun sonuna eklenir. Güncelleştirilemiyor veya blobdaki mevcut bloğu silinemiyor. Bir blok blobu olduğu gibi ek blobun blok kimliği gösterilmez.

Her bir ek blobu bloğunda en fazla 4 MB, farklı bir boyutta olabilir ve bir ek blobu en fazla 50.000 blok içerebilir. Bu nedenle bir ek blobu en büyük boyutu 195 GB'den biraz fazladır (4 MB X 50.000 blok) ' dir.

Aşağıdaki örnek yeni bir ek blob oluşturur ve bazı verileri, bir basit günlük yazma işlemini benzeterek ekler.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L174-L203)]

Bkz: [anlama blok Blobları, sayfa Blobları ve ek Bloblarını](https://msdn.microsoft.com/library/azure/ee691964.aspx) üç BLOB türü arasındaki farklar hakkında daha fazla bilgi için.

## <a name="concurrent-access"></a>Eş zamanlı erişim

Eş zamanlı erişim bir blob'a birden çok istemciden veya birden çok örneği desteklemek için kullanabileceğiniz **Etag'ler** veya **kiraları**.

* **ETag** -blob veya kapsayıcı başka bir işlem tarafından değiştirilmiş algılamak için bir yol sağlar

* **Kira** -elde özel ve yenilenebilir, yazma erişimi veya bir blob için bir süre silmek için bir yol sağlar

Daha fazla bilgi için bkz: [yönetme eşzamanlılık Microsoft Azure depolama alanında](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).

## <a name="naming-containers"></a>Kapsayıcı adlandırma

Azure depolama her blob bir kapsayıcıda yer almalıdır. Kapsayıcı, blob adı bölümü oluşturur. Örneğin, `mydata` Bu örnek blob Urı'lerinde kapsayıcısında adıdır:

    https://storagesample.blob.core.windows.net/mydata/blob1.txt
    https://storagesample.blob.core.windows.net/mydata/photos/myphoto.jpg

Bir kapsayıcı adı aşağıdaki adlandırma kurallarına uygun geçerli bir DNS adı olması gerekir:

1. Kapsayıcı adları bir harf veya sayı ile başlamalı ve yalnızca harf, rakam ve tire (-) karakterini içerebilir.
1. Her tire (-) karakterinden hemen önce ve bir harf veya sayı gelmelidir gerekir; kapsayıcı adlarında art arda tirelere izin verilmez.
1. Kapsayıcı adındaki tüm harfler küçük olmalıdır.
1. Kapsayıcı adları 3-63 karakter uzunluğunda olmalıdır.

Kapsayıcı adının her zaman küçük harfli olması gerektiğini unutmayın. Kapsayıcı adına bir büyük harf eklemek ya da aksi takdirde kapsayıcı adlandırma kurallarını ihlal 400 hatası (Hatalı istek) alabilirsiniz.

## <a name="managing-security-for-blobs"></a>Blobların güvenliğini sağlama

Varsayılan olarak, Azure depolama, verilerinizi hesabı erişim anahtarlarını elinde olan hesap sahibi erişimi kısıtlayarak güvende tutar. Depolama hesabınızda blob verileri paylaşmanız gerektiğinde bunu hesap erişim tuşlarınızı güvenliği tehlikeye atmadan yapmak önemlidir. Ayrıca, Azure storage'da ve kablo üzerinden giderek güvenli olduğundan emin olmak için blob verilerini şifreleyebilirsiniz.

### <a name="controlling-access-to-blob-data"></a>Blob verilerine erişimi denetleme

Varsayılan olarak, depolama hesabınızda blob verileri yalnızca depolama hesabı sahibi erişilebilir. Blob Storage'a karşı istek kimlik doğrulaması varsayılan olarak hesap erişim tuşu gerektirir. Ancak, çeşitli blob verilerinin diğer kullanıcılar tarafından kullanılabilmesini sağlamak isteyebilirsiniz.

Blob depolama erişimi denetleme hakkında daha fazla bilgi için bkz: [blob depolama bölümü için .NET Kılavuzu erişim denetimi hakkında](/azure/storage/storage-dotnet-how-to-use-blobs#controlling-access-to-blob-data).


### <a name="encrypting-blob-data"></a>BLOB verilerini şifreleme

Azure Storage hem istemci hem de sunucuda blob verisi şifreleme destekler.

Blob verilerini şifreleme hakkında daha fazla bilgi için bkz: [blob depolama bölümü şifrelemesi için .NET Kılavuzu](/azure/storage/storage-dotnet-how-to-use-blobs#encrypting-blob-data).

## <a name="next-steps"></a>Sonraki adımlar

Blob storage'nın öğrendiğinize göre daha fazla bilgi için aşağıdaki bağlantıları izleyin.

### <a name="tools"></a>Araçlar
- [F # AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/) bir F # tür Blob, tablo ve kuyruk Azure depolama varlıklar keşfetmek ve bunları CRUD işlemleri kolayca uygulamak için kullanılan sağlayıcısı.
- [FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage) bir F # Microsoft Azure Table Storage hizmeti kullandığınız için API
- [Microsoft Azure Depolama Gezgini (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer) görsel olarak Azure Storage ile Windows, OS X ve Linux üzerinde çalışmanıza olanak tanır Microsoft'tan ücretsiz, bir tek başına uygulamadır.

### <a name="blob-storage-reference"></a>BLOB Depolama başvurusu

- [.NET için Azure depolama API'leri](/dotnet/api/overview/azure/storage)
- [Azure Storage Hizmetleri REST API Başvurusu](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)

### <a name="related-guides"></a>İlgili kılavuzları

- [Azure Blob Depolama C# kullanmaya Başlarken](https://azure.microsoft.com/resources/samples/storage-blob-dotnet-getting-started/)
- [Windows üzerinde AzCopy komut satırı yardımcı programı ile veri aktarımı](/azure/storage/common/storage-use-azcopy)
- [Linux'ta AzCopy komut satırı yardımcı programı ile veri aktarımı](/azure/storage/common/storage-use-azcopy-linux)
- [Azure Storage bağlantı dizelerini yapılandırma](/azure/storage/common/storage-configure-connection-string)
- [Azure depolama ekibi blogu](https://blogs.msdn.microsoft.com/windowsazurestorage/)
