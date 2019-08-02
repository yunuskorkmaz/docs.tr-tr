---
title: F# kullanarak Azure Kuyruk depolama kullanmaya başlama
description: Azure kuyrukları, uygulama bileşenleri arasında güvenilir ve zaman uyumsuz mesajlaşma sağlar. Bulut mesajlaşma, uygulama bileşenlerinizin bağımsız olarak ölçeklendirilmesini sağlar.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 65af98fb88e91d709eb0e35907cbc2dc097634d0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630490"
---
# <a name="get-started-with-azure-queue-storage-using-f"></a>F kullanarak Azure kuyruk depolama ile çalışmaya başlama\#

Azure kuyruk depolama, uygulama bileşenleri arasında bulut mesajlaşmasını sağlar. Uygulamaları ölçeklendirmek için tasarlarken, uygulama bileşenleri genellikle birbirinden bağımsız olarak ölçeklendirilebilecek şekilde ayrılır. Kuyruk depolama, bulutta, masaüstünde, şirket içi sunucuda veya mobil cihazda çalışan uygulama bileşenleri arasındaki iletişim için zaman uyumsuz mesajlaşma sağlar. Kuyruk depolama Ayrıca zaman uyumsuz görevlerin yönetilmesini ve işlem iş akışlarının oluşturulmasını destekler.

### <a name="about-this-tutorial"></a>Bu öğretici hakkında

Bu öğreticide, Azure kuyruk F# depolama kullanarak bazı yaygın görevler için nasıl kod yazacağınız gösterilmektedir. Kapsanan görevler kuyruk oluşturma ve silme ve sıra iletilerini ekleme, okuma ve silme işlemleri içerir.

Kuyruk depolamaya kavramsal bir genel bakış için lütfen [kuyruk depolaması için .net kılavuzuna](/azure/storage/storage-dotnet-how-to-use-queues)bakın.

## <a name="prerequisites"></a>Önkoşullar

Bu kılavuzu kullanmak için önce [bir Azure depolama hesabı oluşturmanız](/azure/storage/storage-create-storage-account)gerekir.
Ayrıca, bu hesap için depolama erişim anahtarınız gerekecektir.

## <a name="create-an-f-script-and-start-f-interactive"></a>F# Betik oluşturma ve etkileşimli başlatma F#

Bu makaledeki örnekler, bir F# uygulama ya da bir F# komut dosyasında kullanılabilir. Bir F# betik oluşturmak için, örneğin `.fsx` `queues.fsx`, F# geliştirme ortamınızda uzantılı bir dosya oluşturun.

Daha sonra, `WindowsAzure.Storage` paketi ve bir `WindowsAzure.Storage.dll` [](https://fsprojects.github.io/Paket/) yönergekullanarakbetiğepaketvebaşvuruyüklemekiçin,paketveyaNuGetgibibirpaketyöneticisi`#r` kullanın. [](package-management.md) [](https://www.nuget.org/)

### <a name="add-namespace-declarations"></a>Ad alanı bildirimleri ekle

Aşağıdaki `open` deyimlerini `queues.fsx` dosyanın en üstüne ekleyin:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L1-L3)]

### <a name="get-your-connection-string"></a>Bağlantı dizenizi alın

Bu öğretici için bir Azure depolama bağlantı dizesi gerekir. Bağlantı dizeleri hakkında daha fazla bilgi için bkz. [depolama bağlantı dizelerini yapılandırma](/azure/storage/storage-configure-connection-string).

Öğreticide, aşağıdaki gibi, komut dosyası için Bağlantı dizenizi girersiniz:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L9-L9)]

Ancak, bu gerçek projeler için **önerilmez** . Depolama hesabı anahtarınız, depolama hesabınızın kök parolasıyla benzerdir. Depolama hesabı anahtarınızı korumak için her zaman özen gösterin. Diğer kullanıcılara dağıtmaktan, sabit kodlamaktan ve başkalarının erişebileceği düz metin dosyasına kaydetmekten kaçının. Güvenliğinin tehlikede olduğunu düşünüyorsanız, Azure portalını kullanarak anahtarınızı yeniden oluşturabilirsiniz.

Gerçek uygulamalar için, depolama Bağlantı dizenizi korumak için en iyi yol bir yapılandırma dosyasıdır. Bağlantı dizesini bir yapılandırma dosyasından getirmek için şunu yapabilirsiniz:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L11-L13)]

Azure Configuration Manager kullanmak isteğe bağlıdır. .NET Framework `ConfigurationManager` türü gibi bir API de kullanabilirsiniz.

### <a name="parse-the-connection-string"></a>Bağlantı dizesini ayrıştırma

Bağlantı dizesini ayrıştırmak için şunu kullanın:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L19-L20)]

Bu, döndürür `CloudStorageAccount`.

### <a name="create-the-queue-service-client"></a>Kuyruk hizmeti istemcisini oluşturma

Sınıfı `CloudQueueClient` , kuyruk depolamada depolanan kuyrukları almanızı sağlar. Hizmet istemcisini oluşturmak için bir yol aşağıda verilmiştir:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L26-L26)]

Artık veri okuyan ve kuyruk depolamaya veri yazan kodu yazmaya hazırsınız.

## <a name="create-a-queue"></a>Sıra oluşturma

Bu örnek, zaten yoksa bir sıranın nasıl oluşturulacağını gösterir:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L32-L36)]

## <a name="insert-a-message-into-a-queue"></a>Bir kuyruğa ileti ekleme

Mevcut bir kuyruğa ileti eklemek için ilk olarak yeni `CloudQueueMessage`bir oluştur. Sonra, `AddMessage` yöntemini çağırın. Bir `CloudQueueMessage` dizeden (UTF-8 biçiminde) `byte` ya da bir dizide oluşturulabilir ve şöyle olabilir:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L42-L44)]

## <a name="peek-at-the-next-message"></a>Sonraki iletiye göz atın

Bir kuyruğun önünde, `PeekMessage` yöntemini çağırarak sıradan kaldırmadan iletiye göz atmayı sağlayabilirsiniz.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L50-L52)]

## <a name="get-the-next-message-for-processing"></a>İşleme için bir sonraki iletiyi alın

Yöntemi çağırarak, `GetMessage` işlenmek üzere bir kuyruğun önündeki iletiyi alabilirsiniz.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L58-L59)]

Daha sonra, kullanarak `DeleteMessage`iletinin başarıyla işlenmesini belirteceksiniz.

## <a name="change-the-contents-of-a-queued-message"></a>Sıraya alınan iletinin içeriğini değiştirme

Alınan bir iletinin içeriğini kuyrukta yerinde değiştirebilirsiniz. İleti bir iş görevini temsil ediyorsa, iş görevinin durumunu güncelleştirmek için bu özelliği kullanabilirsiniz. Aşağıdaki kod, kuyruk iletisini yeni içerikle güncelleştirir ve görünürlük zaman aşımını başka bir 60 saniye uzatmak üzere ayarlar. Bu, iletiyle ilişkili çalışmanın durumunu kaydeder ve istemciye ileti üzerinde çalışmaya devam etmesi için başka bir dakika verir. Bu tekniği, işlem adımı donanım veya yazılım arızası nedeniyle başarısız olursa baştan başlamak zorunda kalmadan, kuyruk iletilerinde çok adımlı iş akışlarını izlemek için kullanabilirsiniz. Genellikle bir yeniden deneme sayısı da olur ve ileti birkaç kez yeniden denense de onu silersiniz. Bu, her işlendiği zaman bir uygulama hatasını tetikleyen bir iletiye karşı koruma sağlar.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L65-L69)]

## <a name="de-queue-the-next-message"></a>Sonraki iletiyi kuyruktan kaldır

Kodunuz, iki adımda bir kuyruktan bir ileti de sıralar. ' İ çağırdığınızda `GetMessage`bir kuyruktaki sonraki iletiyi alırsınız. Öğesinden `GetMessage` döndürülen bir ileti, bu kuyruktan gelen diğer kod okuma iletileri için görünmez hale gelir. Bu ileti, varsayılan olarak 30 saniye boyunca görünmez kalır. İletiyi kuyruktan kaldırma işleminin tamamlanabilmesi için, öğesini de çağırmanız `DeleteMessage`gerekir. Bir iletiyi kaldırmanın bu iki adımlı işlemi, kodunuz, donanım veya yazılım arızasından kaynaklanan bir iletiyi işleyemediğinde, kodunuzun başka bir örneğinin aynı mesajı almasını ve yeniden denemesini sağlar. İleti işlendikten sonra `DeleteMessage` kodunuz doğru şekilde çağırır.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L75-L76)]

## <a name="use-async-workflows-with-common-queue-storage-apis"></a>Ortak kuyruk depolama API 'Leri ile zaman uyumsuz iş akışları kullanma

Bu örnek, genel sıra depolama API 'Leri ile zaman uyumsuz bir iş akışının nasıl kullanılacağını gösterir.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L82-L91)]

## <a name="additional-options-for-de-queuing-messages"></a>İletileri serbest bırakma için ek seçenekler

İleti alımı bir kuyruktan özelleştirmek için kullanabileceğiniz iki yol vardır.
İlk olarak, bir toplu ileti alabilirsiniz (en fazla 32). İkincisi, daha uzun veya daha kısa bir zaman aşımı ayarlayabilir, böylece her iletiyi tamamen işlemek için kodunuzun daha fazla veya daha az zaman aşımına uğramamasını sağlayabilirsiniz. Aşağıdaki kod örneği, bir `GetMessages` çağrıda 20 ileti almak için kullanır ve ardından her iletiyi işler. Ayrıca, her ileti için geçersiz kılma zaman aşımını beş dakikaya ayarlar. 5 dakikalık tüm iletiler için aynı anda başlayacağını unutmayın. bu nedenle, çağrısından `GetMessages`bu yana 5 dakika geçtikten sonra, silinmemiş olan tüm iletiler yeniden görünür hale gelir.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L97-L99)]

## <a name="get-the-queue-length"></a>Sıra uzunluğunu al

Kuyruktaki ileti sayısını tahmin edebilirsiniz. `FetchAttributes` Yöntemi, ileti sayısı dahil olmak üzere kuyruk hizmeti kuyruk özniteliklerini almayı ister. Özelliği, kuyruk hizmeti çağrılmadan `FetchAttributes` yöntemi tarafından alınan son değeri döndürür. `ApproximateMessageCount`

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L105-L106)]

## <a name="delete-a-queue"></a>Kuyruğu silme

Bir kuyruğu ve içerdiği tüm iletileri silmek için, kuyruk nesnesi üzerinde `Delete` yöntemini çağırın.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L112-L113)]

## <a name="next-steps"></a>Sonraki adımlar

Sıra depolamanın temellerini öğrendiğinize göre, daha karmaşık depolama görevleri hakkında bilgi edinmek için bu bağlantıları izleyin.

- [.NET için Azure depolama API 'Leri](/dotnet/api/overview/azure/storage)
- [Azure depolama türü sağlayıcısı](https://github.com/fsprojects/AzureStorageTypeProvider)
- [Azure depolama ekibi blogu](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [Azure depolama bağlantı dizelerini yapılandırma](/azure/storage/common/storage-configure-connection-string)
- [Azure depolama hizmetleri REST API başvurusu](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)
