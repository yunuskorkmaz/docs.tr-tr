---
title: COR_HEAPOBJECT Yapısı
ms.date: 03/30/2017
api_name:
- COR_HEAPOBJECT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_HEAPOBJECT
helpviewer_keywords:
- COR_HEAPOBJECT structure [.NET Framework debugging]
ms.assetid: a92fdf95-492b-49ae-a741-2186e5c1d7c5
topic_type:
- apiref
ms.openlocfilehash: 54af02b48dabdf2042763954805f0d454323ac89
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726372"
---
# <a name="cor_heapobject-structure"></a>COR_HEAPOBJECT Yapısı

Yönetilen yığında bir nesne hakkında bilgi sağlar.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef struct _COR_HEAPOBJECT {  
    CORDB_ADDRESS address;
    ULONG64 size;
    COR_TYPEID type;
} COR_HEAPOBJECT;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`address`|Bellekteki nesnenin adresi.|  
|`size`|Nesnenin bayt cinsinden toplam boyutu.|  
|`type`|Nesnenin türünü temsil eden bir [COR_TYPEID](cor-typeid-structure.md) belirteci.|  
  
## <a name="remarks"></a>Açıklamalar  

 `COR_HEAPOBJECT`örnekler, [ICorDebugProcess5:: EnumerateHeap](icordebugprocess5-enumerateheap-method.md) yöntemi çağırarak doldurulan bir [ICorDebugHeapEnum](icordebugheapenum-interface.md) arabirimi nesnesi numaralandırarak alınabilir.  
  
 `COR_HEAPOBJECT`Örnek, yönetilen yığında canlı bir nesne veya herhangi bir nesne tarafından kökü belirtilmemiş ancak çöp toplayıcı tarafından henüz toplanmayan bir nesne hakkında bilgi sağlar.  
  
 Daha iyi performans için, `COR_HEAPOBJECT.address` alan, `CORDB_ADDRESS` hata ayıklama API 'sinin büyük bir kısmında kullanılan ICorDebugValue arabirimi değeri yerine bir değerdir. Belirli bir nesne adresi için bir ICorDebugValue nesnesi almak üzere, `CORDB_ADDRESS` değeri [ICorDebugProcess5:: GetObject](icordebugprocess5-getobject-method.md) yöntemine geçirebilirsiniz.  
  
 Daha iyi performans için, `COR_HEAPOBJECT.type` alan, `COR_TYPEID` hata ayıklama API 'sinin büyük bir kısmında kullanılan ICorDebugType arabirim değeri yerine bir değerdir. Verilen tür KIMLIĞI için bir ICorDebugType nesnesi elde etmek için, `COR_TYPEID` değeri [ICorDebugProcess5:: GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) metoduna geçirebilirsiniz.  
  
 `COR_HEAPOBJECT`Yapı, başvuru sayılı BIR com arabirimi içerir. `COR_HEAPOBJECT` [ICorDebugHeapEnum:: Next](icordebugheapenum-next-method.md) metodunu çağırarak numaralandırıcıdan bir örnek alırsanız, daha sonra başvuruyu serbest bırakmanız gerekir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Yapıları](debugging-structures.md)
- [Hata Ayıklama](index.md)
