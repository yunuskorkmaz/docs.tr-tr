---
title: ICorDebugThread::CreateStepper Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugThread.CreateStepper
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::CreateStepper
helpviewer_keywords:
- ICorDebugThread::CreateStepper method [.NET Framework debugging]
- CreateStepper method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 4657443f-dd12-431b-a648-175c23f13c83
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 89182739633984011aaab3d7900d376b6db5ef99
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987195"
---
# <a name="icordebugthreadcreatestepper-method"></a>ICorDebugThread::CreateStepper Yöntemi
Bu Icordebugthread etkin çerçeveye Adımlama izin veren bir ICorDebugStepper nesnesi oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CreateStepper (  
    [out] ICorDebugStepper **ppStepper  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ppStepper`  
 [out] Adresine bir işaretçi bir `ICorDebugStepper` bu iş parçacığının etkin çerçeveye Adımlama sağlayan nesne.  
  
## <a name="remarks"></a>Açıklamalar  
 Yönetilmeyen kod etkin olabilir.  
  
 `ICorDebugStepper` Arabirimi, gerçek Adımlama gerçekleştirmek için kullanılmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
