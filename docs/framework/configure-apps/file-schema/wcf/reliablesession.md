---
title: '&lt;reliableSession&gt;'
ms.date: 03/30/2017
ms.assetid: 129b4a59-37f0-4030-b664-03795d257d29
ms.openlocfilehash: 0768cbce237b2d119be719eab1de9da4a551e5ae
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54509811"
---
# <a name="ltreliablesessiongt"></a><span data-ttu-id="c0b92-102">&lt;reliableSession&gt;</span><span class="sxs-lookup"><span data-stu-id="c0b92-102">&lt;reliableSession&gt;</span></span>
<span data-ttu-id="c0b92-103">WS-Reliable Mesajlaşma için ayarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c0b92-103">Defines setting for WS-Reliable Messaging.</span></span> <span data-ttu-id="c0b92-104">Bu öğe için özel bir bağlama eklendiğinde, sonuçta elde edilen kanal tam olarak destekler-bir kez teslim Güvenceleri.</span><span class="sxs-lookup"><span data-stu-id="c0b92-104">When this element is added to a custom binding, the resulting channel can support exactly-once delivery assurances.</span></span>  
  
 <span data-ttu-id="c0b92-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c0b92-105">\<system.serviceModel></span></span>  
<span data-ttu-id="c0b92-106">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="c0b92-106">\<bindings></span></span>  
<span data-ttu-id="c0b92-107">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="c0b92-107">\<customBinding></span></span>  
<span data-ttu-id="c0b92-108">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="c0b92-108">\<binding></span></span>  
<span data-ttu-id="c0b92-109">\<reliableSession ></span><span class="sxs-lookup"><span data-stu-id="c0b92-109">\<reliableSession></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0b92-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c0b92-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c0b92-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c0b92-111">Attributes and Elements</span></span>  
 <span data-ttu-id="c0b92-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c0b92-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c0b92-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c0b92-113">Attributes</span></span>  
  
|<span data-ttu-id="c0b92-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="c0b92-114">Attribute</span></span>|<span data-ttu-id="c0b92-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c0b92-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c0b92-116">AcknowledgementInterval</span><span class="sxs-lookup"><span data-stu-id="c0b92-116">acknowledgementInterval</span></span>|<span data-ttu-id="c0b92-117">A <xref:System.TimeSpan> kanal o noktaya kadar alınan iletileri bir bildirim göndermesini bekleyin geçmeye maksimum zaman aralığını içerir.</span><span class="sxs-lookup"><span data-stu-id="c0b92-117">A <xref:System.TimeSpan> that contains the maximum time interval the channel is going to wait to send an acknowledgment for messages received up to that point.</span></span> <span data-ttu-id="c0b92-118">00:00:0.2 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="c0b92-118">The default is 00:00:0.2.</span></span>|  
|<span data-ttu-id="c0b92-119">FlowControlEnabled</span><span class="sxs-lookup"><span data-stu-id="c0b92-119">flowControlEnabled</span></span>|<span data-ttu-id="c0b92-120">Gelişmiş Akış denetiminin, WS-Reliable Mesajlaşma için akış denetimi Microsoft'a özel uygulanışı etkin olup olmadığını gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="c0b92-120">A Boolean value that indicates whether advanced flow control, a Microsoft-specific implementation of flow control for WS-Reliable messaging, is activated.</span></span> <span data-ttu-id="c0b92-121">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="c0b92-121">The default is `true`.</span></span>|  
|<span data-ttu-id="c0b92-122">InactivityTimeout</span><span class="sxs-lookup"><span data-stu-id="c0b92-122">inactivityTimeout</span></span>|<span data-ttu-id="c0b92-123">A <xref:System.TimeSpan> herhangi bir ileti kanalı hatalı önce göndermemeyi diğer tarafın kanalı göndermemesini en uzun süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="c0b92-123">A <xref:System.TimeSpan> that specifies the maximum duration that the channel is going to allow the other communication party not to send any messages, before faulting the channel.</span></span> <span data-ttu-id="c0b92-124">Varsayılan değer 00:10:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="c0b92-124">The default is 00:10:00.</span></span><br /><br /> <span data-ttu-id="c0b92-125">Bir kanalda etkinlik, bir uygulama ya da altyapı iletileri alma olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="c0b92-125">Activity on a channel is defined as receiving an application or infrastructure messages.</span></span> <span data-ttu-id="c0b92-126">Bu özellik, etkin olmayan bir oturum etkin kalması için en uzun süreyi denetler.</span><span class="sxs-lookup"><span data-stu-id="c0b92-126">This property controls the maximum amount of time to keep an inactive session alive.</span></span> <span data-ttu-id="c0b92-127">Daha uzun süre sahip etkinlik geçerse, oturum altyapısı ve kanal hataları tarafından iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="c0b92-127">If longer time passes with no activity, the session is aborted by the infrastructure and the channel faults.</span></span> <span data-ttu-id="c0b92-128">**Not:**  Uygulamayı düzenli aralıklarla bağlantının etkin kalması için ileti göndermek için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="c0b92-128">**Note:**  It is not necessary for the application to periodically send messages to keep the connection alive.</span></span>|  
|<span data-ttu-id="c0b92-129">MaxPendingChannels</span><span class="sxs-lookup"><span data-stu-id="c0b92-129">maxPendingChannels</span></span>|<span data-ttu-id="c0b92-130">En fazla bekleyebilen kabul edilecek bekleyebileceği kanal sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="c0b92-130">An integer that specifies the maximum number of channels that can wait on the listener to be accepted.</span></span> <span data-ttu-id="c0b92-131">Bu değer 1 için 16384 arasında kapsamlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c0b92-131">This value should be between 1 to 16384 inclusive.</span></span> <span data-ttu-id="c0b92-132">Varsayılan 4'tür.</span><span class="sxs-lookup"><span data-stu-id="c0b92-132">The default is 4.</span></span><br /><br /> <span data-ttu-id="c0b92-133">Kanallar, ne zaman bunlar kabul zamanlanmayı bekleyen aşamasındadır.</span><span class="sxs-lookup"><span data-stu-id="c0b92-133">Channels are pending when they are waiting to be accepted.</span></span> <span data-ttu-id="c0b92-134">Bu sınıra ulaşıldığında, kanal yok oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c0b92-134">Once that limit is reached, no channels are created.</span></span> <span data-ttu-id="c0b92-135">Bunun yerine, bunlar modu bu numara gelecek kadar aşağı (kanal kabul ederek) yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="c0b92-135">Rather, they are put in pending mode until this number goes down (by accepting pending channels).</span></span> <span data-ttu-id="c0b92-136">Bu bir Fabrika içi bir güvenlik sınırıdır.</span><span class="sxs-lookup"><span data-stu-id="c0b92-136">This is a per-factory limit.</span></span><br /><br /> <span data-ttu-id="c0b92-137">Ne zaman eşiğine ulaşıldı ve yeni bir güvenilir oturum oluşturmak bir uzaktan uygulama çalıştığında, istek reddedilir ve bu hataların istenir açma işlemi.</span><span class="sxs-lookup"><span data-stu-id="c0b92-137">When the threshold is reached and a remote application tries to establish a new reliable session, the request is denied and the open operation that prompted this faults.</span></span> <span data-ttu-id="c0b92-138">Bu sınır, giden kanallar bekleyen sayısı için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="c0b92-138">This limit does not apply to the number of pending outgoing channels.</span></span>|  
|<span data-ttu-id="c0b92-139">MaxRetryCount</span><span class="sxs-lookup"><span data-stu-id="c0b92-139">maxRetryCount</span></span>|<span data-ttu-id="c0b92-140">En fazla kaç kez belirten bir tamsayı güvenilir bir kanal için bir bildirim kendi altındaki bir kanalda Send çağırarak almadı bir ileti yeniden dener.</span><span class="sxs-lookup"><span data-stu-id="c0b92-140">An integer that specifies the maximum number of times a reliable channel attempts to retransmit a message it has not received an acknowledgment for, by calling Send on its underlying channel.</span></span><br /><br /> <span data-ttu-id="c0b92-141">Bu değer, sıfırdan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c0b92-141">This value should be greater than zero.</span></span> <span data-ttu-id="c0b92-142">Varsayılan değer 8'dir.</span><span class="sxs-lookup"><span data-stu-id="c0b92-142">The default is 8.</span></span><br /><br /> <span data-ttu-id="c0b92-143">Bu değer, sıfırdan büyük bir tamsayı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c0b92-143">This value should be an integer greater than zero.</span></span> <span data-ttu-id="c0b92-144">Bir bildirim son aktarım sonra kanal hataları alınmazsa.</span><span class="sxs-lookup"><span data-stu-id="c0b92-144">If an acknowledgment is not received after the last retransmission, the channel faults.</span></span><br /><br /> <span data-ttu-id="c0b92-145">Bir ileti, alıcıya teslim alıcı tarafından onaylanmış, aktarılacak olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="c0b92-145">A message is considered to be transferred if its delivery at the recipient has been acknowledged by the recipient.</span></span><br /><br /> <span data-ttu-id="c0b92-146">Bildirim zaman iletilmiş bir ileti için belirli bir süre içinde alınmadı, altyapı, ileti otomatik olarak geçer.</span><span class="sxs-lookup"><span data-stu-id="c0b92-146">If an acknowledgment has not been received within a certain amount of time for a message that has been transmitted, the infrastructure automatically retransmits the message.</span></span> <span data-ttu-id="c0b92-147">Altyapı, en fazla kaç kez bu özelliği tarafından belirtilen ileti yeniden dener.</span><span class="sxs-lookup"><span data-stu-id="c0b92-147">The infrastructure tries to resend the message for at most the number of times specified by this property.</span></span> <span data-ttu-id="c0b92-148">Bir bildirim son aktarım sonra kanal hataları alınmazsa.</span><span class="sxs-lookup"><span data-stu-id="c0b92-148">If an acknowledgment is not received after the last retransmission, the channel faults.</span></span><br /><br /> <span data-ttu-id="c0b92-149">Altyapı üzerinde hesaplanan ortalama gidiş dönüş süresi almadığı ne zaman belirlemek için bir üstel geri alma algoritması kullanır.</span><span class="sxs-lookup"><span data-stu-id="c0b92-149">The infrastructure uses an exponential back-off algorithm to determine when to retransmit, based on a computed average round-trip time.</span></span> <span data-ttu-id="c0b92-150">Süresi 1 saniye aktarım ve yaklaşık 8,5 ilk iletim girişimi ve son aktarım denemesini arasında geçen dakika cinsinden sonuçları her girişimi gecikmeyle Katlama önce başlangıçta başlar.</span><span class="sxs-lookup"><span data-stu-id="c0b92-150">The time initially starts at 1 second before retransmission and doubling the delay with every attempt, which results in approximately 8.5 minutes passing between the first transmission attempt and the last retransmission attempt.</span></span> <span data-ttu-id="c0b92-151">İlk aktarım deneme süresi göre hesaplanan gidiş dönüş süresini ayarlanır ve bu girişimler geçirmesine süre elde edilen esnetme buna göre değişir.</span><span class="sxs-lookup"><span data-stu-id="c0b92-151">The time for the first retransmission attempt is adjusted according to the calculated round-trip time and the resulting stretch of time that those attempts take varies accordingly.</span></span> <span data-ttu-id="c0b92-152">Bu aktarım süresini çeşitli ağ koşulları için dinamik olarak uyum sağlar.</span><span class="sxs-lookup"><span data-stu-id="c0b92-152">This allows the retransmission time to dynamically adapt to varying network conditions.</span></span>|  
|<span data-ttu-id="c0b92-153">maxTransferWindowSize</span><span class="sxs-lookup"><span data-stu-id="c0b92-153">maxTransferWindowSize</span></span>|<span data-ttu-id="c0b92-154">En büyük arabellek boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="c0b92-154">An integer that specifies the maximum size of the buffer.</span></span> <span data-ttu-id="c0b92-155">Geçerli değerler 1 ile 4096 kapsamlı olmalı.</span><span class="sxs-lookup"><span data-stu-id="c0b92-155">Valid values are from 1 to 4096 inclusive.</span></span><br /><br /> <span data-ttu-id="c0b92-156">Bu öznitelik, istemcide henüz bir alıcı tarafından onaylanır iletileri tutmak için güvenilir bir kanal tarafından kullanılan arabelleğin en büyük boyutunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c0b92-156">On the client, this attribute defines the maximum size of the buffer used by a reliable channel to hold messages not yet acknowledged by the receiver.</span></span> <span data-ttu-id="c0b92-157">Bir ileti kotası birimidir.</span><span class="sxs-lookup"><span data-stu-id="c0b92-157">The unit of the quota is a message.</span></span> <span data-ttu-id="c0b92-158">Arabelleği dolu ise, daha fazla gönderme işlemleri engellenir.</span><span class="sxs-lookup"><span data-stu-id="c0b92-158">If the buffer is full, further SEND operations are blocked.</span></span><br /><br /> <span data-ttu-id="c0b92-159">Bu öznitelik, bir alıcı ile kanal tarafından henüz uygulamaya gönderilen gelen iletileri depolamak için kullanılan arabelleğin en büyük boyutunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c0b92-159">On the receiver, this attribute defines the maximum size of the buffer used by the channel to store incoming messages not yet dispatched to the application.</span></span> <span data-ttu-id="c0b92-160">Arabelleği dolu ise, daha ayrıntılı iletiler sessizce alıcı tarafından bırakılır ve istemci tarafından aktarım gerektirir.</span><span class="sxs-lookup"><span data-stu-id="c0b92-160">If the buffer is full, further messages are silently dropped by the receiver and require retransmission by the client.</span></span>|  
|<span data-ttu-id="c0b92-161">ordered</span><span class="sxs-lookup"><span data-stu-id="c0b92-161">ordered</span></span>|<span data-ttu-id="c0b92-162">İletilerin gönderildiği sırada ulşamasını garanti edilip edilmediğini belirten Boolean bir değer.</span><span class="sxs-lookup"><span data-stu-id="c0b92-162">A Boolean that specifies whether messages are guaranteed to arrive in the order they were sent.</span></span> <span data-ttu-id="c0b92-163">Bu ayar `false`, iletileri sıralama dışında gelir.</span><span class="sxs-lookup"><span data-stu-id="c0b92-163">If this setting is `false`, messages can arrive out of order.</span></span> <span data-ttu-id="c0b92-164">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="c0b92-164">The default is `true`.</span></span>|  
|<span data-ttu-id="c0b92-165">ReliableMessagingVersion</span><span class="sxs-lookup"><span data-stu-id="c0b92-165">reliableMessagingVersion</span></span>|<span data-ttu-id="c0b92-166">Geçerli bir değer <xref:System.ServiceModel.ReliableMessagingVersion> kullanılacak WS-ReliableMessaging sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="c0b92-166">A valid value from <xref:System.ServiceModel.ReliableMessagingVersion> that specifies the WS-ReliableMessaging version to be used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c0b92-167">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c0b92-167">Child Elements</span></span>  
 <span data-ttu-id="c0b92-168">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="c0b92-168">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c0b92-169">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c0b92-169">Parent Elements</span></span>  
  
|<span data-ttu-id="c0b92-170">Öğe</span><span class="sxs-lookup"><span data-stu-id="c0b92-170">Element</span></span>|<span data-ttu-id="c0b92-171">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c0b92-171">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c0b92-172">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="c0b92-172">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="c0b92-173">Özel bağlama tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c0b92-173">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c0b92-174">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c0b92-174">Remarks</span></span>  
 <span data-ttu-id="c0b92-175">Güvenilir oturumlar güvenilir Mesajlaşma ve oturumları için özellikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c0b92-175">Reliable sessions provide features for reliable messaging and sessions.</span></span> <span data-ttu-id="c0b92-176">Güvenilir Mesajlaşma iletişimi hatasında yeniden deneme sayısı ve teslim Güvenceleri gibi sırayla varış belirtilmesi iletilerinin sağlar.</span><span class="sxs-lookup"><span data-stu-id="c0b92-176">Reliable messaging retries communication on failure and allows delivery assurances such as in-order arrival of messages to be specified.</span></span> <span data-ttu-id="c0b92-177">Oturumlarının çağrıları arasında istemcilerin zachovat stav relace</span><span class="sxs-lookup"><span data-stu-id="c0b92-177">Sessions maintain state for clients between calls.</span></span> <span data-ttu-id="c0b92-178">Bu öğe Ayrıca isteğe bağlı olarak sıralı mesaj teslimatı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c0b92-178">This element also optionally provides ordered message delivery.</span></span> <span data-ttu-id="c0b92-179">Uygulanan bu oturum, SOAP ve aktarım aracılar çapraz.</span><span class="sxs-lookup"><span data-stu-id="c0b92-179">This implemented session can cross SOAP and transport intermediaries.</span></span>  
  
 <span data-ttu-id="c0b92-180">Her bağlama öğesi gönderirken veya iletileri almak için bir işleme adımını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c0b92-180">Each binding element represents a processing step when sending or receiving messages.</span></span> <span data-ttu-id="c0b92-181">Çalışma zamanında bağlama öğeleri kanal fabrikaları ve ileti göndermek ve almak için gereken gelen ve giden kanal yığınları oluşturmak gerekli olan bir dinleyici oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c0b92-181">At runtime, binding elements create the channel factories and listeners that are necessary to build outgoing and incoming channel stacks required to send and receive messages.</span></span> <span data-ttu-id="c0b92-182">`reliableSession` Uç noktalar arasında güvenilir oturum oluşturmak ve bu oturum davranışını yapılandırma yığınında isteğe bağlı bir katmanı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c0b92-182">The `reliableSession` provides an optional layer in the stack that can establish a reliable session between endpoints and configure the behavior of this session.</span></span>  
  
 <span data-ttu-id="c0b92-183">Daha fazla bilgi için [güvenilir oturumlar](../../../../../docs/framework/wcf/feature-details/reliable-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="c0b92-183">For more information, see [Reliable Sessions](../../../../../docs/framework/wcf/feature-details/reliable-sessions.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0b92-184">Örnek</span><span class="sxs-lookup"><span data-stu-id="c0b92-184">Example</span></span>  
 <span data-ttu-id="c0b92-185">Aşağıdaki örnek, çeşitli taşıma ve istemci durumu korur ve sıralı teslim Güvenceleri belirten öğeleri kodlama, özellikle de güvenilir oturumlar etkinleştirme ileti özel bağlama yapılandırma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c0b92-185">The following example demonstrates how to configure a custom binding with various transport and message encoding elements, especially enabling reliable sessions, which maintains client state and specifies in-order delivery assurances.</span></span> <span data-ttu-id="c0b92-186">Bu özellik, uygulama yapılandırma dosyalarında istemci ve hizmet için yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="c0b92-186">This feature is configured in the application configuration files for the client and service.</span></span> <span data-ttu-id="c0b92-187">Örnek, hizmet yapılandırmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c0b92-187">The example show the service configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c0b92-188">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c0b92-188">See also</span></span>
- <xref:System.ServiceModel.Configuration.ReliableSessionElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>
- [<span data-ttu-id="c0b92-189">Güvenilir Oturumlar</span><span class="sxs-lookup"><span data-stu-id="c0b92-189">Reliable Sessions</span></span>](../../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
- [<span data-ttu-id="c0b92-190">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="c0b92-190">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="c0b92-191">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="c0b92-191">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="c0b92-192">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="c0b92-192">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="c0b92-193">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="c0b92-193">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
