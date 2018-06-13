---
title: Kanal sınıfı
ms.date: 03/30/2017
ms.assetid: d9fae2ca-209c-4341-a0f5-6b79d1a67776
ms.openlocfilehash: 4b7c66560c0c136a258c527d8a681d491eb50aae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485833"
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
