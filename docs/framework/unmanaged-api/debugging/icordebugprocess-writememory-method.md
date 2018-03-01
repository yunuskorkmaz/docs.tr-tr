---
title: "ICorDebugProcess::WriteMemory Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2a1a12d1393d1db69ea47833958fdf828b552064
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocesswritememory-method"></a>ICorDebugProcess::WriteMemory Yöntemi
Bu işlem bellekte bir alanına veri yazar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT WriteMemory(  
    [in]  CORDB_ADDRESS address,  
    [in]  DWORD size,  
    [in, size_is(size)] BYTE buffer[],  
    [out] SIZE_T *written);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `address`  
 [in] A `CORDB_ADDRESS` hangi veriler için bellek alanı taban adresini değer yazılır. Veri aktarımı oluşmadan önce sistem temel adresinde başlayarak belirtilen boyut, bellek alanını yazma için erişilebilir olduğunu doğrular. Erişilebilir durumda değilse, yöntem başarısız olur.  
  
 `size`  
 [in] Bellek alanı yazılacak bayt sayısı.  
  
 `buffer`  
 [in] Yazılacak veriler içeren bir arabellek.  
  
 `written`  
 [out] Bu işlem bellek alanına yazılan bayt sayısı alan bir değişken için bir işaretçi. Varsa `written` null, bu parametre yoksayılır.  
  
## <a name="remarks"></a>Açıklamalar  
 Veriler otomatik olarak tüm kesme noktalarını yazılır. .NET Framework sürüm 2. 0'da, yerel hata ayıklayıcıları bu yöntem yönerge akışa kesme noktaları eklemesine kullanmamanız gerekir. Kullanım [Icordebugprocess2::setunmanagedbreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) yerine.  
  
 `WriteMemory` Yöntemi yalnızca yönetilen kod dışında kullanılması gerekir. Bu yöntem, yanlış kullandıysanız çalışma zamanı bozabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
