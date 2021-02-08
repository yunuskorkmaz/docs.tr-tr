---
description: ': ICorDebugProcess:: GetHelperThreadID yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: ee7bd2106a37c5c67df48a54ff9ab7fa49a03f80
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801026"
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

 Yönetilen ve yönetilmeyen hata ayıklama sırasında, belirtilen KIMLIĞE sahip iş parçacığının, hata ayıklayıcı tarafından verilen bir kesme noktasına isabet ettiği durumlarda çalışmaya devam ettiğinden emin olmak için hata ayıklayıcının sorumluluğundadır. Bir hata ayıklayıcı, bu iş parçacığını kullanıcıdan gizlemek de isteyebilir. İşlemde henüz bir yardımcı iş parçacığı yoksa, `GetHelperThreadID` Yöntem * içinde 0 döndürür `pThreadID` .  
  
 Zamanla değiştirebileceğinden, yardımcı iş parçacığının iş parçacığı KIMLIĞINI önbelleğe alamaz. Her durdurma olayında iş parçacığı KIMLIĞINI yeniden sorgulamalısınız.  
  
 Hata ayıklayıcının yardımcı iş parçacığının iş parçacığı KIMLIĞI, her yönetilmeyen [ICorDebugManagedCallback:: CreateThread](icordebugmanagedcallback-createthread-method.md) olayında doğru olacaktır, böylece bir hata ayıklayıcının yardımcı iş parçacığının Iş parçacığı kimliğini belirlemesine ve kullanıcıdan gizlemesini sağlar. Yönetilmeyen bir olay sırasında yardımcı iş parçacığı olarak tanımlanan bir iş parçacığı `ICorDebugManagedCallback::CreateThread` , yönetilen Kullanıcı kodunu hiçbir şekilde çalıştırmaz.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL. CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
