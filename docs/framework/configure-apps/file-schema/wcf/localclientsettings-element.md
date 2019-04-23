---
title: <localClientSettings> öğesi
ms.date: 03/30/2017
ms.assetid: 4680ace5-f4e1-4fcb-b9d8-a4a4af5cd7ae
ms.openlocfilehash: c5caf183e37edda6efc79ec81f1628180379fd46
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59163104"
---
# <a name="localclientsettings-element"></a>\<localClientSettings > öğesi
Bu bağlama için yerel bir istemci güvenlik ayarlarını belirtir.  
  
 \<system.serviceModel>  
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
|`cacheCookies`|Tanımlama bilgisinin önbelleğe almanın etkin olup olmadığını belirten bir Boole değeri. Varsayılan, `false` değeridir.|  
|`cookieRenewalThresholdPercentage`|Yenilenebilir tanımlama bilgilerinin maksimum yüzdesini belirten bir tamsayı. Bu değer 0 ile 100 arasında aralığında olmalıdır. Varsayılan olarak 90 gündür.|  
|`detectReplays`|Kanal yeniden yürütme saldırıları algılandı ve otomatik olarak ele belirten bir Boole değeri. Varsayılan, `false` değeridir.|  
|`maxClockSkew`|A <xref:System.TimeSpan> iletişim kuran taraflar iki tarafın sistem saatleri arasındaki en büyük zaman farkı belirtir. Varsayılan değer "00: 05:00".<br /><br /> Bu değeri varsayılan değere ayarlandığında, alıcı kabul daha sonra 5 dakika ile ileti gönderme zaman zaman damgaları ile yukarı veya zamandan daha önce iletisi alındı. Gönderme zamanı test geçmeyin iletileri reddedilir. Bu ayar ile birlikte kullanılan `replayWindow` özniteliği.|  
|`maxCookieCachingTime`|A <xref:System.TimeSpan> tanımlama bilgileri maksimum ömrünü belirtir. "10675199.02:48:05.4775807" varsayılan değerdir.|  
|`reconnectTransportOnFailure`|WS-Reliable Mesajlaşma kullanan bağlantı aktarım hatasından sonra yeniden bağlanmayı deneyip denemeyeceğini belirten bir Boole değeri. Varsayılan `true`, sonsuz bir yeniden dener çalıştığının anlamına gelir. Döngü, bağlanılamaz zaman kanala neden olan etkin olmama zaman aşımı tarafından ayrılır.|  
|`replayCacheSize`|Yeniden yürütme algılaması için önbelleğe alınan nonce sayısını belirten pozitif bir tamsayı. Bu sınır aşılırsa, eski nonce kaldırılır ve yeni bir geçici öğe için yeni bir ileti oluşturulur. 500000 varsayılan değerdir.|  
|`replayWindow`|A <xref:System.TimeSpan> içinde tek tek ileti nonce öğelerinin geçerli süresini belirtir.<br /><br /> Bu süre önce gönderilenle olarak aynı nonce ile gönderilen bir iletinin kabul edilmez. Bu öznitelik ile birlikte kullanılan `maxClockSkew` yeniden yürütme saldırıları önlemek için özniteliği. Yeniden yürütme penceresi süresi dolduktan sonra bir saldırganın bir ileti yeniden yürütme. Ancak, bu iletiyi başarısız olacağı `maxClockSkew` test kadar belirli bir süreden daha yeni veya daha önceki gönderme zaman damgalı bir ileti alındı iletileri reddeder.|  
|`sessionKeyRenewalInterval`|A <xref:System.TimeSpan> sonra başlatıcı yenileyecek anahtarı güvenlik oturumu için süreyi belirtir. Varsayılan değer "10: 00:00".|  
|`sessionKeyRolloverInterval`|A <xref:System.TimeSpan> zaman aralığını önceki oturum anahtarının geçerli gelen iletinin anahtar yenilemesi sırasında belirtir. Varsayılan değer "00: 05:00".<br /><br /> Anahtar yenilemesi sırasında istemci ve sunucu her zaman en güncel kullanılabilir anahtarı kullanarak ileti göndermeniz gerekir. Her iki taraf geçiş süresi dolana kadar önceki oturum anahtarı ile güvenli hale gelen iletileri kabul eder.|  
|`timestampValidityDuration`|Bir pozitif <xref:System.TimeSpan> zaman damgası olan geçerli süresini belirtir. Varsayılan değer "00: 15:00".|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Güvenlik >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|Özel bağlama için güvenlik seçeneklerini belirtir.|  
|[\<secureConversationBootstrap>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|Güvenli konuşma hizmeti başlatmak için kullanılan varsayılan değerleri belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ayarlar yerel ayarları hizmeti güvenlik ilkesinden türetilmiş olmadıklarını anlamında gösterir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.LocalClientSettings%2A>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A>
- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)
- [Bağlamaları Genişletme](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Özel Bağlamalar](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [Nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Özel Bağlama Güvenliği](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
