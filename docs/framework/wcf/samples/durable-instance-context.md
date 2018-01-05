---
title: "Dayanıklı Örnek Bağlamı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97bc2994-5a2c-47c7-927a-c4cd273153df
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e4f1f3f9e840ba422e327792ec2b0554fad45902
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="durable-instance-context"></a><span data-ttu-id="1fa2c-102">Dayanıklı Örnek Bağlamı</span><span class="sxs-lookup"><span data-stu-id="1fa2c-102">Durable Instance Context</span></span>
<span data-ttu-id="1fa2c-103">Bu örnek nasıl özelleştirileceğini gösteren [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] dayanıklı örnek bağlamı etkinleştirmek için çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-103">This sample demonstrates how to customize the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] runtime to enable durable instance contexts.</span></span> <span data-ttu-id="1fa2c-104">SQL Server 2005 (SQL Server 2005 Express bu durumda), yedekleme deposu olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-104">It uses SQL Server 2005 as its backing store (SQL Server 2005 Express in this case).</span></span> <span data-ttu-id="1fa2c-105">Ancak, özel depolama mekanizmaları erişmek için bir yol da sağlar.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-105">However, it also provides a way to access custom storage mechanisms.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1fa2c-106">Kurulum yordamı ve yapı yönergeleri Bu örnek için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="1fa2c-107">Bu örnek kanal katmanını ve, hizmet modeli katmanını genişletme içerir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1fa2c-107">This sample involves extending both the channel layer and the service model layer of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="1fa2c-108">Bu nedenle uygulama ayrıntılarını geçmeden önce temel kavramları anlamanız gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-108">Therefore it is necessary to understand the underlying concepts before going into the implementation details.</span></span>  
  
 <span data-ttu-id="1fa2c-109">Dayanıklı örnek bağlamı gerçek dünya senaryolarında genellikle bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-109">Durable instance contexts can be found in the real world scenarios quite often.</span></span> <span data-ttu-id="1fa2c-110">Alışveriş sepeti uygulaması, örneğin, yarı yarıya aracılığıyla alışveriş duraklatma ve başka bir günde devam etmek için yüklemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-110">A shopping cart application for example, has the ability to pause shopping halfway through and continue it on another day.</span></span> <span data-ttu-id="1fa2c-111">Biz alışveriş sepeti sonraki gün ziyaret ettiğinizde böylece bizim özgün bağlamı geri yüklendi.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-111">So that when we visit the shopping cart the next day, our original context is restored.</span></span> <span data-ttu-id="1fa2c-112">Biz değilken alışveriş sepeti uygulaması (sunucu) alışveriş sepeti örneği korumaz dikkate almak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-112">It is important to note that the shopping cart application (on the server) does not maintain the shopping cart instance while we are disconnected.</span></span> <span data-ttu-id="1fa2c-113">Bunun yerine, durumu sağlam bir ortamdan devam ederse ve geri yüklenen bağlamı için yeni bir örnek oluşturulurken kullanır.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-113">Instead, it persists its state into a durable storage media and uses it when constructing a new instance for the restored context.</span></span> <span data-ttu-id="1fa2c-114">Bu nedenle aynı bağlam için hizmet verebilir hizmet örneği önceki örneği ile aynı değil (diğer bir deyişle, aynı bellek adresi yok).</span><span class="sxs-lookup"><span data-stu-id="1fa2c-114">Therefore the service instance that may service for the same context is not the same as the previous instance (that is, it does not have the same memory address).</span></span>  
  
 <span data-ttu-id="1fa2c-115">Bir bağlam kimliği istemci ve hizmet arasındaki alış verişleri küçük bir protokolü tarafından dayanıklı örnek bağlamı mümkün hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-115">Durable instance context is made possible by a small protocol that exchanges a context ID between the client and service.</span></span> <span data-ttu-id="1fa2c-116">Bu bağlam kimliği istemcide oluşturulur ve Hizmeti'ne aktarılan.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-116">This context ID is created on the client and transmitted to the service.</span></span> <span data-ttu-id="1fa2c-117">Hizmet örneği oluşturulduğunda, bu bağlam Kimliğine karşılık gelen kalıcı depolama biriminden kalıcı durum yüklemek hizmet çalışma zamanı çalışır (varsayılan olarak bu, bir SQL Server 2005 veritabanı'dir).</span><span class="sxs-lookup"><span data-stu-id="1fa2c-117">When the service instance is created, the service runtime tries to load the persisted state that corresponds to this context ID from a persistent storage (by default it is a SQL Server 2005 database).</span></span> <span data-ttu-id="1fa2c-118">Durum yok kullanılabiliyorsa, yeni örnek varsayılan durumuna sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-118">If no state is available the new instance has its default state.</span></span> <span data-ttu-id="1fa2c-119">Hizmet uygulaması, hizmet uygulaması durumunu değiştirin ve böylece çalışma zamanı hizmet örneği başlatma sonrasında kaydedebilirsiniz işlemleri işaretlemek için özel bir öznitelik kullanır.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-119">The service implementation uses a custom attribute to mark operations that change the state of the service implementation so that the runtime can save the service instance after invoking them.</span></span>  
  
 <span data-ttu-id="1fa2c-120">Önceki Açıklama tarafından iki adımı kolayca hedefe ulaşmak için ayırt edilebilir:</span><span class="sxs-lookup"><span data-stu-id="1fa2c-120">By the previous description, two steps can easily be distinguished to achieve the goal:</span></span>  
  
1.  <span data-ttu-id="1fa2c-121">İçerik kimliği taşımak için kablo gider ileti değiştirin</span><span class="sxs-lookup"><span data-stu-id="1fa2c-121">Change the message that goes on the wire to carry the context ID.</span></span>  
  
2.  <span data-ttu-id="1fa2c-122">Özel örneklemesini mantığını uygulamak için hizmet yerel davranışını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-122">Change the service local behavior to implement custom instancing logic.</span></span>  
  
 <span data-ttu-id="1fa2c-123">Listedeki birinci kablo iletilerde etkilediğinden özel bir kanalda uygulanması gerekir ve kanal katmana sayfaya.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-123">Because the first one in the list affects the messages on the wire it should be implemented as a custom channel and be hooked up to the channel layer.</span></span> <span data-ttu-id="1fa2c-124">İkinci yalnızca hizmet yerel davranışını etkiler ve bu nedenle birkaç hizmet genişletilebilirlik noktaları genişleterek uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-124">The latter only affects the service local behavior and therefore can be implemented by extending several service extensibility points.</span></span> <span data-ttu-id="1fa2c-125">Sonraki birkaç bölümlerde, bu uzantıların her ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-125">In the next few sections, each of these extensions are discussed.</span></span>  
  
## <a name="durable-instancecontext-channel"></a><span data-ttu-id="1fa2c-126">Dayanıklı InstanceContext kanal</span><span class="sxs-lookup"><span data-stu-id="1fa2c-126">Durable InstanceContext Channel</span></span>  
 <span data-ttu-id="1fa2c-127">İlk şey bakmak için bir kanal katman uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-127">The first thing to look at is a channel layer extension.</span></span> <span data-ttu-id="1fa2c-128">Özel bir kanalda yazma ilk adımı kanal iletişimi yapısına karar vermektir.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-128">The first step in writing a custom channel is to decide the communication structure of the channel.</span></span> <span data-ttu-id="1fa2c-129">Yeni bir kablo protokolü tanıtılan kanal neredeyse her bir kanal kanal yığınında çalışması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-129">As a new wire protocol is being introduced the channel should work with almost any other channel in the channel stack.</span></span> <span data-ttu-id="1fa2c-130">Bu nedenle, tüm ileti exchange desenleri desteklemelidir.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-130">Therefore it should support all the message exchange patterns.</span></span> <span data-ttu-id="1fa2c-131">Ancak, kanal çekirdek işlevselliğini communication yapısını bakılmaksızın aynı olacak.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-131">However, the core functionality of the channel is the same regardless of its communication structure.</span></span> <span data-ttu-id="1fa2c-132">Daha açık belirtmek gerekirse istemciden bağlam Kimliğini iletileri okuma ve yazma ve hizmetinden bu bağlam Kimliğini gelen iletileri okur ve üst düzey geçirin.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-132">More specifically, from the client it should write the context ID to the messages and from the service it should read this context ID from the messages and pass it to the upper levels.</span></span> <span data-ttu-id="1fa2c-133">Nedeniyle, bir `DurableInstanceContextChannelBase` sınıfı, tüm dayanıklı örnek bağlamı kanal uygulamaları için Özet temel sınıf olarak davranan oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-133">Because of that, a `DurableInstanceContextChannelBase` class is created that acts as the abstract base class for all durable instance context channel implementations.</span></span> <span data-ttu-id="1fa2c-134">Bu sınıf, genel durumu makine yönetim işlevleri ve uygulamak ve bağlam bilgilerini ve gelen iletileri okumak için iki korumalı üyeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-134">This class contains the common state machine management functions and two protected members to apply and read the context information to and from messages.</span></span>  
  
```  
class DurableInstanceContextChannelBase  
{  
  //…  
  protected void ApplyContext(Message message)  
  {  
    //…              
  }  
  protected string ReadContextId(Message message)  
  {  
    //…              
  }  
}  
```  
  
 <span data-ttu-id="1fa2c-135">Bu iki yöntem olun kullanımı `IContextManager` yazmak ve bağlam kimliği için veya iletisi okumak için uygulamaları.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-135">These two methods make use of `IContextManager` implementations to write and read the context ID to or from the message.</span></span> <span data-ttu-id="1fa2c-136">(`IContextManager` sözleşme tüm içerik yöneticileri için tanımlamak için kullanılan özel bir arabirim.) Kanal ya da özel bir SOAP üstbilgisi veya bir HTTP tanımlama bilgisi üstbilgisi bağlam Kimliğini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-136">(`IContextManager` is a custom interface used to define the contract for all context managers.) The channel can either include the context ID in a custom SOAP header or in a HTTP cookie header.</span></span> <span data-ttu-id="1fa2c-137">Her bağlamı Yöneticisi uygulama devraldığı `ContextManagerBase` ortak işlevsellik için tüm içerik yöneticileri içeren sınıf.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-137">Each context manager implementation inherits from the `ContextManagerBase` class that contains the common functionality for all context managers.</span></span> <span data-ttu-id="1fa2c-138">`GetContextId` Yöntemi bu sınıftaki istemciden context ID kaynaklanan için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-138">The `GetContextId` method in this class is used to originate the context ID from the client.</span></span> <span data-ttu-id="1fa2c-139">Kimliği ilk kez kaynaklanan bir içerik olduğunda, bu yöntem adı (tipik URI geçersiz dosya adı karakterleri karakter değiştirilir) uzak uç noktası adresi tarafından oluşturulan bir metin dosyasına kaydeder.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-139">When a context ID is originated for the first time, this method saves it into a text file whose name is constructed by the remote endpoint address (the invalid file name characters in the typical URIs are replaced with @ characters).</span></span>  
  
 <span data-ttu-id="1fa2c-140">Daha sonra içerik kimliği aynı uzak uç nokta için gerekli olduğunda, uygun bir dosya var olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-140">Later when the context ID is required for the same remote endpoint, it checks whether an appropriate file exists.</span></span> <span data-ttu-id="1fa2c-141">Aşması durumunda bağlam Kimliğini okur ve döndürür.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-141">If it does, it reads the context ID and returns.</span></span> <span data-ttu-id="1fa2c-142">Aksi halde yeni oluşturulan bağlam Kimliğini döndürür ve bir dosyaya kaydeder.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-142">Otherwise it returns a newly generated context ID and saves it to a file.</span></span> <span data-ttu-id="1fa2c-143">Varsayılan yapılandırma ile bu dosyalar geçerli kullanıcının temp dizininde bulunan ContextStore adlı bir dizin yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-143">With the default configuration, these files are placed in a directory called ContextStore, which resides in the current user’s temp directory.</span></span> <span data-ttu-id="1fa2c-144">Ancak bu konum bağlama öğesi kullanılarak yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-144">However this location is configurable using the binding element.</span></span>  
  
 <span data-ttu-id="1fa2c-145">İçerik kimliği taşıma için kullanılan mekanizma yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-145">The mechanism used to transport the context ID is configurable.</span></span> <span data-ttu-id="1fa2c-146">Ya da HTTP tanımlama bilgisi üstbilgisi veya özel bir SOAP üstbilgi yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-146">It could be either written to the HTTP cookie header or to a custom SOAP header.</span></span> <span data-ttu-id="1fa2c-147">Özel SOAP üstbilgi yaklaşım HTTP olmayan protokolleri (örneğin, TCP veya Named Pipes) ile bu protokolü kullanmayı mümkün kılar.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-147">The custom SOAP header approach makes it possible to use this protocol with non-HTTP protocols (for example, TCP or Named Pipes).</span></span> <span data-ttu-id="1fa2c-148">İki sınıf vardır, yani `MessageHeaderContextManager` ve `HttpCookieContextManager`, bu iki seçenek uygulayın.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-148">There are two classes, namely `MessageHeaderContextManager` and `HttpCookieContextManager`, which implement these two options.</span></span>  
  
 <span data-ttu-id="1fa2c-149">Bunların her ikisi de bağlam Kimliğini iletiye uygun şekilde yazın.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-149">Both of them write the context ID to the message appropriately.</span></span> <span data-ttu-id="1fa2c-150">Örneğin, `MessageHeaderContextManager` sınıfı yazar, bir SOAP üstbilgisini `WriteContext` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-150">For example, the `MessageHeaderContextManager` class writes it to a SOAP header in the `WriteContext` method.</span></span>  
  
```  
public override void WriteContext(Message message)  
{  
  string contextId = this.GetContextId();  
  
  MessageHeader contextHeader =  
    MessageHeader.CreateHeader(DurableInstanceContextUtility.HeaderName,  
      DurableInstanceContextUtility.HeaderNamespace,  
      contextId,   
      true);  
  
  message.Headers.Add(contextHeader);  
}   
```  
  
 <span data-ttu-id="1fa2c-151">Hem `ApplyContext` ve `ReadContextId` yöntemleri `DurableInstanceContextChannelBase` sınıfı çağırma `IContextManager.ReadContext` ve `IContextManager.WriteContext`sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-151">Both the `ApplyContext` and `ReadContextId` methods in the `DurableInstanceContextChannelBase` class invoke the `IContextManager.ReadContext` and `IContextManager.WriteContext`, respectively.</span></span> <span data-ttu-id="1fa2c-152">Ancak, bu içerik yöneticileri doğrudan tarafından oluşturulmaz `DurableInstanceContextChannelBase` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-152">However, these context managers are not directly created by the `DurableInstanceContextChannelBase` class.</span></span> <span data-ttu-id="1fa2c-153">Bunun yerine kullanır `ContextManagerFactory` bu işlemi yapmak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-153">Instead it uses the `ContextManagerFactory` class to do that job.</span></span>  
  
```  
IContextManager contextManager =  
                ContextManagerFactory.CreateContextManager(contextType,   
                this.contextStoreLocation,   
                this.endpointAddress);  
```  
  
 <span data-ttu-id="1fa2c-154">`ApplyContext` Yöntemi gönderen kanalları tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-154">The `ApplyContext` method is invoked by the sending channels.</span></span> <span data-ttu-id="1fa2c-155">Giden iletiler için bağlam kimliği yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-155">It injects the context ID to the outgoing messages.</span></span> <span data-ttu-id="1fa2c-156">`ReadContextId` Yöntemi alıcı kanalları tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-156">The `ReadContextId` method is invoked by the receiving channels.</span></span> <span data-ttu-id="1fa2c-157">Bu yöntem bağlam Kimliğini gelen iletiler kullanılabilir ve ona ekler sağlar `Properties` koleksiyonu `Message` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-157">This method ensures that the context ID is available in the incoming messages and adds it to the `Properties` collection of the `Message` class.</span></span> <span data-ttu-id="1fa2c-158">Ayrıca oluşturur bir `CommunicationException` bağlam Kimliğini okumak için arıza durumunda ve bu nedenle kanal durdurulmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-158">It also throws a `CommunicationException` in case of a failure to read the context ID and thus causes the channel to be aborted.</span></span>  
  
```  
message.Properties.Add(DurableInstanceContextUtility.ContextIdProperty, contextId);  
```  
  
 <span data-ttu-id="1fa2c-159">Devam etmeden önce kullanımını anlamak önemlidir `Properties` koleksiyonunda `Message` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-159">Before proceeding, it is important to understand the usage of the `Properties` collection in the `Message` class.</span></span> <span data-ttu-id="1fa2c-160">Genellikle, bu `Properties` koleksiyonu geçirme verilerini üst düzey kanal katmanından daha düşük olduğunda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-160">Typically, this `Properties` collection is used when passing data from lower to the upper levels from the channel layer.</span></span> <span data-ttu-id="1fa2c-161">Bu şekilde istenen verilere protokol ayrıntılarını bağımsız olarak tutarlı bir şekilde üst düzey sağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-161">This way the desired data can be provided to the upper levels in a consistent manner regardless of the protocol details.</span></span> <span data-ttu-id="1fa2c-162">Diğer bir deyişle, kanal katmanını gönderebilir ve bağlam Kimliğini bir SOAP üstbilgi ya da bir HTTP tanımlama bilgisi üstbilgisi olarak da alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-162">In other words, the channel layer can send and receive the context ID either as a SOAP header or a HTTP cookie header.</span></span> <span data-ttu-id="1fa2c-163">Ancak bu bilgileri kanal katmanını kullanılabilir hale getirir çünkü bu ayrıntılarını bilmek üst düzey için gerekli değildir `Properties` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-163">But it is not necessary for the upper levels to know about these details because the channel layer makes this information available in the `Properties` collection.</span></span>  
  
 <span data-ttu-id="1fa2c-164">Şimdi ile `DurableInstanceContextChannelBase` sınıf yerinde on (IOutputChannel IInputChannel, IOutputSessionChannel, IInputSessionChannel, IRequestChannel, IReplyChannel, IRequestSessionChannel, IReplySessionChannel, gerekli arabirimleri IDuplexChannel, da IDuplexSessionChannel öğelerini) uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-164">Now with the `DurableInstanceContextChannelBase` class in place all ten of the necessary interfaces (IOutputChannel, IInputChannel, IOutputSessionChannel, IInputSessionChannel, IRequestChannel, IReplyChannel, IRequestSessionChannel, IReplySessionChannel, IDuplexChannel, IDuplexSessionChannel) must be implemented.</span></span> <span data-ttu-id="1fa2c-165">Bunlar her kullanılabilir ileti değişim deseni (veri birimi, tek yönlü, çift yönlü ve bunların süre sonuyla çeşitleri) benzer.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-165">They resemble every available message exchange pattern (datagram, simplex, duplex and their sessionful variants).</span></span> <span data-ttu-id="1fa2c-166">Bu uygulamaların her biri devral çağrıları ve daha önce açıklanan temel sınıf `ApplyContext` ve `ReadContexId` uygun şekilde.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-166">Each of these implementations inherit the base class previously described and calls `ApplyContext` and `ReadContexId` appropriately.</span></span> <span data-ttu-id="1fa2c-167">Örneğin, `DurableInstanceContextOutputChannel` - IOutputChannel arabirimi uygulayan - çağırır `ApplyContext` yöntemi her yönteminden iletileri gönderir.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-167">For example, `DurableInstanceContextOutputChannel` - which implements the IOutputChannel interface - calls the `ApplyContext` method from each method that sends the messages.</span></span>  
  
```  
public void Send(Message message, TimeSpan timeout)  
{  
    // Apply the context information before sending the message.  
    this.ApplyContext(message);  
    //…  
}   
```  
  
 <span data-ttu-id="1fa2c-168">Diğer taraftan, `DurableInstanceContextInputChannel` -hangi uygular `IInputChannel` interface - çağrıları `ReadContextId` yöntemi her yönteminde iletilerini alır.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-168">On the other hand, `DurableInstanceContextInputChannel` - which implements the `IInputChannel` interface - calls the `ReadContextId` method in each method which receives the messages.</span></span>  
  
```  
public Message Receive(TimeSpan timeout)  
{  
    //…  
      ReadContextId(message);  
      return message;  
}  
```  
  
 <span data-ttu-id="1fa2c-169">Bunun dışında bu kanal uygulamaları bunları aşağıda kanal kanal yığınında yöntemi çağrılarına temsilci.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-169">Apart from this, these channel implementations delegate the method invocations to the channel below them in the channel stack.</span></span> <span data-ttu-id="1fa2c-170">Ancak, süre sonuyla çeşitleri bağlam Kimliğini gönderilir ve oluşturulacak oturum neden yalnızca ilk ileti için okuma emin olmak için bir temel mantığı vardır.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-170">However, sessionful variants have a basic logic to make sure that the context ID is sent and is read only for the first message that causes the session to be created.</span></span>  
  
```  
if (isFirstMessage)  
{  
//…  
    this.ApplyContext(message);  
    isFirstMessage = false;  
}  
```  
  
 <span data-ttu-id="1fa2c-171">Bu kanal uygulamaları daha sonra eklenen [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kanal çalışma zamanı tarafından `DurableInstanceContextBindingElement` sınıfı ve `DurableInstanceContextBindingElementSection` uygun şekilde sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-171">These channel implementations are then added to the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] channel runtime by the `DurableInstanceContextBindingElement` class and `DurableInstanceContextBindingElementSection` class appropriately.</span></span> <span data-ttu-id="1fa2c-172">Bkz: [HttpCookieSession](../../../../docs/framework/wcf/samples/httpcookiesession.md) kanal bağlama öğeleri ve bağlama öğesi bölümleri hakkında daha fazla ayrıntı için örnek belgeleri.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-172">See the [HttpCookieSession](../../../../docs/framework/wcf/samples/httpcookiesession.md) channel sample documentation for more details about binding elements and binding element sections.</span></span>  
  
## <a name="service-model-layer-extensions"></a><span data-ttu-id="1fa2c-173">Hizmet modeli katmanını uzantıları</span><span class="sxs-lookup"><span data-stu-id="1fa2c-173">Service Model Layer Extensions</span></span>  
 <span data-ttu-id="1fa2c-174">İçerik kimliği kanal katmanını seyahat, hizmet davranışı örneklemesi özelleştirmek için uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-174">Now that the context ID has traveled through the channel layer, the service behavior can be implemented to customize the instantiation.</span></span> <span data-ttu-id="1fa2c-175">Bu örnekte, bir Depolama Yöneticisi'ni yüklemek ve bilgisayara veya kalıcı depoya durumunu kaydetmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-175">In this sample, a storage manager is used to load and save state from or to the persistent store.</span></span> <span data-ttu-id="1fa2c-176">Daha önce açıklandığı gibi bu örnek, yedekleme deposu olarak SQL Server 2005'in kullandığı Depolama Yöneticisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-176">As explained previously, this sample provides a storage manager that uses SQL Server 2005 as its backing store.</span></span> <span data-ttu-id="1fa2c-177">Ancak, aynı zamanda bu uzantı için özel depolama mekanizmaları eklemek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-177">However, it is also possible to add custom storage mechanisms to this extension.</span></span> <span data-ttu-id="1fa2c-178">Ortak bir arabirim Bunu yapmak için tüm depolama yöneticileri tarafından uygulanmalıdır bildirildi.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-178">To do that a public interface is declared, which must be implemented by all storage managers.</span></span>  
  
```  
public interface IStorageManager  
{  
    object GetInstance(string contextId, Type type);  
    void SaveInstance(string contextId, object state);  
}  
```  
  
 <span data-ttu-id="1fa2c-179">`SqlServerStorageManager` Sınıfı içeren varsayılan `IStorageManager` uygulaması.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-179">The `SqlServerStorageManager` class contains the default `IStorageManager` implementation.</span></span> <span data-ttu-id="1fa2c-180">İçinde `SaveInstance` yöntemi belirtilen nesneyi XmlSerializer kullanarak serileştirilen ve SQL Server veritabanına kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-180">In its `SaveInstance` method the given object is serialized using the XmlSerializer and is saved to the SQL Server database.</span></span>  
  
```  
XmlSerializer serializer = new XmlSerializer(state.GetType());  
string data;  
  
using (StringWriter writer = new StringWriter(CultureInfo.InvariantCulture))  
{  
    serializer.Serialize(writer, state);  
    data = writer.ToString();  
}  
  
using (SqlConnection connection = new SqlConnection(GetConnectionString()))  
{  
    connection.Open();  
  
    string update = @"UPDATE Instances SET Instance = @instance WHERE ContextId = @contextId";  
  
    using (SqlCommand command = new SqlCommand(update, connection))  
    {  
        command.Parameters.Add("@instance", SqlDbType.VarChar, 2147483647).Value = data;  
        command.Parameters.Add("@contextId", SqlDbType.VarChar, 256).Value = contextId;  
  
        int rows = command.ExecuteNonQuery();  
  
        if (rows == 0)  
        {  
            string insert = @"INSERT INTO Instances(ContextId, Instance) VALUES(@contextId, @instance)";  
            command.CommandText = insert;  
            command.ExecuteNonQuery();  
        }  
    }  
}  
```  
  
 <span data-ttu-id="1fa2c-181">İçinde `GetInstance` yöntemi serileştirilmiş verilerini okuma için belirtilen bağlamda kimliği ve ondan oluşturulan nesne çağırana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-181">In the `GetInstance` method the serialized data is read for a given context ID and the object constructed from it is returned to the caller.</span></span>  
  
```  
object data;  
using (SqlConnection connection = new SqlConnection(GetConnectionString()))  
{  
    connection.Open();  
  
    string select = "SELECT Instance FROM Instances WHERE ContextId = @contextId";  
    using (SqlCommand command = new SqlCommand(select, connection))  
    {  
        command.Parameters.Add("@contextId", SqlDbType.VarChar, 256).Value = contextId;  
        data = command.ExecuteScalar();  
    }  
}  
  
if (data != null)  
{  
    XmlSerializer serializer = new XmlSerializer(type);  
    using (StringReader reader = new StringReader((string)data))  
    {  
        object instance = serializer.Deserialize(reader);  
        return instance;  
    }  
}  
```  
  
 <span data-ttu-id="1fa2c-182">Kullanıcılar bu depolama yöneticileri doğrudan örneği oluşturmak için beklenen değil.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-182">Users of these storage managers are not supposed to instantiate them directly.</span></span> <span data-ttu-id="1fa2c-183">Kullandıkları `StorageManagerFactory` Depolama Yöneticisi oluşturma ayrıntılarının soyutlar sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-183">They use the `StorageManagerFactory` class, which abstracts from the storage manager creation details.</span></span> <span data-ttu-id="1fa2c-184">Bu sınıf bir statik, üyenin `GetStorageManager`, belirli Depolama Yöneticisi türünün bir örneği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-184">This class has one static member, `GetStorageManager`, which creates an instance of a given storage manager type.</span></span> <span data-ttu-id="1fa2c-185">Tür parametresi ise `null`, bu yöntem varsayılan örneği oluşturur `SqlServerStorageManager` sınıfı ve döndürür.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-185">If the type parameter is `null`, this method creates an instance of the default `SqlServerStorageManager` class and returns it.</span></span> <span data-ttu-id="1fa2c-186">Ayrıca bunu uygulayan emin olmak için belirtilen tür doğrular `IStorageManager` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-186">It also validates the given type to make sure that it implements the `IStorageManager` interface.</span></span>  
  
```  
public static IStorageManager GetStorageManager(Type storageManagerType)  
{  
IStorageManager storageManager = null;  
  
if (storageManagerType == null)  
{  
    return new SqlServerStorageManager();  
}  
else  
{  
    object obj = Activator.CreateInstance(storageManagerType);  
  
    // Throw if the specified storage manager type does not  
    // implement IStorageManager.  
    if (obj is IStorageManager)  
    {  
        storageManager = (IStorageManager)obj;  
    }  
    else  
    {  
        throw new InvalidOperationException(  
                  ResourceHelper.GetString("ExInvalidStorageManager"));  
    }  
  
    return storageManager;  
}                  
}   
```  
  
 <span data-ttu-id="1fa2c-187">Okumak ve kalıcı depolama biriminden örnekleri yazmak için gerekli altyapıyı uygulanır.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-187">The necessary infrastructure to read and write instances from the persistent storage is implemented.</span></span> <span data-ttu-id="1fa2c-188">Şimdi hizmet davranışını değiştirmek için gerekli adımları alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-188">Now the necessary steps to change the service behavior have to be taken.</span></span>  
  
 <span data-ttu-id="1fa2c-189">Bu işlem ilk adım olarak geçerli InstanceContext kanal katmanını gelen bağlam Kimliğini kaydetmek sahibiz.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-189">As the first step of this process we have to save the context ID, which came through the channel layer to the current InstanceContext.</span></span> <span data-ttu-id="1fa2c-190">InstanceContext arasında bağlantı gibi davranır bir çalışma zamanı bileşeni olan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dağıtıcısı ve hizmet örneği.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-190">InstanceContext is a runtime component that acts as the link between the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dispatcher and the service instance.</span></span> <span data-ttu-id="1fa2c-191">Ek durum ve hizmet örneğine davranışı sağlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-191">It can be used to provide additional state and behavior to the service instance.</span></span> <span data-ttu-id="1fa2c-192">Süre sonuyla iletişiminde bağlam Kimliğini yalnızca ilk iletinin gönderildiği için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-192">This is essential because in sessionful communication the context ID is sent only with the first message.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1fa2c-193">Yeni durum ve Genişletilebilir nesne modeli kullanarak davranışı ekleyerek kendi InstanceContext çalışma zamanı bileşeni genişletme sağlar.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-193"> allows extending its InstanceContext runtime component by adding a new state and behavior using its extensible object pattern.</span></span> <span data-ttu-id="1fa2c-194">Genişletilebilir object deseni kullanılan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ya da mevcut çalışma zamanı sınıflarını yeni işlevselliği ile genişletmek veya yeni durumu özellik için bir nesne eklemek için.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-194">The extensible object pattern is used in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] to either extend existing runtime classes with new functionality or to add new state features to an object.</span></span> <span data-ttu-id="1fa2c-195">Genişletilebilir nesne modelinde - IExtensibleObject üç arabirimi olan\<T >, IExtension\<T > ve IExtensionCollection\<T >:</span><span class="sxs-lookup"><span data-stu-id="1fa2c-195">There are three interfaces in the extensible object pattern - IExtensibleObject\<T>, IExtension\<T>, and IExtensionCollection\<T>:</span></span>  
  
-   <span data-ttu-id="1fa2c-196">IExtensibleObject\<T > arabirimini işlevleriyle özelleştirme uzantılarına izin ver nesneler tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-196">The IExtensibleObject\<T> interface is implemented by objects that allow extensions that customize their functionality.</span></span>  
  
-   <span data-ttu-id="1fa2c-197">IExtension\<T > arabirimini uzantıları t türü sınıfların nesneleri tarafından uygulanan</span><span class="sxs-lookup"><span data-stu-id="1fa2c-197">The IExtension\<T> interface is implemented by objects that are extensions of classes of type T.</span></span>  
  
-   <span data-ttu-id="1fa2c-198">IExtensionCollection\<T > arabirimini türlerine göre IExtensions almak için izin veren IExtensions koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-198">The IExtensionCollection\<T> interface is a collection of IExtensions that allows for retrieving IExtensions by their type.</span></span>  
  
 <span data-ttu-id="1fa2c-199">Bu nedenle bir InstanceContextExtension sınıfı IExtension arabirimini uygulayan ve bağlam kimliğini kaydetmek için gerekli durumu tanımlayan oluşturulmalıdır</span><span class="sxs-lookup"><span data-stu-id="1fa2c-199">Therefore an InstanceContextExtension class should be created that implements the IExtension interface and defines the required state to save the context ID.</span></span> <span data-ttu-id="1fa2c-200">Bu sınıf ayrıca Depolama Yöneticisi kullanılan tutmak için durumu sağlar.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-200">This class also provides the state to hold the storage manager being used.</span></span> <span data-ttu-id="1fa2c-201">Yeni durum kaydedildikten sonra bunu değiştirmek mümkün olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-201">Once the new state is saved, it should not be possible to modify it.</span></span> <span data-ttu-id="1fa2c-202">Bu nedenle durumu sağlanan ve oluşturulan ve ardından yalnızca erişilebilir salt okunur özellikler kullanarak aynı anda örneğine kaydedildi.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-202">Therefore the state is provided and saved to the instance at the time it is being constructed and then only accessible using read-only properties.</span></span>  
  
```  
// Constructor  
public DurableInstanceContextExtension(string contextId,   
            IStorageManager storageManager)  
{  
    this.contextId = contextId;  
    this.storageManager = storageManager;              
}  
  
// Read only properties  
public string ContextId  
{  
    get { return this.contextId; }  
}  
  
public IStorageManager StorageManager  
{  
    get { return this.storageManager; }              
}   
```  
  
 <span data-ttu-id="1fa2c-203">InstanceContextInitializer sınıfı IInstanceContextInitializer arabirimini uygulayan ve örnek bağlamı uzantısını yapılandırılan InstanceContext uzantıları koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-203">The InstanceContextInitializer class implements the IInstanceContextInitializer interface and adds the instance context extension to the Extensions collection of the InstanceContext being constructed.</span></span>  
  
```  
public void Initialize(InstanceContext instanceContext, Message message)  
{  
    string contextId =   
  (string)message.Properties[DurableInstanceContextUtility.ContextIdProperty];  
  
    DurableInstanceContextExtension extension =  
                new DurableInstanceContextExtension(contextId,   
                     storageManager);  
    instanceContext.Extensions.Add(extension);  
}  
```  
  
 <span data-ttu-id="1fa2c-204">İçerik kimliği okuma daha önce açıklandığı gibi `Properties` koleksiyonu `Message` sınıfı ve uzantı sınıfı oluşturucuya geçirilen.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-204">As described earlier the context ID is read from the `Properties` collection of the `Message` class and passed to the constructor of the extension class.</span></span> <span data-ttu-id="1fa2c-205">Bu, tutarlı bir şekilde katmanlar arasında bilgi nasıl değiştirilebilir gösterir.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-205">This demonstrates how information can be exchanged between the layers in a consistent manner.</span></span>  
  
 <span data-ttu-id="1fa2c-206">Önemli bir sonraki adım, hizmet örneği oluşturma işlemini geçersiz kılma.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-206">The next important step is overriding the service instance creation process.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="1fa2c-207">Özel örneklemesi davranışları uygulama ve IInstanceProvider arabirimini kullanarak çalışma zamanı kadar takma sağlar.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-207"> allows implementing custom instantiation behaviors and hooking them up to the runtime using the IInstanceProvider interface.</span></span> <span data-ttu-id="1fa2c-208">Yeni `InstanceProvider` sınıfı, bu işlemi yapmak için uygulanır.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-208">The new `InstanceProvider` class is implemented to do that job.</span></span> <span data-ttu-id="1fa2c-209">Oluşturucuda örneği Sağlayıcısı'ndan beklenen hizmet türünü kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-209">In the constructor the service type expected from the instance provider is accepted.</span></span> <span data-ttu-id="1fa2c-210">Daha sonra bu yeni örnekleri oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-210">Later this is used to create new instances.</span></span> <span data-ttu-id="1fa2c-211">İçinde `GetInstance` uygulama Depolama Yöneticisi örneği oluşturulur kalıcı bir örneğin aranıyor.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-211">In the `GetInstance` implementation an instance of a storage manager is created looking for a persisted instance.</span></span> <span data-ttu-id="1fa2c-212">Döndürürse `null` hizmet türü yeni bir örneğini örneği ve yapana.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-212">If it returns `null` then a new instance of the service type is instantiated and returned to the caller.</span></span>  
  
```  
public object GetInstance(InstanceContext instanceContext, Message message)  
{  
    object instance = null;  
  
    DurableInstanceContextExtension extension =  
    instanceContext.Extensions.Find<DurableInstanceContextExtension>();  
  
    string contextId = extension.ContextId;  
    IStorageManager storageManager = extension.StorageManager;              
  
    instance = storageManager.GetInstance(contextId, serviceType);          
  
    if (instance == null)  
    {  
        instance = Activator.CreateInstance(serviceType);  
    }  
  
    return instance;  
}  
```  
  
 <span data-ttu-id="1fa2c-213">Sonraki önemli bir adım yüklemektir `InstanceContextExtension`, `InstanceContextInitializer` ve `InstanceProvider` hizmet modeli çalışma zamanı sınıflara.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-213">The next important step is to install the `InstanceContextExtension`, `InstanceContextInitializer` and `InstanceProvider` classes into the service model runtime.</span></span> <span data-ttu-id="1fa2c-214">Özel bir öznitelik davranışı yüklemek için hizmet uygulaması sınıfları işaretlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-214">A custom attribute could be used to mark the service implementation classes to install the behavior.</span></span> <span data-ttu-id="1fa2c-215">`DurableInstanceContextAttribute` Bu öznitelik için uygulama içerir ve bunu uygulayan `IServiceBehavior` tüm hizmet çalışma zamanı genişletmek için arabirim.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-215">The `DurableInstanceContextAttribute` contains the implementation for this attribute and it implements the `IServiceBehavior` interface to extend the entire service runtime.</span></span>  
  
 <span data-ttu-id="1fa2c-216">Bu sınıf, kullanılacak Depolama Yöneticisi türü kabul eden bir özelliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-216">This class has a property that accepts the type of the storage manager to be used.</span></span> <span data-ttu-id="1fa2c-217">Bu şekilde, kendi belirtmek kullanıcıların uygulama sağlar `IStorageManager` bu öznitelik parametre olarak uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-217">In this way the implementation enables the users to specify their own `IStorageManager` implementation as parameter of this attribute.</span></span>  
  
 <span data-ttu-id="1fa2c-218">İçinde `ApplyDispatchBehavior` uygulama `InstanceContextMode` geçerli `ServiceBehavior` özniteliği doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-218">In the `ApplyDispatchBehavior` implementation the `InstanceContextMode` of the current `ServiceBehavior` attribute is being verified.</span></span> <span data-ttu-id="1fa2c-219">Bu özellik tekliye ayarlarsanız, dayanıklı depolamasına etkinleştirme mümkün değildir ve bir `InvalidOperationException` konak bildirmek için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-219">If this property is set to Singleton, enabling durable instancing is not possible and an `InvalidOperationException` is thrown to notify the host.</span></span>  
  
```  
ServiceBehaviorAttribute serviceBehavior =  
    serviceDescription.Behaviors.Find<ServiceBehaviorAttribute>();  
  
if (serviceBehavior != null &&  
     serviceBehavior.InstanceContextMode == InstanceContextMode.Single)  
{  
    throw new InvalidOperationException(  
       ResourceHelper.GetString("ExSingeltonInstancingNotSupported"));  
}  
```  
  
 <span data-ttu-id="1fa2c-220">Bundan sonra Depolama Yöneticisi, örnek bağlamı başlatıcı ve örnek sağlayıcısı örnekleri oluşturulur ve yüklü `DispatchRuntime` için her bir uç noktası oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-220">After this the instances of the storage manager, instance context initializer, and the instance provider are created and installed in the `DispatchRuntime` created for every endpoint.</span></span>  
  
```  
IStorageManager storageManager =   
    StorageManagerFactory.GetStorageManager(storageManagerType);  
  
InstanceContextInitializer contextInitializer =  
    new InstanceContextInitializer(storageManager);  
  
InstanceProvider instanceProvider =  
    new InstanceProvider(description.ServiceType);  
  
foreach (ChannelDispatcherBase cdb in serviceHostBase.ChannelDispatchers)  
{  
    ChannelDispatcher cd = cdb as ChannelDispatcher;  
  
    if (cd != null)  
    {  
        foreach (EndpointDispatcher ed in cd.Endpoints)  
        {  
            ed.DispatchRuntime.InstanceContextInitializers.Add(contextInitializer);  
            ed.DispatchRuntime.InstanceProvider = instanceProvider;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="1fa2c-221">Şu ana kadar Özet olarak, bu örnek özel kablo protokolü özel bağlam kimliği exchange için etkinleştirilmiş bir kanal üretilen ve aynı zamanda örnekleri kalıcı depolama biriminden yüklemek için davranış depolamasına varsayılan üzerine yazar.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-221">In summary so far, this sample has produced a channel that enabled the custom wire protocol for custom context ID exchange and it also overwrites the default instancing behavior to load the instances from the persistent storage.</span></span>  
  
 <span data-ttu-id="1fa2c-222">Ne sol, hizmet örneği kalıcı depolama alanına kaydetmek için bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-222">What is left is a way to save the service instance to the persistent storage.</span></span> <span data-ttu-id="1fa2c-223">Daha önce açıklandığı gibi zaten var. durumunda kaydetmek için gerekli işlevselliği bir `IStorageManager` uygulaması.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-223">As discussed previously, there is already the required functionality to save the state in an `IStorageManager` implementation.</span></span> <span data-ttu-id="1fa2c-224">Biz şimdi bu ile tümleştirmeniz gerekir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-224">We now must integrate this with the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] runtime.</span></span> <span data-ttu-id="1fa2c-225">Başka bir öznitelik gerekli olan hizmet uygulaması sınıfı yöntemleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-225">Another attribute is required that is applicable to the methods in the service implementation class.</span></span> <span data-ttu-id="1fa2c-226">Bu öznitelik hizmet örneğinin durumunu değiştirme yöntemleri uygulanması gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-226">This attribute is supposed to be applied to the methods that change the state of the service instance.</span></span>  
  
 <span data-ttu-id="1fa2c-227">`SaveStateAttribute` Sınıfı bu işlev uygular.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-227">The `SaveStateAttribute` class implements this functionality.</span></span> <span data-ttu-id="1fa2c-228">Ayrıca uygulayan `IOperationBehavior` değiştirmek için sınıf [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] her bir işlemin çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-228">It also implements `IOperationBehavior` class to modify the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] runtime for each operation.</span></span> <span data-ttu-id="1fa2c-229">Bir yöntem bu özniteliği ile işaretlendiğinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] çalışma zamanı çağırır `ApplyBehavior` yöntemi uygun sırasında `DispatchOperation` oluşturulmuyor.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-229">When a method is marked with this attribute, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] runtime invokes the `ApplyBehavior` method while the appropriate `DispatchOperation` is being constructed.</span></span> <span data-ttu-id="1fa2c-230">Bu yöntem uygulamasında tek satırlık bir kod yoktur:</span><span class="sxs-lookup"><span data-stu-id="1fa2c-230">In this method implementation there is single line of code:</span></span>  
  
```  
dispatch.Invoker = new OperationInvoker(dispatch.Invoker);  
```  
  
 <span data-ttu-id="1fa2c-231">Bu yönerge bir örneğini oluşturur `OperationInvoker` yazın ve atar `Invoker` özelliği `DispatchOperation` oluşturulamıyor.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-231">This instruction creates an instance of `OperationInvoker` type and assigns it to the `Invoker` property of the `DispatchOperation` being constructed.</span></span> <span data-ttu-id="1fa2c-232">`OperationInvoker` İçin oluşturulan varsayılan işlemi çağırıcı için sarmalayıcı sınıftır `DispatchOperation`.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-232">The `OperationInvoker` class is a wrapper for the default operation invoker created for the `DispatchOperation`.</span></span> <span data-ttu-id="1fa2c-233">Bu sınıf uygulayan `IOperationInvoker` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-233">This class implements the `IOperationInvoker` interface.</span></span> <span data-ttu-id="1fa2c-234">İçinde `Invoke` yöntem uygulaması iç işlem çağırıcı gerçek yöntem çağırma temsilcisi.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-234">In the `Invoke` method implementation the actual method invocation is delegated to the inner operation invoker.</span></span> <span data-ttu-id="1fa2c-235">Ancak, Depolama Yöneticisi'nde sonuçları dönmeden önce `InstanceContext` hizmet örneği kaydetmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-235">However, before returning the results the storage manager in the `InstanceContext` is used to save the service instance.</span></span>  
  
```  
object result = innerOperationInvoker.Invoke(instance,  
    inputs, out outputs);  
  
// Save the instance using the storage manager saved in the   
// current InstanceContext.  
InstanceContextExtension extension =  
    OperationContext.Current.InstanceContext.Extensions.Find<InstanceContextExtension>();  
  
extension.StorageManager.SaveInstance(extension.ContextId, instance);  
return result;  
```  
  
## <a name="using-the-extension"></a><span data-ttu-id="1fa2c-236">Uzantı kullanma</span><span class="sxs-lookup"><span data-stu-id="1fa2c-236">Using the Extension</span></span>  
 <span data-ttu-id="1fa2c-237">Kanal katman ve hizmet modeli katmanını uzantıları bitti hem de artık kullanılabilir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-237">Both the channel layer and service model layer extensions are done and they can now be used in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications.</span></span> <span data-ttu-id="1fa2c-238">Özel bağlama kullanma kanal yığına kanal eklemek ve uygun özniteliklere sahip hizmet uygulaması sınıfları işaretlemek hizmetler sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-238">Services have to add the channel into the channel stack using a custom binding and then mark the service implementation classes with the appropriate attributes.</span></span>  
  
```  
[DurableInstanceContext]  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
public class ShoppingCart : IShoppingCart  
{  
//…  
     [SaveState]  
     public int AddItem(string item)  
     {  
         //…  
     }  
//…  
 }  
```  
  
 <span data-ttu-id="1fa2c-239">İstemci uygulamaları DurableInstanceContextChannel özel bağlama kullanma kanal yığına eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-239">Client applications must add the DurableInstanceContextChannel into the channel stack using a custom binding.</span></span> <span data-ttu-id="1fa2c-240">Kanalı yapılandırma dosyasında bildirimli olarak yapılandırmak için bağlama öğesi bölümü bağlama öğesi uzantıları koleksiyona eklenmesi gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-240">To configure the channel declaratively in the configuration file, the binding element section has to be added to the binding element extensions collection.</span></span>  
  
```xml  
<system.serviceModel>  
 <extensions>  
   <bindingElementExtensions>  
     <add name="durableInstanceContext"  
type="Microsoft.ServiceModel.Samples.DurableInstanceContextBindingElementSection, DurableInstanceContextExtension, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null"/>  
   </bindingElementExtensions>  
 </extensions>  
```  
  
 <span data-ttu-id="1fa2c-241">Şimdi bağlama öğesi diğer standart bağlama öğeleri gibi özel bağlama ile birlikte kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="1fa2c-241">Now the binding element can be used with a custom binding just like other standard binding elements:</span></span>  
  
```xml  
<bindings>  
 <customBinding>  
   <binding name="TextOverHttp">  
     <durableInstanceContext contextType="HttpCookie"/>             
     <reliableSession />  
     <textMessageEncoding />  
     <httpTransport />  
   </binding>  
 </customBinding>  
</bindings>  
```  
  
## <a name="conclusion"></a><span data-ttu-id="1fa2c-242">Sonuç</span><span class="sxs-lookup"><span data-stu-id="1fa2c-242">Conclusion</span></span>  
 <span data-ttu-id="1fa2c-243">Bu örnek özel protokol kanal oluşturma ve etkinleştirmek için hizmet davranışını özelleştirmek nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-243">This sample showed how to create a custom protocol channel and how to customize the service behavior to enable it.</span></span>  
  
 <span data-ttu-id="1fa2c-244">Uzantıyı daha fazla kullanıcıları izin vererek geliştirilebilir `IStorageManager` yapılandırma bölümünü kullanarak uygulama.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-244">The extension can be further improved by letting users specify the `IStorageManager` implementation using a configuration section.</span></span> <span data-ttu-id="1fa2c-245">Hizmet koduna derlemeden yedekleme deposu değiştirmek mümkün kılar.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-245">This makes it possible to modify the backing store without recompiling the service code.</span></span>  
  
 <span data-ttu-id="1fa2c-246">Ayrıca bir sınıf uygulama yararlanmaya (örneğin, `StateBag`), örneğinin durumunu saklar.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-246">Furthermore you could try to implement a class (for example, `StateBag`), which encapsulates the state of the instance.</span></span> <span data-ttu-id="1fa2c-247">Bu sınıf, durumu değiştiğinde sürdürmek için sorumludur.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-247">That class is responsible for persisting the state whenever it changes.</span></span> <span data-ttu-id="1fa2c-248">Kaçının kullanarak bu şekilde `SaveState` özniteliği ve kalıcı iş daha doğru bir şekilde gerçekleştirebilirsiniz (örneğin, durum kalıcı durumu gerçekte değiştirildiğinde kaydetme yerine her bir yöntemle zaman zaman `SaveState` özniteliği olarak adlandırılır).</span><span class="sxs-lookup"><span data-stu-id="1fa2c-248">This way you can avoid using the `SaveState` attribute and perform the persisting work more accurately (for example, you could persist the state when the state is actually changed rather than saving it each time when a method with the `SaveState` attribute is called).</span></span>  
  
 <span data-ttu-id="1fa2c-249">Örneği çalıştırdığınızda, aşağıdaki çıktısı görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-249">When you run the sample, the following output is displayed.</span></span> <span data-ttu-id="1fa2c-250">İstemci alışveriş sepetine iki öğe ekler ve hizmetinden'da kendi alışveriş sepeti öğeleri listesini alır.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-250">The client adds two items to its shopping cart and then gets the list of items in its shopping cart from the service.</span></span> <span data-ttu-id="1fa2c-251">Her konsol penceresinde hizmet ve istemci kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-251">Press ENTER in each console window to shut down the service and client.</span></span>  
  
```  
Enter the name of the product: apples  
Enter the name of the product: bananas  
  
Shopping cart currently contains the following items.  
apples  
bananas  
Press ENTER to shut down client  
```  
  
> [!NOTE]
>  <span data-ttu-id="1fa2c-252">Hizmet yeniden veritabanı dosyasının üzerine yazar.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-252">Rebuilding the service overwrites the database file.</span></span> <span data-ttu-id="1fa2c-253">Birden çok örnek çalıştırmaları arasında korunur durumunu izlemek için örnek çalışmaları arasında yeniden değil emin olun.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-253">To observe state preserved across multiple runs of the sample, be sure not to rebuild the sample between runs.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1fa2c-254">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="1fa2c-254">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="1fa2c-255">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1fa2c-255">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="1fa2c-256">Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1fa2c-256">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="1fa2c-257">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1fa2c-257">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1fa2c-258">SQL Server 2005 veya SQL Express 2005'in bu örneği çalıştırmak için çalıştırıyor olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-258">You must be running SQL Server 2005 or SQL Express 2005 to run this sample.</span></span> <span data-ttu-id="1fa2c-259">SQL Server 2005 çalıştırıyorsanız, hizmetin bağlantı dizesi yapılandırmasını değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-259">If you are running SQL Server 2005, you must modify the configuration of the service's connection string.</span></span> <span data-ttu-id="1fa2c-260">Makineler arası çalıştırırken, SQL Server yalnızca sunucu makinesinde gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-260">When running cross-machine, SQL Server is only required on the server machine.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1fa2c-261">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-261">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1fa2c-262">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-262">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="1fa2c-263">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-263">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1fa2c-264">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-264">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Durable`  
  
## <a name="see-also"></a><span data-ttu-id="1fa2c-265">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1fa2c-265">See Also</span></span>
