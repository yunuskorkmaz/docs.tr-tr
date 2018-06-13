---
title: '&lt;localServiceSettings&gt; öğesi'
ms.date: 03/30/2017
ms.assetid: 0658549c-3f65-46dd-8c5c-9895441ed734
ms.openlocfilehash: 1257b151f75d05b610fe3463f8bef5f78d2b2fcd
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32751161"
---
# <a name="ltlocalservicesettingsgt-element"></a>&lt;localServiceSettings&gt; öğesi
Bu bağlama için yerel bir hizmet güvenlik ayarlarını belirtir.  
  
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
|`detectReplays`|Yeniden yürütme saldırılarına karşı kanal algılandı ve otomatik olarak ele olup olmadığını belirten bir Boole değeri. Varsayılan, `false` değeridir.|  
|`inactivityTimeout`|Bir pozitif <xref:System.TimeSpan> kanal bekleyeceği zaman aşımına uğramadan önce etkin olmama süresi belirtir. Varsayılan değer "01: 00:00".|  
|`issuedCookieLifeTime`|A <xref:System.TimeSpan> tüm yeni güvenlik tanımlama bilgilerine verilen ömür süresini belirtir. Kendi ömürleri aşan tanımlama bilgileri dönüştürülünceye ve yeniden anlaşma gerekir. Varsayılan değer "10: 00:00".|  
|`maxCachedCookies`|Önbelleğe alınacak tanımlama bilgisi üst sınırını belirtir pozitif bir tamsayı. Varsayılan değer 1000'dir.|  
|`maxClockSkew`|A <xref:System.TimeSpan> iki iletişim kuran tarafların sistem saatlerinin arasındaki en büyük zaman farkı belirtir. Varsayılan değer "00: 05:00".<br /><br /> Bu değer varsayılan olarak ayarlandığında, alıcı iletileri gönderme zamanı zaman damgaları ile yukarı daha sonra 5 dakika olarak kabul eder veya ileti zamandan daha önce alındı. Gönderme zamanı test geçmeyin iletiler reddedilir. Bu ayar ile birlikte kullanılan `replayWindow` özniteliği.|  
|`maxPendingSessions`|Bekleyen hizmet destekleyen güvenlik oturumları en fazla sayısını belirtir pozitif bir tamsayı. Bu sınıra ulaşıldığında, tüm yeni istemciler SOAP hataları alırsınız. Varsayılan değer 1000'dir.|  
|`maxStatefulNegotiations`|Aynı anda etkin olabilen güvenlik anlaşmaları sayısını belirtir pozitif bir tamsayı. Sınırı aşan anlaşma oturumlar kuyruğa alınır ve yalnızca sınırın altındaki bir alan kullanılabilir duruma geldiğinde tamamlanabilir. Varsayılan değer 1024'tür.|  
|`negotiationTimeout`|A <xref:System.TimeSpan> kanal tarafından kullanılan güvenlik ilkesi ömrü belirtir. Süresi dolduğunda, yeni bir güvenlik ilkesi için istemci ile kanal belirler. Varsayılan değer "00: 02:00".|  
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
 Güvenlik İlkesi hizmetinin bir parçası olarak yayımlanmayan ve istemcinin bağlama etkilemez çünkü yerel bir ayarlardır.  
  
 Aşağıdaki özniteliklerine `localServiceSecuritySettings` öğesi bir hizmet reddi (DOS) güvenlik saldırısı azaltmaya yardımcı olabilir:  
  
-   `maxCachedCookies`: SPNEGO veya SSL anlaşması yaptıktan sonra sunucu tarafından önbelleğe zaman sınırlı SecurityContextTokens en fazla sayısını denetler.  
  
-   `issuedCookieLifetime`: SPNEGO veya SSL anlaşması aşağıdaki sunucusu tarafından verilen SecurityContextTokens ömrü denetler. Sunucu SecurityContextTokens bu süre boyunca önbelleğe alır.  
  
-   `maxPendingSessions`: sunucuda ancak hiçbir uygulama ileti işlendikten için kurulmuş güvenli konuşmaları en fazla sayısını denetler. Bu kota istemcilerin konuşması güvenli konuşmaları oluşturma, böylelikle her istemci için durumunu korumak üzere hizmet yol, ancak hiçbir zaman kullanmadan önler.  
  
-   `inactivityTimeout`: en fazla süreyi denetimleri hizmet güvenli bir konuşma etkin bir uygulama iletisi üzerindeki almadan tutar olduğunu. Bu kota istemcilerin konuşması güvenli konuşmaları oluşturma, böylelikle her istemci için durumunu korumak üzere hizmet yol, ancak hiçbir zaman kullanmadan önler.  
  
 Güvenli Konuşmayla oturumunda unutmayın her ikisi de `inactivityTimeout` ve `receiveTimeout` bağlama özniteliklerinde oturum zaman aşımı süresini etkiler. İki daha kısa zaman aşımları olduğunda belirler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>  
 <xref:System.ServiceModel.Configuration.SecurityElementBase.LocalServiceSettings%2A>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A>  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Bağlamalar](../../../../../docs/framework/wcf/bindings.md)  
 [Bağlamaları Genişletme](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Özel Bağlamalar](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [Özel Bağlama Güvenliği](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
