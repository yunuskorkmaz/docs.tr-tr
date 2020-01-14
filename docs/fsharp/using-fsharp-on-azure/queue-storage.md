---
title: F# kullanarak Azure Kuyruk depolama kullanmaya başlama
description: Azure Queues, uygulama bileşenleri arasında güvenilir ve zaman uyumsuz mesajlaşma sağlar. Bulut mesajlaşma özelliği uygulama bileşenlerinizin bağımsız olarak ölçeklendirilmesini sağlar.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 841068ac91aecc53811359e27d984907569a2c6d
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75935490"
---
# <a name="get-started-with-azure-queue-storage-using-f"></a><span data-ttu-id="acc3d-104">F\# kullanarak Azure kuyruk depolama ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="acc3d-104">Get started with Azure Queue storage using F\#</span></span>

<span data-ttu-id="acc3d-105">Azure Queue depolama birimi, uygulama bileşenleri arasında bulut mesajlaşma özelliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="acc3d-105">Azure Queue storage provides cloud messaging between application components.</span></span> <span data-ttu-id="acc3d-106">Ölçeklendirmek üzere uygulama tasarlarken, uygulama bileşenleri birbirinden bağımsız şekilde ölçeklenebilmek için genellikle birbirinden ayrılır.</span><span class="sxs-lookup"><span data-stu-id="acc3d-106">In designing applications for scale, application components are often decoupled, so that they can scale independently.</span></span> <span data-ttu-id="acc3d-107">Kuyruk depolama bulutta, masaüstünde, şirket içi sunucuda veya mobil bir cihazda çalışan uygulama bileşenleri arasındaki iletişim için zaman uyumsuz mesajlaşma sunar.</span><span class="sxs-lookup"><span data-stu-id="acc3d-107">Queue storage delivers asynchronous messaging for communication between application components, whether they are running in the cloud, on the desktop, on an on-premises server, or on a mobile device.</span></span> <span data-ttu-id="acc3d-108">Kuyruk depolama ayrıca zaman uyumsuz görevlerin yönetilmesini ve süreç iş akışlarının oluşturulmasını destekler.</span><span class="sxs-lookup"><span data-stu-id="acc3d-108">Queue storage also supports managing asynchronous tasks and building process work flows.</span></span>

### <a name="about-this-tutorial"></a><span data-ttu-id="acc3d-109">Bu öğretici hakkında</span><span class="sxs-lookup"><span data-stu-id="acc3d-109">About this tutorial</span></span>

<span data-ttu-id="acc3d-110">Bu öğreticide, Azure kuyruk F# depolama kullanarak bazı yaygın görevler için nasıl kod yazacağınız gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="acc3d-110">This tutorial shows how to write F# code for some common tasks using Azure Queue storage.</span></span> <span data-ttu-id="acc3d-111">Kapsanan görevler kuyruk oluşturma ve silme ve sıra iletilerini ekleme, okuma ve silme işlemleri içerir.</span><span class="sxs-lookup"><span data-stu-id="acc3d-111">Tasks covered include creating and deleting queues and adding, reading, and deleting queue messages.</span></span>

<span data-ttu-id="acc3d-112">Kuyruk depolamaya kavramsal bir genel bakış için lütfen [kuyruk depolaması için .net kılavuzuna](/azure/storage/storage-dotnet-how-to-use-queues)bakın.</span><span class="sxs-lookup"><span data-stu-id="acc3d-112">For a conceptual overview of queue storage, please see [the .NET guide for queue storage](/azure/storage/storage-dotnet-how-to-use-queues).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="acc3d-113">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="acc3d-113">Prerequisites</span></span>

<span data-ttu-id="acc3d-114">Bu kılavuzu kullanmak için önce [bir Azure depolama hesabı oluşturmanız](/azure/storage/storage-create-storage-account)gerekir.</span><span class="sxs-lookup"><span data-stu-id="acc3d-114">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span>
<span data-ttu-id="acc3d-115">Ayrıca, bu hesap için depolama erişim anahtarınız gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="acc3d-115">You'll also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="acc3d-116">F# Betik oluşturma ve etkileşimli başlatma F#</span><span class="sxs-lookup"><span data-stu-id="acc3d-116">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="acc3d-117">Bu makaledeki örnekler, bir F# uygulama ya da bir F# komut dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="acc3d-117">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="acc3d-118">F# Betik oluşturmak için, F# geliştirme ortamınızda `.fsx` uzantılı bir dosya oluşturun (örneğin `queues.fsx`).</span><span class="sxs-lookup"><span data-stu-id="acc3d-118">To create an F# script, create a file with the `.fsx` extension, for example `queues.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="acc3d-119">Ardından, bir `#r` yönergesi kullanarak betiğe `WindowsAzure.Storage` paketini ve başvuru `WindowsAzure.Storage.dll` yüklemek için paket veya [NuGet](https://www.nuget.org/) [gibi bir](https://fsprojects.github.io/Paket/) [Paket Yöneticisi](package-management.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="acc3d-119">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="acc3d-120">Ad alanı bildirimleri ekleme</span><span class="sxs-lookup"><span data-stu-id="acc3d-120">Add namespace declarations</span></span>

<span data-ttu-id="acc3d-121">Aşağıdaki `open` bildirimlerini `queues.fsx` dosyasının üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="acc3d-121">Add the following `open` statements to the top of the `queues.fsx` file:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L1-L3)]

### <a name="get-your-connection-string"></a><span data-ttu-id="acc3d-122">Bağlantı dizenizi alma</span><span class="sxs-lookup"><span data-stu-id="acc3d-122">Get your connection string</span></span>

<span data-ttu-id="acc3d-123">Bu öğretici için bir Azure depolama bağlantı dizesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="acc3d-123">You'll need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="acc3d-124">Bağlantı dizeleri hakkında daha fazla bilgi için bkz. [depolama bağlantı dizelerini yapılandırma](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="acc3d-124">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="acc3d-125">Öğreticide, aşağıdaki gibi, komut dosyası için Bağlantı dizenizi girersiniz:</span><span class="sxs-lookup"><span data-stu-id="acc3d-125">For the tutorial, you'll enter your connection string in your script, like this:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L9-L9)]

<span data-ttu-id="acc3d-126">Ancak, bu gerçek projeler için **önerilmez** .</span><span class="sxs-lookup"><span data-stu-id="acc3d-126">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="acc3d-127">Depolama hesabı anahtarınız depolama hesabınızın kök parolasına benzer.</span><span class="sxs-lookup"><span data-stu-id="acc3d-127">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="acc3d-128">Depolama hesabı anahtarınızı korumak için her zaman özen gösterin.</span><span class="sxs-lookup"><span data-stu-id="acc3d-128">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="acc3d-129">Diğer kullanıcılara dağıtmaktan, sabit kodlamaktan ve başkalarının erişebileceği düz metin dosyasına kaydetmekten kaçının.</span><span class="sxs-lookup"><span data-stu-id="acc3d-129">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="acc3d-130">Güvenliğinin tehlikede olduğunu düşünüyorsanız, Azure portalını kullanarak anahtarınızı yeniden oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="acc3d-130">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="acc3d-131">Gerçek uygulamalar için, depolama Bağlantı dizenizi korumak için en iyi yol bir yapılandırma dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="acc3d-131">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="acc3d-132">Bağlantı dizesini bir yapılandırma dosyasından getirmek için şunu yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="acc3d-132">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L11-L13)]

<span data-ttu-id="acc3d-133">Azure Yapılandırma Yöneticisi'ni kullanmak isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="acc3d-133">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="acc3d-134">.NET Framework `ConfigurationManager` türü gibi bir API de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="acc3d-134">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="acc3d-135">Bağlantı dizesini ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="acc3d-135">Parse the connection string</span></span>

<span data-ttu-id="acc3d-136">Bağlantı dizesini ayrıştırmak için şunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="acc3d-136">To parse the connection string, use:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L19-L20)]

<span data-ttu-id="acc3d-137">Bu, bir `CloudStorageAccount`döndürür.</span><span class="sxs-lookup"><span data-stu-id="acc3d-137">This will return a `CloudStorageAccount`.</span></span>

### <a name="create-the-queue-service-client"></a><span data-ttu-id="acc3d-138">Kuyruk hizmeti istemcisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="acc3d-138">Create the Queue service client</span></span>

<span data-ttu-id="acc3d-139">`CloudQueueClient` sınıfı, kuyruk depolamada depolanan kuyrukları almanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="acc3d-139">The `CloudQueueClient` class enables you to retrieve queues stored in Queue storage.</span></span> <span data-ttu-id="acc3d-140">Hizmet istemcisini oluşturma yöntemlerinden biri aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="acc3d-140">Here's one way to create the service client:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L26-L26)]

<span data-ttu-id="acc3d-141">Artık Kuyruk depolamadan veri okuyan ve bu depolamaya veri yazan kodu yazmaya hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="acc3d-141">Now you are ready to write code that reads data from and writes data to Queue storage.</span></span>

## <a name="create-a-queue"></a><span data-ttu-id="acc3d-142">Kuyruk oluştur</span><span class="sxs-lookup"><span data-stu-id="acc3d-142">Create a queue</span></span>

<span data-ttu-id="acc3d-143">Bu örnek, zaten yoksa bir sıranın nasıl oluşturulacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="acc3d-143">This example shows how to create a queue if it doesn't already exist:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L32-L36)]

## <a name="insert-a-message-into-a-queue"></a><span data-ttu-id="acc3d-144">Kuyruğa bir ileti yerleştirme</span><span class="sxs-lookup"><span data-stu-id="acc3d-144">Insert a message into a queue</span></span>

<span data-ttu-id="acc3d-145">Mevcut bir sıraya bir ileti eklemek için, önce yeni bir `CloudQueueMessage`oluşturun.</span><span class="sxs-lookup"><span data-stu-id="acc3d-145">To insert a message into an existing queue, first create a new `CloudQueueMessage`.</span></span> <span data-ttu-id="acc3d-146">Sonra `AddMessage` yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="acc3d-146">Next, call the `AddMessage` method.</span></span> <span data-ttu-id="acc3d-147">Bir `CloudQueueMessage`, bir dizeden (UTF-8 biçiminde) ya da bir `byte` dizisinden oluşturulabilir, örneğin:</span><span class="sxs-lookup"><span data-stu-id="acc3d-147">A `CloudQueueMessage` can be created from either a string (in UTF-8 format) or a `byte` array, like this:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L42-L44)]

## <a name="peek-at-the-next-message"></a><span data-ttu-id="acc3d-148">Sonraki iletiye gözatın</span><span class="sxs-lookup"><span data-stu-id="acc3d-148">Peek at the next message</span></span>

<span data-ttu-id="acc3d-149">`PeekMessage` yöntemini çağırarak bir kuyruğun önündeki iletiye göz atırsınız ve bunu kuyruktan kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="acc3d-149">You can peek at the message in the front of a queue, without removing it from the queue, by calling the `PeekMessage` method.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L50-L52)]

## <a name="get-the-next-message-for-processing"></a><span data-ttu-id="acc3d-150">İşleme için bir sonraki iletiyi alın</span><span class="sxs-lookup"><span data-stu-id="acc3d-150">Get the next message for processing</span></span>

<span data-ttu-id="acc3d-151">`GetMessage` yöntemini çağırarak, işlenmek üzere kuyruğun önündeki iletiyi alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="acc3d-151">You can retrieve the message at the front of a queue for processing by calling the `GetMessage` method.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L58-L59)]

<span data-ttu-id="acc3d-152">Daha sonra `DeleteMessage`kullanarak iletinin başarıyla işlenmesini belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="acc3d-152">You later indicate successful processing of the message by using `DeleteMessage`.</span></span>

## <a name="change-the-contents-of-a-queued-message"></a><span data-ttu-id="acc3d-153">Kuyruğa alınan iletinin içeriğini değiştirme</span><span class="sxs-lookup"><span data-stu-id="acc3d-153">Change the contents of a queued message</span></span>

<span data-ttu-id="acc3d-154">Alınan bir iletinin içeriğini kuyrukta yerinde değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="acc3d-154">You can change the contents of a retrieved message in-place in the queue.</span></span> <span data-ttu-id="acc3d-155">Eğer ileti bir iş görevini temsil ediyorsa, bu özelliği kullanarak iş görevinin durumunu güncelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="acc3d-155">If the message represents a work task, you could use this feature to update the status of the work task.</span></span> <span data-ttu-id="acc3d-156">Aşağıdaki kod kuyruk iletisini yeni içeriklerle güncelleştirir ve görünürlük zaman aşımını 60 saniye daha uzatır.</span><span class="sxs-lookup"><span data-stu-id="acc3d-156">The following code updates the queue message with new contents, and sets the visibility timeout to extend another 60 seconds.</span></span> <span data-ttu-id="acc3d-157">Bu, ileti ile ilişkili işin durumunu kaydeder ve istemciye ileti üzerinde çalışmaya devam etmesi için bir dakika daha zaman verir.</span><span class="sxs-lookup"><span data-stu-id="acc3d-157">This saves the state of work associated with the message, and gives the client another minute to continue working on the message.</span></span> <span data-ttu-id="acc3d-158">Bir işleme adımı donanım veya yazılım arızasından dolayı başarısız olursa baştan başlamanıza gerek kalmadan kuyruk iletilerindeki çok adımlı iş akışlarını izlemek için bu yöntemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="acc3d-158">You could use this technique to track multi-step workflows on queue messages, without having to start over from the beginning if a processing step fails due to hardware or software failure.</span></span> <span data-ttu-id="acc3d-159">Genellikle bir yeniden deneme sayısı da olur ve ileti birkaç kez yeniden denense de onu silersiniz.</span><span class="sxs-lookup"><span data-stu-id="acc3d-159">Typically, you would keep a retry count as well, and if the message is retried more than some number of times, you would delete it.</span></span> <span data-ttu-id="acc3d-160">Bu, her işlendiğinde bir uygulama hatası tetikleyen bir iletiye karşı koruma sağlar.</span><span class="sxs-lookup"><span data-stu-id="acc3d-160">This protects against a message that triggers an application error each time it is processed.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L65-L69)]

## <a name="de-queue-the-next-message"></a><span data-ttu-id="acc3d-161">Sonraki iletiyi sıradan çıkarmak</span><span class="sxs-lookup"><span data-stu-id="acc3d-161">De-queue the next message</span></span>

<span data-ttu-id="acc3d-162">Kodunuz, bir iletiyi bir kuyruktan iki adımda çıkarır.</span><span class="sxs-lookup"><span data-stu-id="acc3d-162">Your code de-queues a message from a queue in two steps.</span></span> <span data-ttu-id="acc3d-163">`GetMessage`çağırdığınızda sıradaki bir sonraki iletiyi alırsınız.</span><span class="sxs-lookup"><span data-stu-id="acc3d-163">When you call `GetMessage`, you get the next message in a queue.</span></span> <span data-ttu-id="acc3d-164">`GetMessage` döndürülen bir ileti, bu kuyruktan gelen diğer kod okuma iletileri için görünmez hale gelir.</span><span class="sxs-lookup"><span data-stu-id="acc3d-164">A message returned from `GetMessage` becomes invisible to any other code reading messages from this queue.</span></span> <span data-ttu-id="acc3d-165">Varsayılan olarak bu ileti 30 saniye görünmez kalır.</span><span class="sxs-lookup"><span data-stu-id="acc3d-165">By default, this message stays invisible for 30 seconds.</span></span> <span data-ttu-id="acc3d-166">İletiyi kuyruktan kaldırma işleminin tamamlanabilmesi için, `DeleteMessage`de çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="acc3d-166">To finish removing the message from the queue, you must also call `DeleteMessage`.</span></span> <span data-ttu-id="acc3d-167">Bir iletinin iki adımlı kaldırılma süreci, donanım veya yazılım arızasından dolayı kodunuzun bir iletiyi işleyememesi durumunda kodunuzun başka bir örneğinin aynı iletiyi alıp yeniden denemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="acc3d-167">This two-step process of removing a message assures that if your code fails to process a message due to hardware or software failure, another instance of your code can get the same message and try again.</span></span> <span data-ttu-id="acc3d-168">İleti işlendikten sonra kodunuz `DeleteMessage` çağırır.</span><span class="sxs-lookup"><span data-stu-id="acc3d-168">Your code calls `DeleteMessage` right after the message has been processed.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L75-L76)]

## <a name="use-async-workflows-with-common-queue-storage-apis"></a><span data-ttu-id="acc3d-169">Ortak kuyruk depolama API 'Leri ile zaman uyumsuz iş akışları kullanma</span><span class="sxs-lookup"><span data-stu-id="acc3d-169">Use Async workflows with common Queue storage APIs</span></span>

<span data-ttu-id="acc3d-170">Bu örnek, genel sıra depolama API 'Leri ile zaman uyumsuz bir iş akışının nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="acc3d-170">This example shows how to use an async workflow with common Queue storage APIs.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L82-L91)]

## <a name="additional-options-for-de-queuing-messages"></a><span data-ttu-id="acc3d-171">İletileri serbest bırakma için ek seçenekler</span><span class="sxs-lookup"><span data-stu-id="acc3d-171">Additional options for de-queuing messages</span></span>

<span data-ttu-id="acc3d-172">İletilerin bir kuyruktan alınma şeklini iki yöntemle özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="acc3d-172">There are two ways you can customize message retrieval from a queue.</span></span>
<span data-ttu-id="acc3d-173">İlk olarak toplu iletiler alabilirsiniz (en fazla 32).</span><span class="sxs-lookup"><span data-stu-id="acc3d-173">First, you can get a batch of messages (up to 32).</span></span> <span data-ttu-id="acc3d-174">İkinci olarak daha uzun veya daha kısa bir görünmezlik süresi ayarlayarak kodunuzun her iletiyi tamamen işlemesi için daha az veya daha fazla zaman tanıyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="acc3d-174">Second, you can set a longer or shorter invisibility timeout, allowing your code more or less time to fully process each message.</span></span> <span data-ttu-id="acc3d-175">Aşağıdaki kod örneği, tek bir çağrıda 20 ileti almak için `GetMessages` kullanır ve ardından her iletiyi işler.</span><span class="sxs-lookup"><span data-stu-id="acc3d-175">The following code example uses `GetMessages` to get 20 messages in one call and then processes each message.</span></span> <span data-ttu-id="acc3d-176">Ayrıca her ileti için görünmezlik zaman aşımı beş dakika olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="acc3d-176">It also sets the invisibility timeout to five minutes for each message.</span></span> <span data-ttu-id="acc3d-177">5 dakikalık tüm iletiler için aynı anda başlayacağını unutmayın. bu nedenle, `GetMessages`çağrısından bu yana 5 dakika geçtikten sonra, silinmemiş olan tüm iletiler yeniden görünür hale gelir.</span><span class="sxs-lookup"><span data-stu-id="acc3d-177">Note that the 5 minutes starts for all messages at the same time, so after 5 minutes have passed since the call to `GetMessages`, any messages which have not been deleted will become visible again.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L97-L99)]

## <a name="get-the-queue-length"></a><span data-ttu-id="acc3d-178">Kuyruk uzunluğu alma</span><span class="sxs-lookup"><span data-stu-id="acc3d-178">Get the queue length</span></span>

<span data-ttu-id="acc3d-179">Bir kuyruktaki ileti sayısı ile ilgili bir tahmin alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="acc3d-179">You can get an estimate of the number of messages in a queue.</span></span> <span data-ttu-id="acc3d-180">`FetchAttributes` yöntemi, ileti sayısı dahil olmak üzere Kuyruk hizmeti kuyruk özniteliklerini almayı ister.</span><span class="sxs-lookup"><span data-stu-id="acc3d-180">The `FetchAttributes` method asks the Queue service to retrieve the queue attributes, including the message count.</span></span> <span data-ttu-id="acc3d-181">`ApproximateMessageCount` özelliği, Kuyruk hizmeti çağrılmadan `FetchAttributes` yöntemi tarafından alınan son değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="acc3d-181">The `ApproximateMessageCount` property returns the last value retrieved by the `FetchAttributes` method, without calling the Queue service.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L105-L106)]

## <a name="delete-a-queue"></a><span data-ttu-id="acc3d-182">Bir kuyruk silme</span><span class="sxs-lookup"><span data-stu-id="acc3d-182">Delete a queue</span></span>

<span data-ttu-id="acc3d-183">Bir kuyruğu ve içerdiği tüm iletileri silmek için, kuyruk nesnesi üzerinde `Delete` yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="acc3d-183">To delete a queue and all the messages contained in it, call the `Delete` method on the queue object.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L112-L113)]

## <a name="next-steps"></a><span data-ttu-id="acc3d-184">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="acc3d-184">Next steps</span></span>

<span data-ttu-id="acc3d-185">Kuyruk depolamanın temellerini öğrendiğinize göre, daha karmaşık depolama görevleri hakkında daha fazla bilgi edinmek için bu bağlantıları takip edin:</span><span class="sxs-lookup"><span data-stu-id="acc3d-185">Now that you've learned the basics of Queue storage, follow these links to learn about more complex storage tasks.</span></span>

- [<span data-ttu-id="acc3d-186">.NET için Azure Depolama API'leri</span><span class="sxs-lookup"><span data-stu-id="acc3d-186">Azure Storage APIs for .NET</span></span>](/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="acc3d-187">Azure depolama türü sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="acc3d-187">Azure Storage Type Provider</span></span>](https://github.com/fsprojects/AzureStorageTypeProvider)
- [<span data-ttu-id="acc3d-188">Azure Depolama Ekibi Blog’u</span><span class="sxs-lookup"><span data-stu-id="acc3d-188">Azure Storage Team Blog</span></span>](https://docs.microsoft.com/archive/blogs/windowsazurestorage/)
- [<span data-ttu-id="acc3d-189">Azure Depolama bağlantı dizelerini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="acc3d-189">Configure Azure Storage connection strings</span></span>](/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="acc3d-190">Azure Depolama Hizmeti REST API Başvurusu</span><span class="sxs-lookup"><span data-stu-id="acc3d-190">Azure Storage Services REST API Reference</span></span>](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)
