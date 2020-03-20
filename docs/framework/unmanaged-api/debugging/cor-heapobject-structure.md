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
ms.openlocfilehash: efb3d913e1d8ef0c486d7e5e1d9777ae7d88bc71
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179331"
---
# <a name="cor_heapobject-structure"></a>COR_HEAPOBJECT Yapısı
Yönetilen yığındaki bir nesne hakkında bilgi sağlar.  
  
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
|`size`|Nesnenin toplam boyutu, baytlar içinde.|  
|`type`|Nesnenin türünü temsil eden [COR_TYPEID](cor-typeid-structure.md) belirteci.|  
  
## <a name="remarks"></a>Açıklamalar  
 `COR_HEAPOBJECT`örnekler [ICorDebugProcess5::EnumerateHeap](icordebugprocess5-enumerateheap-method.md) yöntemi ni arayarak doldurulan bir [ICorDebugHeapEnum](icordebugheapenum-interface.md) arabirim nesnesini sayısallandırarak alınabilir.  
  
 Örnek, `COR_HEAPOBJECT` yönetilen yığındaki canlı bir nesne veya herhangi bir nesne tarafından köklü olmayan ancak çöp toplayıcı tarafından henüz toplanmamış bir nesne hakkında bilgi sağlar.  
  
 Daha iyi performans `COR_HEAPOBJECT.address` için `CORDB_ADDRESS` alan, hata ayıklama API'sinin çoğunda kullanılan ICorDebugValue arabirim değeri yerine bir değerdir. Belirli bir nesne adresi için bir ICorDebugValue nesnesi elde etmek `CORDB_ADDRESS` için, değeri [ICorDebugProcess5::GetObject](icordebugprocess5-getobject-method.md) yöntemine geçirebilirsiniz.  
  
 Daha iyi performans `COR_HEAPOBJECT.type` için `COR_TYPEID` alan, hata ayıklama API'sinin çoğunda kullanılan ICorDebugType arabirim değeri yerine bir değerdir. Belirli bir tür kimliği için bir ICorDebugType nesnesi elde etmek `COR_TYPEID` için, değeri [ICorDebugProcess5::GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) yöntemine geçirebilirsiniz.  
  
 Yapı, `COR_HEAPOBJECT` referans sayılan com arabirimi içerir. `COR_HEAPOBJECT` [ICorDebugHeapEnum::Sonraki](icordebugheapenum-next-method.md) yöntem çağırarak enumerator bir örnek alırsanız, daha sonra başvuru serbest gerekir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üstbilgi:** CorDebug.idl, CorDebug.h  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Yapıları](debugging-structures.md)
- [Hata ayıklama](index.md)
