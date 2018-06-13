---
title: PeerTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 40bf6be2-8087-4cb3-a66c-408d53eb9269
ms.openlocfilehash: 68e6a25e4e3f47c556363e2fd5aa8d3bb9946449
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485651"
---
# <a name="peertransportbindingelement"></a>PeerTransportBindingElement
PeerTransportBindingElement  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
class PeerTransportBindingElement : TransportBindingElement  
{  
  string ListenIPAddress;  
  sint32 Port;  
  PeerSecuritySettings Security;  
};  
```  
  
## <a name="methods"></a>Yöntemler  
 Duyduğunuz arabirimi belirtin sınıfı herhangi bir yöntem tanımlamıyor.  
  
## <a name="properties"></a>Özellikler  
 Duyduğunuz arabirimi belirtin sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="listenipaddress"></a>ListenIpAddress  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Eş düğüm için iletileri dinlediği IP adresi.  
  
### <a name="port"></a>Bağlantı Noktası  
 Veri türü: SINT32  
  
 Erişim türüne: salt okunur  
  
 Ağ arabirimi, bu kanal iletileri bağlama işlemleri eş bağlantı noktası.  
  
### <a name="security"></a>Güvenlik  
 Veri türü: PeerSecuritySettings  
  
 Erişim türüne: salt okunur  
  
 Eş taşıma güvenlik ayarları.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilen Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlanan root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
