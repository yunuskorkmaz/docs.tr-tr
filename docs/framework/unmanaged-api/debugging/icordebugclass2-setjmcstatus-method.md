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
ms.openlocfilehash: 9fb2f960098e970b4d3d9f0be499f4d9fda6558e
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893904"
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
 'ndaki Yöntemin Kullanıcı `true` tanımlı kod olduğunu belirtmek için olarak ayarlayın; Aksi takdirde, olarak `false`ayarlayın.  
  
## <a name="remarks"></a>Açıklamalar  
 Just-Code (JMC) Stepper, Kullanıcı tanımlı olmayan kodu atlar. Kullanıcı tanımlı kodun bir hata ayıklanabilir kodu alt kümesi olması gerekir.  
  
 `SetJMCStatus`Tüm diğer yöntemler için değeri başarıyla ayarlasa bile, herhangi bir yöntem için değeri ayarlayamazsa, bir S_FALSE HRESULT değeri döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
