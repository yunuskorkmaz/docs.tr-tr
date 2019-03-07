---
title: ICorDebugProcess::GetHelperThreadID Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetHelperThreadID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetHelperThreadID
helpviewer_keywords:
- GetHelperThreadID method [.NET Framework debugging]
- ICorDebugProcess::GetHelperThreadID method [.NET Framework debugging]
ms.assetid: 84e1e605-37c1-49a5-8e12-35db85654622
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cd5e30d08e667dcd5a8be1f9502462f28290068e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494226"
---
# <a name="icordebugprocessgethelperthreadid-method"></a>ICorDebugProcess::GetHelperThreadID Yöntemi
Hata Ayıklayıcı'nın iç yardımcı iş parçacığı işletim sistemi (OS) iş parçacığı Kimliğini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetHelperThreadID (  
    [out] DWORD *pThreadID  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pThreadID`  
 [out] Bir işaretçi işletim sistemi iş parçacığı Hata Ayıklayıcı'nın iç Yardımcısı iş parçacığının kimliği.  
  
## <a name="remarks"></a>Açıklamalar  
 Yönetilen ve yönetilmeyen hata ayıklama sırasında bu, hata ayıklayıcı tarafından yerleştirilen bir kesme noktasına denk gelir, belirtilen Kimliğe sahip bir iş parçacığı çalışan kalmasını sağlamak için hata ayıklayıcı'nın sorumluluğundadır. Bir hata ayıklayıcı ayrıca kullanıcıdan bu iş parçacığı gizlemek isteyebilirsiniz. Hiçbir yardımcı iş parçacığı henüz işlemde varsa `GetHelperThreadID` yöntemi sıfır döndürür *`pThreadID`.  
  
 Zaman içinde değişebilir olduğundan yardımcı iş parçacığının iş parçacığı kimliği önbelleğe alamıyor. İş parçacığı kimliği her durdurma etkinlikte yeniden sorgulaması gerekir.  
  
 Hata Ayıklayıcı'nın yardımcı iş parçacığının iş parçacığı kimliği doğru her yönetilmeyen [Icordebugmanagedcallback::CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) olay, bu nedenle, yardımcı iş parçacığının iş parçacığı Kimliğini belirlemek ve kullanıcıdan gizlemek bir hata ayıklayıcı izin verme. Bir yardımcı iş parçacığı yönetilmeyen sırasında tanımlanan bir iş parçacığı `ICorDebugManagedCallback::CreateThread` olay asla yönetilen kullanıcı kodu çalıştırın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl. CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
