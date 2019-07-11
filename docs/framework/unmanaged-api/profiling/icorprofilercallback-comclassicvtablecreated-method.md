---
title: ICorProfilerCallback::COMClassicVTableCreated Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.COMClassicVTableCreated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::COMClassicVTableCreated
helpviewer_keywords:
- COMClassicVTableCreated method [.NET Framework profiling]
- ICorProfilerCallback::COMClassicVTableCreated method [.NET Framework profiling]
ms.assetid: 6e1834ab-c359-498a-b10b-984ae23cdda4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 062b63776264ae553039a2db0fc99d4fb7bec476
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745332"
---
# <a name="icorprofilercallbackcomclassicvtablecreated-method"></a>ICorProfilerCallback::COMClassicVTableCreated Yöntemi
Profil Oluşturucu, belirtilen IID ve sınıfı bir COM birlikte çalışma vtable oluşturulduğunu bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT COMClassicVTableCreated(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable,  
    [in] ULONG   cSlots);  
```  
  
## <a name="parameters"></a>Parametreler  
 `wrappedClasId`  
 [in] Vtable oluşturulan sınıfın Kimliğidir.  
  
 `implementedIID`  
 [in] Sınıfı tarafından uygulanan arabirim kimliği. Arabirimi yalnızca iç ise bu değer NULL olabilir.  
  
 `pVTable`  
 [in] Vtable başlangıcı için bir işaretçi.  
  
 `cSlots`  
 [in] Vtable içinde olan yuva sayısı.  
  
## <a name="remarks"></a>Açıklamalar  
 Yığın atık toplama izin veren bir durumda olmayabilir çünkü profil oluşturucu bu yöntemin uygulanması Engellemesi gereken değil ve bu nedenle preemptive çöp toplama etkinleştirilemez. Burada profil oluşturucu engellerse ve çöp toplama denenir, çalışma zamanı, bu geri dönene kadar engeller.  
  
 Bu yöntemin uygulanmasını profil oluşturucunun yönetilen koda veya herhangi bir yönetilen bellek ayırma yol neden çağırmalıdır değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [COMClassicVTableDestroyed Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtabledestroyed-method.md)
