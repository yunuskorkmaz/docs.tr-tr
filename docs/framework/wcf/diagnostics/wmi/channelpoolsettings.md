---
title: ChannelPoolSettings
ms.date: 03/30/2017
ms.assetid: d3f475bd-f780-4bbe-b291-339387322964
ms.openlocfilehash: d763be92243768bce9fdaefcd3e3575effac464b
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50200489"
---
# <a name="channelpoolsettings"></a>ChannelPoolSettings
ChannelPoolSettings  
  
## <a name="syntax"></a>Sözdizimi  
  
```csharp
class ChannelPoolSettings  
{  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundChannelsPerEndpoint;  
};  
```  
  
## <a name="methods"></a>Yöntemler  
 ChannelPoolSettings sınıf herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  
 ChannelPoolSettings sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="idletimeout"></a>IdleTimeout  
 Veri türü: tarih/saat  
  
 Erişim türü: salt okunur  
  
 Bağlantı kesilmeden önce boşta kalabileceği en uzun süre.  
  
### <a name="leasetimeout"></a>LeaseTimeout  
 Veri türü: tarih/saat  
  
 Erişim türü: salt okunur  
  
 Bir kira işlemi zaman aşımına uğramadan önce tamamlanması için en uzun süre.  
  
### <a name="maxoutboundchannelsperendpoint"></a>MaxOutboundChannelsPerEndpoint  
 Veri türü: SINT32  
  
 Erişim türü: salt okunur  
  
 Giden kanallar için her uç nokta sayısı.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilmiş Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlı root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Channels.ChannelPoolSettings>
