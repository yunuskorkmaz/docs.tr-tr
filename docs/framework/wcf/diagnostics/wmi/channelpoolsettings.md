---
title: ChannelPoolSettings
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d3f475bd-f780-4bbe-b291-339387322964
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0a56616e97526b2d410d18d97dc1391c6fc32cc3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="channelpoolsettings"></a>ChannelPoolSettings
ChannelPoolSettings  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
class ChannelPoolSettings  
{  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundChannelsPerEndpoint;  
};  
```  
  
## <a name="methods"></a>Yöntemler  
 ChannelPoolSettings sınıfı herhangi bir yöntem tanımlamıyor.  
  
## <a name="properties"></a>Özellikler  
 ChannelPoolSettings sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="idletimeout"></a>IdleTimeout  
 Veri türü: datetime  
  
 Erişim türüne: salt okunur  
  
 Bağlantı kesilmeden önce boşta kalabileceği en uzun süre.  
  
### <a name="leasetimeout"></a>LeaseTimeout  
 Veri türü: datetime  
  
 Erişim türüne: salt okunur  
  
 Zaman aşımından önce tamamlamak bir kira işlemi için en uzun süre.  
  
### <a name="maxoutboundchannelsperendpoint"></a>MaxOutboundChannelsPerEndpoint  
 Veri türü: SINT32  
  
 Erişim türüne: salt okunur  
  
 Her uç noktası için giden kanal sayısı.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilen Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlanan root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Channels.ChannelPoolSettings>
