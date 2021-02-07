---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugHeapEnum:: Next yöntemi'
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
ms.openlocfilehash: 22e81b9b0c4ac2027f932187b6f860d08adf6f97
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691958"
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
 dışı Aslında ' de döndürülen [cor_heapobject](cor-heapobject-structure.md) nesnelerinin sayısına yönelik bir işaretçi `objects` . Bu değer 1 ise `null` olabilir `celt` .  
  
## <a name="remarks"></a>Açıklamalar  

 `COR_HEAPOBJECT.type`Alan, iç içe geçmiş bir başvuru SAYıLı com arabiriminin tanımlayıcısıdır. Bu başvuru, çağıran tarafından yayınlanmalıdır `ICorDebugHeapEnum::Next` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugHeapEnum Arabirimi](icordebugheapenum-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
