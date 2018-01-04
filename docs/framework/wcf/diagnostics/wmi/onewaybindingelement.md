---
title: OneWayBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5c7e17c3-39b9-4214-ae08-9e6141734305
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 47de8c2449c46b12b8d10ac2a5269a18d1454f41
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="onewaybindingelement"></a>OneWayBindingElement
OneWayBindingElement  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## <a name="methods"></a>Yöntemler  
 OneWayBindingElement sınıfı herhangi bir yöntem tanımlamıyor.  
  
## <a name="properties"></a>Özellikler  
 OneWayBindingElement sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="channelpoolsettings"></a>ChannelPoolSettings  
 Veri türü: ChannelPoolSettings  
  
 Erişim türüne: salt okunur  
  
 Kanal havuzu ayarları.  
  
### <a name="maxacceptedchannels"></a>MaxAcceptedChannels  
 Veri türü: SINT32  
  
 Erişim türüne: salt okunur  
  
 Kabul edilen kanal sayısı.  
  
### <a name="packetroutable"></a>PacketRoutable  
 Veri türü: boolean  
  
 Erişim türüne: salt okunur  
  
 Paket yönlendirilebilir olup olmadığını belirten bir değer.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilen Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlanan root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>
