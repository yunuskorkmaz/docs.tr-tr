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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 48364c2bcfa50476ac5f9f00f87c17f97dc14017
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
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
