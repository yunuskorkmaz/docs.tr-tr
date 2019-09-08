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
ms.openlocfilehash: 522ed80f161f114af25e1fa7ad041c8238073d6f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796375"
---
# <a name="ireferenceappid-interface"></a>IReferenceAppId Arabirimi
Geçerli kapsamdaki uygulamanın benzersiz tanımlayıcısına yönelik bir başvuruyu temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|Bunun `IReferenceAppId`başvurduğu uygulamanın kod tanımlayıcısının dize gösterimine yönelik bir işaretçi alır.|  
|`IReferenceAppId::put_CodeBase`|Bunun `IReferenceAppId`başvurduğu uygulamanın kod tanımlayıcısını ayarlar.|  
|`IReferenceAppId::EnumAppPath`|Bu `IReferenceIdentity` `IEnumReferenceIdentity` öğenin`IReferenceAppId`üyelerini temsil eden örnekleri içeren bir örneğe bir arabirim işaretçisi alır.|  
|`IReferenceAppId::get_SubscriptionId`|Bu `IReferenceAppId`abonelik için belirteç tanımlayıcısının dize gösterimine yönelik bir işaretçi alır.|  
|`IReferenceAppId::put_SubscriptionId`|Bu `IReferenceAppId` abonelik için belirteç tanımlayıcısını belirtilen dize değerine ayarlar.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi** Yalıtım. h  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Fusion Arabirimleri](fusion-interfaces.md)
- [IEnumReferenceIdentity Arabirimi](ienumreferenceidentity-interface.md)
- [IReferenceIdentity Arabirimi](ireferenceidentity-interface.md)
