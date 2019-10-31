---
title: ICorDebugProcess::ModifyLogSwitch Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.ModifyLogSwitch
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::ModifyLogSwitch
helpviewer_keywords:
- ICorDebugProcess::ModifyLogSwitch method [.NET Framework debugging]
- ModifyLogSwitch method [.NET Framework debugging]
ms.assetid: 5fd30875-555e-4e96-877b-5dd266cde7c4
topic_type:
- apiref
ms.openlocfilehash: 86b8737577bdb5f61f1061cb217620fae03ebd0c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139378"
---
# <a name="icordebugprocessmodifylogswitch-method"></a>ICorDebugProcess::ModifyLogSwitch Yöntemi
Belirtilen günlük anahtarının önem derecesini ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT ModifyLogSwitch(  
    [in] WCHAR *pLogSwitchName,  
    [in] LONG  lLevel);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pLogSwitchName`  
 'ndaki Günlük anahtarının adını belirten bir dize işaretçisi.  
  
 `lLevel`  
 'ndaki Belirtilen günlük anahtarı için ayarlanacak önem düzeyi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem yalnızca [ICorDebugManagedCallback:: CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) geri çağırma işlemi gerçekleştirildikten sonra geçerlidir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
