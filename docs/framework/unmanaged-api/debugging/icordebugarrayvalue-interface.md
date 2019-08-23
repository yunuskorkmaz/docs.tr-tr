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
ms.openlocfilehash: 99bd3e9ae1faec1b71933681fadf4816b4789c98
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952217"
---
# <a name="icordebugarrayvalue-interface"></a>ICorDebugArrayValue Arabirimi

Tek boyutlu veya çok boyutlu bir diziyi temsil eden ICorDebugHeapValue öğesinin alt sınıfı.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetBaseIndicies Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getbaseindicies-method.md)|Dizideki her boyutun temel dizinini alır.|  
|[GetCount Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getcount-method.md)|Dizideki toplam öğe sayısını alır.|  
|[GetDimensions Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getdimensions-method.md)|Dizinin boyutlarını alır.|  
|[GetElement Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelement-method.md)|Dizide verilen öğeyi temsil eden bir değer alır.|  
|[GetElementAtPosition Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementatposition-method.md)|Diziyi sıfır tabanlı, tek boyutlu bir dizi olarak düşünerek belirtilen konumdaki öğeyi alır.|  
|[GetElementType Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementtype-method.md)|Dizideki öğelerin basit türünü alır.|  
|[GetRank Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getrank-method.md)|Dizideki boyut sayısını alır.|  
|[HasBaseIndicies Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-hasbaseindicies-method.md)|Dizinin temel dizinlere sahip olup olmadığını belirler.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugArrayValue`hem tek boyutlu hem çok boyutlu dizileri destekler.  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** CorDebug. IDL, CorDebug. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
