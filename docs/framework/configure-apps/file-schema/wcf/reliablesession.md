---
title: '&lt;reliableSession&gt;'
ms.date: 03/30/2017
ms.assetid: 129b4a59-37f0-4030-b664-03795d257d29
ms.openlocfilehash: 6b8049e2c493a652405a93eed68f05438819aecb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltreliablesessiongt"></a><span data-ttu-id="aa146-102">&lt;reliableSession&gt;</span><span class="sxs-lookup"><span data-stu-id="aa146-102">&lt;reliableSession&gt;</span></span>
<span data-ttu-id="aa146-103">WS güvenilir Mesajlaşma ayarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="aa146-103">Defines setting for WS-Reliable Messaging.</span></span> <span data-ttu-id="aa146-104">Bu öğe için özel bağlama eklendiğinde, sonuçta elde edilen kanal tam olarak destekleyebilir-kere teslim Güvenceleri.</span><span class="sxs-lookup"><span data-stu-id="aa146-104">When this element is added to a custom binding, the resulting channel can support exactly-once delivery assurances.</span></span>  
  
 <span data-ttu-id="aa146-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="aa146-105">\<system.serviceModel></span></span>  
<span data-ttu-id="aa146-106">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="aa146-106">\<bindings></span></span>  
<span data-ttu-id="aa146-107">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="aa146-107">\<customBinding></span></span>  
<span data-ttu-id="aa146-108">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="aa146-108">\<binding></span></span>  
<span data-ttu-id="aa146-109">\<reliableSession ></span><span class="sxs-lookup"><span data-stu-id="aa146-109">\<reliableSession></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa146-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aa146-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aa146-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="aa146-111">Attributes and Elements</span></span>  
 <span data-ttu-id="aa146-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="aa146-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aa146-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="aa146-113">Attributes</span></span>  
  
|<span data-ttu-id="aa146-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="aa146-114">Attribute</span></span>|<span data-ttu-id="aa146-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aa146-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="aa146-116">acknowledgementInterval</span><span class="sxs-lookup"><span data-stu-id="aa146-116">acknowledgementInterval</span></span>|<span data-ttu-id="aa146-117">A <xref:System.TimeSpan> kanal giderek bu noktaya kadar alınan iletileri bir bildirim göndermek için beklenecek en fazla zaman aralığını içerir.</span><span class="sxs-lookup"><span data-stu-id="aa146-117">A <xref:System.TimeSpan> that contains the maximum time interval the channel is going to wait to send an acknowledgment for messages received up to that point.</span></span> <span data-ttu-id="aa146-118">00:00:0.2 varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="aa146-118">The default is 00:00:0.2.</span></span>|  
|<span data-ttu-id="aa146-119">flowControlEnabled</span><span class="sxs-lookup"><span data-stu-id="aa146-119">flowControlEnabled</span></span>|<span data-ttu-id="aa146-120">Gelişmiş Akış denetimi, bir Microsoft özel uygulama WS güvenilir Mesajlaşma için akış denetimi etkin olup olmadığını gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="aa146-120">A Boolean value that indicates whether advanced flow control, a Microsoft-specific implementation of flow control for WS-Reliable messaging, is activated.</span></span> <span data-ttu-id="aa146-121">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="aa146-121">The default is `true`.</span></span>|  
|<span data-ttu-id="aa146-122">InactivityTimeout</span><span class="sxs-lookup"><span data-stu-id="aa146-122">inactivityTimeout</span></span>|<span data-ttu-id="aa146-123">A <xref:System.TimeSpan> herhangi bir iletisi kanalı hatalı önce göndermemeyi diğer iletişim taraf kanal göndermemesini en uzun süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="aa146-123">A <xref:System.TimeSpan> that specifies the maximum duration that the channel is going to allow the other communication party not to send any messages, before faulting the channel.</span></span> <span data-ttu-id="aa146-124">Varsayılan değer 00:10: 00'dır.</span><span class="sxs-lookup"><span data-stu-id="aa146-124">The default is 00:10:00.</span></span><br /><br /> <span data-ttu-id="aa146-125">Etkinlik kanalda bir uygulama veya altyapı iletileri alma olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="aa146-125">Activity on a channel is defined as receiving an application or infrastructure messages.</span></span> <span data-ttu-id="aa146-126">Bu özellik, etkin olmayan oturumunu Canlı için en fazla süreyi denetler.</span><span class="sxs-lookup"><span data-stu-id="aa146-126">This property controls the maximum amount of time to keep an inactive session alive.</span></span> <span data-ttu-id="aa146-127">Uzun süre hiç etkinlik geçerse, oturumun altyapı ve kanal hataları tarafından iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="aa146-127">If longer time passes with no activity, the session is aborted by the infrastructure and the channel faults.</span></span> <span data-ttu-id="aa146-128">**Not:** uygulamayı düzenli aralıklarla bağlantıyı canlı tut iletileri göndermek için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="aa146-128">**Note:**  It is not necessary for the application to periodically send messages to keep the connection alive.</span></span>|  
|<span data-ttu-id="aa146-129">maxPendingChannels</span><span class="sxs-lookup"><span data-stu-id="aa146-129">maxPendingChannels</span></span>|<span data-ttu-id="aa146-130">Kabul edilecek Dinleyicisi'ni bekleyebilirsiniz kanal maksimum sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="aa146-130">An integer that specifies the maximum number of channels that can wait on the listener to be accepted.</span></span> <span data-ttu-id="aa146-131">Bu değer, 1 değerini 16384 arasında (bunlar dahil) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="aa146-131">This value should be between 1 to 16384 inclusive.</span></span> <span data-ttu-id="aa146-132">Varsayılan değer 4'tür.</span><span class="sxs-lookup"><span data-stu-id="aa146-132">The default is 4.</span></span><br /><br /> <span data-ttu-id="aa146-133">Kanallar, ne zaman oldukları kabul edilmesi için bekleyen bekleyen ' dir.</span><span class="sxs-lookup"><span data-stu-id="aa146-133">Channels are pending when they are waiting to be accepted.</span></span> <span data-ttu-id="aa146-134">Bu sınıra ulaşıldığında, hiçbir kanalı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="aa146-134">Once that limit is reached, no channels are created.</span></span> <span data-ttu-id="aa146-135">Bunun yerine, bunlar modu bu numara gider kadar aşağı (kanalları kabul ederek) koyun.</span><span class="sxs-lookup"><span data-stu-id="aa146-135">Rather, they are put in pending mode until this number goes down (by accepting pending channels).</span></span> <span data-ttu-id="aa146-136">Bir Fabrika başına sınır budur.</span><span class="sxs-lookup"><span data-stu-id="aa146-136">This is a per-factory limit.</span></span><br /><br /> <span data-ttu-id="aa146-137">Ne zaman eşiğine ulaşıldı ve yeni bir güvenilir oturumu uzak uygulama çalıştığında, istek reddedilir ve bu hataları istemde açık işlemi.</span><span class="sxs-lookup"><span data-stu-id="aa146-137">When the threshold is reached and a remote application tries to establish a new reliable session, the request is denied and the open operation that prompted this faults.</span></span> <span data-ttu-id="aa146-138">Bu sınır, giden kanallar bekleyen sayısı için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="aa146-138">This limit does not apply to the number of pending outgoing channels.</span></span>|  
|<span data-ttu-id="aa146-139">MaxRetryCount</span><span class="sxs-lookup"><span data-stu-id="aa146-139">maxRetryCount</span></span>|<span data-ttu-id="aa146-140">En fazla kaç kez belirten bir tamsayı güvenilir bir kanal için bir bildirim gönderme temel kanalda çağırarak almadı bir ileti yeniden dener.</span><span class="sxs-lookup"><span data-stu-id="aa146-140">An integer that specifies the maximum number of times a reliable channel attempts to retransmit a message it has not received an acknowledgment for, by calling Send on its underlying channel.</span></span><br /><br /> <span data-ttu-id="aa146-141">Bu değer sıfırdan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="aa146-141">This value should be greater than zero.</span></span> <span data-ttu-id="aa146-142">Varsayılan 8'dir.</span><span class="sxs-lookup"><span data-stu-id="aa146-142">The default is 8.</span></span><br /><br /> <span data-ttu-id="aa146-143">Bu değer sıfırdan büyük bir tamsayı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="aa146-143">This value should be an integer greater than zero.</span></span> <span data-ttu-id="aa146-144">Bir bildirim son aktarım sonra kanal hataları alınmazsa.</span><span class="sxs-lookup"><span data-stu-id="aa146-144">If an acknowledgment is not received after the last retransmission, the channel faults.</span></span><br /><br /> <span data-ttu-id="aa146-145">Bir ileti alıcının kendi teslim alıcı tarafından onaylanan, aktarılacak olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="aa146-145">A message is considered to be transferred if its delivery at the recipient has been acknowledged by the recipient.</span></span><br /><br /> <span data-ttu-id="aa146-146">Bir bildirim süre iletilmiş bir ileti için belirli bir süre içinde alınmadı, altyapı ileti otomatik olarak geçer.</span><span class="sxs-lookup"><span data-stu-id="aa146-146">If an acknowledgment has not been received within a certain amount of time for a message that has been transmitted, the infrastructure automatically retransmits the message.</span></span> <span data-ttu-id="aa146-147">Altyapı, en fazla kaç kez bu özelliği tarafından belirtilen iletiyi yeniden dener.</span><span class="sxs-lookup"><span data-stu-id="aa146-147">The infrastructure tries to resend the message for at most the number of times specified by this property.</span></span> <span data-ttu-id="aa146-148">Bir bildirim son aktarım sonra kanal hataları alınmazsa.</span><span class="sxs-lookup"><span data-stu-id="aa146-148">If an acknowledgment is not received after the last retransmission, the channel faults.</span></span><br /><br /> <span data-ttu-id="aa146-149">Altyapı hesaplanan bir ortalama gidiş dönüş zamanı temel alınarak yeniden ilettiği ne zaman belirlemek için bir üstel geri alma algoritma kullanır.</span><span class="sxs-lookup"><span data-stu-id="aa146-149">The infrastructure uses an exponential back-off algorithm to determine when to retransmit, based on a computed average round-trip time.</span></span> <span data-ttu-id="aa146-150">Saat 1 saniye sırasında aktarım ve yaklaşık 8,5 ilk iletim girişimini ve son aktarım girişimi arasında geçen dakika cinsinden sonuçları her girişimi gecikmeyle Katlama önce başlangıçta başlatır.</span><span class="sxs-lookup"><span data-stu-id="aa146-150">The time initially starts at 1 second before retransmission and doubling the delay with every attempt, which results in approximately 8.5 minutes passing between the first transmission attempt and the last retransmission attempt.</span></span> <span data-ttu-id="aa146-151">İlk aktarım girişimi yararlanma saatine göre hesaplanan gidiş dönüş süresini göre ve bu girişimler ele zaman ortaya çıkan esnetme buna göre değişir.</span><span class="sxs-lookup"><span data-stu-id="aa146-151">The time for the first retransmission attempt is adjusted according to the calculated round-trip time and the resulting stretch of time that those attempts take varies accordingly.</span></span> <span data-ttu-id="aa146-152">Bu aktarım süresi dinamik olarak değişen ağ koşullarını uyum sağlar.</span><span class="sxs-lookup"><span data-stu-id="aa146-152">This allows the retransmission time to dynamically adapt to varying network conditions.</span></span>|  
|<span data-ttu-id="aa146-153">maxTransferWindowSize</span><span class="sxs-lookup"><span data-stu-id="aa146-153">maxTransferWindowSize</span></span>|<span data-ttu-id="aa146-154">En büyük arabellek boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="aa146-154">An integer that specifies the maximum size of the buffer.</span></span> <span data-ttu-id="aa146-155">Geçerli değerler 1'den 4096 (bunlar dahil) arasındadır.</span><span class="sxs-lookup"><span data-stu-id="aa146-155">Valid values are from 1 to 4096 inclusive.</span></span><br /><br /> <span data-ttu-id="aa146-156">İstemcide, bu öznitelik henüz alıcı tarafından kabul edilen ileti tutmak için güvenilir bir kanal tarafından kullanılan arabellek en büyük boyutunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="aa146-156">On the client, this attribute defines the maximum size of the buffer used by a reliable channel to hold messages not yet acknowledged by the receiver.</span></span> <span data-ttu-id="aa146-157">Bir ileti kota birimidir.</span><span class="sxs-lookup"><span data-stu-id="aa146-157">The unit of the quota is a message.</span></span> <span data-ttu-id="aa146-158">Arabellek dolu olduğunda, başka gönderme işlemleri engellenir.</span><span class="sxs-lookup"><span data-stu-id="aa146-158">If the buffer is full, further SEND operations are blocked.</span></span><br /><br /> <span data-ttu-id="aa146-159">Alıcı, bu öznitelik kanal tarafından henüz uygulamaya gönderilen gelen iletileri depolamak için kullanılan arabelleğin en büyük boyutunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="aa146-159">On the receiver, this attribute defines the maximum size of the buffer used by the channel to store incoming messages not yet dispatched to the application.</span></span> <span data-ttu-id="aa146-160">Arabellek dolu ise, daha ayrıntılı iletiler sessizce alıcı tarafından bırakılan ve istemci tarafından yeniden aktarım gerektirir.</span><span class="sxs-lookup"><span data-stu-id="aa146-160">If the buffer is full, further messages are silently dropped by the receiver and require retransmission by the client.</span></span>|  
|<span data-ttu-id="aa146-161">ordered</span><span class="sxs-lookup"><span data-stu-id="aa146-161">ordered</span></span>|<span data-ttu-id="aa146-162">İletileri gönderildikleri sırayla gelmesi garanti edilip edilmeyeceğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="aa146-162">A Boolean that specifies whether messages are guaranteed to arrive in the order they were sent.</span></span> <span data-ttu-id="aa146-163">Bu ayar ise `false`, iletileri sıralama dışında gelir.</span><span class="sxs-lookup"><span data-stu-id="aa146-163">If this setting is `false`, messages can arrive out of order.</span></span> <span data-ttu-id="aa146-164">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="aa146-164">The default is `true`.</span></span>|  
|<span data-ttu-id="aa146-165">reliableMessagingVersion</span><span class="sxs-lookup"><span data-stu-id="aa146-165">reliableMessagingVersion</span></span>|<span data-ttu-id="aa146-166">Geçerli bir değer <xref:System.ServiceModel.ReliableMessagingVersion> kullanılacak WS-ReliableMessaging sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="aa146-166">A valid value from <xref:System.ServiceModel.ReliableMessagingVersion> that specifies the WS-ReliableMessaging version to be used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aa146-167">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="aa146-167">Child Elements</span></span>  
 <span data-ttu-id="aa146-168">Yok.</span><span class="sxs-lookup"><span data-stu-id="aa146-168">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="aa146-169">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="aa146-169">Parent Elements</span></span>  
  
|<span data-ttu-id="aa146-170">Öğe</span><span class="sxs-lookup"><span data-stu-id="aa146-170">Element</span></span>|<span data-ttu-id="aa146-171">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aa146-171">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="aa146-172">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="aa146-172">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="aa146-173">Özel bağlama tüm bağlama özelliklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="aa146-173">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa146-174">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aa146-174">Remarks</span></span>  
 <span data-ttu-id="aa146-175">Güvenilir oturumlar güvenilir Mesajlaşma ve oturumlar için özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="aa146-175">Reliable sessions provide features for reliable messaging and sessions.</span></span> <span data-ttu-id="aa146-176">Güvenilir Mesajlaşma iletişim başarısızlığı yeniden deneme ve teslim Güvenceleri gibi sıralı varış belirtilmesi iletilerinin sağlar.</span><span class="sxs-lookup"><span data-stu-id="aa146-176">Reliable messaging retries communication on failure and allows delivery assurances such as in-order arrival of messages to be specified.</span></span> <span data-ttu-id="aa146-177">Oturum durumu çağrıları arasında istemcileri için korur.</span><span class="sxs-lookup"><span data-stu-id="aa146-177">Sessions maintain state for clients between calls.</span></span> <span data-ttu-id="aa146-178">Bu öğe Ayrıca isteğe bağlı olarak sipariş edilen ileti teslimi sunar.</span><span class="sxs-lookup"><span data-stu-id="aa146-178">This element also optionally provides ordered message delivery.</span></span> <span data-ttu-id="aa146-179">Bu uygulanan oturum SOAP ve aktarım aracılar arası.</span><span class="sxs-lookup"><span data-stu-id="aa146-179">This implemented session can cross SOAP and transport intermediaries.</span></span>  
  
 <span data-ttu-id="aa146-180">Her bağlama öğesi iletileri alırken veya gönderirken bir işleme adımı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="aa146-180">Each binding element represents a processing step when sending or receiving messages.</span></span> <span data-ttu-id="aa146-181">Çalışma zamanında kanal fabrikaları ve ileti gönderme ve alma için gereken gelen ve giden kanal yığınları oluşturmak gerekli olan dinleyicileri bağlama öğeleri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="aa146-181">At runtime, binding elements create the channel factories and listeners that are necessary to build outgoing and incoming channel stacks required to send and receive messages.</span></span> <span data-ttu-id="aa146-182">`reliableSession` Uç noktalar arasında güvenilir oturum oluşturmak ve bu oturum davranışını yapılandırmak yığınında isteğe bağlı bir katmanı sağlar.</span><span class="sxs-lookup"><span data-stu-id="aa146-182">The `reliableSession` provides an optional layer in the stack that can establish a reliable session between endpoints and configure the behavior of this session.</span></span>  
  
 <span data-ttu-id="aa146-183">Daha fazla bilgi için bkz: [güvenilir oturumlar](../../../../../docs/framework/wcf/feature-details/reliable-sessions.md).</span><span class="sxs-lookup"><span data-stu-id="aa146-183">For more information, see [Reliable Sessions](../../../../../docs/framework/wcf/feature-details/reliable-sessions.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa146-184">Örnek</span><span class="sxs-lookup"><span data-stu-id="aa146-184">Example</span></span>  
 <span data-ttu-id="aa146-185">Aşağıdaki örnek özel bağlama çeşitli aktarım ve istemci durumunu korur ve sıralı teslim Güvenceleri belirtir öğeleri kodlama, özellikle güvenilir oturumlar etkinleştirme ileti ile nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="aa146-185">The following example demonstrates how to configure a custom binding with various transport and message encoding elements, especially enabling reliable sessions, which maintains client state and specifies in-order delivery assurances.</span></span> <span data-ttu-id="aa146-186">Bu özellik uygulama yapılandırma dosyaları istemci ve hizmet için yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="aa146-186">This feature is configured in the application configuration files for the client and service.</span></span> <span data-ttu-id="aa146-187">Örnek, hizmet yapılandırmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="aa146-187">The example show the service configuration.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service   
          name="Microsoft.ServiceModel.Samples.CalculatorService"  
          behaviorConfiguration="CalculatorServiceBehavior">  
        <!-- This endpoint is exposed at the base address provided by host: http://localhost/servicemodelsamples/service.svc  -->  
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
          <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8" />  
          <httpTransport authenticationScheme="Anonymous" bypassProxyOnLocal="false"  
                        hostNameComparisonMode="StrongWildcard"   
                        proxyAuthenticationScheme="Anonymous" realm=""   
                        useDefaultWebProxy="true" />  
        </binding>  
      </customBinding>  
    </bindings>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="aa146-188">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="aa146-188">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ReliableSessionElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>  
 [<span data-ttu-id="aa146-189">Güvenilir Oturumlar</span><span class="sxs-lookup"><span data-stu-id="aa146-189">Reliable Sessions</span></span>](../../../../../docs/framework/wcf/feature-details/reliable-sessions.md)  
 [<span data-ttu-id="aa146-190">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="aa146-190">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="aa146-191">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="aa146-191">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="aa146-192">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="aa146-192">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="aa146-193">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="aa146-193">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
