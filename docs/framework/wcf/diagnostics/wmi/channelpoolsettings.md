---
title: ChannelPoolSettings
ms.date: 03/30/2017
ms.assetid: d3f475bd-f780-4bbe-b291-339387322964
ms.openlocfilehash: 4a3e45140765f99f4a30b77fc9d02b167601b50b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54591490"
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
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
