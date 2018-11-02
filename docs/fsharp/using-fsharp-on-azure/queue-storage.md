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
# <a name="get-started-with-azure-queue-storage-using-f"></a><span data-ttu-id="cc6ec-104">F # kullanarak Azure kuyruk depolama ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="cc6ec-104">Get started with Azure Queue storage using F#</span></span> #

<span data-ttu-id="cc6ec-105">Azure kuyruk depolama, uygulama bileşenleri arasında bulut Mesajlaşma sağlar.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-105">Azure Queue storage provides cloud messaging between application components.</span></span> <span data-ttu-id="cc6ec-106">Böylece ölçeklendirilebilmeleri ölçek için uygulamaları tasarlarken, uygulama bileşenleri genellikle birbirinden ayrılır.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-106">In designing applications for scale, application components are often decoupled, so that they can scale independently.</span></span> <span data-ttu-id="cc6ec-107">Kuyruk depolama, bulutta, masaüstünde, şirket içi sunucusunda veya mobil bir cihazda çalışan uygulama bileşenleri arasındaki iletişim için zaman uyumsuz Mesajlaşma sunar.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-107">Queue storage delivers asynchronous messaging for communication between application components, whether they are running in the cloud, on the desktop, on an on-premises server, or on a mobile device.</span></span> <span data-ttu-id="cc6ec-108">Kuyruk depolama ayrıca zaman uyumsuz görevlerin yönetilmesini ve süreç iş akışlarının oluşturulmasını destekler.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-108">Queue storage also supports managing asynchronous tasks and building process work flows.</span></span>

### <a name="about-this-tutorial"></a><span data-ttu-id="cc6ec-109">Bu eğitim hakkında</span><span class="sxs-lookup"><span data-stu-id="cc6ec-109">About this tutorial</span></span>

<span data-ttu-id="cc6ec-110">Bu öğreticide nasıl yazılacağını göstermektedir F# Azure kuyruk depolama kullanarak bazı ortak görevler için kod.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-110">This tutorial shows how to write F# code for some common tasks using Azure Queue storage.</span></span> <span data-ttu-id="cc6ec-111">Kapsanan görevler oluşturma ve kuyrukları silme ve ekleme, okuma ve silme kuyruk iletileri içerir.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-111">Tasks covered include creating and deleting queues and adding, reading, and deleting queue messages.</span></span>

<span data-ttu-id="cc6ec-112">Kuyruk depolama kavramsal bir genel bakış için bkz. Lütfen [kuyruk depolama için .NET Kılavuzu](/azure/storage/storage-dotnet-how-to-use-queues).</span><span class="sxs-lookup"><span data-stu-id="cc6ec-112">For a conceptual overview of queue storage, please see [the .NET guide for queue storage](/azure/storage/storage-dotnet-how-to-use-queues).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cc6ec-113">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="cc6ec-113">Prerequisites</span></span>

<span data-ttu-id="cc6ec-114">Bu kılavuzu kullanmak için önce [bir Azure depolama hesabı oluşturma](/azure/storage/storage-create-storage-account).</span><span class="sxs-lookup"><span data-stu-id="cc6ec-114">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span>
<span data-ttu-id="cc6ec-115">Ayrıca, bu hesap için depolama erişim anahtarınızı gerekir.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-115">You'll also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="cc6ec-116">Bir F # komut dosyası ve başlangıç F # Etkileşimli oluşturma</span><span class="sxs-lookup"><span data-stu-id="cc6ec-116">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="cc6ec-117">Bu makaledeki örnekleri, F # uygulaması veya bir F # komut dosyası kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-117">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="cc6ec-118">Bir F # komut dosyası oluşturmak için bir dosya oluşturun. `.fsx` uzantısı, örneğin `queues.fsx`, F # geliştirme ortamınızda.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-118">To create an F# script, create a file with the `.fsx` extension, for example `queues.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="cc6ec-119">Ardından, bir [Paket Yöneticisi](package-management.md) gibi [Paket](https://fsprojects.github.io/Paket/) veya [NuGet](https://www.nuget.org/) yüklemek için `WindowsAzure.Storage` paket ve başvuru `WindowsAzure.Storage.dll` bir kullanarakbetiğinizde`#r`yönergesi.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-119">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="cc6ec-120">Ad alanı bildirimleri ekleme</span><span class="sxs-lookup"><span data-stu-id="cc6ec-120">Add namespace declarations</span></span>

<span data-ttu-id="cc6ec-121">Aşağıdaki `open` üst tarafına deyimlerini `queues.fsx` dosyası:</span><span class="sxs-lookup"><span data-stu-id="cc6ec-121">Add the following `open` statements to the top of the `queues.fsx` file:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L1-L3)]

### <a name="get-your-connection-string"></a><span data-ttu-id="cc6ec-122">Bağlantı dizenizi alma</span><span class="sxs-lookup"><span data-stu-id="cc6ec-122">Get your connection string</span></span>

<span data-ttu-id="cc6ec-123">Bu öğreticide bir Azure depolama bağlantı dizesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-123">You'll need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="cc6ec-124">Bağlantı dizeleri hakkında daha fazla bilgi için bkz. [depolama bağlantı dizelerini yapılandırma](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="cc6ec-124">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="cc6ec-125">Öğretici için şunun gibi komut dosyanızdaki bağlantı dizenizi girmenizi isteriz:</span><span class="sxs-lookup"><span data-stu-id="cc6ec-125">For the tutorial, you'll enter your connection string in your script, like this:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L9-L9)]

<span data-ttu-id="cc6ec-126">Ancak, bu, **önerilmez** gerçek projeleri.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-126">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="cc6ec-127">Depolama hesabı anahtarınız depolama hesabınızın kök parolasına benzer.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-127">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="cc6ec-128">Her zaman depolama hesabı anahtarınızı korumak dikkatli olun.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-128">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="cc6ec-129">Sabit kodlama veya başkalarının erişebileceği bir düz metin dosyasına kaydederek diğer kullanıcılara dağıtmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-129">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="cc6ec-130">Tehlikeye girmiş olabilecek düşünüyorsanız Azure portalını kullanarak anahtarınızı yeniden oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-130">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="cc6ec-131">Gerçek uygulamalar, depolama bağlantı dizenizi korumak için en iyi yolu, içinde bir yapılandırma dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-131">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="cc6ec-132">Bir yapılandırma dosyasından bağlantı dizesini getirmek için bunu yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="cc6ec-132">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L11-L13)]

<span data-ttu-id="cc6ec-133">Azure Yapılandırma Yöneticisi'ni kullanmak isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-133">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="cc6ec-134">.NET Framework'ün gibi bir API de kullanabilirsiniz `ConfigurationManager` türü.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-134">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="cc6ec-135">Bağlantı dizesini ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="cc6ec-135">Parse the connection string</span></span>

<span data-ttu-id="cc6ec-136">Bağlantı dizesini ayrıştırmak için kullanın:</span><span class="sxs-lookup"><span data-stu-id="cc6ec-136">To parse the connection string, use:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L19-L20)]

<span data-ttu-id="cc6ec-137">Bu döndürür bir `CloudStorageAccount`.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-137">This will return a `CloudStorageAccount`.</span></span>

### <a name="create-the-queue-service-client"></a><span data-ttu-id="cc6ec-138">Kuyruk hizmeti istemcisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="cc6ec-138">Create the Queue service client</span></span>

<span data-ttu-id="cc6ec-139">`CloudQueueClient` Sınıfı, kuyruk depolamada depolanan kuyrukları almanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-139">The `CloudQueueClient` class enables you to retrieve queues stored in Queue storage.</span></span> <span data-ttu-id="cc6ec-140">Hizmet istemcisini oluşturma yöntemlerinden biri aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="cc6ec-140">Here's one way to create the service client:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L26-L26)]

<span data-ttu-id="cc6ec-141">Artık, verileri okur ve kuyruk depolamaya veri yazan kodu yazmaya hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-141">Now you are ready to write code that reads data from and writes data to Queue storage.</span></span>

## <a name="create-a-queue"></a><span data-ttu-id="cc6ec-142">Kuyruk oluşturma</span><span class="sxs-lookup"><span data-stu-id="cc6ec-142">Create a queue</span></span>

<span data-ttu-id="cc6ec-143">Bu örnek, zaten yoksa bir kuyruk oluşturulacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="cc6ec-143">This example shows how to create a queue if it doesn't already exist:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L32-L36)]

## <a name="insert-a-message-into-a-queue"></a><span data-ttu-id="cc6ec-144">Kuyruğa bir ileti Ekle</span><span class="sxs-lookup"><span data-stu-id="cc6ec-144">Insert a message into a queue</span></span>

<span data-ttu-id="cc6ec-145">Varolan bir kuyruğa ileti eklemek için ilk olarak yeni bir oluşturma `CloudQueueMessage`.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-145">To insert a message into an existing queue, first create a new `CloudQueueMessage`.</span></span> <span data-ttu-id="cc6ec-146">Ardından, arama `AddMessage` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-146">Next, call the `AddMessage` method.</span></span> <span data-ttu-id="cc6ec-147">A `CloudQueueMessage` herhangi birinden bir dize (UTF-8 biçiminde) oluşturulabilir veya `byte` şunun gibi bir dizi:</span><span class="sxs-lookup"><span data-stu-id="cc6ec-147">A `CloudQueueMessage` can be created from either a string (in UTF-8 format) or a `byte` array, like this:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L42-L44)]

## <a name="peek-at-the-next-message"></a><span data-ttu-id="cc6ec-148">Sonraki iletiye gözatın</span><span class="sxs-lookup"><span data-stu-id="cc6ec-148">Peek at the next message</span></span>

<span data-ttu-id="cc6ec-149">Kuyruğun, iletiyi kuyruktan kaldırmadan çağırarak peek `PeekMessage` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-149">You can peek at the message in the front of a queue, without removing it from the queue, by calling the `PeekMessage` method.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L50-L52)]

## <a name="get-the-next-message-for-processing"></a><span data-ttu-id="cc6ec-150">İşleme için sonraki iletiyi Al</span><span class="sxs-lookup"><span data-stu-id="cc6ec-150">Get the next message for processing</span></span>

<span data-ttu-id="cc6ec-151">İleti işleme için bir kuyruğun önündeki çağırarak alabilirsiniz `GetMessage` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-151">You can retrieve the message at the front of a queue for processing by calling the `GetMessage` method.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L58-L59)]

<span data-ttu-id="cc6ec-152">Daha sonra kullanarak iletinin başarılı işleme belirtmek `DeleteMessage`.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-152">You later indicate successful processing of the message by using `DeleteMessage`.</span></span>

## <a name="change-the-contents-of-a-queued-message"></a><span data-ttu-id="cc6ec-153">Kuyruğa Alınan iletinin içeriğini değiştirme</span><span class="sxs-lookup"><span data-stu-id="cc6ec-153">Change the contents of a queued message</span></span>

<span data-ttu-id="cc6ec-154">Bir alınan ileti yerinde sırasındaki içeriğini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-154">You can change the contents of a retrieved message in-place in the queue.</span></span> <span data-ttu-id="cc6ec-155">İleti bir iş görevini temsil ediyorsa, kullanarak iş görevinin durumunu güncelleştirmek için bu özelliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-155">If the message represents a work task, you could use this feature to update the status of the work task.</span></span> <span data-ttu-id="cc6ec-156">Aşağıdaki kod kuyruk iletisini yeni içeriklerle güncelleştirir ve görünürlük zaman aşımını 60 saniye daha uzatır.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-156">The following code updates the queue message with new contents, and sets the visibility timeout to extend another 60 seconds.</span></span> <span data-ttu-id="cc6ec-157">Bu iletiyle ilişkili işin durumunu kaydeder ve istemciye ileti üzerinde çalışmaya devam etmek için bir dakika daha zaman verir.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-157">This saves the state of work associated with the message, and gives the client another minute to continue working on the message.</span></span> <span data-ttu-id="cc6ec-158">Üzerinden bir işleme adımı donanım veya yazılım arızasından dolayı başarısız olursa baştan başlamanıza gerek kalmadan kuyruk çok adımlı iş akışlarını izlemek için bu tekniği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-158">You could use this technique to track multi-step workflows on queue messages, without having to start over from the beginning if a processing step fails due to hardware or software failure.</span></span> <span data-ttu-id="cc6ec-159">Genellikle bir yeniden deneme sayısı yanı tutacak ve ileti en fazla kaç kez denenirse silmeniz.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-159">Typically, you would keep a retry count as well, and if the message is retried more than some number of times, you would delete it.</span></span> <span data-ttu-id="cc6ec-160">Bu, her işlendiğinde bir uygulama hatası tetikleyen bir iletiye karşı koruma sağlar.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-160">This protects against a message that triggers an application error each time it is processed.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L65-L69)]

## <a name="de-queue-the-next-message"></a><span data-ttu-id="cc6ec-161">Sonraki iletiyi sıradan çıkarmak</span><span class="sxs-lookup"><span data-stu-id="cc6ec-161">De-queue the next message</span></span>

<span data-ttu-id="cc6ec-162">Kodunuzun bir iletiyi bir kuyruktan iki adımda kuyruktan.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-162">Your code de-queues a message from a queue in two steps.</span></span> <span data-ttu-id="cc6ec-163">Çağırdığınızda `GetMessage`, sonraki iletiyi bir kuyruğa alın.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-163">When you call `GetMessage`, you get the next message in a queue.</span></span> <span data-ttu-id="cc6ec-164">Öğesinden döndürülen bir ileti `GetMessage` bu kuyruktan iletileri okuyan herhangi bir kod için görünmez hale gelir.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-164">A message returned from `GetMessage` becomes invisible to any other code reading messages from this queue.</span></span> <span data-ttu-id="cc6ec-165">Varsayılan olarak, bu ileti 30 saniye görünmez kalır.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-165">By default, this message stays invisible for 30 seconds.</span></span> <span data-ttu-id="cc6ec-166">İletiyi kuyruktan kaldırmayı tamamlamak için de çağırmanız gerekir `DeleteMessage`.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-166">To finish removing the message from the queue, you must also call `DeleteMessage`.</span></span> <span data-ttu-id="cc6ec-167">Kodunuzun bir iletiyi donanım veya yazılım hatası nedeniyle başarısız olursa, kodunuzun başka bir örneği aynı iletiyi alıp yeniden deneyin, bu iki adımlı işlem, bir iletinin sağlar.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-167">This two-step process of removing a message assures that if your code fails to process a message due to hardware or software failure, another instance of your code can get the same message and try again.</span></span> <span data-ttu-id="cc6ec-168">Kod çağrılarınızı `DeleteMessage` ileti işlendikten sonra sağ.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-168">Your code calls `DeleteMessage` right after the message has been processed.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L75-L76)]

## <a name="use-async-workflows-with-common-queue-storage-apis"></a><span data-ttu-id="cc6ec-169">Genel kuyruk depolama API'leri ile zaman uyumsuz iş akışları kullanın</span><span class="sxs-lookup"><span data-stu-id="cc6ec-169">Use Async workflows with common Queue storage APIs</span></span>

<span data-ttu-id="cc6ec-170">Bu örnek, genel kuyruk depolama API'leri ile zaman uyumsuz bir iş akışı kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-170">This example shows how to use an async workflow with common Queue storage APIs.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L82-L91)]

## <a name="additional-options-for-de-queuing-messages"></a><span data-ttu-id="cc6ec-171">İletilerin kuyruktan çıkarılması için ek seçenekler</span><span class="sxs-lookup"><span data-stu-id="cc6ec-171">Additional options for de-queuing messages</span></span>

<span data-ttu-id="cc6ec-172">Bir kuyruktan ileti alma özelleştirebilirsiniz iki yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-172">There are two ways you can customize message retrieval from a queue.</span></span>
<span data-ttu-id="cc6ec-173">İlk olarak toplu iletiler (en fazla 32) elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-173">First, you can get a batch of messages (up to 32).</span></span> <span data-ttu-id="cc6ec-174">İkinci olarak, daha uzun veya daha kısa bir görünmezlik zaman aşımı, kodunuzun daha fazla veya daha az zaman her iletiyi tamamen işlemesi için izin ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-174">Second, you can set a longer or shorter invisibility timeout, allowing your code more or less time to fully process each message.</span></span> <span data-ttu-id="cc6ec-175">Aşağıdaki kod örneğinde `GetMessages` 20 almak için bir ileti çağırın ve ardından her ileti işler.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-175">The following code example uses `GetMessages` to get 20 messages in one call and then processes each message.</span></span> <span data-ttu-id="cc6ec-176">Beş dakika her ileti için görünmezlik zaman aşımı da ayarlar.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-176">It also sets the invisibility timeout to five minutes for each message.</span></span> <span data-ttu-id="cc6ec-177">Bu nedenle sonra 5 dakika 5 dakika için tüm iletiler aynı anda başlatır Not geçirilen çağrısından sonra `GetMessages`, silinmeyen tüm iletiler yeniden görünür hale gelir.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-177">Note that the 5 minutes starts for all messages at the same time, so after 5 minutes have passed since the call to `GetMessages`, any messages which have not been deleted will become visible again.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L97-L99)]

## <a name="get-the-queue-length"></a><span data-ttu-id="cc6ec-178">Kuyruk uzunluğu alma</span><span class="sxs-lookup"><span data-stu-id="cc6ec-178">Get the queue length</span></span>

<span data-ttu-id="cc6ec-179">Kuyrukta ileti sayısını tahmini elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-179">You can get an estimate of the number of messages in a queue.</span></span> <span data-ttu-id="cc6ec-180">`FetchAttributes` Yöntemi kuyruk hizmetinin ileti sayısı dahil olmak üzere kuyruk özniteliklerini almasını ister.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-180">The `FetchAttributes` method asks the Queue service to retrieve the queue attributes, including the message count.</span></span> <span data-ttu-id="cc6ec-181">`ApproximateMessageCount` Özelliği tarafından alınan en son değeri döndürür `FetchAttributes` kuyruk hizmetini çağırmadan olmadan yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-181">The `ApproximateMessageCount` property returns the last value retrieved by the `FetchAttributes` method, without calling the Queue service.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L105-L106)]

## <a name="delete-a-queue"></a><span data-ttu-id="cc6ec-182">Bir kuyruk silme</span><span class="sxs-lookup"><span data-stu-id="cc6ec-182">Delete a queue</span></span>

<span data-ttu-id="cc6ec-183">Bir kuyruk ve içerdiği tüm iletileri silmek için çağrı `Delete` kuyruk nesnesi üzerinde yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-183">To delete a queue and all the messages contained in it, call the `Delete` method on the queue object.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L112-L113)]

## <a name="next-steps"></a><span data-ttu-id="cc6ec-184">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="cc6ec-184">Next steps</span></span>

<span data-ttu-id="cc6ec-185">Kuyruk depolamanın temellerini öğrendiğinize göre daha karmaşık depolama görevleri hakkında bilgi edinmek için bu bağlantıları izleyin.</span><span class="sxs-lookup"><span data-stu-id="cc6ec-185">Now that you've learned the basics of Queue storage, follow these links to learn about more complex storage tasks.</span></span>

- [<span data-ttu-id="cc6ec-186">.NET için Azure depolama API'leri</span><span class="sxs-lookup"><span data-stu-id="cc6ec-186">Azure Storage APIs for .NET</span></span>](/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="cc6ec-187">Azure depolama tür sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="cc6ec-187">Azure Storage Type Provider</span></span>](https://github.com/fsprojects/AzureStorageTypeProvider)
- [<span data-ttu-id="cc6ec-188">Azure depolama ekibi blogu</span><span class="sxs-lookup"><span data-stu-id="cc6ec-188">Azure Storage Team Blog</span></span>](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [<span data-ttu-id="cc6ec-189">Azure Storage bağlantı dizelerini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="cc6ec-189">Configure Azure Storage connection strings</span></span>](/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="cc6ec-190">Azure depolama hizmetleri REST API Başvurusu</span><span class="sxs-lookup"><span data-stu-id="cc6ec-190">Azure Storage Services REST API Reference</span></span>](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)
