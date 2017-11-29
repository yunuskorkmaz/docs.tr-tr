---
title: DeliveryRequirementsAttribute
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40c5435c-a325-4cf8-9dd0-d6e24b4a56a3
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 40bdc27337daae02795137fc3ac67575787018c1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="deliveryrequirementsattribute"></a>DeliveryRequirementsAttribute
DeliveryRequirementsAttribute  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
class DeliveryRequirementsAttribute : Behavior  
{  
  string QueuedDeliveryRequirements;  
  boolean RequireOrderedDelivery;  
  string TargetContract;  
};  
```  
  
## <a name="methods"></a>Yöntemler  
 DeliveryRequirementsAttribute sınıfı herhangi bir yöntem tanımlamıyor.  
  
## <a name="properties"></a>Özellikler  
 DeliveryRequirementsAttribute sınıfı aşağıdaki özelliklere sahiptir:  
  
### <a name="queueddeliveryrequirements"></a>QueuedDeliveryRequirements  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Bir hizmet için bağlama sözleşmeleri destekleyip desteklemediğini belirtir.  
  
### <a name="requireordereddelivery"></a>RequireOrderedDelivery  
 Veri türü: boolean  
  
 Erişim türüne: salt okunur  
  
 Bağlama sıralanan iletileri destekleyip desteklemediğini belirtir.  
  
### <a name="targetcontract"></a>TargetContract  
 Veri türü: dize  
  
 Erişim türüne: salt okunur  
  
 Geçerli olduğu sözleşme.  
  
## <a name="requirements"></a>Gereksinimler  
  
|MOF|Bildirilen Servicemodel.mof.|  
|---------|-----------------------------------|  
|Ad Alanı|İçinde tanımlanan root\ServiceModel|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.DeliveryRequirementsAttribute>
