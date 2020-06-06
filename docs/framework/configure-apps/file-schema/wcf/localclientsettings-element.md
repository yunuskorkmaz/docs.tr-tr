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
# <a name="localclientsettings-element"></a>\<localClientSettings> öğesi
Bu bağlama için yerel bir istemcinin güvenlik ayarlarını belirtir.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<localClientSettings>**  
  
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
|`cacheCookies`|Tanımlama bilgisi önbelleğe almanın etkin olup olmadığını belirten bir Boolean değer. Varsayılan değer: `false`.|  
|`cookieRenewalThresholdPercentage`|Yenilenebilir tanımlama bilgilerinin maksimum yüzdesini belirten bir tamsayı. Bu değer, ikisi de dahil olmak üzere 0 ile 100 arasında olmalıdır. Varsayılan değer 90 ' dir.|  
|`detectReplays`|Kanala karşı yeniden yürütme saldırılarının algılanıp algılanmayacağını belirten bir Boole değeri. Varsayılan değer: `false`.|  
|`maxClockSkew`|<xref:System.TimeSpan>İki iletişim kuran tarafın sistem saatleri arasındaki en uzun süre farkını belirten bir. Varsayılan değer "00:05:00" dır.<br /><br /> Bu değer varsayılan değere ayarlandığında, alıcı gönderme zamanı zaman damgalarına sahip iletileri, daha sonra veya iletinin alındığı zamandan 5 dakikaya kadar kabul eder. Gönderme zamanı testini geçemediği iletiler reddedilir. Bu ayar, özniteliğiyle birlikte kullanılır `replayWindow` .|  
|`maxCookieCachingTime`|<xref:System.TimeSpan>En fazla tanımlama bilgisi ömrünü belirten bir. Varsayılan değer "10675199.02:48:05.4775807" ' dir.|  
|`reconnectTransportOnFailure`|WS-güvenilir mesajlaşma kullanan bağlantıların, aktarım hatalarından sonra yeniden bağlanmaya çalışıp çalışmadığını belirten bir Boole değeri. Varsayılan olarak, `true` sınırsız yeniden bağlanma girişimlerinin denendiği anlamına gelir. Bu zaman aşımı, kanalın yeniden bağlanamayan bir özel durum oluşturmasına neden olan etkinlik dışı zaman aşımı nedeniyle bozulur.|  
|`replayCacheSize`|Yeniden yürütme algılaması için kullanılan önbelleğe alınmış nonce sayısını belirten pozitif bir tamsayı. Bu sınır aşılırsa, en eski nonce kaldırılır ve yeni ileti için yeni bir nonce oluşturulur. Varsayılan değer 500000 ' dir.|  
|`replayWindow`|<xref:System.TimeSpan>Tek tek ileti nonce öğelerinin geçerli olduğu süreyi belirten bir.<br /><br /> Bu süreden sonra, daha önce gönderilen ile aynı nonce ile gönderilen bir ileti kabul edilmez. Bu öznitelik, yeniden `maxClockSkew` yürütme saldırılarını engellemek için özniteliğiyle birlikte kullanılır. Bir saldırgan, yeniden yürütme penceresinin süresi dolduktan sonra bir iletiyi yeniden oynamıştır. Bununla birlikte, bu ileti, `maxClockSkew` gönderme zamanı zaman damgalarına sahip iletileri, daha sonra veya daha önceki bir süre içinde ileti alındığı zamandan reddeden test başarısız olur.|  
|`sessionKeyRenewalInterval`|<xref:System.TimeSpan>Bu, başlatanın güvenlik oturumu anahtarını yenileyecek süreyi belirten bir. Varsayılan değer "10:00:00" dır.|  
|`sessionKeyRolloverInterval`|Bir <xref:System.TimeSpan> anahtar yenilemesi sırasında önceki oturum anahtarının gelen iletilerde geçerli olduğu zaman aralığını belirten bir. Varsayılan değer "00:05:00" dır.<br /><br /> Anahtar yenileme sırasında, istemci ve sunucu her zaman en geçerli kullanılabilir anahtarı kullanarak ileti göndermelidir. Her iki taraf da, geçiş süresi sona erene kadar önceki oturum anahtarıyla güvenliği sağlanmış gelen iletileri kabul eder.|  
|`timestampValidityDuration`|<xref:System.TimeSpan>Zaman damgasının geçerli olduğu süreyi belirten pozitif bir değer. Varsayılan değer "00:15:00" dır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<security>](security-of-custombinding.md)|Özel bağlama için güvenlik seçeneklerini belirtir.|  
|[\<secureConversationBootstrap>](secureconversationbootstrap.md)|Güvenli konuşma hizmeti başlatmak için kullanılan varsayılan değerleri belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ayarlar, hizmetin güvenlik ilkesinden türetilmiş ayarların olmadığı anlamda yereldir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.LocalClientSettings%2A>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A>
- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Bağlamalar](../../../wcf/bindings.md)
- [Bağlamaları Genişletme](../../../wcf/extending/extending-bindings.md)
- [Özel Bağlamalar](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Özel Bağlama Güvenliği](../../../wcf/samples/custom-binding-security.md)
