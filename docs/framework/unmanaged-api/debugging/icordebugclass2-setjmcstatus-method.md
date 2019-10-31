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
ms.openlocfilehash: a862dd3f6a9c10c6b3a5a0bb41208d351c4ca9f1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125699"
---
# <a name="icordebugclass2setjmcstatus-method"></a>ICorDebugClass2::SetJMCStatus Yöntemi
Sınıfının her yöntemi için, yöntemin Kullanıcı tanımlı kod olup olmadığını belirten bir değer ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `bIsJustMyCode`  
 'ndaki Metodun Kullanıcı tanımlı kod olduğunu göstermek için `true` olarak ayarlayın; Aksi takdirde, `false`olarak ayarlayın.  
  
## <a name="remarks"></a>Açıklamalar  
 Just-Code (JMC) Stepper, Kullanıcı tanımlı olmayan kodu atlar. Kullanıcı tanımlı kodun bir hata ayıklanabilir kodu alt kümesi olması gerekir.  
  
 `SetJMCStatus`, tüm diğer yöntemler için değeri başarıyla ayarlasa bile, herhangi bir yöntem için değeri ayarlayamazsa, S_FALSE değeri bir HRESULT değeri döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
