---
title: ICorDebugStepperEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugStepperEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepperEnum::Next
helpviewer_keywords:
- Next method, ICorDebugStepperEnum interface [.NET Framework debugging]
- ICorDebugStepperEnum::Next method [.NET Framework debugging]
ms.assetid: d0ea0f30-e8d2-48b0-8477-e1a029ceb4dd
topic_type:
- apiref
ms.openlocfilehash: 11d9c7393827b613d49e23972b4896bfe657a544
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138982"
---
# <a name="icordebugstepperenumnext-method"></a>ICorDebugStepperEnum::Next Yöntemi
Geçerli konumdan başlayarak Numaralandırmadaki belirtilen ICorDebugStepper örnek sayısını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT Next(  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugStepper *steppers[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `celt`  
 'ndaki Alınacak `ICorDebugStepper` örneklerinin sayısı.  
  
 `steppers`  
 dışı Her biri bir `ICorDebugStepper` nesnesine işaret eden işaretçiler dizisi.  
  
 `pceltFetched`  
 dışı Aslında döndürülen `ICorDebugStepper` örneklerinin sayısına yönelik işaretçi. `celt` bir tane ise bu değer null olabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
