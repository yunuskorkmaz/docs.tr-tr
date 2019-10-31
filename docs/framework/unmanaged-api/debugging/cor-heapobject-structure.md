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
ms.openlocfilehash: 270360a8950197eca14e02a60554659e5ac7b91c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099072"
---
# <a name="cor_heapobject-structure"></a>COR_HEAPOBJECT Yapısı
Yönetilen yığında bir nesne hakkında bilgi sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
 `COR_HEAPOBJECT` örnekleri, [ICorDebugProcess5:: EnumerateHeap](icordebugprocess5-enumerateheap-method.md) yöntemi çağırarak doldurulan bir [ICorDebugHeapEnum](icordebugheapenum-interface.md) arabirimi nesnesi numaralandırarak alınabilir.  
  
 `COR_HEAPOBJECT` bir örnek, yönetilen yığında canlı bir nesne veya herhangi bir nesne tarafından kökü belirtilmemiş ancak atık toplayıcı tarafından henüz toplanmayan bir nesne hakkında bilgi sağlar.  
  
 Daha iyi performans için `COR_HEAPOBJECT.address` alanı, hata ayıklama API 'sinin büyük bir kısmında kullanılan ICorDebugValue arabirimi değeri yerine `CORDB_ADDRESS` bir değerdir. Belirli bir nesne adresi için bir ICorDebugValue nesnesi almak üzere `CORDB_ADDRESS` değerini [ICorDebugProcess5:: GetObject](icordebugprocess5-getobject-method.md) metoduna geçirebilirsiniz.  
  
 Daha iyi performans için `COR_HEAPOBJECT.type` alanı, hata ayıklama API 'sinin büyük bir kısmında kullanılan ICorDebugType arabirim değeri yerine `COR_TYPEID` bir değerdir. Belirli bir tür KIMLIĞI için bir ICorDebugType nesnesi almak üzere `COR_TYPEID` değerini [ICorDebugProcess5:: GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) metoduna geçirebilirsiniz.  
  
 `COR_HEAPOBJECT` yapısı, başvuru sayılı bir COM arabirimi içerir. [ICorDebugHeapEnum:: Next](icordebugheapenum-next-method.md) metodunu çağırarak numaralandırıcıda bir `COR_HEAPOBJECT` örneği alırsanız, daha sonra başvuruyu serbest bırakmanız gerekir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Yapıları](debugging-structures.md)
- [Hata Ayıklama](index.md)
