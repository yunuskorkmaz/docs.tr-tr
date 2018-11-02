---
title: 'F # kullanarak Azure kuyruk depolama ile çalışmaya başlama'
description: Azure kuyrukları, uygulama bileşenleri arasında güvenilir ve zaman uyumsuz Mesajlaşma sağlar. Mesajlaşma etkinleştirir, uygulama bileşenlerinizin bağımsız olarak ölçeklendirme bulut.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 14bbc657f965fc262d2a83b1fdf982fe5e75d55e
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "33569424"
---
# <a name="get-started-with-azure-queue-storage-using-f"></a>F # kullanarak Azure kuyruk depolama ile çalışmaya başlama #

Azure kuyruk depolama, uygulama bileşenleri arasında bulut Mesajlaşma sağlar. Böylece ölçeklendirilebilmeleri ölçek için uygulamaları tasarlarken, uygulama bileşenleri genellikle birbirinden ayrılır. Kuyruk depolama, bulutta, masaüstünde, şirket içi sunucusunda veya mobil bir cihazda çalışan uygulama bileşenleri arasındaki iletişim için zaman uyumsuz Mesajlaşma sunar. Kuyruk depolama ayrıca zaman uyumsuz görevlerin yönetilmesini ve süreç iş akışlarının oluşturulmasını destekler.

### <a name="about-this-tutorial"></a>Bu eğitim hakkında

Bu öğreticide nasıl yazılacağını göstermektedir F# Azure kuyruk depolama kullanarak bazı ortak görevler için kod. Kapsanan görevler oluşturma ve kuyrukları silme ve ekleme, okuma ve silme kuyruk iletileri içerir.

Kuyruk depolama kavramsal bir genel bakış için bkz. Lütfen [kuyruk depolama için .NET Kılavuzu](/azure/storage/storage-dotnet-how-to-use-queues).

## <a name="prerequisites"></a>Önkoşullar

Bu kılavuzu kullanmak için önce [bir Azure depolama hesabı oluşturma](/azure/storage/storage-create-storage-account).
Ayrıca, bu hesap için depolama erişim anahtarınızı gerekir.

## <a name="create-an-f-script-and-start-f-interactive"></a>Bir F # komut dosyası ve başlangıç F # Etkileşimli oluşturma

Bu makaledeki örnekleri, F # uygulaması veya bir F # komut dosyası kullanılabilir. Bir F # komut dosyası oluşturmak için bir dosya oluşturun. `.fsx` uzantısı, örneğin `queues.fsx`, F # geliştirme ortamınızda.

Ardından, bir [Paket Yöneticisi](package-management.md) gibi [Paket](https://fsprojects.github.io/Paket/) veya [NuGet](https://www.nuget.org/) yüklemek için `WindowsAzure.Storage` paket ve başvuru `WindowsAzure.Storage.dll` bir kullanarakbetiğinizde`#r`yönergesi.

### <a name="add-namespace-declarations"></a>Ad alanı bildirimleri ekleme

Aşağıdaki `open` üst tarafına deyimlerini `queues.fsx` dosyası:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L1-L3)]

### <a name="get-your-connection-string"></a>Bağlantı dizenizi alma

Bu öğreticide bir Azure depolama bağlantı dizesi gerekir. Bağlantı dizeleri hakkında daha fazla bilgi için bkz. [depolama bağlantı dizelerini yapılandırma](/azure/storage/storage-configure-connection-string).

Öğretici için şunun gibi komut dosyanızdaki bağlantı dizenizi girmenizi isteriz:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L9-L9)]

Ancak, bu, **önerilmez** gerçek projeleri. Depolama hesabı anahtarınız depolama hesabınızın kök parolasına benzer. Her zaman depolama hesabı anahtarınızı korumak dikkatli olun. Sabit kodlama veya başkalarının erişebileceği bir düz metin dosyasına kaydederek diğer kullanıcılara dağıtmaktan kaçının. Tehlikeye girmiş olabilecek düşünüyorsanız Azure portalını kullanarak anahtarınızı yeniden oluşturabilirsiniz.

Gerçek uygulamalar, depolama bağlantı dizenizi korumak için en iyi yolu, içinde bir yapılandırma dosyasıdır. Bir yapılandırma dosyasından bağlantı dizesini getirmek için bunu yapabilirsiniz:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L11-L13)]

Azure Yapılandırma Yöneticisi'ni kullanmak isteğe bağlıdır. .NET Framework'ün gibi bir API de kullanabilirsiniz `ConfigurationManager` türü.

### <a name="parse-the-connection-string"></a>Bağlantı dizesini ayrıştırma

Bağlantı dizesini ayrıştırmak için kullanın:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L19-L20)]

Bu döndürür bir `CloudStorageAccount`.

### <a name="create-the-queue-service-client"></a>Kuyruk hizmeti istemcisi oluşturma

`CloudQueueClient` Sınıfı, kuyruk depolamada depolanan kuyrukları almanızı sağlar. Hizmet istemcisini oluşturma yöntemlerinden biri aşağıda verilmiştir:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L26-L26)]

Artık, verileri okur ve kuyruk depolamaya veri yazan kodu yazmaya hazırsınız.

## <a name="create-a-queue"></a>Kuyruk oluşturma

Bu örnek, zaten yoksa bir kuyruk oluşturulacağını gösterir:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L32-L36)]

## <a name="insert-a-message-into-a-queue"></a>Kuyruğa bir ileti Ekle

Varolan bir kuyruğa ileti eklemek için ilk olarak yeni bir oluşturma `CloudQueueMessage`. Ardından, arama `AddMessage` yöntemi. A `CloudQueueMessage` herhangi birinden bir dize (UTF-8 biçiminde) oluşturulabilir veya `byte` şunun gibi bir dizi:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L42-L44)]

## <a name="peek-at-the-next-message"></a>Sonraki iletiye gözatın

Kuyruğun, iletiyi kuyruktan kaldırmadan çağırarak peek `PeekMessage` yöntemi.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L50-L52)]

## <a name="get-the-next-message-for-processing"></a>İşleme için sonraki iletiyi Al

İleti işleme için bir kuyruğun önündeki çağırarak alabilirsiniz `GetMessage` yöntemi.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L58-L59)]

Daha sonra kullanarak iletinin başarılı işleme belirtmek `DeleteMessage`.

## <a name="change-the-contents-of-a-queued-message"></a>Kuyruğa Alınan iletinin içeriğini değiştirme

Bir alınan ileti yerinde sırasındaki içeriğini değiştirebilirsiniz. İleti bir iş görevini temsil ediyorsa, kullanarak iş görevinin durumunu güncelleştirmek için bu özelliği kullanabilirsiniz. Aşağıdaki kod kuyruk iletisini yeni içeriklerle güncelleştirir ve görünürlük zaman aşımını 60 saniye daha uzatır. Bu iletiyle ilişkili işin durumunu kaydeder ve istemciye ileti üzerinde çalışmaya devam etmek için bir dakika daha zaman verir. Üzerinden bir işleme adımı donanım veya yazılım arızasından dolayı başarısız olursa baştan başlamanıza gerek kalmadan kuyruk çok adımlı iş akışlarını izlemek için bu tekniği kullanabilirsiniz. Genellikle bir yeniden deneme sayısı yanı tutacak ve ileti en fazla kaç kez denenirse silmeniz. Bu, her işlendiğinde bir uygulama hatası tetikleyen bir iletiye karşı koruma sağlar.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L65-L69)]

## <a name="de-queue-the-next-message"></a>Sonraki iletiyi sıradan çıkarmak

Kodunuzun bir iletiyi bir kuyruktan iki adımda kuyruktan. Çağırdığınızda `GetMessage`, sonraki iletiyi bir kuyruğa alın. Öğesinden döndürülen bir ileti `GetMessage` bu kuyruktan iletileri okuyan herhangi bir kod için görünmez hale gelir. Varsayılan olarak, bu ileti 30 saniye görünmez kalır. İletiyi kuyruktan kaldırmayı tamamlamak için de çağırmanız gerekir `DeleteMessage`. Kodunuzun bir iletiyi donanım veya yazılım hatası nedeniyle başarısız olursa, kodunuzun başka bir örneği aynı iletiyi alıp yeniden deneyin, bu iki adımlı işlem, bir iletinin sağlar. Kod çağrılarınızı `DeleteMessage` ileti işlendikten sonra sağ.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L75-L76)]

## <a name="use-async-workflows-with-common-queue-storage-apis"></a>Genel kuyruk depolama API'leri ile zaman uyumsuz iş akışları kullanın

Bu örnek, genel kuyruk depolama API'leri ile zaman uyumsuz bir iş akışı kullanmayı gösterir.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L82-L91)]

## <a name="additional-options-for-de-queuing-messages"></a>İletilerin kuyruktan çıkarılması için ek seçenekler

Bir kuyruktan ileti alma özelleştirebilirsiniz iki yolu vardır.
İlk olarak toplu iletiler (en fazla 32) elde edebilirsiniz. İkinci olarak, daha uzun veya daha kısa bir görünmezlik zaman aşımı, kodunuzun daha fazla veya daha az zaman her iletiyi tamamen işlemesi için izin ayarlayabilirsiniz. Aşağıdaki kod örneğinde `GetMessages` 20 almak için bir ileti çağırın ve ardından her ileti işler. Beş dakika her ileti için görünmezlik zaman aşımı da ayarlar. Bu nedenle sonra 5 dakika 5 dakika için tüm iletiler aynı anda başlatır Not geçirilen çağrısından sonra `GetMessages`, silinmeyen tüm iletiler yeniden görünür hale gelir.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L97-L99)]

## <a name="get-the-queue-length"></a>Kuyruk uzunluğu alma

Kuyrukta ileti sayısını tahmini elde edebilirsiniz. `FetchAttributes` Yöntemi kuyruk hizmetinin ileti sayısı dahil olmak üzere kuyruk özniteliklerini almasını ister. `ApproximateMessageCount` Özelliği tarafından alınan en son değeri döndürür `FetchAttributes` kuyruk hizmetini çağırmadan olmadan yöntemi.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L105-L106)]

## <a name="delete-a-queue"></a>Bir kuyruk silme

Bir kuyruk ve içerdiği tüm iletileri silmek için çağrı `Delete` kuyruk nesnesi üzerinde yöntemi.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L112-L113)]

## <a name="next-steps"></a>Sonraki adımlar

Kuyruk depolamanın temellerini öğrendiğinize göre daha karmaşık depolama görevleri hakkında bilgi edinmek için bu bağlantıları izleyin.

- [.NET için Azure depolama API'leri](/dotnet/api/overview/azure/storage)
- [Azure depolama tür sağlayıcısı](https://github.com/fsprojects/AzureStorageTypeProvider)
- [Azure depolama ekibi blogu](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [Azure Storage bağlantı dizelerini yapılandırma](/azure/storage/common/storage-configure-connection-string)
- [Azure depolama hizmetleri REST API Başvurusu](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)
