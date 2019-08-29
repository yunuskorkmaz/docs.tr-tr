---
title: F# kullanarak Azure Blob depolama kullanmaya başlama
description: Azure Blob depolama ile yapılandırılmamış verileri bulutta depolayın.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: c765f38cba7642e813a5966d3b7754c5ce45abbd
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70107117"
---
# <a name="get-started-with-azure-blob-storage-using-f"></a>F kullanarak Azure Blob depolama ile çalışmaya başlama\#

Azure Blob depolama, bulutta nesne/blob olarak yapılandırılmamış verileri depolayan bir hizmettir. BLOB depolama, bir belge, medya dosyası veya uygulama yükleyicisi gibi herhangi bir tür metin veya ikili veri saklayabilir. BLOB depolama alanı da nesne depolama olarak adlandırılır.

Bu makalede, blob depolamayı kullanarak genel görevlerin nasıl gerçekleştirileceği gösterilir. Örnekler, .NET için Azure F# Storage istemci kitaplığı kullanılarak yazılır. Kapsanan görevler, Blobları karşıya yükleme, listeleme, indirme ve silme işlemleri içerir.

Blob depolamaya kavramsal bir genel bakış için bkz. [BLOB depolama için .net Kılavuzu](/azure/storage/storage-dotnet-how-to-use-blobs).

## <a name="prerequisites"></a>Önkoşullar

Bu kılavuzu kullanmak için önce [bir Azure depolama hesabı oluşturmanız](/azure/storage/storage-create-storage-account)gerekir. Bu hesap için depolama erişim anahtarınıza de ihtiyacınız vardır.

## <a name="create-an-f-script-and-start-f-interactive"></a>F# Betik oluşturma ve etkileşimli başlatma F#

Bu makaledeki örnekler, bir F# uygulama ya da bir F# komut dosyasında kullanılabilir. Bir F# betik oluşturmak için, örneğin `.fsx` `blobs.fsx`, F# geliştirme ortamınızda uzantılı bir dosya oluşturun.

Ardından, [](https://fsprojects.github.io/Paket/) bir `WindowsAzure.Storage` `Microsoft.WindowsAzure.ConfigurationManager` `WindowsAzure.Storage.dll` [](https://www.nuget.org/) `Microsoft.WindowsAzure.Configuration.dll` [](package-management.md) yönergesikullanarakvepaketlerinivebaşvurusunuyüklemekiçinpaketveyaNuGet`#r` gibi bir paket Yöneticisi kullanın.

### <a name="add-namespace-declarations"></a>Ad alanı bildirimleri ekle

Aşağıdaki `open` deyimlerini `blobs.fsx` dosyanın en üstüne ekleyin:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a>Bağlantı dizenizi alın

Bu öğretici için bir Azure depolama bağlantı dizesine ihtiyacınız vardır. Bağlantı dizeleri hakkında daha fazla bilgi için bkz. [depolama bağlantı dizelerini yapılandırma](/azure/storage/storage-configure-connection-string).

Öğreticide, Bağlantı dizenizi aşağıdaki gibi bir betiğe girersiniz:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L11-L11)]

Ancak, bu gerçek projeler için **önerilmez** . Depolama hesabı anahtarınız, depolama hesabınızın kök parolasıyla benzerdir. Depolama hesabı anahtarınızı korumak için her zaman özen gösterin. Diğer kullanıcılara dağıtmaktan, sabit kodlamaktan ve başkalarının erişebileceği düz metin dosyasına kaydetmekten kaçının. Güvenliğinin tehlikede olduğunu düşünüyorsanız, Azure portalını kullanarak anahtarınızı yeniden oluşturabilirsiniz.

Gerçek uygulamalar için, depolama Bağlantı dizenizi korumak için en iyi yol bir yapılandırma dosyasıdır. Bağlantı dizesini bir yapılandırma dosyasından getirmek için şunu yapabilirsiniz:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L13-L15)]

Azure Configuration Manager kullanmak isteğe bağlıdır. .NET Framework `ConfigurationManager` türü gibi bir API de kullanabilirsiniz.

### <a name="parse-the-connection-string"></a>Bağlantı dizesini ayrıştırma

Bağlantı dizesini ayrıştırmak için şunu kullanın:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L21-L22)]

Bu, bir `CloudStorageAccount`döndürür.

### <a name="create-some-local-dummy-data"></a>Bazı yerel kukla veriler oluşturma

Başlamadan önce, betiğimizin dizininde bazı sözde yerel veriler oluşturun. Daha sonra bu verileri karşıya yüklersiniz.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L28-L30)]

### <a name="create-the-blob-service-client"></a>Blob hizmeti istemcisini oluşturma

Tür `CloudBlobClient` , blob depolamada depolanan kapsayıcıları ve Blobları almanızı sağlar. Hizmet istemcisini oluşturmak için bir yol aşağıda verilmiştir:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L36-L36)]

Artık BLOB depolama alanına veri okuyan ve veri yazan kodu yazmaya hazırsınız.

## <a name="create-a-container"></a>Kapsayıcı oluşturma

Bu örnek, zaten yoksa kapsayıcının nasıl oluşturulacağını gösterir:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L42-L46)]

Varsayılan olarak, yeni kapsayıcı özeldir ve bu kapsayıcıdan blob 'ları indirmek için depolama erişim anahtarınızı belirtmeniz gerekir. Kapsayıcıdaki dosyaları herkes için kullanılabilir hale getirmek istiyorsanız, kapsayıcıyı aşağıdaki kodu kullanarak genel olacak şekilde ayarlayabilirsiniz:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L48-L49)]

Internet 'teki herkes blob 'ları ortak bir kapsayıcıda görebilir, ancak yalnızca uygun hesap erişim anahtarı veya paylaşılan erişim imzanız varsa bunları değiştirebilir veya silebilirsiniz.

## <a name="upload-a-blob-into-a-container"></a>Bir blobu bir kapsayıcıya yükleme

Azure Blob depolama, blok bloblarını ve sayfa bloblarını destekler. Çoğu durumda, Blok Blobu kullanılacak önerilen türdür.

Bir blok blobuna bir dosya yüklemek için bir kapsayıcı başvurusu alın ve bunu bir Blok Blobu başvurusu almak için kullanın. Blob başvurunuz olduktan sonra, `UploadFromFile` yöntemini çağırarak herhangi bir veri akışını bu akışa yükleyebilirsiniz. Bu işlem, daha önce yoksa blobu oluşturur veya varsa üzerine yazar.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L55-L59)]

## <a name="list-the-blobs-in-a-container"></a>Bir kapsayıcıdaki Blobları listeleme

Bir kapsayıcıdaki Blobları listelemek için, önce bir kapsayıcı başvurusu alın. Daha sonra kapsayıcı ve/veya dizinlerini `ListBlobs` almak için kapsayıcının yöntemini kullanabilirsiniz. Döndürülen `IListBlobItem`zengin özellik kümesine ve yöntemlere erişmek için, bir `CloudBlockBlob`, `CloudPageBlob`veya `CloudBlobDirectory` nesnesine atamalısınız. Tür bilinmiyorsa, ne tür denetimi kullanacağınızı anlamak için bir tür denetimi kullanabilirsiniz. Aşağıdaki kod, `mydata` kapsayıcıdaki her bir öğenin URI 'sini alma ve çıkışın nasıl yapılacağını göstermektedir:

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L67-L80)]

Bloblarını adlarına yol bilgileriyle de girebilirsiniz. Bu, geleneksel bir dosya sisteminde olduğu gibi düzenleme ve geçiş yapabileceğiniz bir sanal dizin yapısı oluşturur. Dizin yapısının yalnızca sanal olduğunu unutmayın. blob depolamada kullanılabilen tek kaynak, kapsayıcılar ve bloblardır. Ancak, depolama istemci kitaplığı bir sanal dizine `CloudBlobDirectory` başvuracak bir nesne sunar ve bu şekilde düzenlenmiş bloblarla çalışma sürecini basitleştirir.

Örneğin, aşağıdaki adlı `photos`kapsayıcıda bulunan blok Blobları kümesini göz önünde bulundurun:

*photo1. jpg*\
*2015/mimari/Description. txt*\
*2015/Architecture/photo3. jpg*\
*2015/Architecture/photo4. jpg*\
*2016/Architecture/photo5. jpg*\
*2016/Architecture/photo6. jpg*\
*2016/mimari/Description. txt*\
*2016/photo7. jpg*\

Bir kapsayıcıda ( `ListBlobs` Yukarıdaki örnekte olduğu gibi) çağırdığınızda, hiyerarşik bir liste döndürülür. Hem hem de `CloudBlobDirectory` `CloudBlockBlob` nesneler içeriyorsa, kapsayıcıda dizin ve Blobları temsil eder, sonuçta elde edilen çıktı şuna benzer:

```console
Directory: https://<accountname>.blob.core.windows.net/photos/2015/
Directory: https://<accountname>.blob.core.windows.net/photos/2016/
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

İsteğe bağlı olarak, `UseFlatBlobListing` `ListBlobs` yönteminin parametresini olarak `true`ayarlayabilirsiniz. Bu durumda, kapsayıcıdaki her blob bir `CloudBlockBlob` nesne olarak döndürülür. Düz bir liste `ListBlobs` döndürmek için çağrısı şöyle görünür:

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

## <a name="download-blobs"></a>Blob 'ları indir

Blob 'ları indirmek için önce bir blob başvurusu alın ve sonra `DownloadToStream` yöntemi çağırın. Aşağıdaki örnek, blob içeriğini `DownloadToStream` bir Stream nesnesine aktarmak için, daha sonra yerel bir dosyada kalıcı hale getirebilmeniz için yöntemini kullanır.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L95-L101)]

Bir Blobun içeriğini bir `DownloadToStream` metin dizesi olarak indirmek için yöntemini de kullanabilirsiniz.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L103-L106)]

## <a name="delete-blobs"></a>Blob 'ları silme

Bir blobu silmek için önce bir blob başvurusu alın ve ardından üzerinde `Delete` yöntemi çağırın.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L112-L116)]

## <a name="list-blobs-in-pages-asynchronously"></a>Sayfalardaki Blobları zaman uyumsuz olarak Listele

Çok sayıda blob listelemeyi veya bir listeleme işleminde geri aldığınız sonuçların sayısını denetlemek istiyorsanız, blob 'ların sonuçları sayfalarında listeleyebilirsiniz. Bu örnek, büyük bir sonuç kümesi döndürmeyi beklerken yürütmenin engellenmemesi için sayfaların zaman uyumsuz olarak nasıl döndürülmeyeceğini gösterir.

Bu örnek, düz bir blob listesini gösterir, ancak `useFlatBlobListing` `ListBlobsSegmentedAsync` yönteminin parametresini olarak `false`ayarlayarak hiyerarşik bir liste da gerçekleştirebilirsiniz.

Örnek, `async` blok kullanarak bir zaman uyumsuz yöntemi tanımlar. ``let!`` Anahtar sözcüğü, listeleme görevi tamamlanana kadar örnek yöntemi yürütmeyi askıya alır.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L122-L160)]

Artık bu zaman uyumsuz yordamı aşağıdaki gibi kullanabiliriz. İlk olarak bazı kukla verileri karşıya yüklersiniz (Bu öğreticide daha önce oluşturulan yerel dosyayı kullanarak).

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L162-L166)]

Şimdi, yordamını çağırın. Zaman uyumsuz `Async.RunSynchronously` işlemin yürütülmesini zorlamak için kullanırsınız.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L168-L168)]

## <a name="writing-to-an-append-blob"></a>Ekleme blobuna yazma

Append blobu, günlüğe kaydetme gibi ekleme işlemleri için iyileştirilmiştir. Bir blok blobu gibi, bir ekleme blobu bloklardan oluşur, ancak ekleme blobuna yeni bir blok eklediğinizde, her zaman blob 'un sonuna eklenir. Ekleme blobundan var olan bir bloğu güncelleştiremez veya silemezsiniz. Bir ekleme Blobun blok kimlikleri bir Blok Blobu için olduğu gibi gösterilmez.

Bir ekleme blobunun her bloğu, en fazla 4 MB olmak üzere farklı bir boyut olabilir ve bir ekleme blobu en fazla 50.000 blok içerebilir. Bu nedenle, bir ekleme Blobun en büyük boyutu 195 GB 'den (4 MB X 50.000 blok) biraz daha fazla.

Aşağıdaki örnek, yeni bir ekleme blobu oluşturur ve basit bir günlüğe kaydetme işleminin benzetimini yapar ve buna veri ekler.

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L174-L203)]

Üç tür blob arasındaki farklar hakkında daha fazla bilgi için bkz. [blok bloblarını, sayfa bloblarını ve ekleme Bloblarını anlama](https://msdn.microsoft.com/library/azure/ee691964.aspx) .

## <a name="concurrent-access"></a>Eşzamanlı erişim

Birden fazla istemciden veya birden çok işlem örneğiyle bir Blobun eşzamanlı erişimini desteklemek için **ETags** veya **kiralamalar**kullanabilirsiniz.

- **ETag** -Blobun veya kapsayıcının başka bir işlem tarafından değiştirildiğini algılamaya yönelik bir yol sağlar

- **Kira** -bir zaman dilimi için bir Blobun özel, yenilenebilir, yazma veya silme erişimi elde etmek için bir yol sağlar

Daha fazla bilgi için bkz. [Microsoft Azure depolama eşzamanlılık yönetimi](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).

## <a name="naming-containers"></a>Kapsayıcıları adlandırma

Azure Storage 'daki her blob bir kapsayıcıda yer almalıdır. Kapsayıcı, blob adının bir parçasını oluşturur. Örneğin, `mydata` Bu örnek blob URI 'lerinde kapsayıcının adıdır:

- https://storagesample.blob.core.windows.net/mydata/blob1.txt
- https://storagesample.blob.core.windows.net/mydata/photos/myphoto.jpg

Bir kapsayıcı adı, aşağıdaki adlandırma kurallarına uyan geçerli bir DNS adı olmalıdır:

1. Kapsayıcı adları bir harf veya sayıyla başlamalıdır ve yalnızca harf, rakam ve tire (-) karakterini içerebilir.
1. Her Dash (-) karakteri hemen önce ve ardından bir harf veya sayı gelmelidir; kapsayıcı adlarında ardışık kesik çizgilerden izin verilmez.
1. Bir kapsayıcı adındaki tüm harflerin küçük harf olması gerekir.
1. Kapsayıcı adları 3 ila 63 karakter uzunluğunda olmalıdır.

Kapsayıcının adının her zaman küçük harfli olması gerektiğini unutmayın. Bir kapsayıcı adına bir büyük harfli harf eklerseniz veya kapsayıcı adlandırma kurallarını ihlal ederseniz, bir 400 hatası (Hatalı Istek) alabilirsiniz.

## <a name="managing-security-for-blobs"></a>Blobların güvenliğini yönetme

Varsayılan olarak, Azure depolama, hesap erişim anahtarlarına sahip olan hesap sahibine erişimi sınırlandırarak verilerinizi güvende tutar. Depolama hesabınızda blob verilerini paylaşmanız gerektiğinde, hesap erişim anahtarlarınızın güvenliğine ödün vermeden bunu yapmak önemlidir. Ayrıca, Azure depolama 'da ve Azure Storage 'da güvenli olduğundan emin olmak için blob verilerini şifreleyebilirsiniz.

### <a name="controlling-access-to-blob-data"></a>Blob verilerine erişimi denetleme

Varsayılan olarak, Depolama hesabınızdaki blob verilerine yalnızca depolama hesabı sahibine erişilebilir. Blob depolamaya karşı istekleri doğrulamak, varsayılan olarak hesap erişim anahtarı gerektirir. Ancak, bazı blob verilerini diğer kullanıcılar için kullanılabilir hale getirmek isteyebilirsiniz.

### <a name="encrypting-blob-data"></a>Blob verilerini şifreleme

Azure depolama, blob verilerini hem istemcide hem de sunucuda şifrelemeyi destekler.

## <a name="next-steps"></a>Sonraki adımlar

BLOB depolama hakkında temel bilgileri öğrendiğinize göre, daha fazla bilgi edinmek için bu bağlantıları izleyin.

### <a name="tools"></a>Araçlar

- [F#Azurestooygettypeınfo sağlayıcısı](https://fsprojects.github.io/AzureStorageTypeProvider/)\
Blob F# , tablo ve kuyruk Azure depolama varlıklarını araştırmak ve bunlara kolayca CRUD işlemleri uygulamak için kullanılabilen bir tür sağlayıcısı.

- [FSharp. Azure. Storage](https://github.com/fsprojects/FSharp.Azure.Storage)\
Microsoft Azure F# tablo depolama hizmeti kullanmak için bir API

- [Microsoft Azure Depolama Gezgini (Mao)](/azure/vs-azure-tools-storage-manage-with-storage-explorer)\
Microsoft 'un Windows, OS X ve Linux üzerinde Azure Depolama verileriyle görsel olarak çalışmanızı sağlayan ücretsiz ve tek başına bir uygulama.

### <a name="blob-storage-reference"></a>BLOB depolama başvurusu

- [.NET için Azure depolama API 'Leri](/dotnet/api/overview/azure/storage)
- [Azure depolama hizmetleri REST API başvurusu](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)

### <a name="related-guides"></a>İlgili kılavuzlar

- [Azure Blob depolama ile çalışmaya başlamaC#](https://azure.microsoft.com/resources/samples/storage-blob-dotnet-getting-started/)
- [Windows 'da AzCopy komut satırı yardımcı programıyla veri aktarma](/azure/storage/common/storage-use-azcopy)
- [Linux üzerinde AzCopy komut satırı yardımcı programıyla veri aktarma](/azure/storage/common/storage-use-azcopy-linux)
- [Azure depolama bağlantı dizelerini yapılandırma](/azure/storage/common/storage-configure-connection-string)
- [Azure depolama ekibi blogu](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [Hızlı Başlangıç: .NET kullanarak nesne depolamada blob oluşturma](/azure/storage/blobs/storage-quickstart-blobs-dotnet)
