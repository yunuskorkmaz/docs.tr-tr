---
title: F# kullanarak Azure Blob depolama kullanmaya başlama
description: Azure Blob depolama ile yapılandırılmamış verileri bulutta depolayın.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 0dda2e04f0052823e9ea35051855d677cd19ea92
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90548481"
---
# <a name="get-started-with-azure-blob-storage-using-f"></a>F kullanarak Azure Blob depolama ile çalışmaya başlama\#

Azure Blob Storage, bulutta nesne/blob olarak yapılandırılmamış veri depolayan bir hizmettir. Blob Storage belge, medya dosyası veya uygulama yükleyici gibi her tür metin veya ikili veri depolayabilir. Blob Storage aynı zamanda nesne depolama olarak adlandırılır.

Bu makalede, blob depolamayı kullanarak genel görevlerin nasıl gerçekleştirileceği gösterilir. Örnekler, .NET için Azure Storage Istemci kitaplığı kullanılarak F # kullanılarak yazılır. Kapsanan görevler, Blobları karşıya yükleme, listeleme, indirme ve silme işlemleri içerir.

Blob depolamaya kavramsal bir genel bakış için bkz. [BLOB depolama için .net Kılavuzu](/azure/storage/blobs/storage-quickstart-blobs-dotnet).

## <a name="prerequisites"></a>Önkoşullar

Bu kılavuzu kullanmak için önce [bir Azure depolama hesabı oluşturmanız](/azure/storage/common/storage-account-create)gerekir. Bu hesap için depolama erişim anahtarınıza de ihtiyacınız vardır.

## <a name="create-an-f-script-and-start-f-interactive"></a>F # betiği oluşturun ve F# Etkileşimli başlatın

Bu makaledeki örnekler bir F # uygulamasında veya F # betiğinde kullanılabilir. F # betiği oluşturmak için, `.fsx` Örneğin `blobs.fsx` f # geliştirme ortamınızda uzantılı bir dosya oluşturun.

Ardından, [NuGet](https://www.nuget.org/) [Paket](https://fsprojects.github.io/Paket/) [package manager](package-management.md) `WindowsAzure.Storage` `Microsoft.WindowsAzure.ConfigurationManager` `WindowsAzure.Storage.dll` `Microsoft.WindowsAzure.Configuration.dll` bir yönergesi kullanarak ve paketlerini ve başvurusunu `#r` yüklemek için paket veya NuGet gibi bir paket Yöneticisi kullanın.

### <a name="add-namespace-declarations"></a>Ad alanı bildirimleri ekleme

Aşağıdaki `open` bildirimlerini `blobs.fsx` dosyasının üstüne ekleyin:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a>Bağlantı dizenizi alma

Bu öğretici için bir Azure depolama bağlantı dizesine ihtiyacınız vardır. Bağlantı dizeleri hakkında daha fazla bilgi için bkz. [depolama bağlantı dizelerini yapılandırma](/azure/storage/storage-configure-connection-string).

Öğreticide, Bağlantı dizenizi aşağıdaki gibi bir betiğe girersiniz:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L11-L11)]

Ancak, bu gerçek projeler için **önerilmez** . Depolama hesabı anahtarınız depolama hesabınızın kök parolasına benzer. Depolama hesabı anahtarınızı korumak için her zaman özen gösterin. Diğer kullanıcılara dağıtmaktan, sabit kodlamaktan ve başkalarının erişebileceği düz metin dosyasına kaydetmekten kaçının. Güvenliğinin tehlikede olduğunu düşünüyorsanız, Azure portalını kullanarak anahtarınızı yeniden oluşturabilirsiniz.

Gerçek uygulamalar için, depolama Bağlantı dizenizi korumak için en iyi yol bir yapılandırma dosyasıdır. Bağlantı dizesini bir yapılandırma dosyasından getirmek için şunu yapabilirsiniz:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L13-L15)]

Azure Yapılandırma Yöneticisi'ni kullanmak isteğe bağlıdır. .NET Framework türü gibi bir API de kullanabilirsiniz `ConfigurationManager` .

### <a name="parse-the-connection-string"></a>Bağlantı dizesini ayrıştırma

Bağlantı dizesini ayrıştırmak için şunu kullanın:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L21-L22)]

Bu, bir döndürür `CloudStorageAccount` .

### <a name="create-some-local-dummy-data"></a>Bazı yerel kukla veriler oluşturma

Başlamadan önce, betiğimizin dizininde bazı sözde yerel veriler oluşturun. Daha sonra bu verileri karşıya yüklersiniz.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L28-L30)]

### <a name="create-the-blob-service-client"></a>Blob hizmeti istemcisi oluşturma

`CloudBlobClient`Tür, blob depolamada depolanan kapsayıcıları ve Blobları almanızı sağlar. Hizmet istemcisini oluşturma yöntemlerinden biri aşağıda verilmiştir:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L36-L36)]

Artık Blob Storage’da n veri okuyan ve bu depolamaya veri yazan kodu yazmaya hazırsınız.

## <a name="create-a-container"></a>Bir kapsayıcı oluşturma

Bu örnek, zaten yoksa, nasıl bir kapsayıcı oluşturulacağını gösterir:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L42-L46)]

Varsayılan olarak yeni kapsayıcı özeldir, bu kapsayıcıdan blob indirmek için depolama erişim anahtarınızı belirlemeniz gerektiği anlamına gelir. Kapsayıcı içindeki dosyaların herkese açık olmasını istiyorsanız, aşağıdaki kodu kullanarak kapsayıcıyı herkesin erişimine açık hale getirebilirsiniz:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L48-L49)]

İnternet üzerindeki herkes, herkese açık bir kapsayıcıdaki blobları görebilir ancak uygun hesap erişim tuşu veya paylaşılan erişim imzanız olması durumunda bunları değiştirebilir veya silebilirsiniz.

## <a name="upload-a-blob-into-a-container"></a>Bir kapsayıcıya bir blob yükleme

Azure Blob Storage blok blobları ve sayfa bloblarını destekler. Çoğu durumda, Blok Blobu kullanılacak önerilen türdür.

Bir dosyayı bir blok blobuna yüklemek için bir kapsayıcı başvurusu alın ve blok blob başvurusu almak için kullanın. Blob başvurunuz olduktan sonra, yöntemini çağırarak herhangi bir veri akışını bu akışa yükleyebilirsiniz `UploadFromFile` . Bu işlem, daha önce yoksa blobu oluşturur veya varsa üzerine yazar.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L55-L59)]

## <a name="list-the-blobs-in-a-container"></a>Kapsayıcıdaki blobları listeleme

Blob’ları bir kapsayıcıda listelemek için ilk olarak bir kapsayıcı başvurusu edinin. Daha sonra kapsayıcı `ListBlobs` ve/veya dizinlerini almak için kapsayıcının yöntemini kullanabilirsiniz. Döndürülen zengin özellik kümesine ve yöntemlere erişmek için, `IListBlobItem` bir `CloudBlockBlob` , `CloudPageBlob` veya `CloudBlobDirectory` nesnesine atamalısınız. Tür bilinmiyorsa, hangisine yayınlayacağınızı belirlemek için bir tür denetimi kullanabilirsiniz. Aşağıdaki kod, `mydata` kapsayıcıdaki her nesnenin URI’nın nasıl alınacağını ve çıkacağını gösterir:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L67-L80)]

Bloblarını adlarına yol bilgileriyle de girebilirsiniz. Bu, geleneksel bir dosya sisteminde olduğu gibi düzenleme ve geçiş yapabileceğiniz sanal bir dizin yapısı oluşturur. Dizin yapısının yalnızca sanal olduğunu unutmayın; Blob Storage’da  kullanılabilecek kaynaklar kapsayıcılar ve bloblardır. Ancak, depolama istemci kitaplığı bir `CloudBlobDirectory` sanal dizine başvuracak bir nesne sunar ve bu şekilde düzenlenmiş bloblarla çalışma sürecini basitleştirir.

Örneğin bir kapsayıcıda yer alan ve `photos` olarak adlandırılan aşağıdaki blok blobları kümesine göz atın:

*photo1.jpg*\
*2015/mimari/description.txt*\
*2015/mimari/photo3.jpg*\
*2015/mimari/photo4.jpg*\
*2016/mimari/photo5.jpg*\
*2016/mimari/photo6.jpg*\
*2016/mimari/description.txt*\
*2016/photo7.jpg*\

`ListBlobs`Bir kapsayıcıda (Yukarıdaki örnekte olduğu gibi) çağırdığınızda, hiyerarşik bir liste döndürülür. Hem hem de nesneler içeriyorsa, `CloudBlobDirectory` `CloudBlockBlob` kapsayıcıda dizin ve Blobları temsil eder, sonuçta elde edilen çıktı şuna benzer:

```console
Directory: https://<accountname>.blob.core.windows.net/photos/2015/
Directory: https://<accountname>.blob.core.windows.net/photos/2016/
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

İsteğe bağlı olarak, `UseFlatBlobListing` `ListBlobs` yönteminin parametresini olarak ayarlayabilirsiniz `true` . Bu durumda, kapsayıcıdaki her blob bir nesne olarak döndürülür `CloudBlockBlob` . `ListBlobs`Düz bir liste döndürmek için çağrısı şöyle görünür:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L82-L89)]

kapsayıcının geçerli içeriğine bağlı olarak, sonuçlar şöyle görünür:

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

## <a name="download-blobs"></a>Blob’ları indirme

Blob 'ları indirmek için önce bir blob başvurusu alın ve sonra yöntemi çağırın `DownloadToStream` . Aşağıdaki örnek, `DownloadToStream` BLOB içeriğini bir Stream nesnesine aktarmak için, daha sonra yerel bir dosyada kalıcı hale getirebilmeniz için yöntemini kullanır.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L95-L101)]

`DownloadToStream`Bir Blobun içeriğini bir metin dizesi olarak indirmek için yöntemini de kullanabilirsiniz.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L103-L106)]

## <a name="delete-blobs"></a>Blob’ları silme

Bir blobu silmek için önce bir blob başvurusu alın ve ardından `Delete` üzerinde yöntemi çağırın.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L112-L116)]

## <a name="list-blobs-in-pages-asynchronously"></a>Blob’ları sayfalarda zaman uyumsuz olarak listeleme

Çok sayıda blob listeliyorsanız veya bir listeleme işlemi ile dönen sonuç sayısını denetlemek isterseniz sonuç sayfalarında blobları listeleyebilirsiniz. Bu örnek, geniş bir sonuç kümesinin dönmesini beklerken çalıştırmanın engellenmemesi için sayfalardaki sonuçların zaman uyumsuz olarak nasıl döneceğini gösterir.

Bu örnek, düz bir blob listesini gösterir, ancak `useFlatBlobListing` yönteminin parametresini olarak ayarlayarak hiyerarşik bir liste da gerçekleştirebilirsiniz `ListBlobsSegmentedAsync` `false` .

Örnek, blok kullanarak bir zaman uyumsuz yöntemi tanımlar `async` . ``let!``Anahtar sözcüğü, listeleme görevi tamamlanana kadar örnek yöntemi yürütmeyi askıya alır.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L122-L160)]

Artık bu zaman uyumsuz yordamı aşağıdaki gibi kullanabiliriz. İlk olarak bazı kukla verileri karşıya yüklersiniz (Bu öğreticide daha önce oluşturulan yerel dosyayı kullanarak).

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L162-L166)]

Şimdi, yordamını çağırın. `Async.RunSynchronously`Zaman uyumsuz işlemin yürütülmesini zorlamak için kullanırsınız.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L168-L168)]

## <a name="writing-to-an-append-blob"></a>Ek blobu yazma

Ek blob, günlük tutma gibi ekleme işlemleri için en iyi duruma getirilmiştir. Blok blobuna benzer şekilde bir ek blobu bloklardan oluşur ancak bir ek bloba yeni bir blok eklediğinizde her zaman blobun sonuna eklenir. Bir ek blobdaki mevcut bloğu güncelleştiremezsiniz veya silemezsiniz. Bir blok blobu olduğu için ek blobun blok kimliği gösterilmez.

Her biri en fazla 4 MB olmak üzere bir ek blobundaki her blok farklı boyutlarda olabilir ve bir ek blobu en fazla 50.000 blok içerebilir. Bu nedenle bir ek blobunun en büyük boyutu 195 GB’den biraz fazladır (4 MB x 50.000 blok).

Aşağıdaki örnek, yeni bir ekleme blobu oluşturur ve basit bir günlüğe kaydetme işleminin benzetimini yapar ve buna veri ekler.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L174-L203)]

Üç blob türü arasındaki farklar hakkında bilgi edinmek için bkz. [Blok Blobları, Sayfa Blobları ve Ek Bloblarını anlama](/rest/api/storageservices/Understanding-Block-Blobs--Append-Blobs--and-Page-Blobs).

## <a name="concurrent-access"></a>Eşzamanlı erişim

Birden fazla istemciden veya birden çok işlem örneğiyle bir Blobun eşzamanlı erişimini desteklemek için **ETags** veya **kiralamalar**kullanabilirsiniz.

- **ETag** -Blobun veya kapsayıcının başka bir işlem tarafından değiştirildiğini algılamaya yönelik bir yol sağlar

- **Kira** -bir zaman dilimi için bir Blobun özel, yenilenebilir, yazma veya silme erişimi elde etmek için bir yol sağlar

Daha fazla bilgi için bkz. [Microsoft Azure depolama eşzamanlılık yönetimi](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).

## <a name="naming-containers"></a>Kapsayıcıları adlandırma

Azure Storage’daki her blob bir kapsayıcıda yer almalıdır. Kapsayıcı, blob adının bir bölümünü oluşturur. Örneğin, bu örnek blob URI’lerinde `mydata` kapsayıcının adıdır:

- `https://storagesample.blob.core.windows.net/mydata/blob1.txt`
- `https://storagesample.blob.core.windows.net/mydata/photos/myphoto.jpg`

Kapsayıcı adı, aşağıdaki adlandırma kurallarına uygun geçerli bir DNS adı olmalıdır:

1. Kapsayıcı adları bir harf veya rakamla başlamalıdır; yalnızca harf, rakam ve tire (-) karakterinden oluşabilir.
1. Her tire (-) karakterinin hemen önünde ve arkasında bir harf veya rakam bulunmalıdır; kapsayıcı adlarında art arda tirelere izin verilmez.
1. Kapsayıcı adındaki tüm harfler küçük harf olmalıdır.
1. Kapsayıcı adları 3-63 karakter arası uzunlukta olmalıdır.

Kapsayıcı adının her zaman küçük harfli olması gerektiğini unutmayın. Kapsayıcı adına bir büyük harf katarsanız ya da başka bir deyişle kapsayıcı adlandırma kurallarını ihlal ederseniz 400 hatası alabilirsiniz (Hatalı İstek).

## <a name="managing-security-for-blobs"></a>Blobların güvenliğini sağlama

Varsayılan olarak Azure Storage, erişimi hesap erişim anahtarlarına sahip olan hesap sahibiyle sınırlandırarak verilerinizi güvende tutar. Depolama hesabınızda blob verileri paylaşmanız gerektiğinde bunu hesap erişim anahtarlarınızın güvenliğini tehlikeye atmadan yapmak önem taşır. Buna ek olarak kablo ve Azure Storage üzerinden güvenle geçmesini sağlamak için blob verilerini şifreleyebilirsiniz.

### <a name="controlling-access-to-blob-data"></a>Blob verilerine erişimi denetleme

Varsayılan olarak depolama hesabındaki blob verileri yalnızca depolama hesabı sahibi tarafından erişilebilir. Blob Depolamaya yönelik kimlik doğrulama istekleri, istek varsayılan olarak hesap erişim anahtarı gerektirir. Ancak, bazı blob verilerini diğer kullanıcılar için kullanılabilir hale getirmek isteyebilirsiniz.

### <a name="encrypting-blob-data"></a>Blob verilerini şifreleme

Azure depolama, blob verilerini hem istemcide hem de sunucuda şifrelemeyi destekler.

## <a name="next-steps"></a>Sonraki adımlar

Blob Storage’ın temellerini öğrendiğinize göre, daha fazla bilgi edinmek için bu bağlantıları izleyin.

### <a name="tools"></a>Araçlar

- [F # Azurestooygettypeınfo sağlayıcı](https://fsprojects.github.io/AzureStorageTypeProvider/)\
Blob, tablo ve kuyruk Azure depolama varlıklarını araştırmak ve bunlara kolayca CRUD işlemleri uygulamak için kullanılabilen bir F # tür sağlayıcısı.

- [FSharp. Azure. Storage](https://github.com/fsprojects/FSharp.Azure.Storage)\
Microsoft Azure Table Storage hizmetini kullanmak için bir F # API 'SI

- [Microsoft Azure Depolama Gezgini (Mao)](/azure/vs-azure-tools-storage-manage-with-storage-explorer)\
Microsoft 'un Windows, OS X ve Linux üzerinde Azure Depolama verileriyle görsel olarak çalışmanızı sağlayan ücretsiz ve tek başına bir uygulama.

### <a name="blob-storage-reference"></a>Blob Storage başvurusu

- [.NET için Azure Depolama API'leri](/dotnet/api/overview/azure/storage)
- [Azure Depolama Hizmeti REST API Başvurusu](/rest/api/storageservices/)

### <a name="related-guides"></a>İlgili kılavuzlar

- [.NET için Azure Blob depolama örnekleri](/samples/azure-samples/storage-blob-dotnet-getting-started/storage-blob-dotnet-getting-started/)
- [AzCopy’yi kullanmaya başlama](/azure/storage/common/storage-use-azcopy-v10)
- [Azure depolama bağlantı dizelerini yapılandırma](/azure/storage/common/storage-configure-connection-string)
- [Azure Depolama Ekibi Blogu](/archive/blogs/windowsazurestorage/)
- [Hızlı Başlangıç: Nesne depolamada blob oluşturmak için .NET kullanma](/azure/storage/blobs/storage-quickstart-blobs-dotnet)
