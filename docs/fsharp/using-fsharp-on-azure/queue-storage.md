---
title: "F # kullanarak Azure kuyruk depolamaya başlayın"
description: "Uygulama bileşenleri arasında güvenilir ve zaman uyumsuz Mesajlaşma Azure kuyrukları sağlar. İleti etkinleştirir bağımsız olarak ölçeklendirebilirsiniz uygulama bileşenlerinizin bulut."
keywords: "Visual f #, f #, işlev, .NET, .NET Core, Azure programlama"
author: sylvanc
ms.author: phcart
ms.date: 09/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 70dc554c-8f4d-42a7-8e2a-6438657d012a
ms.openlocfilehash: 50b2d69a1753add688aa14c3314a0ca2df9f03a4
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2018
---
# <a name="get-started-with-azure-queue-storage-using-f"></a>F # kullanarak Azure kuyruk depolamaya başlayın #

Azure kuyruk depolama uygulama bileşenleri arasında Mesajlaşma bulut sağlar. Böylece bağımsız olarak ölçeklendirebilirsiniz uygulamalar için ölçek tasarlarken, uygulama bileşenleri genellikle birbirinden ayrılır. Bulutta, masaüstünde, bir şirket içi sunucu veya bir mobil cihaz çalıştırıp çalıştırmadığınızı uygulama bileşenleri arasında iletişim için zaman uyumsuz Mesajlaşma kuyruk depolama sunar. Kuyruk depolama ayrıca zaman uyumsuz görevlerin yönetilmesini ve süreç iş akışlarının oluşturulmasını destekler.

### <a name="about-this-tutorial"></a>Bu öğretici hakkında

Bu öğretici Azure kuyruk depolama kullanarak bazı ortak görevler için F # kodunun nasıl yazılacağını gösterir. Kapsanan görevler oluşturma ve silme ve ekleme, okuma ve iletileri kuyruğa silme içerir.

Kuyruk depolama kavramsal bir genel bakış için lütfen bkz [kuyruk depolama için .NET Kılavuzu](/azure/storage/storage-dotnet-how-to-use-queues).

## <a name="prerequisites"></a>Önkoşullar

Bu kılavuzu kullanmak için öncelikle [bir Azure depolama hesabı oluşturma](/azure/storage/storage-create-storage-account).
Bu hesap için depolama erişim anahtarınızı de gerekir.

## <a name="create-an-f-script-and-start-f-interactive"></a>Bir F # betiği ve başlangıç F # Etkileşimli oluşturma

Bu makaledeki örnekler, F # uygulaması veya F # betiği kullanılabilir. F # betiği oluşturmak için dosya oluştur `.fsx` uzantısı, örneğin `queues.fsx`, ortamınızdaki F # geliştirme.

Ardından, kullanın bir [Paket Yöneticisi](package-management.md) gibi [Paket](https://fsprojects.github.io/Paket/) veya [NuGet](https://www.nuget.org/) yüklemek için `WindowsAzure.Storage` paket ve başvuru `WindowsAzure.Storage.dll` bir kullanarakkomut`#r`yönergesi.

### <a name="add-namespace-declarations"></a>Ad alanı bildirimleri ekleme

Aşağıdakileri ekleyin `open` deyimleri üstüne `queues.fsx` dosyası:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L1-L3)]

### <a name="get-your-connection-string"></a>Bağlantı dizenizi Al

Bu öğretici için bir Azure depolama bağlantı dizesi gerekir. Bağlantı dizeleri hakkında daha fazla bilgi için bkz: [Storage bağlantı dizelerini yapılandırma](/azure/storage/storage-configure-connection-string).

Öğretici için şuna benzer betiğinizin bağlantı dizenizi girin:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L9-L9)]

Ancak, bu olduğu **önerilmez** için gerçek projeleri. Depolama hesabı anahtarınız depolama hesabınızın kök parolasına benzer. Her zaman depolama hesabı anahtarınızı korumak dikkatli olun. Sabit kodlama veya başkalarının erişebileceği düz metin dosyasına kaydetme diğer kullanıcılara dağıtmaktan kaçının. Bunu tehlikede olduğunu düşünüyorsanız, Azure Portalı'nı kullanarak anahtarınızı yeniden oluşturabilirsiniz.

İçin gerçek uygulamalar, depolama bağlantı dizenizi korumak için en iyi yapılandırma dosyasında yoludur. Yapılandırma dosyasından bağlantı dizesini almak için bunu yapabilirsiniz:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L11-L13)]

Azure Yapılandırma Yöneticisi'ni kullanarak isteğe bağlıdır. .NET Framework'ün gibi bir API de kullanabilirsiniz `ConfigurationManager` türü.

### <a name="parse-the-connection-string"></a>Bağlantı dizesini ayrıştırma

Bağlantı dizesini ayrıştırmak için kullanın:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L19-L20)]

Bu döndürülecek bir `CloudStorageAccount`.

### <a name="create-the-queue-service-client"></a>Kuyruk hizmeti istemcisi oluşturma

`CloudQueueClient` Sınıfı, kuyruk depolamada depolanan kuyrukları almanızı sağlar. Hizmet istemcisini oluşturma yöntemlerinden biri aşağıda verilmiştir:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L26-L26)]

Şimdi veri okuyan ve kuyruk depolama alanına veri yazan kodu yazmaya hazırsınız.

## <a name="create-a-queue"></a>Bir sıra oluşturun

Bu örnek, zaten yoksa bir sıranın nasıl oluşturulacağını gösterir:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L32-L36)]

## <a name="insert-a-message-into-a-queue"></a>Kuyruğa bir ileti Ekle

Varolan bir sıraya bir ileti eklemek için ilk olarak yeni bir oluşturma `CloudQueueMessage`. Ardından, çağrı `AddMessage` yöntemi. A `CloudQueueMessage` herhangi birinden bir dizeden (UTF-8 biçiminde) oluşturulabilir veya `byte` dizisi şöyle:

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L42-L44)]

## <a name="peek-at-the-next-message"></a>Sonraki iletiye

Size, kuyruğun önündeki iletiye sıradan çağırarak kaldırmadan iletiye göz atabilirsiniz `PeekMessage` yöntemi.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L50-L52)]

## <a name="get-the-next-message-for-processing"></a>İşleme için sonraki ileti alma

Çağırarak bir sıra ön işleme için ileti alabilir `GetMessage` yöntemi.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L58-L59)]

Daha sonra kullanarak iletinin başarılı işleme belirtmek `DeleteMessage`.

## <a name="change-the-contents-of-a-queued-message"></a>Kuyruğa Alınan iletinin içeriğini değiştirme

Bir alınan ileti yerinde sırasındaki içeriğini değiştirebilirsiniz. İleti bir iş görevini temsil ediyorsa, iş görevinin durumunu güncelleştirmek için bu özelliği kullanabilirsiniz. Aşağıdaki kod kuyruk iletisini yeni içeriklerle güncelleştirir ve görünürlük zaman aşımını 60 saniye daha uzatır. Bu ileti ile ilişkili işin durumunu kaydeder ve istemciye ileti üzerinde çalışmaya devam etmek için bir dakika daha zaman verir. Üzerinden bir işleme adımı donanım veya yazılım arızasından dolayı başarısız olursa baştan başlamanıza gerek kalmadan kuyruk iletilerindeki çok adımlı iş akışlarını izlemek için bu tekniği kullanabilirsiniz. Genellikle, bir yeniden deneme sayısı da tutacak ve ileti birden çok bazı kaç kez denenirse, silebilirsiniz. Bu, her işlendiğinde bir uygulama hatası tetikleyen bir iletiye karşı korur.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L65-L69)]

## <a name="de-queue-the-next-message"></a>Sonraki iletiyi sıradan çıkarmak

Kodunuzun bir iletiyi bir kuyruktan iki adımda çıkarır. Çağırdığınızda `GetMessage`, sonraki iletiyi sıraya alın. Döndürülen bir ileti `GetMessage` iletileri bu sıradan okuyan herhangi bir kod görünmez olur. Varsayılan olarak, bu ileti 30 saniye görünmez kalır. İletiyi kuyruktan kaldırmayı tamamlamak için de çağırmanız gerekir `DeleteMessage`. Bir ileti kaldırmanın bu iki adımlı işlem donanım veya yazılım hatası nedeniyle bir ileti işlemek kodunuzu başarısız olursa, kodunuzu başka bir örneği aynı ileti alma ve yeniden deneyin sağlar. Kod çağrılarınızı `DeleteMessage` ileti işlendikten sonra sağ.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L75-L76)]

## <a name="use-async-workflows-with-common-queue-storage-apis"></a>Genel kuyruk depolama API'leri ile zaman uyumsuz iş akışları kullanın

Bu örnek, genel kuyruk depolama API'leri ile zaman uyumsuz iş akışı kullanmayı gösterir.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L82-L91)]

## <a name="additional-options-for-de-queuing-messages"></a>Çıkarılması iletileri için ek seçenekleri

Bir sıradan ileti alma özelleştirebilirsiniz iki yolu vardır.
İlk olarak toplu iletiler (en fazla 32) elde edebilirsiniz. İkinci olarak, bir uzun veya daha kısa bir görünmezlik zaman aşımı kodunuzun her iletiyi tamamen işlemesi için zaman daha az veya daha fazla izin vererek ayarlayabilirsiniz. Aşağıdaki kod örneğinde `GetMessages` 20 almak için iletileri bir çağrı'ı ve ardından her ileti işler. Ayrıca her ileti için beş dakika için görünmezlik zaman aşımı ayarlar. 5 dakikalık sürenin tüm iletiler için aynı anda Not böylece sonra 5 dakika geçirilen çağrısından sonra `GetMessages`, silinmemiş tüm iletiler görünür olacaktır.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L97-L99)]

## <a name="get-the-queue-length"></a>Kuyruk uzunluğu alma

Bir kuyruktaki ileti sayısı tahmini alabilirsiniz. `FetchAttributes` Yöntemi kuyruk hizmeti ileti sayısı dahil olmak üzere kuyruk özniteliklerini almasını ister. `ApproximateMessageCount` Özelliği tarafından alınan en son değeri döndürür `FetchAttributes` kuyruk hizmetini çağırmadan olmadan yöntemi.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L105-L106)]

## <a name="delete-a-queue"></a>Bir kuyruk silme

Bir kuyruk ve içerdiği tüm iletileri silmek için arama `Delete` nesnesinde yöntemi.

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L112-L113)]

## <a name="next-steps"></a>Sonraki adımlar

Kuyruk depolamanın temellerini öğrendiğinize göre daha karmaşık depolama görevleri hakkında bilgi edinmek için aşağıdaki bağlantıları izleyin.

- [.NET için Azure depolama API'leri](/dotnet/api/overview/azure/storage)
- [Azure depolama türü sağlayıcısı](https://github.com/fsprojects/AzureStorageTypeProvider)
- [Azure depolama ekibi blogu](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [Azure Storage bağlantı dizelerini yapılandırma](/azure/storage/common/storage-configure-connection-string)
- [Azure Storage Hizmetleri REST API Başvurusu](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)
