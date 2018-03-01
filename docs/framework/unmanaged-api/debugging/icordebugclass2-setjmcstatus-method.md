---
title: "ICorDebugClass2::SetJMCStatus Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugClass2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass2::SetJMCStatus
helpviewer_keywords:
- ICorDebugClass2::SetJMCStatus method [.NET Framework debugging]
- SetJMCStatus method, ICorDebugClass2 interface [.NET Framework debugging]
ms.assetid: 077e6c7f-f857-480c-bebb-76ee1de4e8fc
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5fa9de4482b674173dba6a8316491507330f6376
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugclass2setjmcstatus-method"></a>ICorDebugClass2::SetJMCStatus Yöntemi
Her sınıf yöntemi için yöntem kullanıcı tanımlı kod olup olmadığını belirten bir değer ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `bIsJustMyCode`  
 [in] Kümesine `true` yöntemi kullanıcı tanımlı olduğunu belirtmek için; Aksi takdirde kümesine kodu `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 Yalnızca-my-code (JMC) Adımlayıcı kullanıcı tanımlı olmayan kod atlar. Kullanıcı tanımlı kod bir alt kümesini debuggable kodu olmalıdır.  
  
 `SetJMCStatus`başarıyla diğer tüm yöntemleri için değeri ayarlar olsa bile herhangi bir yöntem değerini ayarlamak başarısız olursa S_FALSE HRESULT değerini döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
