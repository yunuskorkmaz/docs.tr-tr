---
title: <localClientSettings> öğesi
ms.date: 03/30/2017
ms.assetid: 4680ace5-f4e1-4fcb-b9d8-a4a4af5cd7ae
ms.openlocfilehash: 3ec0394943c030a8866087c98a912682a2a2112e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400316"
---
# <a name="localclientsettings-element"></a><span data-ttu-id="8092b-102">\<localClientSettings> öğesi</span><span class="sxs-lookup"><span data-stu-id="8092b-102">\<localClientSettings> element</span></span>
<span data-ttu-id="8092b-103">Bu bağlama için yerel bir istemcinin güvenlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="8092b-103">Specifies the security settings of a local client for this binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<localClientSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="8092b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8092b-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8092b-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8092b-105">Attributes and Elements</span></span>  
 <span data-ttu-id="8092b-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8092b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8092b-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8092b-107">Attributes</span></span>  
  
|<span data-ttu-id="8092b-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8092b-108">Attribute</span></span>|<span data-ttu-id="8092b-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8092b-109">Description</span></span>|  
|---------------|-----------------|  
|`cacheCookies`|<span data-ttu-id="8092b-110">Tanımlama bilgisi önbelleğe almanın etkin olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="8092b-110">A Boolean value that specifies whether cookie caching is enabled.</span></span> <span data-ttu-id="8092b-111">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="8092b-111">The default is `false`.</span></span>|  
|`cookieRenewalThresholdPercentage`|<span data-ttu-id="8092b-112">Yenilenebilir tanımlama bilgilerinin maksimum yüzdesini belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="8092b-112">An integer that specifies the maximum percentage of cookies that can be renewed.</span></span> <span data-ttu-id="8092b-113">Bu değer, ikisi de dahil olmak üzere 0 ile 100 arasında olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8092b-113">This value should be between 0 and 100 inclusively.</span></span> <span data-ttu-id="8092b-114">Varsayılan değer 90 ' dir.</span><span class="sxs-lookup"><span data-stu-id="8092b-114">The default is 90.</span></span>|  
|`detectReplays`|<span data-ttu-id="8092b-115">Kanala karşı yeniden yürütme saldırılarının algılanıp algılanmayacağını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="8092b-115">A Boolean value that specifies whether replay attacks against the channel are detected and dealt with automatically.</span></span> <span data-ttu-id="8092b-116">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="8092b-116">The default is `false`.</span></span>|  
|`maxClockSkew`|<span data-ttu-id="8092b-117"><xref:System.TimeSpan>İki iletişim kuran tarafın sistem saatleri arasındaki en uzun süre farkını belirten bir.</span><span class="sxs-lookup"><span data-stu-id="8092b-117">A <xref:System.TimeSpan> that specifies the maximum time difference between the system clocks of the two communicating parties.</span></span> <span data-ttu-id="8092b-118">Varsayılan değer "00:05:00" dır.</span><span class="sxs-lookup"><span data-stu-id="8092b-118">The default value is "00:05:00".</span></span><br /><br /> <span data-ttu-id="8092b-119">Bu değer varsayılan değere ayarlandığında, alıcı gönderme zamanı zaman damgalarına sahip iletileri, daha sonra veya iletinin alındığı zamandan 5 dakikaya kadar kabul eder.</span><span class="sxs-lookup"><span data-stu-id="8092b-119">When this value is set to the default, the receiver accepts messages with send-time time stamps up to 5 minutes later or earlier than the time the message was received.</span></span> <span data-ttu-id="8092b-120">Gönderme zamanı testini geçemediği iletiler reddedilir.</span><span class="sxs-lookup"><span data-stu-id="8092b-120">Messages that do not pass the send-time test are rejected.</span></span> <span data-ttu-id="8092b-121">Bu ayar, özniteliğiyle birlikte kullanılır `replayWindow` .</span><span class="sxs-lookup"><span data-stu-id="8092b-121">This setting is used in conjunction with the `replayWindow` attribute.</span></span>|  
|`maxCookieCachingTime`|<span data-ttu-id="8092b-122"><xref:System.TimeSpan>En fazla tanımlama bilgisi ömrünü belirten bir.</span><span class="sxs-lookup"><span data-stu-id="8092b-122">A <xref:System.TimeSpan> that specifies the maximum lifetime of cookies.</span></span> <span data-ttu-id="8092b-123">Varsayılan değer "10675199.02:48:05.4775807" ' dir.</span><span class="sxs-lookup"><span data-stu-id="8092b-123">The default value is "10675199.02:48:05.4775807".</span></span>|  
|`reconnectTransportOnFailure`|<span data-ttu-id="8092b-124">WS-güvenilir mesajlaşma kullanan bağlantıların, aktarım hatalarından sonra yeniden bağlanmaya çalışıp çalışmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="8092b-124">A Boolean value that specifies whether connections using WS-Reliable messaging will attempt to reconnect after transport failures.</span></span> <span data-ttu-id="8092b-125">Varsayılan olarak, `true` sınırsız yeniden bağlanma girişimlerinin denendiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="8092b-125">The default is `true`, which means that infinite attempts to reconnect are attempted.</span></span> <span data-ttu-id="8092b-126">Bu zaman aşımı, kanalın yeniden bağlanamayan bir özel durum oluşturmasına neden olan etkinlik dışı zaman aşımı nedeniyle bozulur.</span><span class="sxs-lookup"><span data-stu-id="8092b-126">The cycle is broken by the inactivity time-out, which causes the channel to throw an exception when it cannot be reconnected.</span></span>|  
|`replayCacheSize`|<span data-ttu-id="8092b-127">Yeniden yürütme algılaması için kullanılan önbelleğe alınmış nonce sayısını belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="8092b-127">A positive integer that specifies the number of cached nonces used for replay detection.</span></span> <span data-ttu-id="8092b-128">Bu sınır aşılırsa, en eski nonce kaldırılır ve yeni ileti için yeni bir nonce oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="8092b-128">If this limit is exceeded, the oldest nonce is removed and a new nonce is created for the new message.</span></span> <span data-ttu-id="8092b-129">Varsayılan değer 500000 ' dir.</span><span class="sxs-lookup"><span data-stu-id="8092b-129">The default value is 500000.</span></span>|  
|`replayWindow`|<span data-ttu-id="8092b-130"><xref:System.TimeSpan>Tek tek ileti nonce öğelerinin geçerli olduğu süreyi belirten bir.</span><span class="sxs-lookup"><span data-stu-id="8092b-130">A <xref:System.TimeSpan> that specifies the duration in which individual message nonces are valid.</span></span><br /><br /> <span data-ttu-id="8092b-131">Bu süreden sonra, daha önce gönderilen ile aynı nonce ile gönderilen bir ileti kabul edilmez.</span><span class="sxs-lookup"><span data-stu-id="8092b-131">After this duration, a message sent with the same nonce as the one sent before will not be accepted.</span></span> <span data-ttu-id="8092b-132">Bu öznitelik, yeniden `maxClockSkew` yürütme saldırılarını engellemek için özniteliğiyle birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8092b-132">This attribute is used in conjunction with the `maxClockSkew` attribute to prevent replay attacks.</span></span> <span data-ttu-id="8092b-133">Bir saldırgan, yeniden yürütme penceresinin süresi dolduktan sonra bir iletiyi yeniden oynamıştır.</span><span class="sxs-lookup"><span data-stu-id="8092b-133">An attacker could replay a message after its replay window has expired.</span></span> <span data-ttu-id="8092b-134">Bununla birlikte, bu ileti, `maxClockSkew` gönderme zamanı zaman damgalarına sahip iletileri, daha sonra veya daha önceki bir süre içinde ileti alındığı zamandan reddeden test başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="8092b-134">This message, however, would fail the `maxClockSkew` test which rejects messages with send-time timestamps up to a specified time later or earlier than the time the message was received.</span></span>|  
|`sessionKeyRenewalInterval`|<span data-ttu-id="8092b-135"><xref:System.TimeSpan>Bu, başlatanın güvenlik oturumu anahtarını yenileyecek süreyi belirten bir.</span><span class="sxs-lookup"><span data-stu-id="8092b-135">A <xref:System.TimeSpan> that specifies the duration after which the initiator will renew the key for the security session.</span></span> <span data-ttu-id="8092b-136">Varsayılan değer "10:00:00" dır.</span><span class="sxs-lookup"><span data-stu-id="8092b-136">The default is "10:00:00".</span></span>|  
|`sessionKeyRolloverInterval`|<span data-ttu-id="8092b-137">Bir <xref:System.TimeSpan> anahtar yenilemesi sırasında önceki oturum anahtarının gelen iletilerde geçerli olduğu zaman aralığını belirten bir.</span><span class="sxs-lookup"><span data-stu-id="8092b-137">A <xref:System.TimeSpan> that specifies the time interval a previous session key is valid on incoming messages during a key renewal.</span></span> <span data-ttu-id="8092b-138">Varsayılan değer "00:05:00" dır.</span><span class="sxs-lookup"><span data-stu-id="8092b-138">The default is "00:05:00".</span></span><br /><br /> <span data-ttu-id="8092b-139">Anahtar yenileme sırasında, istemci ve sunucu her zaman en geçerli kullanılabilir anahtarı kullanarak ileti göndermelidir.</span><span class="sxs-lookup"><span data-stu-id="8092b-139">During key renewal, the client and server must always send messages using the most current available key.</span></span> <span data-ttu-id="8092b-140">Her iki taraf da, geçiş süresi sona erene kadar önceki oturum anahtarıyla güvenliği sağlanmış gelen iletileri kabul eder.</span><span class="sxs-lookup"><span data-stu-id="8092b-140">Both parties will accept incoming messages secured with the previous session key until the rollover time expires.</span></span>|  
|`timestampValidityDuration`|<span data-ttu-id="8092b-141"><xref:System.TimeSpan>Zaman damgasının geçerli olduğu süreyi belirten pozitif bir değer.</span><span class="sxs-lookup"><span data-stu-id="8092b-141">A positive <xref:System.TimeSpan> that specifies the duration in which a time stamp is valid.</span></span> <span data-ttu-id="8092b-142">Varsayılan değer "00:15:00" dır.</span><span class="sxs-lookup"><span data-stu-id="8092b-142">The default is "00:15:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8092b-143">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8092b-143">Child Elements</span></span>  
 <span data-ttu-id="8092b-144">Yok</span><span class="sxs-lookup"><span data-stu-id="8092b-144">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8092b-145">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8092b-145">Parent Elements</span></span>  
  
|<span data-ttu-id="8092b-146">Öğe</span><span class="sxs-lookup"><span data-stu-id="8092b-146">Element</span></span>|<span data-ttu-id="8092b-147">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8092b-147">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-custombinding.md)|<span data-ttu-id="8092b-148">Özel bağlama için güvenlik seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8092b-148">Specifies the security options for a custom binding.</span></span>|  
|[\<secureConversationBootstrap>](secureconversationbootstrap.md)|<span data-ttu-id="8092b-149">Güvenli konuşma hizmeti başlatmak için kullanılan varsayılan değerleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="8092b-149">Specifies the default values used for initiating a secure conversation service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8092b-150">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8092b-150">Remarks</span></span>  
 <span data-ttu-id="8092b-151">Ayarlar, hizmetin güvenlik ilkesinden türetilmiş ayarların olmadığı anlamda yereldir.</span><span class="sxs-lookup"><span data-stu-id="8092b-151">The settings are local in the sense that they are not settings derived from the security policy of the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8092b-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8092b-152">See also</span></span>

- <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.LocalClientSettings%2A>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A>
- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="8092b-153">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="8092b-153">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="8092b-154">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="8092b-154">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="8092b-155">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="8092b-155">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="8092b-156">Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="8092b-156">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="8092b-157">Özel Bağlama Güvenliği</span><span class="sxs-lookup"><span data-stu-id="8092b-157">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
