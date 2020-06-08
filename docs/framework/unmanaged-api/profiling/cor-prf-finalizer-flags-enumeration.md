---
title: COR_PRF_FINALIZER_FLAGS Numaralandırması
ms.date: 03/30/2017
api_name:
- COR_PRF_FINALIZER_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FINALIZER_FLAGS
helpviewer_keywords:
- COR_PRF_FINALIZER_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 297d7721-3911-4f36-9e34-d9da0c33e22a
topic_type:
- apiref
ms.openlocfilehash: b273faafd7abb86ace58bb5c24473406af3ce20e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500981"
---
# <a name="cor_prf_finalizer_flags-enumeration"></a>COR_PRF_FINALIZER_FLAGS Numaralandırması
Bir nesne için sonlandırıcıyı açıklar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum {  
    COR_PRF_FINALIZER_CRITICAL = 0x1  
} COR_PRF_FINALIZER_FLAGS;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Description|  
|------------|-----------------|  
|`COR_PRF_FINALIZER_CRITICAL`|Sonlandırıcı kritik öneme sahiptir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `COR_PRF_FINALIZER_FLAGS`Numaralandırma, bir nesnenin sonlandırıcısını anlatmak Için [ICorProfilerCallback2:: Finalizeableobjectkuyruklanmış](icorprofilercallback2-finalizeableobjectqueued-method.md) yöntemi tarafından kullanılır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Sabit Listeleri](profiling-enumerations.md)
