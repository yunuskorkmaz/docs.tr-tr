---
title: OneWayBindingElement
ms.date: 03/30/2017
ms.assetid: 5c7e17c3-39b9-4214-ae08-9e6141734305
ms.openlocfilehash: 016ff823eb2c84a9f54c0763edadef1224e31517
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62040059"
---
# <a name="onewaybindingelement"></a>OneWayBindingElement
OneWayBindingElement  
  
## <a name="syntax"></a>Sözdizimi  
  
```csharp
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## <a name="methods"></a>Yöntemler  
 OneWayBindingElement sınıf herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  
 OneWayBindingElement sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="channelpoolsettings"></a>ChannelPoolSettings  
 Veri türü: ChannelPoolSettings  
  
 Erişim türü: salt okunur  
  
 Kanal havuzu ayarlarını.  
  
### <a name="maxacceptedchannels"></a>MaxAcceptedChannels  
 Veri türü: SINT32  
  
 Erişim türü: salt okunur  
  
 Kabul edilen kanallar maksimum sayısı.  
  
### <a name="packetroutable"></a>PacketRoutable  
 Veri türü: Boole  
  
 Erişim türü: salt okunur  
  
 Paket yönlendirilebilir olup olmadığını belirten bir değer.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilmiş Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlı root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.OneWayBindingElement>
