---
title: IReferenceIdentity Arabirimi
ms.date: 03/30/2017
api_name:
- IReferenceIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IReferenceIdentity
helpviewer_keywords:
- IReferenceIdentity interface [.NET Framework fusion]
ms.assetid: 9180ac5a-7019-4716-9f83-8a91d157239a
topic_type:
- apiref
ms.openlocfilehash: 8f6a117d1e2fe76c271b0b014e6079370c8b4fe4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127061"
---
# <a name="ireferenceidentity-interface"></a>IReferenceIdentity Arabirimi
Bir kod nesnesinin benzersiz imzasına bir başvuruyu temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|`IReferenceIdentity::Clone`|Belirtilen öznitelik değişiklikleri dışında, bu `IReferenceIdentity`özdeş olan yeni bir `IReferenceIdentity` örneğine bir arabirim işaretçisi alır.|  
|`IReferenceIdentity::EnumAttributes`|Bu `IReferenceIdentity`ilişkili öznitelikleri içeren `IEnumIDENTITY_ATTRIBUTE` örneğine yönelik bir arabirim işaretçisi alır.|  
|`IReferenceIdentity::GetAttribute`|Belirtilen ad alanındaki özniteliğin değerini belirtilen adla alır.|  
|`IReferenceIdentity::SetAttribute`|Belirtilen ad alanına ve belirtilen ada sahip olan özniteliği belirtilen değere ayarlar.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Yalıtım. h  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Fusion Arabirimleri](fusion-interfaces.md)
- [IEnumIDENTITY_ATTRIBUTE Arabirimi](ienumidentity-attribute-interface.md)
