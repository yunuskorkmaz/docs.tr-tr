---
title: IReferenceAppId Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IReferenceAppId
api_location: fusion.dll
api_type: COM
f1_keywords: IReferenceAppId
helpviewer_keywords: IReferenceAppId interface [.NET Framework fusion]
ms.assetid: 8eb9e565-f358-43ce-900e-a8f8a5aa6cfb
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cac4ef63292f1bd342bb94799872b002fdcdf945
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ireferenceappid-interface"></a>IReferenceAppId Arabirimi
Geçerli kapsamdaki uygulama için benzersiz tanımlayıcı başvuru temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|Bu tarafından başvurulan uygulaması için kod tanımlayıcı bir dize gösterimini bir işaretçi alır `IReferenceAppId`.|  
|`IReferenceAppId::put_CodeBase`|Bu tarafından başvurulan uygulama için kod tanımlayıcı ayarlar `IReferenceAppId`.|  
|`IReferenceAppId::EnumAppPath`|Bir arabirim işaretçisi alır bir `IEnumReferenceIdentity` örneğini içeren `IReferenceIdentity` bu üyeleri temsil örnekleri `IReferenceAppId`.|  
|`IReferenceAppId::get_SubscriptionId`|Bu abonelik için bir işaretçi belirteç tanımlayıcı bir dize gösterimini alır `IReferenceAppId`.|  
|`IReferenceAppId::put_SubscriptionId`|Bir abonelik için belirteç tanımlayıcı için ayarlar `IReferenceAppId` belirtilen dize değeri.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Isolation.h  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Fusion arabirimleri](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [Ienumreferenceıdentity arabirimi](../../../../docs/framework/unmanaged-api/fusion/ienumreferenceidentity-interface.md)  
 [Ireferenceıdentity arabirimi](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
