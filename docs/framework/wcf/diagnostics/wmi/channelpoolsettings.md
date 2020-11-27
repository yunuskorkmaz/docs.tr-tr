---
title: ChannelPoolSettings
ms.date: 03/30/2017
ms.assetid: d3f475bd-f780-4bbe-b291-339387322964
ms.openlocfilehash: 3dcc1f3b27d93d5641a4bb2d8082aa3fa88882dc
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96274224"
---
# <a name="channelpoolsettings"></a>ChannelPoolSettings

ChannelPoolSettings  
  
## <a name="syntax"></a>Syntax  
  
```csharp
class ChannelPoolSettings  
{  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundChannelsPerEndpoint;  
};  
```  
  
## <a name="methods"></a>Yöntemler  

 ChannelPoolSettings sınıfı herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  

 ChannelPoolSettings sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="idletimeout"></a>Timeout  

 Veri türü: DateTime  
  
 Erişim türü: salt okunurdur  
  
 Bağlantı kesilmeden önce bağlantının boşta kalabileceği en uzun süre.  
  
### <a name="leasetimeout"></a>LeaseTimeout  

 Veri türü: DateTime  
  
 Erişim türü: salt okunurdur  
  
 Zaman aşımından önce bir kira işleminin tamamlanacağı en uzun süre.  
  
### <a name="maxoutboundchannelsperendpoint"></a>MaxOutboundChannelsPerEndpoint  

 Veri türü: Sint32  
  
 Erişim türü: salt okunurdur  
  
 Her bitiş noktası için giden kanal sayısı üst sınırı.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|ServiceModel. mof içinde bildirilmiştir.|  
|---------|-----------------------------------|  
|Ad Alanı|Root\ServiceModel içinde tanımlı|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
