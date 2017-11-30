---
title: Icordebugarrayvalue Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugArrayValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugArrayValue interface
helpviewer_keywords: ICorDebugArrayValue interface [.NET Framework debugging]
ms.assetid: dc437751-7093-44e2-bfdc-191d9ce3c192
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 13e226ccdcd6becc98d524c429b5cadae8d19c3e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugarrayvalue-interface1"></a>Icordebugarrayvalue Interface1
Tek boyutlu veya çok boyutlu bir array temsil eden Icordebugheapvalue sınıfıdır.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Getbaseındicies yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getbaseindicies-method.md)|Dizideki her boyut temel dizinini alır.|  
|[GetCount yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getcount-method.md)|Dizideki öğeler toplam sayısını alır.|  
|[GetDimensions yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getdimensions-method.md)|Dizi boyutları alır.|  
|[GetElement yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelement-method.md)|Dizideki verilen öğe temsil eden bir değer alır.|  
|[GetElementAtPosition yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementatposition-method.md)|Verilen konumunda dizinin sıfır tabanlı, tek boyutlu bir dizi olarak davranma öğeyi alır.|  
|[GetElementType yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementtype-method.md)|Dizideki öğeleri basit türünü alır.|  
|[GetRank yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getrank-method.md)|Dizideki boyut sayısını alır.|  
|[Hasbaseındicies yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-hasbaseindicies-method.md)|Dizi temel dizinleri olup olmadığını belirler.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugArrayValue`tek boyutlu ve çok boyutlu diziler destekler.  
  
> [!NOTE]
>  Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklama arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
