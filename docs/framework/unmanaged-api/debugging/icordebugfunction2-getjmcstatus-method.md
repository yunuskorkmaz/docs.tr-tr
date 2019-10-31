---
title: ICorDebugFunction2::GetJMCStatus Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.GetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::GetJMCStatus
helpviewer_keywords:
- ICorDebugFunction2::GetJMCStatus method [.NET Framework debugging]
- GetJMCStatus method [.NET Framework debugging]
ms.assetid: 840a71ed-bf5a-4f5e-8ed6-762222b34493
topic_type:
- apiref
ms.openlocfilehash: 360434fe6e08804d8c80c4ea36d585209cc6761a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137814"
---
# <a name="icordebugfunction2getjmcstatus-method"></a>ICorDebugFunction2::GetJMCStatus Metodu
Bu ICorDebugFunction2 nesnesi tarafından temsil edilen işlevin Kullanıcı kodu olarak işaretlenip işaretlenmediğini gösteren bir değer alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetJMCStatus (  
    [out] BOOL   *pbIsJustMyCode  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pbIsJustMyCode`  
 dışı Bu işlev kullanıcı kodu olarak işaretlenmişse `true`Boolean değere yönelik bir işaretçi; Aksi takdirde, değer `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu `ICorDebugFunction2` tarafından temsil edilen işlevin ayıklanamayacağını belirlerseniz, `pbIsJustMyCode` her zaman `false`olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
