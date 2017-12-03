---
title: "Taşıma: UDP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 738705de-ad3e-40e0-b363-90305bddb140
caps.latest.revision: "48"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fc30a755278251ac9e06f2ddd56e2c369b950af4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="transport-udp"></a><span data-ttu-id="32c6a-102">Taşıma: UDP</span><span class="sxs-lookup"><span data-stu-id="32c6a-102">Transport: UDP</span></span>
<span data-ttu-id="32c6a-103">UDP taşıma örnek UDP tek noktaya yayın ve çok noktaya yayın özel olarak uygulamak gösterilmiştir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] taşıma.</span><span class="sxs-lookup"><span data-stu-id="32c6a-103">The UDP Transport sample demonstrates how to implement UDP unicast and multicast as a custom [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] transport.</span></span> <span data-ttu-id="32c6a-104">Örnek olarak özel bir taşıma oluşturmak için önerilen yordamı açıklar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], kanal çerçevesi kullanarak ve aşağıdaki [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] en iyi uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="32c6a-104">The sample describes the recommended procedure for creating a custom transport in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], by using the channel framework and following [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] best practices.</span></span> <span data-ttu-id="32c6a-105">Özel bir taşıma oluşturmaya yönelik adımlar aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="32c6a-105">The steps to create a custom transport are as follows:</span></span>  
  
1.  <span data-ttu-id="32c6a-106">Kanal karar [ileti Exchange desenleri](#MessageExchangePatterns) (IOutputChannel, IInputChannel, IDuplexChannel, IRequestChannel veya IReplyChannel) ChannelFactory ve ChannelListener destekleyecektir.</span><span class="sxs-lookup"><span data-stu-id="32c6a-106">Decide which of the channel [Message Exchange Patterns](#MessageExchangePatterns) (IOutputChannel, IInputChannel, IDuplexChannel, IRequestChannel, or IReplyChannel) your ChannelFactory and ChannelListener will support.</span></span> <span data-ttu-id="32c6a-107">Daha sonra bu arabirimleri süre sonuyla varyasyonları destekleyecek olup olmadığını karar verin.</span><span class="sxs-lookup"><span data-stu-id="32c6a-107">Then decide whether you will support the sessionful variations of these interfaces.</span></span>  
  
2.  <span data-ttu-id="32c6a-108">Bir kanal fabrikası ve ileti değişim deseni destekleyen dinleyici oluşturun.</span><span class="sxs-lookup"><span data-stu-id="32c6a-108">Create a channel factory and listener that support your Message Exchange Pattern.</span></span>  
  
3.  <span data-ttu-id="32c6a-109">Ağa özgü özel durumlar için uygun olan türetilmiş sınıf normalleştirilmiş emin olun <xref:System.ServiceModel.CommunicationException>.</span><span class="sxs-lookup"><span data-stu-id="32c6a-109">Ensure that any network-specific exceptions are normalized to the appropriate derived class of <xref:System.ServiceModel.CommunicationException>.</span></span>  
  
4.  <span data-ttu-id="32c6a-110">Ekleme bir [ \<bağlama >](../../../../docs/framework/misc/binding.md) bir kanal yığınına özel taşıma ekler öğesi.</span><span class="sxs-lookup"><span data-stu-id="32c6a-110">Add a [\<binding>](../../../../docs/framework/misc/binding.md) element that adds the custom transport to a channel stack.</span></span> <span data-ttu-id="32c6a-111">Daha fazla bilgi için bkz: [bir bağlama öğesi ekleme](#AddingABindingElement).</span><span class="sxs-lookup"><span data-stu-id="32c6a-111">For more information, see [Adding a Binding Element](#AddingABindingElement).</span></span>  
  
5.  <span data-ttu-id="32c6a-112">Yapılandırma sistemi için yeni bir bağlama öğesi kullanıma sunmak için bir bağlama öğesi uzantısı bölümü ekleyin.</span><span class="sxs-lookup"><span data-stu-id="32c6a-112">Add a binding element extension section to expose the new binding element to the configuration system.</span></span>  
  
6.  <span data-ttu-id="32c6a-113">Diğer uç noktalara Özellikleri iletişim kurmak için meta verileri uzantıları ekleyin.</span><span class="sxs-lookup"><span data-stu-id="32c6a-113">Add metadata extensions to communicate capabilities to other endpoints.</span></span>  
  
7.  <span data-ttu-id="32c6a-114">Bağlama öğeleri iyi tanımlanmış bir profili göre yığınını önceden yapılandırır bir bağlaması ekleyin.</span><span class="sxs-lookup"><span data-stu-id="32c6a-114">Add a binding that pre-configures a stack of binding elements according to a well-defined profile.</span></span> <span data-ttu-id="32c6a-115">Daha fazla bilgi için bkz: [standart bağlama ekleme](#AddingAStandardBinding).</span><span class="sxs-lookup"><span data-stu-id="32c6a-115">For more information, see [Adding a Standard Binding](#AddingAStandardBinding).</span></span>  
  
8.  <span data-ttu-id="32c6a-116">Bir bağlama bölümü ve yapılandırma sistemi bağlamayı kullanıma sunmak için bağlama yapılandırma öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="32c6a-116">Add a binding section and binding configuration element to expose the binding to the configuration system.</span></span> <span data-ttu-id="32c6a-117">Daha fazla bilgi için bkz: [yapılandırma desteği ekleme](#AddingConfigurationSupport).</span><span class="sxs-lookup"><span data-stu-id="32c6a-117">For more information, see [Adding Configuration Support](#AddingConfigurationSupport).</span></span>  
  
<a name="MessageExchangePatterns"></a>   
## <a name="message-exchange-patterns"></a><span data-ttu-id="32c6a-118">İleti Exchange desenleri</span><span class="sxs-lookup"><span data-stu-id="32c6a-118">Message Exchange Patterns</span></span>  
 <span data-ttu-id="32c6a-119">İlk adım karar vermek için özel bir taşıma yazılırken hangi ileti Exchange desenleri (MEPs) taşıma için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="32c6a-119">The first step in writing a custom transport is to decide which Message Exchange Patterns (MEPs) are required for the transport.</span></span> <span data-ttu-id="32c6a-120">Aralarından seçim yapabileceğiniz üç MEPs vardır:</span><span class="sxs-lookup"><span data-stu-id="32c6a-120">There are three MEPs to choose from:</span></span>  
  
-   <span data-ttu-id="32c6a-121">Veri birimi (IInputChannel/IOutputChannel)</span><span class="sxs-lookup"><span data-stu-id="32c6a-121">Datagram (IInputChannel/IOutputChannel)</span></span>  
  
     <span data-ttu-id="32c6a-122">Veri birimi MEP kullanırken, bir istemci "yangın ve unut" exchange kullanarak bir ileti gönderir.</span><span class="sxs-lookup"><span data-stu-id="32c6a-122">When using a datagram MEP, a client sends a message using a "fire and forget" exchange.</span></span> <span data-ttu-id="32c6a-123">A yangın ve exchange başarılı teslimat bant dışı onay gerektiren bir tane olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="32c6a-123">A fire and forget exchange is one that requires out-of-band confirmation of successful delivery.</span></span> <span data-ttu-id="32c6a-124">İleti, geçiş sırasında kaybolur ve hiçbir zaman hizmete erişmek.</span><span class="sxs-lookup"><span data-stu-id="32c6a-124">The message might be lost in transit and never reach the service.</span></span> <span data-ttu-id="32c6a-125">Gönderme işlemi istemci sonunda başarıyla tamamlarsa, uzak uç noktada bir ileti aldı garanti etmez.</span><span class="sxs-lookup"><span data-stu-id="32c6a-125">If the send operation completes successfully at the client end, it does not guarantee that the remote endpoint has received the message.</span></span> <span data-ttu-id="32c6a-126">Veri birimi üzerine kurallarınızı oluşturabilirsiniz Mesajlaşma için temel yapı bloğu aynıdır — güvenilir protokolleri ve güvenli iletişim kuralları da dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="32c6a-126">The datagram is a fundamental building block for messaging, as you can build your own protocols on top of it—including reliable protocols and secure protocols.</span></span> <span data-ttu-id="32c6a-127">İstemci veri birimi kanalları uygulamak <xref:System.ServiceModel.Channels.IOutputChannel> arabirimi ve hizmet veri birimi kanallar uygulamak <xref:System.ServiceModel.Channels.IInputChannel> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="32c6a-127">Client datagram channels implement the <xref:System.ServiceModel.Channels.IOutputChannel> interface and service datagram channels implement the <xref:System.ServiceModel.Channels.IInputChannel> interface.</span></span>  
  
-   <span data-ttu-id="32c6a-128">İstek-yanıt (IRequestChannel/IReplyChannel)</span><span class="sxs-lookup"><span data-stu-id="32c6a-128">Request-Response (IRequestChannel/IReplyChannel)</span></span>  
  
     <span data-ttu-id="32c6a-129">Bu MEP bir ileti gönderilir ve bir yanıt aldı.</span><span class="sxs-lookup"><span data-stu-id="32c6a-129">In this MEP, a message is sent, and a reply is received.</span></span> <span data-ttu-id="32c6a-130">Desen istek-yanıt çiftlerinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="32c6a-130">The pattern consists of request-response pairs.</span></span> <span data-ttu-id="32c6a-131">İstek-yanıt çağrıları örnekler uzaktan yordam çağrısı (RPC) ve tarayıcı alır.</span><span class="sxs-lookup"><span data-stu-id="32c6a-131">Examples of request-response calls are remote procedure calls (RPC) and browser GETs.</span></span> <span data-ttu-id="32c6a-132">Bu desen yarı çift yönlü da bilinir.</span><span class="sxs-lookup"><span data-stu-id="32c6a-132">This pattern is also known as Half-Duplex.</span></span> <span data-ttu-id="32c6a-133">Bu MEP, istemci kanalları uygulamak <xref:System.ServiceModel.Channels.IRequestChannel> ve hizmet kanalları uygulamak <xref:System.ServiceModel.Channels.IReplyChannel>.</span><span class="sxs-lookup"><span data-stu-id="32c6a-133">In this MEP, client channels implement <xref:System.ServiceModel.Channels.IRequestChannel> and service channels implement <xref:System.ServiceModel.Channels.IReplyChannel>.</span></span>  
  
-   <span data-ttu-id="32c6a-134">Çift yönlü (IDuplexChannel)</span><span class="sxs-lookup"><span data-stu-id="32c6a-134">Duplex (IDuplexChannel)</span></span>  
  
     <span data-ttu-id="32c6a-135">Çift yönlü MEP bir rastgele bir istemci tarafından gönderilen ve herhangi bir sırada alınan ileti sayısı için sağlar.</span><span class="sxs-lookup"><span data-stu-id="32c6a-135">The duplex MEP allows an arbitrary number of messages to be sent by a client and received in any order.</span></span> <span data-ttu-id="32c6a-136">Çift yönlü MEP bir telefon konuşması gibi konuşulan her sözcüğün bir ileti olduğu.</span><span class="sxs-lookup"><span data-stu-id="32c6a-136">The duplex MEP is like a phone conversation, where each word being spoken is a message.</span></span> <span data-ttu-id="32c6a-137">Her iki tarafında da gönderebilir ve bu MEP alabilir, istemci ve hizmet kanalları tarafından uygulanan arabirimi çünkü <xref:System.ServiceModel.Channels.IDuplexChannel>.</span><span class="sxs-lookup"><span data-stu-id="32c6a-137">Because both sides can send and receive in this MEP, the interface implemented by the client and service channels is <xref:System.ServiceModel.Channels.IDuplexChannel>.</span></span>  
  
 <span data-ttu-id="32c6a-138">Her bu MEPs oturumları da destekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="32c6a-138">Each of these MEPs can also support sessions.</span></span> <span data-ttu-id="32c6a-139">Oturum durumunu algılayan bir kanal tarafından sağlanan eklenen bir kanalda alınıp gönderilen tüm iletiler karşılık gelen bir işlevdir.</span><span class="sxs-lookup"><span data-stu-id="32c6a-139">The added functionality provided by a session-aware channel is that it correlates all messages sent and received on a channel.</span></span> <span data-ttu-id="32c6a-140">İstek-yanıt düzeni istek ve yanıt bağıntısı tek başına iki ileti oturum aynıdır.</span><span class="sxs-lookup"><span data-stu-id="32c6a-140">The Request-Response pattern is a stand-alone two-message session, as the request and reply are correlated.</span></span> <span data-ttu-id="32c6a-141">Buna karşılık, oturumlar destekleyen istek-yanıt düzeni bu kanalda tüm istek/yanıt çiftleri birbiriyle ilişkili anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="32c6a-141">In contrast, the Request-Response pattern that supports sessions implies that all request/response pairs on that channel are correlated with each other.</span></span> <span data-ttu-id="32c6a-142">Bu altı MEPs toplam verir — veri birimi, istek-yanıt, çift yönlü, oturumu, istek-yanıt oturumu, veri birimi ve oturumları ile çift yönlü — aralarından seçim yapabileceğiniz.</span><span class="sxs-lookup"><span data-stu-id="32c6a-142">This gives you a total of six MEPs—Datagram, Request-Response, Duplex, Datagram with sessions, Request-Response with sessions, and Duplex with sessions—to choose from.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="32c6a-143">UDP kendiliğinden "yangın ve unut" protokol UDP taşıma için desteklenen tek MEP Datagram, olduğundan.</span><span class="sxs-lookup"><span data-stu-id="32c6a-143">For the UDP transport, the only MEP that is supported is Datagram, because UDP is inherently a "fire and forget" protocol.</span></span>  
  
### <a name="the-icommunicationobject-and-the-wcf-object-lifecycle"></a><span data-ttu-id="32c6a-144">ICommunicationObject ve WCF nesne yaşam döngüsü</span><span class="sxs-lookup"><span data-stu-id="32c6a-144">The ICommunicationObject and the WCF object lifecycle</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="32c6a-145">yaşam döngüsü gibi nesneleri yönetmek için kullanılan yaygın bir durum makinesinin sahip <xref:System.ServiceModel.Channels.IChannel>, <xref:System.ServiceModel.Channels.IChannelFactory>, ve <xref:System.ServiceModel.Channels.IChannelListener> iletişimi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="32c6a-145"> has a common state machine that is used for managing the lifecycle of objects like <xref:System.ServiceModel.Channels.IChannel>, <xref:System.ServiceModel.Channels.IChannelFactory>, and <xref:System.ServiceModel.Channels.IChannelListener> that are used for communication.</span></span> <span data-ttu-id="32c6a-146">Bu iletişimi nesneleri var olabilir beş durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="32c6a-146">There are five states in which these communication objects can exist.</span></span> <span data-ttu-id="32c6a-147">Bu durumu tarafından temsil edilen <xref:System.ServiceModel.CommunicationState> numaralandırma ve aşağıdaki gibi şunlardır:</span><span class="sxs-lookup"><span data-stu-id="32c6a-147">These states are represented by the <xref:System.ServiceModel.CommunicationState> enumeration, and are as follows:</span></span>  
  
-   <span data-ttu-id="32c6a-148">Oluşturulan: Bu durumda bir <xref:System.ServiceModel.ICommunicationObject> olduğunda, ilk örneği.</span><span class="sxs-lookup"><span data-stu-id="32c6a-148">Created: This is the state of a <xref:System.ServiceModel.ICommunicationObject> when it is first instantiated.</span></span> <span data-ttu-id="32c6a-149">Bu durumda hiçbir giriş/çıkış (g/ç) oluşur.</span><span class="sxs-lookup"><span data-stu-id="32c6a-149">No input/output (I/O) occurs in this state.</span></span>  
  
-   <span data-ttu-id="32c6a-150">Açılış: Bu nesneler geçiş durumu ne zaman <xref:System.ServiceModel.ICommunicationObject.Open%2A> olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="32c6a-150">Opening: Objects transition to this state when <xref:System.ServiceModel.ICommunicationObject.Open%2A> is called.</span></span> <span data-ttu-id="32c6a-151">Bu noktada özellikleri değişmez yapılır ve giriş/çıkış başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="32c6a-151">At this point properties are made immutable, and input/output can begin.</span></span> <span data-ttu-id="32c6a-152">Bu geçiş oluşturulan durumundan yalnızca geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="32c6a-152">This transition is valid only from the Created state.</span></span>  
  
-   <span data-ttu-id="32c6a-153">Açılmış: Nesneleri geçiş açma işlemi tamamlandığında bu durumu.</span><span class="sxs-lookup"><span data-stu-id="32c6a-153">Opened: Objects transition to this state when the open process completes.</span></span> <span data-ttu-id="32c6a-154">Bu geçiş yalnızca açılış durumundan geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="32c6a-154">This transition is valid only from the Opening state.</span></span> <span data-ttu-id="32c6a-155">Bu noktada, nesne aktarımı için tam olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="32c6a-155">At this point, the object is fully usable for transfer.</span></span>  
  
-   <span data-ttu-id="32c6a-156">Kapatma: Bu nesneler geçiş durumu ne zaman <xref:System.ServiceModel.ICommunicationObject.Close%2A> normal olarak kapatmak için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="32c6a-156">Closing: Objects transition to this state when <xref:System.ServiceModel.ICommunicationObject.Close%2A> is called for a graceful shutdown.</span></span> <span data-ttu-id="32c6a-157">Bu geçiş yalnızca açık durumundan geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="32c6a-157">This transition is valid only from the Opened state.</span></span>  
  
-   <span data-ttu-id="32c6a-158">Kapalı: kapalı durum nesneleri artık kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="32c6a-158">Closed: In the Closed state objects are no longer usable.</span></span> <span data-ttu-id="32c6a-159">Genel olarak, çoğu yapılandırma İnceleme için hala erişilebilir, ancak hiçbir iletişimi ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="32c6a-159">In general, most configuration is still accessible for inspection, but no communication can occur.</span></span> <span data-ttu-id="32c6a-160">Bu durum, atıldı için eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="32c6a-160">This state is equivalent to being disposed.</span></span>  
  
-   <span data-ttu-id="32c6a-161">Faulted: Faulted, nesneleri incelemesi için erişilebilir ancak artık kullanılamaz durumda.</span><span class="sxs-lookup"><span data-stu-id="32c6a-161">Faulted: In the Faulted state, objects are accessible to inspection but no longer usable.</span></span> <span data-ttu-id="32c6a-162">Nesne bir kurtarılamaz bir hata oluştuğunda, bu duruma geçer.</span><span class="sxs-lookup"><span data-stu-id="32c6a-162">When a non-recoverable error occurs, the object transitions into this state.</span></span> <span data-ttu-id="32c6a-163">Bu durum yalnızca geçerli geçiş halinde olan `Closed` durumu.</span><span class="sxs-lookup"><span data-stu-id="32c6a-163">The only valid transition from this state is into the `Closed` state.</span></span>  
  
 <span data-ttu-id="32c6a-164">Her durum geçişi için yangın olay vardır.</span><span class="sxs-lookup"><span data-stu-id="32c6a-164">There are events that fire for each state transition.</span></span> <span data-ttu-id="32c6a-165"><xref:System.ServiceModel.ICommunicationObject.Abort%2A> Yöntemi herhangi bir zamanda çağrılabilir ve nesne geçişi hemen geçerli durumunu kapalı duruma neden olur.</span><span class="sxs-lookup"><span data-stu-id="32c6a-165">The <xref:System.ServiceModel.ICommunicationObject.Abort%2A> method can be called at any time, and causes the object to transition immediately from its current state into the Closed state.</span></span> <span data-ttu-id="32c6a-166">Çağırma <xref:System.ServiceModel.ICommunicationObject.Abort%2A> tamamlanmamış işlerinizi sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="32c6a-166">Calling <xref:System.ServiceModel.ICommunicationObject.Abort%2A> terminates any unfinished work.</span></span>  
  
<a name="ChannelAndChannelListener"></a>   
## <a name="channel-factory-and-channel-listener"></a><span data-ttu-id="32c6a-167">Kanal fabrikası ve kanal dinleyicisi</span><span class="sxs-lookup"><span data-stu-id="32c6a-167">Channel Factory and Channel Listener</span></span>  
 <span data-ttu-id="32c6a-168">Özel bir taşıma yazma sonraki adım uygulaması oluşturmaktır <xref:System.ServiceModel.Channels.IChannelFactory> ve istemci kanallar için <xref:System.ServiceModel.Channels.IChannelListener> hizmet kanalları.</span><span class="sxs-lookup"><span data-stu-id="32c6a-168">The next step in writing a custom transport is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels and of <xref:System.ServiceModel.Channels.IChannelListener> for service channels.</span></span> <span data-ttu-id="32c6a-169">Kanal katmanını kanallar oluşturmak için bir Fabrika desen kullanır.</span><span class="sxs-lookup"><span data-stu-id="32c6a-169">The channel layer uses a factory pattern for constructing channels.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="32c6a-170">Bu işlem için temel sınıfı Yardımcıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="32c6a-170"> provides base class helpers for this process.</span></span>  
  
-   <span data-ttu-id="32c6a-171"><xref:System.ServiceModel.Channels.CommunicationObject> Uygulayan sınıf <xref:System.ServiceModel.ICommunicationObject> ve 2. adımda daha önce açıklanan durum makinesinin uygular.</span><span class="sxs-lookup"><span data-stu-id="32c6a-171">The <xref:System.ServiceModel.Channels.CommunicationObject> class implements <xref:System.ServiceModel.ICommunicationObject> and enforces the state machine previously described in Step 2.</span></span> 

-   <span data-ttu-id="32c6a-172">''<xref:System.ServiceModel.Channels.ChannelManagerBase> Uygulayan sınıf <xref:System.ServiceModel.Channels.CommunicationObject> ve birleştirilmiş bir temel sınıf sağlar <xref:System.ServiceModel.Channels.ChannelFactoryBase> ve <xref:System.ServiceModel.Channels.ChannelListenerBase>.</span><span class="sxs-lookup"><span data-stu-id="32c6a-172">The``<xref:System.ServiceModel.Channels.ChannelManagerBase> class implements <xref:System.ServiceModel.Channels.CommunicationObject> and provides a unified base class for <xref:System.ServiceModel.Channels.ChannelFactoryBase> and <xref:System.ServiceModel.Channels.ChannelListenerBase>.</span></span> <span data-ttu-id="32c6a-173"><xref:System.ServiceModel.Channels.ChannelManagerBase> Sınıfı çalışır birlikte <xref:System.ServiceModel.Channels.ChannelBase>, uygulayan bir temel sınıfı olan <xref:System.ServiceModel.Channels.IChannel>.</span><span class="sxs-lookup"><span data-stu-id="32c6a-173">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class works in conjunction with <xref:System.ServiceModel.Channels.ChannelBase>, which is a base class that implements <xref:System.ServiceModel.Channels.IChannel>.</span></span>  
  
-   <span data-ttu-id="32c6a-174">''<xref:System.ServiceModel.Channels.ChannelFactoryBase> Uygulayan sınıf <xref:System.ServiceModel.Channels.ChannelManagerBase> ve <xref:System.ServiceModel.Channels.IChannelFactory> ve birleştirir `CreateChannel` overloads birine `OnCreateChannel` soyut yöntemi.</span><span class="sxs-lookup"><span data-stu-id="32c6a-174">The``<xref:System.ServiceModel.Channels.ChannelFactoryBase> class implements <xref:System.ServiceModel.Channels.ChannelManagerBase> and <xref:System.ServiceModel.Channels.IChannelFactory> and consolidates the `CreateChannel` overloads into one `OnCreateChannel` abstract method.</span></span>  
  
-   <span data-ttu-id="32c6a-175"><xref:System.ServiceModel.Channels.ChannelListenerBase> Uygulayan sınıf <xref:System.ServiceModel.Channels.IChannelListener>.</span><span class="sxs-lookup"><span data-stu-id="32c6a-175">The <xref:System.ServiceModel.Channels.ChannelListenerBase> class implements <xref:System.ServiceModel.Channels.IChannelListener>.</span></span> <span data-ttu-id="32c6a-176">Bu temel durum yönetimini mvc'deki.</span><span class="sxs-lookup"><span data-stu-id="32c6a-176">It takes care of basic state management.</span></span>  
  
 <span data-ttu-id="32c6a-177">Bu örnekte Üreteç uygulaması UdpChannelFactory.cs içinde yer alır ve dinleyici uygulama UdpChannelListener.cs içinde yer alır.</span><span class="sxs-lookup"><span data-stu-id="32c6a-177">In this sample, the factory implementation is contained in UdpChannelFactory.cs and the listener implementation is contained in UdpChannelListener.cs.</span></span> <span data-ttu-id="32c6a-178"><xref:System.ServiceModel.Channels.IChannel> Uygulamalarıdır UdpOutputChannel.cs ve UdpInputChannel.cs.</span><span class="sxs-lookup"><span data-stu-id="32c6a-178">The <xref:System.ServiceModel.Channels.IChannel> implementations are in UdpOutputChannel.cs and UdpInputChannel.cs.</span></span>  
  
### <a name="the-udp-channel-factory"></a><span data-ttu-id="32c6a-179">UDP kanal fabrikası</span><span class="sxs-lookup"><span data-stu-id="32c6a-179">The UDP Channel Factory</span></span>  
 <span data-ttu-id="32c6a-180">`UdpChannelFactory` Türetilen <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span><span class="sxs-lookup"><span data-stu-id="32c6a-180">The `UdpChannelFactory` derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span></span> <span data-ttu-id="32c6a-181">Örnek geçersiz kılmaları <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> ileti Kodlayıcı ileti sürümü erişim sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="32c6a-181">The sample overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> to provide access to the message version of the message encoder.</span></span> <span data-ttu-id="32c6a-182">Örnek ayrıca geçersiz kılar <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> böylece biz bizim örneğini kesmeden <xref:System.ServiceModel.Channels.BufferManager> zaman durum makinesinin geçer.</span><span class="sxs-lookup"><span data-stu-id="32c6a-182">The sample also overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> so that we can tear down our instance of <xref:System.ServiceModel.Channels.BufferManager> when the state machine transitions.</span></span>  
  
#### <a name="the-udp-output-channel"></a><span data-ttu-id="32c6a-183">UDP çıktı kanalı</span><span class="sxs-lookup"><span data-stu-id="32c6a-183">The UDP Output Channel</span></span>  
 <span data-ttu-id="32c6a-184">`UdpOutputChannel` Uygulayan <xref:System.ServiceModel.Channels.IOutputChannel>.</span><span class="sxs-lookup"><span data-stu-id="32c6a-184">The `UdpOutputChannel` implements <xref:System.ServiceModel.Channels.IOutputChannel>.</span></span> <span data-ttu-id="32c6a-185">Oluşturucu bağımsız değişkenleri doğrular ve bir hedef oluşturur <xref:System.Net.EndPoint> nesne temel alarak <xref:System.ServiceModel.EndpointAddress> olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="32c6a-185">The constructor validates the arguments and constructs a destination <xref:System.Net.EndPoint> object based on the <xref:System.ServiceModel.EndpointAddress> that is passed in.</span></span>  
  
```csharp
this.socket = new Socket(this.remoteEndPoint.AddressFamily, SocketType.Dgram, ProtocolType.Udp);  
```  
  
 <span data-ttu-id="32c6a-186">Kanal düzgün biçimde veya ungracefully kapatılabilir.</span><span class="sxs-lookup"><span data-stu-id="32c6a-186">The channel can be closed gracefully or ungracefully.</span></span> <span data-ttu-id="32c6a-187">Kanal düzgün biçimde kapalıysa yuva kapatılır ve taban sınıfı için bir çağrı yapılır `OnClose` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="32c6a-187">If the channel is closed gracefully the socket is closed and a call is made to the base class `OnClose` method.</span></span> <span data-ttu-id="32c6a-188">Bu bir özel durum oluşturursa, altyapı çağırır `Abort` kanal emin olmak için temizlendi.</span><span class="sxs-lookup"><span data-stu-id="32c6a-188">If this throws an exception, the infrastructure calls `Abort` to ensure the channel is cleaned up.</span></span>  
  
```csharp
this.socket.Close(0);  
```  
  
 <span data-ttu-id="32c6a-189">Ardından uygulamak `Send()` ve `BeginSend()` / `EndSend()`.</span><span class="sxs-lookup"><span data-stu-id="32c6a-189">We then implement `Send()` and `BeginSend()`/`EndSend()`.</span></span> <span data-ttu-id="32c6a-190">Bu iki ana bölüme parçalara ayırır.</span><span class="sxs-lookup"><span data-stu-id="32c6a-190">This breaks down into two main sections.</span></span> <span data-ttu-id="32c6a-191">İlk biz ileti bir bayt dizisine serileştirir.</span><span class="sxs-lookup"><span data-stu-id="32c6a-191">First we serialize the message into a byte array.</span></span>  
  
```csharp
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 <span data-ttu-id="32c6a-192">Ardından size sonuç verileri kablo göndereceğiz.</span><span class="sxs-lookup"><span data-stu-id="32c6a-192">Then we send the resulting data on the wire.</span></span>  
  
```csharp
this.socket.SendTo(messageBuffer.Array, messageBuffer.Offset, messageBuffer.Count, SocketFlags.None, this.remoteEndPoint);  
```  
  
### <a name="the-udpchannellistener"></a><span data-ttu-id="32c6a-193">UdpChannelListener</span><span class="sxs-lookup"><span data-stu-id="32c6a-193">The UdpChannelListener</span></span>  
 <span data-ttu-id="32c6a-194">'' Örnek uygulayan UdpChannelListener türer <xref:System.ServiceModel.Channels.ChannelListenerBase> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="32c6a-194">The``UdpChannelListener that the sample implements derives from the <xref:System.ServiceModel.Channels.ChannelListenerBase> class.</span></span> <span data-ttu-id="32c6a-195">Veri birimleri almak için tek bir UDP yuva kullanır.</span><span class="sxs-lookup"><span data-stu-id="32c6a-195">It uses a single UDP socket to receive datagrams.</span></span> <span data-ttu-id="32c6a-196">`OnOpen` Yöntemi zaman uyumsuz bir döngü UDP yuvaya kullanarak verileri alır.</span><span class="sxs-lookup"><span data-stu-id="32c6a-196">The `OnOpen` method receives data using the UDP socket in an asynchronous loop.</span></span> <span data-ttu-id="32c6a-197">Veri kodlaması ileti Framework kullanarak iletilere sonra dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="32c6a-197">The data are then converted into messages using the Message Encoding Framework.</span></span>  
  
```csharp
message = MessageEncoderFactory.Encoder.ReadMessage(new ArraySegment<byte>(buffer, 0, count), bufferManager);  
```  
  
 <span data-ttu-id="32c6a-198">Bir dizi kaynaktan, gelen iletileri aynı veri birimi kanal olabilmesinden dolayı `UdpChannelListener` bir singleton dinleyicisi.</span><span class="sxs-lookup"><span data-stu-id="32c6a-198">Because the same datagram channel represents messages that arrive from a number of sources, the `UdpChannelListener` is a singleton listener.</span></span> <span data-ttu-id="32c6a-199">Yoktur, çoğu, bir etkin <xref:System.ServiceModel.Channels.IChannel>'' aynı anda bu dinleyicisi ile ilişkilendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="32c6a-199">There is, at most, one active <xref:System.ServiceModel.Channels.IChannel>``associated with this listener at a time.</span></span> <span data-ttu-id="32c6a-200">Tarafından döndürülen bir kanal, başka bir örnek oluşturur `AcceptChannel` yöntemi sonradan atıldı.</span><span class="sxs-lookup"><span data-stu-id="32c6a-200">The sample generates another one only if a channel that is returned by the `AcceptChannel` method is subsequently disposed.</span></span> <span data-ttu-id="32c6a-201">Bir ileti alındığında, sıraya alınan bu singleton kanal içine var.</span><span class="sxs-lookup"><span data-stu-id="32c6a-201">When a message is received, it is enqueued into this singleton channel.</span></span>  
  
#### <a name="udpinputchannel"></a><span data-ttu-id="32c6a-202">UdpInputChannel</span><span class="sxs-lookup"><span data-stu-id="32c6a-202">UdpInputChannel</span></span>  
 <span data-ttu-id="32c6a-203">`UdpInputChannel` Uygulayan sınıf `IInputChannel`.</span><span class="sxs-lookup"><span data-stu-id="32c6a-203">The `UdpInputChannel` class implements `IInputChannel`.</span></span> <span data-ttu-id="32c6a-204">Tarafından doldurulur gelen iletileri kuyruğunu oluşan `UdpChannelListener`kullanıcının yuva.</span><span class="sxs-lookup"><span data-stu-id="32c6a-204">It consists of a queue of incoming messages that is populated by the `UdpChannelListener`'s socket.</span></span> <span data-ttu-id="32c6a-205">Tarafından bu iletilerin kuyruktan çıkarıldı `IInputChannel.Receive` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="32c6a-205">These messages are dequeued by the `IInputChannel.Receive` method.</span></span>  
  
<a name="AddingABindingElement"></a>   
## <a name="adding-a-binding-element"></a><span data-ttu-id="32c6a-206">Bir bağlama öğesi ekleme</span><span class="sxs-lookup"><span data-stu-id="32c6a-206">Adding a Binding Element</span></span>  
 <span data-ttu-id="32c6a-207">Fabrikaları ve kanallar yerleşik, biz bunları ServiceModel çalışma zamanı için bir bağlama aracılığıyla kullanıma gerekir.</span><span class="sxs-lookup"><span data-stu-id="32c6a-207">Now that the factories and channels are built, we must expose them to the ServiceModel runtime through a binding.</span></span> <span data-ttu-id="32c6a-208">Bir bağlama hizmeti adresi ile ilişkili iletişim yığını temsil eden bağlama öğelerinin bir koleksiyondur.</span><span class="sxs-lookup"><span data-stu-id="32c6a-208">A binding is a collection of binding elements that represents the communication stack associated with a service address.</span></span> <span data-ttu-id="32c6a-209">Yığındaki her öğe tarafından temsil edilen bir [ \<bağlama >](../../../../docs/framework/misc/binding.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="32c6a-209">Each element in the stack is represented by a [\<binding>](../../../../docs/framework/misc/binding.md) element.</span></span>  
  
 <span data-ttu-id="32c6a-210">Örnekte, bağlama öğedir `UdpTransportBindingElement`, den türetilen <xref:System.ServiceModel.Channels.TransportBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="32c6a-210">In the sample, the binding element is `UdpTransportBindingElement`, which derives from <xref:System.ServiceModel.Channels.TransportBindingElement>.</span></span> <span data-ttu-id="32c6a-211">Bu bizim bağlama ile ilişkili oluşturucuları oluşturmak için aşağıdaki yöntemleri geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="32c6a-211">It overrides the following methods to build the factories associated with our binding.</span></span>  
  
```csharp
public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)  
{  
    return (IChannelFactory<TChannel>)(object)new UdpChannelFactory(this, context);  
}  
  
public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)  
{  
    return (IChannelListener<TChannel>)(object)new UdpChannelListener(this, context);  
}  
```  
  
 <span data-ttu-id="32c6a-212">Kopyalama için de üyeleri içeren `BindingElement` ve bizim düzenini (soap.udp) döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="32c6a-212">It also contains members for cloning the `BindingElement` and returning our scheme (soap.udp).</span></span>  
  
## <a name="adding-metadata-support-for-a-transport-binding-element"></a><span data-ttu-id="32c6a-213">Bağlama öğesi bir taşıma için meta verileri desteği ekleme</span><span class="sxs-lookup"><span data-stu-id="32c6a-213">Adding Metadata Support for a Transport Binding Element</span></span>  
 <span data-ttu-id="32c6a-214">Bizim aktarım meta verileri sistemle tümleştirmek için biz içeri ve dışarı aktarma İlkesi desteklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="32c6a-214">To integrate our transport into the metadata system, we must support both the import and export of policy.</span></span> <span data-ttu-id="32c6a-215">Bu bizim bağlama aracılığıyla istemcileri oluşturmak için bize sağlar [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="32c6a-215">This allows us to generate clients of our binding through the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
### <a name="adding-wsdl-support"></a><span data-ttu-id="32c6a-216">WSDL desteği ekleme</span><span class="sxs-lookup"><span data-stu-id="32c6a-216">Adding WSDL Support</span></span>  
 <span data-ttu-id="32c6a-217">Bir bağlama aktarım bağlama öğe meta verileri adresleme bilgilerini alma ve verme sorumludur.</span><span class="sxs-lookup"><span data-stu-id="32c6a-217">The transport binding element in a binding is responsible for exporting and importing addressing information in metadata.</span></span> <span data-ttu-id="32c6a-218">SOAP bağlama kullanırken, aktarım bağlama öğesi de meta verilerde doğru taşıma URI dışarı aktarmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="32c6a-218">When using a SOAP binding, the transport binding element should also export a correct transport URI in metadata.</span></span>  
  
#### <a name="wsdl-export"></a><span data-ttu-id="32c6a-219">WSDL dışarı aktarma</span><span class="sxs-lookup"><span data-stu-id="32c6a-219">WSDL Export</span></span>  
 <span data-ttu-id="32c6a-220">Adresleme bilgilerini dışarı aktarmak için `UdpTransportBindingElement` uygulayan `IWsdlExportExtension` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="32c6a-220">To export addressing information the `UdpTransportBindingElement` implements the `IWsdlExportExtension` interface.</span></span> <span data-ttu-id="32c6a-221">`ExportEndpoint` Yöntemi WSDL bağlantı noktasına doğru adresleme bilgilerini ekler.</span><span class="sxs-lookup"><span data-stu-id="32c6a-221">The `ExportEndpoint` method adds the correct addressing information to the WSDL port.</span></span>  
  
```csharp
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 <span data-ttu-id="32c6a-222">`UdpTransportBindingElement` Uyarlamasını `ExportEndpoint` yöntemi uç nokta bir SOAP bağlama kullandığında taşıma URI ayrıca verir.</span><span class="sxs-lookup"><span data-stu-id="32c6a-222">The `UdpTransportBindingElement` implementation of the `ExportEndpoint` method also exports a transport URI when the endpoint uses a SOAP binding.</span></span>  
  
```csharp
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a><span data-ttu-id="32c6a-223">WSDL içe aktarma</span><span class="sxs-lookup"><span data-stu-id="32c6a-223">WSDL Import</span></span>  
 <span data-ttu-id="32c6a-224">Adres alma işlemek için WSDL içe aktarma sistemini genişletmek için size aşağıdaki yapılandırma yapılandırma dosyasına için Svcutil.exe Svcutil.exe.config dosyasında gösterildiği gibi eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="32c6a-224">To extend the WSDL import system to handle importing the addresses, we must add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <wsdlImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="32c6a-225">Svcutil.exe çalıştırırken WSDL içe aktarma Uzantıları'nı yüklemek için Svcutil.exe alma için iki seçeneğiniz vardır:</span><span class="sxs-lookup"><span data-stu-id="32c6a-225">When running Svcutil.exe, there are two options for getting Svcutil.exe to load the WSDL import extensions:</span></span>  
  
1.  <span data-ttu-id="32c6a-226">/SvcutilConfig kullanarak bizim yapılandırma dosyasına noktası Svcutil.exe:\<Dosya >.</span><span class="sxs-lookup"><span data-stu-id="32c6a-226">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2.  <span data-ttu-id="32c6a-227">Yapılandırma bölümü için Svcutil.exe.config Svcutil.exe ile aynı dizinde ekleyin.</span><span class="sxs-lookup"><span data-stu-id="32c6a-227">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
 <span data-ttu-id="32c6a-228">`UdpBindingElementImporter` Yazın uygulayan `IWsdlImportExtension` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="32c6a-228">The `UdpBindingElementImporter` type implements the `IWsdlImportExtension` interface.</span></span> <span data-ttu-id="32c6a-229">`ImportEndpoint` Yöntemi WSDL bağlantı noktasından adresi alır.</span><span class="sxs-lookup"><span data-stu-id="32c6a-229">The `ImportEndpoint` method imports the address from the WSDL port.</span></span>  
  
```csharp
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a><span data-ttu-id="32c6a-230">İlke desteği ekleme</span><span class="sxs-lookup"><span data-stu-id="32c6a-230">Adding Policy Support</span></span>  
 <span data-ttu-id="32c6a-231">Özel bağlama öğesi bu bağlama öğesi özelliklerini ifade etmek için bir hizmet uç noktası için WSDL bağlama ilke onaylamalarını dışa aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="32c6a-231">The custom binding element can export policy assertions in the WSDL binding for a service endpoint to express the capabilities of that binding element.</span></span>  
  
#### <a name="policy-export"></a><span data-ttu-id="32c6a-232">İlke verme</span><span class="sxs-lookup"><span data-stu-id="32c6a-232">Policy Export</span></span>  
 <span data-ttu-id="32c6a-233">`UdpTransportBindingElement` Yazın uygulayan `IPolicyExportExtension` İlkesi dışarı aktarma desteği eklemek için.</span><span class="sxs-lookup"><span data-stu-id="32c6a-233">The `UdpTransportBindingElement` type implements `IPolicyExportExtension` to add support for exporting policy.</span></span> <span data-ttu-id="32c6a-234">Sonuç olarak, `System.ServiceModel.MetadataExporter` içeren `UdpTransportBindingElement` içerdiği bağlama için ilke oluşturma.</span><span class="sxs-lookup"><span data-stu-id="32c6a-234">As a result, `System.ServiceModel.MetadataExporter` includes `UdpTransportBindingElement` in the generation of policy for any binding that includes it.</span></span>  
  
 <span data-ttu-id="32c6a-235">İçinde `IPolicyExportExtension.ExportPolicy`, biz çok noktaya yayın modunda olduğunda bir onaylama UDP ve başka bir onaylama için ekleriz.</span><span class="sxs-lookup"><span data-stu-id="32c6a-235">In `IPolicyExportExtension.ExportPolicy`, we add an assertion for UDP and another assertion if we are in multicast mode.</span></span> <span data-ttu-id="32c6a-236">Çok noktaya yayın modu etkilediğinden nasıl iletişim yığını oluşturulur ve böylece her iki yüz arasındaki Eşgüdümlü olmalıdır budur.</span><span class="sxs-lookup"><span data-stu-id="32c6a-236">This is because multicast mode affects how the communication stack is constructed, and thus must be coordinated between both sides.</span></span>  
  
```csharp
ICollection<XmlElement> bindingAssertions = context.GetBindingAssertions();  
XmlDocument xmlDocument = new XmlDocument();  
bindingAssertions.Add(xmlDocument.CreateElement(  
UdpPolicyStrings.Prefix, UdpPolicyStrings.TransportAssertion, UdpPolicyStrings.UdpNamespace));  
if (Multicast)  
{  
    bindingAssertions.Add(xmlDocument.CreateElement(
        UdpPolicyStrings.Prefix, 
        UdpPolicyStrings.MulticastAssertion, 
        UdpPolicyStrings.UdpNamespace));  
}  
```  
  
 <span data-ttu-id="32c6a-237">Özel Aktarım bağlama öğeleriyle adresleme, işleme için sorumlu olduğu için `IPolicyExportExtension` mantığınız `UdpTransportBindingElement` WS adresleme sürümünü belirtmek için uygun WS adresleme ilke onaylamalarını dışa aktarma işlemesi gerekir kullanılan.</span><span class="sxs-lookup"><span data-stu-id="32c6a-237">Because custom transport binding elements are responsible for handling addressing, the `IPolicyExportExtension` implementation on the `UdpTransportBindingElement` must also handle exporting the appropriate WS-Addressing policy assertions to indicate the version of WS-Addressing being used.</span></span>  
  
```csharp
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a><span data-ttu-id="32c6a-238">İlke içeri aktarma</span><span class="sxs-lookup"><span data-stu-id="32c6a-238">Policy Import</span></span>  
 <span data-ttu-id="32c6a-239">İlke içeri aktarma sistemini genişletmek için size aşağıdaki yapılandırma yapılandırma dosyasına Svcutil.exe.config dosyasında gösterildiği gibi Svcutil.exe için eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="32c6a-239">To extend the Policy Import system, we must add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <policyImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="32c6a-240">Biz uygulamak sonra `IPolicyImporterExtension` bizim kayıtlı sınıfından (`UdpBindingElementImporter`).</span><span class="sxs-lookup"><span data-stu-id="32c6a-240">Then we implement `IPolicyImporterExtension` from our registered class (`UdpBindingElementImporter`).</span></span> <span data-ttu-id="32c6a-241">İçinde `ImportPolicy()`, biz onaylar bizim ad alanında arayın ve taşıma oluşturmak için olanları işlemek ve çok noktaya yayın olup olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="32c6a-241">In `ImportPolicy()`, we look through the assertions in our namespace, and process the ones for generating the transport and check whether it is multicast.</span></span> <span data-ttu-id="32c6a-242">İşleme onaylar de onaylar bağlama listeden kaldırmalısınız.</span><span class="sxs-lookup"><span data-stu-id="32c6a-242">We also must remove the assertions we handle from the list of binding assertions.</span></span> <span data-ttu-id="32c6a-243">Yeniden Svcutil.exe çalıştırırken, tümleştirme için iki seçenek vardır:</span><span class="sxs-lookup"><span data-stu-id="32c6a-243">Again, when running Svcutil.exe, there are two options for integration:</span></span>  
  
1.  <span data-ttu-id="32c6a-244">/SvcutilConfig kullanarak bizim yapılandırma dosyasına noktası Svcutil.exe:\<Dosya >.</span><span class="sxs-lookup"><span data-stu-id="32c6a-244">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2.  <span data-ttu-id="32c6a-245">Yapılandırma bölümü için Svcutil.exe.config Svcutil.exe ile aynı dizinde ekleyin.</span><span class="sxs-lookup"><span data-stu-id="32c6a-245">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
<a name="AddingAStandardBinding"></a>   
## <a name="adding-a-standard-binding"></a><span data-ttu-id="32c6a-246">Standart bir bağlama ekleme</span><span class="sxs-lookup"><span data-stu-id="32c6a-246">Adding a Standard Binding</span></span>  
 <span data-ttu-id="32c6a-247">Bizim bağlama öğesi aşağıdaki iki yolla kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="32c6a-247">Our binding element can be used in the following two ways:</span></span>  
  
-   <span data-ttu-id="32c6a-248">Özel bağlama üzerinden: özel bağlama bağlama öğelerinin bir rastgele kümesini temel alan kendi bağlama oluşturmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="32c6a-248">Through a custom binding: A custom binding allows the user to create their own binding based on an arbitrary set of binding elements.</span></span>  
  
-   <span data-ttu-id="32c6a-249">Sistem tarafından sağlanan bir bağlamayı kullanarak, bizim bağlama öğesi içerir.</span><span class="sxs-lookup"><span data-stu-id="32c6a-249">By using a system-provided binding that includes our binding element.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="32c6a-250">Bu sistem tarafından tanımlanan bağlama sayısı gibi sağlar `BasicHttpBinding`, `NetTcpBinding`, ve `WsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="32c6a-250"> provides a number of these system-defined bindings, such as `BasicHttpBinding`, `NetTcpBinding`, and `WsHttpBinding`.</span></span> <span data-ttu-id="32c6a-251">Bu bağlamaların her iyi tanımlanmış bir profili ile ilişkilendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="32c6a-251">Each of these bindings is associated with a well-defined profile.</span></span>  
  
 <span data-ttu-id="32c6a-252">Örnek profil bağlamasında uygulayan `SampleProfileUdpBinding`, den türetilen <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="32c6a-252">The sample implements profile binding in `SampleProfileUdpBinding`, which derives from <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="32c6a-253">`SampleProfileUdpBinding` İçindeki en fazla dört bağlama öğeleri içerir: `UdpTransportBindingElement`, `TextMessageEncodingBindingElement CompositeDuplexBindingElement`, ve `ReliableSessionBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="32c6a-253">The `SampleProfileUdpBinding` contains up to four binding elements within it: `UdpTransportBindingElement`, `TextMessageEncodingBindingElement CompositeDuplexBindingElement`, and `ReliableSessionBindingElement`.</span></span>  
  
```csharp
public override BindingElementCollection CreateBindingElements()  
{     
    BindingElementCollection bindingElements = new BindingElementCollection();  
    if (ReliableSessionEnabled)  
    {  
        bindingElements.Add(session);  
        bindingElements.Add(compositeDuplex);  
    }  
    bindingElements.Add(encoding);  
    bindingElements.Add(transport);  
    return bindingElements.Clone();  
}  
```  
  
### <a name="adding-a-custom-standard-binding-importer"></a><span data-ttu-id="32c6a-254">İçeri Aktarıcı bağlama özel bir standart ekleme</span><span class="sxs-lookup"><span data-stu-id="32c6a-254">Adding a Custom Standard Binding Importer</span></span>  
 <span data-ttu-id="32c6a-255">Svcutil.exe ve `WsdlImporter` türü, varsayılan olarak, tanır ve sistem tanımlı bağlamalar alır.</span><span class="sxs-lookup"><span data-stu-id="32c6a-255">Svcutil.exe and the `WsdlImporter` type, by default, recognizes and imports system-defined bindings.</span></span> <span data-ttu-id="32c6a-256">Aksi takdirde, bağlama içeri alır bir `CustomBinding` örneği.</span><span class="sxs-lookup"><span data-stu-id="32c6a-256">Otherwise, the binding gets imported as a `CustomBinding` instance.</span></span> <span data-ttu-id="32c6a-257">Svcutil.exe etkinleştirmek için ve `WsdlImporter` almak için `SampleProfileUdpBinding` `UdpBindingElementImporter` da özel standart bağlama alıcısı davranır.</span><span class="sxs-lookup"><span data-stu-id="32c6a-257">To enable Svcutil.exe and the `WsdlImporter` to import the `SampleProfileUdpBinding` the `UdpBindingElementImporter` also acts as a custom standard binding importer.</span></span>  
  
 <span data-ttu-id="32c6a-258">Özel standart bağlama alma uygulayan `ImportEndpoint` yöntemi `IWsdlImportExtension` incelemek için arabirimi `CustomBinding` , belirli bir standart bağlama tarafından oluşturulmuş olup olmadığını görmek için meta verileri içe örneği.</span><span class="sxs-lookup"><span data-stu-id="32c6a-258">A custom standard binding importer implements the `ImportEndpoint` method on the `IWsdlImportExtension` interface to examine the `CustomBinding` instance imported from metadata to see whether it could have been generated by a specific standard binding.</span></span>  
  
```csharp
if (context.Endpoint.Binding is CustomBinding)  
{  
    Binding binding;  
    if (transportBindingElement is UdpTransportBindingElement)  
    {  
        //if TryCreate is true, the CustomBinding will be replace by a SampleProfileUdpBinding in the  
        //generated config file for better typed generation.  
        if (SampleProfileUdpBinding.TryCreate(bindingElements, out binding))  
        {  
            binding.Name = context.Endpoint.Binding.Name;  
            binding.Namespace = context.Endpoint.Binding.Namespace;  
            context.Endpoint.Binding = binding;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="32c6a-259">Genellikle, özel standart bağlama alma uygulama standart bağlama tarafından ayarlayabilirsiniz yalnızca özellikleri değişti ve diğer tüm özellikleri varsayılanlarına olduğunu doğrulamak için içe aktarılan bağlama öğeleri özelliklerini denetleme içerir.</span><span class="sxs-lookup"><span data-stu-id="32c6a-259">Generally, implementing a custom standard binding importer involves checking the properties of the imported binding elements to verify that only properties that could have been set by the standard binding have changed and all other properties are their defaults.</span></span> <span data-ttu-id="32c6a-260">Standart bağlama alma uygulamak için bir temel stratejidir standart bağlama örneği oluşturmak için bağlama öğeleri özelliklerinden standart bağlama destekler standart bağlama örneği ve karşılaştırmak için bağlama yayma içeri aktarılan bağlama öğeleri ile standart bağlama öğeleri.</span><span class="sxs-lookup"><span data-stu-id="32c6a-260">A basic strategy for implementing a standard binding importer is to create an instance of the standard binding, propagate the properties from the binding elements to the standard binding instance that the standard binding supports, and the compare the binding elements from the standard binding with the imported binding elements.</span></span>  
  
<a name="AddingConfigurationSupport"></a>   
## <a name="adding-configuration-support"></a><span data-ttu-id="32c6a-261">Yapılandırma desteği ekleme</span><span class="sxs-lookup"><span data-stu-id="32c6a-261">Adding Configuration Support</span></span>  
 <span data-ttu-id="32c6a-262">Bizim aktarım yapılandırma yoluyla kullanıma sunmak için iki yapılandırma bölümlerinin uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="32c6a-262">To expose our transport through configuration, we must implement two configuration sections.</span></span> <span data-ttu-id="32c6a-263">İlki bir `BindingElementExtensionElement` için `UdpTransportBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="32c6a-263">The first is a `BindingElementExtensionElement` for `UdpTransportBindingElement`.</span></span> <span data-ttu-id="32c6a-264">Bu şekilde `CustomBinding` uygulamaları bizim bağlama öğesi başvurusu.</span><span class="sxs-lookup"><span data-stu-id="32c6a-264">This is so that `CustomBinding` implementations can reference our binding element.</span></span> <span data-ttu-id="32c6a-265">İkinci bir `Configuration` için bizim `SampleProfileUdpBinding`.</span><span class="sxs-lookup"><span data-stu-id="32c6a-265">The second is a `Configuration` for our `SampleProfileUdpBinding`.</span></span>  
  
### <a name="binding-element-extension-element"></a><span data-ttu-id="32c6a-266">Bağlama öğesi uzantısı öğesi</span><span class="sxs-lookup"><span data-stu-id="32c6a-266">Binding Element Extension Element</span></span>  
 <span data-ttu-id="32c6a-267">Bölüm `UdpTransportElement` olan bir `BindingElementExtensionElement` kullanıma sunan `UdpTransportBindingElement` yapılandırma sistemi.</span><span class="sxs-lookup"><span data-stu-id="32c6a-267">The section `UdpTransportElement` is a `BindingElementExtensionElement` that exposes `UdpTransportBindingElement` to the configuration system.</span></span> <span data-ttu-id="32c6a-268">Birkaç temel geçersiz kılmalar, bizim yapılandırma bölümü adı, bizim bağlama öğesi türü ve bizim bağlama öğesi oluşturmak nasıl tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="32c6a-268">With a few basic overrides, we define our configuration section name, the type of our binding element and how to create our binding element.</span></span> <span data-ttu-id="32c6a-269">Aşağıdaki kodda gösterildiği gibi bir yapılandırma dosyasına biz bizim uzantısı bölümüne sonra kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="32c6a-269">We can then register our extension section in a configuration file as shown in the following code.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <extensions>  
      <bindingElementExtensions>  
        <add name="udpTransport" type="Microsoft.ServiceModel.Samples.UdpTransportElement, UdpTransport />  
      </bindingElementExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="32c6a-270">Uzantı UDP taşıma olarak kullanmak için özel bağlamalar başvurulabilir.</span><span class="sxs-lookup"><span data-stu-id="32c6a-270">The extension can be referenced from custom bindings to use UDP as the transport.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <customBinding>  
       <binding configurationName="UdpCustomBinding">  
         <udpTransport/>  
       </binding>  
      </customBinding>  
    </bindings>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="binding-section"></a><span data-ttu-id="32c6a-271">Bölüm bağlama</span><span class="sxs-lookup"><span data-stu-id="32c6a-271">Binding Section</span></span>  
 <span data-ttu-id="32c6a-272">Bölüm `SampleProfileUdpBindingCollectionElement` olan bir `StandardBindingCollectionElement` kullanıma sunan `SampleProfileUdpBinding` yapılandırma sistemi.</span><span class="sxs-lookup"><span data-stu-id="32c6a-272">The section `SampleProfileUdpBindingCollectionElement` is a `StandardBindingCollectionElement` that exposes `SampleProfileUdpBinding` to the configuration system.</span></span> <span data-ttu-id="32c6a-273">Uygulama toplu temsilci için `SampleProfileUdpBindingConfigurationElement`, den türetilen `StandardBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="32c6a-273">The bulk of the implementation is delegated to the `SampleProfileUdpBindingConfigurationElement`, which derives from `StandardBindingElement`.</span></span> <span data-ttu-id="32c6a-274">`SampleProfileUdpBindingConfigurationElement` Özellikler üzerinde karşılık gelen özelliklere sahip `SampleProfileUdpBinding`ve eşlenecek işlevleri `ConfigurationElement` bağlama.</span><span class="sxs-lookup"><span data-stu-id="32c6a-274">The `SampleProfileUdpBindingConfigurationElement` has properties that correspond to the properties on `SampleProfileUdpBinding`, and functions to map from the `ConfigurationElement` binding.</span></span> <span data-ttu-id="32c6a-275">Son olarak, geçersiz kılma `OnApplyConfiguration` yönteminde bizim `SampleProfileUdpBinding`, aşağıdaki örnek kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="32c6a-275">Finally, override the `OnApplyConfiguration` method in our `SampleProfileUdpBinding`, as shown in the following sample code.</span></span>  
  
```csharp
protected override void OnApplyConfiguration(string configurationName)  
{  
    if (binding == null)
        throw new ArgumentNullException("binding");

    if (binding.GetType() != typeof(SampleProfileUdpBinding))
    {
        throw new ArgumentException(string.Format(CultureInfo.CurrentCulture,
            "Invalid type for binding. Expected type: {0}. Type passed in: {1}.",
            typeof(SampleProfileUdpBinding).AssemblyQualifiedName,
            binding.GetType().AssemblyQualifiedName));
    }
    SampleProfileUdpBinding udpBinding = (SampleProfileUdpBinding)binding;

    udpBinding.OrderedSession = this.OrderedSession;
    udpBinding.ReliableSessionEnabled = this.ReliableSessionEnabled;
    udpBinding.SessionInactivityTimeout = this.SessionInactivityTimeout;
    if (this.ClientBaseAddress != null)
        udpBinding.ClientBaseAddress = ClientBaseAddress;
}
```  
  
 <span data-ttu-id="32c6a-276">Bu işleyici yapılandırma sistemi ile kaydetmek için aşağıdaki bölümde ilgili yapılandırma dosyasına ekleriz.</span><span class="sxs-lookup"><span data-stu-id="32c6a-276">To register this handler with the configuration system, we add the following section to the relevant configuration file.</span></span>  
  
```xml
<configuration>  
  <configSections>  
     <sectionGroup name="system.serviceModel">  
        <sectionGroup name="bindings">  
          <section name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport />  
        </sectionGroup>  
     </sectionGroup>  
  </configSections>  
</configuration>  
```  
  
 <span data-ttu-id="32c6a-277">ServiceModel yapılandırması bölümünden sonra başvuruda bulunulabilir.</span><span class="sxs-lookup"><span data-stu-id="32c6a-277">It can then be referenced from the serviceModel configuration section.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint configurationName="calculator"  
                address="soap.udp://localhost:8001/"   
                bindingConfiguration="CalculatorServer"  
                binding="sampleProfileUdpBinding"   
                contract= "Microsoft.ServiceModel.Samples.ICalculatorContract">  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="the-udp-test-service-and-client"></a><span data-ttu-id="32c6a-278">İstemci ve UDP Test hizmeti</span><span class="sxs-lookup"><span data-stu-id="32c6a-278">The UDP Test Service and Client</span></span>  
 <span data-ttu-id="32c6a-279">Bu örnek aktarım kullanmak için test kodu UdpTestService ve UdpTestClient dizinler kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="32c6a-279">Test code for using this sample transport is available in the UdpTestService and UdpTestClient directories.</span></span> <span data-ttu-id="32c6a-280">Hizmet koduna iki sınamaları oluşur — bir test koddan bağlamalar ve uç noktaları ayarlar ve diğer yapılandırma aracılığıyla yapar.</span><span class="sxs-lookup"><span data-stu-id="32c6a-280">The service code consists of two tests—one test sets up bindings and endpoints from code and the other does it through configuration.</span></span> <span data-ttu-id="32c6a-281">Her iki testleri iki uç nokta kullanın.</span><span class="sxs-lookup"><span data-stu-id="32c6a-281">Both tests use two endpoints.</span></span> <span data-ttu-id="32c6a-282">Bir uç nokta kullanan `SampleUdpProfileBinding` ile [ \<reliableSession >](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) kümesine `true`.</span><span class="sxs-lookup"><span data-stu-id="32c6a-282">One endpoint uses the `SampleUdpProfileBinding` with [\<reliableSession>](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) set to `true`.</span></span> <span data-ttu-id="32c6a-283">Diğer uç nokta ile özel bağlama kullanan `UdpTransportBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="32c6a-283">The other endpoint uses a custom binding with `UdpTransportBindingElement`.</span></span> <span data-ttu-id="32c6a-284">Bu kullanmaya eşdeğerdir `SampleUdpProfileBinding` ile [ \<reliableSession >](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) kümesine `false`.</span><span class="sxs-lookup"><span data-stu-id="32c6a-284">This is equivalent to using `SampleUdpProfileBinding` with [\<reliableSession>](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) set to `false`.</span></span> <span data-ttu-id="32c6a-285">Her iki testleri bir hizmet oluşturmak, her bağlama için bir uç nokta ekleyin, hizmeti açın ve sonra kullanıcıya hizmet kapatmadan önce ENTER tuşuna basın bekler.</span><span class="sxs-lookup"><span data-stu-id="32c6a-285">Both tests create a service, add an endpoint for each binding, open the service and then wait for the user to hit ENTER before closing the service.</span></span>  
  
 <span data-ttu-id="32c6a-286">Hizmet test uygulaması başlattığınızda aşağıdaki çıktı görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="32c6a-286">When you start the service test application you should see the following output.</span></span>  
  
```console
Testing Udp From Code.  
Service is started from code...  
Press <ENTER> to terminate the service and start service from config...  
```  
  
 <span data-ttu-id="32c6a-287">Bu gibi durumlarda, sınama istemci uygulaması sonra yayımlanan uç noktalarına karşı çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="32c6a-287">You can then run the test client application against the published endpoints.</span></span> <span data-ttu-id="32c6a-288">İstemci test uygulaması her uç nokta için bir istemci oluşturur ve beş iletileri her uç noktasına gönderir.</span><span class="sxs-lookup"><span data-stu-id="32c6a-288">The client test application creates a client for each endpoint and sends five messages to each endpoint.</span></span> <span data-ttu-id="32c6a-289">Aşağıdaki çıkış istemcide ' dir.</span><span class="sxs-lookup"><span data-stu-id="32c6a-289">The following output is on the client.</span></span>  
  
```console
Testing Udp From Imported Files Generated By SvcUtil.  
0  
3  
6  
9  
12  
Press <ENTER> to complete test.  
```  
  
 <span data-ttu-id="32c6a-290">Hizmet tam çıktı verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="32c6a-290">The following is the full output on the service.</span></span>  
  
```console
Service is started from code...  
Press <ENTER> to terminate the service and start service from config...  
Hello, world!  
Hello, world!  
Hello, world!  
Hello, world!  
Hello, world!  
   adding 0 + 0  
   adding 1 + 2  
   adding 2 + 4  
   adding 3 + 6  
   adding 4 + 8  
```  
  
 <span data-ttu-id="32c6a-291">İstemci uygulaması yapılandırması'nı kullanarak yayımlanan uç noktalarına karşı çalıştırmak için hizmeti üzerinde ENTER tuşuna basın ve test istemcisi yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="32c6a-291">To run the client application against endpoints published using configuration, hit ENTER on the service and then run the test client again.</span></span> <span data-ttu-id="32c6a-292">Hizmette şu çıktı görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="32c6a-292">You should see the following output on the service.</span></span>  
  
```console
Testing Udp From Config.  
Service is started from config...  
Press <ENTER> to terminate the service and exit...  
```  
  
 <span data-ttu-id="32c6a-293">İstemci yeniden çalışan aynı önceki sonuçları verir.</span><span class="sxs-lookup"><span data-stu-id="32c6a-293">Running the client again yields the same as the preceding results.</span></span>  
  
 <span data-ttu-id="32c6a-294">İstemci kodu ve Svcutil.exe kullanarak yapılandırmayı yeniden oluşturmak için hizmet uygulamasını başlatın ve sonra aşağıdaki Svcutil.exe örnek kök dizininden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="32c6a-294">To regenerate the client code and configuration using Svcutil.exe, start the service application and then run the following Svcutil.exe from the root directory of the sample.</span></span>  
  
```console
svcutil http://localhost:8000/udpsample/ /reference:UdpTranport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
```  
  
 <span data-ttu-id="32c6a-295">Svcutil.exe bağlama uzantısı yapılandırması oluşturmaz Not `SampleProfileUdpBinding`, el ile eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="32c6a-295">Note that Svcutil.exe does not generate the binding extension configuration for the `SampleProfileUdpBinding`, so you must add it manually.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>      
    <extensions>  
      <!-- This was added manually because svcutil.exe does not add this extension to the file -->  
      <bindingExtensions>  
        <add name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport" />  
      </bindingExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="32c6a-296">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="32c6a-296">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="32c6a-297">Çözümü derlemek için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="32c6a-297">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="32c6a-298">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="32c6a-298">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="32c6a-299">Yukarıdaki "UDP Test hizmet ve istemci" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="32c6a-299">Refer to the preceding "The UDP Test Service and Client" section.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="32c6a-300">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="32c6a-300">The samples may already be installed on your machine.</span></span> <span data-ttu-id="32c6a-301">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="32c6a-301">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="32c6a-302">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="32c6a-302">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="32c6a-303">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="32c6a-303">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\Udp`
