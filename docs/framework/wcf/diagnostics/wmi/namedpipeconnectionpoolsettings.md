---
title: NamedPipeConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 079bccb8-54b5-4436-a43d-5567763f72ce
ms.openlocfilehash: 3dddfa878e3cb5bd89fb76009d0dba530debb297
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54725083"
---
# <a name="namedpipeconnectionpoolsettings"></a>NamedPipeConnectionPoolSettings
NamedPipeConnectionPoolSettings  
  
## <a name="syntax"></a>Sözdizimi  
  
```csharp
class NamedPipeConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a>Yöntemler  
 NamedPipeConnectionPoolSettings sınıf herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  
 NamedPipeConnectionPoolSettings sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="groupname"></a>GroupName  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Bağlama öğesi tarafından kullanılan bağlantı havuzunu grup adı.  
  
### <a name="idletimeout"></a>IdleTimeout  
 Veri türü: tarih/saat  
  
 Erişim türü: salt okunur  
  
 Bağlantı kesilmeden önce boşta kalabileceği en uzun süre.  
  
### <a name="maxoutboundconnectionsperendpoint"></a>MaxOutboundConnectionsPerEndpoint  
 Veri türü: SINT32  
  
 Erişim türü: salt okunur  
  
 Giden bağlantılar için istemci üzerindeki her bir uç nokta sayısı.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilmiş Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlı root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
