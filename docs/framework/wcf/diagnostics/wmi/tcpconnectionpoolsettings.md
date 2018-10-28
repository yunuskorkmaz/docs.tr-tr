---
title: TcpConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 19acfba3-c057-4dbc-bac7-8674d7844d83
ms.openlocfilehash: f9e1c043579f632f16a7cf36bf34c2467a743e47
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50189569"
---
# <a name="tcpconnectionpoolsettings"></a>TcpConnectionPoolSettings
TcpConnectionPoolSettings  
  
## <a name="syntax"></a>Sözdizimi  
  
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
 TcpConnectionPoolSettings sınıf herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  
 TcpConnectionPoolSettings sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="groupname"></a>GroupName  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Bağlama öğesi tarafından kullanılan bağlantı havuzunu grup adı.  
  
### <a name="idletimeout"></a>IdleTimeout  
 Veri türü: tarih/saat  
  
 Erişim türü: salt okunur  
  
 Bağlantı kesilmeden önce boşta kalabileceği en uzun süre.  
  
### <a name="leasetimeout"></a>LeaseTimeout  
 Veri türü: tarih/saat  
  
 Erişim türü: salt okunur  
  
 Kira işlemi zaman aşımına uğramadan önce tamamlanması için en uzun süre.  
  
### <a name="maxoutboundconnectionsperendpoint"></a>MaxOutboundConnectionsPerEndpoint  
 Veri türü: SINT32  
  
 Erişim türü: salt okunur  
  
 Her bir uç noktası için en fazla giden bağlantı.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilmiş Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlı root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
