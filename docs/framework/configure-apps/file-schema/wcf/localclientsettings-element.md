---
title: <localClientSettings> öğesi
ms.date: 03/30/2017
ms.assetid: 4680ace5-f4e1-4fcb-b9d8-a4a4af5cd7ae
ms.openlocfilehash: 19eaea71fdaad1b945524cca5cf15634e0b0fa14
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158740"
---
# <a name="localclientsettings-element"></a><span data-ttu-id="f4909-102">\<localClientSettings> öğesi</span><span class="sxs-lookup"><span data-stu-id="f4909-102">\<localClientSettings> element</span></span>

<span data-ttu-id="f4909-103">Bu bağlama için yerel bir istemcinin güvenlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f4909-103">Specifies the security settings of a local client for this binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<localClientSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="f4909-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="f4909-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f4909-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f4909-105">Attributes and Elements</span></span>  

 <span data-ttu-id="f4909-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f4909-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f4909-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f4909-107">Attributes</span></span>  
  
|<span data-ttu-id="f4909-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f4909-108">Attribute</span></span>|<span data-ttu-id="f4909-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f4909-109">Description</span></span>|  
|---------------|-----------------|  
|`cacheCookies`|<span data-ttu-id="f4909-110">Tanımlama bilgisi önbelleğe almanın etkin olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="f4909-110">A Boolean value that specifies whether cookie caching is enabled.</span></span> <span data-ttu-id="f4909-111">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="f4909-111">The default is `false`.</span></span>|  
|`cookieRenewalThresholdPercentage`|<span data-ttu-id="f4909-112">Yenilenebilir tanımlama bilgilerinin maksimum yüzdesini belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="f4909-112">An integer that specifies the maximum percentage of cookies that can be renewed.</span></span> <span data-ttu-id="f4909-113">Bu değer, ikisi de dahil olmak üzere 0 ile 100 arasında olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f4909-113">This value should be between 0 and 100 inclusively.</span></span> <span data-ttu-id="f4909-114">Varsayılan değer 90 ' dir.</span><span class="sxs-lookup"><span data-stu-id="f4909-114">The default is 90.</span></span>|  
|`detectReplays`|<span data-ttu-id="f4909-115">Kanala karşı yeniden yürütme saldırılarının algılanıp algılanmayacağını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="f4909-115">A Boolean value that specifies whether replay attacks against the channel are detected and dealt with automatically.</span></span> <span data-ttu-id="f4909-116">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="f4909-116">The default is `false`.</span></span>|  
|`maxClockSkew`|<span data-ttu-id="f4909-117"><xref:System.TimeSpan>İki iletişim kuran tarafın sistem saatleri arasındaki en uzun süre farkını belirten bir.</span><span class="sxs-lookup"><span data-stu-id="f4909-117">A <xref:System.TimeSpan> that specifies the maximum time difference between the system clocks of the two communicating parties.</span></span> <span data-ttu-id="f4909-118">Varsayılan değer "00:05:00" dır.</span><span class="sxs-lookup"><span data-stu-id="f4909-118">The default value is "00:05:00".</span></span><br /><br /> <span data-ttu-id="f4909-119">Bu değer varsayılan değere ayarlandığında, alıcı gönderme zamanı zaman damgalarına sahip iletileri, daha sonra veya iletinin alındığı zamandan 5 dakikaya kadar kabul eder.</span><span class="sxs-lookup"><span data-stu-id="f4909-119">When this value is set to the default, the receiver accepts messages with send-time time stamps up to 5 minutes later or earlier than the time the message was received.</span></span> <span data-ttu-id="f4909-120">Gönderme zamanı testini geçemediği iletiler reddedilir.</span><span class="sxs-lookup"><span data-stu-id="f4909-120">Messages that do not pass the send-time test are rejected.</span></span> <span data-ttu-id="f4909-121">Bu ayar, özniteliğiyle birlikte kullanılır `replayWindow` .</span><span class="sxs-lookup"><span data-stu-id="f4909-121">This setting is used in conjunction with the `replayWindow` attribute.</span></span>|  
|`maxCookieCachingTime`|<span data-ttu-id="f4909-122"><xref:System.TimeSpan>En fazla tanımlama bilgisi ömrünü belirten bir.</span><span class="sxs-lookup"><span data-stu-id="f4909-122">A <xref:System.TimeSpan> that specifies the maximum lifetime of cookies.</span></span> <span data-ttu-id="f4909-123">Varsayılan değer "10675199.02:48:05.4775807" ' dir.</span><span class="sxs-lookup"><span data-stu-id="f4909-123">The default value is "10675199.02:48:05.4775807".</span></span>|  
|`reconnectTransportOnFailure`|<span data-ttu-id="f4909-124">WS-güvenilir mesajlaşma kullanan bağlantıların, aktarım hatalarından sonra yeniden bağlanmaya çalışıp çalışmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="f4909-124">A Boolean value that specifies whether connections using WS-Reliable messaging will attempt to reconnect after transport failures.</span></span> <span data-ttu-id="f4909-125">Varsayılan olarak, `true` sınırsız yeniden bağlanma girişimlerinin denendiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f4909-125">The default is `true`, which means that infinite attempts to reconnect are attempted.</span></span> <span data-ttu-id="f4909-126">Bu zaman aşımı, kanalın yeniden bağlanamayan bir özel durum oluşturmasına neden olan etkinlik dışı zaman aşımı nedeniyle bozulur.</span><span class="sxs-lookup"><span data-stu-id="f4909-126">The cycle is broken by the inactivity time-out, which causes the channel to throw an exception when it cannot be reconnected.</span></span>|  
|`replayCacheSize`|<span data-ttu-id="f4909-127">Yeniden yürütme algılaması için kullanılan önbelleğe alınmış nonce sayısını belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="f4909-127">A positive integer that specifies the number of cached nonces used for replay detection.</span></span> <span data-ttu-id="f4909-128">Bu sınır aşılırsa, en eski nonce kaldırılır ve yeni ileti için yeni bir nonce oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f4909-128">If this limit is exceeded, the oldest nonce is removed and a new nonce is created for the new message.</span></span> <span data-ttu-id="f4909-129">Varsayılan değer 500000 ' dir.</span><span class="sxs-lookup"><span data-stu-id="f4909-129">The default value is 500000.</span></span>|  
|`replayWindow`|<span data-ttu-id="f4909-130"><xref:System.TimeSpan>Tek tek ileti nonce öğelerinin geçerli olduğu süreyi belirten bir.</span><span class="sxs-lookup"><span data-stu-id="f4909-130">A <xref:System.TimeSpan> that specifies the duration in which individual message nonces are valid.</span></span><br /><br /> <span data-ttu-id="f4909-131">Bu süreden sonra, daha önce gönderilen ile aynı nonce ile gönderilen bir ileti kabul edilmez.</span><span class="sxs-lookup"><span data-stu-id="f4909-131">After this duration, a message sent with the same nonce as the one sent before will not be accepted.</span></span> <span data-ttu-id="f4909-132">Bu öznitelik, yeniden `maxClockSkew` yürütme saldırılarını engellemek için özniteliğiyle birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f4909-132">This attribute is used in conjunction with the `maxClockSkew` attribute to prevent replay attacks.</span></span> <span data-ttu-id="f4909-133">Bir saldırgan, yeniden yürütme penceresinin süresi dolduktan sonra bir iletiyi yeniden oynamıştır.</span><span class="sxs-lookup"><span data-stu-id="f4909-133">An attacker could replay a message after its replay window has expired.</span></span> <span data-ttu-id="f4909-134">Bununla birlikte, bu ileti, `maxClockSkew` gönderme zamanı zaman damgalarına sahip iletileri, daha sonra veya daha önceki bir süre içinde ileti alındığı zamandan reddeden test başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="f4909-134">This message, however, would fail the `maxClockSkew` test which rejects messages with send-time timestamps up to a specified time later or earlier than the time the message was received.</span></span>|  
|`sessionKeyRenewalInterval`|<span data-ttu-id="f4909-135"><xref:System.TimeSpan>Bu, başlatanın güvenlik oturumu anahtarını yenileyecek süreyi belirten bir.</span><span class="sxs-lookup"><span data-stu-id="f4909-135">A <xref:System.TimeSpan> that specifies the duration after which the initiator will renew the key for the security session.</span></span> <span data-ttu-id="f4909-136">Varsayılan değer "10:00:00" dır.</span><span class="sxs-lookup"><span data-stu-id="f4909-136">The default is "10:00:00".</span></span>|  
|`sessionKeyRolloverInterval`|<span data-ttu-id="f4909-137">Bir <xref:System.TimeSpan> anahtar yenilemesi sırasında önceki oturum anahtarının gelen iletilerde geçerli olduğu zaman aralığını belirten bir.</span><span class="sxs-lookup"><span data-stu-id="f4909-137">A <xref:System.TimeSpan> that specifies the time interval a previous session key is valid on incoming messages during a key renewal.</span></span> <span data-ttu-id="f4909-138">Varsayılan değer "00:05:00" dır.</span><span class="sxs-lookup"><span data-stu-id="f4909-138">The default is "00:05:00".</span></span><br /><br /> <span data-ttu-id="f4909-139">Anahtar yenileme sırasında, istemci ve sunucu her zaman en geçerli kullanılabilir anahtarı kullanarak ileti göndermelidir.</span><span class="sxs-lookup"><span data-stu-id="f4909-139">During key renewal, the client and server must always send messages using the most current available key.</span></span> <span data-ttu-id="f4909-140">Her iki taraf da, geçiş süresi sona erene kadar önceki oturum anahtarıyla güvenliği sağlanmış gelen iletileri kabul eder.</span><span class="sxs-lookup"><span data-stu-id="f4909-140">Both parties will accept incoming messages secured with the previous session key until the rollover time expires.</span></span>|  
|`timestampValidityDuration`|<span data-ttu-id="f4909-141"><xref:System.TimeSpan>Zaman damgasının geçerli olduğu süreyi belirten pozitif bir değer.</span><span class="sxs-lookup"><span data-stu-id="f4909-141">A positive <xref:System.TimeSpan> that specifies the duration in which a time stamp is valid.</span></span> <span data-ttu-id="f4909-142">Varsayılan değer "00:15:00" dır.</span><span class="sxs-lookup"><span data-stu-id="f4909-142">The default is "00:15:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f4909-143">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f4909-143">Child Elements</span></span>  

 <span data-ttu-id="f4909-144">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="f4909-144">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f4909-145">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f4909-145">Parent Elements</span></span>  
  
|<span data-ttu-id="f4909-146">Öğe</span><span class="sxs-lookup"><span data-stu-id="f4909-146">Element</span></span>|<span data-ttu-id="f4909-147">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f4909-147">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-custombinding.md)|<span data-ttu-id="f4909-148">Özel bağlama için güvenlik seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f4909-148">Specifies the security options for a custom binding.</span></span>|  
|[\<secureConversationBootstrap>](secureconversationbootstrap.md)|<span data-ttu-id="f4909-149">Güvenli konuşma hizmeti başlatmak için kullanılan varsayılan değerleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="f4909-149">Specifies the default values used for initiating a secure conversation service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f4909-150">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f4909-150">Remarks</span></span>  

 <span data-ttu-id="f4909-151">Ayarlar, hizmetin güvenlik ilkesinden türetilmiş ayarların olmadığı anlamda yereldir.</span><span class="sxs-lookup"><span data-stu-id="f4909-151">The settings are local in the sense that they are not settings derived from the security policy of the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4909-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f4909-152">See also</span></span>

- <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.LocalClientSettings%2A>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A>
- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="f4909-153">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="f4909-153">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f4909-154">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="f4909-154">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="f4909-155">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="f4909-155">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="f4909-156">Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f4909-156">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="f4909-157">Özel Bağlama Güvenliği</span><span class="sxs-lookup"><span data-stu-id="f4909-157">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
