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
ms.openlocfilehash: 9aa7173d81d84d9080d90b0890769ffeaee6a738
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728621"
---
# <a name="ireferenceappid-interface"></a>IReferenceAppId Arabirimi

Geçerli kapsamdaki uygulamanın benzersiz tanımlayıcısına yönelik bir başvuruyu temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|Bunun başvurduğu uygulamanın kod tanımlayıcısının dize gösterimine yönelik bir işaretçi alır `IReferenceAppId` .|  
|`IReferenceAppId::put_CodeBase`|Bunun başvurduğu uygulamanın kod tanımlayıcısını ayarlar `IReferenceAppId` .|  
|`IReferenceAppId::EnumAppPath`|`IEnumReferenceIdentity` `IReferenceIdentity` Bu öğenin üyelerini temsil eden örnekleri içeren bir örneğe bir arabirim işaretçisi alır `IReferenceAppId` .|  
|`IReferenceAppId::get_SubscriptionId`|Bu abonelik için belirteç tanımlayıcısının dize gösterimine yönelik bir işaretçi alır `IReferenceAppId` .|  
|`IReferenceAppId::put_SubscriptionId`|Bu abonelik için belirteç tanımlayıcısını `IReferenceAppId` belirtilen dize değerine ayarlar.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Yalıtım. h  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Fusion Arabirimleri](fusion-interfaces.md)
- [IEnumReferenceIdentity Arabirimi](ienumreferenceidentity-interface.md)
- [IReferenceIdentity Arabirimi](ireferenceidentity-interface.md)
