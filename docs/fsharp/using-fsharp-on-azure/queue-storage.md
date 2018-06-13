---
title: 'F # kullanarak Azure kuyruk depolamaya başlayın'
description: Uygulama bileşenleri arasında güvenilir ve zaman uyumsuz Mesajlaşma Azure kuyrukları sağlar. İleti etkinleştirir bağımsız olarak ölçeklendirebilirsiniz uygulama bileşenlerinizin bulut.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 14bbc657f965fc262d2a83b1fdf982fe5e75d55e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569424"
---
# <a name="get-started-with-azure-queue-storage-using-f"></a><span data-ttu-id="45245-104">F # kullanarak Azure kuyruk depolamaya başlayın</span><span class="sxs-lookup"><span data-stu-id="45245-104">Get started with Azure Queue storage using F#</span></span> #

<span data-ttu-id="45245-105">Azure kuyruk depolama uygulama bileşenleri arasında Mesajlaşma bulut sağlar.</span><span class="sxs-lookup"><span data-stu-id="45245-105">Azure Queue storage provides cloud messaging between application components.</span></span> <span data-ttu-id="45245-106">Böylece bağımsız olarak ölçeklendirebilirsiniz uygulamalar için ölçek tasarlarken, uygulama bileşenleri genellikle birbirinden ayrılır.</span><span class="sxs-lookup"><span data-stu-id="45245-106">In designing applications for scale, application components are often decoupled, so that they can scale independently.</span></span> <span data-ttu-id="45245-107">Bulutta, masaüstünde, bir şirket içi sunucu veya bir mobil cihaz çalıştırıp çalıştırmadığınızı uygulama bileşenleri arasında iletişim için zaman uyumsuz Mesajlaşma kuyruk depolama sunar.</span><span class="sxs-lookup"><span data-stu-id="45245-107">Queue storage delivers asynchronous messaging for communication between application components, whether they are running in the cloud, on the desktop, on an on-premises server, or on a mobile device.</span></span> <span data-ttu-id="45245-108">Kuyruk depolama ayrıca zaman uyumsuz görevlerin yönetilmesini ve süreç iş akışlarının oluşturulmasını destekler.</span><span class="sxs-lookup"><span data-stu-id="45245-108">Queue storage also supports managing asynchronous tasks and building process work flows.</span></span>

### <a name="about-this-tutorial"></a><span data-ttu-id="45245-109">Bu öğretici hakkında</span><span class="sxs-lookup"><span data-stu-id="45245-109">About this tutorial</span></span>

<span data-ttu-id="45245-110">Bu öğretici Azure kuyruk depolama kullanarak bazı ortak görevler için F # kodunun nasıl yazılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="45245-110">This tutorial shows how to write F# code for some common tasks using Azure Queue storage.</span></span> <span data-ttu-id="45245-111">Kapsanan görevler oluşturma ve silme ve ekleme, okuma ve iletileri kuyruğa silme içerir.</span><span class="sxs-lookup"><span data-stu-id="45245-111">Tasks covered include creating and deleting queues and adding, reading, and deleting queue messages.</span></span>

<span data-ttu-id="45245-112">Kuyruk depolama kavramsal bir genel bakış için lütfen bkz [kuyruk depolama için .NET Kılavuzu](/azure/storage/storage-dotnet-how-to-use-queues).</span><span class="sxs-lookup"><span data-stu-id="45245-112">For a conceptual overview of queue storage, please see [the .NET guide for queue storage](/azure/storage/storage-dotnet-how-to-use-queues).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="45245-113">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="45245-113">Prerequisites</span></span>

<span data-ttu-id="45245-114">Bu kılavuzu kullanmak için öncelikle [bir Azure depolama hesabı oluşturma](/azure/storage/storage-create-storage-account).</span><span class="sxs-lookup"><span data-stu-id="45245-114">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span>
<span data-ttu-id="45245-115">Bu hesap için depolama erişim anahtarınızı de gerekir.</span><span class="sxs-lookup"><span data-stu-id="45245-115">You'll also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="45245-116">Bir F # betiği ve başlangıç F # Etkileşimli oluşturma</span><span class="sxs-lookup"><span data-stu-id="45245-116">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="45245-117">Bu makaledeki örnekler, F # uygulaması veya F # betiği kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="45245-117">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="45245-118">F # betiği oluşturmak için dosya oluştur `.fsx` uzantısı, örneğin `queues.fsx`, ortamınızdaki F # geliştirme.</span><span class="sxs-lookup"><span data-stu-id="45245-118">To create an F# script, create a file with the `.fsx` extension, for example `queues.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="45245-119">Ardından, kullanın bir [Paket Yöneticisi](package-management.md) gibi [Paket](https://fsprojects.github.io/Paket/) veya [NuGet](https://www.nuget.org/) yüklemek için `WindowsAzure.Storage` paket ve başvuru `WindowsAzure.Storage.dll` bir kullanarakkomut`#r`yönergesi.</span><span class="sxs-lookup"><span data-stu-id="45245-119">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="45245-120">Ad alanı bildirimleri ekleme</span><span class="sxs-lookup"><span data-stu-id="45245-120">Add namespace declarations</span></span>

<span data-ttu-id="45245-121">Aşağıdakileri ekleyin `open` deyimleri üstüne `queues.fsx` dosyası:</span><span class="sxs-lookup"><span data-stu-id="45245-121">Add the following `open` statements to the top of the `queues.fsx` file:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L1-L3)]

### <a name="get-your-connection-string"></a><span data-ttu-id="45245-122">Bağlantı dizenizi Al</span><span class="sxs-lookup"><span data-stu-id="45245-122">Get your connection string</span></span>

<span data-ttu-id="45245-123">Bu öğretici için bir Azure depolama bağlantı dizesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="45245-123">You'll need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="45245-124">Bağlantı dizeleri hakkında daha fazla bilgi için bkz: [Storage bağlantı dizelerini yapılandırma](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="45245-124">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="45245-125">Öğretici için şuna benzer betiğinizin bağlantı dizenizi girin:</span><span class="sxs-lookup"><span data-stu-id="45245-125">For the tutorial, you'll enter your connection string in your script, like this:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L9-L9)]

<span data-ttu-id="45245-126">Ancak, bu olduğu **önerilmez** için gerçek projeleri.</span><span class="sxs-lookup"><span data-stu-id="45245-126">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="45245-127">Depolama hesabı anahtarınız depolama hesabınızın kök parolasına benzer.</span><span class="sxs-lookup"><span data-stu-id="45245-127">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="45245-128">Her zaman depolama hesabı anahtarınızı korumak dikkatli olun.</span><span class="sxs-lookup"><span data-stu-id="45245-128">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="45245-129">Sabit kodlama veya başkalarının erişebileceği düz metin dosyasına kaydetme diğer kullanıcılara dağıtmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="45245-129">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="45245-130">Bunu tehlikede olduğunu düşünüyorsanız, Azure Portalı'nı kullanarak anahtarınızı yeniden oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="45245-130">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="45245-131">İçin gerçek uygulamalar, depolama bağlantı dizenizi korumak için en iyi yapılandırma dosyasında yoludur.</span><span class="sxs-lookup"><span data-stu-id="45245-131">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="45245-132">Yapılandırma dosyasından bağlantı dizesini almak için bunu yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="45245-132">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L11-L13)]

<span data-ttu-id="45245-133">Azure Yapılandırma Yöneticisi'ni kullanarak isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="45245-133">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="45245-134">.NET Framework'ün gibi bir API de kullanabilirsiniz `ConfigurationManager` türü.</span><span class="sxs-lookup"><span data-stu-id="45245-134">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="45245-135">Bağlantı dizesini ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="45245-135">Parse the connection string</span></span>

<span data-ttu-id="45245-136">Bağlantı dizesini ayrıştırmak için kullanın:</span><span class="sxs-lookup"><span data-stu-id="45245-136">To parse the connection string, use:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L19-L20)]

<span data-ttu-id="45245-137">Bu döndürülecek bir `CloudStorageAccount`.</span><span class="sxs-lookup"><span data-stu-id="45245-137">This will return a `CloudStorageAccount`.</span></span>

### <a name="create-the-queue-service-client"></a><span data-ttu-id="45245-138">Kuyruk hizmeti istemcisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="45245-138">Create the Queue service client</span></span>

<span data-ttu-id="45245-139">`CloudQueueClient` Sınıfı, kuyruk depolamada depolanan kuyrukları almanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="45245-139">The `CloudQueueClient` class enables you to retrieve queues stored in Queue storage.</span></span> <span data-ttu-id="45245-140">Hizmet istemcisini oluşturma yöntemlerinden biri aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="45245-140">Here's one way to create the service client:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L26-L26)]

<span data-ttu-id="45245-141">Şimdi veri okuyan ve kuyruk depolama alanına veri yazan kodu yazmaya hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="45245-141">Now you are ready to write code that reads data from and writes data to Queue storage.</span></span>

## <a name="create-a-queue"></a><span data-ttu-id="45245-142">Bir sıra oluşturun</span><span class="sxs-lookup"><span data-stu-id="45245-142">Create a queue</span></span>

<span data-ttu-id="45245-143">Bu örnek, zaten yoksa bir sıranın nasıl oluşturulacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="45245-143">This example shows how to create a queue if it doesn't already exist:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L32-L36)]

## <a name="insert-a-message-into-a-queue"></a><span data-ttu-id="45245-144">Kuyruğa bir ileti Ekle</span><span class="sxs-lookup"><span data-stu-id="45245-144">Insert a message into a queue</span></span>

<span data-ttu-id="45245-145">Varolan bir sıraya bir ileti eklemek için ilk olarak yeni bir oluşturma `CloudQueueMessage`.</span><span class="sxs-lookup"><span data-stu-id="45245-145">To insert a message into an existing queue, first create a new `CloudQueueMessage`.</span></span> <span data-ttu-id="45245-146">Ardından, çağrı `AddMessage` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="45245-146">Next, call the `AddMessage` method.</span></span> <span data-ttu-id="45245-147">A `CloudQueueMessage` herhangi birinden bir dizeden (UTF-8 biçiminde) oluşturulabilir veya `byte` dizisi şöyle:</span><span class="sxs-lookup"><span data-stu-id="45245-147">A `CloudQueueMessage` can be created from either a string (in UTF-8 format) or a `byte` array, like this:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L42-L44)]

## <a name="peek-at-the-next-message"></a><span data-ttu-id="45245-148">Sonraki iletiye</span><span class="sxs-lookup"><span data-stu-id="45245-148">Peek at the next message</span></span>

<span data-ttu-id="45245-149">Size, kuyruğun önündeki iletiye sıradan çağırarak kaldırmadan iletiye göz atabilirsiniz `PeekMessage` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="45245-149">You can peek at the message in the front of a queue, without removing it from the queue, by calling the `PeekMessage` method.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L50-L52)]

## <a name="get-the-next-message-for-processing"></a><span data-ttu-id="45245-150">İşleme için sonraki ileti alma</span><span class="sxs-lookup"><span data-stu-id="45245-150">Get the next message for processing</span></span>

<span data-ttu-id="45245-151">Çağırarak bir sıra ön işleme için ileti alabilir `GetMessage` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="45245-151">You can retrieve the message at the front of a queue for processing by calling the `GetMessage` method.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L58-L59)]

<span data-ttu-id="45245-152">Daha sonra kullanarak iletinin başarılı işleme belirtmek `DeleteMessage`.</span><span class="sxs-lookup"><span data-stu-id="45245-152">You later indicate successful processing of the message by using `DeleteMessage`.</span></span>

## <a name="change-the-contents-of-a-queued-message"></a><span data-ttu-id="45245-153">Kuyruğa Alınan iletinin içeriğini değiştirme</span><span class="sxs-lookup"><span data-stu-id="45245-153">Change the contents of a queued message</span></span>

<span data-ttu-id="45245-154">Bir alınan ileti yerinde sırasındaki içeriğini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="45245-154">You can change the contents of a retrieved message in-place in the queue.</span></span> <span data-ttu-id="45245-155">İleti bir iş görevini temsil ediyorsa, iş görevinin durumunu güncelleştirmek için bu özelliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="45245-155">If the message represents a work task, you could use this feature to update the status of the work task.</span></span> <span data-ttu-id="45245-156">Aşağıdaki kod kuyruk iletisini yeni içeriklerle güncelleştirir ve görünürlük zaman aşımını 60 saniye daha uzatır.</span><span class="sxs-lookup"><span data-stu-id="45245-156">The following code updates the queue message with new contents, and sets the visibility timeout to extend another 60 seconds.</span></span> <span data-ttu-id="45245-157">Bu ileti ile ilişkili işin durumunu kaydeder ve istemciye ileti üzerinde çalışmaya devam etmek için bir dakika daha zaman verir.</span><span class="sxs-lookup"><span data-stu-id="45245-157">This saves the state of work associated with the message, and gives the client another minute to continue working on the message.</span></span> <span data-ttu-id="45245-158">Üzerinden bir işleme adımı donanım veya yazılım arızasından dolayı başarısız olursa baştan başlamanıza gerek kalmadan kuyruk iletilerindeki çok adımlı iş akışlarını izlemek için bu tekniği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="45245-158">You could use this technique to track multi-step workflows on queue messages, without having to start over from the beginning if a processing step fails due to hardware or software failure.</span></span> <span data-ttu-id="45245-159">Genellikle, bir yeniden deneme sayısı da tutacak ve ileti birden çok bazı kaç kez denenirse, silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="45245-159">Typically, you would keep a retry count as well, and if the message is retried more than some number of times, you would delete it.</span></span> <span data-ttu-id="45245-160">Bu, her işlendiğinde bir uygulama hatası tetikleyen bir iletiye karşı korur.</span><span class="sxs-lookup"><span data-stu-id="45245-160">This protects against a message that triggers an application error each time it is processed.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L65-L69)]

## <a name="de-queue-the-next-message"></a><span data-ttu-id="45245-161">Sonraki iletiyi sıradan çıkarmak</span><span class="sxs-lookup"><span data-stu-id="45245-161">De-queue the next message</span></span>

<span data-ttu-id="45245-162">Kodunuzun bir iletiyi bir kuyruktan iki adımda çıkarır.</span><span class="sxs-lookup"><span data-stu-id="45245-162">Your code de-queues a message from a queue in two steps.</span></span> <span data-ttu-id="45245-163">Çağırdığınızda `GetMessage`, sonraki iletiyi sıraya alın.</span><span class="sxs-lookup"><span data-stu-id="45245-163">When you call `GetMessage`, you get the next message in a queue.</span></span> <span data-ttu-id="45245-164">Döndürülen bir ileti `GetMessage` iletileri bu sıradan okuyan herhangi bir kod görünmez olur.</span><span class="sxs-lookup"><span data-stu-id="45245-164">A message returned from `GetMessage` becomes invisible to any other code reading messages from this queue.</span></span> <span data-ttu-id="45245-165">Varsayılan olarak, bu ileti 30 saniye görünmez kalır.</span><span class="sxs-lookup"><span data-stu-id="45245-165">By default, this message stays invisible for 30 seconds.</span></span> <span data-ttu-id="45245-166">İletiyi kuyruktan kaldırmayı tamamlamak için de çağırmanız gerekir `DeleteMessage`.</span><span class="sxs-lookup"><span data-stu-id="45245-166">To finish removing the message from the queue, you must also call `DeleteMessage`.</span></span> <span data-ttu-id="45245-167">Bir ileti kaldırmanın bu iki adımlı işlem donanım veya yazılım hatası nedeniyle bir ileti işlemek kodunuzu başarısız olursa, kodunuzu başka bir örneği aynı ileti alma ve yeniden deneyin sağlar.</span><span class="sxs-lookup"><span data-stu-id="45245-167">This two-step process of removing a message assures that if your code fails to process a message due to hardware or software failure, another instance of your code can get the same message and try again.</span></span> <span data-ttu-id="45245-168">Kod çağrılarınızı `DeleteMessage` ileti işlendikten sonra sağ.</span><span class="sxs-lookup"><span data-stu-id="45245-168">Your code calls `DeleteMessage` right after the message has been processed.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L75-L76)]

## <a name="use-async-workflows-with-common-queue-storage-apis"></a><span data-ttu-id="45245-169">Genel kuyruk depolama API'leri ile zaman uyumsuz iş akışları kullanın</span><span class="sxs-lookup"><span data-stu-id="45245-169">Use Async workflows with common Queue storage APIs</span></span>

<span data-ttu-id="45245-170">Bu örnek, genel kuyruk depolama API'leri ile zaman uyumsuz iş akışı kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="45245-170">This example shows how to use an async workflow with common Queue storage APIs.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L82-L91)]

## <a name="additional-options-for-de-queuing-messages"></a><span data-ttu-id="45245-171">Çıkarılması iletileri için ek seçenekleri</span><span class="sxs-lookup"><span data-stu-id="45245-171">Additional options for de-queuing messages</span></span>

<span data-ttu-id="45245-172">Bir sıradan ileti alma özelleştirebilirsiniz iki yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="45245-172">There are two ways you can customize message retrieval from a queue.</span></span>
<span data-ttu-id="45245-173">İlk olarak toplu iletiler (en fazla 32) elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="45245-173">First, you can get a batch of messages (up to 32).</span></span> <span data-ttu-id="45245-174">İkinci olarak, bir uzun veya daha kısa bir görünmezlik zaman aşımı kodunuzun her iletiyi tamamen işlemesi için zaman daha az veya daha fazla izin vererek ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="45245-174">Second, you can set a longer or shorter invisibility timeout, allowing your code more or less time to fully process each message.</span></span> <span data-ttu-id="45245-175">Aşağıdaki kod örneğinde `GetMessages` 20 almak için iletileri bir çağrı'ı ve ardından her ileti işler.</span><span class="sxs-lookup"><span data-stu-id="45245-175">The following code example uses `GetMessages` to get 20 messages in one call and then processes each message.</span></span> <span data-ttu-id="45245-176">Ayrıca her ileti için beş dakika için görünmezlik zaman aşımı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="45245-176">It also sets the invisibility timeout to five minutes for each message.</span></span> <span data-ttu-id="45245-177">5 dakikalık sürenin tüm iletiler için aynı anda Not böylece sonra 5 dakika geçirilen çağrısından sonra `GetMessages`, silinmemiş tüm iletiler görünür olacaktır.</span><span class="sxs-lookup"><span data-stu-id="45245-177">Note that the 5 minutes starts for all messages at the same time, so after 5 minutes have passed since the call to `GetMessages`, any messages which have not been deleted will become visible again.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L97-L99)]

## <a name="get-the-queue-length"></a><span data-ttu-id="45245-178">Kuyruk uzunluğu alma</span><span class="sxs-lookup"><span data-stu-id="45245-178">Get the queue length</span></span>

<span data-ttu-id="45245-179">Bir kuyruktaki ileti sayısı tahmini alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="45245-179">You can get an estimate of the number of messages in a queue.</span></span> <span data-ttu-id="45245-180">`FetchAttributes` Yöntemi kuyruk hizmeti ileti sayısı dahil olmak üzere kuyruk özniteliklerini almasını ister.</span><span class="sxs-lookup"><span data-stu-id="45245-180">The `FetchAttributes` method asks the Queue service to retrieve the queue attributes, including the message count.</span></span> <span data-ttu-id="45245-181">`ApproximateMessageCount` Özelliği tarafından alınan en son değeri döndürür `FetchAttributes` kuyruk hizmetini çağırmadan olmadan yöntemi.</span><span class="sxs-lookup"><span data-stu-id="45245-181">The `ApproximateMessageCount` property returns the last value retrieved by the `FetchAttributes` method, without calling the Queue service.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L105-L106)]

## <a name="delete-a-queue"></a><span data-ttu-id="45245-182">Bir kuyruk silme</span><span class="sxs-lookup"><span data-stu-id="45245-182">Delete a queue</span></span>

<span data-ttu-id="45245-183">Bir kuyruk ve içerdiği tüm iletileri silmek için arama `Delete` nesnesinde yöntemi.</span><span class="sxs-lookup"><span data-stu-id="45245-183">To delete a queue and all the messages contained in it, call the `Delete` method on the queue object.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L112-L113)]

## <a name="next-steps"></a><span data-ttu-id="45245-184">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="45245-184">Next steps</span></span>

<span data-ttu-id="45245-185">Kuyruk depolamanın temellerini öğrendiğinize göre daha karmaşık depolama görevleri hakkında bilgi edinmek için aşağıdaki bağlantıları izleyin.</span><span class="sxs-lookup"><span data-stu-id="45245-185">Now that you've learned the basics of Queue storage, follow these links to learn about more complex storage tasks.</span></span>

- [<span data-ttu-id="45245-186">.NET için Azure depolama API'leri</span><span class="sxs-lookup"><span data-stu-id="45245-186">Azure Storage APIs for .NET</span></span>](/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="45245-187">Azure depolama türü sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="45245-187">Azure Storage Type Provider</span></span>](https://github.com/fsprojects/AzureStorageTypeProvider)
- [<span data-ttu-id="45245-188">Azure depolama ekibi blogu</span><span class="sxs-lookup"><span data-stu-id="45245-188">Azure Storage Team Blog</span></span>](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [<span data-ttu-id="45245-189">Azure Storage bağlantı dizelerini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="45245-189">Configure Azure Storage connection strings</span></span>](/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="45245-190">Azure Storage Hizmetleri REST API Başvurusu</span><span class="sxs-lookup"><span data-stu-id="45245-190">Azure Storage Services REST API Reference</span></span>](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)
