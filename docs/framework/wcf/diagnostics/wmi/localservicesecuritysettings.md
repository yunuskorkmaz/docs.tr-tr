---
description: ': LocalServiceSecuritySettings hakkında daha fazla bilgi edinin'
title: LocalServiceSecuritySettings
ms.date: 03/30/2017
ms.assetid: 490aa0e5-5242-4f8d-b505-5ec6287633b4
ms.openlocfilehash: f7220e8253c6ab218414c1be7ed90e5d593b4692
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743947"
---
# <a name="localservicesecuritysettings"></a>LocalServiceSecuritySettings

LocalServiceSecuritySettings  
  
## <a name="syntax"></a>Syntax  
  
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

 LocalServiceSecuritySettings sınıfı herhangi bir yöntem tanımlamaz.  
  
## <a name="properties"></a>Özellikler  

 LocalServiceSecuritySettings sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="detectreplays"></a>DetectReplays  

 Veri türü: Boole  
  
 Erişim türü: salt okunurdur  
  
 Kanala karşı yeniden yürütme saldırılarının algılanıp algılanmayacağını belirten bir Boole değeri.  
  
### <a name="inactivitytimeout"></a>InactivityTimeout  

 Veri türü: DateTime  
  
 Erişim türü: salt okunurdur  
  
 Hizmetin desteklediği en fazla beklemedeki güvenlik oturumu sayısı.  
  
### <a name="issuedcookielifetime"></a>Issuedtarif ıelifetime  

 Veri türü: DateTime  
  
 Erişim türü: salt okunurdur  
  
 Tüm yeni güvenlik tanımlama bilgilerine verilen yaşam süresini belirten bir TimeSpan.  
  
### <a name="maxcachedcookies"></a>MaxCachedCookies  

 Veri türü: Sint32  
  
 Erişim türü: salt okunurdur  
  
 Önbelleğe alınabilecek tanımlama bilgisi sayısı üst sınırı.  
  
### <a name="maxclockskew"></a>MaxClockSkew  

 Veri türü: DateTime  
  
 Erişim türü: salt okunurdur  
  
 İki iletişim kuran tarafın sistem saatleri arasındaki en uzun süre farkını belirten bir TimeSpan.  
  
### <a name="maxpendingsessions"></a>MaxPendingSessions  

 Veri türü: Sint32  
  
 Erişim türü: salt okunurdur  
  
 Hizmette bekleyen en fazla bağlantı sayısı.  
  
### <a name="maxstatefulnegotiations"></a>Maxstatefulanlaşmaları  

 Veri türü: Sint32  
  
 Erişim türü: salt okunurdur  
  
 Aynı anda etkin olabilen güvenlik anlaşmaları sayısı.  
  
### <a name="negotiationtimeout"></a>NegotiationTimeout  

 Veri türü: DateTime  
  
 Erişim türü: salt okunurdur  
  
 Sunucu ve istemci arasındaki güvenlik anlaşması aşaması için en uzun süreyi belirten bir TimeSpan.  
  
### <a name="reconnecttransportonfailure"></a>ReconnectTransportOnFailure  

 Veri türü: Boole  
  
 Erişim türü: salt okunurdur  
  
 WS-Reliable mesajlaşma kullanan bağlantıların aktarım arızasından sonra yeniden bağlanmaya çalışıp çalışmadığını belirten bir Boole değeri.  
  
### <a name="replaycachesize"></a>ReplayCacheSize  

 Veri türü: Sint32  
  
 Erişim türü: salt okunurdur  
  
 Yeniden yürütme algılaması için kullanılan önbelleğe alınmış nonce sayısı.  
  
### <a name="replaywindow"></a>ReplayWindow  

 Veri türü: DateTime  
  
 Erişim türü: salt okunurdur  
  
 Tek tek ileti nonce öğelerinin geçerli olduğu süreyi belirten bir TimeSpan.  
  
### <a name="sessionkeyrenewalinterval"></a>SessionKeyRenewalInterval  

 Veri türü: DateTime  
  
 Erişim türü: salt okunurdur  
  
 Başlatanın güvenlik oturumu için anahtarı yenileme süresini belirten bir TimeSpan.  
  
### <a name="sessionkeyrolloverinterval"></a>SessionKeyRolloverInterval  

 Veri türü: DateTime  
  
 Erişim türü: salt okunurdur  
  
 Anahtar yenileme sırasında gelen iletilerde önceki oturum anahtarının geçerli olduğu zaman aralığını belirten bir TimeSpan.  
  
### <a name="timestampvalidityduration"></a>TimestampValidityDuration  

 Veri türü: DateTime  
  
 Erişim türü: salt okunurdur  
  
 Zaman damgasının geçerli olduğu süreyi belirten bir TimeSpan.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|ServiceModel. mof içinde bildirilmiştir.|  
|---------|-----------------------------------|  
|Ad Alanı|Root\ServiceModel içinde tanımlı|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
