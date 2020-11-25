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
ms.openlocfilehash: 1db2c9b5e65ae150f05242172f5ea16db433bbb5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717831"
---
# <a name="icordebugclass2setjmcstatus-method"></a>ICorDebugClass2::SetJMCStatus Yöntemi

Sınıfının her yöntemi için, yöntemin Kullanıcı tanımlı kod olup olmadığını belirten bir değer ayarlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `bIsJustMyCode`  
 'ndaki `true` Metodun Kullanıcı tanımlı kod olduğunu belirtmek için olarak ayarlanır; Aksi takdirde, olarak ayarlayın `false` .  
  
## <a name="remarks"></a>Açıklamalar  

 Just-Code (JMC) Stepper, Kullanıcı tanımlı olmayan kodu atlar. Kullanıcı tanımlı kodun bir hata ayıklanabilir kodu alt kümesi olması gerekir.  
  
 `SetJMCStatus` Tüm diğer yöntemler için değeri başarıyla ayarlasa bile, herhangi bir yöntem için değeri ayarlayamazsa, bir S_FALSE HRESULT değeri döndürür.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
