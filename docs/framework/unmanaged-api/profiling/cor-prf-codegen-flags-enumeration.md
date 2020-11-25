---
title: COR_PRF_CODEGEN_FLAGS Sabit Listesi
ms.date: 03/30/2017
api_name:
- COR_PRF_CODEGEN_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_CODEGEN_FLAGS
helpviewer_keywords:
- COR_PRF_CODEGEN_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 3e184022-0247-4824-a23d-6b29593d8d01
topic_type:
- apiref
ms.openlocfilehash: 3252e3b33da743c0e146e25f798c0e669aeb74ef
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718611"
---
# <a name="cor_prf_codegen_flags-enumeration"></a>COR_PRF_CODEGEN_FLAGS Sabit Listesi

[ICorProfilerFunctionControl:: SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) yöntemiyle ayarlanabilmesi için kod oluşturma bayraklarını tanımlar.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef enum {  
    COR_PRF_CODEGEN_DISABLE_INLINING =          0x0001,  
    COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS = 0x0002,  
} COR_PRF_CODEGEN_FLAGS;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`COR_PRF_CODEGEN_DISABLE_INLINING`|Bu işlevin gövdesinde hiçbir işlev satır içine alınmaz. Ancak, işlevin kendisine çağıranları satır içine alınmış olabilir.|  
|`COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS`|Bu işlevin gövdesi için tüm iyileştirmeler devre dışı bırakılacak. Ancak, işlevin kendisi hala çağıranlar içinde yer alabilir.|  
  
## <a name="remarks"></a>Açıklamalar  

 `COR_PRF_CODEGEN_FLAGS`Numaralandırma, [ICorProfilerFunctionControl:: SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) yöntemi tarafından, profil oluşturucunun JIT işlevi için kod oluşturmayı denetlemesini etkinleştirmek üzere kullanılır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Numaralandırmaları](profiling-enumerations.md)
