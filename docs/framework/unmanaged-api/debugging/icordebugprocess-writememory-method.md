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
ms.openlocfilehash: eaf5b9980d55b0efb473b4631a8c052b013d0796
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137251"
---
# <a name="icordebugprocesswritememory-method"></a>ICorDebugProcess::WriteMemory Yöntemi
Bu işlemdeki bir bellek alanına veri yazar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT WriteMemory(  
    [in]  CORDB_ADDRESS address,  
    [in]  DWORD size,  
    [in, size_is(size)] BYTE buffer[],  
    [out] SIZE_T *written);  
```  
  
## <a name="parameters"></a>Parametreler  
 `address`  
 'ndaki Verilerin yazıldığı bellek alanının temel adresi olan bir `CORDB_ADDRESS` değeri. Veri aktarımı gerçekleşmeden önce, sistem, belirtilen boyuttaki bellek alanının temel adresten başlayarak, yazma için erişilebilir olduğunu doğrular. Erişilebilir değilse, yöntemi başarısız olur.  
  
 `size`  
 'ndaki Bellek alanına yazılacak baytların sayısı.  
  
 `buffer`  
 'ndaki Yazılacak verileri içeren bir arabellek.  
  
 `written`  
 dışı Bu işlemdeki bellek alanına yazılan bayt sayısını alan bir değişken işaretçisi. `written` NULL ise, bu parametre yok sayılır.  
  
## <a name="remarks"></a>Açıklamalar  
 Veriler, herhangi bir kesme noktası arkasında otomatik olarak yazılır. .NET Framework sürüm 2,0 ' de yerel hata ayıklayıcılar, yönerge akışına kesme noktaları eklemek için bu yöntemi kullanmamalıdır. Bunun yerine [ICorDebugProcess2:: SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) kullanın.  
  
 `WriteMemory` yöntemi yalnızca yönetilen kodun dışında kullanılmalıdır. Yanlış kullanılırsa, bu yöntem çalışma zamanını bozabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
