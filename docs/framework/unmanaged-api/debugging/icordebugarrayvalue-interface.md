---
title: ICorDebugArrayValue Arabirimi
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
ms.openlocfilehash: 67fd1a9174b04e42b53f2b866a1dfdd504362aa9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645623"
---
# <a name="icordebugarrayvalue-interface"></a>ICorDebugArrayValue Arabirimi

Bir tek boyutlu veya çok boyutlu diziyi temsil eden Icordebugheapvalue öğesinin.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetBaseIndicies Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getbaseindicies-method.md)|Dizideki her boyutun temel dizini alır.|  
|[GetCount Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getcount-method.md)|Dizideki öğelerin toplam sayısını alır.|  
|[GetDimensions Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getdimensions-method.md)|Dizinin boyut sayısını alır.|  
|[GetElement Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelement-method.md)|Belirtilen öğe dizideki temsil eden bir değer alır.|  
|[GetElementAtPosition Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementatposition-method.md)|Verilen konumunda dizinin sıfır tabanlı, tek boyutlu bir dizi olarak davranılması öğesini alır.|  
|[GetElementType Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementtype-method.md)|Dizideki öğelerin basit türünü alır.|  
|[GetRank Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getrank-method.md)|Dizinin boyut sayısını alır.|  
|[HasBaseIndicies Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-hasbaseindicies-method.md)|Bir dizi temel dizinleri olup olmadığını belirler.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugArrayValue` tek boyutlu ve çok boyutlu diziler destekler.  
  
> [!NOTE]
>  Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
