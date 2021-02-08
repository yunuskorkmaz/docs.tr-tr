---
description: 'Daha fazla bilgi edinin: NamedPipeConnectionPoolSettings'
title: NamedPipeConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 079bccb8-54b5-4436-a43d-5567763f72ce
ms.openlocfilehash: 8d724c7a24f62a8d48797125528eb8a194ece660
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803119"
---
# <a name="namedpipeconnectionpoolsettings"></a>NamedPipeConnectionPoolSettings

NamedPipeConnectionPoolSettings  
  
## <a name="syntax"></a>Syntax  
  
```csharp
class NamedPipeConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a>Yöntemler  

 NamedPipeConnectionPoolSettings sınıfı herhangi bir yöntem tanımlamaz.  
  
## <a name="properties"></a>Özellikler  

 NamedPipeConnectionPoolSettings sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="groupname"></a>Adýdýr  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Bağlama öğesi tarafından kullanılan bağlantı havuzunun grup adı.  
  
### <a name="idletimeout"></a>Timeout  

 Veri türü: DateTime  
  
 Erişim türü: salt okunurdur  
  
 Bağlantı kesilmeden önce bağlantının boşta kalabileceği en uzun süre.  
  
### <a name="maxoutboundconnectionsperendpoint"></a>MaxOutboundConnectionsPerEndpoint  

 Veri türü: Sint32  
  
 Erişim türü: salt okunurdur  
  
 İstemcideki her bir uç nokta için giden bağlantı sayısı üst sınırı.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|ServiceModel. mof içinde bildirilmiştir.|  
|---------|-----------------------------------|  
|Ad Alanı|Root\ServiceModel içinde tanımlı|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
