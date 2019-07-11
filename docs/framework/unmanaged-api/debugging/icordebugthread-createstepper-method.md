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
ms.openlocfilehash: 95a00e8646589e7897636c1698b7c2647cd233fd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771806"
---
# <a name="icordebugthreadcreatestepper-method"></a>ICorDebugThread::CreateStepper Yöntemi
Bu Icordebugthread etkin çerçeveye Adımlama izin veren bir ICorDebugStepper nesnesi oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
