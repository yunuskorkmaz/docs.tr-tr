---
title: ICorDebugThread::GetDebugState Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetDebugState
helpviewer_keywords:
- GetDebugState method [.NET Framework debugging]
- ICorDebugThread::GetDebugState method [.NET Framework debugging]
ms.assetid: 9be27b0c-1d99-4722-b0d4-40cf6753ce5c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 95d9696e29bc1b460c94d7f4d8afd3de82653333
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419636"
---
# <a name="icordebugthreadgetdebugstate-method"></a>ICorDebugThread::GetDebugState Metodu
Bu Icordebugthread nesne geçerli hata ayıklama durumunu alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetDebugState (  
    [out] CorDebugThreadState   *pState  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pState`  
 [out] Bu iş parçacığı geçerli hata ayıklama durumunu açıklayan CorDebugThreadState numaralandırma değerlerinin Bitsel birleşimine gösteren bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 İşlem şu anda durursa, `pState` işlemi devam için bu iş parçacığının gerçek geçerli durumu olsaydı bu iş parçacığı için var olan hata ayıklama durumuna temsil eder.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
