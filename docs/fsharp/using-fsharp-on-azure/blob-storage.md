---
title: F# kullanarak Azure Blob depolama kullanmaya başlama
description: Azure Blob Depolama ile bulutta yapılandırılmamış veri Store.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 3d020c2cd9a11db1cd4b7a60113e1be03655f763
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65880043"
---
# <a name="get-started-with-azure-blob-storage-using-f"></a>F kullanarak Azure Blob depolamayı kullanmaya başlama\#

Azure Blob Depolama, yapılandırılmamış verileri nesne/BLOB olarak bulutta depolayan bir hizmettir. BLOB Depolama, herhangi bir türde metin veya belge, medya dosyası veya uygulama Yükleyici gibi ikili veri depolayabilir. BLOB storage ayrıca nesne depolama olarak adlandırılır.

Bu makalede, Blob depolamayı kullanarak ortak görevleri nasıl gerçekleştireceğinizi gösterir. Örnekleri kullanılarak yazılan F# .NET için Azure depolama istemci kitaplığı kullanarak. Kapsanan görevleri yüklemek, listelemek, indirmek ve blobları silme işlemini içerir.

Blob depolama kavramsal bir genel bakış için bkz: [blob depolama için .NET Kılavuzu](/azure/storage/storage-dotnet-how-to-use-blobs).

## <a name="prerequisites"></a>Önkoşullar

Bu kılavuzu kullanmak için önce [bir Azure depolama hesabı oluşturma](/azure/storage/storage-create-storage-account). Ayrıca bu hesap için depolama erişim anahtarınızı gerekir.

## <a name="create-an-f-script-and-start-f-interactive"></a>Oluşturma bir F# betik ve başlangıç F# etkileşimli

Bu makaledeki örnekleri ya da kullanılabilir bir F# uygulama veya bir F# betiği. Oluşturmak için bir F# betik, bir dosya oluşturun `.fsx` uzantısı, örneğin `blobs.fsx`içinde F# geliştirme ortamı.

Ardından, bir [Paket Yöneticisi](package-management.md) gibi [Paket](https://fsprojects.github.io/Paket/) veya [NuGet](https://www.nuget.org/) yüklemek için `WindowsAzure.Storage` ve `Microsoft.WindowsAzure.ConfigurationManager` paketler ve başvuru `WindowsAzure.Storage.dll` ve `Microsoft.WindowsAzure.Configuration.dll` komut dosyası kullanarak bir `#r` yönergesi.

### <a name="add-namespace-declarations"></a>Ad alanı bildirimleri ekleme

Aşağıdaki `open` üst tarafına deyimlerini `blobs.fsx` dosyası:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a>Bağlantı dizenizi alma

Bu öğreticide bir Azure depolama bağlantı dizesi gerekir. Bağlantı dizeleri hakkında daha fazla bilgi için bkz. [depolama bağlantı dizelerini yapılandırma](/azure/storage/storage-configure-connection-string).

Öğretici için şunun gibi komut dosyanızdaki bağlantı dizenizi girin:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L11-L11)]

Ancak, bu, **önerilmez** gerçek projeleri. Depolama hesabı anahtarınız depolama hesabınızın kök parolasına benzer. Depolama hesabı anahtarınızı korumak için her zaman özen gösterin. Diğer kullanıcılara dağıtmaktan, sabit kodlamaktan ve başkalarının erişebileceği düz metin dosyasına kaydetmekten kaçının. Tehlikeye girmiş olabilecek düşünüyorsanız Azure portalını kullanarak anahtarınızı yeniden oluşturabilirsiniz.

Gerçek uygulamalar, depolama bağlantı dizenizi korumak için en iyi yolu, içinde bir yapılandırma dosyasıdır. Bir yapılandırma dosyasından bağlantı dizesini getirmek için bunu yapabilirsiniz:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L13-L15)]

Azure Yapılandırma Yöneticisi'ni kullanmak isteğe bağlıdır. .NET Framework'ün gibi bir API de kullanabilirsiniz `ConfigurationManager` türü.

### <a name="parse-the-connection-string"></a>Bağlantı dizesini ayrıştırma

Bağlantı dizesini ayrıştırmak için kullanın:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L21-L22)]

Bu döndürür bir `CloudStorageAccount`.

### <a name="create-some-local-dummy-data"></a>Yerel bazı örnek veri oluşturma

Başlamadan önce bazı işlevsiz bir yerel veri betiğimizi dizininde oluşturun. Daha sonra bu verileri karşıya yükleyin.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L28-L30)]

### <a name="create-the-blob-service-client"></a>Blob hizmeti istemcisi oluşturma

`CloudBlobClient` Türü kapsayıcıları ve Blob Depolama alanında depolanan blobları almanızı sağlar. Hizmet istemcisini oluşturma yöntemlerinden biri aşağıda verilmiştir:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L36-L36)]

Şimdi, okuyan ve Blob depolamaya veri yazan kodu yazmaya hazırsınız.

## <a name="create-a-container"></a>Bir kapsayıcı oluşturma

Bu örnek, zaten yoksa, bir kapsayıcı oluşturma işlemi gösterilmektedir:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L42-L46)]

Varsayılan olarak, yeni özel Bu kapsayıcıdan BLOB indirmek için depolama erişim anahtarınızı belirlemeniz gerektiği anlamına kapsayıcıdır. Kapsayıcı içindeki dosyaların herkese kullanılabilmesini istiyorsanız, kapsayıcı aşağıdaki kodu kullanarak genel olarak ayarlayabilirsiniz:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L48-L49)]

Internet'teki herkes ortak bir kapsayıcıdaki blobları görebilir ancak değiştirdiğinizde ya da yalnızca uygun hesap erişim anahtarı veya paylaşılan erişim imzası varsa bunları silin.

## <a name="upload-a-blob-into-a-container"></a>Bir kapsayıcıya bir blob yükleme

Azure Blob Depolama blok blobları ve sayfa bloblarını destekler. Çoğu durumda, bir blok blobu kullanmak için önerilen türdür.

Bir dosyayı bir blok blobuna yüklemek için bir kapsayıcı başvurusu alın ve blok blob başvurusu almak için kullanın. Bir blob başvurusunu aldıktan sonra herhangi bir veri akışı için çağırarak yükleyebilirsiniz `UploadFromFile` yöntemi. Bu işlem, daha önce mevcut fırsatınız veya mevcut değilse üzerine blob oluşturur.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L55-L59)]

## <a name="list-the-blobs-in-a-container"></a>Bir kapsayıcıdaki blobları Listele

Bir kapsayıcıdaki blobları listelemek için ilk olarak bir kapsayıcı başvurusu alın. Daha sonra kapsayıcının kullanabilirsiniz `ListBlobs` blobları ve/veya dizinleri içine almak için yöntemi. Zengin özellik ve yöntem dönen erişmeye `IListBlobItem`, kendisine dönüştürmelisiniz bir `CloudBlockBlob`, `CloudPageBlob`, veya `CloudBlobDirectory` nesne. Tür bilinmiyorsa, yayınlayacağınızı belirlemek için bir tür denetimi kullanabilirsiniz. Aşağıdaki kod, almak ve her nesnenin URI çıkış gösterilmiştir `mydata` kapsayıcı:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L67-L80)]

Adı blobları adlarında yol bilgileriyle de kullanabilirsiniz. Bu, geleneksel bir dosya sisteminde olduğu gibi çapraz geçiş düzenleyebilir ve bir sanal dizin yapısı oluşturur. Dizin yapısı yalnızca sanaldır - kaynak yalnızca Blob Depolama alanında kullanılabilir kapsayıcılar ve bloblar kullanılabilir unutmayın. Ancak, depolama istemcisi kitaplığı sunan bir `CloudBlobDirectory` sanal dizine ait ve bu şekilde düzenlenen bloblarla çalışma sürecini basitleştirmek için nesne.

Örneğin, aşağıdaki adlı bir kapsayıcı içinde blok blobları kümesine göz önünde bulundurun `photos`:

*photo1.jpg*\
*2015/Architecture/Description.txt*\
*2015/Architecture/photo3.jpg*\
*2015/Architecture/photo4.jpg*\
*2016/Architecture/photo5.jpg*\
*2016/Architecture/photo6.jpg*\
*2016/Architecture/Description.txt*\
*2016/photo7.jpg*\

Çağırdığınızda `ListBlobs` (Yukarıdaki örnek) olduğu gibi bir kapsayıcı, hiyerarşik bir listeleme döndürülür. Her ikisi de içeriyorsa `CloudBlobDirectory` ve `CloudBlockBlob` sonuçta çıktı şuna benzer sonra dizinleri ve blobları kapsayıcıda sırasıyla temsil eden nesneler:

```console
Directory: https://<accountname>.blob.core.windows.net/photos/2015/
Directory: https://<accountname>.blob.core.windows.net/photos/2016/
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

İsteğe bağlı olarak ayarlayabileceğiniz `UseFlatBlobListing` parametresinin `ListBlobs` yönteme `true`. Bu durumda kapsayıcıdaki her blob olarak döndürülen bir `CloudBlockBlob` nesne. Çağrı `ListBlobs` döndürülecek bir düz liste aşağıdaki gibi görünür:

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L82-L89)]

ve kapsayıcınızı geçerli içeriğini bağlı olarak, sonuçlar şöyle görünür:

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

## <a name="download-blobs"></a>Blobları indirin

Blobları indirmek için önce bir blob başvurusu alın ve sonra çağrı `DownloadToStream` yöntemi. Aşağıdaki örnekte `DownloadToStream` blob içeriklerini, ardından yerel bir dosyaya kalıcı bir akış nesnesine aktarmak için yöntemi.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L95-L101)]

Ayrıca `DownloadToStream` bir metin dizesi olarak bir blobun içeriklerini indirmek için yöntemi.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L103-L106)]

## <a name="delete-blobs"></a>Blobları Sil

Bir blobu silmek için önce bir blob başvurusu alın ve sonra çağrı `Delete` yöntemini.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L112-L116)]

## <a name="list-blobs-in-pages-asynchronously"></a>BLOB'ları sayfalarda zaman uyumsuz olarak listeleme

Çok sayıda BLOB listeliyorsanız veya bir listeleme işlemi ile dönen sonuç sayısını denetlemek isterseniz sonuç sayfalarında blobları listeleyebilirsiniz. Bu örnek, böylece geniş bir sonuç kümesinin dönmesini beklerken yürütme engellenip engellenmediğini sayfalarda zaman uyumsuz olarak sonuçları döndürmek nasıl gösterir.

Bu örnek düz bir blob listesi gösterir, ancak ayarlayarak hiyerarşik bir listeleme gerçekleştirebilirsiniz `useFlatBlobListing` parametresinin `ListBlobsSegmentedAsync` yönteme `false`.

Örnek zaman uyumsuz bir yöntem tanımlar kullanarak bir `async` blok. ``let!`` Anahtar sözcüğü listeleme görevi tamamlanana kadar örnek yöntemin yürütülmesini askıya alır.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L122-L160)]

Artık bu zaman uyumsuz bir yordam gibi kullanabiliriz. İlk (Bu öğreticide daha önce oluşturulan yerel dosya kullanarak) işlevsiz bazı veriler yükleyin.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L162-L166)]

Şimdi, rutinin çağırın. Kullandığınız `Async.RunSynchronously` zaman uyumsuz işlem yürütülmesini zorlamak için.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L168-L168)]

## <a name="writing-to-an-append-blob"></a>Bir ek blobu yazma

Bir ekleme blobu, günlüğe kaydetme gibi ekleme işlemleri için iyileştirilmiştir. Blok blobuna benzer bir ek blobu bloklardan oluşur ancak bir ek bloba yeni bir blok eklediğinizde her zaman blobun sonuna eklenir. Güncelleştiremezsiniz veya ek blobdaki mevcut bloğu silin. Bir blok blobu için olduğu gibi ek blobun blok kimliği gösterilmez.

Her bir ek blobu bloğunda en çok 4 MB, farklı boyutlarda olabilir ve bir ek blobu en fazla 50.000 blok içerebilir. Bu nedenle bir ek blobunun en büyük boyutu 195 GB'tan biraz daha fazladır (4 MB X 50.000 blok) ' dir.

Aşağıdaki örnek, yeni bir ek blob oluşturur ve bazı veriler, bir basit günlüğe kaydetme işlemini benzeterek buna.

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L174-L203)]

Bkz: [anlama blok Blobları, sayfa Blobları ve ekleme Blobları](https://msdn.microsoft.com/library/azure/ee691964.aspx) üç tür BLOB arasındaki farklar hakkında daha fazla bilgi için.

## <a name="concurrent-access"></a>Eş zamanlı erişim

Birden çok istemciden veya birden çok işlem örnekleri eş zamanlı erişim bir blob olarak desteklemek için kullanabileceğiniz **Etag'ler** veya **kiraları**.

* **ETag** -blob veya kapsayıcı başka bir işlem tarafından değiştirilmiş algılamak için bir yol sağlar

* **Kira** -özel ve yenilenebilir elde etmek, yazma veya silme bir süre için bir bloba erişimi için bir yol sağlar.

Daha fazla bilgi için [Microsoft Azure Depolama'da eşzamanlılığı yönetme](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).

## <a name="naming-containers"></a>Kapsayıcı adlandırma

Her blob Azure depolamadaki bir kapsayıcıda yer almalıdır. Kapsayıcı, blob adının bir kısmını oluşturur. Örneğin, `mydata` Bu örnek blob Urı'lerinde kapsayıcısında adıdır:

- https://storagesample.blob.core.windows.net/mydata/blob1.txt
- https://storagesample.blob.core.windows.net/mydata/photos/myphoto.jpg

Bir kapsayıcı adı, geçerli bir DNS adı, aşağıdaki adlandırma kurallarına uygun olmalıdır:

1. Kapsayıcı adları bir harf veya sayı ile başlamalıdır ve yalnızca harf, rakam ve tire (-) karakteri içermelidir.
1. Her tire (-) karakterinin hemen önünde ve bir harf veya rakam olmalıdır; kapsayıcı adlarında art arda tirelere izin verilmez.
1. Kapsayıcı adındaki tüm harfler küçük olmalıdır.
1. Kapsayıcı adları 3 ila 63 karakter uzunluğunda olmalıdır.

Kapsayıcı adının her zaman küçük harfli olması gerektiğini unutmayın. Kapsayıcı adına bir büyük harf içerir ya da aksi takdirde kapsayıcı adlandırma kurallarını ihlal (Hatalı istek) 400 hatası alabilirsiniz.

## <a name="managing-security-for-blobs"></a>Blobların güvenliğini sağlama

Varsayılan olarak, Azure depolama, veri erişimi hesap erişim anahtarlarını elinde olan bir hesap sahibi sınırlayarak güvende tutar. Depolama hesabınızda blob verileri paylaşmanız gerektiğinde bunu hesap erişim tuşlarınızı güvenliğini tehlikeye atmadan yapmak önemlidir. Ayrıca, aktarımda ve Azure Depolama'da güvenli olduğundan emin olmak için blob verilerini şifreleyebilirsiniz.

### <a name="controlling-access-to-blob-data"></a>Blob verilerine erişimi denetleme

Varsayılan olarak, depolama hesabınızdaki blob verileri yalnızca depolama hesabı sahibi erişilebilir. Blob depolamaya yönelik isteklerine kimlik doğrulaması varsayılan olarak hesap erişim anahtarı gerektirir. Ancak, belirli blob verilerinin diğer kullanıcılar tarafından kullanılabilmesini sağlamak isteyebilirsiniz.

### <a name="encrypting-blob-data"></a>BLOB verilerini şifreleme

Azure Storage hem istemci hem de sunucuda blob verilerin şifrelenmesini destekler.

## <a name="next-steps"></a>Sonraki adımlar

Blob storage'nın temellerini öğrendiğinize göre daha fazla bilgi için bu bağlantıları izleyin.

### <a name="tools"></a>Araçlar

- [F#AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/)\
Bir F# Blob, tablo ve kuyruk Azure depolama varlıkları keşfedin ve bunları CRUD işlemleri kolayca uygulamak için kullanılan bir tür sağlayıcısı.

- [FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage)\
Bir F# API, Microsoft Azure tablo depolama hizmetini kullanma

- [Microsoft Azure Depolama Gezgini (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer)\
Microsoft'un Windows, OS X ve Linux'ta Azure depolama verileriyle görsel olarak çalışmanızı sağlayan ücretsiz, tek başına uygulama.

### <a name="blob-storage-reference"></a>BLOB storage başvurusu

- [.NET için Azure depolama API'leri](/dotnet/api/overview/azure/storage)
- [Azure depolama hizmetleri REST API Başvurusu](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)

### <a name="related-guides"></a>İlgili kılavuzları

- [C# ' de Azure Blob Depolama kullanmaya başlama](https://azure.microsoft.com/resources/samples/storage-blob-dotnet-getting-started/)
- [Windows üzerinde AzCopy komut satırı yardımcı programı ile veri aktarma](/azure/storage/common/storage-use-azcopy)
- [Linux üzerinde AzCopy komut satırı yardımcı programı ile veri aktarma](/azure/storage/common/storage-use-azcopy-linux)
- [Azure Storage bağlantı dizelerini yapılandırma](/azure/storage/common/storage-configure-connection-string)
- [Azure depolama ekibi blogu](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [Hızlı Başlangıç: NET'i kullanarak nesne depolamada blob oluşturma](/azure/storage/blobs/storage-quickstart-blobs-dotnet)
