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
ms.openlocfilehash: 2c84112984e9cb7dec2a492ac16af00e14770806
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782487"
---
# <a name="icordebugheapenumnext-method"></a>ICorDebugHeapEnum::Next Yöntemi
Yönetilen yığında nesneler hakkında bilgi içeren [cor_heapobject](cor-heapobject-structure.md) örneklerinin belirtilen sayısını alır.  
  
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
 dışı Her biri yönetilen yığında bir nesne hakkında bilgi sağlayan [cor_heapobject](cor-heapobject-structure.md) nesnesine işaret eden işaretçiler dizisi.  
  
 Pceltfettiz  
 dışı Aslında `objects`döndürülen [cor_heapobject](cor-heapobject-structure.md) nesnelerinin sayısına yönelik bir işaretçi. Bu değer, `celt` 1 ise `null` olabilir.  
  
## <a name="remarks"></a>Açıklamalar  
 `COR_HEAPOBJECT.type` alanı, iç içe geçmiş bir başvuru sayılı COM arabiriminin tanımlayıcısıdır. Bu başvuru, `ICorDebugHeapEnum::Next`çağıranı tarafından yayınlanmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugHeapEnum Arabirimi](icordebugheapenum-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
