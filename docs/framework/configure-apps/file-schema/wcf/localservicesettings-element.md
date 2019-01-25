---
title: '&lt;localServiceSettings&gt; öğesi'
ms.date: 03/30/2017
ms.assetid: 0658549c-3f65-46dd-8c5c-9895441ed734
ms.openlocfilehash: 6427f28bfbaa38df20696911f5f72c73d992c971
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54535236"
---
# <a name="ltlocalservicesettingsgt-element"></a>&lt;localServiceSettings&gt; öğesi
Bu bağlama için yerel bir hizmetin güvenlik ayarlarını belirtir.  
  
 \<system.serviceModel>  
\<bağlamaları >  
\<customBinding >  
\<bağlama >  
\<Güvenlik >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<security>
  <localServiceSettings detectReplays="Boolean"
                        inactivityTimeout="TimeSpan"
                        issuedCookieLifeTime="TimeSpan"
                        maxCachedCookies="Integer"
                        maxClockSkew="TimeSpan"
                        maxPendingSessions="Integer"
                        maxStatefulNegotiations="Integer"
                        negotiationTimeout="TimeSpan"
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
|`detectReplays`|Kanal yeniden yürütme saldırıları algılandı ve otomatik olarak ele belirten bir Boole değeri. Varsayılan, `false` değeridir.|  
|`inactivityTimeout`|Bir pozitif <xref:System.TimeSpan> kanal bekleyeceği zaman aşımına uğramadan önce etkin olmama süresini belirtir. Varsayılan değer "01: 00:00".|  
|`issuedCookieLifeTime`|A <xref:System.TimeSpan> tüm yeni güvenlik tanımlama bilgilerine verilen ömür süresini belirtir. Kendi ömürlerine aşan tanımlama bilgileri geri dönüştürülünceye ve yeniden sağlanması gerekir. Varsayılan değer "10: 00:00".|  
|`maxCachedCookies`|Önbelleğe alınabilecek tanımlama bilgileri maksimum sayısını belirten bir pozitif tamsayı. Varsayılan değer 1000'dir.|  
|`maxClockSkew`|A <xref:System.TimeSpan> iletişim kuran taraflar iki tarafın sistem saatleri arasındaki en büyük zaman farkı belirtir. Varsayılan değer "00: 05:00".<br /><br /> Bu değeri varsayılan değere ayarlandığında, alıcı kabul daha sonra 5 dakika ile ileti gönderme zaman zaman damgaları ile yukarı veya zamandan daha önce iletisi alındı. Gönderme zamanı test geçmeyin iletileri reddedilir. Bu ayar ile birlikte kullanılan `replayWindow` özniteliği.|  
|`maxPendingSessions`|Hizmetin desteklediği güvenlik oturumu bekleyen maksimum sayısını belirten pozitif bir tamsayı. Bu sınıra ulaşıldığında, tüm yeni istemciler SOAP hataları alırsınız. Varsayılan değer 1000'dir.|  
|`maxStatefulNegotiations`|Aynı anda etkin olabilen güvenlik anlaşmaları sayısını belirten pozitif bir tamsayı. Sınırı aşan anlaşma oturumları kuyruğa alınır ve sınırın altına bir alan kullanılabilir duruma geldiğinde tamamlanabilir. Varsayılan değer 1024'tür.|  
|`negotiationTimeout`|A <xref:System.TimeSpan> kanal tarafından kullanılan güvenlik ilkesinin ömrünü belirtir. Süre dolduğunda istemci için yeni bir güvenlik ilkesi ile kanal belirler. Varsayılan değer "00: 02:00".|  
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
 Güvenlik İlkesi hizmetin bir parçası olarak yayımlanmaz ve istemci bağlaması etkilemez çünkü yerel ayarlardır.  
  
 Aşağıdaki öznitelikleri `localServiceSecuritySettings` öğesi bir hizmet reddi (DOS) güvenlik saldırısı azaltılmasına yardımcı olabilir:  
  
-   `maxCachedCookies`: zaman sınırlı SecurityContextTokens, sunucu tarafından SPNEGO veya SSL anlaşması yaptıktan sonra önbelleğe alınan en fazla sayısını denetler.  
  
-   `issuedCookieLifetime`: SPNEGO veya SSL anlaşması aşağıdaki sunucu tarafından verilen SecurityContextTokens ömrünü denetler. Sunucu SecurityContextTokens bu süre boyunca önbelleğe alır.  
  
-   `maxPendingSessions`: sunucuda ancak herhangi bir uygulama iletisi işlendi için oluşturulan güvenli konuşma en fazla sayısını denetler. Bu kota, hizmetine güvenli konuşma oluşturma, böylelikle her istemci için durumunu korumak üzere bir hizmetin neden, ancak hiçbir zaman kullanarak istemcilerin önler.  
  
-   `inactivityTimeout`: en uzun süreyi denetimleri hizmet güvenli konuşma etkin bir uygulama iletisi üzerindeki almadan tutar. Bu kota, hizmetine güvenli konuşma oluşturma, böylelikle her istemci için durumunu korumak üzere bir hizmetin neden, ancak hiçbir zaman kullanarak istemcilerin önler.  
  
 Bir güvenli konuşma oturumu unutmayın hem `inactivityTimeout` ve `receiveTimeout` öznitelikleri bağlama üzerinde oturum zaman aşımı süresini etkiler. İki daha kısa zaman aşımları olduğunda belirler.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.LocalServiceSettings%2A>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)
- [Bağlamaları Genişletme](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Özel Bağlamalar](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [Nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Özel Bağlama Güvenliği](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
