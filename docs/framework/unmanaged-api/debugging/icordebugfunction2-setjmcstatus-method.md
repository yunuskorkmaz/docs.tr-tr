---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugFunction2:: SetJMCStatus yöntemi'
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
ms.openlocfilehash: d2df9d47808b0220a91bd344e7600f8d16eccdb4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692197"
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
 'ndaki `true` İşlevi Kullanıcı kodu olarak işaretlemek için olarak ayarlayın; Aksi takdirde, olarak ayarlayın `false` .  
  
## <a name="return-values"></a>Dönüş Değerleri  
  
|HRESULT|Description|  
|-------------|-----------------|  
|`S_OK`|İşlev başarıyla işaretlendi.|  
|`CORDBG_E_FUNCTION_NOT_DEBUGGABLE`|İşlev, hata ayıklanamadığından Kullanıcı kodu olarak işaretlenemedi.|  
  
## <a name="remarks"></a>Açıklamalar  

 Bir Yalnızca kendi kodum Stepper, Kullanıcı olmayan kodu atlar. Kullanıcı kodu hata ayıklanabilir kodunun bir alt kümesi olmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
