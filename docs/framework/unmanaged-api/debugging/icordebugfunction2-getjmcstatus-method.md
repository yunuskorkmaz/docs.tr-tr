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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d23a0a489cfe13201b7798920feb3528db3b0709
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988669"
---
# <a name="icordebugfunction2getjmcstatus-method"></a>ICorDebugFunction2::GetJMCStatus Metodu
Bu Icordebugfunction2 nesnesi tarafından temsil edilen işlevi kullanıcı kodu işaretlenmiş olup olmadığını gösteren bir değer alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetJMCStatus (  
    [out] BOOL   *pbIsJustMyCode  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pbIsJustMyCode`  
 [out] Boolean bir değer için bir işaretçi `true`, bu işlev, kullanıcı kodu işaretlenmiş; Aksi takdirde, değeri `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 İşlev bu tarafından temsil edilen varsa `ICorDebugFunction2` ayıklanamıyor, `pbIsJustMyCode` her zaman `false`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
