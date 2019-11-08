---
title: <reliableSession>
ms.date: 03/30/2017
ms.assetid: 129b4a59-37f0-4030-b664-03795d257d29
ms.openlocfilehash: 95f6646041dc2dd7bae7691a0a9f748c844f50b6
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738753"
---
# <a name="reliablesession"></a><span data-ttu-id="e61e1-101">Reliableoturum > \<</span><span class="sxs-lookup"><span data-stu-id="e61e1-101">\<reliableSession></span></span>
<span data-ttu-id="e61e1-102">WS-güvenilir mesajlaşma için ayarı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e61e1-102">Defines setting for WS-Reliable Messaging.</span></span> <span data-ttu-id="e61e1-103">Bu öğe özel bir bağlamaya eklendiğinde, elde edilen kanal, tam olarak bir kez teslimat hakkı destekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="e61e1-103">When this element is added to a custom binding, the resulting channel can support exactly-once delivery assurances.</span></span>  
  
<span data-ttu-id="e61e1-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="e61e1-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e61e1-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="e61e1-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="e61e1-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="e61e1-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="e61e1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="e61e1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="e61e1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="e61e1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="e61e1-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<reliableSession >**</span><span class="sxs-lookup"><span data-stu-id="e61e1-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<reliableSession>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e61e1-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e61e1-110">Syntax</span></span>  
  
```xml  
<reliableSession acknowledgementInterval="TimeSpan"
                 flowControlEnabled="Boolean"
                 inactivityTimeout="TimeSpan"
                 maxPendingChannels="Integer"
                 maxRetryCount="Integer"
                 maxTransferWindowSize="Integer"
                 reliableMessagingVersion="Default/WSReliableMessagingFebruary2005/WSReliableMessaging11"
                 ordered="Boolean" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e61e1-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e61e1-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e61e1-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e61e1-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e61e1-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e61e1-113">Attributes</span></span>  
  
|<span data-ttu-id="e61e1-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e61e1-114">Attribute</span></span>|<span data-ttu-id="e61e1-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e61e1-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e61e1-116">bildiren Gementınterval</span><span class="sxs-lookup"><span data-stu-id="e61e1-116">acknowledgementInterval</span></span>|<span data-ttu-id="e61e1-117">Kanalın bu noktaya kadar alınan iletiler için bildirim göndermek üzere bekleyeceği maksimum zaman aralığını içeren bir <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="e61e1-117">A <xref:System.TimeSpan> that contains the maximum time interval the channel is going to wait to send an acknowledgment for messages received up to that point.</span></span> <span data-ttu-id="e61e1-118">Varsayılan değer 00:00:0.2 ' dir.</span><span class="sxs-lookup"><span data-stu-id="e61e1-118">The default is 00:00:0.2.</span></span>|  
|<span data-ttu-id="e61e1-119">flowControlEnabled</span><span class="sxs-lookup"><span data-stu-id="e61e1-119">flowControlEnabled</span></span>|<span data-ttu-id="e61e1-120">Gelişmiş akış denetiminin, WS-güvenilir mesajlaşma için Microsoft 'a özgü akış denetimi uygulamasının etkinleştirilip etkinleştirilmediğini belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="e61e1-120">A Boolean value that indicates whether advanced flow control, a Microsoft-specific implementation of flow control for WS-Reliable messaging, is activated.</span></span> <span data-ttu-id="e61e1-121">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="e61e1-121">The default is `true`.</span></span>|  
|<span data-ttu-id="e61e1-122">InactivityTimeout</span><span class="sxs-lookup"><span data-stu-id="e61e1-122">inactivityTimeout</span></span>|<span data-ttu-id="e61e1-123">Kanalın, diğer iletişim tarafına, kanalı hatalı olmadan önce hiçbir ileti gönderemediğinden izin veren en uzun süreyi belirten <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="e61e1-123">A <xref:System.TimeSpan> that specifies the maximum duration that the channel is going to allow the other communication party not to send any messages, before faulting the channel.</span></span> <span data-ttu-id="e61e1-124">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="e61e1-124">The default is 00:10:00.</span></span><br /><br /> <span data-ttu-id="e61e1-125">Bir kanaldaki etkinlik, uygulama veya altyapı iletileri alma olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="e61e1-125">Activity on a channel is defined as receiving an application or infrastructure messages.</span></span> <span data-ttu-id="e61e1-126">Bu özellik, etkin olmayan bir oturumun etkin tutulması için en uzun süreyi denetler.</span><span class="sxs-lookup"><span data-stu-id="e61e1-126">This property controls the maximum amount of time to keep an inactive session alive.</span></span> <span data-ttu-id="e61e1-127">Daha uzun süre hiçbir etkinlik olmadan geçerse, oturum altyapı ve kanal hataları tarafından iptal edilir.</span><span class="sxs-lookup"><span data-stu-id="e61e1-127">If longer time passes with no activity, the session is aborted by the infrastructure and the channel faults.</span></span> <span data-ttu-id="e61e1-128">**Note:**  Uygulamanın bağlantıyı canlı tutmak için düzenli olarak ileti gönderebilmesi gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="e61e1-128">**Note:**  It is not necessary for the application to periodically send messages to keep the connection alive.</span></span>|  
|<span data-ttu-id="e61e1-129">maxPendingChannels</span><span class="sxs-lookup"><span data-stu-id="e61e1-129">maxPendingChannels</span></span>|<span data-ttu-id="e61e1-130">Dinleyicide bekleyebilen en fazla kanal sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="e61e1-130">An integer that specifies the maximum number of channels that can wait on the listener to be accepted.</span></span> <span data-ttu-id="e61e1-131">Bu değer 1 ila 16384 arasında olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e61e1-131">This value should be between 1 to 16384 inclusive.</span></span> <span data-ttu-id="e61e1-132">Varsayılan değer 4 ' dir.</span><span class="sxs-lookup"><span data-stu-id="e61e1-132">The default is 4.</span></span><br /><br /> <span data-ttu-id="e61e1-133">Kanallar kabul edilmeden önce bekliyor.</span><span class="sxs-lookup"><span data-stu-id="e61e1-133">Channels are pending when they are waiting to be accepted.</span></span> <span data-ttu-id="e61e1-134">Bu sınıra ulaşıldığında, hiçbir kanal oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="e61e1-134">Once that limit is reached, no channels are created.</span></span> <span data-ttu-id="e61e1-135">Bunun yerine, bu sayı kapatılıncaya kadar (bekleyen kanalları kabul ederek) bekleyen moda konur.</span><span class="sxs-lookup"><span data-stu-id="e61e1-135">Rather, they are put in pending mode until this number goes down (by accepting pending channels).</span></span> <span data-ttu-id="e61e1-136">Bu, fabrika başına bir limit.</span><span class="sxs-lookup"><span data-stu-id="e61e1-136">This is a per-factory limit.</span></span><br /><br /> <span data-ttu-id="e61e1-137">Eşiğe ulaşıldığında ve bir uzak uygulama yeni bir güvenilir oturum kurmaya çalıştığında, istek reddedilir ve bu hataları isteyen açma işlemi yapılır.</span><span class="sxs-lookup"><span data-stu-id="e61e1-137">When the threshold is reached and a remote application tries to establish a new reliable session, the request is denied and the open operation that prompted this faults.</span></span> <span data-ttu-id="e61e1-138">Bu sınır, bekleyen giden kanalların sayısı için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="e61e1-138">This limit does not apply to the number of pending outgoing channels.</span></span>|  
|<span data-ttu-id="e61e1-139">maxRetryCount</span><span class="sxs-lookup"><span data-stu-id="e61e1-139">maxRetryCount</span></span>|<span data-ttu-id="e61e1-140">Güvenilir bir kanalın, temel aldığı kanalda Gönder ' i çağırarak bildirim almamış bir iletiyi yeniden göndermek için yaptığı deneme sayısının üst sınırını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="e61e1-140">An integer that specifies the maximum number of times a reliable channel attempts to retransmit a message it has not received an acknowledgment for, by calling Send on its underlying channel.</span></span><br /><br /> <span data-ttu-id="e61e1-141">Bu değer sıfırdan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e61e1-141">This value should be greater than zero.</span></span> <span data-ttu-id="e61e1-142">Varsayılan değer 8 ' dir.</span><span class="sxs-lookup"><span data-stu-id="e61e1-142">The default is 8.</span></span><br /><br /> <span data-ttu-id="e61e1-143">Bu değer sıfırdan büyük bir tamsayı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e61e1-143">This value should be an integer greater than zero.</span></span> <span data-ttu-id="e61e1-144">Son yeniden iletim sonrasında bir bildirim alınmıyorsa, kanal hataları.</span><span class="sxs-lookup"><span data-stu-id="e61e1-144">If an acknowledgment is not received after the last retransmission, the channel faults.</span></span><br /><br /> <span data-ttu-id="e61e1-145">Alıcı tarafından alıcının teslimatı onaylanmışsa bir ileti aktarıldıkları kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="e61e1-145">A message is considered to be transferred if its delivery at the recipient has been acknowledged by the recipient.</span></span><br /><br /> <span data-ttu-id="e61e1-146">Bir bildirim, iletilen bir ileti için belirli bir süre içinde alınmadığında, altyapı iletiyi otomatik olarak yeniden iletir.</span><span class="sxs-lookup"><span data-stu-id="e61e1-146">If an acknowledgment has not been received within a certain amount of time for a message that has been transmitted, the infrastructure automatically retransmits the message.</span></span> <span data-ttu-id="e61e1-147">Altyapı, bu özellik tarafından belirtilen en fazla kaç kez iletiyi yeniden göndermeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="e61e1-147">The infrastructure tries to resend the message for at most the number of times specified by this property.</span></span> <span data-ttu-id="e61e1-148">Son yeniden iletim sonrasında bir bildirim alınmıyorsa, kanal hataları.</span><span class="sxs-lookup"><span data-stu-id="e61e1-148">If an acknowledgment is not received after the last retransmission, the channel faults.</span></span><br /><br /> <span data-ttu-id="e61e1-149">Altyapı, hesaplanan ortalama gidiş dönüş zamanına bağlı olarak ne zaman yeniden aktarım için bir üstel geri dönüş algoritması kullanır.</span><span class="sxs-lookup"><span data-stu-id="e61e1-149">The infrastructure uses an exponential back-off algorithm to determine when to retransmit, based on a computed average round-trip time.</span></span> <span data-ttu-id="e61e1-150">İlk iletim denemesi ve son yeniden iletme girişimi arasında yaklaşık 8,5 dakika boyunca yeniden iletimden önce 1 saniye içinde başlar ve her denemede gecikme süresi ikiye geçer.</span><span class="sxs-lookup"><span data-stu-id="e61e1-150">The time initially starts at 1 second before retransmission and doubling the delay with every attempt, which results in approximately 8.5 minutes passing between the first transmission attempt and the last retransmission attempt.</span></span> <span data-ttu-id="e61e1-151">İlk yeniden iletim denemesinin saati, hesaplanan gidiş dönüş zamanına ve bu girişimlere göre farklılık gösteren elde edilen süre uzatılmasına göre düzeltilir.</span><span class="sxs-lookup"><span data-stu-id="e61e1-151">The time for the first retransmission attempt is adjusted according to the calculated round-trip time and the resulting stretch of time that those attempts take varies accordingly.</span></span> <span data-ttu-id="e61e1-152">Bu, yeniden aktarım süresinin farklı ağ koşullarına dinamik olarak uyum sağlamasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="e61e1-152">This allows the retransmission time to dynamically adapt to varying network conditions.</span></span>|  
|<span data-ttu-id="e61e1-153">maxTransferWindowSize</span><span class="sxs-lookup"><span data-stu-id="e61e1-153">maxTransferWindowSize</span></span>|<span data-ttu-id="e61e1-154">Arabelleğin en büyük boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="e61e1-154">An integer that specifies the maximum size of the buffer.</span></span> <span data-ttu-id="e61e1-155">Geçerli değerler 1 ile 4096 arasında olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e61e1-155">Valid values are from 1 to 4096 inclusive.</span></span><br /><br /> <span data-ttu-id="e61e1-156">İstemcide, bu öznitelik, alıcı tarafından henüz onaylanmayan iletileri tutmak için güvenilir bir kanal tarafından kullanılan arabelleğin en büyük boyutunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e61e1-156">On the client, this attribute defines the maximum size of the buffer used by a reliable channel to hold messages not yet acknowledged by the receiver.</span></span> <span data-ttu-id="e61e1-157">Kota birimi bir iletidir.</span><span class="sxs-lookup"><span data-stu-id="e61e1-157">The unit of the quota is a message.</span></span> <span data-ttu-id="e61e1-158">Arabellek doluysa, daha fazla gönderme işlemi engellenir.</span><span class="sxs-lookup"><span data-stu-id="e61e1-158">If the buffer is full, further SEND operations are blocked.</span></span><br /><br /> <span data-ttu-id="e61e1-159">Alıcıda, bu öznitelik kanal tarafından henüz uygulamaya dağıtılan gelen iletileri depolamak için kullanılan arabelleğin en büyük boyutunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e61e1-159">On the receiver, this attribute defines the maximum size of the buffer used by the channel to store incoming messages not yet dispatched to the application.</span></span> <span data-ttu-id="e61e1-160">Arabellek doluysa, daha fazla ileti alıcı tarafından sessizce bırakılır ve istemci tarafından yeniden aktarım gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e61e1-160">If the buffer is full, further messages are silently dropped by the receiver and require retransmission by the client.</span></span>|  
|<span data-ttu-id="e61e1-161">ordered</span><span class="sxs-lookup"><span data-stu-id="e61e1-161">ordered</span></span>|<span data-ttu-id="e61e1-162">İletilerin gönderildikleri sırada gelmesi garanti edilip edilmeyeceğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="e61e1-162">A Boolean that specifies whether messages are guaranteed to arrive in the order they were sent.</span></span> <span data-ttu-id="e61e1-163">Bu ayar `false`, iletiler sırayla gelebilir.</span><span class="sxs-lookup"><span data-stu-id="e61e1-163">If this setting is `false`, messages can arrive out of order.</span></span> <span data-ttu-id="e61e1-164">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="e61e1-164">The default is `true`.</span></span>|  
|<span data-ttu-id="e61e1-165">Belirten ReliableMessagingVersion</span><span class="sxs-lookup"><span data-stu-id="e61e1-165">reliableMessagingVersion</span></span>|<span data-ttu-id="e61e1-166">Kullanılacak WS-ReliableMessaging sürümünü belirten <xref:System.ServiceModel.ReliableMessagingVersion> geçerli bir değer.</span><span class="sxs-lookup"><span data-stu-id="e61e1-166">A valid value from <xref:System.ServiceModel.ReliableMessagingVersion> that specifies the WS-ReliableMessaging version to be used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e61e1-167">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e61e1-167">Child Elements</span></span>  
 <span data-ttu-id="e61e1-168">Yok.</span><span class="sxs-lookup"><span data-stu-id="e61e1-168">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e61e1-169">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e61e1-169">Parent Elements</span></span>  
  
|<span data-ttu-id="e61e1-170">Öğe</span><span class="sxs-lookup"><span data-stu-id="e61e1-170">Element</span></span>|<span data-ttu-id="e61e1-171">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e61e1-171">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e61e1-172">\< bağlama ></span><span class="sxs-lookup"><span data-stu-id="e61e1-172">\<binding></span></span>](bindings.md)|<span data-ttu-id="e61e1-173">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e61e1-173">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e61e1-174">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e61e1-174">Remarks</span></span>  
 <span data-ttu-id="e61e1-175">Güvenilir Oturumlar, güvenilir mesajlaşma ve oturumlara yönelik özellikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e61e1-175">Reliable sessions provide features for reliable messaging and sessions.</span></span> <span data-ttu-id="e61e1-176">Güvenilir Mesajlaşma, hata durumunda iletişim kurmayı yeniden dener ve iletilerin belirli bir sırada gönderilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="e61e1-176">Reliable messaging retries communication on failure and allows delivery assurances such as in-order arrival of messages to be specified.</span></span> <span data-ttu-id="e61e1-177">Oturumlar, çağrılar arasındaki istemciler için durumu korur.</span><span class="sxs-lookup"><span data-stu-id="e61e1-177">Sessions maintain state for clients between calls.</span></span> <span data-ttu-id="e61e1-178">Bu öğe Ayrıca isteğe bağlı olarak sıralı ileti teslimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e61e1-178">This element also optionally provides ordered message delivery.</span></span> <span data-ttu-id="e61e1-179">Bu uygulanan oturum, SOAP ve aktarım aracıları arası olabilir.</span><span class="sxs-lookup"><span data-stu-id="e61e1-179">This implemented session can cross SOAP and transport intermediaries.</span></span>  
  
 <span data-ttu-id="e61e1-180">Her bağlama öğesi ileti gönderirken veya alırken bir işleme adımını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e61e1-180">Each binding element represents a processing step when sending or receiving messages.</span></span> <span data-ttu-id="e61e1-181">Çalışma zamanında, bağlama öğeleri, ileti göndermek ve almak için gereken giden ve gelen kanal yığınları oluşturmak için gereken kanal fabrikalarını ve dinleyicileri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e61e1-181">At runtime, binding elements create the channel factories and listeners that are necessary to build outgoing and incoming channel stacks required to send and receive messages.</span></span> <span data-ttu-id="e61e1-182">`reliableSession`, uç noktalar arasında güvenilir bir oturum kurabilen ve bu oturumun davranışını yapılandırasağlayan yığında isteğe bağlı bir katman sağlar.</span><span class="sxs-lookup"><span data-stu-id="e61e1-182">The `reliableSession` provides an optional layer in the stack that can establish a reliable session between endpoints and configure the behavior of this session.</span></span>  
  
 <span data-ttu-id="e61e1-183">Daha fazla bilgi için bkz. [Güvenilir Oturumlar](../../../wcf/feature-details/reliable-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="e61e1-183">For more information, see [Reliable Sessions](../../../wcf/feature-details/reliable-sessions.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e61e1-184">Örnek</span><span class="sxs-lookup"><span data-stu-id="e61e1-184">Example</span></span>  
 <span data-ttu-id="e61e1-185">Aşağıdaki örnek, özel bir bağlamanın çeşitli taşıma ve ileti kodlama öğeleriyle nasıl yapılandırılacağını gösterir, özellikle de istemci durumunu tutan ve sipariş içi teslim bildirimlerini belirten güvenilir oturumları etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="e61e1-185">The following example demonstrates how to configure a custom binding with various transport and message encoding elements, especially enabling reliable sessions, which maintains client state and specifies in-order delivery assurances.</span></span> <span data-ttu-id="e61e1-186">Bu özellik, istemci ve hizmet için uygulama yapılandırma dosyalarında yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="e61e1-186">This feature is configured in the application configuration files for the client and service.</span></span> <span data-ttu-id="e61e1-187">Örnek, hizmet yapılandırmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e61e1-187">The example show the service configuration.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <!-- This endpoint is exposed at the base address provided by host: http://localhost/servicemodelsamples/service.svc -->
        <!-- specify customBinding binding and a binding configuration to use -->
        <endpoint address=""
                  binding="customBinding"
                  bindingConfiguration="Binding1"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- The mex endpoint is exposed at http://localhost/servicemodelsamples/service.svc/mex -->
        <endpoint address="mex"
                  binding="mexHttpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>
    <!-- custom binding configuration - configures HTTP transport, reliable sessions -->
    <bindings>
      <customBinding>
        <binding name="Binding1">
          <reliableSession />
          <security authenticationMode="SecureConversation"
                    requireSecurityContextCancellation="true">
          </security>
          <compositeDuplex />
          <oneWay />
          <textMessageEncoding messageVersion="Soap12WSAddressing10"
                               writeEncoding="utf-8" />
          <httpTransport authenticationScheme="Anonymous"
                         bypassProxyOnLocal="false"
                         hostNameComparisonMode="StrongWildcard"
                         proxyAuthenticationScheme="Anonymous"
                         realm=""
                         useDefaultWebProxy="true" />
        </binding>
      </customBinding>
    </bindings>
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceMetadata httpGetEnabled="True" />
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="e61e1-188">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e61e1-188">See also</span></span>

- <xref:System.ServiceModel.Configuration.ReliableSessionElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>
- [<span data-ttu-id="e61e1-189">Güvenilir Oturumlar</span><span class="sxs-lookup"><span data-stu-id="e61e1-189">Reliable Sessions</span></span>](../../../wcf/feature-details/reliable-sessions.md)
- [<span data-ttu-id="e61e1-190">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="e61e1-190">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e61e1-191">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="e61e1-191">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="e61e1-192">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="e61e1-192">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="e61e1-193">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="e61e1-193">\<customBinding></span></span>](custombinding.md)
