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
ms.openlocfilehash: d0dc301c67d09ebb15bf47cef15e642fb7c78fb9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792615"
---
# <a name="icordebugprocessgethelperthreadid-method"></a>ICorDebugProcess::GetHelperThreadID Yöntemi
Hata ayıklayıcının iç yardımcı iş parçacığının işletim sistemi (OS) iş parçacığı KIMLIĞINI alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetHelperThreadID (  
    [out] DWORD *pThreadID  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pThreadID`  
 dışı Hata ayıklayıcının iç yardımcı iş parçacığının işletim sistemi iş parçacığı KIMLIĞINE yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Yönetilen ve yönetilmeyen hata ayıklama sırasında, belirtilen KIMLIĞE sahip iş parçacığının, hata ayıklayıcı tarafından verilen bir kesme noktasına isabet ettiği durumlarda çalışmaya devam ettiğinden emin olmak için hata ayıklayıcının sorumluluğundadır. Bir hata ayıklayıcı, bu iş parçacığını kullanıcıdan gizlemek de isteyebilir. İşlemde henüz bir yardımcı iş parçacığı yoksa, `GetHelperThreadID` yöntemi *`pThreadID`sıfır döndürür.  
  
 Zamanla değiştirebileceğinden, yardımcı iş parçacığının iş parçacığı KIMLIĞINI önbelleğe alamaz. Her durdurma olayında iş parçacığı KIMLIĞINI yeniden sorgulamalısınız.  
  
 Hata ayıklayıcının yardımcı iş parçacığının iş parçacığı KIMLIĞI, her yönetilmeyen [ICorDebugManagedCallback:: CreateThread](icordebugmanagedcallback-createthread-method.md) olayında doğru olacaktır, böylece bir hata ayıklayıcının yardımcı iş parçacığının Iş parçacığı kimliğini belirlemesine ve kullanıcıdan gizlemesini sağlar. Yönetilmeyen `ICorDebugManagedCallback::CreateThread` bir olay sırasında yardımcı iş parçacığı olarak tanımlanan bir iş parçacığı, yönetilen Kullanıcı kodunu hiçbir şekilde çalıştırmaz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL. CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
