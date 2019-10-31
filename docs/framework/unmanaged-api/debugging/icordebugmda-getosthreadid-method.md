---
title: ICorDebugMDA::GetOSThreadId Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetOSThreadId
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetOSThreadId
helpviewer_keywords:
- ICorDebugMDA::GetOSThreadId method [.NET Framework debugging]
- GetOSThreadId method [.NET Framework debugging]
ms.assetid: 7ca7c364-ade4-4219-b434-9f6ae2359be6
topic_type:
- apiref
ms.openlocfilehash: e9846234f8217b822860c2400a54a91a651a0a56
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129827"
---
# <a name="icordebugmdagetosthreadid-method"></a>ICorDebugMDA::GetOSThreadId Metodu
[ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) tarafından temsil edilen yönetilen hata ayıklama Yardımcısı (MDA) ' nin yürütüldüğü işletim SISTEMI (OS) iş parçacığı tanımlayıcısını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetOSThreadId (  
    [out] DWORD    *pOsTid  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pOsTid`  
 dışı İşletim sistemi iş parçacığı tanımlayıcısına yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 İşletim sistemi iş parçacığı bir ICorDebugThread yerine, bir MDA 'ın yerel bir iş parçacığında ya da henüz yönetilen kodu girilmemiş yönetilen bir iş parçacığında tetiklenme durumlarına izin vermek için kullanılır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugMDA Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
