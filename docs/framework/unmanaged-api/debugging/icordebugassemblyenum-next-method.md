---
title: ICorDebugAssemblyEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugAssemblyEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssemblyEnum::Next method
helpviewer_keywords:
- ICorDebugAssemblyEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugAssemblyEnum interface [.NET Framework debugging]
ms.assetid: b3e7d0c2-3baa-4ef8-8e3f-b865cf252940
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 00adc852a0940766cdd4188ffa5d6be2b472e51f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744882"
---
# <a name="icordebugassemblyenumnext-method"></a>ICorDebugAssemblyEnum::Next Yöntemi
Koleksiyondan geçerli imleç konumundan başlayarak belirtilen sayıda derlemeleri alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugAssembly *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `celt`  
 [in] Alınacak derlemeleri sayısı.  
  
 `values`  
 [out] Bir dizi işaretçileri, her biri bir derlemeyi temsil eden bir Icordebugassembly nesneye işaret eder.  
  
 `pceltFetched`  
 [out] Gerçekte döndürülen derlemeleri sayısı için bir işaretçi. Bu değer null olabilir, `celt` biridir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
