---
title: LocalServiceSecuritySettings
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 490aa0e5-5242-4f8d-b505-5ec6287633b4
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: f4cc5d0676ef397f67bd9d16b2b19c6f3ee2d57e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="localservicesecuritysettings"></a>LocalServiceSecuritySettings
LocalServiceSecuritySettings  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
 LocalServiceSecuritySettings sınıfı herhangi bir yöntem tanımlamıyor.  
  
## <a name="properties"></a>Özellikler  
 LocalServiceSecuritySettings sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="detectreplays"></a>DetectReplays  
 Veri türü: boolean  
  
 Erişim türüne: salt okunur  
  
 Yeniden yürütme saldırılarına karşı kanal algılandı ve otomatik olarak ele olup olmadığını belirten bir Boole değeri.  
  
### <a name="inactivitytimeout"></a>InactivityTimeout  
 Veri türü: datetime  
  
 Erişim türüne: salt okunur  
  
 Hizmeti destekler güvenlik oturumları bekleyen maksimum sayısı.  
  
### <a name="issuedcookielifetime"></a>IssuedCookieLifetime  
 Veri türü: datetime  
  
 Erişim türüne: salt okunur  
  
 Tüm yeni güvenlik tanımlama bilgilerine verilen ömür süresini belirten bir TimeSpan.  
  
### <a name="maxcachedcookies"></a>MaxCachedCookies  
 Veri türü: SINT32  
  
 Erişim türüne: salt okunur  
  
 Önbelleğe alınacak tanımlama bilgisi maksimum sayısı.  
  
### <a name="maxclockskew"></a>MaxClockSkew  
 Veri türü: datetime  
  
 Erişim türüne: salt okunur  
  
 İki iletişim kuran tarafların sistem saatlerinin arasındaki en büyük zaman farkı belirten bir TimeSpan.  
  
### <a name="maxpendingsessions"></a>MaxPendingSessions  
 Veri türü: SINT32  
  
 Erişim türüne: salt okunur  
  
 Hizmet bağlantılarında bekleyen maksimum sayısı.  
  
### <a name="maxstatefulnegotiations"></a>MaxStatefulNegotiations  
 Veri türü: SINT32  
  
 Erişim türüne: salt okunur  
  
 Aynı anda etkin olabilen güvenlik anlaşmaları sayısı.  
  
### <a name="negotiationtimeout"></a>NegotiationTimeout  
 Veri türü: datetime  
  
 Erişim türüne: salt okunur  
  
 Sunucu ve istemci arasındaki güvenlik anlaşması aşaması için en fazla süreyi belirten bir TimeSpan.  
  
### <a name="reconnecttransportonfailure"></a>ReconnectTransportOnFailure  
 Veri türü: boolean  
  
 Erişim türüne: salt okunur  
  
 WS güvenilir Mesajlaşma kullanarak bağlantıları aktarım hataları sonra yeniden bağlanmayı denemek olup olmadığını belirten bir Boole değeri.  
  
### <a name="replaycachesize"></a>ReplayCacheSize  
 Veri türü: SINT32  
  
 Erişim türüne: salt okunur  
  
 Yeniden yürütme algılaması için önbelleğe alınan nonce sayısı.  
  
### <a name="replaywindow"></a>ReplayWindow  
 Veri türü: datetime  
  
 Erişim türüne: salt okunur  
  
 Tek ileti nonce öğelerinin geçerli olduğu süreyi belirten bir TimeSpan.  
  
### <a name="sessionkeyrenewalinterval"></a>SessionKeyRenewalInterval  
 Veri türü: datetime  
  
 Erişim türüne: salt okunur  
  
 Sonra ve Başlatıcı anahtarı için güvenlik oturumu yeniler süreyi belirten bir TimeSpan.  
  
### <a name="sessionkeyrolloverinterval"></a>SessionKeyRolloverInterval  
 Veri türü: datetime  
  
 Erişim türüne: salt okunur  
  
 Zaman aralığını belirten bir TimeSpan anahtar yenileme sırasında bir önceki oturum anahtarı gelen iletileri geçerli değil.  
  
### <a name="timestampvalidityduration"></a>TimestampValidityDuration  
 Veri türü: datetime  
  
 Erişim türüne: salt okunur  
  
 Zaman damgası geçerli olduğu süreyi belirten bir TimeSpan.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilen Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlanan root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
