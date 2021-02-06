---
description: ': ICorDebugThread:: CreateStepper yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 378ce28281f4f284c36194f993a53598a9de3854
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659367"
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
 dışı `ICorDebugStepper` Bu iş parçacığının etkin çerçevesinin üzerinde Adımlama sağlayan bir nesnenin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 Etkin çerçeve yönetilmeyen bir kod olabilir.  
  
 Bu `ICorDebugStepper` arabirim, gerçek adımlamayı gerçekleştirmek için kullanılmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
