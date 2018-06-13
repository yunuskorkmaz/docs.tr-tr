---
title: TcpTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 33bbc1e5-44e4-4ee3-b7b5-801dc78956e4
ms.openlocfilehash: e64f689923d95546c8cecdf47c247faf79242ebf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485838"
---
# <a name="tcptransportbindingelement"></a>TcpTransportBindingElement
TcpTransportBindingElement  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
class TcpTransportBindingElement : ConnectionOrientedTransportBindingElement  
{  
  TcpConnectionPoolSettings ConnectionPoolSettings;  
  sint32 ListenBacklog;  
  boolean PortSharingEnabled;  
  boolean TeredoEnabled;  
};  
```  
  
## <a name="methods"></a>Yöntemler  
 TcpTransportBindingElement sınıfı herhangi bir yöntem tanımlamıyor.  
  
## <a name="properties"></a>Özellikler  
 TcpTransportBindingElement sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="connectionpoolsettings"></a>Tcptransport  
 Veri türü: TcpConnectionPoolSettings  
  
 Erişim türüne: salt okunur  
  
 Bağlantı havuzu ayarları.  
  
### <a name="listenbacklog"></a>listenBacklog  
 Veri türü: SINT32  
  
 Erişim türüne: salt okunur  
  
 Bekleyen sıraya alınan bağlantı isteklerini maksimum sayısı.  
  
### <a name="portsharingenabled"></a>portSharingEnabled  
 Veri türü: boolean  
  
 Erişim türüne: salt okunur  
  
 TCP bağlantı noktası paylaşma Bu bağlantı için etkin olup olmadığını belirten bir Boole değeri.  
  
### <a name="teredoenabled"></a>teredoEnabled  
 Veri türü: boolean  
  
 Erişim türüne: salt okunur  
  
 Teredo (güvenlik duvarının arkasındaki adresleme istemciler için bir teknoloji) etkin olup olmadığını belirten bir Boole değeri.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilen Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlanan root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
