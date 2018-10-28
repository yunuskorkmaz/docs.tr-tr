---
title: TransportBindingElement
ms.date: 03/30/2017
ms.assetid: 54ecfbee-53c0-410c-a7fa-a98f2e40c545
ms.openlocfilehash: 79d8b1f4a5127ca36eb57954cff6ee6a97e55e41
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50182664"
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Channels.TransportBindingElement>
