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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 172f7df4f028c1ddc0f5565e95291e857ee6fa1d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
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
