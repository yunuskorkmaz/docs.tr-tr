---
title: ICorDebugProcess::EnableLogMessages Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.EnableLogMessages
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::EnableLogMessages
helpviewer_keywords:
- ICorDebugProcess::EnableLogMessages method [.NET Framework debugging]
- EnableLogMessages method [.NET Framework debugging]
ms.assetid: 14a4e5a3-3eaf-4f53-9dd1-762726963a23
topic_type:
- apiref
ms.openlocfilehash: 4134062be93a2fc5e76949d465a7b5822556b408
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128897"
---
# <a name="icordebugprocessenablelogmessages-method"></a>ICorDebugProcess::EnableLogMessages Yöntemi
Günlük iletilerinin hata ayıklayıcıya aktarılmasını sağlar ve devre dışı bırakır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EnableLogMessages([in]BOOL fOnOff);  
```  
  
## <a name="parameters"></a>Parametreler  
 `fOnOff`  
 [in] `true` günlük iletilerinin iletimini sunar; `false`, iletimi devre dışı bırakır.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem yalnızca [ICorDebugManagedCallback:: CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) geri çağırma işlemi oluştuktan sonra geçerlidir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
