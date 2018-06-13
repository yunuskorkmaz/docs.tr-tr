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
ms.openlocfilehash: 15b102be5a792f982edeb320199576bdddbd859a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412366"
---
# <a name="icordebugfunction2setjmcstatus-method"></a>ICorDebugFunction2::SetJMCStatus Yöntemi
Sadece kendi kodumu bu Icordebugfunction2 tarafından temsil edilen işlevi işaretler atlama.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `bIsJustMyCode`  
 [in] Kümesine `true` işlevi kullanıcı kodu; olarak işaretlemek için Aksi takdirde kümesine `false`.  
  
## <a name="return-values"></a>Dönüş Değerleri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|`S_OK`|İşlev başarıyla işaretlendi.|  
|`CORDBG_E_FUNCTION_NOT_DEBUGGABLE`|Hata ayıklaması yapılamıyor çünkü işlev kullanıcı kodu olarak işaretlenemez.|  
  
## <a name="remarks"></a>Açıklamalar  
 Sadece kendi kodumu Adımlayıcı kullanıcı olmayan kod atlar. Kullanıcı kodu bir alt kümesini debuggable kodu olmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
