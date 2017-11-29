---
title: "Kanal sınıfı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9fae2ca-209c-4341-a0f5-6b79d1a67776
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1df634a61cce695fca74fdfe53beea6c0f83d082
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="channel-class"></a>Kanal sınıfı
Kanal  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
class Channel  
{  
  string LocalAddress;  
  Endpoint ref;  
  string RemoteAddress;  
  string SessionId;  
  string Type;  
};  
```  
  
## <a name="methods"></a>Yöntemler  
 Kanal sınıfı herhangi bir yöntem tanımlamıyor.  
  
## <a name="properties"></a>Özellikler  
 Kanal sınıfı aşağıdaki özelliklere sahiptir.  
  
### <a name="localaddress"></a>LocalAddress  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Kanalı yerel uç nokta.  
  
### <a name="ref"></a>ref  
 Veri türü: uç noktası  
  
 Erişim türüne: salt okunur  
  
 Uç nokta kanal başvuru bağlanır.  
  
### <a name="remoteaddress"></a>RemoteAddress  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Kanal ile ilişkilendirilen uzak adres.  
  
### <a name="sessionid"></a>SessionId  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Geçerli oturum kimliği, varsa.  
  
### <a name="type"></a>Tür  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Kanal türü.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilen Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlanan root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Channels.ChannelBase>
