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
# <a name="get-started-with-azure-queue-storage-using-f"></a><span data-ttu-id="6ba44-104">F kullanarak Azure kuyruk depolama ile çalışmaya başlama\#</span><span class="sxs-lookup"><span data-stu-id="6ba44-104">Get started with Azure Queue storage using F\#</span></span>

<span data-ttu-id="6ba44-105">Azure kuyruk depolama, uygulama bileşenleri arasında bulut mesajlaşmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ba44-105">Azure Queue storage provides cloud messaging between application components.</span></span> <span data-ttu-id="6ba44-106">Uygulamaları ölçeklendirmek için tasarlarken, uygulama bileşenleri genellikle birbirinden bağımsız olarak ölçeklendirilebilecek şekilde ayrılır.</span><span class="sxs-lookup"><span data-stu-id="6ba44-106">In designing applications for scale, application components are often decoupled, so that they can scale independently.</span></span> <span data-ttu-id="6ba44-107">Kuyruk depolama, bulutta, masaüstünde, şirket içi sunucuda veya mobil cihazda çalışan uygulama bileşenleri arasındaki iletişim için zaman uyumsuz mesajlaşma sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ba44-107">Queue storage delivers asynchronous messaging for communication between application components, whether they are running in the cloud, on the desktop, on an on-premises server, or on a mobile device.</span></span> <span data-ttu-id="6ba44-108">Kuyruk depolama Ayrıca zaman uyumsuz görevlerin yönetilmesini ve işlem iş akışlarının oluşturulmasını destekler.</span><span class="sxs-lookup"><span data-stu-id="6ba44-108">Queue storage also supports managing asynchronous tasks and building process work flows.</span></span>

### <a name="about-this-tutorial"></a><span data-ttu-id="6ba44-109">Bu öğretici hakkında</span><span class="sxs-lookup"><span data-stu-id="6ba44-109">About this tutorial</span></span>

<span data-ttu-id="6ba44-110">Bu öğreticide, Azure kuyruk F# depolama kullanarak bazı yaygın görevler için nasıl kod yazacağınız gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6ba44-110">This tutorial shows how to write F# code for some common tasks using Azure Queue storage.</span></span> <span data-ttu-id="6ba44-111">Kapsanan görevler kuyruk oluşturma ve silme ve sıra iletilerini ekleme, okuma ve silme işlemleri içerir.</span><span class="sxs-lookup"><span data-stu-id="6ba44-111">Tasks covered include creating and deleting queues and adding, reading, and deleting queue messages.</span></span>

<span data-ttu-id="6ba44-112">Kuyruk depolamaya kavramsal bir genel bakış için lütfen [kuyruk depolaması için .net kılavuzuna](/azure/storage/storage-dotnet-how-to-use-queues)bakın.</span><span class="sxs-lookup"><span data-stu-id="6ba44-112">For a conceptual overview of queue storage, please see [the .NET guide for queue storage](/azure/storage/storage-dotnet-how-to-use-queues).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6ba44-113">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="6ba44-113">Prerequisites</span></span>

<span data-ttu-id="6ba44-114">Bu kılavuzu kullanmak için önce [bir Azure depolama hesabı oluşturmanız](/azure/storage/storage-create-storage-account)gerekir.</span><span class="sxs-lookup"><span data-stu-id="6ba44-114">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span>
<span data-ttu-id="6ba44-115">Ayrıca, bu hesap için depolama erişim anahtarınız gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="6ba44-115">You'll also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="6ba44-116">F# Betik oluşturma ve etkileşimli başlatma F#</span><span class="sxs-lookup"><span data-stu-id="6ba44-116">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="6ba44-117">Bu makaledeki örnekler, bir F# uygulama ya da bir F# komut dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6ba44-117">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="6ba44-118">Bir F# betik oluşturmak için, örneğin `.fsx` `queues.fsx`, F# geliştirme ortamınızda uzantılı bir dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6ba44-118">To create an F# script, create a file with the `.fsx` extension, for example `queues.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="6ba44-119">Daha sonra, `WindowsAzure.Storage` paketi ve bir `WindowsAzure.Storage.dll` [](https://fsprojects.github.io/Paket/) yönergekullanarakbetiğepaketvebaşvuruyüklemekiçin,paketveyaNuGetgibibirpaketyöneticisi`#r` kullanın. [](package-management.md) [](https://www.nuget.org/)</span><span class="sxs-lookup"><span data-stu-id="6ba44-119">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="6ba44-120">Ad alanı bildirimleri ekle</span><span class="sxs-lookup"><span data-stu-id="6ba44-120">Add namespace declarations</span></span>

<span data-ttu-id="6ba44-121">Aşağıdaki `open` deyimlerini `queues.fsx` dosyanın en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="6ba44-121">Add the following `open` statements to the top of the `queues.fsx` file:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L1-L3)]

### <a name="get-your-connection-string"></a><span data-ttu-id="6ba44-122">Bağlantı dizenizi alın</span><span class="sxs-lookup"><span data-stu-id="6ba44-122">Get your connection string</span></span>

<span data-ttu-id="6ba44-123">Bu öğretici için bir Azure depolama bağlantı dizesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="6ba44-123">You'll need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="6ba44-124">Bağlantı dizeleri hakkında daha fazla bilgi için bkz. [depolama bağlantı dizelerini yapılandırma](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="6ba44-124">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="6ba44-125">Öğreticide, aşağıdaki gibi, komut dosyası için Bağlantı dizenizi girersiniz:</span><span class="sxs-lookup"><span data-stu-id="6ba44-125">For the tutorial, you'll enter your connection string in your script, like this:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L9-L9)]

<span data-ttu-id="6ba44-126">Ancak, bu gerçek projeler için **önerilmez** .</span><span class="sxs-lookup"><span data-stu-id="6ba44-126">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="6ba44-127">Depolama hesabı anahtarınız, depolama hesabınızın kök parolasıyla benzerdir.</span><span class="sxs-lookup"><span data-stu-id="6ba44-127">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="6ba44-128">Depolama hesabı anahtarınızı korumak için her zaman özen gösterin.</span><span class="sxs-lookup"><span data-stu-id="6ba44-128">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="6ba44-129">Diğer kullanıcılara dağıtmaktan, sabit kodlamaktan ve başkalarının erişebileceği düz metin dosyasına kaydetmekten kaçının.</span><span class="sxs-lookup"><span data-stu-id="6ba44-129">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="6ba44-130">Güvenliğinin tehlikede olduğunu düşünüyorsanız, Azure portalını kullanarak anahtarınızı yeniden oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ba44-130">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="6ba44-131">Gerçek uygulamalar için, depolama Bağlantı dizenizi korumak için en iyi yol bir yapılandırma dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="6ba44-131">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="6ba44-132">Bağlantı dizesini bir yapılandırma dosyasından getirmek için şunu yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6ba44-132">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L11-L13)]

<span data-ttu-id="6ba44-133">Azure Configuration Manager kullanmak isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="6ba44-133">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="6ba44-134">.NET Framework `ConfigurationManager` türü gibi bir API de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ba44-134">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="6ba44-135">Bağlantı dizesini ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="6ba44-135">Parse the connection string</span></span>

<span data-ttu-id="6ba44-136">Bağlantı dizesini ayrıştırmak için şunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="6ba44-136">To parse the connection string, use:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L19-L20)]

<span data-ttu-id="6ba44-137">Bu, döndürür `CloudStorageAccount`.</span><span class="sxs-lookup"><span data-stu-id="6ba44-137">This will return a `CloudStorageAccount`.</span></span>

### <a name="create-the-queue-service-client"></a><span data-ttu-id="6ba44-138">Kuyruk hizmeti istemcisini oluşturma</span><span class="sxs-lookup"><span data-stu-id="6ba44-138">Create the Queue service client</span></span>

<span data-ttu-id="6ba44-139">Sınıfı `CloudQueueClient` , kuyruk depolamada depolanan kuyrukları almanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ba44-139">The `CloudQueueClient` class enables you to retrieve queues stored in Queue storage.</span></span> <span data-ttu-id="6ba44-140">Hizmet istemcisini oluşturmak için bir yol aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="6ba44-140">Here's one way to create the service client:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L26-L26)]

<span data-ttu-id="6ba44-141">Artık veri okuyan ve kuyruk depolamaya veri yazan kodu yazmaya hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="6ba44-141">Now you are ready to write code that reads data from and writes data to Queue storage.</span></span>

## <a name="create-a-queue"></a><span data-ttu-id="6ba44-142">Sıra oluşturma</span><span class="sxs-lookup"><span data-stu-id="6ba44-142">Create a queue</span></span>

<span data-ttu-id="6ba44-143">Bu örnek, zaten yoksa bir sıranın nasıl oluşturulacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="6ba44-143">This example shows how to create a queue if it doesn't already exist:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L32-L36)]

## <a name="insert-a-message-into-a-queue"></a><span data-ttu-id="6ba44-144">Bir kuyruğa ileti ekleme</span><span class="sxs-lookup"><span data-stu-id="6ba44-144">Insert a message into a queue</span></span>

<span data-ttu-id="6ba44-145">Mevcut bir kuyruğa ileti eklemek için ilk olarak yeni `CloudQueueMessage`bir oluştur.</span><span class="sxs-lookup"><span data-stu-id="6ba44-145">To insert a message into an existing queue, first create a new `CloudQueueMessage`.</span></span> <span data-ttu-id="6ba44-146">Sonra, `AddMessage` yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="6ba44-146">Next, call the `AddMessage` method.</span></span> <span data-ttu-id="6ba44-147">Bir `CloudQueueMessage` dizeden (UTF-8 biçiminde) `byte` ya da bir dizide oluşturulabilir ve şöyle olabilir:</span><span class="sxs-lookup"><span data-stu-id="6ba44-147">A `CloudQueueMessage` can be created from either a string (in UTF-8 format) or a `byte` array, like this:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L42-L44)]

## <a name="peek-at-the-next-message"></a><span data-ttu-id="6ba44-148">Sonraki iletiye göz atın</span><span class="sxs-lookup"><span data-stu-id="6ba44-148">Peek at the next message</span></span>

<span data-ttu-id="6ba44-149">Bir kuyruğun önünde, `PeekMessage` yöntemini çağırarak sıradan kaldırmadan iletiye göz atmayı sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ba44-149">You can peek at the message in the front of a queue, without removing it from the queue, by calling the `PeekMessage` method.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L50-L52)]

## <a name="get-the-next-message-for-processing"></a><span data-ttu-id="6ba44-150">İşleme için bir sonraki iletiyi alın</span><span class="sxs-lookup"><span data-stu-id="6ba44-150">Get the next message for processing</span></span>

<span data-ttu-id="6ba44-151">Yöntemi çağırarak, `GetMessage` işlenmek üzere bir kuyruğun önündeki iletiyi alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ba44-151">You can retrieve the message at the front of a queue for processing by calling the `GetMessage` method.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L58-L59)]

<span data-ttu-id="6ba44-152">Daha sonra, kullanarak `DeleteMessage`iletinin başarıyla işlenmesini belirteceksiniz.</span><span class="sxs-lookup"><span data-stu-id="6ba44-152">You later indicate successful processing of the message by using `DeleteMessage`.</span></span>

## <a name="change-the-contents-of-a-queued-message"></a><span data-ttu-id="6ba44-153">Sıraya alınan iletinin içeriğini değiştirme</span><span class="sxs-lookup"><span data-stu-id="6ba44-153">Change the contents of a queued message</span></span>

<span data-ttu-id="6ba44-154">Alınan bir iletinin içeriğini kuyrukta yerinde değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ba44-154">You can change the contents of a retrieved message in-place in the queue.</span></span> <span data-ttu-id="6ba44-155">İleti bir iş görevini temsil ediyorsa, iş görevinin durumunu güncelleştirmek için bu özelliği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ba44-155">If the message represents a work task, you could use this feature to update the status of the work task.</span></span> <span data-ttu-id="6ba44-156">Aşağıdaki kod, kuyruk iletisini yeni içerikle güncelleştirir ve görünürlük zaman aşımını başka bir 60 saniye uzatmak üzere ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6ba44-156">The following code updates the queue message with new contents, and sets the visibility timeout to extend another 60 seconds.</span></span> <span data-ttu-id="6ba44-157">Bu, iletiyle ilişkili çalışmanın durumunu kaydeder ve istemciye ileti üzerinde çalışmaya devam etmesi için başka bir dakika verir.</span><span class="sxs-lookup"><span data-stu-id="6ba44-157">This saves the state of work associated with the message, and gives the client another minute to continue working on the message.</span></span> <span data-ttu-id="6ba44-158">Bu tekniği, işlem adımı donanım veya yazılım arızası nedeniyle başarısız olursa baştan başlamak zorunda kalmadan, kuyruk iletilerinde çok adımlı iş akışlarını izlemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ba44-158">You could use this technique to track multi-step workflows on queue messages, without having to start over from the beginning if a processing step fails due to hardware or software failure.</span></span> <span data-ttu-id="6ba44-159">Genellikle bir yeniden deneme sayısı da olur ve ileti birkaç kez yeniden denense de onu silersiniz.</span><span class="sxs-lookup"><span data-stu-id="6ba44-159">Typically, you would keep a retry count as well, and if the message is retried more than some number of times, you would delete it.</span></span> <span data-ttu-id="6ba44-160">Bu, her işlendiği zaman bir uygulama hatasını tetikleyen bir iletiye karşı koruma sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ba44-160">This protects against a message that triggers an application error each time it is processed.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L65-L69)]

## <a name="de-queue-the-next-message"></a><span data-ttu-id="6ba44-161">Sonraki iletiyi kuyruktan kaldır</span><span class="sxs-lookup"><span data-stu-id="6ba44-161">De-queue the next message</span></span>

<span data-ttu-id="6ba44-162">Kodunuz, iki adımda bir kuyruktan bir ileti de sıralar.</span><span class="sxs-lookup"><span data-stu-id="6ba44-162">Your code de-queues a message from a queue in two steps.</span></span> <span data-ttu-id="6ba44-163">' İ çağırdığınızda `GetMessage`bir kuyruktaki sonraki iletiyi alırsınız.</span><span class="sxs-lookup"><span data-stu-id="6ba44-163">When you call `GetMessage`, you get the next message in a queue.</span></span> <span data-ttu-id="6ba44-164">Öğesinden `GetMessage` döndürülen bir ileti, bu kuyruktan gelen diğer kod okuma iletileri için görünmez hale gelir.</span><span class="sxs-lookup"><span data-stu-id="6ba44-164">A message returned from `GetMessage` becomes invisible to any other code reading messages from this queue.</span></span> <span data-ttu-id="6ba44-165">Bu ileti, varsayılan olarak 30 saniye boyunca görünmez kalır.</span><span class="sxs-lookup"><span data-stu-id="6ba44-165">By default, this message stays invisible for 30 seconds.</span></span> <span data-ttu-id="6ba44-166">İletiyi kuyruktan kaldırma işleminin tamamlanabilmesi için, öğesini de çağırmanız `DeleteMessage`gerekir.</span><span class="sxs-lookup"><span data-stu-id="6ba44-166">To finish removing the message from the queue, you must also call `DeleteMessage`.</span></span> <span data-ttu-id="6ba44-167">Bir iletiyi kaldırmanın bu iki adımlı işlemi, kodunuz, donanım veya yazılım arızasından kaynaklanan bir iletiyi işleyemediğinde, kodunuzun başka bir örneğinin aynı mesajı almasını ve yeniden denemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ba44-167">This two-step process of removing a message assures that if your code fails to process a message due to hardware or software failure, another instance of your code can get the same message and try again.</span></span> <span data-ttu-id="6ba44-168">İleti işlendikten sonra `DeleteMessage` kodunuz doğru şekilde çağırır.</span><span class="sxs-lookup"><span data-stu-id="6ba44-168">Your code calls `DeleteMessage` right after the message has been processed.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L75-L76)]

## <a name="use-async-workflows-with-common-queue-storage-apis"></a><span data-ttu-id="6ba44-169">Ortak kuyruk depolama API 'Leri ile zaman uyumsuz iş akışları kullanma</span><span class="sxs-lookup"><span data-stu-id="6ba44-169">Use Async workflows with common Queue storage APIs</span></span>

<span data-ttu-id="6ba44-170">Bu örnek, genel sıra depolama API 'Leri ile zaman uyumsuz bir iş akışının nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6ba44-170">This example shows how to use an async workflow with common Queue storage APIs.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L82-L91)]

## <a name="additional-options-for-de-queuing-messages"></a><span data-ttu-id="6ba44-171">İletileri serbest bırakma için ek seçenekler</span><span class="sxs-lookup"><span data-stu-id="6ba44-171">Additional options for de-queuing messages</span></span>

<span data-ttu-id="6ba44-172">İleti alımı bir kuyruktan özelleştirmek için kullanabileceğiniz iki yol vardır.</span><span class="sxs-lookup"><span data-stu-id="6ba44-172">There are two ways you can customize message retrieval from a queue.</span></span>
<span data-ttu-id="6ba44-173">İlk olarak, bir toplu ileti alabilirsiniz (en fazla 32).</span><span class="sxs-lookup"><span data-stu-id="6ba44-173">First, you can get a batch of messages (up to 32).</span></span> <span data-ttu-id="6ba44-174">İkincisi, daha uzun veya daha kısa bir zaman aşımı ayarlayabilir, böylece her iletiyi tamamen işlemek için kodunuzun daha fazla veya daha az zaman aşımına uğramamasını sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ba44-174">Second, you can set a longer or shorter invisibility timeout, allowing your code more or less time to fully process each message.</span></span> <span data-ttu-id="6ba44-175">Aşağıdaki kod örneği, bir `GetMessages` çağrıda 20 ileti almak için kullanır ve ardından her iletiyi işler.</span><span class="sxs-lookup"><span data-stu-id="6ba44-175">The following code example uses `GetMessages` to get 20 messages in one call and then processes each message.</span></span> <span data-ttu-id="6ba44-176">Ayrıca, her ileti için geçersiz kılma zaman aşımını beş dakikaya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6ba44-176">It also sets the invisibility timeout to five minutes for each message.</span></span> <span data-ttu-id="6ba44-177">5 dakikalık tüm iletiler için aynı anda başlayacağını unutmayın. bu nedenle, çağrısından `GetMessages`bu yana 5 dakika geçtikten sonra, silinmemiş olan tüm iletiler yeniden görünür hale gelir.</span><span class="sxs-lookup"><span data-stu-id="6ba44-177">Note that the 5 minutes starts for all messages at the same time, so after 5 minutes have passed since the call to `GetMessages`, any messages which have not been deleted will become visible again.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L97-L99)]

## <a name="get-the-queue-length"></a><span data-ttu-id="6ba44-178">Sıra uzunluğunu al</span><span class="sxs-lookup"><span data-stu-id="6ba44-178">Get the queue length</span></span>

<span data-ttu-id="6ba44-179">Kuyruktaki ileti sayısını tahmin edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ba44-179">You can get an estimate of the number of messages in a queue.</span></span> <span data-ttu-id="6ba44-180">`FetchAttributes` Yöntemi, ileti sayısı dahil olmak üzere kuyruk hizmeti kuyruk özniteliklerini almayı ister.</span><span class="sxs-lookup"><span data-stu-id="6ba44-180">The `FetchAttributes` method asks the Queue service to retrieve the queue attributes, including the message count.</span></span> <span data-ttu-id="6ba44-181">Özelliği, kuyruk hizmeti çağrılmadan `FetchAttributes` yöntemi tarafından alınan son değeri döndürür. `ApproximateMessageCount`</span><span class="sxs-lookup"><span data-stu-id="6ba44-181">The `ApproximateMessageCount` property returns the last value retrieved by the `FetchAttributes` method, without calling the Queue service.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L105-L106)]

## <a name="delete-a-queue"></a><span data-ttu-id="6ba44-182">Kuyruğu silme</span><span class="sxs-lookup"><span data-stu-id="6ba44-182">Delete a queue</span></span>

<span data-ttu-id="6ba44-183">Bir kuyruğu ve içerdiği tüm iletileri silmek için, kuyruk nesnesi üzerinde `Delete` yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="6ba44-183">To delete a queue and all the messages contained in it, call the `Delete` method on the queue object.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L112-L113)]

## <a name="next-steps"></a><span data-ttu-id="6ba44-184">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="6ba44-184">Next steps</span></span>

<span data-ttu-id="6ba44-185">Sıra depolamanın temellerini öğrendiğinize göre, daha karmaşık depolama görevleri hakkında bilgi edinmek için bu bağlantıları izleyin.</span><span class="sxs-lookup"><span data-stu-id="6ba44-185">Now that you've learned the basics of Queue storage, follow these links to learn about more complex storage tasks.</span></span>

- [<span data-ttu-id="6ba44-186">.NET için Azure depolama API 'Leri</span><span class="sxs-lookup"><span data-stu-id="6ba44-186">Azure Storage APIs for .NET</span></span>](/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="6ba44-187">Azure depolama türü sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="6ba44-187">Azure Storage Type Provider</span></span>](https://github.com/fsprojects/AzureStorageTypeProvider)
- [<span data-ttu-id="6ba44-188">Azure depolama ekibi blogu</span><span class="sxs-lookup"><span data-stu-id="6ba44-188">Azure Storage Team Blog</span></span>](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [<span data-ttu-id="6ba44-189">Azure depolama bağlantı dizelerini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6ba44-189">Configure Azure Storage connection strings</span></span>](/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="6ba44-190">Azure depolama hizmetleri REST API başvurusu</span><span class="sxs-lookup"><span data-stu-id="6ba44-190">Azure Storage Services REST API Reference</span></span>](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)
