---
title: PeerTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 40bf6be2-8087-4cb3-a66c-408d53eb9269
ms.openlocfilehash: 437ccc0446e3cc05596ab12b7908177b7f78e431
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54670660"
---
# <a name="peertransportbindingelement"></a>PeerTransportBindingElement
PeerTransportBindingElement  
  
## <a name="syntax"></a>Sözdizimi  
  
```csharp
class PeerTransportBindingElement : TransportBindingElement  
{  
  string ListenIPAddress;  
  sint32 Port;  
  PeerSecuritySettings Security;  
};  
```  
  
## <a name="methods"></a>Yöntemler  
 Duyduğunuz arabirimi belirtin sınıf herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  
 Duyduğunuz arabirimi belirtin sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="listenipaddress"></a>ListenIpAddress  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Eş düğüm iletileri için dinlediği IP adresi.  
  
### <a name="port"></a>Bağlantı Noktası  
 Veri türü: SINT32  
  
 Erişim türü: salt okunur  
  
 Bu kanal iletileri bağlama işlemleri eş ağ arabirim bağlantı noktası.  
  
### <a name="security"></a>Güvenlik  
 Veri türü: PeerSecuritySettings  
  
 Erişim türü: salt okunur  
  
 Eş taşıma güvenlik ayarları.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilmiş Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlı root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
