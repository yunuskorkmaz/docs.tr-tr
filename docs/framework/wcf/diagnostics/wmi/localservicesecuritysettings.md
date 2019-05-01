---
title: LocalServiceSecuritySettings
ms.date: 03/30/2017
ms.assetid: 490aa0e5-5242-4f8d-b505-5ec6287633b4
ms.openlocfilehash: 15304630eb8a14e01d4815ddddc84cd32796fdcf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61963455"
---
# <a name="localservicesecuritysettings"></a>LocalServiceSecuritySettings
LocalServiceSecuritySettings  
  
## <a name="syntax"></a>Sözdizimi  
  
```csharp
class LocalServiceSecuritySettings  
{  
  boolean DetectReplays;  
  datetime InactivityTimeout;  
  datetime IssuedCookieLifetime;  
  sint32 MaxCachedCookies;  
  datetime MaxClockSkew;  
  sint32 MaxPendingSessions;  
  sint32 MaxStatefulNegotiations;  
  datetime NegotiationTimeout;  
  boolean ReconnectTransportOnFailure;  
  sint32 ReplayCacheSize;  
  datetime ReplayWindow;  
  datetime SessionKeyRenewalInterval;  
  datetime SessionKeyRolloverInterval;  
  datetime TimestampValidityDuration;  
};  
```  
  
## <a name="methods"></a>Yöntemler  
 LocalServiceSecuritySettings sınıf herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  
 LocalServiceSecuritySettings sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="detectreplays"></a>DetectReplays  
 Veri türü: Boole  
  
 Erişim türü: salt okunur  
  
 Kanal yeniden yürütme saldırıları algılandı ve otomatik olarak ele belirten bir Boole değeri.  
  
### <a name="inactivitytimeout"></a>InactivityTimeout  
 Veri türü: tarih/saat  
  
 Erişim türü: salt okunur  
  
 Hizmetin desteklediği güvenlik oturumu bekleyen maksimum sayısı.  
  
### <a name="issuedcookielifetime"></a>IssuedCookieLifetime  
 Veri türü: tarih/saat  
  
 Erişim türü: salt okunur  
  
 Tüm yeni güvenlik tanımlama bilgilerine verilen ömür süresini belirten bir TimeSpan.  
  
### <a name="maxcachedcookies"></a>MaxCachedCookies  
 Veri türü: SINT32  
  
 Erişim türü: salt okunur  
  
 Önbelleğe alınabilecek tanımlama bilgileri maksimum sayısı.  
  
### <a name="maxclockskew"></a>MaxClockSkew  
 Veri türü: tarih/saat  
  
 Erişim türü: salt okunur  
  
 İki iletişim kuran tarafların sistem saatleri arasındaki en uzun süre farkını belirten bir TimeSpan.  
  
### <a name="maxpendingsessions"></a>MaxPendingSessions  
 Veri türü: SINT32  
  
 Erişim türü: salt okunur  
  
 Bekleyen hizmet bağlantıları maksimum sayısı.  
  
### <a name="maxstatefulnegotiations"></a>MaxStatefulNegotiations  
 Veri türü: SINT32  
  
 Erişim türü: salt okunur  
  
 Aynı anda etkin olabilen güvenlik anlaşmaları sayısını.  
  
### <a name="negotiationtimeout"></a>NegotiationTimeout  
 Veri türü: tarih/saat  
  
 Erişim türü: salt okunur  
  
 Sunucu ve istemci arasındaki güvenlik anlaşması aşaması için süre üst sınırını belirten bir TimeSpan.  
  
### <a name="reconnecttransportonfailure"></a>ReconnectTransportOnFailure  
 Veri türü: Boole  
  
 Erişim türü: salt okunur  
  
 WS-Reliable Mesajlaşma kullanan bağlantı aktarım hatasından sonra yeniden bağlanmaya olup olmadığını belirten bir Boole değeri.  
  
### <a name="replaycachesize"></a>ReplayCacheSize  
 Veri türü: SINT32  
  
 Erişim türü: salt okunur  
  
 Yeniden yürütme algılaması için önbelleğe alınan nonce sayısını.  
  
### <a name="replaywindow"></a>ReplayWindow  
 Veri türü: tarih/saat  
  
 Erişim türü: salt okunur  
  
 Tek tek ileti nonce öğelerinin geçerli kalacağı süreyi belirten bir TimeSpan.  
  
### <a name="sessionkeyrenewalinterval"></a>SessionKeyRenewalInterval  
 Veri türü: tarih/saat  
  
 Erişim türü: salt okunur  
  
 Sonra ve Başlatıcı anahtarı için güvenlik oturumu yeniler süreyi belirten bir TimeSpan.  
  
### <a name="sessionkeyrolloverinterval"></a>SessionKeyRolloverInterval  
 Veri türü: tarih/saat  
  
 Erişim türü: salt okunur  
  
 Zaman aralığını belirten bir TimeSpan anahtar yenilemesi sırasında önceki oturum anahtarının gelen iletileri geçerli değil.  
  
### <a name="timestampvalidityduration"></a>TimestampValidityDuration  
 Veri türü: tarih/saat  
  
 Erişim türü: salt okunur  
  
 Zaman damgası geçerli olduğu süreyi belirten bir TimeSpan.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilmiş Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlı root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
