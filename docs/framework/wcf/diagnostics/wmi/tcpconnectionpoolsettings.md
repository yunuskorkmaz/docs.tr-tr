---
title: TcpConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 19acfba3-c057-4dbc-bac7-8674d7844d83
ms.openlocfilehash: de00cac851e4c6d0fd6df16f3a01b65bb5f43415
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294683"
---
# <a name="tcpconnectionpoolsettings"></a>TcpConnectionPoolSettings

TcpConnectionPoolSettings  
  
## <a name="syntax"></a>Syntax  
  
```csharp
class TcpConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a>Yöntemler  

 TcpConnectionPoolSettings sınıfı herhangi bir yöntem tanımlamaz.  
  
## <a name="properties"></a>Özellikler  

 TcpConnectionPoolSettings sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="groupname"></a>Adýdýr  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Bağlama öğesi tarafından kullanılan bağlantı havuzunun grup adı.  
  
### <a name="idletimeout"></a>Timeout  

 Veri türü: DateTime  
  
 Erişim türü: salt okunurdur  
  
 Bağlantı kesilmeden önce bağlantının boşta kalabileceği en uzun süre.  
  
### <a name="leasetimeout"></a>LeaseTimeout  

 Veri türü: DateTime  
  
 Erişim türü: salt okunurdur  
  
 Zaman aşımından önce kira işleminin tamamlanacağı en uzun süre.  
  
### <a name="maxoutboundconnectionsperendpoint"></a>MaxOutboundConnectionsPerEndpoint  

 Veri türü: Sint32  
  
 Erişim türü: salt okunurdur  
  
 Her bitiş noktası için giden bağlantı üst sınırı.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|ServiceModel. mof içinde bildirilmiştir.|  
|---------|-----------------------------------|  
|Ad Alanı|Root\ServiceModel içinde tanımlı|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
