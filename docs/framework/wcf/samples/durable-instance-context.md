---
title: Dayanıklı Örnek Bağlamı
ms.date: 03/30/2017
ms.assetid: 97bc2994-5a2c-47c7-927a-c4cd273153df
ms.openlocfilehash: 25772e7f119ddd5a144d223f402e815380b3eba5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59773382"
---
# <a name="durable-instance-context"></a><span data-ttu-id="793ab-102">Dayanıklı Örnek Bağlamı</span><span class="sxs-lookup"><span data-stu-id="793ab-102">Durable Instance Context</span></span>
<span data-ttu-id="793ab-103">Bu örnek nasıl özelleştirileceğini dayanıklı örnek bağlamı etkinleştirmek için Windows Communication Foundation (WCF) çalışma zamanı gösterir.</span><span class="sxs-lookup"><span data-stu-id="793ab-103">This sample demonstrates how to customize the Windows Communication Foundation (WCF) runtime to enable durable instance contexts.</span></span> <span data-ttu-id="793ab-104">SQL Server 2005 (SQL Server 2005 Express bu durumda), yedekleme deposu olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="793ab-104">It uses SQL Server 2005 as its backing store (SQL Server 2005 Express in this case).</span></span> <span data-ttu-id="793ab-105">Ancak, ayrıca özel depolama mekanizmaları erişmek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="793ab-105">However, it also provides a way to access custom storage mechanisms.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="793ab-106">Bu örnek için Kurulum yordamı ve derleme yönergelerini, bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="793ab-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="793ab-107">Bu örnek, kanal katmanını hem de WCF hizmet modeli katmanını genişletme içerir.</span><span class="sxs-lookup"><span data-stu-id="793ab-107">This sample involves extending both the channel layer and the service model layer of the WCF.</span></span> <span data-ttu-id="793ab-108">Bu nedenle uygulama ayrıntılarına geçmeden önce temel kavramları anlamak gereklidir.</span><span class="sxs-lookup"><span data-stu-id="793ab-108">Therefore it is necessary to understand the underlying concepts before going into the implementation details.</span></span>  
  
 <span data-ttu-id="793ab-109">Dayanıklı örnek bağlamı gerçek dünya senaryolarında genellikle bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="793ab-109">Durable instance contexts can be found in the real world scenarios quite often.</span></span> <span data-ttu-id="793ab-110">Alışveriş sepeti uygulaması, örneğin, yarı yarıya aracılığıyla alışveriş duraklatma ve başka bir gün devam özelliğine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="793ab-110">A shopping cart application for example, has the ability to pause shopping halfway through and continue it on another day.</span></span> <span data-ttu-id="793ab-111">Böylece biz alışveriş sepetini sonraki günün ziyaret ettiğinizde, bizim orijinal bağlamdaki geri yüklenir.</span><span class="sxs-lookup"><span data-stu-id="793ab-111">So that when we visit the shopping cart the next day, our original context is restored.</span></span> <span data-ttu-id="793ab-112">Biz değilken alışveriş sepeti uygulaması (sunucu) alışveriş sepeti örneği korumaz dikkat edin önemlidir.</span><span class="sxs-lookup"><span data-stu-id="793ab-112">It is important to note that the shopping cart application (on the server) does not maintain the shopping cart instance while we are disconnected.</span></span> <span data-ttu-id="793ab-113">Bunun yerine, bir kalıcı depolama ortamı durumuna devam ediyorsa ve geri yüklenen bağlamı için yeni bir örneği oluşturulurken kullanır.</span><span class="sxs-lookup"><span data-stu-id="793ab-113">Instead, it persists its state into a durable storage media and uses it when constructing a new instance for the restored context.</span></span> <span data-ttu-id="793ab-114">Bu nedenle aynı bağlamının hizmet verebilir hizmet örneği önceki örnekle aynı değil (diğer bir deyişle, aynı bellek adresi yok).</span><span class="sxs-lookup"><span data-stu-id="793ab-114">Therefore the service instance that may service for the same context is not the same as the previous instance (that is, it does not have the same memory address).</span></span>  
  
 <span data-ttu-id="793ab-115">Dayanıklı örnek bağlamı yapan bir bağlam kimliği istemci ve hizmet arasında küçük bir protokolü tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="793ab-115">Durable instance context is made possible by a small protocol that exchanges a context ID between the client and service.</span></span> <span data-ttu-id="793ab-116">Bu bağlam Kimliğini istemcide oluşturulur ve Hizmeti'ne aktarılan.</span><span class="sxs-lookup"><span data-stu-id="793ab-116">This context ID is created on the client and transmitted to the service.</span></span> <span data-ttu-id="793ab-117">Hizmet çalışma zamanı hizmet örneği oluşturulduğunda, bu bağlam Kimliğine karşılık gelen bir kalıcı depolama alanından kalıcı durum yüklemeye çalışır (varsayılan olarak bu, bir SQL Server 2005 veritabanını'dir).</span><span class="sxs-lookup"><span data-stu-id="793ab-117">When the service instance is created, the service runtime tries to load the persisted state that corresponds to this context ID from a persistent storage (by default it is a SQL Server 2005 database).</span></span> <span data-ttu-id="793ab-118">Yeni örnek varsayılan durumuna sahipse durumu olmadan kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="793ab-118">If no state is available the new instance has its default state.</span></span> <span data-ttu-id="793ab-119">Hizmet uygulaması, çalışma zamanı başlatma sonrasında hizmet örneği kaydedebilirsiniz hizmet uygulama durumunu değiştiren işlemleri işaretlemek için özel bir öznitelik kullanır.</span><span class="sxs-lookup"><span data-stu-id="793ab-119">The service implementation uses a custom attribute to mark operations that change the state of the service implementation so that the runtime can save the service instance after invoking them.</span></span>  
  
 <span data-ttu-id="793ab-120">Önceki açıklamaya göre iki adımı kolayca kaydetme amacına ulaşmanız için ayırt edilebilir:</span><span class="sxs-lookup"><span data-stu-id="793ab-120">By the previous description, two steps can easily be distinguished to achieve the goal:</span></span>  
  
1. <span data-ttu-id="793ab-121">İçerik kimliği yürütmek için kablo üzerinde giden ileti değiştirin</span><span class="sxs-lookup"><span data-stu-id="793ab-121">Change the message that goes on the wire to carry the context ID.</span></span>  
  
2. <span data-ttu-id="793ab-122">Özel örneklemesini mantığını uygulamak için hizmet yerel davranışını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="793ab-122">Change the service local behavior to implement custom instancing logic.</span></span>  
  
 <span data-ttu-id="793ab-123">Kablodaki iletileri listesindeki ilk öğe etkilediği için özel bir kanal uygulanması gerekir ve kanal katmana aşılayın.</span><span class="sxs-lookup"><span data-stu-id="793ab-123">Because the first one in the list affects the messages on the wire it should be implemented as a custom channel and be hooked up to the channel layer.</span></span> <span data-ttu-id="793ab-124">İkincisi yalnızca hizmet yerel davranışını etkiler ve bu nedenle birkaç hizmet genişletilebilirlik noktaları genişleterek uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="793ab-124">The latter only affects the service local behavior and therefore can be implemented by extending several service extensibility points.</span></span> <span data-ttu-id="793ab-125">Sonraki birkaç bölümde her biri bu uzantıları ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="793ab-125">In the next few sections, each of these extensions are discussed.</span></span>  
  
## <a name="durable-instancecontext-channel"></a><span data-ttu-id="793ab-126">Dayanıklı InstanceContext kanal</span><span class="sxs-lookup"><span data-stu-id="793ab-126">Durable InstanceContext Channel</span></span>  
 <span data-ttu-id="793ab-127">Bakmak için ilk şey, bir kanal katman uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="793ab-127">The first thing to look at is a channel layer extension.</span></span> <span data-ttu-id="793ab-128">Özel bir kanalda yazma ilk adımı, kanal iletişimi yapısına karar vermektir.</span><span class="sxs-lookup"><span data-stu-id="793ab-128">The first step in writing a custom channel is to decide the communication structure of the channel.</span></span> <span data-ttu-id="793ab-129">Yeni bir kablo protokolünü tanıtılan kanal kanal yığınında neredeyse herhangi bir kanal ile çalışması gerekir.</span><span class="sxs-lookup"><span data-stu-id="793ab-129">As a new wire protocol is being introduced the channel should work with almost any other channel in the channel stack.</span></span> <span data-ttu-id="793ab-130">Bu nedenle, tüm ileti exchange desenleri desteklemelidir.</span><span class="sxs-lookup"><span data-stu-id="793ab-130">Therefore it should support all the message exchange patterns.</span></span> <span data-ttu-id="793ab-131">Ancak, temel işlevlerini kanal iletişimi yapısını bağımsız olarak aynıdır.</span><span class="sxs-lookup"><span data-stu-id="793ab-131">However, the core functionality of the channel is the same regardless of its communication structure.</span></span> <span data-ttu-id="793ab-132">Daha açık belirtmek gerekirse istemciden gelen iletileri bağlam Kimliğini yazın ve hizmetten okunduğunu bu bağlam Kimliğini ve üst düzeylere geçirin.</span><span class="sxs-lookup"><span data-stu-id="793ab-132">More specifically, from the client it should write the context ID to the messages and from the service it should read this context ID from the messages and pass it to the upper levels.</span></span> <span data-ttu-id="793ab-133">Nedeniyle, bir `DurableInstanceContextChannelBase` sınıfı tüm dayanıklı örnek bağlamı kanal uygulamaları için soyut temel sınıf görevi gören oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="793ab-133">Because of that, a `DurableInstanceContextChannelBase` class is created that acts as the abstract base class for all durable instance context channel implementations.</span></span> <span data-ttu-id="793ab-134">Bu sınıf, durum makine yaygın yönetim işlevlerine ve uygulamak ve bağlam bilgisi ve gelen iletileri okumak için iki korumalı üyeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="793ab-134">This class contains the common state machine management functions and two protected members to apply and read the context information to and from messages.</span></span>  
  
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
  
 <span data-ttu-id="793ab-135">Bu iki yöntem olun kullanım `IContextManager` bağlam kimliği için veya iletinin okunup yazılacağını uygulamaları.</span><span class="sxs-lookup"><span data-stu-id="793ab-135">These two methods make use of `IContextManager` implementations to write and read the context ID to or from the message.</span></span> <span data-ttu-id="793ab-136">(`IContextManager` tüm içerik yöneticileri için anlaşma tanımlamak için kullanılan özel bir arabirim.) Kanal ya da özel bir SOAP üst bilgi ya da bir HTTP tanımlama bilgisi üstbilgisi bağlam Kimliğini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="793ab-136">(`IContextManager` is a custom interface used to define the contract for all context managers.) The channel can either include the context ID in a custom SOAP header or in a HTTP cookie header.</span></span> <span data-ttu-id="793ab-137">Her İçerik Yöneticisi uygulama devraldığı `ContextManagerBase` ortak işlevsellik için tüm içerik yöneticileri içeren sınıf.</span><span class="sxs-lookup"><span data-stu-id="793ab-137">Each context manager implementation inherits from the `ContextManagerBase` class that contains the common functionality for all context managers.</span></span> <span data-ttu-id="793ab-138">`GetContextId` Yöntemi bu sınıftaki istemciden bağlam Kimliğini kaynaklanan için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="793ab-138">The `GetContextId` method in this class is used to originate the context ID from the client.</span></span> <span data-ttu-id="793ab-139">KODU ilk kez kaynaklı bir içerik olduğunda, bu yöntem adı (tipik bir URI'leri geçersiz dosya adı karakterleri içeren karakter değiştirilir) uzak uç nokta adresine göre oluşturulmuş olan bir metin dosyasına kaydeder.</span><span class="sxs-lookup"><span data-stu-id="793ab-139">When a context ID is originated for the first time, this method saves it into a text file whose name is constructed by the remote endpoint address (the invalid file name characters in the typical URIs are replaced with @ characters).</span></span>  
  
 <span data-ttu-id="793ab-140">Daha sonra bağlam Kimliğini aynı uzak uç nokta için gerekli olduğunda, uygun bir dosyanın var olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="793ab-140">Later when the context ID is required for the same remote endpoint, it checks whether an appropriate file exists.</span></span> <span data-ttu-id="793ab-141">Varsa, bağlam Kimliğini okur ve döndürür.</span><span class="sxs-lookup"><span data-stu-id="793ab-141">If it does, it reads the context ID and returns.</span></span> <span data-ttu-id="793ab-142">Aksi halde yeni oluşturulan bağlam Kimliğini döndürür ve bir dosyaya kaydeder.</span><span class="sxs-lookup"><span data-stu-id="793ab-142">Otherwise it returns a newly generated context ID and saves it to a file.</span></span> <span data-ttu-id="793ab-143">Varsayılan yapılandırma ile bu dosyalar geçerli kullanıcının temp dizininde bulunduğu ContextStore adlı bir dizin yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="793ab-143">With the default configuration, these files are placed in a directory called ContextStore, which resides in the current user’s temp directory.</span></span> <span data-ttu-id="793ab-144">Ancak bu konuma bağlama öğesi kullanılarak yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="793ab-144">However this location is configurable using the binding element.</span></span>  
  
 <span data-ttu-id="793ab-145">ID kontextu taşıma için kullanılan mekanizma yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="793ab-145">The mechanism used to transport the context ID is configurable.</span></span> <span data-ttu-id="793ab-146">Ya da HTTP tanımlama bilgisi üstbilgisi veya özel bir SOAP üst bilgisi için yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="793ab-146">It could be either written to the HTTP cookie header or to a custom SOAP header.</span></span> <span data-ttu-id="793ab-147">Özel SOAP üstbilgi yaklaşımı, bu Protokolü HTTP olmayan protokolleri (örneğin, TCP veya Named Pipes) ile kullanmak üzere mümkün kılar.</span><span class="sxs-lookup"><span data-stu-id="793ab-147">The custom SOAP header approach makes it possible to use this protocol with non-HTTP protocols (for example, TCP or Named Pipes).</span></span> <span data-ttu-id="793ab-148">İki sınıfı vardır, yani `MessageHeaderContextManager` ve `HttpCookieContextManager`, bu iki seçenek uygulayın.</span><span class="sxs-lookup"><span data-stu-id="793ab-148">There are two classes, namely `MessageHeaderContextManager` and `HttpCookieContextManager`, which implement these two options.</span></span>  
  
 <span data-ttu-id="793ab-149">Her ikisi de bağlam Kimliğini iletiye uygun şekilde yazın.</span><span class="sxs-lookup"><span data-stu-id="793ab-149">Both of them write the context ID to the message appropriately.</span></span> <span data-ttu-id="793ab-150">Örneğin, `MessageHeaderContextManager` sınıfı için bir SOAP üst bilgisinde, Yazar `WriteContext` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="793ab-150">For example, the `MessageHeaderContextManager` class writes it to a SOAP header in the `WriteContext` method.</span></span>  
  
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
  
 <span data-ttu-id="793ab-151">Hem `ApplyContext` ve `ReadContextId` yöntemleri `DurableInstanceContextChannelBase` sınıfı çağırma `IContextManager.ReadContext` ve `IContextManager.WriteContext`sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="793ab-151">Both the `ApplyContext` and `ReadContextId` methods in the `DurableInstanceContextChannelBase` class invoke the `IContextManager.ReadContext` and `IContextManager.WriteContext`, respectively.</span></span> <span data-ttu-id="793ab-152">Ancak, bu bağlam yöneticileri doğrudan tarafından oluşturulmaz `DurableInstanceContextChannelBase` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="793ab-152">However, these context managers are not directly created by the `DurableInstanceContextChannelBase` class.</span></span> <span data-ttu-id="793ab-153">Bunun yerine kullanır `ContextManagerFactory` , işini yapması için sınıf.</span><span class="sxs-lookup"><span data-stu-id="793ab-153">Instead it uses the `ContextManagerFactory` class to do that job.</span></span>  
  
```  
IContextManager contextManager =  
                ContextManagerFactory.CreateContextManager(contextType,   
                this.contextStoreLocation,   
                this.endpointAddress);  
```  
  
 <span data-ttu-id="793ab-154">`ApplyContext` Yöntemi gönderen kanalları tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="793ab-154">The `ApplyContext` method is invoked by the sending channels.</span></span> <span data-ttu-id="793ab-155">Bu bağlam Kimliğini giden iletileri ekler.</span><span class="sxs-lookup"><span data-stu-id="793ab-155">It injects the context ID to the outgoing messages.</span></span> <span data-ttu-id="793ab-156">`ReadContextId` Yöntemi alma kanalları tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="793ab-156">The `ReadContextId` method is invoked by the receiving channels.</span></span> <span data-ttu-id="793ab-157">Bu yöntem, bağlam Kimliğini gelen iletiler kullanılabilir ve bu gruba ekler sağlar `Properties` koleksiyonunu `Message` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="793ab-157">This method ensures that the context ID is available in the incoming messages and adds it to the `Properties` collection of the `Message` class.</span></span> <span data-ttu-id="793ab-158">Ayrıca bir `CommunicationException` bağlam Kimliğini okumak için bir arıza durumunda ve bu nedenle kanal durdurulmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="793ab-158">It also throws a `CommunicationException` in case of a failure to read the context ID and thus causes the channel to be aborted.</span></span>  
  
```  
message.Properties.Add(DurableInstanceContextUtility.ContextIdProperty, contextId);  
```  
  
 <span data-ttu-id="793ab-159">Devam etmeden önce kullanımını anlamak önemli olan `Properties` koleksiyonda `Message` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="793ab-159">Before proceeding, it is important to understand the usage of the `Properties` collection in the `Message` class.</span></span> <span data-ttu-id="793ab-160">Genellikle bu `Properties` koleksiyonu geçirme verilerini üst düzeylere kanal katmanından daha düşük olduğunda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="793ab-160">Typically, this `Properties` collection is used when passing data from lower to the upper levels from the channel layer.</span></span> <span data-ttu-id="793ab-161">Bu şekilde istenen veri protokol ayrıntılarını bağımsız olarak tutarlı bir şekilde üst düzeylere sağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="793ab-161">This way the desired data can be provided to the upper levels in a consistent manner regardless of the protocol details.</span></span> <span data-ttu-id="793ab-162">Diğer bir deyişle, kanal katmanını gönderebilir ve bağlam Kimliğini bir SOAP üst bilgisi ya da bir HTTP tanımlama bilgisi üstbilgisi olarak ya da alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="793ab-162">In other words, the channel layer can send and receive the context ID either as a SOAP header or a HTTP cookie header.</span></span> <span data-ttu-id="793ab-163">Kanal katmanını bu bilgi kullanılabilir hale getirir çünkü ilgili bu ayrıntıları öğrenmek üst düzey için gerekli değildir, ancak `Properties` koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="793ab-163">But it is not necessary for the upper levels to know about these details because the channel layer makes this information available in the `Properties` collection.</span></span>  
  
 <span data-ttu-id="793ab-164">Artık ile `DurableInstanceContextChannelBase` sınıfı yerinde on (IOutputChannel IInputChannel, IOutputSessionChannel, IInputSessionChannel, IRequestChannel, IReplyChannel'ı, IRequestSessionChannel, IReplySessionChannel, gerekli arabirimleri IDuplexChannel, da IDuplexSessionChannel öğelerini) uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="793ab-164">Now with the `DurableInstanceContextChannelBase` class in place all ten of the necessary interfaces (IOutputChannel, IInputChannel, IOutputSessionChannel, IInputSessionChannel, IRequestChannel, IReplyChannel, IRequestSessionChannel, IReplySessionChannel, IDuplexChannel, IDuplexSessionChannel) must be implemented.</span></span> <span data-ttu-id="793ab-165">Bunlar, her kullanılabilir ileti değişim deseni (veri birimi, tek yönlü, çift yönlü ve kapatamaması türevlerini) benzer.</span><span class="sxs-lookup"><span data-stu-id="793ab-165">They resemble every available message exchange pattern (datagram, simplex, duplex and their sessionful variants).</span></span> <span data-ttu-id="793ab-166">Bu uygulamalardan her biri devral çağrıları ve daha önce açıklanan temel sınıf `ApplyContext` ve `ReadContexId` uygun şekilde.</span><span class="sxs-lookup"><span data-stu-id="793ab-166">Each of these implementations inherit the base class previously described and calls `ApplyContext` and `ReadContexId` appropriately.</span></span> <span data-ttu-id="793ab-167">Örneğin, `DurableInstanceContextOutputChannel` - IOutputChannel arabirimi uygulayan - çağırır `ApplyContext` yöntemi her yöntemden iletileri gönderir.</span><span class="sxs-lookup"><span data-stu-id="793ab-167">For example, `DurableInstanceContextOutputChannel` - which implements the IOutputChannel interface - calls the `ApplyContext` method from each method that sends the messages.</span></span>  
  
```  
public void Send(Message message, TimeSpan timeout)  
{  
    // Apply the context information before sending the message.  
    this.ApplyContext(message);  
    //…  
}   
```  
  
 <span data-ttu-id="793ab-168">Öte yandan, `DurableInstanceContextInputChannel` -uygulayan `IInputChannel` arabirim - çağrıları `ReadContextId` yöntemi her yönteminde iletileri alır.</span><span class="sxs-lookup"><span data-stu-id="793ab-168">On the other hand, `DurableInstanceContextInputChannel` - which implements the `IInputChannel` interface - calls the `ReadContextId` method in each method which receives the messages.</span></span>  
  
```  
public Message Receive(TimeSpan timeout)  
{  
    //…  
      ReadContextId(message);  
      return message;  
}  
```  
  
 <span data-ttu-id="793ab-169">Bu dışında bu kanal uygulamaları bunları aşağıda kanala kanal yığınındaki yöntem çağrıları temsilci.</span><span class="sxs-lookup"><span data-stu-id="793ab-169">Apart from this, these channel implementations delegate the method invocations to the channel below them in the channel stack.</span></span> <span data-ttu-id="793ab-170">Ancak kapatamaması çeşitleri, bağlam Kimliğini gönderilir ve oluşturulacak oturum neden yalnızca ilk ileti için okuma emin olmak için bir temel mantığı vardır.</span><span class="sxs-lookup"><span data-stu-id="793ab-170">However, sessionful variants have a basic logic to make sure that the context ID is sent and is read only for the first message that causes the session to be created.</span></span>  
  
```  
if (isFirstMessage)  
{  
//…  
    this.ApplyContext(message);  
    isFirstMessage = false;  
}  
```  
  
 <span data-ttu-id="793ab-171">Bu kanal uygulamaları WCF kanalı çalışma zamanı tarafından eklenen `DurableInstanceContextBindingElement` sınıfı ve `DurableInstanceContextBindingElementSection` uygun şekilde sınıfı.</span><span class="sxs-lookup"><span data-stu-id="793ab-171">These channel implementations are then added to the WCF channel runtime by the `DurableInstanceContextBindingElement` class and `DurableInstanceContextBindingElementSection` class appropriately.</span></span> <span data-ttu-id="793ab-172">Bkz: [HttpCookieSession](../../../../docs/framework/wcf/samples/httpcookiesession.md) kanal bağlama öğeleri ve öğe bölümleri bağlama hakkında daha fazla ayrıntı için örnek belgeler.</span><span class="sxs-lookup"><span data-stu-id="793ab-172">See the [HttpCookieSession](../../../../docs/framework/wcf/samples/httpcookiesession.md) channel sample documentation for more details about binding elements and binding element sections.</span></span>  
  
## <a name="service-model-layer-extensions"></a><span data-ttu-id="793ab-173">Hizmet modeli katman uzantıları</span><span class="sxs-lookup"><span data-stu-id="793ab-173">Service Model Layer Extensions</span></span>  
 <span data-ttu-id="793ab-174">Kanal katmanını bağlam Kimliğini konuşmalar yapmıştır, hizmet davranışı oluşturmada özelleştirmek için uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="793ab-174">Now that the context ID has traveled through the channel layer, the service behavior can be implemented to customize the instantiation.</span></span> <span data-ttu-id="793ab-175">Bu örnekte, bir Depolama Yöneticisi'ni yüklemek ve durumu kalıcı depolama ya da kaydetmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="793ab-175">In this sample, a storage manager is used to load and save state from or to the persistent store.</span></span> <span data-ttu-id="793ab-176">Bu örnek, daha önce açıklandığı şekilde, SQL Server 2005, yedekleme deposu olarak kullanan bir Depolama Yöneticisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="793ab-176">As explained previously, this sample provides a storage manager that uses SQL Server 2005 as its backing store.</span></span> <span data-ttu-id="793ab-177">Ancak, aynı zamanda bu uzantı için özel depolama mekanizmaları eklemek mümkündür.</span><span class="sxs-lookup"><span data-stu-id="793ab-177">However, it is also possible to add custom storage mechanisms to this extension.</span></span> <span data-ttu-id="793ab-178">Ortak bir arabirim Bunu yapmak için tüm depolama yöneticileri tarafından uygulanmalıdır bildirilir.</span><span class="sxs-lookup"><span data-stu-id="793ab-178">To do that a public interface is declared, which must be implemented by all storage managers.</span></span>  
  
```  
public interface IStorageManager  
{  
    object GetInstance(string contextId, Type type);  
    void SaveInstance(string contextId, object state);  
}  
```  
  
 <span data-ttu-id="793ab-179">`SqlServerStorageManager` Sınıfı içeren varsayılan `IStorageManager` uygulaması.</span><span class="sxs-lookup"><span data-stu-id="793ab-179">The `SqlServerStorageManager` class contains the default `IStorageManager` implementation.</span></span> <span data-ttu-id="793ab-180">İçinde `SaveInstance` yöntemi belirtilen nesneyi XmlSerializer kullanarak serileştirilmiş ve SQL Server veritabanına kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="793ab-180">In its `SaveInstance` method the given object is serialized using the XmlSerializer and is saved to the SQL Server database.</span></span>  
  
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
  
 <span data-ttu-id="793ab-181">İçinde `GetInstance` yöntemi serileştirilmiş veriler için belirli bir bağlam kimliği okunur ve bundan oluşturulan nesne çağırana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="793ab-181">In the `GetInstance` method the serialized data is read for a given context ID and the object constructed from it is returned to the caller.</span></span>  
  
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
  
 <span data-ttu-id="793ab-182">Kullanıcılar bu depolama yöneticileri doğrudan örneklemek için beklenen değil.</span><span class="sxs-lookup"><span data-stu-id="793ab-182">Users of these storage managers are not supposed to instantiate them directly.</span></span> <span data-ttu-id="793ab-183">Kullandıkları `StorageManagerFactory` sınıfını Depolama Yöneticisi oluşturma ayrıntılarının soyutlar.</span><span class="sxs-lookup"><span data-stu-id="793ab-183">They use the `StorageManagerFactory` class, which abstracts from the storage manager creation details.</span></span> <span data-ttu-id="793ab-184">Bu sınıf, bir statik üye sahip `GetStorageManager`, belirli bir Depolama Yöneticisi türün örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="793ab-184">This class has one static member, `GetStorageManager`, which creates an instance of a given storage manager type.</span></span> <span data-ttu-id="793ab-185">Tür parametresi ise `null`, bu yöntem varsayılan bir örneğini oluşturur `SqlServerStorageManager` sınıfı ve döndürür.</span><span class="sxs-lookup"><span data-stu-id="793ab-185">If the type parameter is `null`, this method creates an instance of the default `SqlServerStorageManager` class and returns it.</span></span> <span data-ttu-id="793ab-186">Ayrıca bunu uygulayan emin olmak için verilen tür doğrular `IStorageManager` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="793ab-186">It also validates the given type to make sure that it implements the `IStorageManager` interface.</span></span>  
  
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
  
 <span data-ttu-id="793ab-187">Okumak ve kalıcı depolama alanından örnekleri yazmak için gerekli altyapıyı uygulanır.</span><span class="sxs-lookup"><span data-stu-id="793ab-187">The necessary infrastructure to read and write instances from the persistent storage is implemented.</span></span> <span data-ttu-id="793ab-188">Artık bir hizmet davranışını değiştirmek için gerekli adımları alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="793ab-188">Now the necessary steps to change the service behavior have to be taken.</span></span>  
  
 <span data-ttu-id="793ab-189">Bu işlemin ilk adımı kaydetmek için geçerli InstanceContext kanal katmanını gelen bağlam Kimliğini sahibiz.</span><span class="sxs-lookup"><span data-stu-id="793ab-189">As the first step of this process we have to save the context ID, which came through the channel layer to the current InstanceContext.</span></span> <span data-ttu-id="793ab-190">InstanceContext WCF dağıtıcı ve hizmet örneği arasındaki bağlantı olarak davranan bir çalışma zamanı bileşenidir.</span><span class="sxs-lookup"><span data-stu-id="793ab-190">InstanceContext is a runtime component that acts as the link between the WCF dispatcher and the service instance.</span></span> <span data-ttu-id="793ab-191">Ek durum ve hizmet örneği için davranış sağlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="793ab-191">It can be used to provide additional state and behavior to the service instance.</span></span> <span data-ttu-id="793ab-192">Kapatamaması iletişimde bağlam Kimliğini yalnızca ilk iletinin gönderildiği için bu gereklidir.</span><span class="sxs-lookup"><span data-stu-id="793ab-192">This is essential because in sessionful communication the context ID is sent only with the first message.</span></span>  
  
 <span data-ttu-id="793ab-193">Yeni durum ve Genişletilebilir nesne desenine kullanarak davranışı ekleyerek kendi InstanceContext çalışma zamanı bileşeni genişletme WCF sağlar.</span><span class="sxs-lookup"><span data-stu-id="793ab-193">WCF allows extending its InstanceContext runtime component by adding a new state and behavior using its extensible object pattern.</span></span> <span data-ttu-id="793ab-194">Genişletilebilir nesne düzeni WCF'de ya da var olan çalışma zamanı sınıflar yeni işlevlerle genişletmek veya bir nesne için yeni durum özellikler eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="793ab-194">The extensible object pattern is used in WCF to either extend existing runtime classes with new functionality or to add new state features to an object.</span></span> <span data-ttu-id="793ab-195">Genişletilebilir nesne deseni - IExtensibleObject üç arabirimi vardır\<T >, IExtension\<T > ve IExtensionCollection\<T >:</span><span class="sxs-lookup"><span data-stu-id="793ab-195">There are three interfaces in the extensible object pattern - IExtensibleObject\<T>, IExtension\<T>, and IExtensionCollection\<T>:</span></span>  
  
-   <span data-ttu-id="793ab-196">IExtensibleObject\<T > arabirimini işlevleriyle özelleştirme uzantılara izin ver nesneler tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="793ab-196">The IExtensibleObject\<T> interface is implemented by objects that allow extensions that customize their functionality.</span></span>  
  
-   <span data-ttu-id="793ab-197">IExtension\<T > arabirimini uzantıları t türü sınıfların nesneleri tarafından uygulanan</span><span class="sxs-lookup"><span data-stu-id="793ab-197">The IExtension\<T> interface is implemented by objects that are extensions of classes of type T.</span></span>  
  
-   <span data-ttu-id="793ab-198">IExtensionCollection\<T > türüne göre IExtensions almak için izin veren IExtensions koleksiyonunu arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="793ab-198">The IExtensionCollection\<T> interface is a collection of IExtensions that allows for retrieving IExtensions by their type.</span></span>  
  
 <span data-ttu-id="793ab-199">Bu nedenle InstanceContextExtension sınıfı IExtension arabirimi uygulayan ve bağlam kimliğini kaydetmek için gerekli durumu tanımlayan oluşturulmalıdır</span><span class="sxs-lookup"><span data-stu-id="793ab-199">Therefore an InstanceContextExtension class should be created that implements the IExtension interface and defines the required state to save the context ID.</span></span> <span data-ttu-id="793ab-200">Bu sınıf, durum Yöneticisi tarafından kullanılan depolama tutmak için de sağlar.</span><span class="sxs-lookup"><span data-stu-id="793ab-200">This class also provides the state to hold the storage manager being used.</span></span> <span data-ttu-id="793ab-201">Yeni durumu kaydedildikten sonra değiştirmek olası olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="793ab-201">Once the new state is saved, it should not be possible to modify it.</span></span> <span data-ttu-id="793ab-202">Bu nedenle durum sağlanan ve oluşturulan ve ardından yalnızca erişilebilir salt okunur özelliklerini kullanarak zaman örneğine kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="793ab-202">Therefore the state is provided and saved to the instance at the time it is being constructed and then only accessible using read-only properties.</span></span>  
  
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
  
 <span data-ttu-id="793ab-203">InstanceContextInitializer sınıfı IInstanceContextInitializer arabirimi uygulayan ve örnek bağlamı uzantısını yapılandırılmakta InstanceContext uzantıları koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="793ab-203">The InstanceContextInitializer class implements the IInstanceContextInitializer interface and adds the instance context extension to the Extensions collection of the InstanceContext being constructed.</span></span>  
  
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
  
 <span data-ttu-id="793ab-204">Daha önce açıklandığı gibi bağlam Kimliğini gelen okunur `Properties` koleksiyonunu `Message` sınıfı ve extension sınıfının oluşturucusuna geçirilen.</span><span class="sxs-lookup"><span data-stu-id="793ab-204">As described earlier the context ID is read from the `Properties` collection of the `Message` class and passed to the constructor of the extension class.</span></span> <span data-ttu-id="793ab-205">Bu bilgi tutarlı bir şekilde katmanlar arasında nasıl değiştirilebilir gösterir.</span><span class="sxs-lookup"><span data-stu-id="793ab-205">This demonstrates how information can be exchanged between the layers in a consistent manner.</span></span>  
  
 <span data-ttu-id="793ab-206">Önemli bir sonraki adım, hizmet örneği oluşturma işlemi geçersiz kılıyor.</span><span class="sxs-lookup"><span data-stu-id="793ab-206">The next important step is overriding the service instance creation process.</span></span> <span data-ttu-id="793ab-207">WCF özel oluşturmada davranışları uygulama ve bunları IInstanceProvider arabirimini kullanarak çalışma zamanı kadar takma sağlar.</span><span class="sxs-lookup"><span data-stu-id="793ab-207">WCF allows implementing custom instantiation behaviors and hooking them up to the runtime using the IInstanceProvider interface.</span></span> <span data-ttu-id="793ab-208">Yeni `InstanceProvider` sınıfı, işi yapmak için uygulanır.</span><span class="sxs-lookup"><span data-stu-id="793ab-208">The new `InstanceProvider` class is implemented to do that job.</span></span> <span data-ttu-id="793ab-209">Oluşturucuda örneği sağlayıcısından beklenen hizmet türünü kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="793ab-209">In the constructor the service type expected from the instance provider is accepted.</span></span> <span data-ttu-id="793ab-210">Daha sonra bu yeni örnekleri oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="793ab-210">Later this is used to create new instances.</span></span> <span data-ttu-id="793ab-211">İçinde `GetInstance` uygulama Depolama Yöneticisi örneği oluşturulur için kalıcı bir örneği aranıyor.</span><span class="sxs-lookup"><span data-stu-id="793ab-211">In the `GetInstance` implementation an instance of a storage manager is created looking for a persisted instance.</span></span> <span data-ttu-id="793ab-212">Döndürürse `null` hizmet türü yeni bir örneğini örneği ve arayana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="793ab-212">If it returns `null` then a new instance of the service type is instantiated and returned to the caller.</span></span>  
  
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
  
 <span data-ttu-id="793ab-213">Sonraki önemli adım `InstanceContextExtension`, `InstanceContextInitializer` ve `InstanceProvider` sınıflara service model çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="793ab-213">The next important step is to install the `InstanceContextExtension`, `InstanceContextInitializer` and `InstanceProvider` classes into the service model runtime.</span></span> <span data-ttu-id="793ab-214">Özel bir öznitelik, hizmet uygulaması sınıflar yükleme davranışı işaretlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="793ab-214">A custom attribute could be used to mark the service implementation classes to install the behavior.</span></span> <span data-ttu-id="793ab-215">`DurableInstanceContextAttribute` Bu öznitelik için ise uygulamayı içerir ve bunu uygulayan `IServiceBehavior` tüm hizmet çalışma zamanı genişletmek için arabirim.</span><span class="sxs-lookup"><span data-stu-id="793ab-215">The `DurableInstanceContextAttribute` contains the implementation for this attribute and it implements the `IServiceBehavior` interface to extend the entire service runtime.</span></span>  
  
 <span data-ttu-id="793ab-216">Bu sınıf, kullanılacak Depolama Yöneticisi türü kabul eden bir özelliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="793ab-216">This class has a property that accepts the type of the storage manager to be used.</span></span> <span data-ttu-id="793ab-217">Bu şekilde, uygulama kendi belirtmek kullanıcıların sağlar. `IStorageManager` bu öznitelik parametre olarak uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="793ab-217">In this way the implementation enables the users to specify their own `IStorageManager` implementation as parameter of this attribute.</span></span>  
  
 <span data-ttu-id="793ab-218">İçinde `ApplyDispatchBehavior` uygulama `InstanceContextMode` geçerli `ServiceBehavior` öznitelik doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="793ab-218">In the `ApplyDispatchBehavior` implementation the `InstanceContextMode` of the current `ServiceBehavior` attribute is being verified.</span></span> <span data-ttu-id="793ab-219">Bu özellik için Singleton olarak ayarlanırsa dayanıklı örneği oluşturmayı etkinleştirmek mümkün değildir ve bir `InvalidOperationException` ana bilgisayara bildirmek için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="793ab-219">If this property is set to Singleton, enabling durable instancing is not possible and an `InvalidOperationException` is thrown to notify the host.</span></span>  
  
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
  
 <span data-ttu-id="793ab-220">Bundan sonra Depolama Yöneticisi, örnek bağlamı başlatıcı ve örnek sağlayıcısı örnekleri oluşturulur ve yüklü `DispatchRuntime` için her bir uç noktası oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="793ab-220">After this the instances of the storage manager, instance context initializer, and the instance provider are created and installed in the `DispatchRuntime` created for every endpoint.</span></span>  
  
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
  
 <span data-ttu-id="793ab-221">Şu ana kadar Özet olarak, bu örnek için özel bir bağlam kimliği exchange özel kablo protokolünü etkinleştirilmiş bir kanal üretmiştir ve de varsayılan davranışı, kalıcı depolamadan örnekleri yüklenemedi depolamasına üzerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="793ab-221">In summary so far, this sample has produced a channel that enabled the custom wire protocol for custom context ID exchange and it also overwrites the default instancing behavior to load the instances from the persistent storage.</span></span>  
  
 <span data-ttu-id="793ab-222">Ne bırakılır, hizmet örneği kalıcı depolama alanına kaydetmek için bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="793ab-222">What is left is a way to save the service instance to the persistent storage.</span></span> <span data-ttu-id="793ab-223">Daha önce açıklandığı gibi zaten var. durumunda kaydetmek için gerekli işlevselliği bir `IStorageManager` uygulaması.</span><span class="sxs-lookup"><span data-stu-id="793ab-223">As discussed previously, there is already the required functionality to save the state in an `IStorageManager` implementation.</span></span> <span data-ttu-id="793ab-224">Biz artık bu WCF çalışma zamanı ile tümleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="793ab-224">We now must integrate this with the WCF runtime.</span></span> <span data-ttu-id="793ab-225">Başka bir özniteliği gereklidir hizmet uygulaması sınıfı yöntemleri için geçerli olan.</span><span class="sxs-lookup"><span data-stu-id="793ab-225">Another attribute is required that is applicable to the methods in the service implementation class.</span></span> <span data-ttu-id="793ab-226">Bu öznitelik hizmet örneğinin durumunu değiştiren yöntemlere uygulanması gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="793ab-226">This attribute is supposed to be applied to the methods that change the state of the service instance.</span></span>  
  
 <span data-ttu-id="793ab-227">`SaveStateAttribute` Sınıfı bu işlevselliğini uygular.</span><span class="sxs-lookup"><span data-stu-id="793ab-227">The `SaveStateAttribute` class implements this functionality.</span></span> <span data-ttu-id="793ab-228">Ayrıca uygulayan `IOperationBehavior` her işlem için WCF çalışma zamanını değiştirmek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="793ab-228">It also implements `IOperationBehavior` class to modify the WCF runtime for each operation.</span></span> <span data-ttu-id="793ab-229">Bu özniteliği ile işaretli bir yöntem, WCF çalıştırma zamanı çağırır `ApplyBehavior` yöntemi sırasında uygun `DispatchOperation` oluşturulmuyor.</span><span class="sxs-lookup"><span data-stu-id="793ab-229">When a method is marked with this attribute, the WCF runtime invokes the `ApplyBehavior` method while the appropriate `DispatchOperation` is being constructed.</span></span> <span data-ttu-id="793ab-230">Bu yöntem uygulaması tek satırlık bir kod vardır:</span><span class="sxs-lookup"><span data-stu-id="793ab-230">In this method implementation there is single line of code:</span></span>  
  
```  
dispatch.Invoker = new OperationInvoker(dispatch.Invoker);  
```  
  
 <span data-ttu-id="793ab-231">Bu yönerge bir örneğini oluşturur `OperationInvoker` yazın ve buna atayan `Invoker` özelliği `DispatchOperation` oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="793ab-231">This instruction creates an instance of `OperationInvoker` type and assigns it to the `Invoker` property of the `DispatchOperation` being constructed.</span></span> <span data-ttu-id="793ab-232">`OperationInvoker` İçin oluşturulan varsayılan işlem çağırıcı için bir sarmalayıcı sınıftır `DispatchOperation`.</span><span class="sxs-lookup"><span data-stu-id="793ab-232">The `OperationInvoker` class is a wrapper for the default operation invoker created for the `DispatchOperation`.</span></span> <span data-ttu-id="793ab-233">Bu sınıfın uyguladığı `IOperationInvoker` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="793ab-233">This class implements the `IOperationInvoker` interface.</span></span> <span data-ttu-id="793ab-234">İçinde `Invoke` gerçek yöntem çağırma için iç işlem çağırıcı temsilci yöntem uygulaması.</span><span class="sxs-lookup"><span data-stu-id="793ab-234">In the `Invoke` method implementation the actual method invocation is delegated to the inner operation invoker.</span></span> <span data-ttu-id="793ab-235">Ancak, Depolama Yöneticisi'nde sonuçları döndüren önce `InstanceContext` hizmet örneği kaydetmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="793ab-235">However, before returning the results the storage manager in the `InstanceContext` is used to save the service instance.</span></span>  
  
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
  
## <a name="using-the-extension"></a><span data-ttu-id="793ab-236">Uzantısını kullanma</span><span class="sxs-lookup"><span data-stu-id="793ab-236">Using the Extension</span></span>  
 <span data-ttu-id="793ab-237">Kanal katmanını ve hizmet modeli katman uzantıları bitti hem de WCF uygulamaları artık kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="793ab-237">Both the channel layer and service model layer extensions are done and they can now be used in WCF applications.</span></span> <span data-ttu-id="793ab-238">Özel bağlama kullanma kanal yığına kanal ekleyin ve ardından uygun özniteliklere sahip hizmet uygulama sınıfları işaretlemek hizmetleriniz var.</span><span class="sxs-lookup"><span data-stu-id="793ab-238">Services have to add the channel into the channel stack using a custom binding and then mark the service implementation classes with the appropriate attributes.</span></span>  
  
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
  
 <span data-ttu-id="793ab-239">İstemci uygulamaları DurableInstanceContextChannel özel bağlama kullanma kanal yığına eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="793ab-239">Client applications must add the DurableInstanceContextChannel into the channel stack using a custom binding.</span></span> <span data-ttu-id="793ab-240">Kanal yapılandırma dosyasında bildirimli olarak yapılandırmak için bağlama öğesi uzantıları koleksiyona eklenecek bağlama öğesi bölümü vardır.</span><span class="sxs-lookup"><span data-stu-id="793ab-240">To configure the channel declaratively in the configuration file, the binding element section has to be added to the binding element extensions collection.</span></span>  
  
```xml  
<system.serviceModel>  
 <extensions>  
   <bindingElementExtensions>  
     <add name="durableInstanceContext"  
type="Microsoft.ServiceModel.Samples.DurableInstanceContextBindingElementSection, DurableInstanceContextExtension, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null"/>  
   </bindingElementExtensions>  
 </extensions>  
```  
  
 <span data-ttu-id="793ab-241">Artık bağlama öğesi, diğer standart bağlama öğeleri gibi özel bir bağlama ile kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="793ab-241">Now the binding element can be used with a custom binding just like other standard binding elements:</span></span>  
  
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
  
## <a name="conclusion"></a><span data-ttu-id="793ab-242">Sonuç</span><span class="sxs-lookup"><span data-stu-id="793ab-242">Conclusion</span></span>  
 <span data-ttu-id="793ab-243">Bu örnek bir özel Protokolü kanalının nasıl oluşturulacağı ve etkinleştirmek için hizmet davranışını özelleştirmek nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="793ab-243">This sample showed how to create a custom protocol channel and how to customize the service behavior to enable it.</span></span>  
  
 <span data-ttu-id="793ab-244">Uzantı belirtin kullanıcılar izin vererek daha fazla geliştirilebilir `IStorageManager` bir yapılandırma bölümünü kullanarak uygulama.</span><span class="sxs-lookup"><span data-stu-id="793ab-244">The extension can be further improved by letting users specify the `IStorageManager` implementation using a configuration section.</span></span> <span data-ttu-id="793ab-245">Hizmet kodu yeniden derlemeden yedekleme deposu değiştirmek mümkün kılar.</span><span class="sxs-lookup"><span data-stu-id="793ab-245">This makes it possible to modify the backing store without recompiling the service code.</span></span>  
  
 <span data-ttu-id="793ab-246">Ayrıca bir sınıf uygulamak çalışabilir (örneğin, `StateBag`), örneğinin durumunu saklar.</span><span class="sxs-lookup"><span data-stu-id="793ab-246">Furthermore you could try to implement a class (for example, `StateBag`), which encapsulates the state of the instance.</span></span> <span data-ttu-id="793ab-247">Bu sınıf, durumu değiştiğinde kalıcı hale getirmekten sorumludur.</span><span class="sxs-lookup"><span data-stu-id="793ab-247">That class is responsible for persisting the state whenever it changes.</span></span> <span data-ttu-id="793ab-248">Kullanarak önlemek bu şekilde `SaveState` özniteliği ve kalıcı hale getirme iş daha doğru bir şekilde gerçekleştirin (örneğin, durum kalıcı durum gerçekten değiştirildiğinde kaydetmek yerine her bir yöntemle zaman zaman `SaveState` özniteliği olarak adlandırılır).</span><span class="sxs-lookup"><span data-stu-id="793ab-248">This way you can avoid using the `SaveState` attribute and perform the persisting work more accurately (for example, you could persist the state when the state is actually changed rather than saving it each time when a method with the `SaveState` attribute is called).</span></span>  
  
 <span data-ttu-id="793ab-249">Aşağıdaki çıktı örneği çalıştırdığınızda görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="793ab-249">When you run the sample, the following output is displayed.</span></span> <span data-ttu-id="793ab-250">İstemci, iki öğe, alışveriş sepetine ekler ve hizmetten'da, alışveriş sepetine içinde öğelerin listesini alır.</span><span class="sxs-lookup"><span data-stu-id="793ab-250">The client adds two items to its shopping cart and then gets the list of items in its shopping cart from the service.</span></span> <span data-ttu-id="793ab-251">Her konsol penceresi hizmet ve istemci kapatmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="793ab-251">Press ENTER in each console window to shut down the service and client.</span></span>  
  
```  
Enter the name of the product: apples  
Enter the name of the product: bananas  
  
Shopping cart currently contains the following items.  
apples  
bananas  
Press ENTER to shut down client  
```  
  
> [!NOTE]
>  <span data-ttu-id="793ab-252">Hizmet yeniden oluşturma, veritabanı dosyasının üzerine yazar.</span><span class="sxs-lookup"><span data-stu-id="793ab-252">Rebuilding the service overwrites the database file.</span></span> <span data-ttu-id="793ab-253">Örnek birden fazla çalıştırma sonucunda korunur durumu gözlemek için örnek çalıştırma arasında yeniden emin olun.</span><span class="sxs-lookup"><span data-stu-id="793ab-253">To observe state preserved across multiple runs of the sample, be sure not to rebuild the sample between runs.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="793ab-254">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="793ab-254">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="793ab-255">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="793ab-255">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="793ab-256">Çözümü derlemek için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="793ab-256">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="793ab-257">Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="793ab-257">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="793ab-258">Bu örneği çalıştırmak için SQL Server 2005 veya SQL Express 2005 çalıştırıyor olmalısınız.</span><span class="sxs-lookup"><span data-stu-id="793ab-258">You must be running SQL Server 2005 or SQL Express 2005 to run this sample.</span></span> <span data-ttu-id="793ab-259">SQL Server 2005 çalıştırıyorsanız, hizmetin bağlantı dizesi yapılandırmasını değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="793ab-259">If you are running SQL Server 2005, you must modify the configuration of the service's connection string.</span></span> <span data-ttu-id="793ab-260">Çapraz makine çalıştırırken, SQL Server yalnızca sunucu makinesinde gereklidir.</span><span class="sxs-lookup"><span data-stu-id="793ab-260">When running cross-machine, SQL Server is only required on the server machine.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="793ab-261">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="793ab-261">The samples may already be installed on your machine.</span></span> <span data-ttu-id="793ab-262">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="793ab-262">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="793ab-263">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="793ab-263">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="793ab-264">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="793ab-264">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Durable`  
