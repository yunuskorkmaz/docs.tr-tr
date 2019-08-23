---
title: <localServiceSettings> öğesi
ms.date: 03/30/2017
ms.assetid: 0658549c-3f65-46dd-8c5c-9895441ed734
ms.openlocfilehash: 36fcc9454a5762a4a375cc7f6eaee1c4cf0580e2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931725"
---
# <a name="localservicesettings-element"></a>\<localServiceSettings > öğesi
Bu bağlama için yerel bir hizmetin güvenlik ayarlarını belirtir.  
  
 \<system.serviceModel>  
\<bağlama >  
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
|`detectReplays`|Kanala karşı yeniden yürütme saldırılarının algılanıp algılanmayacağını belirten bir Boole değeri. Varsayılan, `false` değeridir.|  
|`inactivityTimeout`|Kanalın zaman <xref:System.TimeSpan> aşımına uğramadan önce bekleyeceği eylemsizlik süresini belirten bir pozitif sayı. Varsayılan değer "01:00:00" dır.|  
|`issuedCookieLifeTime`|Tüm <xref:System.TimeSpan> yeni güvenlik tanımlama bilgilerine verilen yaşam süresini belirten bir. Yaşam sürelerini aşan tanımlama bilgileri geri dönüştürülür ve yeniden anlaşma olması gerekir. Varsayılan değer "10:00:00" dır.|  
|`maxCachedCookies`|Önbelleğe alınabilecek tanımlama bilgisi sayısı üst sınırını belirten pozitif bir tamsayı. Varsayılan değer 1000 ' dir.|  
|`maxClockSkew`|İki <xref:System.TimeSpan> iletişim kuran tarafın sistem saatleri arasındaki en uzun süre farkını belirten bir. Varsayılan değer "00:05:00" dır.<br /><br /> Bu değer varsayılan değere ayarlandığında, alıcı gönderme zamanı zaman damgalarına sahip iletileri, daha sonra veya iletinin alındığı zamandan 5 dakikaya kadar kabul eder. Gönderme zamanı testini geçemediği iletiler reddedilir. Bu ayar, `replayWindow` özniteliğiyle birlikte kullanılır.|  
|`maxPendingSessions`|Hizmetin desteklediği en fazla beklemedeki güvenlik oturumu sayısını belirten pozitif bir tamsayı. Bu sınıra ulaşıldığında, tüm yeni istemciler SOAP hataları alır. Varsayılan değer 1000'dir.|  
|`maxStatefulNegotiations`|Aynı anda etkin olabilen güvenlik anlaşmaları sayısını belirten pozitif bir tamsayı. Sınırın üzerinde olan anlaşma oturumları sıraya alınır ve yalnızca sınırın altındaki bir boşluk kullanılabilir hale geldiğinde tamamlanabilir. Varsayılan değer 1024 ' dir.|  
|`negotiationTimeout`|Kanal <xref:System.TimeSpan> tarafından kullanılan güvenlik ilkesinin ömrünü belirten bir. Süre sona erdiğinde, kanal yeni bir güvenlik ilkesi için istemcisiyle yeniden anlaşmaya varılır. Varsayılan değer "00:02:00" dır.|  
|`reconnectTransportOnFailure`|WS-güvenilir mesajlaşma kullanan bağlantıların, aktarım hatalarından sonra yeniden bağlanmaya çalışıp çalışmadığını belirten bir Boole değeri. Varsayılan `true`olarak, sınırsız yeniden bağlanma girişimlerinin denendiği anlamına gelir. Bu zaman aşımı, kanalın yeniden bağlanamayan bir özel durum oluşturmasına neden olan etkinlik dışı zaman aşımı nedeniyle bozulur.|  
|`replayCacheSize`|Yeniden yürütme algılaması için kullanılan önbelleğe alınmış nonce sayısını belirten pozitif bir tamsayı. Bu sınır aşılırsa, en eski nonce kaldırılır ve yeni ileti için yeni bir nonce oluşturulur. Varsayılan değer 500000 ' dir.|  
|`replayWindow`|Tek <xref:System.TimeSpan> tek ileti nonce öğelerinin geçerli olduğu süreyi belirten bir.<br /><br /> Bu süreden sonra, daha önce gönderilen ile aynı nonce ile gönderilen bir ileti kabul edilmez. Bu öznitelik, `maxClockSkew` yeniden yürütme saldırılarını engellemek için özniteliğiyle birlikte kullanılır. Bir saldırgan, yeniden yürütme penceresinin süresi dolduktan sonra bir iletiyi yeniden oynamıştır. Bununla birlikte, bu ileti, gönderme zamanı `maxClockSkew` zaman damgalarına sahip iletileri, daha sonra veya daha önceki bir süre içinde ileti alındığı zamandan reddeden test başarısız olur.|  
|`sessionKeyRenewalInterval`|Bu <xref:System.TimeSpan> , başlatanın güvenlik oturumu anahtarını yenileyecek süreyi belirten bir. Varsayılan değer "10:00:00" dır.|  
|`sessionKeyRolloverInterval`|Bir <xref:System.TimeSpan> anahtar yenilemesi sırasında önceki oturum anahtarının gelen iletilerde geçerli olduğu zaman aralığını belirten bir. Varsayılan değer "00:05:00" dır.<br /><br /> Anahtar yenileme sırasında, istemci ve sunucu her zaman en geçerli kullanılabilir anahtarı kullanarak ileti göndermelidir. Her iki taraf da, geçiş süresi sona erene kadar önceki oturum anahtarıyla güvenliği sağlanmış gelen iletileri kabul eder.|  
|`timestampValidityDuration`|Zaman damgasının <xref:System.TimeSpan> geçerli olduğu süreyi belirten pozitif bir değer. Varsayılan değer "00:15:00" dır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Güvenlik >](security-of-custombinding.md)|Özel bağlama için güvenlik seçeneklerini belirtir.|  
|[\<Securebir Bootstrap >](secureconversationbootstrap.md)|Güvenli konuşma hizmeti başlatmak için kullanılan varsayılan değerleri belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ayarlar, hizmetin güvenlik ilkesinin bir parçası olarak yayımlanmadığı ve istemcinin bağlamasını etkilemediği için yereldir.  
  
 `localServiceSecuritySettings` Öğesinin aşağıdaki öznitelikleri, hizmet reddi (DOS) güvenlik saldırısını azaltmaya yardımcı olabilir:  
  
- `maxCachedCookies`: SPNEGO veya SSL anlaşması yapıldıktan sonra sunucu tarafından önbelleğe alınan en fazla zaman sınırlı SecurityContextTokens sayısını denetler.  
  
- `issuedCookieLifetime`: SPNEGO veya SSL anlaşmasını izleyen sunucu tarafından verilen SecurityContextTokens ömrünü denetler. Sunucu bu süre için SecurityContextTokens önbelleğe alır.  
  
- `maxPendingSessions`: sunucuda oluşturulan ancak hiçbir uygulama iletisi işlenen en fazla güvenli konuşma sayısını denetler. Bu kota, istemcilerin hizmette güvenli konuşmalar kurmasını engeller ve bu sayede hizmetin her bir istemci için durumu korumasına ve hiçbir zaman bunları kullanmamasına neden olur.  
  
- `inactivityTimeout`: hizmetin, üzerinde bir uygulama iletisi almadan güvenli bir konuşmayı canlı tutacağı en uzun süreyi denetler. Bu kota, istemcilerin hizmette güvenli konuşmalar kurmasını engeller ve bu sayede hizmetin her bir istemci için durumu korumasına ve hiçbir zaman bunları kullanmamasına neden olur.  
  
 Güvenli bir konuşma oturumunda, hem hem de `inactivityTimeout` `receiveTimeout` bağlamadaki özniteliklerin oturum zaman aşımını etkilediğini unutmayın. İki, zaman aşımlarının ne zaman gerçekleşeceğini belirler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.LocalServiceSettings%2A>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Bağlamalar](../../../wcf/bindings.md)
- [Bağlamaları Genişletme](../../../wcf/extending/extending-bindings.md)
- [Özel Bağlamalar](../../../wcf/extending/custom-bindings.md)
- [\<customBinding >](custombinding.md)
- [Nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Özel Bağlama Güvenliği](../../../wcf/samples/custom-binding-security.md)
