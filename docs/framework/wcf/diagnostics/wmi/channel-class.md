---
title: Kanal sınıfı
ms.date: 03/30/2017
ms.assetid: d9fae2ca-209c-4341-a0f5-6b79d1a67776
ms.openlocfilehash: 3fbf398cca7ae9adbbecb9439bf3cbd32eb03969
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54668398"
---
# <a name="channel-class"></a>Kanal sınıfı
Kanal  
  
## <a name="syntax"></a>Sözdizimi  
  
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
 Kanal sınıfı herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  
 Kanal sınıfı aşağıdaki özelliklere sahiptir.  
  
### <a name="localaddress"></a>LocalAddress  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Kanal için yerel uç nokta.  
  
### <a name="ref"></a>ref  
 Veri türü: Uç Noktası  
  
 Erişim türü: salt okunur  
  
 Bir başvuru kanal uç noktasına bağlanır.  
  
### <a name="remoteaddress"></a>RemoteAddress  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Kanal ile ilişkilendirilen uzak adres.  
  
### <a name="sessionid"></a>SessionId  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Geçerli oturum kimliği, varsa.  
  
### <a name="type"></a>Tür  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Kanal türü.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilmiş Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlı root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Channels.ChannelBase>
