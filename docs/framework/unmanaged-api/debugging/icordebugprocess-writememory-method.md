---
title: ICorDebugProcess::WriteMemory Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.WriteMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::WriteMemory
helpviewer_keywords:
- ICorDebugProcess::WriteMemory method [.NET Framework debugging]
- WriteMemory method [.NET Framework debugging]
ms.assetid: d5c07d86-045d-4391-893b-0bcd2959f90e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2e9d640fb1c9dae5bb195baa504e560ba8e45821
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57497099"
---
# <a name="icordebugprocesswritememory-method"></a>ICorDebugProcess::WriteMemory Yöntemi
Bu işlem belleği veri yazar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT WriteMemory(  
    [in]  CORDB_ADDRESS address,  
    [in]  DWORD size,  
    [in, size_is(size)] BYTE buffer[],  
    [out] SIZE_T *written);  
```  
  
## <a name="parameters"></a>Parametreler  
 `address`  
 [in] A `CORDB_ADDRESS` hangi verilere bellek alanı taban adresini değer yazılır. Veri aktarımı gerçekleşmeden önce sistem temel adreste başlayan belirtilen boyut, bellek alanını yazma için erişilebilir olduğunu doğrular. Erişilebilir durumda değilse, yöntem başarısız olur.  
  
 `size`  
 [in] Bellek alanına yazılacak bayt sayısı.  
  
 `buffer`  
 [in] Yazılacak veriler içeren arabellek.  
  
 `written`  
 [out] Bu işlem bellek alanında yazılan bayt sayısını alır bir değişken için bir işaretçi. Varsa `written` NULL ise bu parametre yoksayılır.  
  
## <a name="remarks"></a>Açıklamalar  
 Veriler herhangi bir kesme noktası otomatik olarak yazılır. .NET Framework sürüm 2. 0'da, yerel hata ayıklayıcılarının bu yöntem kesme noktaları yönerge akımına eklenecek kullanmamanız gerekir. Kullanım [Icordebugprocess2::setunmanagedbreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) yerine.  
  
 `WriteMemory` Yöntemi yalnızca yönetilen kod dışında kullanılması gerekir. Bu yöntem, çalışma zamanı yanlış kullandıysanız bozabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
