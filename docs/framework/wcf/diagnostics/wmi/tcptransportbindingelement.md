---
title: TcpTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 33bbc1e5-44e4-4ee3-b7b5-801dc78956e4
ms.openlocfilehash: 0d5dc5c9b9bf2313d18c9fadb1a2adb87c1b11b1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54610792"
---
# <a name="tcptransportbindingelement"></a>TcpTransportBindingElement
TcpTransportBindingElement  
  
## <a name="syntax"></a>Sözdizimi  
  
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
 TcpTransportBindingElement sınıf herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  
 TcpTransportBindingElement sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="connectionpoolsettings"></a>Tcptransport  
 Veri türü: TcpConnectionPoolSettings  
  
 Erişim türü: salt okunur  
  
 Bağlantı havuzu ayarları.  
  
### <a name="listenbacklog"></a>listenBacklog  
 Veri türü: SINT32  
  
 Erişim türü: salt okunur  
  
 Bekleyen sıraya alınan bağlantı isteklerinin sayısı.  
  
### <a name="portsharingenabled"></a>portSharingEnabled  
 Veri türü: Boole  
  
 Erişim türü: salt okunur  
  
 Bu bağlantı için TCP bağlantı noktası paylaşımının etkin olup olmadığını belirten bir Boole değeri.  
  
### <a name="teredoenabled"></a>teredoEnabled  
 Veri türü: Boole  
  
 Erişim türü: salt okunur  
  
 Teredo (güvenlik duvarının arkasındaki istemcilere için bir teknoloji) etkin olup olmadığını belirten bir Boole değeri.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilmiş Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlı root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
