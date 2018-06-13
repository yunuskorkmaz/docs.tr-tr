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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 20833624b4b853a1a56964e11a25f446c6b39053
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414719"
---
# <a name="icordebugmdagetosthreadid-method"></a>ICorDebugMDA::GetOSThreadId Metodu
Yönetilen hata ayıklama Yardımcısı (MDA) bağlı temsil ettiği işletim sistemi (OS) iş parçacığı tanımlayıcısını alır [Icordebugmda](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) yürütüyor.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetOSThreadId (  
    [out] DWORD    *pOsTid  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pOsTid`  
 [out] İşletim sistemi iş parçacığı tanımlayıcısı için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 İşletim sistemi iş parçacığı bir Icordebugthread yerine bir MDA yerel iş parçacığı veya yönetilen kod henüz girilmemiş yönetilen bir iş parçacığı tetiklenir durumlar için izin vermek için kullanılır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugMDA Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)  
 [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
