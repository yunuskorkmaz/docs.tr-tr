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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f179b58ff8eb51e2843780d3212cf38ed7d13216
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61609457"
---
# <a name="corheapobject-structure"></a>COR_HEAPOBJECT Yapısı
Yönetilen yığındaki bir nesne hakkında bilgi sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
|`size`|Nesnesinin bayt cinsinden toplam boyutu.|  
|`type`|A [cor_typeıd](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) nesnenin türünü temsil eden belirteci.|  
  
## <a name="remarks"></a>Açıklamalar  
 `COR_HEAPOBJECT` örnekleri numaralandırarak alınabilir bir [Icordebugheapenum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) çağırarak doldurulur arabirimi nesnesi [Icordebugprocess5::enumerateheap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) yöntemi.  
  
 A `COR_HEAPOBJECT` örneği, yönetilen yığındaki bir canlı nesne hakkında ya da herhangi bir nesne tarafından kökü belirtilmemiş ancak henüz çöp toplayıcısı tarafından toplanmış değil bir nesne hakkında bilgi sağlar.  
  
 Daha iyi performans için `COR_HEAPOBJECT.address` alan bir `CORDB_ADDRESS` değeri yerine Icordebugvalue arabirimi hata ayıklama API çoğunu kullanılan değer. Icordebugvalue nesnenin verilen nesnenin adresini almak için geçirebilirsiniz `CORDB_ADDRESS` değerini [Icordebugprocess5::GetObject](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md) yöntemi.  
  
 Daha iyi performans için `COR_HEAPOBJECT.type` alan bir `COR_TYPEID` değeri yerine Icordebugtype arabirimi hata ayıklama API çoğunu kullanılan değer. Icordebugtype nesneyi bir verilen tür Kimliğini almak için geçirebilirsiniz `COR_TYPEID` değerini [Icordebugprocess5::gettypefortypeıd](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md) yöntemi.  
  
 `COR_HEAPOBJECT` Yapısı başvuru sayılan bir COM arabirimi içerir. Aldığınız varsa bir `COR_HEAPOBJECT` çağırarak numaralandırıcı örneğinden [Icordebugheapenum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) yöntemi, başvuru daha sonra serbest bırakmanız gerekir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Yapıları](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
