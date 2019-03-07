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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49ced1b4be888c7550c3927d1b319ab2f0bef086
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57501012"
---
# <a name="icordebugfunction2setjmcstatus-method"></a>ICorDebugFunction2::SetJMCStatus Yöntemi
Yalnızca benim kodum bu Icordebugfunction2 tarafından temsil edilen işlevi işaretler Adımlama.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `bIsJustMyCode`  
 [in] Kümesine `true` işlevi kullanıcı kodu; olarak işaretlemek için Aksi takdirde, kümesine `false`.  
  
## <a name="return-values"></a>Dönüş Değerleri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|`S_OK`|İşlev başarıyla işaretlendi.|  
|`CORDBG_E_FUNCTION_NOT_DEBUGGABLE`|İşlevi, hata ayıklaması yapamazsınız çünkü kullanıcı kodu işaretlenemez.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yalnızca kendi kodum Adımlayıcı kullanıcı olmayan kod atlar. Kullanıcı kodu hata ayıklaması yapılabilir kod bir alt kümesi olmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
