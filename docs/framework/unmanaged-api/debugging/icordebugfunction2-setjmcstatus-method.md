---
title: "ICorDebugFunction2::SetJMCStatus Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction2.SetJMCStatus
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunction2::SetJMCStatus
helpviewer_keywords:
- ICorDebugFunction2::SetJMCStatus method [.NET Framework debugging]
- SetJMCStatus method, ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: 22c27b01-2869-4214-b840-5921f7c874fc
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0ecbcd5b8171a169fbfdd7175d3d9dfbbcb3855f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
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
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
