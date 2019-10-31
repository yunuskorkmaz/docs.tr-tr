---
title: ICorDebugFunction2::SetJMCStatus Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::SetJMCStatus
helpviewer_keywords:
- ICorDebugFunction2::SetJMCStatus method [.NET Framework debugging]
- SetJMCStatus method, ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: 22c27b01-2869-4214-b840-5921f7c874fc
topic_type:
- apiref
ms.openlocfilehash: 758364b2d63343e464b727d5a1c1817533a6acea
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137791"
---
# <a name="icordebugfunction2setjmcstatus-method"></a>ICorDebugFunction2::SetJMCStatus Yöntemi
Yalnızca kendi kodum Adımlama için bu ICorDebugFunction2 tarafından temsil edilen işlevi işaretler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `bIsJustMyCode`  
 'ndaki İşlevi Kullanıcı kodu olarak işaretlemek için `true` olarak ayarlayın; Aksi takdirde, `false`olarak ayarlayın.  
  
## <a name="return-values"></a>Dönüş Değerleri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|`S_OK`|İşlev başarıyla işaretlendi.|  
|`CORDBG_E_FUNCTION_NOT_DEBUGGABLE`|İşlev, hata ayıklanamadığından Kullanıcı kodu olarak işaretlenemedi.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir Yalnızca kendi kodum Stepper, Kullanıcı olmayan kodu atlar. Kullanıcı kodu hata ayıklanabilir kodunun bir alt kümesi olmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
