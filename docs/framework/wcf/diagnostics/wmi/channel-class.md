---
description: 'Daha fazla bilgi edinin: Kanal sınıfı'
title: Kanal sınıfı
ms.date: 03/30/2017
ms.assetid: d9fae2ca-209c-4341-a0f5-6b79d1a67776
ms.openlocfilehash: dcc92f78f09e9a73a24134c6c0685949f46f38dd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757728"
---
# <a name="channel-class"></a>Kanal sınıfı

Kanal  
  
## <a name="syntax"></a>Syntax  
  
```csharp
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

 Kanal sınıfı herhangi bir yöntem tanımlamaz.  
  
## <a name="properties"></a>Özellikler  

 Kanal sınıfı aşağıdaki özelliklere sahiptir.  
  
### <a name="localaddress"></a>LocalAddress  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Kanal için Yerel uç nokta.  
  
### <a name="ref"></a>ref  

 Veri türü: uç nokta  
  
 Erişim türü: salt okunurdur  
  
 Kanalın bağlandığı uç noktaya başvuru.  
  
### <a name="remoteaddress"></a>RemoteAddress  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Kanalla ilişkilendirilen uzak adres.  
  
### <a name="sessionid"></a>SessionId  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Varsa, geçerli oturum kimliği.  
  
### <a name="type"></a>Tür  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Kanalın türü.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|ServiceModel. mof içinde bildirilmiştir.|  
|---------|-----------------------------------|  
|Ad Alanı|Root\ServiceModel içinde tanımlı|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.ChannelBase>
