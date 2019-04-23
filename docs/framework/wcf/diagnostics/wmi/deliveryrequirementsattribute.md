---
title: DeliveryRequirementsAttribute
ms.date: 03/30/2017
ms.assetid: 40c5435c-a325-4cf8-9dd0-d6e24b4a56a3
ms.openlocfilehash: c81e4b27969d879a70806082f48879cbf1b32ccc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59979218"
---
# <a name="deliveryrequirementsattribute"></a>DeliveryRequirementsAttribute
DeliveryRequirementsAttribute  
  
## <a name="syntax"></a>Sözdizimi  
  
```csharp
class DeliveryRequirementsAttribute : Behavior  
{  
  string QueuedDeliveryRequirements;  
  boolean RequireOrderedDelivery;  
  string TargetContract;  
};  
```  
  
## <a name="methods"></a>Yöntemler  
 DeliveryRequirementsAttribute sınıf herhangi bir yöntemi tanımlamaz.  
  
## <a name="properties"></a>Özellikler  
 DeliveryRequirementsAttribute sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="queueddeliveryrequirements"></a>NotAllowed  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Bir hizmet için bağlama sözleşmeleri destekleyip desteklemediğini belirtir.  
  
### <a name="requireordereddelivery"></a>RequireOrderedDelivery  
 Veri türü: Boole  
  
 Erişim türü: salt okunur  
  
 Bağlama sıralı iletileri destekleyip desteklemediğini belirtir.  
  
### <a name="targetcontract"></a>TargetContract  
 Veri türü: dize  
  
 Erişim türü: salt okunur  
  
 Geçerli sözleşme.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilmiş Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlı root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.DeliveryRequirementsAttribute>
