---
title: DeliveryRequirementsAttribute
ms.date: 03/30/2017
ms.assetid: 40c5435c-a325-4cf8-9dd0-d6e24b4a56a3
ms.openlocfilehash: a70a4ba40b569acc7893b21d796194224dc4ee78
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96274055"
---
# <a name="deliveryrequirementsattribute"></a>DeliveryRequirementsAttribute

DeliveryRequirementsAttribute  
  
## <a name="syntax"></a>Syntax  
  
```csharp
class DeliveryRequirementsAttribute : Behavior  
{  
  string QueuedDeliveryRequirements;  
  boolean RequireOrderedDelivery;  
  string TargetContract;  
};  
```  
  
## <a name="methods"></a>Yöntemler  

 DeliveryRequirementsAttribute sınıfı herhangi bir yöntem tanımlamaz.  
  
## <a name="properties"></a>Özellikler  

 DeliveryRequirementsAttribute sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="queueddeliveryrequirements"></a>QueuedDeliveryRequirements  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Bir hizmet bağlamasının sözleşmeleri destekleyip desteklemediğini belirtir.  
  
### <a name="requireordereddelivery"></a>RequireOrderedDelivery  

 Veri türü: Boole  
  
 Erişim türü: salt okunurdur  
  
 Bağlamanın sıralanmış iletileri destekleyip desteklemediğini belirtir.  
  
### <a name="targetcontract"></a>TargetContract  

 Veri türü: dize  
  
 Erişim türü: salt okunurdur  
  
 Geçerli olduğu sözleşme.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|ServiceModel. mof içinde bildirilmiştir.|  
|---------|-----------------------------------|  
|Ad Alanı|Root\ServiceModel içinde tanımlı|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.DeliveryRequirementsAttribute>
