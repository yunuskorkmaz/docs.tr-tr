---
title: TransportBindingElement
ms.date: 03/30/2017
ms.assetid: 54ecfbee-53c0-410c-a7fa-a98f2e40c545
ms.openlocfilehash: 45bfcd069391156bc85cc4c26f2b172770197a9e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96234849"
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
