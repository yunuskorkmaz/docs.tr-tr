---
title: TcpTransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33bbc1e5-44e4-4ee3-b7b5-801dc78956e4
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4b9aa7e0d9eaba0181b17b44da1bf871c10af814
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
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
