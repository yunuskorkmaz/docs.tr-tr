---
description: 'Daha fazla bilgi edinin: ReliableSessionBindingElement'
title: ReliableSessionBindingElement
ms.date: 03/30/2017
ms.assetid: effda125-b8d3-4de6-8c0e-f59f5ea8f6eb
ms.openlocfilehash: 582fd62a8751a31c2834b7d81219a237c9887236
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743869"
---
# <a name="reliablesessionbindingelement"></a>ReliableSessionBindingElement

ReliableSessionBindingElement  
  
## <a name="syntax"></a>Syntax  
  
```csharp
class ReliableSessionBindingElement : BindingElement  
{  
  datetime AcknowledgementInterval;  
  boolean FlowControlEnabled;  
  datetime InactivityTimeout;  
  sint32 MaxPendingChannels;  
  sint32 MaxRetryCount;  
  sint32 MaxTransferWindowSize;  
  boolean Ordered;  
  integer ReliableMessagingVersion;  
};  
```  
  
## <a name="methods"></a>Yöntemler  

 ReliableSessionBindingElement sınıfı herhangi bir yöntem tanımlamaz.  
  
## <a name="properties"></a>Özellikler  

 ReliableSessionBindingElement sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="acknowledgementinterval"></a>Bildiren Gementınterval  

 Veri türü: DateTime  
  
 Erişim türü: salt okunurdur  
  
 Bir hedefin, fabrika tarafından oluşturulan güvenilir kanallarda ileti kaynağına bir onay göndermeden önce beklediği zaman aralığı.  
  
### <a name="flowcontrolenabled"></a>FlowControlEnabled  

 Veri türü: Boole  
  
 Erişim türü: salt okunurdur  
  
 Akış denetiminin etkinleştirilip etkinleştirilmediğini belirten bir Boolean değer.  
  
### <a name="inactivitytimeout"></a>InactivityTimeout  

 Veri türü: DateTime  
  
 Erişim türü: salt okunurdur  
  
 Kanalın, diğer iletişim tarafına ait diğer tarafın kanaldan önce herhangi bir ileti gönderemediğinden izin verilen en uzun süreyi belirtir.  
  
### <a name="maxpendingchannels"></a>MaxPendingChannels  

 Veri türü: Sint32  
  
 Erişim türü: salt okunurdur  
  
 Dinleyicide kabul edilmesini bekleyebilen kanal sayısı üst sınırı.  
  
### <a name="maxretrycount"></a>MaxRetryCount  

 Veri türü: Sint32  
  
 Erişim türü: salt okunurdur  
  
 Güvenilir bir kanalın, kendisi için onay almadığı bir iletiyi kendi temel kanalına çağırarak, en fazla kaç kez yeniden aktarmak için deneme sayısı `Send` .  
  
### <a name="maxtransferwindowsize"></a>MaxTransferWindowSize  

 Veri türü: Sint32  
  
 Erişim türü: salt okunurdur  
  
 Güvenilir oturum için en büyük aktarım penceresi boyutu.  
  
### <a name="ordered"></a>Sipariş edildi  

 Veri türü: Boole  
  
 Erişim türü: salt okunurdur  
  
 İletilerin gönderildikleri sırada gelmesi garanti edilip edilmeyeceğini belirten bir Boole değeri.  
  
### <a name="reliablemessagingversion"></a>Belirten ReliableMessagingVersion  

 Veri türü: tamsayı  
  
 Erişim türü: salt okunurdur  
  
 Güvenilir oturumda kullanılan WS-ReliableMessaging protokol sürümünü belirten bir tamsayı.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|ServiceModel. mof içinde bildirilmiştir.|  
|---------|-----------------------------------|  
|Ad Alanı|Root\ServiceModel içinde tanımlı|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>
