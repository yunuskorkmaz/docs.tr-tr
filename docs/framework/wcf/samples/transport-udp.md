---
title: 'Taşıma: UDP'
ms.date: 03/30/2017
ms.assetid: 738705de-ad3e-40e0-b363-90305bddb140
ms.openlocfilehash: 3fd16ccd634b6875eae1e87547c35c6cba79c857
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143778"
---
# <a name="transport-udp"></a><span data-ttu-id="dd0dc-102">Taşıma: UDP</span><span class="sxs-lookup"><span data-stu-id="dd0dc-102">Transport: UDP</span></span>
<span data-ttu-id="dd0dc-103">UDP Transport örneği, udp unicast ve multicast'in özel bir Windows Communication Foundation (WCF) taşıması olarak nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-103">The UDP Transport sample demonstrates how to implement UDP unicast and multicast as a custom Windows Communication Foundation (WCF) transport.</span></span> <span data-ttu-id="dd0dc-104">Örnek, kanal çerçevesini kullanarak ve WCF en iyi uygulamalarını izleyerek WCF'de özel bir aktarım oluşturmak için önerilen yordamı açıklar.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-104">The sample describes the recommended procedure for creating a custom transport in WCF, by using the channel framework and following WCF best practices.</span></span> <span data-ttu-id="dd0dc-105">Özel bir aktarım oluşturma adımları aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="dd0dc-105">The steps to create a custom transport are as follows:</span></span>  
  
1. <span data-ttu-id="dd0dc-106">Kanal [İleti Değişim Desenleri](#MessageExchangePatterns) 'nden hangisini (IOutputChannel, IInputChannel, IDuplexChannel, IRequestChannel veya IReplyChannel) KanalFactory ve ChannelListener'ın destekleyeceğine karar verin.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-106">Decide which of the channel [Message Exchange Patterns](#MessageExchangePatterns) (IOutputChannel, IInputChannel, IDuplexChannel, IRequestChannel, or IReplyChannel) your ChannelFactory and ChannelListener will support.</span></span> <span data-ttu-id="dd0dc-107">Ardından, bu arabirimlerin oturumlu varyasyonlarını destekleyip desteklemeyeceğinize karar verin.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-107">Then decide whether you will support the sessionful variations of these interfaces.</span></span>  
  
2. <span data-ttu-id="dd0dc-108">İleti Alışverişi Modelinizi destekleyen bir kanal fabrikası ve dinleyici oluşturun.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-108">Create a channel factory and listener that support your Message Exchange Pattern.</span></span>  
  
3. <span data-ttu-id="dd0dc-109">Ağa özgü özel özel durumların uygun türemiş sınıfa normalleştirildiğinden emin <xref:System.ServiceModel.CommunicationException>olun.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-109">Ensure that any network-specific exceptions are normalized to the appropriate derived class of <xref:System.ServiceModel.CommunicationException>.</span></span>  
  
4. <span data-ttu-id="dd0dc-110">Kanal yığınına özel aktarım ekleyen [ \<bağlayıcı](../../configure-apps/file-schema/wcf/bindings.md) bir>öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-110">Add a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element that adds the custom transport to a channel stack.</span></span> <span data-ttu-id="dd0dc-111">Daha fazla bilgi için [bkz.](#AddingABindingElement)</span><span class="sxs-lookup"><span data-stu-id="dd0dc-111">For more information, see [Adding a Binding Element](#AddingABindingElement).</span></span>  
  
5. <span data-ttu-id="dd0dc-112">Yapılandırma sistemine yeni bağlama öğesi ortaya çıkarmak için bağlayıcı öğe uzantısı bölümü ekleyin.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-112">Add a binding element extension section to expose the new binding element to the configuration system.</span></span>  
  
6. <span data-ttu-id="dd0dc-113">Yetenekleri diğer uç noktalara iletmek için meta veri uzantıları ekleyin.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-113">Add metadata extensions to communicate capabilities to other endpoints.</span></span>  
  
7. <span data-ttu-id="dd0dc-114">Iyi tanımlanmış bir profile göre bağlama öğeleri yığınını önceden yapılandıran bir bağlama ekleyin.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-114">Add a binding that pre-configures a stack of binding elements according to a well-defined profile.</span></span> <span data-ttu-id="dd0dc-115">Daha fazla bilgi için [bkz.](#AddingAStandardBinding)</span><span class="sxs-lookup"><span data-stu-id="dd0dc-115">For more information, see [Adding a Standard Binding](#AddingAStandardBinding).</span></span>  
  
8. <span data-ttu-id="dd0dc-116">Yapılandırma sistemine bağlamayı ortaya çıkarmak için bağlama bölümü ve bağlama yapılandırma öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-116">Add a binding section and binding configuration element to expose the binding to the configuration system.</span></span> <span data-ttu-id="dd0dc-117">Daha fazla bilgi için [bkz.](#AddingConfigurationSupport)</span><span class="sxs-lookup"><span data-stu-id="dd0dc-117">For more information, see [Adding Configuration Support](#AddingConfigurationSupport).</span></span>  
  
<a name="MessageExchangePatterns"></a>
## <a name="message-exchange-patterns"></a><span data-ttu-id="dd0dc-118">İleti Değişim Desenleri</span><span class="sxs-lookup"><span data-stu-id="dd0dc-118">Message Exchange Patterns</span></span>  
 <span data-ttu-id="dd0dc-119">Özel bir aktarım yazmanın ilk adımı, aktarım için hangi İleti Değişim Desenleri'nin (MEP) gerekli olduğuna karar vermektir.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-119">The first step in writing a custom transport is to decide which Message Exchange Patterns (MEPs) are required for the transport.</span></span> <span data-ttu-id="dd0dc-120">Aralarından seçim yapabileceğiniz üç MEP vardır:</span><span class="sxs-lookup"><span data-stu-id="dd0dc-120">There are three MEPs to choose from:</span></span>  
  
- <span data-ttu-id="dd0dc-121">Datagram (IInputChannel/IOutputChannel)</span><span class="sxs-lookup"><span data-stu-id="dd0dc-121">Datagram (IInputChannel/IOutputChannel)</span></span>  
  
     <span data-ttu-id="dd0dc-122">Bir datagram MEP kullanırken, bir istemci bir "yangın ve unut" değişimi kullanarak bir ileti gönderir.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-122">When using a datagram MEP, a client sends a message using a "fire and forget" exchange.</span></span> <span data-ttu-id="dd0dc-123">Bir yangın ve unutmak değişimi başarılı teslimat bant dışı onay gerektiren biridir.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-123">A fire and forget exchange is one that requires out-of-band confirmation of successful delivery.</span></span> <span data-ttu-id="dd0dc-124">İleti geçiş sırasında kaybolabilir ve hizmete asla ulaşmaz.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-124">The message might be lost in transit and never reach the service.</span></span> <span data-ttu-id="dd0dc-125">Gönderme işlemi istemci sonunda başarıyla tamamlanırsa, uzak bitiş noktasının iletiyi aldığını garanti etmez.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-125">If the send operation completes successfully at the client end, it does not guarantee that the remote endpoint has received the message.</span></span> <span data-ttu-id="dd0dc-126">Veri gramı, güvenilir protokoller ve güvenli protokoller de dahil olmak üzere kendi protokollerinizi oluşturabileceğiniz için mesajlaşma için temel bir yapı taşıdır.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-126">The datagram is a fundamental building block for messaging, as you can build your own protocols on top of it—including reliable protocols and secure protocols.</span></span> <span data-ttu-id="dd0dc-127">İstemci datagram <xref:System.ServiceModel.Channels.IOutputChannel> kanalları <xref:System.ServiceModel.Channels.IInputChannel> arabirimi uygular ve hizmet datagram kanalları arabirimi uygular.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-127">Client datagram channels implement the <xref:System.ServiceModel.Channels.IOutputChannel> interface and service datagram channels implement the <xref:System.ServiceModel.Channels.IInputChannel> interface.</span></span>  
  
- <span data-ttu-id="dd0dc-128">İstek-Yanıt (IRequestChannel/IReplyChannel)</span><span class="sxs-lookup"><span data-stu-id="dd0dc-128">Request-Response (IRequestChannel/IReplyChannel)</span></span>  
  
     <span data-ttu-id="dd0dc-129">Bu MEP'de bir ileti gönderilir ve bir yanıt alınır.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-129">In this MEP, a message is sent, and a reply is received.</span></span> <span data-ttu-id="dd0dc-130">Desen istek-yanıt çiftlerinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-130">The pattern consists of request-response pairs.</span></span> <span data-ttu-id="dd0dc-131">İstek yanıt çağrılarına örnek olarak uzaktan yordam çağrıları (RPC) ve tarayıcı GET'leri verilebilir.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-131">Examples of request-response calls are remote procedure calls (RPC) and browser GETs.</span></span> <span data-ttu-id="dd0dc-132">Bu desen, Yarı Çift Yönlü olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-132">This pattern is also known as Half-Duplex.</span></span> <span data-ttu-id="dd0dc-133">Bu MEP'de istemci <xref:System.ServiceModel.Channels.IRequestChannel> kanalları uygular ve <xref:System.ServiceModel.Channels.IReplyChannel>hizmet kanalları uygular.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-133">In this MEP, client channels implement <xref:System.ServiceModel.Channels.IRequestChannel> and service channels implement <xref:System.ServiceModel.Channels.IReplyChannel>.</span></span>  
  
- <span data-ttu-id="dd0dc-134">Çift yönlü (IDuplexChannel)</span><span class="sxs-lookup"><span data-stu-id="dd0dc-134">Duplex (IDuplexChannel)</span></span>  
  
     <span data-ttu-id="dd0dc-135">Çift yönlü MEP, bir istemci tarafından rasgele sayıda iletinin gönderilmesine ve herhangi bir sırada alınmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-135">The duplex MEP allows an arbitrary number of messages to be sent by a client and received in any order.</span></span> <span data-ttu-id="dd0dc-136">Dubleks MEP, konuşulan her kelimenin bir mesaj olduğu bir telefon konuşması gibidir.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-136">The duplex MEP is like a phone conversation, where each word being spoken is a message.</span></span> <span data-ttu-id="dd0dc-137">Her iki taraf da bu MEP'de gönderip alabileceğinden, istemci <xref:System.ServiceModel.Channels.IDuplexChannel>ve servis kanalları tarafından uygulanan arabirim.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-137">Because both sides can send and receive in this MEP, the interface implemented by the client and service channels is <xref:System.ServiceModel.Channels.IDuplexChannel>.</span></span>  
  
 <span data-ttu-id="dd0dc-138">Bu MEP'lerin her biri oturumları da destekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-138">Each of these MEPs can also support sessions.</span></span> <span data-ttu-id="dd0dc-139">Oturum alabilen bir kanal tarafından sağlanan ek işlevsellik, bir kanalda gönderilen ve alınan tüm iletileri ilişkilendirmektir.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-139">The added functionality provided by a session-aware channel is that it correlates all messages sent and received on a channel.</span></span> <span data-ttu-id="dd0dc-140">İstek ve yanıt ilişkilendirilmeden İstek-Yanıt deseni tek başına bir iki ileti oturumudur.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-140">The Request-Response pattern is a stand-alone two-message session, as the request and reply are correlated.</span></span> <span data-ttu-id="dd0dc-141">Buna karşılık, oturumları destekleyen İstek-Yanıt deseni, o kanaldaki tüm istek/yanıt çiftlerinin birbiriyle ilişkili olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-141">In contrast, the Request-Response pattern that supports sessions implies that all request/response pairs on that channel are correlated with each other.</span></span> <span data-ttu-id="dd0dc-142">Bu size toplam altı MEPs-Datagram, İstek-Yanıt, Çift Yönlü, Oturumlu Datagram, oturumlarla İstek-Yanıt ve oturumlarla Çift Yönlü-seçim yapmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-142">This gives you a total of six MEPs—Datagram, Request-Response, Duplex, Datagram with sessions, Request-Response with sessions, and Duplex with sessions—to choose from.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dd0dc-143">UDP taşıma için desteklenen tek MEP Datagram'dır, çünkü UDP doğal olarak bir "ateş ve unut" protokolüdür.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-143">For the UDP transport, the only MEP that is supported is Datagram, because UDP is inherently a "fire and forget" protocol.</span></span>  
  
### <a name="the-icommunicationobject-and-the-wcf-object-lifecycle"></a><span data-ttu-id="dd0dc-144">ICommunicationObject ve WCF nesne yaşam döngüsü</span><span class="sxs-lookup"><span data-stu-id="dd0dc-144">The ICommunicationObject and the WCF object lifecycle</span></span>  
 <span data-ttu-id="dd0dc-145">WCF gibi <xref:System.ServiceModel.Channels.IChannel>nesnelerin yaşam döngüsü yönetmek için kullanılan ortak bir <xref:System.ServiceModel.Channels.IChannelFactory>durum <xref:System.ServiceModel.Channels.IChannelListener> makinesi vardır , , , ve iletişim için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-145">WCF has a common state machine that is used for managing the lifecycle of objects like <xref:System.ServiceModel.Channels.IChannel>, <xref:System.ServiceModel.Channels.IChannelFactory>, and <xref:System.ServiceModel.Channels.IChannelListener> that are used for communication.</span></span> <span data-ttu-id="dd0dc-146">Bu iletişim nesnelerinin var olabileceği beş durum vardır.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-146">There are five states in which these communication objects can exist.</span></span> <span data-ttu-id="dd0dc-147">Bu durumlar numaralandırma <xref:System.ServiceModel.CommunicationState> ile temsil edilir ve aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="dd0dc-147">These states are represented by the <xref:System.ServiceModel.CommunicationState> enumeration, and are as follows:</span></span>  
  
- <span data-ttu-id="dd0dc-148">Oluşturuldu: Bu, ilk <xref:System.ServiceModel.ICommunicationObject> anlık olarak bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-148">Created: This is the state of a <xref:System.ServiceModel.ICommunicationObject> when it is first instantiated.</span></span> <span data-ttu-id="dd0dc-149">Bu durumda giriş/çıktı (I/O) oluşmaz.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-149">No input/output (I/O) occurs in this state.</span></span>  
  
- <span data-ttu-id="dd0dc-150">Açılış: Nesneler çağrıldığında <xref:System.ServiceModel.ICommunicationObject.Open%2A> bu duruma geçiş.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-150">Opening: Objects transition to this state when <xref:System.ServiceModel.ICommunicationObject.Open%2A> is called.</span></span> <span data-ttu-id="dd0dc-151">Bu noktada özellikleri değişmez hale getirilir ve giriş/çıkış başlayabilir.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-151">At this point properties are made immutable, and input/output can begin.</span></span> <span data-ttu-id="dd0dc-152">Bu geçiş yalnızca Oluşturulan durumdan geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-152">This transition is valid only from the Created state.</span></span>  
  
- <span data-ttu-id="dd0dc-153">Açıldı: Açık işlem tamamlandığında nesneler bu duruma geçiş.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-153">Opened: Objects transition to this state when the open process completes.</span></span> <span data-ttu-id="dd0dc-154">Bu geçiş yalnızca Açılış durumundan geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-154">This transition is valid only from the Opening state.</span></span> <span data-ttu-id="dd0dc-155">Bu noktada, nesne aktarım için tamamen kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-155">At this point, the object is fully usable for transfer.</span></span>  
  
- <span data-ttu-id="dd0dc-156">Kapanış: Zarif bir kapatma <xref:System.ServiceModel.ICommunicationObject.Close%2A> çağrıldığında nesneler bu duruma geçiş.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-156">Closing: Objects transition to this state when <xref:System.ServiceModel.ICommunicationObject.Close%2A> is called for a graceful shutdown.</span></span> <span data-ttu-id="dd0dc-157">Bu geçiş yalnızca Açılan durumdan geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-157">This transition is valid only from the Opened state.</span></span>  
  
- <span data-ttu-id="dd0dc-158">Kapalı: Kapalı durumda nesneler artık kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-158">Closed: In the Closed state objects are no longer usable.</span></span> <span data-ttu-id="dd0dc-159">Genel olarak, yapılandırmanın çoğu denetim için hala erişilebilir, ancak hiçbir iletişim oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-159">In general, most configuration is still accessible for inspection, but no communication can occur.</span></span> <span data-ttu-id="dd0dc-160">Bu durum elden çıkarılmaya eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-160">This state is equivalent to being disposed.</span></span>  
  
- <span data-ttu-id="dd0dc-161">Hatalı: Hatalı durumda, nesneler denetim için erişilebilir, ancak artık kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-161">Faulted: In the Faulted state, objects are accessible to inspection but no longer usable.</span></span> <span data-ttu-id="dd0dc-162">Kurtarılamayan bir hata oluştuğunda, nesne bu duruma geçiş eder.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-162">When a non-recoverable error occurs, the object transitions into this state.</span></span> <span data-ttu-id="dd0dc-163">Bu durumdan tek geçerli geçiş `Closed` devlete.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-163">The only valid transition from this state is into the `Closed` state.</span></span>  
  
 <span data-ttu-id="dd0dc-164">Her eyalet geçişi için ateş eden olaylar vardır.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-164">There are events that fire for each state transition.</span></span> <span data-ttu-id="dd0dc-165">Yöntem <xref:System.ServiceModel.ICommunicationObject.Abort%2A> herhangi bir zamanda çağrılabilir ve nesnenin geçerli durumundan Kapalı duruma hemen geçişine neden olur.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-165">The <xref:System.ServiceModel.ICommunicationObject.Abort%2A> method can be called at any time, and causes the object to transition immediately from its current state into the Closed state.</span></span> <span data-ttu-id="dd0dc-166">Arama, <xref:System.ServiceModel.ICommunicationObject.Abort%2A> bitmemiş işleri sona erdirir.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-166">Calling <xref:System.ServiceModel.ICommunicationObject.Abort%2A> terminates any unfinished work.</span></span>  
  
<a name="ChannelAndChannelListener"></a>
## <a name="channel-factory-and-channel-listener"></a><span data-ttu-id="dd0dc-167">Kanal Fabrikası ve Kanal Dinleyicisi</span><span class="sxs-lookup"><span data-stu-id="dd0dc-167">Channel Factory and Channel Listener</span></span>  
 <span data-ttu-id="dd0dc-168">Özel bir aktarım yazmanın bir sonraki <xref:System.ServiceModel.Channels.IChannelFactory> adımı, istemci kanalları <xref:System.ServiceModel.Channels.IChannelListener> ve servis kanalları için bir uygulama oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-168">The next step in writing a custom transport is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels and of <xref:System.ServiceModel.Channels.IChannelListener> for service channels.</span></span> <span data-ttu-id="dd0dc-169">Kanal katmanı, kanal oluşturmak için bir fabrika deseni kullanır.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-169">The channel layer uses a factory pattern for constructing channels.</span></span> <span data-ttu-id="dd0dc-170">WCF bu işlem için taban sınıf yardımcıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-170">WCF provides base class helpers for this process.</span></span>  
  
- <span data-ttu-id="dd0dc-171">Sınıf, <xref:System.ServiceModel.Channels.CommunicationObject> daha <xref:System.ServiceModel.ICommunicationObject> önce Adım 2'de açıklanan durum makinesini uygular ve zorlar.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-171">The <xref:System.ServiceModel.Channels.CommunicationObject> class implements <xref:System.ServiceModel.ICommunicationObject> and enforces the state machine previously described in Step 2.</span></span>

- <span data-ttu-id="dd0dc-172">Sınıf <xref:System.ServiceModel.Channels.ChannelManagerBase> uygular <xref:System.ServiceModel.Channels.CommunicationObject> ve birleşik bir taban <xref:System.ServiceModel.Channels.ChannelFactoryBase> <xref:System.ServiceModel.Channels.ChannelListenerBase>sınıfı sağlar ve.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-172">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class implements <xref:System.ServiceModel.Channels.CommunicationObject> and provides a unified base class for <xref:System.ServiceModel.Channels.ChannelFactoryBase> and <xref:System.ServiceModel.Channels.ChannelListenerBase>.</span></span> <span data-ttu-id="dd0dc-173">Sınıf, <xref:System.ServiceModel.Channels.ChannelManagerBase> uygulayan bir <xref:System.ServiceModel.Channels.ChannelBase>taban sınıf olan ile <xref:System.ServiceModel.Channels.IChannel>birlikte çalışır.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-173">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class works in conjunction with <xref:System.ServiceModel.Channels.ChannelBase>, which is a base class that implements <xref:System.ServiceModel.Channels.IChannel>.</span></span>  
  
- <span data-ttu-id="dd0dc-174">Sınıf, <xref:System.ServiceModel.Channels.ChannelFactoryBase> <xref:System.ServiceModel.Channels.ChannelManagerBase> <xref:System.ServiceModel.Channels.IChannelFactory> `CreateChannel` aşırı yüklemeleri tek bir `OnCreateChannel` soyut yöntemde uygular ve birleştirir.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-174">The <xref:System.ServiceModel.Channels.ChannelFactoryBase> class implements <xref:System.ServiceModel.Channels.ChannelManagerBase> and <xref:System.ServiceModel.Channels.IChannelFactory> and consolidates the `CreateChannel` overloads into one `OnCreateChannel` abstract method.</span></span>  
  
- <span data-ttu-id="dd0dc-175">Sınıf <xref:System.ServiceModel.Channels.ChannelListenerBase> uygular. <xref:System.ServiceModel.Channels.IChannelListener></span><span class="sxs-lookup"><span data-stu-id="dd0dc-175">The <xref:System.ServiceModel.Channels.ChannelListenerBase> class implements <xref:System.ServiceModel.Channels.IChannelListener>.</span></span> <span data-ttu-id="dd0dc-176">Temel devlet yönetimini hallediyor.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-176">It takes care of basic state management.</span></span>  
  
 <span data-ttu-id="dd0dc-177">Bu örnekte fabrika uygulaması UdpChannelFactory.cs ve dinleyici uygulaması UdpChannelListener.cs yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-177">In this sample, the factory implementation is contained in UdpChannelFactory.cs and the listener implementation is contained in UdpChannelListener.cs.</span></span> <span data-ttu-id="dd0dc-178"><xref:System.ServiceModel.Channels.IChannel> Uygulamalar UdpOutputChannel.cs ve UdpInputChannel.cs.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-178">The <xref:System.ServiceModel.Channels.IChannel> implementations are in UdpOutputChannel.cs and UdpInputChannel.cs.</span></span>  
  
### <a name="the-udp-channel-factory"></a><span data-ttu-id="dd0dc-179">UDP Kanal Fabrikası</span><span class="sxs-lookup"><span data-stu-id="dd0dc-179">The UDP Channel Factory</span></span>  
 <span data-ttu-id="dd0dc-180"><xref:System.ServiceModel.Channels.ChannelFactoryBase>Türetilmiştir. `UdpChannelFactory`</span><span class="sxs-lookup"><span data-stu-id="dd0dc-180">The `UdpChannelFactory` derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span></span> <span data-ttu-id="dd0dc-181">Örnek, ileti <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> kodlayıcısının ileti sürümüne erişim sağlamak için geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-181">The sample overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> to provide access to the message version of the message encoder.</span></span> <span data-ttu-id="dd0dc-182">Örnek aynı zamanda, devlet makinesinin <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> <xref:System.ServiceModel.Channels.BufferManager> geçiş yaptığı örneğimizi yıkabilmemiz için de geçersiz kılıyor.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-182">The sample also overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> so that we can tear down our instance of <xref:System.ServiceModel.Channels.BufferManager> when the state machine transitions.</span></span>  
  
#### <a name="the-udp-output-channel"></a><span data-ttu-id="dd0dc-183">UDP Çıkış Kanalı</span><span class="sxs-lookup"><span data-stu-id="dd0dc-183">The UDP Output Channel</span></span>  
 <span data-ttu-id="dd0dc-184">Uygular `UdpOutputChannel` <xref:System.ServiceModel.Channels.IOutputChannel>.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-184">The `UdpOutputChannel` implements <xref:System.ServiceModel.Channels.IOutputChannel>.</span></span> <span data-ttu-id="dd0dc-185">Oluşturucu bağımsız değişkenleri doğrular ve <xref:System.Net.EndPoint> geçirilene <xref:System.ServiceModel.EndpointAddress> göre bir hedef nesnesi inşa eder.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-185">The constructor validates the arguments and constructs a destination <xref:System.Net.EndPoint> object based on the <xref:System.ServiceModel.EndpointAddress> that is passed in.</span></span>  
  
```csharp
this.socket = new Socket(this.remoteEndPoint.AddressFamily, SocketType.Dgram, ProtocolType.Udp);  
```  
  
 <span data-ttu-id="dd0dc-186">Kanal zarif veya zarif bir şekilde kapatılabilir.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-186">The channel can be closed gracefully or ungracefully.</span></span> <span data-ttu-id="dd0dc-187">Kanal incelikle kapatılırsa soket kapatılır ve taban sınıf `OnClose` yöntemine çağrı yapılır.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-187">If the channel is closed gracefully the socket is closed and a call is made to the base class `OnClose` method.</span></span> <span data-ttu-id="dd0dc-188">Bu bir özel durum oluşturursa, altyapı kanalının temizlenmesini sağlamak için çağırır. `Abort`</span><span class="sxs-lookup"><span data-stu-id="dd0dc-188">If this throws an exception, the infrastructure calls `Abort` to ensure the channel is cleaned up.</span></span>  
  
```csharp
this.socket.Close(0);  
```  
  
 <span data-ttu-id="dd0dc-189">Daha sonra `Send()` `BeginSend()` / `EndSend()`uygulamak ve .</span><span class="sxs-lookup"><span data-stu-id="dd0dc-189">We then implement `Send()` and `BeginSend()`/`EndSend()`.</span></span> <span data-ttu-id="dd0dc-190">Bu iki ana bölüme ayrılır.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-190">This breaks down into two main sections.</span></span> <span data-ttu-id="dd0dc-191">Önce iletiyi bir bayt dizisine serihale getireceğiz.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-191">First we serialize the message into a byte array.</span></span>  
  
```csharp
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 <span data-ttu-id="dd0dc-192">Sonra ortaya çıkan verileri kabloya göndeririz.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-192">Then we send the resulting data on the wire.</span></span>  
  
```csharp
this.socket.SendTo(messageBuffer.Array, messageBuffer.Offset, messageBuffer.Count, SocketFlags.None, this.remoteEndPoint);  
```  
  
### <a name="the-udpchannellistener"></a><span data-ttu-id="dd0dc-193">The UdpChannelListener</span><span class="sxs-lookup"><span data-stu-id="dd0dc-193">The UdpChannelListener</span></span>  
 <span data-ttu-id="dd0dc-194">`UdpChannelListener` Örneğin uyguladığı uygulama sınıftan <xref:System.ServiceModel.Channels.ChannelListenerBase> türetilmiştir.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-194">The `UdpChannelListener` that the sample implements derives from the <xref:System.ServiceModel.Channels.ChannelListenerBase> class.</span></span> <span data-ttu-id="dd0dc-195">Veri gramlarını almak için tek bir UDP soketi kullanır.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-195">It uses a single UDP socket to receive datagrams.</span></span> <span data-ttu-id="dd0dc-196">Yöntem, `OnOpen` udp soketi kullanarak asynchronous döngü içinde veri alır.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-196">The `OnOpen` method receives data using the UDP socket in an asynchronous loop.</span></span> <span data-ttu-id="dd0dc-197">Veriler daha sonra İleti Kodlama Çerçevesi kullanılarak iletilere dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-197">The data are then converted into messages using the Message Encoding Framework.</span></span>  
  
```csharp
message = MessageEncoderFactory.Encoder.ReadMessage(new ArraySegment<byte>(buffer, 0, count), bufferManager);  
```  
  
 <span data-ttu-id="dd0dc-198">Aynı datagram kanalı bir dizi kaynaktan gelen iletileri `UdpChannelListener` temsil ettiği için, tek tonlu bir dinleyicidir.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-198">Because the same datagram channel represents messages that arrive from a number of sources, the `UdpChannelListener` is a singleton listener.</span></span> <span data-ttu-id="dd0dc-199">Bir anda bu dinleyiciile ilişkili en fazla bir etkin vardır. <xref:System.ServiceModel.Channels.IChannel></span><span class="sxs-lookup"><span data-stu-id="dd0dc-199">There is, at most, one active <xref:System.ServiceModel.Channels.IChannel> associated with this listener at a time.</span></span> <span data-ttu-id="dd0dc-200">Örnek, yalnızca `AcceptChannel` yöntem tarafından döndürülen bir kanal sonradan imha edilirse başka bir kanal oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-200">The sample generates another one only if a channel that is returned by the `AcceptChannel` method is subsequently disposed.</span></span> <span data-ttu-id="dd0dc-201">Bir ileti alındığı zaman, bu singleton kanala sıralanır.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-201">When a message is received, it is enqueued into this singleton channel.</span></span>  
  
#### <a name="udpinputchannel"></a><span data-ttu-id="dd0dc-202">UdpInputChannel</span><span class="sxs-lookup"><span data-stu-id="dd0dc-202">UdpInputChannel</span></span>  
 <span data-ttu-id="dd0dc-203">Sınıf `UdpInputChannel` uygular. `IInputChannel`</span><span class="sxs-lookup"><span data-stu-id="dd0dc-203">The `UdpInputChannel` class implements `IInputChannel`.</span></span> <span data-ttu-id="dd0dc-204">Bu `UdpChannelListener`'soketi tarafından doldurulur gelen iletileri bir kuyruk oluşur.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-204">It consists of a queue of incoming messages that is populated by the `UdpChannelListener`'s socket.</span></span> <span data-ttu-id="dd0dc-205">Bu iletiler `IInputChannel.Receive` yöntem tarafından dequeued vardır.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-205">These messages are dequeued by the `IInputChannel.Receive` method.</span></span>  
  
<a name="AddingABindingElement"></a>
## <a name="adding-a-binding-element"></a><span data-ttu-id="dd0dc-206">Bağlama Öğesi Ekleme</span><span class="sxs-lookup"><span data-stu-id="dd0dc-206">Adding a Binding Element</span></span>  
 <span data-ttu-id="dd0dc-207">Artık fabrikalar ve kanallar inşa edildiklerine göre, onları bir bağlama yoluyla ServiceModel çalışma süresine maruz bırakmalıyız.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-207">Now that the factories and channels are built, we must expose them to the ServiceModel runtime through a binding.</span></span> <span data-ttu-id="dd0dc-208">Bağlama, bir hizmet adresiyle ilişkili iletişim yığınını temsil eden bağlama öğeleri topluluğudur.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-208">A binding is a collection of binding elements that represents the communication stack associated with a service address.</span></span> <span data-ttu-id="dd0dc-209">Yığındaki her öğe bağlayıcı bir [ \<>](../../configure-apps/file-schema/wcf/bindings.md) öğesi ile temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-209">Each element in the stack is represented by a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element.</span></span>  
  
 <span data-ttu-id="dd0dc-210">Örnekte, bağlama öğesi `UdpTransportBindingElement`, hangi türetilmiştir <xref:System.ServiceModel.Channels.TransportBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-210">In the sample, the binding element is `UdpTransportBindingElement`, which derives from <xref:System.ServiceModel.Channels.TransportBindingElement>.</span></span> <span data-ttu-id="dd0dc-211">Bizim bağlama ile ilişkili fabrikalar oluşturmak için aşağıdaki yöntemleri geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-211">It overrides the following methods to build the factories associated with our binding.</span></span>  
  
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
  
 <span data-ttu-id="dd0dc-212">Ayrıca klonlama `BindingElement` ve bizim düzeni (soap.udp) dönen üyeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-212">It also contains members for cloning the `BindingElement` and returning our scheme (soap.udp).</span></span>  
  
## <a name="adding-metadata-support-for-a-transport-binding-element"></a><span data-ttu-id="dd0dc-213">Aktarım Bağlama Öğesi için Meta Veri Desteği Ekleme</span><span class="sxs-lookup"><span data-stu-id="dd0dc-213">Adding Metadata Support for a Transport Binding Element</span></span>  
 <span data-ttu-id="dd0dc-214">Taşımamızı meta veri sistemine entegre etmek için, hem ithalatı hem de dışa aktarmayı desteklemeliyiz.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-214">To integrate our transport into the metadata system, we must support both the import and export of policy.</span></span> <span data-ttu-id="dd0dc-215">Bu bize [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)aracılığıyla bizim bağlama istemcileri oluşturmak için izin verir.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-215">This allows us to generate clients of our binding through the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
### <a name="adding-wsdl-support"></a><span data-ttu-id="dd0dc-216">WSDL Desteği Ekleme</span><span class="sxs-lookup"><span data-stu-id="dd0dc-216">Adding WSDL Support</span></span>  
 <span data-ttu-id="dd0dc-217">Bağlayıcıdaki aktarım bağlama öğesi, meta verilerdeki adresleme bilgilerinin dışa aktarılmasından ve aktarılmasından sorumludur.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-217">The transport binding element in a binding is responsible for exporting and importing addressing information in metadata.</span></span> <span data-ttu-id="dd0dc-218">SOAP bağlama kullanırken, taşıma bağlama elemanı da meta verilerde doğru bir aktarım URI dışa aktarmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-218">When using a SOAP binding, the transport binding element should also export a correct transport URI in metadata.</span></span>  
  
#### <a name="wsdl-export"></a><span data-ttu-id="dd0dc-219">WSDL İhracat</span><span class="sxs-lookup"><span data-stu-id="dd0dc-219">WSDL Export</span></span>  
 <span data-ttu-id="dd0dc-220">Adresbilgilerini dışa `UdpTransportBindingElement` aktarmak için `IWsdlExportExtension` arabirimi uygular.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-220">To export addressing information the `UdpTransportBindingElement` implements the `IWsdlExportExtension` interface.</span></span> <span data-ttu-id="dd0dc-221">Yöntem, `ExportEndpoint` WSDL bağlantı noktasına doğru adresbilgilerini ekler.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-221">The `ExportEndpoint` method adds the correct addressing information to the WSDL port.</span></span>  
  
```csharp
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 <span data-ttu-id="dd0dc-222">Yöntemin `UdpTransportBindingElement` `ExportEndpoint` uygulanması, son nokta bir SOAP bağlama kullandığında bir taşıma URI'si de dışa aktarMaktadır.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-222">The `UdpTransportBindingElement` implementation of the `ExportEndpoint` method also exports a transport URI when the endpoint uses a SOAP binding.</span></span>  
  
```csharp
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a><span data-ttu-id="dd0dc-223">WSDL İthalat</span><span class="sxs-lookup"><span data-stu-id="dd0dc-223">WSDL Import</span></span>  
 <span data-ttu-id="dd0dc-224">WSDL alma sistemini adresleri alma işlemlerini işlemek için genişletmek için, Svcutil.exe.config dosyasında gösterildiği gibi Svcutil.exe için yapılandırma dosyasına aşağıdaki yapılandırmayı eklememiz gerekir.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-224">To extend the WSDL import system to handle importing the addresses, we must add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file.</span></span>  
  
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
  
 <span data-ttu-id="dd0dc-225">Svcutil.exe çalıştırırken, WSDL alma uzantıları yüklemek için Svcutil.exe almak için iki seçenek vardır:</span><span class="sxs-lookup"><span data-stu-id="dd0dc-225">When running Svcutil.exe, there are two options for getting Svcutil.exe to load the WSDL import extensions:</span></span>  
  
1. <span data-ttu-id="dd0dc-226">Svcutil.exe'yi /SvcutilConfig kullanarak yapılandırma\<dosyamıza yönlendirin: dosya>.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-226">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2. <span data-ttu-id="dd0dc-227">Yapılandırma bölümünü Svcutil.exe ile aynı dizinde Svcutil.exe.config'e ekleyin.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-227">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
 <span data-ttu-id="dd0dc-228">Tür `UdpBindingElementImporter` `IWsdlImportExtension` arabirimi uygular.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-228">The `UdpBindingElementImporter` type implements the `IWsdlImportExtension` interface.</span></span> <span data-ttu-id="dd0dc-229">Yöntem `ImportEndpoint` adresi WSDL bağlantı noktasından içeri aktolur.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-229">The `ImportEndpoint` method imports the address from the WSDL port.</span></span>  
  
```csharp
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a><span data-ttu-id="dd0dc-230">İlke Desteği Ekleme</span><span class="sxs-lookup"><span data-stu-id="dd0dc-230">Adding Policy Support</span></span>  
 <span data-ttu-id="dd0dc-231">Özel bağlama öğesi, bu bağlama öğesinin yeteneklerini ifade etmek için bir hizmet bitiş noktası için WSDL bağlayıcıilki iddialarını dışa aktarabilir.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-231">The custom binding element can export policy assertions in the WSDL binding for a service endpoint to express the capabilities of that binding element.</span></span>  
  
#### <a name="policy-export"></a><span data-ttu-id="dd0dc-232">İlke İhracatı</span><span class="sxs-lookup"><span data-stu-id="dd0dc-232">Policy Export</span></span>  
 <span data-ttu-id="dd0dc-233">Tür, `UdpTransportBindingElement` dışa aktarma ilkesi için destek eklemek için uygular. `IPolicyExportExtension`</span><span class="sxs-lookup"><span data-stu-id="dd0dc-233">The `UdpTransportBindingElement` type implements `IPolicyExportExtension` to add support for exporting policy.</span></span> <span data-ttu-id="dd0dc-234">Sonuç olarak, `System.ServiceModel.MetadataExporter` `UdpTransportBindingElement` bunu içeren herhangi bir bağlama için ilke oluşturma içerir.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-234">As a result, `System.ServiceModel.MetadataExporter` includes `UdpTransportBindingElement` in the generation of policy for any binding that includes it.</span></span>  
  
 <span data-ttu-id="dd0dc-235">Içinde, `IPolicyExportExtension.ExportPolicy`biz çok noktaya yayın modunda ise UDP ve başka bir iddia için bir iddia ekleyin.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-235">In `IPolicyExportExtension.ExportPolicy`, we add an assertion for UDP and another assertion if we are in multicast mode.</span></span> <span data-ttu-id="dd0dc-236">Bunun nedeni, çok noktaya yayın modunun iletişim yığınının nasıl oluşturulduğuna etki etmesi ve bu nedenle her iki taraf arasında koordine edilmesi dir.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-236">This is because multicast mode affects how the communication stack is constructed, and thus must be coordinated between both sides.</span></span>  
  
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
  
 <span data-ttu-id="dd0dc-237">Özel aktarım bağlama öğeleri adresleme işlemekten sorumlu olduğundan, `IPolicyExportExtension` ws-addressing sürümünü niçin kullanıldığını göstermek için uygun WS Adresleme ilkesi iddialarını dışa aktarma yı da ele almalıdır. `UdpTransportBindingElement`</span><span class="sxs-lookup"><span data-stu-id="dd0dc-237">Because custom transport binding elements are responsible for handling addressing, the `IPolicyExportExtension` implementation on the `UdpTransportBindingElement` must also handle exporting the appropriate WS-Addressing policy assertions to indicate the version of WS-Addressing being used.</span></span>  
  
```csharp
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a><span data-ttu-id="dd0dc-238">İlke İthalatı</span><span class="sxs-lookup"><span data-stu-id="dd0dc-238">Policy Import</span></span>  
 <span data-ttu-id="dd0dc-239">İlke Alma sistemini genişletmek için, Svcutil.exe.config dosyasında gösterildiği gibi Svcutil.exe için yapılandırma dosyasına aşağıdaki yapılandırmayı eklememiz gerekir.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-239">To extend the Policy Import system, we must add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file.</span></span>  
  
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
  
 <span data-ttu-id="dd0dc-240">Sonra bizim `IPolicyImporterExtension` kayıtlı sınıftan`UdpBindingElementImporter`uygulamak ( ).</span><span class="sxs-lookup"><span data-stu-id="dd0dc-240">Then we implement `IPolicyImporterExtension` from our registered class (`UdpBindingElementImporter`).</span></span> <span data-ttu-id="dd0dc-241">'de, `ImportPolicy()`ad alanımızdaki iddialara bakarız ve taşımayı oluşturmak için olanları işleyip çok noktaya yayın olup olmadığını kontrol ediyoruz.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-241">In `ImportPolicy()`, we look through the assertions in our namespace, and process the ones for generating the transport and check whether it is multicast.</span></span> <span data-ttu-id="dd0dc-242">Ayrıca, ele aldığımız iddiaları bağlayıcı iddialar listesinden de kaldırmalıyız.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-242">We also must remove the assertions we handle from the list of binding assertions.</span></span> <span data-ttu-id="dd0dc-243">Yine, Svcutil.exe çalıştırırken, tümleştirme için iki seçenek vardır:</span><span class="sxs-lookup"><span data-stu-id="dd0dc-243">Again, when running Svcutil.exe, there are two options for integration:</span></span>  
  
1. <span data-ttu-id="dd0dc-244">Svcutil.exe'yi /SvcutilConfig kullanarak yapılandırma\<dosyamıza yönlendirin: dosya>.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-244">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2. <span data-ttu-id="dd0dc-245">Yapılandırma bölümünü Svcutil.exe ile aynı dizinde Svcutil.exe.config'e ekleyin.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-245">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
<a name="AddingAStandardBinding"></a>
## <a name="adding-a-standard-binding"></a><span data-ttu-id="dd0dc-246">Standart Bağlama Ekleme</span><span class="sxs-lookup"><span data-stu-id="dd0dc-246">Adding a Standard Binding</span></span>  
 <span data-ttu-id="dd0dc-247">Bağlama öğemiz aşağıdaki iki şekilde kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="dd0dc-247">Our binding element can be used in the following two ways:</span></span>  
  
- <span data-ttu-id="dd0dc-248">Özel bir bağlama yoluyla: Özel bir bağlama, kullanıcının rasgele bir bağlama öğesi kümesini temel alan kendi bağlamasını oluşturmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-248">Through a custom binding: A custom binding allows the user to create their own binding based on an arbitrary set of binding elements.</span></span>  
  
- <span data-ttu-id="dd0dc-249">Bağlama öğemizi içeren sistem tarafından sağlanan bir bağlama kullanarak.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-249">By using a system-provided binding that includes our binding element.</span></span> <span data-ttu-id="dd0dc-250">WCF, bu sistem tanımlı bağlamaların bir `BasicHttpBinding` `NetTcpBinding`dizi `WsHttpBinding`sini sağlar;</span><span class="sxs-lookup"><span data-stu-id="dd0dc-250">WCF provides a number of these system-defined bindings, such as `BasicHttpBinding`, `NetTcpBinding`, and `WsHttpBinding`.</span></span> <span data-ttu-id="dd0dc-251">Bu bağlamaların her biri iyi tanımlanmış bir profille ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-251">Each of these bindings is associated with a well-defined profile.</span></span>  
  
 <span data-ttu-id="dd0dc-252">`SampleProfileUdpBinding`Örnek, <xref:System.ServiceModel.Channels.Binding>'den türeyen profil bağlama' uygular.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-252">The sample implements profile binding in `SampleProfileUdpBinding`, which derives from <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="dd0dc-253">İçinde `SampleProfileUdpBinding` en fazla dört bağlama `UdpTransportBindingElement`öğesi `TextMessageEncodingBindingElement CompositeDuplexBindingElement`içerir: , , ve `ReliableSessionBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-253">The `SampleProfileUdpBinding` contains up to four binding elements within it: `UdpTransportBindingElement`, `TextMessageEncodingBindingElement CompositeDuplexBindingElement`, and `ReliableSessionBindingElement`.</span></span>  
  
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
  
### <a name="adding-a-custom-standard-binding-importer"></a><span data-ttu-id="dd0dc-254">Özel Standart Bağlama İthalatçısı Ekleme</span><span class="sxs-lookup"><span data-stu-id="dd0dc-254">Adding a Custom Standard Binding Importer</span></span>  
 <span data-ttu-id="dd0dc-255">Svcutil.exe ve `WsdlImporter` türü, varsayılan olarak, tanır ve sistem tanımlı bağlamaları alır.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-255">Svcutil.exe and the `WsdlImporter` type, by default, recognizes and imports system-defined bindings.</span></span> <span data-ttu-id="dd0dc-256">Aksi takdirde, bağlama bir `CustomBinding` örnek olarak içe aktarılır.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-256">Otherwise, the binding gets imported as a `CustomBinding` instance.</span></span> <span data-ttu-id="dd0dc-257">Svcutil.exe ve almak `WsdlImporter` `SampleProfileUdpBinding` için `UdpBindingElementImporter` de özel bir standart bağlayıcı ithalatçı olarak hareket etmesini sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-257">To enable Svcutil.exe and the `WsdlImporter` to import the `SampleProfileUdpBinding` the `UdpBindingElementImporter` also acts as a custom standard binding importer.</span></span>  
  
 <span data-ttu-id="dd0dc-258">Özel bir standart bağlayıcı içe `ImportEndpoint` aktarıcı, meta `CustomBinding` verilerden alınan örneği incelemek ve belirli bir standart bağlama tarafından oluşturulup oluşturulmadığını görmek için `IWsdlImportExtension` arabirimde yöntem uygular.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-258">A custom standard binding importer implements the `ImportEndpoint` method on the `IWsdlImportExtension` interface to examine the `CustomBinding` instance imported from metadata to see whether it could have been generated by a specific standard binding.</span></span>  
  
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
  
 <span data-ttu-id="dd0dc-259">Genel olarak, özel bir standart bağlama içe aktarma işlemi, yalnızca standart bağlama tarafından ayarlanmış olabilecek özelliklerin değiştiğini ve diğer tüm özelliklerin varsayılanları olduğunu doğrulamak için içe aktarılan bağlama öğelerinin özelliklerini denetlemeyi içerir.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-259">Generally, implementing a custom standard binding importer involves checking the properties of the imported binding elements to verify that only properties that could have been set by the standard binding have changed and all other properties are their defaults.</span></span> <span data-ttu-id="dd0dc-260">Standart bağlayıcı lık uygulamak için temel bir strateji, standart bağlamanın bir örneğini oluşturmak, özellikleri bağlama öğelerinden standart bağlamanın desteklediği standart bağlama örneğine yaymak ve bağlamayı karşılaştırmaktır. alınan bağlama elemanları ile standart bağlama öğeleri.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-260">A basic strategy for implementing a standard binding importer is to create an instance of the standard binding, propagate the properties from the binding elements to the standard binding instance that the standard binding supports, and the compare the binding elements from the standard binding with the imported binding elements.</span></span>  
  
<a name="AddingConfigurationSupport"></a>
## <a name="adding-configuration-support"></a><span data-ttu-id="dd0dc-261">Yapılandırma Desteği Ekleme</span><span class="sxs-lookup"><span data-stu-id="dd0dc-261">Adding Configuration Support</span></span>  
 <span data-ttu-id="dd0dc-262">Yapılandırma yoluyla taşımamızı ortaya çıkarmak için iki yapılandırma bölümü uygulamamız gerekir.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-262">To expose our transport through configuration, we must implement two configuration sections.</span></span> <span data-ttu-id="dd0dc-263">İlki bir `BindingElementExtensionElement` `UdpTransportBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-263">The first is a `BindingElementExtensionElement` for `UdpTransportBindingElement`.</span></span> <span data-ttu-id="dd0dc-264">Bu, `CustomBinding` uygulamaların bağlayıcı öğemize başvurması içindir.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-264">This is so that `CustomBinding` implementations can reference our binding element.</span></span> <span data-ttu-id="dd0dc-265">İkincisi bizim `Configuration` için `SampleProfileUdpBinding`.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-265">The second is a `Configuration` for our `SampleProfileUdpBinding`.</span></span>  
  
### <a name="binding-element-extension-element"></a><span data-ttu-id="dd0dc-266">Bağlama Öğesi Uzantısı Öğesi</span><span class="sxs-lookup"><span data-stu-id="dd0dc-266">Binding Element Extension Element</span></span>  
 <span data-ttu-id="dd0dc-267">Bölüm, `UdpTransportElement` yapılandırma `BindingElementExtensionElement` sistemine `UdpTransportBindingElement` maruz kalan bir bölümdür.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-267">The section `UdpTransportElement` is a `BindingElementExtensionElement` that exposes `UdpTransportBindingElement` to the configuration system.</span></span> <span data-ttu-id="dd0dc-268">Birkaç temel geçersiz kılmayla yapılandırma bölüm adımızı, bağlama öğemizin türünü ve bağlama öğemizi nasıl oluşturabileceğimizi tanımlarız.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-268">With a few basic overrides, we define our configuration section name, the type of our binding element and how to create our binding element.</span></span> <span data-ttu-id="dd0dc-269">Daha sonra uzantı bölümümüzi aşağıdaki kodda gösterildiği gibi bir yapılandırma dosyasına kaydedebiliriz.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-269">We can then register our extension section in a configuration file as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="dd0dc-270">Uzantı, udp'yi aktarım olarak kullanmak için özel bağlamalardan başvurulabilir.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-270">The extension can be referenced from custom bindings to use UDP as the transport.</span></span>  
  
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
  
### <a name="binding-section"></a><span data-ttu-id="dd0dc-271">Bağlama Bölümü</span><span class="sxs-lookup"><span data-stu-id="dd0dc-271">Binding Section</span></span>  
 <span data-ttu-id="dd0dc-272">Bölüm, `SampleProfileUdpBindingCollectionElement` yapılandırma `StandardBindingCollectionElement` sistemine `SampleProfileUdpBinding` maruz kalan bir bölümdür.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-272">The section `SampleProfileUdpBindingCollectionElement` is a `StandardBindingCollectionElement` that exposes `SampleProfileUdpBinding` to the configuration system.</span></span> <span data-ttu-id="dd0dc-273">Uygulamanın büyük bir kısmı `SampleProfileUdpBindingConfigurationElement`, ' den `StandardBindingElement`türetilen .</span><span class="sxs-lookup"><span data-stu-id="dd0dc-273">The bulk of the implementation is delegated to the `SampleProfileUdpBindingConfigurationElement`, which derives from `StandardBindingElement`.</span></span> <span data-ttu-id="dd0dc-274">Üzerinde `SampleProfileUdpBindingConfigurationElement` özellikleri `SampleProfileUdpBinding`karşılık gelen özelliklere sahip ve `ConfigurationElement` bağlama eşlenecek işlevleri.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-274">The `SampleProfileUdpBindingConfigurationElement` has properties that correspond to the properties on `SampleProfileUdpBinding`, and functions to map from the `ConfigurationElement` binding.</span></span> <span data-ttu-id="dd0dc-275">Son olarak, `OnApplyConfiguration` aşağıdaki örnek `SampleProfileUdpBinding`kodda gösterildiği gibi, bizim yöntemi geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-275">Finally, override the `OnApplyConfiguration` method in our `SampleProfileUdpBinding`, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="dd0dc-276">Bu işleyiciyi yapılandırma sistemine kaydetmek için ilgili yapılandırma dosyasına aşağıdaki bölümü ekliyoruz.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-276">To register this handler with the configuration system, we add the following section to the relevant configuration file.</span></span>  
  
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
  
 <span data-ttu-id="dd0dc-277">Daha sonra serviceModel yapılandırma bölümünden başvurulabilir.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-277">It can then be referenced from the serviceModel configuration section.</span></span>  
  
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
  
## <a name="the-udp-test-service-and-client"></a><span data-ttu-id="dd0dc-278">UDP Test Hizmeti ve İstemci</span><span class="sxs-lookup"><span data-stu-id="dd0dc-278">The UDP Test Service and Client</span></span>  
 <span data-ttu-id="dd0dc-279">Bu örnek aktarımı kullanmak için test kodu UdpTestService ve UdpTestClient dizinlerinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-279">Test code for using this sample transport is available in the UdpTestService and UdpTestClient directories.</span></span> <span data-ttu-id="dd0dc-280">Hizmet kodu iki testten oluşur— bir test koddan bağlamalar ve uç noktalar ayarlar ve diğeri yapılandırma yoluyla yapar.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-280">The service code consists of two tests—one test sets up bindings and endpoints from code and the other does it through configuration.</span></span> <span data-ttu-id="dd0dc-281">Her iki testde de iki uç nokta kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-281">Both tests use two endpoints.</span></span> <span data-ttu-id="dd0dc-282">Bir uç nokta `SampleUdpProfileBinding` [ \<ile güvenilirSession>'](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) yi `true`kullanır.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-282">One endpoint uses the `SampleUdpProfileBinding` with [\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) set to `true`.</span></span> <span data-ttu-id="dd0dc-283">Diğer uç nokta ile `UdpTransportBindingElement`özel bir bağlama kullanır.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-283">The other endpoint uses a custom binding with `UdpTransportBindingElement`.</span></span> <span data-ttu-id="dd0dc-284">Bu, güvenilir `SampleUdpProfileBinding` Oturum>ile `false`kullanmaya eşdeğerdir. [ \<](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="dd0dc-284">This is equivalent to using `SampleUdpProfileBinding` with [\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) set to `false`.</span></span> <span data-ttu-id="dd0dc-285">Her iki test de bir hizmet oluşturur, her bağlama için bir bitiş noktası ekler, hizmeti açar ve ardından kullanıcının hizmeti kapatmadan önce ENTER tuşuna basmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-285">Both tests create a service, add an endpoint for each binding, open the service and then wait for the user to hit ENTER before closing the service.</span></span>  
  
 <span data-ttu-id="dd0dc-286">Hizmet testi uygulamasını başlattığınızda aşağıdaki çıktıyı görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-286">When you start the service test application you should see the following output.</span></span>  
  
```console
Testing Udp From Code.  
Service is started from code...  
Press <ENTER> to terminate the service and start service from config...  
```  
  
 <span data-ttu-id="dd0dc-287">Daha sonra test istemcisi uygulamasını yayımlanmış uç noktalara göre çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-287">You can then run the test client application against the published endpoints.</span></span> <span data-ttu-id="dd0dc-288">İstemci test uygulaması her bitiş noktası için bir istemci oluşturur ve her bitiş noktasına beş ileti gönderir.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-288">The client test application creates a client for each endpoint and sends five messages to each endpoint.</span></span> <span data-ttu-id="dd0dc-289">Aşağıdaki çıktı istemcidedir.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-289">The following output is on the client.</span></span>  
  
```console
Testing Udp From Imported Files Generated By SvcUtil.  
0  
3  
6  
9  
12  
Press <ENTER> to complete test.  
```  
  
 <span data-ttu-id="dd0dc-290">Aşağıdaki hizmetin tam çıktısi.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-290">The following is the full output on the service.</span></span>  
  
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
  
 <span data-ttu-id="dd0dc-291">İstemci uygulamasını yapılandırma kullanılarak yayınlanan uç noktalara göre çalıştırmak için hizmette ENTER tuşuna basın ve test istemcisini yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-291">To run the client application against endpoints published using configuration, hit ENTER on the service and then run the test client again.</span></span> <span data-ttu-id="dd0dc-292">Hizmette aşağıdaki çıktıyı görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-292">You should see the following output on the service.</span></span>  
  
```console
Testing Udp From Config.  
Service is started from config...  
Press <ENTER> to terminate the service and exit...  
```  
  
 <span data-ttu-id="dd0dc-293">İstemciyi yeniden çalıştırmak, önceki sonuçlarla aynı verimi verir.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-293">Running the client again yields the same as the preceding results.</span></span>  
  
 <span data-ttu-id="dd0dc-294">Svcutil.exe kullanarak istemci kodunu ve yapılandırmasını yeniden oluşturmak için servis uygulamasını başlatın ve ardından aşağıdaki Svcutil.exe'yi örneğin kök dizininden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-294">To regenerate the client code and configuration using Svcutil.exe, start the service application and then run the following Svcutil.exe from the root directory of the sample.</span></span>  
  
```console
svcutil http://localhost:8000/udpsample/ /reference:UdpTransport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
```  
  
 <span data-ttu-id="dd0dc-295">Svcutil.exe için bağlayıcı uzantısı yapılandırma oluşturmaz `SampleProfileUdpBinding`unutmayın , bu yüzden el ile eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-295">Note that Svcutil.exe does not generate the binding extension configuration for the `SampleProfileUdpBinding`, so you must add it manually.</span></span>  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="dd0dc-296">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="dd0dc-296">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="dd0dc-297">Çözümü oluşturmak için, Windows [Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-297">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="dd0dc-298">Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-298">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
3. <span data-ttu-id="dd0dc-299">Önceki "UDP Test Hizmeti ve İstemci" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-299">Refer to the preceding "The UDP Test Service and Client" section.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="dd0dc-300">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-300">The samples may already be installed on your machine.</span></span> <span data-ttu-id="dd0dc-301">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-301">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="dd0dc-302">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-302">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="dd0dc-303">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="dd0dc-303">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\Udp`
