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
ms.openlocfilehash: fb3e0ccb57cf3b056bd25e643706e49b8bc75531
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792548"
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
 Veriler, herhangi bir kesme noktası arkasında otomatik olarak yazılır. .NET Framework sürüm 2,0 ' de yerel hata ayıklayıcılar, yönerge akışına kesme noktaları eklemek için bu yöntemi kullanmamalıdır. Bunun yerine [ICorDebugProcess2:: SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md) kullanın.  
  
 `WriteMemory` yöntemi yalnızca yönetilen kodun dışında kullanılmalıdır. Yanlış kullanılırsa, bu yöntem çalışma zamanını bozabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
