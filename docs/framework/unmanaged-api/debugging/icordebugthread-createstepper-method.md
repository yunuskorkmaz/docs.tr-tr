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
ms.openlocfilehash: d1b058aef66ed32c2cadcc3cfd72320dd8eb7729
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133588"
---
# <a name="icordebugthreadcreatestepper-method"></a>ICorDebugThread::CreateStepper Yöntemi
Bu ICorDebugThread 'in etkin çerçevesiyle Adımlama sağlayan bir ICorDebugStepper nesnesi oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CreateStepper (  
    [out] ICorDebugStepper **ppStepper  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ppStepper`  
 dışı Bu iş parçacığının etkin çerçevesinde Adımlama sağlayan bir `ICorDebugStepper` nesnesinin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Etkin çerçeve yönetilmeyen bir kod olabilir.  
  
 `ICorDebugStepper` arabirimi, gerçek adımlamayı gerçekleştirmek için kullanılmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
