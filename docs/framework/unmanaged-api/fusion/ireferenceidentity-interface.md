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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4708fa173725e4c91a13f5b92cdbb1fdf8a8a4d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432109"
---
# <a name="ireferenceidentity-interface"></a>IReferenceIdentity Arabirimi
Bir kod nesnesinin benzersiz imza başvuru temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|`IReferenceIdentity::Clone`|Arabirim işaretçisi yeni bir alır `IReferenceIdentity` için aynı olan örneği `IReferenceIdentity`, belirtilen öznitelik değişikliklerini dışında.|  
|`IReferenceIdentity::EnumAttributes`|Bir arabirim işaretçisi alır bir `IEnumIDENTITY_ATTRIBUTE` bu ile ilişkili öznitelikleri içeren örneği `IReferenceIdentity`.|  
|`IReferenceIdentity::GetAttribute`|Belirtilen ada sahip belirtilen ad alanında özniteliğinin değerini alır.|  
|`IReferenceIdentity::SetAttribute`|Belirtilen ad ve belirtilen değeri belirtilen ada sahip öznitelik ayarlar.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Isolation.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Fusion Arabirimleri](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [IEnumIDENTITY_ATTRIBUTE Arabirimi](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md)
