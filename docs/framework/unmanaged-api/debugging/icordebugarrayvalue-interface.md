---
title: Icordebugarrayvalue Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue interface
helpviewer_keywords:
- ICorDebugArrayValue interface [.NET Framework debugging]
ms.assetid: dc437751-7093-44e2-bfdc-191d9ce3c192
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a96f2b21e524f03ea3290be268244eaceeb5c7f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugarrayvalue-interface1"></a>Icordebugarrayvalue Interface1
Tek boyutlu veya çok boyutlu bir array temsil eden Icordebugheapvalue sınıfıdır.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetBaseIndicies Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getbaseindicies-method.md)|Dizideki her boyut temel dizinini alır.|  
|[GetCount Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getcount-method.md)|Dizideki öğeler toplam sayısını alır.|  
|[GetDimensions Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getdimensions-method.md)|Dizi boyutları alır.|  
|[GetElement Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelement-method.md)|Dizideki verilen öğe temsil eden bir değer alır.|  
|[GetElementAtPosition Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementatposition-method.md)|Verilen konumunda dizinin sıfır tabanlı, tek boyutlu bir dizi olarak davranma öğeyi alır.|  
|[GetElementType Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementtype-method.md)|Dizideki öğeleri basit türünü alır.|  
|[GetRank Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getrank-method.md)|Dizideki boyut sayısını alır.|  
|[HasBaseIndicies Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-hasbaseindicies-method.md)|Dizi temel dizinleri olup olmadığını belirler.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugArrayValue` tek boyutlu ve çok boyutlu diziler destekler.  
  
> [!NOTE]
>  Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
