---
title: 'Taşıma: UDP'
ms.date: 03/30/2017
ms.assetid: 738705de-ad3e-40e0-b363-90305bddb140
ms.openlocfilehash: 051b5d6c7a1fc5d110016be9faf9b08653c28a6e
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045439"
---
# <a name="transport-udp"></a><span data-ttu-id="6ca3b-102">Taşıma: UDP</span><span class="sxs-lookup"><span data-stu-id="6ca3b-102">Transport: UDP</span></span>
<span data-ttu-id="6ca3b-103">UDP taşıma örneği, UDP tek noktaya yayın ve çok noktaya yayının özel bir Windows Communication Foundation (WCF) taşıması olarak nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-103">The UDP Transport sample demonstrates how to implement UDP unicast and multicast as a custom Windows Communication Foundation (WCF) transport.</span></span> <span data-ttu-id="6ca3b-104">Örnek, kanal çerçevesini ve aşağıdaki WCF en iyi yöntemlerini kullanarak WCF 'de özel bir aktarım oluşturmak için önerilen yordamı açıklar.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-104">The sample describes the recommended procedure for creating a custom transport in WCF, by using the channel framework and following WCF best practices.</span></span> <span data-ttu-id="6ca3b-105">Özel bir aktarım oluşturma adımları aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="6ca3b-105">The steps to create a custom transport are as follows:</span></span>  
  
1. <span data-ttu-id="6ca3b-106">ChannelFactory ve ChannelListener 'ın destekleyeceği kanal [Iletisi değişimi desenlerinin](#MessageExchangePatterns) (IOutputChannel, IInputChannel, IDuplexChannel, IRequestChannel veya IReplyChannel destekleyen desteklenecektir) hangisi olacağına karar verin.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-106">Decide which of the channel [Message Exchange Patterns](#MessageExchangePatterns) (IOutputChannel, IInputChannel, IDuplexChannel, IRequestChannel, or IReplyChannel) your ChannelFactory and ChannelListener will support.</span></span> <span data-ttu-id="6ca3b-107">Ardından, bu arabirimlerin oturumsuz çeşitlemelerini desteklememeye karar verin.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-107">Then decide whether you will support the sessionful variations of these interfaces.</span></span>  
  
2. <span data-ttu-id="6ca3b-108">Ileti değişim modelinizi destekleyen bir kanal fabrikası ve dinleyicisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-108">Create a channel factory and listener that support your Message Exchange Pattern.</span></span>  
  
3. <span data-ttu-id="6ca3b-109">Ağa özgü özel durumların, uygun türetilmiş sınıfına <xref:System.ServiceModel.CommunicationException>normalleştirildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-109">Ensure that any network-specific exceptions are normalized to the appropriate derived class of <xref:System.ServiceModel.CommunicationException>.</span></span>  
  
4. <span data-ttu-id="6ca3b-110">Özel aktarımı bir kanal yığınına ekleyen bir [ \<bağlama >](../../../../docs/framework/misc/binding.md) öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-110">Add a [\<binding>](../../../../docs/framework/misc/binding.md) element that adds the custom transport to a channel stack.</span></span> <span data-ttu-id="6ca3b-111">Daha fazla bilgi için bkz. [bağlama öğesi ekleme](#AddingABindingElement).</span><span class="sxs-lookup"><span data-stu-id="6ca3b-111">For more information, see [Adding a Binding Element](#AddingABindingElement).</span></span>  
  
5. <span data-ttu-id="6ca3b-112">Yeni bağlama öğesini yapılandırma sistemine göstermek için bağlama öğesi uzantısı bölümü ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-112">Add a binding element extension section to expose the new binding element to the configuration system.</span></span>  
  
6. <span data-ttu-id="6ca3b-113">Diğer uç noktalara iletişim kurmak için meta veri uzantıları ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-113">Add metadata extensions to communicate capabilities to other endpoints.</span></span>  
  
7. <span data-ttu-id="6ca3b-114">İyi tanımlanmış bir profile göre bağlama öğeleri yığınını önceden yapılandıran bir bağlama ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-114">Add a binding that pre-configures a stack of binding elements according to a well-defined profile.</span></span> <span data-ttu-id="6ca3b-115">Daha fazla bilgi için bkz. [Standart bağlama ekleme](#AddingAStandardBinding).</span><span class="sxs-lookup"><span data-stu-id="6ca3b-115">For more information, see [Adding a Standard Binding](#AddingAStandardBinding).</span></span>  
  
8. <span data-ttu-id="6ca3b-116">Yapılandırma sistemine bağlamayı göstermek için bağlama bölümü ve bağlama yapılandırma öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-116">Add a binding section and binding configuration element to expose the binding to the configuration system.</span></span> <span data-ttu-id="6ca3b-117">Daha fazla bilgi için bkz. [yapılandırma desteği ekleme](#AddingConfigurationSupport).</span><span class="sxs-lookup"><span data-stu-id="6ca3b-117">For more information, see [Adding Configuration Support](#AddingConfigurationSupport).</span></span>  
  
<a name="MessageExchangePatterns"></a>   
## <a name="message-exchange-patterns"></a><span data-ttu-id="6ca3b-118">İleti değişimi desenleri</span><span class="sxs-lookup"><span data-stu-id="6ca3b-118">Message Exchange Patterns</span></span>  
 <span data-ttu-id="6ca3b-119">Özel bir aktarım yazarken ilk adım, taşıma için hangi Ileti değişim desenlerinin (MEPs) gerekli olduğuna karar vermeye yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-119">The first step in writing a custom transport is to decide which Message Exchange Patterns (MEPs) are required for the transport.</span></span> <span data-ttu-id="6ca3b-120">Aralarından seçim yapabileceğiniz üç/PS vardır:</span><span class="sxs-lookup"><span data-stu-id="6ca3b-120">There are three MEPs to choose from:</span></span>  
  
- <span data-ttu-id="6ca3b-121">Veri birimi (IInputChannel/IOutputChannel)</span><span class="sxs-lookup"><span data-stu-id="6ca3b-121">Datagram (IInputChannel/IOutputChannel)</span></span>  
  
     <span data-ttu-id="6ca3b-122">Bir veri birimi MEP kullanırken, istemci "yangın ve unut" Exchange kullanarak bir ileti gönderir.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-122">When using a datagram MEP, a client sends a message using a "fire and forget" exchange.</span></span> <span data-ttu-id="6ca3b-123">Bir ateş ve unutur, başarılı teslimin bant dışı onayını gerektiren bir adım.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-123">A fire and forget exchange is one that requires out-of-band confirmation of successful delivery.</span></span> <span data-ttu-id="6ca3b-124">İleti iletimde kaybolmuş olabilir ve hizmete hiçbir şekilde ulaşamamalıdır.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-124">The message might be lost in transit and never reach the service.</span></span> <span data-ttu-id="6ca3b-125">Gönderme işlemi istemci sonunda başarıyla tamamlanırsa, uzak uç noktanın iletiyi aldığını garanti etmez.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-125">If the send operation completes successfully at the client end, it does not guarantee that the remote endpoint has received the message.</span></span> <span data-ttu-id="6ca3b-126">Bu veri birimi, güvenilir protokoller ve güvenli protokoller de dahil olmak üzere kendi protokollerinizi oluşturabileceğiniz gibi, mesajlaşma için temel bir yapı taşıdır.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-126">The datagram is a fundamental building block for messaging, as you can build your own protocols on top of it—including reliable protocols and secure protocols.</span></span> <span data-ttu-id="6ca3b-127">İstemci veri birimi kanalları arabirimini <xref:System.ServiceModel.Channels.IOutputChannel> <xref:System.ServiceModel.Channels.IInputChannel> uygulayan arabirimi ve hizmet veri birimi kanallarını uygular.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-127">Client datagram channels implement the <xref:System.ServiceModel.Channels.IOutputChannel> interface and service datagram channels implement the <xref:System.ServiceModel.Channels.IInputChannel> interface.</span></span>  
  
- <span data-ttu-id="6ca3b-128">İstek-yanıt (IRequestChannel/IReplyChannel destekleyen desteklenecektir)</span><span class="sxs-lookup"><span data-stu-id="6ca3b-128">Request-Response (IRequestChannel/IReplyChannel)</span></span>  
  
     <span data-ttu-id="6ca3b-129">Bu MEP 'de bir ileti gönderilir ve bir yanıt alındı.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-129">In this MEP, a message is sent, and a reply is received.</span></span> <span data-ttu-id="6ca3b-130">Bu model, istek-yanıt çiftlerinden oluşur.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-130">The pattern consists of request-response pairs.</span></span> <span data-ttu-id="6ca3b-131">İstek-yanıt çağrısı örnekleri, uzak yordam çağrılardır (RPC) ve tarayıcı alır.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-131">Examples of request-response calls are remote procedure calls (RPC) and browser GETs.</span></span> <span data-ttu-id="6ca3b-132">Bu model, yarı çift yönlü olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-132">This pattern is also known as Half-Duplex.</span></span> <span data-ttu-id="6ca3b-133">Bu MEP 'de, istemci kanalları <xref:System.ServiceModel.Channels.IRequestChannel> ve hizmet kanalları uygular. <xref:System.ServiceModel.Channels.IReplyChannel></span><span class="sxs-lookup"><span data-stu-id="6ca3b-133">In this MEP, client channels implement <xref:System.ServiceModel.Channels.IRequestChannel> and service channels implement <xref:System.ServiceModel.Channels.IReplyChannel>.</span></span>  
  
- <span data-ttu-id="6ca3b-134">Çift yönlü (IDuplexChannel)</span><span class="sxs-lookup"><span data-stu-id="6ca3b-134">Duplex (IDuplexChannel)</span></span>  
  
     <span data-ttu-id="6ca3b-135">Çift yönlü MEP, istemci tarafından rastgele sayıda iletinin gönderilmesini ve herhangi bir sırada alınmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-135">The duplex MEP allows an arbitrary number of messages to be sent by a client and received in any order.</span></span> <span data-ttu-id="6ca3b-136">Çift yönlü MEP, konuşulan her sözcüğün bir ileti olduğu bir telefon konuşması gibidir.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-136">The duplex MEP is like a phone conversation, where each word being spoken is a message.</span></span> <span data-ttu-id="6ca3b-137">Her iki taraf da bu MEP 'de gönderebildiğinden ve alabileceği için, istemci ve hizmet kanalları <xref:System.ServiceModel.Channels.IDuplexChannel>tarafından uygulanan arabirim.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-137">Because both sides can send and receive in this MEP, the interface implemented by the client and service channels is <xref:System.ServiceModel.Channels.IDuplexChannel>.</span></span>  
  
 <span data-ttu-id="6ca3b-138">Bu MEPs 'lerin her biri, oturumları da destekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-138">Each of these MEPs can also support sessions.</span></span> <span data-ttu-id="6ca3b-139">Oturum kullanan bir kanal tarafından sunulan ek işlevsellik, bir kanalda gönderilen ve alınan tüm iletileri ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-139">The added functionality provided by a session-aware channel is that it correlates all messages sent and received on a channel.</span></span> <span data-ttu-id="6ca3b-140">İstek ve yanıt bağıntılı olduğundan, Istek-yanıt deseninin tek başına iki ileti oturumu vardır.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-140">The Request-Response pattern is a stand-alone two-message session, as the request and reply are correlated.</span></span> <span data-ttu-id="6ca3b-141">Buna karşılık, oturumları destekleyen Istek-yanıt deseninin, o kanaldaki tüm istek/yanıt çiftlerinin birbirleriyle bağıntılı olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-141">In contrast, the Request-Response pattern that supports sessions implies that all request/response pairs on that channel are correlated with each other.</span></span> <span data-ttu-id="6ca3b-142">Bu, arasından seçim yapmak için toplam altı adet, veri birimi, Istek-yanıt, çift yönlü, oturumlarla oturum, oturum Isteği ve oturumlarla çift yönlü veri birimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-142">This gives you a total of six MEPs—Datagram, Request-Response, Duplex, Datagram with sessions, Request-Response with sessions, and Duplex with sessions—to choose from.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6ca3b-143">UDP bir "yangın ve unut" Protokolü olduğundan, UDP taşıması için desteklenen tek MEP yalnızca veri birimi olur.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-143">For the UDP transport, the only MEP that is supported is Datagram, because UDP is inherently a "fire and forget" protocol.</span></span>  
  
### <a name="the-icommunicationobject-and-the-wcf-object-lifecycle"></a><span data-ttu-id="6ca3b-144">Idimmunicationobject ve WCF nesne yaşam döngüsü</span><span class="sxs-lookup"><span data-stu-id="6ca3b-144">The ICommunicationObject and the WCF object lifecycle</span></span>  
 <span data-ttu-id="6ca3b-145">WCF,, ve gibi <xref:System.ServiceModel.Channels.IChannel> <xref:System.ServiceModel.Channels.IChannelFactory>nesnelerin yaşam döngüsünü yönetmek için kullanılan, ve <xref:System.ServiceModel.Channels.IChannelListener> iletişim için kullanılan bir ortak durum makinesine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-145">WCF has a common state machine that is used for managing the lifecycle of objects like <xref:System.ServiceModel.Channels.IChannel>, <xref:System.ServiceModel.Channels.IChannelFactory>, and <xref:System.ServiceModel.Channels.IChannelListener> that are used for communication.</span></span> <span data-ttu-id="6ca3b-146">Bu iletişim nesnelerinin bulunabileceği beş durum vardır.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-146">There are five states in which these communication objects can exist.</span></span> <span data-ttu-id="6ca3b-147">Bu durumlar, <xref:System.ServiceModel.CommunicationState> sabit listesi tarafından temsil edilir ve aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="6ca3b-147">These states are represented by the <xref:System.ServiceModel.CommunicationState> enumeration, and are as follows:</span></span>  
  
- <span data-ttu-id="6ca3b-148">Yaratıl Bu, ilk örneklendiği <xref:System.ServiceModel.ICommunicationObject> zaman öğesinin durumudur.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-148">Created: This is the state of a <xref:System.ServiceModel.ICommunicationObject> when it is first instantiated.</span></span> <span data-ttu-id="6ca3b-149">Bu durumda giriş/çıkış (g/ç) oluşmaz.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-149">No input/output (I/O) occurs in this state.</span></span>  
  
- <span data-ttu-id="6ca3b-150">Açma Çağrıldığında nesneler bu duruma <xref:System.ServiceModel.ICommunicationObject.Open%2A> geçer.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-150">Opening: Objects transition to this state when <xref:System.ServiceModel.ICommunicationObject.Open%2A> is called.</span></span> <span data-ttu-id="6ca3b-151">Bu noktada özellikler sabit hale getirilir ve giriş/çıkış başlayabilir.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-151">At this point properties are made immutable, and input/output can begin.</span></span> <span data-ttu-id="6ca3b-152">Bu geçiş yalnızca oluşturulan durumdan geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-152">This transition is valid only from the Created state.</span></span>  
  
- <span data-ttu-id="6ca3b-153">Makta Nesneler, açık işlem tamamlandığında bu duruma geçiş yapar.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-153">Opened: Objects transition to this state when the open process completes.</span></span> <span data-ttu-id="6ca3b-154">Bu geçiş yalnızca açma durumunda geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-154">This transition is valid only from the Opening state.</span></span> <span data-ttu-id="6ca3b-155">Bu noktada, nesne aktarım için tamamen kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-155">At this point, the object is fully usable for transfer.</span></span>  
  
- <span data-ttu-id="6ca3b-156">Ayraç Nesneler düzgün kapanma için çağrıldığında bu <xref:System.ServiceModel.ICommunicationObject.Close%2A> duruma geçiş yapılır.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-156">Closing: Objects transition to this state when <xref:System.ServiceModel.ICommunicationObject.Close%2A> is called for a graceful shutdown.</span></span> <span data-ttu-id="6ca3b-157">Bu geçiş yalnızca açık durumda geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-157">This transition is valid only from the Opened state.</span></span>  
  
- <span data-ttu-id="6ca3b-158">Kapandı Kapalı durum nesnelerinde artık kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-158">Closed: In the Closed state objects are no longer usable.</span></span> <span data-ttu-id="6ca3b-159">Genel olarak, çoğu yapılandırmaya hala inceleme için erişilebilir, ancak hiçbir iletişim gerçekleşmez.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-159">In general, most configuration is still accessible for inspection, but no communication can occur.</span></span> <span data-ttu-id="6ca3b-160">Bu durum atılmıştı.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-160">This state is equivalent to being disposed.</span></span>  
  
- <span data-ttu-id="6ca3b-161">Alındı Hatalı durumda, nesnelere denetim için erişilebilir ancak artık kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-161">Faulted: In the Faulted state, objects are accessible to inspection but no longer usable.</span></span> <span data-ttu-id="6ca3b-162">Kurtarılabilir olmayan bir hata oluştuğunda, nesne bu duruma geçer.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-162">When a non-recoverable error occurs, the object transitions into this state.</span></span> <span data-ttu-id="6ca3b-163">Bu durumdan geçerli olan tek geçiş `Closed` durumunda olur.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-163">The only valid transition from this state is into the `Closed` state.</span></span>  
  
 <span data-ttu-id="6ca3b-164">Her durum geçişi için başlatılan olaylar vardır.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-164">There are events that fire for each state transition.</span></span> <span data-ttu-id="6ca3b-165"><xref:System.ServiceModel.ICommunicationObject.Abort%2A> Yöntemi herhangi bir zamanda çağrılabilir ve nesnenin geçerli durumundan Kapalı durumuna geçmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-165">The <xref:System.ServiceModel.ICommunicationObject.Abort%2A> method can be called at any time, and causes the object to transition immediately from its current state into the Closed state.</span></span> <span data-ttu-id="6ca3b-166">Çağırma <xref:System.ServiceModel.ICommunicationObject.Abort%2A> , tamamlanmamış işleri sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-166">Calling <xref:System.ServiceModel.ICommunicationObject.Abort%2A> terminates any unfinished work.</span></span>  
  
<a name="ChannelAndChannelListener"></a>   
## <a name="channel-factory-and-channel-listener"></a><span data-ttu-id="6ca3b-167">Kanal fabrikası ve kanal dinleyicisi</span><span class="sxs-lookup"><span data-stu-id="6ca3b-167">Channel Factory and Channel Listener</span></span>  
 <span data-ttu-id="6ca3b-168">Özel bir aktarım yazarken bir sonraki adım, istemci kanalları <xref:System.ServiceModel.Channels.IChannelFactory> <xref:System.ServiceModel.Channels.IChannelListener> ve hizmet kanalları için bir uygulama oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-168">The next step in writing a custom transport is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels and of <xref:System.ServiceModel.Channels.IChannelListener> for service channels.</span></span> <span data-ttu-id="6ca3b-169">Kanal katmanı, kanal oluşturmak için bir fabrika kalıbı kullanır.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-169">The channel layer uses a factory pattern for constructing channels.</span></span> <span data-ttu-id="6ca3b-170">WCF bu işlem için temel sınıf yardımcıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-170">WCF provides base class helpers for this process.</span></span>  
  
- <span data-ttu-id="6ca3b-171">Sınıfı <xref:System.ServiceModel.Channels.CommunicationObject> , daha <xref:System.ServiceModel.ICommunicationObject> önce 2. adımda açıklanan durum makinesini uygular ve uygular.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-171">The <xref:System.ServiceModel.Channels.CommunicationObject> class implements <xref:System.ServiceModel.ICommunicationObject> and enforces the state machine previously described in Step 2.</span></span> 

- <span data-ttu-id="6ca3b-172">Sınıfı, <xref:System.ServiceModel.Channels.ChannelManagerBase>ve içinBirleşikbir<xref:System.ServiceModel.Channels.ChannelFactoryBase>temel sınıfsağlar.<xref:System.ServiceModel.Channels.ChannelListenerBase> <xref:System.ServiceModel.Channels.CommunicationObject></span><span class="sxs-lookup"><span data-stu-id="6ca3b-172">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class implements <xref:System.ServiceModel.Channels.CommunicationObject> and provides a unified base class for <xref:System.ServiceModel.Channels.ChannelFactoryBase> and <xref:System.ServiceModel.Channels.ChannelListenerBase>.</span></span> <span data-ttu-id="6ca3b-173">Sınıfı ile <xref:System.ServiceModel.Channels.ChannelBase>birlikte çalışarak, uygulayan <xref:System.ServiceModel.Channels.IChannel>bir temel sınıf olan. <xref:System.ServiceModel.Channels.ChannelManagerBase></span><span class="sxs-lookup"><span data-stu-id="6ca3b-173">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class works in conjunction with <xref:System.ServiceModel.Channels.ChannelBase>, which is a base class that implements <xref:System.ServiceModel.Channels.IChannel>.</span></span>  
  
- <span data-ttu-id="6ca3b-174">`CreateChannel` <xref:System.ServiceModel.Channels.ChannelManagerBase> Sınıfı,<xref:System.ServiceModel.Channels.IChannelFactory> ve yüklerini tek bir`OnCreateChannel` soyut yöntemde uygular ve birleştirir. <xref:System.ServiceModel.Channels.ChannelFactoryBase></span><span class="sxs-lookup"><span data-stu-id="6ca3b-174">The <xref:System.ServiceModel.Channels.ChannelFactoryBase> class implements <xref:System.ServiceModel.Channels.ChannelManagerBase> and <xref:System.ServiceModel.Channels.IChannelFactory> and consolidates the `CreateChannel` overloads into one `OnCreateChannel` abstract method.</span></span>  
  
- <span data-ttu-id="6ca3b-175"><xref:System.ServiceModel.Channels.ChannelListenerBase> Sınıfı uygular<xref:System.ServiceModel.Channels.IChannelListener>.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-175">The <xref:System.ServiceModel.Channels.ChannelListenerBase> class implements <xref:System.ServiceModel.Channels.IChannelListener>.</span></span> <span data-ttu-id="6ca3b-176">Temel durum yönetiminden çok dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-176">It takes care of basic state management.</span></span>  
  
 <span data-ttu-id="6ca3b-177">Bu örnekte, fabrika uygulamasının UdpChannelFactory.cs içinde yer aldığı ve dinleyici uygulamasının UdpChannelListener.cs içinde yer aldığı.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-177">In this sample, the factory implementation is contained in UdpChannelFactory.cs and the listener implementation is contained in UdpChannelListener.cs.</span></span> <span data-ttu-id="6ca3b-178"><xref:System.ServiceModel.Channels.IChannel> Uygulamalar UdpOutputChannel.cs ve UdpInputChannel.cs ' dir.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-178">The <xref:System.ServiceModel.Channels.IChannel> implementations are in UdpOutputChannel.cs and UdpInputChannel.cs.</span></span>  
  
### <a name="the-udp-channel-factory"></a><span data-ttu-id="6ca3b-179">UDP kanal fabrikası</span><span class="sxs-lookup"><span data-stu-id="6ca3b-179">The UDP Channel Factory</span></span>  
 <span data-ttu-id="6ca3b-180">`UdpChannelFactory` Öğesinden<xref:System.ServiceModel.Channels.ChannelFactoryBase>türetilir.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-180">The `UdpChannelFactory` derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span></span> <span data-ttu-id="6ca3b-181">Örnek, ileti <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> kodlayıcının ileti sürümüne erişim sağlamak için geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-181">The sample overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> to provide access to the message version of the message encoder.</span></span> <span data-ttu-id="6ca3b-182">Örnek ayrıca durum makinesi <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> geçişi <xref:System.ServiceModel.Channels.BufferManager> sırasında örneğimizi daha fazla belirleyebilmemiz için geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-182">The sample also overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> so that we can tear down our instance of <xref:System.ServiceModel.Channels.BufferManager> when the state machine transitions.</span></span>  
  
#### <a name="the-udp-output-channel"></a><span data-ttu-id="6ca3b-183">UDP çıkış kanalı</span><span class="sxs-lookup"><span data-stu-id="6ca3b-183">The UDP Output Channel</span></span>  
 <span data-ttu-id="6ca3b-184">`UdpOutputChannel` Uygular .<xref:System.ServiceModel.Channels.IOutputChannel></span><span class="sxs-lookup"><span data-stu-id="6ca3b-184">The `UdpOutputChannel` implements <xref:System.ServiceModel.Channels.IOutputChannel>.</span></span> <span data-ttu-id="6ca3b-185">Oluşturucu bağımsız değişkenleri doğrular ve geçirilen öğesine bağlı <xref:System.Net.EndPoint> <xref:System.ServiceModel.EndpointAddress> olarak bir hedef nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-185">The constructor validates the arguments and constructs a destination <xref:System.Net.EndPoint> object based on the <xref:System.ServiceModel.EndpointAddress> that is passed in.</span></span>  
  
```csharp
this.socket = new Socket(this.remoteEndPoint.AddressFamily, SocketType.Dgram, ProtocolType.Udp);  
```  
  
 <span data-ttu-id="6ca3b-186">Kanal düzgün şekilde kapatılabilir veya düzgün şekilde kapatılabilir.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-186">The channel can be closed gracefully or ungracefully.</span></span> <span data-ttu-id="6ca3b-187">Kanal kapalıysa, yuva kapanır ve temel sınıf `OnClose` yöntemine bir çağrı yapılır.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-187">If the channel is closed gracefully the socket is closed and a call is made to the base class `OnClose` method.</span></span> <span data-ttu-id="6ca3b-188">Bu, bir özel durum oluşturursa, kanalın temizlendiğinden `Abort` emin olmak için altyapı çağrılır.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-188">If this throws an exception, the infrastructure calls `Abort` to ensure the channel is cleaned up.</span></span>  
  
```csharp
this.socket.Close(0);  
```  
  
 <span data-ttu-id="6ca3b-189">Ardından, ve `Send()` ' `BeginSend()` /i uyguladık.`EndSend()`</span><span class="sxs-lookup"><span data-stu-id="6ca3b-189">We then implement `Send()` and `BeginSend()`/`EndSend()`.</span></span> <span data-ttu-id="6ca3b-190">Bu, iki ana bölümde kesilir.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-190">This breaks down into two main sections.</span></span> <span data-ttu-id="6ca3b-191">İlk olarak, iletiyi bir bayt dizisine serileştirtik.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-191">First we serialize the message into a byte array.</span></span>  
  
```csharp
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 <span data-ttu-id="6ca3b-192">Sonuç olarak elde edilen verileri tel olarak göndereceğiz.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-192">Then we send the resulting data on the wire.</span></span>  
  
```csharp
this.socket.SendTo(messageBuffer.Array, messageBuffer.Offset, messageBuffer.Count, SocketFlags.None, this.remoteEndPoint);  
```  
  
### <a name="the-udpchannellistener"></a><span data-ttu-id="6ca3b-193">UdpChannelListener</span><span class="sxs-lookup"><span data-stu-id="6ca3b-193">The UdpChannelListener</span></span>  
 <span data-ttu-id="6ca3b-194">Örneğin uyguladığı örnek <xref:System.ServiceModel.Channels.ChannelListenerBase> sınıfından türetiliyor. `UdpChannelListener`</span><span class="sxs-lookup"><span data-stu-id="6ca3b-194">The `UdpChannelListener` that the sample implements derives from the <xref:System.ServiceModel.Channels.ChannelListenerBase> class.</span></span> <span data-ttu-id="6ca3b-195">Veri birimlerini almak için tek bir UDP yuvası kullanır.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-195">It uses a single UDP socket to receive datagrams.</span></span> <span data-ttu-id="6ca3b-196">Yöntemi `OnOpen` , UDP yuvasını zaman uyumsuz bir döngüde kullanarak verileri alır.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-196">The `OnOpen` method receives data using the UDP socket in an asynchronous loop.</span></span> <span data-ttu-id="6ca3b-197">Veriler daha sonra Ileti kodlama çerçevesi kullanılarak iletilere dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-197">The data are then converted into messages using the Message Encoding Framework.</span></span>  
  
```csharp
message = MessageEncoderFactory.Encoder.ReadMessage(new ArraySegment<byte>(buffer, 0, count), bufferManager);  
```  
  
 <span data-ttu-id="6ca3b-198">Aynı veri birimi kanalı, bir dizi kaynaktan `UdpChannelListener` gelen iletileri temsil ettiğinden, tek bir dinleyici olur.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-198">Because the same datagram channel represents messages that arrive from a number of sources, the `UdpChannelListener` is a singleton listener.</span></span> <span data-ttu-id="6ca3b-199">En çok, bu dinleyiciyle aynı anda <xref:System.ServiceModel.Channels.IChannel> bir tane olmak üzere bir etkin.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-199">There is, at most, one active <xref:System.ServiceModel.Channels.IChannel> associated with this listener at a time.</span></span> <span data-ttu-id="6ca3b-200">Örnek, yalnızca `AcceptChannel` yöntemi tarafından döndürülen bir kanal daha sonra atıldığı takdirde bir tane oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-200">The sample generates another one only if a channel that is returned by the `AcceptChannel` method is subsequently disposed.</span></span> <span data-ttu-id="6ca3b-201">Bir ileti alındığında, bu Singleton kanalında sıraya alınır.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-201">When a message is received, it is enqueued into this singleton channel.</span></span>  
  
#### <a name="udpinputchannel"></a><span data-ttu-id="6ca3b-202">UdpInputChannel</span><span class="sxs-lookup"><span data-stu-id="6ca3b-202">UdpInputChannel</span></span>  
 <span data-ttu-id="6ca3b-203">`UdpInputChannel` Sınıfı uygular`IInputChannel`.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-203">The `UdpInputChannel` class implements `IInputChannel`.</span></span> <span data-ttu-id="6ca3b-204">Bu, `UdpChannelListener`kendi yuvası tarafından doldurulan bir gelen ileti kuyruğundan oluşur.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-204">It consists of a queue of incoming messages that is populated by the `UdpChannelListener`'s socket.</span></span> <span data-ttu-id="6ca3b-205">Bu iletiler `IInputChannel.Receive` yöntemi tarafından kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-205">These messages are dequeued by the `IInputChannel.Receive` method.</span></span>  
  
<a name="AddingABindingElement"></a>   
## <a name="adding-a-binding-element"></a><span data-ttu-id="6ca3b-206">Bağlama öğesi ekleme</span><span class="sxs-lookup"><span data-stu-id="6ca3b-206">Adding a Binding Element</span></span>  
 <span data-ttu-id="6ca3b-207">Fabrikalar ve kanallar derlenmesine göre, bunları bir bağlama aracılığıyla ServiceModel çalışma zamanına göstermemiz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-207">Now that the factories and channels are built, we must expose them to the ServiceModel runtime through a binding.</span></span> <span data-ttu-id="6ca3b-208">Bağlama, bir hizmet adresiyle ilişkili iletişim yığınını temsil eden bağlama öğelerinin koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-208">A binding is a collection of binding elements that represents the communication stack associated with a service address.</span></span> <span data-ttu-id="6ca3b-209">Yığındaki her öğe bir [ \<bağlama >](../../../../docs/framework/misc/binding.md) öğesi tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-209">Each element in the stack is represented by a [\<binding>](../../../../docs/framework/misc/binding.md) element.</span></span>  
  
 <span data-ttu-id="6ca3b-210">Örnekte, bağlama öğesi `UdpTransportBindingElement`öğesinden <xref:System.ServiceModel.Channels.TransportBindingElement>türetilir.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-210">In the sample, the binding element is `UdpTransportBindingElement`, which derives from <xref:System.ServiceModel.Channels.TransportBindingElement>.</span></span> <span data-ttu-id="6ca3b-211">Bağlamamız ile ilişkili fabrikaları oluşturmak için aşağıdaki yöntemleri geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-211">It overrides the following methods to build the factories associated with our binding.</span></span>  
  
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
  
 <span data-ttu-id="6ca3b-212">Ayrıca, `BindingElement` klonımızın (SOAP. UDP) kopyalanması ve döndürülmesi için Üyeler de bulunur.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-212">It also contains members for cloning the `BindingElement` and returning our scheme (soap.udp).</span></span>  
  
## <a name="adding-metadata-support-for-a-transport-binding-element"></a><span data-ttu-id="6ca3b-213">Bir taşıma bağlama öğesi için meta veri desteği ekleme</span><span class="sxs-lookup"><span data-stu-id="6ca3b-213">Adding Metadata Support for a Transport Binding Element</span></span>  
 <span data-ttu-id="6ca3b-214">Aktarımımızı meta veri sistemine tümleştirmek için, hem ilkenin içeri ve dışarı aktarılmasını desteklememiz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-214">To integrate our transport into the metadata system, we must support both the import and export of policy.</span></span> <span data-ttu-id="6ca3b-215">Bu, [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)aracılığıyla bağlamamız için istemci oluşturmamızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-215">This allows us to generate clients of our binding through the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
### <a name="adding-wsdl-support"></a><span data-ttu-id="6ca3b-216">WSDL desteği ekleme</span><span class="sxs-lookup"><span data-stu-id="6ca3b-216">Adding WSDL Support</span></span>  
 <span data-ttu-id="6ca3b-217">Bir bağlamadaki aktarım bağlama öğesi, meta verilerde adres bilgilerinin dışarı ve içeri aktarılmasından sorumludur.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-217">The transport binding element in a binding is responsible for exporting and importing addressing information in metadata.</span></span> <span data-ttu-id="6ca3b-218">SOAP bağlama kullanılırken, aktarım bağlama öğesi meta verilerde doğru bir taşıma URI 'sini de dışarı aktarmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-218">When using a SOAP binding, the transport binding element should also export a correct transport URI in metadata.</span></span>  
  
#### <a name="wsdl-export"></a><span data-ttu-id="6ca3b-219">WSDL dışarı aktarma</span><span class="sxs-lookup"><span data-stu-id="6ca3b-219">WSDL Export</span></span>  
 <span data-ttu-id="6ca3b-220">Adres bilgilerini `UdpTransportBindingElement` dışarı aktarmak için `IWsdlExportExtension` arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-220">To export addressing information the `UdpTransportBindingElement` implements the `IWsdlExportExtension` interface.</span></span> <span data-ttu-id="6ca3b-221">`ExportEndpoint` Yöntemi, wsdl bağlantı noktasına doğru adres bilgilerini ekler.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-221">The `ExportEndpoint` method adds the correct addressing information to the WSDL port.</span></span>  
  
```csharp
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 <span data-ttu-id="6ca3b-222">Ayrıca, bu, `ExportEndpoint` uç nokta bir soap bağlama kullandığında, yönteminin uygulanmasıbiraktarımURI'sinidışaaktarır.`UdpTransportBindingElement`</span><span class="sxs-lookup"><span data-stu-id="6ca3b-222">The `UdpTransportBindingElement` implementation of the `ExportEndpoint` method also exports a transport URI when the endpoint uses a SOAP binding.</span></span>  
  
```csharp
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a><span data-ttu-id="6ca3b-223">WSDL Içeri aktarma</span><span class="sxs-lookup"><span data-stu-id="6ca3b-223">WSDL Import</span></span>  
 <span data-ttu-id="6ca3b-224">WSDL içeri aktarma sistemini, adresleri içeri aktarmayı işleyecek şekilde genişletmek için, Svcutil. exe. config dosyasında gösterildiği gibi Svcutil. exe için yapılandırma dosyasına aşağıdaki yapılandırmayı eklememiz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-224">To extend the WSDL import system to handle importing the addresses, we must add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file.</span></span>  
  
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
  
 <span data-ttu-id="6ca3b-225">Svcutil. exe dosyasını çalıştırırken, Svcutil. exe ' nin WSDL içeri aktarma uzantılarını yüklemesi için iki seçenek vardır:</span><span class="sxs-lookup"><span data-stu-id="6ca3b-225">When running Svcutil.exe, there are two options for getting Svcutil.exe to load the WSDL import extensions:</span></span>  
  
1. <span data-ttu-id="6ca3b-226">/SvcutilConfig:\<File > kullanarak Svcutil. exe ' yi yapılandırma dosyanıza yazın.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-226">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2. <span data-ttu-id="6ca3b-227">Svcutil. exe. config dosyasına, Svcutil. exe ile aynı dizinde yapılandırma bölümünü ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-227">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
 <span data-ttu-id="6ca3b-228">`UdpBindingElementImporter` Türü ,`IWsdlImportExtension` arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-228">The `UdpBindingElementImporter` type implements the `IWsdlImportExtension` interface.</span></span> <span data-ttu-id="6ca3b-229">`ImportEndpoint` Yöntemi wsdl bağlantı noktasından adresi içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-229">The `ImportEndpoint` method imports the address from the WSDL port.</span></span>  
  
```csharp
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a><span data-ttu-id="6ca3b-230">Ilke desteği ekleme</span><span class="sxs-lookup"><span data-stu-id="6ca3b-230">Adding Policy Support</span></span>  
 <span data-ttu-id="6ca3b-231">Özel bağlama öğesi, söz konusu bağlama öğesinin yeteneklerini ifade etmek için bir hizmet uç noktası için WSDL bağlamasındaki ilke onaylamalarını dışarı aktarabilir.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-231">The custom binding element can export policy assertions in the WSDL binding for a service endpoint to express the capabilities of that binding element.</span></span>  
  
#### <a name="policy-export"></a><span data-ttu-id="6ca3b-232">İlke dışarı aktarma</span><span class="sxs-lookup"><span data-stu-id="6ca3b-232">Policy Export</span></span>  
 <span data-ttu-id="6ca3b-233">Türü `UdpTransportBindingElement` , ilke `IPolicyExportExtension` dışarı aktarma desteği eklemek için uygular.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-233">The `UdpTransportBindingElement` type implements `IPolicyExportExtension` to add support for exporting policy.</span></span> <span data-ttu-id="6ca3b-234">Sonuç olarak, `System.ServiceModel.MetadataExporter` onu içeren `UdpTransportBindingElement` herhangi bir bağlama için ilke oluşturmaya dahildir.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-234">As a result, `System.ServiceModel.MetadataExporter` includes `UdpTransportBindingElement` in the generation of policy for any binding that includes it.</span></span>  
  
 <span data-ttu-id="6ca3b-235">İçinde `IPolicyExportExtension.ExportPolicy`, çok noktaya yayın modundayken UDP ve başka bir onaylama için bir onaylama ekleyeceğiz.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-235">In `IPolicyExportExtension.ExportPolicy`, we add an assertion for UDP and another assertion if we are in multicast mode.</span></span> <span data-ttu-id="6ca3b-236">Bunun nedeni, çok noktaya yayın modunun iletişim yığınının oluşturulmasını etkilemesi ve bu nedenle her iki taraf arasında koordine olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-236">This is because multicast mode affects how the communication stack is constructed, and thus must be coordinated between both sides.</span></span>  
  
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
  
 <span data-ttu-id="6ca3b-237">Özel aktarım bağlama öğeleri, adresleme `IPolicyExportExtension` 'yi işlemekten sorumlu olduğundan, ' `UdpTransportBindingElement` deki uygulamanın, ws-Addressing sürümünü göstermek için uygun ws-Addressing ilke onayları vermeyi de işlemesi gerekir kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-237">Because custom transport binding elements are responsible for handling addressing, the `IPolicyExportExtension` implementation on the `UdpTransportBindingElement` must also handle exporting the appropriate WS-Addressing policy assertions to indicate the version of WS-Addressing being used.</span></span>  
  
```csharp
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a><span data-ttu-id="6ca3b-238">İlke Içeri aktarma</span><span class="sxs-lookup"><span data-stu-id="6ca3b-238">Policy Import</span></span>  
 <span data-ttu-id="6ca3b-239">Ilke Içeri aktarma sistemini genişletmek için, Svcutil. exe. config dosyasında gösterildiği gibi Svcutil. exe için yapılandırma dosyasına aşağıdaki yapılandırmayı eklememiz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-239">To extend the Policy Import system, we must add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file.</span></span>  
  
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
  
 <span data-ttu-id="6ca3b-240">Ardından, kayıtlı `IPolicyImporterExtension` sınıfımızdan (`UdpBindingElementImporter`) uyguladık.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-240">Then we implement `IPolicyImporterExtension` from our registered class (`UdpBindingElementImporter`).</span></span> <span data-ttu-id="6ca3b-241">' `ImportPolicy()`De, ad boşluğumuzdaki onaylamaları inceleyerek, nakliyenizi oluşturmak ve çok noktaya yayın olup olmadığını denetlemek için bunları işletireceğiz.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-241">In `ImportPolicy()`, we look through the assertions in our namespace, and process the ones for generating the transport and check whether it is multicast.</span></span> <span data-ttu-id="6ca3b-242">Ayrıca, idare ettiğimiz onayları, bağlama onayları listesinden kaldırdık.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-242">We also must remove the assertions we handle from the list of binding assertions.</span></span> <span data-ttu-id="6ca3b-243">Yine, Svcutil. exe dosyasını çalıştırırken, tümleştirme için iki seçenek vardır:</span><span class="sxs-lookup"><span data-stu-id="6ca3b-243">Again, when running Svcutil.exe, there are two options for integration:</span></span>  
  
1. <span data-ttu-id="6ca3b-244">/SvcutilConfig:\<File > kullanarak Svcutil. exe ' yi yapılandırma dosyanıza yazın.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-244">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2. <span data-ttu-id="6ca3b-245">Svcutil. exe. config dosyasına, Svcutil. exe ile aynı dizinde yapılandırma bölümünü ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-245">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
<a name="AddingAStandardBinding"></a>   
## <a name="adding-a-standard-binding"></a><span data-ttu-id="6ca3b-246">Standart bağlama ekleme</span><span class="sxs-lookup"><span data-stu-id="6ca3b-246">Adding a Standard Binding</span></span>  
 <span data-ttu-id="6ca3b-247">Binding öðemiz aşağıdaki iki şekilde kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="6ca3b-247">Our binding element can be used in the following two ways:</span></span>  
  
- <span data-ttu-id="6ca3b-248">Özel bağlama aracılığıyla: Özel bağlama, kullanıcının rastgele bağlama öğeleri kümesini temel alarak kendi bağlamasını oluşturmalarına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-248">Through a custom binding: A custom binding allows the user to create their own binding based on an arbitrary set of binding elements.</span></span>  
  
- <span data-ttu-id="6ca3b-249">Bağlama öğesini içeren sistem tarafından sağlanmış bir bağlama kullanarak.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-249">By using a system-provided binding that includes our binding element.</span></span> <span data-ttu-id="6ca3b-250">WCF,, ve `BasicHttpBinding` `WsHttpBinding`gibi bu sistem tarafından tanımlanan bağlamaları `NetTcpBinding`sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-250">WCF provides a number of these system-defined bindings, such as `BasicHttpBinding`, `NetTcpBinding`, and `WsHttpBinding`.</span></span> <span data-ttu-id="6ca3b-251">Bu bağlamaların her biri iyi tanımlanmış bir profille ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-251">Each of these bindings is associated with a well-defined profile.</span></span>  
  
 <span data-ttu-id="6ca3b-252">Örnek, ' de `SampleProfileUdpBinding`' den <xref:System.ServiceModel.Channels.Binding>türetilen profil bağlamasını uygular.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-252">The sample implements profile binding in `SampleProfileUdpBinding`, which derives from <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="6ca3b-253">, `SampleProfileUdpBinding` İçinde en fazla dört bağlama öğesi içerir: `UdpTransportBindingElement`, `TextMessageEncodingBindingElement CompositeDuplexBindingElement`ve `ReliableSessionBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-253">The `SampleProfileUdpBinding` contains up to four binding elements within it: `UdpTransportBindingElement`, `TextMessageEncodingBindingElement CompositeDuplexBindingElement`, and `ReliableSessionBindingElement`.</span></span>  
  
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
  
### <a name="adding-a-custom-standard-binding-importer"></a><span data-ttu-id="6ca3b-254">Özel standart bağlama Içeri aktarıcı ekleme</span><span class="sxs-lookup"><span data-stu-id="6ca3b-254">Adding a Custom Standard Binding Importer</span></span>  
 <span data-ttu-id="6ca3b-255">Svcutil. exe ve `WsdlImporter` türü varsayılan olarak sistem tarafından tanımlanan bağlamaları tanır ve içeri aktarır.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-255">Svcutil.exe and the `WsdlImporter` type, by default, recognizes and imports system-defined bindings.</span></span> <span data-ttu-id="6ca3b-256">Aksi takdirde, bağlama bir `CustomBinding` örnek olarak içeri aktarılır.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-256">Otherwise, the binding gets imported as a `CustomBinding` instance.</span></span> <span data-ttu-id="6ca3b-257">Svcutil. exe ' yi etkinleştirmek ve `WsdlImporter` `SampleProfileUdpBinding` içeri aktarmak `UdpBindingElementImporter` için özel bir standart bağlama İçeri Aktarıcı işlevi de çalışır.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-257">To enable Svcutil.exe and the `WsdlImporter` to import the `SampleProfileUdpBinding` the `UdpBindingElementImporter` also acts as a custom standard binding importer.</span></span>  
  
 <span data-ttu-id="6ca3b-258">Özel standart bağlama İçeri Aktarıcı, belirli `ImportEndpoint` bir standart bağlama `IWsdlImportExtension` tarafından oluşturulup oluşturulmayacağını görmek `CustomBinding` için meta verilerden içeri aktarılan örneği incelemek üzere arabirimindeki yöntemi uygular.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-258">A custom standard binding importer implements the `ImportEndpoint` method on the `IWsdlImportExtension` interface to examine the `CustomBinding` instance imported from metadata to see whether it could have been generated by a specific standard binding.</span></span>  
  
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
  
 <span data-ttu-id="6ca3b-259">Genellikle, özel bir standart bağlama alma programı uygulamak, yalnızca standart bağlama tarafından ayarlanmış olabilecek özelliklerin değiştiğini ve diğer tüm özelliklerin varsayılan olduğunu doğrulamak için içeri aktarılan bağlama öğelerinin özelliklerinin denetlenmesini içerir.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-259">Generally, implementing a custom standard binding importer involves checking the properties of the imported binding elements to verify that only properties that could have been set by the standard binding have changed and all other properties are their defaults.</span></span> <span data-ttu-id="6ca3b-260">Standart bağlama alma işlemi uygulamaya yönelik temel bir strateji, standart bağlamanın bir örneğini oluşturmaktır, bağlama öğelerinden özellikleri standart bağlamanın desteklediği standart bağlama örneğine yayar ve bağlamayı karşılaştırın İçeri aktarılan bağlama öğeleriyle standart bağlamalardan öğeler.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-260">A basic strategy for implementing a standard binding importer is to create an instance of the standard binding, propagate the properties from the binding elements to the standard binding instance that the standard binding supports, and the compare the binding elements from the standard binding with the imported binding elements.</span></span>  
  
<a name="AddingConfigurationSupport"></a>   
## <a name="adding-configuration-support"></a><span data-ttu-id="6ca3b-261">Yapılandırma desteği ekleme</span><span class="sxs-lookup"><span data-stu-id="6ca3b-261">Adding Configuration Support</span></span>  
 <span data-ttu-id="6ca3b-262">Aktarımımızı yapılandırma yoluyla göstermek için iki yapılandırma bölümü uygulamamız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-262">To expose our transport through configuration, we must implement two configuration sections.</span></span> <span data-ttu-id="6ca3b-263">Birincisi için `BindingElementExtensionElement` `UdpTransportBindingElement`bir.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-263">The first is a `BindingElementExtensionElement` for `UdpTransportBindingElement`.</span></span> <span data-ttu-id="6ca3b-264">Bu, `CustomBinding` uygulamaların bağlama öğesine başvurabilmesi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-264">This is so that `CustomBinding` implementations can reference our binding element.</span></span> <span data-ttu-id="6ca3b-265">İkincisi, bizim `SampleProfileUdpBinding`için `Configuration` bir ' dir.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-265">The second is a `Configuration` for our `SampleProfileUdpBinding`.</span></span>  
  
### <a name="binding-element-extension-element"></a><span data-ttu-id="6ca3b-266">Bağlama öğesi uzantı öğesi</span><span class="sxs-lookup"><span data-stu-id="6ca3b-266">Binding Element Extension Element</span></span>  
 <span data-ttu-id="6ca3b-267">Bu `UdpTransportElement` bölüm,`BindingElementExtensionElement` yapılandırma sistemine yönelikbir'dır.`UdpTransportBindingElement`</span><span class="sxs-lookup"><span data-stu-id="6ca3b-267">The section `UdpTransportElement` is a `BindingElementExtensionElement` that exposes `UdpTransportBindingElement` to the configuration system.</span></span> <span data-ttu-id="6ca3b-268">Birkaç temel geçersiz kılma sayesinde yapılandırma bölüm adı ' nı, bağlama öðemizin türünü ve bağlama öğesini nasıl oluşturacağınız anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-268">With a few basic overrides, we define our configuration section name, the type of our binding element and how to create our binding element.</span></span> <span data-ttu-id="6ca3b-269">Ardından, aşağıdaki kodda gösterildiği gibi, uzantı bölümümüzü bir yapılandırma dosyasına kaydedebiliriz.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-269">We can then register our extension section in a configuration file as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="6ca3b-270">Uzantıya, taşıma olarak UDP 'yi kullanmak için özel bağlamalardan başvurulabilir.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-270">The extension can be referenced from custom bindings to use UDP as the transport.</span></span>  
  
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
  
### <a name="binding-section"></a><span data-ttu-id="6ca3b-271">Bağlama bölümü</span><span class="sxs-lookup"><span data-stu-id="6ca3b-271">Binding Section</span></span>  
 <span data-ttu-id="6ca3b-272">Bu `SampleProfileUdpBindingCollectionElement` bölüm,`StandardBindingCollectionElement` yapılandırma sistemine yönelikbir'dır.`SampleProfileUdpBinding`</span><span class="sxs-lookup"><span data-stu-id="6ca3b-272">The section `SampleProfileUdpBindingCollectionElement` is a `StandardBindingCollectionElement` that exposes `SampleProfileUdpBinding` to the configuration system.</span></span> <span data-ttu-id="6ca3b-273">Uygulamanın toplu işlemi, `SampleProfileUdpBindingConfigurationElement`' den `StandardBindingElement`türetilen öğesine Temsilcili.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-273">The bulk of the implementation is delegated to the `SampleProfileUdpBindingConfigurationElement`, which derives from `StandardBindingElement`.</span></span> <span data-ttu-id="6ca3b-274">, `SampleProfileUdpBindingConfigurationElement` `ConfigurationElement` Üzerinde `SampleProfileUdpBinding`özelliklerine karşılık gelen özelliklerine ve bağlamadan eşlenecek işlevlere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-274">The `SampleProfileUdpBindingConfigurationElement` has properties that correspond to the properties on `SampleProfileUdpBinding`, and functions to map from the `ConfigurationElement` binding.</span></span> <span data-ttu-id="6ca3b-275">Son olarak, aşağıdaki `OnApplyConfiguration` örnek kodda gösterildiği `SampleProfileUdpBinding`gibi, sitemizdeki yöntemi geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-275">Finally, override the `OnApplyConfiguration` method in our `SampleProfileUdpBinding`, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="6ca3b-276">Bu işleyiciyi yapılandırma sistemine kaydetmek için ilgili yapılandırma dosyasına aşağıdaki bölümü ekleyeceğiz.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-276">To register this handler with the configuration system, we add the following section to the relevant configuration file.</span></span>  
  
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
  
 <span data-ttu-id="6ca3b-277">Daha sonra serviceModel yapılandırma bölümünden başvurulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-277">It can then be referenced from the serviceModel configuration section.</span></span>  
  
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
  
## <a name="the-udp-test-service-and-client"></a><span data-ttu-id="6ca3b-278">UDP test hizmeti ve Istemcisi</span><span class="sxs-lookup"><span data-stu-id="6ca3b-278">The UDP Test Service and Client</span></span>  
 <span data-ttu-id="6ca3b-279">Bu örnek taşımanın kullanılması için test kodu, UdpTestService ve UdpTestClient dizinlerinde bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-279">Test code for using this sample transport is available in the UdpTestService and UdpTestClient directories.</span></span> <span data-ttu-id="6ca3b-280">Hizmet kodu iki testten oluşur; bir test koddan bağlamaları ve uç noktaları ayarlar ve diğeri de yapılandırma yoluyla yapılır.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-280">The service code consists of two tests—one test sets up bindings and endpoints from code and the other does it through configuration.</span></span> <span data-ttu-id="6ca3b-281">Her iki test iki uç nokta kullanır.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-281">Both tests use two endpoints.</span></span> <span data-ttu-id="6ca3b-282">Bir uç nokta, `SampleUdpProfileBinding` ile [ \<ayarlanan](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) `true`reliableoturum > kullanır.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-282">One endpoint uses the `SampleUdpProfileBinding` with [\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) set to `true`.</span></span> <span data-ttu-id="6ca3b-283">Diğer uç nokta ile `UdpTransportBindingElement`özel bir bağlama kullanır.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-283">The other endpoint uses a custom binding with `UdpTransportBindingElement`.</span></span> <span data-ttu-id="6ca3b-284">Bu, `SampleUdpProfileBinding` [ \<reliableoturum >](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) olarak `false`ayarlanan ile birlikte kullanılmasına eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-284">This is equivalent to using `SampleUdpProfileBinding` with [\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) set to `false`.</span></span> <span data-ttu-id="6ca3b-285">Her iki test de bir hizmet oluşturur, her bağlama için bir uç nokta ekler, hizmeti açar ve ardından hizmeti kapatmadan önce kullanıcının ENTER tuşuna basmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-285">Both tests create a service, add an endpoint for each binding, open the service and then wait for the user to hit ENTER before closing the service.</span></span>  
  
 <span data-ttu-id="6ca3b-286">Hizmet testi uygulamasını başlattığınızda, aşağıdaki çıktıyı görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-286">When you start the service test application you should see the following output.</span></span>  
  
```console
Testing Udp From Code.  
Service is started from code...  
Press <ENTER> to terminate the service and start service from config...  
```  
  
 <span data-ttu-id="6ca3b-287">Daha sonra, test istemci uygulamasını yayımlanan uç noktalara karşı çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-287">You can then run the test client application against the published endpoints.</span></span> <span data-ttu-id="6ca3b-288">İstemci test uygulaması her bir uç nokta için bir istemci oluşturur ve her uç noktaya beş ileti gönderir.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-288">The client test application creates a client for each endpoint and sends five messages to each endpoint.</span></span> <span data-ttu-id="6ca3b-289">Aşağıdaki çıktı istemcide bulunur.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-289">The following output is on the client.</span></span>  
  
```console
Testing Udp From Imported Files Generated By SvcUtil.  
0  
3  
6  
9  
12  
Press <ENTER> to complete test.  
```  
  
 <span data-ttu-id="6ca3b-290">Hizmetin tam çıkışı aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-290">The following is the full output on the service.</span></span>  
  
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
  
 <span data-ttu-id="6ca3b-291">İstemci uygulamasını yapılandırma kullanılarak yayınlanan uç noktalara karşı çalıştırmak için, hizmette ENTER tuşuna basın ve ardından test istemcisini yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-291">To run the client application against endpoints published using configuration, hit ENTER on the service and then run the test client again.</span></span> <span data-ttu-id="6ca3b-292">Hizmette aşağıdaki çıktıyı görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-292">You should see the following output on the service.</span></span>  
  
```console
Testing Udp From Config.  
Service is started from config...  
Press <ENTER> to terminate the service and exit...  
```  
  
 <span data-ttu-id="6ca3b-293">İstemciyi yeniden çalıştırmak, önceki sonuçlarla aynı sonucu verir.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-293">Running the client again yields the same as the preceding results.</span></span>  
  
 <span data-ttu-id="6ca3b-294">Svcutil. exe kullanarak istemci kodunu ve yapılandırmayı yeniden oluşturmak için, hizmet uygulamasını başlatın ve ardından örnek kök dizininden aşağıdaki Svcutil. exe dosyasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-294">To regenerate the client code and configuration using Svcutil.exe, start the service application and then run the following Svcutil.exe from the root directory of the sample.</span></span>  
  
```console
svcutil http://localhost:8000/udpsample/ /reference:UdpTransport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
```  
  
 <span data-ttu-id="6ca3b-295">Svcutil. exe `SampleProfileUdpBinding`' nin için bağlama uzantısı yapılandırması oluşturmadığına, bu nedenle el ile eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-295">Note that Svcutil.exe does not generate the binding extension configuration for the `SampleProfileUdpBinding`, so you must add it manually.</span></span>  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6ca3b-296">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="6ca3b-296">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="6ca3b-297">Çözümü derlemek için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-297">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="6ca3b-298">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-298">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
3. <span data-ttu-id="6ca3b-299">Önceki "UDP test hizmeti ve Istemcisi" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-299">Refer to the preceding "The UDP Test Service and Client" section.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="6ca3b-300">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-300">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6ca3b-301">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-301">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="6ca3b-302">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-302">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6ca3b-303">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="6ca3b-303">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\Udp`
