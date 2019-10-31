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
ms.openlocfilehash: 6f20fb2e9e026253fb02b47dfcd63cf655acc4ee
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131653"
---
# <a name="ireferenceappid-interface"></a>IReferenceAppId Arabirimi
Geçerli kapsamdaki uygulamanın benzersiz tanımlayıcısına yönelik bir başvuruyu temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|`IReferenceAppId::get_CodeBase`|Bu `IReferenceAppId`başvurduğu uygulamanın kod tanımlayıcısının dize gösterimine yönelik bir işaretçi alır.|  
|`IReferenceAppId::put_CodeBase`|Bu `IReferenceAppId`başvurduğu uygulamanın kod tanımlayıcısını ayarlar.|  
|`IReferenceAppId::EnumAppPath`|Bu `IReferenceAppId`üyelerini temsil eden `IReferenceIdentity` örneklerini içeren bir `IEnumReferenceIdentity` örneğine yönelik bir arabirim işaretçisi alır.|  
|`IReferenceAppId::get_SubscriptionId`|Bu `IReferenceAppId`abonelik için belirteç tanımlayıcısının dize gösterimine yönelik bir işaretçi alır.|  
|`IReferenceAppId::put_SubscriptionId`|Bu `IReferenceAppId` abonelik için belirteç tanımlayıcısını belirtilen dize değerine ayarlar.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Yalıtım. h  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Fusion Arabirimleri](fusion-interfaces.md)
- [IEnumReferenceIdentity Arabirimi](ienumreferenceidentity-interface.md)
- [IReferenceIdentity Arabirimi](ireferenceidentity-interface.md)
