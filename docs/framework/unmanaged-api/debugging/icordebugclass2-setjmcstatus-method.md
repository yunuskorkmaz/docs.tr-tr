---
title: ICorDebugClass2::SetJMCStatus Yöntemi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6ed6570e11008e52d4b1f97c2dc90e2ccbef2e35
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471394"
---
# <a name="icordebugclass2setjmcstatus-method"></a>ICorDebugClass2::SetJMCStatus Yöntemi
Sınıfının her yöntemi için yöntem kullanıcı tarafından tanımlanan kod olup olmadığını gösteren bir değer ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `bIsJustMyCode`  
 [in] Kümesine `true` yöntemi, kullanıcı tanımlı olduğunu belirtmek için; Aksi takdirde, kümesine kodu `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 Just--kendi kodum (JMC) Adımlayıcı kullanıcı tanımlı olmayan kod atlar. Kullanıcı tarafından tanımlanan kod hata ayıklaması yapılabilir kod bir alt kümesi olmalıdır.  
  
 `SetJMCStatus` başarılı bir şekilde tüm diğer yöntemler için değeri ayarlar bile herhangi bir yöntem için bir değer ayarlamak başarısız olursa bir HRESULT değerini S_FALSE döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
