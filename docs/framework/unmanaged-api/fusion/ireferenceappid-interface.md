---
title: IReferenceAppId Arabirimi
ms.date: 03/30/2017
api_name:
- IReferenceAppId
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IReferenceAppId
helpviewer_keywords:
- IReferenceAppId interface [.NET Framework fusion]
ms.assetid: 8eb9e565-f358-43ce-900e-a8f8a5aa6cfb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2484fa61c03b95e7cbdb452b92a68a2049701374
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
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
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Fusion Arabirimleri](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [IEnumReferenceIdentity Arabirimi](../../../../docs/framework/unmanaged-api/fusion/ienumreferenceidentity-interface.md)  
 [IReferenceIdentity Arabirimi](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
