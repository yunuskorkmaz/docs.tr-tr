---
description: 'Daha fazla bilgi edinin: OneWayBindingElement'
title: OneWayBindingElement
ms.date: 03/30/2017
ms.assetid: 5c7e17c3-39b9-4214-ae08-9e6141734305
ms.openlocfilehash: 9c2ccc301bd854c7b85fcc53551ed6def329a8fa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803093"
---
# <a name="onewaybindingelement"></a>OneWayBindingElement

OneWayBindingElement  
  
## <a name="syntax"></a>Syntax  
  
```csharp
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## <a name="methods"></a>Yöntemler  

 OneWayBindingElement sınıfı herhangi bir yöntem tanımlamaz.  
  
## <a name="properties"></a>Özellikler  

 OneWayBindingElement sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="channelpoolsettings"></a>ChannelPoolSettings  

 Veri türü: ChannelPoolSettings  
  
 Erişim türü: salt okunurdur  
  
 Kanal havuzu ayarları.  
  
### <a name="maxacceptedchannels"></a>MaxAcceptedChannels  

 Veri türü: Sint32  
  
 Erişim türü: salt okunurdur  
  
 Kabul edilen en fazla kanal sayısı.  
  
### <a name="packetroutable"></a>Packetyönlendirilebilir  

 Veri türü: Boole  
  
 Erişim türü: salt okunurdur  
  
 Paketin yönlendirilebilir olup olmadığını gösteren bir değer.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|ServiceModel. mof içinde bildirilmiştir.|  
|---------|-----------------------------------|  
|Ad Alanı|Root\ServiceModel içinde tanımlı|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.OneWayBindingElement>
