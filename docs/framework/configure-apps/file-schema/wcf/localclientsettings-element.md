---
title: <localClientSettings> öğesi
ms.date: 03/30/2017
ms.assetid: 4680ace5-f4e1-4fcb-b9d8-a4a4af5cd7ae
ms.openlocfilehash: e7331105582a4a48b7edd8cd4f6a691771b0b8ff
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930806"
---
# <a name="localclientsettings-element"></a><span data-ttu-id="d07e3-102">\<localClientSettings > öğesi</span><span class="sxs-lookup"><span data-stu-id="d07e3-102">\<localClientSettings> element</span></span>
<span data-ttu-id="d07e3-103">Bu bağlama için yerel bir istemcinin güvenlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d07e3-103">Specifies the security settings of a local client for this binding.</span></span>  
  
 <span data-ttu-id="d07e3-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d07e3-104">\<system.serviceModel></span></span>  
<span data-ttu-id="d07e3-105">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="d07e3-105">\<bindings></span></span>  
<span data-ttu-id="d07e3-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="d07e3-106">\<customBinding></span></span>  
<span data-ttu-id="d07e3-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="d07e3-107">\<binding></span></span>  
<span data-ttu-id="d07e3-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="d07e3-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d07e3-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d07e3-109">Syntax</span></span>  
  
```xml  
<security>
   <localClientSettings cacheCookies="Boolean"
                        cookieRenewalThresholdPercentage="Integer"
                        detectReplays="Boolean"
                        maxClockSkew="TimeSpan"
                        maxCookieCachingTime="TimeSpan"
                        reconnectTransportOnFailure="Boolean"
                        replayCacheSize="Integer"
                        replayWindow="TimeSpan"
                        sessionKeyRenewalInterval="TimeSpan"
                        sessionKeyRolloverInterval="TimeSpan"
                        timestampValidityDuration="TimeSpan" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d07e3-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d07e3-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d07e3-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d07e3-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d07e3-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d07e3-112">Attributes</span></span>  
  
|<span data-ttu-id="d07e3-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d07e3-113">Attribute</span></span>|<span data-ttu-id="d07e3-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d07e3-114">Description</span></span>|  
|---------------|-----------------|  
|`cacheCookies`|<span data-ttu-id="d07e3-115">Tanımlama bilgisi önbelleğe almanın etkin olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="d07e3-115">A Boolean value that specifies whether cookie caching is enabled.</span></span> <span data-ttu-id="d07e3-116">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="d07e3-116">The default is `false`.</span></span>|  
|`cookieRenewalThresholdPercentage`|<span data-ttu-id="d07e3-117">Yenilenebilir tanımlama bilgilerinin maksimum yüzdesini belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="d07e3-117">An integer that specifies the maximum percentage of cookies that can be renewed.</span></span> <span data-ttu-id="d07e3-118">Bu değer, ikisi de dahil olmak üzere 0 ile 100 arasında olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d07e3-118">This value should be between 0 and 100 inclusively.</span></span> <span data-ttu-id="d07e3-119">Varsayılan değer 90 ' dir.</span><span class="sxs-lookup"><span data-stu-id="d07e3-119">The default is 90.</span></span>|  
|`detectReplays`|<span data-ttu-id="d07e3-120">Kanala karşı yeniden yürütme saldırılarının algılanıp algılanmayacağını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="d07e3-120">A Boolean value that specifies whether replay attacks against the channel are detected and dealt with automatically.</span></span> <span data-ttu-id="d07e3-121">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="d07e3-121">The default is `false`.</span></span>|  
|`maxClockSkew`|<span data-ttu-id="d07e3-122">İki <xref:System.TimeSpan> iletişim kuran tarafın sistem saatleri arasındaki en uzun süre farkını belirten bir.</span><span class="sxs-lookup"><span data-stu-id="d07e3-122">A <xref:System.TimeSpan> that specifies the maximum time difference between the system clocks of the two communicating parties.</span></span> <span data-ttu-id="d07e3-123">Varsayılan değer "00:05:00" dır.</span><span class="sxs-lookup"><span data-stu-id="d07e3-123">The default value is "00:05:00".</span></span><br /><br /> <span data-ttu-id="d07e3-124">Bu değer varsayılan değere ayarlandığında, alıcı gönderme zamanı zaman damgalarına sahip iletileri, daha sonra veya iletinin alındığı zamandan 5 dakikaya kadar kabul eder.</span><span class="sxs-lookup"><span data-stu-id="d07e3-124">When this value is set to the default, the receiver accepts messages with send-time time stamps up to 5 minutes later or earlier than the time the message was received.</span></span> <span data-ttu-id="d07e3-125">Gönderme zamanı testini geçemediği iletiler reddedilir.</span><span class="sxs-lookup"><span data-stu-id="d07e3-125">Messages that do not pass the send-time test are rejected.</span></span> <span data-ttu-id="d07e3-126">Bu ayar, `replayWindow` özniteliğiyle birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d07e3-126">This setting is used in conjunction with the `replayWindow` attribute.</span></span>|  
|`maxCookieCachingTime`|<span data-ttu-id="d07e3-127">En <xref:System.TimeSpan> fazla tanımlama bilgisi ömrünü belirten bir.</span><span class="sxs-lookup"><span data-stu-id="d07e3-127">A <xref:System.TimeSpan> that specifies the maximum lifetime of cookies.</span></span> <span data-ttu-id="d07e3-128">Varsayılan değer "10675199.02:48:05.4775807" ' dir.</span><span class="sxs-lookup"><span data-stu-id="d07e3-128">The default value is "10675199.02:48:05.4775807".</span></span>|  
|`reconnectTransportOnFailure`|<span data-ttu-id="d07e3-129">WS-güvenilir mesajlaşma kullanan bağlantıların, aktarım hatalarından sonra yeniden bağlanmaya çalışıp çalışmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="d07e3-129">A Boolean value that specifies whether connections using WS-Reliable messaging will attempt to reconnect after transport failures.</span></span> <span data-ttu-id="d07e3-130">Varsayılan `true`olarak, sınırsız yeniden bağlanma girişimlerinin denendiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="d07e3-130">The default is `true`, which means that infinite attempts to reconnect are attempted.</span></span> <span data-ttu-id="d07e3-131">Bu zaman aşımı, kanalın yeniden bağlanamayan bir özel durum oluşturmasına neden olan etkinlik dışı zaman aşımı nedeniyle bozulur.</span><span class="sxs-lookup"><span data-stu-id="d07e3-131">The cycle is broken by the inactivity time-out, which causes the channel to throw an exception when it cannot be reconnected.</span></span>|  
|`replayCacheSize`|<span data-ttu-id="d07e3-132">Yeniden yürütme algılaması için kullanılan önbelleğe alınmış nonce sayısını belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="d07e3-132">A positive integer that specifies the number of cached nonces used for replay detection.</span></span> <span data-ttu-id="d07e3-133">Bu sınır aşılırsa, en eski nonce kaldırılır ve yeni ileti için yeni bir nonce oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d07e3-133">If this limit is exceeded, the oldest nonce is removed and a new nonce is created for the new message.</span></span> <span data-ttu-id="d07e3-134">Varsayılan değer 500000 ' dir.</span><span class="sxs-lookup"><span data-stu-id="d07e3-134">The default value is 500000.</span></span>|  
|`replayWindow`|<span data-ttu-id="d07e3-135">Tek <xref:System.TimeSpan> tek ileti nonce öğelerinin geçerli olduğu süreyi belirten bir.</span><span class="sxs-lookup"><span data-stu-id="d07e3-135">A <xref:System.TimeSpan> that specifies the duration in which individual message nonces are valid.</span></span><br /><br /> <span data-ttu-id="d07e3-136">Bu süreden sonra, daha önce gönderilen ile aynı nonce ile gönderilen bir ileti kabul edilmez.</span><span class="sxs-lookup"><span data-stu-id="d07e3-136">After this duration, a message sent with the same nonce as the one sent before will not be accepted.</span></span> <span data-ttu-id="d07e3-137">Bu öznitelik, `maxClockSkew` yeniden yürütme saldırılarını engellemek için özniteliğiyle birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d07e3-137">This attribute is used in conjunction with the `maxClockSkew` attribute to prevent replay attacks.</span></span> <span data-ttu-id="d07e3-138">Bir saldırgan, yeniden yürütme penceresinin süresi dolduktan sonra bir iletiyi yeniden oynamıştır.</span><span class="sxs-lookup"><span data-stu-id="d07e3-138">An attacker could replay a message after its replay window has expired.</span></span> <span data-ttu-id="d07e3-139">Bununla birlikte, bu ileti, gönderme zamanı `maxClockSkew` zaman damgalarına sahip iletileri, daha sonra veya daha önceki bir süre içinde ileti alındığı zamandan reddeden test başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="d07e3-139">This message, however, would fail the `maxClockSkew` test which rejects messages with send-time timestamps up to a specified time later or earlier than the time the message was received.</span></span>|  
|`sessionKeyRenewalInterval`|<span data-ttu-id="d07e3-140">Bu <xref:System.TimeSpan> , başlatanın güvenlik oturumu anahtarını yenileyecek süreyi belirten bir.</span><span class="sxs-lookup"><span data-stu-id="d07e3-140">A <xref:System.TimeSpan> that specifies the duration after which the initiator will renew the key for the security session.</span></span> <span data-ttu-id="d07e3-141">Varsayılan değer "10:00:00" dır.</span><span class="sxs-lookup"><span data-stu-id="d07e3-141">The default is "10:00:00".</span></span>|  
|`sessionKeyRolloverInterval`|<span data-ttu-id="d07e3-142">Bir <xref:System.TimeSpan> anahtar yenilemesi sırasında önceki oturum anahtarının gelen iletilerde geçerli olduğu zaman aralığını belirten bir.</span><span class="sxs-lookup"><span data-stu-id="d07e3-142">A <xref:System.TimeSpan> that specifies the time interval a previous session key is valid on incoming messages during a key renewal.</span></span> <span data-ttu-id="d07e3-143">Varsayılan değer "00:05:00" dır.</span><span class="sxs-lookup"><span data-stu-id="d07e3-143">The default is "00:05:00".</span></span><br /><br /> <span data-ttu-id="d07e3-144">Anahtar yenileme sırasında, istemci ve sunucu her zaman en geçerli kullanılabilir anahtarı kullanarak ileti göndermelidir.</span><span class="sxs-lookup"><span data-stu-id="d07e3-144">During key renewal, the client and server must always send messages using the most current available key.</span></span> <span data-ttu-id="d07e3-145">Her iki taraf da, geçiş süresi sona erene kadar önceki oturum anahtarıyla güvenliği sağlanmış gelen iletileri kabul eder.</span><span class="sxs-lookup"><span data-stu-id="d07e3-145">Both parties will accept incoming messages secured with the previous session key until the rollover time expires.</span></span>|  
|`timestampValidityDuration`|<span data-ttu-id="d07e3-146">Zaman damgasının <xref:System.TimeSpan> geçerli olduğu süreyi belirten pozitif bir değer.</span><span class="sxs-lookup"><span data-stu-id="d07e3-146">A positive <xref:System.TimeSpan> that specifies the duration in which a time stamp is valid.</span></span> <span data-ttu-id="d07e3-147">Varsayılan değer "00:15:00" dır.</span><span class="sxs-lookup"><span data-stu-id="d07e3-147">The default is "00:15:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d07e3-148">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d07e3-148">Child Elements</span></span>  
 <span data-ttu-id="d07e3-149">Yok.</span><span class="sxs-lookup"><span data-stu-id="d07e3-149">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d07e3-150">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d07e3-150">Parent Elements</span></span>  
  
|<span data-ttu-id="d07e3-151">Öğe</span><span class="sxs-lookup"><span data-stu-id="d07e3-151">Element</span></span>|<span data-ttu-id="d07e3-152">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d07e3-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d07e3-153">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="d07e3-153">\<security></span></span>](security-of-custombinding.md)|<span data-ttu-id="d07e3-154">Özel bağlama için güvenlik seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d07e3-154">Specifies the security options for a custom binding.</span></span>|  
|[<span data-ttu-id="d07e3-155">\<Securebir Bootstrap ></span><span class="sxs-lookup"><span data-stu-id="d07e3-155">\<secureConversationBootstrap></span></span>](secureconversationbootstrap.md)|<span data-ttu-id="d07e3-156">Güvenli konuşma hizmeti başlatmak için kullanılan varsayılan değerleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="d07e3-156">Specifies the default values used for initiating a secure conversation service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d07e3-157">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d07e3-157">Remarks</span></span>  
 <span data-ttu-id="d07e3-158">Ayarlar, hizmetin güvenlik ilkesinden türetilmiş ayarların olmadığı anlamda yereldir.</span><span class="sxs-lookup"><span data-stu-id="d07e3-158">The settings are local in the sense that they are not settings derived from the security policy of the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d07e3-159">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d07e3-159">See also</span></span>

- <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.LocalClientSettings%2A>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A>
- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="d07e3-160">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="d07e3-160">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d07e3-161">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="d07e3-161">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="d07e3-162">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="d07e3-162">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="d07e3-163">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="d07e3-163">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="d07e3-164">Nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma</span><span class="sxs-lookup"><span data-stu-id="d07e3-164">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="d07e3-165">Özel Bağlama Güvenliği</span><span class="sxs-lookup"><span data-stu-id="d07e3-165">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
