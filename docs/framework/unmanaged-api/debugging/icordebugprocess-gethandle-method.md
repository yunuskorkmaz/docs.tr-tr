---
title: ICorDebugProcess::GetHandle Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetHandle
helpviewer_keywords:
- GetHandle method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::GetHandle method [.NET Framework debugging]
ms.assetid: e7d3ecf5-09d2-4d94-abb6-ff3483deebb6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c5d81564a34ed8e7ef75840e3a174661c36f5411
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994505"
---
# <a name="icordebugprocessgethandle-method"></a>ICorDebugProcess::GetHandle Metodu
İşlem için bir tanıtıcı alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetHandle([out] HPROCESS *phProcessHandle);  
```  
  
## <a name="parameters"></a>Parametreler  
 `phProcessHandle`  
 [out] Bir işaretçi bir `HPROCESS` yani işlem tanıtıcısı.  
  
## <a name="remarks"></a>Açıklamalar  
 Hata ayıklama arabirimi tarafından alınan tanıtıcı aittir. Hata ayıklayıcı tanıtıcı kullanmadan önce yinelenen.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
