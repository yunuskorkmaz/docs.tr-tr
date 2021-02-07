---
description: 'Daha fazla bilgi edinin: TransportBindingElement'
title: TransportBindingElement
ms.date: 03/30/2017
ms.assetid: 54ecfbee-53c0-410c-a7fa-a98f2e40c545
ms.openlocfilehash: de08feaf8abec3a0dfee97e92d68d5223cd0de44
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757117"
---
# <a name="transportbindingelement"></a>TransportBindingElement

TransportBindingElement  
  
## <a name="syntax"></a>Syntax  
  
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

 TransportBindingElement sınıfı herhangi bir yöntem tanımlamaz.  
  
## <a name="properties"></a>Özellikler  

 TransportBindingElement sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="manualaddressing"></a>ManualAddressing  

 Veri türü: Boole  
  
 Erişim türü: salt okunurdur  
  
 Kullanıcının ileti adreslemesinin denetimini almak isteyip istemediğini belirten bir Boole değeri.  
  
### <a name="maxbufferpoolsize"></a>MaxBufferPoolSize  

 Veri türü: sint64  
  
 Erişim türü: salt okunurdur  
  
 Bağlama için en büyük arabellek havuzu boyutu.  
  
### <a name="maxreceivedmessagesize"></a>Değerini  

 Veri türü: sint64  
  
 Erişim türü: salt okunurdur  
  
 Bu bağlama tarafından işlenen bir ileti için boyut üst sınırı.  
  
### <a name="scheme"></a>Düzen  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Taşımanın URI şeması.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|ServiceModel. mof içinde bildirilmiştir.|  
|---------|-----------------------------------|  
|Ad Alanı|Root\ServiceModel içinde tanımlı|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.TransportBindingElement>
