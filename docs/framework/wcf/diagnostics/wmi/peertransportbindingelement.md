---
title: PeerTransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40bf6be2-8087-4cb3-a66c-408d53eb9269
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 25893b1f3cf6cf20ae674bade5090a70c5f381a2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
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
