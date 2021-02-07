---
description: 'Daha fazla bilgi edinin: TcpTransportBindingElement'
title: TcpTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 33bbc1e5-44e4-4ee3-b7b5-801dc78956e4
ms.openlocfilehash: b52bb2eb4b40648808459f76e068a6f72f9476a4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715151"
---
# <a name="tcptransportbindingelement"></a>TcpTransportBindingElement

TcpTransportBindingElement  
  
## <a name="syntax"></a>Syntax  
  
```csharp
class TcpTransportBindingElement : ConnectionOrientedTransportBindingElement  
{  
  TcpConnectionPoolSettings ConnectionPoolSettings;  
  sint32 ListenBacklog;  
  boolean PortSharingEnabled;  
  boolean TeredoEnabled;  
};  
```  
  
## <a name="methods"></a>Yöntemler  

 TcpTransportBindingElement Class herhangi bir yöntem tanımlamaz.  
  
## <a name="properties"></a>Özellikler  

 TcpTransportBindingElement class aşağıdaki özelliklere sahiptir:  
  
### <a name="connectionpoolsettings"></a>NamedPipeTransport  

 Veri türü: TcpConnectionPoolSettings  
  
 Erişim türü: salt okunurdur  
  
 Bağlantı havuzu ayarları.  
  
### <a name="listenbacklog"></a>ListenBacklog  

 Veri türü: Sint32  
  
 Erişim türü: salt okunurdur  
  
 Beklemede olabilecek en fazla sıraya alınmış bağlantı isteği sayısı.  
  
### <a name="portsharingenabled"></a>PortSharingEnabled  

 Veri türü: Boole  
  
 Erişim türü: salt okunurdur  
  
 Bu bağlantı için TCP bağlantı noktası paylaşımının etkin olup olmadığını belirten bir Boolean değer.  
  
### <a name="teredoenabled"></a>TeredoEnabled  

 Veri türü: Boole  
  
 Erişim türü: salt okunurdur  
  
 Teredo 'Nun (güvenlik duvarlarının arkasındaki istemcileri adresleme teknolojisinin) etkin olup olmadığını belirten bir Boole değeri.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|ServiceModel. mof içinde bildirilmiştir.|  
|---------|-----------------------------------|  
|Ad Alanı|Root\ServiceModel içinde tanımlı|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
