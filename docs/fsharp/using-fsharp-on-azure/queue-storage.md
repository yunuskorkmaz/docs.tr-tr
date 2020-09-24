---
title: F# kullanarak Azure Kuyruk depolama kullanmaya başlama
description: Azure Queues, uygulama bileşenleri arasında güvenilir ve zaman uyumsuz mesajlaşma sağlar. Bulut mesajlaşma özelliği uygulama bileşenlerinizin bağımsız olarak ölçeklendirilmesini sağlar.
author: sylvanc
ms.date: 09/20/2016
ms.custom: devx-track-fsharp
ms.openlocfilehash: 5d6074751f226f0587c4c73bfa9ff56d9aca2bc1
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91100093"
---
# <a name="get-started-with-azure-queue-storage-using-f"></a>F kullanarak Azure kuyruk depolama ile çalışmaya başlama\#

Azure Queue depolama birimi, uygulama bileşenleri arasında bulut mesajlaşma özelliği sağlar. Ölçeklendirmek üzere uygulama tasarlarken, uygulama bileşenleri birbirinden bağımsız şekilde ölçeklenebilmek için genellikle birbirinden ayrılır. Kuyruk depolama bulutta, masaüstünde, şirket içi sunucuda veya mobil bir cihazda çalışan uygulama bileşenleri arasındaki iletişim için zaman uyumsuz mesajlaşma sunar. Kuyruk depolama ayrıca zaman uyumsuz görevlerin yönetilmesini ve süreç iş akışlarının oluşturulmasını destekler.

### <a name="about-this-tutorial"></a>Bu öğretici hakkında

Bu öğreticide, Azure kuyruk depolama kullanan bazı yaygın görevler için F # kodu yazma işlemi gösterilmektedir. Kapsanan görevler kuyruk oluşturma ve silme ve sıra iletilerini ekleme, okuma ve silme işlemleri içerir.

Kuyruk depolamaya kavramsal bir genel bakış için lütfen [kuyruk depolaması için .net kılavuzuna](/azure/storage/storage-dotnet-how-to-use-queues)bakın.

## <a name="prerequisites"></a>Ön koşullar

Bu kılavuzu kullanmak için önce [bir Azure depolama hesabı oluşturmanız](/azure/storage/storage-create-storage-account)gerekir.
Ayrıca, bu hesap için depolama erişim anahtarınız gerekecektir.

## <a name="create-an-f-script-and-start-f-interactive"></a>F # betiği oluşturun ve F# Etkileşimli başlatın

Bu makaledeki örnekler bir F # uygulamasında veya F # betiğinde kullanılabilir. F # betiği oluşturmak için, `.fsx` Örneğin `queues.fsx` f # geliştirme ortamınızda uzantılı bir dosya oluşturun.

Daha sonra, [NuGet](https://www.nuget.org/) [Paket](https://fsprojects.github.io/Paket/) paketi [package manager](package-management.md) `WindowsAzure.Storage` ve `WindowsAzure.Storage.dll` bir yönerge kullanarak betiğe paket ve başvuru yüklemek için, paket veya NuGet gibi bir paket Yöneticisi kullanın `#r` .

### <a name="add-namespace-declarations"></a>Ad alanı bildirimleri ekleme

Aşağıdaki `open` bildirimlerini `queues.fsx` dosyasının üstüne ekleyin:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L1-L3)]

### <a name="get-your-connection-string"></a>Bağlantı dizenizi alma

Bu öğretici için bir Azure depolama bağlantı dizesi gerekir. Bağlantı dizeleri hakkında daha fazla bilgi için bkz. [depolama bağlantı dizelerini yapılandırma](/azure/storage/storage-configure-connection-string).

Öğreticide, aşağıdaki gibi, komut dosyası için Bağlantı dizenizi girersiniz:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L9-L9)]

Ancak, bu gerçek projeler için **önerilmez** . Depolama hesabı anahtarınız depolama hesabınızın kök parolasına benzer. Depolama hesabı anahtarınızı korumak için her zaman özen gösterin. Diğer kullanıcılara dağıtmaktan, sabit kodlamaktan ve başkalarının erişebileceği düz metin dosyasına kaydetmekten kaçının. Güvenliğinin tehlikede olduğunu düşünüyorsanız, Azure portalını kullanarak anahtarınızı yeniden oluşturabilirsiniz.

Gerçek uygulamalar için, depolama Bağlantı dizenizi korumak için en iyi yol bir yapılandırma dosyasıdır. Bağlantı dizesini bir yapılandırma dosyasından getirmek için şunu yapabilirsiniz:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L11-L13)]

Azure Yapılandırma Yöneticisi'ni kullanmak isteğe bağlıdır. .NET Framework türü gibi bir API de kullanabilirsiniz `ConfigurationManager` .

### <a name="parse-the-connection-string"></a>Bağlantı dizesini ayrıştırma

Bağlantı dizesini ayrıştırmak için şunu kullanın:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L19-L20)]

Bu, döndürür `CloudStorageAccount` .

### <a name="create-the-queue-service-client"></a>Kuyruk hizmeti istemcisi oluşturma

`CloudQueueClient`Sınıfı, kuyruk depolamada depolanan kuyrukları almanızı sağlar. Hizmet istemcisini oluşturma yöntemlerinden biri aşağıda verilmiştir:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L26-L26)]

Artık Kuyruk depolamadan veri okuyan ve bu depolamaya veri yazan kodu yazmaya hazırsınız.

## <a name="create-a-queue"></a>Bir kuyruk oluşturma

Bu örnek, zaten yoksa bir sıranın nasıl oluşturulacağını gösterir:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L32-L36)]

## <a name="insert-a-message-into-a-queue"></a>Kuyruğa bir ileti yerleştirme

Mevcut bir kuyruğa ileti eklemek için ilk olarak yeni bir oluştur `CloudQueueMessage` . Sonra, yöntemini çağırın `AddMessage` . Bir `CloudQueueMessage` dizeden (UTF-8 biçiminde) ya da bir dizide oluşturulabilir ve `byte` şöyle olabilir:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L42-L44)]

## <a name="peek-at-the-next-message"></a>Sonraki iletiye gözatın

Bir kuyruğun önünde, yöntemini çağırarak sıradan kaldırmadan iletiye göz atmayı sağlayabilirsiniz `PeekMessage` .

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L50-L52)]

## <a name="get-the-next-message-for-processing"></a>İşleme için bir sonraki iletiyi alın

Yöntemi çağırarak, işlenmek üzere bir kuyruğun önündeki iletiyi alabilirsiniz `GetMessage` .

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L58-L59)]

Daha sonra, kullanarak iletinin başarıyla işlenmesini belirteceksiniz `DeleteMessage` .

## <a name="change-the-contents-of-a-queued-message"></a>Kuyruğa alınan iletinin içeriğini değiştirme

Alınan bir iletinin içeriğini kuyrukta yerinde değiştirebilirsiniz. Eğer ileti bir iş görevini temsil ediyorsa, bu özelliği kullanarak iş görevinin durumunu güncelleştirebilirsiniz. Aşağıdaki kod kuyruk iletisini yeni içeriklerle güncelleştirir ve görünürlük zaman aşımını 60 saniye daha uzatır. Bu, ileti ile ilişkili işin durumunu kaydeder ve istemciye ileti üzerinde çalışmaya devam etmesi için bir dakika daha zaman verir. Bir işleme adımı donanım veya yazılım arızasından dolayı başarısız olursa baştan başlamanıza gerek kalmadan kuyruk iletilerindeki çok adımlı iş akışlarını izlemek için bu yöntemi kullanabilirsiniz. Genellikle bir yeniden deneme sayısı da olur ve ileti birkaç kez yeniden denense de onu silersiniz. Bu, her işlendiğinde bir uygulama hatası tetikleyen bir iletiye karşı koruma sağlar.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L65-L69)]

## <a name="de-queue-the-next-message"></a>Sonraki iletiyi sıradan çıkarmak

Kodunuz, bir iletiyi bir kuyruktan iki adımda çıkarır. `GetMessage`' İ çağırdığınızda bir kuyruktaki sonraki iletiyi alırsınız. Öğesinden döndürülen bir ileti, `GetMessage` Bu kuyruktan gelen diğer kod okuma iletileri için görünmez hale gelir. Varsayılan olarak bu ileti 30 saniye görünmez kalır. İletiyi kuyruktan kaldırma işleminin tamamlanabilmesi için, öğesini de çağırmanız gerekir `DeleteMessage` . Bir iletinin iki adımlı kaldırılma süreci, donanım veya yazılım arızasından dolayı kodunuzun bir iletiyi işleyememesi durumunda kodunuzun başka bir örneğinin aynı iletiyi alıp yeniden denemesini sağlar. `DeleteMessage`İleti işlendikten sonra kodunuz doğru şekilde çağırır.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L75-L76)]

## <a name="use-async-workflows-with-common-queue-storage-apis"></a>Ortak kuyruk depolama API 'Leri ile zaman uyumsuz iş akışları kullanma

Bu örnek, genel sıra depolama API 'Leri ile zaman uyumsuz bir iş akışının nasıl kullanılacağını gösterir.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L82-L91)]

## <a name="additional-options-for-de-queuing-messages"></a>İletileri serbest bırakma için ek seçenekler

İletilerin bir kuyruktan alınma şeklini iki yöntemle özelleştirebilirsiniz.
İlk olarak toplu iletiler alabilirsiniz (en fazla 32). İkinci olarak daha uzun veya daha kısa bir görünmezlik süresi ayarlayarak kodunuzun her iletiyi tamamen işlemesi için daha az veya daha fazla zaman tanıyabilirsiniz. Aşağıdaki kod örneği, `GetMessages` bir çağrıda 20 ileti almak için kullanır ve ardından her iletiyi işler. Ayrıca her ileti için görünmezlik zaman aşımı beş dakika olarak ayarlanır. 5 dakikalık tüm iletiler için aynı anda başlayacağını unutmayın. bu nedenle, çağrısından bu yana 5 dakika geçtikten sonra `GetMessages` , silinmemiş olan tüm iletiler yeniden görünür hale gelir.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L97-L99)]

## <a name="get-the-queue-length"></a>Kuyruk uzunluğu alma

Bir kuyruktaki ileti sayısı ile ilgili bir tahmin alabilirsiniz. `FetchAttributes`Yöntemi, ileti sayısı dahil olmak üzere kuyruk hizmeti kuyruk özniteliklerini almayı ister. `ApproximateMessageCount`Özelliği, kuyruk hizmeti çağrılmadan yöntemi tarafından alınan son değeri döndürür `FetchAttributes` .

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L105-L106)]

## <a name="delete-a-queue"></a>Bir kuyruk silme

Bir kuyruğu ve içerdiği tüm iletileri silmek için, `Delete` kuyruk nesnesi üzerinde yöntemini çağırın.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L112-L113)]

## <a name="next-steps"></a>Sonraki adımlar

Kuyruk depolamanın temellerini öğrendiğinize göre, daha karmaşık depolama görevleri hakkında daha fazla bilgi edinmek için bu bağlantıları takip edin:

- [.NET için Azure Depolama API'leri](/dotnet/api/overview/azure/storage)
- [Azure depolama türü sağlayıcısı](https://github.com/fsprojects/AzureStorageTypeProvider)
- [Azure Depolama Ekibi Blogu](/archive/blogs/windowsazurestorage/)
- [Azure depolama bağlantı dizelerini yapılandırma](/azure/storage/common/storage-configure-connection-string)
- [Azure Depolama Hizmeti REST API Başvurusu](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)
