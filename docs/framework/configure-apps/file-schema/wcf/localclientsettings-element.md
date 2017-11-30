---
title: "&lt;localClientSettings&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4680ace5-f4e1-4fcb-b9d8-a4a4af5cd7ae
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d56c7c199ed437fdfc1277ecb6c99f7b8c6cbe38
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltlocalclientsettingsgt-element"></a><span data-ttu-id="8aae4-102">&lt;localClientSettings&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="8aae4-102">&lt;localClientSettings&gt; element</span></span>
<span data-ttu-id="8aae4-103">Bu bağlama için yerel bir istemci güvenlik ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="8aae4-103">Specifies the security settings of a local client for this binding.</span></span>  
  
 <span data-ttu-id="8aae4-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="8aae4-104">\<system.serviceModel></span></span>  
<span data-ttu-id="8aae4-105">\<bağlamaları ></span><span class="sxs-lookup"><span data-stu-id="8aae4-105">\<bindings></span></span>  
<span data-ttu-id="8aae4-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="8aae4-106">\<customBinding></span></span>  
<span data-ttu-id="8aae4-107">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="8aae4-107">\<binding></span></span>  
<span data-ttu-id="8aae4-108">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="8aae4-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8aae4-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8aae4-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8aae4-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8aae4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8aae4-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8aae4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8aae4-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8aae4-112">Attributes</span></span>  
  
|<span data-ttu-id="8aae4-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8aae4-113">Attribute</span></span>|<span data-ttu-id="8aae4-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8aae4-114">Description</span></span>|  
|---------------|-----------------|  
|`cacheCookies`|<span data-ttu-id="8aae4-115">Tanımlama bilgisi önbelleğe almanın etkin olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="8aae4-115">A Boolean value that specifies whether cookie caching is enabled.</span></span> <span data-ttu-id="8aae4-116">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="8aae4-116">The default is `false`.</span></span>|  
|`cookieRenewalThresholdPercentage`|<span data-ttu-id="8aae4-117">Yenilenebilir tanımlama bilgilerini yüzdesinin üst sınırını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="8aae4-117">An integer that specifies the maximum percentage of cookies that can be renewed.</span></span> <span data-ttu-id="8aae4-118">Bu değer ikisi de dahil olmak 0 ile 100 arasında olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8aae4-118">This value should be between 0 and 100 inclusively.</span></span> <span data-ttu-id="8aae4-119">Varsayılan olarak 90 gündür.</span><span class="sxs-lookup"><span data-stu-id="8aae4-119">The default is 90.</span></span>|  
|`detectReplays`|<span data-ttu-id="8aae4-120">Yeniden yürütme saldırılarına karşı kanal algılandı ve otomatik olarak ele olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="8aae4-120">A Boolean value that specifies whether replay attacks against the channel are detected and dealt with automatically.</span></span> <span data-ttu-id="8aae4-121">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="8aae4-121">The default is `false`.</span></span>|  
|`maxClockSkew`|<span data-ttu-id="8aae4-122">A <xref:System.TimeSpan> iki iletişim kuran tarafların sistem saatlerinin arasındaki en büyük zaman farkı belirtir.</span><span class="sxs-lookup"><span data-stu-id="8aae4-122">A <xref:System.TimeSpan> that specifies the maximum time difference between the system clocks of the two communicating parties.</span></span> <span data-ttu-id="8aae4-123">Varsayılan değer "00: 05:00".</span><span class="sxs-lookup"><span data-stu-id="8aae4-123">The default value is "00:05:00".</span></span><br /><br /> <span data-ttu-id="8aae4-124">Bu değer varsayılan olarak ayarlandığında, alıcı iletileri gönderme zamanı zaman damgaları ile yukarı daha sonra 5 dakika olarak kabul eder veya ileti zamandan daha önce alındı.</span><span class="sxs-lookup"><span data-stu-id="8aae4-124">When this value is set to the default, the receiver accepts messages with send-time time stamps up to 5 minutes later or earlier than the time the message was received.</span></span> <span data-ttu-id="8aae4-125">Gönderme zamanı test geçmeyin iletiler reddedilir.</span><span class="sxs-lookup"><span data-stu-id="8aae4-125">Messages that do not pass the send-time test are rejected.</span></span> <span data-ttu-id="8aae4-126">Bu ayar ile birlikte kullanılan `replayWindow` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="8aae4-126">This setting is used in conjunction with the `replayWindow` attribute.</span></span>|  
|`maxCookieCachingTime`|<span data-ttu-id="8aae4-127">A <xref:System.TimeSpan> tanımlama bilgilerini en uzun kullanım ömrünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="8aae4-127">A <xref:System.TimeSpan> that specifies the maximum lifetime of cookies.</span></span> <span data-ttu-id="8aae4-128">Varsayılan değer "10675199.02:48:05.4775807" dir.</span><span class="sxs-lookup"><span data-stu-id="8aae4-128">The default value is "10675199.02:48:05.4775807".</span></span>|  
|`reconnectTransportOnFailure`|<span data-ttu-id="8aae4-129">WS güvenilir Mesajlaşma kullanarak bağlantıları aktarım hataları sonra yeniden bağlanmayı deneyip denemeyeceğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="8aae4-129">A Boolean value that specifies whether connections using WS-Reliable messaging will attempt to reconnect after transport failures.</span></span> <span data-ttu-id="8aae4-130">Varsayılan değer `true`, yeniden bağlanma girişimleri sonsuz denenme anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="8aae4-130">The default is `true`, which means that infinite attempts to reconnect are attempted.</span></span> <span data-ttu-id="8aae4-131">Döngü, bağlanılamaz zaman bir özel durum kanala neden olan etkinlik zaman aşımını tarafından ayrılır.</span><span class="sxs-lookup"><span data-stu-id="8aae4-131">The cycle is broken by the inactivity time-out, which causes the channel to throw an exception when it cannot be reconnected.</span></span>|  
|`replayCacheSize`|<span data-ttu-id="8aae4-132">Yeniden yürütme algılaması için önbelleğe alınan nonce sayısını belirten pozitif bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="8aae4-132">A positive integer that specifies the number of cached nonces used for replay detection.</span></span> <span data-ttu-id="8aae4-133">Bu sınır aşılırsa, en eski nonce kaldırılır ve yeni bir geçici öğe için yeni ileti oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="8aae4-133">If this limit is exceeded, the oldest nonce is removed and a new nonce is created for the new message.</span></span> <span data-ttu-id="8aae4-134">500000 varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="8aae4-134">The default value is 500000.</span></span>|  
|`replayWindow`|<span data-ttu-id="8aae4-135">A <xref:System.TimeSpan> , tek tek ileti nonce öğelerinin geçerli süresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8aae4-135">A <xref:System.TimeSpan> that specifies the duration in which individual message nonces are valid.</span></span><br /><br /> <span data-ttu-id="8aae4-136">Bu süre önce gönderilen hesapla aynı nonce ile gönderilen bir ileti kabul edilmedi.</span><span class="sxs-lookup"><span data-stu-id="8aae4-136">After this duration, a message sent with the same nonce as the one sent before will not be accepted.</span></span> <span data-ttu-id="8aae4-137">Bu öznitelik ile birlikte kullanılan `maxClockSkew` yeniden yürütme saldırılarını önlemek için öznitelik.</span><span class="sxs-lookup"><span data-stu-id="8aae4-137">This attribute is used in conjunction with the `maxClockSkew` attribute to prevent replay attacks.</span></span> <span data-ttu-id="8aae4-138">Bir saldırgan yeniden yürütme penceresinin süresi dolduktan sonra bir ileti yeniden yürütme.</span><span class="sxs-lookup"><span data-stu-id="8aae4-138">An attacker could replay a message after its replay window has expired.</span></span> <span data-ttu-id="8aae4-139">Ancak, bu iletiyi başarısız olacağı `maxClockSkew` ileti alınan iletileri sonraki veya önceki zamandan belirtilen süre kadar gönderme zaman damgalı reddeder test.</span><span class="sxs-lookup"><span data-stu-id="8aae4-139">This message, however, would fail the `maxClockSkew` test which rejects messages with send-time timestamps up to a specified time later or earlier than the time the message was received.</span></span>|  
|`sessionKeyRenewalInterval`|<span data-ttu-id="8aae4-140">A <xref:System.TimeSpan> geçmesi Başlatıcı yenilenecektir anahtarı için güvenlik oturumu süresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8aae4-140">A <xref:System.TimeSpan> that specifies the duration after which the initiator will renew the key for the security session.</span></span> <span data-ttu-id="8aae4-141">Varsayılan değer "10: 00:00".</span><span class="sxs-lookup"><span data-stu-id="8aae4-141">The default is "10:00:00".</span></span>|  
|`sessionKeyRolloverInterval`|<span data-ttu-id="8aae4-142">A <xref:System.TimeSpan> zaman aralığı bir önceki oturum anahtarı gelen iletileri geçerli anahtar yenileme sırasında belirtir.</span><span class="sxs-lookup"><span data-stu-id="8aae4-142">A <xref:System.TimeSpan> that specifies the time interval a previous session key is valid on incoming messages during a key renewal.</span></span> <span data-ttu-id="8aae4-143">Varsayılan değer "00: 05:00".</span><span class="sxs-lookup"><span data-stu-id="8aae4-143">The default is "00:05:00".</span></span><br /><br /> <span data-ttu-id="8aae4-144">Anahtar yenileme sırasında istemci ve sunucu her zaman en güncel kullanılabilir anahtarı kullanarak iletileri göndermeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8aae4-144">During key renewal, the client and server must always send messages using the most current available key.</span></span> <span data-ttu-id="8aae4-145">Her iki taraf rollover süresi dolmadan önceki oturum anahtarı ile güvenli hale gelen iletileri kabul eder.</span><span class="sxs-lookup"><span data-stu-id="8aae4-145">Both parties will accept incoming messages secured with the previous session key until the rollover time expires.</span></span>|  
|`timestampValidityDuration`|<span data-ttu-id="8aae4-146">Bir pozitif <xref:System.TimeSpan> zaman damgası olduğu geçerli süresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8aae4-146">A positive <xref:System.TimeSpan> that specifies the duration in which a time stamp is valid.</span></span> <span data-ttu-id="8aae4-147">Varsayılan değer "00: 15:00".</span><span class="sxs-lookup"><span data-stu-id="8aae4-147">The default is "00:15:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8aae4-148">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8aae4-148">Child Elements</span></span>  
 <span data-ttu-id="8aae4-149">Yok.</span><span class="sxs-lookup"><span data-stu-id="8aae4-149">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8aae4-150">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8aae4-150">Parent Elements</span></span>  
  
|<span data-ttu-id="8aae4-151">Öğe</span><span class="sxs-lookup"><span data-stu-id="8aae4-151">Element</span></span>|<span data-ttu-id="8aae4-152">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8aae4-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8aae4-153">\<Güvenlik ></span><span class="sxs-lookup"><span data-stu-id="8aae4-153">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|<span data-ttu-id="8aae4-154">Özel bağlama için güvenlik seçeneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8aae4-154">Specifies the security options for a custom binding.</span></span>|  
|[<span data-ttu-id="8aae4-155">\<secureConversationBootstrap ></span><span class="sxs-lookup"><span data-stu-id="8aae4-155">\<secureConversationBootstrap></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|<span data-ttu-id="8aae4-156">Güvenli Konuşmayla hizmeti başlatmak için kullanılan varsayılan değerleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="8aae4-156">Specifies the default values used for initiating a secure conversation service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8aae4-157">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8aae4-157">Remarks</span></span>  
 <span data-ttu-id="8aae4-158">Yerel hizmet güvenlik ilkesinden türetilmiş ayarları olmadıklarını herkese açık ayarlardır.</span><span class="sxs-lookup"><span data-stu-id="8aae4-158">The settings are local in the sense that they are not settings derived from the security policy of the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8aae4-159">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8aae4-159">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>  
 <xref:System.ServiceModel.Configuration.SecurityElementBase.LocalClientSettings%2A>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A>  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="8aae4-160">Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="8aae4-160">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="8aae4-161">Bağlamaları genişletme</span><span class="sxs-lookup"><span data-stu-id="8aae4-161">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="8aae4-162">Özel bağlamalar</span><span class="sxs-lookup"><span data-stu-id="8aae4-162">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="8aae4-163">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="8aae4-163">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="8aae4-164">Nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma</span><span class="sxs-lookup"><span data-stu-id="8aae4-164">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="8aae4-165">Özel bağlama güvenliği</span><span class="sxs-lookup"><span data-stu-id="8aae4-165">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
