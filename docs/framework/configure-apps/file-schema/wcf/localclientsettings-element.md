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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cabde7eb9dd122c2f7060b2f2e2c16f5949dc1f3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltlocalclientsettingsgt-element"></a>&lt;localClientSettings&gt; öğesi
Bu bağlama için yerel bir istemci güvenlik ayarlarını belirtir.  
  
 \<system.serviceModel >  
\<bağlamaları >  
\<customBinding >  
\<bağlama >  
\<Güvenlik >  
  
## <a name="syntax"></a>Sözdizimi  
  
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
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`cacheCookies`|Tanımlama bilgisi önbelleğe almanın etkin olup olmadığını belirten bir Boole değeri. Varsayılan, `false` değeridir.|  
|`cookieRenewalThresholdPercentage`|Yenilenebilir tanımlama bilgilerini yüzdesinin üst sınırını belirten bir tamsayı. Bu değer ikisi de dahil olmak 0 ile 100 arasında olmalıdır. Varsayılan olarak 90 gündür.|  
|`detectReplays`|Yeniden yürütme saldırılarına karşı kanal algılandı ve otomatik olarak ele olup olmadığını belirten bir Boole değeri. Varsayılan, `false` değeridir.|  
|`maxClockSkew`|A <xref:System.TimeSpan> iki iletişim kuran tarafların sistem saatlerinin arasındaki en büyük zaman farkı belirtir. Varsayılan değer "00: 05:00".<br /><br /> Bu değer varsayılan olarak ayarlandığında, alıcı iletileri gönderme zamanı zaman damgaları ile yukarı daha sonra 5 dakika olarak kabul eder veya ileti zamandan daha önce alındı. Gönderme zamanı test geçmeyin iletiler reddedilir. Bu ayar ile birlikte kullanılan `replayWindow` özniteliği.|  
|`maxCookieCachingTime`|A <xref:System.TimeSpan> tanımlama bilgilerini en uzun kullanım ömrünü belirtir. Varsayılan değer "10675199.02:48:05.4775807" dir.|  
|`reconnectTransportOnFailure`|WS güvenilir Mesajlaşma kullanarak bağlantıları aktarım hataları sonra yeniden bağlanmayı deneyip denemeyeceğini belirten bir Boole değeri. Varsayılan değer `true`, yeniden bağlanma girişimleri sonsuz denenme anlamına gelir. Döngü, bağlanılamaz zaman bir özel durum kanala neden olan etkinlik zaman aşımını tarafından ayrılır.|  
|`replayCacheSize`|Yeniden yürütme algılaması için önbelleğe alınan nonce sayısını belirten pozitif bir tamsayı. Bu sınır aşılırsa, en eski nonce kaldırılır ve yeni bir geçici öğe için yeni ileti oluşturulur. 500000 varsayılan değerdir.|  
|`replayWindow`|A <xref:System.TimeSpan> , tek tek ileti nonce öğelerinin geçerli süresini belirtir.<br /><br /> Bu süre önce gönderilen hesapla aynı nonce ile gönderilen bir ileti kabul edilmedi. Bu öznitelik ile birlikte kullanılan `maxClockSkew` yeniden yürütme saldırılarını önlemek için öznitelik. Bir saldırgan yeniden yürütme penceresinin süresi dolduktan sonra bir ileti yeniden yürütme. Ancak, bu iletiyi başarısız olacağı `maxClockSkew` ileti alınan iletileri sonraki veya önceki zamandan belirtilen süre kadar gönderme zaman damgalı reddeder test.|  
|`sessionKeyRenewalInterval`|A <xref:System.TimeSpan> geçmesi Başlatıcı yenilenecektir anahtarı için güvenlik oturumu süresini belirtir. Varsayılan değer "10: 00:00".|  
|`sessionKeyRolloverInterval`|A <xref:System.TimeSpan> zaman aralığı bir önceki oturum anahtarı gelen iletileri geçerli anahtar yenileme sırasında belirtir. Varsayılan değer "00: 05:00".<br /><br /> Anahtar yenileme sırasında istemci ve sunucu her zaman en güncel kullanılabilir anahtarı kullanarak iletileri göndermeniz gerekir. Her iki taraf rollover süresi dolmadan önceki oturum anahtarı ile güvenli hale gelen iletileri kabul eder.|  
|`timestampValidityDuration`|Bir pozitif <xref:System.TimeSpan> zaman damgası olduğu geçerli süresini belirtir. Varsayılan değer "00: 15:00".|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Güvenlik >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|Özel bağlama için güvenlik seçeneklerini belirtir.|  
|[\<secureConversationBootstrap >](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|Güvenli Konuşmayla hizmeti başlatmak için kullanılan varsayılan değerleri belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yerel hizmet güvenlik ilkesinden türetilmiş ayarları olmadıklarını herkese açık ayarlardır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>  
 <xref:System.ServiceModel.Configuration.SecurityElementBase.LocalClientSettings%2A>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A>  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Bağlamaları](../../../../../docs/framework/wcf/bindings.md)  
 [Bağlamaları genişletme](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Özel bağlamalar](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [Nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [Özel bağlama güvenliği](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
