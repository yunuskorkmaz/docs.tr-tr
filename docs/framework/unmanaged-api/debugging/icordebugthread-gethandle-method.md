---
title: ICorDebugThread::GetHandle Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetHandle
helpviewer_keywords:
- GetHandle method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetHandle method [.NET Framework debugging]
ms.assetid: 172ef8c4-2ead-4cfc-bd2e-dee4fb7191cd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 54981be7104eb04ac6347ad13b61a69f40d4377c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67770616"
---
# <a name="icordebugthreadgethandle-method"></a>ICorDebugThread::GetHandle Yöntemi
Bu Icordebugthread etkin parçası için geçerli bir tanıtıcı alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetHandle (  
    [out] HTHREAD *phThreadHandle  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `phThreadHandle`  
 [out] Bu iş parçacığının etkin bölümünün tanıtıcısı bir HTHREAD işaretçisi.  
  
## <a name="remarks"></a>Açıklamalar  
 İşlemi yürütür ve iş parçacığı farklı kısımlarını farklı tanıtıcı değişebilir.  
  
 Bu işleyici hata ayıklama API'si tarafından sahiplenilir. Hata ayıklayıcı kullanmadan önce çoğaltmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
