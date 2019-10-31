---
title: ICorDebugProcess::GetThread Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetThread
helpviewer_keywords:
- ICorDebugProcess::GetThread method [.NET Framework debugging]
- GetThread method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: a48261ed-700b-41c9-8cb4-18c526546603
topic_type:
- apiref
ms.openlocfilehash: 6bf73a4be40f1fbd8e9d37477907001604e8e4a6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128814"
---
# <a name="icordebugprocessgetthread-method"></a>ICorDebugProcess::GetThread Metodu
Belirtilen işletim sistemi (OS) iş parçacığı KIMLIĞINE sahip bu işlemin iş parçacığını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetThread(  
    [in] DWORD dwThreadId,  
    [out] ICorDebugThread **ppThread);  
```  
  
## <a name="parameters"></a>Parametreler  
 `dwThreadId`  
 'ndaki Alınacak iş parçacığının işletim sistemi iş parçacığı KIMLIĞI.  
  
 `ppThread`  
 dışı İş parçacığını temsil eden ICorDebugThread nesnesinin adresine yönelik bir işaretçi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
