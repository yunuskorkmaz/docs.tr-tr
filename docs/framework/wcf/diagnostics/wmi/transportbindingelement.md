---
title: TransportBindingElement
ms.date: 03/30/2017
ms.assetid: 54ecfbee-53c0-410c-a7fa-a98f2e40c545
ms.openlocfilehash: 303e5523befb68c65bc50ee3933af58897929363
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54668463"
---
# <a name="transportbindingelement"></a>TransportBindingElement
TransportBindingElement  
  
## <a name="syntax"></a>Sözdizimi  
  
```csharp
class TransportBindingElement : BindingElement  
{  
  boolean ManualAddressing;  
  sint64 MaxBufferPoolSize;  
  sint64 MaxReceivedMessageSize;  
  string Scheme;  
};  
```  
  
## <a name="methods"></a>Yöntemler  
 TransportBindingElement sınıf herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  
 TransportBindingElement sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="manualaddressing"></a>manualAddressing  
 Veri türü: Boole  
  
 Erişim türü: salt okunur  
  
 Kullanıcının ileti adresleme denetimini ele geçirmesine isteyip istemediğini belirten bir Boole değeri.  
  
### <a name="maxbufferpoolsize"></a>maxBufferPoolSize  
 Veri türü: sint64  
  
 Erişim türü: salt okunur  
  
 Bağlama için en fazla arabellek havuzu boyutu.  
  
### <a name="maxreceivedmessagesize"></a>maxReceivedMessageSize  
 Veri türü: sint64  
  
 Erişim türü: salt okunur  
  
 Bu bağlama tarafından işlenen bir ileti için en büyük boyutu.  
  
### <a name="scheme"></a>Düzen  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Taşıma için kullanılacak URI düzeni.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilmiş Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlı root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Channels.TransportBindingElement>
