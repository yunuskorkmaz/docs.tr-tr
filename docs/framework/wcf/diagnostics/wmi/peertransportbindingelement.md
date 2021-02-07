---
description: 'Daha fazla bilgi edinin: PeerTransportBindingElement'
title: PeerTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 40bf6be2-8087-4cb3-a66c-408d53eb9269
ms.openlocfilehash: b1ca8020f51a5f9b121f7d238d82b9971d13cdd4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757338"
---
# <a name="peertransportbindingelement"></a>PeerTransportBindingElement

PeerTransportBindingElement  
  
## <a name="syntax"></a>Syntax  
  
```csharp
class PeerTransportBindingElement : TransportBindingElement  
{  
  string ListenIPAddress;  
  sint32 Port;  
  PeerSecuritySettings Security;  
};  
```  
  
## <a name="methods"></a>Yöntemler  

 PeerTransportBindingElement Class herhangi bir yöntem tanımlamaz.  
  
## <a name="properties"></a>Özellikler  

 PeerTransportBindingElement class aşağıdaki özelliklere sahiptir:  
  
### <a name="listenipaddress"></a>ListenIPAddress  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Eş düğümün iletileri dinlediği IP adresi.  
  
### <a name="port"></a>Bağlantı noktası  

 Veri türü: Sint32  
  
 Erişim türü: salt okunurdur  
  
 Bu bağlamanın eş kanal iletilerini işlediği ağ arabirimi bağlantı noktası.  
  
### <a name="security"></a>Güvenlik  

 Veri türü: PeerSecuritySettings  
  
 Erişim türü: salt okunurdur  
  
 Eş taşıma güvenlik ayarları.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|ServiceModel. mof içinde bildirilmiştir.|  
|---------|-----------------------------------|  
|Ad Alanı|Root\ServiceModel içinde tanımlı|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
