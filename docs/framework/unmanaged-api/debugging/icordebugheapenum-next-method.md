---
title: ICorDebugHeapEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugHeapEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapEnum::Next
helpviewer_keywords:
- ICorDebugHeapEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugHeapEnum interface [.NET Framework debugging]
ms.assetid: 2221fd06-9e27-4113-972e-2530db8c3594
topic_type:
- apiref
ms.openlocfilehash: 1beb69bfaad9acb9c269ad8becb81bea64edb6a2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138466"
---
# <a name="icordebugheapenumnext-method"></a>ICorDebugHeapEnum::Next Yöntemi
Yönetilen yığında nesneler hakkında bilgi içeren, belirtilen [cor_heapobject](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) örnek sayısını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_HEAPOBJECT  objects[],   
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 celt  
 'ndaki Alınacak nesne sayısı.  
  
 nesneleri  
 dışı Her biri yönetilen yığında bir nesne hakkında bilgi sağlayan bir [cor_heapobject](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) nesnesine işaret eden işaretçiler dizisi.  
  
 Pceltfettiz  
 dışı Gerçekten `objects`döndürülen [cor_heapobject](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) nesne sayısına yönelik bir işaretçi. Bu değer, `celt` 1 ise `null` olabilir.  
  
## <a name="remarks"></a>Açıklamalar  
 `COR_HEAPOBJECT.type` alanı, iç içe geçmiş bir başvuru sayılı COM arabiriminin tanımlayıcısıdır. Bu başvuru, `ICorDebugHeapEnum::Next`çağıranı tarafından yayınlanmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugHeapEnum Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
