---
title: F# kullanarak Azure Kuyruk depolama kullanmaya başlama
description: Azure kuyrukları, uygulama bileşenleri arasında güvenilir ve zaman uyumsuz mesajlaşma sağlar. Bulut mesajlaşma, uygulama bileşenlerinizin bağımsız olarak ölçeklendirilmesini sağlar.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: a09cbdd4b995e34177c110ce91b02162bb19dfa8
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423854"
---
# <a name="get-started-with-azure-queue-storage-using-f"></a>F\# kullanarak Azure kuyruk depolama ile çalışmaya başlama

Azure kuyruk depolama, uygulama bileşenleri arasında bulut mesajlaşmasını sağlar. Uygulamaları ölçeklendirmek için tasarlarken, uygulama bileşenleri genellikle birbirinden bağımsız olarak ölçeklendirilebilecek şekilde ayrılır. Kuyruk depolama, bulutta, masaüstünde, şirket içi sunucuda veya mobil cihazda çalışan uygulama bileşenleri arasındaki iletişim için zaman uyumsuz mesajlaşma sağlar. Kuyruk depolama Ayrıca zaman uyumsuz görevlerin yönetilmesini ve işlem iş akışlarının oluşturulmasını destekler.

### <a name="about-this-tutorial"></a>Bu öğretici hakkında

Bu öğreticide, Azure kuyruk F# depolama kullanarak bazı yaygın görevler için nasıl kod yazacağınız gösterilmektedir. Kapsanan görevler kuyruk oluşturma ve silme ve sıra iletilerini ekleme, okuma ve silme işlemleri içerir.

Kuyruk depolamaya kavramsal bir genel bakış için lütfen [kuyruk depolaması için .net kılavuzuna](/azure/storage/storage-dotnet-how-to-use-queues)bakın.

## <a name="prerequisites"></a>Prerequisites

Bu kılavuzu kullanmak için önce [bir Azure depolama hesabı oluşturmanız](/azure/storage/storage-create-storage-account)gerekir.
Ayrıca, bu hesap için depolama erişim anahtarınız gerekecektir.

## <a name="create-an-f-script-and-start-f-interactive"></a>F# Betik oluşturma ve etkileşimli başlatma F#

Bu makaledeki örnekler, bir F# uygulama ya da bir F# komut dosyasında kullanılabilir. F# Betik oluşturmak için, F# geliştirme ortamınızda `.fsx` uzantılı bir dosya oluşturun (örneğin `queues.fsx`).

Ardından, bir `#r` yönergesini kullanarak `WindowsAzure.Storage` paketini ve betiğe `WindowsAzure.Storage.dll` ' ü yüklemek için, paket veya [NuGet](https://www.nuget.org/) [gibi bir](https://fsprojects.github.io/Paket/) [Paket Yöneticisi](package-management.md) kullanın.

### <a name="add-namespace-declarations"></a>Ad alanı bildirimleri ekle

Aşağıdaki `open` deyimlerini `queues.fsx` dosyasının üst kısmına ekleyin:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L1-L3)]

### <a name="get-your-connection-string"></a>Bağlantı dizenizi alın

Bu öğretici için bir Azure depolama bağlantı dizesi gerekir. Bağlantı dizeleri hakkında daha fazla bilgi için bkz. [depolama bağlantı dizelerini yapılandırma](/azure/storage/storage-configure-connection-string).

Öğreticide, aşağıdaki gibi, komut dosyası için Bağlantı dizenizi girersiniz:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L9-L9)]

Ancak, bu gerçek projeler için **önerilmez** . Depolama hesabı anahtarınız, depolama hesabınızın kök parolasıyla benzerdir. Depolama hesabı anahtarınızı korumak için her zaman dikkatli olun. Diğer kullanıcılara dağıtmaktan, sabit kodlamasına veya başkalarının erişebileceği bir düz metin dosyasına kaydetmekten kaçının. Güvenliğinin tehlikede olduğunu düşünüyorsanız, Azure portalını kullanarak anahtarınızı yeniden oluşturabilirsiniz.

Gerçek uygulamalar için, depolama Bağlantı dizenizi korumak için en iyi yol bir yapılandırma dosyasıdır. Bağlantı dizesini bir yapılandırma dosyasından getirmek için şunu yapabilirsiniz:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L11-L13)]

Azure Configuration Manager kullanmak isteğe bağlıdır. .NET Framework `ConfigurationManager` türü gibi bir API de kullanabilirsiniz.

### <a name="parse-the-connection-string"></a>Bağlantı dizesini Ayrıştır

Bağlantı dizesini ayrıştırmak için şunu kullanın:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L19-L20)]

Bu, bir `CloudStorageAccount`döndürür.

### <a name="create-the-queue-service-client"></a>Kuyruk hizmeti istemcisini oluşturma

`CloudQueueClient` sınıfı, kuyruk depolamada depolanan kuyrukları almanızı sağlar. Hizmet istemcisini oluşturmak için bir yol aşağıda verilmiştir:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L26-L26)]

Artık veri okuyan ve kuyruk depolamaya veri yazan kodu yazmaya hazırsınız.

## <a name="create-a-queue"></a>Sıra oluşturma

Bu örnek, zaten yoksa bir sıranın nasıl oluşturulacağını gösterir:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L32-L36)]

## <a name="insert-a-message-into-a-queue"></a>Bir kuyruğa ileti ekleme

Mevcut bir sıraya bir ileti eklemek için, önce yeni bir `CloudQueueMessage`oluşturun. Sonra `AddMessage` yöntemini çağırın. Bir `CloudQueueMessage`, bir dizeden (UTF-8 biçiminde) ya da bir `byte` dizisinden oluşturulabilir, örneğin:

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L42-L44)]

## <a name="peek-at-the-next-message"></a>Sonraki iletiye göz atın

`PeekMessage` yöntemini çağırarak bir kuyruğun önündeki iletiye göz atırsınız ve bunu kuyruktan kaldırabilirsiniz.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L50-L52)]

## <a name="get-the-next-message-for-processing"></a>İşleme için bir sonraki iletiyi alın

`GetMessage` yöntemini çağırarak, işlenmek üzere kuyruğun önündeki iletiyi alabilirsiniz.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L58-L59)]

Daha sonra `DeleteMessage`kullanarak iletinin başarıyla işlenmesini belirtirsiniz.

## <a name="change-the-contents-of-a-queued-message"></a>Sıraya alınan iletinin içeriğini değiştirme

Alınan bir iletinin içeriğini kuyrukta yerinde değiştirebilirsiniz. İleti bir iş görevini temsil ediyorsa, iş görevinin durumunu güncelleştirmek için bu özelliği kullanabilirsiniz. Aşağıdaki kod, kuyruk iletisini yeni içerikle güncelleştirir ve görünürlük zaman aşımını başka bir 60 saniye uzatmak üzere ayarlar. Bu, iletiyle ilişkili çalışmanın durumunu kaydeder ve istemciye ileti üzerinde çalışmaya devam etmesi için başka bir dakika verir. Bu tekniği, işlem adımı donanım veya yazılım arızası nedeniyle başarısız olursa baştan başlamak zorunda kalmadan, kuyruk iletilerinde çok adımlı iş akışlarını izlemek için kullanabilirsiniz. Genellikle bir yeniden deneme sayısı da olur ve ileti birkaç kez yeniden denense de onu silersiniz. Bu, her işlendiği zaman bir uygulama hatasını tetikleyen bir iletiye karşı koruma sağlar.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L65-L69)]

## <a name="de-queue-the-next-message"></a>Sonraki iletiyi kuyruktan kaldır

Kodunuz, iki adımda bir kuyruktan bir ileti de sıralar. `GetMessage`çağırdığınızda sıradaki bir sonraki iletiyi alırsınız. `GetMessage` döndürülen bir ileti, bu kuyruktan gelen diğer kod okuma iletileri için görünmez hale gelir. Bu ileti, varsayılan olarak 30 saniye boyunca görünmez kalır. İletiyi kuyruktan kaldırma işleminin tamamlanabilmesi için, `DeleteMessage`de çağırmanız gerekir. Bir iletiyi kaldırmanın bu iki adımlı işlemi, kodunuz, donanım veya yazılım arızasından kaynaklanan bir iletiyi işleyemediğinde, kodunuzun başka bir örneğinin aynı mesajı almasını ve yeniden denemesini sağlar. İleti işlendikten sonra kodunuz `DeleteMessage` çağırır.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L75-L76)]

## <a name="use-async-workflows-with-common-queue-storage-apis"></a>Ortak kuyruk depolama API 'Leri ile zaman uyumsuz iş akışları kullanma

Bu örnek, genel sıra depolama API 'Leri ile zaman uyumsuz bir iş akışının nasıl kullanılacağını gösterir.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L82-L91)]

## <a name="additional-options-for-de-queuing-messages"></a>İletileri serbest bırakma için ek seçenekler

İleti alımı bir kuyruktan özelleştirmek için kullanabileceğiniz iki yol vardır.
İlk olarak, bir toplu ileti alabilirsiniz (en fazla 32). İkincisi, daha uzun veya daha kısa bir zaman aşımı ayarlayabilir, böylece her iletiyi tamamen işlemek için kodunuzun daha fazla veya daha az zaman aşımına uğramamasını sağlayabilirsiniz. Aşağıdaki kod örneği, tek bir çağrıda 20 ileti almak için `GetMessages` kullanır ve ardından her iletiyi işler. Ayrıca, her ileti için geçersiz kılma zaman aşımını beş dakikaya ayarlar. 5 dakikalık tüm iletiler için aynı anda başlayacağını unutmayın. bu nedenle, `GetMessages`çağrısından bu yana 5 dakika geçtikten sonra, silinmemiş olan tüm iletiler yeniden görünür hale gelir.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L97-L99)]

## <a name="get-the-queue-length"></a>Sıra uzunluğunu al

Kuyruktaki ileti sayısını tahmin edebilirsiniz. `FetchAttributes` yöntemi, ileti sayısı dahil olmak üzere Kuyruk hizmeti kuyruk özniteliklerini almayı ister. `ApproximateMessageCount` özelliği, Kuyruk hizmeti çağrılmadan `FetchAttributes` yöntemi tarafından alınan son değeri döndürür.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L105-L106)]

## <a name="delete-a-queue"></a>Kuyruğu silme

Bir kuyruğu ve içerdiği tüm iletileri silmek için, kuyruk nesnesi üzerinde `Delete` yöntemi çağırın.

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L112-L113)]

## <a name="next-steps"></a>Sonraki adımlar

Sıra depolamanın temellerini öğrendiğinize göre, daha karmaşık depolama görevleri hakkında bilgi edinmek için bu bağlantıları izleyin.

- [.NET için Azure depolama API 'Leri](/dotnet/api/overview/azure/storage)
- [Azure depolama türü sağlayıcısı](https://github.com/fsprojects/AzureStorageTypeProvider)
- [Azure depolama ekibi blogu](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [Azure depolama bağlantı dizelerini yapılandırma](/azure/storage/common/storage-configure-connection-string)
- [Azure depolama hizmetleri REST API başvurusu](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)
